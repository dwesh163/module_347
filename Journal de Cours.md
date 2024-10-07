## 9 Septembre 2024

Installation de Docker Desktop depuis https://www.docker.com/products/docker-desktop/

### Listes des commandes Docker

#### 1. `docker version`

Affiche des informations détaillées sur la version de Docker installée sur le système, y compris les versions du client et du serveur.

```bash
docker version
```

#### 2. `docker search`

Recherche des images Docker disponibles dans le registre public Docker Hub.

```bash
docker search <nom_image>
```

#### 3. `docker image pull`

Télécharge (ou "pull") une image Docker depuis un registre (par défaut Docker Hub).

```bash
docker image pull <nom_image>
```

#### 4. `docker container run`

Crée et démarre un conteneur à partir d'une image Docker spécifiée. Vous pouvez ajouter des options pour le mode interactif, les ports, etc.

```bash
docker container run <options> <nom_image>
```

Exemples :

```bash
docker container run -it ubuntu bash
docker container run -d -p 8080:80 nginx
```

#### 5. `docker container rename`

Renomme un conteneur existant.

```bash
docker container rename <ancien_nom> <nouveau_nom>
```

#### 6. `docker container exec`

Exécute une commande dans un conteneur Docker en cours d'exécution.

```bash
docker container exec <options> <id_conteneur> <commande>
```

Exemple :

```bash
docker container exec -it <id_conteneur> bash
```

#### 7. `docker container ls`

Liste tous les conteneurs en cours d'exécution. Ajouter l'option -a pour afficher les conteneurs arrêtés.

```bash
docker container ls
docker container ls -a
```

#### 8. `docker image ls`

Liste toutes les images Docker disponibles localement.

```bash
docker image ls
```

#### 9. `docker container kill`

Arrête immédiatement un conteneur en cours d'exécution (en envoyant un signal SIGKILL).

```bash
docker container kill <id_conteneur>
```

#### 10. `docker container stop`

Arrête un conteneur en douceur en envoyant un signal d'arrêt (SIGTERM).

```bash
docker container stop <id_conteneur>
```

#### 11. `docker container rm`

Supprime un ou plusieurs conteneurs arrêtés.

```bash
docker container rm <id_conteneur>
```

#### 12. `docker image rm`

Supprime une ou plusieurs images Docker locales.

```bash
docker image rm <nom_image> <id_image>
```

## 23 Septembre 2024

Démarrer un docker MySql avec l'(image)[https://hub.docker.com/_/mysql] sur Docker hub

#### Pull image

```bash
docker pull mysql:latest
```

#### Run the image

```bash
docker run --name module374 -e MYSQL_ROOT_PASSWORD=1234 -e MYSQL_DATABASE=module374 -e MYSQL_USER=user -e MYSQL_PASSWORD=secret -p 3306:3306 -d mysql:latest
```

#### Enter in the docker

```bash
docker exec -it module374 mysql -p
```

## 30 Septembre 2024

Créer une image docker personnalisée avec un Dockerfile

```Dockerfile
# Utilisation de l'image officielle MySQL la plus récente
FROM mysql:latest

# Permettre à MySQL de démarrer sans mot de passe root
ENV MYSQL_ALLOW_EMPTY_PASSWORD=1

# Copie du fichier init.sql dans le répertoire où MySQL recherche les scripts
COPY init.sql /docker-entrypoint-initdb.d/
```