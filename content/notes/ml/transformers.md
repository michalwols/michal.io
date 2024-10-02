---
time_modified: 2024-10-01T22:49:57-04:00
time_created: 2024-09-05T00:15:26-04:00
---

# Transformers and LLMs (Large Language Models) and 

#ml/nlp/llm


## Components 

### Tokenization
- [GitHub - SumanthRH/tokenization: A comprehensive deep dive into the world of tokens](https://github.com/SumanthRH/tokenization/)
- [GitHub - openai/tiktoken: tiktoken is a fast BPE tokeniser for use with OpenAI's models.](https://github.com/openai/tiktoken)

### Positional Encoding

### RoPE
- [ ] [Rotary Embeddings: A Relative Revolution | EleutherAI Blog](https://blog.eleuther.ai/rotary-embeddings/)

### Embedding Tables

### Attention

#### Flash Attention

#### Grouped Query Attention

#### Flex Attention
### Normalization

#### RMS Norm

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