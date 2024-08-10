# 🐳 Installing Docker on Your Fydetab DUO with FydeOS + Portainer Dashboard 🚀

> [!NOTE]  
> All the process is described in more detail in this [video](https://youtu.be/DVWhIUo99RM?feature=shared).

Hi there! 👋 In this guide, I'll show you how to install Docker on your Fydetab DUO tablet running FydeOS. 

<br>

# 📚 Index
* [🛠️ Prerequisites](#prerequisites)
* [🖥️ 1. Update Debian container](#step1)
* [🔨 2. Install Docker prerequisites](#step2)
* [🐳 3. Install Docker tools](#step3)
* [✅ 4. Check that Docker can run](#step4)
* [📊 5. Install and run Portainer to manage our Docker images](#step5)


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

## 🔨 2. Install Docker prerequisites <a name=step2></a>

We are going to follow the [official installation guide for Debian](https://docs.docker.com/desktop/install/debian/).

- **We need to install gnome-terminal:** 
```
sudo apt install gnome-terminal
```

## 🐳 3. Install Docker tools (Docker Engine) <a name=step3></a>

Now we are going to follow the [instructions](https://docs.docker.com/engine/install/debian/#install-using-the-repository) to setup Docker with `apt` repository

1. **Set up Docker's `apt` repository (copy and execute this in the terminal)**
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

2. **Install Docker packages**
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

<br>

## ✅ 4. Check that Docker can run <a name=step4></a> 

- **Run the Hello World image**
```
sudo docker run hello-world
```

You should see the following output

![](/Images/FydeOS/Docker/docker_hello_world.png)



<br>

## 📊 5. Install and run Portainer to manage our Docker images <a name=step5></a> 

We are going to follow the same steps that are described in [this tutorial](https://pimylifeup.com/raspberry-pi-portainer/) for the Raspberry Pi.

1. **Lets download the Portainer image**
```
sudo docker pull portainer/portainer-ce:latest
```

2. **Start and run the Portainer container**
```
sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

3. **Go to the URL `http://localhost:9000`** and create a new user

![](/Images/FydeOS/Docker/portainer_login.png)


4. **Go to the `Home` page and login to the local installation**

![](/Images/FydeOS/Docker/portainer_local_dashboard.png)


5. **Enjoy your images and containers!!**
![](/Images/FydeOS/Docker/portainer_local_dashboard_imagesandcontainers.png)