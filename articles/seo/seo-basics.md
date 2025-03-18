<!-- Filename: jdocmanual?manual=user&heading=seo&filename=seo-basics.md / Display title: Notions de base du SEO  -->

## Définition

L'optimisation pour les moteurs de recherche est le processus d'amélioration d'un large éventail de caractéristiques d'un site web dans le but d'améliorer le positionnement dans lequel il est classé dans les moteurs de recherche.

Le processus d'optimisation d'un site web est multifacette, car de nombreux facteurs affectent la position qu'une page pourrait occuper dans un moteur de recherche.

- S'assurer que le contenu a une structure appropriée en utilisant le HTML sémantique
- Améliorer la qualité du contenu des pages individuelles
- S'assurer que le site web peut traiter les demandes rapidement
- Activer des URL adaptées aux moteurs de recherche pour rendre l'adresse web des pages 'compréhensible par l'homme'
- Ajouter un balisage sémantique contextuel en utilisant les données de Schema

Ressource : Guide de démarrage pour l'optimisation pour les moteurs de recherche (SEO)

## Structure du site et URLs descriptives

Au début, les sites web étaient structurés comme des fichiers HTML individuels dans une hiérarchie en arbre. Certains sites sont encore structurés de cette manière. Les CMS sont différents. Les pages individuelles sont assemblées à partir de contenu stocké dans des tables de base de données. Les URLs pour les premiers et les seconds sont différentes, peut-être comme ceci :
```
https://www.example.com/user/seo/seo-basics.html
https://www.example.com/index.php?option=com_jdocmanual&view=manual&manual=user&heading=seo&filename=seo-basics
```
Il est évident que la première est plus facile à retenir et à taper. Les moteurs de recherche les préfèrent.

Dans le CMS Joomla, une URL de la première forme peut être configurée comme suit :

1. Créez une catégorie de contenu nommée **User**.
2. Créez une catégorie de contenu nommée **SEO** qui est un enfant de *User*.
3. Créez un article et assignez-le à la catégorie *SEO*.
4. Créez un élément de menu **User** de type **Liste de catégories** en utilisant la catégorie *User*.
5. Créez un élément de menu **SEO** de type **Liste de catégories** en utilisant la catégorie *SEO*.
6. Configurez la fonctionnalité SEO de Joomla dans *Configuration Globale*.

Testez-le avec votre URL SEO : naviguez via les listes User et SEO jusqu'à la page SEO Basics. Les Breadcrumbs devraient afficher : `Vous êtes ici : Accueil / User / SEO / SEO Basics`. Mais pas si vous avez créé un type d'élément de menu d'article unique pour *SEO Basics* !

## Réduire la Duplication

Le problème avec les CMS est que le même contenu peut être accessible avec des URLs différentes. Dans l'exemple ci-dessus, les deux URLs fonctionneront (mais pas sur ce site), tout comme `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Une seule de ces URLs devrait être reconnue par les moteurs de recherche et définie comme l'URL **canonique**. Mais laquelle et comment ?

Le plugin **System - SEF** propose une aide à ce sujet. Il a trois paramètres :

* **Domaine du site :** Si votre site est accessible via plusieurs domaines, entrez ici le domaine préféré (parfois appelé canonique). **Remarque :** `https://example.com` et `https://www.example.com` sont des domaines différents.
* **Gestion stricte de index.php :** Cette option permet une gestion plus stricte de 'index.php' dans les URLs lorsque 'Utiliser la réécriture d'URL' est activé dans la Configuration Globale. Elle supprimera 'index.php' si une URL le contient encore et redirigera les requêtes entrantes avec 'index.php' vers la version sans 'index.php'.
* **Barre oblique finale pour les URLs :** Forcer Joomla à n'utiliser que des URLs avec ou sans barre oblique finale. Lorsqu'elle est activée, cela forcera l'URL correcte avec des redirections et ne s'applique que lorsque 'Ajouter un suffixe à l'URL' est désactivé.

Explication des **Tags Canoniques** par Daniel Morell :

* Comment créer des Tags Canoniques Joomla
* Plugin et Documentation :

Pour Joomla 4 et 5, avant d'activer, le plugin nécessite que `if ($app->isAdmin()) {` soit changé en `if ($app->isClient('admin')) {` aux lignes 72 et 99 de *plugins /system / customcanonical / customcanonical.php*.

Dans un article, sélectionnez l'onglet Publication puis le bouton **Auto** de l'*URL Canonique*. Cela placera un lien comme suit sur n'importe quelle page affichant l'article unique :
```
    <link href="/jdm3/en/user/seo/seo-basics.html" rel="canonical" />
```

## Qualité du Contenu

Faites en sorte que ce que vous écrivez soit intéressant et facile à lire. Les paragraphes longs sont souvent accablants et difficiles à lire. Les paragraphes d'une seule ligne paraissent incorrects ! Peut-être devraient-ils vraiment être des points à puce. Visez des paragraphes d'environ trois lignes. Relisez ce que vous écrivez et supprimez les mots inutiles.

Gardez votre contenu à jour et évitez de copier des informations provenant d'autres sites. Si possible, vérifiez votre contenu.

### HTML Sémantique

Le contenu doit être constitué d'une hiérarchie de titres et de paragraphes avec d'autres éléments selon les besoins (listes, tableaux, etc.). Ne confondez pas structure et apparence - n'utilisez donc pas un titre pour mettre en gras ou le gras pour un titre. Voici un exemple de balisage sémantique d'un article :

```html
  <h2>Utilisation des titres</h2>
  <p>Ceci est un article sur l'importance des titres.</p>

  <h2>Pourquoi utiliser des titres ?</h2>
  <p>Il est important d'utiliser des titres pour que les robots des moteurs de recherche puissent identifier ce qui est une
  partie <strong>importante</strong> de votre article.</p>

  <h3>Types de titres</h3>
  <p>Vous pouvez utiliser des types de titres prédéfinis, mais ils doivent être ordonnés et structurés dans votre page. H1 sera le titre de la page inséré par Joomla, avec H2 utilisé pour les sous-titres de la page. Tous les titres dans vos sous-titres doivent être en cascade en utilisant H3, H4, et H5 selon le besoin.</p>

  <h2>Est-il difficile de mettre en œuvre des titres ?</h2>
  <p>Il est très facile de mettre en œuvre des titres, il vous suffit d'utiliser le code HTML approprié.</p>
```
Notez que le *Titre* d'un article deviendra un titre `<h1>` si nécessaire, alors ne l'utilisez pas dans le corps de l'article.

## Anticiper les termes de recherche

Choisissez des titres explicites pour vos pages et les en-têtes au sein des pages. Par exemple, si vous ne savez pas ce qu'est le *HTML sémantique* ou si vous souhaitez obtenir plus d'informations sur ce sujet, ce sont ces mots que vous saisiriez dans un moteur de recherche. Pensez aux personnes qui pourraient être intéressées par les informations que vous fournissez. Que vont-elles rechercher ? Mais gardez les titres et les en-têtes assez courts – certaines sources préconisent de ne pas dépasser 60 caractères.

## Attention aux publicités

Rien ne dissuadera plus les visiteurs d'un site que des publicités apparaissant ici, là et partout, déplaçant ainsi les véritables informations sous vos yeux. Les publicités qui changent toutes les quelques secondes sont également agaçantes et consomment les ressources des utilisateurs finaux. Beaucoup utiliseront des bloqueurs de publicité!

## Prudence avec les liens

Les liens sont à la fois une bénédiction et une malédiction ! Ils peuvent influencer le classement SEO de votre site en bien ou en mal selon que vous ayez des liens vers des sources réputées ou non. Et ils doivent être maintenus. Vous pouvez avoir des liens vers des articles internes ou externes qui ont disparu, proposent des informations obsolètes ou ne sont plus pertinents. Meilleur conseil : créez un lien si la cible apporte un véritable avantage à vos visiteurs et utilisez l'attribut de lien `nofollow` si vous ne souhaitez pas que le site cible soit associé à votre site.

Il existe de nombreux outils de vérification de liens disponibles, certains gratuits ou en version freemium et d'autres payants, souvent dans le cadre d'un service de surveillance de site.

## Titre de la Page et Description

Dans la balise `<head>` de chaque page, il devrait y avoir une balise `<title>` et une balise `<description>`. Joomla facilite la tâche de définir un titre différent pour chaque page. Malheureusement, il est aussi très facile de négliger de définir un Titre et une Description appropriés sur chaque page.

À titre d'exemple, prenons la page de liste de catégorie **SEO** mentionnée ci-dessus. La balise `<title>` de la source de la page indique **SEO** et la balise `<description>` est absente. Dans le formulaire **Menus : Éditer l'Élément** pour cet élément de menu, il y a un onglet **Affichage de la Page** avec un champ **Titre de la Page du Navigateur**. Insérez `SEO - Liste d'Articles` ici et c'est ce qui apparaît dans la balise `<title>` et dans l'onglet du navigateur.

Dans l'onglet **Métadonnées**, avec le champ **Description Méta** configuré sur `Liste d'articles sur l'Optimisation pour les Moteurs de Recherche.`, c'est exactement ce qui apparaît dans le champ `<description>`. La Description est parfois utilisée pour accompagner un Titre de page dans les résultats de recherche, il convient donc de la rendre pertinente.

Plus d'informations :
* Article de magazine : Balises de titre SEO Joomla
* Explorer le Cœur : Options SEO Natives

## Optimiser les images

Inutile de dire que des images attrayantes peuvent énormément améliorer un site. Mais trop d'images qui sont trop grandes attirent des pénalités SEO. Voici quelques conseils :

* Placez les images à côté du texte qu'elles illustrent.
* Utilisez un texte **alt** descriptif.
* Utilisez des mots séparés par des tirets pour les noms des images, par exemple cat-on-hot-tin-roof.jpg.
* Utilisez le bon type d'image pour la tâche : png pour les affiches, jpg pour les photographies.
* Utilisez des images réactives - il existe un plugin Joomla qui crée dynamiquement des versions webp des images png et jpg en plusieurs tailles.

*Traduit par openai.com*
