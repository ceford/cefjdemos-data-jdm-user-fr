<!-- Filename: J4.x:Optional_Technical_Requirements / Display title: Exigences Techniques Optionnelles -->

Cette page répertorie les exigences techniques *optionnelles* qui ne sont pas nécessaires pour installer et exécuter Joomla! mais sont requises pour certaines API internes. La liste a été créée pour Joomla 4.

| Élément                   | Description                                                                                                                                     |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Application**           |                                                                                                                                                 |
| JApplicationDaemon        | Nécessite `ext/pcntl` et `ext/posix` de PHP                                                                                                     |
| **Archive**               |                                                                                                                                                 |
| BZ2                       | Nécessite `ext/bz2` de PHP                                                                                                                      |
| GZip                      | Nécessite `ext/zlib` de PHP                                                                                                                     |
| Zip                       | Nécessite `ext/zip` ou `ext/zlib` de PHP                                                                                                        |
| **Cache**                 |                                                                                                                                                 |
| APC                       | Nécessite `ext/apc` de PHP sur PHP 5.3 ou 5.4, `ext/apcu` sur PHP 5.5 ou 5.6, non supporté sur PHP 7.x (Note: CECI DOIT ÊTRE VÉRIFIÉ)            |
| APCu                      | Nécessite `ext/apcu` de PHP sur PHP 5.3+                                                                                                        |
| CacheLite                 | Nécessite le paquet PEAR Cache_Lite (testé sur 1.7.16, fonctionnera avec 1.8)                                                                   |
| Memcache                  | Nécessite `ext/memcache` de PHP et un serveur Memcache (Note: L'extension Memcache n'est pas compatible avec PHP 7.x)                           |
| Memcached                 | Nécessite `ext/memcached` de PHP et un serveur Memcached                                                                                        |
| Redis                     | Nécessite `ext/redis` de PHP et un serveur Redis                                                                                                |
| Wincache                  | Nécessite `ext/wincache` de PHP (Windows seulement)                                                                                             |
| XCache                    | Nécessite `ext/xcache` de PHP                                                                                                                   |
| **Adaptateurs Client**    |                                                                                                                                                 |
| LDAP                      | Nécessite `ext/ldap` de PHP                                                                                                                     |
| HTTP/Curl                 | Nécessite `ext/curl` de PHP                                                                                                                     |
| HTTP/Socket               | Nécessite que la fonction `fsockopen()` de PHP soit activée                                                                                     |
| HTTP/Stream               | Nécessite la fonction `fopen()` de PHP et que `allow_url_fopen` soit activé                                                                     |
| **Cryptographie**         |                                                                                                                                                 |
| JCrypt                    | Nécessite `ext/mcrypt` de PHP pour tous les chiffrements sauf le SodiumCipher qui nécessite `ext/sodium`                                         |
| JKeychain                 | Nécessite `ext/openssl` de PHP                                                                                                                  |
| **Base de Données**       |                                                                                                                                                 |
| Microsoft SQL Azure       | Nécessite `ext/sqlsrv` de PHP (l'extension PHP 5.x ne supporte que Windows, une version compatible Linux de l'extension est disponible pour PHP 7.x) |
| Microsoft SQL Server      | Nécessite `ext/sqlsrv` de PHP (l'extension PHP 5.x ne supporte que Windows, une version compatible Linux de l'extension est disponible pour PHP 7.x) |
| MySQL                     | Nécessite `ext/mysql` de PHP (non supporté sur PHP 7.x)                                                                                         |
| MySQLi                    | Nécessite `ext/mysqli` de PHP                                                                                                                   |
| Oracle                    | Nécessite `ext/pdo` de PHP avec support Oracle (disponible uniquement pour 3PD ; le CMS ne fonctionnera pas avec)                               |
| PDO MySQL                 | Nécessite `ext/pdo` de PHP avec support MySQL                                                                                                   |
| PostgreSQL                | Nécessite `ext/pgsql` de PHP                                                                                                                    |
| SQLite                    | Nécessite `ext/pdo` de PHP avec support SQLite (disponible uniquement pour 3PD ; le CMS ne fonctionnera pas avec)                               |
| **Image**                 |                                                                                                                                                 |
|                           | Nécessite `ext/gd` de PHP                                                                                                                       |
|                           | Nécessite `ext/fileinfo` de PHP                                                                                                                 |
| **Session**               |                                                                                                                                                 |
| APC                       | Nécessite `ext/apc` de PHP sur PHP 5.3 ou 5.4, `ext/apcu` sur PHP 5.5 ou 5.6, non supporté sur PHP 7.x (Note: CECI DOIT ÊTRE VÉRIFIÉ)          |
| Memcache                  | Nécessite `ext/memcache` de PHP et un serveur Memcache (Note: L'extension Memcache n'est pas compatible avec PHP 7.x)                           |
| Memcached                 | Nécessite `ext/memcached` de PHP et un serveur Memcached                                                                                        |
| Wincache                  | Nécessite `ext/wincache` de PHP (Windows seulement)                                                                                             |
| XCache                    | Nécessite `ext/xcache` de PHP                                                                                                                   |
| **AMÉLIORATIONS OPTIONNELLES** |                                                                                                                                          |
| **Chaîne**                |                                                                                                                                                 |
| mbstring                  | Activez `ext/mbstring` de PHP pour que la bibliothèque phputf8 utilise les fonctions natives                                                     |

*Traduit par openai.com*
