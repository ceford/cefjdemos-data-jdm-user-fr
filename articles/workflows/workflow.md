<!-- Filename: J4.x:Workflow / Display title: Workflow de Publication  -->

## Introduction

Dans Joomla, un flux de travail est une séquence d'étapes dans la vie d'un article, de sa conception à sa disparition. Les étapes sont généralement effectuées par différentes personnes ayant des responsabilités différentes. Par exemple, dans le monde de la presse, un sous-editeur prend une histoire d'un journaliste et vérifie son exactitude, sa grammaire, sa lisibilité et sa longueur, voire plus. Le sous-editeur transmettra alors l'histoire à l'éditeur, qui peut accepter ou rejeter l'histoire, décider de son emplacement dans le journal, etc.

Le composant Workflow est utilisé pour ajouter des **étapes** aux articles afin d'améliorer les états statiques (non publié, publié, mis à la corbeille et archivé) avec des **transitions**. Les états statiques et les transitions sont enregistrés séparément afin que les flux de travail puissent être activés ou désactivés selon les besoins sans affecter l'état des éléments de contenu. Les flux de travail sont activés ou désactivés dans l'onglet *Intégration* de la page *Articles : Options*.

Il existe une page tutoriel contenant les étapes pour la création d'un exemple de flux de travail : [Scénarios de flux de travail](jdocmanual?article=user/workflows/workflow-scenarios).

## Termes et Définitions

- *Flux de travail :* Un flux de travail est une séquence complète d'étapes. Plusieurs flux de travail différents peuvent être créés pour différents objectifs. Le composant Flux de travail contient un *Flux de travail de base* et les données d'exemple du blog ont un *Flux de travail de blog* plus complexe.
- *Étape :* Une étape est un emplacement dans un flux de travail. Par exemple, un article non publié peut être à l'Étape 1 : En préparation ou à l'Étape 2 : Prêt pour examen, etc. C'est l'étape de l'élément qui est enregistrée dans la base de données.
- *Transition :* Une transition est un changement d'une étape à une autre, souvent vers la suivante dans le flux de travail, mais elle peut aussi revenir à l'étape précédente ou à l'étape initiale.
- *État :* L'état d'un article peut être non publié, publié, mis à la corbeille ou archivé. Un état peut être modifié en exécutant une transition de flux de travail à condition que l'utilisateur ait la permission de changer d'état.
- *Catégorie :* Lorsqu'il y a utilisation de flux de travail, un flux de travail spécifique peut être sélectionné pour une catégorie dans l'onglet *Flux de travail* du formulaire *Article : Modifier la catégorie*.

## La Liste des Flux de Travail

Lorsque les flux de travail sont activés, la liste des flux de travail disponibles peut être consultée en sélectionnant **Contenu → Flux de travail** dans le menu Administrateur.

![Liste des flux de travail](../../../en/images/workflows/workflows-list.png)

- Le **Statut** d'un flux de travail peut être Activé, Désactivé ou Envoyé à la corbeille.
- Le **Nom** est un lien vers le formulaire de modification du flux de travail.
- L'élément **Par défaut** est utilisé pour les nouveaux éléments qui ne sont pas assignés à une catégorie ayant un flux de travail défini.
- L'élément **Étapes** est un bouton indiquant le nombre d'étapes et un lien vers la liste des étapes pour le flux de travail.
- L'élément **Transitions** est un bouton indiquant le nombre de transitions et un lien vers la liste des transitions pour le flux de travail.
- L'**ID** est la valeur numérique du flux de travail utilisée en interne.

## Étapes

Les étapes sont accessibles via la liste *Workflows*. Sélectionnez le bouton jaune affichant le nombre d'étapes.

![Liste des étapes de workflow](../../../en/images/workflows/workflow-stages-list.png)

Sélectionnez le nom d'une étape pour l'éditer.

![Formulaire d'édition d'étape de workflow](../../../en/images/workflows/workflow-stage-edit.png)

## Transitions

Dans les flux de travail, les articles passent d'une étape à une autre. Les transitions sont gérées via la liste des *Transitions*.

![La liste des transitions](../../../en/images/workflows/workflow-transitions-list.png)

- La *Phase Actuelle* définit où commence cette transition.
- La *Phase Cible* définit où se termine cette transition.

### Étapes de Transition

Les phases *Actuelle* et *Cible* sont définies dans le formulaire *Modifier la Transition* :

![Formulaire de modification de transition](../../../en/images/workflows/workflow-transition-edit.png)

L'onglet *Actions de Transition* est utilisé pour définir l'*État* dans lequel l'élément sera après que la transition soit terminée.

![Onglet des actions du formulaire de modification de transition](../../../en/images/workflows/workflow-transition-edit-actions-tab.png)

- **État de Mise en Avant** Indique si l'élément sera *Mis en Avant* ou non.
- **État de Publication** Sélectionnez l'état cible dans la liste.

L'onglet *Notifications de Transition* est utilisé pour définir si une notification est envoyée pour cet état. Par exemple, si un article a été écrit mais doit être relu, un e-mail pourrait être envoyé pour notifier l'éditeur.

![Onglet des notifications du formulaire de modification de transition](../../../en/images/workflows/workflow-transition-edit-notifications-tab.png)

- **Envoyer une Notification** Si c'est réglé sur *Oui*, des champs supplémentaires apparaissent.
- **Texte de Message Supplémentaire** Ajoutez un texte de message supplémentaire ou utilisez une chaîne de langue pour rendre le texte de message traduisible.
- **Groupes d'Utilisateurs** Sélectionnez qui recevra la notification, par exemple tous les utilisateurs du groupe d'utilisateurs *Éditeur*.
- **Utilisateurs** Sélectionnez des utilisateurs individuels pour recevoir cette notification.

### Permissions

L'onglet des permissions contrôle l'accès à cette transition par des groupes d'utilisateurs sélectionnés. En général, les permissions sont héritées des paramètres de permission dans *Articles : Options*.

### Plugins de Transition de Flux de Travail

Les plugins de flux de travail sont utilisés pour des actions déclenchées par des transitions. Allez à **Système → Plugins** et changez le filtre *- Sélectionner le Type -* à *workflow*. Chacun de ces plugins peut être désactivé s'il n'est pas nécessaire.

![Liste des plugins de flux de travail](../../../en/images/workflows/workflow-plugins.png)

- **Mise en Avant de Flux de Travail** Cette action met en œuvre le changement du statut d'*Article Mis en Avant* de *Oui* à *Non*.
- **Notification de Flux de Travail** Cette action met en œuvre la notification d'un utilisateur qu'un changement de phase nécessite une attention.
- **Publication de Flux de Travail** Cette action met en œuvre un changement d'état d'un article d'un état à un autre parmi *Publié*, *Non publié*, *Dans la corbeille* ou *Archivé*. Si l'utilisateur n'a pas la permission de changer l'état, cela échouera avec un message explicatif. La transition qui a demandé le changement d'état réussira tout de même !

## Catégories

Les articles peuvent être attribués à des catégories. Elles correspondent à un certain flux de travail et peuvent être personnalisées de diverses manières. Vous pouvez définir un statut, une catégorie parente et également restreindre l'accès ainsi que les autorisations. Cette option ne se trouve pas dans l'écran des flux de travail. Pour cette option, vous devez aller à **Contenu → Catégories**. Une fois là, ouvrez n'importe quelle catégorie et vous verrez un onglet *Flux de travail*.

![Flux de travail édition de la catégorie des articles](../../../en/images/workflows/workflow-categories-blog.png)

### Exemple

Certains articles doivent être disponibles uniquement pour les administrateurs ou les utilisateurs d'un rang supérieur.

- Créez une catégorie nommée *Restreint*
- Réglez toutes les autorisations sur *Autorisé* pour les administrateurs ou des rangs supérieurs.
- Déplacez les articles concernés vers la catégorie *Restreint*.

Cela évite de régler les autorisations sur des articles individuels.

## Gestion des versions

Lorsque le workflow est activé, les champs gérés par le workflow sont exclus de la gestion des versions (comme "état" et "en vedette") afin d'éviter les conflits de permissions.

## Exemples

Des exemples spécifiques sont disponibles pour illustrer comment utiliser les Flux de Travail pour différents groupes d'utilisateurs :

- [Exemple 1](jdocmanual?article=user/workflows/workflow-example-1) utilise les groupes d'utilisateurs par défaut Auteur, Éditeur et Éditeur pour préparer des éléments pour une newsletter.
- [Exemple 2](jdocmanual?article=user/workflows/workflow-example-2) utilise des groupes d'utilisateurs personnalisés pour préparer des éléments pour les réunions de comité.

*Traduit par openai.com*

