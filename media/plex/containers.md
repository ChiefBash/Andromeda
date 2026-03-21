<p align="center"><img width="300" height="138" alt="image" src="https://github.com/user-attachments/assets/b409128b-c3b6-48bd-ae7e-2837d0139154" /></p>

# Plex

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
      - /mnt/HDD1/media/christmas:/chirstmas
      - /mnt/HDD1/media/halloween:/halloween
    restart: unless-stopped
```

---

<p align="center"><img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/01584339-8e70-474f-bf6b-89694585309d" /></p>

# Tautulli

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
