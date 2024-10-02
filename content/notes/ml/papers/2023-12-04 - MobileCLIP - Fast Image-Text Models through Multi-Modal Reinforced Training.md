#clip #vision-language #mobile

- Dataset Augmentation
	- CoCa for Captions (multiple per image), in addition to source captions
	- Text and Image Embeddings from larger CLIP Models
		- embed multiple augmented versions of the images and synthetic captions
		- use multiple CLIP models in ensemble
		- store augmentation params and use them at train time to reproduce augmented version of image
- Loss
	- CLIP loss + distillation term
	- compute on real and synth data and sum up for final loss
- Models
	- Text-RepMixer
		- ![[Pasted image 20231205123930.png]]
	- Vision - FastViT variant called MCi
		- reduce MLP expansion ratio from 4 to 3, because of "significant amount of redundancy in linear layers", make the model deeper instead
		- **MCi2 matches FastViT on ImageNet (84.5%) while being 15% faster and 14.3% smaller**
- Training
	- 12M
		- 8 A100s
		- 8,192 Batch Size
	- 1B
		- 256 A100s
		- 65,536 Batch Size
	- Dataset Reinforcement
		- 5 synthetic captions per image using the `coca_ViT-L-14` model in OpenCLIP
		- concatenate two CLIP image embeddings (datacomp and openai ViT-L-14)
		- store in Bfloat16
		- use gzipped pickle
	- Strong Augmentation 
- Inference
	- iPhone 12 with CoreML

![[Pasted image 20231205130408.png]]
![[Pasted image 20231205130246.png]]

---

- Ideas
	- Captioning model that takes image and source caption when generating new captions 
		- potentially also use nearest neighbors