<!-- Filename: J4.x:Hosting_Setup / Display title: Configuration de l'hébergement -->

## Introduction

Cette page offre des conseils à ceux qui sont complètement novices en matière de technologies d'hébergement. Vous pouvez configurer un site web sur votre propre ordinateur portable ou de bureau. C'est ce qu'on appelle l'hébergement local, et c'est un bon moyen d'expérimenter de nouvelles fonctionnalités, et c'est entièrement gratuit. Pour rendre le contenu de votre site web accessible au reste du monde, vous aurez besoin d'un compte sur un service d'hébergement et, pour cela, vous devrez payer.

## Logiciels de Support

Joomla! est une application qui dépend de trois éléments de logiciels de support : le langage de script PHP, une base de données (l'une de MySQL, MariaDB ou PostgreSQL) et un serveur web (l'un de Apache, Nginx, Microsoft IIS, ou ...). Les numéros de version minimum sont indiqués dans les tableaux suivants :

### Exigences pour Joomla! 5.x

| Logiciel          | Recommandé      | Minimum     |
|-------------------|-----------------|-------------|
| PHP               | 8.3             | 8.1.0       |
| **Bases de données** |                 |             |
| MySQL             | 8.1             | 8.0.13      |
| MariaDB           | 11.1.0          | 10.4.0      |
| PostgreSQL        | 16.0            | 12.0        |
| **Serveurs Web**  |                 |             |
| Apache            | 2.4             | 2.4         |
| Nginx             | 1.25            | 1.21        |
| Microsoft IIS     | 10              | 10          |

### Exigences pour Joomla! 4.x

| Logiciel          | Recommandé      | Minimum     |
|-------------------|-----------------|-------------|
| PHP               | 8.2             | 7.2.5       |
| **Bases de données** |                 |             |
| MySQL             | 8.0             | 5.6         |
| PostgreSQL        | 11.0            | 11.0        |
| **Serveurs Web**  |                 |             |
| Apache            | 2.4             | 2.4         |
| Nginx             | 1.18            | 1.10        |
| Microsoft IIS     | 10              | 8           |

## Services d'hébergement

Les services d'hébergement commercial fournissent tout ce dont vous avez besoin pour soutenir un site web. Certains offrent également l'installation en un clic d'applications populaires telles que les systèmes de gestion de contenu, les forums de discussion, les wikis, etc. Mais veuillez noter : les experts du forum Joomla ne recommandent pas l'utilisation de l'installation en un clic pour Joomla.

Chaque service d'hébergement propose différents plans à différents niveaux de prix. Plus vous payez, plus vous obtenez d'espace disque et de bande passante, ainsi que davantage d'adresses e-mail, de bases de données, etc. Certains fournissent également un nom de domaine gratuit. Le plus souvent, vous devez payer pour un nom de domaine et une petite redevance annuelle d'enregistrement.

## Hébergement Gratuit

Il n'existe pas d'hébergement vraiment gratuit ! Cependant, un partenaire d'hébergement Joomla propose un site web Joomla gratuit dans le domaine joomla.com. Cela vous offre l'opportunité d'essayer votre propre site Joomla entièrement fonctionnel, sans frais. C'est similaire à un plan d'hébergement mutualisé, mais avec des restrictions et des sollicitations fréquentes pour passer à un plan payant. De plus, le plan gratuit doit être renouvelé tous les 30 jours sous peine d'être résilié. L'article suivant montre les étapes nécessaires pour configurer un site Joomla gratuit.

* [Hébergement Joomla Gratuit](jdocmanual?article=user/hosting/free-hosting)

Si vous découvrez que vous aimez Joomla, vous pouvez passer à un plan payant ou chercher ailleurs un service d'hébergement adapté à vos besoins et à votre budget.

## Hébergement Partagé

Vous pouvez obtenir un plan d'hébergement minimal pour environ 50 £/$/€ par an. Ce niveau de plan est souvent appelé hébergement partagé et convient à tout ce qui n'implique pas de données sensibles. Les entreprises doivent chercher un conseil spécialisé sur les plans d'hébergement appropriés. Choisir un service d'hébergement n'est pas sans problèmes. Le moins cher peut avoir des paramètres *php.ini* indûment restrictifs qui n'apparaissent pas dans leur publicité. Certains peuvent avoir une mauvaise réputation en matière de support.

Si vous optez pour un plan d'hébergement partagé, vérifiez les éléments suivants :

- Support pour les applications PHP telles que Joomla, WordPress et Mediawiki.
- Espace disque : 500 Mo est un minimum absolu. 1 Go ou plus serait mieux si vous prévoyez d'utiliser beaucoup d'images.
- Nombre de bases de données : Joomla en utilise une, mais vous découvrirez bientôt que vous en avez besoin de 5 ou 10 ou plus. Certains plans offrent un nombre illimité dans l'allocation totale de l'espace disque.
- Taille de la base de données : avec Smart Search, la base de données peut croître très rapidement. Si l'hébergement partagé a une restriction sur la taille de la base de données, il sera important de découvrir ce que c'est. Cela peut entraîner un dysfonctionnement du site.
- Nombre d'adresses email : en abondance !
- Nombre de connexions HTTP et DB au serveur, limitées par certains hôtes partagés.
- Sauvegardes : comment sont-elles faites, et y a-t-il un document de Conditions d'Utilisation (TOS) précisant qui est responsable des sauvegardes.

Vérifiez également le panneau de contrôle et la plateforme proposés. D'après les messages du forum, la plupart utilisent cPanel sur Linux. Le service d'hébergement devrait fournir tous les logiciels de support de base pour le site web :

- Serveur web Apache 2.4+ - *les index de répertoire* devraient être désactivés. Également pris en charge :
  - Nginx 1.18+ (moins d'utilisateurs donc moins de support forum)
  - Microsoft IIS\[6\] (moins d'utilisateurs donc moins de support forum)
- Base de données MySQLi 8.1+ ou clone MariaDB avec support InnoDB. Également pris en charge :
  - PostgreSQL 11.0+ (moins d'utilisateurs donc moins de support forum).
- PHP 8+ est recommandé.
- Outil de gestion de base de données phpMyAdmin.

Avant d'acheter, vérifiez les exigences PHP minimales suivantes pour Joomla :

- *memory_limit* - Minimum : 256M
- *upload_max_filesize* - Minimum : 64M
- *post_max_size* - Minimum : 64M
- *max_execution_time* - Recommandé : 30
- *allow_url_fopen* - true

Beaucoup de ces paramètres peuvent être définis par l'utilisateur dans cPanel. Demandez si cela est possible.

Si vous avez acheté un nom de domaine, votre service d'hébergement le configurera pour vous. Ils devraient également vous fournir une adresse IP à utiliser jusqu'à ce que votre enregistrement de domaine soit propagé aux serveurs de noms de domaine (DNS), généralement quelques heures.

L'article suivant montre à quoi vous attendre si vous achetez un plan d'hébergement qui inclut une interface utilisateur cPanel.

* [Hébergement cPanel](jdocmanual?article=user/hosting/cpanel-hosting)

## Hébergement VPS

Un plan d'hébergement de serveur privé virtuel (VPS) offre un accès complet à un serveur qui partage du matériel. Il se comporte comme un ordinateur dédié. Vous pouvez arrêter et démarrer le serveur, le redémarrer et installer votre propre logiciel exactement comme vous le feriez sur un ordinateur de bureau. Vous pouvez créer des comptes pour des utilisateurs individuels, tout comme dans l'hébergement mutualisé. En général, vous pouvez permettre certaines fonctionnalités qui ne sont normalement pas autorisées dans les comptes d'hébergement mutualisé.

Les plans d'hébergement dédié et cloud sont similaires en principe, mais offrent soit des ressources dédiées, soit des ressources adaptées à vos besoins.

Ces plans avancés ne sont pas couverts ici.

## Hébergement local

La plupart des personnes qui développent des sites Web conservent des copies locales sur un ordinateur portable ou de bureau pour tester des mises à jour ou de nouvelles extensions ou pour essayer de nouveaux designs. Mettre en place un site de développement local nécessite quelques connaissances techniques, mais il est assez facile de suivre des instructions simples.

Les articles suivants décrivent comment configurer un hébergement local sur différents types d'ordinateurs de bureau ou portables :

* [Hébergement local sur Windows](jdocmanual?article=user/hosting/local-hosting-on-windows) uniquement pour Windows
* [Hébergement local avec XAMPP](jdocmanual?article=user/hosting/local-hosting-with-xampp) pour Linux, Mac et Windows.
* [Hébergement local sur Linux](jdocmanual?article=user/hosting/local-hosting-on-linux)

