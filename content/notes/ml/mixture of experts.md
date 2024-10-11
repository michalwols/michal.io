---
time_modified: 2024-10-11T11:36:22-04:00
time_created: 2024-04-21T18:58:55-04:00
---

#moe

## TLDR
1. Better models for less compute (larger capacity models under same compute budget)
2. Best for batched inference (server or offline)1
3. Balanced Routing is important, otherwise get stragglers, memory balance issues and dead experts
4. Most models use MoE layers in FFNs (token level feed forward networks)


- [ ] [Mixture of Experts Explained](https://huggingface.co/blog/moe)
- [ ] [\[M2L 2024\] Mixture of Experts - Diego de Las Casas (Mistral AI)- YouTube](https://youtu.be/ayguaRDBkgQ?si=ZO9dUXX24xjOef58) - Great lecture from Mistal team, goes into details, most of the notes here are from that talk

## Routing

### Problem: Load Balancing

If the token assignments are not balanced across experts you end up with **stragglers** and **out of memory** issues as some experts hold and process way more inputs than others.

**Dead Experts** will not get gradients and will stop getting routed to

#### Auxiliary Load Balancing Loss

Penalize routing function for producing imbalanced weights

![[Screenshot 2024-10-09 at 10.06.13 AM.png]]

#### Capped Expert Capacity

Set a max capacity for each expert **C**,  any inputs to the expert below **C** get dropped or assigned to a different expert.

Thanks to **residual connections** the dropped inputs are not completely dropped from the network
![[Screenshot 2024-10-09 at 10.11.39 AM.png]]

**NOTE: Expert Capacity leaks information in causal models since it uses batch level statistics**

![[Pasted image 20241009110800.png]]
### Token Choice

Each token sent to K experts

### Expert Choice

Each expert picks N tokens

**leaks information for decoder models**


## Gating

![[Screenshot 2024-10-09 at 9.37.12 AM.png]]


Layer wise 

```
sum(gate_i(x) * expert_i(x))
```

### Noisy Top-K Gating

No longer used in practice

```
gate(x) = softmax(keep_top_k(H(x), k))
H(x)_i = (x * W_g)_i + StandardNormal() * softplus((x * W_noise)_i)


# keep_top_k  set all values except top k to -inf (masking for softmax)
# StandardNormal() * softplus((x * W_noise)_i) randomizes the gating
```


### Top-K Gating

```
gate(x) = softmax(keep_top_k(H(x), k))
H(x)_i = (x * W_g)_i


# keep_top_k  set all values except top k to 0
```


## Distributed Setting


### Expert Parallelism (EP)
![[Screenshot 2024-10-09 at 9.40.40 AM.png]]

puts experts on different GPUs and sends routed tokens to the GPU that the expert is on

Can be combined with **Data Parallelism**, by replicating non expert layers on all devices and keeping experts split up:

![[Screenshot 2024-10-09 at 9.43.40 AM.png]]


## Inference

**Decouples processing speed from parameter count** - allows us to use really large capacity models without having to do as much compute at inference time

Adds some overhead vs dense model of the same size due to communication (about 20% slower)

Reduces compute to memory ratio (less compute with same amount of memory compared to dense models), meaning it's more likely to be memory bound than dense models.

Need **large batch size** at inference to balance compute and memory

**More efficient for batch processing and other compute intense tasks like prefill, speculative decoding**

Larger KV Cache since more FFN parameters

## Training

**Tend to perform better for the same training budget**

Number of experts tends to increase quality (8-64 tends to be the best tradeoff)


## Tweaks
### Mixture of Depth

use expert routing and only update the top K tokens (forwarding the remaining tokens). use routing weight to modulate outputs of the tokens (to make it differentiable)

### Granularity
[\[2402.07871\] Scaling Laws for Fine-Grained Mixture of Experts](https://arxiv.org/abs/2402.07871)

### Shared Experts

Have a few experts that process all tokens, allowing the routed ones to specialize more

### Batch Prioritized Routing

Drop tokens with small gating weights

![[Pasted image 20241009200653.png]]

## MoE LLMs / Transformers


### FFN MoE

Usually MoE layer for feed forward module.


#### GShard

#### [Mixtral 8x7B](https://youtu.be/ayguaRDBkgQ?si=XVXew1-ZxUyW0rSU&t=1228)

Replaced FFN layers with MoEs, 8 experts, with 2 tokens routed to each expert. Leads to ~14B active parameters per token

#### Deepseek v2
#### [OLMoE](https://arxiv.org/abs/2409.02060)

### Attention MoE

Not usually done with Attention layers because attention requires access to all tokens.

**Mixture-of-Attention** - routes queries
**Switch Transformer** - successor to GShard, but claims attention MoE was too unstable
**SwitchHead**  - routes values


## MoEs in Vision


### Sparse MoE

### Soft MoE



- [ ] [GitHub - databricks/megablocks](https://github.com/databricks/megablocks)
- [ ] [Training MoEs at Scale with PyTorch - Mihir Patel & Brian Chu, Databricks - YouTube](https://www.youtube.com/watch?v=1c56wxv00hI)
- [ ] [\[2407.06204\] A Survey on Mixture of Experts](https://arxiv.org/abs/2407.06204)