<!-- Filename: How_do_you_convert_an_htaccess.txt_file_into_a_.htaccess_file%3F / Display title: Comment convertir un fichier htaccess.txt en fichier .htaccess ? -->

### Introduction

Lors de l'utilisation de PHP en tant que module Apache, vous pouvez
modifier les paramètres de configuration en utilisant les directives
dans les fichiers de configuration d'Apache (par exemple, les fichiers
httpd.conf et .htaccess). Pour le faire, vous aurez besoin des
privilèges "AllowOverride Options" ou "AllowOverride All". Si vous avez
le contrôle sur votre propre configuration Apache, vous pouvez et devez
utiliser httpd.conf. Si vous n'avez pas le contrôle sur votre
configuration Apache (par exemple en cas de un serveur partagé), vous
devez utiliser les fichiers .htaccess.

### Procédure

1.  Il convient tout d'abord de localiser par FTP le fichier
    htaccess.txt dans le répertoire à la racine de votre site. Le
    fichier a du s'installer au cours de l'installation de Joomla!.
    (Notez que ce nom de fichier ne commence pas par un point). Ouvrez
    et lisez attentivement le fichier htaccess.txt. Il contient des
    suggestions importantes pour la protection de votre site.
2.  Faites dans ce fichier, les ajustements approprié pour votre site,
    et enregistrez dans votre répertoire à la racine du site sous le
    nom : .htaccess (y compris avec le point au début). Assurez-vous
    d'avoir décoché la case pour l'option "Masquer les fichiers qui
    commencent par un point" dans votre programme FTP.
3.  Testez votre site en frontend et backend. Si des erreurs se
    produisent, renommez le fichier htaccess.txt et corrigez vos
    modifications. Si vous ne parvenez pas à le faire fonctionner, vous
    pourriez avoir à laisser le fichier nommé htaccess.txt.
4.  Utilisez la fonction phpinfo() pour vous assurer que toutes les
    configurations sont définies comme vous le souhaitez. Note : les
    fichiers accessibles par le web et qui intègrent la fonction
    phpinfo() présentent des risques potentiels pour la sécurité
    puisqu'ils peuvent fournir de nombreuses informations utiles
    concernant votre serveur. Il faut toujours supprimer ces fichiers
    après utilisation.

### Informations complémentaires

- <a href="http://us2.php.net/configuration.changes" class="external text"
  target="_blank" rel="nofollow noreferrer noopener">Documentation
  officielle PHP : Comment modifier la configuration ?</a>
- <a href="http://us2.php.net/manual/en/ini.php#ini.list"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Documentation officielle PHP : List
  of PHP INI directives</a>
