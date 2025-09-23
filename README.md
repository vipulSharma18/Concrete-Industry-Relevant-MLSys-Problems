# Concrete-Industry-Relevant-MLSys-Problems
A repo tracking concrete ML sys problems that I discover while browsing ML discord servers. I'm hoping this is a good opportunity for people new to the field to make a meaningful contribution.


- [ ] efficient MoE: reduce the cost of all2all between experts and reduce the dynamic data dependent expert loading memory bandwidth that can't be compiled into CUDA graph cause its data dependent. related work: https://pytorch.org/blog/accelerating-moes-with-a-triton-persistent-cache-aware-grouped-gemm-kernel/

- [ ] multimodality supporting flash attention: "implement flash hybrid interleaved multi-sequence full/causal attention without flex attention nor using lame massive attention mask nor iteratively running attention on each sequence...yeh- so like- text tokens followed by diffusing image followed by text tokens followed by something else followed by some other full attention thing etc...mainly for this type of thing ppl use flex...also- it would preferrably be done using at least hopper arch, because tma fast, and flash 2 (as in version 2) slow....this model use it https://bagel-ai.org/" from user zippika on EAI discord. References: A Survey of Efficient
Attention Methods:
Hardware-efficient, Sparse, Compact, and Linear Attention, https://pytorch.org/blog/flexattention/

- [ ] Hardware aware data loaders: optimize the matrix shapes of data to allow for efficient use of DRAM bursts and banks while loading data for pre-training. check how this impacts the speed run performance by increasing memory footprint on DRAM due to padding. Things to look into: typical data loaders and their memory access code. Related: sequence packing to avoid wasted flops on padded input. just do packing while being aligned with DRAM burst size.

- [ ] "SECOND GPU_MODE AMD $100K kernel competition: ⚡️DISTRIBUTED KERNELS!! You now get free access to a full **8xMI300 node** to optimize all2all, gemm + reducescatter, and allreduce + gemm kernels -- all relevant to frontier LMs!" - From Alex Zhang on Twitter (https://x.com/a1zhang/status/1960773095599562987). More relevant messages from GPU mode discord:
  - > "GPU MODE is going MULTI GPU MODE with another $100K kernel competition in collaboration with AMD where you'll be optimizing 3 different distributed inference kernels on MI300 designed by @daniel huang    
    > Single node 8 GPU all-to-all kernel    
    > Single node 8 GPU GEMM + reduce-scatter kernel     
    > Single node 8 GPU allgather + GEMM kernel    
    >
    > Logistics    
    > Please register here to be eligibile for prize money https://amdchallenge2025.datamonsters.com/    
    > Kernel submissions will be accepted from Aug 30 to Oct 13    
    > Winner will be invited to an awards ceremony in SF on Oct 20    
    > Detailed write-ups and hints from @az"    
  - > "Iris is an experimental, open-source library from the AMD Research team that adds SHMEM-like Remote Memory Access (RMA) to Triton — making multi-GPU programming feel like single-GPU and letting you quickly iterate over designs, algorithms, work distribution & assignment strategies in minutes.    
    > Pure Python + Triton (~370 LOC)    
    > Examples from simple memory ops to fused/overlapped GEMM: https://github.com/ROCm/iris/blob/main/examples/README.md    
    > Familiar PyTorch and Triton-like APIs    
    > Supports MI300X, MI350X, MI355X    
    > GitHub: https://github.com/ROCm/iris     
- [ ] JaneStreet GPU Mode Hackathon for optimizing sequence models. Optimize Mamba2, RetNet, Hawk, and xLSTM: https://github.com/janestreet-gpu-mode/hackathon
- [ ] Train video models in a single day, new edition: https://arxiv.org/abs/2309.16669. Repo tracking this work: https://github.com/vipulSharma18/we-have-video-models-at-home
- [ ] Sharpen quantization skills with Unsloth puzzles. They were good enough to be used for hiring: https://colab.research.google.com/drive/1JqKqA1XWeLHvnYAc0wzrR4JBCnq43HyH?usp=sharing
