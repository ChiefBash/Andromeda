<img width="336" height="287" alt="image" src="https://github.com/user-attachments/assets/469d28d2-1990-46b0-bbd6-584572ef4c90" />

<img width="810" height="217" alt="Installation" src="https://github.com/user-attachments/assets/de7e8748-7d84-4780-b8d4-fe67adfac77d" />

## UPDATE ENDEAVOUROS
```
sudo pacman -Syyu
```

## BACKUP
<p>Before installing Docker, create a backup on Timeshift, just in case something breaks.</p>

## INSTALL DOCKER
```
sudo pacman -Syu docker
```

## START & ENABLE DOCKER
```
sudo systemctl start docker
```
```
sudo systemctl enable docker
```

## PERMISSION CHANGE
```
sudo usermod -aG docker chiefbash
```

## INSTALL DOCKER COMPOSE
```
sudo pacman -Syu docker-compose
```
