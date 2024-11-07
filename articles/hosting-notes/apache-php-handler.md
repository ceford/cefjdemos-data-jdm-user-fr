<!-- Filename: J4.x:Apache_PHP_Handler / Display title: Gestionnaires Apache PHP -->

## Notes

Pour déterminer la méthode utilisée par votre serveur web pour gérer les fichiers PHP, utilisez les liens **Administrateur / Système / Informations système** et sélectionnez l'onglet Informations PHP. Recherchez la page pour **API du serveur**. Les moyens courants pour un serveur web Apache de gérer les fichiers PHP incluent les suivants :

### DSO (mod_php)

- **Avantage :** l'un des gestionnaires les plus rapides disponibles.
- **Inconvénient :** fonctionne uniquement avec une seule version de PHP ; les fichiers enregistrés par des scripts PHP sont détenus par l'utilisateur Apache **sauf** lorsqu'ils sont utilisés en conjonction avec mod_ruid2.
- **Pour reconnaître :** API du serveur - Apache 2.0 Handler

### CGI/FastCGI

- **Avantage :** les scripts s'exécutent en tant qu'utilisateur du domaine ou sous-domaine, gestionnaire très rapide.
- **Inconvénient :** plus lent que mod_php, ne peut pas modifier la configuration PHP dans un fichier .htaccess.
- **Pour reconnaître :** API du serveur - CGI/FastCGI

### FPM/FastCGI

- **Avantage :** très rapide, niveau supplémentaire de flexibilité.
- **Inconvénient :** utilise plus de mémoire que la plupart des autres, ne peut pas modifier la configuration PHP dans un fichier .htaccess.
- **Pour reconnaître :** API du serveur - FPM/FastCGI

### LSAPI (mod_lsapi)

- **Avantages :**
   - Fournit un support pour la mise en cache.
   - C'est le gestionnaire le plus performant avec une faible empreinte mémoire.
   - Aucune configuration nécessaire.
   - Peut fonctionner avec plusieurs versions de PHP dans une même configuration.
   - Prend en charge les directives de configuration PHP via les fichiers .htaccess.
   - Sécurisé car les scripts s'exécutent en tant que propriétaire du domaine.
- **Inconvénients :**
   - Ne rend pas disponibles toutes les capacités LSAPI.
- **Pour reconnaître :** API du serveur - ?

Sur un ordinateur portable ou de bureau local, vous pouvez utiliser mod_php, mais vous devrez peut-être définir l'utilisateur Apache sur votre propre nom d'utilisateur et pointer la racine du document vers un emplacement dans votre propre espace de fichiers. Sinon, vous aurez des problèmes de permissions de fichiers et de dossiers.

Sur un service d'hébergement, vous devez utiliser l'une des alternatives FastCGI ou LSAPI. Les services d'hébergement peuvent vous offrir un choix.

*Traduit par openai.com*

