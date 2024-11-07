<!-- Filename: Using_A_Sitemap / Display title: Utilisation d'un plan du site  -->

## Utiliser un Sitemap

Bien que les moteurs de recherche puissent généralement trouver vos pages grâce à la manière dont elles sont reliées à d'autres endroits sur Internet, il est judicieux de créer un Sitemap qui donne aux robots des moteurs de recherche une liste des pages de votre site Web - pensez-y comme une carte pour trouver tout le contenu de votre site. Les Sitemaps ne sont pas seulement importants pour les moteurs de recherche, ils sont également très utiles pour les personnes handicapées qui peuvent avoir besoin d'une interface simple pour visualiser la structure de votre site et naviguer sur le site sans utiliser vos structures de menu. <a href="https://www.w3.org/TR/WCAG20-TECHS/G63.html" rel="nofollow noreferrer noopener">Note du W3C Working Group sur les Sitemaps</a>

Un sitemap remplit plusieurs fonctions :

- Fournit une liste structurée donnant un aperçu de tout le contenu de votre site Web
- Permet à un visiteur d'obtenir rapidement un aperçu de la structure de votre site
- Offre un moyen alternatif de naviguer sur votre site Web, sans avoir besoin de structures de menu complexes
- Fournit aux moteurs de recherche un moyen de trouver le contenu qui pourrait ne pas être disponible via vos structures de menu (par exemple, des pages d'atterrissage)

### Types de Sitemap

Il est possible de fournir des sitemaps pour des types d'informations spécifiques, notamment :

- Vidéo <a href="https://support.google.com/webmasters/answer/80471" rel="nofollow noreferrer noopener">Aide Google sur les sitemaps vidéo</a>
- Images <a href="https://support.google.com/webmasters/answer/answer.py?answer=178636" rel="nofollow noreferrer noopener">Aide Google sur les sitemaps d'images</a>
- Actualités <a href="https://support.google.com/news/publisher/answer/75717" rel="nofollow noreferrer noopener">Aide Google sur les sitemaps d'actualités</a>
- International <a href="https://support.google.com/webmasters/answer/2620865?hl=fr&amp;ref_topic=2370587" rel="nofollow noreferrer noopener">Aide Google sur les sitemaps internationaux</a>

Ces sitemaps spécialisés vous permettent de fournir des informations relatives au type de média spécifique - par exemple, avec un sitemap vidéo, vous pouvez fournir des informations sur la durée, la catégorie et le statut familial; avec des sitemaps d'images, vous pouvez spécifier le sujet de l'image, sa licence d'utilisation et le type d'image.

### Créer un sitemap

Sur un site statique, créer un sitemap consiste simplement à créer manuellement un fichier XML en utilisant les normes appropriées et à le sauvegarder en tant que fichier XML. Sur un site dynamique, où le contenu change régulièrement, cela n'est pas vraiment une option - vous devriez mettre à jour manuellement le fichier sitemap chaque fois que vous ajoutez un nouveau contenu!

Pour cette raison, il existe plusieurs extensions de sitemap disponibles sur l'annuaire des extensions Joomla (<a href="https://extensions.joomla.org/category/structure-a-navigation/site-map" rel="noreferrer noopener">Catégorie Sitemap sur l'annuaire des extensions Joomla</a>) qui vous permettent de créer dynamiquement un sitemap conforme aux normes de sitemap attendues par les moteurs de recherche.
<a href="https://www.sitemaps.org/" rel="nofollow noreferrer noopener">Protocole Sitemaps</a>

La plupart de ces extensions fonctionnent en choisissant les éléments de menu que vous souhaitez inclure dans un sitemap et en spécifiant la fréquence à laquelle ils changent (voir Fréquence de mise à jour). Il est également possible d'inclure des sous-pages de ces éléments de menu (par exemple, un élément de menu pourrait mener à une page de blog de catégorie, mais vous souhaitez afficher tous les articles qui sont affichés sur cette page en tant qu'éléments individuels - un autre exemple pourrait être un élément de menu pointant sur une page de catégorie de boutique, et dans le sitemap vous voudriez lister la catégorie, puis chaque produit à l'intérieur comme un lien séparé).

### Fréquence de mise à jour

Bien que vous puissiez spécifier manuellement dans votre Sitemap la fréquence à laquelle les robots des moteurs de recherche doivent visiter votre site Web, les moteurs de recherche ont généralement des systèmes intégrés qui ajustent automatiquement la fréquence des visites de retour en fonction de la fréquence à laquelle la page en question a changé.

Ainsi, par exemple, si vous indiquez aux robots des moteurs de recherche de visiter votre page quotidiennement, mais que lorsque la page est visitée, rien n'a changé depuis une semaine, ils peuvent ajuster la fréquence des visites en conséquence et ne pas revenir aussi souvent que vous leur avez dit. Vous pouvez demander, via les divers portails de webmasters, d'ajuster le taux de revisite si nécessaire.

Cela suggérerait donc que si vous avez du contenu changeant régulièrement, votre site Web sera visité plus fréquemment - ce qui entraînera un indexage plus rapide du contenu par rapport aux sites Web qui ne changent pas souvent.

Il est généralement conseillé de spécifier les pages qui sont statiques pour être explorées moins souvent que celles qui changent régulièrement. Par exemple, un article textuel statique pourrait être configuré avec une fréquence de mise à jour d'une fois par mois, tandis que votre page de blog ou d'actualités pourrait être configurée avec une fréquence de mise à jour d'une fois par jour ou une fois par semaine, en fonction de la fréquence à laquelle vous ajoutez du nouveau contenu.

### Sitemaps HTML

Un sitemap HTML est essentiellement une table des matières pour votre site que vous pouvez mettre à la disposition des visiteurs de votre site Web. Cela a deux objectifs :

1. Il offre un endroit où les visiteurs peuvent facilement accéder à n'importe quel contenu de votre site, même s'il n'est pas nécessairement facile d'accès par d'autres aides à la navigation sur le site
2. Il fournit un stock centralisé de liens vers le contenu de votre site qui peut être facilement indexé par les moteurs de recherche
3. Il permet aux utilisateurs ayant des handicaps de naviguer rapidement sur votre site Web avec une liste simple de liens, plutôt qu'à travers des menus complexes

Au minimum, un sitemap devrait lier les sections et pages principales de votre site, mais plus il est détaillé, mieux c'est.

Il existe des extensions disponibles précédemment mentionnées qui créent automatiquement des sitemaps basés sur le contenu Joomla.

### Sitemaps XML

Les sitemaps XML sont un moyen facile pour les webmasters d'informer les moteurs de recherche des nouvelles et anciennes pages de leurs sites qui sont disponibles pour l'exploration. Sous sa forme la plus simple, un Sitemap est un fichier XML qui répertorie les URL d'un site accompagné de métadonnées supplémentaires sur chaque URL (quand elle a été mise à jour pour la dernière fois, à quelle fréquence elle change généralement et son importance relative par rapport aux autres URL du site) pour que les moteurs de recherche puissent explorer le site plus intelligemment.

L'utilisation du protocole Sitemap ne garantit pas que les pages Web sont incluses dans les moteurs de recherche, mais fournit des indices aux robots d'exploration pour mieux explorer votre site.

1. Un sitemap XML fournit une liste de liens vers le contenu de votre site qui peut être facilement indexé par les moteurs de recherche
2. Il est possible de créer des sitemaps XML spécifiques pour les actualités, les URL mobiles, les images et les vidéos

Il existe des extensions disponibles qui créent automatiquement des sitemaps XML basés sur le contenu Joomla.

*Traduit par openai.com*

