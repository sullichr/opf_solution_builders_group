# Installing Ubuntu

*this is a stub, please fill in with detailed information*

## Ubuntu

### Versions

The Power9 CPU is supported by Ubuntu Server 18.04 and above. Be sure to select the
ppc64el iso from the official Ubuntu download page:

https://ubuntu.com/download/server/power

The Power9 compatible Ubuntu install ISO should have 'ppc64el' in the file name,
for example:

ubuntu-18.04-server-ppc64el.iso

### USB Install

To install with a USB key, insert the key into the front USB port and boot the
machine. Allow time for the system to perform hardware intialization, after
which you should see the OpenBMC console.

The BMC will display a list boot options, which may be local disks if an boot
partition is found on installed hard disks, network boot options, and the
Ubuntu install USB. Use the arrow keys to select the USB disk and hit
enter.

Install Ubuntu Server as you normally would.

### Install on NVME

If your Power9 system has NVME storage devices, these should appear as disks in
the install target selection. If they do not, and your system does have NVME
installed, see the NVME section in this documentation.

The operating system can be installed normally on an NVME device.

### RAID setup

Linux software RAID is supported in Power9 Ubuntu linux. Local disks can be
combined into a RAID at installation time, see this guide for instructions on
installing Ubuntu Server on RAID:

https://help.ubuntu.com/lts/serverguide/advanced-installation.html
