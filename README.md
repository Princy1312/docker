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

### 3.  Télécharger une image

```bash
docker pull nginx
```

Télécharge l'image **nginx** depuis Docker Hub.

### 4.  Exécuter un conteneur

```bash
docker run -d -p 8080:80 nginx
```

- `-d` : mode détaché (en arrière-plan)
- `-p` : redirige le port 8080 local vers le port 80 du conteneur

### 5.  Lister les conteneurs

```bash
docker ps       # Conteneurs actifs
docker ps -a    # Tous les conteneurs
```

### 6.  Arrêter ou supprimer un conteneur

```bash
docker stop <nom_ou_id_du_conteneur>
docker rm <nom_ou_id_du_conteneur>
```

### 7.  Supprimer une image

```bash
docker rmi nginx
```

---

##  Construire une image personnalisée

Créer un fichier `Dockerfile` :

```Dockerfile
# Dockerfile
FROM python:3.10
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

Puis construire l'image :

```bash
docker build -t mon-app .
docker run -p 5000:5000 mon-app
```

---

##  Utiliser Docker Compose (optionnel)

Créer un fichier `docker-compose.yml` :

```yaml
version: "3"
services:
  web:
    build: .
    ports:
      - "5000:5000"
```

Puis lancer avec :

```bash
docker-compose up
```

---

##  Vérification des commandes 

```bash
docker images         # Liste des images
docker logs <id>      # Voir les logs
docker exec -it <id> bash  # Accès au terminal du conteneur
```
# 🐳 Docker - Commandes essentielles

Ce fichier contient les commandes Docker pour les éléments suivants : **image**, **container**, **Dockerfile**, **compose**, **volume**, **network**.

```bash
# ----------------------------
# 📦 Docker Image
# ----------------------------
docker images                     # Lister les images
docker pull <image>              # Télécharger une image
docker build -t nom:tag .        # Construire une image avec un Dockerfile
docker tag <id> nouveau:tag      # Taguer une image
docker image inspect <image>     # Inspecter une image
docker history <image>           # Voir les couches d'une image
docker rmi <image>               # Supprimer une image
docker image prune               # Supprimer les images non utilisées
docker image prune -a            # Supprimer toutes les images inutilisées

# ----------------------------
# 🧱 Docker Container
# ----------------------------
docker run -d -p 80:80 nginx     # Lancer un conteneur
docker ps                        # Lister les conteneurs actifs
docker ps -a                     # Lister tous les conteneurs
docker stop <id>                 # Arrêter un conteneur
docker rm <id>                   # Supprimer un conteneur
docker restart <id>              # Redémarrer un conteneur
docker logs <id>                 # Voir les logs
docker exec -it <id> bash        # Accéder à un conteneur

# ----------------------------
# 📝 Dockerfile
# ----------------------------
# Exemple de Dockerfile :
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm", "start"]

# ----------------------------
# 📦 Docker Compose
# ----------------------------
# Exemple docker-compose.yml :
version: "3"
services:
  web:
    build: .
    ports:
      - "3000:3000"

# Commandes :
docker-compose up                # Lancer tous les services
docker-compose down              # Stopper et supprimer les services
docker-compose up --build        # Rebuild + lancer

# ----------------------------
# 💾 Docker Volume
# ----------------------------
docker volume create mon_volume  # Créer un volume
docker volume ls                 # Lister les volumes
docker run -v mon_volume:/data nginx  # Utiliser un volume
docker volume rm mon_volume      # Supprimer un volume

# ----------------------------
# 🌐 Docker Network
# ----------------------------
docker network create mon_net    # Créer un réseau
docker network ls                # Lister les réseaux
docker run --network mon_net nginx  # Lancer dans un réseau
docker network rm mon_net        # Supprimer un réseau
```
