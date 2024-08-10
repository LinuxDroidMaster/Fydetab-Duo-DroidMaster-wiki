# 👨‍👩‍👧‍👦 How to enable multiple Linux containers in FydeOS 🚀

> [!NOTE]  
> All the process is described in more detail in this [video](https://youtu.be/DVWhIUo99RM?feature=shared).

Hi there! 👋 In this guide, I'll show you how to configure multiple Debian containers on your Fydetab DUO tablet running FydeOS. This way we can have separted environtments to test certaing apps or configurations without modifying our main Linux subsystem container 


1. **First, we need to go to the following URL in the web browser:**
```
chrome://flags
```
![](/Images/FydeOS/MultipleContainers/chrome_flags.png)

2. **Look for `Allow multiple containers` and enable it. After modifying this option we need to `reboot` the tablet**

![](/Images/FydeOS/MultipleContainers/chrome_flags_multiplecontainers.png)

3. **Once you have `rebooted` the tablet we can go to the Linux settings and we will see a new option called `Manage extra containers`

![](/Images/FydeOS/MultipleContainers/extra_containers_settings.png)

I recommend you increasing the size dedicated to Linux because all the containers depend on this option (as an example I have set this option to `30 GB`)

![](/Images/FydeOS/MultipleContainers/disk_size_linux.png)

4. Inside the new `Manage extra containers` section we can create all the Linux containers we want. Also you can start or stop the containers from this menu

![](/Images/FydeOS/MultipleContainers/multiple_containers_menu.png)

> [!NOTE]  
> To log in to one of the containers just open the `Terminal` application and select it from there.