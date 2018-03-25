# Docker

- S'imaginer un container comme un espace clôt, avec seulement un environnement d'exécution<sup>[1]</sup> léger (e.g. `python:2.7-slim`, `openjdk:8-jdk-alpine`, ...), des ports qu'on ouvre et qu'on ferme pour communiquer avec l'environnement extérieur (e.g. `EXPOSE 80`), des fichiers qu'on place à l'intérieur et qui représentent notre app (e.g. `ADD . /app`), des variables d'environnement qu'on ajoute pour configurer l'espace (e.g. `ENV NAME World`) et des exécutions qu'on contrôle (e.g. `CMD ["python", "app.py"]`) pour lancer notre app ou nos services.


<span style="font-size:90%"><sup>[1]</sup> runtime environment</span>