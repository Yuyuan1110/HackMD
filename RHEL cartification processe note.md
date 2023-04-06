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

    - Check the path in KS file are correctly.