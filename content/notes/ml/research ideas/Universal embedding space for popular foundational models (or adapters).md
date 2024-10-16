---
time_modified: 2024-10-13T02:32:00-04:00
time_created: 2024-10-11T11:34:18-04:00
---

## Goals
- [ ] train adapters to align a bunch of popular foundational models
- [ ] potentially have one universal embedding space and encoders and decoders to project into them

## Pros
- [ ] index in universal embedding space, swap models without having to reindex
- [ ] swap out models based on task (model routing and speculative decoding)
- [ ] task specific model routing for encoders in different modalities (ex: different sized inputs and models for OCR, document, image, segmentation inputs)




Matryoshka based embeddings