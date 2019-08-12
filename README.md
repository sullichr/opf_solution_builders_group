# OpenPOWER Foundation Solution Builders Group Data

This is a section dedicated to discussion about best practices around hardware configurations.
Hardware Reference Architecture.

## Hardware Reference Architecture

These instructions will get you up and running on your Power9 PPC64LE machine for development and testing purposes. 

### Prerequisites
The only prerequisite is you have Power9 PPC64LE hardware.
```
AC922
```


* [Deployment of new hardware](hardware_information/Deployment-of-new-hardware.md)
    * [Racking Machine](hardware_information/Deployment-of-new-hardware.md#racking-machine)
        * [Power Requirement](hardware_information/Deployment-of-new-hardware.md#racking-machine)
        * [Network](hardware_information/Deployment-of-new-hardware.md#racking-machine)
        * [OpemBMC / IPMI](hardware_information/Deployment-of-new-hardware.md#racking-machine)
* [Install of Operating system](hardware_information/Install-of-operating-system.md)
    * [Redhat / CentOS](hardware_information/Install-of-operating-system.md)
        * [Versions of OS to install](hardware_information/Install-of-operating-system.md)
        * [Install on NVMe](hardware_information/Install-of-operating-system.md)
        * [RAID Setup](hardware_information/Install-of-operating-system.md)
            * [MD](hardware_information/Install-of-operating-system.md)
    * [Ubuntu](hardware_information/Install-of-operating-system.md)
        * [Versions of OS to install](hardware_information/Install-of-operating-system.md)
        * [Install on NVMe](hardware_information/Install-of-operating-system.md)
        * [RAID Setup](hardware_information/Install-of-operating-system.md)
            * [MD](hardware_information/Install-of-operating-system.md)
            * [ZFS](hardware_information/Install-of-operating-system.md)

## Installing Software

A step by step series of examples that tell you how to get a development env running

### Prerequisites
The only prerequisite is you have Power9 PPC64LE hardware.
```
PPC64LE Machine
```

* [Available Binaries](software_information/Available_Binaries.md)
* [How to compile new tools](software_information/)
    * [Optimization of tools](software_information/)
* [Install Scripts Available](software_information/)
* [Install of GPU Software](software_information/)
    * [CUDA](software_information/)
    * [OpenCV](software_information/)
    * [Tensorflow / Keras](software_information/)
    * [Caffe](software_information/)
    * [PyTorch](software_information/)
* [Install Tools for FPGA](software_information/)
    * [Deeds..?](software_information/)
    * [others...](software_information/)
* [Build HPC cluster](software_information/)
    * [SLURM](software_information/)
    * [SGE](software_information/)
* [Build Cloud environment](software_information/)
    * [Openstack](software_information/)



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

