<!-- Filename: Joomla_3.x_to_4.x_Step_by_Step_Migration / Display title: Migration Joomla 3.x vers 4.x étape par étape -->

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Attention !

Ce guide suppose que vous démarrez sur Joomla 3.10.x. Si vous êtes sur
une version antérieure, assurez-vous de mettre à niveau vers Joomla 3.10
avant de passer à Joomla 4. Il n'y a pas d'urgence. Assurez-vous que
toutes vos extensions sont prêtes pour Joomla 4.x. Joomla 3.10.x sera
supporté jusqu'au 16 août 2023.


Voici les instructions étape par étape pour migrer votre site 3.10.x
vers Joomla ! 4.x. Bien qu'il existe des centaines de scénarios
différents, ceci vous donnera la procédure de base à suivre. Les
migrations très complexes seront probablement le résultat d'extensions
tierces installées. Nous vous encourageons à contacter les développeurs
des extensions tierces installées sur votre site Joomla pour connaître
le chemin qu'ils suggèrent pour migrer leurs extensions.

## Intro

La migration de Joomla ! 3.10.x vers 4.x est considérée comme une
mini-migration. En effet, les extensions de base de Joomla seront mises
à niveau en un seul clic via le composant de mise à jour de Joomla !
dans la partie administrateur de Joomla. De nombreuses extensions
tierces peuvent également être mises à niveau en un clic. D'autres ne le
sont pas. Vous devez examiner chacune d'entre elles et déterminer le
chemin que l'extension doit suivre pour passer de la version 3.10 à la
version 4.x. Si vous ne l'avez pas encore fait, vous pourriez être
intéressé par la lecture des documents suivants :
Auto-évaluation
et  Planification de la migration de 3.10 à
4.x
avant de suivre les étapes suivantes
Les extensions de base de Joomla ! sont :

- Catégories
- Articles
- Menus
- Modules (modules de base - pas de modules tiers)
- Journaux d'activité
- Bannières
- Champs
- Historique du contenu
- Contacts
- Messagerie
- Flux d'actualités
- Redirections
- Recherche (séparé en 4.x. Les sites 3.x existants pourront toujours
  migrer. Cependant, nous recommandons d'utiliser La recherche avancée à
  l'avenir. Voir les notes de la section Évaluation de chaque extension)
- Recherche avancée
- Tags
- Liens web (séparé mais votre site peut l'utiliser et il migrera. Voir
  les notes de la section Évaluation de chaque extension)

## Etape par étape

### Créez un environnement de développement

1.  Assurez-vous que vous exécutez la dernière version de Joomla 3.10.x
    avant de poursuivre.
2.  Faites une sauvegarde de votre site 3.10.x. Vous pouvez utiliser un
    outil suggéré (voir les *Outils suggérés* en bas de page) ou vous
    pouvez le faire manuellement.
    -  Principes de base de la sauvegarde d'un site web
      Joomla !
    -  Quelles sont les meilleures pratiques pour les sauvegardes de
      sites ?
3.  Assurez-vous que votre environnement est conforme aux
    <a href="https://downloads.joomla.org/technical-requirements"
    class="external text" target="_blank"
    rel="noreferrer noopener">exigences techniques pour Joomla 4</a>
    avant de poursuivre.
4.  Créez une nouvelle base de données et un nouvel utilisateur pour
    restaurer votre site 3.10.x.
5.  Créez un site de test ou une zone de développement pour travailler
    et restaurez la copie de sauvegarde de votre site 3.10.x à l'un des
    endroits suivants :
    - Un sous-domaine.
    - Un sous-répertoire.
    - Un périphérique local. Joomla a un tutoriel détaillé sur
      l'installation de
      <a href="https://sourceforge.net/projects/xampp/" class="external text"
      target="_blank" rel="nofollow noreferrer noopener">XAMPP</a> à
      XAMPP. Cependant,
      <a href="https://www.wampserver.com/en/" class="external text"
      target="_blank" rel="nofollow noreferrer noopener">WAMP</a>,
      <a href="https://www.mamp.info/en/windows/" class="external text"
      target="_blank" rel="nofollow noreferrer noopener">MAMP</a>,
      <a href="https://sourceforge.net/projects/lampas/" class="external text"
      target="_blank" rel="nofollow noreferrer noopener">LAMP</a> sont
      toutes des alternatives appropriées.
    - Un nouveau compte d'hébergement sur un domaine temporaire à la
      racine. (Si vous souhaitez changer d'hébergement au cours du
      processus de migration).
      - Restauration d'un site sur un périphérique local. Voir
         Installation de Joomla
        localement
        et [Configuration de votre poste de travail pour le
        développement de
        Joomla](https://docs.joomla.org/Setting_up_your_workstation_for_Joomla_development "Special:MyLanguage/Setting up your workstation for Joomla development").
      - Restauration d'un site avec un outil listé en bas de page.
        (Lisez la documentation du développeur).
6.  Dans votre emplacement de test, mettez à jour votre instance
    Joomla ! 3.10.x vers la dernière version de maintenance.
7.  Assurez-vous que vous avez le dernier schéma de base de données mis
    à jour vers la dernière version 3.10.x en allant dans l'onglet
    **Gestion des Extensions **→** Base de données**. Si votre schéma
    n'est pas à jour comme dans l'image suivante, cliquez sur le bouton
    **Corriger** :<img
    src="https://docs.joomla.org/images/thumb/6/61/J310-admin-extension-database-fix-en.png/800px-J310-admin-extension-database-fix-en.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/6/61/J310-admin-extension-database-fix-en.png/1200px-J310-admin-extension-database-fix-en.png 1.5x, https://docs.joomla.org/images/thumb/6/61/J310-admin-extension-database-fix-en.png/1600px-J310-admin-extension-database-fix-en.png 2x"
    data-file-width="2560" data-file-height="812" width="800" height="254"
    alt="J310-admin-extension-database-fix-en.png" />
8.  Vider la corbeille : Avez-vous des articles dans la corbeille ? Si
    c'est le cas, supprimez-les (ainsi que tous les médias qui peuvent
    leur être associés s'ils ne sont pas utilisés ailleurs sur le site).
    Les articles (ainsi que les catégories et les éléments de menu)
    laissés dans la corbeille peuvent empêcher une migration de se
    terminer sans erreur.
9.  Tester.
10. Faites une nouvelle sauvegarde.

### Evaluer chaque extension

Dans votre
planning,
vous avez déterminé quelles extensions tierces restaient ou partaient et
comment elles migraient. Pour cette partie de l'étape par étape, vous
allez utiliser deux sections différentes du site de manière intensive ;
La vérification avant mise à jour dans

Composants

 Vérification avant mise à jour.

1.  Utilisation du contrôle de "pré-mise à jour" : pour pouvoir utiliser
    le contrôle de pré-mise à jour, vous devez configurer le composant
    de mise à jour de Joomla ! pour Joomla 4. Pour ce faire, procédez
    comme suit :
2.  Allez sur **Components **→** Mise à jour de Joomlaǃ**. (Il devrait
    indiquer qu'aucune mise à jour n'a été trouvée. Si ce n'est pas le
    cas, mettez à jour Joomla à la dernière version (doit être 3.10.x)
    et testez. Puis faites une autre sauvegarde). Cliquez sur le bouton
    Paramètres dans le coin supérieur droit.
3.  Sélectionnez *Le prochain Joomlaǃ* dans le menu déroulant pour le
    canal de mise à jour.<img
    src="https://docs.joomla.org/images/thumb/7/72/Migration_J3toJ4_update_channel-en.png/800px-Migration_J3toJ4_update_channel-en.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/7/72/Migration_J3toJ4_update_channel-en.png 1.5x"
    data-file-width="1000" data-file-height="384" width="800" height="307"
    alt="Migration J3toJ4 update channel-en.png" />
4.  Cliquez sur Enregistrer et fermer
5.  Vous verrez alors votre version installée de Joomla, la dernière
    version de Joomla ! et l'URL du package de mise à jour. Joomla vous
    montrera à nouveau la configuration requise pour Joomla 4. S'il
    signale que vous avez un système ou des extensions incompatibles, il
    vous le dira ici. Prenez un moment pour consulter cette page.<img
    src="https://docs.joomla.org/images/thumb/3/3a/J310-admin-update_to_4-pre_update_check-en.png/800px-J310-admin-update_to_4-pre_update_check-en.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/3/3a/J310-admin-update_to_4-pre_update_check-en.png 1.5x"
    data-file-width="1200" data-file-height="559" width="800" height="373"
    alt="J310-admin-update to 4-pre update check-en.png" />
6.  Regardez le contrôle de pré-mise à jour et le contrôle de pré-mise à
    jour des extensions dans l'onglet Contrôle de pré-mise à jour du
    composant Joomla Update. Si une extension qui n'est pas dans votre
    planning est listée ici, ajoutez-la à votre liste d'extensions à
    examiner.
7.  Si vous avez migré de Joomla ! 2.5 à 3.x dans le passé, il peut y
    avoir quelques extensions restantes qui doivent être nettoyées.
    Voici les anciennes extensions 2.5 ou 3.x qui doivent être
    désinstallées avant la mise à jour vers Joomla 4 :
    - plg_content_geshi
    - template admin Bluestork
    - Beez_20
    - Beez5
    - Atomic

    1.  En ce qui concerne les templates, désinstallez tous les
        templates frontend ou backend de base, sauf Protostar et Beez3
        (templates frontend) et Isis ou Hathor (templates
        administrateur). **NOTE : Protostar n'est PAS compatible avec
        Joomla 4**. Lors de la migration, il disparaîtra. Vous aurez
        besoin d'avoir un template sélectionné comme "par défaut" et
        vous pouvez utiliser Protostar ou Beez3. Protostar disparaîtra
        lors de la migration vers Joomla 4.x.
        1.  Si vous rencontrez d'autres fichiers qui doivent être
            désinstallés, veuillez les ajouter à cette page. Ceci est un
            wiki, donc tout le monde peut ajouter à la page. Merci
            d'avance pour votre service.
8.  Vous remarquerez les balises indiquant si une extension est
    compatible ou non. Ces balises indiquent généralement la vérité si
    elles disent Non ou Oui. Si elles disent "Balise de compatibilité
    manquante", cela signifie que le développeur de l'extension n'a pas
    utilisé de balise dans son extension et que nous ne savons pas si
    elle est ou non compatible avec Joomla 4. Contactez le développeur
    pour vérifier.
9.  Mise à jour des extensions : mettez à jour toutes les extensions que
    vous conserverez dans votre site Web. Dans Joomla ! 3.10.x, vous
    pouvez aller dans **Gestionnaire d'extensions **→** onglet Mise à
    jour** et cliquer sur **Trouver les mises à jour** qui ajoutera une
    info-bulle dans la colonne Version, sous l'onglet Gérer, donnant
    quelques informations de compatibilité depuis le backend. Cette
    fonctionnalité ne prend en charge que les extensions qui se mettent
    à jour via l'onglet Mise à jour du gestionnaire d'extensions. Si
    vous avez installé des extensions qui n'utilisent pas la mise à jour
    des extensions Joomla, elles doivent être évaluées manuellement
    comme indiqué ci-dessous. Il en va de même pour les extensions qui
    ont une info-bulle. Vous devrez toujours vérifier le type de paquet
    et le chemin de migration avec le développeur de l'extension pour
    vérifier comment mettre à niveau/migrer.
10. Désinstaller et examiner les extensions : allez dans **Gestionnaire
    d'extensions **→** onglet Gérer**.
11. Cliquez sur le bouton *Outils de recherche* pour afficher les
    options de filtrage.
12. Sélectionnez le package dans la liste déroulante.<img
    src="https://docs.joomla.org/images/thumb/5/50/J310-admin-extension-manage-package-en.png/800px-J310-admin-extension-manage-package-en.png"
    decoding="async"
    srcset="https://docs.joomla.org/images/thumb/5/50/J310-admin-extension-manage-package-en.png/1200px-J310-admin-extension-manage-package-en.png 1.5x, https://docs.joomla.org/images/5/50/J310-admin-extension-manage-package-en.png 2x"
    data-file-width="1502" data-file-height="658" width="800" height="350"
    alt="J310-admin-extension-manage-package-en.png" />Il est recommandé
    de sélectionner d'abord le package, car si vous devez désinstaller
    quelque chose dans un package, il désinstallera automatiquement et
    en une seule fois les modules, les plugins ou tout autre élément
    associé dans le package.
13. Désinstallez tous les packages qui ne sont plus nécessaires ou qui
    ne seront pas transférés vers Joomla 4.
14. Répétez ce processus en passant par l'onglet Gérer pour tous les
    types dans la liste déroulante : Composant, Fichier, Langue,
    Bibliothèque, Module, Plugin et Template. Si l'auteur indique projet
    Joomla, ne touchez pas à ces extensions. Pour toutes les autres,
    assurez-vous de désinstaller celles qui ne sont pas utilisées ou qui
    ne sont pas compatibles avec Joomla! 4.x. **NOTE!** Vous ne pourrez
    pas désinstaller un template qui est défini par défaut. Vous devrez
    sélectionner un template supporté par Core comme Beez3 ou Protostar
    et ensuite désinstaller le template si vous avez besoin de le
    faire.
    *Autre rappel :'* **Protostar n'est pas compatible avec Joomla
    4.x**. Lors de la migration, il disparaîtra. En le sélectionnant par
    défaut, vous arrivez simplement à Joomla 4.x.
15. Notez toutes les versions des packages et des composants en cours
    d'exécution que vous conserverez sur votre site. Vous pouvez les
    copier/coller dans un document pour référence.
16. Pour toutes les extensions que vous gardez mais n'utilisez pas le
    gestionnaire d'extensions pour mettre à jour en un clic
    (**Extensions **→** Gérer **→** Mettre à jour**) mettez à jour
    toutes les extensions avec les dernières versions.
17. Avant et pendant la mise à jour, notez si les extensions ont les
    versions 3.10.x et 4.x dans le même package. Si c'est le cas, elles
    pourront être mises à jour en un clic. Si ce n'est pas le cas, et
    que les versions 3.10 et 4.x ont des packages différents, vous devez
    les examiner au cas par cas. En règle générale, elles relèvent de
    l'un des scénarios suivants :
    - L'extension a des packages séparés mais lors de la mise à jour
      vers 4.x, ils détectent automatiquement cela et fonctionnent
      toujours. Assurez-vous que le développeur le confirme.
    - L'extension a des packages séparés qui doivent être désinstallés
      dans 3.10.x et ensuite installés avec la version de Joomla 4.x une
      fois que le site est migré. Un exemple de ceci pourrait être un
      plugin de contenu. Il est très simple de le désinstaller en 3.10.x
      puis de le réinstaller en 4.x.
    - Voir  Considérations sur les
      templates
      pour des informations plus spécifiques sur les templates et
       Conversion d'un template précédent de version de
      Joomla !
      .

#### Notes sur la recherche (com_search)

Search (com_search) sera séparé de Joomla 4.x. La recherche (com_search)
migrera vers Joomla 4. Après la migration, vous devrez le mettre à jour
vers la version de Joomla 4.x via com_installer. Il continuera à être
maintenu, mais plus de la même manière qu'une extension tierce en
recevant des mises à jour via com_installer. Il est recommandé
d'utiliserla Recherche avancée (com_finder) à l'avenir. La recherche
sera toujours disponible à l'adresse
<a href="https://extensions.joomla.org/category/official-extensions/"
class="external free" target="_blank"
rel="noreferrer noopener">https://extensions.joomla.org/category/official-extensions/</a>
.

#### Notes sur les liens web

Les liens Web ont été dissociés dans la version 3.4 de Joomla. S'il
était utilisé sur un site 2.5, le processus de migration en prendrait
note et migrerait le composant liens web et ses données. Pour la
migration de 3.10.x à 4.x, il en sera de même. Il est toujours
disponible et maintenu sur le JED à l'adresse
<a href="https://extensions.joomla.org/category/official-extensions/"
class="external text" target="_blank" rel="noreferrer noopener">Official
Extensions</a>.

#### Notes sur l'ancien routage d'URL

L'ancien routage ne sera pas disponible dans Joomla 4.x. Seul le routage
moderne sera disponible. Lorsque vous effectuez la migration, si vous
utilisez le routage héritage, le système le changera automatiquement en
routage moderne. Vous devrez exécuter un vérificateur de liens brisés
sur votre site après la migration vers Joomla 4.x et "avant de mettre en
ligne".

### Passage à Joomla ! 4.x

Une fois que vous avez mis à jour ou désinstallé vos extensions tierces
pour que seules celles compatibles avec Joomla ! 4 restent dans votre
installation, continuez avec les étapes suivantes :

1.  Allez dans **Système **→** Configuration **→** onglet Serveur** et
    faites passer le rapport d'erreur de de Défaut à Maximum. Veillez
    enregistrer et fermer. <img
    src="https://docs.joomla.org/images/thumb/8/84/J310-system-global-config-server-tab-en.png/500px-J310-system-global-config-server-tab-en.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/8/84/J310-system-global-config-server-tab-en.png/750px-J310-system-global-config-server-tab-en.png 1.5x, https://docs.joomla.org/images/thumb/8/84/J310-system-global-config-server-tab-en.png/1000px-J310-system-global-config-server-tab-en.png 2x"
    data-file-width="1496" data-file-height="1002" width="500" height="335"
    alt="J310-system-global-config-server-tab-en.png" />
2.  Faites une autre sauvegarde.
3.  Allez sur **Composants **→** mise à jour de Joomla**. (Il devrait
    être indiqué qu'aucune mise à jour n'a été trouvée. Si ce n'est pas
    le cas, mettez à jour Joomla à la dernière version et testez. Puis
    faites une autre sauvegarde). Cliquez sur le bouton Options dans le
    coin supérieur droit.
4.  Sélectionnez 'Joomla Next *dans la liste déroulante pour le serveur
    de mise à jour.<img
    src="https://docs.joomla.org/images/thumb/f/fd/J310-component-joomla-update-select-support-en.png/500px-J310-component-joomla-update-select-support-en.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/f/fd/J310-component-joomla-update-select-support-en.png/750px-J310-component-joomla-update-select-support-en.png 1.5x, https://docs.joomla.org/images/thumb/f/fd/J310-component-joomla-update-select-support-en.png/1000px-J310-component-joomla-update-select-support-en.png 2x"
    data-file-width="1382" data-file-height="772" width="500" height="279"
    alt="J310-component-joomla-update-select-support-en.png" />*
5.  Cliquez sur Enregistrer et fermer.
6.  Vous verrez alors votre version installée de Joomla, la dernière
    version de Joomla ! et l'URL du paquet de mise à jour. Joomla vous
    montrera à nouveau la configuration requise pour Joomla 4. S'il
    signale que vous avez un système ou des extensions incompatibles, il
    vous le dira ici. Prenez un moment pour revoir cette page<img
    src="https://docs.joomla.org/images/thumb/a/a8/J310-to-j4-dev-update-found-en.png/800px-J310-to-j4-dev-update-found-en.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/a/a8/J310-to-j4-dev-update-found-en.png/1200px-J310-to-j4-dev-update-found-en.png 1.5x, https://docs.joomla.org/images/a/a8/J310-to-j4-dev-update-found-en.png 2x"
    data-file-width="1466" data-file-height="1079" width="800" height="589"
    alt="J310-to-j4-dev-update-found-en.png" />
7.  Si la mise à jour ne s'affiche pas, allez dans **Gestionnaire
    d'extension **→** Mise à jour** et cliquez sur Purge du Cache dans
    la barre d'outils. La mise à jour vers Joomla ! 4 devrait maintenant
    s'afficher.
8.  Croisez les doigts, et assurez-vous d'avoir cette sauvegarde
    disponible au cas où.
9.  Cliquez sur le bouton Installer la mise à jour.
10. Faites du thé pendant que la barre d'état passe au vert. Le temps
    que cela prend dépend de votre site, de votre connexion Internet et
    de la vitesse du serveur. Le processus prend environ deux minutes.
    Lorsque la mise à jour est terminée, vous serez probablement
    déconnecté de l'administrateur. Reconnectez-vous. Deux fois.
11. Si tout se passe bien, vous obtiendrez un tout nouveau look pour le
    panneau de l'administrateur du backend.<img
    src="https://docs.joomla.org/images/thumb/5/53/J4-administrator-overview-en.png/800px-J4-administrator-overview-en.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/5/53/J4-administrator-overview-en.png/1200px-J4-administrator-overview-en.png 1.5x, https://docs.joomla.org/images/thumb/5/53/J4-administrator-overview-en.png/1600px-J4-administrator-overview-en.png 2x"
    data-file-width="1640" data-file-height="752" width="800" height="367"
    alt="J4-administrator-overview-en.png" />
12. Allez dans **Système **→** Maintenance **→** Base de données** et
    cliquez sur *Réparer* si des erreurs apparaissent.
13. Dans **Système **→** Installation **→** Découvrir** voyez s'il y a
    des extensions à installer. (Il ne devrait pas y en avoir !)
14. Allez à l'interface de votre site et voyez s'il s'affiche même si ce
    n'est pas le bon template. Si oui, continuez. Si non, voir [les
    erreurs fréquentes lors d'une
    migration](https://docs.joomla.org/Joomla_3.10_to_4.x_Common_Migration_Errors "Special:MyLanguage/Joomla 3.10 to 4.x Common Migration Errors").
15. Faites une sauvegarde.
16. Installez votre nouveau template ou d'autres extensions si vous en
    avez à installer. Sauvegardez souvent.
17. Configurez-les. Sauvegardez souvent.
18. Exécutez un vérificateur de liens brisés et réparez tous les liens
    brisés.
19. Testez tout. Sauvegardez souvent.
20. Si tout fonctionne comme prévu, remettez le rapport d'erreur sur le
    système par défaut (**Système **→** Configuration
    globale **→** onglet Système de configuration**). Veillez à
    enregistrer et à fermer.

### Mise en service de votre site Joomla ! 4.x

1.  Lorsque vous êtes prêt à mettre en ligne, sauvegardez votre site
    3.10 pour la dernière fois. Restaurez-le dans un sous-répertoire ou
    un sous-domaine si vous le souhaitez.
2.  Sauvegardez votre site Joomla ! 4.x et déplacez ou restaurez votre
    site Joomla ! 4.x à la racine (ou changez les serveurs de noms si
    vous construisiez sur un domaine temporaire à la racine d'un nouveau
    compte d'hébergement).
3.  Testez à nouveau.
4.  Si vous aviez apporté des modifications de sécurité au fichier
    .htaccess, vous aurez peut-être à modifier une ou plusieurs lignes
    pour passer à la prochaine version de Joomla 4. Veuillez consulter
     Modifications du htaccess après Joomla
    4.0.4
    pour déterminer si vous devez modifier votre fichier ou non.
5.  Retirez le site Joomla ! 3.10 du serveur dans les deux jours qui
    suivent, sauf si vous avez modifié votre fichier *robots.txt* pour
    bloquer les robots des moteurs de recherche.
6.  Supprimez tous les sites de développement sur lesquels vous avez
    travaillé ou mettez-les à jour s'ils utilisent une version actuelle
    afin d'éviter toute tentative de piratage de votre serveur.

Si des données ont été modifiées sur le site 3.10 pendant la migration
vers la version 4.x, vous devrez les transférer sur le site 4.x avant la
mise en ligne. Vous pouvez le faire manuellement (assurez-vous de
conserver les mêmes identifiants d'utilisateur - allez-y dans l'ordre)
ou en utilisant une <a
href="https://extensions.joomla.org/category/migration-a-conversion/data-import-a-export%20transfer%20tool/third-party%20extension/"
class="external text" target="_blank"
rel="noreferrer noopener">extension tierce</a>.

## Outils suggérés

- <a
  href="http://extensions.joomla.org/extensions/access-a-security/site-security/backup/1606"
  class="external text" target="_blank" rel="noreferrer noopener">Akeeba
  Backup</a> est très populaire pour la sauvegarde et la restauration.
  Voir d'autres <a href="https://extensions.joomla.org/tags/backup/"
  class="external text" target="_blank" rel="noreferrer noopener">outils
  de sauvegarde</a>.

## Informations connexes
