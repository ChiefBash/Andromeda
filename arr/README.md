<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/6a1a6800-a31a-4e27-bb6a-f058e8a2e782" />
</p>

# Homarr

```
services:
  homarr:
    image: ghcr.io/ajnart/homarr:latest
    container_name: homarr
    environment:
      - TZ=America/Chicago
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - ./homarr:/config
      - ./homarr/data:/data
    ports:
      - 7575:7575
    restart: unless-stopped
```

---

<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/12da5755-4d09-4210-bd36-cdb945eff196" /></p>

# Bazarr

```
services:
  bazarr:
    image: lscr.io/linuxserver/bazarr:latest
    container_name: bazarr
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - ./bazarr:/config
      - /mnt/HDD1/media/movies:/movies
      - /mnt/HDD1/media/shows:/shows
    ports:
      - 6767:6767
    restart: unless-stopped
```

---

<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/aba41f42-1a61-4720-aeea-a72f84b3ac05" /></p>

# Lidarr

```
services:
  lidarr:
    image: lscr.io/linuxserver/lidarr:latest
    container_name: lidarr
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - ./lidarr:/config
      - /mnt/HDD1/media/music:/music
      - /mnt/HDD5/downloads:/downloads
    ports:
      - 8686:8686
    restart: unless-stopped
```

---


<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/78e05bc0-eea1-4827-835f-c9fccf9bb2c8" /></p>

# Radarr

```
services:
  radarr:
    image: lscr.io/linuxserver/radarr:latest
    container_name: radarr
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - ./radarr:/config
      - /mnt/HDD1/media/movies:/movies
      - /mnt/HDD5/downloads:/downloads
    ports:
      - 7878:7878
    restart: unless-stopped
```

---

<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/5c6e2d93-ece0-4412-ac75-f872ccaa26f4" />
</p>

# Readarr

```
services:
  readarr:
    image: lscr.io/linuxserver/readarr:0.4.19-nightly
    container_name: readarr
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - ./readarr:/config
      - /mnt/HDD1/media/books/:/books
      - /mnt/HDD5/downloads:/downloads
    ports:
      - 8787:8787
    restart: unless-stopped
```

---

<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/1d3a5fdc-8b61-449d-8573-428a69c20fa1" />
</p>

# Seerr

```
services:
  seerr:
    image: seerr/seerr:develop
    container_name: seerr
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - ./seerr:/config
    ports:
      - 5055:5055
    restart: unless-stopped
```

---

<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/8cc1d351-e5f2-4eb2-8421-f735112608ab" /></p>

# Sonarr

```
services:
  sonarr:
    image: lscr.io/linuxserver/sonarr:latest
    container_name: sonarr
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/Chicago
    volumes:
      - ./sonarr:/config
      - /mnt/HDD1/media/shows:/shows
      - /mnt/HDD5/downloads:/downloads
    ports:
      - 8989:8989
    restart: unless-stopped
```
