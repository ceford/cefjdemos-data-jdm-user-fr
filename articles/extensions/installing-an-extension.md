<!-- Filename: Installing_an_extension / Display title: Installation d'une extension  -->

## Documentation de l'extension

Avant de commencer, il est toujours judicieux de lire la documentation associée à une extension. La plupart des extensions ont des pages d'accueil et des forums, et il est conseillé de les consulter en premier lieu. Si un fichier README est inclus avec l'extension, vous devriez le lire. Il peut y avoir des instructions spéciales d'installation ou de configuration.

## Système d'installation des extensions

Le formulaire Système / Installer / Extensions est assez bien documenté dans l'écran d'aide. Ce qui n'est pas si évident, c'est que chacune des méthodes d'installation est un plugin. Dans les premières éditions de Joomla 4, le plugin Installer depuis le Web était en premier dans la liste et il est possible que ce soit encore le cas dans les versions qui ont été mises à jour. Avoir cette méthode en premier est peu pratique si vous utilisez habituellement l'une des autres méthodes, car cela prend quelques secondes pour récupérer des données depuis le site du répertoire des extensions de Joomla.

Pour changer l'ordre :

- Allez dans **Tableau de Bord Principal / Plugins**
- Sélectionnez **installer** dans le filtre déroulant **Sélectionner le Type**.
- Sélectionnez l'icône **Ordre de Tri** pour révéler les poignées de tri
  (points de suspension verticaux).
- Faites glisser l'élément **Installer - Installer depuis le Web** en bas de la liste.
- Retournez à **Système / Installer / Extensions** pour voir le résultat.

Vous êtes alors prêt à utiliser l'une des méthodes d'installation standards.

### Télécharger le fichier du package

Pour la plupart des extensions et des utilisateurs, la procédure sera :

- Téléchargez l'extension sur votre machine locale sous forme de fichier zip.
- Depuis le back-end de votre site Joomla (administration) sélectionnez
  **Système → Installer → Extensions**.
- Depuis l'onglet **Télécharger le fichier du package**, sélectionnez le bouton *Parcourir pour le fichier* et sélectionnez le package de l'extension sur votre ordinateur local ou faites glisser et déposez le fichier depuis votre gestionnaire de fichiers.
- Le processus de téléchargement et d'installation commence automatiquement,
- Certaines extensions peuvent fournir des instructions supplémentaires pour l'installation.
- Notez que les modules et plugins doivent généralement être activés avant de pouvoir fonctionner.

### Installer depuis un dossier

Certaines extensions peuvent être trop grandes pour utiliser la méthode de téléchargement de fichier du package, généralement en raison d'une limite sur la *Taille maximum de fichier téléversé* définie par votre hôte. Dans ce cas, vous pouvez utiliser la méthode Installer depuis un dossier.

- Créez un répertoire temporaire sur votre disque dur local et décompressez le fichier d'archive de l'extension dans ce répertoire temporaire.
- Utilisez FTP pour téléverser le contenu de ce répertoire (y compris les fichiers et sous-répertoires) dans le répertoire /tmp de la racine Joomla sur votre serveur de manière à avoir un chemin tel que /tmp/acmeextension.
- Dans le champ Répertoire d'installation, spécifiez le répertoire du serveur où vous avez téléversé les fichiers et sous-répertoires du package, par exemple /home/nom_utilisateur/public_html/tmp/acmeextension.
- Sélectionnez le bouton **Vérifier et Installer** et Joomla! installera le contenu du répertoire donné.

### Installer depuis une URL

Au lieu de télécharger un fichier zip sur votre ordinateur local, vous pouvez simplement utiliser l'URL de téléchargement. Joomla ira chercher le fichier zip directement et économisera les étapes de téléchargement et de téléversement des méthodes précédentes.

### Installer depuis le Web

Cette option vous permet d'installer une extension directement depuis le répertoire d'extensions Joomla! La liste initiale est dans l'ordre du nombre de critiques mais vous pouvez sélectionner par Catégorie pour trouver rapidement une liste d'extensions qui pourraient convenir à vos besoins.

## Découverte de l'installation du système

Comme décrit dans l'écran d'aide, la fonction Découverte vous permet d'installer des extensions trop volumineuses pour certains systèmes, en particulier les environnements d'hébergement partagé à faible coût. Quelque chose qui peut ne pas être évident est que vous pourriez avoir besoin de créer des dossiers à différents endroits sur votre service d'hébergement, généralement :

- Téléchargez les fichiers du site dans siteroot/components/com_mybigcomponent
- Téléchargez les fichiers d'administrateur dans siteroot/administrator/components/com_mybigcomponent
- Téléchargez les médias (css et javascript) dans siteroot/media/com_mybigcomponent
- Téléchargez les fichiers de langue du site dans siteroot/language/en-GB s'ils ne sont pas dans un dossier de langue dans le dossier du site du composant.
- Téléchargez les fichiers de langue de l'administrateur dans siteroot/administrator/language/en-GB s'ils ne sont pas dans un dossier de langue dans le dossier de l'administrateur du composant.

Une fois cela fait, la fonction Découverte devrait trouver et permettre l'installation du composant, et cela pourrait effectivement fonctionner.

## Langues d'installation du système

La langue par défaut est l'anglais GB. Elle ne peut pas être supprimée ou installée. 
Ce n'est peut-être pas évident, mais chaque page charge d'abord les chaînes en-GB appropriées pour s'assurer que les clés de langue utilisées par les programmeurs n'apparaissent pas dans le rendu de la page. Si la langue sélectionnée par l'utilisateur n'est pas l'anglais, alors la langue de l'utilisateur est chargée, remplaçant les chaînes anglaises. Si une langue n'a pas été entièrement traduite, le résultat sera un mélange de la langue de l'utilisateur et des chaînes anglaises. Cela peut sembler étrange, mais c'est mieux qu'un mélange de la langue de l'utilisateur et de clés de programmeur.

Dans la liste des langues disponibles, sélectionnez celle que vous devez installer. Certaines sont marquées d'un bouton vert pour indiquer qu'elles sont à jour avec la version actuelle de Joomla. D'autres sont marquées d'un bouton jaune pour indiquer qu'elles ne sont pas tout à fait à jour. Allez-y et installez-les quand même. Vous pouvez voir quelques mots anglais à des endroits qui devraient être dans votre langue sélectionnée. Mais cela peut être rare.

*Traduit par openai.com*

