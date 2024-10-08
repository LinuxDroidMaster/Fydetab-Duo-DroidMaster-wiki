# 🍷 Installing Wine on Your Fydetab DUO with FydeOS 🚀

> [!NOTE]  
> All the process is described in more detail in this [video](https://youtu.be/6SiFNZiIPQo?feature=shared).

Hi there! 👋 In this guide, I'll show you how to install Wine on your Fydetab DUO tablet running FydeOS. Wine will allow you to run Windows applications on your device. Let's get started! 💪

<br>

# 📚 Index
* [🛠️ Prerequisites](#prerequisites)
* [🖥️ 1. Update Debian container](#step1)
* [🛍️ 2. Install Pi-Apps store](#step2)
* [🍷 3. Install Wine](#step3)
* [✅ 4. Check that you can use Wine](#step4)
* [🖵 5. Adjust Wine resolution and run Winecfg](#step5)


<br>
<br>

## 🛠️ Prerequisites <a name=prerequisites></a>

Before we begin, make sure you have the following:

- A Fydetab DUO tablet with FydeOS 📱
- Internet connection 🌐
- Access to FydeOS terminal. If you don't know you to do it check this [video](https://youtu.be/TnV74KBCk3g?list=PL4worxVHtqXrko2FcWYwot_rdWKLKrtpK&t=442)


<br>

## 🖥️ 1. Update Debian container <a name=step1></a>

* 🖥️ Access FydeOS Terminal app and start the penguin container:

Execute the following commands: 

```
sudo apt update -y
sudo apt upgrade -y
```


<br>

## 🛍️ 2. Install Pi-Apps store <a name=step2></a>

1. 🖥️ **Open the Debian terminal** 

2. 📦 **Install [Pi-Apps store](https://pi-apps.io/):** 

Run the following command:
```
wget -qO- https://raw.githubusercontent.com/Botspot/pi-apps/master/install | bash
```

## 🍷 3. Install Wine <a name=step3></a>

1. **🛍️ Open Pi-Apps Store from the FydeOS menu in the "Linux Apps" folder**

![Pi-Apps Store from the FydeOS menu](/Images/FydeOS/Wine/piapps_from_menu.png)

2. **🔍 Search for "Wine" from the store**

<div style="display: flex; justify-content: space-between;">
  <img src="/Images/FydeOS/Wine/piapps_search.png" alt="image 1" style="width: 45%;"/>
  <img src="/Images/FydeOS/Wine/piapps_wine_install.png" alt="image 2" style="width: 45%;"/>
</div>

3. **Click on "Install" and wait until the process finishes**


<br>

## ✅ 4. Check that you can use Wine <a name=step4></a> 

1. ⬇️ **Download a x64 app to run (for example [Notepad++](https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v8.6.7/npp.8.6.7.Installer.x64.exe))**

2. **From the Debian terminal run the following command to execute the installer**
```
box64 wine npp.8.6.7.Installer.x64.exe
```
3. **Complete the installation process and check that Notepad++ runs**

> [!NOTE]  
> After the installation process finishes you can find the installation path of the executables here: `
cd ~/.wine/drive_c/Program\ Files\
`

![](/Images/FydeOS/Wine/notepad_working_small.png)


<br>

## 🖵 5. Adjust Wine resolution and run Winecfg <a name=step5></a> 

The text from the applications that runs with Wine looks quite small, to fix it we need to change the DPI options using Winecfg. 

1. Run Winecfg with the following command
```
box64 wine winecfg
```
2. Go to the `Graphics` tab and increate the DPI slide (I set it at 192 but you can increase or decrease the value as you prefer). After that when you run anything with Wine, the text and everything will be bigger.

![](/Images/FydeOS/Wine/winecfg_graphics.png)


