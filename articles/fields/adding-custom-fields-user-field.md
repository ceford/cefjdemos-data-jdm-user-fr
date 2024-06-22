<!-- Filename: J3.x:Adding_custom_fields/User_Field / Display title: Ajout de champs personnalisés/Champ Utilisateur -->

## Champ Utilisateur

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

### Utilisateur

Fourni un champ pour sélectionner un utilisateur dans une liste modale.
Ce champ affiche le nom d'utilisateur et enregistre l'ID de
l'utilisateur.

#### Paramètres

Il n’existe pas d'options particulière pour ce champ.

#### Informations connexes

Lisez  Type de champ de formulaire
Utilisateur.

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/7/71/User_field_create-fr.png/800px-User_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/7/71/User_field_create-fr.png 1.5x"
data-file-width="996" data-file-height="660" width="800" height="530"
alt="User field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/4/42/User-fr.png/800px-User-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/4/42/User-fr.png 1.5x"
data-file-width="1002" data-file-height="262" width="800" height="209"
alt="User-fr.png" />

Et si vous cliquez, une fenêtre modale va s'ouvrir et vous pouvez y
sélectionner un utilisateur.

<img
src="https://docs.joomla.org/images/thumb/3/3c/User_2-fr.png/800px-User_2-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/3/3c/User_2-fr.png 1.5x"
data-file-width="812" data-file-height="516" width="800" height="508"
alt="User 2-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<img
src="https://docs.joomla.org/images/2/25/User_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="181"
width="800" height="181" alt="User field frontend-fr.png" />

<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/Url_Field"
id="content-button" class="button expand success">Précédent : Champ
URL</a> <a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Usergroup_Field"
id="content-button" class="button expand">Suivant ː Champ Groupe
d'utilisateurs</a>
