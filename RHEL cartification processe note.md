# RHEL cartification processe note


- ## Prepare in advence

    1. Download **cert tool** and **KS file** from DELL contact partner or project owner and copy them to your storage device.
        ![](https://drive.google.com/u/0/uc?id=1vmXqGqvyuzUaxIeekj-vYWb9huXt3_ip&export=download)
        
        ****note: please used latest version cert tool to do test, cert tool requires an update at least every three months***

    2. Get the [cert plan](https://drive.google.com/drive/folders/1fZv0OvV9PspJNC5exRYGg1QmrkmUtv3H?usp=share_link) from DELL contact partner or project owner
    
- ## Deploying RHEL cert environment base on Pxe-Boot server 

    - Rename "certTool" and "kernel-debuginfo" floder to "rhcert-x86_64" and "debuginfo" then copy to path: "/var/www/html/*[rhel]*/"
        ![](https://drive.google.com/u/0/uc?id=13_NNWEMHCOC_yoNA-klE_Zde9Of2yC5W&export=download)
    - Command `createrepo -p .` to create repodate: 
        ![](https://drive.google.com/u/0/uc?id=10VT_IB8LEbP9sCLkxCs3kkAU7F0bOs-P&export=download)

    - Check the path in KS file are correct.
        ![](https://drive.google.com/u/0/uc?id=1Ihu-t5Y0WygtCVQMkNzI8tX0DsbwpmAb&export=download)
        
        ![](https://drive.google.com/u/0/uc?id=1-ijEERiuLrcFfktfkM3ZvArrJ8oGX9cP&export=download)
        
        ![](https://drive.google.com/u/0/uc?id=16yKbD-S1zIyB301n0iK9XdhvMvRxJjpc&export=download)
    - Check that the boot menu selection settings are correct
        ![](https://drive.google.com/u/0/uc?id=1bxNgiIGmY6B96ri70aIj16C1YB81tkWo&export=download)
    
    
    

- ## Start certification on SUT
    - Before testing, please delete "nomodeset" in grub and update.
    - Red Hat certification CLI(rhcert-cli) command allows partners to run tests in interactive mode. To run the certification tests using Red Hat Certification CLI, execute the following commands on the image under-test:  
    `# rhcert-cli`
    `# rhcert-ci`
    
    - Following command can check test plan and path:  
    `# rhcert-cli plan`  
    `# rhcert-ci plan`
    ![](https://drive.google.com/u/0/uc?id=1fMtvTGAUX2_ASsFfzXksptR6wrplbvuN&export=download)
    
    - Start test with following command:  
        - e.g.: `# rhcert-cli run --test=hwcert/core`
    
    - Some test request parameter: `--device` or `--server`  
        - e.g.: `#rhcert-cli run --test=hwcert/storage/PCIE_NVMe --device=nvme0n1`   
        - e.g.: `#rhcert-cli run --test=hwcert/network/wlan/WirelessAC --device=wlp0s20f3 --server=192.168.1.113`
    
    - Add plan to test:  
        - e.g. Add WirelessAX test:`# rhcert-cli plan --add --test=hwcert/network/wlan/WirelessAX --device=wlp0s20f3 --server=192.168.1.113`  
        
        - e.g. Add video test of NV with UDI: `# rhcert-cli plan --add --test=video --property --udi=/devices/pci0000:00/0000:00:01.0/0000:01:00.0`  
        *You will be prompted to answer the following questions, please anser as follows:*  
        ![](https://drive.google.com/u/0/uc?id=1EMisdjVJJN-pPUrHYRPZM1F5kBUqbriB&export=download)  
        *Then you can see the test have been add to the test plan:*
        ![](https://drive.google.com/u/0/uc?id=1uIPZdQqGgl0nTJFt-5uyjueKVmtwtWb3&export=download)
        
        - e.g. Add Audio test with devide: `# rhcert-cli plan --add --test=audio --property --device=internal`  
        *audio device UDI: /devices/pci0000:00/0000:00:1f.3/sof_sdw/sound/card0*
    
    - Save the log:
        - After complete the every each test that need to save the log then clean it:  
        `# rhcert-cli save`  
        `# rhcert-cli clean`  
        *Please save log to folder and rename to test item name.*
        
### For Fv_test, please start virtqemud service and run `#virsh list`, if it doesn't give any error then run fv test.
`#systemctl start virtqemud`

#### **And put hwcert-image to /var/www/rhcert/store/transfer/fv-images/RHEL9/**


1.	Delete the below files in HUT/SUT if they are present.  
2.	`#rm -rf /var/lib/libvirt/images/hwcertData.img`  
`#rm -rf /etc/libvirt/qemu/hwcert-x86_64.xml`
3.	Extract the required images at "/var/lib/libvirt/images/"  
`#tar xmvfj hwcertData.img.tar.bz2`  
`#tar xmvfj hwcert-x86_64.img.tar.bz2`  
4.	Rename the files and restore the SELinux context
`#mv hwcertData-RHCERTIFICATION-1-updates-RHEL-8-20220222.0.img hwcertData.img`
`#mv hwcert-image-8.4-195.x86_64.qcow2 hwcert-x86_64.img`  
`#/sbin/restorecon -v hwcertData.img`  
`#/sbin/restorecon -v hwcert-x86_64.img`  

5. Replace the "hwcert-x86_64.xml" file at "/etc/libvirt/qemu/.And activate the default network with this command `#virsh net-start default`.

**if the command didn't working normally, check the log what if it show "error creating bridge interface virbr0 file exists", command `#sudo ip link delete virbr0` and retry `#virsh net-start default`.**