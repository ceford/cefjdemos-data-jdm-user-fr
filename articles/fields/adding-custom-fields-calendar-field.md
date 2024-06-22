<!-- Filename: J3.x:Adding_custom_fields/Calendar_Field / Display title: Ajout de champs personnalisés/Champ Calendrier -->

## Champ Calendrier

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

## Champ Calendrier

Fournit une zone de texte pour la saisie d'une date. Une icône à côté de
la zone de texte fournit un lien vers un calendrier en fenêtre modale,
qui peut également être utilisé pour entrer la valeur de la date.

#### Paramètres

Si vous utilisez la date par défaut ː la valeur peut être au format ISO
8601 (YYYY-MM-DD HH:MM:SS) ou bien NOW, qui affiche la date courante.
**Attention** : Même si vous ne spécifiez pas l'heure dans la date par
défaut, l'heure sera affichée lorsque le paramètre *Affichage de
l'heure* est activé.
Les paramètres spécifiques pour ce champ sont :

- Affichage de l'heure
  Si actif, le champ calendrier attend une date et une heure et va
  également afficher l'heure. Les formats sont localisés en utilisant
  les chaînes de langues habituelles.

#### Informations connexes

Veuillez consulter :

-  Type de champ de formulaire
  calendrier
- <a href="http://php.net/manual/en/datetime.formats.date.php"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Formats de date</a>

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/f/fc/Calendar_field_create-fr.png/670px-Calendar_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/f/fc/Calendar_field_create-fr.png/1005px-Calendar_field_create-fr.png 1.5x, https://docs.joomla.org/images/f/fc/Calendar_field_create-fr.png 2x"
data-file-width="1014" data-file-height="746" width="670" height="493"
alt="Calendar field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante

<img
src="https://docs.joomla.org/images/thumb/2/20/Calendar-fr.png/670px-Calendar-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/2/20/Calendar-fr.png/1005px-Calendar-fr.png 1.5x, https://docs.joomla.org/images/2/20/Calendar-fr.png 2x"
data-file-width="1058" data-file-height="643" width="670" height="407"
alt="Calendar-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<img
src="https://docs.joomla.org/images/thumb/9/91/Calendar_field_frontend-fr.png/670px-Calendar_field_frontend-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/9/91/Calendar_field_frontend-fr.png 1.5x"
data-file-width="800" data-file-height="202" width="670" height="169"
alt="Calendar field frontend-fr.png" />

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Parameters_for_all_Custom_Fields"
id="content-button" class="button expand success">Précédent : Paramètres
pour tous les Champs Personnalisés</a> <a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Checkboxes_Field"
id="content-button" class="button expand">Suivant : Champ Cases à
cocher</a>
