Создайте папку в нужном вам месте, положите туда файл GPU_Benchmark_180s.c.u.t.w.exe
Скачайте архив cuBLAS.and.cuDNN_CUDA12_win_v3.7z и распакуйте содержимое в папку с файлом GPU_Benchmark_180s.c.u.t.w.exe 
Запустите файл GPU_Benchmark_180s.c.u.t.w.exe
-----------------------------------------
# CUDA FP16 Tensor Core Benchmark with Telemetry

A lightweight, sustained-load benchmark for measuring FP16 Tensor Core performance (TFLOPS) on NVIDIA GPUs using cuBLAS GEMM. Unlike synthetic spikes, this tool runs a continuous 180-second workload while monitoring real-time hardware telemetry: GPU Clock, Core Voltage (U), Temperature (T), and Board Power (W).

## Features
- **Real Performance:** Uses `cublasGemmEx` with `CUBLAS_COMPUTE_32F` and `CUBLAS_GEMM_DEFAULT_TENSOR_OP` to fully utilize Tensor Cores.
- **Sustained Load:** 180-second continuous test to observe thermal and power throttling behavior.
- **Hardware Telemetry:** Dynamically loads NVML and NVAPI to report Clock, Voltage, Temperature, and Power without requiring a full CUDA Toolkit installation.
- **Result Validation:** Performs a mathematical sanity check at the end to ensure compute integrity (`PASS`/`FAIL`).

## Requirements
- NVIDIA GPU with Compute Capability 7.0 or higher (Volta, Turing, Ampere, Ada, Hopper).
- Windows OS (64-bit).
- *(Optional but recommended)* NVIDIA Display Drivers installed (for NVML/NVAPI telemetry).

*Note: For accurate voltage and power readings, run the executable as Administrator.*

## Example Output
```text
GPU: NVIDIA GeForce RTX 2060
Compute capability: 7.5
Matrix: 4096 x 4096
Mode: FP16 Tensor Core
Duration: 180 seconds

Warming up GPU...
Warmup complete.
Starting 180-second test...

Time:   10.0 s | Interval: 38.095 TFLOPS | Average: 38.095 TFLOPS | GEMM: 2770 | GPUClock: 1605 MHz | U: 0.750 V | T:50*C | Power: ~126 W
Time:   20.1 s | Interval: 37.716 TFLOPS | Average: 37.905 TFLOPS | GEMM: 5510 | GPUClock: 1605 MHz | U: 0.750 V | T:54*C | Power: ~127 W
...
Time:  170.3 s | Interval: 37.025 TFLOPS | Average: 37.228 TFLOPS | GEMM: 45960 | GPUClock: 1605 MHz | U: 0.750 V | T:63*C | Power: ~131 W

========== FINAL RESULTS ==========
Total GEMM operations: 48570
Total GPU compute time: 179.36 seconds
Average FP16 performance: 37.219 TFLOPS
Validation: PASS
===================================
