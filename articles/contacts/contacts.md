<!-- Filename: contacts.md / Display title: Contacts  -->

## Introduction

Un contact est une collection d'informations personnelles concernant un individu. Vous pouvez souhaiter rendre ces informations disponibles sur votre site web pour un affichage public ou privé. Par exemple, vous pouvez vouloir répertorier les membres clés de votre organisation ou communauté. Le composant Contact de Joomla! est conçu à cet effet. Il vous permet de lister des personnes et leurs informations personnelles sur votre site web, sans qu'elles soient nécessairement des utilisateurs enregistrés. Vous pouvez également autoriser n'importe qui, ou seulement les utilisateurs enregistrés, à envoyer des e-mails à ces personnes.

À titre d'exemple de l'utilisation des données personnelles, vous pourriez consulter la page Wikipédia sur les commissions parlementaires du Royaume-Uni. Vous y verrez des listes de commissions avec des informations contextuelles sur les présidents respectifs. Si vous suivez un lien vers une commission, vous verrez une liste de membres avec des informations sélectionnées sur chaque individu. Pour réaliser quelque chose de similaire dans Joomla, vous mettriez en place des catégories et sous-catégories pour chaque commission. Comme ceci :

```
Chambre des Communes
- Affaires
- Culture
- ...
Chambre des Lords
- Communications
- Constitution
- ...
```
Chaque membre de la commission dispose d'informations supplémentaires non présentes dans les données par défaut - affiliation politique, telle que Conservateur, Travailliste ou SNP, et circonscription, la zone du pays qu'ils représentent. Ces éléments peuvent être collectés en utilisant des Champs Personnalisés.

Il faut faire preuve de prudence dans la collecte et l'affichage d'informations personnelles. Les individus peuvent être très sensibles à la mise à disposition de leurs informations en ligne.

## Données de Contact

Les contacts sont créés via la page de liste des contacts. Sélectionnez le bouton `Nouveau` dans la barre d'outils pour ajouter une nouvelle entrée. Il existe également un plugin **Utilisateur - Créateur de contact** qui crée automatiquement un contact lorsqu'un nouvel utilisateur est enregistré.

Dans le formulaire **Contacts : Modifier**, entrez toutes les données dont vous disposez sur le contact.

![Capture d'écran de saisie des données](../../../en/images/contacts/contact-data-entry.png "Capture d'écran de saisie des données")

**Notes :**

Dans la capture d'écran, le **Poste** a été saisi comme *Président*, ce qui avait du sens dans le contexte d'une liste de catégorie de membres du comité, mais cela n'a pas de sens dans le contexte d'une liste de contacts en vedette qui consiste en tous les présidents de tous les comités. Il est nécessaire d'être plus spécifique : *Président du Comité de la Culture, des Médias et du Sport*.

Les champs **Premier**, **Deuxième** et **Troisième Champ de Tri** nécessitent que des mots soient ajoutés pour chaque entrée afin de permettre un tri selon un ordre défini par l'utilisateur, tel qu'un ordre conventionnel de nom de famille et prénom. Cela est couvert plus en détail dans cet article.

L'onglet **Informations Diverses** contient un champ d'édition de texte avec une courte déclaration personnelle.

L'onglet **Supplémentaire** contient les champs personnalisés *Parti* et *Circonscription*.

L'onglet **Formulaire** contient des paramètres pour le formulaire de contact par email. Si une adresse email n'est pas saisie, ce champ n'est pas affiché.

## Affichage des Contacts

Le composant Contact propose quatre éléments de menu pour afficher les données de contact :

* Contact Unique
* Contacts en Vedette
* Lister les Contacts dans une Catégorie
* Lister Tous les Contacts dans un Arborescence de Catégorie

Il est conseillé d'essayer chaque type de menu pour voir à quoi ressemble le rendu.
Quelques exemples :

### Lister Toutes les Catégories dans une Arborescence de Catégories de Contacts

Dans ce cas, l'arborescence de catégories se compose d'une catégorie parente et de deux sous-catégories :
```
Chambre des Communes
- Comité des Affaires
- Comité de la Culture
```
![toutes les catégories dans une arborescence de catégorie](../../../en/images/contacts/contact-all-committees.png "Toutes les Catégories dans une Arborescence de Catégorie de Contacts")

La deuxième ligne de chaque entrée provient de la Description de la Catégorie.

Si vous sélectionnez un des liens de Comité, la page du Comité pourrait ressembler à celle-ci :

![contacts dans une catégorie](../../../en/images/contacts/contact-culture-committee.png "Contacts dans une Catégorie")

La mise en page n'est pas tout à fait comme désirée. Il aurait été préférable d'inclure une
image miniature de chaque individu et une meilleure mise en page des détails. Cela
peut être fait avec une surcharge de modèle (plus tard).

### Lister les Contacts dans une Catégorie

Pour le Comité des Affaires, il y a un élément de menu Lister les Contacts dans une Catégorie.
Cela entraîne l'utilisation d'une mise en page différente :

![liste de catégories de contacts](../../../en/images/contacts/contact-category-list.png "Liste de Catégories de Contacts")

Mieux mais toujours pas tout à fait correct ! Un surclassement de style était nécessaire pour réduire le style de l'image. Encore une fois, il semble qu'une surcharge de modèle pourrait être utile.

### Contacts en Vedette

Pour cet exemple, les présidents de tous les comités ont été marqués comme en vedette.

![contacts en vedette](../../../en/images/contacts/contact-featured.png "Contacts en Vedette")

## Ordre de Tri

L'ordre dans lequel les contacts apparaissent peut être défini dans les options du composant Contact ou dans un élément de menu. Ce dernier remplace le premier s'il est défini. Les paramètres disponibles sont les suivants :
* **Nom** Le nom du contact. Cela peut ne pas convenir pour un ordre alphabétique.
* **Nom de Tri** Ce sont les trois champs *Champ de Tri* dans le formulaire de données de Contact mentionné précédemment.
* **Ordre** C'est l'ordre dans lequel les contacts apparaissent dans la liste des Contacts.
* **Ordre des Contacts en Vedette** Les contacts en vedette apparaissent avant les autres contacts, mais sinon les contacts sont affichés dans l'ordre de la liste.

