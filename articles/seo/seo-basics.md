<!-- Filename: jdocmanual?manual=user&heading=seo&filename=seo-basics.md / Display title: Principes de base du SEO -->

## Définition

L'optimisation pour les moteurs de recherche est le processus d'amélioration d'un large éventail de caractéristiques d'un site web dans le but d'améliorer la position à laquelle il est classé dans les moteurs de recherche.

Le processus d'optimisation d'un site web est à multiples facettes car de nombreux facteurs influencent le classement d'une page dans un moteur de recherche.

- S'assurer que le contenu a une structure appropriée en utilisant du HTML sémantique
- Améliorer la qualité du contenu des pages individuelles.
- S'assurer que le site web peut traiter les requêtes rapidement.
- Activer les URL conviviales pour les moteurs de recherche afin de rendre l'adresse web des pages *lisible par l'humain*.
- Ajouter un balisage sémantique contextuel en utilisant les données Schema.

Ressource : [Search Engine Optimization (SEO) Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)

## Structure du site et URLs descriptives

Dans les premiers temps, les sites Web étaient structurés sous forme de fichiers HTML individuels dans une hiérarchie arborescente. Certains sites Web sont encore structurés de cette manière. Les CMS sont différents. Les pages individuelles sont assemblées à partir de contenu stocké dans des tables de base de données. Les URL pour les premiers et les seconds sont différents, peut-être comme ceci :

```
https://www.example.com/user/seo/seo-basics.html
https://www.example.com/index.php?option=com_jdocmanual&view=manual&manual=user&heading=seo&filename=seo-basics
```

Il est évident que le premier est plus facile à mémoriser et à taper. Les moteurs de recherche les préfèrent.

Dans le CMS Joomla, une URL de la première forme peut être configurée comme suit :

1. Créez une Catégorie de Contenu nommée **Utilisateur**.
2. Créez une Catégorie de Contenu nommée **SEO** qui est une sous-catégorie de *Utilisateur*.
3. Créez un article et assignez-le à la catégorie *SEO*.
4. Créez un élément de menu **Utilisateur** de type **Liste de Catégorie** en utilisant la catégorie *Utilisateur*.
5. Créez un élément de menu **SEO** de type **Liste de Catégorie** en utilisant la catégorie *SEO*.
6. Configurez la fonctionnalité SEO de Joomla dans la *Configuration Globale*.

Testez-le avec votre URL SEO : naviguez via les listes Utilisateur et SEO jusqu'à la page Bases du SEO. Le fil d'Ariane devrait afficher : `Vous êtes ici : Accueil / Utilisateur / SEO / Bases du SEO`. Mais pas si vous avez créé un type d'élément de menu Article Unique pour *Bases du SEO* !

## Réduire la duplication

Le problème avec les CMS est que le même contenu peut être disponible à des adresses URL différentes. Dans l'exemple ci-dessus, les deux URL fonctionneront (mais pas sur ce site), tout comme `https://example.com/index.php?option=com_content&view=category&id=18&ItemID=17`. Une seule de ces URL doit être reconnue par les moteurs de recherche et définie comme l'URL **canonique**. Mais laquelle et comment ?

Le plugin **System - SEF** fournit une certaine aide. Il comporte trois réglages :

- **Domaine du site** Si votre site peut être consulté via plusieurs domaines, entrez ici le domaine préféré (parfois appelé canonique). **Remarque :** `https://example.com` et `https://www.example.com` sont des domaines différents.
- **Gestion stricte de index.php** Cette option permet une gestion plus stricte de `index.php` dans les URLs lorsque **Utiliser la réécriture d’URL** est activée dans la configuration globale. Elle supprimera `index.php` si une URL le contient encore et redirigera les requêtes entrantes avec `index.php` vers la version sans `index.php`.
- **Barre oblique finale pour les URLs** Forcer Joomla à n'utiliser que des URLs avec ou sans barre oblique finale. Lorsqu'elle est activée, cela forcera l'utilisation de la bonne URL avec redirections et n'est appliqué que lorsque 'Ajouter un suffixe à l’URL' est désactivé.

Sinon, voir l'explication des **balises canoniques** par [Daniel Morell](https://www.danielmorell.com/blog/how-to-create-joomla-canonical-tags).

## Qualité du contenu

Rendez ce que vous écrivez intéressant et facile à lire. Les longs paragraphes sont souvent accablants et difficiles à lire. Les paragraphes d'une seule ligne semblent incorrects ! Peut-être devraient-ils vraiment être des points à puce. Visez des paragraphes d'environ trois lignes. Lisez ce que vous écrivez et éliminez tous les mots inutiles.

Maintenez votre contenu à jour et évitez de copier des informations d'autres sites. Si possible, vérifiez votre contenu.

### HTML sémantique

Le contenu doit être constitué d'une hiérarchie de titres et de paragraphes avec d'autres éléments selon les besoins (listes, tableaux, etc.). Ne confondez pas la structure avec l'apparence - n'utilisez donc pas un titre pour rendre le texte en gras ou du texte en gras pour créer un titre. Voici un exemple de balisage sémantique d'un article :

```html
  <h2>Using headings</h2>
  <p>This is an article about the importance of headings.</p>

  <h2>Why use headings?</h2>
  <p>It is important to use headings so that search engine bots can tell what
  is an <strong>important</strong> part of your article.</p>

  <h3>Types of headings</h3>
  <p>You can use set types of headings, but they should be ordered, and
  structured, within your page.  H1 will be the page title inserted by Joomla,
  with H2 being used for sub-headings of the page.  Any headings within your
  sub-headings should cascade using H3, H4, and H5 as appropriate.</p>

  <h2>Is it hard to implement headings?</h2>
  <p>It is really easy to implement headings, you just use the appropriate
  HTML code.</p>
```

Notez qu'un article *Titre* deviendra un en-tête `<h1>` si nécessaire, donc ne l'utilisez pas dans le corps d'un article.

## Anticiper les termes de recherche

Choisissez des titres explicites pour vos pages et les en-têtes dans les pages. Par exemple, si vous ne savez pas ce qu'est le *HTML Sémantique* ou souhaitez plus d'informations sur ce sujet, ce sont les mots que vous entrez dans un moteur de recherche. Pensez aux personnes qui pourraient être intéressées par les informations que vous fournissez. Que vont-elles rechercher ? Mais gardez les Titres et En-têtes assez courts - certaines sources disent pas plus de 60 caractères.

## Attention aux publicités

Rien ne dissuadera plus les visiteurs du site que des publicités apparaissant ici, là et partout, déplaçant les vraies informations sous vos yeux. Les publicités qui changent toutes les quelques secondes sont également gênantes et consomment les ressources des utilisateurs finaux. Beaucoup utiliseront des bloqueurs de publicités !

## Attention aux liens

Les liens sont à la fois une bénédiction et une malédiction ! Ils peuvent affecter le classement SEO de votre site en bien ou en mal, selon que vous ayez des liens vers des sources de bonne ou de mauvaise réputation. Et ils doivent être entretenus. Vous pouvez avoir des liens vers des articles internes ou externes qui ont disparu, présentent des informations obsolètes ou ne sont plus pertinents. Meilleur conseil : liez si la cible apporte un réel bénéfice à vos visiteurs et utilisez l'attribut de lien `nofollow` si vous ne souhaitez pas que le site cible soit associé à votre site.

Il existe de nombreux outils de vérification de liens disponibles, certains gratuits ou freemium et d'autres payants, souvent dans le cadre d'un service de surveillance de site.

## Titre de la page et description

Dans la `<head>` de chaque page, il devrait y avoir une balise `<title>` et une balise `<description>`. Joomla rend très facile de définir un titre différent pour chaque page. Malheureusement, il est également très facile de négliger de définir un Titre et une Description appropriés sur chaque page.

Par exemple, prenez la page de liste de catégorie **SEO** mentionnée ci-dessus. La source de la page `<title>` indique **SEO** et la `<description>` est manquante. Dans le formulaire **Menus: Modifier l'élément** pour cet élément de menu, il y a un onglet **Affichage de la page** avec un champ **Titre de la page dans le navigateur**. Insérez `SEO - Liste des articles` là-bas et c'est ce qui apparaît dans la balise `<title>` et dans l'onglet du navigateur.

Dans l'onglet **Méta-données**, avec le champ **Méta-description** défini sur `Liste d'articles sur l'optimisation des moteurs de recherche.`, c'est exactement ce qui apparaît dans le champ `<description>`. La description est parfois utilisée pour accompagner un titre de page dans les résultats de recherche, il est donc important de la rendre pertinente.

Plus d'informations :
* Article de magazine : [Joomla SEO title tags](https://magazine.joomla.org/all-issues/september/joomla-seo-title-tags)
* [Explorez le cœur : options SEO natives](https://magazine.joomla.org/all-issues/june/explore-the-core-native-seo-options)

## Optimiser les images

Inutile de dire que des images attrayantes peuvent énormément améliorer un site. Mais trop d'images trop grandes attirent des pénalités SEO. Voici quelques conseils :

- Placez les images à côté du texte qu'elles illustrent.
- Utilisez un texte **alt** descriptif.
- Utilisez des mots séparés par des tirets pour les noms des images, par exemple chat-sur-un-toit-brûlant.jpg.
- Utilisez le bon type d'image pour le travail : png pour les affiches, jpg pour les photographies.
- Utilisez des images réactives - il existe un [plugin Joomla](https://responsive-images.dgrammatiko.dev/) qui crée dynamiquement des versions webp des images png et jpg en plusieurs tailles.

*Traduit par openai.com*

