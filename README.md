# inventaire-legacy

## Présentation

Dépôt réalisé dans le cadre du TP 06 « Reprendre un dépôt et livrer une version »

Le projet nous a été confié dans un état dégradé : historique illisible, fichiers inutiles
versionnés, secret commité, branches en conflit et aucune version publiée.
L'objectif est de le remettre en état puis de livrer la version 1.0.0.

## Équipe

Hevans DILOUAKANA
Jeffrey VODOUHE
Baptiste BAZABAS
Arman MELKONYAN

## Description du programme

Programme Java de gestion d'inventaire, composé de deux classes :

`Panier` : additionne des prix hors taxes et calcule le total toutes taxes comprises ;
`Stock` : enregistre les entrées et les sorties d'articles, et refuse une sortie
  supérieure à la quantité disponible.

## Prérequis

- JDK 17 ou plus récent 


## Compilation et exécution

```bash
javac -d out src/*.java
java -cp out Panier
```

## Contribuer

Les règles (nommage des branches, format des messages de commit, Pull Requests)
sont décrites dans [CONTRIBUTING.md](CONTRIBUTING.md).

## Licence

Projet distribué sous licence MIT. Voir [LICENSE](LICENSE).