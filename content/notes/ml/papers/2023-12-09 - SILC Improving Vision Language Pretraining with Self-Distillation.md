CLIP + DINO

1. Each global view used in Lself−dist needs to be aligned with text, otherwise the two objectives diverge. This is realized by computing the image-text contrastive loss for each global view while maintaining the same batch size. 
2. The momentum scheduler of the EMA should not converge to 1.0. Otherwise the teacher stops learning from image-text loss as the update step becomes too small in the later stage of the training. We therefore use a **fixed momentum**.

- [ ] two global views cropped between (0.4 − 1.0) of the original image area  
- [ ] eight local views cropped between (0.05 − 0.4)





### TODO

Tune from SigLIP

use tokens 