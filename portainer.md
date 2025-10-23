<img width="610" height="199" alt="image" src="https://github.com/user-attachments/assets/fbc21779-6292-42b0-b302-6ff1dd262e9c" />

<img width="1619" height="434" alt="Why" src="https://github.com/user-attachments/assets/7dd28f03-82de-4526-9dd1-14fb62510055" />
<p>
</p>

---

<img width="1619" height="434" alt="Installation" src="https://github.com/user-attachments/assets/e9d5cc57-f96f-444d-8550-87f223ad157d" />

<b>BACKUP</b>
<p>
Create a backup on TImeshift, just in case anything breaks.
</p>

<b>CREATE PORTAINER VOLUME</b>
```
sudo docker volume create portainer_data
```

<b>INSTALL PORTAINER</b>
```
sudo docker run -d -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

<b>POST-INSTALLATION</b>
<p>
After Portainer has finished installing, open a web browser and go to <u>https://localhost:9000</u> and create an administrator account.
</p>
