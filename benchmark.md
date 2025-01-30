---
title: Tracking Latest Benchmarks of dyGiLa 
feature_image: "/pic/title-pic-c.png"
excerpt: "benchmark on supercomputer"
---
Along the course of development of dyGiLa, multiple stages of benchmark on computing clusters will be conducted.
This page dedicates to track the benchmarks of dyGiLa on different hardwares and their scaling capabilities. 
Based on what kind and how many computing resources on hand, the statistics of benchmark data may change according how many 
resources can be put on benchmark runs.

#### Strong Scaling Benchmark on LUMI 
 
<img src="{{ site.github.url }}/pic/bench1-lumiG-logy.png" alt="Home" width="100%">

dyGiLa is developed upon few frameworks. There is framework providing mathematical objects, discretized spital grid and time points for lattice field theory support.
And there is also framework providing data streaming in mean of parallel for post-hoc analysis and in-situ visualizing simulating data. 
The former is provided by [HILA](https://cft-hy.github.io/HILA.home) project, while the latter is project [Ascent](https://ascent.readthedocs.io/en/latest) 
Make sure they have been compiled or installed in the proper way before going to next steps. 

To leverage modern hybrid CPU-GPGPU computational source, both [HILA](https://cft-hy.github.io/HILA.home) and [Ascent](https://ascent.readthedocs.io/en/latest)
need [GNU make](https://www.gnu.org/software/make/), [CMake](https://cmake.org/), `MPI` ([mpich](https://www.mpich.org/), [openmpi](https://www.open-mpi.org/)), 
`FFTW`([FFTW3](https://fftw.org/)) and [LLVM/Clang](https://llvm.org/), make sure these softwares and libraries have been installed on the system you intend to work on. 
When the targeted platform offers [GPGPU](https://en.wikipedia.org/wiki/General-purpose_computing_on_graphics_processing_units) supporting, the vendor-specific 
firmware and libraries have to be installed and configured properly as well. For the `Nvidia` hardware, the architecture e.g.,`sm_75, sm_80, sm_90` etc have to be identified properly for the hardware,
and [CUDA](https://developer.nvidia.com/cuda-toolkit) have to be installed, `OpenACC` is not supported. For `ÀMD` hardware, [drivers](https://www.amd.com/en/support/download/drivers.html) and 
[ROCm](https://rocm.docs.amd.com/en/latest/index.html) open source library have to be installed. 
However, things for AMD hardwares could be tricky dependent on their architecture,`ÀMD Instinct CDNA` architecture have the full support from [ROCm](https://rocm.docs.amd.com/en/latest/index.html), while `Radeon RDNA` only partially supported by [ROCm](https://rocm.docs.amd.com/en/latest/index.html). 
To know if given AMD hardware is supported by ROCm, one could check the [ROCm support list](https://rocm.docs.amd.com/projects/install-on-linux/en/latest/reference/system-requirements.html) 


