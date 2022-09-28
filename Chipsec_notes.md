# Chipsec_note

## Preparation 
- Connected to the Internet
- [Download](https://drive.google.com/file/d/1wu6coKgubQrr_IHsBcv-ZVsHE9c5jFju/view?usp=sharing) the Chipsec tool

## For test

### 1. Install latest version Python

- Install the latest version python and with administrator
    ![](https://drive.google.com/u/0/uc?id=1mbzXAXlDCxPE0z1R4e7yAcNa_wvbsRih&export=download)

- Added python to PATH
    ![](https://drive.google.com/u/0/uc?id=1mv825eRbkJndVcw4Gthj8NKuWB7c553F&export=download)

- Colse install window.
    ![](https://drive.google.com/u/0/uc?id=1XLgIx1OiirNP0feLbNMoXCiuliMQOKf6&export=download)
 
### 2. Install "csg_utils" and "chardet"

- Open powershell as administrator
    ![](https://drive.google.com/u/0/uc?id=17OstV7WnH9VZIzdY7D-bXhZ-YgfYkL22&export=download)

- Navigate to csg_utils file directory and install package
     - `cd c:\User\<user>\...\Chipsec_1.8.8\csg_utils-1.5.3`
     - `pip install csg_utils-1.5.3-py3-none-any.whl`
     - `pip install chardet`
    ![](https://drive.google.com/u/0/uc?id=1Re8cZ87iOAF-qF7Q6XYQgapct98Je-uD&export=download)

### 3. Disable signature enforcement

- Open start menu then holding shift key and press "Restart"
    ![](https://drive.google.com/u/0/uc?id=1UIEEmgyFM6Z22xChPgB3m6GR5NQqF4Iz&export=download)
 
- Select Troubleshoot\
    ![](https://drive.google.com/u/0/uc?id=14U3zgCbGhqFXZ12g8n9VqH3MAOcrQ0_0&export=download)

- Select “Advanced options”\
    ![](https://drive.google.com/u/0/uc?id=17B-XIiLbQRvQ_4JYuFpMa5e6htNKQtP0&export=download)

- Click the “Startup Settings” tile
    ![](https://drive.google.com/u/0/uc?id=1I1GS6rOJixmbRwRa0MSzKrqpv3ypIQ4e&export=download)

- Click the “Restart” button to restart your PC into the Startup Settings screen
    ![](https://drive.google.com/u/0/uc?id=11UqHNg3Ztd0S2jjsoHDwOa3OJ6_Kjlpn&export=download)

- Type “7” or “F7” at the Startup Settings screen to activate the “Disable driver signature enforcement” option\
    ![](https://drive.google.com/u/0/uc?id=1I1tV8_THxAX5TfbLD0YnPsWPUx8ZTM5M&export=download)

### 4. Disable core isolation

- Start menu type "core isolation" then disable it
    ![](https://drive.google.com/u/0/uc?id=1yKOuZ4KNdlJa-N938foOnCGgZ-pzTVON&export=download)

### 5. Execute Chipsec_main

- Run powershell as administrator and execute chipsec test.
    - `cd c:\User\<user name>\...\Chipsec_1.8.8\chipsec-1.8.8-main\`
    - `python .\chipsec_main.py > normal.txt`
    - `python .\dell_chipsec_parser.py normal.txt --mode none`

    ![](https://drive.google.com/u/0/uc?id=13EIHPRvN74SzzMzozOUHJ65X7BIy7FPX&export=download)

### 6. check error log form logs floder

- Navigate to the "logs" folder and observe a file in the following format: Chipsec_modelname_modelnumber_biosversion_(servicetag)_InternalName.txt" Rename the file to include the InternalName at end(example: Chipsec_Latitude_5290__1.0.0_(1ZY94M2)_BreckenridgeMLK.txt)  and attach this file to results (Required Data).
    ![](https://drive.google.com/u/0/uc?id=1LTSHFSBD1Nm78-o1FwJzJTPxNr-1ZWAM&export=download)
    
    - note: If time is allocated, address any items in the 'Warnings.txt" (see chipsec TC for more details if needed).


## Build Driver

- note: Complete the above steps to "4. Disable Core Isolation" and continue with the steps below

### 1. Install CHIPSEC Dependencies

- Run powershell as administrator and Install package: pywin32, setuptools, WConio2
    - `cd c:\User\<user name>\...\Chipsec_1.8.8\chipsec-1.8.8-main\`
    - `pip install -r .\windows_requirements.txt`
    ![](https://drive.google.com/u/0/uc?id=1yRaH3IdE3j2UYoig8_GxD4fnTHwKH57S&export=download)

- Install Visual Studio
    - Run "VisualStudioSetup" as administrator
        ![](https://drive.google.com/u/0/uc?id=1EqDLG1ZJrQ8nXK20IPvaSYucoWeXqnW1&export=download)
        
    - Press "continue"
        ![](https://drive.google.com/u/0/uc?id=1Hfoz0V-ZsxA0l0llOA57XPzg4U3DLBYe&export=download)
        
    - Tick "Desktop development with C++" then press "Install"
        ![](https://drive.google.com/u/0/uc?id=1usJbbKqjxxG98ZSrjxHq8p3JBXKKnRo6&export=download)
        
- Install more dependencies option
    - Lunch Visual Studio Installer and select "Modify"
        ![](https://drive.google.com/u/0/uc?id=1C23199HjuGQvIOJJlG61KO6APZZrTRl-&export=download)
        
    - Search "Latest" and Tick item below" than press "Modify"
        - MSVX v143 - VS2022 C++ x64/x86 build tools (Latest)
        - MSVX v143 - VS2022 C++ x64/x86 Spectre-mitigated libs (Latest)
        - MSVX v143 - VS2022 C++ ARM build tools (Latest)
        - MSVX v143 - VS2022 C++ ARM Spectre-mitigated libs (Latest)
        - MSVX v143 - VS2022 C++ ARM64 build tools (Latest)
        - MSVX v143 - VS2022 C++ ARM64 Spectre-mitigated libs (Latest)
        - MSVX v143 - VS2022 C++ ARM64EC build tools (Latest)
        - MSVX v143 - VS2022 C++ ARM64EC Spectre-mitigated libs (Latest)

        ![](https://drive.google.com/u/0/uc?id=1BLohtMX8sP5ZIGTKigVxEW4B4oOBJGzN&export=download)
        

- Install SDK & WDK
    - Run "winsdksetup" as adminitrator and install by defualt
        ![](https://drive.google.com/u/0/uc?id=1aQFWw3XRaGlIIGSVtBgiXKjCwsBE8zdJ&export=download)
        ![](https://drive.google.com/u/0/uc?id=1pz7tA5Qe_nmcTG0-gniZOjJ9JmokW14Y&export=download)
        ![](https://drive.google.com/u/0/uc?id=1xpgIFDcth1BM3E9dQOuh-Na7iDvj4KFP&export=download)
        ![](https://drive.google.com/u/0/uc?id=1yB1Lwr9keGdgQUo-sjspH-PPVxt1yB8j&export=download)
        
    - Run "wdksetup" as administrator and by install default
        ![](https://drive.google.com/u/0/uc?id=1Mo28ubMX_BvDdUnh0sbRB5rE0IUqwMa4&export=download)
        ![](https://drive.google.com/u/0/uc?id=1jS9NW8ZNzm66fXsk1ASoa_R0LmjeDz0G&export=download)
        ![](https://drive.google.com/u/0/uc?id=1Z_iuJIpBqcArwEAY2JAPVFkF7vzxzEgZ&export=download)
        ![](https://drive.google.com/u/0/uc?id=1PzZ7pUw_LU5qCOsytybFXgWsb0K5A5ko&export=download)
        
    - Install VSIX by default
        ![](https://drive.google.com/u/0/uc?id=1dYiwweM7niuZo-7r6ebqwpJSz4MwYXuI&export=download)
        ![](https://drive.google.com/u/0/uc?id=1tg2npVaWjh5Ou1mONMN1j5G__vNy7sRG&export=download)
        ![]()

### 2. Build driver

- Run "Developer powershell for vs 2022" as administrator
    - `cd c:\User\<user name>\...\Chipsec_1.8.8\chipsec-1.8.8-main\driver\win7`
    - `build /p:Platform=x64`
    ![](https://drive.google.com/u/0/uc?id=1CFwLxOLrUmcrjCjJarrEVP5O7p5714Bd&export=download)
    ![](https://drive.google.com/u/0/uc?id=1p90h-N3Jy9yPR5jR5cYVr4Hrc8VInbXv&export=download)
    ![](https://drive.google.com/u/0/uc?id=1Oqd7LyLEodLRKTiSZBkShHKma1LIFyM7&export=download)
    