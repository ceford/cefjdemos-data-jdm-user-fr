<!-- Filename: Smart_Search_Frequently_Asked_Questions / Display title: FAQ sur la recherche intelligente -->

## Pourquoi devrais-je utiliser la recherche intelligente ?

La technologie de recherche s'est considérablement améliorée au fil des ans depuis le lancement de Joomla, et pourtant le composant de recherche standard et de base n'a pas beaucoup changé au cours de cette période. Il est encore très rudimentaire et manque des fonctionnalités de recherche auxquelles les utilisateurs web s'attendent désormais, surtout compte tenu de la prévalence de moteurs de recherche avancés tels que Google. La recherche intelligente vous permet d'incorporer certaines de ces fonctionnalités de recherche plus avancées dans votre site web.

## Pourquoi créer un plugin de recherche intelligente ?

En général, si vous avez un type de contenu qui n'est pas géré par les composants principaux de Joomla, et que vous souhaitez offrir à vos visiteurs la possibilité de rechercher ce contenu, vous devrez écrire un plugin de recherche intelligente pour le prendre en charge. Par exemple, supposons que vous ayez un composant qui stocke des informations sur différentes espèces animales. Le composant maintient une table de base de données contenant des champs tels que le nom scientifique, le nom vernaculaire, la classification et une description. Dans ce cas, vous devrez créer un plugin qui indiquera à l'indexeur de recherche intelligente comment indexer les données de cette table. En plus d'indexer des mots et des expressions individuels, vous pouvez également demander au plugin d’ajouter chaque enregistrement à une carte de contenu, qui pourrait inclure dans ce cas les classifications biologiques de <a href="https://fr.wikipedia.org/wiki/Taxonomie_(biologie)" rel="nofollow noreferrer noopener">règne, embranchement, classe, ordre et famille</a>. Les cartes de contenu peuvent ensuite être utilisées pour filtrer les résultats de recherche.

## Peut-on sélectionner plusieurs nœuds à partir des menus déroulants de filtrage ?

Oui, cela est entièrement pris en charge par Smart Search lui-même. En effet, vous pouvez utiliser n'importe quelle interface utilisateur que vous souhaitez concevoir pour les filtres. Il vous suffit de jeter un œil au code fourni dans le module et le composant standard Frontend, et vous verrez comment procéder.

## J'ai un grand site. Puis-je utiliser Smart Search ?

Les grands sites peuvent être mieux servis avec un moteur de recherche dédié et autonome, tel que Solr, plutôt que l'implémentation pure-PHP utilisée dans Smart Search. Dans cette première itération de la recherche avancée dans Joomla, il est probable que des problèmes liés à l'évolutivité et aux performances apparaissent. Il y a également le potentiel de conditions de concurrence lors de la mise à jour de l'index en cas de modifications fréquentes du contenu. Ces problèmes devraient être traités plus en détail dans une future version de Joomla.

## Pourquoi la recherche intelligente a-t-elle autant de tables ?

La recherche intelligente ajoute un certain nombre de nouvelles tables à une installation Joomla, y compris 16 "tables de mappage". Ces tables de mappage résolvent la relation de plusieurs à plusieurs entre les termes de recherche et les éléments de contenu qui les contiennent. En théorie, ces 16 tables pourraient être fusionnées en une seule table, ce qui aurait un impact négligeable sur les petits sites. Cependant, sur les sites plus grands, il y aurait un impact substantiel sur les performances, car la table de mappage contiendrait un très grand nombre d'entrées et la mise à jour d'une table aussi grande peut être chronophage.

## Pourquoi la recherche intelligente utilise-t-elle autant d'espace disque ?

Maintenir un index de termes de recherche nécessite une quantité considérable d'espace disque, qui augmente avec le nombre de termes que contiennent les éléments de contenu. Puisque les phrases sont également indexées, plus les phrases sont longues, plus l'espace disque requis est important. Pour la recherche intelligente dans Joomla 2.5, la longueur maximale d'une phrase a été fixée à 3 termes, constituant ainsi un compromis raisonnable entre l'utilisabilité de la recherche et l'utilisation de l'espace disque. Il est probable que ce sera un paramètre ajustable dans une future version de la recherche intelligente.

## Pourquoi les entrées dans les tables de correspondance ne sont-elles pas uniformément distribuées ?

Il est peut-être surprenant que le nombre d'entrées dans chacune des tables de correspondance ne soit même pas à peu près le même. Assurément, la performance serait améliorée avec une distribution uniforme ? En réalité, non, il existe un compromis entre la performance d'insertion et la performance de recherche, une distribution uniforme étant bonne pour la première mais mauvaise pour la seconde. C'est un domaine de recherche continue où le nombre de tables et l'algorithme de distribution peuvent être modifiés à la lumière de l'expérience.

## Pourquoi y a-t-il un plugin de contenu de recherche intelligente séparé ?

C'est simplement une commodité qui facilite l'activation ou la désactivation de tous les plugins de recherche intelligente en une seule opération. Cela a été jugé souhaitable car la recherche intelligente n'est pas activée par défaut dans Joomla 2.5.

## Pourquoi les plugins de recherche intelligente utilisent-ils des événements distincts tels que *onFinderContentAfterSave* ?

La recherche intelligente utilise ses propres événements, tels que onFinderContentAfterSave, plutôt que l'équivalent générique onContentAfterSave, uniquement par souci de commodité pour faciliter l'activation ou la désactivation de l'indexation de la recherche intelligente en activant/désactivant un seul plugin.

## Pourquoi la recherche intelligente n'est-elle pas activée par défaut dans Joomla 2.5 et Joomla 3.x ?

Étant donné que Joomla 2.5 est le dernier de la série 1.x/2.x, il doit maintenir un haut degré de rétrocompatibilité avec la version précédente de la série. Comme la recherche intelligente est quelque chose de complètement nouveau et n'a aucune ressemblance avec le composant de recherche classique de cette version ou des versions antérieures, il a été considéré important que les utilisateurs passant à ces versions plus récentes ne soient pas contraints de changer la façon dont la recherche fonctionne sur leurs sites. En effet, l'activation de la recherche intelligente est quelque chose qui doit être fait de manière réfléchie et soigneusement planifiée.

## Pourquoi n'y a-t-il pas d'API de recherche ?

L'objectif de la version actuelle de Smart Search était de transférer le code de l'ancien composant JXtended Finder vers la dernière version de Joomla. Comme ce code était déjà considéré comme stable et qu'il y avait seulement une courte opportunité pour transférer le code, une refonte majeure de Finder a été jugée hors de portée pour la version Joomla 2.5. Par conséquent, le code utilise des Plugins pour éviter toute modification du code central du CMS, plutôt que de développer une véritable API de recherche. Nous envisageons de créer une telle API pour une future itération de Joomla.

## La recherche intelligente peut-elle effectuer une recherche par facettes ?

Oui. La recherche avancée disponible depuis la page des résultats de recherche et le module de recherche intelligente illustrent comment vous pouvez filtrer les résultats pour produire une recherche par facettes. Rien ne vous empêche de créer vos propres variantes de ces idées de base. Par exemple, vous pourriez modifier les listes déroulantes simples pour accepter des sélections multiples, ou vous pourriez remplacer les listes déroulantes par un ensemble de cases à cocher.

## Pourquoi les recherches par joker ne sont-elles pas prises en charge ?

L'ancien système de recherche de Joomla utilisait une méthode très primitive qui reposait sur la recherche FULLTEXT fournie par la base de données. Cela était très inefficace mais offrait un moyen simple de gérer les requêtes de recherche par joker. La Recherche Intelligente propose une fonction d'auto-complétion qui est effectivement une recherche par joker des termes dans l'index, mais la recherche par joker complète n'est pas prise en charge en raison du risque de paralyser le serveur si la fonctionnalité devait être abusée. Dans la plupart des cas, la recherche par joker est utilisée pour prendre en compte les variations d’un terme de recherche. Par exemple, rechercher *jongl\** pour obtenir des références à *jonglage* ainsi que *jongleur*. La Recherche Intelligente cherche à éviter le besoin de recherche par joker en prenant en charge la racinisation des mots où les mots ayant la même racine sont considérés comme équivalents, de sorte que la recherche de *jongleur* renverra également les occurrences de *jonglage* sans avoir besoin d'utiliser des jokers.

## La recherche intelligente peut-elle être utilisée sur des sites multilingues ?

Oui, mais certains problèmes doivent encore être résolus, notamment en ce qui concerne la prise en charge des langues asiatiques.

- Pour être indexé correctement, vous devez vous assurer que tout le contenu est en UTF-8 valide.
- La fonction *Vouliez-vous dire ?* utilise la fonction Soundex pour trouver des phrases de recherche phonétiquement similaires. Cependant, Soundex ne fonctionne pas bien pour les langues non anglaises et pour de nombreuses langues, elle ne fonctionne pas du tout. Nous cherchons actuellement des méthodes alternatives pour offrir cette fonctionnalité.

Si vous utilisez la recherche intelligente sur un site multilingue et que vous rencontrez des problèmes, veuillez les signaler sur le traqueur afin que nous puissions mieux comprendre les problèmes à résoudre.

## Les plugins Finder *jXTended* fonctionneront-ils avec Smart Search ?

Non. Vous devrez mettre à jour les plugins Finder pour qu'ils fonctionnent avec Smart Search. Cependant, les modifications devraient être faciles à réaliser et, dans la plupart des cas, entraîneront un code nettement réduit. Si vous examinez les plugins Smart Search actuels, vous devriez constater que la mise à jour d'un plugin Finder est assez simple.

*Traduit par openai.com*

