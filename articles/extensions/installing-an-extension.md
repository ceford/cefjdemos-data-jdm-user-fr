<!-- Filename: Installing_an_extension / Display title: Installation d'une extension -->

Avant de commencer, il est toujours préférable de consulter la
documentation associée à une extension. La plupart des extensions
propose des pages d'accueil et autres forums et il est toujours
intéressant de les consulter en premier. S'il existe un fichier README
inclus dans l'extension, vous devriez également le consulter.

Pour la plupart des extensions et la plupart des utilisateurs, la
procédure sera :

- Télécharger l'extension sur votre ordinateur dans un dossier au format
  zip.
- Depuis le backend de votre site Joomla! (interface d'administration)
  sélectionnez Extensions  **→**  Gérer/Installation.
- Cliquez sur le bouton *Choisissez un fichier* et sélectionnez le
  paquet de l'extension sur votre ordinateur.
- Cliquez sur le bouton **Envoyer & Installer**.
- Certaines extensions peuvent nécessiter d'autres actions pour
  l'installation.
- Notez que les modules et plugins doivent être activés avant de pouvoir
  fonctionner.

Il peut se présenter certaines situations dans lesquelles cette
procédure ne fonctionnera pas.

Parfois, il est nécessaire de décompresser les fichiers en local avant
de les installer. Si vous obtenez un message d'erreur précisant que le
format de fichier n'est pas correcte, il vous sera alors nécessaire de
le décompresser. Après décompression, essayez d'installer les éléments
individuellement. Notez que les fichiers que vous téléchargez à l'aide
de l'installateur doivent toujours être zippés.

Il arrive parfois, vous ne puissiez pas utiliser le programme
d'installation automatisée. Par exemple, des extensions très
volumineuses peuvent dépasser en taille la limite de téléchargement
maximale autorisée par votre hébergeur.

Egalement, si vous voyez une erreur du type :

    Warning: is_dir() [function.is-dir]: open_basedir restriction in effect. File(/) is not within the allowed path(s): ...

cela peut-être du à une restriction de votre compte d'hébergement qui
conduit Joomla! à tenter de vérifier si le répertoire racine existe.
Dans ce cas, vous ne serez pas en mesure d'utiliser le programme
d'installation automatisée.

## Installation manuelle

Tout d'abord, décompressez tous les fichiers dans un répertoire en local
(par exemple `com_installer`). Puis transférer le répertoire (via FTP) à
un dossier dans le répertoire d'installation (par exemple
`administrator/components`), approprié pour le type d'extension que vous
installez (cela peut être retrouvé dans le fichier xml qui aura une
ligne du type :

). Utilisez alors le programme d'installation et sélectionnez "Installer
depuis un répertoire" en indiquant le nom correcte du répertoire. Ce nom
de répertoire doit être un chemin absolu depuis la racine du système de
fichiers.
