<!-- Filename: J3.x:Adding_custom_fields/Editor_Field / Display title: Ajout de champs personnalisés/Champ Editeur -->

<span id="section-portal-heading"></span>

## Champ Editor (éditeur)

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

### Editeurs

Fournit une liste déroulante des éditeurs WYSIWYG disponibles.

#### Paramètres

Les paramètres spécifiques pour ce champ sont ː

- Afficher les boutons
  Vous pouvez décider si les boutons doivent être affichés ou non.
- Boutons à cacher
  Vous pouvez sélectionner dans le menu déroulant les boutons spéciaux à
  cacher dans la barre d'outil de l'éditeur. **A Noter** : Ce paramètre
  est seulement utile si 'Afficher les boutons' est mis à *Oui*.
- Largeur
  Cette valeur définit la largeur (en pixels) de l'éditeur WYSIWYG. La
  valeur par défaut est 100%.
- Height
  Cette valeur définit la hauteur (en pixels) de l'éditeur WYSIWYG. La
  valeur par défaut est 250px.
- Filtre
  Autorise le système à sauvegarder certaines balises html ou des
  données brutes.

#### Informations connexes

Lisez  Type de champ de formulaire
d'éditeur.

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/0/02/Editor_field_create-fr.png/800px-Editor_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/0/02/Editor_field_create-fr.png 1.5x"
data-file-width="965" data-file-height="828" width="800" height="686"
alt="Editor field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/1/19/Editor-fr.png/800px-Editor-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/1/19/Editor-fr.png 1.5x"
data-file-width="978" data-file-height="632" width="800" height="517"
alt="Editor-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<img
src="https://docs.joomla.org/images/2/20/Editor_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="192"
width="800" height="192" alt="Editor field frontend-fr.png" />

<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/Color_Field"
id="content-button" class="button expand success">Précédent : Champ
Couleur</a> <a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Integer_Field"
id="content-button" class="button expand">Suivant ː Champ Nombre
entier</a>
