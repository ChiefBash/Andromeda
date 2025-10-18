## PORTAINER

### WHY?
<p>
</p>

---

## INSTALLATION

### BACKUP
<p>
Create a backup on TImeshift, just in case anything breaks.
</p>

### CREATE PORTAINER VOLUME
```
sudo docker volume create portainer_data
```

### INSTALL PORTAINER
```
sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

### POST-INSTALLATION
<p>
After Portainer has finished installing, open a web browser and go to https://localhost:9000 and create an administrator account.
</p>
