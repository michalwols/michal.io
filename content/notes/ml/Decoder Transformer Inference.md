---
time_modified: 2024-10-03T23:01:53-04:00
time_created: 2024-09-25T21:08:25-04:00
---
#inference #llm 


- [ ] [Transformer Inference Arithmetic | kipply's blog](https://kipp.ly/transformer-inference-arithmetic/)

![[Pasted image 20241003215519.png]]



Prefill vs generation, compute bound vs memory bound


## Chunked Prefill (for batched inference)

Split up the prefill compute into chunks to reduce the units of work so that large prefills do not interfere with other request doing generation in the same batch

![[Pasted image 20241003220522.png]]

- [ ] [\[2403.02310\] Taming Throughput-Latency Tradeoff in LLM Inference with Sarathi-Serve](https://arxiv.org/abs/2403.02310)

## KV Cache

### Grouped Query Attention

Less Keys and Values, to reduce Key Value Cache

### Paged Attention
- [ ] [Fast LLM Serving with vLLM and PagedAttention - YouTube](https://www.youtube.com/watch?v=5ZlavKF_98U)

Avoid padding out samples with fixed size blocks, use proper paging, split up samples across smaller pages

### Sliding Window Attention => Rolling Buffer KV Cache
- [ ] [Exploring the Latency/Throughput & Cost Space for LLM Inference // Timothée Lacroix // CTO Mistral - YouTube](https://www.youtube.com/watch?v=mYRqvB1_gRk)


### Cross Layer KV Cache Sharing

- [ ] [\[2405.12981\] Reducing Transformer Key-Value Cache Size with Cross-Layer Attention](https://arxiv.org/abs/2405.12981)
![[Pasted image 20241003225937.png]]
[\[2405.05254\] You Only Cache Once: Decoder-Decoder Architectures for Language Models](https://arxiv.org/abs/2405.05254)


### StreamingLLM

See [[Long Context Transformers]]


### Prompt / Prefix Caching

Cache KV cache for common prefixes


### Low Precision and Compression

Use bf16, float8, int8 or smaller dtypes like int4 to save memory


## Speculative Decoding



## Prefix Caching


## Continuous Batching / Inflight Batching

- [ ] [Accelerating LLM Inference with vLLM - YouTube](https://www.youtube.com/watch?v=qBFENFjKE-M)

![[Pasted image 20241003220433.png]]



## Flash Attention


## Mixture of Experts
Reduce compute, skipping experts

## Quantization




## Structured Decoding / Generation


## LLM Routing
Predict best (speed / cost / expert) model for given request and route based on that

## Metrics

### Time to First Token

### Inter Token Latency


---
## Links
- [ ] [Understanding the LLM Inference Workload - Mark Moyou, NVIDIA - YouTube](https://www.youtube.com/watch?v=z2M8gKGYws4)
- [ ] [Mastering LLM Techniques: Inference Optimization | NVIDIA Technical Blog](https://developer.nvidia.com/blog/mastering-llm-techniques-inference-optimization/)
- [ ] [Optimizing AI Inference at Character.AI](https://research.character.ai/optimizing-inference/)