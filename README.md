# rp2022

This repository contains the code used in the research project for the Bachelor 
Computer Science and Engineering of Delft University of Technology. The project 
involves benchmarking of several sparse CNN accelerators, the original code 
can be found in the following repositories: 

* https://github.com/google-research/sputnik
* https://github.com/marsupialtail/gpu-sparsert
* https://github.com/Darcy-Chen/Accelerating
* https://github.com/NVIDIA/MinkowskiEngine

## Experiment Environment

* Ubuntu 18.04
* Python >= 3.6.9
* CUDA 11.4 with cuDNN 8.2 and PyTorch 1.9.0 or CUDA 10.2 with cuDNN 8.2 and PyTorch 1.8.1
* GCC >= 7.4.0
* cmake >= 3.1

## Installation

```
 git clone https://github.com/Darcy-Chen/rp2022.git
 cd rp2022
```

To install each library, follow the installation guide in the corresponding directory.