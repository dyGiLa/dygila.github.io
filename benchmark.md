---
title: Tracking Latest Benchmarks of dyGiLa 
feature_image: "/pic/title-pic-c.png"
excerpt: "benchmark on supercomputer"
---
Along the course of development and deploy of dyGiLa, multiple stages of benchmark on computing clusters will be conducted.
This page dedicates to track the benchmarks of dyGiLa on different hardwares and their scaling capabilities. 
Based on what kind and how many computing resources on hand, the statistics of benchmark data may change according to how many 
resources could be put on benchmark runs.

#### Strong Scaling Benchmark on LUMI supercomputer -- 30. Jan. 2024
The following plot shows dyGiLa's strong scaling characteristics on `LUMI-G` GPGPU partition.
the parallel data streaming engine `pario` was turned off in this benchmark.
the simulation domain has 2048\*2048\*2048 = 8.5899 billions sites on uniform lattice.
On each site, there are `18 + 18 + 1 + 3 + 1 = 41` `float` type numbers, which correspond to 2 complex valued matrix fields, 2 scalar filed and one vector field.
Then the total simulation data is `1.408749 Terabyte`. This setup was run on LUMI-G with different number of nodes ranged form 6 to 30. 
A LUMI-C run with 64 EPYC milan nodes is presented in same plot.
 
<img src="{{ site.github.url }}/pic/bench1-lumiG-logy.png" alt="Home" width="100%">

The programming environment (PE) `LUMI/24.03` was used in this benchmark. 
This PE provides Cray-spined `Clang/17.0.1` compiler, and `ROCm/6.0.3`.


