<!-- Filename: Managing_404_Errors / Display title: Gestion des erreurs 404 -->

## Pourquoi le 404 Not Found est important

Le problème le plus courant avec les sites web qui ont du mal à se classer dans les moteurs de recherche est le nombre d'erreurs de « page non trouvée » - communément appelées erreurs *404* car il s'agit du code d'état renvoyé si la page ne peut pas être trouvée.

Tout d'abord, il y a des raisons légitimes d'avoir des erreurs 404 – si vous avez une page pour un événement qui a eu lieu, ou un service que vous ne proposez plus. Dans ces cas-là, la page sera éventuellement retirée de l'index des moteurs de recherche et ne sera plus associée à votre site.

Le problème survient si vous avez beaucoup d'erreurs 404 – par exemple si vous dépubliez une catégorie qui contenait des centaines d'articles. Du point de vue du moteur de recherche, ce n'est pas une bonne expérience pour leurs visiteurs, car ils arrivent sur votre site et l'information que le moteur de recherche leur a indiquée est absente. C'est pourquoi il n'est pas judicieux d'avoir trop d'erreurs 404 sur votre site.

## Google Search Central

La première étape consiste à découvrir combien vous en avez – ce qui peut être fait en utilisant [Search Central de Google](https://developers.google.com/search). Il s'agit d'un ensemble d'outils gratuit qui vous permet d'analyser votre site Web et de détecter rapidement les problèmes, les erreurs et les soucis. Il est recommandé d'enregistrer chaque site que vous gérez sur Search Central pour vous assurer d'être informé en cas de problèmes.

Lorsque vous visitez Search Central, il y a une section qui vous montre les erreurs d'URL dans les résultats de recherche – cela vous fournira une liste des erreurs 404 que Google a trouvées sur votre site, ainsi qu'un graphique qui vous montre comment cela a évolué au fil du temps. Si le graphique commence à monter, examinez pourquoi il y a des pages qui étaient sur votre site et qui ne peuvent maintenant plus être trouvées.

S'il y a eu un problème temporaire sur votre site, vous pouvez marquer les erreurs comme étant corrigées.

![outils pour les webmasters](../../../en/images/performance/404-discovery.png)

## Résolution des problèmes

La découverte n'est qu'une partie du processus. Une fois que vous avez découvert les URL problématiques, faites quelque chose à ce sujet (si cela nécessite une correction !) en redirigeant la page vers une autre du site, en rétablissant la page d'origine ou en analysant la cause de l'erreur 404.

Si vous devez rediriger une page, vous pouvez utiliser le plugin "System - Redirect" pour collecter les pages manquantes et le composant "System / Redirects" pour rediriger les pages manquantes vers des pages existantes.

## Surveillance des Problèmes

Si vous souhaitez surveiller votre trafic 404, la meilleure façon de le faire dans Analytics est d'examiner ce qui se passe lorsque vous avez une erreur 404. Dans la plupart des cas, le titre de la page change en 404 – nous pouvons donc créer un segment personnalisé qui filtrera le trafic ayant un titre de 404 et vous indiquera quelle est la page de destination. Cela devrait vous permettre de surveiller et de gérer de manière proactive vos erreurs 404 et de vous assurer que vos visiteurs n'atterrissent pas sur des liens morts.

![Alertes Analytics trafic 404](../../../en/images/performance/404-analytics-alerts.png)

![Vue d'ensemble du public alertes Analytics](../../../en/images/performance/404-analytics-alerts-2.png)

Google offre également la possibilité, dans Analytics, de configurer des alertes. Les alertes vous permettent de recevoir un courriel lorsque certains événements se produisent. Dans ce cas, nous pouvons configurer une alerte pour être notifié s'il y a plus de 5 % d'augmentation du nombre d'erreurs 404 sur une période hebdomadaire – ce qui pourrait signifier que nous avons un problème avec le site Web qui nécessite une enquête.

C'est une excellente manière de rester à jour, même si vous n'avez pas consulté votre tableau de bord !

![Email d'alertes Analytics](../../../en/images/performance/404-analytics-alerts-email.png)

## Suivi des erreurs avec un tableau de bord

Il existe également un tableau de bord que vous pouvez installer appelé le *Tableau de Bord d'Intégrité des Données*, qui vous montre des informations sur les erreurs 404, ainsi que d'autres métriques qui pourraient vous intéresser. Il suffit de rechercher dans la Galerie Google Analytics pour *Tableau de Bord d'Intégrité des Données* et de sélectionner sous quel profil l'installer.

![Intégrité des données](../../../en/images/performance/404-data-integrity.png)

*Traduit par openai.com*

