---
time_modified: 2024-10-01T22:49:57-04:00
time_created: 2024-04-21T18:58:55-04:00
---

- [ ] [Mixture of Experts Explained](https://huggingface.co/blog/moe)

routers

- token
- expert





### Mixture of Depth

use expert routing and only update the top K tokens (forwarding the remaining tokens). use routing weight to modulate outputs of the tokens (to make it differentiable)