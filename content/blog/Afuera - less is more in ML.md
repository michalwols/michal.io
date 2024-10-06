---
time_modified: 2024-10-06T10:58:17-04:00
time_created: 2024-10-05T14:00:37-04:00
draft: true
---

https://media.tenor.com/cmh1OvY7i-cAAAAM/javier-milei-afuera.gif

[\[2409.15156\] Rethinking Conventional Wisdom in Machine Learning: From Generalization to Scaling](https://arxiv.org/abs/2409.15156)


Or breaking down the ML administrative state


- [ ] Spacial priors
- [ ] Normalization
- [ ] Precision and bits
- [ ] Softmax normalization
- [ ] Breaking large operations
	- [ ] MoE
- [ ] Recurrence
- [ ] Probabilities
- [ ] Sigmoid over softmax
- [ ] Optimizer states
- [ ] Sparse updates
- [ ] Lora 
- [ ] Shifts and adds over multiplies
- [ ] Reduce synchronization 
- [ ] Grouped attention
- [ ] Large intermediates
- [ ] Encoder
- [ ] Drop the dropout, with large dataset and less epochs
	- [ ] [x.com](https://x.com/yaroslavvb/status/1842931176316739708)
	- [ ] 

# ideas
- [ ]  N to 1 attention heads, to get rid of distributed representations
- [ ] Capped activation functions to get rid of normalization layers 
- [ ] Replace FFN with lookup tables
- [ ] Recurrence or diffusion over long tape
- [ ] Intermediate level tokens aggregating to reduce input sizes
- [ ] Early causal conv to pool near by context
- [ ] Fast and slow memory
- [ ] Ligits only
- [ ] Factor FFN
- [ ] Get rid tokenizers,
	- [ ] Characters pooled with convolutions
	- [ ] Output tokens
- [ ] drop requirement for large datasets, distill multiple teachers on synthetic data