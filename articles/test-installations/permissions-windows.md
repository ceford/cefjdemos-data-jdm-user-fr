<!-- Filename: How_do_Windows_file_permissions_work? / Display title: Autorisations de fichiers : Windows  -->

## Introduction

Pour ceux d'entre vous qui développent ou livrent vos sites Joomla! depuis un environnement Windows, il est parfois difficile d'obtenir des informations pertinentes concernant les autorisations. Malheureusement, il est vrai que la majorité des services Web sont proposés sous Unix et que Unix est assez bien documenté dans cet environnement. Espérons que les informations suivantes contribueront à dissiper toute confusion et fourniront également quelques conseils. 

## Aperçu des serveurs web Windows

Tout d'abord, discutons des différences entre les serveurs. En général, la plupart des utilisateurs de Windows semblent utiliser soit Apache (Win32) soit Microsoft IIS. Ces deux serveurs web fonctionnent de manière très différente et utilisent des modèles de livraison légèrement différents. Apache (Win32) fonctionne généralement sur l'ordinateur hôte en tant qu'Utilisateur sous lequel il a été installé, tandis que IIS s'installe sous un utilisateur spécifique mais fonctionnera sous un nouvel utilisateur installé *IUSR_*.

## Paramètres par Défaut des Permissions

Par défaut, Unix tend à donner un accès complet uniquement à l'utilisateur *propriétaire* des fichiers et des répertoires. En revanche, Windows, par défaut, attribue également des permissions complètes au groupe *Everyone* (Tout le monde). La première chose qu'un bon administrateur Windows fera est de retirer les droits du groupe *Everyone* pour améliorer la sécurité. Pour les tests sur un PC local, cela n'est probablement pas nécessaire, mais cela explique pourquoi, si *Everyone* n'est pas retiré et que vous exécutez une sorte de script de vérification des permissions ou le contrôle pré-installation de Joomla!, vous aurez des permissions complètes de *Lecture, Écriture et Exécution*. Vous acquérez les droits du groupe *Everyone*.

## Microsoft Internet Information Server (IIS)

IIS est disponible en deux principales versions, PWS (Personal WebServer) et IIS (Internet Information Server). Essentiellement, ce sont la même application. PWS est simplement une version allégée d'IIS conçue pour les environnements de bureau, tandis qu'IIS est conçu pour les environnements serveurs. PWS vous limite à un seul site principal, donc vos installations d'applications se feront généralement dans des sous-répertoires du site principal. IIS, quant à lui, offre la fonctionnalité pour exécuter des Hôtes Virtuels depuis ces répertoires, fournissant ainsi la capacité multi-sites.

En raison des différentes limitations fonctionnelles, PWS n'a pas l'*Assistant Permissions* car il est jugé inutile. Seul un utilisateur utilisera le serveur PWS. Dans IIS, de nombreux utilisateurs utiliseront le serveur, nécessitant ainsi des attributions de permissions différentes.

Une fois le compte *Everyone* supprimé, Windows IIS se retrouve avec le compte *IUSR_** ayant des droits de premier niveau sur les répertoires du serveur Web. Une vérification des permissions devrait maintenant donner des résultats différents. Seul le compte *IUSR_** dispose de toutes les permissions et les autres utilisateurs devraient obtenir soit *Lecture Seule* soit aucun droit. Les droits sont déterminés par quels autres utilisateurs ont été assignés quels droits manuellement aux répertoires IIS.

### Attribution des Permissions

Attribuer les permissions sous Windows est relativement simple, mais peut être un peu déroutant parfois. Cliquez avec le bouton droit sur le dossier ou le fichier approprié. Sélectionner *Propriétés* ou *Partage et Sécurité* vous dirigera vers le panneau de gestion de la Sécurité Windows. Sélectionner (cliquez une fois) un nom d'utilisateur listé affichera les droits de cet utilisateur dans la moitié inférieure du panneau. Certains droits peuvent être *grisés*. Ils sont indisponibles, soit parce que l'utilisateur courant (celui sous lequel vous êtes connecté) n'a pas suffisamment de permissions pour les modifier, soit parce qu'ils sont hérités du répertoire ci-dessus et ont été définis pour utiliser les permissions du répertoire de niveau supérieur. (C'est généralement le mécanisme par défaut.)

Comme vous pouvez le voir, Windows utilise le schéma de Permissions/Droits suivant :

| # | Contrôle | Autorisations # |
| :---: | :---- | :--- |
| 1.| Contrôle Total | Autorise : 1, 2, 3, 4, 5, 6, 7 |
| 2.| Modifier | Autorise : 2, 3, 4, 5, 6 |- |
| 3.| Lire & Exécuter | Autorise : 3, 4 |- |
| 4.| Lister le Contenu du Dossier | Autorise : 4 (mais ne peut pas exécuter de programmes) |- |
| 5.| Lire | Autorise : 5 (Implique : 4) |- |
| 6.| Écrire | Autorise : 6 (Implique : 4) |- |
| 7.| Permissions Spéciales | Autorise : Combinaisons |

### Propriétés des Permissions de fichier Windows

Les permissions de fichier Windows peuvent être vues comme ayant des propriétés similaires aux permissions de fichier UNIX ou Linux (Modes). Elles sont juste représentées différemment. Par exemple, si vous êtes principalement un utilisateur Unix/Linux, vous êtes probablement habitué à voir les permissions représentées comme 644/666 755/777, au lieu d'être décrites dans les termes ci-dessus. Donc, quand vous utilisez 644, cela signifie :

- Le propriétaire de ce fichier peut lire et écrire.
- Le groupe du propriétaire peut lire le fichier.
- Tout le monde peut lire le fichier.

**Note :** Les permissions Windows et Unix (Listes de Contrôle d'Accès) ne s'équivalent pas exactement ; Windows n'utilise pas le mécanisme de *Groupes* de la même manière. Pour cette discussion et en ce qui concerne l'environnement hébergement Web, elles peuvent être mises en équivalence. Cependant, sous Windows, les *Groupes* ne sont pas utilisés et *Everyone* devrait avoir été retiré. C'est là que Windows et Unix ne s'équivalent pas tout à fait, mais ce qui peut être fait est de *faire correspondre* ou *corréler* des significations équivalentes.

Ce résumé ne va pas vraiment vous fournir un guide des permissions spécifiques à Windows ou à NTFS, mais plutôt une compréhension de la façon dont les permissions couramment citées dans le style numéroté UNIX/Linux se corrèlent sur une machine avec un système de fichiers NTFS. Les fichiers placés dans le dossier racine `www` ou `public_html`, ou dans n'importe quel répertoire vers lequel pointe votre site (`www.domain.com` ou `localhost`) sur votre disque dur, devraient être possédés par votre compte utilisateur, mais seulement si cet utilisateur n'est pas considéré comme un utilisateur privilégié tel qu'*Administrateur* sous Windows ou *root* sous UNIX/Linux. Ces comptes autorisent beaucoup trop d'accès et ne devraient jamais être utilisés pour un usage quotidien.

### Meilleures Pratiques

Les pratiques couramment utilisées en matière de sécurité suggèrent que tous les **fichiers** devraient avoir les permissions suivantes :

- **Propriétaire** Lire & Écrire
- **Groupe** Lecture Seule
- **Autres** Lecture Seule

Tous les **répertoires/dossiers** devraient avoir les permissions suivantes :

- **Propriétaire** Lire, Écrire & Exécuter
- **Groupe** Lire & Exécuter
- **Autres** Lire & Exécuter

Arguablement, ce n'est pas forcément une sécurité *optimale*, mais un équilibre doit être trouvé entre sécurité, fonctionnalité et maintenabilité.

Windows, contrairement à Unix, ne maintient pas une seule ACL pour *Exécuter*, mais fournit simplement *Lire & Exécuter* combiné, ce qui n'implique pas *Écrire*. Cependant, l'ACL *Lire & Exécuter* implique *Lister le Contenu du Dossier*. Par conséquent, si vous avez seulement des permissions *Lire & Écrire* sur un répertoire mais pas *Exécuter*, vous ne pourrez pas voir le contenu du répertoire et vous pourriez également avoir des problèmes lorsque vous essayez de lancer le fichier via un navigateur Web. Une certaine compréhension des permissions UNIX/Linux est nécessaire pour les équivaloir/corréler pleinement aux permissions Windows. Le tableau suivant devrait vous aider :

| Mode Unix | ACL Windows | Commentaires |
|:---:| :--- | :--- |
| 7 | Modifier | Lire, Écrire & Exécuter, vous devriez être le propriétaire de ce fichier |
| 6 | Lire & Écrire | |
| 5 | Lire & Exécuter | utilisé pour la plupart des applications |
| 4 | Lecture Seule | la sécurité par l'obscurité n'est pas une bonne pratique |
| 3 | Écrire & Exécuter | non disponible sous Windows, sauf si les Permissions *Spéciales* sont utilisées, pas couramment utilisé |
| 2 | Écriture Seule | non disponible sous Windows, sauf si les Permissions *Spéciales* sont utilisées, pas couramment utilisé |
| 1 | Exécuter Seul | (non disponible sous Windows, sauf si les Permissions *Spéciales* sont utilisées, pas couramment utilisé) |

En comparaison des modes Unix, lorsque vous voyez quelque chose comme 644, décomposez cela en trois éléments :

Le premier chiffre représente les permissions du Propriétaire, le second représente les permissions du Groupe et le troisième, les permissions des Autres. L'équivalent Windows serait :

- **Propriétaire** (6) Lire & Écrire
- **Groupe** (4) Lecture Seule
- **Autres** (4) Lecture Seule

Espérons que cet exemple offre un certain aperçu sur la façon de corréler les Modes/Permissions Unix en Permissions/ACLs Windows. Ce document n'inclut pas des sujets plus complexes tels que les permissions *Effectives*, *Héritées*, ou *Spéciales*. Malgré la facilité d'utilisation de Windows, les mécanismes de Permissions et ACL de Microsoft sont en réalité raisonnablement complexes et très étendus, mais cela pourrait juste vous donner une référence rapide pour essayer d'atténuer une partie de la confusion autour des traductions de Permissions Unix et Windows. 

*Traduit par openai.com*

