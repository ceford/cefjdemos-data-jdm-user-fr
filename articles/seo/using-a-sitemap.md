<!-- Filename: Using_A_Sitemap / Display title: Utiliser un plan de site -->

## Utiliser un plan de site

Alors que les moteurs de recherche peuvent généralement trouver vos
pages par la façon dont elles sont liées à partir d'autres endroits sur
Internet, il est de bonne pratique de créer un plan de site qui donne
aux moteurs de recherche une liste des pages de votre site Web - voyez
cela comme une carte pour trouver tout le contenu sur votre site.  
Les plans du site ne sont pas seulement importants pour les moteurs de
recherche, ils sont aussi très utiles pour les personnes handicapées qui
peuvent avoir besoin d'une interface simple pour visualiser la structure
de votre site et naviguer sur le site sans utiliser vos structures de
menu. <a href="https://www.w3.org/TR/WCAG20-TECHS/G63.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">W3C Working Group Note on
Sitemaps</a>  

Un plan de site a plusieurs objectifs :

- Fournit une liste structurée montrant une vue d'ensemble de tout le
  contenu de votre site Web.
- Permet à un visiteur d'obtenir rapidement une vue d'ensemble de la
  structure de votre site.
- Fournit une autre façon de naviguer sur votre site Web, sans avoir
  besoin de structures de menu complexes.
- Fournit aux moteurs de recherche un moyen de trouver du contenu qui
  pourrait ne pas être disponible à travers vos structures de menu (par
  exemple, les pages de destination).

### Types de plan de site

Il est possible de fournir des plans de site pour des types
d'informations spécifiques, notamment :

- Vidéo <a href="https://support.google.com/webmasters/answer/80471"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Aide Google sur les plans de site
  vidéo</a>
- Images <a
  href="https://support.google.com/webmasters/answer/answer.py?answer=178636"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Aide Google sur les plans de site
  image</a>
- Actualités
  <a href="https://support.google.com/news/publisher/answer/75717"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Aide Google sur les plans de site
  d'actualités</a>
- International <a
  href="https://support.google.com/webmasters/answer/2620865?hl=en&amp;ref_topic=2370587"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Aide Google sur les plans de site
  internationaux</a>

Ces plans de site spécialisés vous permettent de fournir des
informations relatives au type de média spécifique - par exemple, avec
un plan de site vidéo, vous pouvez fournir des informations sur le temps
d'exécution, la catégorie et le statut ; avec les plans de site image,
vous pouvez spécifier le sujet de l'image, sa licence d'utilisation et
le type d'image.

### Créer un plan de site

Sur un site statique, la création d'un plan de site est la création
manuelle d'un fichier XML en utilisant les normes appropriées, et
l'enregistrement sous forme de fichier XML. Sur un site dynamique, où le
contenu change régulièrement, ce n'est pas vraiment une option - vous
auriez à mettre à jour manuellement le fichier sitemap chaque fois que
vous avez ajouté du nouveau contenu !

For this reason there are several sitemap extensions available on the
Joomla Extensions Directory (<a
href="https://extensions.joomla.org/category/structure-a-navigation/site-map"
class="external text" target="_blank" rel="noreferrer noopener">Sitemap
category on Joomla Extensions Directory</a>) which allow you to
dynamically build a sitemap which meets the sitemap standards expected
by search engines.
<a href="https://www.sitemaps.org/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">Sitemaps protocol</a>

Most of these extensions work by choosing menu items which you wish to
include in a sitemap, and specifying how often they change (see Update
Frequency). It is also possible to include sub-pages from those menu
items (for example, a menu item might lead to a category blog page, but
you want to display all the articles which are shown on this page as
individual items - another example might be a menu item pointing at a
shop category page, and in the sitemap you would want to list the
category, and then each product within it as a separate link).

### Fréquence de mise à jour

While you can manually specify in your Sitemap how frequently search
engine spiders should visit your website, most search engines have
in-built systems which automatically adjust the frequency of return
visits based on how often the page in question has changed.

So, for example, if you tell search engine bots to visit your page on a
daily basis, but when it visits the page nothing has changed for a week,
it may adjust the frequency of revisits accordingly and not return as
often as you told it to. You can request, via the various webmasters
portals, for the revisit rate to be amended if required.

This would suggest, therefore, that if you have regularly changing
content, your website will be 'spidered' more frequently - leading to
content being indexed quicker than websites which do not change often.

It is generally sensible to specify pages which are static to be crawled
less frequently than those which change regularly. For example, a static
text article might be set with an update frequency of once a month,
whereas your blog or news page may be set with an update frequency of
once a day or once a week, depending on how often you add new content.

### Plans de site HTML

An HTML sitemap is essentially a table of contents for your site which
you can make available to visitors of your website. This serves two
purposes:

1.  It provides a place where visitors can go to easily get to any
    content on your site, even if it isn't necessarily easy to access by
    other navigation aids on the site
2.  It provides a centralised store of links to the content on your site
    that can be easily indexed by search engines
3.  It allows users with disabilities to be able to quickly navigate
    your website with a simple list of links, rather than through
    complex menus

At the very least, a sitemap should link to the main sections and pages
within your site, but the more detailed you can make it, the better.

There are available extensions previously mentioned that create sitemaps
automatically based on Joomla content.

### Plans de site XML

XML Sitemaps are an easy way for webmasters to inform search engines
about new and existing pages on their sites that are available for
crawling. In its simplest form, a Sitemap is an XML file that lists URLs
for a site along with additional metadata about each URL (when it was
last updated, how often it usually changes, and how important it is,
relative to other URLs in the site) so that search engines can more
intelligently crawl the site.

Using the Sitemap protocol does not guarantee that web pages are
included in search engines, but provides hints for web crawlers to do a
better job of crawling your site.

1.  Un plan du site XML fournit une liste de liens vers le contenu de
    votre site qui peuvent être facilement indexés par les moteurs de
    recherche.
2.  Il est possible de créer des plans de site XML spécifiques pour des
    sites d'actualités, les URL mobiles, les images et la vidéo.

Il existe des extensions disponibles qui créent automatiquement des
plans de site XML basés sur le contenu Joomla.
