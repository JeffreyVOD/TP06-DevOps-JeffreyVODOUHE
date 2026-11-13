# Contribuer à inventaire-legacy

## Le principe

1. Chaque modification part d'une **issue**.
2. On travaille sur une **branche** créée depuis `main` à jour.
3. On ouvre une **Pull Request** qui ferme l'issue.
4. Deux autres membres de l'équipe la **relisent** et l'approuvent.
5. On fusionne.

Personne ne pousse directement sur `main` : la branche est protégée.

## Nommage des branches

Format : `<type>/<numéro-issue>-<description-courte>`, en minuscules, avec des tirets.

| Type | Usage | Exemple |
|------|-------|---------|
| `feat` | nouvelle fonctionnalité | `feat/12-export-csv` |
| `fix` | correction de bug | `fix/7-tva-panier` |
| `docs` | documentation uniquement | `docs/3-changelog` |
| `chore` | ménage, configuration, outillage | `chore/5-retirer-target` |

## Messages de commit

On suit [Conventional Commits](https://www.conventionalcommits.org/fr/) :

<type>(<portée optionnelle>): <résumé à l'impératif, 72 caractères max>

<corps optionnel : pourquoi ce changement, pas comment>

Refs #<numéro-issue>

- Types : `feat`, `fix`, `docs`, `chore`, `refactor`, `test`.
- Le résumé dit **ce que fait** le commit.
- Un commit = un changement cohérent.

## Pull Requests

- Le titre suit le même format qu'un message de commit.
- La description contient le quoi, le pourquoi et `Closes #<numéro>`.
- Une PR = une issue.
- Deux autres membres doivent approuver la PR avant la fusion.
- Le code doit compiler avant de demander une revue.

## Revue

- Le relecteur commente une ligne précise du diff.
- Il vérifie la compilation, les conventions et l'absence de fichiers parasites.
- L'auteur répond à chaque commentaire avant la fusion.

## Après la fusion

- On supprime la branche sur GitHub et en local.
- On déplace la carte de l'issue dans la colonne « Fait ».

## Secrets

Aucun secret dans le dépôt. Les valeurs vont dans `.env` (ignoré par Git) et les nouvelles variables sont documentées dans `.env.example`, sans valeur.