<p align="center"><img width="336" height="287" alt="image" src="https://github.com/user-attachments/assets/469d28d2-1990-46b0-bbd6-584572ef4c90" /></p>

## UPDATE & UPGRADE UBUNTU
```
sudo apt update && sudo apt upgrade -y
```

## BACKUP
<p align="center">Before installing Docker, create a backup on Timeshift, just in case something breaks.</p>

## INSTALL DOCKER
```
sudo apt install docker -y
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
sudo apt install docker-compose -y
```
