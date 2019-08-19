# OpenPOWER Foundation Solution Builders Group Data
This is a section dedicated to discussion about best practices around hardware configurations.
Hardware Reference Architecture.


## Hardware Reference Architecture
These instructions will get you up and running on your Power9 PPC64LE machine for development and testing purposes.

### Prerequisites
The only prerequisite is you have Power9 PPC64LE hardware like the following:
```
AC922
```

### List of Hardware Related Items
* [Deployment of new hardware](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/Deployment-of-new-hardware.md)
    * [Racking Machine](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/Deployment-of-new-hardware.md#racking-machine)
        * [Power Requirement](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/Deployment-of-new-hardware.md#power-requirements)
        * [Network](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/Deployment-of-new-hardware.md#networking)
        * [OpemBMC / IPMI](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/Deployment-of-new-hardware.md#openbmcipmi)
* [Install of Operating system](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/Install-of-operating-system.md)
    * [Redhat / CentOS](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_rhel_centos.md)
        * [Versions of OS to install](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_rhel_centos.md#versions)
        * [Install on NVMe](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_rhel_centos.mdInstall-of-operating-system.md#install-on-nvme)
        * [RAID Setup](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_rhel_centos.md#raid-setup)
            * [MD](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_rhel_centos.md#md)
    * [Ubuntu](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_ubuntu.md)
        * [Versions of OS to install](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_ubuntu.md#versions)
        * [Install on NVMe](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_ubuntu.md#install-on-nvme)
        * [RAID Setup](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_ubuntu.md#raid-setup)
            * [MD](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_ubuntu.md#md)
            * [ZFS](https://github.com/sullichr/opf_solution_builders_group/blob/master/hardware_information/installing_ubuntu.md#zfs)



## Installing Software
A step by step series of examples that tell you how to get a development env running

### Prerequisites
The only prerequisite is you have Power9 PPC64LE hardware:
```
PPC64LE Machine
```
### List of Software Related Items
* [Available Binaries](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/Available_Binaries.md)
* [How to compile new tools](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [Optimization of tools](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
* [Install Scripts Available](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
* [Install of GPU Software](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [CUDA](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [OpenCV](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [Tensorflow / Keras](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [Caffe](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [PyTorch](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
* [Install Tools for FPGA](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [Deeds..?](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [others...](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
* [Build HPC cluster](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [SLURM](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [SGE](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
* [Build Cloud environment](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)
    * [Openstack](https://github.com/sullichr/opf_solution_builders_group/blob/master/software_information/)



## General Information

Explain how to run the automated tests for this system

## Contributing

Please read the standard policies on github code of conduct, and the process for submitting pull requests.

## Authors

* **Christopher M. Sullivan** - *Initial work* - [sullichr](https://github.com/sullichr)


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Thanks to Linton Ward for all the great discussions.
