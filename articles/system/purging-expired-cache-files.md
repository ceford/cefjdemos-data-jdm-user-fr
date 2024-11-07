<!-- Filename: Purging_expired_cache_files / Display title: Purger le cache expiré  -->

## Fichiers de Cache

Les fichiers de cache sont des fichiers temporaires créés pour améliorer la performance de votre site. Vous devez vous assurer que les fichiers de cache qui ont expiré, et qui ne sont donc plus nécessaires, sont supprimés du système. Sinon, vous finirez par manquer d'espace disque.

Les fichiers de cache expirés peuvent être purgés depuis l'interface Administrateur ou via l'interface de ligne de commande (CLI).

## Purge - Méthode Administrateur

Depuis le *Tableau de Bord Accueil*
* Sélectionnez l'option **Cache** dans le panneau *Système*.
* Sur la page *Maintenance: Vider le cache*, sélectionnez le bouton **Vider le cache expiré** dans la barre d'outils.

## Purge - Méthode en ligne de commande

Ouvrez une fenêtre de terminal et accédez au répertoire `cli` à la racine de votre site.  
Si vous ne savez pas quelles commandes CLI sont disponibles, exécutez la commande suivante : 
```bash
php joomla.php
```  
Vous verrez une liste de commandes disponibles. La commande `cache` est :  
```bash
php joomla.php cache:clean
```  
Il devrait y avoir un message de confirmation en vert ou peut-être un message d'erreur en bordeaux.  

## Suppression automatique des fichiers de cache expirés

Vous pouvez supprimer automatiquement les fichiers de cache expirés en utilisant une tâche cron. Les services d'hébergement facilitent cette tâche en fournissant un formulaire pour sélectionner la fréquence d'exécution d'une tâche et la commande à utiliser. Ainsi, vous pouvez choisir de programmer le cron pour qu'il s'exécute tous les jours à 05:00 avec la commande suivante :
```
/usr/local/bin/ea-php82 /home/username/public_html/cli/joomla.php cache:clean
```
La plupart des gestionnaires de tâches *cron* vous permettent de saisir une adresse e-mail à laquelle le résultat du cron sera envoyé. Si vous ne souhaitez pas qu'un message soit envoyé, ajoutez ` > /dev/null 2>&1` à la commande.

La version de PHP utilisée en ligne de commande est souvent différente de celle utilisée pour la diffusion d'un site web. Elle pourrait être incompatible avec Joomla. Utilisez donc le chemin complet vers la version de PHP que vous souhaitez utiliser plutôt que `php` seul.

*Traduit par openai.com*

