# Docker

## Commandes

- `docker ps` : liste les containeurs en marche.
- `docker ps -a` : liste les containeurs en marche et ceux qui sont arrêtés.
- `docker stop <container-name|id>` : arrête le containeur <container-name|id>.
- `docker rm <container-name|id>` : supprime le containeur <container-name|id> (en supposant qu'il est arrêté).
- `docker images` : liste toutes les images.
- `docker rmi <image-name|id>` : supprime l'image <image-name|id>.
- `docker ps/images -q` : liste seulement les IDs (e.g. `docker rm $(docker ps -a -q)`)

Assigner un nom à un containeur est vraiment important. Cela permet de pouvoir utiliser les commandes ci-dessus avec la forme <container-name> (plus pratique que de manipuler les ids). Mais cela permet aussi de pouvoir référencer facilement des contaneurs entre eux sur un même réseau (voir section `Network` et commande ci-dessous).

- `docker run --rm -d --name my-container -p 80:8080 -e MY_ENV='hello world' --network <network-name> <image-name>`
    - `--rm` : supprime le containeur lorsqu'il s'arrête
    - `-d` : fait tourner le containeur en arrière-plan (sinon les sorties standard sont affichées sur l'entrée standard où le containeur est exécutés).
    - `--name` : permet de donner un nom au containeur (voir remarque ci-dessus).
    - `-p <host-port:container-port>` : mappe le port <container-port> du containeur au port <host-port> de l'hôte docker.
    - `-e <env>=<value>` : créer une variable d'environnement et l'envoie au processus exécuté.
    - `--network <network-name>` : créer le containeur dans le réseau <network-name>.

- `docker exec -it <container-name> <command>` : exécute une commande disponible dans le containeur <container-name>.

## Container

- S'imaginer un container comme un espace clôt, avec seulement un environnement d'exécution (runtime environment) léger (e.g. `python:2.7-slim`, `openjdk:8-jdk-alpine`, ...), des ports qu'on ouvre et qu'on ferme pour communiquer avec d'autres containeurs (e.g. `EXPOSE 80`), des fichiers qu'on place à l'intérieur et qui représentent notre application (e.g. `COPY . /usr/src/app`), des variables d'environnement qu'on ajoute pour configurer l'espace (e.g. `ENV HELLO world`) et des exécutions qu'on contrôle (e.g. `CMD python app.py`) pour lancer notre application ou nos services.


## Network

- La communication inter-containeurs par les noms ne fonctionne pas avec le bridge docker par défaut. Il faut créer un nouveau réseau (voir ci-dessous).
- Exemple de communication entre containers dans un même réseau
```bash
docker network create my-network
docker run -d --name my-pgsql --network my-network -p 5432:5432 -e POSTGRES_PASSWORD=secret postgres
docker run -d --rm --name my-app --network my-network -p 80:8080 myapp
# now inside my-app we can connect to the database with host `my-pgsql:5432`
```


