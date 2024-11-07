<!-- Filename: J6.x:Workflow_Scenarios_Example_2 / Display title: Exemple de flux de travail 2  -->

## Introduction

Cet exemple implique deux utilisateurs, Alice et Bob, qui sont respectivement la présidente et le secrétaire d'un comité. Le flux de travail implique la préparation et l'approbation des ordres du jour et des procès-verbaux des réunions du comité. Charlie est un membre du comité qui aura accès aux documents du comité lorsqu'ils seront publiés. Le flux de travail utilise uniquement le frontend.

## Groupes d'utilisateurs

Commencez par créer de nouveaux groupes d'utilisateurs, tous enfants de *Enregistré*.

- **Comité** Un enfant de *Enregistré* 
- **Président** Un enfant de *Comité*
- **Secrétaire** Un enfant de *Comité*

![Groupes d'utilisateurs personnalisés](../../../en/images/workflows/example-2-user-groups.png)

## Niveau d'accès utilisateur

- Créez un nouveau niveau, **Comité** et ajoutez *Comité* aux Groupes d'utilisateurs avec accès à la visualisation.
- Dans le niveau d'accès *Spécial*, ajoutez *Comité* aux Groupes d'utilisateurs avec accès à la visualisation.

![Niveaux d'accès à la visualisation](../../../en/images/workflows/example-2-viewing-access-levels.png)

## Créer des utilisateurs

- **Alice** dans le groupe *Présidente*.
- **Bob** dans le groupe *Secrétaire*.
- **Charlie** dans le groupe *Comité*.

## Créer le Flux de Travail

- **Nom** *Flux de Travail du Comité*
- **Description** *Flux de travail pour la préparation des documents du Comité.*
- **Permissions**
  - **Comité** Tous réglés sur *Hérité* Non autorisé (hérité).
  - **Président** Tous réglés sur *Autorisé* sauf *Supprimer*. Peut-être...
  - **Secrétaire** Tous réglés sur *Autorisé* sauf *Supprimer* et *Modifier État*.

![Liste des flux de travail](../../../en/images/workflows/example-2-workflows-list.png)

### Créer les Étapes du Flux de Travail

- **Brouillon** 
  - **Remarque** *Documents en préparation.* 
  - **Permissions** Tous laissés sur *Hérité*.
- **Revue**
  - **Remarque** *Documents en attente d'approbation.* 
  - **Permissions** Tous laissés sur *Hérité*.
- **Publication**
  - **Remarque** *Documents publiés.* 
  - **Permissions** Tous laissés sur *Hérité*.

![Étapes du flux de travail](../../../en/images/workflows/example-2-stages-committee-workflow.png)

### Créer les Transitions du Flux de Travail

#### Brouillon à Revue

C'est la transition normale vers l'avant dans la séquence des étapes.

- **Nom** *Brouillon/Revue*
- **Onglet Transition**
  - **Étape Actuelle** *Brouillon*
  - **Étape Cible** *Revue*
  - **Remarque** *Transition vers l'étape suivante.*
- **Onglet Actions de Transition**
  - **État en Vedette** *- Aucun Sélectionné -*
  - **État de Publication** *- Aucun Sélectionné -*
- **Onglet Notification**
  - **Envoyer une Notification** *Oui* Les destinataires doivent avoir *Recevoir les Emails du Système* activé pour recevoir les notifications par email.
  - **Texte de Message Supplémentaire** Quelque chose de spécifique à ce flux de travail ?
  - **Groupes d'Utilisateurs** *Président*
  - **Utilisateurs** Une alternative à l'utilisation des Groupes d'Utilisateurs.
- **Onglet Permissions** Tous réglés sur **Hérité**.

#### Revue à Brouillon

Il s'agit du retour à une étape précédente dans la séquence invoqué lorsque le Président nécessite plus de travail de la part du Secrétaire. Les champs de formulaire sont similaires à ceux de Brouillon/Revue sauf pour la Remarque et les *Étape Actuelle* et *Étape Cible* qui sont inversées.

#### Revue à Publication

C'est la transition qui change l'état d'un article de *Non publié* à *Publié*. Seul le Président a la permission de faire ce changement.

- **Nom** *Revue/Publication*
- **Onglet Transition**
  - **Étape Actuelle** *Revue*
  - **Étape Cible** *Publication*
  - **Remarque** *La transition finale vers la publication.*
- **Onglet Actions de Transition**
  - **État en Vedette** *- Aucun Sélectionné -*
  - **État de Publication** *Publié*
- **Onglet Notification**
  - **Envoyer une Notification** *Oui* Les destinataires doivent avoir *Recevoir les Emails du Système* activé pour recevoir les notifications par email.
  - **Texte de Message Supplémentaire** *Un article du comité a été publié et est maintenant disponible pour consultation.*
  - **Groupes d'Utilisateurs** *Comité*
  - **Utilisateurs** Une alternative à l'utilisation des Groupes d'Utilisateurs.
- **Onglet Permissions**
  - **Secrétaire** Régler *Exécuter Transition* sur *Refusé*.

#### Publication à Revue

C'est un changement de Publication à Revue. Est-ce vraiment nécessaire ? Un article publié peut encore être modifié par le Secrétaire ou le Président. Peut-être qu'un document du Comité avec des données sensibles a été publié par erreur.

Si nécessaire, créez une Transition similaire à la transition *Revue à Publication* mais avec les Étapes inversées, les *Actions de Transition / État de Publication* réglées sur *Non Publié* et un message générique de *Texte de Message Supplémentaire*.

#### Archivage

C'est la transition exécutée lorsque un document du Comité n'est plus nécessaire. Dans le flux de travail, il reste dans l'étape de Publication mais l'état de l'article est changé de Publié à Archivé.

- **Nom** *Archivage*
- **Onglet Transition**
  - **Étape Actuelle** *Publication*
  - **Étape Cible** *Publication*
  - **Remarque** *Changer l'état de l'article de Publié à Archivé.*
- **Onglet Actions de Transition**
  - **État en Vedette** *- Aucun Sélectionné -*
  - **État de Publication** *Archivé*
- **Onglet Notification**
  - **Envoyer une Notification** *Non* Ce n'est pas une transition qui nécessite une action. 
- **Onglet Permissions**
  - **Secrétaire** Régler *Exécuter Transition* sur *Refusé*.

![Transitions du flux de travail](../../../en/images/workflows/example-2-transitions-committee-workflow.png)

## Créer une Nouvelle Catégorie

<div class="alert alert-warning">Cette étape est vraiment importante ! Les nouveaux documents du Comité doivent être créés avec cette catégorie, sinon ils adopteront le flux de travail par défaut qui nécessite un Super Utilisateur pour le changer.</div>

- **Titre** *Comité* 
- **Flux de travail** Sélectionnez *Flux de travail du Comité* dans la liste des flux de travail.
- **Autorisations** 
  - Auteur, Éditeur et Éditeur en chef : Tous réglés sur *Non autorisé* ou laissés sur *Non autorisé (Hérité)*.
  - Comité : Tous laissés sur *Hérité*.
  - Président : Tous sauf *Supprimer* réglés sur *Autorisé*.
  - Secrétaire : Tous sauf *Supprimer* et *Modifier l'état* réglés sur *Autorisé*.

## Créer un Élément de Menu

- **Titre** *Documents du Comité*
- **Type d'Élément de Menu** Liste de Catégories
- **Choisir une Catégorie** *Comité*
- **Accès** *Comité*

![Élément de menu des documents du comité](../../../en/images/workflows/example-2-menu-item.png)

## Vérifiez le Site

Connectez-vous successivement en tant qu'Alice, Bob, Charlie et un Super Utilisateur pour voir ce qu'ils peuvent voir :

Alice, Bob et Charlie peuvent voir l'élément de Menu, mais personne d'autre ne le peut, même pas un Super Utilisateur. Après avoir sélectionné l'élément du menu, Alice et Bob peuvent voir un tableau des documents du Comité, y compris ceux qui n'ont pas été publiés. Charlie ne peut voir qu'un tableau des documents publiés du Comité ou un message explicatif si aucun n'a été publié.

Alice et Bob peuvent également voir un lien Éditer pour chaque article et un bouton **Nouvel Article**. Cela est généralement utilisé par Bob pour créer un document du Comité, mais Alice peut également le faire.

![Vue de Bob de la liste des catégories des documents du comité](../../../en/images/workflows/example-2-committee-papers.png)

### Pour Créer et Publier un Document du Comité

- Connectez-vous en tant que Secrétaire et sélectionnez le bouton **Nouvel Article** dans la page *Documents du Comité*.
- Entrez le texte et *Enregistrez*. Cela peut être fait en plusieurs sessions d'édition, peut-être sur plusieurs jours ou semaines. L'article reste Non publié et au stade Brouillon jusqu'à...
- Sélectionnez l'onglet *Publication* dans le formulaire d'édition et définissez l'*Étape du Workflow* sur Exécuter la Transition **Brouillon/Examen**.
- Sélectionnez **Enregistrer & Fermer** pour effectuer la transition.
- Le travail du Secrétaire est pour l'instant terminé et un message a été envoyé au Président du Comité.
- Le Président se connecte, vérifie que le document est prêt pour l'Examen et utilise la transition **Examen/Publication** pour rendre le document *Publié*. Le travail du Président est pour l'instant terminé et un message est envoyé aux membres du Comité.
- Les membres du Comité peuvent se connecter et accéder au document publié. 

*Traduit par openai.com*

