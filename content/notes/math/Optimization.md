---
time_modified: 2024-10-03T21:05:16-04:00
time_created: 2024-08-23T21:53:43-04:00
---

#optim 



## Optimizers

### SGD + Momentum

### Adam

#### AdamW


### LAMB


### Lion

- [automl/lion at master · google/automl · GitHub](https://github.com/google/automl/tree/master/lion)
- [GitHub - lucidrains/lion-pytorch: 🦁 Lion, new optimizer discovered by Google Brain using genetic algorithms that is purportedly better than Adam(w), in Pytorch](https://github.com/lucidrains/lion-pytorch)
	- [[WIP] Testing the lion optimizer by mitchellnw · Pull Request #432 · mlfoundations/open_clip · GitHub](https://github.com/mlfoundations/open_clip/pull/432)
	- [discuss whether it worked or didn't work · lucidrains/lion-pytorch · Discussion #1 · GitHub](https://github.com/lucidrains/lion-pytorch/discussions/1)
- [Lion 8 bit by lucidrains · Pull Request #188 · TimDettmers/bitsandbytes · GitHub](https://github.com/TimDettmers/bitsandbytes/pull/188)






## Warmup


## Schedules

## Regularization

### Weight Decay

### Gradient Clipping


## Batch Size vs Learning Rate


## Distributed
[distributed\_shampoo](https://github.com/facebookresearch/optimizers/tree/main/distributed_shampoo)




- [ ] [GitHub - nikhilvyas/SOAP](https://github.com/nikhilvyas/SOAP)
- [ ] [\[2409.03137\] The AdEMAMix Optimizer: Better, Faster, Older](https://arxiv.org/abs/2409.03137)

## Hyperparameter Optimization

- [Optuna: A hyperparameter optimization framework](https://github.com/optuna/optuna)
- [Tune: Scalable Hyperparameter Tuning — Ray 1.13.0](https://docs.ray.io/en/latest/tune/index.html)
- [GitHub - facebookresearch/nevergrad: A Python toolbox for performing gradient-free optimization](https://github.com/facebookresearch/nevergrad)
- [GitHub - Facebook/Ax: Adaptive Experimentation Platform](https://github.com/facebook/Ax)
- [GitHub - pytorch/botorch: Bayesian optimization in PyTorch](https://github.com/pytorch/botorch)
- [GitHub - google/vizier: Python-based research interface for blackbox and hyperparameter optimization, based on the internal Google Vizier Service.](https://github.com/google/vizier)

## muP

[x.com](https://x.com/AiEleuther/status/1838209774002864330)

- [ ] [The Practitioner's Guide to the Maximal Update Parameterization | EleutherAI Blog](https://blog.eleuther.ai/mutransfer/)



### Evolutionary

[EvoTorch](https://github.com/nnaisense/evotorch)

## Tips


> 1. For small batch sizes - AdamW with small decay
> 2. Large batch sizes (say 1000s) - LAMB. LAMB is ~ AdamW + warmup + cosine decay rolled into one and all you need to decide on is a learning rate (3e-4 :)

https://twitter.com/sgondala2/status/1555677621748346880


> LR warmup was one of the things looked at in https://arxiv.org/abs/2110.04369, the idea being it helps you use a **higher peak LR** which lets you overall train faster. so when ablating I'd also try adding a warmup and also increasing your max LR

https://twitter.com/zacharynado/status/1555920966982803457

> ...I have done extensive experiments of schedules like cos vs linear vs staircase etc decays. If each one is tuned correctly, they always end up giving the same results. So I think it's not worth spending time on that.

https://twitter.com/giffmana/status/1555818856756793344

> Just in case: **warm-up** seems to typically **not be needed at small batch or with small models**, so you may not notice its effect in "mini" experiments.

https://twitter.com/giffmana/status/1555819323586928640


> I think it's (warmup) mostly to do with the starting beta's of Adam being poorly chosen. The linear warmup gives the exponential moving averages some time to get the correct values before learning starts in earnest.

https://twitter.com/pbloemesquire/status/1555834823578632195

> My experience, gained from fine tuning with small data, is that lr schedule dramatically impacts the end result accuracy.  And yes, some form of warmup helps a lot.

https://twitter.com/JFPuget/status/1555836240968093696


> Also, gradient clipping hard clip by value at +-3 to 5 is very useful. **I'm generally a fan of aggressive learning rates / schedules + aggressive clipping settings**, with some long decay schedules and adaptive gradient methods (e.g. Adam family) for my model training.

https://twitter.com/kastnerkyle/status/1555565583294496769