# pxe server on RHEL 8.6 (UEFI BOOT)
## 1. Prepare in advence
- RHEL-8.6.iso
- [pxe_server_tool](https://drive.google.com/drive/folders/1nUmIxL-zn5wUfNFQZ3LV3Mht7_B7qtL2?usp=sharing)
- target iso (e.g. RHEL-8.6.iso)
- USB falsh deivce
## 2. BIOS Setting Check
- Upgrade the BIOS to the latest stable version.
- Load the BIOS default setting, check follow BIOS settings:
    - General-> System Configuration -> SATA Operation:
        - For Desktop: Only support **AHCI/NVME** option.
        - For Laptops: Support both **AHCI/NVME** and RAID ON options.
    - Boot Configuration -> Enable Secure Boot: Turn Off

## 3. USB Drive Flash Tool: Rufus
- [Download the latest version Rufus](https://rufus.ie/en_IE.html)
- Open the tool, select the RHEL 8.6 ISO image. Keep the resting options as default setting and click START.\
 ![](https://drive.google.com/u/0/uc?id=1OKX1-vuUhKPp92q74B09jj5MvsoQaHGa&export=download)

- Select Write in DD Image mode, click Ok.\
 ![](https://drive.google.com/u/0/uc?id=1Ioh46KeJnqTPbccnc0uOFIptHEviU4Io&export=download)
- Complete the RHEL ISO image burn process.
## 4. Installation Steps:
- Download the RHEL 8.6 ISO image from SWB and burn the ISO image to the USB stick.
- Boot up the system with the USB stick.
- Select “**Install Red Hat Enterprise Linux 8.6**” and press “**E**”.
- Add follow parameter at the end of the line which starts with “**linuxefi**” and press “***ctrl + x***” to continue.\
`xdrv=vesa nomodeset`
- For the language selection page, keep default as follow and click **Continue**.
- Select **Software Selection**, choose “***Workstation***” and check “***Development Tools***” as Add-Ons Packages.
- Select **Installation Destination** and create your partition table or created automatically.
- Select **Root Password** to set the root password.
- Select **User Creation** to setup a user account.
- Keep the rest settings as default and Click **Begin Installation**.
    - Complete the installation and click **Reboot System**.

- Edit boot grub parameter:
    - `# gedit /boot/efi/EFI/redhat/grubenv`
    - Delete `nomodeset`
    - For RKL-S platforms, add `i915.force_probe=*` at the end of the line which starts with `kernelopts=root `
- **Reboot** the system to complete the OS installation

## 5. Mount the NTFS driver and copy ISO to server
- Open terminal with root then cd to pxe_server_tool
    - `# cd /home/user/pxe_server_tool/`
- Enable NTFS support
    - `# rpm -i fuse-ntfs-3g-2013.1.13-2.el7.rf.x86_64.rpm`\
    you can W/R NTFS format now, then copy ISO to path `/home/user/`

## 6. Connect LAN and set IPv4
- Tick "Connect automatically"
![](https://drive.google.com/u/0/uc?id=1pAZUmqLDbylrfUx7nalpQfuHJxL4kcH3&export=download)

- Set IPv4 Adderss: "192.168.1.101"  Netmask: "255.255.255.0"  Getway: "192.168.1.1"
![](https://drive.google.com/u/0/uc?id=1T49aJOL1j5kX6v6tvxy8iOFTiT_z2jDJ&export=download)

- Press and re-start network.

## 7. Install tools PXE_server need
- Copy iso to path:/home/user/ then mount to path:/media
    - `mount rhel.iso /media`
- Copy [pxe_server_tool](https://drive.google.com/drive/folders/1nUmIxL-zn5wUfNFQZ3LV3Mht7_B7qtL2?usp=sharing) to path:/home/user/ ,then enter pxe_server_tool directory 
    - `cd /home/user/pxe_server_tool`
- Start bash code to auto build server
    - `sh build_pxe_server.sh`

## If need add other ISO please refernce the [document](https://drive.google.com/drive/folders/19PM4ijwSxGq0FABkFv1RyKVU__9-1JZs?usp=sharing)


### DTM path: /var/www/html/rhel/debuginfo/

### kernel path: /var/www/html/rhel/x86_64/BaseOS/Packages/

### repoindate: createrepo ./ -p
