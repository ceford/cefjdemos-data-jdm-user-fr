<!-- Filename: Customising_the_Smart_Search_results_page / Display title: Remplacements de disposition de recherche intelligente  -->

## Pages de Résultats

Le composant de Recherche Intelligente comporte cinq fichiers de mise en page que vous pouvez personnaliser à votre guise. Pour démarrer le processus à partir du menu de l'administrateur :

* Sélectionnez **Système / Modèles du site / Détails et fichiers de Cassiopeia**.
* Sélectionnez l'onglet **Créer des remplacements**.
* Dans le panneau Composants, sélectionnez **com_finder**.
* Sélectionnez l'élément **Recherche**.
* Dans le panneau de l'Éditeur, sélectionnez **html / com_finder / search** pour voir la liste des fichiers de remplacement créés.

Ces fichiers ne seront pas affectés par les mises à jour de Joomla, mais il se peut que vous soyez rappelé de les vérifier si les sources originales sont mises à jour.

## La Vue de Recherche (Disposition par Défaut)

La vue de recherche par défaut est divisée en plusieurs parties : la disposition par
défaut, la disposition du formulaire, la disposition des résultats et la disposition du tri.

### La disposition par défaut (default.php)

Cette disposition est très simple. Elle définit simplement la structure dans laquelle
le formulaire de recherche et les résultats de recherche sont affichés. Cette disposition
est également responsable du chargement de la feuille de style CSS par défaut pour la
recherche intelligente qui se trouve dans `media/com_finder/css/finder.css`, donc vous
pourriez vouloir la modifier pour charger vos propres règles CSS pour la recherche
intelligente.

### La disposition du formulaire (default_form.php)

Cette disposition définit le code nécessaire pour que le formulaire de recherche fonctionne
correctement. La disposition utilise du code JavaScript, donc vous devez prendre soin de
préserver les sélecteurs qui ne devraient pas être modifiés à moins de savoir ce que vous
faites.

La méthode de vue `getFields` inclut un certain nombre de champs cachés qui sont
nécessaires pour une recherche fiable. Le terme de recherche est défini par le champ
d'entrée avec le nom "q".

### La disposition des résultats (default_results.php)

Cette disposition produit la liste des résultats correspondants pour le terme de
recherche. Elle gère également la pagination et charge des dispositions pour chaque
résultat de recherche individuel.

### La disposition de résultat (default_result.php)

C'est la disposition chargée pour afficher un seul résultat.

### La disposition du tri (default_sorting.php)

Cet élément n'est présent que si « Afficher les champs de tri » est réglé sur Oui et
qu'un ou plusieurs champs de tri supplémentaires sont sélectionnés dans l'onglet Avancé
de l'élément de menu.

*Traduit par openai.com*

