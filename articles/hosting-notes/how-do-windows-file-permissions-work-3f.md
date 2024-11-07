<!-- Filename: How_do_Windows_file_permissions_work%3F / Display title: Permissions de fichiers Windows  -->

## Introduction

Pour ceux d'entre vous qui développent ou livrent leurs sites Joomla! à partir d'un environnement Windows, il est parfois difficile d'obtenir des informations pertinentes concernant les permissions. Malheureusement, il est vrai que la plupart des sites Web sont hébergés sous Unix et que Unix est assez bien documenté dans cet environnement. Espérons que les informations suivantes permettront de dissiper toute confusion et de fournir quelques conseils.

### Vue d'ensemble du serveur Web Windows

Tout d'abord, discutons des différences entre les serveurs. En général, la plupart des utilisateurs de Windows semblent utiliser soit Apache(Win32) soit Microsoft IIS. Ces deux serveurs web fonctionnent de manière très différente et utilisent des modèles de diffusion légèrement différents. Apache(Win32) fonctionne généralement sur l'ordinateur hôte en tant qu'utilisateur sous lequel il a été installé, tandis que IIS s'installe sous un utilisateur spécifique mais fonctionne sous un nouvel utilisateur *IUSR_*.

### Paramètres de permission par défaut

Par défaut, Unix a tendance à n'accorder un accès complet qu'à l'utilisateur *propriétaire* des fichiers et des répertoires. À l'inverse, Windows attribue également par défaut le groupe *Tous les utilisateurs* avec des permissions complètes. La première chose que tout bon administrateur Windows fera est de supprimer les droits du groupe *Tous les utilisateurs* pour améliorer la sécurité. Pour des tests sur PC locaux, ce n'est probablement pas nécessaire, mais cela explique pourquoi, si *Tous les utilisateurs* n'est pas supprimé et que vous exécutez une forme de script de vérification des permissions ou la vérification de préinstallation de Joomla!, vous aurez en général des permissions complètes de *Lecture, Écriture et Exécution*, car vous obtenez les droits du groupe *Tous les utilisateurs*.

### Microsoft Internet Information Server (IIS)

IIS existe en deux versions principales, PWS (Personal WebServer) et IIS (Internet Information Server). Essentiellement, il s'agit de la même application. PWS est simplement une version allégée d'IIS conçue pour les environnements de bureau, tandis qu'IIS est conçu pour les environnements de serveur. PWS vous limite à un seul site web principal, donc vos installations d'applications se trouveront généralement dans les sous-répertoires du site web principal. IIS, en revanche, offre la fonctionnalité permettant aux hôtes virtuels de fonctionner à partir de ces répertoires, offrant une capacité multisite.

En raison des limitations fonctionnelles différentes, PWS ne dispose pas de l'*Assistant de permissions* car il est jugé inutile. Un seul utilisateur utilisera le serveur PWS. Dans IIS, de nombreux utilisateurs utiliseront le serveur, donc des attributions de permissions différentes sont nécessaires.

Une fois que le compte *Tous les utilisateurs* est supprimé, le compte *IUSR_* de Windows IIS dispose maintenant des droits de niveau supérieur aux répertoires du serveur web. Une vérification des permissions devrait maintenant donner des résultats différents. Seul le compte *IUSR_* a des permissions complètes et les autres utilisateurs devraient acquérir soit *Lecture seule* soit aucun droit. Les droits sont déterminés par le fait que d'autres utilisateurs ont été assignés manuellement à quels droits aux répertoires IIS.

### Attribution des permissions

Attribuer des permissions dans Windows est assez simple, mais peut être un peu déroutant parfois. Faites un clic droit sur le dossier ou fichier approprié. Sélectionner *Propriétés* ou *Partage et sécurité* vous amènera au volet de gestion de la sécurité de Windows. Sélectionner (cliquer une fois) un nom d'utilisateur répertorié affichera les droits de cet utilisateur dans la moitié inférieure du volet. Certains droits peuvent être *grisés*. Ceux-ci sont indisponibles, soit parce que l'utilisateur actuel (vous êtes connecté en tant que) n'a pas de permissions suffisantes pour les modifier, soit parce qu'ils sont hérités du répertoire supérieur et ont été définis pour utiliser les permissions de ce répertoire de niveau supérieur (c'est généralement le mécanisme par défaut).

Comme vous pouvez le voir, Windows utilise le schéma de Permissions/Droits suivant :

| # | Permissions | Droits |
|:-----:|:----------|:---------|
| 1 | Contrôle total | Autorise : 1, 2, 3, 4, 5, 6, 7 |
| 2 | Modifier | Autorise : 2, 3, 4, 5, 6 |
| 3 | Lire et exécuter | Autorise : 3, 4 |
| 4 | Lister les contenus des dossiers | Autorise : 4 (mais ne peut pas exécuter de programmes) |
| 5 | Lecture | Autorise : 5 (Implique : 4) |
| 6 | Écriture | Autorise : 6 (Implique : 4) |
| 7 | Permissions spéciales | Autorise : Combinaisons |

### Propriétés des permissions de fichiers Windows

Les permissions de fichiers Windows peuvent être vues comme ayant des propriétés **similaires** aux permissions de fichiers UNIX ou Linux (Modes), elles sont juste représentées différemment. Par exemple, si vous êtes principalement un utilisateur Unix/Linux, vous êtes probablement habitué à avoir des permissions représentées comme 644/666 755/777, au lieu d'être décrites dans les termes ci-dessus. Donc, lorsque vous voyez 644, cela équivaut à :

* Le propriétaire de ce fichier peut le lire et l'écrire.
* Le groupe du propriétaire peut lire le fichier.
* Tout le monde peut lire le fichier.

**Remarque :** Les permissions (listes de contrôle d'accès) de Windows et Unix ne correspondent pas exactement, car Windows n'utilise pas le mécanisme des *Groupes* de la même manière. Cependant, pour cette discussion et en ce qui concerne l'environnement d'hébergement Web, elles peuvent être sommairement assimilées. Ah, mais, dans Windows, ***les Groupes*** ne sont pas utilisés et ***Tous les utilisateurs*** devrait avoir été supprimé. C'est là que Windows et Unix ne correspondent pas tout à fait, mais ce qui peut être fait, c'est *apparier* ou *corréler* des significations équivalentes.

Ce document n'est pas vraiment conçu pour vous fournir un guide spécifique aux permissions Windows ou NTFS mais plutôt pour vous permettre de comprendre la corrélation des permissions souvent citées de style UNIX/Linux sur une machine avec un système de fichiers NTFS. Les fichiers placés dans le répertoire racine www ou public_html, ou quel que soit le répertoire vers lequel pointe votre site (www.domain.com.au ou localhost) sur votre disque dur, devraient être la propriété de votre compte utilisateur, mais seulement si cet utilisateur n'est pas considéré comme un utilisateur privilégié comme *Administrateur* sur Windows ou *root* sur UNIX/Linux. Ces comptes permettent un accès beaucoup trop large et ne devraient jamais être utilisés pour un usage quotidien.

### Meilleures pratiques

Les pratiques de sécurité couramment utilisées suggèrent que tous les **fichiers** devraient avoir les permissions suivantes :

* **Propriétaire :** Lecture & Écriture
* **Groupe :** Lecture seule
* **Autres :** Lecture seule

Tous les **répertoires/dossiers** devraient avoir les permissions suivantes :

* **Propriétaire :** Lecture, Écriture & Exécution
* **Groupe :** Lecture & Exécution
* **Autres :** Lecture & Exécution

On peut dire que ce n'est pas nécessairement la sécurité *optimale*, mais un équilibre doit être trouvé entre sécurité, fonctionnalité et maintenabilité. Windows, contrairement à Unix, ne maintient pas une liste de contrôle d'accès unique pour l'*Exécution*, mais fournit simplement *Lire & Exécuter* combiné, ce qui n'implique pas l'*Écriture*. Cependant, le contrôle d'accès *Lire & Exécuter* implique *Lister le contenu du répertoire*. Par conséquent, si vous avez uniquement les permissions de *Lecture & Écriture* sur un répertoire mais pas l'*Exécution*, vous ne pourrez pas voir le contenu du répertoire et pourriez également rencontrer des problèmes en essayant d'exécuter le fichier via un navigateur web. Une petite compréhension des permissions de UNIX/Linux est requise pour les assimiler/corréler pleinement aux permissions de Windows. Le tableau suivant devrait vous aider :

| Mode Unix | ACL Windows | Commentaires |
|:-----:|:----------|:---------|
| 7 | Modifier | Lire, Écrire & Exécuter, vous devriez être le propriétaire de ce fichier |
| 6 | Lire & Écrire |  |
| 5 | Lire & Exécuter | utilisé pour la plupart des applications |
| 4 | Lecture seule | la sécurité par l'obscurité n'est pas une bonne pratique |
| 3 | Écrire & Exécuter | non disponible via Windows, sauf si les "Permissions spéciales" sont utilisées, pas couramment utilisé |
| 2 | Écriture seule | non disponible via Windows, sauf si les "Permissions spéciales" sont utilisées, pas couramment utilisé |
| 1 | Exécution seule | non disponible via Windows, sauf si les "Permissions spéciales" sont utilisées, pas couramment utilisé |

Comparé aux Modes Unix, lorsque vous voyez quelque chose comme 644, vous le décomposez en trois éléments :

**6** : **4** : **4**

Le premier chiffre représente les permissions du **Propriétaire**, le deuxième représente les permissions du ***Groupe*** et le troisième, les ***Autres*** permissions. L'équivalent Windows serait :

* **Propriétaire** (6) : **Lire & Écrire**
* **Groupe** (4) : **Lecture seule**
* **Autres** (4) : **Lecture seule**

Espérons que cet exemple offre un aperçu de la façon de corréler les modes/permissions Unix aux permissions/ACL Windows. Ce document n'inclut pas de sujets plus complexes tels que les permissions *Efficaces*, *Héritées*, ou *Spéciales*. Malgré la facilité d'utilisation de Windows, les mécanismes de permissions et d'ACL de Microsoft sont en réalité raisonnablement complexes et très extensifs, mais cela peut juste vous donner une référence rapide pour essayer d'atténuer certaines des confusions entourant les traductions des permissions Unix et Windows.

