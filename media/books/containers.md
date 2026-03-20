<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/2046b30f-89c6-4d56-94cd-7dc409b4240f" />
</p>

# Audiobookshelf

```
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
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
      - VERSION=docker
      - PLEX_CLAIM=token
      - NVIDIA_VISIBLE_DEVICES=all
      - NVIDIA_DRIVER_CAPABILITIES=compute,video,utility
    volumes:
      - ./plex:/config
      - /mnt/HDD1/media/movies:/movies
      - /mnt/HDD1/media/shows:/shows
      - /mnt/HDD1/media/videos:/videos
    restart: unless-stopped
```

---

<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/1b4bf258-ba13-4e76-8458-d40ad420044b" />
</p>

# Kavita

```
services:
  tautulli:
    image: lscr.io/linuxserver/tautulli:latest
    container_name: tautulli
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - ./tautulli:/config
    ports:
      - 8181:8181
    restart: unless-stopped
```
