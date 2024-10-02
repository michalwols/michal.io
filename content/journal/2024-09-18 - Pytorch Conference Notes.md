#pytorch



## Pytorch Conference
#pytorch
- [ ] [Schedule | LF Events](https://events.linuxfoundation.org/pytorch-conference/program/schedule/)

## [Activation Checkpointing](https://pytorch2024.sched.com/event/1fHmo?iframe=no) (SAC - Selective Activation Checkpointing
\
![[Screenshot 2024-09-19 at 12.23.35 PM.png]]
![[Screenshot 2024-09-19 at 12.22.39 PM.png]]
- **torch.compile automatically does some recomputation** 
- By default, torch.compile will use the min-cut partitioner, which chooses to recompute certain ops with the objective of minimizing number of tensors saved for backward boundary 
- It's primary objective is to reduce runtime however, so it is relatively conservative wrt recomputation, e.g. we only recompute fusible, non-compute intensive ops, and have a heuristic to avoid long fusible chains.

in 2.5 a new checkpoint API will allow setting checkpointing policy
2.4 has a new compile only memory budget API to trade off memory for speed 

```python
torch._dynamo.config.activation_memory_budget = 0.5 
out = torch.compile(fn)(inp)
```


## Timeline of LLMS
[PyTorch Conference 2024: Keynote: Navigating the Architectural Ti...](https://pytorch2024.sched.com/event/1iw0K/keynote-navigating-the-architectural-timeline-of-llms-sebastian-raschka-staff-research-engineer-lightning-ai?iframe=no&w=100%&sidebar=yes&bg=no)


#### Data Quality - Filtering, Curriculum, Synthetic

![[Screenshot 2024-09-19 at 12.32.49 PM.png]]
![[Screenshot 2024-09-19 at 12.34.03 PM.png]]![[Screenshot 2024-09-19 at 12.35.47 PM.png]]![[Screenshot 2024-09-19 at 12.37.05 PM.png]]

### grouped query attention
### larger vocab

### RMS Norm

### RoPE Encoding (relative)

### mixture of experts (ex mixtral)

### Sliding Window Attention
![[Screenshot 2024-09-19 at 12.41.13 PM.png]]


[litgpt/litgpt/model.py at main · Lightning-AI/litgpt · GitHub](https://github.com/Lightning-AI/litgpt/blob/main/litgpt/model.py)


## Better GPU Support in Apache Ray

![[Screenshot 2024-09-19 at 1.14.31 PM.png]]![[Screenshot 2024-09-19 at 1.14.52 PM.png]]