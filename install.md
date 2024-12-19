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

### Getting Source and Compile

Same as most of FOSS project, dyGiLa is hosted on public source code repositories service providers such as Bitbucket, Github and GitLab.
```console
$ git clone git@github.com:dyGiLa/dyGiLa.git 
```
or
```console
$ git clone https://Quang01@bitbucket.org/hindmars/he3-simulator.git
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
* `lumi-hip`: GPU-aware MPI architecture on cluster LUMI
There are more possibly supported architecture configurations can be found in [HILA](https://cft-hy.github.io/HILA.home) source files.

If every goes well, user could find the linked binary executable `dyGiLa` under `./build` folder.
