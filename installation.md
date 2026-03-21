## Ubuntu

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
