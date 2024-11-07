<!-- Filename: J4.x:Fix_%22Database_Table_Structure_NOT_Up_to_Date%22_before_Update / Display title: Structure de la Table de Base de Données  -->

## Erreurs Signalées

Lors de la mise à jour de Joomla!, la structure des tables de la base de données doit être à jour avant que le processus puisse commencer. Le *Contrôle Pré-Mise à Jour pour Joomla* se plaint si ce n'est pas le cas.

Mais lorsque vous allez dans **Système → Maintenance → Base de données**, il n'y a aucune entrée disponible. Cela a été signalé dans plusieurs versions de Joomla! 4.x.

## Quelle est la cause

Le problème est causé par une table `#__schemas` vide dans la base de données. Cela se produit très probablement lorsque l'instance Joomla! n'est pas installée par l'installateur officiel de Joomla! mais via un script personnalisé qui n'a pas rempli toutes les données requises.  

## Comment réparer

Vous pouvez résoudre ce problème en ajoutant la valeur manquante à la table. En utilisant phpMyAdmin (ou un autre client de base de données), allez à la table `#__extensions`. Recherchez name='files_joomla' et notez l'extension_id (dans notre cas *211*).

Ensuite, vous devez connaître le dernier script SQL installé. Allez dans `administrator/components/com_admin/sql/updates/mysql` et trouvez le nom de fichier avec la version la plus élevée. Dans cet exemple, supposons que *4.0.3-2021-09-05.sql* soit le nom de fichier avec la version la plus élevée. Maintenant, vous devez l'ajouter dans votre requête d'insertion en tant que deuxième valeur :

```sql
INSERT INTO `#__schemas` (`extension_id`, `version_id`) VALUES (211, '4.0.3-2021-09-05');
```

ou pour PostgreSQL :

```sql
INSERT INTO "#__schemas" ("extension_id", "version_id") VALUES (211, '4.0.3-2021-09-05');
```

Remplacez `#__` par votre préfixe de base de données avant d'exécuter les instructions.

Ensuite, depuis le menu Administrateur, allez à **Système → Maintenance → Base de données** et réparez les tables.

Maintenant, la mise à jour devrait fonctionner comme prévu.

*Traduit par openai.com*

