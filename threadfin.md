<img width="285" height="80" src="https://github.com/user-attachments/assets/875960ea-1f76-4ea7-81b1-cc3379d5dccf" />

<img width="810" height="217" src="https://github.com/user-attachments/assets/7dd28f03-82de-4526-9dd1-14fb62510055" />
<p>
</p>

---

<img width="810" height="217" src="https://github.com/user-attachments/assets/6b9c4e2c-4697-40f2-8a4f-1da00f97b941" />

### TORRENT/COMPOSE.YAML

<p>
Ensure the compose.yaml file of the torrent stack in Portainer is accurate. This is the section of code if necessary:
</p>

```
threadfin:
    image: mgoerentz/threadfin:latest
    container_name: threadfin
    network_mode: service:gluetun
    environment:
      - PUID=1000
      - PGID=1000
      - THREADFIN_PORT=34400
    volumes:
      - /home/chiefbash/docker/threadfin/config:/home/threadfin/conf
      - /home/chiefbash/docker/threadfin/tmp:/tmp/threadfin:rw
    labels:
      - deunhealth.restart.on.unhealthy=true
    depends_on:
      gluetun:
        condition: service_healthy
        restart: true
    restart: unless-stopped
```

<p>
Under the Gluetun service, make sure port 34400 is specified in the port section.
</p>

```
service:
  gluetun:
    ports:
      - 34400:34400
```

### PLAYLIST

### XMLTV

### FILTER

### MAPPING

### USERS

### SETTINGS

### IMPORT TO PLEX
