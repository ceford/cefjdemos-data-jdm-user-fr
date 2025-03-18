<!-- Filename: J5.x:Managing_Mail_Template_Layout / Display title: Modèles de courrier -->

## Introduction

Les modèles de courrier sont utilisés pour envoyer des messages email du système en **texte brut** ou en **HTML**, ou les deux, sélectionnés dans le formulaire *Modèles de courrier : Options*. Si une seule méthode est sélectionnée, l'alternative ne sera pas présente dans le formulaire d'édition du message.

La capture d'écran suivante montre une sélection des 26 modèles de courrier standard disponibles. La liste est accessible en sélectionnant **Système -> Modèles de courrier** dans le menu Administrateur.

![mail templates list](../../../en/images/templates/mail-templates-list.png)

Les messages électroniques peuvent être personnalisés pour modifier la mise en page, l'apparence et le libellé afin de répondre aux besoins de votre site. Par exemple, vous pourriez vouloir utiliser un logo de site et un schéma de couleurs dans ces e-mails envoyés aux clients. La personnalisation des e-mails envoyés aux administrateurs est moins importante.

Il existe deux méthodes de personnalisation : via les *Options du modèle de mail* pour tous les modèles de mail et via les *Paramètres de mail par modèle*.

## Modèle de courrier : Options

Sélectionnez le bouton **Options** dans la barre d'outils de la liste *Modèles de courrier* pour accéder aux paramètres généraux des modèles de courrier. Sélectionnez le bouton *Basculer l'aide en ligne* pour voir si certains champs du formulaire ont une aide supplémentaire.

![mail templates options](../../../en/images/templates/mail-templates-options.png)

### Format du courrier

Sachez qu'un destinataire peut configurer un client de messagerie pour utiliser du HTML simple ou du texte brut afin d'éviter le téléchargement des images. Il peut donc être préférable de définir le *Format de courriel* sur *Texte brut* ou *Les deux*.

### Paramètres de courrier par modèle

Si cela est réglé sur **Oui**, les formulaires de modification de modèles de courriel individuels comportent un onglet supplémentaire *Options* qui vous permet de modifier les paramètres de courriel pour ce modèle et éventuellement de vous permettre d'envoyer une copie (BCC) à une adresse électronique spécifique à condition que le champ **Envoyer une copie** ici soit également réglé sur **Activé**.

## Formulaire d'édition de modèle

Dans la liste des modèles de courrier, vous pouvez sélectionner n'importe quel modèle pour le modifier. Le lien du titre mène au formulaire de modification pour le modèle anglais par défaut. Chaque drapeau est un lien vers le même modèle dans cette langue.

### L'onglet Courrier

![edit mail template form](../../../en/images/templates/mail-template-edit.png)

Le contenu des zones Sujet et Corps est initialement stocké dans des chaînes de langue. Cela permet de *Réinitialiser le Sujet par Défaut* ou le *Corps*. Cependant, une fois qu'un modèle de courrier spécifique a été modifié, ses champs Sujet et Corps sont stockés dans la table `#__mail_templates`.

Les éléments entre accolades sont des balises de remplacement qui sont remplacées par de vraies valeurs lorsque l'email est envoyé. Dans l'exemple ci-dessus, `{SITENAME}` serait le nom que vous avez choisi pour votre site. `{Method}` serait la méthode de transport de courrier sélectionnée : `PHP Mail`, `Sendmail` ou `SMTP`.

Les balises de remplacement disponibles varient d'un mail à l'autre. Vous pouvez ajouter vos propres balises de remplacement personnalisées, mais cela nécessite un plugin personnalisé, décrit dans un [article de Magazine](https://magazine.joomla.org/all-issues/february-2025/joomla-5-email-templates-how-to-add-variables-via-plugin) de février 2025.

### L'onglet Options

Cet onglet est présent uniquement si les *Paramètres de courriel par modèle* sont définis sur *Oui* dans *Modèles de courriel : Options*. L'illustration ci-dessous montre une capture d'écran avec les *Paramètres de courriel* définis sur *Non*. S'ils sont définis sur *Oui*, davantage de champs de formulaire apparaissent, remplaçant les options de courriel définies dans la configuration globale, onglet Serveur.

![edit mail template form](../../../en/images/templates/mail-template-edit-options.png)

Si vous souhaitez envoyer une copie carbone invisible d'un email sortant à une adresse email spécifique, vous pouvez l'entrer dans le champ *Envoyer une copie à l'email*.

## Remplacements de modèles de courrier

Pour créer un modèle de courrier de remplacement dans un modèle personnalisé :

1. Allez dans Système -> Modèles de site -> Ouvrez votre modèle (par exemple, Cassiopeia).
2. Dans l'onglet Créer des remplacements, sélectionnez joomla -> mail.
3. Joomla copiera le fichier `mailtemplate.php` dans le répertoire `/html/layouts/joomla/mail/` de votre modèle, où vous pourrez le modifier selon vos besoins.

Une fois que la substitution est créée, vous pouvez ajuster la mise en page et les styles de vos e-mails sans affecter le modèle de base.

## Liste des modèles de courrier

| Titre | Extension | Description |
|-------|-----------|-------------|
| Journal d'actions utilisateur : Mail de notification | Journal d'actions utilisateur | Mail envoyé aux administrateurs concernant de nouvelles entrées dans le journal d'actions utilisateur. |
| Configuration Globale : Test de courrier | Configuration | Envoyé lorsque vous cliquez sur le bouton "Envoyer un mail de test" dans la Configuration Globale. Il est envoyé à l'adresse mail de l'expéditeur définie dans les paramètres de courrier. |
| Contacts : Mail du formulaire de contact | Contacts | L'e-mail du "Formulaire de contact". |
| Contacts : Copie du mail du formulaire de contact | Contacts | Envoyé à l'expéditeur d'un mail avec le formulaire de contact si l'option "Envoyer une copie à l'expéditeur" est activée et sélectionnée. |
| Messages : Nouveau message | Messagerie | E-mail contenant un message créé dans le composant de messagerie. |
| Vie Privée : Demande d'exportation de données (Admin) | Vie Privée | Mail pour informer l'utilisateur qu'une demande pour exporter les données de ce site a été créée par l'administrateur |
| Vie Privée : Demande de suppression de données (Admin) | Vie Privée | Mail pour informer l'utilisateur qu'une demande pour supprimer les données de ce site a été créée par l'administrateur |
| Vie Privée : Demande d'exportation de données | Vie Privée | Mail pour vérifier que les données d'un utilisateur doivent être exportées du site |
| Vie Privée : Demande de suppression de données | Vie Privée | Mail pour vérifier que les données d'un utilisateur doivent être supprimées du site |
| Vie Privée : Exportation des données utilisateur | Vie Privée | Mail avec exportation des données utilisateur |
| Utilisateurs : Mail en masse aux utilisateurs | Utilisateurs | L'e-mail "Mail en masse aux utilisateurs". |
| Utilisateurs : Réinitialisation de mot de passe | Utilisateurs | Envoyé à un utilisateur par le lien "Mot de passe oublié ?" par exemple dans un formulaire de connexion. |
| Utilisateurs : Notification de nouveau compte à l'admin | Utilisateurs | Notification à l'admin qu'un nouveau compte activé a été créé. |
| Utilisateurs : Demande à l'admin de vérifier un nouveau compte | Utilisateurs | Notification aux admins pour vérifier un nouveau compte vérifié. |
| Utilisateurs : Compte activé par l'admin | Utilisateurs | Notification envoyée à l'utilisateur que le nouveau compte a été activé par un administrateur. |
| Utilisateurs : Nouveau compte avec activation par l'admin | Utilisateurs | Notification à l'utilisateur concernant le nouveau compte, qui devra maintenant être activé par un admin. |
| Utilisateurs : Nouveau compte avec activation par l'admin (avec PW) | Utilisateurs | Notification à l'utilisateur concernant le nouveau compte, qui devra maintenant être activé par un admin. Le mot de passe en clair est inclus dans le mail. |
| Utilisateurs : Nouveau compte sans activation | Utilisateurs | Notification à l'utilisateur concernant le nouveau compte. Le compte est déjà activé. |
| Utilisateurs : Nouveau compte sans activation (avec PW) | Utilisateurs | Notification à l'utilisateur concernant le nouveau compte. Le compte est déjà activé. Le mot de passe en clair est inclus dans le mail. |
| Utilisateurs : Nouveau compte avec auto-activation | Utilisateurs | Notification à l'utilisateur concernant le nouveau compte, que l'utilisateur devra maintenant auto-activer. |
| Utilisateurs : Nouveau compte avec auto-activation (avec PW) | Utilisateurs | Notification à l'utilisateur concernant le nouveau compte, que l'utilisateur devra maintenant auto-activer. Le mot de passe en clair est inclus dans le mail. |
| Utilisateurs : Rappel de nom d'utilisateur | Utilisateurs | Envoyé à un utilisateur par le lien "Nom d'utilisateur oublié ?" par exemple dans un formulaire de connexion. |
| Code envoyé par email | Authentification à plusieurs facteurs - Code d'authentification par email | Envoyé aux utilisateurs depuis la page d'authentification à plusieurs facteurs lors de l'utilisation de l'option "Code d'authentification par email". |
| Tâche - Consentement à la vie privée : Renouveler le consentement | Tâche - Consentements à la vie privée | Rappel de renouveler le consentement à la vie privée pour ce site web. |
| Joomla : Notification de mise à jour | Tâche - Notification de mise à jour de Joomla! | Envoyé aux administrateurs du site lorsque le plugin de tâche "Notification de mise à jour de Joomla!" détecte une mise à jour. |
| Utilisateurs : Nouvel utilisateur | Utilisateur - Joomla! | Envoyé à un nouvel utilisateur lorsqu'il est créé dans le backend. |

*Traduit par openai.com*

