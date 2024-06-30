# ☠️ UNBRICK the Fydetab DUO and flash the official images 🚀

Heyyy!!! 👋 In this guide I'm going to show you how to unbrick the Fydetab Duo in case you flash an image that is not compatible and you can't enter maskrom mode with the usual button combination. 

<br>

# 📚 Index
* [🛠️ Prerequisites](#prerequisites)
* [👹 MASKROM mode](#maskrom)
* [☀️ How to flash the official images](#flashing_images)


<br>
<br>

## 🛠️ Prerequisites <a name=prerequisites></a>

**If you have flashed an image to the Fydetab Duo you should already have all this tools but if not,  make sure you have this in your computer:**

- [Rockchip Driver](https://dl.radxa.com/tools/windows/DriverAssitant_v5.0.zip)
- Flashing tool: You can download the tools for Linux and Mac from the official [Fydetab Duo Wiki](https://wiki.fydetabduo.com/flashing_the_fydetab_duo#utilising-the-image-flash-tool-provided-by-rockchip). For Windows you can use the last available version [here (RKDevTool vX.XX)](https://docs.radxa.com/en/rock5/rock5b/low-level-dev/rkdevtool). 
- [AOSP Fydetab DUO image (the file we are going to flash)](https://wiki.fydetabduo.com/os-release-board/aosp)

**Unzip all files so you have everything uncompressed**



<br>

## 👹 MASKROM mode <a name=maskrom></a>

**To flash any image into the Fydetab Duo we need to enter `MASKROM` mode**


**- How to enter MASKROM mode:**

- Connect the USB from the PC to the tablet
- Power off completely the tablet
- Press and hold the `Vol +`, while holding it quick press `Power` button (releasing it but not the `Vol +`), then release `Vol +`. 


- [Video - Opening Fydetab Duo (Forcing MASKROM mode) - Unbrick Fydetab Duo](https://youtu.be/FPHwv__BagI)

If you can't enter MASKROM mode this way because you have flashed some image incorrectly (happened to me) and every time you press the `Power` button the tablet turns on, then you need to open the tablet and use the inner `MASKROM` button.

![](/Images/General/brick/device_opened1.jpg)
![](/Images/General/brick/device_opened2.jpg)

Basically the steps to enter `MASKROM` mode with the button on the PCB are: 

1. Force a shutdown holding the powerbutton for 10 seconds. 
2. Press and hold the `MASKROM` mode from the PCB. While holding the button connect the USB from the tablet to the PC. 
3. Open `RKDevTool.exe` and you will see that a device is detected on MASKROM mode. 

![](/Images/General/brick/flash_tool_screenshot.png)



<br>

## ☀️ How to flash the official images <a name=flashing_images></a>

You can download the images from the Official Wiki. After that, you can flash them with these steps: 

1. Enter MASKROM mode as explained in the previous section. 
2. Open `RKDevTool.exe` tool and go to the second tab, `Upgrade Firmware`. 
3. Click on the `Firmware` button and select the downloaded image to flash (remember to  uncompress it so it has `.img` as the extension).
4. Click on the `Upgrade` button to start the process. 

![](/Images/General/brick/flashing_images.png)

5. When the process is finished the tablet will automatically boot to the new operating system. You have now recovered your Fydetab, enjoy!!!