<!-- Filename: J4.x:Switching_Templates / Display title: Modification des modèles  -->

## Modèles de Site et d’Administrateur

Joomla 4 est livré avec un seul modèle de site, Cassiopeia, et un seul modèle d’administrateur, Atum. Vous pouvez obtenir des modèles supplémentaires auprès de fournisseurs tiers de modèles, gratuits et payants, et vous pouvez créer vos propres modèles, le plus facilement sous forme de modèles enfants.

Il est peu probable que vous souhaitiez utiliser un modèle d’administrateur alternatif, donc cet article ne couvre que les modèles de site alternatifs. À titre d’illustration, un modèle enfant a été créé avec un thème vert comme décrit dans l’article sur les Modèles Enfants. De plus, le site utilisé pour l’illustration a installé des Données d’Exemple de Test.  

## Style du Modèle par Défaut

Un de vos modèles doit être marqué comme le modèle par défaut. Il est utilisé pour toutes les pages sauf celles qui spécifient un modèle alternatif. Pour définir le modèle par défaut :

- Sélectionnez **Système → Panneau de Modèles → Styles de Modèle du Site**
  dans le menu Administrateur.
- Sélectionnez l'un des boutons dans la colonne Par Défaut.

![liste des styles de modèles du site](../../../en/images/templates/switch-templates-styles-list.png)

Jetez un coup d'œil à votre site pour vérifier que toutes les pages utilisent le modèle par défaut.

## Utilisation d'un style alternatif

Joomla vous permet de sélectionner un style pour une page spécifique à partir de son affectation au menu. La sélection peut être effectuée depuis le formulaire de style de modèle ou le formulaire de modification de menu. Les méthodes produisent le même résultat. La première méthode est plus pratique pour la sélection d'un groupe d'éléments de menu appartenant au même menu.

### Méthode d'affectation de menu du modèle

Depuis la liste des styles de modèles :

- Sélectionnez un style qui **n'est pas** défini comme par défaut. L'étoile jaune indique le style par défaut.
- Sélectionnez l'onglet Affectation de menu.
- Sélectionnez des éléments de menu individuels ou basculez tous les éléments d'un menu.
- Enregistrez

![onglet d'affectation du menu de la page d'édition de style des modèles](../../../en/images/templates/switch-templates-styles-edit-style-menu-assignment.png)

Dans cet exemple, tous les éléments de menu du menu `Main Menu Testing` ont été sélectionnés. Retournez sur votre site et sélectionnez n'importe lequel des éléments de menu qui devraient utiliser le modèle sélectionné.

### Méthode des détails du menu

Cette méthode est utilisée pour définir le modèle pour des éléments de menu individuels.

- Sélectionnez **Menus → \[Nom du menu\]** dans le menu Administrateur.
- Sélectionnez un lien d'élément de menu dans la colonne Titre pour ouvrir le formulaire de modification.
- Dans le champ **Style de modèle**, sélectionnez le style de modèle souhaité.
- Enregistrez

![formulaire d'édition d'éléments de menu montrant la sélection de style](../../../en/images/templates/switch-templates-styles-edit-menu-style.png)

Retournez sur votre site et sélectionnez l'élément de menu modifié pour vérifier qu'il s'affiche avec le style de modèle sélectionné.

*Traduit par openai.com*

