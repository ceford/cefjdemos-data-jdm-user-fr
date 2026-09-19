<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "Configuration de Docker",
    "description": "",
    "author": ""
}
-->

## Configurer un environnement Joomla local à l’aide de Docker

Pour faire fonctionner Joomla sur votre ordinateur, quatre éléments sont nécessaires : 
- télécharger et configurer un serveur web **Apache** ou **nginx**, 
- un service de base de données comme **MySQL ou** **MariaDB**, 
- et, bien sûr, nous avons besoin de **PHP** 
- et de **Joomla.** 

Pour que tous ces éléments différents puissent effectivement communiquer entre eux, la plupart
d’entre nous utilisent des logiciels préconfigurés comme **XAMPP**, **Laragon** ou **FlyEnv**.

Cependant, les configurations traditionnelles peuvent facilement entraîner des conflits de ports ou
des serveurs de bases de données qui refusent mystérieusement de démarrer. Lorsqu’un serveur local
tombe en panne, vous pouvez vous retrouver à télécharger et à réinstaller manuellement des sites
Joomla entiers encore et encore, simplement pour tester une seule PR,
et risquer de perdre votre travail en corrigeant un bug. Cela consomme un temps précieux, et les
correctifs ne sont généralement que des solutions temporaires.

**Le passage à Docker ([En savoir plus sur Docker](https://docs.docker.com/get-started/))** 
Avec Docker, vous pouvez

ignorez entièrement la configuration manuelle. Au lieu d’installer des
serveurs web directement sur votre ordinateur, il vous suffit d’écrire un
seul fichier de « recette ». Docker télécharge, isole et connecte
automatiquement tous les éléments en arrière-plan. Si quelque chose tombe
en panne, vous ne réinstallez pas toute votre configuration ; vous
redémarrez simplement le conteneur.

Dans ce guide, vous apprendrez la façon la plus simple de mettre en place un
environnement Joomla local avec Docker, afin de passer moins de temps à
réparer des serveurs et plus de temps à contribuer.

### Prérequis

Une seule chose doit être installée avant de commencer : **Docker Desktop**.

- Téléchargez-le depuis [**docker.com**](https://www.docker.com/) et exécutez
  le programme d’installation
- Sous Windows, laissez l’option « Use WSL 2 instead of Hyper-V » cochée -
  cela accélère les choses
- Ouvrez Docker Desktop et attendez que le coin inférieur gauche affiche
  l’état vert **Engine running**.

![Docker Desktop](../../../en/images/hosting-local/docker-setup/01-docker-setup-desktop.png)

C’est tout.

### Le fichier docker-compose.yml

Lorsque vous avez besoin que plusieurs services communiquent entre eux — comme
un serveur web (Apache/Nginx), PHP et une base de données (MySQL/MariaDB) — vous
utilisez un fichier spécial d’orchestration appelé `docker-compose.yml`. Ce fichier
sert de modèle pour votre projet, en définissant tous les services nécessaires et
la manière dont ils collaborent. (L’image officielle Docker de Joomla est en fait
basée sur une image PHP et Apache. Cela signifie qu’en utilisant uniquement cette
image Joomla, vous disposez de PHP, d’Apache et de Joomla réunis).

Commencez par créer un nouveau dossier sur votre ordinateur pour votre projet (par
exemple, sur votre Bureau, créez un dossier appelé `joomla-docker`).

Dans ce dossier, créez un nouveau fichier texte et donnez-lui exactement ce nom :

    docker-compose.yml

Ouvrez ce fichier dans n’importe quel éditeur de texte (comme VS Code ou le
Bloc-notes), collez le code suivant exactement tel quel, puis enregistrez-le :

```
    services:
      joomla:
        image: joomla:latest
        ports:
          - "8080:80"
        environment:
          - JOOMLA_DB_HOST=db
          - JOOMLA_DB_USER=joomla
          - JOOMLA_DB_PASSWORD=joomlapass
          - JOOMLA_DB_NAME=joomladb
        depends_on:
          - db
      db:
        image: mariadb:10.11
        environment:
          - MYSQL_ROOT_PASSWORD=rootpass
          - MYSQL_DATABASE=joomladb
          - MYSQL_USER=joomla
          - MYSQL_PASSWORD=joomlapass
        volumes:
          - db_data:/var/lib/mysql
    volumes:
      db_data:
```

### Démarrage de l’environnement

Ouvrez votre terminal (ou PowerShell sous Windows), accédez à votre dossier `joomla-docker`
et exécutez :

```
    docker compose up -d
```

La première fois que vous exécutez cette commande, Docker télécharge les
images Joomla et MariaDB, ce qui peut prendre une ou deux minutes selon la
vitesse de votre connexion Internet. Ensuite, chaque démarrage ultérieur est
presque instantané, comme vous pouvez le voir ci-dessous.

![Sortie du terminal lors du démarrage de Docker](../../../en/images/hosting-local/docker-setup/02-docker-setup-terminal-transcript.png)

### L’installateur Joomla

Ouvrez votre navigateur et accédez à `http://localhost:8080`. Vous devriez voir
l’écran d’installation de Joomla.

![Configuration du site de l’installateur Joomla](../../../en/images/hosting-local/docker-setup/03-docker-setup-joomla-installer-sitename.png)

Indiquez le nom de votre site et les informations d’administration sur le premier écran.

![Données de connexion de l’installateur Joomla](../../../en/images/hosting-local/docker-setup/04-docker-setup-joomla-installer-login-data.png)

Lorsque vous atteignez l’écran **Configuration de la base de données**, c’est là
que la plupart des utilisateurs restent bloqués :

**Ne saisissez pas `localhost` comme nom d’hôte.**

Comme la base de données s’exécute dans son propre conteneur, Joomla a besoin du
nom du service du conteneur — et non de localhost. Utilisez exactement les valeurs suivantes :

- **Type de base de données :** MySQLi
- **Nom d’hôte :** `db`
- **Nom d’utilisateur :** `joomla`
- **Mot de passe :** `joomlapass`
- **Nom de la base de données :** `joomladb`

![Configuration de la base de données de l’installateur Joomla](../../../en/images/hosting-local/docker-setup/05-docker-setup-joomla-installer-database-config.png)

Cliquez pour continuer, terminez l’installation, et le tour est joué.

Lorsque vous avez fini de travailler pour la journée, exécutez `docker compose stop` pour
mettez les conteneurs en pause et libérez de la mémoire. Votre site sera exactement là où
vous l’avez laissé la prochaine fois.

------------------------------------------------------------------------

### Problèmes courants

- **La page à l’adresse localhost:8080 ne se charge pas juste après le démarrage :** Le
  conteneur de base de données prend quelques secondes pour terminer son initialisation. Attendez 30
  secondes, puis actualisez la page.
- **Le port 8080 est déjà utilisé :** Remplacez `"8080:80"` par `"8081:80"` dans le
  fichier Compose et accédez-y à l’adresse `localhost:8081`.
- **Les conteneurs ont démarré, mais Joomla affiche une erreur de base de données :** Vérifiez que
  votre nom d’hôte dans l’installateur est `db` et non `localhost`.

### Astuce de pro : accéder aux fichiers Joomla pour le développement

Pour le moment, votre site Joomla fonctionne, mais les fichiers PHP réels
sont cachés à l’intérieur du conteneur Docker. Si vous souhaitez contribuer à Joomla,
tester des PR ou écrire vos propres extensions, vous devez disposer de ces fichiers sur
votre ordinateur afin de pouvoir les ouvrir dans VS Code ou dans votre éditeur préféré.

Pour synchroniser les fichiers du conteneur avec votre disque dur local, il vous suffit
d’ajouter deux lignes(`volumes: `) et (`- ./site_joomla:/var/www/html`)
à la section `joomla` de votre fichier `docker-compose.yml`, comme indiqué ci-dessous :

```yml
services:
  joomla:
    image: joomla:latest
    ports:
      - "8080:80"
    volumes:
      - ./site_joomla:/var/www/html
    # ... (rest of your settings)
```

**Ce que cela fait :** 

La prochaine fois que vous exécuterez `docker compose up -d`, Docker créera automatiquement
un dossier appelé `site_joomla` juste à côté de votre fichier compose. Il
copiera l’intégralité du cœur de Joomla (y compris le panneau d’administration,
les composants et les templates) dans ce dossier.

![Explorateur de l’IDE affichant l’installation de Joomla dans Docker](../../../en/images/hosting-local/docker-setup/06-docker-setup-ide-explorer.png)

Toute modification de code effectuée dans ce dossier sur votre ordinateur sera instantanément
mise à jour dans le conteneur en cours d’exécution ! Vous êtes maintenant entièrement prêt pour le
développement local.

### Astuce bonus 1 : Tester des versions spécifiques de Joomla et PHP

Lors du test des PR, les responsables vous demanderont souvent de tester avec
des versions spécifiques de PHP. Avec XAMPP, rétrograder ou mettre à niveau PHP est un
cauchemar. Avec Docker, cela prend deux secondes.

Au lieu d’utiliser `image: `**`joomla:latest`** dans votre
**`docker-compose.yml`**, vous pouvez spécifier des versions exactes à l’aide de balises. Par exemple, si vous devez tester **Joomla 5.2** avec **PHP 8.3**, il vous suffit de modifier cette ligne en : **`image: joomla:5.2-php8.3-apache`**

Exécutez à nouveau **`docker compose up -d`**, et Docker remplacera instantanément
votre environnement serveur. Vous trouverez toutes les balises de version disponibles sur la
<a href="https://hub.docker.com/_/joomla" class="ng-star-inserted"
target="_blank" rel="noopener" data-hveid="0"
data-ved="0CAAQ_4QMahgKEwjl8vi347CTAxUAAAAAHQAAAAAQkgI">page officielle de Joomla
sur Docker Hub</a>.

### Astuce bonus 2 : Ajouter phpMyAdmin

Si vous venez de **XAMPP**, une interface visuelle pour consulter votre
base de données pourrait vous manquer. Vous pouvez facilement ajouter
**phpMyAdmin** à votre configuration en ajoutant un nouveau **bloc de
service** en bas de votre fichier **`docker-compose.yml`** :

```yml
    phpmyadmin:
        image: phpmyadmin/phpmyadmin:latest
        ports:
          - "8081:80"
        environment:
          - PMA_HOST=db
        depends_on:
          - db
```

Redémarrez vos conteneurs, puis vous pourrez accéder à phpMyAdmin en vous
rendant sur **http://localhost:8081** dans votre navigateur. Connectez-vous
simplement avec **`joomla`** comme nom d’utilisateur et **`joomlapass`**
comme mot de passe.

*Traduit par openai.com*