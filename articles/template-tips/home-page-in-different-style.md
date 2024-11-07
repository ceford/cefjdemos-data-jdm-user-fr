<!-- Filename: J4.x:Home_Page_in_Different_Style / Display title: Page d'accueil dans un style différent -->

## Page d'accueil du site

Une page d'accueil du site peut être sélectionnée à partir de n'importe quel type d'élément de menu en choisissant une icône grise dans la colonne Accueil de n'importe quelle liste d'éléments de menu. Essayez de faire un changement ! Consultez le changement sur votre site dans un onglet ou une fenêtre de navigateur séparé. Vous pouvez facilement revenir en arrière. Si vous souhaitez une page d'accueil distinctive, vous pourriez choisir un type d'élément de menu Article unique, un type d'élément de menu Blog de catégorie, un type d'élément de menu Articles en vedette, ou autre chose.

Supposons que vous souhaitiez donner à votre page d'accueil une apparence distincte, un peu différente de toutes les autres pages de votre site. Il existe de nombreuses méthodes disponibles pour personnaliser l'apparence d'une page d'accueil :

- Via des modules assignés uniquement à la page d'accueil.
- Via des styles personnalisés.
- Via une substitution ou une mise en page de modèle.
- Via un modèle séparé ou un modèle enfant utilisé uniquement pour l'élément de menu de la page d'accueil.
- Plus…?

## Exemple : Données d'exemple de Cassiopeia

Les données d'exemple de Cassiopeia créent une page d'accueil en utilisant un type de menu **Articles en vedette**. Elle est présentée comme sur la capture d'écran ci-dessous (quelques modifications mineures ont été apportées à certains articles pour obtenir une meilleure capture d'écran ici).

![page d'accueil utilisant cassiopeia et les données d'exemple](../../../en/images/templates/templates-home-page-style-cassiopeia-sample-data.png)

Voici comment la mise en page est réalisée :

### Module Image

La grande image sous la barre de menu se trouve dans un module personnalisé nommé Image affecté à la position du bandeau dans le modèle Cassiopeia.

![module personnalisé utilisé dans le style des données d'exemple](../../../en/images/templates/templates-home-page-style-custom-module-image.png)

Dans l'onglet Affectation du menu, le module est affecté uniquement à l'accueil :

![onglet d'affectation du menu du module personnalisé](../../../en/images/templates/templates-home-page-style-custom-module-menu-assignment.png)

L'image de fond est sélectionnée dans l'onglet Options du formulaire de modification Modules : Personnalisé.

Dans l'onglet Avancé / Champ Mise en page, l'élément `banner` est sélectionné. La mise en page du bandeau est une mise en page de modèle :

### Mise en page de modèle

La mise en page de module par défaut dans `siteroot/modules/mod_custom/tmpl/default.php` n'affiche pas le module comme souhaité. Il existe une mise en page alternative dans `siteroot/templates/cassiopeia/html/mod_custom/banner.php`. Comme `banner.php` n'est pas présent dans le code du module personnalisé, il fonctionne comme une mise en page que vous pouvez sélectionner plutôt qu'une substitution qui est toujours utilisée. Dans le module Image, vous pouvez sélectionner la mise en page par défaut, enregistrer et recharger le site pour voir la différence. Revenez à la mise en page du bandeau et enregistrez à nouveau pour restaurer le comportement normal.

Il existe des articles séparés sur les substitutions et les mises en page.

### Module Newsflash

Sous la grande image se trouvent trois petits boîtiers chacun avec une image et du texte en dessous. Ils sont créés à l'aide d'un module Articles - Newsflash dans la position haut-a du modèle. Le module est configuré pour afficher 3 articles. Son affectation de menu est uniquement pour l'accueil. L'onglet Avancé a la mise en page réglée sur horizontal et le style du module réglé sur noCard.

![module newsflash](../../../en/images/templates/templates-home-page-style-newsflash-module-image.png)

Ceci conclut l'explication de la création de la page d'accueil avec les données d'exemple de Cassiopeia.

## Plus d'options

Vous pourriez souhaiter faire plus. Un schéma de couleurs différent pour la page d'accueil, ou un filigrane, ou une mise en page personnalisée. Voici quelques idées :

### Affichage de la page

Dans la forme des menus : Modifier l'élément pour le menu d'accueil, sélectionnez l'onglet Affichage de la page. Le champ Classe de la page est généralement vide. Tout ce qui y est entré devient une classe supplémentaire dans l'élément de la page. Par exemple, entrer `fancyhome` résulte en ce qui suit dans la sortie de la page d'accueil pour cette unique page :
```html
<body class="site com_content wrapper-static view-featured no-layout no-task itemid-101 fancyhome has-sidebar-right">
```
Vous pouvez ensuite créer un fichier user.css via **Système**→**Modèles de site**→**Détails et fichiers de Cassiopeia**. Sélectionnez le bouton `Nouveau fichier` et créez user.css dans le dossier css. Ensuite, entrez des styles dans le formulaire d'édition de user.css. Exemple :
```css
    .fancyhome {
      background-color: #f8fff8;
    }
```
Cela dotera la page d'accueil d'un fond vert pâle. Utilisez \#f8f8ff pour un fond bleu pâle ou \#ffffee pour un jaune pâle. Vous pouvez faire tout un tas d'autres choses avec votre style fancyhome, mais vous devez avoir une bonne connaissance pratique du css.

### Modèles de page d'accueil alternatifs

Vous pouvez installer des modèles de site alternatifs, obtenus auprès de fournisseurs de modèles tiers. Et vous pouvez créer des modèles enfants qui se comportent de manière similaire. Dans les deux cas, vous pouvez choisir quel modèle doit être le défaut pour toutes les pages et lequel doit être utilisé uniquement pour la page d'accueil.

- Sélectionnez **Système → Styles de modèles de site** dans le menu Administrateur.
- Sélectionnez le modèle que vous souhaitez utiliser pour la page d'accueil. Il doit être l'un de ceux non sélectionnés comme modèle par défaut.
- Dans l'onglet Assignation du menu, sélectionnez uniquement l'élément de menu Accueil. Tout ce qui n'est pas sélectionné ici utilisera toujours votre modèle par défaut.
- Vous pourriez sélectionner certaines options dans l'onglet Avancé, mais elles varient selon chaque modèle et ne sont pas couvertes ici.

Il existe d'autres articles sur la personnalisation de Cassiopeia.

*Traduit par openai.com*

