<!-- Filename: Planning_for_Mini-Migration_-_Joomla_3.10.x_to_4.x / Display title: Planning d'une mini-migration - Joomla 3.10 à 4.x -->

Passer de Joomla 3.10.x à 4.x est considéré comme une mini-migration ou
une migration mineure. Cela signifie que les extensions de base de
Joomla seront mises à jour en un seul clic contrairement aux extensions
tierces qui doivent être analysées au cas par cas.

## Introduction

Les migrations sont un bon moment pour réévaluer les objectifs, nettoyer
et développer d'autres domaines/éléments de votre site. Plus vous serez
organisé avec vos idées, vos pensées et vos plans, mieux ce sera.
Planifiez, planifiez, planifiez. La planification facilite l'exécution.

Commencez à planifier en posant les questions suivantes ou en effectuant
les tâches énumérées ci-dessous. Il se peut que vous ayez d'autres
éléments à planifier en fonction de la complexité de votre site.
Malheureusement, il n'est pas possible d'énumérer tous les scénarios
possibles. Pour obtenir de l'aide, veuillez consulter le
<a href="https://forum.joomla.org/viewforum.php?f=812"
class="external text" target="_blank" rel="noreferrer noopener">Forum
sur la migration et la mise à niveau vers Joomla 4.x</a>.

## Le pont 3.10.x

Joomla 3.10.x est destiné à servir de transition entre le cycle de vie
de Joomla 3 et celui de Joomla 4. Joomla 3.10.x sera principalement une
version contenant des rétroportages des changements d'API de la branche
de développement de Joomla 4.x pour aider à faciliter la transition vers
la prochaine version majeure pour la communauté. La nouvelle version
3.10.x de Joomla est une excellente fonctionnalité du composant de mise
à jour de Joomla ! pour vous aider dans votre processus de
mini-migration : le  Vérification avant mise à
jour.
Une fois que votre site web est mis à jour à la version 3.10, la
vérification de pré-mise à jour vous permettra de vérifier la
compatibilité avec Joomla 4.0 de vos options et paramètres PHP et SQL,
ainsi que des extensions que vous utilisez, à condition que les
développeurs d'extensions aient utilisé la balise targetplatform. Voir
la documentation  Vérification avant mise à
jour
pour plus d'informations.

## Planification des actions

Ce qui suit suppose que vous avez déjà mis à jour votre site Joomla 3.x
à la version 3.10.x. Cela vous permettra de profiter du Pre-Update
Checker dans le cadre de votre planification.

1.  Assurez-vous que votre site web fonctionne sous 3.10.x.
2.  Évaluez vos objectifs initiaux pour le site. La migration est une
    occasion de vous recentrer sur vos objectifs ou de changer de
    direction.
3.  Votre serveur répond-il aux exigences techniques minimales
    <a href="http://www.joomla.org/about-joomla/technical-requirements.html"
    class="external text" target="_blank" rel="noreferrer noopener">les
    exigences techniques</a> pour Joomla 4 ? Si ce n'est pas le cas,
    vous devrez changer d'hébergeur. Il n'y a pas de meilleur moment
    pour changer d'hébergeur que lors d'une migration.
4.  Quel type d'environnement de développement utiliserez-vous ? Un
    environnement de développement sur votre machine en local ? Un
    sous-domaine ou un sous-répertoire sur votre serveur ? Un nouveau
    serveur/compte d'hébergement en raison de spécifications
    techniques ?
5.  Faire une liste de toutes les extensions tierces utilisées. Cela
    inclut les composants, modules, plugins, langages et templates. Vous
    pouvez simplement les copier/coller dans un document pour référence,
    ou un papier et un stylo fonctionne aussi. Indiquez si ces
    extensions sont utilisées fortement, modérément, presque jamais ou
    pas du tout.
6.  Déterminez si les extensions tierces dont vous dépendez sont prêtes
    pour la version de Joomla vers laquelle vous migrez en sélectionnant
    l'option Joomla Next (une fois que vous utilisez Joomla 3.10.x) dans
    le composant de mise à jour de Joomla et vérifiez si elles sont
    compatibles avec Joomla 4. N'exécutez pas la mise à jour vers la
    version 4.x, sélectionnez simplement l'option version suivante de
    Joomla dans les options de mise à jour de Joomla afin que le
    vérificateur de pré-mise à jour puisse s'afficher. Cela vous aidera
    à obtenir une vue d'ensemble des extensions utilisées et de leur
    compatibilité. Il ne s'agit pas d'un substitut à la nécessité de
    toujours utiliser Extensions → Gérer. Vous en saurez plus à ce sujet
    dans le Pas à Pas et dans la documentation du composant
     Vérification avant mise à
    jour.
    Il s'agit simplement de se préparer sur les extensions tierces qui
    vont rester ou partir ou être remplacées.
7.  Déterminez si vous avez vraiment besoin de toutes les extensions que
    vous utilisez. Se pourrait-il que Joomla 4 ait intégré des
    fonctionnalités qui pourraient éliminer l'utilisation d'une
    extension tierce ?
8.  Consultez vos catégories et vos articles. Y a-t-il un nettoyage à
    faire pour éviter de migrer des contenus inutiles ?
9.  Qu'en est-il de votre template ? Si vous avez acheté votre template
    auprès d'une source tierce, existe-t-il une version 4.x de
    celle-ci ? Souhaitez-vous continuer à l'utiliser ? Y a-t-il une mise
    à niveau publié par le développeur ? La nouvelle version est-elle
    responsive ? Votre template est-il un template personnalisé ? Ou
    a-t-il été fortement personnalisé à partir d'un modèle tiers ? Le
    template de base de Joomla pour Joomla 3.x, '*Protostar n'est PAS
    compatible avec Joomla 4*. Il disparaîtra lors de la migration.
    L'utilisation du template de base de Joomla pour Joomla 4.x,
    Cassiopeia, pourrait être une option pour vous. Pour un
    développement des considérations basées sur les templates, voir
     Considérations sur les templates pendant la
    migration.
10. Si vous remplacez votre template par un nouveau template, aura-t-il
    besoin de nouvelles images ? Par exemple, si votre site actuel a un
    fond blanc et que votre logo ou d'autres images sont des images .jpg
    avec un fond blanc, cela ne sera pas très esthétique sur un nouveau
    template ayant un fond de couleur différente.
11. Si vous modifiez la conception ou la navigation de votre site,
    aurez-vous des pages obsolètes qui nécessiteront une redirection ?
    Si c'est le cas, documentez-les. Un tableur est utile pour
    documenter les liens qui devront être modifiés.

<a
href="https://docs.joomla.org/Joomla_3.x_to_4.x_Step_by_Step_Migration"
id="content-button" class="button expand">Migration étape par étape de
Joomla! 3.x vers 4.x</a>
