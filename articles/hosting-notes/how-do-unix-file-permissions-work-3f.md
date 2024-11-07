<!-- Filename: How_do_UNIX_file_permissions_work%3F / Display title: Permissions de fichiers UNIX -->

Les permissions de fichiers Unix/Linux peuvent être déroutantes. Les permissions UNIX de base se déclinent en trois catégories :

    Permissions du propriétaire : Contrôlez votre propre accès aux fichiers.
    Permissions du groupe : Contrôlez l'accès pour vous et votre groupe.
    Permissions des autres : Contrôlez l'accès pour toutes les autres personnes.

Dans Unix, lorsque les permissions sont configurées, le serveur vous permet de définir différentes permissions pour chacune de ces trois catégories d'utilisateurs. Dans un environnement de serveur Web, les permissions sont utilisées pour contrôler quels propriétaires de sites Web peuvent accéder à quels répertoires et fichiers.

## À quoi ressemblent les permissions Unix ?

Lorsque vous visualisez vos fichiers via la ligne de commande en utilisant la commande Unix `ls -l`, vous verrez des lignes comme les suivantes, une pour chaque fichier et répertoire :

```
drwxr-xr-x@  7 nomutilisateur  groupeutilisateur    224 13 Feb 10:48 includes
-rw-r--r--@  1 nomutilisateur  groupeutilisateur   1060 13 Apr 21:00 index.php
```
Explication :
* Le premier caractère de la ligne est un d pour répertoire ou un - pour fichier, ou ...
* Les 9 caractères suivants sont 3 groupes de 3 représentant lecture (r), écriture (w) et exécution (x) ou un symbole moins (-) signifiant aucun accès pour chacun des Propriétaire, Groupe et Autres.
* Le symbole @ est l'un des nombreux attributs étendus possibles.
* Le nombre avant le nom d'utilisateur est la profondeur du répertoire.
* Les deux noms sont le nom d'utilisateur propriétaire et le groupe d'utilisateur,
* L'entier suivant est la taille du fichier en octets.
* La date suivante inclut l'heure pour les éléments récents ou l'année pour les éléments plus anciens.
* Enfin, il y a le nom du fichier ou du répertoire.

Dans un utilitaire FTP, l'ordre peut être différent et il peut y avoir plus ou moins d'informations.

### Propriétaire (Utilisateur) se rapporte au nom d'utilisateur

Le Propriétaire (Utilisateur) est normalement vous, ces permissions seront appliquées sur le nom de votre compte d'hébergement.

### Groupe se rapporte au groupe d'utilisateur

Les permissions de Groupe seront appliquées aux autres personnes qui sont dans le même groupe que vous ; dans un environnement d'hébergement, il est très rare qu'il y ait d'autres personnes dans le même groupe que vous. Cela protège vos fichiers et répertoires d'être accessibles à quiconque pourrait également avoir un compte d'hébergement sur le même serveur que vous.

### Autre se rapporte à tout le reste

Les permissions Autre, seront appliquées à quiconque sur le serveur qui n'est ni vous ni dans votre groupe. Donc dans un environnement de serveur Web, en gardant à l'esprit que personne d'autre n'est normalement dans votre groupe, cela concerne tout le monde accédant au serveur sauf vous. Chacune des trois séries de permissions est définie de la manière suivante :

    r = Permissions de lecture
    w = Permissions d'écriture
    x = Permissions d'exécution

    Propriétaire Groupe Autre
    r w x r w x r w x

Comme beaucoup d'entre vous le savent déjà, les permissions sont normalement exprimées sous forme de valeur numérique, quelque chose comme 755 ou 644. alors, comment cela se rapporte-t-il à ce que nous avons discuté plus haut ? Chaque caractère des permissions se voit attribuer une valeur numérique, cette valeur est attribuée dans chaque ensemble de trois, donc nous n'avons besoin d'utiliser que trois valeurs et de les réutiliser pour chaque ensemble.

    Propriétaire Groupe Autre
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Maintenant que nous avons une valeur qui représente chaque permission, nous pouvons les exprimer en termes numériques. Les valeurs sont simplement additionnées dans leurs ensembles respectifs de 3, ce qui nous donnera à son tour seulement trois chiffres qui nous indiqueront quelles permissions sont définies. Si nous apprenons qu'un fichier a les permissions de 777, cela signifierait que ce qui suit est vrai.

    Propriétaire Groupe Autre
    r w x r w x r w x
    4 2 1 4 2 1 4 2 1

Ainsi...

      4+2+1 4+2+1 4+2+1
    =   7     7     7

Le propriétaire du fichier aurait toutes les permissions de lecture, écriture et exécution, le groupe aurait également toutes les permissions de lecture, écriture et exécution, et le reste du monde peut aussi lire, écrire et exécuter le fichier. Les permissions par défaut attribuées aux fichiers et répertoires par le serveur sont normalement ;

    Fichiers = 644
    Répertoires = 755

Ces permissions permettraient, pour les fichiers ;

    644 = rw- r-- r--
    Le propriétaire a les permissions de lecture et écriture
    Le groupe a uniquement les permissions de lecture
    L'autre a uniquement les permissions de lecture

et pour les répertoires ;

    755 = rwx r-x r-x
    Le propriétaire a les permissions de lecture, écriture et exécution
    Le groupe a uniquement les permissions de lecture et exécution
    L'autre a uniquement les permissions de lecture et exécution

Les choses peuvent devenir un peu compliquées lorsque nous commençons à parler de serveurs Web partagés ; le logiciel du serveur Web fonctionnera avec son propre nom d'utilisateur et son propre nom de groupe ; la plupart des serveurs sont configurés pour qu'ils utilisent soit "apache" et "apache", soit "nobody" et "nobody" comme nom d'utilisateur et nom de groupe. Voici le problème. Votre serveur Web s'exécute en tant qu'utilisateur propre, et cet utilisateur n'est pas vous ni dans votre groupe, donc les deux premiers ensembles de permissions ne s'appliquent pas à lui. Seules les permissions monde (autre) s'appliquent. Par conséquent, si vous configurez un ensemble de permissions similaire à 640 sur les fichiers de votre site web, votre serveur Web ne pourra pas exécuter les fichiers de votre site web.

    640 = rw- r-- ---
    Le propriétaire a les permissions de lecture et écriture
    Le groupe a uniquement les permissions de lecture
    L'autre n'a pas de droits

Le serveur Web n'est affecté d'aucune permission et ne peut pas exécuter, écrire ou plus important, même lire le fichier pour délivrer son contenu au navigateur du visiteur du site Web. Si un répertoire devait être attribué les permissions 750, cela aurait le même effet, car le serveur Web n'a même pas les permissions de lire les fichiers dans le répertoire, même si les fichiers dans ce répertoire avaient des permissions favorables.

    750 = rw- r-x ---
    Le propriétaire a les permissions de lecture et écriture
    Le groupe a les permissions de lecture et exécution
    L'autre n'a pas de droits

Les répertoires ont une particularité supplémentaire : si un répertoire n'a pas la permission d'exécution attribuée dans l'ensemble Monde, même si les permissions de lecture et écriture sont attribuées, si le programme ne s'exécute pas en tant qu'utilisateur ou groupe, il ne pourra toujours pas accéder aux fichiers dans le répertoire. La permission d'exécution permet au programme d'"exécuter" des commandes dans le répertoire, donc sans cette permission, le programme (dans notre cas un serveur Web) ne peut pas exécuter la commande "Lecture", et ne peut donc pas fournir votre fichier au navigateur des utilisateurs.

## Comment cela se rapporte-t-il à Joomla?

Bonne question, eh bien, dans un premier temps, cela serait important lors du processus d'installation Web. Si vous vous souvenez de lorsque vous avez exécuté l'installateur Web Joomla!, nous cherchions à désigner certains répertoires comme étant inscriptibles. Nous voyons un certain nombre de messages indiquant soit qu'il y a eu des problèmes d'autorisations lors de l'installation, soit demandant quelles permissions sont recommandées. Certains considèrent même que le message demandant des permissions "inscriptibles" est trop vague.

Malheureusement, comme l'installateur Web ne sait pas comment votre serveur est configuré, il ne peut pas être plus précis. Cependant, une fois que vous comprenez les paramètres d'autorisations et que vous en savez un peu sur les environnements d'hébergement Web, vous réaliserez que le terme *inscriptible* est en fait très spécifique et une description plus qu'adéquate de ce dont Joomla! a besoin. En pensant aux informations ci-dessus, vous vous souviendrez peut-être qu'il y a trois endroits où les permissions d'écriture peuvent être définies :

    Propriétaire inscriptible
    Groupe inscriptible
    Autres inscriptibles

En se rappelant également que le serveur Web ne fonctionne généralement pas comme votre propre utilisateur ou dans le même groupe. Lorsque vous exécutez l'installateur Web depuis un navigateur, c'est le serveur Web qui tente d'accéder aux fichiers, il s'agit donc des permissions "Autres" qui lui seront appliquées. Si les permissions "Autres" n'autorisent pas le serveur Web à lire, écrire ou exécuter des commandes dans les répertoires Joomla!, vous recevrez le message indiquant que les répertoires ne sont pas *inscriptibles*.

Dans ce cas, vous devrez configurer les permissions Autres pour qu'elles soient "7" sur les répertoires listés dans l'installateur Web. Ainsi, vos permissions totales pourraient être quelque chose comme 757, dans le pire des cas, vous pourriez avoir besoin de définir 777. Ces permissions très ouvertes peuvent être réinitialisées à 755 après l'exécution de l'installateur afin de garantir la sécurité de vos répertoires et fichiers.

    757 = rwx r-x rwx
    Le propriétaire a la lecture, l'écriture et l'exécution
    Le groupe a la lecture et l'exécution
    Les autres ont la lecture, l'écriture et l'exécution

Pour compliquer encore les choses, de nombreuses entreprises d'hébergement utilisent un logiciel appelé phpsuExec ou suExec, ces outils modifient la façon dont le serveur Web fonctionne, là où le serveur Web ne fonctionnerait normalement pas en tant que votre nom d'utilisateur, dans ce cas, il le fait. L'utilisation des permissions *autres* peut ne pas être nécessaire, maintenant vous pouvez uniquement avoir besoin de configurer les répertoires pour qu'ils soient *inscriptibles* pour votre propre nom d'utilisateur et nom de groupe, ce qui permet de définir les permissions de répertoire à 755 ou 775 au lieu de 757 ou 777. 

    755 = rwx r-x r-x
    Le propriétaire a la lecture, l'écriture et l'exécution
    Le groupe a la lecture et l'exécution
    Les autres ont la lecture et l'exécution

    775 = rwx rwx r-x
    Le propriétaire a la lecture, l'écriture et l'exécution
    Le groupe a la lecture, l'écriture et l'exécution
    Les autres ont la lecture et l'exécution

Le serveur Web aura toujours besoin d'avoir l'exécution définie pour le nom d'utilisateur et la lecture, les permissions d'exécution du nom de groupe définies pour qu'il puisse exécuter la commande de lecture sur les fichiers à l'intérieur du répertoire. Encore une fois, ces permissions peuvent être rétrogradées à 755 après l'installation de l'installateur Web. Voilà pour les répertoires, qu'en est-il des fichiers? C'est là que les choses deviennent un peu plus simples. La plupart des fichiers utilisés par Joomla! seront parfaitement satisfaits des permissions par défaut 644.

    644 = rw- r-- r--
    Le propriétaire a la lecture, l'écriture
    Le groupe a la lecture
    Les autres ont la lecture

C'est valable si vous n'avez pas besoin d'écrire dans les fichiers à partir du serveur Web, les mêmes règles s'appliquent que pour les répertoires si vous avez ce besoin. Un fichier que vous aimeriez peut-être rendre "inscriptible" pour le serveur Web est votre fichier configuration.php. Il s'agit du fichier de configuration de Joomla!, si vous prévoyez de changer la configuration via l'interface d'administration Web, ce fichier devra être inscriptible pour le serveur Web.

Si votre serveur avait besoin que les permissions de répertoire soient définies sur "Autres" Inscripitible pour l'installation, alors ce fichier aura probablement aussi besoin d'être 757 ou 777. Laisser ce fichier à 757 ou 777 est dangereux, car vous laissez tout le monde avoir un accès "Write", de nombreuses exploitations de sites Web profitent de ce fait, donc en général, il n'est pas recommandé que ce fichier ait ces autorisations.

Si votre serveur Web a l'un des outils SU installés et que vous avez seulement eu besoin de configurer 755 sur les répertoires pour l'installation, alors vous aurez probablement aussi seulement besoin de définir 755 ou 775 sur ce fichier pour permettre l'édition via l'interface d'administration, et ces permissions sont généralement considérées comme plus sécurisées que 757 ou 777.

En conclusion, quelles permissions devraient être définies pour l'installation de Joomla! ? Eh bien, comme vous pouvez le voir, cela dépend!

Je sais que ce n'est pas aussi utile que vous l'auriez souhaité et que ce n'est certainement pas une réponse définitive, mais en général, après l'installation, tous les paramètres "7" non sécurisés peuvent être réinitialisés à quelque chose de plus sécurisé. Par exemple :

    Fichiers = 644
    Répertoires = 755

Ces permissions permettraient, pour les fichiers ;

    644 = rw- r-- r--
    Le propriétaire a la lecture et l'écriture
    Le groupe a uniquement la lecture
    Les autres ont uniquement la lecture

et pour les répertoires,

    755 = rwx r-x r-x
    Le propriétaire a la lecture, l'écriture et l'exécution
    Le groupe a juste la lecture et l'exécution
    Les autres ont juste la lecture et l'exécution

Si vous avez un accès à un shell SSH, les commandes suivantes peuvent être exécutées à partir de la ligne de commande pour réinitialiser tous les fichiers et répertoires aux valeurs par défaut du serveur de 755 et 644. Changez de répertoire pour le répertoire supérieur (" / ") de votre installation Joomla!, puis exécutez :

    find . -type f -exec chmod 644 {} \;
    find . -type d -exec chmod 755 {} \;

Si vous n'avez qu'un accès FTP, cela peut être une tâche très chronophage, cependant, sauf si vous avez changé plus de répertoires pendant l'installation que ce qui était demandé, vous devriez seulement avoir besoin de réinitialiser environ 10 répertoires et le fichier *configuration.php*.

Gardez à l'esprit que pour installer des extensions ou des modèles après l'installation réelle de Joomla! vous devrez peut-être augmenter à nouveau les permissions par défaut sur les répertoires appropriés juste pendant la période d'installation, vous pourrez ensuite les diminuer à nouveau après l'installation de l'add-on.

Si vous décidez d'utiliser le *caching*, le répertoire de cache devra être *inscriptible* par l'utilisateur du serveur Web pour lui permettre d'écrire ses fichiers temporaires.

## Corriger les permissions de manière récursive

Dans une fenêtre de terminal, en partant de la racine du site Joomla, utilisez les commandes suivantes pour définir les permissions des fichiers et des dossiers aux valeurs par défaut de Joomla.

```bash
find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;
```

Remarque : La commande `find` suppose qu'elle doit commencer depuis le répertoire actuel. Pour être sûr, allez dans votre répertoire public_html et spécifiez un chemin comme le premier argument. Certains shells, comme bash sur Apple OS X, doivent avoir un chemin spécifié dans la commande `find`.

Testez toutes les extensions tierces après avoir modifié les permissions.

*Traduit par openai.com*

