<!-- Filename: Visual_Studio_Code_Primer / Display title: Introduction à Visual Studio Code  -->

## VS Code - Un IDE Gratuit Populaire

De Wikipedia :

> Visual Studio Code, également communément appelé VS Code, est un
> éditeur de code source conçu par Microsoft pour Windows, Linux et macOS.
> Ses fonctionnalités incluent la prise en charge du débogage, la coloration
> syntaxique, l’auto-complétion intelligente, les extraits de code, le
> refactoring de code et l’intégration de Git. Les utilisateurs peuvent
> modifier le thème, les raccourcis clavier, les préférences, et installer
> des extensions pour ajouter des fonctionnalités supplémentaires.

## Installation

Le site de VS Code
a une page par défaut avec une liste déroulante pour chaque plateforme prise en charge. Il y a de fortes chances que votre plateforme soit pré-sélectionnée. Téléchargez et installez, et vous êtes prêt à partir.

### Prise en main

La page *Get Started* de VS Code contient quelques éléments de démarrage (*Start*), une liste d'éléments récents (*Recent*) et une courte liste de guides pratiques (*Walkthroughs*). Si vous êtes complètement nouveau sur VS Code, il est recommandé de les consulter. Ils ne prennent que quelques minutes.

La documentation de VS Code est disponible dans le menu *Aide / Documentation*. Les [Vidéos Introductives](https://code.visualstudio.com/docs/getstarted/introvideos) valent vraiment le détour. Chacune dure de 2 à 6 minutes et offre une excellente introduction aux fonctionnalités de VS Code.

La documentation officielle est l'endroit où aller si vous souhaitez rechercher des informations spécifiques.

### Extensions VS Code

VS Code peut être utilisé pour tout type de texte, y compris une large gamme de langages de programmation. Il fonctionne avec JavaScript sans ajouter d'extensions. D'autres langages sont détectés par le contexte, donc si vous commencez à créer et enregistrer du code PHP, vous serez probablement invité à installer un pack de support PHP.

Cliquez sur l'icône *Extensions* dans la *Barre d'Activité* à gauche pour voir ce que vous avez installé et ce qui est recommandé. Vous aurez besoin de l'extension de débogage PHP !

### La disposition de l'écran VS Code

Quelques termes utilisés dans les instructions suivantes :

- **Barre d'Activité** la barre étroite à gauche de l'écran. Sélectionnez une icône pour ouvrir ou fermer la barre latérale principale.
- **Barre Latérale Principale** lorsqu'elle est ouverte, elle affiche les détails de l'activité sélectionnée.
- **Barre d'État** en bas de l'écran. Elle montre ce qui se passe.
- **Panneau** une zone sous les éditeurs de texte pour afficher d'autres informations.

Sélectionnez une icône de disposition en haut à droite pour ouvrir ou fermer l'un de ces éléments.

## Création d'une Extension Joomla

Pour créer une extension, votre objectif est de créer un fichier zip que vous pouvez installer sur un site Joomla en cours de fonctionnement. Ainsi, vous avez besoin d'un dossier pour contenir votre code. Celui-ci devrait être situé dans votre espace de fichiers personnel sur votre ordinateur portable ou de bureau utilisé pour le développement local. Il ne devrait pas être dans l'arborescence de votre site web. Par exemple, vous pourriez utiliser *~/jextensions* pour contenir des sous-dossiers pour différentes extensions. J'utilise *~/git* car c'est court et facile à orthographier bien que potentiellement déroutant puisque chaque sous-dossier utilise un dépôt git séparé.

### Code Exemples

Si vous souhaitez disposer de code d'exemple sur lequel travailler, il existe une extension disponible sur GitHub nommée *mod_debugme*. Comme le nom l'indique, il s'agit d'un module avec quelques bugs. En plus du code du module, il y a un fichier *build.xml* qui montre une façon d'automatiser la construction pour les tests et la création d'un fichier zip.

Le module est conçu pour afficher les trois prochains événements (anniversaires) par défaut provenant d'une liste stockée dans une table de base de données. Vous pourriez imaginer cela étant utilisé dans un site de bureau ou familial dans l'attente d'un gâteau.

Il peut être préférable de commencer en utilisant des commandes git depuis la ligne de commande. Commencez par créer un dossier pour votre code puis clonez le dépôt distant :
```sh
    mkdir ~/git
    cd ~/git
    git clone https://github.com/ceford/j4xdemos-mod-debugme
```
La réponse devrait prendre seulement quelques secondes :
```sh
    Clonage dans 'j4xdemos-mod-debugme'...
    remote: Enumération des objets: 23, fait.
    remote: Comptage des objets: 100% (23/23), fait.
    remote: Compression des objets: 100% (16/16), fait.
    remote: Total 23 (delta 3), réutilisé 23 (delta 3), pack-réutilisé 0
    Décompression des objets: 100% (23/23), fait.
```
Vous devriez prendre un moment pour examiner le contenu du dossier :
```sh
    cd j4xdemos-mod-debugme
    ls -al
    total 16
    drwxr-xr-x   6 ceford  staff   192  2 Sep 17:48 .
    drwxr-xr-x   3 ceford  staff    96  2 Sep 17:48 ..
    drwxr-xr-x  12 ceford  staff   384  2 Sep 17:48 .git
    -rw-r--r--   1 ceford  staff  1402  2 Sep 17:48 README.md
    -rw-r--r--   1 ceford  staff   927  2 Sep 17:48 build.xml
    drwxr-xr-x   8 ceford  staff   256  2 Sep 17:48 mod_debugme
```
Le dossier *.git* contient des informations sur le dépôt. Le fichier *README.md* est un document markdown qui décrit ce dépôt. Le fichier *build.xml* est utilisé pour construire l'extension avec un outil externe, Phing - décrit plus tard. Le dossier *mod_debugme* contient le code de l'extension.

### Installer dans Joomla

Compressez le dossier de l'extension pour créer un fichier zip installable :
```sh
    zip -r mod_debugme.zip mod_debugme
```
Vous pouvez maintenant installer le fichier zip sur le site Joomla que vous utilisez pour les tests. Après l'installation, vous devez créer un module de site et l'assigner à une position de module. Comme c'est un module défectueux, vous pourriez l'assigner à une position sur *Toutes les pages* pendant que vous travaillez dessus ; ou vous pourriez l'assigner à une position sur une seule page ; ou vous pouvez le positionner dans un article qui a son propre élément de menu.

Après l'installation, supprimez le fichier zip.

### Activer le Mode Débogage

Dans la Configuration Globale de Joomla, réglez *Système de Débogage* sur *Oui* et *Rapport d'Erreur* sur *Maximum*.

Lorsque vous ouvrez une page contenant le module bogué, vous verrez une trace de pile indiquant où une erreur a été déclenchée.

![trace de pile vscode](../../../en/images/test-installations/vscode-primer-stack-trace.png)

Parfois, l'erreur de codage se trouve sur la première ligne de la trace de pile. Autrement, si l'erreur est déclenchée dans le code de la bibliothèque, par exemple en passant des données invalides à une fonction de base de données, l'erreur de codage peut se trouver plus bas dans la liste des appels de fonction.

## Ouvrir le dossier des extensions dans VS Code

Dans VS Code, utilisez le menu Fichier / Ouvrir un dossier pour localiser et ouvrir le dossier contenant votre copie locale du code de l'extension *mod_debugme*. Vous devriez voir quelque chose de similaire à ce qui suit :

![vue du dossier vscode](../../../en/images/test-installations/vscode-primer-screen.png)

Vous pouvez peut-être diagnostiquer le problème simplement en lisant le code. Dans le cas de l'erreur *Class "DebugHelper" not found*, vous verrez qu'une déclaration *use* a été commentée quelques lignes plus haut. Oublier d'insérer une déclaration *use* est une erreur courante lors du développement initial !

Corrigez ce problème puis compressez et installez à nouveau le module. Cette étape peut devenir un peu fastidieuse lorsque vous avez plusieurs problèmes. C'est là que les outils de construction deviennent utiles.

## Phing

Phing est un outil en ligne de commande, disponible sur toutes les plateformes, utilisé pour construire des paquets logiciels en utilisant des instructions stockées dans un fichier xml, nommé build.xml par défaut. Pour travailler avec le code d'une extension, il peut être utilisé pour faire deux choses :

- copier les fichiers modifiés de votre dossier source d'extension vers les emplacements corrects dans le dossier de votre site web.
- générer un nouveau fichier zip pour de nouvelles installations.

Téléchargez et installez Phing. D'autres outils de construction sont disponibles ! Vous pourriez installer Phing dans votre propre dossier bin ou dans un dossier bin système. Vous devez noter le chemin vers votre code Phing. Dans cet exemple, il est *~/bin/phing-latest.phar*. Vous pouvez l'essayer depuis la ligne de commande après avoir changé dans le dossier contenant votre code d'extension :
```sh
    cd ~/git/j4xdemos-mod-debugme
    php ~/bin/phing-latest.phar
```
Réponse :
```sh
    Buildfile: /Users/ceford/git/j4xdemos-mod-debugme/build.xml

    mod_debugme > main:
          ... Tous les fichiers copiés seront mentionnés ici
          [zip] Construction du zip : /Users/ceford/zips/mod_debugme.zip

    BUILD FINISHED

    Total time: 0.0863 seconds
```

## Tâches VS Code

Pour exécuter Phing à partir de VS Code, vous devez créer un fichier *tasks.json* dans le dossier *.vscode* à la racine du dossier *j4xdemos-mod-debugme*. Si ce dernier n'existe pas, créez-le d'abord. Ensuite, créez le fichier *tasks.json* et entrez le code suivant :

```json
    {
        // Voir https://go.microsoft.com/fwlink/?LinkId=733558
        // pour la documentation sur le format du fichier tasks.json
        "version": "2.0.0",
        "tasks": [
          {
            "label": "Build mod_debugme",
            "type": "shell",
            "command": "php ~/bin/phing-latest.phar",
            "windows": {
              "command": "php ~/bin/phing-latest.phar"
            },
            "group": "build",
            "presentation": {
              "reveal": "always",
              "panel": "shared"
            }
          }
        ]
    }
```

Les utilisateurs de Windows doivent corriger la commande spécifique à Windows. Vous pouvez maintenant construire l'extension en utilisant le menu *Terminal / Exécuter la tâche de construction*. Le résultat de la commande devrait apparaître dans le panneau du Terminal sous la zone d'édition.

```sh
      *  Exécution de la tâche : php ~/bin/phing-latest.phar

    Buildfile: /Users/ceford/git/gitdemo/j4xdemos-mod-debugme/build.xml

    mod_debugme > main:

          [zip] Rien à faire : /Users/ceford/zips/mod_debugme.zip est à jour.

    CONSTRUCTION TERMINÉE

    Temps total : 0.1031 secondes

     *  Le terminal sera réutilisé par les tâches, appuyez sur une touche pour le fermer.
```

Il peut y avoir des messages d'erreur incompréhensibles. La cause la plus probable est des chemins d'accès invalides aux dossiers dans le fichier *build.xml* ou un dossier qui n'a pas été créé. Juste un autre type de problème à déboguer !

## Débogage

Vous devriez être capable de corriger le premier bug par inspection du code. Les problèmes plus compliqués nécessitent de parcourir le code avec le débogueur. Cela vous permet d'inspecter les variables pour voir si elles contiennent les valeurs que vous attendez, par exemple lors du passage d'arguments à des fonctions de bibliothèque.

### Paramètres *php.ini*

Pour configurer le débogage avec Xdebug, vous devez faire quelques entrées en haut de votre fichier *php.ini*.
```ini
    zend_extension="xdebug.so"
    xdebug.mode="debug"
    xdebug.client_port=9003
    xdebug.start_with_request = yes
```
Après avoir enregistré les modifications, redémarrez votre serveur Apache.

### Ajouter une fenêtre de site web

Votre dossier d'extension contient seulement quelques fichiers, les ***sources*** des fichiers installés sur votre site web. Le débogage en temps réel implique la mise en place de points d'arrêt dans vos fichiers de ***site***, vous devez donc accéder à ces fichiers. Vous pouvez utiliser le menu *Fichier / Ajouter un dossier à l'espace de travail...* pour ajouter le dossier du site à votre espace de travail. Cependant, il est très probable que vous finissiez par apporter des modifications aux fichiers du site au lieu des fichiers source. Il est donc probablement préférable d'ouvrir une fenêtre VS Code séparée pour le débogage.

- **Ouvrir une nouvelle fenêtre :** Dans le menu VS Code, sélectionnez *Fichier / Nouvelle fenêtre* et sélectionnez le dossier contenant votre site Joomla.
- **Ouvrir un dossier :** Dans la fenêtre qui vient d'être ouverte, sélectionnez *Fichier / Ouvrir un dossier...* dans le menu VS Code. Trouvez votre dossier de site web et sélectionnez-le. Vous devriez voir une liste de tous les fichiers de votre site Joomla dans la barre latérale principale.

### Configuration de lancement

Pour que le débogage fonctionne réellement dans VS Code, vous avez besoin d'une configuration de lancement. À la racine de votre site web, créez un dossier nommé *.vscode* (notez le point de départ) contenant un fichier nommé *launch.json* avec le contenu suivant :
```json
    {
        "configurations": [
            {
                "name": "Listen for XDebug",
                "type": "php",
                "request": "launch",
                "hostname": "0.0.0.0",
                "port": 9003,
                "stopOnEntry": true,
                "pathMappings": {
                    "/Users/ceford/Sites/j421rc2": "${workspaceFolder}"
                }
            }
        ]
    }
```
N'oubliez pas de remplacer l'élément pathMappings dans cet exemple par les pathMappings réels de votre propre site. L'élément stopOnEntry suspendra l'exécution sur la toute première ligne de code PHP exécutée.

### Déboguer *mod_debugme*

Maintenant, vous êtes prêt à trouver et à corriger les bugs dans le module installé.

- **Trouver le code du module :** Trouvez le premier bug à la ligne 16 de JROOT/modules/mod_debugme/mod_debugme.php.
- **Définir un point d'arrêt :** Cliquez dans l'espace à gauche du numéro 16. Un point rouge pâle apparaîtra lorsque vous survolez et deviendra rouge vif après avoir cliqué pour indiquer qu'un point d'arrêt a été défini.
- **Démarrer le débogage :** Dans le menu VS Code, sélectionnez *Exécuter / Démarrer le débogage*. Dans votre navigateur, rechargez votre site. Votre fenêtre VS Code devrait réapparaître avec le code arrêté à la première ligne du fichier *index.php* du site. En haut de l'écran se trouvent quelques icônes pour contrôler le processus de débogage. Elles devraient être explicites. Sinon, consultez la documentation d'aide de VS Code.
- **Continuer :** Sélectionnez le bouton de continuation - le code s'exécutera jusqu'à votre premier point d'arrêt. Examinez le code pour voir quel est le problème.
- **Survoler :** Si vous survolez un variable à laquelle une valeur a été assignée, une petite bulle d'information apparaîtra résumant les attributs de cette variable. Il n'y a pas de bulle d'information pour les variables qui n'ont pas reçu de valeurs.
- **Variables :** La colonne de gauche contient plus d'informations sur l'état du code au moment du point d'arrêt. Il y en a trop pour les couvrir ici. Explorez-les au besoin !
- **Arrêter le débogage :** Il est probablement préférable de sélectionner l'icône Continuer, sinon la page web est livrée vide. Sinon, vous pouvez utiliser le bouton Arrêter ou le menu Exécuter / Arrêter le débogage.

### Corriger un bug

**N'oubliez pas :** Ne corrigez pas le bug dans le code du site web ! Corrigez-le dans le code source !

Corrigez le code source puis utilisez *Terminal / Exécuter la tâche de construction...*.

Redémarrez le débogage.

### Conseils

Quelques problèmes pas si évidents :

- Vous corrigez le premier bug mais il se bloque toujours sur cette ligne. Regardez dans mod_debugme.xml pour voir où la source des classes avec espaces de noms est définie. Une fois corrigé dans la source, vous devez réinstaller le fichier zip ou supprimer *administrator/cache/autoload_psr4.php*. Lorsqu'il est absent, Joomla reconstruit ce fichier à partir des fichiers manifeste. Mais s'il a une entrée incorrecte ou manquante, il ne se corrige pas tant que l'extension n'est pas réinstallée.
- Parfois, vous devez définir un point d'arrêt quelques lignes avant la ligne où l'erreur se produit, surtout si vous souhaitez vérifier les valeurs passées aux appels de fonction.
- La table *xxx.yyy\\debugme* n'existe pas. Ah oui, le code pour créer une table à l'installation et la supprimer à la désinstallation n'a jamais été créé. Vous devrez exécuter une requête SQL dans phpMyAdmin en utilisant le contenu du fichier *mod\\debugme.sql*. N'oubliez pas de changer *\#\\* dans les noms de table pour votre préfixe de base de données. Et quand ça échoue toujours, vérifiez le nom de la table dans le code.

## Capture d'écran

Lorsque tout est réparé, voici ce que vous pourriez voir :

![vue du module corrigé dans vscode](../../../en/images/test-installations/vscode-primer-debugme-fixed.png)

Jours de fête ?  

## Références

Depuis la documentation Joomla ! : [Visual Studio Code](https://docs.joomla.org/Visual_Studio_Code) couvre également la configuration d'autres outils, par exemple CodeSniffer et PHPUnit.

*Traduit par openai.com*

