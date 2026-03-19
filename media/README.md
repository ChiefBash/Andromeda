<h1>Directory Map</h1>

```
Docker map here
```

```
Media drive here
```

<h1>Hardware Acceleration</h1>

To set up hardware acceleration for Plex in a docker container, use [this guide form TizuTech](https://tizutech.com/plex-transcoding-with-docker-nvidia-gpu/). This guide is from Feburary 2024 so the driver information is inaccurate, but the process is the same. Just in case the website is inaccessable, here ae the instructions:

<h3>Install NVIDIA Drivers</h3>

After installing Ubuntu, the drivers for NVIDIA should install alongside installnig the operating system (this is if you allow Ubuntu to check for third-party drivers; this will install NVIDIA proprietary drivers). If, for whatever reason, this does not happen, follow these steps:

```
# Search apt for NVIDIA drivers.
sudo apt search nvidia-driver
# At the time of writing the latest driver is 550.

# Install the headless server drivers.
# This command is if you are using Ubuntu Server.
sudo apt install nvidia-headless-550-server

# Install the NVIDIA Utils
sudo apt install nvidia-utils-550-server

# Search apt for libnvidia-encode. Needed for Plex transcoding
sudo apt search nvidia-encode

# Install the libnvidia-encode package.
sudo apt install libnvidia-encode-550-server
```

<h3>nvidia-smi</h3>

Enter the `nvidia-smi` command after the driver(s) installation is complete. If the drivers were installed correctly, the terminal should display something like this:

```
nvidia-smi

# Output
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 510.73.05    Driver Version: 510.73.05    CUDA Version: 11.6     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  Quadro P2000        Off  | 00000000:0B:00.0 Off |                  N/A |
| 44%   31C    P8     5W /  75W |      2MiB /  5120MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```

<h3>NVIDIA Container Toolkit</h3>

After installing the drivers, the container toolkit needs to be installed. This is what officially allows the Docker container to use information from the NVIDIA graphics card.

<h3>Setting Up The Package Repository</h3>

In my experience, this command did not work for me. It may be because I used it in a different Linux distro, but if for some reason this command doesn't work, skip to the next step.

```
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg   && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list |     sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' |     sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

<h3>Installing NVIDIA Container Toolkit</h3>

```
# Update and install NVIDIA Container Toolkit
sudo apt-get update

sudo apt-get install -y nvidia-container-toolkit

# Configure NVIDIA Container Toolkit
sudo nvidia-ctk runtime configure --runtime=docker

sudo systemctl restart docker

# Test GPU integration
docker run --gpus all nvidia/cuda:11.5.2-base-ubuntu20.04 nvidia-smi
```

<h3>Docker Compose Options</h3>

After the drivers and container toolkit are isntalled, the options can now be added to the Docker COmpose file. When using these options, this will only work with the [LinuxServer.io docker image of Plex](https://docs.linuxserver.io/images/docker-plex/). From what I understand, these settings will not work with other images of Plex. This image will allow transcoding to work correctly when using the graphics card. Below is an example of the container toolkit kit being implemeted:

```
---
version: "3.8"
services:
  plex:
    image: lscr.io/linuxserver/plex:latest
    container_name: plex
    network_mode: host
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]

    environment:
      - PUID=1001
      - PGID=1001
      - VERSION=docker
      - PLEX_CLAIM=##CLAIM-TOKEN##
      - NVIDIA_VISIBLE_DEVICES=all
      - NVIDIA_DRIVER_CAPABILITIES=compute,video,utility
    volumes:
      - /home/tizu/plex/appdata/config:/config
      - /mnt/media/TV Shows:/tv
      - /mnt/media/Movies:/movies
      - /mnt/media/Music:/music
    restart: unless-stopped
```

<h3>Update Plex Settings</h3>

Log in to the Plex server, go to Setting in the top-right corner.
<img width="250" height="53" alt="image" src="https://github.com/user-attachments/assets/321fd465-0783-463b-9682-fbe3c8b961d1" />

On the left-sidebar, scroll down to <b>Transcoder</b> and check the following boxes: <b>Use hardware acceleration when avaialble</b>, <b>Use hardware-accelerated video encoding</b> and <b>Enable HEVC Optimaization (experimental)</b>. Select the graphics card for the <b>Hardware transcoding device</b> and save changes when complete.

<img width="1218" height="828" alt="image" src="https://github.com/user-attachments/assets/99836bbf-4200-455f-8ced-526e5728152c" />
