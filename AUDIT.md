Liste des erreurs : 

- Mauvais messages pour les commit : Ils ne respectent aucun format et ne donnent pour la plupart aucune indication sur ce qui a été fait
- Le head pointe sur un commit qui n'est pas le dernier réalisé

- Secret versionné : le fichier .env contenant une clé d'API est présent dans l'historique (commit 2e26a12 "fix"). Action : le retirer de tout l'historique avec git filter-repo, puis révoquer la clé, car le dépôt est déjà public
- Fichiers inutiles versionnés : target/Panier.class (fichier compilé) et src/Panier.java.bak (copie de sauvegarde)