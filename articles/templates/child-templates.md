<!-- Filename: J4.x:Child_Templates / Display title: Modèles Enfant  -->


## Exemple travaillé

À partir de **Panneau Système → Modèles → Modèles du site**

- Sélectionnez *Détails et fichiers de Cassiopeia*.
- Sélectionnez le bouton *Créer un modèle enfant*.
- Remplissez la boîte de dialogue contextuelle du modèle enfant et
  sélectionnez le bouton Créer un modèle enfant :

![formulaire de création de modèle enfant](../../../en/images/templates/child-templates-create-green.png)

La sélection de Cassiopeia - Default dans le champ Styles de modèle
supplémentaires semble inutile (est-ce un bug ?).

- Sélectionnez *Fermer* dans la barre d'outils pour fermer le formulaire
  du modèle parent.
- Sélectionnez le nouveau modèle, *Détails et fichiers de
  Cassiopeia_green*, dans la liste des modèles.

À ce stade, il y a une structure de fichiers mais un seul fichier existe :
templateDetails.xml. Ce fichier peut être modifié si vous souhaitez
changer certains aspects de la configuration du modèle, par exemple des
positions de modèle à ajouter ou supprimer.

### Créer un fichier user.css

- Sélectionnez le bouton *Nouveau fichier* dans la barre d'outils.
- Dans le formulaire *Créer ou télécharger un nouveau fichier*, assurez-vous
  de sélectionner le dossier `css`.
- Remplissez le nom du fichier avec `user`. NE PAS ajouter de suffixe !
- Sélectionnez le type de fichier `.css`.
- Sélectionnez le bouton *Créer*.

![formulaire de création du fichier user css](../../../en/images/templates/child-templates-create-green-user-css.png)

Le fichier user.css est vide, prêt pour que vous y saisissiez des styles
personnalisés. Commencez par entrer le code suivant pour le thème vert :
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
    a, a:hover, a:focus {
      color: darkgreen;
    }
    .btn-info {
        background-color: darkgreen;
        border-color: #30638d;
        color: #fff;
    }
    .btn-primary, .btn-primary:focus, .btn-primary:hover {
        background-color: darkgreen;
        border-color: var(--cassiopeia-color-hover);
    }

    .btn-check:focus + .btn-info, .btn-info:focus, .btn-info:hover {
        background-color: darkgreen;
        border-color: #264f71;
        color: #fff;
    }
```
Vous devrez peut-être revenir à ce fichier user.css pour ajouter plus de
styles plus tard.

- Sélectionnez *Enregistrer & Fermer* ou séparément, *Enregistrer* puis
  *Fermer le fichier*.
- Sélectionnez *Fermer* pour fermer le formulaire de personnalisation.

### Élément de menu

À ce stade, un élément de menu est nécessaire pour exploiter le modèle
enfant. Une nouvelle installation de Joomla 4 a le menu principal dans
la position de la barre latérale droite avec un élément. Cela semble être
une bonne place pour un nouvel élément de menu.

- Sélectionnez **Menus → Menu principal** dans le menu de
  l'administrateur.
- Sélectionnez le bouton *Nouveau* dans la barre d'outils.
- Entrez un titre approprié, *Articles en vedette verts* semble
  approprié pour ce cas.
- Sélectionnez le **Type d'élément de menu → Sélectionner**.
- Choisissez un type d'élément de menu dans la boîte de dialogue contextuelle
  de type d'élément de menu — Articles en vedette dans cet exemple.
- Sélectionnez *cassiopeia_manual - Default* dans le champ de formulaire
  *Style de modèle*.

![formulaire de modification d'élément de menu de modèle enfant](../../../en/images/templates/child-templates-create-green-menu-item.png)

- Pour le bien de la capture d'écran suivante, la disposition du blog a
  été réglée sur Articles principaux : 0, Articles d'introduction : 3 et
  Direction colonnes multiples : En travers.

### Vue du site

- Sur la page d'accueil de votre site, sélectionnez l'élément de menu
  nouvellement créé.

![site montrant le modèle de thème vert personnalisé](../../../en/images/templates/child-templates-green-site-result.png)

### Modifier le style

- Sélectionnez **Système → Panneau Modèles → Styles de modèle du
  site** dans le menu de l'administrateur.
- Sélectionnez *Cassiopeia_green - Default* dans la liste des styles.
- Changez le nom du style en *Cassiopeia Vert*. Cela permet seulement
  d'améliorer le nom tel qu'il apparaît dans les listes.
- Sélectionnez *Enregistrer et fermer*.

*Traduit par openai.com*

