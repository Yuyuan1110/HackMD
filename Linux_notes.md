# Linux note

## common use command

### Command note
- Thunderbolt devices
    - `# boltctl`

- Check PCI
    - `# lspci`

- Chack BT address
    - `# hcitool dev`

- SOS report
    - `# sosreport`

- display log
    - `# cat /sys/kernel/debug/dri/0/i915_display_info > xxx_i915_display_info.log`

- change MAC address
    - `# sudo ifconfig eth0 down`
    - `# sudo ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX`
    - `# sudo ifconfig eth0 up`\
    ***below just for ubuntu***
    - `# sudo /etc/init.d/networking stop`
    - `# sudo /etc/init.d/networking restart`

- Check BIOS version: 
    - `# dmidecode -t 0`

- Check Memory:
    - `# free -m`
## Ubuntu

### Command note

- Install test kernel: 
    - `# dpkg -i *.deb`

- environment parameter
    - `# vim /boot/grub/grub.cfg` or ` gedit /etc/default/grub`\
    add parameter at the end of the line which starts with `quite` 
    
    the other method
    - `# vim /etc/default/grub `
    - `# update-grub`

- Check kernel: 
    - `# uname -r`

- unzip tar
    - `tar xvf file.tar.gz`

- cpu status
    - `cat /sys/kernel/debug/pmc_core/package_cstate_show`

- check WWAN state
    - `mmcli -m 0`

- set signature trust to false
    -  `sudo vim /etc/fwupd/daemon.conf`
## RHEL

### Command note

- Install test kernel:
    - `# rpm -ivh *.rpm`

- environment parameter: 
    - `# gedit /boot/efi/EFI/redhat/grubenv`

- kernel list
    - `# rpm -qa`

- cat grub parameter
    - `# cat /proc/cmdline`

- check UUID
    - `# blkid`

- How to fix A start job is running for /dev/disk/by-uuid/[partition uuid]
    - `# vim /etc/fstab`
    - replace UUID in "swap" line with that show in blkid.

## Chromebook

### Command note


### 




