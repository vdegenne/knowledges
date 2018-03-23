# Docker

- S'imaginer un container comme un espace clôt, seulement avec des ports qu'on ouvre et qu'on ferme pour communiquer avec l'environnement extérieur, avec un environnement d'exécution<sup>[1]</sup> "runtime" léger (e.g. `python:2.7-slim`, `openjdk:8-jdk-alpine`, ...), des fichiers qu'on place à l'intérieur (et qui représentent notre app), des variables d'environnement qu'on ajoute pour configurer l'espace et des exécutions qu'on contrôle (e.g. `CMD ["python", "app.py"]`) pour lancer notre app ou nos services.


<span style="font-size:90%"><sup>[1]</sup> : runtime environment</span>