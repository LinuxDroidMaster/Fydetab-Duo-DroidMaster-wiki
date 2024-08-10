# 🤖 Installing Android AOSP + Magisk + Google Apps on Your Fydetab DUO 🚀

> [!NOTE]  
> All the process is described in more detail in this [video](https://youtu.be/6SiFNZiIPQo?feature=shared).

Hi there! 👋 In this guide, I'll show you how to install Android AOSP on your Fydetab DUO tablet.

<br>

# 📚 Index
* [🛠️ Prerequisites](#prerequisites)
* [🖥️ 1. Installing AOSP ROM](#step1)
* [👹 2. Installing Magisk](#step2)
* [📲 3. Installing GApps](#step3)
* [❌ 4. Problems I found in AOSP](#step4)


<br>
<br>

## 🛠️ Prerequisites <a name=prerequisites></a>

**Before we begin, make sure you have the following files downloaded:**

- [ADB and Fastboot files from the official Google page](https://developer.android.com/tools/releases/platform-tools)
- [Rockchip Driver](https://dl.radxa.com/tools/windows/DriverAssitant_v5.0.zip)
- Flashing tool: You can download the tools for Linux and Mac from the official [Fydetab Duo Wiki](https://wiki.fydetabduo.com/flashing_the_fydetab_duo#utilising-the-image-flash-tool-provided-by-rockchip). For Windows you can use the last available version [here (RKDevTool vX.XX)](https://docs.radxa.com/en/rock5/rock5b/low-level-dev/rkdevtool). 
- [AOSP Fydetab DUO image (the file we are going to flash)](https://wiki.fydetabduo.com/os-release-board/aosp)

**Unzip all files including the AOSP ROM which by default comes in an .img.xz file and we have to unzip it to make it an .img file. You should have this:**

![](/Images/Android/AOSP/files_needed.png)


<br>

## 🖥️ 1. Installing AOSP ROM <a name=step1></a>

- The first thing to do is installing the Rockchip Driver we have downloaded. For this, open the `DriverAssitant_v5.0` folder and execute the file `DriverInstall.exe`.

- Click on `Install Driver`:

![](/Images/Android/AOSP/install_drivers.png)

- Open the folder that contains the flashing tool:  `RKDevTool_Release_v2.96` folder (check the version you have downloaded for the name) and execute the tool `RKDevTool.exe`.

- To flash Android AOSP we need to open the second tab (leave the first one as it comes)

![](/Images/Android/AOSP/flashing_tool_android_empty.png)

To help you this is an image of the tool in English, **but for now we are not going to do anything in the tool.**

![](/Images/Android/AOSP/flashing_tool_english.png)


- Connect the tablet to the PC with a USB cable that allow data transfering (**the default cable that comes with the Fydetab is not valid**).

- Now turn off the tablet until it is completely switched off.

- We need to enter on `MASKROM/LOADER` mode (MASKROM and LOADER are the same). For this hold the `Vol +` button for like 20 seconds and then press for 0,5 - 1 seconds the `Power` button and release it, then release the `Vol +` button (technically you should release both buttons at the same time but this is the process that works better for me). 

- If the process was correct you should see now in the flashing tool the following message: 

**Note: If the tablet turns on, turn it off and repeat the previous step.**

![](/Images/Android/AOSP/device_detected_in_flashing_tool.png)

- Now click on the first button and select the ROM file we downloaded in the prerequisites, `fydetab_duo-aosp12-update-20221110.img` (remember that you need to unzip the file when downloaded so it has the extension `.img` and not `.img.xz`)

![](/Images/Android/AOSP/selecint_rom_flashing_tool.png)

- Start the flashing process by pressing the second button. On the right side you will see some messages and the % progress of the process.

![](/Images/Android/AOSP/start_process_flashing_AOSP.png)

- When the process is completed the tablet will boot into the `Android AOSP ROM` directly. Enjoy!

<p align="center">
  <img src="/Images/Android/AOSP/AOSP_12_screenshots/1.png" width="200" />
  <img src="/Images/Android/AOSP/AOSP_12_screenshots/2.png" width="200" />
  <img src="/Images/Android/AOSP/AOSP_12_screenshots/3.png" width="200" />
  <img src="/Images/Android/AOSP/AOSP_12_screenshots/4.png" width="200" />
</p>




<br>

## 👹 2. Installing Magisk <a name=step2></a>

- You can download everything directly on the tablet but I feel that is way easier download all in the PC and move it to the tablet with the USB connection. Remember to change this option so the tablet appears like a Disk in your computer: 

<p align="center">
  <img src="/Images/Android/AOSP/usb_options.png" width="200" />
  <img src="/Images/Android/AOSP/file_transfer_option_usb.png" width="200" />
</p>

- Download the latest version of Magisk available in the [official GitHub](https://github.com/topjohnwu/Magisk/releases)

- Install Magisk on the tablet. We have 2 options: 

    - Move the apk to the tablet and open it from the `Explorer` app. Select the `APK installer` and install it. 

    - Install the app via `adb` from the PC. First, open the `platform-tools` folder (we had it from the prerequisites) and open a terminal in this folder

    Tip: You can write `cmd` in the file explorer and a terminal will be opened in that path: 

    ![](/Images/Android/AOSP/adb_open_terminal.png)

    In the terminal check that device is detected with the command `adb.exe devices`. You should see 1 entry in the output: 

    ![](/Images/Android/AOSP/adb_devices.png)

    Copy the `Magisk-v27.0.apk` app to the folder we are using, `platform-tools` and install it with the command: 

    ```
    adb install Magisk-v27.0.apk
    ```
    ![](/Images/Android/AOSP/adb_install_magisk.png)
    
- Now the Magisk app is installed in the tablet but we need to install a patched `boot.img` so Magisk can manage `root` permissions. You have 2 options: 

    - Extract your own `boot.img`. You can follow the steps described [here](https://xdaforums.com/t/gsi-rom-install-magisk-with-no-root-on-gsi-rom-dsu-method.4651428/) and patch it with Magisk (just click on `Install` > `Select and Patch a File`)

    - Use this [`patched_boot.img`](https://drive.google.com/file/d/1fKNB77ybKclnfaytaWoTLfF4offsghES/view?usp=sharing) file that I created following the previous process so you don't need to do it. 

- Copy the `pacthed_boot.img` in to the same folder we were using, `platform-tools`.

- Reboot the tablet into recovery mode with the command: 
```
adb.exe reboot recovery
```

- In the tablet move down with the `Vol -` button and select `Enter fastboot` with the `Power` button:

![](/Images/Android/AOSP/fasboot_enter.png)

- Check that the device is recognized in `fastboot` mode with the following command: 
```
fastboot.exe devices
```

![](/Images/Android/AOSP/fastboot_devices_command.png)

- Flash the `patched_boot.img` with the command:

```
fastboot flash boot patched_boot.img
```

![](/Images/Android/AOSP/fastboot_flash_boot.png)

- Reboot the tablet with the command
```
fastboot.exe reboot
```

![](/Images/Android/AOSP/fasboot_reboot.png)

- Open `Magisk` app in the tablet and accept the message that appears. After 5 seconds the tablet will reboot and we will have finished the installation of Magisk

<p align="center">
  <img src="/Images/Android/AOSP/magisk_message.png" width="200" />
  <img src="/Images/Android/AOSP/magisk_installed.png" width="200" />
</p>




<br>

## 📲 3. Installing GApps <a name=step3></a>

- Download the Magisk GApps for Android 12 from this [link](https://sourceforge.net/projects/magiskgapps/files/android-12L-ALPHA/17.10.2022/MagiskGApps-a.12L.BASIC.10.16.2022.zip/download)

- Copy the download file, `MagiskGApps-a.12L.BASIC.10.16.2022.zip` to the tablet.

- Open `Magisk` app and go to the `Modules` tab. 

- Click on `Install from storage` and select the `MagiskGApps-a.12L.BASIC.10.16.2022.zip` file. The process will start and when it finishes we need to `reboot` the tablet (click on the `reboot` button)

![](/Images/Android/AOSP/magisk_installing.png)

- You will see the `Google Play Store` app and you can start using it

![](/Images/Android/AOSP/play_store.png)



<br>

## ❌ 4. Problems I found in AOSP <a name=step4></a>

- I need to wake the tablet 2 times so it wakes properly. I press 1 time the `Power` button, the screen brighteen in black and I need to press it again to lock it and to 

- The screen is locked and can not rotate. You can rotate it manually using the following `adb` commands: 

```
adb shell settings put system accelerometer_rotation 0  #disable auto-rotate
adb shell settings put system user_rotation 3  #270° clockwise
```

Info from [StackOverflow](https://stackoverflow.com/questions/25864385/changing-android-device-orientation-with-adb): 
```
accelerometer_rotation: auto-rotation, 0 disable, 1 enable
user_rotation: actual rotation, clockwise, 0 0°, 1 90°, 2 180°, 3 270°
```
