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

docker run --rm -v "${PWD}/entrees:/entrees:ro" -v "${PWD}/resultats:/resultats" analyse-stock:v1

On monte le dossier "entrees" avec celui présent sur notre machine locale. Ce dossier se trouve dans le dossier où les commandes sont exécutés. Et on monte le dossier "resultat" au volume nommé créé précedemment ("stock-rapport").

## Tests et resultats
Renvoyer vers preuves/verification.md et decrire le resultat attendu.

## Reproduction apres git clone
Donner les etapes exactes, notamment la creation de resultats.
