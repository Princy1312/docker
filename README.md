# docker

#  Introduction à Docker

Docker est un outil permettant de créer, déployer et exécuter des applications dans des **conteneurs**. Voici les étapes essentielles pour l'utiliser.

---

##  Étapes de base pour utiliser Docker

### 1. 🔧 Installation de Docker

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

---

##  Résumé

| Étape               | Commande clé                        |
|--------------------|-------------------------------------|
| Lancer un test     | `docker run hello-world`           |
| Télécharger image  | `docker pull <nom>`                |
| Lancer conteneur   | `docker run -d -p ...`             |
| Arrêter conteneur  | `docker stop <id>`                 |
| Construire image   | `docker build -t nom .`            |

---

