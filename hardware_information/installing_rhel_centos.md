# Installing Redhat / Centos

## Redhat / Centos

### Versions

The Power9 CPU is supported by Redhat and Centos versions 7.5 and above.

It is important to select the correct installation iso file for the Power9
architecture, as they differ from the standard ppcle install media.

For Centos, download ISOs from one of the iso mirrors here:

http://isoredirect.centos.org/altarch/7/isos/power9/

The correct ISO will have 'power9' in the filename, for example:

CentOS-7-power9-Everything-1810.iso

For RHEL installs, obtain an 'alt-server' iso from RedHat. Contact RedHat to
ensure that you have a license for the alt-server ppcle64 distribution.

The RedHat ISOs compatible with Power9 will have 'alt-server' in the filename,
for example:

rhel-alt-server-7.6-ppc64le-boot.iso

### USB Install

To install with a USB key, insert the key into the front USB port and boot the
machine. Allow time for the system to perform hardware intialization, after
which you should see the Petitboot console.

Petitboot will display a list boot options, which may be local disks if an boot
partition is found on installed hard disks, network boot options, and the
Centos or RedHat install USB. Use the arrow keys to select the USB disk and hit
enter.

If the installation process freezes, or you see errors, see 'Troubleshooting'
section below.

Install as you normally would by selecting timezone, installtion targets and
software selection.

### Install on NVME

If your Power9 system has NVME storage devices, these should appear as disks in
the install target selection. If they do not, and your system does have NVME
installed, see the NVME section in this documentation.

The operating system can be installed normally on an NVME device.

### RAID setup

Linux software RAID is supported in Power9 Centos/RHEL linux. Local disks can
be combined into a RAID at installation time, see this guide for instructions
on installing Centos/RHEL on RAID:

https://www.thegeekdiary.com/how-to-install-centos-rhel-7-on-raid-1-partition/


### Troubleshooting

If booting the install media results in a freeze with a black screen, or if you
see errors like:

dracut-initqueue[779]: Warning: dracut-initqueue timeout - starting timeout scripts

you may need to edit the install media boot command.

1. boot the system into the Petitboot menu.
2. Select the USB boot device
3. press 'e'
4. Note the UUID of the install media
5. add to the boot command line: `inst.stage2=hd:UUID='UUID'` where 'UUID'
  is the UUID of the install media
6. save
7. select the USB install option and boot
