# TensorRT

## Usage 
- Download the model from https://catalog.ngc.nvidia.com/orgs/nvidia/teams/tao/models/trafficcamnet
- Install TAO Toolkit following https://docs.nvidia.com/tao/tao-toolkit/index.html and download the computer vision samples
- Run interactive TAO session using `tao detectnet_v2`
- To download the dataset from KITTI, follow the instruction in 'cv_samples_v1.2.0/detectnet_v2/detectnet_v2.ipynb'
- To run inference using the unpruned model: 
```
detectnet_v2 inference -e unpruned_config.txt \
                            -o  result \
                            -i data/testing/image_2 \
                            -k tlt_encode
```
- To convert the model for using TensorRT:
```
converter resnet18_trafficcamnet_pruned.etlt \
                   -c trafficcamnet_int8.bin \
                   -k tlt_encode\
                   -o output_cov/Sigmoid,output_bbox/BiasAdd \
                   -d 3,384,1248 \
                   -i nchw \
                   -m 64 \
                   -e  resnet18_trafficcamnet_pruned.trt \
                   -b 4
```
- To run inference using the pruned model:
```
detectnet_v2 inference -e pruned_traffic_config.txt \
                            -o  result \
                            -i data/testing/image_2 \
                            -k tlt_encode
```