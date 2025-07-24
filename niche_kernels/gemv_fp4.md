**What is this about:** gemv kernel is general matrix vector product. It's a core operation in ML.

**Why is it important:** Tensor cores are inefficient with vectors (1D array), they're made for tensors (2D arrays). But, inference often uses batch size of 1 with some sequence length. After prefill is done, query is a single token and MLPs get (1, hidden dim) as input. This implies that there's a lot of matrix-vector products happening on the Tensor cores.

**Existing examples:** People have been trying to optimize such a fundamental operation for different precisions for a while, for example, Bruce-Lee-LY/cuda_hgemv: Several optimization methods of half-precision general matrix vector multiplication (HGEMV) using CUDA core. https://share.google/KolRiHlvqmXWzfR9X.

**What needs to be done:** Due to the new FP4 precision, new gemv kernels that support vector@matrix in FP4 are needed that can be run on FP4 Tensor cores efficiently.