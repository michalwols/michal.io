---
time_modified: 2024-10-13T02:32:00-04:00
time_created: 2024-10-09T12:23:13-04:00
---

## Goal
Train a better foundational image backbone 
SSL and CLIP style models don't get sufficient supervision for all downstream tasks

## Idea
Use VLM with a tiny LLM as a decoder to pose all vision related tasks as a multi task learning task, support multi image input. T5 like approach


- [ ] small LLM + large vision backbone
- [ ] multi task across all vision tasks



- [ ] [GitHub - TIGER-AI-Lab/VLM2Vec: This repo contains the code and data for "VLM2Vec: Training Vision-Language Models for Massive Multimodal Embedding Tasks"](https://github.com/TIGER-AI-Lab/VLM2Vec)