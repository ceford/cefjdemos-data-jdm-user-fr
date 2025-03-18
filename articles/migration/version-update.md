<!-- Filename: J4.x:Updating_from_an_existing_version / Display title: Mise à jour de la version  -->

## Introduction

**Rappelez-vous : Sauvegardez toujours votre site avant de le mettre à jour.**

La méthode recommandée pour mettre à jour les installations de Joomla! est d'utiliser le *Composant de mise à jour de Joomla*.

Une installation standard de Joomla 4 et ultérieure inclut un panneau de notifications utile sur le tableau de bord d'accueil après connexion. Vous pouvez voir en un clin d'œil si une mise à jour est disponible et le numéro de version.

Le message de mise à jour qui apparaît dans le panneau de notifications dépend du *Canal de mise à jour* défini dans la page *Options de mise à jour de Joomla* et de la version *Mineure* actuelle. Avec le **Canal de mise à jour** réglé sur **Par défaut**, les mises à jour au sein de la version *Majeure* actuelle sont notifiées. Avec le paramètre défini sur *Joomla Next*, vous pouvez mettre à jour vers la dernière version actuelle, puis sélectionner le bouton **Vérifier les mises à jour** pour voir si la prochaine version *Majeure* est disponible.

Bien que Joomla vous informe lorsqu'une mise à jour est disponible, c'est à vous de réaliser la mise à jour. C'est un processus simple qui devrait être effectué dès que possible pour maintenir le site à jour.

## Accéder au composant de mise à jour

Si le panneau de notifications est affiché sur le tableau de bord d'accueil, sélectionnez le bouton **x.y.z Disponible - Mettre à jour maintenant !** pour accéder au composant de mise à jour.

![notification de mise à jour Joomla sur le tableau de bord d'accueil](../../../en/images/migration/version-update-notification-home-dashboard.png)

Sinon, pour accéder au composant de mise à jour depuis le menu Administrateur, sélectionnez **Système** pour passer par le **Tableau de bord du système**.

![notification de mise à jour Joomla dans le tableau de bord du système](../../../en/images/migration/version-update-notification-system-dashboard.png)

Le tableau de bord du système dispose d'un *panneau de mise à jour* qui comprend un lien Joomla qui affichera le numéro de version de mise à jour disponible. Sélectionnez le lien **Joomla** pour accéder au composant de mise à jour.

## Réalisation de la mise à jour

Joomla! 4 et 5 fournissent une Vérification Pré-Mise à Jour pour les mises à jour vers des versions mineures. Cette vue du composant de mise à jour de Joomla affiche les spécifications techniques du serveur sur lequel le site est hébergé ainsi que les extensions du noyau et tierces qui utilisent le serveur de mise à jour sous forme de liste.

**Remarque :** L'écran de *Vérification Pré-Mise à Jour* ne s'affiche pas si le site est sur la version **Mineure** actuelle.

![vérification pré-mise à jour joomla](../../../en/images/migration/version-update-pre-update-check.png)

Portez une attention particulière aux résultats de la vérification et prenez les mesures nécessaires pour rectifier tout problème mis en évidence avant de procéder à la mise à jour. Vous pourriez avoir besoin de mettre à jour, désactiver ou désinstaller les extensions incompatibles avant de mettre à jour Joomla.

Il n'est pas rare de voir des avertissements pour les *Paramètres Recommandés* car ceux-ci sont souvent spécifiques au serveur et liés à l'hébergement. Il y a de fortes chances qu'ils existaient lorsque vous avez installé Joomla et qu'ils n'empêcheront probablement pas la mise à jour de s'achever.

*N'oubliez pas que vous êtes vivement conseillé de faire une sauvegarde si vous ne l'avez pas déjà fait !*

Il y a un lien sous le bouton de mise à jour. Dans la plupart des cas, vous pouvez ignorer ce lien. Il offre une option pour télécharger manuellement les fichiers de mise à jour si votre serveur est derrière un pare-feu ou autrement incapable de contacter les serveurs de mise à jour Joomla.

Une fois que vous avez examiné la Vérification Pré-Mise à Jour et que vous êtes satisfait, sélectionnez **Mise à Jour**.

### Confirmation de la mise à jour

![page début de mise à jour](../../../en/images/migration/version-update-start-update.png)

Cochez la case pour confirmer que vous avez effectué une sauvegarde et vérifié que les extensions sont compatibles, puis cliquez sur **Commencer la Mise à Jour**.

### Avancement de la mise à jour

![page de progression de mise à jour](../../../en/images/migration/version-update-progress.png)

Une fois la mise à jour lancée, une barre de progression apparaîtra au fur et à mesure que les fichiers Joomla sont mis à jour.

### Achèvement

![page de fin de mise à jour](../../../en/images/migration/version-update-completion.png)

Lorsque la barre de progression atteint 100%, un message système confirmera que votre site a été mis à jour ainsi que le numéro de version. Le numéro de version sera également mis à jour dans la barre d'outils supérieure, à côté du nom du site.

Cliquez sur le bouton **Retour** et vous serez renvoyé au Composant de Mise à Jour Joomla où il est possible de vérifier à nouveau les mises à jour.

## Vérifications après mise à jour

Une fois la mise à jour terminée, vous devriez effectuer quelques vérifications pour vous assurer que tout s'est déroulé comme prévu, qu'aucune erreur n'est présente et qu'il n'y a pas de modifications nécessitant des actions supplémentaires.

### Vérification du Frontend

Accédez au frontend du site Web et vérifiez qu'il fonctionne et s'affiche comme avant la mise à jour. Utilisez la combinaison *Shift + Recharger* pour forcer votre navigateur à recharger les modifications apportées aux feuilles de style et aux scripts.

### Vérifications du Système

Dans le menu latéral, sélectionnez **Système** pour accéder au tableau de bord du système. Cela vous donne un aperçu de l'état actuel de votre site Joomla.

![Tableau de bord du système après mise à jour](../../../en/images/migration/version-update-after-update.png)

Dans cet exemple, nous pouvons voir que depuis la mise à jour, nous avons deux éléments nécessitant notre attention. Ils sont marqués par une étiquette incluant un nombre. Le nombre indique combien d'éléments nécessitent une attention. En cliquant sur chacun d'eux, vous pourrez les corriger.

**Remarque** : Le tableau de bord du système effectue une vérification à chaque chargement de la page. Gardez à l'esprit que les paramètres de mise en cache du navigateur pourraient affecter cela. Il est recommandé de vider le cache du navigateur lors des vérifications en utilisant *Shift + Recharger*.

### Vérification de la Base de Données

Naviguez vers **Système → Maintenance → Base de Données**. Si votre base de données est à jour, vous devriez voir un écran similaire à celui ci-dessous :

![Vérification de la base de données après mise à jour sans problèmes](../../../en/images/migration/version-update-after-update-database-check-no-problems.png)

Si votre base de données n'est pas à jour, vous verrez un écran listant les problèmes trouvés, similaire à celui ci-dessous :

![Vérification de la base de données après mise à jour avec problèmes](../../../en/images/migration/version-update-after-update-database-check-problems.png)

Dans ce cas, sélectionnez le *Nom* de l’extension à problème, puis le bouton Mettre à jour la structure dans la barre d'outils. Joomla mettra à jour votre base de données pour corriger les problèmes listés, puis elle réaffichera l'écran. Si la correction a réussi, l'affichage indiquera que la base de données est à jour.

**Remarque** : Si des erreurs persistent, assurez-vous que toutes les tables de la base de données sont cochées.

## Découverte du système

Dans certains cas, lorsque vous mettez à jour vers une nouvelle version de Joomla, de nouvelles extensions de base sont ajoutées. Si des problèmes se sont posés lors de la mise à jour de la base de données, ces extensions peuvent ne pas avoir été correctement installées. Pour vérifier cela, accédez à **Système → Découvrir**. Ensuite, sélectionnez l'icône Découvrir dans la barre d'outils. L'écran devrait apparaître comme suit :

![Écran de découverte sans extensions à installer](../../../en/images/migration/version-update-after-update-discover.png)

Si c'est le cas, vous savez que toutes les nouvelles extensions ajoutées lors de la mise à jour ont été correctement installées dans la base de données.

Si des extensions non installées apparaissent, elles s'afficheront de manière similaire à l'écran suivant :

![Écran de découverte avec des extensions à installer découvertes](../../../en/images/migration/version-update-after-update-discover-found.png)

Dans ce cas, cochez les cases et cliquez sur l'icône Installer dans la barre d'outils. Joomla installera l'extension ou les extensions, puis affichera l'écran ne montrant aucune extension découverte. À ce stade, les nouvelles extensions ont été installées dans la base de données.

## Dépannage

Si vous avez des questions, des problèmes ou des erreurs avant, pendant ou après
la mise à jour, veuillez les poser sur le
[Forum Migrer et Mettre à jour vers Joomla! 4.x](https://forum.joomla.org/viewforum.php?f=812).

Si vous rencontrez des problèmes ou des erreurs au cours du processus de mise à jour, voici quelques
conseils.

- Vider le cache de votre navigateur. Il peut y avoir eu des modifications du CSS ou
  du JavaScript qui devront être rechargées par votre navigateur Web après une
  mise à jour.
- Si des messages d'erreur de base de données apparaissent après la mise à jour, assurez-vous de vérifier
  le lien **Système → Panneau de Maintenance → Base de données**. Dans certains
  cas, si une erreur de base de données se produit, cela empêchera toutes les
  mises à jour de la base de données de s'exécuter. Dans ce cas, vous pouvez les exécuter à partir du lien
  Base de données et ensuite utiliser la méthode **Système → Installer → Découvrir**
  pour vérifier et installer toutes les nouvelles extensions.
- Le processus de mise à jour crée ou ajoute à un fichier log nommé
administrator/logs/joomla_update.php que vous pouvez ouvrir avec un éditeur de texte pour
voir les étapes enregistrées dans le journal. Il affichera les étapes principales (télécharger le zip,
installer, exécuter les instructions SQL, nettoyer), quelque chose comme ceci :

```
2024-04-17T09:13:16+00:00    INFO 127.0.0.1    update    Mise à jour lancée par l'utilisateur Jimmy (139). L'ancienne version est 5.0.3.
2024-04-17T09:13:18+00:00    INFO 127.0.0.1    update    Téléchargement du fichier de mise à jour depuis ...
2024-04-17T09:13:28+00:00    INFO 127.0.0.1    update    Fichier Joomla_5.1.0-Stable-Update_Package.zip téléchargé.
2024-04-17T09:13:28+00:00    INFO 127.0.0.1    update    Début de l'installation de la nouvelle version.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Finalisation de l'installation.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Début des mises à jour SQL.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    La version actuelle de la base de données (schéma) est 5.0.0-2023-09-11.
... Beaucoup de requêtes SQL individuelles
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Fin des mises à jour SQL.
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Désinstallation des extensions
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Suppression des fichiers et dossiers supprimés.
2024-04-17T09:13:44+00:00    INFO 127.0.0.1    update    Nettoyage après installation.
2024-04-17T09:13:44+00:00    INFO 127.0.0.1    update    Mise à jour vers la version 5.1.0 terminée.
```

*Traduit par openai.com*
