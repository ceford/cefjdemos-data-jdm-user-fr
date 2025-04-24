<!-- Filename: J4.x:Installing_Joomla / Display title: Installation de Joomla -->

## Introduction

Installer Joomla! pour la première fois est très facile. Après avoir terminé les étapes préliminaires, configuré un environnement d'hébergement et créé une base de données, l'installateur web intégré de Joomla configurera votre nouveau site en quelques minutes. Les étapes précédentes :

### Configuration de l'hébergement

Si vous n'avez pas encore configuré un environnement d'hébergement, vous devez le faire maintenant, soit sur un service d'hébergement, soit sur votre ordinateur local.

De plus, certaines configurations PHP doivent être suffisantes pour que Joomla puisse s'installer. Les paramètres se trouvent généralement dans un fichier de configuration *php.ini* ou *user.ini* sur le serveur. Si vous êtes sur un hébergement mutualisé, parlez à votre service d'hébergement pour savoir comment modifier ces paramètres s'il est possible de le faire. Si vous travaillez sur un serveur local, par exemple avec XAMPP, ou un VPS ou un hébergement dédié, vous ne devriez pas être restreint par ces paramètres et pouvez les définir vous-même.

Les valeurs minimales pour le fichier *php.ini* sont indiquées ci-dessous :

- *memory_limit :* 256M
- *upload_max_filesize :* 64M
- *post_max_size :* 64M
- *max_execution_time :* 30

Il est possible de travailler avec des valeurs plus basses pour upload_max_filesize et post_max_size, mais les fichiers de plus grande taille échoueront à télécharger et causeront des problèmes imprévisibles.

### Configuration de la base de données

Si vous n'avez pas encore configuré une base de données, faites-le maintenant. Cela est couvert pour un service d'hébergement cPanel dans le didacticiel [cPanel Hosting](jdocmanual?article=user/hosting/cpanel-hosting). Il existe également un didacticiel *Création d'une base de données pour Joomla!* qui couvre les méthodes localhost et phpMyAdmin.

Vous devrez noter les informations de base sur la base de données nécessaires lors du démarrage de l'installation réelle de Joomla.

- Emplacement de la base de données, généralement *localhost* même sur un service d'hébergement.  
  Il peut s'agir du serveur d'un hôte spécifique tel que *`dbserver1.yourhost.com`*.
- Le nom de la base de données
- Le nom de l'utilisateur de la base de données
- Le mot de passe de l'utilisateur de la base de données

## Préparer l'installation

### Téléchargement et téléchargement des fichiers de package Joomla!

Téléchargez la version actuelle de Joomla ! depuis le lien sur la page [Télécharger Joomla](https://downloads.joomla.org/).

Déplacez le fichier zip du package d'installation de Joomla téléchargé sur le serveur.  
Pour un service d'hébergement, vous pouvez utiliser la fonction de téléchargement du gestionnaire de fichiers cPanel ou utiliser un client FTP pour transférer le fichier zip Joomla 5.x téléchargé sur votre serveur. Il existe plusieurs clients FTP disponibles.  
Voici une [Comparaison détaillée des logiciels clients FTP](https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software).  
En cas de doute, utilisez FileZilla.

Il est préférable de déplacer le paquet zip téléchargé vers votre serveur et de le décompresser là-bas plutôt que de le décompresser localement puis de déplacer l'arborescence de fichiers. Normalement, vous téléchargez vos fichiers web dans le dossier racine de votre service d'hébergement. Celui-ci est généralement nommé `public_html` mais d'autres variations incluent `htdocs` et cela dépend de la configuration de votre hébergeur. Pour les besoins de Joomla, vous pouvez charger les fichiers directement dans *public_html* ou un sous-dossier que vous avez créé à l'intérieur.

**Avertissement :** Si vous décompressez les fichiers sur votre propre ordinateur, puis les copiez sur votre serveur, assurez-vous de ne déplacer que les dossiers et fichiers contenus **à l'intérieur** du package Joomla. Si vous décompressez les dossiers et fichiers dans un dossier, par exemple appelé *`Joomla`* et que vous téléchargez ensuite ce dossier, votre site devra être accessible à *`votresite.com/Joomla`* au lieu de *`votresite.com`*. Vous pouvez renommer le sous-répertoire de Joomla à quelque chose de plus approprié pour le site, comme jblog, et vous pourriez trouver cela pratique. **Remarque :** les noms de répertoire doivent être en minuscules, sans espaces et utiliser des tirets plutôt que des soulignements pour séparer les mots.

Les fichiers de l'archive zip peuvent être extraits directement sur l'hôte à l'aide de divers outils en ligne de commande (par exemple, unzip), qui doivent être installés sur le serveur. Si votre service d'hébergement utilise l'outil d'administration cPanel, le bouton Extraire peut être appuyé dans le Gestionnaire de fichiers. En dehors de cela, l'outil gratuit tiers Akeeba Kickstart peut également être utilisé à cet effet. Les fichiers et répertoires décompressés seront placés dans le dossier actuel. L'extraction sur votre ordinateur local dépend de votre système d'exploitation. Essayez un clic droit et voyez s'il y a un menu d'extraction. Dans ce cas, votre système d'exploitation peut placer les fichiers dans un dossier portant le même nom que le fichier zip. Après extraction, vous pouvez supprimer le fichier zip et renommer le dossier d'extraction pour quelque chose de court et adapté à une utilisation dans une URL.

## Démarrer l'installation

Avec les exigences ci-dessus remplies, une base de données créée et les fichiers Joomla nécessaires en place, vous êtes prêt à installer Joomla. Lancez l'installateur web Joomla en ouvrant votre navigateur préféré et en naviguant vers le nom de domaine du site. Sur une installation d'hébergement, vous utiliserez *`https://www.yoursitename.com`*. Si vous installez Joomla localement, vous utiliserez *`http://localhost/`* et vous devriez voir l'écran d'installation.

![Joomla installer part 1, installation language and site name](../../../en/images/getting-started/installing-joomla-installer-1.png)

Joomla tentera d'identifier automatiquement le champ *Sélectionner la langue* à partir de la langue de votre navigateur. Vous pouvez le modifier si nécessaire.

Veuillez remplir les informations suivantes.

- **Nom du site** Le nom de votre site web — cela peut être modifié à tout moment ultérieurement dans la page de Configuration Globale du Site.

Lorsque tout sur la première page est terminé, sélectionnez le bouton *Setup Login Data* pour continuer.

## Données de connexion

Vous devriez maintenant voir l'écran des données de connexion.

![Joomla installer part 2, login data](../../../en/images/getting-started/installing-joomla-installer-2.png)

Remplissez les informations suivantes.

- **Nom Réel** Le nom de l'Utilisateur Super. C'est ainsi que Joomla vous saluera lorsque vous vous connecterez.
- **Nom d'utilisateur du compte Super Utilisateur** Le nom d'utilisateur pour le *Super Utilisateur*. Évitez d'utiliser *admin* comme nom d'Administrateur !
- **Mot de Passe Admin** Rappelez-vous qu'un Super Utilisateur a un contrôle maximum sur le Site et les interfaces Administrateur, donc utilisez un mot de passe difficile. Utilisez **Mon Profil** dans l'interface *Administration* pour le changer plus tard.
- **Adresse Email du Super Utilisateur** L'adresse email du Super Utilisateur. Entrez un email valide au cas où vous oublieriez votre mot de passe. C'est l'adresse email où vous recevrez un lien pour changer le mot de passe du Super Utilisateur.

Lorsque tout sur la deuxième page est terminé, sélectionnez le bouton *Setup Database Connection* pour continuer.

## Configuration de la base de données

Entrez les informations de la base de données notées lors de la création de la base de données pour cette installation.

![Joomla installer part 3, database configuration](../../../en/images/getting-started/installing-joomla-installer-3.png)

Pour simplification, ces instructions sont une référence à l'installation avec une base de données MySQLi. Les instructions sur la page d'installation sont explicites, mais les voici à nouveau :

- **Type de base de données** MySQLi est la base de données couramment utilisée
- **Nom d'hôte** Où se trouve votre base de données. Commun est *localhost*,
  même sur les services d'hébergement. Cependant, certains hébergeurs utilisent un serveur de base de données spécifique tel que *dbserver1.votrehébergeur.com*.
- **Nom d'utilisateur** Le nom d'utilisateur utilisé pour se connecter à la base de données
- **Mot de passe** Le mot de passe pour l'utilisateur de la base de données (pas votre mot de passe administrateur)
- **Nom de la base de données** Le nom de la base de données
- **Préfixe de table** Ceci est généré automatiquement comme une fonctionnalité de sécurité. Vous pouvez accepter la valeur par défaut générée aléatoirement ou la modifier. N'oubliez pas de mettre le caractère de soulignement (`_`) à la fin du préfixe.
- **Chiffrement de la connexion** spécifie comment la connexion à la base de données doit être chiffrée. Si vous ne savez pas - il est préférable de s'en tenir à la valeur par défaut. Cependant, cela permet aux entreprises qui utilisent une authentification à sens unique ou bidirectionnelle pour la connexion à la base de données de la fournir.

Tous ces choix et plus encore peuvent être modifiés sur la page de Configuration Globale du Site, sous *Options du Serveur* après l'installation. Notez que vous risquez de casser votre installation si vous modifiez ces paramètres après l'installation, à moins d'avoir une copie complète de la base de données actuelle utilisée par l'installation de Joomla. Les usages courants seraient de mettre à jour le nom d'utilisateur et le mot de passe de la base de données ou de compléter un déplacement d'une installation existante vers un nouvel hôte avec des paramètres différents.

Après avoir sélectionné le bouton *Installer Joomla*, vous devriez voir la barre de progression de l'installation de Joomla.

![Joomla installer part 4, installation progress bar](../../../en/images/getting-started/installing-joomla-installer-4.png)

Une fois l'installation terminée, vous devriez voir la page de succès.

## Finition

### Succès et finition de l'installation

Félicitations ! Votre site Joomla est prêt.

![Joomla installer part 5, your joomla site is ready](../../../en/images/getting-started/installing-joomla-installer-5.png)

La capture d'écran ci-dessus montre une installation développeur. Une installation de production  
supprime automatiquement le dossier Installation.

Si vous souhaitez commencer à utiliser Joomla immédiatement sans installer de langues supplémentaires, vous pouvez sélectionner *Ouvrir l'administrateur* pour accéder au *tableau de bord de l'administrateur* ou sélectionner *Ouvrir le site* pour aller à la page d'accueil du site. Vous pourriez voir une section avec les réglages PHP recommandés.

- **Paramètres Recommandés** Ces paramètres sont recommandés dans votre configuration PHP, mais n'empêcheront pas l'installation de Joomla!. Vous pouvez vous référer aux instructions ci-dessus sur la manière de les modifier si nécessaire.

### Langues supplémentaires

Dans le cadre du processus d'installation de Joomla, vous avez la possibilité d'installer des langues supplémentaires avant de terminer l'installation.

Pour ce faire, sélectionnez le bouton Installer des langues supplémentaires

Cela vous mènera à une page d'installation supplémentaire vous permettant de sélectionner les langues dont vous avez besoin.

#### Installer des langues supplémentaires

Une liste de packs linguistiques est affichée.

![Joomla installer part 6, install additional languages](../../../en/images/getting-started/installing-joomla-installer-6.png)

Sélectionnez jusqu'à 3 langues que vous souhaitez installer. (Plus de 3 à la fois peuvent causer des problèmes de dépassement de temps; vous pouvez en installer d'autres plus tard.)

Souvenez-vous des éléments suivants :

- Les packs de langues inclus dans les distributions personnalisées ne seront pas listés à cette étape car ils sont déjà installés.
- Une version des packs proposés correspondra à la version majeure de Joomla (5.0.x, 5.1.x, etc.). La version mineure du pack peut ne pas correspondre, par exemple vous installez la version 5.0.3 et un pack de langue 5.0.2 est affiché.
- Les packs de langues non correspondants dans l'exemple ci-dessus peuvent avoir des chaînes non traduites.
- Les packs de langues non correspondants seront proposés comme mise à jour lorsque les packs seront mis à jour par les équipes de traduction enregistrées. La mise à jour disponible sera affichée dans le Panneau de contrôle ainsi que dans **Extensions → Mise à jour**. Ce comportement est similaire à **Extensions → Installer des langues**.

Sélectionnez *Suivant* et une barre de progression s'affichera pendant l'installation du ou des packs linguistiques.

#### Choisissez la Langue par Défaut

Quand l'installation des langues est terminée, vous verrez à présent un écran similaire indiquant *Félicitations ! Votre site Joomla est prêt.* La différence sera une liste des langues installées vous permettant de sélectionner la langue par défaut pour le site et l'interface Administrateur.

![Joomla installer part 7, choose default language](../../../en/images/getting-started/installing-joomla-installer-7.png)

- Sélectionnez la langue par défaut que vous souhaitez utiliser.
- Lorsque vous avez sélectionné la langue par défaut, sélectionnez le bouton *Définir la langue par défaut* pour confirmer.
- Un message système s'affichera confirmant que Joomla a défini la langue par défaut pour l'ADMINISTRATEUR et le SITE. Ce message peut être fermé.

#### Finaliser

Vous pouvez maintenant naviguer vers le *Tableau de bord administrateur*. Connectez-vous en sélectionnant *Ouvrir l'administrateur* ou allez directement à la page d'accueil de votre site en sélectionnant *Ouvrir le site*.

*Traduit par openai.com*

