# docker

#  Introduction à Docker

Docker est un outil permettant de créer, déployer et exécuter des applications dans des **conteneurs**. Voici les étapes essentielles pour l'utiliser.

---

##  Étapes de base pour utiliser Docker

### 1. Installation de Docker

- Aller sur [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
- Télécharger Docker Desktop (Windows, Mac) ou utiliser `apt`, `yum` pour Linux.

```bash
# Ubuntu
sudo apt update
sudo apt install docker.io
```

### 2.  Lancer un conteneur simple

```bash
docker run hello-world
```

Ce test permet de vérifier si Docker est bien installé.


```

#Docker-commande essentielle 

---

##  Docker Image

### Lister les images
```bash
docker images
# ou
docker image ls
```

### Télécharger une image
```bash
docker pull <image>
```

### Construire une image avec un Dockerfile
```bash
docker build -t nom:tag .
```

### Taguer une image
```bash
docker tag <id_image> nouveau_nom:tag
```

### Inspecter une image
```bash
docker image inspect <image>
```

### Voir les couches d'une image
```bash
docker history <image>
```

### Supprimer une image
```bash
docker rmi <image>
```

### Nettoyer les images non utilisées
```bash
docker image prune
docker image prune -a
```

---

##  Docker Container

### Lancer un conteneur nginx
```bash
docker run -d -p 80:80 nginx
```

### Lister les conteneurs en cours d'exécution
```bash
docker ps
```

### Lister tous les conteneurs (même arrêtés)
```bash
docker ps -a
```

### Lancer un conteneur interactif basé sur Ubuntu
```bash
docker run -it ubuntu bash
```

### Lancer un conteneur nommé nginx en arrière-plan
```bash
docker run -d --name mon_nginx nginx
```

### Arrêter le conteneur `mon_nginx`
```bash
docker stop mon_nginx
```

### Redémarrer le conteneur `mon_nginx`
```bash
docker restart mon_nginx
```

### Voir les logs d’un conteneur
```bash
docker logs mon_nginx
```

### Accéder à un conteneur en ligne de commande
```bash
docker exec -it mon_nginx bash
```

---

##  Dockerfile

### Exemple de fichier Dockerfile
```Dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]
```

---

##  Docker Compose

### Exemple de docker-compose.yml
```yaml
version: "3"
services:
  web:
    build: .
    ports:
      - "3000:3000"
```

### Lancer les services
```bash
docker-compose up
```

### Lancer avec reconstruction
```bash
docker-compose up --build
```

### Stopper et supprimer les services
```bash
docker-compose down
```

---

##  Docker Volume

### Créer un volume
```bash
docker volume create mon_volume
```

### Lister les volumes
```bash
docker volume ls
```

### Utiliser un volume dans un conteneur
```bash
docker run -v mon_volume:/data nginx
```

### Supprimer un volume
```bash
docker volume rm mon_volume
```

---

##  Docker Network

### Créer un réseau
```bash
docker network create mon_net
```

### Lister les réseaux
```bash
docker network ls
```

### Utiliser un réseau lors du run
```bash
docker run --network mon_net nginx
```

### Supprimer un réseau
```bash
docker network rm mon_net
```
---

