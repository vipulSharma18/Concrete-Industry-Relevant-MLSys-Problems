# Concrete-Industry-Relevant-MLSys-Problems
A repo tracking concrete ML sys problems that I discover while browsing ML discord servers. I'm hoping this is a good opportunity for people new to the field to make a meaningful contribution.


- [ ] efficient MoE: reduce the cost of all2all between experts and reduce the dynamic data dependent expert loading memory bandwidth that can't be compiled into CUDA graph cause its data dependent. related work: https://pytorch.org/blog/accelerating-moes-with-a-triton-persistent-cache-aware-grouped-gemm-kernel/

- [ ] multimodality supporting flash attention: "implement flash hybrid interleaved multi-sequence full/causal attention without flex attention nor using lame massive attention mask nor iteratively running attention on each sequence...yeh- so like- text tokens followed by diffusing image followed by text tokens followed by something else followed by some other full attention thing etc...mainly for this type of thing ppl use flex...also- it would preferrably be done using at least hopper arch, because tma fast, and flash 2 (as in version 2) slow....this model use it https://bagel-ai.org/" from user zippika on EAI discord. References: A Survey of Efficient
Attention Methods:
Hardware-efficient, Sparse, Compact, and Linear Attention, https://pytorch.org/blog/flexattention/

- [ ] Hardware aware data loaders: optimize the matrix shapes of data to allow for efficient use of DRAM bursts and banks while loading data for pre-training. check how this impacts the speed run performance by increasing memory footprint on DRAM due to padding. Things to look into: typical data loaders and their memory access code. Related: sequence packing to avoid wasted flops on padded input. just do packing while being aligned with DRAM burst size.

- [ ] "SECOND GPU_MODE AMD $100K kernel competition: ⚡️DISTRIBUTED KERNELS!! You now get free access to a full **8xMI300 node** to optimize all2all, gemm + reducescatter, and allreduce + gemm kernels -- all relevant to frontier LMs!" - From Alex Zhang on Twitter (https://x.com/a1zhang/status/1960773095599562987).

From user seraphim on GPU mode discord:
"GPU MODE is going MULTI GPU MODE with another $100K kernel competition in collaboration with AMD where you'll be optimizing 3 different distributed inference kernels on MI300 designed by @daniel huang 
Single node 8 GPU all-to-all kernel
Single node 8 GPU GEMM + reduce-scatter kernel
Single node 8 GPU allgather + GEMM kernel

Logistics
Please register here to be eligibile for prize money https://amdchallenge2025.datamonsters.com/
Registration is open until September 20
Kernel submissions will be accepted from Aug 30 to Oct 13
Winner will be invited to an awards ceremony in SF on Oct 20

Same as before you can expect to
Make submissions at ⁠submissions
We'll share updates on ⁠status
Detailed write-ups and hints from @az
And you can continue chatting on ⁠general-leaderboard
"
