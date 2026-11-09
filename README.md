-Лёгкий бенчмарк для длительного тестирования вычислительной производительности графических процессоров NVIDIA в режимах FP16 и FP32 с использованием матричных операций GEMM через библиотеку cuBLAS.

-Бенчмарк проводит отдельные тесты в обоих режимах: FP16 с использованием тензорных ядер (Tensor Cores) и FP32 с использованием CUDA-ядер (CUDA Cores). Это позволяет непосредственно сравнить производительность GPU в двух форматах вычислений и определить соотношение между ними.

*В отличие от синтетических тестов с кратковременными пиковыми нагрузками, бенчмарк обеспечивает продолжительную вычислительную нагрузку, одновременно отслеживая телеметрию видеокарты в реальном времени: частоту GPU, напряжение ядра, температуру и потребляемую мощность всей платы.*
---
1. Создайте папку в нужном вам месте с именем TensorBench, положите туда файл GPU_Benchmark_180s.c.u.t.w.exe

2. Скачайте архив cuBLAS.and.cuDNN_CUDA12_win_v3.7z и распакуйте содержимое в папку TensorBench рядом с файлом GPU_Benchmark_180s.c.u.t.w.exe
- Прямая ссылка на архив: https://github.com/Purfview/whisper-standalone-win/releases/download/libs/cuBLAS.and.cuDNN_CUDA12_win_v3.7z

3. Запустите файл GPU_Benchmark_180s.c.u.t.w.exe

## Note: 180s.c.u.t.w расшифровка названия:
- 180 продолжительность,
- s. секунды, 
- c. сокращённо Clock частота GPU, 
- u. напряжение 0.750 V, 
- t. температура *C, 
- w. потребление Wat.
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
- https://github.com/Purfview/whisper-standalone-win/releases/download/libs/cuBLAS.and.cuDNN_CUDA12_win_v3.7z
3. Run the GPU_Benchmark_180s.c.u.t.w.exe file.

*Note: 
- For accurate voltage and power readings, run the executable as Administrator.
- The benchmark uses FP16 matrix multiplication with Tensor Cores through the cuBLAS library. The test ran continuously for 180 seconds.
- Minor follow-up: I also tested a hard lock at 1605 MHz / 0.750 V. 
- Result: Average performance slightly increased to 37.219 TFLOPS (48,570 total GEMMs vs 48,390 previously) with zero micro-dips. 
- Conclusion: A slightly lower but strictly stable clock yields better average throughput than targeting the absolute edge of the OCP limit.*

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
Time:   30.1 s | Interval: 37.550 TFLOPS | Average: 37.787 TFLOPS | GEMM: 8240 | GPUClock: 1605 MHz | U: 0.750 V | T:56*C | Power: ~128 W
Time:   40.1 s | Interval: 37.378 TFLOPS | Average: 37.685 TFLOPS | GEMM: 10950 | GPUClock: 1605 MHz | U: 0.750 V | T:58*C | Power: ~128 W
Time:   50.1 s | Interval: 37.201 TFLOPS | Average: 37.588 TFLOPS | GEMM: 13650 | GPUClock: 1605 MHz | U: 0.750 V | T:59*C | Power: ~128 W
Time:   60.1 s | Interval: 37.085 TFLOPS | Average: 37.504 TFLOPS | GEMM: 16340 | GPUClock: 1605 MHz | U: 0.750 V | T:60*C | Power: ~129 W
Time:   70.1 s | Interval: 37.107 TFLOPS | Average: 37.448 TFLOPS | GEMM: 19030 | GPUClock: 1605 MHz | U: 0.750 V | T:61*C | Power: ~122 W
Time:   80.1 s | Interval: 37.145 TFLOPS | Average: 37.410 TFLOPS | GEMM: 21730 | GPUClock: 1605 MHz | U: 0.750 V | T:61*C | Power: ~122 W
Time:   90.2 s | Interval: 37.124 TFLOPS | Average: 37.378 TFLOPS | GEMM: 24430 | GPUClock: 1605 MHz | U: 0.750 V | T:62*C | Power: ~131 W
Time:  100.2 s | Interval: 37.008 TFLOPS | Average: 37.341 TFLOPS | GEMM: 27120 | GPUClock: 1605 MHz | U: 0.750 V | T:62*C | Power: ~122 W
Time:  110.2 s | Interval: 37.094 TFLOPS | Average: 37.319 TFLOPS | GEMM: 29810 | GPUClock: 1605 MHz | U: 0.750 V | T:62*C | Power: ~130 W
Time:  120.2 s | Interval: 37.123 TFLOPS | Average: 37.302 TFLOPS | GEMM: 32510 | GPUClock: 1605 MHz | U: 0.750 V | T:62*C | Power: ~122 W
Time:  130.3 s | Interval: 37.058 TFLOPS | Average: 37.284 TFLOPS | GEMM: 35200 | GPUClock: 1605 MHz | U: 0.750 V | T:62*C | Power: ~130 W
Time:  140.3 s | Interval: 37.055 TFLOPS | Average: 37.267 TFLOPS | GEMM: 37890 | GPUClock: 1605 MHz | U: 0.750 V | T:62*C | Power: ~128 W
Time:  150.3 s | Interval: 37.074 TFLOPS | Average: 37.254 TFLOPS | GEMM: 40580 | GPUClock: 1605 MHz | U: 0.750 V | T:63*C | Power: ~128 W
Time:  160.3 s | Interval: 37.034 TFLOPS | Average: 37.241 TFLOPS | GEMM: 43270 | GPUClock: 1605 MHz | U: 0.750 V | T:63*C | Power: ~130 W
Time:  170.3 s | Interval: 37.025 TFLOPS | Average: 37.228 TFLOPS | GEMM: 45960 | GPUClock: 1605 MHz | U: 0.750 V | T:63*C | Power: ~131 W

========== FINAL RESULTS ==========
Total GEMM operations: 48570
Total GPU compute time: 179.36 seconds
Average FP16 performance: 37.219 TFLOPS
Validation: PASS
===================================
