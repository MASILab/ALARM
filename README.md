# ALARM: automatic liver attenuation estimation
###  [[project page]](https://github.com/MASILab/ALARM/)  

The liver attenuation estimations can be achieved from a single CT abdomen scan
<img src="https://github.com/MASILab/ALARM/blob/master/screenshot/Figure1.jpg" width="600px"/>

It has been implemented as a single Docker.
```diff
+ The code and docker are free for noncommercial purposes.
+ The licence.md shows the terms for commercial and for-profit purposes.
```

## Quick Start
#### Get our docker image
```
sudo docker pull masidocker/spiders:liver_attenuation_v1_0_1
```
#### Run SLANT brain segmentation
You can run the following command or change the "input_dir", then you will have the final segmentation results in output_dir
```
# you need to specify the input directory
export input_dir=/home/input_dir   
# make that directory
sudo mkdir $input_dir
# put dicom images to the input_dir
# set output directory
export output_dir=$input_dir/output
#run the docker
sudo nvidia-docker run -it --rm -v {input path}:/INPUTS/ -v {output path}:/OUTPUTS masidocker/spiders:liver_attenuation_v1_0_1 /extra/run_deep_wholebody.sh
```


## Detailed envrioment setting  

#### Testing platform
- Ubuntu 16.04
- cuda 8.0
- Pytorch 0.2
- Docker version 1.13.1-cs9
- Nvidia-docker version 1.0.1 to 2.0.3


#### install Docker
```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce
```

#### install Nvidia-Docker
```
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update
sudo apt-get install -y nvidia-docker2
```


