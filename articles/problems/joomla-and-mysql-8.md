<!-- Filename: Joomla_and_MySQL_8 / Display title: Joomla et MySQL 8 -->

## Problème du plugin d'authentification MySQL par défaut

Il n'est pas possible de se connecter à une base de données MySQL 8 en
utilisant Joomla
<img src="https://docs.joomla.org/images/4/4d/Compat_icon_3_x.png"
decoding="async" data-file-width="40" data-file-height="17" width="40"
height="17" alt="Joomla 3.x" />. La raison en est que MySQL 8 a beaucoup
de changements sous le capot. Un changement qui affecte Joomla est le
plugin d'authentification par défaut qui est `sha256_password` au lieu
de `mysql_native_password`. Le pilote PHP MySQL natif ne supporte pas
MySQL 8 avec ce plugin, mais d'autres langages de programmation tels que
GO ou PERL ont aussi des difficultés. <a
href="https://github.com/php/php-src/commit/d6e81f0bfd0cb90586dd83d4fd47a4302605261a"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">PHP 7.3 (alpha)</a> est cependant
compatible avec MySQL 8.

## Solution pour que Joomla fonctionne avec MySQL 8

Heureusement, il existe une solution de contournement ! Nous pouvons
utiliser le plugin d'authentification par défaut
` mysql_native_password ` pour MySQL. Nous devons ouvrir notre fichier
de configuration ` sudo nano /etc/my.cnf ` (veuillez noter que votre
fichier peut être dans un répertoire différent) et ajouter la
configuration suivante :

    [mysqld]
    default-authentication-plugin=mysql_native_password

Si vous n'avez pas accès à votre fichier de configuration, vous pouvez
mettre à jour votre utilisateur comme suit :

    ALTER USER 'username'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

Remplacez le nom d'utilisateur par le nom du compte utilisateur et le
mot de passe avec le mot de passe appartenant au compte. Redémarrez
MySQL et vous avez terminé, mais seulement si vous avez installé Joomla
3.8 ou 3.9.

## Comment fonctionne le plugin d'authentification par défaut MySQL

L'avantage de `mysql_native_password` est qu'il supporte un mécanisme de
challenge-response qui est très rapide et ne nécessite pas de connexion
cryptée. Cependant, `mysql_native_password` repose sur l'algorithme SHA1
et NIST a recommandé d'arrêter de l'utiliser.

En outre, si deux comptes d'utilisateur utilisent le même mot de passe,
la transformation ` mysql_native_password ` est la même dans la table
mysql.user. Bien que le hachage n'expose pas les informations sur le mot
de passe réel, il indique toujours les deux utilisateurs qui utilisent
le même mot de passe. Pour éviter cela, Salt devrait être utilisé. Salt
est essentiellement un nombre aléatoire utilisé comme l'une des entrées
des fonctions de hachage cryptographiques utilisées pour transformer les
mots de passe des utilisateurs. Puisque Salt est aléatoire et différent
pour chaque exécution, même si deux utilisateurs utilisent les mêmes
mots de passe, le résultat final de la transformation sera très
différent. Depuis MySQL 5.6, le plugin d'authentification
sha256_password est supporté. Il utilise plusieurs tours de hachage
SHA256 sur un mot de passe salt pour s'assurer que la transformation de
hachage est plus sécurisée. Cependant, il nécessite des connexions
chiffrées ou la prise en charge d'une paire de clés RSA. Ainsi, alors
que la sécurité par mot de passe est renforcée, des connexions
sécurisées et plusieurs cycles de transformations de hachage nécessitent
plus de temps dans le processus d'authentification.

cache_sha2_password essaie de combiner le meilleur des deux mondes.
<sup>[\[1\]](#cite_note-1)</sup>

1.  <span id="cite_note-1">[↑](#cite_ref-1) <a
    href="https://mysqlserverteam.com/mysql-8-0-4-new-default-authentication-plugin-caching_sha2_password/"
    class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://mysqlserverteam.com/mysql-8-0-4-new-default-authentication-plugin-caching_sha2_password/</a></span>
