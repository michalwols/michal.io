---
draft: true
time_modified: 2024-10-01T23:54:55-04:00
time_created: 2024-10-01T23:27:14-04:00
---


# An always up to date guide to Image Recognition

## Preprocessing

#### AutoAugment

#### Mixup

##### Manifold Mixup


#### Cutout

## Architectures

#### ResNet

#### EfficientNet

Scaling width, depth and input resolution

### Convolution Variants

### Width vs Depth

### Receptive Fields

### Attention

### Activations

#### Softmax

invariant to shifts

[Why use softmax as opposed to standard normalization?](https://stackoverflow.com/questions/17187507/why-use-softmax-as-opposed-to-standard-normalization)

##### Temperature

#### ReLU

Cheap to compute `max(0, x)`

dying neurons

#### Sigmoid

vanishing gradients

### Normalization

#### BatchNorm

#### LayerNorm

#### WeightNorm

## Regularization

#### Weight Decay

##### Bias Decay

#### Dropout


#### Label Smoothing

## Losses


## Training

#### Initialization

#### Learning Rate Warmup

#### Large Batch Training

#### Mixed Precision

## Optimization

#### Optimizers


#### Learning Rate Schedules


## Inference Tricks

#### FixRes

#### Multi Crop

## Noise

## Class Imbalance

#### Oversampling

#### Class Weights

## Label Hierarchies

## Multi Label

## Transfer Learning

## Knowledge Distillation

## Few Shot Learning

## Datasets

## Simulation

## Semi Supervised

## Self Supervised / Unsupervised

## Fine Grained Recognition

## Deployment

#### Model Compression / Prunning

#### Mobile

#### Batch Inference

#### Streaming Inference

#### Low Latency Inference

## Issues

#### Bias

#### Training / Serving Skew

#### Adversarial Examples

#### Privacy / Federated Learning

## Evaluation

## Results

#### Parameter Settings


## Parameter Count, FLOPS, Inference Speed

## Dataset Size vs Performance

## Current Heuristics and Best Practices


## Applications

#### Medical Imaging

#### Face Recognition
