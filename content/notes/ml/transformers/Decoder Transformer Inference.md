- [ ] [Transformer Inference Arithmetic | kipply's blog](https://kipp.ly/transformer-inference-arithmetic/)


Prefill vs generation, compute bound vs memory bound

## KV Cache

### Grouped Query Attention

Less Keys and Values, to reduce Key Value Cache

### Paged Attention
- [ ] [Fast LLM Serving with vLLM and PagedAttention - YouTube](https://www.youtube.com/watch?v=5ZlavKF_98U)

Avoid padding out samples with fixed size blocks, use proper paging, split up samples across smaller pages


### Sliding Window Attention => Rolling Buffer KV Cache
- [ ] [Exploring the Latency/Throughput & Cost Space for LLM Inference // Timothée Lacroix // CTO Mistral - YouTube](https://www.youtube.com/watch?v=mYRqvB1_gRk)


## Speculative Decoding



## Prefix Caching


## Continuous Batching

- [ ] [Accelerating LLM Inference with vLLM - YouTube](https://www.youtube.com/watch?v=qBFENFjKE-M)



## Flash Attention


## Mixture of Experts
Reduce compute, skipping experts

## Quantization




## Structured Decoding / Generation

