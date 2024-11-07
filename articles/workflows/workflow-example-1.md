<!-- Filename: J6.x:Workflow_Scenarios_Example_1 / Display title: Exemple de Flux de Travail 1  -->

## Introduction

Un flux de travail consiste en des *étapes* et des *transitions* entre ces étapes. Pour tout article, c'est l'étape actuelle qui est enregistrée dans la base de données et utilisée pour identifier le flux de travail et les transitions utilisées par ce flux de travail.

Un seul site peut avoir de nombreux flux de travail. Ici, un *Flux de travail de bulletin d'information* est utilisé comme exemple pour expliquer comment trois personnes ayant des rôles différents peuvent être impliquées dans la production d'un article de bulletin d'information. L'exemple utilise les groupes d'utilisateurs par défaut de Joomla : Auteur, Éditeur et Éditeur en chef. Cela pose un problème : un Auteur peut uniquement voir les articles publiés et ne peut donc pas rééditer les articles non publiés. Une méthode pour éviter ce problème est couverte dans [Exemple 2](jdocmanual?article=user/workflows/workflow-example-2).

![Liste des flux de travail](../../../en/images/workflows/example-1-workflows-list.png)

Remarquez que le *Flux de travail de base* est défini comme le *Par défaut*. Cela peut avoir des conséquences problématiques couvertes plus loin dans cet article !

## Les Utilisateurs

- *Arthur* est un utilisateur assigné au **Groupe Auteur** de Joomla. Il peut créer de nouveaux articles et modifier ses propres articles mais il ne peut pas modifier les articles écrits par d'autres utilisateurs ni changer l'état des articles. Par conséquent, il ne peut pas publier ses propres articles. Son travail consiste à rédiger de nouveaux articles.
- *Eddie* est un utilisateur assigné au **Groupe Éditeur** de Joomla. Il peut modifier des articles créés par n'importe quel utilisateur, y compris Arthur et lui-même. Lui aussi ne peut pas changer l'état d'un article. Son travail consiste à revoir les articles soumis par Eddie, à vérifier la précision, l'orthographe et la grammaire, la qualité des images, etc.
- *Pru* est une utilisatrice assignée au **Groupe Éditeur** de Joomla. Elle peut faire tout ce que Eddie et Arthur peuvent faire. De plus, elle peut changer l'état d'un article. Il est de sa responsabilité de décider si un article est acceptable pour publication et de le publier.

## Les Étapes

Il y a quatre étapes dans ce flux de travail :

![Liste des flux de travail](../../../en/images/workflows/example-1-workflow-stages.png)

- **Brouillon** est l'étape créée par Arthur pour un nouvel article.
- **Relecture** est l'étape où Eddie prend le relais pour relire le contenu.
- **Approbation** est l'étape où Pru prend le relais pour décider si l'article est suffisamment bon pour être publié.
- **Publication** est l'étape lorsque l'article a été approuvé et publié.

Les formulaires de saisie de données des étapes nécessitent peu d'explications, juste un nom et une description.

## Les Transitions

Deux transitions sont nécessaires entre chaque étape : une pour revenir à l'étape précédente si plus de travail est requis ; et une seconde pour migrer à l'étape suivante. Des transitions supplémentaires sont nécessaires pour gérer la suppression d'un article :

![Liste des flux de travaux](../../../en/images/workflows/example-1-workflow-transitions.png)

- **Ébauche/Revue** pour déplacer l'étape de l'Ébauche à la Revue.
- **Revue/Ébauche** pour revenir de l'étape Revue à l'Ébauche.
- **Revue/Approuver** pour déplacer l'étape de l'Approbation à la Revue.
- **Approuver/Revue** pour revenir de l'étape Approbation à la Revue.
- **Revue/Publier** pour déplacer l'étape à publiée et changer le statut de l'article en *Publié*.
- **Publier** Pour définir l'état de l'article à *Publié* lorsque la transition est exécutée par un Auteur ou un Éditeur.
- **Dépublier** pour changer le statut de l'article en *Non publié*.
- **Archiver** pour changer le statut de l'article en *Archivé*.
- **Poubelle** pour changer le statut de l'article en *Mise à la corbeille*.

Les trois dernières transitions permettent à Pru de changer le statut d'un article lorsqu'il n'est plus nécessaire.

### Éditer la Transition

Le formulaire de saisie des données comporte quatre onglets en commençant par l'onglet *Transition* :

![Liste des flux de travaux](../../../en/images/workflows/example-1-edit-transition.png)

- **Nom** Il est préférable d'utiliser les étapes actuelles et cibles dans le nom.
- **Étape actuelle** L'étape avant que la transition n'ait lieu.
- **Étape cible** L'étape après que la transition ait eu lieu.
- **Note** Toute note explicative pour aider à expliquer la transition.

#### L'onglet *Actions de Transition* :

![Liste des flux de travaux](../../../en/images/workflows/example-1-edit-transition-actions.png)

- **État en Vedette** Définir l'état en vedette que doit avoir un élément après avoir exécuté cette transition. Laissez cette option à *-Non Sélectionné-* si l'utilisateur susceptible d'exécuter cette transition n'a pas la permission de mettre en avant des articles.
- **État de Publication** Définir l'état publié qu'un élément doit avoir après avoir exécuté cette transition. Laissez cette option à *-Non Sélectionné-* si l'utilisateur susceptible d'exécuter cette transition n'a pas la permission de changer l'état de l'article.

#### L'onglet *Notifications* :

![Liste des flux de travaux](../../../en/images/workflows/example-1-edit-transition-notification.png)

- **Envoyer une Notification** Réglez ceci à *Oui* là où des notifications sont nécessaires, par exemple quand Arthur doit informer Eddie qu'un article est prêt pour la revue.
- **Texte du Message Supplémentaire** Ceci est un texte supplémentaire générique pour aider le destinataire.
- **Groupes d'Utilisateurs** Vous pouvez choisir d'envoyer la notification à un ou plusieurs groupes d'utilisateurs ou à aucun et envoyer la notification à des individus à la place.
- **Utilisateurs** Sélectionnez les utilisateurs individuels dans la liste des utilisateurs.

#### L'onglet *Permissions* :

Notez que *Auteur* a *Exécuter Transition* réglé à Autorisé (Hérité). Ne changez pas ces paramètres pour les autres transitions qu'un Auteur ne devrait pas utiliser car cela affecterait également les Éditeurs et les Éditeurs en chef.

## La Catégorie d'Article

Chaque article est assigné à un flux de travail lors du premier enregistrement. Si l'article est d'abord
assigné à une catégorie qui a un flux de travail sélectionné, il est assigné à ce flux de travail. Sinon, il est assigné au flux de travail par défaut. Cela peut être problématique car le composant de flux de travail ne fournit pas de méthode pour changer le flux de travail une fois qu'il est attribué. Il peut être modifié par un Super Utilisateur en utilisant l'Action par lot dans la page de liste des Articles.

### Créer une Catégorie de Newsletter

Une nouvelle catégorie de Newsletter est nécessaire pour afficher la Newsletter comme un Blog de Catégorie et pour s'assurer que les articles de la Newsletter sont assignés au flux de travail de la Newsletter.

![Liste des flux de travail](../../../en/images/workflows/example-1-newsletter-category.png)

## L'Élément de Menu Bulletin

Pour que les visiteurs du site puissent voir le Bulletin, il doit être sur la page d'accueil ou lié à un élément de menu. Pour suivre cet exemple, créez un nouvel élément de menu de type *Blog de Catégorie* en utilisant la catégorie *Bulletin*.

Essayez l'élément de menu du site. Il s'agit probablement d'une page vierge avec ce message :

<div class="alert alert-info">
Il n'y a pas d'articles dans cette catégorie. Si des sous-catégories s'affichent sur cette page, elles peuvent avoir des articles.
</div>

## Se connecter en tant qu'Arthur

Vous vous souvenez d'Arthur l'Auteur ? Après connexion, la page Newsletter devrait avoir un bouton intitulé **Nouvel Article**. Sélectionnez-le pour composer un nouvel article.

### Composer un Article

Remplissez le formulaire d'édition d'article comme vous le feriez pour n'importe quel article. Sauf qu'avant le premier enregistrement, regardez l'onglet *Publication*.

- **Étape de Workflow** doit être réglée sur **Exécuter la Transition** *Brouillon/Revue*.
- **Catégorie** doit être réglée sur *Newsletter*.

Lorsque vous avez terminé l'édition de l'article, sélectionnez *Enregistrer* ou *Enregistrer & Fermer*.

<div class="alert alert-danger">Après avoir fermé l'article, Arthur ne peut plus l'éditer car les utilisateurs du groupe Auteur ne peuvent pas voir les articles non publiés.</div>

## Se connecter en tant qu'Eddie

Eddie l'Éditeur a la permission de voir les articles non publiés, donc la page de la Newsletter affiche tous les articles non publiés pour qu'il puisse les éditer.

### Revoir l'article

Sélectionnez l'article rédigé par Eddie et apportez les modifications nécessaires pour l'améliorer. Une fois satisfait, dans l'onglet *Publication* :

- **Étape du Workflow** doit être réglée sur **Exécuter la transition** *Réviser/Approuver*.

Contrairement à Arthur qui ne peut pas voir son article après l'avoir enregistré, Eddie peut voir et éditer l'article à nouveau. Il peut également définir la transition pour la prochaine étape sur Approuver/Publier. La transition fonctionnera mais l'article ne sera pas publié car Eddie n'a pas la permission de Publier.

## Se connecter en tant que Pru

Lorsque l'étape d'approbation a été définie dans le processus, Pru aurait dû recevoir un message l'incitant à agir. Connectez-vous donc en tant que Pru pour examiner l'article et définir son étape de workflow sur **Exécuter la Transition** *Publier*. *Enregistrer et Fermer* l'article pour voir le résultat publié. Déconnectez-vous pour voir le résultat sans le lien Modifier.

Remarque : une autre étape est nécessaire pour permettre à Pru de revenir à l'étape de publication à révision si elle souhaite qu'Eddie corrige quelque chose.

## Flux de travail du Backend

Les groupes d'utilisateurs Auteur, Éditeur et Éditeur en chef sont destinés à être utilisés en frontend. Le problème pour Arthur est qu'il ne peut pas accéder à ses articles en brouillon depuis le frontend, car son groupe d'utilisateurs n'a pas accès aux articles non publiés.

Vous pouvez autoriser l'accès au backend pour tous les membres de ces groupes comme suit :

- Allez à la page **Configuration Globale**.
- Sélectionnez l'onglet **Permissions**.
- Sélectionnez *Auteur* et définissez **Connexion Administrateur** sur *Autorisé*.
- **Enregistrer**
- Allez à la page **Articles : Options**.
- Sélectionnez son onglet **Permissions**.
- Sélectionnez *Auteur* et définissez **Accès à l'interface d'administration** sur *Autorisé*.

Cela permettra à Arthur, Eddie et Pru de se connecter au backend avec accès aux éléments de Contenu. Un tableau de bord d'accueil beaucoup réduit :

![Tableau de bord d'accueil pour Arthur](../../../en/images/workflows/example-1-backend-home.png)

Mais Arthur a accès à ses articles en brouillon :

![Liste d'articles pour Arthur](../../../en/images/workflows/example-1-backend-articles.png)

Notez qu'Arthur ne peut pas modifier le dernier élément de la liste car ce n'est pas l'un de ses propres articles. Le titre de l'article n'est pas lié. De même, Arthur ne peut modifier aucune des catégories existantes car il n'a pas la permission et elles ne sont pas non plus liées. Il peut créer une nouvelle catégorie, mais celle-ci est non publiée et il ne peut pas la publier !

## Correction pour Mauvais Flux de Travail

Si vous assignez un article au mauvais flux de travail, deux méthodes sont disponibles pour résoudre le problème.

### Méthode Super Utilisateur

- Allez dans la liste des **Articles**.
- Cochez la case de l'article problématique.
- Sélectionnez le bouton **Actions** dans la barre d'outils.
- Sélectionnez le bouton **Lot** dans la liste.
- Sélectionnez **Changer l'étape** dans le dialogue *Traitement par lot des articles sélectionnés*.
- Choisissez un flux de travail et une étape appropriés.
- Sélectionnez le bouton **Traiter**.

![Liste des articles pour Arthur](../../../en/images/workflows/example-1-backend-batch.png)

### Méthode de Secours

Alternativement, vous pouvez modifier une table de la base de données avec phpMyAdmin ou un outil similaire.

Informations requises :

- L'ID de l'article de la dernière colonne de la liste des articles.
- L'ID d'une étape dans le flux de travail requis de la dernière colonne de la liste
  des étapes du flux de travail que vous souhaitez utiliser.

Dans phpMyAdmin :

- Parcourez la table #__workflow_associations pour trouver l'item_id qui contient
  l'ID de votre article.
- Changez la valeur de stage_id par l'ID de l'étape que vous avez recherché dans le
  flux de travail requis.

Retournez à votre liste d'articles et vérifiez que l'article problématique utilise
maintenant le bon flux de travail.

*Traduit par openai.com*

