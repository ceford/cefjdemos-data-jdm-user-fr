<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Laragon pour Windows",
    "description": "",
    "author": ""
}
-->

## Configurer un environnement Joomla local à l’aide de Laragon

Laragon est un outil Windows léger qui gère Apache, MySQL et
PHP dans une installation simple. Aucun fichier de configuration, aucune
configuration manuelle : téléchargez, exécutez et commencez à créer/tester
Joomla. Consultez cet article dans le magazine de la communauté Joomla : [Laragon : le serveur AMP hautes performances et sans effort
pour Windows](https://magazine.joomla.org/all-issues/october-2025/laragon-the-effortless,-high-performance-amp-server-for-windows).

Ce guide vous permet de partir de zéro pour obtenir un site Joomla local
fonctionnel et couvre également une petite anomalie de l’interface dans la
dernière version, facile à corriger une fois que vous savez ce qui se passe.

### Téléchargement et installation de Laragon

Pour commencer, rendez-vous sur la [page de téléchargement officielle de
Laragon](https://laragon.org/download). Téléchargez la version complète de
Laragon (actuellement v8.6.1), car elle inclut tout ce dont vous avez besoin
(comme Apache, MySQL et les dernières versions de PHP) dès le départ.
Vous pouvez également télécharger directement l’[installateur](https://github.com/leokhoa/laragon/releases/download/8.6.1/laragon-wamp.exe).

Une fois le fichier `.exe` téléchargé, double-cliquez dessus pour commencer
l’installation.

**Remarque concernant Windows Defender :** Laragon étant un outil de développement
puissant, Windows Defender SmartScreen peut empêcher son démarrage et afficher
un écran d’avertissement bleu. C’est normal : cliquez simplement sur **Plus
d’informations**, puis cliquez sur le bouton **Exécuter quand même** qui apparaît
en bas.

![avertissement de protection de l’installation de laragon](../../../en/images/hosting-local/laragon-setup-windows/01-laragon-setup-windows-protected-warning.png)

Parcourez l’assistant d’installation. Les paramètres par défaut conviennent parfaitement,
mais gardez un œil sur ces deux détails importants :

1.  **Emplacement de destination :** Laissez le dossier d’installation sur
    `C:\laragon`. Installer le logiciel dans un dossier profondément imbriqué dans `Program Files` ou
    `Documents` peut parfois entraîner des problèmes d’autorisations par la suite.
2.  **Options d’installation :** Assurez-vous que la case **Hôtes virtuels
    automatiques** est cochée. Il s’agit de la fonctionnalité qui attribue à votre site Joomla local une adresse
    claire (comme `http://myjoomla.test`) au lieu d’une adresse IP brute.

![options d’installation de Laragon](../../../en/images/hosting-local/laragon-setup-windows/02-laragon-setup-options.jpg)

Une fois l’installation terminée, redémarrez votre ordinateur. (l’assistant
d’installation vous proposera de faire de même)

### Démarrer votre serveur et autoriser le pare-feu

Ouvrez Laragon depuis votre menu Démarrer et cliquez sur le bouton **Start All**.

Comme il s’agit de la première fois que vous exécutez un serveur local, Windows doit
vérifier qu’il est sûr. Des invites du Pare-feu Windows Defender
apparaîtront pour demander un accès réseau pour des services tels que **Apache HTTP
Server**, **MySQL** et **Mailpit**.

- Cliquez simplement sur **Autoriser l’accès** dans chacune de ces invites.

Une fois l’accès autorisé, Laragon démarrera votre environnement local. Vous saurez
qu’il fonctionne lorsque les numéros de port d’Apache et de MySQL apparaîtront dans
la fenêtre de Laragon.

### Le problème « Déjà en cours d’exécution » (et comment le résoudre)

Lorsque vous avez terminé votre travail, vous pouvez cliquer sur « Tout arrêter » pour désactiver Apache
et MySQL, puis cliquer sur le « X » dans le coin supérieur droit pour fermer la
fenêtre de Laragon.

Voici le problème : cliquer sur le « X » n’arrête pas complètement
Laragon. Il continue de fonctionner discrètement en arrière-plan. Si vous essayez d’ouvrir
à nouveau l’application Laragon depuis votre menu Démarrer ou votre bureau, vous verrez un avertissement
jaune dans le coin inférieur droit de votre écran indiquant :
**« Laragon est déjà en cours d’exécution ! »**

![avis de configuration de Laragon indiquant qu’il est déjà en cours d’exécution](../../../en/images/hosting-local/laragon-setup-windows/03-laragon-setup-already-running-notice.png)

**Le piège :** si vous cliquez sur le « X » de ce petit avertissement jaune pour le fermer, la fenêtre principale de Laragon disparaîtra également, vous empêchant complètement d’accéder au panneau de contrôle. (Remarque : il peut également arriver qu’une fenêtre contextuelle concernant la licence apparaisse et provoque le gel de l’interface de manière similaire).

**La solution :** si votre interface disparaît ou se fige, il vous suffit de
forcez la fermeture du processus en arrière-plan et redémarrez depuis le début. C'est très simple :

1.  Appuyez sur `Ctrl + Shift + Esc` sur votre clavier pour ouvrir le **Gestionnaire des tâches Windows**.
2.  Recherchez **Laragon** dans la liste des processus en cours d’exécution.
3.  Faites un clic droit dessus et sélectionnez **Terminer la tâche**.

C’est tout ! Vous avez arrêté en toute sécurité le processus en arrière-plan bloqué. Vous pouvez maintenant ouvrir Laragon depuis votre menu Démarrer, et il se chargera parfaitement, vous permettant de cliquer sur « Start All » sans aucune erreur.

### Gestion des fenêtres contextuelles de licence (les écrans de rappel)

Laragon est gratuit pour le développement et les tests non commerciaux,
sans qu'il soit nécessaire d'acheter une licence. Cependant, après avoir
utilisé l'application pendant un certain temps, vous rencontrerez
probablement une invite « Clé de licence » vous encourageant à soutenir
le projet.

Comme vous utilisez la version gratuite, vous pouvez simplement fermer
ces écrans, mais voici la séquence à laquelle vous attendre :

1.  La fenêtre principale **Clé de licence** apparaîtra par-dessus votre
    interface Laragon. Cliquez sur le texte **Fermer** ou sur le « X ».<br>
    ![fenêtre de clé de licence de la configuration de laragon](../../../en/images/hosting-local/laragon-setup-windows/04-laragon-setup-license-key-window.png)

2.  Immédiatement après l'avoir fermée, une seconde fenêtre contextuelle
    **Avertissement** apparaîtra, vous rappelant que Laragon fonctionne
    sans licence. Cliquez sur **OK** ou sur le « X ».<br>
    ![avertissement d'absence de licence de la configuration de laragon](../../../en/images/hosting-local/laragon-setup-windows/05-laragon-setup-no-license-warning.png)

3.  Une fois ce second avertissement fermé, Laragon peut automatiquement s'ouvrir

    votre navigateur web et vous rediriger vers `https://laragon.org/key`. Vous
    pouvez simplement fermer cet onglet du navigateur.
4.  Lorsque vous revenez à l’interface de Laragon et cliquez sur **Start All** pour
    redémarrer votre serveur, vous devrez peut-être fermer exactement ces deux fenêtres
    contextuelles une nouvelle fois.

Après les avoir fermées une deuxième fois, les fenêtres contextuelles disparaîtront et
vous serez entièrement libre d’utiliser Laragon !

*(Remarque : Si, à un moment quelconque pendant l’affichage de ces fenêtres contextuelles, votre interface Laragon se fige et devient inutilisable, souvenez-vous simplement de l’astuce `Ctrl + Shift + Esc`
du Gestionnaire des tâches mentionnée à l’étape précédente pour mettre fin au processus
en arrière-plan et repartir de zéro.)*

### Créer une base de données pour Joomla

Avant d’installer Joomla, vous avez besoin d’une base de données vide pour y stocker ses données.
Laragon inclut un gestionnaire de bases de données intégré appelé HeidiSQL, vous disposez donc
déjà de tout ce dont vous avez besoin.

1.  Assurez-vous que les services Laragon sont en cours d’exécution (cliquez sur **Start All**).
2.  Cliquez sur le bouton **Database** dans l’interface principale de Laragon.
3.  Une fenêtre Session Manager s’ouvrira. Laragon renseigne automatiquement
    les identifiants locaux par défaut pour vous (Utilisateur : `root`, Mot de passe :
    *\[laissez vide\]*).
4.  Cliquez sur le bouton **Open** en bas de la fenêtre.<br>    
    **Dépannage : erreur « Access denied for user 'root'@'localhost' » :
    ** Si vous cliquez sur le bouton **Open** et obtenez immédiatement une erreur d’échec
    de connexion, ne vous inquiétez pas ! Cela signifie généralement qu’un autre programme
    MySQL (comme XAMPP ou MySQL Workbench) s’exécute en arrière-plan, ce qui bloque l’accès
    de Laragon au port de la base de données (port 3306).<br>
    ![dépannage de l'accès à la configuration de Laragon](../../../en/images/hosting-local/laragon-setup-windows/06-laragon-setup-troubleshooting.jpg)

    **La solution :**
    1.  Appuyez sur la touche Windows, saisissez **Services**, puis appuyez sur Entrée.
    2.  Faites défiler la liste vers le bas pour trouver **MySQL**, **MySQL80** ou **MariaDB**.
    3.  Faites un clic droit sur le service en cours d'exécution et sélectionnez **Arrêter**.
    4.  Retournez dans Laragon, cliquez sur **Tout arrêter**, puis sur **Tout démarrer**, et
        essayez à nouveau de cliquer sur **Ouvrir** dans le gestionnaire de sessions. Il devrait
        se connecter sans afficher d'erreur.
5.  Une fois connecté et dans le gestionnaire de bases de données HeidiSQL, regardez la colonne
    de gauche. Faites un clic droit sur le nom du serveur (généralement intitulé `Laragon.MySQL`
    ou `127.0.0.1`).
6.  Passez la souris sur **Créer**, puis sélectionnez **Base de données**.
7.  Une petite fenêtre s'affichera. Saisissez un nom simple pour votre base de données dans le
    champ « Nom » (par exemple : `joomla_dev`). Vous pouvez laisser la liste déroulante
    « Interclassement » sur son réglage par défaut.
8.  Cliquez sur **OK**.
Votre nouvelle base de données apparaît dans la liste à gauche. C'est
tout ! Vous pouvez maintenant fermer complètement la fenêtre du gestionnaire de bases de données.

### Obtenir vos fichiers Joomla

Maintenant que votre serveur et votre base de données sont prêts, il est temps de mettre les
fichiers Joomla en place. La manière de procéder dépend entièrement de ce que vous souhaitez
accomplir avec cette configuration locale :

**Méthode 1 : Pour créer un site Web standard** Si vous souhaitez simplement créer
un site Web ou tester des extensions, vous avez besoin de la version stable standard.

- Rendez-vous sur la [page officielle de téléchargement de Joomla](https://downloads.joomla.org) 
  et téléchargez le fichier `.zip` du dernier **Package complet**.

**Méthode 2 : Pour tester les PR de la communauté (test de correctifs)** Si votre objectif est
d’aider la communauté en testant des correctifs et des Pull Requests, vous avez besoin d’un
package précompilé contenant le code le plus récent.

- **La version Nightly Build :** Téléchargez le dernier fichier `.zip` Nightly Build depuis
  [Nightly Builds](https://developer.joomla.org/nightly-builds.html).
  Ces versions sont générées chaque nuit et sont parfaites pour être utilisées avec le composant Joomla Patch Tester.
- **Le package précompilé de la PR :** Sinon, si vous testez une PR
  spécifique sur GitHub, faites défiler la page de la PR jusqu’en bas, cliquez
  sur **Show all checks**, puis recherchez le lien **Download Prebuilt packages**.
  ![lien vers le package précompilé de configuration de Laragon](../../../en/images/hosting-local/laragon-setup-windows/07-laragon-setup-prebuilt-package-link.png)

**Méthode 3 : Pour contribuer au code principal** Si vous prévoyez d’écrire du code et
de soumettre vos propres Pull Requests, vous avez besoin du code source brut et non compilé.

- Clonez directement le [dépôt GitHub de Joomla CMS](https://github.com/joomla/joomla-cms)
  dans votre environnement Laragon à l’aide de Git.
- *Important :* Un clone brut depuis GitHub ne fonctionnera pas immédiatement : vous devez
  ouvrir le terminal de Laragon et exécuter `composer install` et `npm ci` dans votre
  dossier afin de compiler les dépendances PHP et les ressources CSS/JS. (Comme
  vous avez installé la version complète de Laragon, Composer et NPM sont
  déjà installés sur votre système).

### **Placer les fichiers dans Laragon :**

Quelle que soit la méthode choisie, la procédure pour faire fonctionner les fichiers dans Laragon
est exactement la même :

1.  Ouvrez l’interface de Laragon et cliquez sur le bouton **Root**. Cela
    ouvre automatiquement le dossier `C:\laragon\www` sur votre ordinateur.
2.  Dans ce dossier `www`, créez un nouveau dossier pour votre projet. Choisissez
    un nom de dossier simple, en minuscules et sans espaces (par exemple :
    `joomla_dev` ou `joomla_pr_test`).
3.  Placez vos fichiers Joomla dans ce nouveau dossier. (Si vous avez téléchargé un
    fichier `.zip` avec la méthode 1 ou 2, extrayez tout le contenu directement dans ce
    dossier. Si vous utilisez Git avec la méthode 3, clonez le dépôt dans ce dossier).
4.  Comme vous avez activé les « hôtes virtuels automatiques » lors de l’installation,
    Laragon utilise automatiquement le nom de votre dossier pour créer votre adresse web locale. Ainsi, un
    dossier nommé `joomla_dev` devient accessible dans votre navigateur à l’adresse `http://joomla_dev.test`.
    <br>
    **Astuce : gardez vos environnements propres :** Il est recommandé de créer
    des dossiers différents pour les différentes versions de Joomla ou pour des tests de PR spécifiques
    (par exemple, un dossier nommé `joomla5_stable` et un autre nommé
    `joomla4_dev`). Laragon les exécutera volontiers tous côte à côte avec
    leurs propres URL `.test` propres, empêchant votre code et vos bases de données
    de se mélanger !
    <br>
    ![dossiers de projets de configuration de Laragon](../../../en/images/hosting-local/laragon-setup-windows/08-laragon-setup-project-folders.png)

## Exécution du programme d’installation de Joomla

Vous disposez de votre base de données, et vos fichiers Joomla se trouvent dans leur nouveau
dossier (par exemple, `C:\laragon\www\joomla_dev`). Il est maintenant temps
d’installer réellement Joomla !

**Étape cruciale : rechargez Apache !** Si Laragon était déjà en cours d’exécution lorsque
vous avez créé votre nouveau dossier de projet, Laragon ne sait pas encore que ce dossier
existe.

- Ouvrez l’interface de Laragon.

- Cliquez sur **« Reload »** en haut à droite. *(Cela force Laragon à analyser le
  dossier `www` et à générer la nouvelle adresse `http://joomla_dev.test`).*

**Terminer la configuration :**

1. Ouvrez votre navigateur web et saisissez l’URL générée automatiquement pour votre projet
   (par ex. `http://joomla_dev.test`).
2. La page du programme d’installation web de Joomla devrait s’afficher immédiatement.
3. Choisissez votre langue et saisissez un nom pour votre site Joomla.
4. Configurez votre compte de super utilisateur (n’oubliez pas ces identifiants, vous
   en aurez besoin pour accéder au tableau de bord d’administration de Joomla !).
5.  Sur l’écran **Configuration de la base de données**, saisissez les identifiants de la
    base de données Laragon que vous avez créée précédemment :
    - **Type de base de données :** `MySQLi` (par défaut)
    - **Nom d’hôte :** `localhost`
    - **Nom d’utilisateur :** `root`
    - **Mot de passe :** *\[Laissez ce champ complètement vide\]*
    - **Nom de la base de données :** Le nom exact que vous avez saisi précédemment dans HeidiSQL
      (par exemple, `joomla_dev`).
    ![paramètres de la base de données de l’installation de Joomla avec Laragon](../../../en/images/hosting-local/laragon-setup-windows/09-laragon-setup-joomla-installer-database.png)

6.  Cliquez sur **Installer Joomla**.

Une fois la barre de progression terminée, un message de réussite s’affiche. Vous pouvez
maintenant cliquer sur **Ouvrir le site** pour afficher votre site web local en ligne, ou sur **Ouvrir
l’administration** pour vous connecter à l’interface d’administration de Joomla.

C’est tout : votre site Joomla local est en ligne et prêt à l’emploi.

*Traduit par openai.com*