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

- cat grub parameter
    - `# cat /proc/cmdline`

- display log
    - `# cat /sys/kernel/debug/dri/0/i915_display_info > xxx_i915_display_info.log`

- change MAC address
    - `# sudo ifconfig eth0 down`
    - `# sudo ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX`
    - `# sudo ifconfig eth0 up`\
    ***below just for ubuntu***
    - `# sudo /etc/init.d/networking stop`
    - `# sudo /etc/init.d/networking restart`
## Ubuntu

### Command note

- Install test kernel: 
    - `# dpkg -i *.deb`

- environment parameter
    - `# gedit /boot/grub/grub.cfg` or ` gedit /etc/default/grub`\
    add parameter at the end of the line which starts with `quite` 

- Check kernel: 
    - `# uname -r`

- Check BIOS version: 
    - `# dmidecode -t 0`

- unzip tar
    - `tar -xvf file.tar`

- cpu status
    - `cat /sys/kernel/debug/pmc_core/package_cstate_show`
## RHEL

### Command note

- Install test kernel:
    - `# rpm -ivh *.rpm`

- environment parameter: 
    - `# gedit /boot/efi/EFI/redhat/grubenv`

- kernel list
    - `# rpm -qa`




