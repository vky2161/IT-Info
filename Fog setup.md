
# FOG Project Installation and Storage Configuration Guide

## Overview

This document describes the basic installation of a FOG Project server on Linux, the initial web configuration, and how image storage works.

---

# Prerequisites

- Linux Server (Ubuntu/Debian recommended)
    
- Static IP Address
    
- Internet connectivity
    
- Root or sudo privileges
    
- DHCP server (either on the FOG server or an existing DHCP server)
    

---

# Step 1 – Update the Server

```bash
sudo apt update
sudo apt upgrade -y
```

---

# Step 2 – Install Git

Check if Git is installed:

```bash
git --version
```

If not installed:

```bash
sudo apt install git -y
```

Verify:

```bash
git --version
```

---

# Step 3 – Download FOG

```bash
cd /opt
sudo git clone https://github.com/FOGProject/fogproject.git
```

Go to the installer directory:

```bash
cd fogproject/bin
```

Verify the installer exists:

```bash
ls
```

You should see:

```
installfog.sh
```

---

# Step 4 – Run the Installer

```bash
sudo ./installfog.sh
```

Typical installation selections:

|Prompt|Selection|
|---|---|
|Installation Type|Normal Server|
|DHCP handled by FOG|Yes (only if this server is the DHCP server)|
|Existing DHCP Server|No|
|HTTPS|No (recommended for initial setup)|
|DNS handled by DHCP|Depends on your environment|

---

# Step 5 – Complete the Web Installation

Open a browser:

```
http://<FOG_Server_IP>/fog/management
```

Example:

```
http://192.168.1.10/fog/management
```

Click:

```
Install/Update Now
```

After completion, return to the login page.

Default credentials:

```
Username: fog
Password: password
```

Change the password after the first login.

---

# Step 6 – Verify Storage Node

Navigate to:

```
Storage Management
```

Open:

```
DefaultMember
```

Verify:

- Storage Path = `/images`
    
- Correct server IP
    
- Master Node = Enabled
    

---

# Image Storage

FOG stores captured images in:

```
/images
```

This directory is **not** inside the FOG installation folder.

Example:

```
/
├── images
├── home
├── opt
│   └── fogproject
└── var
```

---

# Check Storage Location

```bash
df -h /images
```

Example:

```
Filesystem      Size Used Avail Mounted on
/dev/sda2       500G 40G 460G /
```

FOG uses all available free space on the filesystem where `/images` is mounted.

---

# Capture Workflow

1. Register the client using PXE boot.
    
2. Create an Image Definition.
    
3. Assign the image to the host.
    
4. Schedule an Upload task.
    
5. Boot the client via PXE.
    
6. The image is stored in:
    

```
/images/<ImageName>
```

Example:

```
/images/Windows11
```

---

# Deploy Workflow

1. Register the destination computer.
    
2. Assign the required image.
    
3. Schedule a Deploy task.
    
4. PXE boot the client.
    
5. FOG downloads the image from `/images` and deploys it to the target disk.
    

---

# Useful Commands

Check available storage:

```bash
df -h
```

Check the images filesystem:

```bash
df -h /images
```

List disks:

```bash
lsblk
```

Find partition UUID:

```bash
sudo blkid
```

Restart FOG services:

```bash
sudo systemctl restart FOGImageReplicator
sudo systemctl restart FOGMulticastManager
```

---

# Best Practices

- Use a static IP address for the FOG server.
    
- Use a dedicated disk or partition for `/images`.
    
- Keep the operating system and image repository on separate storage when possible.
    
- Back up the `/images` directory regularly.
    
- Verify available disk space before capturing large images.
    
- Change the default administrator password after installation.
