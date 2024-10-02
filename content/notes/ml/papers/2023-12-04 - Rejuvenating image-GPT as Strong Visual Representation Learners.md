#vit #selfsup
by Sucheng Ren1* Zeyu Wang2* Hongru Zhu1 Junfei Xiao1 Alan Yuille1 Cihang Xie2

- D-iGPT
	- predict semantic tokens (CLIP) instead of pixels 
	- predict next token and visible tokens (from pixels)
	- 4 tokens per image (112x112 for 224 images)
	- random permutation of tokens into a sequence (position is encoded)
- 89.5% top 1 on ImageNet with ViT-L
- 86.1% when training on imagenet only
- Training
	- pretraining
		- 300 epochs
		- batch size 4096
		- peak learning rate to lr = 1.5e−4 × batchsize/256
		- 224x224
	- imagenet tunning
		- vit-b
		- linear layer
		- 100 epochs
		- 224x224


---
- Ideas
	- replace transformer with Mamba
	- multi modal 
		- use CLIP text encoders and feed it as starting token or generate them after image tokens (or mix)
		- use text token embeddings or full text embedding

- Questions
	- sounds like mostly just distillation from a strong CLIP model