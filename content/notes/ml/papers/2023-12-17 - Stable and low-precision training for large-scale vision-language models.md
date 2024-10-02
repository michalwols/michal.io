---
time_modified: 2024-10-01T22:49:57-04:00
time_created: 2023-12-17T12:50:39-05:00
---

#clip #vision-language 

- CLIP 1B Vit-Huge
- SwitchBack
	- int8 linear
	- 13-25% speedup
	- ~90% of transformer compute spent in linear layers
	- quant
		- quant noise grows with matrix multiply inner dimension size
			- happens with CLIP due to large batch size requirement
		- use 16bit precision for gradient of weight multiplication
		- int8 for forward and input grads
		- provide Triton kernel for SwitchBack
- reduce large magnitude features
	- layer scale init to 0
	- **loss spikes** occur 1-8 iterations after the squared gradients become under-estimated by their AdamW **second moment estimator**.
		- use **AdamW-Adafactor**, works better than grad clipping
- StableAdamW == AdamW-Adafactor
	- AdamW + Adafactor clipping
		- tracks the average ratio of the gradient square to the second moment estimator and lowers the learning rate when the ratio is large




```python
class SwitchBackMatmul(autograd.Function): @staticmethod

def forward(ctx, X, W): # X [b, n] inputs  
	# W [n, m] weights
	
	# save tensors in ctx
	ctx.save_for_backward = X, W  
	X_int8, state_X = row-wise_quantize(X)
	
	W_int8, state_W = tensor-wise_quantize(W)
	
	# Return output
	return matmul_int8_and_dequanitze(
	  X_int8, 
	  W_int8.t(), 
	  state_X, 
	  state_W
	)

@staticmethod  
def backward(ctx, G):
	# G [b, m] gradient to output # Recover tensors from ctx
	X, W = ctx.save_for_backward G_rowwise = rowwise_quantize(G)
	
	W_int8, state_W = tensor-wise_quantize_transpose(W)
	
	# Use 8bit matmul only for X_gradient
	X_gradient = matmul_int8_and_dequanitze(
	  G_int8, 
	  W_int8.t(), 
	  state_X, 
	  state_W
	)  
	W_gradient = matmul_fp16(G.t(), X)
	
	return X_gradient, W_gradient


class SwitchBackLinear(nn.Linear): def forward(self, X):
	return SwitchBackMatmul.apply(X, self.weight)
```