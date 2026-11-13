# TP 06 — Reprendre un dépôt et livrer une version

Hash du premier commit : a718f0a2e2934d1448268c511a3f6229349ee206

## J3 — Conflit entre `arrondi` et `nouvelle-tva` (issue #13)

### Prédiction (13/11/2026, 14:18, avant toute fusion)

**Ce que je pense voir** : la première fusion (`arrondi`) passera sans problème. La seconde (`nouvelle-tva`) affichera un **CONFLICT** dans `src/Panier.java`. Les deux branches modifient la même ligne, le `return` de `totalTtc()`, que `main` n'a pas touchée : Git ne peut pas choisir tout seul.

**La version qui doit l'emporter** : **aucune des deux seule, un mélange.**
- De `arrondi`, je garde l'**arrondi au centime** : un prix TTC doit tomber au centime, quel que soit le taux. Sans arrondi, `15.5 * 1.055` affiche `16.352499999999999`.
- De `nouvelle-tva`, je garde le **nouveau taux de 5,5 %** : c'est l'objet de la branche. À confirmer avec le commanditaire, puisque c'est une décision métier, pas une décision Git.

### Résultat réel

`git merge origin/arrondi` → `Merge made by the 'ort' strategy.`, sans conflit.

`git merge origin/nouvelle-tva` :

```
Auto-merging src/Panier.java
CONFLICT (content): Merge conflict in src/Panier.java
Automatic merge failed; fix conflicts and then commit the result.
```

```java
<<<<<<< HEAD
        return Math.round(total * 1.20 * 100) / 100.0;
=======
        return total * 1.055;
>>>>>>> origin/nouvelle-tva
```

**Prédiction confirmée** ✅ sur le conflit. Correction sur mon exemple : sans arrondi, le programme affiche en réalité `16.3525`, et non `16.352499999999999`. Ça reste 4 décimales pour un prix, donc l'arrondi reste nécessaire.

**Résolution retenue** :

```java
        return Math.round(total * 1.055 * 100) / 100.0;
```

Le programme affiche `16.35` (10 + 5,5 = 15,50 € HT, × 1,055 = 16,3525, arrondi à 16,35 € TTC). `javac src/*.java` compile.
