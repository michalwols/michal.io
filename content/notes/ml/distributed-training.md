---
time_modified: 2024-10-01T22:49:57-04:00
time_created: 2024-09-04T21:03:20-04:00
---
# Distributed Training

[LLM-Training-Puzzles/Distributed.ipynb at main · srush/LLM-Training-Puzzles · GitHub](https://github.com/srush/LLM-Training-Puzzles/blob/main/Distributed.ipynb)


## Data Parallel


## Model Parallel


### Tensor Parallel

Split Tensors

### Pipeline Parallelism

Split by layer

## Activation Checkpointing


## Gradient Accumulation


## CPU Offloading



- [ ] [How Fully Sharded Data Parallel (FSDP) works? - YouTube](https://www.youtube.com/watch?v=By_O0k102PY)
- [ ] [Lecture 12 (Part2): Maximize GPU Utilization - YouTube](https://www.youtube.com/watch?v=v1ekwGFksrY)
## DeepSpeed
- [ ] [Training Overview and Features - DeepSpeed](https://www.deepspeed.ai/training/#features)

- [ ] [Latest News - DeepSpeed](https://www.deepspeed.ai/)
- [ ] [Stanford CS25: V4 I From Large Language Models to Large Multimodal Models - YouTube](https://youtu.be/cYfKQ6YG9Qo?si=mudhUXf-SR4q-ef_&t=1074)

### ZeRO1

### ZeRO2

### ZeRO3


1. Most memory taken up by optimizer states (adam moments need to be stored in full precision)



## Multi Datacenter / Federated
- [ ] [Multi-Datacenter Training: OpenAI's Ambitious Plan To Beat Google's Infrastructure](https://www.semianalysis.com/p/multi-datacenter-training-openais?%2F=)

- [ ] [Arthur Douillard on X: "@dylan522p You may want to read into the latest advance of dist/fed learning for LLMs, e.g. DiLoCo, OpenDiLoCo, Flower. You could summarize those as the Branch-Train-Merge you mention, but on steroids. https://t.co/MrRrIOkj8A" / X](https://x.com/Ar_Douillard/status/1831307367171952838)