# REX — Arman MELKONYAN (`iampigtrol`)

## Ce que j'ai fait

### 1. Le conflit entre `arrondi` et `nouvelle-tva` (J3)
- J'ai ouvert l'**issue #13**, avec le label `bug`, le milestone `v.1.0.0` et un critère de fin.
- J'ai écrit et commité ma **prédiction datée** dans `Journal.md` (13/11/2026, 14:18) **avant** la fusion (commit `cdc5b8a`).
- J'ai fusionné les deux branches sur `fix/13-conflit-tva` :
  - `arrondi` est passée seule ;
  - `nouvelle-tva` a donné un **CONFLICT** sur le `return` de `totalTtc()`, comme prévu.
- **Résolution** (commit `9ab0e41`) : `Math.round(total * 1.055 * 100) / 100.0`. Je garde le taux de `nouvelle-tva` et l'arrondi de `arrondi`. Le programme affiche `16.35` au lieu de `16.3525`.
- J'ai demandé le taux au commanditaire, qui a confirmé la nouvelle TVA à 5,5 %. C'est noté dans le journal (commit `d06faa4`) et dans un commentaire sur la PR.
- J'ai ouvert la **PR #14**, avec `Closes #13` et la justification complète. Elle a été approuvée par Jeffrey et Hevans, puis je l'ai fusionnée. L'issue #13 s'est fermée automatiquement.

### 2. Relire les Pull Requests de l'équipe
J'ai commenté à chaque fois une ligne précise du diff, puis j'ai **revérifié la correction** avant d'approuver :

| PR | Ma première revue | Ce que j'ai relevé | Suite |
|---|---|---|---|
| #9 README | Request changes | Il manquait mon nom dans l'équipe (ligne 15) | Corrigé par Hevans (`06cf3c5`), j'ai approuvé, puis fusionné |
| #10 LICENSE | Request changes | Il manquait mon nom dans le copyright (ligne 3) | Corrigé par Hevans (`108fa33`), j'ai approuvé, puis fusionné |
| #2 AUDIT | Request changes | Donner le hash exact du commit qui contient le `.env` (`2e26a12`), prévoir `git filter-repo` et la révocation de la clé ; coquille « ausunc » | Corrigé par Baptiste (`178c4e0`), j'ai approuvé |
| #11 CONTRIBUTING | Approve | Coquille « de un » → « d'un » (que j'ai corrigée, `fa35761`) ; puis les ``` retirés autour du format de commit (ligne 28) | J'ai remis le bloc de code (`116c692`), puis fusionné |
| #12 .gitignore | Approve | Le `.gitignore` empêche `.env` de revenir, mais le fichier reste dans l'historique | Fusionnée ; l'issue #8 s'est fermée |
| #17 REX de Jeffrey | Request changes | La réécriture a retiré `target/` et `Panier.java.bak`, mais **pas le `.env`** (ligne 18) ; la protection de `main` a-t-elle été rétablie ? | En attente |

J'ai fusionné **cinq PR** dans `main` : #10, #9, #12, #11 et #14.

### 3. Signaler le secret encore présent
Après la réécriture de l'historique, `git log --all -- .env` renvoyait toujours `2e26a12`. Je l'ai signalé à Jeffrey dans un commentaire sur la PR #12, avec la commande à lancer : `git filter-repo --path .env --invert-paths`.

## Ce qui a coincé

- **Le secret.** Le `.env` a été supprimé par un nouveau commit, mais il reste lisible dans l'ancien commit `2e26a12`, alors que le dépôt est déjà public. Il aurait fallu le retirer de l'historique **avant** le premier push. Maintenant, il faut réécrire l'historique, faire un push forcé, que tout le monde reprenne une copie à jour du dépôt, et révoquer la clé.
- **La réécriture d'historique au mauvais endroit.** Le `git filter-repo` qui a été poussé a retiré `target/` et `Panier.java.bak`, ce que l'énoncé demandait de faire seulement sur une copie jetable, et pas le `.env`. Tous les hashes ont changé : mes commits cités dans ce REX ont été réécrits (par exemple, ma résolution est passée de `4ab2644` à `9ab0e41`).
- **La fusion bloquée.** La protection de `main` demande **2 approbations**, alors que l'énoncé en demande une. Il fallait relancer les autres pour chaque PR.
- **Au début, je ne savais pas ce qu'était une revue** : j'ai dû comprendre la différence entre *Comment*, *Approve* et *Request changes*, et comment commenter une ligne précise du diff.
- **Le choix de la TVA** n'était pas une question de Git : il a fallu demander au commanditaire au lieu de deviner.

## Ce que je referais autrement

- **Prendre un chantier dès le début du TP**, au lieu d'arriver quand les autres avaient déjà commencé.
- **Poser la question métier avant d'écrire ma prédiction**, pour que la justification s'appuie sur la réponse du client dès le départ.
- **Vérifier `git log --all -- .env` avant toute publication**, et après toute réécriture : c'est la commande qui montre si le secret est encore dans l'historique.
- **Se mettre d'accord avant une réécriture d'historique** : qui la fait, sur quels fichiers, et à quel moment, pour éviter de la faire deux fois.
