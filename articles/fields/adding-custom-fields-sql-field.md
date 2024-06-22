<!-- Filename: J3.x:Adding_custom_fields/Sql_Field / Display title: Ajout de champs personnalisés/Champ SQL -->

## Champ Sql

**Les articles de cette série**

1.  Introduction
2.   Paramètres des champs
    personnalisés
3.   Champ
    Calendrier
4.   Champ Cases à
    cocher
5.   Champ
    Couleur
6.   Champ
    Editeur
7.   Champ Entier
    relatif
8.   Champ
    Liste
9.   Champ Liste
    d'images
10.  Champ
    Média
11.  Champ Bouton
    Radio
12.  Champ
    Répétabilité
13.  Champ
    Sql
14.  Champ
    Texte
15.  Champ Zone de
    texte
16.  Champ
    URL
17.  Champ
    Utilisateur
18.  Champ Groupe
    d'utilisateurs
19.  Comment grouper les champs
    personnalisés
20.  Quels sont les composants supportant les champs
    personnalisés
21.  Implémentation dans votre
    composant
22.  Utiliser les champs personnalisés dans vos
    substitutions

### Sql

Fournit une liste déroulante des entrées obtenues par l'exécution d'une
requête dans la base de données Joomla. La première liste de résultats
retournée par la requête fournit les valeurs de la liste déroulante.

#### Paramètres

Les paramètres spécifiques pour ce champ sont ː

- Multiple
  Si activé, permet le choix multiple de valeurs.
- Requête
  La requête SQL qui fournira les données pour la liste déroulante. La
  requête doit fournir deux colonnes ; une appelée 'value' qui va
  contenir les valeurs de la liste d'éléments ; l'autre appelée 'text'
  qui contient le texte affiché dans la liste déroulante.

#### Informations connexes

Lisez  Type de champ de formulaire
SQL.

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/d/d1/Sql_field_create-fr.png/800px-Sql_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/d/d1/Sql_field_create-fr.png 1.5x"
data-file-width="1018" data-file-height="724" width="800" height="569"
alt="Sql field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/e/e8/Sql-fr.png/800px-Sql-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/e/e8/Sql-fr.png 1.5x"
data-file-width="1013" data-file-height="546" width="800" height="431"
alt="Sql-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<img src="https://docs.joomla.org/images/1/1b/Sql_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="191"
width="800" height="191" alt="Sql field frontend-fr.png" />

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Repeatable_Field"
id="content-button" class="button expand success">Précédent : Champ
Répétable</a>
<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/Text_Field"
id="content-button" class="button expand">Suivant : Champ Texte</a>
