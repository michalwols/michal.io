---
time_modified: 2024-10-11T11:36:11-04:00
time_created: 2023-12-09T00:06:17-05:00
---
- [ ] [A Mathematical Framework for Transformer Circuits](https://transformer-circuits.pub/2021/framework/index.html)
- [ ] [Fact Finding: Attempting to Reverse-Engineer Factual Recall on the Neuron Level (Post 1) — AI Alignment Forum](https://www.alignmentforum.org/posts/iGuwZTHWb6DFY3sKB/fact-finding-attempting-to-reverse-engineer-factual-recall)
- [ ] [An Extremely Opinionated Annotated List of My Favourite Mechanistic Interpretability Papers v2 — AI Alignment Forum](https://www.alignmentforum.org/posts/NfFST5Mio7BCAQHPA/an-extremely-opinionated-annotated-list-of-my-favourite)
- [ ] [Toy Models of Superposition](https://transformer-circuits.pub/2022/toy_model/index.html)
- [ ] [Towards Monosemanticity: Decomposing Language Models With Dictionary Learning](https://transformer-circuits.pub/2023/monosemantic-features)
- [ ] [Softmax Linear Units](https://transformer-circuits.pub/2022/solu/index.html)
- [ ] [Concrete Steps to Get Started in Transformer Mechanistic Interpretability — Neel Nanda](https://www.neelnanda.io/mechanistic-interpretability/getting-started)
- [ ] Amazing series from 3Blue1Brown:
	- [ ] [How large language models work, a visual intro to transformers | Chapter 5, Deep Learning - YouTube](https://www.youtube.com/watch?v=wjZofJX0v4M)
	- [ ] [[Attention in transformers, visually explained | Chapter 6, Deep Learning - YouTube](https://www.youtube.com/watch?v=eMlx5fFNoYc)](https://www.youtube.com/watch?v=9-Jl0dxWQs8)
	- [ ] [How might LLMs store facts | Chapter 7, Deep Learning - YouTube](https://www.youtube.com/watch?v=9-Jl0dxWQs8)
- [ ] Neel Nanda Transformer Series
	- [ ] [What is a Transformer? (Transformer Walkthrough Part 1/2) - YouTube](https://youtu.be/bOYE6E8JrtU?si=5JboYdaRBEQ4kRD0)
	- [ ] [Implementing GPT-2 From Scratch (Transformer Walkthrough Part 2/2) - YouTube](https://youtu.be/dsjUDacBw8o?si=mYdUuzZ_RdLKu_gs)
	- [ ] [A Walkthrough of A Mathematical Framework for Transformer Circuits - YouTube](https://youtu.be/KV5gbOmHbjU?si=KHB4B7PyQdjYR-Kt)


## Encoder-Decoder


T5

## Decoder

GPT

[Why decoder only beats encoder-decoder (Stanford CS25: V4 I Hyung Won Chung of OpenAI - YouTube)](https://youtu.be/orDKvo8h71o?si=Y4FQIbZEcnJCFkYr&t=1615): 

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


---

# Transformers and LLMs (Large Language Models) 

#ml/nlp/llm


## Components 

### Tokenization
- [GitHub - SumanthRH/tokenization: A comprehensive deep dive into the world of tokens](https://github.com/SumanthRH/tokenization/)
- [GitHub - openai/tiktoken: tiktoken is a fast BPE tokeniser for use with OpenAI's models.](https://github.com/openai/tiktoken)

### Positional Encoding

### RoPE
- [ ] [Rotary Embeddings: A Relative Revolution | EleutherAI Blog](https://blog.eleuther.ai/rotary-embeddings/)
- [ ] [\[2410.06205\] Round and Round We Go! What makes Rotary Positional Encodings useful?](https://arxiv.org/abs/2410.06205)

### Embedding Tables

### Attention

#### Flash Attention

#### Grouped Query Attention

#### Flex Attention
### Normalization

#### RMS Norm


#### Why not BatchNorm

Can't use batchnorm in causal models because it leads to information leakage (since it uses batch level statistics)

### Residual


### Feed Forward


### Activation Functions


### Classifier


### MoE - Mixture of Experts

## Tricks

### Speculative Decoding

### KV Cache


### Context Length




---
# Other


- [LLM Worksheet - Google Sheets](https://docs.google.com/spreadsheets/d/1kT4or6b0Fedd-W_jMwYpb63e1ZR3aePczz3zlbJW-Y4/edit#gid=741531996)

- [GitHub - lm-sys/FastChat: The release repo for "Vicuna: An Open Chatbot Impressing GPT-4"](https://github.com/lm-sys/FastChat)
- [GitHub - kernelmachine/cbtm: Code repository for the c-BTM paper](https://github.com/kernelmachine/cbtm)
- 



## Chat

- [GitHub - imoneoi/openchat: OpenChat: Advancing Open-source Language Models with Imperfect Data](https://github.com/imoneoi/openchat)
- [LangChain](https://blog.langchain.dev/)


## Alignment


### Instruction Tuning

- [GitHub - huggingface/alignment-handbook: Robust recipes for to align language models with human and AI preferences](https://github.com/huggingface/alignment-handbook)
- [GitHub - allenai/open-instruct](https://github.com/allenai/open-instruct)

### RLHF
- [Fine-tuning 20B LLMs with RLHF on a 24GB consumer GPU](https://huggingface.co/blog/trl-peft)
- [Illustrating Reinforcement Learning from Human Feedback (RLHF)](https://huggingface.co/blog/rlhf)

- [[29 Nov 2023] RLHF Lecture @ Stanford - Google Slides](https://docs.google.com/presentation/d/1T6X8ZlwrBek14wGfKljLxikwkTBDdM88r0AZ6NiodU4/edit#slide=id.g2a01be3ce56_1_345)
### DPO
- [[2305.18290] Direct Preference Optimization: Your Language Model is Secretly a Reward Model](https://arxiv.org/abs/2305.18290)
- [RLHF progress: Scaling DPO to 70B, DPO vs PPO update, Tülu 2, Zephyr-β, meaningful evaluation, data contamination](https://www.interconnects.ai/p/rlhf-progress-scaling-dpo-to-70b)

- [Fine-tune a Mistral-7b model with DPO.ipynb](https://colab.research.google.com/drive/15iFBr1xWgztXvhrj5I9fBv20c7CFOPBE?usp=sharing#scrollTo=YpdkZsMNylvp)
- [GitHub - eric-mitchell/direct-preference-optimization: Reference implementation for DPO (Direct Preference Optimization)](https://github.com/eric-mitchell/direct-preference-optimization)
- [Fine-tune Llama 2 with DPO](https://huggingface.co/blog/dpo-trl)
- [RLHF and DPO compared: user feedback methods for LLM optimization | by Automata | 𝐀𝐈 𝐦𝐨𝐧𝐤𝐬.𝐢𝐨 | Oct, 2023 | Medium](https://medium.com/aimonks/rlhf-and-dpo-compared-user-feedback-methods-for-llm-optimization-44f4234ae689)

## Training

- [The Novice's LLM Training Guide](https://rentry.org/llm-training)

- [[2310.18313] FP8-LM: Training FP8 Large Language Models](https://arxiv.org/abs/2310.18313)

### Fine Tuning 

- [GitHub - OpenAccess-AI-Collective/axolotl: Go ahead and axolotl questions](https://github.com/OpenAccess-AI-Collective/axolotl)
- [GitHub - unslothai/unsloth: Finetune Llama 3.1, Mistral, Phi & Gemma LLMs 2-5x faster with 80% less memory](https://github.com/unslothai/unsloth)


### Distillation / Pruning / Compression

- [\[2407.14679\] Compact Language Models via Pruning and Knowledge Distillation](https://arxiv.org/abs/2407.14679)

## Inference


### GGML / LLAMA.CPP

[Introduction to ggml](https://huggingface.co/blog/introduction-to-ggml)

## Open Models

- [Mistral NeMo | Mistral AI | Frontier AI in your hands](https://mistral.ai/news/mistral-nemo/)

## Serving

- [Hamel’s Blog - Optimizing latency](https://hamel.dev/notes/llm/inference/03_inference.html)

### Quantization
- [GitHub - PanQiWei/AutoGPTQ: An easy-to-use LLMs quantization package with user-friendly apis, based on GPTQ algorithm.](https://github.com/PanQiWei/AutoGPTQ)
- [GitHub - IST-DASLab/gptq: Code for the ICLR 2023 paper "GPTQ: Accurate Post-training Quantization of Generative Pretrained Transformers".](https://github.com/IST-DASLab/gptq)

## Tutorials

- [GitHub - RahulSChand/llama2.c-for-dummies: Step by step explanation/tutorial of llama2.c](https://github.com/RahulSChand/llama2.c-for-dummies)

### Visualization

- [LLM Visualization](https://bbycroft.net/llm)



### Decoding

- [X](https://twitter.com/hongyangzh/status/1733169111625064833)


## Inference Benchmarks

- [Performance of llama.cpp on Apple Silicon · ggerganov/llama.cpp · Discussion #4167 · GitHub](https://github.com/ggerganov/llama.cpp/discussions/4167)


## Evaluation

[Evaluate LLMs and RAG a practical example using Langchain and Hugging Face](https://www.philschmid.de/evaluate-llm)

## Applications

### Text to SQL
- [GitHub - defog-ai/sqlcoder: SoTA LLM for converting natural language questions to SQL queries](https://github.com/defog-ai/sqlcoder)


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