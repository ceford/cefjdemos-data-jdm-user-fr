<!-- Filename: J4.x:Setup_a_Multilingual_Site / Display title: Configurer un site multilingue  -->

## Données d'échantillon

Joomla est livré avec deux ensembles de données d'échantillon : Blog et Multilingue. Il existe un troisième ensemble de test mais uniquement pour les utilisateurs travaillant avec la version de développement de Joomla. Si vous avez un site existant avec des articles, des menus et des modules, il sera similaire en principe à un site avec les données d'échantillon Blog installées.

Dans le tableau de bord principal, les données d'échantillon multilingues indiquent **Avant de commencer, assurez-vous d'avoir au moins 2 langues installées avec leurs langues de contenu et qu'aucune donnée d'échantillon n'a été installée**. Cela vous amènera probablement à créer un site multilingue en exécutant manuellement les étapes requises une par une. C'est une procédure sujette à erreur dans laquelle vous êtes susceptible de faire une erreur, surtout si vous utilisez plusieurs langues. Les erreurs peuvent être corrigées, mais l'ensemble du processus est un peu fastidieux et peut être déroutant.

Vous pouvez ignorer ce conseil et utiliser les données d'échantillon multilingues pour configurer un site multilingue si vous comprenez comment apporter quelques corrections aux menus et modules originaux plus tard.

## Site Initial

Un site Joomla nouvellement installé possède un **Menu Principal** dans la barre latérale droite. Il contient un seul élément de menu nommé **Accueil** de type Articles en vedette. Il y a aussi un **Formulaire de Connexion** dans la barre latérale droite.

Au départ, il n'y a pas d'articles en vedette, donc la partie principale de la page est vide.

## Exemple de données de blog

Si vous avez créé votre propre contenu de site, vous ne devriez **pas** installer les données d'exemple de blog. Cependant, veuillez lire cette section pour voir comment elle se compare. Autrement :

- Sélectionnez **Installer** dans la section des Données d'Exemple Multilingues du Tableau de Bord Accueil. Les étapes d'installation apparaîtront brièvement puis disparaîtront.
- Vous devriez remarquer que plusieurs nouveaux menus sont installés (rechargez la page administrateur et développez le menu Menus) :
  - Menu Principal du Blog.
  - Menu du Bas, contenant des éléments de menu Connexion/Déconnexion.
  - Menu Spécial, visible après la connexion.
- Sélectionnez l'icône **Ouvrir le frontend** dans la barre de statut en haut ou rechargez le Site s'il est déjà ouvert dans un onglet séparé.

Vous devez vous attendre à voir une mise en page remplie d'informations sur les Articles en Vedette :

- En haut se trouve le nouveau menu **Menu Principal du Blog** pour divers agencements de blog et articles.
- Dans la barre latérale droite se trouvent des modules pour un Formulaire de Connexion, un Menu Principal et un flux RSS de Mon Blog.
- Après la connexion, la barre latérale droite a un Menu Spécial pour les actions réservées à l'Administrateur.
- L'élément **Accueil** du Menu Principal mène à la mise en page des Articles en Vedette.
- L'élément **Blog** en haut mène à une mise en page de Catégorie de Blog quelque peu différente de celle des Articles en Vedette.

Prenez quelques minutes pour explorer les éléments de menu et les types d'informations auxquels ils mènent.

## Installer et Publier les Langues de Contenu

Commencez par installer toutes les langues que vous envisagez d'utiliser. Si vous devez installer une langue supplémentaire plus tard, vous devrez compléter manuellement les étapes de configuration pour cette langue, une par une. Cela sera couvert ailleurs. Pour ce tutoriel, le français, l'allemand et le gallois ont été ajoutés à la langue par défaut en anglais du site lors de l'installation de Joomla. Pour ajouter des langues après l'installation :

- Sélectionnez **Système** → **Installer des Langues** dans le menu Administrateur.
- Sélectionnez le bouton **Installer** pour chaque langue que vous proposez d'utiliser.

Les langues installées doivent être **publiées** pour les rendre disponibles. Depuis le menu Administrateur :

* Sélectionnez **Système / Panneau de gestion / Langues de contenu**
* Dans la colonne Statut, **Publiez** chacune des langues que vous souhaitez utiliser.

## Données d'exemple multilingues

L'installation des données d'exemple multilingues a des effets dont vous devrez vous occuper plus tard :

- Les menus dans la barre latérale droite seront dépubliés. Cela signifie que le module du Menu Principal sera dépublié et qu'il n'y aura pas de lien vers la mise en page des Articles en Vedette. Si vous aviez d'autres liens dans le Menu Principal, ils seront également indisponibles.
- Le Menu Spécial sera dépublié. Cela fournissait un lien pour créer un nouveau post.

Les données d'exemple multilingues offrent les fonctionnalités supplémentaires suivantes :

- Une catégorie d'article pour chaque langue.
- Un article configuré pour chaque langue, bien qu'en texte pseudo Lorem ipsum.
- Un menu séparé pour chaque langue. Vous verrez cela dans la liste **Administrateur → Menus**.
- Un module de menu **Menu Principal xx-YY** dans la barre latérale droite du site, où xx-YY est un code de langue tel que en-GB.
- L'élément de menu **Principal** mène désormais à une mise en page de Blog de Catégorie pour les articles dans la langue sélectionnée. Il contient un seul article.
- Il y a un module **Sélecteur de Langue** dans la barre latérale droite. Il est sans titre pour éviter la nécessité d'un module séparé pour chaque langue avec des titres traduits. La sélection se fait par drapeau de langue. Essayez-le.

À noter : les mots fournis par Joomla seront traduits, par exemple dans le Fil d'Ariane et le Formulaire de Connexion. Les mots tapés par les utilisateurs doivent être traduits manuellement, par exemple Formulaire de Connexion et Menu Principal. Plus d'informations à ce sujet plus tard.

## Résolution des problèmes initiaux

### Ordre des langues

Vous pouvez remarquer que le sélecteur de langue affiche les langues dans un ordre alphabétique inversé. Pour changer l'ordre :

- Sélectionnez **Système → Langues de contenu** dans le menu Administrateur.
- Utilisez les icônes de points de suspension verticaux pour faire glisser les langues dans l'ordre souhaité.
- Rechargez le site et vérifiez que le sélecteur de langue affiche maintenant les langues dans votre ordre préféré.

### Ordre des modules de la barre latérale droite

L'ordre des modules dans la barre latérale droite est une question de préférence personnelle. Pour changer l'ordre :

- Sélectionnez **Contenu → Modules du site** dans le menu Administrateur.
- Filtrez par **Position → sidebar-right**.
- Sélectionnez l'icône de la colonne d'ordre pour révéler les poignées de glissement d'ordre (icônes de points de suspension verticaux). L'icône de l'en-tête de colonne devrait être un chevron pointant vers le haut.
- Faites glisser les éléments dans l'ordre :
  - Sélecteur de langue
  - Menu principal (toutes variantes - l'ordre n'a pas d'importance).
  - Menu spécial
  - Formulaire de connexion
  - Articles archivés
  - Diffusion

### Articles en vedette

Le menu principal d'origine est non publié, mais l'élément de menu Accueil qu'il contient peut être reproduit ailleurs. L'endroit le plus pratique est le menu supérieur.

- Sélectionnez **Menus → Menu Principal Blog** dans le menu Administrateur.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
- Entrez un **Titre** dans le formulaire **Menus : Nouvel Élément**, par exemple **En vedette**.
- Utilisez le bouton **Sélectionner** dans le champ **Type d'élément de menu**.
- Sélectionnez **Articles → Articles en vedette** dans la liste des **Types d'élément de menu**.
- Sélectionnez **Enregistrer** dans la barre d'outils.
- Dans le champ **Ordre**, sélectionnez **- Premier -**.
- Dans l'onglet **Disposition du Blog**, réglez **Articles d'intro** à 3.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

### Affectation des modules du site

La disposition initiale des Articles en vedette de la page d'accueil a été créée en assignant des modules sélectionnés pour n'apparaître que sur cette seule page. La nouvelle page En vedette doit être ajoutée pour chacun de ces modules.

- Sélectionnez **contenu → Modules du site** dans le menu Administrateur.
- Trouvez et sélectionnez l'élément **Image**.
- Dans l'onglet **Affectation de menu**, trouvez et cochez l'élément **En vedette** dans la section **Menu Principal Blog**.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.
- Trouvez et sélectionnez l'élément **Derniers articles**.
- Dans l'onglet **Affectation de menu**, trouvez et cochez l'élément **En vedette** dans la section **Menu Principal Blog**.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

## Recharger le site

Lorsque vous rechargez le site, le premier élément du menu supérieur sera le lien "À la une" menant à la mise en page des articles en vedette. L'élément Blog adjacent est une mise en page de Blog de Catégorie plus compacte. Essayez le sélecteur de langue. Le texte fourni par Joomla, dans les fils d'Ariane et le formulaire de connexion, change en conséquence. De plus, les articles en vedette incluent maintenant un article issu des données d'exemple multilingues, dans la langue sélectionnée. Celui-ci peut se trouver sur la dernière page.

### Site multilingue hybride ou pur

À ce stade, vous avez un site hybride : certains contenus sont disponibles dans toutes les langues et d'autres dans une langue spécifique. Si vous souhaitez un site purement multilingue, vous devrez dépublier le module Blog du menu principal, et peut-être d'autres. Dans certains cas, vous souhaiterez peut-être produire des modules spécifiques à une langue, par exemple, le formulaire de connexion pourrait avoir des versions avec les titres Formulaire de connexion, Login Formular et Ffurflen Mewngofnodi.

Ce que vous faites ensuite dépend de vous !

## Menu Principal Original

Votre module de Menu Principal original, qui est maintenant non publié, pourrait avoir contenu des éléments de menu supplémentaires. Vous pourriez le publier. Le problème est que l'élément Accueil renvoie au même emplacement que chacune des pages d'accueil de menu spécifiques à une langue, mais uniquement en anglais. Vous pouvez contourner cela de la manière suivante :

- Sélectionnez **Menus** → **Menu Principal** dans le menu de l'administrateur.
- Sélectionnez l'élément de menu **Accueil**.
- Sélectionnez l'onglet **Type de lien**.
- Réglez **Afficher dans le menu** sur **Non**.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.
- Sélectionnez **Contenu** → **Modules du site** dans le menu de l'administrateur.
- Trouvez le **Menu Principal** et publiez-le, en changeant la croix grise en une coche verte.

Les éléments visibles dans le Menu Principal original devraient maintenant fonctionner normalement. Si le Menu Principal n'a pas d'éléments visibles, il ne sera pas affiché.  

## Ajouter une Langue Supplémentaire

Après la configuration initiale d'un site multilingue, si vous souhaitez ajouter une autre langue, vous devrez passer par les étapes manuellement, une par une :

### Étape 1 : Installer la Langue

- Sélectionnez **Système **→** Installer **→** Langues** dans le menu de l'Administrateur.
- Trouvez la langue requise dans la liste **Extensions : Langues**.
- Sélectionnez le bouton **Installer**.
- Un message apparaîtra : **L'installation du pack de langue a été réussie.**

Dans cet exemple, la langue supplémentaire est l'espagnol.

### Étape 2 : Publier et Classer

- Sélectionnez **Système **→** Gérer **→** Langues de Contenu** dans le menu de l'Administrateur.
- Activez la langue nouvellement installée : sélectionnez le bouton Statut pour transformer la croix grise en coche verte.
- Utilisez les icônes de points de suspension verticales pour faire glisser les langues dans l'ordre désiré.

### Étape 3 : Créer un Menu

- Sélectionnez **Menus **→** Gérer** dans le menu de l'Administrateur.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
- Entrez un titre de menu approprié et un nom unique, exemples : Menu Principal (es-ES) et menumain-es-es.
- Entrez une description, par exemple : Le menu principal pour le site en langue espagnole (es-ES).

### Étape 4 : Ajouter un Module de Menu

- Sélectionnez **Menus **→** Gérer** dans le menu de l'Administrateur.
- Sélectionnez le bouton **Ajouter un module pour ce menu** pour le menu nouvellement créé.
- Entrez un titre approprié, par exemple : Menu Principal es-ES
- Sélectionnez une Position : Sidebar-droite
- Sélectionnez une Langue : espagnol (es-ES)
- Sélectionnez **Enregistrer**.
- Classez le module : dans la liste de classement, sélectionnez l'élément après lequel ce nouvel élément doit apparaître.
- Sélectionnez **Enregistrer & Fermer**.

### Étape 5 : Ajouter une Catégorie

- Sélectionnez **Contenu **→** Catégories** dans le menu de l'Administrateur.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
- Entrez un titre approprié, par exemple : Categoría (es-es)
- Sélectionnez la langue correcte : espagnol (es-ES)
- Sélectionnez l'onglet **Associations**.
- Pour chaque langue, sélectionnez une catégorie. Il n'y a qu'un seul choix dans chaque cas.
- Sélectionnez **Enregistrer & Fermer**.

### Étape 6 : Ajouter un Élément de Menu

- Sélectionnez **Menus **→** Menu Principal (es-ES)**, le menu nouvellement créé.
- Sélectionnez le bouton **Nouveau** dans la barre d'outils.
- Entrez un titre approprié, par exemple : Página de inicio
- Utilisez le bouton Sélectionner à la fin du champ **Type d'Élément de Menu** pour sélectionner un type d'élément.
- Dans la liste déroulante, sélectionnez **Articles **→** Blog de Catégorie**.
- Dans le champ Choisir une Catégorie, utilisez le bouton Sélectionner.
- Dans la liste pop-up des Catégories, sélectionnez la catégorie Categoría (es-es).
- Réglez le champ **Page par Défaut** sur **Oui**.
- Dans la liste déroulante **Langue**, sélectionnez **Espagnol (es-ES)**.
- **Enregistrer & Fermer**

### Étape 7 : Ajouter un Article

La manière simple d'ajouter un article pour la nouvelle langue est de copier un article existant.

- Sélectionnez **Contenu **→** Articles** dans le menu de l'Administrateur.
- Sélectionnez l'article à copier, dans cet exemple **Article (en-GB)**.
- Dans le formulaire **Articles : Modifier**, changez le titre en **Article (es-ES)**.
- Changez la **Catégorie** en **Categoria (es-es) (es-ES)**.
- Changez la **Langue** en espagnol (es-ES).
- Sélectionnez **Enregistrer comme Copie** dans la liste déroulante **Enregistrer & Fermer** de la barre d'outils. **Attention !**
- Sélectionnez l'onglet **Associations**.
- Pour chaque langue, sélectionnez un article à associer - l'article équivalent dans chaque langue.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

## Ajouter un Article Multilingue

Supposons que vous souhaitiez créer un article dans chacune de vos langues sélectionnées.

- Sélectionnez **Contenu **→** Articles **→** +** depuis le menu Administrateur ou le bouton **Nouveau** dans la barre d'outils de la liste des articles.
- Entrez un titre pour l'article, par exemple **William Shakespeare**.
- Réglez le champ **Catégorie** sur **Catégorie (en-gb) (en-GB)**.
- Réglez le champ **Langue** sur **Anglais (en-GB)**.
- Entrez le **Texte de l'Article**, par exemple à partir de Wikipédia :

« William Shakespeare (bapt. 26 avril 1564 – 23 avril 1616) était un dramaturge, poète et acteur anglais. Il est largement considéré comme le plus grand écrivain de la langue anglaise et le plus grand dramaturge du monde. Il est souvent appelé le poète national de l'Angleterre et le "Barde d'Avon" (ou simplement "le Barde"). Ses œuvres existantes, y compris des collaborations, se composent d'environ 39 pièces, 154 sonnets, trois longs poèmes narratifs et quelques autres vers, dont certains d'auteur incertain. Ses pièces ont été traduites dans toutes les grandes langues vivantes et sont jouées plus souvent que celles de tout autre dramaturge. Il reste sans doute l'écrivain le plus influent de la langue anglaise, et ses œuvres continuent d'être étudiées et réinterprétées. »

- Sélectionnez **Enregistrer** dans la barre d'outils.
- Sélectionnez l'onglet **Associations**.
- Pour chaque langue :
  - Sélectionnez le bouton **Créer**.
  - Dans le formulaire contextuel **Nouvel Article**, entrez un titre traduit, **William Shakespeare**.
  - Réglez la Catégorie sur celle de la langue que vous avez sélectionnée.
  - Entrez le texte traduit dans le champ **Texte de l'Article** (vous pouvez essayer <a href="https://translate.google.com/" rel="nofollow noreferrer noopener">https://translate.google.com/</a>).
  - Sélectionnez **Enregistrer & Fermer**.
- Après qu'un nouvel article pour chaque langue a été créé, sélectionnez **Enregistrer & Fermer**.

## Menu Principal

Si vous avez un lien vers un article pour toutes les langues dans le menu principal et que vous utilisez plus tard cet article comme base pour des articles associés dans d'autres langues, vous devrez modifier le lien du menu principal. Sinon, changer de langue avec cet article sélectionné entraînera une erreur de type Page non trouvée dans la langue sélectionnée.

- Sélectionnez **Menus** → **Menu Principal** dans le menu Administrateur.
- Sélectionnez l'élément de menu que vous devez modifier, par exemple **William Shakespeare**.
- Modifiez le champ **Langue** en **Anglais (en-GB)**.
- Sélectionnez **Enregistrer & Fermer** dans la barre d'outils.

S'il n'y a que cet élément dans le menu principal, ce module disparaîtra lors du changement vers d'autres langues.

*Traduit par openai.com*

