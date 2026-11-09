1. Создайте папку в нужном вам месте с именем TensorBench, положите туда файл GPU_Benchmark_180s.c.u.t.w.exe

2. Скачайте архив cuBLAS.and.cuDNN_CUDA12_win_v3.7z и распакуйте содержимое в папку TensorBench рядом с файлом GPU_Benchmark_180s.c.u.t.w.exe

3. Запустите файл GPU_Benchmark_180s.c.u.t.w.exe
-----
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

## How to Run
1. Create a folder in the desired location named TensorBench and place the GPU_Benchmark_180s.c.u.t.w.exe file there.
2. Download the cuBLAS.and.cuDNN_CUDA12_win_v3.7z archive and unzip the contents into the TensorBench folder next to the GPU_Benchmark_180s.c.u.t.w.exe file.
3. Run the GPU_Benchmark_180s.c.u.t.w.exe file.

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

Time:   10.0 s | Interval: 37.443 TFLOPS | Average: 37.443 TFLOPS | GEMM: 2720 | GPUClock: 1605 MHz | U: 0.750 V | T:55*C | Power: ~120 W
Time:   20.0 s | Interval: 37.332 TFLOPS | Average: 37.388 TFLOPS | GEMM: 5430 | GPUClock: 1620 MHz | U: 0.750 V | T:57*C | Power: ~75 W
Time:   30.0 s | Interval: 37.250 TFLOPS | Average: 37.342 TFLOPS | GEMM: 8110 | GPUClock: 1620 MHz | U: 0.750 V | T:59*C | Power: ~130 W
Time:   40.1 s | Interval: 37.187 TFLOPS | Average: 37.303 TFLOPS | GEMM: 10810 | GPUClock: 1620 MHz | U: 0.750 V | T:60*C | Power: ~129 W
Time:   50.1 s | Interval: 37.180 TFLOPS | Average: 37.279 TFLOPS | GEMM: 13510 | GPUClock: 1620 MHz | U: 0.750 V | T:61*C | Power: ~130 W
Time:   60.1 s | Interval: 37.110 TFLOPS | Average: 37.250 TFLOPS | GEMM: 16200 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~130 W
Time:   70.1 s | Interval: 37.086 TFLOPS | Average: 37.227 TFLOPS | GEMM: 18890 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~131 W
Time:   80.1 s | Interval: 37.049 TFLOPS | Average: 37.205 TFLOPS | GEMM: 21580 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~130 W
Time:   90.1 s | Interval: 37.063 TFLOPS | Average: 37.189 TFLOPS | GEMM: 24270 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~130 W
Time:  100.2 s | Interval: 37.064 TFLOPS | Average: 37.176 TFLOPS | GEMM: 26960 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~123 W
Time:  110.2 s | Interval: 37.015 TFLOPS | Average: 37.162 TFLOPS | GEMM: 29650 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~123 W
Time:  120.2 s | Interval: 37.023 TFLOPS | Average: 37.150 TFLOPS | GEMM: 32340 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~125 W
Time:  130.2 s | Interval: 37.103 TFLOPS | Average: 37.147 TFLOPS | GEMM: 35030 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~122 W
Time:  140.2 s | Interval: 37.060 TFLOPS | Average: 37.140 TFLOPS | GEMM: 37720 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~130 W
Time:  150.3 s | Interval: 37.012 TFLOPS | Average: 37.132 TFLOPS | GEMM: 40410 | GPUClock: 1605 MHz | U: 0.750 V | T:62*C | Power: ~123 W
Time:  160.3 s | Interval: 36.997 TFLOPS | Average: 37.123 TFLOPS | GEMM: 43100 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~130 W
Time:  170.3 s | Interval: 37.005 TFLOPS | Average: 37.116 TFLOPS | GEMM: 45790 | GPUClock: 1620 MHz | U: 0.750 V | T:62*C | Power: ~130 W

========== FINAL RESULTS ==========
Total GEMM operations: 48390
Total GPU compute time: 179.22 seconds
Average FP16 performance: 37.109 TFLOPS
Validation: PASS
===================================
