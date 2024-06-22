<!-- Filename: Common_problems_when_enabling_Search_Engine_Friendly_(SEF)_URLs / Display title: Problèmes courants lors de l'activation de la réécriture d'URL en clair (SEF) -->

Activer la réécriture d'URL en clair (SEF) peut générer des erreurs si
votre hébergeur de site n'est pas correctement configuré pour supporter
la réécriture d'URL. Il existe de nombreuses combinaisons de
technologies de serveurs et de systèmes d'exploitation, donc même s'il
n'est pas possible de donner des réponses certaines à chaque problème de
réécriture d'URL, les problèmes les plus courants sont cependant listés
ci-dessous.

## Votre serveur utilise-t-il Apache ?

Lorsque vous activez la réécriture des URL (SEF) dans Joomla!, il est
possible de réécrire les URLs sans /index.php/ ce qui demande l'usage de
mod_rewrite (ou l'équivalent pour IIS) - si votre serveur n'utilise pas
Apache, ou n'a pas la possibilité de réécrire les URLs de cette manière,
des messages d'erreur vont s'afficher lorsque ce paramètre est activé.
Désactivez ce paramètre et vérifiez si la réécriture fonctionne sans
cela.

Vérifiez aussi que vous avez une section 'Directory' dans le fichier de
configuration de Apache qui autorise la surcharge du fichier .htaccess,
sinon le fichier .htaccess dans le répertoire racine de Joomla! SERA
IGNORE. La ligne nécessaire est :

     AllowOverride all

## Votre serveur utilise-t-il IIS ?

Si vous utilisez IIS, référez-vous à ces liens qui peuvent vous être
utiles ː

- IIS
- <a href="https://docs.joomla.org/IIS6_and_SEF_URLs_using_Joomla_1.5x"
  class="mw-redirect" title="IIS6 and SEF URLs using Joomla 1.5x">IIS6 and
  SEF URLs using Joomla 1.5x</a>
- <a href="https://docs.joomla.org/IIS7_and_SEF_URLs_using_Joomla_1.5x"
  class="mw-redirect" title="IIS7 and SEF URLs using Joomla 1.5x">IIS7 and
  SEF URLs using Joomla 1.5x</a>

## Avez-vous vidé votre cache ?

Lorsque vous effectuez des modifications de paramétrage SEF il est
conseillé de vider son cache, et si vous mettez en cache les URL (par
exemple via l'utilisation d'une extension tierce SEF), effectuez les
modifications nécessaire aussi et videz les URLs mises en cache si
nécessaire.

## Avez-vous changé vos domaines ?

Parfois, si vous avez modifié vos noms de domaines (par exemple de
localhost ou d'un environnement de test vers un domaine de production)
vous devez changer la valeur de la variable `$live_site` dans le fichier
configuration.php présent à la racine de votre site Joomla. La valeur de
cette variable doit être modifiée manuellement. Elle ne se trouve pas
dans les écrans de la configuration globale du site d'administration.

Généralement, cela ressemblera à cela :

    var $live_site = 'http://example.com';

Ou, si vous accéder à votre site web dans un sous-répertoire nommé
joomla, cela ressemblera à cela ː

    var $live_site = 'http://example.com/joomla';

Lorsque vous déplacez vos domaines, cette valeur peut exiger une
modification pour prendre en compte le changement de domaine ː

    var $live_site = 'http://mynewdomain.com';

Souvent, il n'est même pas nécessaire de préciser cette variable du
tout - dans ce cas, laisser la vide ː

    var $live_site = '';

Often, there is no need to specify this variable at all - in which place
simply leave it blank:

    var $live_site = '';

- Référez-vous à <a
  href="http://www.scribd.com/doc/2300167/Joomla-v-15-Configure-and-troubleshoot-SEF-URLs"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">Scribd</a> de
  <a href="https://docs.joomla.org/GHOP_students/Benjamin_H%C3%A4ttasch"
  class="mw-redirect" title="GHOP students/Benjamin Hättasch">Benjamin
  Hättasch</a> qui contient des instructions étape par étape pour
  installer et déverminer vos réécritures d'URL.
