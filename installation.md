## Ubuntu

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

## Timeshift

---

## GNOME Extensions

---

## Oh-my-ZSH

---

<p align="center"><img width="336" height="287" alt="image" src="https://github.com/user-attachments/assets/469d28d2-1990-46b0-bbd6-584572ef4c90" /></p>

## Docker

### Update & upgrade Ubuntu

```
sudo apt update && sudo apt upgrade -y
```

### Backup

Before installing Docker, create a backup on Timeshift, just in case something breaks.

### Install Docker

```
sudo apt install docker -y
```

### Start & enable Docker

```
sudo systemctl start docker
```

```
sudo systemctl enable docker
```

### Permission change

```
sudo usermod -aG docker chiefbash
```

### Install Docker Compose

```
sudo apt install docker-compose -y
```

---

<p align="center"><img width="610" height="199" src="https://github.com/user-attachments/assets/fbc21779-6292-42b0-b302-6ff1dd262e9c" /></p>

## Portainer

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
