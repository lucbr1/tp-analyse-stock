# Analyse de stock avec Docker

## Auteurs
Lucas Brun & Lucas Bieszczad

## Construction
docker build -t analyse-stock:v1 .

On utilise la base ubuntu:24.04 avec le FROM.
Puis avec la commande RUN on installe python3.
On se place ensuite dans le répertoire de travail /app avec le WORKDIR.
Puis on copie le script python "stock.py" avec COPY.
Et enfin au démarrage on exécute le script en utilisant python3 avec la commande CMD.

## Execution avec montages
docker volume create stock-rapport

docker run --rm -v "$(pwd)/entrees:/entrees:ro" -v stock-rapport:/resultats analyse-stock:v1

On monte le dossier "entrees" avec celui présent sur notre machine locale. Ce dossier se trouve dans le dossier où les commandes sont exécutés. Et on monte le dossier "resultat" au volume nommé créé précedemment ("stock-rapport").

## Tests et resultats
Voir verification.md

## Reproduction apres git clone

Construire l'image analyse-stock en se plaçant dans le dossier du DockerFile: `docker build -t analyse-stock:v1 .`

Création du volume nommé pour stocker les résultats : `docker volume create stock-rapport`

Création et exécution du conteneur :

 - avec suppression immédiate : `docker run --rm -v "$(pwd)/entrees:/entrees:ro" -v stock-rapport:/resultats analyse-stock:v1`

 - sans suppression immédiate : `docker run -v "$(pwd)/entrees:/entrees:ro" -v stock-rapport:/resultats --name analyse-stock analyse-stock:v1`

## Informations supplémentaires

Le stock est faible lorsqu'il est inférieur ou égal à 5.
Si le stock est égal à 0 il est faible et en rupture.
