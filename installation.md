## Ubuntu

---

## Timeshift

---

## GNOME Extensions

---

## Oh-my-ZSH

---

## Docker & Docker Compose

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
