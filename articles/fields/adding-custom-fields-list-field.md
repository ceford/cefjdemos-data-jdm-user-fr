<!-- Filename: J3.x:Adding_custom_fields/List_Field / Display title: Ajout de champs personnalisés/Champ Liste -->

## Champ Liste

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

### Liste

Le type de champ de formulaire Liste fournit une liste déroulante ou une
liste d'entrées prédéfinies et personnalisées. Si le champ a une valeur
enregistrée, cette option est sélectionnée lors du premier chargement de
la page. Sinon, la valeur par défaut (le cas échéant) est sélectionnée.

#### Paramètres

Les paramètres spécifiques pour ce champ sont ː

- Multiple
  Si activé, permet le choix multiple de valeurs.
- Valeurs de la liste
  Les valeurs à afficher dans la liste.

#### Informations connexes

Lisez  Type de champ de formulaire
Liste.

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante. <img
src="https://docs.joomla.org/images/thumb/0/05/List_field_create-fr.png/800px-List_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/0/05/List_field_create-fr.png 1.5x"
data-file-width="1036" data-file-height="798" width="800" height="616"
alt="List field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/8/81/List-fr.png/800px-List-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/8/81/List-fr.png/1200px-List-fr.png 1.5x, https://docs.joomla.org/images/8/81/List-fr.png 2x"
data-file-width="1462" data-file-height="512" width="800" height="280"
alt="List-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous.

<img
src="https://docs.joomla.org/images/5/56/List_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="253"
width="800" height="253" alt="List field frontend-fr.png" />

Le paramètre *Affichage automatique* se charge de la position du champ
et le modèle de site est responsable du rendu du champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Integer_Field"
id="content-button" class="button expand success">Précédent ː Champ
Nombre entier</a> <a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/List_of_Images_Field"
id="content-button" class="button expand">Suivant ː Champ Liste
d'images</a>
