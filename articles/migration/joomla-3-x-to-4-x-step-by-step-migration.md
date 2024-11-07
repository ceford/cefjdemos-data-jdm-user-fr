<!-- Filename: Joomla_3.x_to_4.x_Step_by_Step_Migration / Display title: Joomla 3 à 4 Étape par Étape -->

## Introduction

**Attention :** Ce guide suppose que vous commencez avec Joomla 3.10.x. Si vous êtes sur une version antérieure, assurez-vous de mettre à jour vers Joomla 3.10 d'abord avant de passer à Joomla 4. Il n'y a pas de précipitation. Assurez-vous que toutes vos extensions sont prêtes pour Joomla 4.x. Joomla 3.10.x est pris en charge jusqu'au 16 août 2023.

Voici les instructions étape par étape pour migrer un site 3.10.x vers Joomla! 4.x. Bien qu'il existe des centaines de scénarios différents, cela vous donnera la procédure de base à suivre. Les migrations très complexes seront probablement dues aux extensions tierces installées. Nous vous encourageons à contacter les développeurs des extensions tierces installées sur votre site Joomla pour connaître leur chemin suggéré pour migrer leurs extensions.

## Étape par Étape

### Configurer un Lieu de Développement

1. Assurez-vous de faire fonctionner la version Joomla 3.10.x la plus récente avant de continuer.
2. Faites une sauvegarde de votre site en direct 3.10.x. Vous pouvez utiliser un outil suggéré (voir les *Outils Suggérés* en bas de la page) ou le faire manuellement.
   - [Notions de Base sur la Sauvegarde pour un Site Web Joomla!](https://docs.joomla.org/Special:MyLanguage/Backup_Basics_for_a_Joomla!_Web_Site)
   - [Quelles sont les meilleures pratiques pour les sauvegardes de site ?](https://docs.joomla.org/Special:MyLanguage/What_are_the_best_practices_for_site_backups%3F)
3. Assurez-vous que votre environnement répond aux
   [exigences techniques pour Joomla 4](https://downloads.joomla.org/technical-requirements) avant de continuer.
4. Créez une nouvelle base de données et un nouvel utilisateur pour restaurer votre site 3.10.x.
5. Créez un site de test ou une zone de construction pour travailler dedans et restaurez la copie de sauvegarde de votre site 3.10.x à l'un des endroits suivants :
   - Un sous-domaine.
   - Un sous-répertoire.
   - Un appareil local. Joomla dispose d'un tutoriel détaillé sur l'installation de XAMPP. Cependant, [WAMP](https://www.wampserver.com/en/), [MAMP](https://www.mamp.info/fr/windows/) et [LAMP](https://sourceforge.net/projects/lampas/) sont toutes des alternatives adaptées.
   - Un nouveau compte d'hébergement sur un domaine temporaire à la racine. (Si vous souhaitez changer d'hôte pendant la migration.)
     - Restaurez un site sur un appareil local. Voir [Installation de Joomla localement](https://docs.joomla.org/Special:MyLanguage/Installing_Joomla_locally) et [Configuration de votre station de travail pour le développement Joomla](https://docs.joomla.org/Special:MyLanguage/Setting_up_your_workstation_for_Joomla_development).
     - Restaurez un site avec un outil répertorié en bas de la page. (Lisez la documentation du développeur.)
6. Dans votre lieu de test, mettez à jour votre instance Joomla! 3.10.x à la dernière version de maintenance.
7. Assurez-vous que votre schéma de base de données est mis à jour vers la dernière version 3.10.x en allant dans **Gestionnaire d'extensions → Onglet Base de données**. Si votre schéma n'est pas à jour comme dans l'image suivante, cliquez sur le bouton **Corriger** :<br>
   ![base de données des extensions joomla 3](../../../en/images/migration/admin-extension-database-fix.png)
8. Videz la corbeille : avez-vous des articles dans la corbeille ? Si c’est le cas, supprimez-les (et tous les médias pertinents qui peuvent y être associés et qui ne sont pas utilisés ailleurs sur le site). Les articles (catégories et éléments de menu également) laissés dans la corbeille peuvent causer des problèmes lors d’une migration sans erreurs.
9. Testez.
10. Sauvegardez à nouveau.

### Évaluer Chaque Extension

Lors de votre planification, vous avez déterminé quelles extensions tierces restaient ou partaient et comment elles migraient. Pour cette partie de l'étape par étape, vous utiliserez intensivement deux sections différentes du site : le *Vérificateur de Mise à Jour* dans **Composants → Mise à Jour Joomla!** et **Extensions → Gérer → Gérer**. Vous allez examiner chaque extension installée sur votre site. Vous déterminerez si elles doivent être mises à jour vers la dernière version ou désinstallées. Plus de détails dans [Vérificateur de Mise à Jour](https://docs.joomla.org/Special:MyLanguage/:Pre-Update_Check).

1. Utiliser le **Vérificateur de Mise à Jour** pour utiliser le Vérificateur de Mise à Jour, vous devrez configurer le composant de Mise à Jour Joomla! sur Joomla 4. Pour ce faire, suivez :
2. Allez dans **Composants → Mise à Jour Joomla!** Il devrait dire qu'aucune mise à jour n’est trouvée. Si ce n'est pas le cas, mettez à jour Joomla à la dernière version (doit être 3.10.x) et testez. Ensuite, faites une autre sauvegarde. Cliquez sur le bouton Options en haut à droite.
3. Sélectionnez *Joomla Next* dans le menu déroulant pour Canal de Mise à Jour.<br>
   ![sélection du canal d'options de mise à jour](../../../en/images/migration/update-options-channel.png)
4. Cliquez sur **Enregistrer & Fermer**
5. Vous verrez alors votre Version Joomla Installée, la dernière version Joomla! et l’URL pour le package de mise à jour. Joomla vous montrera à nouveau les exigences pour Joomla 4. Si cela signale que vous avez soit un système incompatible soit des extensions, cela vous le dira ici. Prenez un moment pour examiner cette page. <br>
   ![mise à jour sur 4 vérificateur de mise à jour](../../../en/images/migration/update-to-4-pre-update-check.png)
   <div class="alert alert-warning"><strong>Remarque :</strong> Ne mettez PAS à jour vers Joomla! 4 pour l’instant. Cela sert uniquement à préparer vos extensions tierces et à rendre le site compatible avec Joomla! 4.</div>
6. Examinez le Vérificateur de Mise à Jour et le Vérificateur de Mise à Jour des Extensions dans l’onglet Vérificateur de Mise à Jour du composant Mise à Jour Joomla. Si une extension qui n'est pas dans votre planification est répertoriée ici, ajoutez-la à votre liste d'extensions à examiner.
7. Si vous avez migré de Joomla! 2.5 vers 3.x dans le passé, il peut y avoir des extensions résiduelles à nettoyer. Ce sont les extensions 2.5 ou 3.x plus anciennes qui doivent être désinstallées avant de passer à Joomla 4 :
   - plg_content_geshi
   - Template de l'Administrateur Bluestork
   - Beez_20
   - Beez5
   - Atomic
   1. Pour ce qui est des templates, désinstallez tous les templates principaux du frontend ou de l'administrateur sauf Protostar et Beez3 (templates frontend) et Isis ou Hathor (templates administrateurs). **REMARQUE : Protostar n'est PAS compatible avec Joomla 4**. Lors de la migration, il disparaîtra. Vous devez avoir un template sélectionné par défaut et vous pouvez utiliser Protostar ou Beez3. Protostar disparaîtra lors de la migration vers Joomla 4.x.
   2. Si vous rencontrez d'autres fichiers à désinstaller, veuillez les ajouter à cette page. C’est un wiki donc n’importe qui peut ajouter à la page. Merci d'avance pour votre service.
8. Vous remarquerez les étiquettes indiquant si une extension est compatible ou non. Ces étiquettes indiquent généralement la vraie histoire s’ils disent Non ou Oui. S’ils indiquent *Étiquette de Compatibilité Manquante*, cela signifie que le développeur de l’extension n’a pas utilisé d'étiquette dans leur extension, nous ne savons donc pas si elle est compatible ou non avec Joomla 4. Parlez au développeur pour vérifier.
9. **Mettre à jour les Extensions :** mettez à jour toutes les extensions que vous garderez sur votre site. Dans Joomla! 3.10.x, vous pouvez aller à **Gestionnaire d'extensions → Onglet Mise à jour** et cliquer sur **Rechercher des mises à jour** qui ajoutera une info-bulle dans la colonne Version, sous l'onglet Gérer, fournissant certaines informations de compatibilité depuis le backend. Fonctionnalité qui ne prend en charge que les extensions mises à jour via l'onglet Mise à Jour du Gestionnaire d'Extensions. Si vous avez installé des extensions qui n’utilisent pas la mise à jour de l’extension Joomla, elles doivent être évaluées manuellement comme détaillé ci-dessous. Il en va de même pour ces extensions qui ont une info-bulle. Vous devrez encore vérifier le type de package et le chemin de migration avec le développeur de l’extension pour vérifier comment procéder à la mise à niveau/migration.
10. Examinez et Désinstallez les Extensions Extensions : allez dans **Gestionnaire d'extensions → Gérer**
11. Cliquez sur le Bouton *Outils de Recherche* pour afficher les options de filtrage
12. Sélectionnez Package dans le menu déroulant *Sélectionner le Type.*<br>
    ![page de gestion des extensions](../../../en/images/migration/extensions-manage.png)
    <div class="alert alert-info">Il est recommandé de sélectionner d'abord Package, car si vous avez besoin de désinstaller quelque chose dans un package, cela désinstallera automatiquement les modules, plugins ou tout autre élément associé au package en une seule fois.</div>
13. Désinstallez tous les Packages qui ne sont plus nécessaires ou qui ne migreront pas vers Joomla 4.
14. Répétez ce processus de passage en revue de l'onglet Gérer pour tous les Types dans le menu déroulant : Composant, Fichier, Langue, Bibliothèque, Module, Plugin et Template. Si l’Auteur indique Projet Joomla!, laissez ces extensions tranquilles. Pour tous les autres, assurez-vous de désinstaller ceux qui ne sont pas utilisés ou non compatibles avec Joomla! 4.x. 
    <div class="alert alert-danger"><strong>REMARQUE !</strong> Vous ne pourrez pas désinstaller un template défini par défaut. Vous devrez sélectionner un template Core pris en charge comme Beez3 ou Protostar, puis désinstaller le template si vous devez le faire.
    <em>Un autre rappel :</em> <strong>Protostar n'est pas compatible avec Joomla 4</strong>. Lors de la migration, il disparaitra. Le sélectionner par défaut vous amène simplement à Joomla 4.x.</div>
15. Faites une note des versions de Packages et Composants actuellement utilisés que vous garderez sur votre site. Vous pouvez les copier/coller dans un document pour référence.
16. Pour toute extension que vous conservez mais qui n'utilise pas le Gestionnaire d'Extensions pour la mise à jour en un clic (**Extensions → Gérer → Mise à jour**), mettez à jour toutes les extensions vers les dernières versions.
17. Avant et pendant que vous mettez à jour, notez si les extensions ont à la fois des versions 3.10.x et 4.x dans le même package. Si tel est le cas, elles seront bien pour la *mise à jour en un clic*. Sinon, et si les paquets 3.10 et 4.x sont différents, vous devrez les examiner au cas par cas. Ils tomberont normalement dans l'un des scénarios suivants :
    - L'extension dispose de paquets séparés mais lors de la mise à niveau vers 4.x, elle les détecte automatiquement et continue de fonctionner. Assurez-vous que le développeur le confirme.
    - L'extension dispose de paquets séparés qui doivent être désinstallés dans 3.10.x puis installés avec la version Joomla 4.x une fois le site migré. Un exemple pourrait être un plugin de contenu. Il est très simple de le désinstaller dans 3.10.x puis de le réinstaller dans 4.x.
    - Consultez [Considérations sur les Modèles](https://docs.joomla.org/Special:MyLanguage/Template_Considerations_During_Migration)
      pour plus d'informations spécifiques sur les modèles et 
      [Conversion d'un modèle de version Joomla! antérieure](https://docs.joomla.org/J3.x:Converting_A_Previous_Joomla!_Version_Template)

#### Notes sur Search (com_search)

Search (com_search) sera découplé dans Joomla 4.x. Search (com_search) migrera vers Joomla 4. Après la migration, vous devrez le mettre à jour vers la version Joomla 4.x via com_installer. Il continuera d'être maintenu, mais plus à la manière d'une extension tierce en recevant des mises à jour via com_installer. Il est recommandé d'utiliser Smart Search (com_finder) à l'avenir. Search est toujours disponible dans le [Répertoire des Extensions Joomla](https://extensions.joomla.org/category/official-extensions/).

#### Notes sur les Weblinks

Les Weblinks ont été découplés dans Joomla 3.4. Si cela était utilisé sur un site 2.5, le processus de migration le note et migre le composant Weblinks et les données. Pour la migration de 3.10.x vers 4.x, cela sera pareil. Il est toujours disponible et maintenu sur le JED à [Extensions Officielles](https://extensions.joomla.org/category/official-extensions).

#### Notes sur le Routage Hérité

Le routage hérité ne sera pas disponible dans Joomla 4.x. Seul le Mode Moderne sera disponible. Lors de la migration, si vous utilisez le routage Hérité, le système les changera automatiquement en Mode Moderne. Vous voudrez exécuter un vérificateur de liens cassés sur votre site après avoir migré vers Joomla 4.x et *avant de passer en ligne*.

### Passer à Joomla! 4.x

Une fois que vous avez soit mis à jour, soit désinstallé vos extensions tierces afin que seules celles compatibles avec Joomla! 4 restent dans votre installation, continuez avec les étapes suivantes :

1. Allez dans **Système → Configuration Globale → Onglet Serveur** et réglez le Reporting des Erreurs de Système sur Maximum. Assurez-vous d'Enregistrer & Fermer. <br>
   ![configuration globale du système onglet serveur](../../../en/images/migration/system-global-configuration-server-tab.png)
2. Faites une autre sauvegarde.
3. Allez dans **Composants → Mise à Jour Joomla**. (Il devrait dire qu'aucune mise à jour n'est trouvée. Si ce n'est pas le cas, mettez à jour Joomla vers la dernière version et testez. Ensuite, faites une autre sauvegarde.) Cliquez sur le bouton Options en haut à droite.
4. Sélectionnez *Joomla Next* dans le menu déroulant pour Canal de Mise à Jour.<br>
   ![sélection du canal de mise à jour de composant joomla](../../../en/images/migration/update-select-channel.png)
5. Cliquez sur **Enregistrer & Fermer**.
6. Vous verrez alors votre Version Joomla Installée, la Dernière version Joomla! et l’URL pour le package de mise à jour. Joomla vous montrera à nouveau les exigences pour Joomla 4. Si cela signale que bạn avez un système incompatible ou des extensions, cela vous le dira ici. Prenez un moment pour examiner cette page.<br>
   ![vérification de mise à jour pour joomla 4](../../../en/images/migration/update-check.png)
7. Si la mise à jour n'apparaît pas, allez dans **Gestion des extensions → Mise à jour** et appuyez sur Vider le Cache depuis la barre d'outils. Maintenant, la mise à jour vers Joomla 4 devrait apparaître.
8. Croisez les doigts, et assurez-vous que vous avez cette sauvegarde disponible en cas de besoin.
9. Cliquez sur le bouton Installer la Mise à Jour.
10. Faites du thé pendant que la barre de statut charge jusqu'à être entièrement verte. Le temps que cela prend dépend de votre site, de la connexion Internet et de la vitesse du serveur. Le processus prend environ deux minutes. Une fois la mise à jour terminée, vous serez probablement déconnecté de l'Administrateur. Connectez-vous encore une fois. Deux fois.
11. Si tout se passe bien, vous verrez un tout nouveau look pour le panneau d'administration en arrière-plan.<br>
    ![joomla 4 ou 5 tableau de bord d'accueil](../../../en/images/migration/j4-home-dashboard.png)
12. Allez dans **Système → Maintenance → Base de données** et cliquez sur *Corriger* si des erreurs apparaissent.
13. Dans **Système → Installer → Découvrir**, voyez s'il y a des extensions à installer. (Il ne devrait y en avoir aucune !)
14. Allez sur le frontend de votre site et voyez si cela apparaît même si ce n'est pas le bon modèle. Si c'est le cas, continuez. Si ce n'est pas le cas, consultez les erreurs courantes lors de la migration.
15. Faites une sauvegarde.
16. Installez votre nouveau modèle ou d'autres extensions si vous en avez à installer. Sauvegardez souvent.
17. Configurez-les. Sauvegardez souvent.
18. Exécutez un vérificateur de liens cassés et corrigez les liens cassés.
19. Testez tout. Sauvegardez souvent.
20. Si tout fonctionne comme prévu, réglez à nouveau le Reporting des Erreurs sur Default Système (**Système → Configuration Globale → Onglet Serveur**). Assurez-vous d**'Enregistrer & Fermer**.

### Mettre en Ligne votre Site Joomla! 4.x

1. Lorsque vous êtes prêt à mettre en ligne, sauvegardez votre site 3.10 pour la dernière fois. Restaurez-le dans un sous-répertoire ou un sous-domaine si vous le souhaitez.
2. Sauvegardez votre site Joomla! 4.x et déplacez ou restaurez votre site Joomla! 4.x à la racine (ou changez les serveurs de noms si vous créiez sur un domaine temporaire à la racine d’un nouveau compte d’hébergement).
3. Testez à nouveau.
4. SI vous avez apporté des modifications de sécurité au fichier .htaccess dans le passé, vous devrez peut-être changer une ligne (ou des lignes) pour mettre à jour vers la prochaine version de Joomla 4. Veuillez aller sur
   [Modifications Htaccess après Joomla 4](https://docs.joomla.org/Htaccess_changes_after_joomla4.0.4) pour déterminer si vous devez modifier votre fichier ou non.
5. Supprimez le site Joomla! 3.10 du serveur dans les deux jours, sauf si vous avez modifié votre fichier *robots.txt* pour empêcher les moteurs de recherche de l'explorer.
6. Supprimez tous les sites de développement sur lesquels vous avez travaillé ou tenez-les à jour s'ils fonctionnent sur une version actuelle afin de prévenir les tentatives de piratage sur votre serveur.

Si vous avez eu des changements de données sur le site 3.10 pendant que vous migriez vers 4.x, vous voudrez transférer ces données sur le site 4.x avant de passer en ligne. Vous pouvez le faire manuellement (assurez-vous de conserver les mêmes IDs d'utilisateurs - procédez dans l'ordre) ou en utilisant une [extension tierce](https://extensions.joomla.org/category/migration-a-conversion/data-import-a-%20export%20transfer%20tool/third-party%20extension/).

## Outils suggérés

- [Akeeba Backup](http://extensions.joomla.org/extensions/access-a-security/site-security/backup/1606)
  est très populaire pour la sauvegarde et la restauration.
- Plus d'[outils de sauvegarde](https://extensions.joomla.org/tags/backup/).

*Traduit par openai.com*

