<!-- Filename: J4.x:Installing_Joomla / Display title: Installation de Joomla! -->

Ceci est une page temporaire jusqu'à la sortie de Joomla 4. En
attendant, merci de consulter  Installation de Joomla!
3.x

Installer Joomla ! pour la première fois est très facile. Une fois les
étapes préliminaires terminées, à savoir la configuration d'un
environnement d'hébergement et la création d'une base de données, le
programme d'installation web intégré de Joomla mettra en place votre
nouveau site en quelques minutes seulement. Les étapes précédentes :

### Configuration de l'hébergement

Si vous n'avez pas encore mis en place un environnement d'hébergement,
vous devez le faire maintenant, soit sur un service d'hébergement, soit
sur votre ordinateur local. Lisez la  Configuration de
l'hébergement
pour plus de détails.

En outre, certains paramètres PHP doivent être suffisants pour que
Joomla puisse s'installer. Ces paramètres se trouvent généralement dans
un fichier de configuration **php.ini** ou **user.ini** sur le serveur.
Si vous êtes sur un hébergement partagé, demandez à votre service
d'hébergement comment modifier ces paramètres si cela est possible. Si
vous travaillez sur un hôte local, par exemple avec
XAMPP, ou
sur un VPS ou un hôte dédié, vous ne devriez pas être limité par ces
paramètres et vous pouvez les définir vous-même.

Les valeurs de PHP.ini ci-dessous sont uniquement des *valeurs
suggérées*.

- memory_limit - **Minimum :** 64M **Recommandé :** 128M ou plus
- upload_max_filesize - **Minimum :** 30M
- post_max_size - **Minimum :** 30M
- max_execution_time - **Recommandé :** 30

Il est possible de travailler avec des valeurs inférieures de
upload_max_filesize et post_max_size mais les extensions plus
importantes ne pourront pas être téléchargées et causeront des problèmes
imprévisibles.

### Configuration de la base de données

Si vous n'avez pas encore configuré une base de données, faites-le
maintenant. Elle est couverte pour un service d'hébergement dans le
tutoriel  Configuration de
l'hébergement.
Il existe également un tutoriel  Création d'une base de données pour
Joomla !
qui couvre les méthodes de l'hôte local et de phpMyAdmin.

Vous devrez noter les informations de base sur la base de données
nécessaires au démarrage de l'installation de Joomla.

- Emplacement de la base de données, généralement *localhost*, même sur
  un service d'hébergement. Il peut s'agir d'un serveur d'un hôte
  spécifique tel que *`dbserver1.yourhost.com`*.
- Le nom de la base de données
- Le nom de l'utilisateur de la base de données
- Le mot de passe de l'utilisateur de la base de données

## Préparation de l'installation

### Téléchargement et envoi du package de fichiers Joomla!

Téléchargez la version actuelle de Joomla ! à partir du lien figurant
sur la page
<a href="https://downloads.joomla.org/" class="external text"
target="_blank" rel="noreferrer noopener">Télécharger Joomla</a>.

Déplacez le fichier zip du paquet d'installation de Joomla téléchargé
vers le serveur. Pour un service d'hébergement, vous pouvez utiliser la
fonction de téléchargement du gestionnaire de fichiers de cPanel ou
utiliser un client FTP pour transférer le fichier zip téléchargé de
Joomla 4.x. sur votre serveur. Il existe plusieurs clients FTP
disponibles. Voici une comparaison détaillée <a
href="https://en.wikipedia.org/wiki/Comparison_of_FTP_client_software"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Comparaison des logiciels clients
FTP</a>. En cas de doute, utilisez FileZilla.

Le dossier "racine" de votre serveur

Il est préférable de déplacer le package zip téléchargé vers votre
serveur et de le décompresser là-bas plutôt que de le décompresser
localement et de déplacer ensuite l'arborescence de fichiers.
Normalement, vous téléchargez vos fichiers Web dans le dossier racine de
votre service d'hébergement. Ce dossier est généralement nommé
"public_html" mais d'autres variantes incluent "htdocs" et cela dépend
de la façon dont votre hôte a configuré le serveur. Pour les besoins de
Joomla, vous pouvez charger les fichiers directement dans "public_html"
ou dans un sous-dossier que vous avez créé à l'intérieur.

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Attention !

Les fichiers du package zip peuvent être extraits directement sur l'hôte
à l'aide de divers outils en ligne de commande (par exemple, unzip), qui
doivent être installés sur le serveur. Si votre service d'hébergement
utilise l'outil d'administration cPanel, vous pouvez cliquer sur le
bouton Extraire dans le gestionnaire de fichiers. En outre, l'outil
tiers gratuit
<a href="https://www.akeeba.com/products/akeeba-kickstart.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Akeeba Kickstart</a> peut également
être utilisé à cette fin. Les fichiers et répertoires décompressés
seront placés dans le dossier actuel. L'extraction sur votre ordinateur
local dépend de votre système d'exploitation. Essayez un clic droit et
voyez s'il y a un menu d'extraction. Dans ce cas, votre système
d'exploitation peut placer les fichiers dans un dossier portant le même
nom que le fichier zip. Après l'extraction, vous pouvez supprimer le
fichier zip et renommer le dossier d'extraction en quelque chose de
court et adapté à une utilisation dans une url.

## Démarrer l'installation

Une fois les exigences ci-dessus satisfaites, une base de données créée
et les fichiers Joomla requis en place, vous êtes prêt à installer
Joomla. Lancez le programme d'installation web de Joomla en ouvrant
votre navigateur préféré et en naviguant vers le nom de domaine du site.
Sur une installation d'hébergement, vous utiliserez
*`https://www.yoursitename.com`*. Si vous installez Joomla! localement,
vous allez utiliser *`http://localhost/`* et vous devriez voir l'écran
d'installation.

<img
src="https://docs.joomla.org/images/5/51/J4x_Installation_screen_page_1-fr.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="397" width="500" height="397"
alt="J4x Installation screen page 1-fr.png" />

Joomla! va essayer d'identifier automatiquement le champ "Sélectionnez
la langue d'installation" selon la langue de votre navigateur. Vous
pouvez la modifier si nécessaire.

Remplissez les informations suivantes.

- *Nom du site* : le nom de votre site web - il peut être modifié à tout
  moment ultérieurement dans la page  Configuration générale du
  site.

Lorsque tout est terminé sur la première page, cliquez sur le bouton
**Configuration des données de connexion** pour continuer :

## Données de connexion

Vous devriez maintenant voir l'écran des données de connexion.

<img
src="https://docs.joomla.org/images/6/66/J4x_Installation_screen_page_2.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="481" width="500" height="481"
alt="J4x Installation screen page 2.png" />

Remplissez les informations suivantes.

- **Nom réel** : Le nom du super utilisateur. C'est ainsi que Joomla
  vous accueillera lorsque vous vous connecterez !
- '*Nom d'utilisateur du Super Utilisateur* : Le nom d'utilisateur du
  *Super Utilisateur*. Evitez d'utiliser admin (qui est une bonne  Mon
  Profil
  dans l'interface *Administration* pour le changer plus tard.
- **Mot de passe Admin** : rappelez-vous que le super utilisateur a le
  contrôle maximum du site (frontend & backend), donc essayez d'utiliser
  un mot de passe difficile. Utilisez  Mon
  Profil
  dans l'interface *Administration* pour le changer plus tard.
- **Adresse email du super utilisateur** : L'adresse email du super
  utilisateur. Entrez un courriel valide au cas où vous oublieriez votre
  mot de passe. C'est l'adresse électronique où vous recevrez un lien
  pour changer le mot de passe de l'administrateur.

Lorsque tout est terminé sur la deuxième page, cliquez sur le bouton
**Configuration de la connexion à la base de données** pour continuer :

## Configuration de la base de données

### Paramètres de configuration

Vous devrez entrer les informations sur la base de données que vous
utiliserez pour Joomla ! maintenant. Vous pouvez également lire ou
revoir <a
href="https://docs.joomla.org/Cr%C3%A9ation_d%27une_base_de_donn%C3%A9es_pour_Joomla!"
class="new"
title="Special:MyLanguage/Création d&#39;une base de données pour Joomla! (page does not exist)">Création
d'une base de données pour Joomla !</a>.

<img
src="https://docs.joomla.org/images/4/4f/J40_Installation_screen_page_3.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="637" width="500" height="637"
alt="J40 Installation screen page 3.png" />

Pour simplifier, ces instructions font référence à l'installation avec
une base de données
<a href="https://en.wikipedia.org/wiki/MySQLi" class="extiw"
title="wikipedia:MySQLi">MySQLi</a>. Les instructions sur la page
d'installation sont explicites, mais les voici à nouveau :

- **Type de base de données** : MySQLi est la base de données
  communément utilisée.
- **Hostname** : Où se trouve votre base de données. Le nom commun est
  *`localhost`*, mais certains hébergeurs utilisent un serveur de base
  de données spécifique tel que

*dbserver1.yourhost.com*.

- **Nom d'Utilisateur** : l'identifiant à utiliser pour se connecter à
  la base de données
- **Mot de Passe** : le mot de passe associé à l'utilisateur de la base
  de données
- **Nom de la Base de Données** : le nom de la base de données
- **Préfixe de Tables** : un préfixe est généré automatiquement, mais
  vous pouvez le modifier. Par exemple, vous pouvez utiliser `jos3_`.
  Mais n'oubliez pas d'ajouter un tiret bas

(`_`) à la fin du préfixe.

- **Chiffrement de la connexion** : spécifie comment la connexion à la
  base de données doit être chiffrée. Si vous ne savez pas - alors il
  est préférable de s'en tenir à la valeur par défaut. Cependant, cela
  permet aux structures qui ont un chiffrement SSL bidirectionnel vers
  la base de données de le renseigner.

Tous ces choix et bien d'autres peuvent être modifiés sur la page Configuration générale du
Site.
sous les Options du serveur, une fois l'installation terminée. Notez que
vous allez "casser" votre installation si vous modifiez ces paramètres
après l'installation, à moins que vous ne disposiez d'une copie complète
de la base de données actuelle utilisée par l'installation de Joomla !
Les utilisations courantes sont la mise à jour du nom d'utilisateur et
du mot de passe de la base de données ou le déplacement d'une
installation existante vers un nouvel hébergement avec des paramètres
différents.

Après avoir cliqué sur le bouton *Installer Joomla*, vous devriez voir
le logo de Joomla tourner. Une fois l'installation terminée, vous
devriez voir la page de réussite !

## Terminer l'installation

### Succès et fin de l'installation

Félicitations ! Joomla ! 4 est maintenant installé. Si vous voulez
commencer à utiliser Joomla de la bonne façon sans [installation de
langues
supplémentaires](https://docs.joomla.org/J4.x:Installing_Joomla#Installing_Extra_Languages "Special:MyLanguage/J4.x:Installing Joomla")
il y a une dernière étape pour terminer l'installation. Vous devez
supprimer le **Dossier d'installation**. Cliquez sur **Supprimer le
dossier d'installation** et un message de réussite apparaîtra. Vous
pouvez maintenant naviguer vers le **Tableau de bord de
l'administrateur** en vous connectant en cliquant sur **Complete & Open
Admin** ou aller directement sur votre site en cliquant sur **Complete &
Open Site**.

<img
src="https://docs.joomla.org/images/e/e0/J40_Installation_screen_page_4.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="318" width="500" height="318"
alt="J40 Installation screen page 4.png" />

Si vous souhaitez commencer à utiliser Joomla immédiatement sans installation de langues
supplémentaires.
vous pouvez sélectionner **Ouvrir l'administrateur** pour accéder au
**Tableau de bord de l'administrateur** ou sélectionner **Ouvrir le
site** pour accéder à la page d'accueil du site.

Vous pouvez voir une section avec des paramètres PHP recommandés.

- **Paramètres recommandés** : Ces paramètres sont recommandés dans
  votre configuration PHP, mais n'empêcheront pas Joomla ! d'être
  installé. Vous pouvez vous référer aux instructions ci-dessus sur la
  façon dont ils peuvent être modifiés s'il y a un besoin de le faire.

### Installation de langues supplémentaires

Dans le cadre du processus d'installation de Joomla, vous avez la
possibilité d'installer des langues supplémentaires avant de terminer
l'installation en supprimant le **Dossier d'installation**, cliquez
sur :

Pour cela, cliquez sur le bouton "Installer des langues
supplémentaires".

Vous accéderez alors à une page d'installation supplémentaire qui vous
permettra de sélectionner les langues souhaitées.

#### Installation des langues

Une liste des paquets de langue s'affiche.

<img
src="https://docs.joomla.org/images/c/ce/J40_Installation_screen_page_5.png"
decoding="async" data-file-width="500" data-file-height="755"
width="500" height="755" alt="J40 Installation screen page 5.png" />

Sélectionnez jusqu'à 3 langues que vous souhaitez installer (plus de 3 à
la fois peut causer des problèmes de délai - vous pouvez en installer
d'autres plus tard).

Souvenez-vous de ce qui suit ː

- Les packs de langue inclus dans les distributions personnalisées ne
  seront pas répertoriés à ce stade car ils sont déjà installés.
- La version des packs proposés correspondra à la version majeure de
  Joomla (4.0.x, 4.1.x, etc.). La version mineure du pack peut ne pas
  correspondre, par exemple, vous installez la version 4.0.3 et un pack
  de langue 4.0.2 est affiché.
- Les packs de langue non référencés dans l'exemple ci-dessus peuvent
  avoir des chaînes non traduites.
- Les packs de langue non référencés seront proposés comme mise à jour
  lorsque les packs seront mis à jour par les équipes de traduction
  enregistrées. La mise à jour disponible sera affichée dans le panneau
  de contrôle ainsi que dans **Extensions Manager **→** Update**. Ce
  comportement est similaire à celui de **Extensions
  Manager **→** Installer les langues**.

Cliquez sur **Suivant** et une barre de progression s'affichera pendant
l'installation du ou des packs de langues.

#### Choisissez la langue par défaut

Une fois l'installation des
langues terminée, vous verrez apparaître un écran très similaire : "
Félicitations ! Votre site Joomla est prêt.". La différence sera une
liste des langues installées vous permettant de sélectionner la langue
par défaut pour le site et l'interface administrateur.

<img
src="https://docs.joomla.org/images/d/d2/J40_Installation_screen_page_4_default_langs.png"
class="thumbborder" decoding="async" data-file-width="500"
data-file-height="650" width="500" height="650" alt="500" />

- Sélectionnez la langue par défaut que vous souhaitez utiliser.
- Lorsque vous avez sélectionné la langue par défaut, cliquez sur le
  bouton **Définir la langue par défaut** pour confirmer.
- Un message système sera affiché pour confirmer que Joomla a défini la
  langue par défaut de l'ADMINISTRATEUR et du SITE. Ce message peut être
  fermé.

#### Finalisation

Vous devez maintenant supprimer le *Dossier d'installation*. Cliquez sur
**Supprimer le dossier d'installation**. Vous obtiendrez un message de
confirmation et vous pouvez maintenant vous rendre dans le **Tableau de
bord de l'administrateur** en cliquant sur **Terminer et ouvrir Admin**
ou aller directement sur votre site en cliquant sur **Terminer et ouvrir
Site**.

## Related Information

-  Hosting
  Setup
-  Hosting and Server
  Setup
-  Creating A VPS Testing
  Server
-  Setting up your local
  environment
-  Joomla CLI
  Installation
