# Spécifications du projet : Analyseur de questionnaire XLSForm

## 1. Description
Le projet consiste à développer un utilitaire (moteur d'analyse / CLI) capable d'analyser un questionnaire au format XLSForm afin d'identifier tous les chemins et sauts possibles générés par les structures de contrôle (skip logic / relevant). L'outil modélisera ensuite ces chemins sous forme de graphe ou d'arborescence.

## 2. Contexte et Problématique
La conception de questionnaires numériques (via KoboToolbox, ODK, etc.) nécessite souvent des formulaires longs et complexes avec de multiples sauts conditionnels. 
Bien que la création directe via Excel (XLSForm) soit beaucoup plus rapide et pratique que les interfaces web (qui nécessitent de nombreux clics), la phase de **test des conditions de sauts** reste un point noir.

Actuellement, pour s'assurer que les sauts fonctionnent correctement, les équipes doivent réaliser de multiples tests manuels de bout en bout, en essayant chaque combinaison de réponses, ce qui peut prendre plusieurs jours de travail pour plusieurs personnes. 
 
L'idée est de créer un programme qui automatise cette vérification. En extrayant à l'avance toutes les arborescences possibles, on s'assure que le questionnaire est robuste avant le déploiement sur le terrain.

## 3. Types de Données (Format d'entrée)
Le fichier attendu est un classeur Excel `.xlsx` respectant le standard XLSForm, composé de 3 feuilles principales :
* **survey** : Feuille principale listant les variables (questions), leur type (`text`, `select_one`, `select_multiple`, etc.), leur identifiant (`name`), leur libellé (`label`), les conditions d'affichage (`relevant`), les contraintes (`constraint`), et le caractère obligatoire (`required`).
* **choices** : Le dictionnaire des modalités de réponses. Elle associe un nom de liste (`list_name`) aux différentes options de réponse (code `name` et libellé `label`).
* **settings** : Paramètres globaux du questionnaire (titre, version, etc.).

## 4. Déroulement du Programme (Workflow)
L'exécution du programme suivra ces étapes :
1. **Lecture du fichier** : Téléversement et parsing du fichier XLSForm (`.xlsx`).
2. **Vérification de la structure** : Validation de la présence des feuilles obligatoires (`survey`, `choices`, `settings`) et des colonnes requises.
3. **Analyse des logiques** : Évaluation des colonnes `relevant` et `constraint`.
4. **Génération des chemins** : Calcul de tous les parcours (chemins) possibles en fonction des choix multiples.
5. **Restitution** : 
   - Génération d'une liste détaillée des chemins.
   - Génération d'un graphe ou d'une représentation visuelle de l'arborescence.

## 5. Analyse Descendante
*(À définir)*
