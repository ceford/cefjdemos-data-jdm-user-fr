<!-- Filename: Setting_up_automatic_Smart_Search_indexing / Display title: Indexation de recherche intelligente   -->

## Indexation Automatique

Bien que l'index de Recherche Intelligente soit automatiquement mis à jour chaque fois que des éléments de contenu sont modifiés, il existe certaines circonstances où vous devez relancer l'indexeur. Vous pouvez le faire manuellement en utilisant le bouton de la barre d'outils Index sur la page Recherche Intelligente : Contenu Indexé. Cependant, si vous avez besoin de réindexer le contenu automatiquement, il est également possible de lancer l'indexeur à partir de la ligne de commande. Cela rend particulièrement pratique l'exécution de l'indexeur depuis un travail *cron*.

Depuis le répertoire cli, la ligne de commande est :

```
php joomla.php finder:index
```

La sortie typique de l'indexeur en ligne de commande se présente comme suit :

    INDEXEUR Recherche Intelligente
    ============================

    Démarrage de l'Indexeur
    Configuration des plugins Finder
    Configuré 154 éléments en 0,094 secondes.
     * Lot traité 1 en 0,213 secondes.
     * Lot traité 2 en 0,182 secondes.
     * Lot traité 3 en 0,177 secondes.
     * Lot traité 4 en 0,009 secondes.
    Temps total de traitement : 0,676 secondes.

## Purge avant l'indexation

En général, exécuter l'indexeur effectuera une mise à jour incrémentielle de l'index. C'est-à-dire qu'il ne mettra à jour l'index que pour les éléments de contenu qui ont changé depuis la dernière mise à jour de l'index. Cependant, si vous avez besoin de supprimer complètement toutes les entrées existantes de l'index avant de le reconstruire entièrement, vous devez effectuer une opération de "purge puis indexation". Pour cela, vous pouvez ajouter l'argument `--purge` à la ligne de commande, comme ceci :

    php joomla.php finder:index -- purge

Notez que cela tentera de préserver tous les filtres statiques que vous avez pu configurer, alors qu'en cliquant sur le bouton "Purge" dans la barre d'outils de l'administrateur, vos filtres statiques ne seront **pas** préservés.

## Configuration d'une tâche *cron*

Bien que les détails spécifiques soient en dehors de la portée de cet article, en général, vous devrez simplement entrer la commande ci-dessus dans le gestionnaire de tâches *cron* et spécifier l'heure ou les heures auxquelles la tâche doit être exécutée. Vous devrez probablement inclure le chemin complet vers l'indexeur. Par exemple, comme ceci :

```php
php /var/www/myjoomla/cli/joomla.php finder:index -- purge
```

Et possiblement le chemin complet vers le fichier php, tel que `/usr/local/opt/php@8.2/bin/php`.

## Problèmes de Mémoire Insuffisante

Si votre site a des exigences d'indexation particulièrement complexes, il est possible que l'allocation standard de mémoire ne soit pas suffisante pour que l'indexeur s'exécute jusqu'à son terme. Vous pouvez augmenter la mémoire allouée à l'indexeur en ligne de commande en utilisant un paramètre supplémentaire sur la ligne de commande, comme ceci :

```php
php -d memory_limit=256M joomla.php finder:index
```

Remplacez le `256M` par ce qui est approprié pour votre situation.

L'indexeur en ligne de commande utilise les mêmes paramètres que l'indexeur sur la page Recherche intelligente : Contenu indexé. Vous pouvez modifier les paramètres en utilisant le bouton Options de la barre d'outils sur cette page. Notez que les deux champs **Taille de Lot de l'Indexeur** et **Limite de la Table de Mémoire** influencent la quantité de mémoire utilisée par l'indexeur.

*Traduit par openai.com*

