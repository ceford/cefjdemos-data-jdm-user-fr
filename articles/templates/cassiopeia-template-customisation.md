<!-- Filename: J4.x:Cassiopeia_Template_Customisation / Display title: Personnalisation de Cassiopée -->

## Introduction

Cassiopeia est le modèle de site fourni avec Joomla 4. C'est un modèle d'usage général **accessible** et **réactif**. Il peut être personnalisé via les options de modèle et le fichier *user.css* par des utilisateurs ayant quelques connaissances en HTML et CSS.

L'illustration suivante montre l'apparence d'un site Joomla 4 avec un article et quelques éléments de menu créés.

![Vue d'article unique Cassiopeia](../../../en/images/templates/cassiopeia-customisation-article-view.png)

## Modèles : Modifier le style

Vous pouvez expérimenter avec l'apparence du site en ouvrant le formulaire Modifier le style. Allez dans **Système → Modèles → Styles du modèle de site** et sélectionnez le titre du modèle dans la colonne Style, Cassiopeia - Par défaut. L'onglet Avancé contient des réglages que vous pouvez ajuster :

![Cassiopeia modifier le style onglet avancé](../../../en/images/templates/cassiopeia-customisation-edit-style.png)

Pour essayer les options, ouvrez un onglet ou une fenêtre de navigateur avec l'interface Administrateur et un second onglet ou une fenêtre avec l'interface Site, puis alternez après chaque changement enregistré.

### Marque

- **Oui** par défaut. La barre de logo Cassiopeia contenant un logo ou un nom de marque est affichée avec un arrière-plan sombre, bleu par défaut.
- **Non** La barre de logo n'est pas affichée. Les options pour sélectionner un logo, un titre et une accroche disparaissent.

L'image de marque par défaut est le mot Cassiopeia en tant qu'image dans un fichier SVG. C'est ce qui est affiché dans la première illustration ci-dessus.

Vous pourriez définir la Marque sur Non si vous souhaitez fournir un branding dans un module HTML personnalisé.

### Logo

- **Aucun** Le logo d'image par défaut de Cassiopeia sera utilisé à moins qu'un Titre ne soit défini.
- **Image de logo** Le Logo sélectionné apparaîtra à la place du logo Cassiopeia même si un Titre est défini.

### Titre (alternative au logo)

- **Mon nom de marque** S'il est présent et que vous n'avez pas sélectionné d'image de logo, les mots dans le champ Titre apparaîtront mais en soulignés dans la barre bleue supérieure.

### Accroche

- **Toujours à votre service** Si elle est présente, les mots dans le champ accroche apparaîtront en petite taille de police sous l'image du logo ou le nom de la marque.

![Cassiopeia marque avec accroche](../../../en/images/templates/cassiopeia-customisation-brand-with-tagline.png)

### Schéma de polices

- **Aucun** par défaut. La famille de polices spécifiée dans la feuille de style du modèle est utilisée, ce qui signifie généralement que le site utilisera les polices que vous connaissez déjà disponibles sur votre propre ordinateur.
- **Autres** Une famille de polices située dans la hiérarchie des dossiers du modèle ou téléchargée depuis le web sera utilisée. Vous pouvez voir l'apparence modifiée du texte sur une page lorsque vous rechargez le site après avoir modifié cette option.

### Thème de couleur

- **Standard** Une couleur d'arrière-plan bleu foncé pour la barre de marque et d'autres éléments tels que le bouton Connexion.
- **Alternative** Une couleur d'arrière-plan bordeaux au lieu du bleu foncé.

![Cassiopeia schéma de couleurs alternatif](../../../en/images/templates/cassiopeia-customisation-alt-color-scheme.png)

### Disposition

- **Statique** par défaut. La largeur maximale est fixée à 1320px. Sur les écrans plus larges, la marge devient simplement plus large.
- **Fluide** Il n'y a pas de largeur maximale.

La vue sur un appareil mobile à écran étroit :

![Vue mobile Cassiopeia](../../../en/images/templates/cassiopeia-customisation-mobile-view.png)

### En-tête fixe

- **Non** par défaut. Les éléments d'en-tête et le contenu défilent vers le haut hors de la fenêtre.
- **Oui** Sauf sur les écrans étroits, les éléments d'en-tête restent fixés en haut de la fenêtre tandis que les éléments de contenu défilent vers le haut. Cela n'est évident que lorsque le contenu de la page est plus grand que la fenêtre.

### Lien retour en haut

- **Non** par défaut. Il n'y a pas de lien retour en haut.
- **Oui** Lorsque le contenu est plus grand que la fenêtre, en bas à droite de la page se trouve un bouton marqué d'un chevron vers le haut. Sélectionnez-le pour faire défiler vers le haut de la page.

![Cassiopeia retour en haut](../../../en/images/templates/cassiopeia-customisation-back-to-top.png)

## Positions des Modèles Cassiopeia

Lorsque vous construisez un site avec Cassiopeia, il devient vraiment utile de connaître les emplacements des positions que vous pouvez utiliser pour les modules. Certaines sont descriptives, comme *menu* et *bottom-a*, mais il n'est pas si évident de savoir où elles se trouvent avant de les utiliser. Cette illustration devrait vous aider :

![Positions des modèles Cassiopeia](../../../en/images/templates/cassiopeia-template-positions.png)

Essayez ce qui suit :

### Déplacer le Module Menu vers la Position *menu*

Un site Joomla 4 nouvellement installé a un menu dans la position *sidebar-right*, visible dans la première illustration ci-dessus. Pour ce tutoriel, certains éléments de menu ont été ajoutés, dont un qui est un parent avec deux éléments enfants. Pour déplacer ce menu vers la position menu, allez à **Contenu**→**Modules du site** dans le menu de l'Administrateur. Dans la liste, il y a trois modules, y compris le Menu Principal. Sélectionnez-le pour ouvrir le formulaire d'édition des Modules : Menu.

Dans l'onglet Module, changez le champ Position à Menu \[menu\]. Enregistrez et regardez le résultat dans l'affichage du site. Le menu a l'air correct, mais les éléments enfants n'y sont pas.

Dans le formulaire d'édition du menu, sélectionnez l'onglet Avancé et faites défiler jusqu'au champ Layout. C'est une liste déroulante avec quatre options. --From Module-- / Default est sélectionné par défaut. Essayez les autres options et visualisez le résultat. (N'oubliez pas de *sauvegarder* dans le formulaire d'édition et de recharger dans la vue du Site.) Aucune des options --From Module-- n'affiche les éléments du menu enfant, mais les deux options --From Cassiopeia Template-- le font.

![Positions menu Cassiopeia](../../../en/images/templates/cassiopeia-customisation-menu-position.png)

Alors quelle différence fait **Rétractable** ?

- Liste rétractable : Sur les appareils mobiles à écran étroit, le menu se rétracte en une icône Hamburger jusqu'à ce qu'il soit sélectionné. Lors de la sélection, il s'étend pour montrer une liste verticale.
- Liste déroulante : Le menu apparaît toujours sous forme de liste verticale.

### Déplacer le Module Menu vers la Position *topbar*

Dans l'onglet Module du formulaire d'édition, définissez la Position à Barre Supérieure \[topbar\] et regardez le résultat. Il y a un problème - le menu est positionné plus à gauche que lorsqu'il était dans la position du menu. C'est parce que la position du menu et l'emplacement du logo ont une classe CSS de *grid-child*, mais la barre supérieure ne l'a pas. Cela peut être corrigé avec une entrée dans le fichier *user.css*, ci-dessous.  

## Personnaliser Cassiopeia

Que faire si vous n'aimez pas la couleur du fond d'en-tête bleu foncé ? Supposons que vous préfériez un thème vert foncé. Pour régler cela, vous devez avoir quelques connaissances en CSS. Allez dans **Système**→**Modèles de site**→**Détails et fichiers de Cassiopeia** pour ouvrir le formulaire du modèle : Personnaliser (Cassiopeia).

L'illustration ci-dessous montre deux groupes de dossiers. Le premier groupe se compose des dossiers et fichiers de modèle que vous ne devez pas modifier, mais auxquels vous pouvez ajouter. En particulier, vous pouvez ajouter des fichiers HTML de remplacement de modèle au dossier *html*. Le second groupe contient les fichiers média du modèle que vous ne devez pas modifier. Cependant, vous pouvez ajouter un fichier *user.css* dans le dossier *css* et/ou un fichier *user.js* dans le dossier *js*. Vous le feriez si vous vouliez effectuer quelques modifications simples de l'apparence du site.

![Cassiopeia éditer fichiers](../../../en/images/templates/cassiopeia-customisation-edit-files.png)

Notez qu'il n'y a pas de fichier *user.css* présent dans le dossier *css*. C'est un fichier que vous créez vous-même afin de pouvoir remplacer les styles définis précédemment. S'il n'est pas présent, créez-le maintenant en sélectionnant le dossier *css* puis le bouton *Nouveau*. Dans la boîte de dialogue pour un nouveau fichier, sélectionnez le dossier *css* sinon le nouveau fichier apparaîtra au mauvais endroit. Entrez user (en minuscules et sans *.css*) dans le champ Nom du fichier et sélectionnez *.css* dans le champ Type de fichier. Sélectionnez le bouton Créer pour créer le fichier. Si *user.css* est déjà présent, sélectionnez-le pour ouvrir le formulaire d'édition.

### En-têtes

Pour commencer simplement, changez la couleur des en-têtes en vert foncé. Les en-têtes sont des balises dans la gamme *h1, h2, h3, h4, h5* et *h6*. Dans le fichier *user.css* entrez la définition du style :
```css
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
```
Enregistrez et rechargez le site pour voir le résultat. Le titre de la page ou de l'article devrait être vert foncé. Si ce n'est pas le cas, vérifiez ce que vous avez tapé. Le langage officiel pour la documentation Joomla est l'anglais britannique, donc "colour" plutôt que "color" comme en anglais américain. Mais en CSS il faut que ce soit "color". La ponctuation est-elle correcte ?

Il n'est pas si évident que certaines balises autres que les en-têtes peuvent être stylisées pour ressembler à des en-têtes. Ajoutez donc ceci :
```css
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
```
Notez ici que le point avant (.) est un sélecteur de classe, par exemple Dummy H1 - donc il y a un point dans le fichier CSS mais pas dans le nom de la classe.

### Fond de l'en-tête

Dans l'onglet du navigateur contenant le site, ouvrez vos outils de développement de navigateur, Firefox dans cet exemple, et sélectionnez la balise d'en-tête.

![Outils de développement Cassiopeia](../../../en/images/templates/cassiopeia-customisation-developer-tools.png)

Cela montre les styles utilisés. Le style container-header est où le couleur de fond et l'image de fond sont définis. Ils doivent être surchargés dans le fichier *user.css*. Essayez ceci :
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
```
### Style *topbar*

Rappelez-vous ce commentaire sur le menu étant trop à gauche dans le topbar ? C'est parce qu'il n'a pas de largeur maximale et de marges appropriées définies. Mettez ceci dans le fichier *user.css* pour corriger cela :
```css
    .container-topbar {
      max-width: 1320px;
      margin-left: auto;
      margin-right: auto;
    }
```
Ceci est le thème vert fonctionnel :

![Cassiopeia thème vert](../../../en/images/templates/cassiopeia-customisation-green-theme.png)

### Accessibilité

Notez qu'il doit y avoir un contraste suffisant entre les couleurs de fond et de premier plan pour respecter les normes d'accessibilité du web. Vous pouvez vérifier votre contraste sur le WebAIM Contrast Checker. Le vert foncé est \#006400.

## Remplacements

L'onglet Créer des Remplacements dans le formulaire Personnaliser les Modèles : Cassiopeia affiche la liste des extensions pour lesquelles vous pouvez créer un remplacement. Notez les différents symboles : sélectionnez un symbole de dossier pour afficher une liste des dossiers et fichiers qu'il contient ; sélectionnez un symbole de fichiers multiples pour créer immédiatement un remplacement pour cette extension ; l'élément créé disparaît de la liste - sélectionnez l'onglet Éditeur et trouvez le remplacement créé dans le dossier *html*. Il peut y avoir plus d'un fichier créé - les fichiers créés sont copiés depuis l'extension originale, prêts pour que vous les modifiiez. Pour cela, vous devez connaître un peu de HTML et de PHP !

Voici l'onglet Créer des Remplacements :

![Création de remplacements dans Cassiopeia](../../../en/images/templates/cassiopeia-customisation-create-overrides.png)

Si vous faites simplement des essais et ne souhaitez vraiment pas un remplacement, vous pouvez *Fermer* le formulaire d'édition, sélectionner le bouton Gérer les Dossiers dans la barre d'outils et sélectionner le bouton Supprimer en bas du formulaire modal Gérer les Dossiers.

Les remplacements concernent vraiment la personnalisation des extensions plutôt que le modèle Cassiopeia, et c'est une autre histoire.

## Modèles Enfants

Si vous souhaitez apporter des modifications plus substantielles à l'apparence du site, vous pourriez créer un modèle enfant. Cela copie juste une petite sélection de dossiers et de fichiers que vous pouvez modifier ou ajouter, tout en continuant à utiliser les dossiers et fichiers du modèle parent. En utilisant des modèles enfants, vous pourriez avoir certaines pages avec une couleur de thème et d'autres pages avec une couleur de thème différente. Les modèles enfants sont abordés ailleurs. Voici une illustration de la structure de fichiers dans un enfant de Cassiopeia :

![Fichiers du modèle enfant Cassiopeia](../../../en/images/templates/cassiopeia-customisation-child-template-files.png)

