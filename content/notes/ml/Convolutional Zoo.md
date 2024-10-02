---
time_modified: 2024-10-01T22:49:57-04:00
time_created: 2024-10-01T13:37:19-04:00
---
# MobileNetV4: Universal Models for the Mobile Ecosystem
### Authors
Danfeng Qin, Chas Leichner, Manolis Delakis, Marco Fornoni, Shixin Luo, Fan Yang, Weijun Wang, Colby Banbury, Chengxi Ye, Berkin Akin, Vaibhav Aggarwal, Tenghui Zhu, Daniele Moro, and Andrew Howard

### Institution
Google

### Date Published
September 2024 (arXiv submission date)

## TLDR
MobileNetV4 introduces **universal models** optimized for diverse mobile platforms, achieving **mostly Pareto-optimal performance** across CPUs, DSPs, GPUs, and accelerators. The architecture integrates **Universal Inverted Bottlenecks (UIB)** and **Mobile MQA**, providing both flexibility and efficiency, especially with the optimized **Neural Architecture Search (NAS)**. The largest model, MNv4-Hybrid-Large, reaches **87% ImageNet-1K accuracy** with only **3.8ms latency** on Pixel 8 EdgeTPU.

## Tags
MobileNetV4, UIB, NAS, Mobile MQA, Pareto optimality, EdgeTPU, mobile efficiency, hardware-aware, distillation, ImageNet, mobile models

## Key Points
1. **Universal Inverted Bottlenecks (UIB)**:
   - Combines multiple block types (Inverted Bottleneck, ConvNext, FFN) for flexible architecture.
   - Adds an **Extra DepthWise (ExtraDW)** variant.
2. **Mobile MQA (Multi-Query Attention)**:
   - A novel attention block for mobile devices, achieving **39% speedup** compared to previous attention mechanisms.
3. **Optimized NAS Recipe**:
   - Two-phase search for coarse and fine-grained model optimization.
4. **Distillation for Efficiency**:
   - Introduces novel dataset mixing and augmentation strategies for improved generalization.

## Detailed Summary
### Introduction
MobileNetV4 focuses on providing efficient on-device neural networks for mobile ecosystems, balancing between **accuracy and hardware efficiency**. This generation introduces **Universal Inverted Bottlenecks (UIB)**, **Mobile MQA**, and a **refined NAS recipe** to achieve superior performance across **CPUs, DSPs, GPUs, and accelerators** like EdgeTPU.

### Universal Inverted Bottlenecks
UIB unifies blocks like Inverted Bottleneck (IB), ConvNext, and Feed Forward Networks (FFN). It introduces **ExtraDW**, which extends spatial mixing and channel mixing for efficiency and flexibility in **computational utilization**. UIB can adapt to different hardware architectures, optimizing both memory and computation.

### Mobile MQA
Mobile MQA improves the efficiency of attention mechanisms by **sharing keys and values across heads**, reducing **memory bandwidth requirements**. This optimization results in **39% faster inference** on EdgeTPUs and significant efficiency gains on mobile GPUs.

### Neural Architecture Search (NAS)
The **two-phase NAS** process first performs a coarse-grained search to optimize filters and then refines the configurations of UIB layers. This results in models like MNv4-Conv-S and MNv4-Hybrid-L that are optimized for various hardware platforms.

### Distillation Strategy
The paper introduces a **novel distillation technique**, improving accuracy by using a **dynamic dataset mixing strategy** that combines augmentations and class-balancing methods, particularly from the **JFT dataset**. This boosts generalization and reduces overfitting in models like **MNv4-Hybrid-L**.

### Performance
The MNv4 suite, especially the **Hybrid-Large** model, delivers **87% accuracy** on ImageNet-1K while maintaining low latencies (3.8ms) on the **Pixel 8 EdgeTPU**, setting a new benchmark for efficient mobile models.

## Models
- **MobileNetV4-Conv-S**: Optimized for **low MACs** with 73.8% ImageNet accuracy and 0.2ms latency.
- **MobileNetV4-Hybrid-L**: Achieves **87% ImageNet accuracy** in 3.8ms on EdgeTPU, utilizing both UIB and Mobile MQA.

## Datasets
- **ImageNet-1K**: Used for training and evaluation.
- **JFT-300M**: Used for **distillation**, with class-balanced resampling to boost generalization.

## Results
| Model            | Accuracy (Top-1) | MACs (G) | Pixel 6 CPU Latency (ms) | EdgeTPU Latency (ms) |
|------------------|------------------|----------|---------------------------|-----------------------|
| MobileNetV4-Conv-S | 73.8%            | 0.2      | 2.4                       | 3.8                   |
| MobileNetV4-Hybrid-L | 87%             | 5.9      | 20.8                      | 3.8                   |

## Hyper Parameters
| Hyper Parameter    | Conv-S  | Conv-M  | Hybrid-M  | Conv-L  | Hybrid-L |
|--------------------|---------|---------|-----------|---------|----------|
| Batch Size         | 4096    | 4096    | 16384     | 16384   | 16384    |
| Peak Learning Rate | 0.002   | 0.004   | 0.016     | 0.004   | 0.01     |
| Warm-up Epochs     | 5       | 5       | 20        | 20      | 20       |
| Training Epochs    | 9600    | 500     | 500       | 500     | 500      |

## Hardware and Software
- **Training Hardware**: Pixel 6 and Pixel 8 (CPU), Samsung S23 GPU, EdgeTPU, Qualcomm DSP.
- **Software**: TensorFlow, TensorFlow Lite, PyTorch-to-TFLite conversion.

## Code Examples
### Universal Inverted Bottleneck (UIB) Block Example (PyTorch)
```python
import torch
import torch.nn as nn

class UIBBlock(nn.Module):
    def __init__(self, in_channels, out_channels, kernel_size=3, stride=1):
        super(UIBBlock, self).__init__()
        self.conv1 = nn.Conv2d(in_channels, in_channels, kernel_size, stride, groups=in_channels)
        self.bn1 = nn.BatchNorm2d(in_channels)
        self.conv2 = nn.Conv2d(in_channels, out_channels, 1)
        self.bn2 = nn.BatchNorm2d(out_channels)
        self.relu = nn.ReLU(inplace=True)

    def forward(self, x):
        x = self.conv1(x)
        x = self.bn1(x)
        x = self.relu(x)
        x = self.conv2(x)
        x = self.bn2(x)
        return x
```

## Review
**Rating**: 9/10  
The paper provides significant advances in mobile model optimization, particularly through its innovative use of UIB and Mobile MQA blocks. The authors' focus on Pareto optimality across a wide range of mobile hardware is highly commendable. However, more details on real-world deployment scenarios would further validate its universal applicability.

## Related Works
1. **MobileNetV1** (Andrew Howard, 2017): Introduced depthwise-separable convolutions for mobile efficiency.
2. **MobileNetV2** (Mark Sandler, 2018): Enhanced with linear bottlenecks and inverted residuals.
3. **ConvNext** (Zhuang Liu, 2022): Developed a convnet for modern vision tasks.
4. **FastViT** (Pavan Kumar Vasu, 2023): Hybrid vision transformer optimized for speed.

## Follow Up Ideas
1. Explore **UIB blocks** in non-vision tasks such as speech processing for mobile devices.
2. Extend **Mobile MQA** to general attention mechanisms in larger language models.
3. Investigate **NAS optimization** for real-time systems with more stringent hardware constraints.