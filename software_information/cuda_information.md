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

Instructions for downloading will be provided, for instance for CUDA 10.1 and
NVIDIA Driver 418.87:

```bash
$ wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda-repo-rhel7-10-1-local-10.1.243-418.87.00-1.0-1.ppc64le.rpm
$ sudo rpm -i cuda-repo-rhel7-10-1-local-10.1.243-418.87.00-1.0-1.ppc64le.rpm
$ sudo yum clean all
$ sudo yum -y install nvidia-driver-latest-dkms cuda
```

This will install all the necessary components, including the NVIDIA driver. A
reboot is recommended.

### Ubuntu 18.04

Select Version 18.04 and then use the provided install instructions:

```bash
$ wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/ppc64el/cuda-ubuntu1804.pin
$ sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
$ wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda-repo-ubuntu1804-10-1-$ $ local-10.1.243-418.87.00_1.0-1_ppc64el.deb
$ sudo dpkg -i cuda-repo-ubuntu1804-10-1-local-10.1.243-418.87.00_1.0-1_ppc64el.deb
$ sudo apt-key add /var/cuda-repo-10-1-local-10.1.243-418.87.00/7fa2af80.pub
$ sudo apt-get update
$ sudo apt-get -y install cuda
```

## Install script

The install script is common to all supported operating systems. From the
website, select runfile (local) as the Installer Type and follow the
instructions.

```bash
$ wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/ cuda_10.1.243_418.87.00_linux_ppc64le.run
$ sudo sh cuda_10.1.243_418.87.00_linux_ppc64le.run
```

## Testing

Check to make sure the nvidia driver is loaded:

```bash
$ lsmod | grep nvidia
nvidia_uvm            959025  0
nvidia_drm             54094  0
nvidia_modeset       1258758  1 nvidia_drm
nvidia              17483267  2 nvidia_modeset,nvidia_uvm
drm_kms_helper        182400  2 ast,nvidia_drm
drm                   453521  5 ast,ttm,drm_kms_helper,nvidia_drm
ipmi_msghandler        51075  3 ipmi_powernv,ipmi_devintf,nvidia
```

Mext run `nvidia-smi`, which will display information about the devices seen
by the nvidia driver:

```bash
$ nvidia-smi
Fri Aug 16 15:09:26 2019
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 418.67       Driver Version: 418.67       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Tesla V100-SXM2...  On   | 00000004:04:00.0 Off |                    0 |
| N/A   33C    P0    35W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   1  Tesla V100-SXM2...  On   | 00000004:05:00.0 Off |                    0 |
| N/A   35C    P0    36W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   2  Tesla V100-SXM2...  On   | 00000035:03:00.0 Off |                    0 |
| N/A   32C    P0    36W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
|   3  Tesla V100-SXM2...  On   | 00000035:04:00.0 Off |                    0 |
| N/A   36C    P0    36W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```
