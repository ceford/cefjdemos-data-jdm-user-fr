<!-- Filename: Installing_Joomla!_using_BitNami_Joomla!_stack / Display title: Installation de Bitnami  -->

## Préface

**REMARQUE :** La pile BitNami Joomla! n'existe plus en tant qu'installateur autonome. Elle est désormais disponible sous forme de : 1) Instance basée sur le cloud, 2) Dans un conteneur, soit Kubernetes soit Docker, ou 3) Une machine virtuelle. La machine virtuelle fonctionnera sur votre système d'exploitation dans un hyperviseur tel que Virtual Box ou VMware Player. Elle est toujours fournie avec toutes les dépendances requises comme dans l'installateur autonome.

L'option 1 ci-dessous ne s'applique plus. De plus, dans l'option 2, la pile BitNami Lamp Stack, plus bas, est livrée dans le cloud ou sur une machine virtuelle. Dans tous les cas, Bitnami facilite une installation locale performante de Joomla! à la fois facile et complète.

Vous pouvez télécharger la dernière version du package Bitnami pour Joomla! pour Windows, Linux et Mac sur <a href="http://bitnami.org/stack/joomla" rel="nofollow noreferrer noopener">http://bitnami.org/stack/joomla</a>.

**Révision nécessaire !**

La pile BitNami Joomla! est un installateur tout-en-un qui facilite l'installation de Joomla sur votre ordinateur. Elle est gratuite, facile à utiliser et autonome. Cela signifie qu'elle regroupe et configure automatiquement chaque logiciel (dépendance) nécessaire pour exécuter Joomla à des fins de développement ou de production, y compris le serveur HTTP Apache, MySQL et PHP.

## Option 1 : Pile Joomla! (Recommandé)

Cette méthode suppose que vous avez déjà un environnement **AMP** (serveur HTTP Apache, MySQL et PHP) installé sur (**W**indows/**L**inux/**M**ac).

### Installation de la pile Joomla!

Quel que soit le système d'exploitation que vous utilisez (Windows / Linux / Mac), le processus d'installation est le même.

Téléchargez la dernière version de la pile Joomla! depuis le <a href="http://bitnami.org/stack/joomla" rel="nofollow noreferrer noopener">site BitNami</a>.

Trouvez l'installateur que vous venez de télécharger (le nom du fichier sera similaire à bitnami-joomla-VERSION-linux-installer.run). Double-cliquez sur l'icône pour lancer l'installateur.

Si vous utilisez Linux, vous devrez d'abord donner des permissions d'exécution au fichier, en utilisant cette commande :

chmod +x /path/to/bitnami-joomla-VERSION-linux-installer.run

<img src="https://docs.joomla.org/images/a/a0/Joomla_welcome2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Configuration Joomla Bitnami lampstack" />

Cliquez sur "Next".

<img src="https://docs.joomla.org/images/5/5f/Joomla_components2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Composants Joomla Bitnami lampstack" />

Sélectionnez les composants que vous souhaitez installer. Si vous n'êtes pas sûr, laissez les composants par défaut cochés. Cliquez sur "Next" lorsque vous avez terminé.

<img src="https://docs.joomla.org/images/0/0a/Joomla_directory2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Répertoire d'installation Joomla Bitnami lampstack" />

Il vous sera demandé où vous souhaitez installer le programme. Indiquez l'emplacement où vous souhaitez installer la pile BitNami Joomla! et cliquez sur "Next" lorsque vous avez terminé.

<img src="https://docs.joomla.org/images/3/3c/Joomla_userdata2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Compte administrateur Joomla Bitnami lampstack" />

L'utilisateur et le mot de passe que vous fournissez ici seront utilisés pour créer le compte administrateur dans Joomla! Cliquez sur "Next" lorsque vous avez terminé.

<img src="https://docs.joomla.org/images/8/8b/Joomla_sitename2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Nom du site Joomla Bitnami lampstack" />

Tapez le nom que vous souhaitez utiliser pour votre site Joomla, puis cliquez sur "Next".

<img src="https://docs.joomla.org/images/d/dd/JoomlaReadytoinstall2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Prêt à installer Joomla Bitnami lampstack" />

L'installateur vous permet de configurer un compte email afin que Joomla! puisse envoyer des notifications par email. Cliquez sur "Next".

<img src="https://docs.joomla.org/images/9/9d/JoomlaCopyingfiles2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Copie des fichiers Joomla Bitnami lampstack" />

Patientez un moment pendant que l'installateur copie les fichiers et configure votre installation Joomla!

<img src="https://docs.joomla.org/images/e/ea/Joomlafinalscreen2.png" decoding="async" data-file-width="614" data-file-height="538" width="614" height="538" alt="Écran final Joomla Bitnami lampstack" />

Joomla! est maintenant configuré et prêt à être utilisé. Cliquez sur "Finish" pour lancer l'application.

<img src="https://docs.joomla.org/images/8/8d/JoomlaManager.png" decoding="async" data-file-width="784" data-file-height="586" width="784" height="586" alt="Gérer les serveurs Joomla Bitnami lampstack" />

Utiliser l'outil de gestion est simple pour démarrer/arrêter les serveurs Apache et MySQL.

<img src="https://docs.joomla.org/images/7/73/Joomlaapplicationscreen2.png" decoding="async" data-file-width="982" data-file-height="729" width="982" height="729" alt="Écran d'application Joomla" />

Vous pouvez facilement gérer la base de données Joomla! avec phpMyAdmin.

<img src="https://docs.joomla.org/images/f/f3/JoomlaphpMyAdmin.png" decoding="async" data-file-width="982" data-file-height="751" width="982" height="751" alt="Écran phpMyAdmin" />

## Option 2 : BitNami LAMPStack et Joomla!

### Qu'est-ce que BitNami LAMPStack ?

BitNami LAMPStack est un package gratuit et facile à installer qui regroupe chaque
élément logiciel (dépendance) nécessaire pour configurer un environnement LAMP (Apache, MySQL
et PHP pour Linux) fonctionnel à des fins de développement ou de production. Il est autonome, ne modifie pas
votre système et peut être désinstallé facilement. Vous pouvez télécharger la dernière
version de BitNami LAMPStack pour Linux sur 
<a href="http://bitnami.org/stack/lampstack"
rel="nofollow noreferrer noopener">http://bitnami.org/stack/lampstack</a>.
Une <a href="http://bitnami.org/stack/wampstack"
rel="nofollow noreferrer noopener">version Windows</a>
et une <a href="http://bitnami.org/stack/mampstack"
rel="nofollow noreferrer noopener">version OS X</a> sont également disponibles.

Quel que soit le système d'exploitation que vous utilisez (Windows / Linux / Mac), le processus
d'installation est le même.

### Installation de BitNami LAMPStack

Trouvez l'installateur que vous venez de télécharger sur le site Web de BitNami (le
nom de fichier sera similaire à
bitnami-lampstack-VERSION-linux-installer.run). Double-cliquez sur l'icône pour
lancer l'installateur.

<img src="https://docs.joomla.org/images/1/14/Lampstack_welcome.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Bitnami lampstack bienvenue" />

Cliquez sur "Suivant".

<img src="https://docs.joomla.org/images/7/78/Lampstack_directory.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Bitnami lampstack répertoire" />

Il vous demandera maintenant où vous souhaitez installer le programme. Sélectionnez l'emplacement sur votre machine et cliquez sur "Suivant" lorsque vous avez terminé.

<img src="https://docs.joomla.org/images/2/22/Lampstack_passwd.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Bitnami lampstack mot de passe" />

Tapez votre mot de passe root MySQL. Ce sera le mot de passe pour l'utilisateur "root"
pour la base de données.

<img src="https://docs.joomla.org/images/7/72/LampstackReadytoinstall.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Bitnami lampstack prêt à installer" />

L'installateur est maintenant prêt à commencer le processus d'installation. Cliquez sur "Suivant".

<img src="https://docs.joomla.org/images/1/19/LampstackCopyingfiles.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Bitnami lampstack copie de fichiers" />

Attendez un moment pendant que l'installateur copie les fichiers et configure votre
installation de LAMPStack.

<img src="https://docs.joomla.org/images/b/bc/Lampstackfinalscreen.png"
decoding="async" data-file-width="516" data-file-height="391"
width="516" height="391" alt="Bitnami lampstack écran final" />

BitNami LAMPStack est maintenant installé et prêt à être utilisé. Cliquez sur "Terminer" pour
lancer l'application.

### Installation manuelle de Joomla!

Suivez les instructions décrites dans l'article Installation de Joomla.

*Traduit par openai.com*

