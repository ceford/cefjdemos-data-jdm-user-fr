<!-- Filename: jdocmanual?manual=user&heading=performance&filename=page-analysis.md / Display title: Analyse de la Page -->

## Phare

> Phare est un outil automatisé et open-source destiné à améliorer la qualité des pages web. Vous pouvez l'exécuter sur n'importe quelle page web, publique ou nécessitant une authentification. Il propose des audits pour la performance, l'accessibilité, les applications web progressives, le SEO, et bien plus encore.

Il est disponible en tant qu'outil complémentaire pour Google Chrome et Firefox et peut être exécuté à partir de la ligne de commande. Cela est utile pour tester dans un environnement de développement local.

Plus d'informations sur le site Chrome pour les développeurs : Phare.

Vous pouvez utiliser l'outil en ligne depuis [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/).

La capture d'écran suivante montre la première partie du rapport PageSpeed Insights :

![Rapport PageSpeed Insights](../../../en/images/performance/performance-pagespeed-insights.png "Rapport PageSpeed Insights")

## Améliorations des performances

La deuxième partie du rapport suggère des méthodes pour améliorer les performances :

* **Éliminer les ressources qui bloquent le rendu** - Économies potentielles de 540 ms. Franchement, c'est trop de travail pour trop peu de récompense.
* **Activer la compression du texte** Économies potentielles de 11 KiB. Dans la Configuration Globale, panneau Serveur, réglez la Compression des Pages GZip sur *Oui*. Cela laisse de petits fichiers JavaScript et CSS à minifier et compresser.
* **Réduire le CSS inutilisé** Économies potentielles de 62 KiB. Les coupables sont template.min.css et joomla-fontawesome.min.css, mais cela implique de personnaliser le CSS pour chaque page du site, ce qui est trop sujet à erreur pour trop peu de récompense.
* **Servir les ressources statiques avec une politique de cache efficace** - 21 ressources trouvées. Références fournies, y compris des références spécifiques à Joomla.

Le message global est que certaines suggestions valent la peine d'être corrigées et d'autres non.

## Rapport Mobile vs Bureau

Le rapport Bureau diffère généralement du rapport Mobile. Quelques problèmes supplémentaires identifiés dans ce cas :

* **Tailler correctement les images** - Économies potentielles de 48 KiB. La balise d'image est en fait optimisée avec des images webp de 768 et 1200 pixels de large. Il semble qu'une taille intermédiaire soit nécessaire.

## Accessibilité

* **Les liens n'ont pas de nom discernable** Cela fait référence aux flèches de gauche et de droite en bas de la page qui permettent de naviguer vers l'avant ou l'arrière. Le texte a été omis pour éviter les problèmes de traduction. Il faut y repenser !
* **Les cibles tactiles n'ont pas une taille ou un espacement suffisant** Cela fait référence à la taille des éléments du menu dans les colonnes de gauche et de droite. Ils ont besoin de plus d'espace vertical - un ajustement CSS est nécessaire.

## Meilleures pratiques et SEO

Bien qu'ils aient tous les deux obtenu un score de 100 pour Mobile et Desktop, ils doivent être vérifiés à nouveau après chaque changement de conception.

## Résumé

Tous les problèmes sur ce site ont été résolus sauf le démantèlement des fichiers CSS et la minification des petits fichiers de composants Javascript et CSS.
*Traduit par openai.com*

