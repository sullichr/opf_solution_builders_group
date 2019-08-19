# GPU pass-through for PPC64le VMs

This guide provides instructions for running KVM virtual machines on a Power9
system with GPU passthrough. The result will be vone or more virtual machines
that each have access to one or more GPU devices on the host.

This procedure was carried out on a Centos 7.5 system with kernel 4.14.0

> **IMPORTANT** this guide assumes that NVIDIA drivers have not been installed
> on the host. All graphic drivers that might claim the GPU device must be
> removed prior to creating VMs. If NVIDIA drivers are installed, uninstall
> them and make sure no `nvidia` modules are loaded.

## Overview

* Add the ``vfio-pci.disable_idle_d3=1`` parameter to the kernel in grub.cfg
* Turn off SMT
* Blacklist the nouveau module
* Rebuild the initramfs
* Reboot and check that nouveau is not loaded
* Find the PCI ids of the GPUS
* Insert the GPU into the VM as a host device

## Add the kernel parameter

In `/boot/grub2/grub.cfg`, create a new menuentry by copying the entry for
the kernel you plan to boot, and add `vfio-pci.disable_idle_d3=1` to the
kernel line for the new entry.

In this example, I simply appended '- testing' to the primary menu entry title


```
menuentry 'CentOS Linux (4.14.0-49.10.1.el7a.ppc64le) 7 (AltArch) - testing' --class centos --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-4.14.0-49.el7a.ppc64le-advanced-800c95d4-65ea-41c6-af9a-8dad6213a597' {
        load_video
        insmod gzio
        insmod part_msdos
        insmod xfs
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-ieee1275='ieee1275//pciex@3fffe40500000/pci@0/pci@0/pci@2/sata@0/disk@0,msdos2' --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  4d574a87-ece1-476c-8102-23df7ba53d35
        else
          search --no-floppy --fs-uuid --set=root 4d574a87-ece1-476c-8102-23df7ba53d35
        fi
        linux /vmlinuz-4.14.0-49.10.1.el7a.ppc64le root=/dev/mapper/centos-root ro crashkernel=auto rd.lvm.lv=centos/root rd.lvm.lv=centos/swap rhgb quiet LANG=en_US.UTF-8 vfio-pci.disable_idle_d3=1
        initrd /initramfs-4.14.0-49.10.1.el7a.ppc64le.img
}
```

Note where the kernel parameter is added:

```
linux /vmlinuz-4.14.0-49.10.1.el7a.ppc64le root=/dev/mapper/centos-root ro crashkernel=auto rd.lvm.lv=centos/root rd.lvm.lv=centos/swap rhgb quiet LANG=en_US.UTF-8 vfio-pci.disable_idle_d3=1
```


>  If you want create a new initrd image with a different name below, be sure
>  to also change the `initrd` line in the menu entry.


## Turn off SMT


This disables symmetry multithreading, which interfers with isolating the GPU
device. Use the `ppc64_cpu` command for this:

```bash
$ ppc64_cpu --smt=off
```

## Blacklist the nouveau module

Create a file `/etc/modprobe.d/blacklist-nouveau.conf` with these contents:

```
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
```

## Rebuild the initrd

For Red Hat based distros, the ``dracut`` command does this. It may not be
necessary, but I have explicitly disabled the nouveau module in the initrd
while rebuilding.


> **CAUTION**  This command will over-write your exisiting initrd, unless you
> specify a different name or kernel. I simply backed up the existing initrd
> and let it over-write.

```bash
$ cp /boot/initramfs-4.14.0-49.10.1.el7a.ppc64le.img /boot/initramfs-4.14.0-49.10.1.el7a.ppc64le-bak.img

$ dracut -fv --omit-drivers nouveau
```

This will create a new `/boot/initramfs-4.14.0-49.10.1.el7a.ppc64le.img`

If you want to make the previous known-good configuration a grub menu entry
for easy recovery if something goes wrong, rename your initrd images and update
the grub menu entries appropriately.


## Reboot and check that nouveau is not loaded


```bash
$ reboot
<after reboot>
$ lsmod | grep nouveau
$
```

You should see no nouveau module listed.

> NOTE: this is a good time to verify there are no NVIDIA driver modules loaded

```bash
$ lsmod | grep nvidia
$
```

## Find the PCI ids of the GPUS

```bash
$ lspci -nn | grep -i nvidia
0002:01:00.0 3D controller [0302]: NVIDIA Corporation GP100GL [Tesla P100 SXM2 16GB] [10de:15f9] (rev a1)
000a:01:00.0 3D controller [0302]: NVIDIA Corporation GP100GL [Tesla P100 SXM2 16GB] [10de:15f9] (rev a1)
```

The number in the first column contains  ``<domain>:<bus>:<slot>.<function>``


## Insert the GPU into the VM as a host device


For this example, I used libvirt to create a KVM virtual machine, then edited
its XML definition to insert the host device identified by the device id
above. Insert this block somewhere in the ``<devices>`` block.

```xml
<hostdev mode='subsystem' type='pci' managed='yes'>
  <source>
    <address domain='0x0002' bus='0x01' slot='0x00' function='0x0'/>
  </source>
  <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
</hostdev>
```

Make sure the domain, bus, and slot numbers in the `<source>` block
correspond to the ids you found above. In the ``<address>`` line outside of
the `<source>` block, make sure the domain, bus, and slot numbers are unique
in this file, i.e. no other defined PCI devices in the file share them.

## Start your VM


Start up the VM, you should see the GPU in the VM as a PCI device


```bash
[root@power-gputest ~]# lspci -nn | grep -i nvidia
00:06.0 3D controller [0302]: NVIDIA Corporation GP100GL [Tesla P100 SXM2 16GB] [10de:15f9] (rev a1)
```

Install nvidia-drivers and CUDA toolkit in your VM.
