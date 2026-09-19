<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Joomla 5 vers 6 \u00e9tape par \u00e9tape",
    "description": " ",
    "author": ""
}
-->

<div class="alert alert-warning">
<p class="h3">Avertissement</p>

Ce guide suppose que vous utilisez Joomla 5.4.x. Si vous utilisez une version antérieure, veillez à migrer ou à mettre à jour vers Joomla 5.4.x avant de procéder à la mise à niveau vers Joomla 6.x.
</div>

## Introduction

Bonne nouvelle pour Joomla 5.4.x vers 6.x : il s’agit d’une mise à niveau, et non d’une migration. Pourquoi ? Pour deux raisons principales :

- Les extensions Joomla 5 (J5) qui ont supprimé toutes les dépréciations de code, utilisent du code Joomla à jour et ne nécessitent pas l’activation du plug-in Behaviour - Backward Compatibility fonctionneront dans Joomla 6 (J6)
- La plupart des autres fonctionneront avec le nouveau plug-in Behaviour - Backward Compatibility 6 activé

Cette documentation reflète le processus simplifié en combinant la planification et les étapes détaillées dans un seul document. Vous aurez néanmoins besoin de certaines compétences. Consultez l’[[Migration Step by Step Self Assessment|auto-évaluation]] pour déterminer si vous devriez ou non effectuer vous-même la mise à niveau.

<div class="alert alert-info">
<p class="h3">Documentation destinée aux développeurs pour la mise à niveau de 5.4 vers 6.0 des extensions tierces.</p>

- [Éléments supprimés et incompatibilités](https://manual.joomla.org/60/removed-backward-incompatibility)
- [Nouvelles dépréciations](https://manual.joomla.org/60/new-deprecations)

- [Documentation sur les migrations](https://manual.joomla.org/migrations)
- [Nouvelles fonctionnalités](https://manual.joomla.org/60/new-features/)
</div>

## Planification de la migration de 5.4.x vers 6.x

### Spécifications d’hébergement/techniques

1. Déterminez si votre environnement d’hébergement répond aux exigences. Vous ne pourrez pas 
mettre à niveau vers Joomla 6 si l’environnement de votre serveur ne respecte pas les 
[exigences techniques](https://manual.joomla.org/docs/get-started/technical-requirements/) 
minimales. L’option de mise à niveau n’apparaîtra pas dans le composant de mise à jour de Joomla.
    - PHP 8.3
    - MySQL 8.0.13
    - MariaDB 10.6.x
    - PostgreSQL 14.0

Vous pouvez consulter les informations de votre système sur un site Joomla 5 en cliquant sur Système -> Informations système. Contactez votre fournisseur d’hébergement si votre serveur ne répond pas aux exigences.

![Tableau de bord du système avec le lien Informations système encadré](../../../en/images/migration/joomla-5-to-6-steps/01-steps-5-to-6-system-dashboard.png)

Voici un exemple d’environnement qui répond aux exigences techniques. Il affiche MySQL 8.0.43, PHP 8.3, Joomla 5.4.x et le plug-in de compatibilité ascendante désactivé.
![Informations système affichant la version de Joomla, la version de PHP, le type de base de données, la version de la base de données et le plug-in de compatibilité ascendante désactivé](../../../en/images/migration/joomla-5-to-6-steps/02-steps-5-to-6-system-information.png)

2. Vérifiez la compatibilité de toutes vos extensions avec Joomla 6. Il existe plusieurs scénarios concernant les extensions tierces pour cette mise à niveau.

    1. L’extension peut être compatible avec J5 et J6 SANS utiliser le plug-in de compatibilité ascendante.
    2. L’extension peut être compatible avec J5 et J6 EN utilisant le plug-in de compatibilité ascendante.
    3. L’extension peut sembler fonctionner dans J6, mais lorsque vous essayez de l’utiliser, elle ne fonctionne pas.
    4. L’extension peut rendre le site entier inutilisable.

Ne vous inquiétez pas ! Ce n’est pas aussi grave qu’il n’y paraît ! Commençons par parler des plug-ins de compatibilité ascendante.

<div class="alert alert-warning">
<p class="h3">Avertissement</p>

Pour effectuer une mise à niveau de Joomla 5.4.x vers 6.x, le plug-in de compatibilité ascendante pour Joomla 5 DOIT être DÉSACTIVÉ.
</div>

### Les plug-ins de compatibilité ascendante

Le plug-in [Behaviour - Backward Compatibility 6](https://manual.joomla.org/60/compat-plugin/) inclus avec Joomla 5.4.x vise à améliorer la compatibilité ascendante entre Joomla 5 et Joomla 6. Le plug-in aide les extensions tierces à utiliser des classes qui ne sont plus incluses dans Joomla 6. Il est implémenté en tant que type de plug-in « Behaviour » afin de garantir son chargement avant celui de tout autre plug-in.

![Page des plug-ins affichant les plug-ins de compatibilité ascendante](../../../en/images/migration/joomla-5-to-6-steps/03-steps-5-to-6-bc-plugins.png)

L’image ci-dessus montre deux plug-ins de compatibilité ascendante :

1. Behaviour - Backward Compatibility et
2. Behaviour - Backward Compatibility 6

Le plug-in Behaviour - Backward Compatibility (sans chiffre dans le nom du plug-in) est fourni avec Joomla 4.4.x afin de créer une couche de compatibilité ascendante pour les extensions Joomla 5. **Ce plug-in doit être désactivé avant la mise à niveau vers J6**.
Le plugin « Behaviour - Backward Compatibility 6 » est fourni avec Joomla 5.4.x afin de créer une couche de compatibilité descendante pour les extensions Joomla 6.

Les deux plugins ne peuvent pas être activés simultanément lors de la mise à niveau vers J6.

Avant de mettre à niveau Joomla 5 vers Joomla 6, le plugin « Behaviour - Backward Compatibility » (sans chiffre dans le nom du plugin) doit être désactivé. Vous devez vous assurer que toutes vos extensions tierces peuvent fonctionner sur votre site sans que le plugin « Behaviour - Backward Compatibility » soit activé avant de pouvoir effectuer la mise à niveau vers J6.

Après avoir vérifié que chacune de vos extensions tierces est compatible et pleinement fonctionnelle dans J5 sans que le plugin « Behaviour - Backward Compatibility » soit activé, vous pouvez le désactiver. Cela dit, nous vous recommandons de faire preuve de prudence. Avant de désactiver le plugin de compatibilité descendante, il est suggéré de faire l’une des deux choses suivantes :
1. Effectuez cette opération sur un site de développement ou de test. Ainsi, si vous oubliez accidentellement une extension qui rend votre interface d’administration inaccessible, cela ne mettra pas votre site de production hors service.
2. Assurez-vous d’avoir accès à la base de données. Ainsi, vous pourrez réactiver rapidement le plugin via la base de données si nécessaire. Vous trouverez plus d’informations ci-dessous.

Lors de la mise à niveau vers J5.4.x, le plugin « Comportement - Compatibilité ascendante 6 » sera automatiquement activé. Dans les nouvelles installations de J6, le plugin de compatibilité ascendante sera désactivé par défaut.

Le plugin « Comportement - Compatibilité ascendante 6 », qui prend en charge les extensions fonctionnant sous J5, sera disponible pendant toute la durée de J6. Dans J7, les extensions J5 ne seront plus rendues compatibles avec les versions précédentes par ce plugin. Cela donne aux développeurs d’extensions deux années supplémentaires pour rendre leurs extensions compatibles avec J6 sans le plugin de compatibilité ascendante. L’objectif est qu’à chaque version d’un cycle de vie, un plugin de compatibilité ascendante prenne en charge le cycle de vie qui la précède, jusqu’au cycle de vie suivant.
Pouvez-vous désactiver le plugin « Behaviour - Backward Compatibility 6 » dans J6 ? Excellente question. Après avoir vérifié que chacune de vos extensions tierces est compatible et pleinement fonctionnelle sans que le plugin de compatibilité descendante soit activé, vous pouvez désactiver le plugin « Behaviour - Backward Compatibility 6 ». Cela dit, nous vous recommandons de faire preuve de prudence. Avant de désactiver le plugin « Behaviour - Backward Compatibility 6 », il est suggéré de faire l’une des deux choses suivantes :

1. Faites-le sur un site de développement/test. Ainsi, si vous avez accidentellement oublié une extension qui rend votre interface d’administration inaccessible, cela ne mettra pas votre site de production hors service.
2. Assurez-vous d’avoir accès à la base de données. Ainsi, vous pourrez réactiver rapidement le plugin si nécessaire. Plus d’informations ci-dessous.

### Vérification préalable à la mise à jour ou gestion des extensions

En théorie, la vérification préalable à la mise à jour devrait vous indiquer si vos extensions tierces sont compatibles avec J6. Cependant, cette vérification n’est utile que si tous les développeurs d’extensions ont indiqué la compatibilité de leurs extensions. Dans un monde idéal, la section **Extensions** de la vérification préalable à la mise à jour vous indiquerait si une extension :

* Peut être mise à niveau sans activer le plug-in de compatibilité ascendante
* Peut être mise à niveau avec le plug-in de compatibilité ascendante activé
* Nécessite une mise à jour avant de passer de J5 à J6
* Est totalement incompatible
Les tests ont révélé des divergences entre les extensions compatibles et celles qui ne le sont pas. Il ne s’agit pas d’un problème du composant de vérification préalable à la mise à jour. Les développeurs d’extensions transmettent plutôt, par l’intermédiaire de leurs extensions, les informations qui permettent d’alimenter correctement la vérification préalable à la mise à jour. Si leurs extensions ne sont pas codées pour fournir les informations correctes à la vérification préalable à la mise à jour, cette dernière, pas plus que le projet Joomla!, ne peut pratiquement rien y faire. Le site web du développeur de l’extension tierce constitue une bonne source d’informations pour vérifier comment l’extension concernée doit être traitée lors de la mise à niveau de J5 vers J6.

L’image plus bas dans cette section montre un exemple du composant de vérification préalable à la mise à jour dans Joomla 5.4.x, dans la section Extensions.

La section supérieure affiche les extensions qui nécessitent une mise à jour. Veuillez accéder à Système -> Mise à jour -> Extensions et mettre à jour vos extensions.
La section centrale affiche les extensions pour lesquelles les informations de mise à jour ne sont pas disponibles auprès du développeur de l’extension. Vous ne saurez pas si elles sont compatibles ou non sans les tester ou contacter le développeur.

La section inférieure affiche les extensions qui ne nécessitent aucune mise à jour. Cela signifie que les extensions indiquent à Joomla qu’elles sont compatibles avec Joomla 6. Il n’est pas précisé si elles nécessitent ou non le plugin de compatibilité ascendante.

Veuillez noter que ces extensions ne sont pas recommandées par le projet Joomla. Elles sont présentées uniquement à titre d’exemple. Elles ont été sélectionnées aléatoirement dans la JED à des fins de test.

![Section des extensions de la vérification préalable à la mise à jour](../../../en/images/migration/joomla-5-to-6-steps/04-steps-5-to-6-pre-update-check.png)

Il est recommandé d’utiliser uniquement la section **Extensions** du composant de vérification préalable à la mise à jour comme une vue d’ensemble très générale, et non comme la source de vérité absolue. En d’autres termes, il est possible que vous ne puissiez pas faire confiance au composant de vérification préalable à la mise à jour selon les extensions que vous utilisez.
*Quelle est donc la source de vérité ?* Systèmes -> Gérer les extensions

![Tableau de bord du système avec « Gérer les extensions » entouré](../../../en/images/migration/joomla-5-to-6-steps/05-steps-5-to-6-system-dashboard-manage.png)

Depuis l’écran Extensions : Gérer, vous pourrez voir toutes les extensions tierces que vous utilisez sur le site. Dans la capture d’écran ci-dessous, vous voyez l’écran principal. Dans la colonne Auteur, vous pouvez voir le nom d’un développeur d’extensions populaire sur plusieurs lignes. Vous pouvez également voir l’auteur du projet Joomla sur plusieurs lignes.

![Page principale de gestion des extensions](../../../en/images/migration/joomla-5-to-6-steps/06-steps-5-to-6-extensions-manage.png)

Vérifiez vos extensions tierces. Ensuite, vous devrez déterminer si elles sont compatibles avec J6 (avec ou sans le plug-in de compatibilité ascendante) ou non. Si elles ne le sont pas, la mise à niveau échouera.

### Trois façons de vérifier la compatibilité de vos extensions tierces avec J6

1. Consultez le site Web du développeur.
2. Effectuez une sauvegarde/copie de votre site J5, restaurez-la sur un sous-domaine, activez le débogage, puis suivez les étapes détaillées (ci-dessous) pour effectuer la mise à niveau vers J6. Vérifiez si quelque chose ne fonctionne plus. Si c’est le cas, désactivez chaque extension qui génère une erreur et notez l’extension concernée. Vous devrez contacter le développeur à ce sujet, car elle n’est pas compatible avec J6.
3. Installez un paquetage J6 vierge sur un sous-domaine, activez le plugin « Behaviour - Backward Compatibility », installez toutes les extensions que vous utilisez et vérifiez si elles fonctionnent.

REMARQUE : L’annuaire des extensions Joomla! JED affichera des badges de compatibilité avec Joomla 6 pour les extensions compatibles avec ou sans l’utilisation du plugin de compatibilité ascendante.
Vous pourriez combiner les approches ci-dessus. Commencez par une installation propre et testez vos extensions. Lorsque vous saurez lesquelles fonctionnent ou non, vous pourrez travailler avec les développeurs pour voir où ils en sont dans leur développement pour J6. ENSUITE, une fois que toutes vos extensions fonctionnent sur un site propre, vous saurez que vous pouvez **tester** une mise à niveau complète de J5.4.x vers 6.x.

Vous voudrez peut-être déterminer si une extension fonctionne sans le plug-in de compatibilité ascendante activé. Si c’est le cas, vous devrez avoir accès à la base de données. Prévoyez-le. Assurez-vous d’avoir accès à la base de données.

Après avoir installé une nouvelle installation de J6, le plug-in de compatibilité ascendante sera désactivé. Installez chaque extension une par une. Si elle met votre site hors service, activez le plug-in de compatibilité ascendante via la base de données.
Le plugin de rétrocompatibilité se trouve dans la base de données, dans la table #__extensions. Il s’appelle plg_behaviour_compat6. Définissez le champ Enabled sur 0 pour désactiver le plugin et sur 1 pour l’activer. En réactivant le plugin de rétrocompatibilité, vous pourrez peut-être à nouveau accéder à l’interface d’administration de Joomla (à condition que l’extension fonctionne avec le plugin de rétrocompatibilité).

OU

Vous pouvez désactiver certaines extensions dans la base de données afin de continuer à tester vos autres extensions et de vérifier si elles fonctionneront sans que le plugin de compatibilité soit activé. Ces entrées se trouvent dans la table #__extensions. Remplacez la valeur du champ Enabled par 0 pour désactiver l’extension.
Dans certains cas, lorsque vous installez une extension dans J6 qui n’est pas compatible, que le plug-in de compatibilité ascendante soit activé ou non, vous devrez rechercher dans la base de données les entrées correspondant à cette extension (il peut y en avoir quelques-unes ou beaucoup) et les désactiver jusqu’à ce que vous puissiez de nouveau accéder à l’administration. Ces entrées se trouvent dans la table #__extensions. Vous devrez modifier le champ Enabled à 0 pour désactiver l’extension. Une fois que vous pourrez de nouveau accéder à l’administration de Joomla, vous pourrez la désinstaller correctement depuis Système -> Gérer -> Extensions. Contactez ensuite le développeur.

### Cassiopeia et Weblinks

#### Cassiopeia

Cassiopeia restera le modèle du site pour Joomla 6. Vos personnalisations devraient fonctionner correctement, mais nous vous recommandons tout de même d’effectuer des tests sur un site de développement pour vous en assurer.

#### com_weblinks

L’extension Liens fonctionne dans J6 sans que le plugin de compatibilité ascendante soit activé dans la version 5.4.0+ :

- [Liens évolués dans le JCM](https://magazine.joomla.org/all-issues/september-2025/joomla-weblinks-evolved-insights-from-gsoc-2025). 
- [Liens sur le JED](https://extensions.joomla.org/extension/weblinks/).

### Test

Dans le cadre de votre planification, il est recommandé de tester votre mise à niveau sur un sous-domaine ou en local afin de vérifier qu’elle fonctionne parfaitement. Veillez à noter toutes les étapes à suivre pour que votre mise à niveau se déroule **parfaitement**.

Une fois que vous avez testé votre mise à niveau sur un sous-domaine ou en local, et qu’elle fonctionne **parfaitement**, vous pouvez sauvegarder votre site de production et effectuer la mise à niveau de celui-ci. Les instructions détaillées se trouvent ci-dessous.

## Mise à niveau étape par étape

Le site que vous allez mettre à niveau doit répondre à toutes les exigences techniques et exécuter Joomla 5.4.x pour pouvoir être mis à niveau. Si votre site n’exécute pas encore Joomla 5.4.x, mettez-le à jour vers la version 5.4.x avant de passer à J6.

1. Suivez toutes les instructions de la section Planification (ci-dessus) avant la mise à niveau.
2. **Sauvegardez votre site web.**
3. Mettez à jour toutes les extensions qui doivent l’être.
4. Désactivez ou désinstallez toutes les extensions qui ne sont pas compatibles avec J6.
5. Activez le débogage (Configuration globale -> onglet Système -> paramètre Débogage du système sur Oui).
6. **Sauvegardez à nouveau votre site web.**
7. **Testez votre sauvegarde pour vous assurer qu’elle peut être restaurée.** (Oui, faites-le. Vous vous sentirez mieux.)
8. Accédez à Système -> Mise à jour -> Joomla
![Le tableau de bord du système avec Joomla à mettre à jour mis en évidence](../../../en/images/migration/joomla-5-to-6-steps/07-steps-5-to-6-system-dashboard-joomla.png)

9. Cliquez sur le bouton Options dans la barre d’outils supérieure, à droite.
![La page de mise à jour de Joomla avec le bouton Options mis en évidence](../../../en/images/migration/joomla-5-to-6-steps/08-steps-5-to-6-joomla-update.png)
10. Remplacez le canal de mise à jour par Joomla Next.
![Options de mise à jour de Joomla avec le canal de mise à jour encadré](../../../en/images/migration/joomla-5-to-6-steps/09-steps-5-to-6-joomla-update-options.png)

11. Cliquez sur Enregistrer et fermer dans la barre d’outils supérieure.
12. Si votre serveur répond aux spécifications techniques, l’écran suivant s’affichera, avec des liens dans la barre latérale gauche pour les Paramètres requis, les Paramètres recommandés et les Extensions.
![Vérification préalable à la mise à jour avec la barre latérale encadrée](../../../en/images/migration/joomla-5-to-6-steps/10-steps-5-to-6-pre-update-check-for-6.png)

13. Il y a de fortes chances que vos Paramètres requis et vos Paramètres recommandés soient corrects, car cet écran ne s’affiche pas si votre environnement ne répond pas aux exigences techniques. Les extensions peuvent toutefois poser problème. Consultez la section Planification (ci-dessus) consacrée à la vérification préalable à la mise à jour et expliquant pourquoi celle-ci peut ne pas afficher de coche verte tout en indiquant que toutes les extensions sont compatibles. Vous avez déjà effectué vos tests (n’est-ce pas ?), vous savez donc déjà si elles sont compatibles ou non.
14. Le plugin Rétrocompatibilité 6 est activé dans Joomla 5.4.x. Pour effectuer la mise à niveau vers J6, le plugin Comportement - Rétrocompatibilité doit être désactivé.
15. **Si vous n’avez pas suivi les instructions de la section Planification (ci-dessus) pour l’exécution d’essai, arrêtez-vous maintenant, retournez à la section Planification et suivez les instructions. La planification est l’étape la plus importante de cette mise à niveau.**
16. Une fois que vous êtes certain que toutes vos extensions sont compatibles avec J6 et que vous avez testé la mise à niveau avec un résultat parfait, vous pouvez cocher le bouton pour reconnaître les avertissements concernant les extensions potentiellement incompatibles et poursuivre la mise à jour. Cliquez sur OK dans la fenêtre contextuelle, puis cliquez sur le bouton Mettre à jour.
![Avis de reconnaissance des avertissements](../../../en/images/migration/joomla-5-to-6-steps/11-steps-5-to-6-pre-update-warnings.png)

17. Ensuite, votre site vous demandera à nouveau de confirmer que vous avez effectué une sauvegarde (ce que vous avez fait et dont vous avez vérifié la restauration).
![Page de téléversement et de mise à jour vers Joomla 6](../../../en/images/migration/joomla-5-to-6-steps/12-steps-5-to-6-upload-and-update.png)
18. Votre site effectuera la mise à niveau vers J6.
![Page de progression de la mise à niveau](../../../en/images/migration/joomla-5-to-6-steps/13-steps-5-to-6-joomla-update-progress.png)

19. Une mise à niveau réussie affichera un écran similaire à celui-ci :
![Page d’état de la mise à jour indiquant la réussite](../../../en/images/migration/joomla-5-to-6-steps/14-steps-5-to-6-joomla-update-success.png)

20. Vous verrez que votre site utilise Joomla 6 dans le coin supérieur droit de l’écran.
21. Testez l’interface publique de votre site.
22. Testez l’administration de votre site.
23. Désactivez le débogage dans Système -> Configuration globale -> onglet Serveur.
24. Configurez votre nouvelle recherche avancée si nécessaire.
25. Savourez une boisson agréable et émerveillez-vous de votre talent.

## Que faire en cas de problème ?

Si vous avez tout testé au préalable, cela ne devrait pas arriver. Mais il est possible que quelque chose ait changé dans l’environnement ou que du code d’une extension ait été modifié entre le moment où vous avez effectué vos tests et votre mise à niveau.

Comme vous avez activé le débogage avant de commencer, vous devriez pouvoir voir quelle extension est à l’origine du problème et la désactiver (cela devra peut-être être fait depuis la base de données si vous ne pouvez plus accéder à l’interface d’administration pour la désactiver). Ainsi, votre site sera opérationnel pendant que vous cherchez ce qui s’est mal passé et que vous le corrigez.

Dans le pire des cas, restaurez votre sauvegarde afin d’avoir le temps d’analyser ce qui s’est passé dans un environnement de test.

La correction de la base de données peut résoudre certains de vos problèmes. Accédez au tableau de bord système et cliquez sur Base de données.

![Tableau de bord système avec le lien Base de données encadré](../../../en/images/migration/joomla-5-to-6-steps/15-steps-5-to-6-system-dashboard-database.png)
Sur la page Maintenance : Base de données, tous les problèmes de structure de base de données que votre site peut rencontrer seront affichés. Cochez la case appropriée, puis cliquez sur le bouton Mettre à jour la structure dans la barre d’outils supérieure.

![Page de maintenance de la base de données affichant un problème](../../../en/images/migration/joomla-5-to-6-steps/16-steps-5-to-6-maintenance-database.png)

## Autres endroits où obtenir de l’aide

- [Forum Joomla : section Migration et mise à niveau 6.x](https://forum.joomla.org/viewforum.php?f=866&sid=47959551fb677ee3690f8b61eece277b)
- [Communauté Joomla sur Mattermost](https://joomlacommunity.cloud.mattermost.com/main/channels/town-square)

*Traduit par openai.com*