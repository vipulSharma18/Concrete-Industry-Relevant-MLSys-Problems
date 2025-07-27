```
mkdir build && cd build
cmake ..
make -j$(nproc)
```

for enabling debugging with cuda-gdb which will slow down code a lot:
```
cmake -DENABLE_CUDA_DEBUG=True ...
```