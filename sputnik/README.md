# Sputnik

Sputnik is a library of sparse linear algebra kernels and utilities for deep learning.

## Build

The test and benchmark suites additionally depend on [abseil/abseil-cpp](https://github.com/abseil/abseil-cpp), [google/googltest](https://github.com/google/googletest), and [google/benchmark](https://github.com/google/benchmark). These dependencies are includes as submodules in [third_party](https://github.com/google-research/sputnik/tree/os-build/third_party). To build the test suite and/or benchmark suite, set `-DBUILD_TEST=ON` and/or `-DBUILD_BENCHMARK=ON` in your `cmake` command.
To install the third party libraries: 
```
cd sputnik
cd third_party
rm -rf abseil-cpp
git clone https://github.com/abseil/abseil-cpp.git
rm -rf benchmark
git clone https://github.com/google/benchmark.git
rm -rf googletest
git clone https://github.com/google/googletest.git
```

Sputnik uses the CMake build system. Sputnik depends on the CUDA toolkit (v10.1+) and supports SM70+. The only additional dependency for the library is [google/glog](https://github.com/google/glog). To build the library, enter the project directory and run the following commands:
Match the -DCUDA_ARCHS with your GPU archtecture

`mkdir build && cd build`

`cmake .. -DCMAKE_BUILD_TYPE=Release`

`make -j12`

`cmake .. -DCMAKE_BUILD_TYPE=Release -DBUILD_TEST=ON -DBUILD_BENCHMARK=ON -DCUDA_ARCHS="80"`

## Docker

Sputnik provides a [Dockerfile](https://github.com/google-research/sputnik/blob/os-build/Dockerfile) that builds the proper environment with all dependencies. Note that [nvidia-docker](https://github.com/NVIDIA/nvidia-docker) must be installed to run on GPU. To build the image, run the following command:

`docker build . -t sputnik-dev`

To launch the container with the sputnik source mounted under `/mount` (assuming you're working out of $HOME), run the following:

`sudo docker run --runtime=nvidia -v ~/:/mount/ -it sputnik-dev:latest`

## Usage
- To benchmark the spmm, run `./spmm_benchmark`, you can change the shape and sparsity of the matrix in '/spmm/spmm_benchmark.cu.cc', similar for other calculations.
- To export the matrices used for the benchmarking to csv files, add the following code to line 432 in 'matrix.utils.cu.cc', include <iostream> and include <fstream>
```
      std::ofstream myfile;
      myfile.open ("example.csv");
      for (int i = 0; i < num_elements_with_padding_; i++) {
          myfile << values_[i] << ' ';
      }
      myfile.close();
```
