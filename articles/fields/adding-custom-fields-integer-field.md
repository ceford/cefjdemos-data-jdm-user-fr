<!-- Filename: J3.x:Adding_custom_fields/Integer_Field / Display title: Ajout de champs personnalisés/Champ Nombre entier -->

## Champ Nombre entier

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

### Nombre entier

Fournis une liste déroulante de nombres entiers entre une valeur
minimale (première) et maximale (dernière).

#### Paramètres

Special options within this field are:

- Multiple
  Autorise de choisir plusieurs valeurs.
- Première
  La plus petite valeur de la liste.
- Dernière
  La plus grande valeur de la liste.
- Incrémentation
  Chaque valeur sera la valeur précédente incrémentée par cet entier, en
  commençant par la première valeur jusqu'à ce que la dernière valeur
  soit atteinte.

#### Informations connexes

Lisez  Type de champ de formulaire Nombre
entier

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/f/fd/Integer_field_create-fr.png/800px-Integer_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/f/fd/Integer_field_create-fr.png 1.5x"
data-file-width="971" data-file-height="756" width="800" height="623"
alt="Integer field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/e/e6/Integer-fr.png/800px-Integer-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/e/e6/Integer-fr.png 1.5x"
data-file-width="969" data-file-height="284" width="800" height="234"
alt="Integer-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.

<img
src="https://docs.joomla.org/images/1/10/Integer_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="188"
width="800" height="188" alt="Integer field frontend-fr.png" />

<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/Editor_Field"
id="content-button" class="button expand success">Précédent : Champ
Editeur</a>
<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/List_Field"
id="content-button" class="button expand">Suivant : Champ Liste</a>
