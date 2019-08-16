# Installing NVIDIA drivers and the CUDA Toolkit

Nvidia provides ppcle binaries for both drivers and the CUDA toolkit. You can
Install these using standard package management for Centos and Ubuntu, or
using the install script provided by NVIDIA.

Install scripts and package repositories for the latest CUDA Toolkit versions
can be found at NVIDIA's developer site:

https://developer.nvidia.com/cuda-downloads

Select Linux, ppc64le and your distribution.

## Packages

### RHEL / Centos 7

Select Version 7 and then

rpm (local)

Instruictions for downloading will be provided, for instance for CUDA 10.1 and
NVIDIA Driver 418.87:

wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda-repo-rhel7-10-1-local-10.1.243-418.87.00-1.0-1.ppc64le.rpm
sudo rpm -i cuda-repo-rhel7-10-1-local-10.1.243-418.87.00-1.0-1.ppc64le.rpm
sudo yum clean all
sudo yum -y install nvidia-driver-latest-dkms cuda

This will install all the necessary components, including the NVIDIA driver. A
reboot is recommended.

### Ubuntu 18.04

Select Version 18.04 and then use the provided install instructions:

wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/ppc64el/cuda-ubuntu1804.pin
sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda-repo-ubuntu1804-10-1-local-10.1.243-418.87.00_1.0-1_ppc64el.deb
sudo dpkg -i cuda-repo-ubuntu1804-10-1-local-10.1.243-418.87.00_1.0-1_ppc64el.deb
sudo apt-key add /var/cuda-repo-10-1-local-10.1.243-418.87.00/7fa2af80.pub
sudo apt-get update
sudo apt-get -y install cuda

## Install script

The install script is common to all supported operating systems. From the
website, select runfile (local) as the Installer Type and follow the
instructions.

wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.243_418.87.00_linux_ppc64le.run

sudo sh cuda_10.1.243_418.87.00_linux_ppc64le.run
