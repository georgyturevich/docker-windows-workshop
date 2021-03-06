# Workshop Setup

You will be provided with a virtual machine which is already prepped for the lab. In this step you'll add your Docker ID and test the VM.

> If you're **not** at a hosted workshop and you're just running through this yourself, you can create your own [lab VM](lab-vm.md). If you **are** at a workshop, you should already have the credentials for your own VM.

## Steps

* [1. Get a Docker ID](#1)
* [2. Connect to your VM](#2)
* [3. Update your workshop content](#3)
* [3. Test your setup](#4)

## <a name="1"></a>Step 1: Get a Docker ID

You will build images and push them to Docker Hub during the workshop, so they are available to use later. You'll need a Docker ID to push images.

- Sign up for a free Docker ID on [Docker Hub](https://hub.docker.com)

## <a name="2"></a>Step 2. Connect to your VM

You have a dedicated VM running in Azure. This is a Windows Server 2016 VM with Docker and some useful tools installed. You will be provided with the VM credentials at the workshop.

> Your Azure VM will be destoyed after the workshop, so your work will be lost - but the images you push to Docker Hub will still be available.

You do not need Docker running on your laptop, but you will need a Remote Desktop client to connect to the VM.

- Windows - use the built-in Remote Desktop Connection app
- Mac - install [Microsoft Remote Desktop](https://itunes.apple.com/us/app/microsoft-remote-desktop/id715768417?mt=12) from the app store
- Linux - install [Remmina](http://www.remmina.org/wp/), or any RDP client you prefer.

## <a name="3"></a>Step 3. Setup your VM

Open a PowerShell prompt from the start menu.

> **Do not use PowerShell ISE for the workshop!** It has a strange relationship with the `docker login` command, and you won't get far with it.

Start by updating the workshop content:

```
cd C:\scm\docker-windows-workshop
git pull
```

Now run the update script - it will prompt you for your Docker ID. The script updates the tools on the VM and sets up your Docker ID in an environment variable:

```
cd lab-vm
.\update.ps1
```

> Be sure to use **your** Docker ID - mine is `sixeyed`, so that's what I enter into the script.

## <a name="3"></a>Step 4. Test your setup

Login to Docker Hub with your Docker credentials:

```
docker login --username $env:dockerId
```

Then check the Docker setup by running:

```
cd $env:workshop
.\verify.ps1
```

You should see a useful message, proving your Docker setup is working correctly.

# Next Up

On to [Part 1](part-1.md)!
