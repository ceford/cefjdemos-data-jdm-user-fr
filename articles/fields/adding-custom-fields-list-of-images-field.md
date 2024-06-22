<!-- Filename: J3.x:Adding_custom_fields/List_of_Images_Field / Display title: Ajout de champs personnalisés/Champ Liste d'images -->

<span id="section-portal-heading"></span>

## Champ Liste d'images

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

### Liste d'images

Fournit une liste déroulante de fichiers images.

#### Paramètres

Les paramètres spécifiques pour ce champ sont ː

- Répertoire
  Le chemin du système de fichier du répertoire contenant les fichiers
  images à lister.
- Multiple
  Autorise de choisir plusieurs valeurs.
- Classe de l'image
  La classe qui est ajoutée à l'image (balise src).

#### Informations connexes

Lisez  Type de champ de formulaire Liste
d'images.

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/a/ad/Image_field_create-fr.png/800px-Image_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/a/ad/Image_field_create-fr.png 1.5x"
data-file-width="996" data-file-height="747" width="800" height="600"
alt="Image field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/1/1e/Image-fr.png/800px-Image-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/1/1e/Image-fr.png 1.5x"
data-file-width="989" data-file-height="263" width="800" height="213"
alt="Image-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<img
src="https://docs.joomla.org/images/e/e4/Image_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="213"
width="800" height="213" alt="Image field frontend-fr.png" />

<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/List_Field"
id="content-button" class="button expand success">Précédent : Champ
Liste</a>
<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/Media_Field"
id="content-button" class="button expand">Suivant : Champ Médias</a>
