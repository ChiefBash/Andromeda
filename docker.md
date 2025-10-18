## DOCKER
### WHY?
<p>

</p>

---

## INSTALLATION

### UPDATE ENDEAVOUROS

```
sudo pacman -Syyu
```

### BACKUP

<p>
Before installing Docker, create a backup on Timeshift, just in case something breaks.
</p>

### INSTALL DOCKER

```
sudo pacman -Syu docker
```

### START & ENABLE DOCKER

```
sudo systemctl start docker
```
```
sudo systemctl enable docker
```

### START & ENABLE DOCKER

```
sudo usermod -aG docker chiefbash
```

### INSTALL DOCKER COMPOSE

```
sudo pacman -Syu docker-compose
```
