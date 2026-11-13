# REX — Arman MELKONYAN (`iampigtrol`)

## Ce que j'ai fait

### 1. Relire les Pull Requests de l'équipe
J'ai relu les cinq Pull Requests ouvertes, en commentant à chaque fois une ligne précise du diff :

| PR | Ma revue | Ce que j'ai relevé |
|---|---|---|
| #9 README | Request changes | Il manquait mon nom dans l'équipe (ligne 15) |
| #10 LICENSE | Request changes | Il manquait mon nom dans le copyright (ligne 3) |
| #2 AUDIT | Request changes | Donner le hash exact du commit qui contient le `.env` (`2e26a12`), prévoir `git filter-repo` et la révocation de la clé ; coquille « ausunc » |
| #11 CONTRIBUTING | Approve | Coquille « de un » → « d'un », que j'ai corrigée moi-même (commit `3656cbf`) |
| #12 .gitignore | Approve | Le `.gitignore` empêche `.env` de revenir, mais le fichier reste dans l'historique : il faut encore un `git filter-repo` |

### 2. Le conflit entre `arrondi` et `nouvelle-tva` (J3)
- **Issue #13**, avec le label `bug`, le milestone `v.1.0.0` et un critère de fin.
- **Prédiction datée** dans `Journal.md` (13/11/2026, 14:18), commitée avant la fusion (commit `ee25d65`).
- Fusion des deux branches sur `fix/13-conflit-tva` : `arrondi` est passée seule, `nouvelle-tva` a donné un **CONFLICT** sur le `return` de `totalTtc()`, comme prévu.
- **Résolution** (commit `4ab2644`) : `Math.round(total * 1.055 * 100) / 100.0`. On garde le taux de `nouvelle-tva` et l'arrondi de `arrondi`. Le programme affiche `16.35` au lieu de `16.3525`.
- J'ai demandé le taux au commanditaire, qui a confirmé la nouvelle TVA à 5,5 % (commit `a7479ce`, commentaire sur la PR).
- **Pull Request #14**, avec `Closes #13` et la justification complète.

## Ce qui a coincé

- **Le secret.** Le `.env` a été supprimé par un nouveau commit, mais il reste lisible dans l'ancien commit `2e26a12`, alors que le dépôt est déjà public. Il aurait fallu le retirer de l'historique **avant** le premier push. Maintenant, il faut réécrire l'historique, faire un push forcé, que tout le monde reclone, et révoquer la clé.
- **La fusion bloquée.** La protection de `main` demande **2 approbations**, alors que l'énoncé en demande une. Même après ma revue, les PR #11 et #12 ne pouvaient pas être fusionnées tant qu'un autre membre n'avait pas approuvé.
- **Au début, je ne savais pas ce qu'était une revue** : j'ai dû comprendre la différence entre *Comment*, *Approve* et *Request changes*, et comment commenter une ligne précise du diff.
- **Le choix de la TVA** n'était pas une question de Git : il a fallu demander au commanditaire au lieu de deviner.

## Ce que je referais autrement

- **Prendre un chantier dès le début du TP**, au lieu d'arriver quand les autres avaient déjà commencé : j'aurais pu prendre l'issue #8, qui m'était assignée.
- **Poser la question métier avant d'écrire ma prédiction**, pour que la justification s'appuie sur la réponse du client dès le départ.
- **Vérifier `git log --all -- .env` avant toute publication** : c'est la commande qui montre que le secret est encore dans l'historique.
