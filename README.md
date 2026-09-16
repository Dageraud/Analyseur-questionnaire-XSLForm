# Analyseur de questionnaire XLSForm

Ce projet consiste à écrire un programme qui va générer l'ensemble des chemins possibles que l'on peut rencontrer à partir d'un fichier XLSForm (questionnaire).

* **Fichier d'entrée :** Classeur Excel composé de 3 feuilles (`survey`, `choices` et `settings`).
* **Fonctionnement :** Le programme va analyser les logiques indiquées au niveau de la feuille `survey`, établir une liaison entre les questions de `survey` et les réponses possibles dans `choices`, valider ces logiques, et enfin générer la liste de tous les chemins possibles ainsi qu'un graphe / arborescence récapitulatif.

> **Pour plus de détails sur le contexte, les types de données, et l'analyse technique du projet, veuillez consulter les [Spécifications Techniques (specs.md)](specs.md).**
