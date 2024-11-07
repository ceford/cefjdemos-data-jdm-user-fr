<!-- Filename: J4.x:Logging_in_to_Joomla / Display title: Connexion à Joomla -->

## Introduction

L'une des grandes qualités de Joomla! est qu'il offre la flexibilité d'effectuer des tâches via le Tableau de bord d'administration (souvent appelé le backend) et, si activé, de réaliser des tâches directement depuis le frontend (la partie publique) du site web.

L'accès au frontend est un moyen simple et efficace permettant aux rédacteurs de contenu d'ajouter ou de modifier rapidement des articles sans avoir besoin de se rendre sur le Tableau de bord d'administration.

La connexion Joomla est configurée pour contrôler ce que les utilisateurs peuvent voir et faire (ou ne pas faire) en utilisant le composant Utilisateur de Joomla et les puissants Niveaux de Contrôle d'Accès (ACL). Cela signifie qu'un site Joomla peut avoir des utilisateurs qui utilisent uniquement le backend, d'autres qui utilisent seulement le frontend et d'autres encore qui utilisent les deux.

Ce qui suit couvre la connexion et déconnexion à la fois du backend et du frontend d'un site Joomla.

**Remarque :** Un administrateur Joomla peut avoir désactivé l'accès au frontend, nécessitant que toutes les tâches soient effectuées en utilisant le Tableau de bord d'administration du backend.

### Connexion Administrateur

Naviguez vers la page de connexion de l'administrateur. C'est l'adresse web du site web ajoutée à /administrator, par exemple, my-joomla-website.com/administrator qui affiche la page de connexion de l'administrateur Joomla :

![Formulaire de connexion administrateur](../../../en/images/getting-started/logging-in-to-joomla-administrator-login-form.png)

1.  Ajoutez votre **Nom d'utilisateur**
2.  Ajoutez votre **Mot de passe**

Sélectionnez le bouton **Se connecter** pour accéder au Tableau de bord d'accueil de Joomla !.

**Remarque :**

1.  Joomla offre une option pour configurer et utiliser l'authentification Web. 
    Cela n'est pas dans le cadre de ce tutoriel.
2.  Si un site web a plusieurs langues installées, vous pourrez sélectionner une langue à utiliser à partir d'une liste déroulante avant de vous connecter.

### Déconnexion Administrateur

Pour vous déconnecter, sélectionnez le **Menu Utilisateur** puis **Déconnexion**.

![Lien de déconnexion administrateur](../../../en/images/getting-started/logging-in-to-joomla-logout-link.png)

### Connexion au site

Si l'accès au frontend est activé, un formulaire de connexion aura été ajouté au site. Joomla permet plusieurs façons de le faire. Une installation standard inclut un formulaire de connexion dans la barre latérale du site mais vous pouvez trouver un lien qui a été ajouté au menu du site ou peut-être dans le pied de page. Dans certains cas, un lien *Créer une page* peut exister. Le design du site déterminera où vous accédez au formulaire de connexion.

Cet exemple utilise un formulaire de connexion situé dans la barre latérale droite.

![Module de formulaire de connexion au site](../../../en/images/getting-started/logging-in-to-joomla-site-login-form.png)

Dans le **Formulaire de connexion**

1.  Ajoutez votre **Nom d'utilisateur**
2.  Ajoutez votre **Mot de passe**

Sélectionnez le bouton **Se connecter**.

Lors de la connexion depuis le frontend du site, vous pouvez rester sur la même page depuis laquelle vous vous êtes connecté ou vous pouvez être dirigé vers votre page de Profil. Vous remarquerez que le formulaire de connexion contient également un bouton **Déconnexion**.

### Déconnexion du site

![Module de formulaire de déconnexion du site](../../../en/images/getting-started/logging-in-to-joomla-site-logout-form.png)

Pour vous déconnecter, allez au formulaire de connexion et sélectionnez le bouton **Déconnexion**.  

## Conseils

- Certains administrateurs de sites Joomla installent des extensions qui cachent ou restreignent l'accès au tableau de bord administrateur du backend. Vous pourriez avoir besoin de prendre des mesures supplémentaires ou de visiter une URL de connexion alternative.
- Si vous effectuez des modifications en utilisant la connexion sur le frontend, gagnez du temps en vous connectant sur la page que vous souhaitez éditer.

*Traduit par openai.com*

