# TP2 : analyse complète du corpus de 1964
Le notebook

s_analyse_complete.ipynb réunit les quatre travaux faits sur le corpus des journaux de 1964 dans un seul notebook, dans l'ordre :

Mots-clés (YAKE) : extraction des expressions de deux mots les plus caractéristiques de quelques journaux.
Nuage de mots : comptage du nombre de journaux où apparaît chaque mot, retrait des mots inutiles (avec une raison pour chacun), puis génération du nuage (1964_etape3.png).
Entités nommées (spaCy) : personnes, organisations et lieux. Chaque entité compte une fois par journal, les entrées parasites sont écartées et seules celles présentes dans au moins 5 journaux sont gardées.
Analyse de sentiment : 10 phrases tirées au hasard, analysées avec TextBlob-FR (polarité et subjectivité) puis avec un modèle transformers (label et score). Un tableau final résume les résultats.

Les imports et la configuration sont en haut du notebook.

Comment le lancer
Le notebook est dans tps/tp2/. Les journaux doivent être dans data/txt/ à la racine du projet, et les fichiers sont lus depuis ../../data/txt.
Lancez d'abord la cellule d'installation, puis exécutez les cellules dans l'ordre.
Les cellules d'installation utilisent uv pip et ne sont à lancer qu'une fois.
Réglages importants
year = 1964 : l'année étudiée.
SEUIL = 5 : une entrée n'est gardée que si elle apparaît dans au moins 5 journaux.
La graine random.seed(4) fixe le tirage des 10 phrases.
État du travail
Partie 1 (mots-clés) : faite.
Partie 2 (nuage de mots) : faite ; la conclusion reste à rédiger.
Partie 3 (entités nommées) : les listes d'exclusion des personnes et des organisations sont à compléter (marquées TODO) ; les lieux sont faits. La conclusion reste à rédiger.
Partie 4 (sentiment) : faite ; la lecture des résultats reste à rédiger.
Conclusion générale : à rédiger pour le rapport final.