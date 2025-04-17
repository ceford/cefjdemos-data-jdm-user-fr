<!-- Filename: J4.x:Installing_Joomla / Display title: Installation de Joomla -->

## Introduction

Installer Joomla! pour la première fois est très facile. Après avoir terminé les
étapes préliminaires, mis en place un environnement d'hébergement et créé une
base de données, l'installateur web intégré de Joomla configurera votre nouveau site en
quelques minutes seulement. Les étapes précédentes :

### Configuration de l'Hébergement

Si vous n'avez pas encore configuré un environnement d'hébergement, vous devez le faire maintenant,
soit sur un service d'hébergement, soit sur votre ordinateur local.

De plus, certains paramètres PHP doivent être suffisants pour que Joomla
s'installe. Les paramètres se trouvent généralement dans un fichier de configuration *php.ini* ou *user.ini*
sur le serveur. Si vous êtes sur un hébergement mutualisé, parlez à
votre service d'hébergement pour savoir comment changer ces paramètres s'il est
possible de le faire. Si vous travaillez sur un localhost, par exemple avec
XAMPP, ou un
VPS ou un hôte dédié, vous ne devriez pas être limité par ces paramètres
et pouvez les définir vous-même.

Les valeurs minimales pour le fichier *php.ini* sont indiquées ci-dessous :

- *memory_limit:* 256M
- *upload_max_filesize:* 64M
- *post_max_size:* 64M
- *max_execution_time:* 30

Il est possible de travailler avec des valeurs inférieures de upload_max_filesize et
post_max_size, mais les extensions plus grandes échoueront à se télécharger et causeront
des problèmes imprévisibles.

### Configuration de la Base de Données

Si vous n'avez pas encore configuré une base de données, faites-le maintenant. Cela est couvert pour un service d'hébergement cPanel dans le tutoriel
[Hébergement cPanel](jdocmanual?article=user/hosting/cpanel-hosting). Il y a aussi un tutoriel *Créer une base de données pour
Joomla!*
qui couvre les méthodes localhost et phpMyAdmin.

Vous devrez noter les informations de base relatives à la base de données nécessaires lorsque l'installation réelle
de Joomla commencera.

- Emplacement de la base de données, généralement *localhost* même sur un service d'hébergement.
  Il peut s'agir du serveur d'un hôte spécifique tel que *`dbserver1.votrehébergeur.com`*.
- Le nom de la base de données
- Le nom de l'utilisateur de la base de données
- Le mot de passe de l'utilisateur de la base de données

## Préparation pour l'Installation

### Télécharger et Télécharger les Fichiers du Paquet Joomla!

Téléchargez la version actuelle de Joomla! depuis le lien sur la page
[Télécharger Joomla](https://downloads.joomla.org/)

Déplacez le fichier zip du paquet d'installation Joomla téléchargé vers le serveur. Pour un service d'hébergement, vous pouvez utiliser la fonction Téléchargement du Gestionnaire de Fichiers de cPanel ou utiliser un Client FTP pour transférer le fichier zip Joomla 5.x téléchargé sur votre serveur. Il existe plusieurs clients FTP disponibles. Voici une [Comparaison des logiciels clients FTP](https://fr.wikipedia.org/wiki/Comparaison_des_logiciels_clients_FTP) détaillée. En cas de doute, utilisez FileZilla.

Le dossier *root* de votre serveur

Il est préférable de déplacer le paquet zip téléchargé sur votre serveur et de le décompresser sur place plutôt que de le décompresser localement puis de déplacer l'arborescence des fichiers. Normalement, vous téléchargez vos fichiers web dans le dossier racine de votre service d'hébergement. Celui-ci est typiquement nommé `public_html` mais d'autres variations incluent `htdocs` et cela dépend de la manière dont votre hôte a configuré le serveur. Pour Joomla, vous pouvez charger les fichiers directement dans *public_html* ou un sous-dossier que vous avez créé à l'intérieur.

**Avertissement :** Si vous décompressez les fichiers sur votre propre ordinateur, puis les copiez sur votre serveur, assurez-vous de ne déplacer que les dossiers et fichiers contenus **à l'intérieur** du paquet Joomla. Si vous décompressez les dossiers et fichiers dans un dossier, par exemple appelé *`Joomla`* et que vous téléchargez ensuite ce dossier, votre site devra être accessible à *`votresite.com/Joomla`* au lieu de *`votresite.com`*. Vous pouvez renommer le sous-répertoire de Joomla à quelque chose de plus approprié à votre site, comme jblog, et vous pourriez trouver cela pratique. **Remarque :** les noms de répertoires doivent être en minuscules, sans espaces et en utilisant des tirets plutôt que des sous-tirets pour séparer les mots.

Les fichiers du paquet zip peuvent être extraits directement sur l'hôte en utilisant divers outils de ligne de commande (par exemple, unzip), qui doivent être installés sur le serveur. Si votre service d'hébergement utilise l'outil d'admin cPanel, le bouton Extraire peut être pressé dans le Gestionnaire de Fichiers. En dehors de cela, l'outil gratuit tiers Akeeba Kickstart peut aussi être utilisé à cette fin. Les fichiers et répertoires décompressés seront placés dans le dossier actuel. L'extraction sur votre ordinateur local dépend de votre système d'exploitation. Essayez un clic droit et voyez s'il y a un menu d'extraction. Dans ce cas votre système d'exploitation peut placer les fichiers dans un dossier portant le même nom que le fichier zip. Après extraction, vous pouvez supprimer le fichier zip et renommer le dossier d'extraction pour quelque chose de court et approprié pour une utilisation dans une URL.

## Commencer l'installation

Avec les exigences ci-dessus remplies, une base de données créée et les fichiers Joomla nécessaires en place, vous êtes prêt à installer Joomla. Lancez l'installateur web de Joomla en ouvrant votre navigateur préféré et en accédant au nom de domaine du site. Sur une installation hébergée, vous utiliserez *`https://www.votrenomsite.com`*. Si vous installez Joomla localement, vous utiliserez *`http://localhost/`* et vous devriez voir l'écran d'installation.

![Installateur Joomla partie 1, langue d'installation et nom du site](../../../en/images/getting-started/installing-joomla-installer-1.png)

Joomla essaiera d'identifier automatiquement le champ *Sélectionner la langue* à partir de la langue de votre navigateur. Vous pouvez le modifier si nécessaire.

Renseignez les informations suivantes.

- **Nom du site** Le nom de votre site web — cela peut être modifié à tout moment ultérieurement dans la page de configuration globale du site.

Une fois que tout est complété sur la première page, le bouton *Configurer les données de connexion* pour continuer.

## Données de Connexion

Vous devriez maintenant voir l'écran des données de connexion.

![Installateur Joomla, partie 2, données de connexion](../../../en/images/getting-started/installing-joomla-installer-2.png)

Remplissez les informations suivantes.

- **Nom Réel** Le nom de l'Utilisateur Super. C'est ainsi que Joomla vous
  accueillera lorsque vous vous connecterez.
- **Nom d'utilisateur du compte Super Utilisateur** Le nom d'utilisateur pour le *Super Utilisateur*.
  Évitez d'utiliser *admin* comme nom d'Administrateur !
- **Mot de passe Administrateur** Rappelez-vous qu'un Super Utilisateur a un contrôle maximal sur
  les interfaces du Site et de l'Administrateur, donc utilisez un mot de passe difficile.
  Utilisez **Mon Profil** dans l'interface d'*Administration* pour le modifier plus tard.
- **Adresse Email du Super Utilisateur** L'adresse email du Super Utilisateur. Entrez une
  adresse email valide au cas où vous oublieriez votre mot de passe. C'est l'adresse
  email où vous recevrez un lien pour changer le mot de passe du Super Utilisateur.

Lorsque tout sur la deuxième page est complété, cliquez sur le bouton *Configurer la connexion à la base de données* 
pour continuer.


## Configuration de la Base de Données

Entrez les informations de la base de données notées lors de la création de la base de données pour cette installation.

![Installateur Joomla partie 3, configuration de la base de données](../../../en/images/getting-started/installing-joomla-installer-3.png)

Pour simplifier, ces instructions se réfèrent à une installation avec une base de données MySQLi. Les instructions sur la page d'installation sont explicites, mais les voici à nouveau :

- **Type de Base de Données** MySQLi est la base de données couramment utilisée.
- **Nom d'Hôte** L'endroit où se trouve votre base de données. Communément *localhost*, même sur des services d'hébergement. Cependant, certains hôtes utilisent un serveur de base de données spécifique tel que *dbserver1.yourhost.com*.
- **Nom d'Utilisateur** Le nom d'utilisateur utilisé pour se connecter à la base de données.
- **Mot de Passe** Le mot de passe de l'utilisateur de la base de données (et non pas votre mot de passe d'administrateur).
- **Nom de la Base de Données** Le nom de la base de données.
- **Préfixe des Tables** Ceci est généré automatiquement comme une fonctionnalité de sécurité. Vous pouvez accepter le préfixe par défaut généré aléatoirement ou le modifier. N'oubliez juste pas de mettre le caractère de soulignement (`_`) à la fin du préfixe.
- **Cryptage de la Connexion** spécifie comment la connexion à la base de données doit être cryptée. Si vous ne savez pas, il est préférable de conserver la valeur par défaut. Cependant, cela permet aux entreprises qui utilisent une authentification à un ou deux facteurs pour la connexion à la base de données de la fournir.

Tous ces choix et bien plus peuvent être modifiés sur la page de Configuration Globale du Site, sous *Options du Serveur* après la fin de l'installation. Notez que vous risquerez de casser votre installation si vous modifiez ces paramètres après l'installation, à moins que vous n'ayez une copie complète de la base de données actuelle utilisée par l'installation Joomla. Les utilisations courantes seraient de mettre à jour le nom d'utilisateur et le mot de passe de la base de données ou de terminer un transfert d'une installation existante vers un nouvel hôte avec différents paramètres.

Après avoir cliqué sur le bouton *Installer Joomla*, vous devriez voir une barre de progression de l'installation Joomla.

![Installateur Joomla partie 4, barre de progression de l'installation](../../../en/images/getting-started/installing-joomla-installer-4.png)

Une fois l'installation terminée, vous devriez voir la page de succès.

## Finir

### Succès et finalisation de l'installation

Félicitations ! Votre site Joomla est prêt.

![Installateur Joomla partie 5, votre site Joomla est prêt](../../../en/images/getting-started/installing-joomla-installer-5.png)

La capture d'écran ci-dessus montre une installation de développement. Une installation de production retire automatiquement le dossier d'installation.

Si vous souhaitez commencer à utiliser Joomla immédiatement sans installer de langues supplémentaires, vous pouvez sélectionner *Ouvrir Administrateur* pour accéder au *Tableau de bord de l'administrateur* ou sélectionner *Ouvrir le site* pour aller à la page d'accueil du site. Vous pourriez voir une section avec les paramètres PHP recommandés.

- **Paramètres Recommandés** Ces paramètres sont recommandés dans votre configuration PHP, mais n'empêcheront pas Joomla ! d'être installé. Vous pouvez vous référer aux instructions ci-dessus sur la manière dont ils peuvent être modifiés si nécessaire.

### Langues Supplémentaires

Dans le cadre du processus d'installation de Joomla, vous avez la possibilité d'installer des langues supplémentaires avant de finaliser l'installation.

Pour ce faire, sélectionnez le bouton Installer des langues supplémentaires

Cela vous mènera à une page d'installation supplémentaire vous permettant de sélectionner les langues dont vous avez besoin.

#### Installer des Langues Supplémentaires

Une liste de packs de langues est affichée.

![Installateur Joomla partie 6, installer des langues supplémentaires](../../../en/images/getting-started/installing-joomla-installer-6.png)

Sélectionnez jusqu'à 3 langues que vous souhaitez installer. (Plus de 3 à la fois peut provoquer des problèmes de délai d'attente; vous pouvez en installer plus tard.)

Souvenez-vous des points suivants :

- Les packs de langues inclus dans les distributions personnalisées ne seront pas listés à cette étape car ils sont déjà installés.
- Une version des packs proposés correspondra à la version majeure de Joomla (5.0.x, 5.1.x, etc.). La version mineure du pack peut ne pas correspondre, par exemple, vous installez la version 5.0.3 et un pack de langues 5.0.2 est proposé.
- Les packs de langues non assortis dans l'exemple ci-dessus peuvent contenir des chaînes non traduites.
- Les packs de langues non assortis seront proposés comme mise à jour lorsque les packs seront mis à jour par les équipes de traduction enregistrées. La mise à jour disponible sera indiquée dans le panneau de contrôle ainsi que dans **Extensions → Mise à jour**. Ce comportement est similaire à **Extensions → Installer Langues**.

*Suivant* et une barre de progression s'afficheront pendant l'installation du ou des packs de langues.

#### Choisir la Langue par Défaut

Lorsque l'installation des langues est terminée, un écran similaire s'affichera avec un message *Félicitations ! Votre site Joomla est prêt*. La différence sera une liste des langues installées vous permettant de sélectionner la langue par défaut pour le site et l'interface administrateur.

![Installateur Joomla partie 7, choisir la langue par défaut](../../../en/images/getting-started/installing-joomla-installer-7.png)

- Sélectionnez la langue par défaut que vous souhaitez utiliser.
- Lorsque vous avez sélectionné la langue par défaut, utilisez le bouton *Définir la langue par défaut* pour confirmer.
- Un message système s'affichera confirmant que Joomla a défini la langue par défaut de l'ADMINISTRATEUR et du SITE. Ce message peut être fermé.

#### Finaliser

Vous pouvez maintenant naviguer vers le *Tableau de bord de l'administrateur*. Connectez-vous en sélectionnant *Ouvrir Administrateur* ou allez directement à la page d'accueil de votre site en sélectionnant *Ouvrir le site*.

