<!-- Filename: jdocmanual?manual=user&heading=migration&filename=migration-basics.md / Display title: Notions de Base sur la Migration  -->

## Terminologie

Les documents Joomla! utilisent une variété de termes pour signifier le passage d'une version plus ancienne à une version plus récente :

* **Migration ou mini-migration** est un terme habituellement appliqué au changement d'une version *Majeure* plus ancienne à une version *Majeure* plus récente, parfois à travers plusieurs versions *Majeures* intermédiaires.
* **Mise à niveau** est un terme habituellement appliqué au changement d'une version récente à la version suivante dans une séquence de versions *Mineures*.
* **Mise à jour** est un terme généralement utilisé pour le processus de mise à niveau en utilisant le composant de mise à jour de Joomla. C'est le mot utilisé dans l'interface Administrateur dans Joomla! 3, 4 et 5. Désormais, le terme *Mise à jour* sera utilisé dans cet article.

Il est également utile de savoir que Joomla suit la norme de versionnement sémantique. En bref, étant donné un numéro de version MAJEURE.MINEURE.CORRECTIF, tel que 5.1.0 :

* La version **MAJEURE** permet des ruptures de compatibilité ascendante.
* La version **MINEURE** permet d'ajouter des fonctionnalités de manière compatible avec la compatibilité ascendante au sein de la version Majeure.
* La version **CORRECTIF** permet des corrections de bugs compatibles avec la compatibilité ascendante.

Il peut y avoir des suffixes supplémentaires comme *alpha*, *bêta* ou *rc*, mais pas dans les versions stables destinées aux sites de production.

## Raisons de Mettre à Jour

Les raisons de mettre à jour sont nombreuses et variées :

* **Sécurité** Bien que Joomla! soit reconnu comme un CMS très sécurisé, des vulnérabilités occasionnelles sont découvertes et corrigées dans les versions Mineures ou de Correctif.
* **Modifications d'hébergement** Joomla utilise le langage de script *PHP* et un serveur de base de données tel que *MySQL*, *MariaDB* ou *PostGres*. Ils évoluent avec le temps et les services d'hébergement doivent se tenir à jour. Ainsi, vous pourriez constater qu'une version plus ancienne de Joomla ne fonctionne plus ou ne fonctionne pas correctement si vous changez de service d'hébergement.
* **Changemenst de design** Vous pourriez souhaiter améliorer l'apparence de votre site, le rendre plus performant sur les appareils mobiles et optimiser son classement dans les moteurs de recherche. Vous pourriez également devoir respecter les exigences légales d'*Accessibilité*.
* **Fonctionnalité** Vous pourriez vouloir utiliser une extension Joomla qui offre une fonctionnalité non fournie par les extensions de base de Joomla. Vos choix pourraient être limités par votre version Majeure actuelle.

## Sauvegarde avant mise à jour

**C'est vraiment important !** Même si vous avez réalisé plusieurs mises à jour intermédiaires, il est possible que quelque chose ne fonctionne pas correctement pendant le processus de mise à jour. Cela pourrait laisser votre site défectueux. Le conseil standard proposé dans les forums est de revenir à votre dernière sauvegarde, de découvrir pourquoi la sauvegarde a échoué, de la corriger, puis d'essayer à nouveau.

**Akeeba Backup** est un outil gratuit disponible dans le répertoire des extensions Joomla (JED) auquel vous avez accès directement via Système / Installer des extensions / Installer depuis le Web. Il ne faut qu'une minute ou deux pour le télécharger et l'installer. Il analyse votre système pour configurer un profil à l'aide d'un Assistant de Configuration. Il effectue ensuite une sauvegarde que vous pouvez télécharger pour la conserver en sécurité.

## Auto-évaluation

Avant de procéder à une mise à jour de version *Majeure* ou *Mineure*, il est nécessaire d'évaluer votre système et vos extensions tierces existantes pour vérifier leur compatibilité avec la version cible de Joomla. Il est utile d'établir une liste des extensions tierces que vous avez installées. Dans Joomla 4 et 5, la liste *Système / Extensions / Gérer* dispose d'un filtre permettant de sélectionner les **Extensions non-noyau**. Cela n'est pas présent dans Joomla 3.

Vous pouvez également utiliser le **Forum Post Assistant**. Cet outil est conçu pour analyser un site et produire un rapport adapté à une publication sur les forums Joomla afin d'aider les experts du forum à diagnostiquer les problèmes de votre site. Cependant, il dispose d'une interface utilisateur privée qui vous informe sur votre site. Ses listes d'extensions (Composants, etc.) indiquent celles qui sont *tierces*.

Les problèmes qui surviennent lors des mises à jour sont généralement associés à des extensions tierces qui ne sont pas compatibles avec la version cible de Joomla. Vous devez vérifier la compatibilité de chaque extension et **désinstaller** celles qui sont connues pour être incompatibles. Vous pourrez peut-être installer des versions compatibles plus tard.

Vous devriez définir l'un des modèles de site par défaut comme votre **modèle par défaut** :

* Les modèles par défaut de Joomla! 1.5 sont Rhuk_milkyway, JA Purity, Beez.
* Les modèles par défaut de Joomla! 2.5 sont Atomic, Beez3, et Beez25.
* Les modèles par défaut de Joomla! 3 sont Protostar et Beez3.
* Le modèle par défaut de Joomla! 4 est uniquement Cassiopeia.

## Test local

Dans la mesure du possible, il est préférable de configurer un environnement de test local sur votre ordinateur portable ou votre poste de travail à domicile pour tester votre procédure de mise à jour. Vous pouvez utiliser la sauvegarde de votre site en ligne pour alimenter votre site de test. Votre site local doit être capable d'exécuter votre copie de votre site en ligne et disposer de spécifications PHP et de base de données adéquates pour faire fonctionner le site mis à jour. Un article distinct décrit comment configurer un environnement de test à domicile.

## Informations supplémentaires

Il existe plusieurs articles décrivant des scénarios de mise à jour spécifiques qui ne sont pas inclus dans ce manuel, car ils sont anciens ou répétitifs.

* https://docs.joomla.org/Why_Migrate
* https://docs.joomla.org/Migration_Step_by_Step_Self_Assessment
* https://docs.joomla.org/J3.x:Updating_Joomla_(Install_Method)
* https://docs.joomla.org/J3.x:Updating_Joomla_(Update_Method)
* https://docs.joomla.org/Planning_Migration_-_Joomla_1.5_to_4
* https://docs.joomla.org/Planning_for_Migration
* https://docs.joomla.org/Pre-Update_Check
* https://docs.joomla.org/Template_Considerations_During_Migration
* https://docs.joomla.org/J3.x:Update_fails_with_an_error_message
* https://docs.joomla.org/Converting_an_existing_website_to_a_Joomla!_website
* https://docs.joomla.org/Potential_backward_compatibility_issues_in_Joomla_4
->
*Traduit par openai.com*

