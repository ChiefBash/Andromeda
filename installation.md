# Ubuntu

### Language

<img width="1117" height="793" alt="image" src="https://github.com/user-attachments/assets/132c4249-0b28-48c9-add7-cad221a469ee" />

### Accessibility

<img width="1585" height="1124" alt="image" src="https://github.com/user-attachments/assets/baee7b00-9145-46d2-9d96-51f1990b5622" />

### Keyboard Layout

<img width="1584" height="1123" alt="image" src="https://github.com/user-attachments/assets/17daccb0-9d42-450c-9611-727fbbb85b4b" />

### Internet Connection

Select the wired connection option. If a worse case scenario, Wi-Fi will work. *If a wired connection is not detected, it will say that it cannot be detected.*

<img width="1581" height="1120" alt="image" src="https://github.com/user-attachments/assets/aa42a46f-9d41-45d4-934f-613d0ac31d95" />

### Type Of Installation

<img width="1581" height="1118" alt="image" src="https://github.com/user-attachments/assets/87958ab7-436c-4dda-97a7-e506d12e6db0" />

### Applications

<img width="1580" height="1120" alt="image" src="https://github.com/user-attachments/assets/3669b88d-bba6-4c6c-a15f-114425500586" />

### Optimization

<img width="1615" height="1145" alt="image" src="https://github.com/user-attachments/assets/300ccc83-f95f-405b-bca8-2afaf68b89e0" />

### Disk Setup


<img width="1615" height="1142" alt="image" src="https://github.com/user-attachments/assets/901b0d12-2a1a-4181-b8e6-ef94fd78e48b" />

---

# Timeshift

---

# GNOME Extensions

---

# Oh-my-ZSH

---

<p align="center"><img width="336" height="287" alt="image" src="https://github.com/user-attachments/assets/469d28d2-1990-46b0-bbd6-584572ef4c90" /></p>

# Docker

### Update & upgrade Ubuntu

```
sudo apt update && sudo apt upgrade -y
```

### Backup

Before installing Docker, create a backup on Timeshift, just in case something breaks.

### Add Docker's official GPG key

```
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### Add the repository to apt sources

```
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF
```

### Install the latest version of Docker

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

### Check the status of Docker & enable (if necessary)

```
sudo systemctl status docker
sudo systemctl enable docker
```
### Add username to Docker group

```
sudo usermod -aG docker $USER
```

### Optional: Create a Docker container (hello-world)

```
sudo docker run hello-world
```

*Docker configuration(s) in the terminal must be entered as `sudo`, otherwise the command will not work.*

---

<p align="center"><img width="610" height="199" src="https://github.com/user-attachments/assets/fbc21779-6292-42b0-b302-6ff1dd262e9c" /></p>

# Portainer

### Backup

Create a backup on Timeshift, just in case anything breaks.

### Create Portainer volume
```
sudo docker volume create portainer_data
```

### Install Portainer
```
sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

### Post-installation

After Portainer has finished installing, open a web browser and go to the [Portainer dashboard](https://localhost:9000) and create an administrator account.

---

# Oracle VirtualBox

### Update System and Install Repository Tools

```
sudo apt update && sudo apt upgrade -y
sudo apt install curl ca-certificates gpg lsb-release -y
```

### Import VirtualBox GPG Key

```
curl -fSsL https://www.virtualbox.org/download/oracle_vbox_2016.asc | gpg --dearmor | sudo tee /usr/share/keyrings/virtualbox.gpg > /dev/null
```

### Add VirtualBox Repository

```
cat <<EOF | sudo tee /etc/apt/sources.list.d/virtualbox.sources
Types: deb
URIs: http://download.virtualbox.org/virtualbox/debian
Suites: $(lsb_release -cs)
Components: contrib
Architectures: $(dpkg --print-architecture)
Signed-By: /usr/share/keyrings/virtualbox.gpg
EOF
```

### Install VirtualBox

```
sudo apt install virtualbox-7.2 build-essential dkms linux-headers-$(uname -r) -y
```

### Verify Installation Source

```
apt-cache policy virtualbox-7.2
```

### Check VirtualBox service status

```
sudo systemctl status vboxdrv
```

### Enable VirtualBox service ( if required)

```
sudo systemctl enable vboxdrv --now
```

### Add user to vboxusers group

```
sudo usermod -a -G vboxusers $USER
```
