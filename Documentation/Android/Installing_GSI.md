# 🤖 Installing Android GSI ROMs on Your Fydetab DUO 🚀

> [!NOTE]  
> All the process is described in more detail in this [video - pending]().

Hi there! 👋 In this guide, I'll show you how to install Android AOSP on your Fydetab DUO tablet.

<br>

# 📚 Index
* [🛠️ Prerequisites](#prerequisites)
* [🖥️ 1. Download GSI ROMs](#step1)
* [📲 2. Installing a GSI ROM](#step2)


<br>
<br>

## 🛠️ Prerequisites <a name=prerequisites></a>

- Make sure you have all the files from the Android AOSP prerequisites downloaded: 
    - `DriverAssitant_v5.0`
    - `platform-tools`
    - `RKDevTool_Release_v2.96`

- [Install Android AOSP](/Documentation/Android/Installing_AOSP.md)


<br>

## 🖥️ 1. Download GSI ROMs <a name=step1></a>

- Download a GSI ROM from the [following list](https://github.com/phhusson/treble_experimentations/wiki/Generic-System-Image-(GSI)-list) (choose one that is Android 12 or greater)

- Take into account that the system partion on the Fydetab Duo AOSP is not too big so most of the ROMs that contains Google Apps are too big. I have tried the following ones: 

    - `crDroid-10.5-arm64_bvN-Unofficial.img`
    - `lineage-21.0-20240526-UNOFFICIAL-arm64_bvS.img`



<br>

## 📲 2. Installing a GSI ROM <a name=step2></a>

**Note: If you have installed Android AOSP with Magisk you should know already how to use ADB and Fastboot**

- Boot the tablet into fastboot mode
```
adb.exe reboot recovery
```

- In the tablet move down with the `Vol -` button and select `Enter fastboot` with the `Power` button:

![](/Images/Android/AOSP/fasboot_enter.png)

- Move the GSI ROM you downloaded into the `platform-tools` folder

- Delete `product` partition to create some space
```
fastboot delete-logical-partition product
```

- Flash the GSI ROM
```
fastboot.exe flash system crDroid-10.5-arm64_bvN-Unofficial.img
```
![](/Images/Android/AOSP/flashing_gsi.png)

- Reboot into recovery
```
fastboot.exe reboot recovery
```

- Select `Wipe Data / Factory Reset` and confirm
- Select `Reboot System now`

- Wait until the tablet reboots and enjoy your new ROM