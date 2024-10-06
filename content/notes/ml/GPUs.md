---
time_modified: 2024-10-04T12:18:00-04:00
time_created: 2024-10-03T11:13:34-04:00
---
#gpu #hardware


[[Cloud GPUs]]

# GPU Programming

- [ ] See [[cuda]]
- [ ] [GPU MODE - YouTube](https://www.youtube.com/channel/UCJgIbYl6C5no72a0NUAPcTA)
- [ ] [GitHub - gpu-mode/resource-stream: GPU programming related news and material links](https://github.com/gpu-mode/resource-stream)

# GPU Architecture

- [ ] [Modern GPU Architecture | GPU Programming - YouTube](https://youtu.be/whPSD8sdx-0?si=PBPU2woJPHaf0E8n)
- [ ] [ml-engineering/compute/accelerator at master · stas00/ml-engineering · GitHub](https://github.com/stas00/ml-engineering/tree/master/compute/accelerator)


## Tensor Cores





# Specs



|                       | NVIDIA B200        | NVIDIA B100        | NVIDIA H200          | NVIDIA H100          | NVIDIA A100        |
| :-------------------- | :----------------- | :----------------- | :------------------- | :------------------- | :----------------- |
| Architecture          | Blackwell          | Blackwell          | Hopper               | Hopper               | Ampere             |
| FP64                  | 40 teraFLOPS       | 30 teraFLOPS       | 34 teraFLOPS         | 34 teraFLOPS         | 9.7 teraFLOPS      |
| FP64 Tensor Core      | 40 teraFLOPS       | 30 teraFLOPS       | 67 teraFLOPS         | 67 teraFLOPS         | 19.5 teraFLOPS     |
| FP32                  | 80 teraFLOPS       | 60 teraFLOPS       | 67 teraFLOPS         | 67 teraFLOPS         | 19.5 teraFLOPS     |
| FP32 Tensor Core      | 2.2 petaFLOPS      | 1.8 petaFLOPS      | 989 teraFLOPS        | 989 teraFLOPS        | 312 teraFLOPS      |
| FP16/BF16 Tensor Core | 4.5 petaFLOPS      | 3.5 petaFLOPS      | 1979 teraFLOPS       | 1979 teraFLOPS       | 624 teraFLOPS      |
| INT8 Tensor Core      | 9 petaOPs          | 7 petaOPs          | 3958 teraOPs         | 3958 teraOPs         | 1248 teraOPs       |
| FP8 Tensor Core       | 9 petaFLOPS        | 7 petaFLOPS        | 3958 teraFLOPS       | 3958 teraFLOPS       | -                  |
| FP4 Tensor Core       | 18 petaFLOPS       | 14 petaFLOPS       | -                    | -                    | -                  |
| GPU Memory            | 192GB HBM3e        | 192GB HBM3e        | 141GB HBM3e          | 80GB HBM3            | 80GB HBM2e         |
| Memory Bandwidth      | Up to 8TB/s        | Up to 8TB/s        | 4.8TB/s              | 3.2TB/s              | 2TB/s              |
| Multi-Instance GPUs   | Up to 7 MIGs @23GB | Up to 7 MIGs @23GB | Up to 7 MIGs @16.5GB | Up to 7 MIGs @16.5GB | Up to 7 MIGs @10GB |
| Interconnect          | NVLink 1.8TB/s     | NVLink 1.8TB/s     | NVLink 900GB/s       | NVLink 900GB/s       | NVLink 600GB/s     |


