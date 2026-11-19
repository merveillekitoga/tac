
## Partie 1 : clustering des documents

### Première analyse

Dans un premier temps, j'ai adapté le notebook de clustering (`s2_clustering.ipynb`) aux journaux des années 1960 à 1969 du corpus CAMille. J'ai produit une visualisation des clusters pour 3, 4, 5 et 6 groupes.

Cette première analyse a révélé plusieurs problèmes :
- **Le prétraitement ne retirait pas la ponctuation.** L'instruction `text.translate(string.punctuation)` ne supprime rien : il faut une table de correspondance.
- **Les listes de mots étaient bruitées.** On trouvait des mots courants, des fragments d'OCR et des nombres (117, 2400, 1963). Les clusters ne correspondaient donc à aucune rubrique.
- **Les résultats changeaient à chaque exécution.** Le KMeans n'avait pas de graine fixe : deux exécutions identiques donnaient des découpages différents.

### Améliorations
 
Pour corriger ces problèmes, j'ai modifié le code en trois endroits :
- **La fonction de prétraitement** : la ponctuation est retirée avec `str.maketrans`, puis seuls les mots alphabétiques de plus de 2 lettres sont gardés. Les nombres et la plupart des fragments d'OCR disparaissent.
- **La reproductibilité** : le KMeans reçoit `random_state=0` et `n_init=10`. Chaque exécution donne alors le même résultat.

Après ces corrections, j'ai comparé 3 à 6 clusters. Les groupes stables sont les annonces (logement, emploi) et le sport. La politique et la culture se séparent à partir de 5 clusters, et une rubrique automobile apparaît à partir de 5 clusters également.

### Choix retenu

J'ai retenu **6 clusters**, parce que chacun correspond à une rubrique identifiable : politique, culture, sport, automobile, logement et emploi. Le groupe économique (cours, marché, actions) n'apparaît pas de façon stable : ses termes se répartissent entre les autres clusters selon le découpage.
.