---
time_modified: 2024-10-01T22:49:57-04:00
time_created: 2023-12-09T00:06:17-05:00
---

## Encoder-Decoder

T5

## Decoder

GPT

[Why decoder only beats encoder-decoder](https://youtu.be/orDKvo8h71o?si=Y4FQIbZEcnJCFkYr&t=1615): 

|                                       | Encoder-decoder                                    | Decoder-only                                   |
| ------------------------------------- | -------------------------------------------------- | ---------------------------------------------- |
| **Additional cross attention**        | Separate cross attention                           | Self-attention serving both roles              |
| **Parameter sharing**                 | Separate parameters for input and target           | Shared parameters                              |
| **Target-to-input attention pattern** | Only attends to the last layer of encoder's output | Within-layer (i.e. layer 1 attends to layer 1) |
| **Input attention**                   | Bidirectional                                      | Unidirectional*                                |


1. In generative applications causal attention allows us to cache previous steps since tokens only attend up to their step (KV Cache)
	1. With encoder models need to recompute full sequence at each step to update previous tokens


![[Pasted image 20240925222505.png]]
> from [Stanford CS 25 - Google Slides](https://docs.google.com/presentation/d/1u05yQQaw4QXLVYGLI6o3YoFHv6eC3YN8GvWD8JMumpE/edit#slide=id.g26e4534ad50_0_547)



### Decoder Improvements


1. pre norm (norm before attention)
2. RMS norm - cheaper
3. RoPE position embeddings
4. Grouped Query Attention - Smaller KV cache
5. Mixture of Experts - More Parameters with less Flops
6. SwiGLU / other GLU variants


![[Pasted image 20240925224133.png]]




## Encoder

BERT
ViT (MAE)



## Links


### Articles

- [Transformer Math 101 | EleutherAI Blog](https://blog.eleuther.ai/transformer-math/)

- [The Annotated Transformer (2022 - Rush)](http://nlp.seas.harvard.edu/annotated-transformer/)
- [The Illustrated Transformer (Alammar)](http://jalammar.github.io/illustrated-transformer/)
- [Transformers From Scratch (2019 - Bloem)](https://peterbloem.nl/blog/transformers)
- [Transformer Walkthrough: A walkthrough of transformer architecture code (2022 - Riedl)](https://github.com/markriedl/transformer-walkthrough)

- https://github.com/cmhungsteve/Awesome-Transformer-Attention

- [Transformer models: an introduction and catalog — 2023 Edition - AI, software, tech, and people, not in that order… by X](https://amatriain.net/blog/transformer-models-an-introduction-and-catalog-2d1e9039f376/)


### Lectures


- [Stanford CS25: Transformers United (2021)](https://www.youtube.com/playlist?list=PLoROMvodv4rNiJRchCzutFw5ItR_Z27CM)
- [Lecture 20 - Transformers and Attention - YouTube](https://www.youtube.com/watch?v=IFKRf-BAqZo)


### Code

- [xformers: Hackable and optimized Transformers building blocks, supporting a composable construction.](https://github.com/facebookresearch/xformers)
- [GitHub - lucidrains/x-transformers: A simple but complete full-attention transformer with a set of promising experimental features from various papers](https://github.com/lucidrains/x-transformers)
- [GitHub - explosion/curated-transformers: 🤖 A PyTorch library of curated Transformer models and their composable components](https://github.com/explosion/curated-transformers)