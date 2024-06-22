<!-- Filename: J3.x:Adding_custom_fields/Media_Field / Display title: Ajout de champs personnalisés/Champ Médias -->

<span id="section-portal-heading"></span>

## Champ Médias

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

### Médias

Fournit un accès en modal au gestionnaire de médias pour l'insertion
d'images avec chargement par les utilisateurs disposant des
autorisations appropriées.

#### Paramètres

Les paramètres spécifiques pour ce champ sont ː

- Répertoire
  Le répertoire d'images par défaut pour ce champ. Par défaut, le champ
  Médias est le répertoire principal /images de manière inhérente, donc
  quelle que soit le répertoire saisi dans le champ Répertoire, il est
  supposé être présent dans le répertoire images. Donc si vous souhaitez
  que votre répertoire par défaut soit
  https://docs.joomla.org/images/myimages, il faut simplement saisir
  myimages dans le champ Répertoire.
- Prévisualisation
  Affiche ou masque la prévisualisation de l'image sélectionnée.
- Classe de l'image
  La classe qui est ajoutée à l'image (balise src).

#### Informations connexes

Lisez  Type de champ de formulaire
Médias.

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/2/25/Media_field_create-fr.png/800px-Media_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/2/25/Media_field_create-fr.png 1.5x"
data-file-width="987" data-file-height="750" width="800" height="608"
alt="Media field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/c/cb/Media-fr.png/800px-Media-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/c/cb/Media-fr.png 1.5x"
data-file-width="982" data-file-height="421" width="800" height="343"
alt="Media-fr.png" />

Et si vous cliquez, une fenêtre modale va s'ouvrir et vous pourrez y
sélectionner un utilisateur. <a
href="https://docs.joomla.org/index.php?title=Special:Upload&amp;wpDestFile=Media_2-fr.png"
class="new" title="File:Media 2-fr.png">800px</a>

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<img
src="https://docs.joomla.org/images/a/a4/Media_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="453"
width="800" height="453" alt="Media field frontend-fr.png" />

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/List_of_Images_Field"
id="content-button" class="button expand success">Précédent ː Champ
Liste d'images</a>
<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/Radio_Field"
id="content-button" class="button expand">Précédent : Champ Radio</a>
