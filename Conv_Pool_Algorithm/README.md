# Accelerating convolutional neural network on GPUs

This is a copy of the source code of Accelerating convolutional neural network on GPUs. 

## Installation

```
$ cd Conv_Pool_Algorithm
$ wget https://www.dropbox.com/s/5yeny1wv0ayn481/dataset.zip
$ unzip dataset.zip
```

When running on Jetson using Docker Container, run this before installing:
```
apt-get update
apt-get install -y sudo
sudo apt-get install unzip
```
Change Makefile from /ECR/cudnn and /PECR/cudnn line 37, 245, 246 to match your local cuda path, 
line 251 to match the architecture of the device used

## Usage

To run convolution:

```
$ cd ECR
$ bash run_ecr_comparation.sh
```

To run convolution and max pooling by the fellow steps:
```
$ cd PECR
$ bash run_pecr_comparation.sh
```

The dataset used contains the input matrix and is stored as text files. 
To test the library with your own input, put the shape of the matrices in conv_shape and the name of the matrix files in file_list.
