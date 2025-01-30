---
title: Clone repo and Compilations
feature_image: "/pic/title-pic-c.png"
excerpt: "Clone repo and compilation"
---

### Library Dependencies 

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

### Getting Source and Compile

Same as most of FOSS project, dyGiLa is hosted on public source code repositories service providers Bitbucket and Github.
```console
$ git clone git@github.com:dyGiLa/dyGiLa.git ./dyGiLa
```
or
```console
$ git clone https://bitbucket.org/hindmars/he3-simulator.git ./dyGila
```
will fetch default branch to the current path under the folder `dyGiLa`.
After this run 
```console
$ cd dyGiLa
$ make -j n ARCH=xxx-xxx
```
to compile the dyGiLa binary. Here `n` is thread numbers of parallel compilation, and `ARCH=xxx-xxx` specifies the architectures of hardwares,
it could be 
* `vanila`:`X86-64` CUP architecture
* `ÀVX`: SIMP/AVX vector accelerating CUP architecture

or for specific clusters:
* `mahti`: CPU architecture on cluster mahti
* `mahti-cuda`: GPU-aware MPI architecture on cluster mahti
* `lumi`: CPU architecture on cluster LUMI
* `lumi-hip-CC`: GPU-aware MPI architecture on cluster LUMI
There are more possibly supported architecture configurations can be found in [HILA](https://cft-hy.github.io/HILA.home) source files.

If every goes well, user could find the linked binary executable `dyGiLa` under `./build` folder.
However, the reality could be hash and complicated, especially on computational clusters, to which dyGiLa targets.
In most common cases, these big machines are configured with [Lmod](https://lmod.readthedocs.io/en/latest/) module system.
The crucial dependency may be missing on their available list such as `LLVM/Clang`, which provides `Abstract Syntax Tree (AST)` utilities for 
GPU kernel generation. For how to solve this problem or walk around it, please read [Dependencies On Supercomputer of HILA](https://cft-hy.github.io/HILA.home/install).
