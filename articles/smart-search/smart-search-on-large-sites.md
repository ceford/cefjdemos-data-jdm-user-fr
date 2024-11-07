<!-- Filename: Smart_Search_on_large_sites / Display title: Recherche Intelligente sur les Grands Sites -->

## Indexation du site

La recherche intelligente fonctionne en créant et en maintenant un index indépendant de termes de recherche dans plusieurs tables de la base de données. Le problème pour les grands sites est que le processus d'indexation peut être assez lourd en termes d'utilisation du processeur, de la mémoire et du disque. Même après la construction initiale de l'index, les mises à jour incrémentielles peuvent également être lourdes. La bonne nouvelle, c'est que l'interrogation de l'index est une opération relativement rapide et légère.

La recherche intelligente convient à la majorité des sites Joomla. Cependant, la recherche pose des défis particuliers pour les grands sites. Il faut se rappeler que la recherche intelligente est une implémentation PHP pure d'un moteur de recherche et que les sites particulièrement grands seraient mieux servis avec un moteur de recherche autonome tel que Solr.

Pour utiliser la recherche intelligente sur un grand site, vous devrez probablement ajuster certains paramètres de configuration. Ce qui suit est un ensemble de conseils généraux sur ce à quoi prêter attention et ce qu'il faut essayer d'ajuster. Il existe un certain nombre de problèmes connus liés à l'exécution de la recherche intelligente sur de grands sites qui, espérons-le, seront corrigés dans les futures versions, et ceux-ci sont également décrits ici.

## Utilisez toujours l'indexeur en ligne de commande

Étant donné que le processus d'indexation initial peut prendre beaucoup de temps, il est préférable d'exécuter l'indexeur depuis la ligne de commande pour éviter tout problème lié à l'expiration des sessions de navigateur. L'indexeur CLI ne se désactive pas, peu importe le temps nécessaire pour terminer, et il peut être facilement interrompu en cas de problème. De plus, les messages d'erreur sont visibles avec l'indexeur CLI, alors qu'ils sont masqués lorsqu'on le lance depuis l'Administrateur.

Pour utiliser le CLI, ouvrez un terminal, passez au dossier cli à la racine de votre site et exécutez la commande suivante :

```
php joomla.php finder:index
```

## Traitement par lots

L'indexeur divise la tâche d'indexation en lots d'éléments de contenu. Par défaut, la taille du lot est fixée à 30, ce qui signifie que jusqu'à 30 éléments de contenu seront indexés par lot. Augmenter la taille du lot peut potentiellement accélérer le processus d'indexation, mais cela utilisera plus de mémoire et possiblement plus d'espace disque temporaire.

## Problèmes de Mémoire Insuffisante

Si l'indexeur manque de mémoire, essayez de faire les ajustements suivants un par un jusqu'à ce que le problème soit résolu.

1. Diminuez la taille du lot. Si vous avez des éléments de contenu particulièrement volumineux, l'indexeur peut manquer de mémoire même avec un seul élément de contenu, alors essayez de la réduire à 5 au départ et si vous manquez toujours de mémoire, réduisez-la à 1.
2. Si vous pouvez allouer plus de mémoire à l'indexeur, faites-le. Vous pouvez augmenter la mémoire allouée à l'indexeur en ligne de commande en utilisant un paramètre supplémentaire dans la ligne de commande. Par exemple, pour augmenter la limite de mémoire à 256 Mo, utilisez la commande suivante, en remplaçant le *256M* par autant de mémoire que vous pouvez allouer en toute sécurité à un processus sur votre système.<br> 
   *php -d memory_limit=256M finder_indexer.php*
3. Réduisez la limite de la table de mémoire. La valeur par défaut est de 30000 termes, ce qui signifie que dès que la table temporaire en mémoire *#__finder_tokens* atteint ce nombre de lignes, l'indexeur passera à l'utilisation d'une table disque au lieu d'une table mémoire. Il se peut que vous n'ayez pas assez de mémoire pour gérer une table mémoire pleine ou presque pleine, donc réduire la limite indiquera à l'indexeur de passer au disque plus tôt et d'utiliser ainsi moins de mémoire. Essayez 10000 ou même des nombres beaucoup plus petits.
4. Changez le moteur de base de données utilisé pour les tables *__finder_tokens* et *#__finder_tokens_aggregate* de MEMORY à InnoDB. Cela pourrait sérieusement affecter les performances puisqu'une plus grande partie du processus d'indexation utilisera le disque au lieu de la mémoire, mais cela pourrait permettre à l'indexeur de terminer sans manquer de mémoire. Attendez-vous à ce que le processus d'indexation dure beaucoup plus longtemps. Cela n'affectera cependant pas les performances de recherche.
5. Essayez d'identifier quels éléments de contenu provoquent le manque de mémoire de l'indexeur. Si ce n'est pas évident, vous pourriez essayer de désactiver tous les plugins Smart Search sauf un. Exécuter l'indexeur avec un seul plugin activé à la fois devrait révéler quels types de contenu causent le problème. En dernier recours, envisagez de diviser quelques éléments de contenu exceptionnellement volumineux en éléments séparés. Si le problème concerne un type de contenu personnalisé, examinez le code du plugin et envisagez d'indexer moins de contenu disponible par élément.


## Problèmes d'Espace Disque Insuffisant

Les tables d'index de Smart Search peuvent croître rapidement ! Les tables *#__finder_links_termsX* (où *X* est un caractère hexadécimal unique) contiennent une ligne par terme/phrase par élément de contenu, et un seul article Joomla contenant 1000 mots se traduira typiquement par l'ajout d'environ 3000 lignes dans ces tables. Un second article de taille similaire ajoutera un nombre similaire de lignes même si les deux articles contiennent les mêmes mots. Un site avec des dizaines de milliers d'articles, dont certains peuvent contenir des milliers de mots, est susceptible de se retrouver avec ces tables de mappage contenant des millions de lignes. Il n'est pas rare que les tables d'index occupent plusieurs gigaoctets d'espace disque dans de telles circonstances.

Avec la version actuelle de Smart Search, il n'y a pas grand-chose que vous puissiez faire à ce sujet. Cependant, on espère que dans la prochaine version, vous pourrez ajuster le nombre de mots par phrase qui sont indexés. Actuellement, cela est fixé à 3, ce qui signifie que chaque mot qui est indexé est également indexé en tant que partie d'une paire de mots adjacents et en tant que partie d'un triplet de mots adjacents. Cela est utile pour la fonctionnalité d'auto-complétion et améliore généralement la qualité des résultats de recherche. Sur les sites où l'espace disque est un problème, il serait bien de réduire cela à 2 voire même 1, de sorte que les tables de mappage soient proportionnellement plus petites.

## Notes

1. Il n'y a actuellement aucun verrouillage de concurrence pour empêcher plus d'un processus de faire fonctionner l'indexeur en même temps. Cela entraînera presque certainement un index corrompu. Même quelqu'un enregistrant des modifications sur un élément de contenu pendant qu'un index complet est effectué pourrait potentiellement endommager l'index.

*Traduit par openai.com*

