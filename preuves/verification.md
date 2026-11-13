# Verification du projet

Pour chaque cas, coller la commande, sa sortie, et votre explication.

1. Jeu initial de quatre articles.

docker run --rm -v "$(pwd)/entrees:/entrees:ro" -v stock-rapport:/resultats analyse-stock:v1

References : 4
Unites : 16
Valeur totale : 670.00 EUR
References en stock faible : 3
References en rupture : 1

Les entrées sont lues depuis le fichier local. Les résultats sont enregistrés dans le volume nommé et affichés dans la console. Les valeurs sont correctes.

2. CSV modifie sans reconstruction.

docker run --rm -v "$(pwd)/entrees:/entrees:ro" -v stock-rapport:/resultats analyse-stock:v1

References : 4
Unites : 26
Valeur totale : 770.00 EUR
References en stock faible : 2
References en rupture : 0

Comme on lit directement le fichier local, les valeurs ont été modifiées sans reconstruction nécessaire. Nous avons mis le stock de câbles à 10 et leur prix également à 10.

3. Tentative d'ecriture dans entrees en lecture seule.



4. Rapport relu depuis un autre conteneur avec le meme volume nomme.



5. Entree absente, vide ou invalide.

docker run --rm -v "$(pwd)/entrees:/entrees:ro" -v stock-rapport:/resultats analyse-stock:v1

Erreur : invalid literal for int() with base 10: ''

En enlevant un stock au câbles, une erreur est affichée dans la console.