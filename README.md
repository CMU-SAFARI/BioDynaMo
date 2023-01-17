# Supplementary Materials for "High-Performance and Scalable Agent-Based Simulation with BioDynaMo"

This repository contains all Supplementary Materials for the paper: Breitwieser et al., "High-Performance and Scalable Agent-Based Simulation with BioDynaMo" available at [https://doi.org/10.1145/3572848.3577480](https://doi.org/10.1145/3572848.3577480).

## Paper abstract

Agent-based modeling plays an essential role in gaining insights into biology, sociology, economics, and other fields. However, many existing agent-based simulation platforms are not suitable for large-scale studies due to the low performance of the underlying simulation engines. To overcome this limitation, we present a novel high-performance simulation engine.

We identify three key challenges for which we present the following solutions. First, to maximize parallelization, we present an optimized grid to search for neighbors and parallelize the merging of thread-local results. Second, we reduce the memory access latency with a NUMA-aware agent iterator, agent sorting with a space-filling curve, and a custom heap memory allocator. Third, we present a mechanism to omit the collision force calculation under certain conditions.

Our evaluation shows an order of magnitude improvement over Biocellion, three orders of magnitude speedup over Cortex3D and NetLogo, and the ability to simulate 1.72 billion agents on a single server.

## List of Files


* `SF0-additional-evaluations.pdf`: This document complements the main paper by providing additional performance evaluations.
* `SF1-readme.pdf`: This document provides detailed documentation, step-by-step instructions to reproduce the results, and ideas on how to reuse and repurpose this artifact.
* `SF2-code.tar.gz`: This archive contains all the necessary code to produce all results shown in the paper.
* `SF3-bdm-publication-image.tar.gz`: This archive contains a self-contained docker image to simplify executing our benchmarks and aid long-term reproducibility.
* `SF4-raw-results.tar.gz`: This archive contains the raw results we obtained when we executed the benchmarks on our systems.

>**Warning**
>Due to Github's file size limitations, the files `SF2-code.tar.gz` and `SF3-bdm-publication-image.tar.gz` are exclusively hosted on Zenodo: [https://doi.org/10.5281/zenodo.7544675](https://doi.org/10.5281/zenodo.7544675).

## License Information

License information for the code repositories in `SF2-code.tar.gz` can be found in the files:

* `biodynamo/LICENSE`
* `bdm-paper-examples/LICENSE`

## Getting Started

Setting up a new system requires four steps.
More details can be found in Section 2 in `SF1-readme.pdf`.

1. Download and extract the code archive in Supplementary File SF2.
2. Install the following software packages on the host machine: 
    Docker (version >= 19.0.3), 
    Intel Vtune sampling driver (version 2022.2.0),
    and the Linux `screen` command.
3. Load the docker image provided by Supplementary File SF3.
4. Verify the setup by executing the following command in the `bdm-paper-examples` directory:
    `docker/run.sh ./run-functional-evaluation.sh`

## Reproducing Results

We separate the benchmarks into multiple scripts with different memory and disk space requirements to allow researchers with less powerful hardware to execute a subset of benchmarks.
To execute one of the scripts below, change into the `bdm-paper-examples` directory, and pass the script as a parameter to the command `docker/run.sh`.
More details can be found in Section 4 in `SF1-readme.pdf`.

* `run-main.sh`:
  This script executes the majority of benchmarks described in the evaluation section of the
  paper and outputs Figure 5 (left) and Figures 9--12.

* `run-comparison-with-others.sh`:
This script executes the comparison of BioDynaMo with Cortex3D and NetLogo and outputs 
Figure 8.

* `run-runtime-complexity.sh`:
This script analyses the runtime and memory consumption of BioDynaMo, with the number
of agents increasing from $10^3$ to $10^9$, and generates
Figure 6.

* `run-profiling.sh`:
This script performs the microarchitecture analysis for all simulations in Table 1 
  and generates Figure 5 (right).

* `run-biocellion-cmprsn-single-node.sh`:
This script executes the small-scale comparison with Biocellion and the optimization
analysis in Figure 7b (right).

* `run-biocellion-cmprsn-cluster.sh`:
This script executes the large-scale comparison with Biocellion, the optimization analysis in
    Figure 7b (left), and renders the visualization in Figure 7a.

## Reusing and Repurposing the Artifact
Besides reproducing the results, researchers can build upon our artifact in numerous ways.
A non-exhaustive list of possibilities with detailed instructions is given in Section 5 in `SF1-readme.pdf`.
These possibilities include:

* Add additional benchmarks
* Evaluate the effectiveness of additional optimizations
* Evaluate BioDynaMo's performance for additional simulations

## Contact

Please contact us with any feedback or if you need any help building on BioDynaMo.
You can reach us at [lukas.breitwieser@gmail.com](mailto:lukas.breitwieser@gmail.com) and [omutlu@gmail.com](mailto:omutlu@gmail.com).

