<!-- Filename: Backup_Basics_for_a_Joomla!_Web_Site / Display title: Sauvegarde d'un site Joomla! - principes de base -->

Conservez toujours une sauvegarde récente de votre site. Les accidents
arrivent, mais il y a de nombreuses autres raisons d'avoir vos fichiers
de sauvegarde à portée de main avant que le besoin ne se fasse sentir.
**N.B. : les sauvegardes ne doivent pas être utilisées pour restaurer un
site piraté car le piratage peut être présent sur le site depuis un
certain temps et avoir été sauvegardé avec le site.**

Les causes de la perte de données sont nombreuses. Les sites Joomla
peuvent être compromis par des attaquants malveillants si
l'administrateur du site n'a pas prêté attention à la sécurité ou dans
les cas où les pirates contournent la meilleure sécurité. Joomla ! est
conçu pour le travail en équipe, et même de bons rédacteurs peuvent
commettre une erreur qui nuit au site.

Il existe de nombreuses raisons pour lesquelles les administrateurs de
sites Web doivent rétablir le site dans un état de fonctionnement
antérieur.

Exercez-vous à la fois à la sauvegarde et à la restauration. Personne ne
devrait attendre une urgence pour tester ses compétences et ses outils
pour faire face à une urgence. Très souvent, les gens créent une
sauvegarde de quelque chose qui est vide ou corrompu et découvrent
qu'aucune de leurs données critiques n'a été sauvegardée. Personne
n'aime un navire qui coule avec des canots de sauvetage vides. Il est
également judicieux de s'entraîner à faire sortir les gens des canots de
sauvetage et à les faire entrer dans un nouveau système opérationnel.

Avoir une sauvegarde n'est pas seulement une question d'accident ; une
personne qui connaît bien la sauvegarde peut aider à développer de
nouvelles fonctionnalités en toute sécurité. La sauvegarde et la
restauration aident les gestionnaires de sites Web à créer un site de
test où les nouvelles modifications peuvent être mises en pratique sans
mettre en danger le site de production. Le clone peut être créé sur une
machine locale faisant office de serveur de test ou sur tout autre
dossier ou compte d'hébergement Web prenant en charge les versions SQL
et PHP utilisées par le site que vous avez sauvegardé.

Il est facile pour quiconque de mélanger leur site de production et leur
site de test, alors modifiez tout simplement la couleur du template de
votre site de test pour rappeler aux développeurs que le site de test
n'est pas ouvert au public.

## Sauvegarder un site web Joomla en utilisant Akeeba (méthode habituelle)

C'est la méthode préférée en utilisant l'extension de sauvegarde
d'Akeeba.

- Akeeba Backup produit un fichier *.jpa*.
- Le fichier compressé *.jpa* contient tous les fichiers du site web et
  le contenu de la base de données.
- Le fichier *.jpa* comprend également un installateur.
- Le fichier *kickstart.php* d'Akeeba permet de décompresser le fichier
  *jpa*.
- Ensuite, exécutez le programme d'installation et installez votre site
  comme lors d'une installation classique de Joomla.
- Le programme d'installation modifie la configuration en vue de sa
  restauration dans un emplacement différent et demande les informations
  de la nouvelle base de données.

Vous pouvez télécharger l'extension Akeeba Backup à partir du <a
href="https://extensions.joomla.org/extensions/extension/access-a-security/site-security/akeeba-backup/"
class="external text" target="_blank"
rel="noreferrer noopener">Répertoire des extensions de Joomla</a>. Vous
y trouverez également un lien vers des instructions complètes.

## Méthode de sauvegarde en deux parties

Une sauvegarde complète de votre site Joomla comporte deux parties. Ce
sont :

1.  Les informations de la base de données, généralement situées dans
    votre base de données MySQL.
2.  Les fichiers et les dossiers de votre site Web, tels qu'ils sont
    hébergés sur la plupart des sites HTML statiques.

Si vous ne sauvegardez pas vos fichiers et votre base de données, votre
sauvegarde est incomplète.

### Sauvegarde de la base de données

L'une des premières étapes de la sauvegarde de votre site Joomla
consiste à fermer le site au public, à sauvegarder les fichiers, puis à
rouvrir le site. Les étapes de
<a href="https://docs.phpmyadmin.net/en/latest/index.html"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">la documentation phpMyAdmin</a>
omettent cette opération indispensable. Allez dans l'onglet
**Administration de Joomla **→** Système Configuration **→** Site**,
mettez *Site hors-ligne* = 'Oui*.*

Cela modifiera alors le fichier *configuration.php* à la racine de votre
site web Joomla.

Un administrateur devra utiliser le panneau de contrôle de votre
hébergement pour visualiser ce fichier ou utiliser le FTP pour
télécharger et visualiser le fichier. Dans le fichier
*configuration.php*, vous pouvez trouver le nom de votre base de données
qui devra être sauvegardée.

Recherchez la ligne dont le code ressemble à `var $db = 'x1234';` ou
`public $db = 'x1234';` Où *x1234* est le nom de votre base de données.

En utilisant les informations de connexion de votre serveur ou
hébergeur, ouvrez l'outil PhpMyAdmin. Ouvrez la base de données et
recherchez la table nommée "users", puis cliquez sur l'icône "Afficher"
pour voir les données de cette table.

Vous devriez voir le nom des utilisateurs ayant un compte sur votre site
Joomla. Cette vue vous permet d'être sûr que vous allez sauvegarder la
bonne base de données.

Cliquez sur l'onglet *Exporter*, puis sur *Exécuter*.

Votre navigateur va télécharger votre base de données dans un fichier
SQL.

Localisez ce fichier (le dossier de destination varie selon votre
navigateur/configuration), puis déplacez-le vers un emplacement sur.

Les bases de données SQL peuvent être sauvegardées sans PhpMyAdmin mais
en utilisant une ligne de commande SQL. Si vous savez déjà comment
faire, vous n'avez probablement pas besoin de cette documentation.

Il est recommandé de sauvegarder la base de données au moins deux fois
par semaine, voire même tous les jours (et plus) si vous avez un site
actif.

### Sauvegarde du système de fichiers

Poursuivez avec votre site hors-ligne (voir ci-dessus). Vos dossiers et
fichiers Joomla! peuvent être sauvegardés en les téléchargeant avec un
utilitaire FTP ou en utilisant le gestionnaire de fichiers de votre
hébergement web. Ces deux options fonctionnent aussi bien l'une que
l'autre.

Les outils FTP déplacent des milliers de fichiers Joomla, ce qui prend
du temps. La plupart des hébergeurs proposent un panneau de contrôle
permettant de placer des milliers de fichiers dans un seul dossier, puis
de créer un fichier zip très rapidement.

Cela signifie que votre site est hors ligne pendant un court laps de
temps et que vous n'aurez qu'un seul fichier zip. Accédez au panneau de
contrôle de votre hébergement et recherchez l’icône du gestionnaire de
fichiers.

Si vous utilisez le gestionnaire de fichiers de votre hébergeur,
utilisez cette interface pour sélectionner votre dossier sur le serveur
et créez un fichier zip. Téléchargez le fichier zip sur votre ordinateur
et décompressez-le pour voir quels sont les fichiers à l'intérieur de ce
zip. Cette option vous permet également de décompresser ce même fichier
zip pour la restauration vers un site de test.

La sauvegarde des fichiers Joomla! par FTP n'est pas différente de la
sauvegarde d'un site HTML statique. Téléchargez tous les fichiers et
dossiers présents dans le répertoire principal. Le téléchargement se
fera dans un dossier sur votre ordinateur. Assurez-vous que la structure
des fichiers et répertoires reste la même que celle du site distant.
Lorsque vous restaurez les fichiers, vous utiliserez un utilitaire FTP
pour charger les fichiers sur un nouveau serveur.

**Dès que vous avez téléchargé vos fichiers en zip ou via FTP, vous
pouvez remettre votre site en ligne.**

## Documentation complémentaire sur les sauvegardes

La plupart des administrateurs de site Joomla! ont accès à leurs données
MySQL à l'aide de l'interface graphique appelée PhpMyAdmin. Pour plus
d'informations, consultez : <a
href="https://docs.phpmyadmin.net/fr/latest/faq.html#how-can-i-backup-my-database-or-table"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Comment puis-je sauvegarder ma base
de données ou ma table ?</a>

Il existe plusieurs extensions de sauvegarde automatique sur le
<a href="http://extensions.joomla.org" class="external text"
target="_blank" rel="noreferrer noopener">Répertoire des Extensions
Joomla</a>. Voici un lien vers les <a
href="http://extensions.joomla.org/extensions/extension?searchall=backup&amp;controller=filter"
class="external text" target="_blank"
rel="noreferrer noopener">extensions de sauvegarde pour Joomla</a>.

Lorsque les serveurs sont hébergés dans le même bâtiment que l'équipe,
les administrateurs web doivent prendre des précautions supplémentaires
pour stocker les copies de sauvegarde de la base de données/des fichiers
dans un autre bâtiment. Un incendie, un vol, un dégât des eaux ou tout
autre dommage peut entrainer un effacement du site ET des sauvegardes.
Les administrateurs web doivent faire régulièrement une copie de la base
de données et des fichiers sur CD ou sur un disque dur externe.

## Notes additionnelles

### 2FA (Authentification en deux étapes)

Si vous utilisez l'authentification en 2 étapes (disponible depuis août
2014) et que vous n'avez plus accès à votre site, vous pouvez renommer
le dossier plugins/twofactorauth en twofactorauth.BAK et vous connectez
au backend de votre site. Ensuite, désactivez tous les plugins du groupe
"twofactorauth". Enfin, renommez le dossier plugins/twofactorauth.BAK de
votre site en twofactorauth.

- Voir également :  Didacticiel sur l'authentification en deux
  étapes
