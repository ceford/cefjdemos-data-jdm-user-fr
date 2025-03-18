<!-- Filename: J5.x:Improving_SEO_with_Strict_Routing_and_SEF_URLs / Display title: SEO Routage Strict -->

## Introduction

L'option de routage strict, introduite dans Joomla 5.2, améliore les performances SEO de la plateforme en permettant des règles de routage plus strictes grâce à un commutateur dans le plugin *System - SEF*. Elle aide à éliminer le contenu en double en appliquant des URL plus cohérentes et en redirigeant les doublons vers l'URL correcte avec une redirection 301.

![system sef plugin settings](../../../en/images/seo/seo-system-sef-plugin.png)

### Imposition de suffixes

Actuellement, Joomla permet l'accès aux URL avec ou sans suffixe lorsque cette option est activée dans les options de *Configuration globale*.

L'option **Appliquer un suffixe par redirection** dans le plugin *System - SEF* impose un comportement de suffixe cohérent. Lorsqu'elle est activée, elle redirige les requêtes GET vers une URL avec un suffixe si celui-ci est manquant. Elle redirigera également les URLs avec un paramètre de format de requête vers l'URL plus propre, en remplaçant le suffixe par le paramètre de format si nécessaire.

Cette fonctionnalité devrait devenir le comportement par défaut dans Joomla 6.0, où l'option pour l'activer ou la désactiver sera supprimée, et cette fonctionnalité sera intégrée au système de routage principal. Pour l'instant, cette option permet aux utilisateurs de tester le comportement sur des systèmes en production et de la désactiver si des problèmes imprévus surviennent pendant la période de transition de Joomla 5.1 à 6.0.

## Comment accéder

Pour activer l'acheminement strict pour le SEO :

1. Sélectionnez l'élément **Plugins** dans le *Tableau de bord d'accueil*.
1. Trouvez et ouvrez le plugin **System - SEF**.
2. Réglez **Routage strict** sur *Oui* pour activer une gestion plus stricte des URL.
3. Réglez **Imposer un suffixe par redirection** sur Oui ou Non selon votre préférence pour l'application des suffixes d'URL.

Une fois activé, Joomla redirigera automatiquement les URL en double vers celle correcte avec une redirection 301, améliorant le référencement en consolidant le contenu sous une URL unique et autoritaire.

## Notes supplémentaires

Cette fonctionnalité est conçue pour fonctionner comme une étape préparatoire pour d'autres améliorations SEO et est automatiquement activée pour les nouvelles installations de Joomla 5.2. Elle prépare le terrain pour de futures améliorations du système de routage de Joomla.
*Traduit par openai.com*

