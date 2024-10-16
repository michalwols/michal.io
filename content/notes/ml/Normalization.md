---
time_modified: 2024-10-16T14:35:45-04:00
time_created: 2024-10-15T08:13:55-04:00
---

|**Normalization Method**|**Normalization Axis**|**Key Advantages**|**Key Disadvantages**|**Best Use Case**|
|---|---|---|---|---|
|**Batch Normalization**|Across mini-batch and feature|- Accelerates convergence  <br>- Provides regularization  <br>- Effective for large batches|- Ineffective with small batches  <br>- Not ideal for RNNs or variable-length sequences|CNNs, fully connected layers in vision tasks|
|**Instance Normalization**|Per instance, per channel|- Effective for tasks requiring instance-level statistics  <br>- Good for style transfer|- Ignores global batch statistics  <br>- Less effective for tasks requiring batch-wide consistency|Style transfer, GANs|
|**Layer Normalization**|Across feature dimension per input|- Independent of batch size  <br>- Works well with RNNs and transformers  <br>- Effective for sequential data|- Computationally more intensive than BatchNorm  <br>- Not as effective for convolutional layers|Transformers, RNNs, attention models|
|**RMS Normalization**|RMS across feature dimension|- Efficient variant of LayerNorm  <br>- Reduces computation by skipping mean subtraction  <br>- Suitable for large-scale models|- Lack of mean subtraction can cause instability in certain tasks|Transformers, large models where efficiency is critical|
|**Group Normalization**|Across groups of feature channels|- Works well with small mini-batches  <br>- Effective for visual recognition tasks  <br>- Less sensitive to batch size|- Needs manual tuning of the number of groups  <br>- Not as effective as BatchNorm with large batches|Vision models (ResNets, object detection)|
|**Weight Normalization**|Reparameterization of weights|- Simplifies optimization  <br>- Improves training speed  <br>- Less sensitive to batch size|- Needs to be combined with other methods for optimal performance|Reinforcement learning, generative models|
|**Spectral Normalization**|Normalizes spectral norm of weight matrices|- Ensures a bounded Lipschitz constant  <br>- Stabilizes GAN training  <br>- Reduces exploding gradients|- Can increase computational overhead  <br>- Specialized for GANs, less generalizable|GANs, particularly in the discriminator|
|**Batch-Instance Norm**|Weighted mix of BatchNorm and InstanceNorm|- Flexibility in balancing global and instance-level statistics  <br>- Adaptable to various vision tasks|- Additional complexity with two normalizations  <br>- Needs fine-tuning for optimal balance|Vision tasks like style transfer and object detection|
|**Switchable Norm**|Weighted combination of multiple normalization methods|- Adapts to the specific needs of each layer  <br>- Can combine strengths of BatchNorm, InstanceNorm, and LayerNorm|- Computationally expensive  <br>- Requires extra parameters for weighting|General deep learning models where adaptation is key|
|**Batch Renormalization**|Across mini-batch and feature with correction|- Works with small mini-batches  <br>- More stable for online learning or non-i.i.d. data|- Additional complexity  <br>- Slightly slower than standard BatchNorm|Small-batch training, online learning, RL|
|**Mean-Only Batch Norm**|Subtracts batch mean (ignores variance)|- Computationally efficient  <br>- Prevents mean-shift  <br>- Simplifies training|- Skips variance normalization, less robust for complex data|Large-scale models where variance normalization isn’t crucial|


## BatchNorm


$$
\hat{x}_i = \frac{x_i - \mu_B}{\sqrt{\sigma_B^2 + \epsilon}}
$$
$$
y_i = \gamma \hat{x}_i + \beta
$$





## Group Normalization

$$
\hat{x}_i = \frac{x_i - \mu_G}{\sqrt{\sigma_G^2 + \epsilon}}
$$

$$
y_i = \gamma \hat{x}_i + \beta
$$
##  Weight Normalization


$$
w = \frac{g}{\|v\|} v
$$


## LayerNorm

$$
\hat{x}_i = \frac{x_i - \mu_L}{\sqrt{\sigma_L^2 + \epsilon}}
$$

$$
y_i = \gamma \hat{x}_i + \beta
$$

## RMSNorm

$$
% RMS Normalization
% Root Mean Square:
\text{RMS}(x) = \sqrt{\frac{1}{N} \sum_{i=1}^N x_i^2}
$$

$$
% Normalization step:
\hat{x}_i = \frac{x_i}{\text{RMS}(x) + \epsilon}
$$

$$
% Output with learnable parameters:
y_i = \gamma \hat{x}_i + \beta
$$
## InstanceNorm

$$
\hat{x}_i = \frac{x_i - \mu_I}{\sqrt{\sigma_I^2 + \epsilon}}
$$
$$
y_i = \gamma \hat{x}_i + \beta
$$


## QKNorm
- [ ] [\[2010.04245\] Query-Key Normalization for Transformers](https://arxiv.org/abs/2010.04245)