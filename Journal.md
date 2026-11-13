# TP 06 — Reprendre un dépôt et livrer une version

Hash du premier commit : a718f0a2e2934d1448268c511a3f6229349ee206

## J3 — Conflit entre `arrondi` et `nouvelle-tva` (issue #13)

### Prédiction (13/11/2026, 14:18, avant toute fusion)

**Ce que je pense voir** : la première fusion (`arrondi`) passera sans problème. La seconde (`nouvelle-tva`) affichera un **CONFLICT** dans `src/Panier.java`. Les deux branches modifient la même ligne, le `return` de `totalTtc()`, que `main` n'a pas touchée : Git ne peut pas choisir tout seul.

**La version qui doit l'emporter** : **aucune des deux seule, un mélange.**
- De `arrondi`, je garde l'**arrondi au centime** : un prix TTC doit tomber au centime, quel que soit le taux. Sans arrondi, `15.5 * 1.055` affiche `16.352499999999999`.
- De `nouvelle-tva`, je garde le **nouveau taux de 5,5 %** : c'est l'objet de la branche. À confirmer avec le commanditaire, puisque c'est une décision métier, pas une décision Git.
