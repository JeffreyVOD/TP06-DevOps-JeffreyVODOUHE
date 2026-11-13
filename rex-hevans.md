## Ce que j'ai fait

### 1. Préparer mon environnement et comprendre le dépôt

- Création d'une clé SSH (ed25519) et ajout à mon compte GitHub.
- Exécution de `creer-depot.sh` en local pour reproduire l'état initial du dépôt
  et l'analyser avant toute modification (`git ls-files`, `git log --all --graph`,
  `git shortlog -sne --all`).
- Repérage des défauts : `.env` commité, `target/Panier.class` et `Panier.java.bak`
  versionnés, messages de commit illisibles, double identité de Marc, branche morte
  `test-marc`, conflit entre `arrondi` et `nouvelle-tva`.

### 2. Organiser le suivi du travail

- Vérification et configuration des flux automatiques du board GitHub, voir 
 que les automatisations fonctionnaient, pour qu'une issue arrive seule dans « Todo » et passe
en « Fait » quand sa Pull Request est fusionnée. Ça nous évite de déplacer les cartes
à la main et le board reste fidèle à l'avancement réel.
- Création de l'issue #18 pour mon REX, avec un critère de fin et des conditions de validation.

### 3. Rédiger et corriger la documentation

- **README** (issue #4, PR #9) : première version, puis correction après 9 commentaires
  de revue : vrais titres Markdown, liste de l'équipe à 4 membres, prérequis JDK 17,
  commandes de compilation et d'exécution, lien vers `CONTRIBUTING.md`.
  J'ai retiré la section « Configuration » après avoir vérifié que le programme
  ne lit aucun fichier `.env`.
- **Licence** (issue #5, PR #10) : correction de la ligne du copyright après la revue
  de iampigtrol, qui signalait l'absence d'Arman MELKONYAN.

### 4. Vérifier l'historique du dépôt

- Contrôle sur un clone frais avec `git log --all --oneline -- .env` : le commit
  `2e26a12` (« fix ») contenait encore `.env`, malgré une première réécriture.
- Confirmation avec `git branch -r --contains 2e26a12` : les 12 branches distantes
  étaient concernées, `main` comprise.
- Signalement à Jeffrey avec les commandes de correction (`git filter-repo`).

## Ce qui a coincé

**Le réseau de l'école bloquait SSH.** Après avoir configuré ma clé SSH, le clonage
échouait avec `port 22: Connection timed out`. Ce n'était pas ma clé : le port 22
était bloqué. Je suis passé par HTTPS, qui fonctionnait.

**Mon premier README a été refusé en revue.** Je pensais qu'il était correct, mais
il ne contenait aucun vrai titre Markdown, il oubliait un membre de l'équipe
et ne disait pas comment compiler. Les neuf commentaires m'ont montré que je n'avais
pas relu mon fichier dans l'onglet « Aperçu » avant d'ouvrir la Pull Request.

**La réécriture de l'historique m'a désorienté.** Lors d'un `git fetch`, toutes
les branches sont apparues en `forced update`. Mon clone reposait sur l'ancien
historique, et pousser depuis ce clone aurait pu réintroduire le `.env`. J'ai dû
supprimer mon clone et repartir d'un clone propre.

**Le secret n'avait pas vraiment disparu.** Après cette réécriture, je pensais
le problème réglé. En vérifiant, j'ai découvert que le commit contenant la clé
était toujours présent dans toutes les branches.

## Ce que je referais autrement

- **Préparer mon environnement avant le TP** : vérifier `javac -version`,
  `git filter-repo --version` et ma connexion à GitHub dès le début, plutôt
  que de découvrir les manques au moment d'en avoir besoin.
- **Relire mon travail comme un relecteur** : afficher l'aperçu Markdown
  et me relire avant d'ouvrir une Pull Request, pour ne pas faire perdre de temps
  à l'équipe sur des erreurs évitables.
- **Suivre la convention de nommage dès la première branche** : ma branche
  `docs/readme` aurait dû s'appeler `docs/4-readme`, comme le reste de l'équipe.
- **Toujours vérifier plutôt que supposer** : après une opération sensible comme
  une réécriture d'historique, contrôler le résultat sur un clone frais
  avec `git log --all -- .env`. C'est cette vérification qui a révélé que le secret
  était toujours public.
- **Mieux se coordonner pendant une réécriture** : convenir à l'avance que personne
  ne pousse pendant l'opération, et que tout le monde re-clone juste après.