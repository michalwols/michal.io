---
time_modified: 2024-10-11T13:46:39-04:00
time_created: 2024-10-10T15:06:05-04:00
---

Train small model that can query external sources


```
input query_token query_embeddings query_results_token result_embeddings …
```



Bootstrap from existing LLM, and on device nearest neighbor index (embedding tables only)

Curriculum learning by paging in different partitions of the data and distilling from the large LLM