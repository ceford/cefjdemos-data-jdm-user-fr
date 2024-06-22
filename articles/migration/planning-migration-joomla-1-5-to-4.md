<!-- Filename: Planning_Migration_-_Joomla_1.5_to_4 / Display title: Planification d'une migration - Joomla! 1.5 vers 3.x -->

Passer de Joomla! 1.5 à 3.x peut être considéré comme une migration
majeure. Cela signifie que les modifications considérables apportées à
Joomla! comme l'abandon des tableaux, les nouvelles technologies
utilisées nécessitent une véritable migration et non une simple mise à
niveau ou mise à jour. Les extensions natives de Joomla, comme les
extensions tierces devront faire l'objet d'une migration vers Joomla!
3.x, y compris les templates. Chaque élément doit faire l'objet d'une
attention toute particulière, d'une planification, d'une prise de
décision et d'actions. Vous devez rester organisé tout au long du
processus.

## Introduction

Ce qui est intéressant avec la migration c'est que c'est le parfait
moment pour réévaluer les objectifs, créer un nouveau design (template),
nettoyer et développer d'autres éléments de votre site. Plus vous êtes
organisé dans vos idées et plans, mieux c'est. Planifiez, planifiez,
planifiez ! La planification rend l'exécution plus aisée.

Commencez votre planification en vous posant les questions ou en
réalisant les tâches énumérées ci-dessous. En fonction de la complexité
de votre site, il se peut que vous ayez plus d'éléments à planifier.
Malheureusement, il n'y a aucun moyen de lister l'ensemble des scénarios
possibles.

{{{1}}}

## Planification des actions

### Généralités

1.  Réévaluer les objectifs originels de votre site. Une migration est
    une opportunité d'étudier et de se concentrer à nouveau sur vos
    objectifs, voire de changer de direction.
2.  Est-ce que votre serveur répond aux
    <a href="http://www.joomla.org/about-joomla/technical-requirements.html"
    class="external text" target="_blank"
    rel="noreferrer noopener">exigences techniques</a> minimums pour
    supporter Joomla! 3 ? Si ce n'est pas le cas, il vous faudra changer
    également d'hébergement. La migration devient alors également le bon
    moment pour envisager de changer d'hébergement.
3.  Quel type d'environnement de développement allez-vous utiliser ? Un
    environnement de développement en local sur votre machine ? Un
    sous-domaine ou un sous-répertoire sur votre serveur actuel ? Un
    nouveau serveur et/ou hébergeur pour répondre aux spécifications
    techniques ?

### Le noyau Joomla!

1.  Faites un nettoyage de votre site actuel. Jetez un œil à vos
    Sections, Catégories et Articles. Les sections sont converties en
    niveau supérieur de catégories dans Joomla! 2.5. Est-il nécessaire
    de réaliser un nettoyage plus conséquent afin de ne pas migrer du
    contenu inutile, comme des documents que vous souhaiteriez
    supprimer ? Au contraire, il se peut que vous ayez des documents
    supplémentaires à ajouter.
2.  Organisez votre contenu sur le site actuel. Est-ce que les
    catégories dont vous disposez sont toujours d'actualité ? Complétez
    les nouvelles catégories que vous souhaitez ajouter à votre nouveau
    site.
3.  Avez-vous des articles dans la corbeille ? Si oui, supprimez-les
    (ainsi que l'ensemble des médias qui peuvent leur être associés
    s'ils ne sont pas utilisés ailleurs sur le site). Les articles
    (comme les catégories et les éléments de menu) qui seraient laissés
    dans la corbeille peuvent générer, une fois migrés, des anomalies de
    doublons d'alias .
4.  Le gestionnaire de médias. Décidez si vous souhaitez migrer
    l'intégralité de votre répertoire /images ou simplement une partie
    de celui-ci. Si votre gestionnaire de médias est devenu au fil du
    temps un "désastre", vous pourrez décider de transférer des images
    spécifiques via FTP ou cPanel au lieu de migrer l'intégralité du
    répertoire. A l'avenir, organisez les dossiers du gestionnaire de
    médias afin de ne plus vous retrouver dans un grand bazar.
5.  Si vous utilisez des composants Joomla! tels que Contacts, Liens web
    ou Fils d'actualités, prenez-en note car vous aurez besoin de les
    transférer.
6.  Vérifiez vos menus et déterminez si vous allez tous les conserver ou
    seulement certains menus spécifiques et éléments de menus. Supprimez
    les éléments de menu présents dans la corbeille pour éviter tout
    doublon d'alias.
7.  Si vous souhaitez revoir le design ou modifier la navigation de
    votre site, allez-vous avoir des pages obsolètes qui nécessiteront
    une redirection ? Notez sur un document externe toutes les URLs qui
    ont besoin d'être redirigées.
1.  Avez-vous “modifié le noyau” de votre site 1.5 ? Si c'est le cas,
    ces modifications ne seront pas migrées vers Joomla! 3. Vous
    souhaiterez alors trouver des alternatives pour modifier le noyau de
    Joomla! 3 (<a
    href="https://docs.joomla.org/How_to_override_the_output_from_the_Joomla!_core"
    class="new"
    title="Special:MyLanguage/How to override the output from the Joomla! core (page does not exist)">Comment
    substituer le rendu du noyau Joomla</a>, [Comprendre les
    substitutions de
    rendu](https://docs.joomla.org/Understanding_Output_Overrides "Special:MyLanguage/Understanding Output Overrides"),
     Substitutions de mise en page dans
    Joomla.
2.  Vérifiez votre Gestionnaire des utilisateurs. Avez-vous l'intention
    de tous les transférer ? Y-a-t-il du nettoyage à faire ? Peut-être
    que certains Supers Administrateurs ne devant plus avoir d'accès ou
    des spammeurs devraient être supprimés ? Utilisez-vous une extension
    tierce pour améliorer les profils utilisateurs ? Cette partie
    nécessite d'être planifiée minutieusement. Surtout si les données
    utilisateurs changent fréquemment.
3.  Existe-t-il des nouvelles fonctionnalités de Joomla! que vous
    souhaiteriez utiliser, comme la gestion des niveaux d'accès (ACL),
    les tags ? Si c'est le cas, commencez à planifier tout cela dès
    maintenant. La planification des ACLs est un travail délicat. La
    rigueur est très importante.

### Extensions tierces

1.  Faites une liste de toutes les extensions tierces que vous utilisez.
    Cela inclut les composants, modules, plugins, langues et templates.
    Vous pouvez utiliser la <a
    href="https://docs.joomla.org/images/5/59/Third-Party_Extension_Inventory_Worksheet.pdf"
    class="external text" target="_blank" rel="noreferrer noopener">feuille
    d'inventaire des extensions tierces</a> ou, si vous préférez, les
    copier/coller dans un document. Une feuille de papier et un crayon
    conviennent également parfaitement. Indiquez si ces extensions sont
    utilisées fortement, modérément, presque jamais ou pas du tout.
1.  Déterminez si les extensions tierces dont vous avez besoin sont
    disponibles pour la version de Joomla! sur laquelle vous allez
    migrer.
2.  Déterminez si vous avez vraiment besoin de toutes les extensions que
    vous utilisez. Est-ce que des fonctionnalités natives de Joomla! 3
    peuvent être utilisées à la place d'extensions tierces ?
3.  Qu'en est-il de votre template ? Si vous l'avez acheté auprès d'un
    tiers, existe-t-il une version 3.x de celui-ci ? Allez-vous
    continuer de l'utiliser ? Est-ce que le développeur a publié un
    chemin pour la migration . Est-ce que la nouvelle version est
    responsive ? Est-ce que votre template est personnalisé ? Ou est-ce
    que votre template tiers a été fortement personnalisé ? Pour des
    informations sur les considérations en matière de template, voir
     Considérations sur les templates lors d'une
    migration.
1.  Si vous remplacez votre template par un nouveau template, aura-t-il
    besoin de nouvelles images ? Par exemple, si votre site actuel a un
    fond blanc et que votre logo ou d'autres images sont des images .jpg
    avec un fond blanc, cela ne sera pas très esthétique sur un nouveau
    template ayant un fond de couleur différente.

<a
href="https://docs.joomla.org/Joomla_1.5_to_4.x_Step_by_Step_Migration"
id="content-button" class="button expand">Joomla 1.5 to 4.x Step by Step
Migration</a>
