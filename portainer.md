<img width="750" height="300" alt="image" src="https://github.com/user-attachments/assets/6b4ac327-68ab-42bc-9292-75552fd5b6c6" />

<img width="1619" height="434" alt="Why" src="https://github.com/user-attachments/assets/7dd28f03-82de-4526-9dd1-14fb62510055" />
<p>
</p>

---

<img width="1619" height="434" alt="Installation" src="https://github.com/user-attachments/assets/e9d5cc57-f96f-444d-8550-87f223ad157d" />

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
