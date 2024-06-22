<!-- Filename: J3.x:Updating_Joomla_(Update_Method) / Display title: Mettre à jour Joomla! (méthode de mise à jour) -->

Voici la méthode recommandée pour mettre à jour un site web Joomla.

C'est non seulement la méthode recommandée, mais également la plus
simple pour mettre à jour le CMS Joomla. Cette méthode est parfois
appelée ***Mise à jour en un clic***. Si vous ne parvenez pas à utiliser
cette méthode du fait de cas d'utilisation spécifique (distributions,
langages, vitesse de l'hébergement), vous pouvez mettre à jour le CMS
Joomla! en utilisant la ** méthode
d'installation**.

Cette méthode est adaptée pour

- Tous les mises à jours Joomla! **3.x.x** à **3.x.x** (mise à jour de
  maintenance)

Cette méthode n'est pas adaptée pour

- CMS Joomla! **3.1.2** à **≥ 3.1.3** - voir [Instructions spéciales
  pour les mises à niveaux de la version
  3.1.2](https://docs.joomla.org/J3.x:Detailed_instructions_for_updating_from_3.1.2_to_3.1.4 "Special:MyLanguage/J3.x:Detailed instructions for updating from 3.1.2 to 3.1.4")

## Comment mettre à jour

Avez-vous besoin de mettre à jour votre installation Joomla ? Si une
mise à jour est disponible, vous verrez un message indiquant une mise à
jour et un bouton à cliquer.

<img
src="https://docs.joomla.org/images/thumb/9/91/J3-update-control-panel-notify-fr.PNG/450px-J3-update-control-panel-notify-fr.PNG"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/9/91/J3-update-control-panel-notify-fr.PNG 1.5x"
data-file-width="517" data-file-height="313" width="450" height="272"
alt="J3-update-control-panel-notify-fr.PNG" />

Vous verrez également une alerte dans la 'barre latérale gauche' en bas
de page.

<img
src="https://docs.joomla.org/images/9/96/J3-update-control-panel-notify-alternative-fr.PNG"
class="thumbborder" decoding="async" data-file-width="238"
data-file-height="202" width="238" height="202"
alt="J3-update-control-panel-notify-alternative-fr.PNG" />

Joomla! vous informera sur la page d'accueil de votre administration
(panneau d'administration) lorsqu'une mise à jour est disponible. La
mise à jour ne se fera pas automatiquement d'elle-même. Il est de la
responsabilité de l'administrateur de lancer la mise à jour et vérifier
qu'elle s'est effectuée avec succès.

Vous trouverez ci-après les étapes recommandées qui sont nécessaires
pour effectuer une mise à jour de votre installation Joomla.

### Etape 1 : sauvegarde

Assurez-vous d'avoir une **SAUVEGARDE A JOUR** de votre site actuel !
Dans de nombreux cas, votre hébergeur va faire des sauvegardes
périodiques de votre site. **NE** vous reposer **PAS** sur ces
sauvegardes ! Il est **FORTEMENT RECOMMANDE** d'effectuer vos propres
sauvegardes.

### Etape 2 : mise à jour du composant

Il vous faut aller dans le composant de mise à jour. Cliquez sur le
'bouton' mettre à jour ou sur le 'lien de la barre latérale' vu
précédemment, ou dans le menu principal, sélectionnez et cliquez sur
**Composants **→** Mise à jour de Joomla!**. Vous devriez alors voir
ceci :

<img
src="https://docs.joomla.org/images/7/7e/J3-joomla-update-component-fr.PNG"
class="thumbborder" decoding="async" data-file-width="974"
data-file-height="341" width="974" height="341"
alt="J3-joomla-update-component-fr.PNG" />

Sélectionnez 'Transfert direct' (par défaut) ou 'Transfert par FTP'
comme méthode pour charger les nouveaux fichiers du noyau dans votre
installation. Avez-vous fait une sauvegarde ? Voir l'étape 1 ci-dessus.

### Etape 3 : lancer la mise à jour

Cliquez sur le bouton "Mettre à jour" et la mise à jour va se lancer.

<img
src="https://docs.joomla.org/images/a/a4/J3-updating-your-joomla-files-fr.PNG"
class="thumbborder" decoding="async" data-file-width="697"
data-file-height="321" width="697" height="321"
alt="J3-updating-your-joomla-files-fr.PNG" />

Lorsque la mise à jour est terminée, un bandeau s'affichera vous
informant que votre site a été mis à jour avec succès vers la nouvelle
version.

<img
src="https://docs.joomla.org/images/4/44/J3-jooml-update-successful-fr.PNG"
class="thumbborder" decoding="async" data-file-width="698"
data-file-height="327" width="698" height="327"
alt="J3-jooml-update-successful-fr.PNG" />

Une fois que la mise à jour est terminée, vous pouvez avoir besoin de
vider le cache de votre navigateur pour ajuster toute modification des
CSS du template.

## Configurations pour la mise à jour de Joomla!

Dans la plupart des cas, vous n'aurez pas à modifier ces paramètres. Les
choix par défaut assurent que votre installation du CMS Joomla! soit
toujours vérifiée par rapport au serveur de mise à jour et que la
personne ayant un accès administrateur puisse effecteur la mise à jour
l'installation.

L'écran des paramètres s'affiche en cliquant sur le bouton 'paramètres'
situé sur l'écran de Mise à jour de Joomla. Après avoir cliqué sur le
bouton 'paramètres', vous verrez l'image suivante.

<img
src="https://docs.joomla.org/images/f/fb/J3-update-component-configure-server-fr.PNG"
class="thumbborder" decoding="async" data-file-width="690"
data-file-height="438" width="690" height="438"
alt="J3-update-component-configure-server-fr.PNG" />

### Paramétrer le serveur de mise à jour

L'encart de mise à jour qui s'affiche sur la page d'accueil de
l'administration dépend de la configuration du serveur de mise à jour et
de la mise en cache.

<img
src="https://docs.joomla.org/images/4/4f/J3-update-component-configure-server-options-fr.PNG"
class="thumbborder" decoding="async" data-file-width="417"
data-file-height="220" width="417" height="220"
alt="J3-update-component-configure-server-options-fr.PNG" />

La première option affiche la dernière mise à jour de la version majeure
installée (par défaut). La seconde affiche la dernière mise à jour de la
dernière version de Joomla. La mise en cache peut faire que la mise à
jour disponible ne soit pas détectée et vous devez donc purger le cache.

### Permissions

<img
src="https://docs.joomla.org/images/6/6d/J3-update-component-configure-server-permissions-fr.PNG"
class="thumbborder" decoding="async" data-file-width="846"
data-file-height="417" width="846" height="417"
alt="J3-update-component-configure-server-permissions-fr.PNG" />
