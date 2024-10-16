---
time_modified: 2024-10-15T12:16:24-04:00
time_created: 2024-09-04T21:03:20-04:00
---
# TLDR
 - [ ] want large models, large batch sizes and fast training, need to distribute data, model and optimizer state across device / nodes
 - [ ] Communication overhead and pipeline bubbles become an issue

See [ml-engineering/training/model-parallelism](https://github.com/stas00/ml-engineering/tree/master/training/model-parallelism) for a more detailed breakdown

# Parallelism Types
## Data Parallel

Replicate Model on each device, split batch into sub batches for each device, synchronize at each step.\

Works great for smaller models that fit on a single device (ex: Vision Models)

## Model Parallel

### Tensor Parallel

Split Tensors into chunks


![[Pasted image 20241015121402.png]]

### Pipeline Parallelism

Split model by layer, with each device holding a set of consecutive layers.

Naive pipeline parallelism leads to bubbles so batches are split into microbatches so that all devices can do processing in parallel on the sub batches.

![[Pasted image 20241015101045.png]]

- [ ] [Introducing GPipe, an Open Source Library for Efficiently Training Large-scale N](https://research.google/blog/introducing-gpipe-an-open-source-library-for-efficiently-training-large-scale-neural-network-models/)
## Sequence Parallelism

For sequence models split the sequence and process subsequences on different devices

- [ ] [\[2310.01889\] Ring Attention with Blockwise Transformers for Near-Infinite Context](https://arxiv.org/abs/2310.01889)

## Expert Parallelism for MoEs

Put a subset of experts on different devices, see [[Mixture of Experts#Expert Parallelism (EP)]]


## Combinations

###  3D Parallelism (Data, Pipeline and Tensor)

![[Pasted image 20241015101516.png]]

# Saving Memory

## Activation Checkpointing

## Gradient Accumulation

## CPU Offloading

## Quantization, Compression and Mixed Precision

## Optimizers

### 1 Bit Adam



# Communication 

![[Pasted image 20241015101932.png]]

## Primitives

- [ ] [Point-to-point communication — NCCL 2.23.4 documentation](https://docs.nvidia.com/deeplearning/nccl/user-guide/docs/usage/p2p.html#)
- [ ] [Collective Operations — NCCL 2.23.4 documentation](https://docs.nvidia.com/deeplearning/nccl/user-guide/docs/usage/collectives.html)

### AllReduce

all-gather, all-reduce, broadcast, reduce, reduce-scatter as well as point-to-point send and receive



## Libraries / Backends
- [ ] [Communication Backends, Raw performance benchmarking · MLBench](https://mlbench.github.io/2020/09/08/communication-backend-comparison/)

### NCCL
- [ ] [NVIDIA Collective Communication Library (NCCL) Documentation — NCCL 2.23.4 documentation](https://docs.nvidia.com/deeplearning/nccl/user-guide/docs/index.html)

### MPI

### Gloo

## Networking

### NVlink 

### InfiniBand

# Fault Tolerance


# Distributed Training Frameworks

## Torch FSDP (Fully Sharded Data Parallel) and FSDP2

- [ ] [\[2304.11277\] PyTorch FSDP: Experiences on Scaling Fully Sharded Data Parallel](https://arxiv.org/abs/2304.11277)
- [ ] [How Fully Sharded Data Parallel (FSDP) works? - YouTube](https://www.youtube.com/watch?v=By_O0k102PY)
- [ ] [Lecture 12 (Part2): Maximize GPU Utilization - YouTube](https://www.youtube.com/watch?v=v1ekwGFksrY)
- [ ] [torchtitan/docs/fsdp.md at main · pytorch/torchtitan · GitHub](https://github.com/pytorch/torchtitan/blob/main/docs/fsdp.md)
![[Pasted image 20241015101855.png]]


![[Pasted image 20241004082004.png]]



### Device Mesh


![[Pasted image 20241004081840.png]]

## DeepSpeed
- [ ] [Training Overview and Features - DeepSpeed](https://www.deepspeed.ai/training/#features)
- [ ] [Latest News - DeepSpeed](https://www.deepspeed.ai/)
- [ ] [Stanford CS25: V4 I From Large Language Models to Large Multimodal Models - YouTube](https://youtu.be/cYfKQ6YG9Qo?si=mudhUXf-SR4q-ef_&t=1074)
- [ ] [DeepSpeed: Extreme-scale model training for everyone - Microsoft Research](https://www.microsoft.com/en-us/research/blog/deepspeed-extreme-scale-model-training-for-everyone/)
- [ ] [Search - Microsoft Research](https://www.microsoft.com/en-us/research/search/?q=deepspeed)

### ZeRO1

### ZeRO2

### ZeRO3


1. Most memory taken up by optimizer states (adam moments need to be stored in full precision)


### ZeRO++
- [ ] [\[2306.10209\] ZeRO++: Extremely Efficient Collective Communication for Giant Model Training](https://arxiv.org/abs/2306.10209)

## Megatron

## FairScale


## Ray Train


## TorchTitan
- [ ] [\[2410.06511v1\] TorchTitan: One-stop PyTorch native solution for production ready LLM pre-training](https://arxiv.org/abs/2410.06511v1)


# Decentralized Multi Datacenter / Federated Training / Asynchronous Training

- [ ] [INTELLECT–1: Launching the First Decentralized Training of a 10B Parameter Model](https://www.primeintellect.ai/blog/intellect-1)
- [ ] [Multi-Datacenter Training: OpenAI's Ambitious Plan To Beat Google's Infrastructure](https://www.semianalysis.com/p/multi-datacenter-training-openais?%2F=)
- [ ] [Arthur Douillard on X: "@dylan522p You may want to read into the latest advance of dist/fed learning for LLMs, e.g. DiLoCo, OpenDiLoCo, Flower. You could summarize those as the Branch-Train-Merge you mention, but on steroids. https://t.co/MrRrIOkj8A" / X](https://x.com/Ar_Douillard/status/1831307367171952838)
- [ ] [Decentralized Training of Deep Learning Models](https://vaibhawvipul.github.io/2024/10/15/Decentralized-Training-of-Deep-Learning-Models.html)
- [ ] [GitHub - PrimeIntellect-ai/prime: prime (previously called ZeroBand) is a framework for efficient, globally distributed training of AI models over the internet.](https://github.com/PrimeIntellect-ai/Prime)


#### Async SGD




# Links
- [ ] [Distributed Training Of Deep Learning Models : Part \~ 1](https://vaibhawvipul.github.io/2024/09/29/Distributed-Training-of-Deep-Learning-models-Part-~-1.html) #distributed
- [ ] [How to train a model on 10k H100 GPUs?](https://soumith.ch/blog/2024-10-02-training-10k-scale.md.html) #distributed 
- [ ] [Self contained example of how pipeline parallel works (AFAB and 1F1B) in 200 LOC · GitHub](https://gist.github.com/3outeille/a3d4d91bb07af64c8f33d5aaee5145fe)
- [ ] [ml-engineering/training/model-parallelism at master · stas00/ml-engineering · GitHub](https://github.com/stas00/ml-engineering/tree/master/training/model-parallelism)



- [ ] [Slaying OOMs with PyTorch FSDP and torchao - YouTube](https://www.youtube.com/watch?v=UvRl4ansfCg)
- [ ] [LLM-Training-Puzzles/Distributed.ipynb at main · srush/LLM-Training-Puzzles · GitHub](https://github.com/srush/LLM-Training-Puzzles/blob/main/Distributed.ipynb)


- [ ] DeepSpeed
- [ ] Torch FSDP
- [ ] [GitHub - pytorch/torchtitan: A native PyTorch Library for large model training](https://github.com/pytorch/torchtitan)
- [ ] Fairscale
- [ ] Megatron

