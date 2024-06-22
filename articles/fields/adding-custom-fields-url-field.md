<!-- Filename: J3.x:Adding_custom_fields/Url_Field / Display title: Ajout de champs personnalisés/Champ URL -->

## Champ URL

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

### URL

Fournit un champ de saisie d'URL.

#### Paramètres

Les paramètres spécifiques pour ce champ sont ː

- Protocoles
  Les protocoles autorisés sont HTTP, HTTPS, FTP, FTPS, MAILTO, URL et
  FILE. Ce champ personnalisé est principalement un champ texte avec le
  type de l'url lors de la création dans le site d'administration, d'un
  article, d'un contact ou dans un composant qui supporte les champs
  personnalisés. Il est seulement possible de saisir une URL qualifiée -
  une avec un protocole et un domaine tel que `http://exemple.com`.
  L'url va être traduite en
  <a href="https://fr.wikipedia.org/wiki/Punycode" class="external text"
  target="_blank" rel="nofollow noreferrer noopener">punycode</a> avant
  son enregistrement. Ceci assure que l'url fonctionnera comme attendu
  quel que soit l'environnement.
- URLs relatives
  Utilisez ce paramètre pour déterminer si les URLs relatives sont
  autorisées ou non.

#### Informations connexes

Lisez  Type de champ de formulaire
URL.

#### Captures d'écran

##### Créer le champ

Supposons que vous créez un champ avec les options présentées dans la
figure suivante.

<img
src="https://docs.joomla.org/images/thumb/8/8f/Url_field_create-fr.png/800px-Url_field_create-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/8/8f/Url_field_create-fr.png 1.5x"
data-file-width="999" data-file-height="691" width="800" height="553"
alt="Url field create-fr.png" />

##### Utiliser le champ en backend

Dans l'administration lors de la création d'un article ou d'un contact,
vous voyez le champ comme dans l'image suivante ː

<img
src="https://docs.joomla.org/images/thumb/e/ee/URL-fr.png/800px-URL-fr.png"
decoding="async"
srcset="https://docs.joomla.org/images/e/ee/URL-fr.png 1.5x"
data-file-width="999" data-file-height="264" width="800" height="211"
alt="URL-fr.png" />

##### Utiliser le champ en frontend

Sur le site public, vous pouvez voir le champ comme sur l'image
ci-dessous. Le paramètre *Affichage automatique* se charge de la
position du champ et le modèle de site est responsable du rendu du
champ.
Les champs sont uniquement visibles sur le site public lorsqu'ils sont
remplis avec des données dans l'article. Si le champ n'est pas requis,
pouvez-vous vous en passer ?

<img src="https://docs.joomla.org/images/b/b5/Url_field_frontend-fr.png"
decoding="async" data-file-width="800" data-file-height="179"
width="800" height="179" alt="Url field frontend-fr.png" />

<a
href="https://docs.joomla.org/J3.x:Adding_custom_fields/Textarea_Field"
id="content-button" class="button expand success">Précédent : Champ Zone
de texte</a>
<a href="https://docs.joomla.org/J3.x:Adding_custom_fields/User_Field"
id="content-button" class="button expand">Suivant : Champ
Utilisateur</a>
