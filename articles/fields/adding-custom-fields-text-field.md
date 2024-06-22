<!-- Filename: J3.x:Adding_custom_fields/Text_Field / Display title: Ajout de champs personnalisés/Champ Texte -->

## Champ Texte

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

### Texte

Fournit une zone de texte pour la saisie des données.

#### Paramètres

Les paramètres spécifiques pour ce champ sont ː

- Filtre
  Permet au système de sauvegarder certaines balises html ou des données
  brutes. Utilisez le filtre brut pour assurer que le code html est
  préservé quand le formulaire est traité.
- Longueur maximale
  Le nombre de caractères maximum pouvant être saisis.

#### Informations connexes

Lisez  Type de champ de formulaire
Texte.

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/2/27/Text_field_create-fr.png/800px-Text_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/2/27/Text_field_create-fr.png 1.5x"
data-file-width="1043" data-file-height="663" width="800" height="509"
alt="Text field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/4/4b/Text-fr.png/800px-Text-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/4/4b/Text-fr.png 1.5x"
data-file-width="1053" data-file-height="264" width="800" height="201"
alt="Text-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<img
src="https://docs.joomla.org/images/1/13/Text_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="182"
width="800" height="182" alt="Text field frontend-fr.png" />

<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/Sql_Field"
id="content-button" class="button expand success">Précédent : Champ
SQL</a> <a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Textarea_Field"
id="content-button" class="button expand">Suivant : Champ Zone de
texte</a>
