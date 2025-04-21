<!-- Filename: Smart_Search_on_large_sites / Display title: Recherche Intelligente sur Grands Sites -->

## Indexation du site

Smart Search fonctionne en créant et en maintenant un index indépendant des termes de recherche dans un certain nombre de tables de base de données. Le problème pour les grands sites est que le processus d'indexation peut être assez lourd en termes d'utilisation de CPU, de mémoire et de disque. Même après la construction initiale de l'index, les mises à jour incrémentielles peuvent également être lourdes. La bonne nouvelle est que l'interrogation de l'index est une opération relativement rapide et légère.

La recherche intelligente convient à la majorité des sites Joomla. Cependant, la recherche présente des défis particuliers pour les grands sites. Il faut se rappeler que la recherche intelligente est une implémentation pure en PHP d'un moteur de recherche et que les sites particulièrement grands pourraient bénéficier davantage d'un moteur de recherche autonome tel que Solr.

Pour utiliser la recherche intelligente sur un grand site, vous devrez probablement ajuster certains paramètres de configuration. Voici quelques conseils généraux sur ce à quoi faire attention et ce qu'il faut essayer de modifier.

## Toujours utiliser l'indexeur CLI

Comme le processus d'indexation initiale peut prendre beaucoup de temps, il est préférable d'exécuter l'indexeur depuis la ligne de commande pour éviter tout problème lié à l'expiration des sessions de navigation. L'indexeur CLI ne s'expirera pas, quel que soit le temps nécessaire pour se terminer, et il peut être facilement interrompu en cas de problème. De plus, les messages d'erreur sont visibles avec l'indexeur CLI, tandis qu'ils pourraient être masqués lorsqu'ils sont exécutés depuis l'Administrateur.

Pour utiliser l'interface en ligne de commande, ouvrez un terminal, accédez au dossier cli à la racine de votre site et entrez la commande suivante :

```
php joomla.php finder:index
```

## Traitement par lot

L'indexeur divise la tâche d'indexation en lots d'éléments de contenu. Par défaut, la taille des lots est fixée à 50, ce qui signifie que jusqu'à 50 éléments de contenu seront indexés par lot. Augmenter la taille des lots peut potentiellement accélérer le processus d'indexation, mais cela utilisera plus de mémoire et éventuellement plus d'espace disque temporaire.

## Problèmes de Mémoire Insuffisante

Si l'indexeur manque de mémoire, essayez d'apporter les ajustements suivants un par un jusqu'à ce que le problème soit résolu.

1. Réduisez la taille du lot. Si vous avez des éléments de contenu particulièrement volumineux, l'indexeur peut manquer de mémoire même pour un seul élément de contenu, essayez donc de la réduire à 5 au début et si vous manquez toujours de mémoire, réduisez-la à 1.
2. Si vous pouvez allouer plus de mémoire à l'indexeur, faites-le. Vous pouvez augmenter la mémoire allouée à l'indexeur en ligne de commande en utilisant un paramètre supplémentaire sur la ligne de commande. Par exemple, pour augmenter la limite de mémoire à 256 Mo, utilisez la commande suivante, en remplaçant les *256M* par autant de mémoire que vous pouvez allouer en toute sécurité à un processus sur votre système.
```php
    php -d memory_limit=256M joomla.php finder:index
```
3. Essayez d'identifier quels éléments de contenu font que l'indexeur manque de mémoire. Si ce n'est pas évident, vous pourriez essayer de désactiver tous les plugins Smart Search sauf un. Exécuter l'indexeur avec un seul plugin activé à la fois devrait révéler quel(s) type(s) de contenu causent le problème. En dernier recours, envisagez de diviser quelques éléments de contenu exceptionnellement volumineux en éléments séparés. Si le problème concerne un type de contenu personnalisé, examinez le code du plugin et envisagez d'indexer moins de contenu disponible par élément.

## Problèmes d'Espace Disque Insuffisant

Les tables d'index de recherche intelligente peuvent croître rapidement ! La table *#__finder_links_termsX* contient une ligne par terme/phrase par élément de contenu et un unique article Joomla contenant 1000 mots entraînera typiquement l'ajout d'environ 3000 lignes à ces tables. Un second article de taille similaire ajoutera un nombre similaire de lignes même si les deux articles contiennent les mêmes mots. Un site avec des dizaines de milliers d'articles, dont certains peuvent contenir des milliers de mots, est susceptible de se retrouver avec cette table de correspondance contenant des millions de lignes. Il n'est pas rare que les tables d'index occupent plusieurs gigaoctets d'espace disque dans de telles circonstances.

L'index a une option pour choisir entre la précision de la recherche et la taille de l'index. Lorsque vous avez activé "Recherche de phrases" dans les options globales du composant, votre index sera plus grand, mais il permettra également d'obtenir des résultats de recherche plus précis. Le désactiver signifiera un index beaucoup plus petit, mais aussi l'impossibilité de rechercher des phrases entières.

## Notes

1. Il n'existe actuellement aucun verrouillage de concurrence pour empêcher plus d'un processus de faire fonctionner l'indexeur en même temps. Cela entraînera presque certainement un index corrompu. Même quelqu'un enregistrant des modifications sur un élément de contenu pendant qu'un index complet est effectué pourrait potentiellement endommager l'index.

*Traduit par openai.com*

