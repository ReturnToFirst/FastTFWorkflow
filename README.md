# FastTFWorkflow
Tutorial about How to change your slow tensorflow training faster

## Description
**THIS CODE ONLY WORKS ON NVIDIA GPUS**

Assuming dataset length is infinite, lnline preprocessing can cause CPU bottleneck that can decrease training throughput.\
This code samples show unoptimized/optimized tensorflow workflow.

## Requirements

### Hardware Requirements
* x86-64 (AMD64) CPU
* RAM >= 8GiB
* NVIDIA [Computer Capability](https://developer.nvidia.com/cuda-gpus) 7.0+ GPUs
    * GPU memory > 12GiB for default batch size

#### Test Environment
* CPU : Intel(R) Xeon(R) Gold 5218R
* GPU : 2x A100 80GB PCI-E
* RAM : 255GiB

## Optimization used in this repo
1. [Nvidia DALI](https://developer.nvidia.com/dali/) - GPU Accelerated Dataloader
2. [Mixed Precision](https://arxiv.org/abs/1710.03740) - Better [MMA(Matrix Multiply-Accumulate)](https://en.wikipedia.org/wiki/Multiply-accumulate_operation) throughput than TF32
3. [XLA](https://www.tensorflow.org/xla) - JIT-Compile and fuse operators to effective job scheduling in GPUs
4. (Optional) [Multi GPU training](https://www.tensorflow.org/api_docs/python/tf/distribute/MirroredStrategy) - Use more then one GPU for training


## Usage
1. Clone this repo with submodule
   ```
   git clone --recursive https://github.com/ReturnToFirst/FastTFWorkflow.git

3. Compare performance between unoptimized/optimized workflow

### For advanced users

[after_optimization_multi.ipynb](https://github.com/ReturnToFirst/FastTFWorkflow/blob/master/after_optimization_multi.ipynb) shows training process with multi gpu. 


## DISCLAIMER
> Depanding on devices in computer, performance can be decreased.\
> This optimized code will not show best performance.\
> Multi-GPUs Training doesn't works on test envrionment.\
> Wrong description or code there.