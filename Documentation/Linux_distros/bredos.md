# 🍞 BredOS (Arch Linux ARM)


Hi there! 👋 In this guide, I'll show you how to install BredOS Fydetab DUO tablet. This is the best working Linux distro in the Fydetab. Thanks to [Panda](https://github.com/Rippanda12) for her development

![](/Images/Linux/BredOS/preview.jpg)

<br>

# 📚 Index
* [🛠️ Prerequisites](#prerequisites)
* [🖥️ 1. Installing BredOS](#step1)
* [📦 2. Installing Fydetab packages / OTA updates](#step2)
* [⚙️ Go back to FydeOS or standard images](#step3)


<br>
<br>

## 🛠️ Prerequisites <a name=prerequisites></a>

**Before we begin, make sure you have the following files downloaded:**

- [Rockchip Driver](https://dl.radxa.com/tools/windows/DriverAssitant_v5.0.zip)

- Flashing tool **(RKDevTool vX.XX)**: You can download the tools for Linux and Mac from the official [Fydetab Duo Wiki](https://wiki.fydetabduo.com/flashing_the_fydetab_duo#utilising-the-image-flash-tool-provided-by-rockchip). For Windows you can use the last available version 
    - [Link](https://docs.radxa.com/en/compute-module/cm5/radxa-os/low-level-dev/rkdevtool)
    - [Alternative in case `Link 1` doesn't work](https://dl.radxa.com/tools/windows/)
    - [Link to version v2.96](https://dl.radxa.com/tools/windows/RKDevTool_Release_v2.96_zh.zip)

- [`rk3588_spl_loader_v1.15.113.bin` file (or the last one available)](https://dl.radxa.com/rock5/sw/images/loader/rk3588_spl_loader_v1.15.113.bin)

- [BredOS image (the file we are going to flash)](https://repo.bredos.org/). Select the last one available: 

**Unzip all files including the Linux image which by default comes in an .img.xz file and we have to unzip it to make it an .img file. You should have this:**

![](/Images/Linux/BredOS/download_image_from_repo.png)



<br>

## 🖥️ 1. Installing BredOS <a name=step1></a>

> [!NOTE]
> The only thing that doesn't work right now in BredOS is the fingerprint reader and the sleep mode (you have to turn off the device).

- The first thing to do is installing the Rockchip Driver we have downloaded. For this, open the `DriverAssitant_v5.0` folder and execute the file `DriverInstall.exe`.

- Click on `Install Driver`:

![](/Images/Android/AOSP/install_drivers.png)

- Open the folder that contains the flashing tool:  `RKDevTool_Release_v2.96` folder (check the version you have downloaded for the name) and execute the tool `RKDevTool.exe`.

- In the flashing tool set the following configuration and click on `RUN`: 
    - Select the SPI loader file
    - Select the BredOS image
    - Check `Write by Address`
    - Click on `RUN` and wait until the process finishes

![](/Images/Linux/BredOS/flashing_tool_config.png)


<br>

## 📦 2. Installing Fydetab packages / OTA updates <a name=step2></a>

After the tablet boots into BredOS follow the Bred installer and configure a new user. 

![](/Images/Linux/BredOS/bredOS_installer.jpg)


When you have the basic setup configured execute the following commands in the terminal to have everything working fine in the Fydetab: 

```
sudo pacman -Syu fydetabduo-post-install
reboot
```

Wait until the tablet reboot and enjoy :)



<br>

## ⚙️ Go back to FydeOS or standard images <a name=step3></a>

> [!CAUTION]
> Make sure you backup all your data

BredOS images comes with the uefi boot instead of the original uboot. This means that you can no longer enter `MASKROM` mode with the Vol + Power key combination. Instead you can execute the following command in the terminal (**THIS ENTIRELY WIPE YOUR DATA**)

```
sudo dd if=/dev/urandom of=/dev/mmcblk0 bs=10M count=2
```

Now the tablet should be in `MASROM` mode and you can flash the standard images. In case you need it check the [`Unbrick` section](https://wiki.fydetabduo.com/unbrick_the_fydetab_duo) in the official Fydetab wiki. 
