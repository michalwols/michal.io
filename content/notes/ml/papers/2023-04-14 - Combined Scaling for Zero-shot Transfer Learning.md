
#clip #ml/contrastive

[[2111.10050] Combined Scaling for Zero-shot Transfer Learning](https://arxiv.org/abs/2111.10050)

Intorduces a new combined scaling method called "BASIC"

- scales up contrastive image-text models to larger model, data and batch size
- achieves 85.7% top-1 accuracy on the ImageNet
- beats CLIP by 9%
- 6.6B image-text pair noisy dataset (JFT Dataset)
- uses gradient accumulation and checkpointing to expand the batch size to 2^20
	- accumulates gradient for contrastive matrix
	- recomputes features in backprop to save having to store the gradients (gradient checkpointing)
		- rematerialize activations and normalization layers since they are cheap to compute but use a lot of memory for gradients
- Use "AdaFactorW" optimizer (AdamW + AdaFactor)B