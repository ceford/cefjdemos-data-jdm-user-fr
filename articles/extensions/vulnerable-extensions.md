<!-- Filename: jdocmanual?manual=user&heading=extensions&filename=vulnerable-extensions.md / Display title: Extensions Vulnérables -->

## Sources d'extensions

Tout le monde peut rédiger et distribuer une extension Joomla! en tant que service à la communauté mondiale. Ces extensions de **tiers** peuvent être trouvées sur les sites web de développeurs d'extensions professionnels, des blogs personnels, GitHub et des dépôts similaires, ainsi que sur le site web de l'annuaire des extensions Joomla.

## Extensions Vulnérables

Très peu de sources proposent des extensions délibérément malveillantes. En général, une **extension vulnérable** est celle dans laquelle une faille de sécurité a été découverte (ou à laquelle elle contribue) après sa sortie initiale.

Les extensions vulnérables ne sont pas nécessairement mal codées. À mesure que le Web évolue, les exigences techniques et les pratiques de codage communément acceptées changent. Les projets actifs publient de nouvelles versions de leurs extensions au fur et à mesure que les exigences changent et corrigent rapidement toute vulnérabilité signalée.

Si vous vous inquiétez de l'une de vos extensions, vous devriez consulter la liste des Extensions Vulnérables de Joomla (VEL) qui contient des informations sur plus de 240 extensions, principalement anciennes.

## Le Vérificateur JED

Si vous êtes préoccupé par une extension qui n'apparaît pas dans le VEL, vous pouvez utiliser l'extension JED Checker. C'est une extension utilisée pour vérifier les extensions soumises pour apparaître dans la liste du Répertoire des Extensions Joomla. Elle s'installe comme n'importe quelle autre extension. Lors de son utilisation, elle accepte un fichier zip d'extension et examine son contenu pour vérifier la conformité avec les normes JED. Elle est extrêmement utile même pour les extensions qui n'apparaissent pas dans la liste JED. Voici une capture d'écran d'exemple :

![résultat du vérificateur jed](../../../en/images/extensions/extensions-jed-checker.png)

Les 400 fichiers PHP avec avis de licence GPL manquant se trouvent dans des bibliothèques tierces avec une licence différente. Les 30 fichiers identifiés par le script de scan anti-malware Joomla se trouvent également dans ces bibliothèques tierces. Il y a du travail à faire sur les fichiers manquant de sécurité JEXEC !

## Suppression d'une Extension Vulnérable

### Faire une Liste des Fichiers à Supprimer

Si vous pouvez le localiser, lisez le fichier xml de l'extension pour déterminer exactement quels répertoires, fichiers et tables de base de données ont été ajoutés à votre système. Le fichier XML se trouve dans l'archive zip originale utilisée lors du processus d'installation de l'extension. Par exemple, l'archive zip pour une extension appelée mod_vulnerable contiendrait un fichier XML appelé mod_vulnerable.xml, et pourrait contenir une liste de fichiers comme la suivante :

```
    mod_vulnerable.php
    mod_vulnerable/vulnerable_file.txt
    mod_vulnerable/another_vulnerable_file.txt
    mod_vulnerable/yet_another_vulnerable_file.txt
    mod_vulnerable/index.html
```

### Désinstaller Via l'Installeur Joomla

En utilisant l'installeur dans l'interface d'administration de Joomla!, désinstallez l'extension vulnérable. Vous devrez peut-être également désinstaller les modules, composants ou plugins associés.

### Vérifier que le Processus de Désinstallation est Complet

Ne faites pas confiance à l'extension pour supprimer en toute sécurité tous ses fichiers. Comparez les répertoires et les fichiers sur votre système avec la liste XML de l'extension pour vous assurer que tous les fichiers liés ont bien été supprimés.

### Optionnellement, Supprimer les Tables de Base de Données Associées

Vérifiez votre base de données et supprimez toutes les tables créées par l'extension. Pour faciliter le processus de mise à niveau vers de nouvelles versions, de nombreux scripts de désinstallation ne suppriment pas les tables de base de données associées. Vous pouvez trouver la liste des tables dans le fichier XML de chaque extension.

Si vous prévoyez d'installer une version plus sûre et compatible de la même extension et souhaitez réutiliser les données existantes, vous pouvez généralement laisser les tables de base de données en l'état.

### Supprimer les Liens de Menu

Simplement supprimer les liens de menu vers une extension, ou dépublier un module n'est **pas** suffisant pour protéger votre site ! Tant que les fichiers de l'extension existent sur votre serveur, vous êtes vulnérable. Notez comment, dans les exemples suivants, un attaquant peut contourner le fichier index de Joomla! pour cibler directement n'importe quel fichier, de n'importe quelle extension.

```
    www.votre_site.org/components/com_bad_component/vulnerable_file.php
    www.votre_site.org/modules/mod_bad_module/vulnerable_file.php
```

*Traduit par openai.com*

