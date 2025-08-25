# Concrete-Industry-Relevant-MLSys-Problems
A repo tracking concrete ML sys problems that I discover while browsing ML discord servers. I'm hoping this is a good opportunity for people new to the field to make a meaningful contribution.


- [ ] efficient MoE: reduce the cost of all2all between experts and reduce the dynamic data dependent expert loading memory bandwidth that can't be compiled into CUDA graph cause its data dependent. related work: https://pytorch.org/blog/accelerating-moes-with-a-triton-persistent-cache-aware-grouped-gemm-kernel/

- [ ] multimodality supporting flash attention: "implement flash hybrid interleaved multi-sequence full/causal attention without flex attention nor using lame massive attention mask nor iteratively running attention on each sequence...yeh- so like- text tokens followed by diffusing image followed by text tokens followed by something else followed by some other full attention thing etc...mainly for this type of thing ppl use flex...also- it would preferrably be done using at least hopper arch, because tma fast, and flash 2 (as in version 2) slow....this model use it https://bagel-ai.org/" from user zippika on EAI discord. References: A Survey of Efficient
Attention Methods:
Hardware-efficient, Sparse, Compact, and Linear Attention, https://pytorch.org/blog/flexattention/
- [ ] Hardware aware data loaders: optimize the matrix shapes of data to allow for efficient use of DRAM bursts and banks while loading data for pre-training. check how this impacts the speed run performance by increasing memory footprint on DRAM due to padding. Things to look into: typical data loaders and their memory access code. Related: We do sequence packing of prompts to ensure we can do parallel batch inference by making all samples of the same size.
