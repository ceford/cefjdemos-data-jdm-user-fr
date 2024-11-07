<!-- Filename: J6.x:Article_Access_Restriction / Display title: Article : Restriction d'accès  -->

## Introduction

Il existe plusieurs raisons de restreindre l'accès aux articles sur un site web. Certains contenus peuvent être privés pour des utilisateurs spécifiques, comme les membres d'un comité. Ou bien le site peut contenir du contenu commercial à accès payant. Joomla offre un système puissant de liste de contrôle d'accès (ACL) pour restreindre l'accès. Il est décrit dans un article séparé sur le [Contrôle d'Accès](jdocmanual?article=user/users/access-control) dans la section Utilisateur de ce manuel.

Cet article décrit la mise en œuvre de la restriction d'accès dans le formulaire *Article : Édition*.

## Restriction par Niveau d'Accès

Joomla fournit les Niveaux d'Accès visibles dans la capture d'écran suivante :

![Niveaux d'accès des utilisateurs](../../../en/images/articles/article-access-user-groups.png)

Les niveaux d'accès apparaissent dans l'onglet *Contenu* du formulaire *Article : Éditer*.

- **Public** Peut être vu par tout le monde - aussi bien par les utilisateurs connectés que par ceux qui ne le sont pas.
- **Invité** Ce niveau d'accès restreint l'accès aux utilisateurs qui **NE SONT PAS** connectés.
- **Enregistré** Ce niveau restreint l'accès aux utilisateurs connectés. Un article avec l'*Accès* défini sur *Enregistré* nécessitera une connexion au front-end avant que l'article puisse être consulté.
- **Spécial** Ce niveau restreint l'accès aux utilisateurs qui sont connectés et font partie d'un groupe d'utilisateurs spécifique autre qu'Enregistré. De plus, il est possible de différencier le contenu que certains utilisateurs connectés peuvent accéder mais d'autres pas. Typiquement, cela pourrait être un site web où des abonnements sont requis pour accéder à du contenu supplémentaire.
- **Super Utilisateurs** Définir ce niveau signifie que seul un Super Utilisateur peut accéder à l'article. Cela pourrait être utilisé pour des articles sur la gestion du site.

Notez que cette liste concerne la **Visualisation** ou le fait d'avoir la permission de voir le contenu. Vous pouvez créer des niveaux d'accès supplémentaires et des groupes d'utilisateurs afin de personnaliser qui peut voir quoi.

## Restriction Partielle pour Lire Plus

Parfois, vous pourriez souhaiter restreindre l'accès à un article tout en permettant un accès libre à un aperçu de l'article. C'est une méthode courante pour mettre en place un accès payant à du contenu commercial. Procédure :

- Trouvez l'article à restreindre partiellement dans la liste des *Articles* et ouvrez-le pour édition.
- Insérez un *Saut de Page* après le premier paragraphe. L'outil Saut de Page se trouve près du bas de la liste *Contenu CMS* dans le formulaire d'édition d'article TinyMCE.
- Définissez le niveau d'*Accès* de l'article sur *Enregistré*.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

### Restreindre l'accès à des Articles individuellement

Ouvrez l'élément de menu *Blog Catégorie* ou *Articles en Vedette* où l'article apparaîtra.

- Dans l'onglet **Options**, réglez **Liens non autorisés** sur **Oui**. C'est en bas de la liste des Options.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

### Restreindre l'accès aux Articles Globalement

* Définissez les Catégories concernées à un niveau de vue *Public*, sinon les éléments de menu ne seront pas visibles pour les utilisateurs non connectés.
* Définissez les articles des Catégories concernées à un niveau de vue Enregistré. Cela peut être fait en sélectionnant les articles et en utilisant le bouton *Batch*.
* Allez à **Contenu → Articles → Options**
* Réglez **Liens non autorisés** sur **Oui** dans l'onglet Articles. Si réglé sur Oui, les liens vers le contenu enregistré seront affichés même si vous n'êtes pas connecté. Vous devrez vous connecter pour accéder à l'élément complet.

**Remarque :** Le texte dans un Article sans un saut de *Lire Plus* est traité comme tout texte d'introduction. Si vous avez un Article censé être restreint aux utilisateurs Enregistrés uniquement mais ne possède pas de Lire Plus, alors tout l'article sera visible pour tous les utilisateurs. Ajoutez donc un Lire Plus à l'article ! 

*Traduit par openai.com*

