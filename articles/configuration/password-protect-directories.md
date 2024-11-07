<!-- Filename: How_do_you_password_protect_directories_using_htaccess%3F / Display title: Protéger les répertoires par mot de passe  -->

## Introduction

Vous pouvez souhaiter protéger un répertoire ou un site entier de l'accès public. Une raison pour faire cela est de refuser l'accès public à un site de développement. Seules les personnes connaissant le nom d'utilisateur et le mot de passe y auront accès. Une autre raison est la paranoïa - par exemple, la protection du dossier administrateur pour que les utilisateurs doivent saisir un nom d'utilisateur et un mot de passe juste pour accéder au formulaire de connexion de l'administrateur Joomla.

La méthode décrite ici est pour les serveurs Apache utilisant un fichier *.htaccess*.

### Mise en garde de Apache.org

L'authentification de base ne doit pas être considérée comme sécurisée selon une définition rigoureuse de la sécurité. Bien que le mot de passe soit stocké sur le serveur dans un format crypté, il peut être transmis du client au serveur en texte clair à travers le réseau. Quiconque écoute avec une variété de renifleurs de paquets pourra lire le nom d'utilisateur et le mot de passe à mesure qu'il passe.

Le nom d'utilisateur et le mot de passe sont transmis à chaque requête, pas seulement lorsque l'utilisateur les saisit pour la première fois. Donc, le renifleur de paquets n'a pas besoin de capter à un moment particulièrement stratégique, mais juste assez longtemps pour voir une seule requête passer à travers le réseau.

En plus de cela, le contenu lui-même est également transmis en clair sur le réseau, et donc si le site web contient des informations sensibles, le même renifleur de paquets aurait accès à ces informations, même si le nom d'utilisateur et le mot de passe n'étaient pas utilisés pour accéder directement au site.

N'utilisez pas l'authentification de base pour quoi que ce soit nécessitant une véritable sécurité. C'est préjudiciable pour la plupart des utilisateurs, car très peu de personnes prendront la peine, ou auront le logiciel ou l'équipement nécessaire, pour découvrir des mots de passe. Cependant, si quelqu'un avait le désir d'entrer, cela lui prendrait peu de temps pour le faire.

L'authentification de base sur une connexion SSL, cependant, sera sécurisée, car tout sera crypté, y compris le nom d'utilisateur et le mot de passe.

## Utilisation de cPanel

Si vous utilisez un service d'hébergement, vous devriez utiliser sa méthode pour la protection des répertoires. Par exemple, cPanel propose une option nommée Confidentialité des répertoires. En la sélectionnant, vous pouvez naviguer jusqu'à n'importe quel répertoire et lui attribuer un nom. Vous aurez ensuite la possibilité de créer un nom d'utilisateur et un mot de passe pour le répertoire nommé. Simple ?

Si vous regardez maintenant dans le répertoire que vous avez protégé, vous trouverez un nouveau fichier .htaccess contenant quelque chose de semblable au paramétrage suivant pour protéger le dossier api de Joomla :

```
#----------------------------------------------------------------cp:ppd
# Section gérée par cPanel : Répertoires protégés par mot de passe     -cp:ppd
# - Ne modifiez pas cette section du fichier htaccess !                -cp:ppd
#----------------------------------------------------------------cp:ppd
AuthType Basic
AuthName "API"
AuthUserFile "/home/username/.htpasswds/public_html/[jroot]/api/passwd"
Require valid-user
#----------------------------------------------------------------cp:ppd
# Fin de la section gérée par cPanel : Répertoires protégés par mot de passe -cp:ppd
#----------------------------------------------------------------cp:ppd
```

Il est important de savoir que la protection des répertoires cPanel peut utiliser le même fichier .htaccess que celui utilisé par Joomla pour d'autres fins.

Si vous regardez dans le fichier de mot de passe cité, vous verrez le nom d'utilisateur que vous avez fourni et la version chiffrée du mot de passe.

La protection peut être retirée en répétant le processus et en décochant la case `Protéger par mot de passe ce répertoire`. Cela supprime la section d'authentification du fichier .htaccess. Cependant, cela ne supprime pas le fichier .htaccess !

## Règles .htaccess

Vous pouvez effectuer toutes les étapes nécessaires manuellement. Cet outil peut vous aider :

<a href="https://www.htaccessredirect.net/"
 rel="nofollow noreferrer noopener"><em>générateur</em> .htaccess</a>

Il crée les fichiers nécessaires pour vous. Vous devez spécifier le nom d'utilisateur,
le mot de passe et le chemin.

Remplissez les deux sections : **Fichier de protection par mot de passe** et **Générateur htpasswd**,
puis sélectionnez le bouton `Générer le code`. Vous obtiendrez le texte pour le
fichier .htaccess et le texte pour le fichier .htpasswd dans des boîtes séparées.
Exemples :
```
//Fichier de protection par mot de passe
<Files /admin>
AuthName "Prompt"
AuthType Basic
AuthUserFile /home/user/.htpasswd
Require valid-user
</Files>
```

```
John:$apr1$a3dbt6j7$KJQr137CY9QuN6tYl6M4Z1
```

*Traduit par openai.com*

