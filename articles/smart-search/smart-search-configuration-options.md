<!-- Filename: Smart_Search_configuration_options / Display title: Options de Recherche Intelligente -->

## À propos des options

Les options vous permettent de gérer les paramètres globaux de la recherche intelligente. Les paramètres des options sont hérités par les vues, mais les paramètres d'un élément de menu remplaceront les paramètres globaux.

Le panneau des options est divisé en deux parties. Lorsque vous avez terminé d'apporter des modifications, sélectionnez le bouton Enregistrer, sinon sélectionnez le bouton Annuler pour abandonner les modifications.

## Options de Recherche

Les options de recherche contrôlent le comportement des formulaires de recherche et des résultats de recherche pour l'interface Finder.

- **Description du Résultat** - Cette option contrôle si les résultats de recherche doivent être affichés avec des descriptions. Par défaut, elle est activée.
- **Longueur de la Description** - Cette option contrôle la longueur maximale en caractères des descriptions des résultats de recherche. Les descriptions sont tronquées à la longueur maximale, mais la troncature est toujours effectuée au dernier caractère d'espace pour éviter de couper un mot en deux. Efficace uniquement lorsque l'option Description du Résultat est activée. Par défaut, 255 caractères.
- **URL du Résultat** - Cette option contrôle si les résultats de recherche doivent être affichés avec des URLs sous la description (si activée). Par défaut, elle est activée.
- **Recherche Avancée** - Cette option contrôle si les options de recherche avancée doivent être affichées. Par défaut, elle est activée.
- **Étendre la Recherche Avancée** - Les options de recherche avancée sont contenues dans un conteneur rétractable. Cette option contrôle si le conteneur des options de recherche avancée doit être déployé par défaut. Par défaut, elle est désactivée.
- **Filtres de Date** - Cette option contrôle si les filtres de date doivent être affichés dans les options de recherche avancée. Par défaut, elle est désactivée.
- **Étiquettes de Résultat** - Cette option contrôle si les résultats de recherche doivent être affichés avec des Étiquettes. Nécessite l'installation des Étiquettes JXtended. Par défaut, elle est activée.
- **Mettre en Évidence les Termes de Recherche** - Cette option contrôle si les termes de recherche doivent être mis en évidence dans les résultats de recherche. Par défaut, elle est activée.

## Options d'index

Les options d'index contrôlent le comportement de l'indexeur utilisé pour traiter et analyser le contenu à rechercher. La plupart des paramètres, tels que le multiplicateur de poids et les options de stemmer, ne produiront pas de modifications immédiates car ils sont utilisés lors de l'indexation et les effets de ces modifications ne se verront qu'après la purge et le réexécution de l'index.

- **Taille de lot de l'indexeur** - Cette option contrôle la taille des lots de l'indexeur. L'indexeur de recherche intelligente divise le processus d'indexation total en plusieurs lots pour réduire la charge du serveur et éviter les limites de mémoire et de temps d'exécution de PHP. Si les éléments de contenu indexés sont particulièrement courts et/ou le serveur est particulièrement rapide, l'indexeur peut traiter plus d'éléments par lot. Cependant, si les éléments de contenu indexés sont particulièrement longs et/ou le serveur est particulièrement lent, l'indexeur doit traiter moins d'éléments par lot. Par défaut à 50.
- **Limite de table mémoire** - Cette option contrôle la limite de table mémoire. L'indexeur de recherche intelligente utilise des tables mémoire MySQL pour stocker temporairement les données de contenu au lieu de les stocker dans les tampons de mémoire de PHP car les éléments de contenu volumineux épuiseront rapidement les paramètres de limite de mémoire par défaut de PHP. Cependant, les tables mémoire MySQL ont également des limites de taille ajustables et les réajuster n'est pas fiable. Ce paramètre est fourni pour gérer les tables mémoire avec des limites de taille plus petites que d'habitude et ne doit être ajusté qu'en cas de rencontres avec des erreurs Table Full lors de l'indexation. Par défaut à 30,000. Si vous rencontrez des erreurs de type "table full", essayez de **réduire** ce paramètre. La valeur optimale devrait donner des tables mémoire légèrement plus petites que le paramètre <a href="http://dev.mysql.com/doc/refman/5.1/en/server-system-variables.html#sysvar_max_heap_table_size" rel="nofollow noreferrer noopener"><em>max_heap_table_size</em></a> dans MySQL, qui par défaut est de 16 mégaoctets.
- **Multiplicateur de poids du texte du titre** - Cette option contrôle l'influence du texte du titre sur le score de pertinence global d'un résultat de recherche. Par défaut à 1,7.
- **Multiplicateur de poids du texte du corps** - Cette option contrôle l'influence du texte du corps sur le score de pertinence global d'un résultat de recherche. Par défaut à 0,7.
- **Multiplicateur de poids des méta-données** - Cette option contrôle l'influence du texte des méta-données sur le score de pertinence global d'un résultat de recherche. Par défaut à 1,2.
- **Multiplicateur de poids du texte du chemin** - Cette option contrôle l'influence du texte du chemin/URL sur le score de pertinence global d'un résultat de recherche. Par défaut à 2,0.
- **Multiplicateur de poids du texte divers** - Cette option contrôle l'influence du texte divers sur le score de pertinence global d'un résultat de recherche. Par défaut à 0,3.
- **Stemmer** - Cette option contrôle quel stemmer de langue doit être utilisé lors de l'indexation. Le stemmer English Only est une implémentation en pur PHP qui n'a pas de dépendances. Le stemmer Snowball nécessite l'extension PHP Stem mais offre un support pour 14 langues incluant le danois, l'allemand, l'anglais, l'espagnol, le finnois, le français, le hongrois, l'italien, le norvégien, le néerlandais, le portugais, le roumain, le russe et le turc. Par défaut à English Only.
- **Activer la journalisation** - crée un fichier journal pendant le processus d'indexation. Par défaut à non.

*Traduit par openai.com*

