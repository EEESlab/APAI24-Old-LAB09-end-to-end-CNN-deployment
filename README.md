# [APAI23-LAB09] End-to-end CNN deployment 


# 1. Setup

## Download the repo

Open the usual VM used for the other labs, then:
```
$ cd <work_dir>
$ git clone https://github.com/EEESlab/APAI24-Old-LAB09-end-to-end-CNN-deployment.git --recurse-submodules --shallow-submodules
```

**Note**: make sure to clone with `--recurse-submodules` !

## Setup PULP-SDK and related 

Source:
```
$ source setup_pulp_sdk.sh
```

Install dependencies
```
$ pip install onnx ortools 
```


# 2. How to run the code


#### 1. `cd` to dory directory
   
`$ cd APAI24-Old-LAB09-end-to-end-CNN-deployment/dory`

#### 2. Generate the network

```
$ python network_generate.py Quantlab <target> ../<network>/config.json --perf_layer
```


The `target` can be:

* `PULP.PULP_gvsoc` - 8-core cluster execution
* `PULP.PULP_NE16` - NE16 execution


The `network` can be:

* `Network1` - network with a 3x3 convolution for the last layer

* `Network2` - network with a 5x5 convolution for the last layer

#### 3. Build and run the code

   
`$ make -C application clean all run CORE=8`
