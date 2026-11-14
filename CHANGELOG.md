# Changelog

Toutes les évolutions notables du projet sont notées dans ce fichier.

Format : [Keep a Changelog](https://keepachangelog.com/fr/1.1.0/). Versions : [Semantic Versioning](https://semver.org/lang/fr/).

## [1.0.0] - 2026-11-13

Première version publiée après la reprise du dépôt `inventaire-legacy`.

### Modifié
- Le total TTC du panier applique le nouveau taux de TVA de 5,5 % (au lieu de 20 %), validé par le commanditaire le 13/11/2026 (#14).
- Le total TTC est arrondi au centime : le panier d'exemple affiche `16.35` au lieu d'un montant à 4 décimales (#14).

### Ajouté
- `README.md` : présentation du projet, de l'équipe et du programme, prérequis et configuration (#9).
- `CONTRIBUTING.md` : nommage des branches, format des messages de commit, règles de Pull Request et de revue (#11).
- Licence MIT (#10).
- `AUDIT.md` : état des lieux du dépôt à la reprise, dont le secret versionné et les fichiers inutiles (#2).
- `.gitignore` complet : secrets, fichiers compilés (`target/`, `*.class`), sauvegardes (`*.bak`), fichiers d'IDE et système (#12).

### Supprimé
- Fichier compilé `target/Panier.class` et copie de sauvegarde `src/Panier.java.bak`, retirés du dépôt et de son historique (#12).

[1.0.0]: https://github.com/JeffreyVOD/TP06-DevOps-JeffreyVODOUHE/releases/tag/v1.0.0
