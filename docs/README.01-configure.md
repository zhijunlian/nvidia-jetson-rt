# Configure NVIDIA Jetson TX2 Board

## [HOST] Check for available SSH connection to Jetson TX2
```
# to connect Jetson board
$ ssh nvidia@JETSON_IP_ADDRESS
# to copy files to Jetson board
$ scp setup.txt nvidia@JETSON_IP_ADDRESS:/home/nvidia
```

## [HOST] Copy CUDA/TensorFlow packages to Jetson TX2
```
$ scp $HOME/nvidia/jetpack_download/cuda-repo-l4t-8-0-local_8.0.84-1_arm64.deb nvidia@JETSON_IP_ADDRESS:/home/nvidia
$ scp $HOME/nvidia/jetpack_download/libcudnn6_6.0.21-1+cuda8.0_arm64.deb nvidia@JETSON_IP_ADDRESS:/home/nvidia
$ scp $HOME/nvidia/jetpack_download/libcudnn6-dev_6.0.21-1+cuda8.0_arm64.deb nvidia@JETSON_IP_ADDRESS:/home/nvidia
$ scp $HOME/nvidia/jetpack_download/libcudnn6-doc_6.0.21-1+cuda8.0_arm64.deb nvidia@JETSON_IP_ADDRESS:/home/nvidia
$ scp $HOME/nvidia/jetpack_download/nv-gie-repo-ubuntu1604-ga-cuda8.0-trt2.1-20170614_1-1_arm64.deb nvidia@JETSON_IP_ADDRESS:/home/nvidia
```

## [TARGET] Update Ubuntu packages
```
$ sudo apt update
$ sudo apt upgrade
$ sudo apt autoremove
```

## [TARGET] Install CUDA and TensorFlow
```
$ sudo dpkg -i /home/nvidia/cuda-repo-l4t-8-0-local_8.0.84-1_arm64.deb
$ sudo dpkg -i /home/nvidia/libcudnn6_6.0.21-1+cuda8.0_arm64.deb
$ sudo dpkg -i /home/nvidia/libcudnn6-dev_6.0.21-1+cuda8.0_arm64.deb
$ sudo dpkg -i /home/nvidia/libcudnn6-doc_6.0.21-1+cuda8.0_arm64.deb
$ sudo dpkg -i /home/nvidia/nv-gie-repo-ubuntu1604-ga-cuda8.0-trt2.1-20170614_1-1_arm64.deb
$ sudo apt update
$ sudo apt install cuda-toolkit-8.0
$ sudo apt install tensorrt-2.1.2
# add these commands at the end of `$HOME.profile`
export PATH=/usr/local/cuda-8.0/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64:$LD_LIBRARY_PATH
```
