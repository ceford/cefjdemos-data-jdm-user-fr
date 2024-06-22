<!-- Filename: J3.x:Update_fails_with_an_error_message / Display title: Echec de la mise à jour avec un message d'erreur -->

Joomla!  3.6.1

## Erreurs signalées

Lors du processus de mise à jour de votre site Joomla! vers la version
Joomla! 3.6.1 via l'extension native de mise à jour de Joomla, ce
message d'erreur peut s'afficher : <img
src="https://docs.joomla.org/images/9/98/Joomla-3.6.1-error-message-en.png"
decoding="async" data-file-width="782" data-file-height="36" width="782"
height="36" alt="Joomla-3.6.1-error-message-en.png" />

## Versions affectées

Informations générales

Ce billet concerne uniquement la version Joomla! : **3.6.1**

## Quelle en est la cause ?

La version 3.6.1 introduit, comme niveau suplémentaire de sécurité, une
vérification de jeton CSRF pour le composant de mise à jour. Les
versions 3.6.0 et inférieures jusqu'à 2.5.4 (toutes les versions
disposant du composant de mise à jour) seront affectées par l'anomalie
concernant le jeton CSRF car ces versions ne vont pas générer le code
nécessaire au contrôle. Les futures mises à jour fonctionneront
correctement.

## Comment résoudre l'anomalie ?

### Mise à jour depuis Joomla! 3.6.0

- Retournez sur la page d'accueil de votre administration
  `exemple.com/administrator`
- Puis, allez dans Extensions  **→**  Gérer  **→**  Base de données
- Vous devriez voir un message informant que la base de données est
  obsolète.
- Cliquez sur le bouton `Correction` dans la barre d'outils.

### Mise à jour depuis les versions ANTÉRIEURES à Joomla! 3.6.0

Si votre site fonctionne sous une version antérieure à 3.6.0 :  

- Mettez d'abord à jour vers Joomla! 3.6.0 et *NON PAS'* directement
  vers Joomla! 3.6.1  
- Mettez à jour le composant `com_joomlaupdate` via le gestionnaire des
  extensions  
- Puis exécutez la mise à jour de Joomla! 3.6.0 vers Joomla! 3.6.1.

Une nouvelle version du composant `com_joomlaupdate` est disponible dans
votre backend et apparaîtra sur votre écran de mise à jour des
extensions.

Pour plus d'informations

Veuillez consulter l'annonce officielle concernant cette anomalie <a
href="https://www.joomla.org/announcements/release-news/5666-the-joomla-3-6-1-update.html"
class="external text" target="_blank" rel="noreferrer noopener">EN
CLIQUANT ICI</a>

**Remarque**: si votre site est exécuté avec PHP 5.3, ce message
d'erreur pourrait s'afficher lorsque vous essayerez de vous
connecter :  
` 0 Failed to start the session: already started by PHP ($_SESSION is set).`  
Joomla! 3.6.2 résoudra cette anomalie. Veuillez consulter :
<a href="https://github.com/joomla/joomla-cms/pull/11430"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Fix logging in in PHP 5.3</a>.
