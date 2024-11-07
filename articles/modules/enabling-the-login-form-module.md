<!-- Filename: Enabling_the_Login_Form_module / Display title: Formulaire de Connexion  -->

## Méthodes de Connexion au Site

Il existe deux façons de permettre aux utilisateurs enregistrés de se connecter à la partie frontale d'un site web. Il y a un élément de menu **Formulaire de Connexion** trouvé dans le groupe d'éléments de menu Utilisateurs. Il doit avoir ses permissions *Accès* réglées sur *Invité*. Un deuxième élément de menu *Déconnexion* est nécessaire avec ses permissions *Accès* réglées sur *Enregistré*.

L'alternative est le module **Formulaire de Connexion**. Il est installé par défaut en position *sidebar-right* dans une nouvelle installation de Joomla. Ce module peut être déplacé à une autre position, non publié, mis à la corbeille et supprimé. Ces dernières actions s'appliquent à une instance du module et non au code du module. Ainsi, vous pouvez créer un nouveau module *Formulaire de Connexion* ou en faire un duplicata, peut-être pour une utilisation dans différents modèles. Le module Formulaire de Connexion change son affichage après connexion pour présenter un bouton *Déconnexion*.

## Le Module de Formulaire de Connexion

Pour publier un formulaire de connexion non publié :

* Sélectionnez **Contenu → Modules du site** dans le menu Administrateur.
* Recherchez le module **Formulaire de connexion**.
* Si l'icône **Statut** est une coche verte dans un cercle, c'est qu'il est déjà activé. Si l'icône Statut est une croix grise, il est actuellement désactivé. Sélectionnez l'icône pour activer le module.
* Si le module *Formulaire de connexion* n'est pas présent dans la liste, réglez les options de filtre, sélectionnez le champ Statut - sur *Tous* ou *Corbeille* pour vérifier s'il a été mis à la corbeille. Si c'est le cas, il peut être publié en sélectionnant son icône de corbeille.
* Si le module Formulaire de connexion est manquant, créez-en un nouveau.

Pour créer un nouveau formulaire de connexion ou un second formulaire de connexion :

* Sélectionnez **Contenu → Modules du site** dans le menu Administrateur.
* Sélectionnez le bouton **Nouveau** dans la barre d'outils.
* Dans la liste des modules, sélectionnez l'élément **Connexion**.
* Remplissez le formulaire de saisie de données *Modules : Connexion*.
  - Entrez un titre unique.
  - Sélectionnez une position de modèle ou créez une position nommée pour l'utiliser dans un article.
  - Remplissez les autres champs comme approprié.
* **Enregistrer & Fermer**
* Testez que le module apparaît correctement dans l'interface du site.

## Pour assigner le module de formulaire de connexion à des pages web sélectionnées

Vous pouvez faire apparaître le module de formulaire de connexion sur une ou plusieurs pages en l'assignant à des éléments de menu sélectionnés. Cela se fait en utilisant les champs du groupe d'assignation de menu sur l'écran d'édition du module :

- Sélectionnez l'onglet **Assignation de menu**.
- La liste **Assignation du module** propose quatre options :
  - **Sur toutes les pages** : Le module de formulaire de connexion apparaîtra sur toutes les pages.
  - **Aucune page** : Le module de formulaire de connexion n'apparaîtra sur aucune page.
  - **Seulement sur les pages sélectionnées** : Une liste de tous les menus et éléments de menu de votre site apparaîtra. Le module de formulaire de connexion apparaîtra sur les pages sélectionnées dans cette liste.
  - **Sur toutes les pages sauf celles sélectionnées** : Le formulaire de connexion apparaîtra sur toutes les pages non sélectionnées.
- **Sélection du menu** : Affiche une liste de tous les menus et éléments de menu parmi lesquels un ou plusieurs peuvent être sélectionnés. Ce champ est utilisé uniquement si le champ **Menus** est défini sur **Sélectionner des éléments de menu dans la liste**.

  ![assignation de menu du module](../../../en/images/modules/modules-login-menu-assignment.png)

## Pour personnaliser le module de formulaire de connexion

Si vous souhaitez modifier l'apparence du module de connexion, vous pouvez ajouter des styles, soit des styles Bootstrap, soit vos propres styles définis dans votre fichier user.css du modèle. Ajoutez les styles dans l'onglet **Avancé** du formulaire d'édition des modules : Connexion.

Si vous souhaitez modifier les informations affichées dans le formulaire de connexion, vous pouvez créer une substitution de modèle. Consultez la section sur les [Substitutions de Modèle](jdocmanual?article=user/templates/template-overrides) pour plus de détails.

*Traduit par openai.com*

