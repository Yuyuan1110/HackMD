# Chipsec_note

## Press [THERE](https://drive.google.com/file/d/1wu6coKgubQrr_IHsBcv-ZVsHE9c5jFju/view?usp=sharing)  to download Chipsec tool
## 1. Install latest version Python

- Install the latest version python and with administrator
![](https://drive.google.com/u/0/uc?id=1mbzXAXlDCxPE0z1R4e7yAcNa_wvbsRih&export=download)

- Added python to PATH
![](https://drive.google.com/u/0/uc?id=1mv825eRbkJndVcw4Gthj8NKuWB7c553F&export=download)

- Colse install window.
 ![](https://drive.google.com/u/0/uc?id=1XLgIx1OiirNP0feLbNMoXCiuliMQOKf6&export=download)
 
## 2. Install "csg_utils" and "chardet"

- Open powershell as administrator
![](https://drive.google.com/u/0/uc?id=17OstV7WnH9VZIzdY7D-bXhZ-YgfYkL22&export=download)

- Navigate to csg_utils file directory and install package
     - `cd c:\User\<user>\...\Chipsec_1.8.8\csg_utils-1.5.3`
     - `pip install csg_utils-1.5.3-py3-none-any.whl`
     - `pip install chardet`
![](https://drive.google.com/u/0/uc?id=1Re8cZ87iOAF-qF7Q6XYQgapct98Je-uD&export=download)

## 3. Disable signature enforcement

- Open start menu then holding shift key and press "Restart"
![](https://drive.google.com/u/0/uc?id=1UIEEmgyFM6Z22xChPgB3m6GR5NQqF4Iz&export=download)
 
- Select Troubleshoot  
![](https://drive.google.com/u/0/uc?id=14U3zgCbGhqFXZ12g8n9VqH3MAOcrQ0_0&export=download)

- Select “Advanced options”  
![](https://drive.google.com/u/0/uc?id=17B-XIiLbQRvQ_4JYuFpMa5e6htNKQtP0&export=download)

- Click the “Startup Settings” tile
![](https://drive.google.com/u/0/uc?id=1I1GS6rOJixmbRwRa0MSzKrqpv3ypIQ4e&export=download)

- Click the “Restart” button to restart your PC into the Startup Settings screen

![](https://drive.google.com/u/0/uc?id=11UqHNg3Ztd0S2jjsoHDwOa3OJ6_Kjlpn&export=download)

- Type “7” or “F7” at the Startup Settings screen to activate the “Disable driver signature enforcement” option  
![](https://drive.google.com/u/0/uc?id=1I1tV8_THxAX5TfbLD0YnPsWPUx8ZTM5M&export=download)

## 4. Disable core isolation

- Start menu type "core isolation" then disable it
![](https://drive.google.com/u/0/uc?id=1yKOuZ4KNdlJa-N938foOnCGgZ-pzTVON&export=download)

## 5. Execute Chipsec_main

- Run powershell as administrator and execute chipsec test.
    - `cd c:\User\<user name>\...\Chipsec_1.8.8\chipsec-1.8.8-main\`
    - `python .\chipsec_main.py > normal.txt`
    - `python .\dell_chipsec_parser.py normal.txt --mode none`
![](https://drive.google.com/u/0/uc?id=13EIHPRvN74SzzMzozOUHJ65X7BIy7FPX&export=download)

## 6. check error log form logs floder

- Navigate to the "logs" folder and observe a file in the following format: Chipsec_modelname_modelnumber_biosversion_(servicetag)_InternalName.txt" Rename the file to include the InternalName at end(example: Chipsec_Latitude_5290__1.0.0_(1ZY94M2)_BreckenridgeMLK.txt)  and attach this file to results (Required Data).
![](https://drive.google.com/u/0/uc?id=1LTSHFSBD1Nm78-o1FwJzJTPxNr-1ZWAM&export=download)
        - note: If time is allocated, address any items in the 'Warnings.txt" (see chipsec TC for more details if needed).
        
