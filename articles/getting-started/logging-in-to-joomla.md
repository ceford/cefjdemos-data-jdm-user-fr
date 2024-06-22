<!-- Filename: J4.x:Logging_in_to_Joomla / Display title: Se connecter sur Joomla -->

<span id="main-portal-heading">**Didacticiel**  
Se connecter et se déconnecter de Joomla !</span> Joomla!  4.0

## Introduction

L'un des grands avantages de Joomla ! est qu'il offre la possibilité
d'effectuer des tâches par le biais du tableau de bord de
l'administrateur (souvent appelé "backend") et, s'il est activé,
d'effectuer des tâches directement à partir du front (la partie du site
web destinée au public).

L'accès frontal est un moyen simple et efficace de permettre aux
rédacteurs de contenu d'ajouter ou de modifier rapidement des articles
sans avoir à se rendre dans le tableau de bord de l'administrateur.

Votre connexion Joomla est configurée pour contrôler ce que vous pouvez
voir et faire (ou ne pas faire) en utilisant le gestionnaire
d'utilisateurs de Joomla et les puissants niveaux de contrôle d'accès
(ACL). Cela signifie qu'un site web Joomla peut avoir des utilisateurs
qui utilisent uniquement le backend, d'autres qui utilisent uniquement
le front et d'autres encore qui utilisent les deux.

Ce qui suit couvre la connexion et la déconnexion à partir du backend et
du front de votre site web Joomla.

**Note :** Votre administrateur Joomla a peut-être désactivé l'accès au
front-end, ce qui implique que toutes les tâches doivent être effectuées
à l'aide du tableau de bord de l'administrateur back-end.

Les étapes abordées dans ce tutoriel sont basées sur une installation
standard de Joomla !

## Connexion et déconnexion du tableau de bord de l'administrateur du backend

### Connexion

Accédez à la page de connexion de l'administrateur. Il s'agit de
l'adresse web de votre site web, suivie de /administrator, par exemple,
mon-siteweb-joomla.com/administrator.

Vous accédez alors à la connexion de l'administrateur de Joomla :

<img
src="https://docs.joomla.org/images/thumb/2/2a/J4x_administrator_login_en.png/800px-J4x_administrator_login_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/2/2a/J4x_administrator_login_en.png 1.5x"
data-file-width="1000" data-file-height="562" width="800" height="450"
alt="J4x administrator login en.png" />

1.  Ajouter votre **Nom d'utilisateur**.
2.  Ajouter votre **Mot de passe**.

Cliquez sur le bouton de **Connexion** et vous accéderez au tableau de
bord principal de Joomla !

**Note :**

1.  Joomla vous offre la possibilité de configurer et d'utiliser
    l'authentification Web - cela n'entre pas dans le cadre de ce
    tutoriel.
2.  Si le site Web a d'autres langues installées, vous serez en mesure
    de sélectionner la langue appropriée dans une liste déroulante avant
    de vous connecter.

### Déconnexion

Pour vous déconnecter, cliquez sur le **Menu utilisateur** puis sur
**Déconnexion**.

<img
src="https://docs.joomla.org/images/thumb/8/89/J4x_administrator_logout_en.png/800px-J4x_administrator_logout_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/8/89/J4x_administrator_logout_en.png 1.5x"
data-file-width="1000" data-file-height="159" width="800" height="127"
alt="J4x administrator logout en.png" />

## Connexion et déconnexion à partir du front du site web

### Connexion

Si l'accès frontal est activé, un formulaire de connexion aura été
ajouté au site web. Joomla permet de le faire de plusieurs façons. Une
installation standard inclut un formulaire de connexion dans la barre
latérale du site web, mais vous pouvez constater qu'un lien a été ajouté
au menu du site web, ou peut-être dans le pied de page. Dans certains
cas, un lien "Créer une page" peut exister. La conception du site Web
déterminera l'endroit où vous pourrez accéder au formulaire de
connexion.

Dans cet exemple, nous utilisons un formulaire de connexion sur le site
Web qui se trouve dans la barre latérale.

<img
src="https://docs.joomla.org/images/thumb/a/ae/J4x_front_end_login_en.png/800px-J4x_front_end_login_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/a/ae/J4x_front_end_login_en.png 1.5x"
data-file-width="1000" data-file-height="548" width="800" height="438"
alt="J4x front end login en.png" />
  
Dans le **Formulaire de connexion** :

1.  Ajouter votre **Nom d'utilisateur**.
2.  Ajouter votre **Mot de passe**.

Cliquez sur le bouton **Connexion**.

Lorsque vous vous connectez à partir de la page d'accueil du site, vous
resterez sur la même page que celle où vous vous êtes connecté. Vous
remarquerez que le formulaire de connexion sera également remplacé par
un bouton *Déconnexion*.

### Déconnexion

<img
src="https://docs.joomla.org/images/thumb/a/a9/J4x_front_end_logout_en.png/800px-J4x_front_end_logout_en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/a/a9/J4x_front_end_logout_en.png 1.5x"
data-file-width="1000" data-file-height="233" width="800" height="186"
alt="J4x front end logout en.png" />

Pour vous déconnecter, allez à l'endroit où vous vous êtes connecté et
cliquez sur le bouton **Déconnexion**.

## Astuces

- Certains administrateurs de sites web Joomla installent des extensions
  qui masquent ou limitent l'accès au tableau de bord de
  l'administrateur. Vous devrez peut-être prendre des mesures
  supplémentaires ou visiter une autre URL de connexion.
- Si vous effectuez des modifications en utilisant la connexion
  frontale, gagnez du temps en vous connectant à la page que vous
  souhaitez modifier.
