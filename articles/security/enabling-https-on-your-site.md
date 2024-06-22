<!-- Filename: Enabling_HTTPS_on_your_site / Display title: Activer HTTPS sur votre site -->

<table class="navbox" data-cellspacing="0">

<tbody>
<tr class="odd">
<td><table class="nowraplinks navbox-inner" data-cellspacing="0">

<tbody>
<tr class="header">
<th colspan="2" class="navbox-title" scope="col">Security Checklist <img
src="https://docs.joomla.org/images/7/7b/Compat_icon_CMS.png"
decoding="async" data-file-width="87" data-file-height="17" width="87"
height="17" alt="Joomla CMS" /></th>
</tr>
&#10;<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-abovebelow"></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-list navbox-odd"><table
class="nowraplinks navbox-subgroup" data-cellspacing="0">

<tbody>
<tr class="header">
<th colspan="2" class="navbox-title" scope="col"><em>Articles in this
series</em></th>
</tr>
&#10;<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td colspan="2" class="navbox-list navbox-odd"><ul>
<li><a href="https://docs.joomla.org/Security_Checklist/Getting_Started"
title="Special:MyLanguage/Security Checklist/Getting Started">Getting
Started</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Hosting_and_Server_Setup"
title="Special:MyLanguage/Security Checklist/Hosting and Server Setup">Hosting
and Server Setup</a></li>
<li><a href="https://docs.joomla.org/Enabling_HTTPS_on_your_site"
title="Special:MyLanguage/Enabling HTTPS on your site">Enabling HTTPS on
your site</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Where_can_you_learn_more_about_file_permissions%3F"
title="Special:MyLanguage/Security Checklist/Where can you learn more about file permissions?">Learn
about file permissions</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/Testing_and_Development"
title="Special:MyLanguage/Security Checklist/Testing and Development">Testing
and Development</a></li>
<li><a href="https://docs.joomla.org/Security_Checklist/Joomla!_Setup"
title="Special:MyLanguage/Security Checklist/Joomla! Setup">Joomla!
Setup</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklisthttps://docs.joomla.org/Security%20Checklist/Site%20Administration">Site
Administration</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklisthttps://docs.joomla.org/Security%20Checklist/Site%20Recovery">Site
Recovery</a></li>
<li><a
href="https://docs.joomla.org/Security_Checklist/You_have_been_hacked_or_defaced"
title="Special:MyLanguage/Security Checklist/You have been hacked or defaced">You
have been hacked or defaced</a></li>
</ul></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table></td>
</tr>
</tbody>
</table>

## Qu'est-ce que SSL/TLS ?

Transport Layer Security (TLS) est le successeur de Secure Sockets Layer
(SSL), même si la plupart des gens y font encore référence dans les
articles de blog. Avez-vous déjà remarqué le cadenas à côté de l'URL
lorsque vous naviguez sur Internet ? Cela signifie que toutes les
données que vous envoyez à ce site web sont cryptées, de sorte que toute
personne ayant piraté votre réseau (ou autre) et pouvant intercepter vos
requêtes ne peut pas voir les données - elle ne peut voir que les URL
auxquelles vous accédez.

## Pourquoi utiliser TLS ?

Google (et la plupart des autres moteurs de recherche) traite désormais
les sites utilisant https avec
préférence<sup>[\[1\]](#cite_note-1)</sup>. En outre, de nombreux
navigateurs signalent tout site Web comportant un formulaire (tel qu'un
formulaire de connexion ou de contact) qui n'utilise pas
https<sup>[\[2\]](#cite_note-2)</sup>.

## Comment configurer TLS ?

Pour configurer le certificat, le plus simple est de demander à votre
hébergeur de le faire pour vous.

Le bon certificat à acheter dépend des protections de sécurité requises
pour votre site Web. Si vous ne le savez pas, l'option la moins chère et
la plus simple est probablement d'utiliser
<a href="https://letsencrypt.org/" class="external text" target="_blank"
rel="nofollow noreferrer noopener">Let's Encrypt</a> - c'est gratuit et,
selon votre hébergeur, peut souvent être configuré directement à partir
de votre tableau de bord d'hébergement cpanel ou plesk.

Si vous avez acheté une IP dédiée et un certificat SSL, il vous suffit
de demander l'aide de votre hébergeur, qui se chargera de le faire
signer et de l'installer au bon endroit pour vous.

## Comment rediriger tout mon trafic vers https

### Dans Joomla

Le moyen le plus simple de faire respecter le trafic https est de le
faire dans Joomla. Dans la configuration globale, il y a une option
"Force HTTPS" qui vous permet de forcer HTTPS soit dans la zone de
l'administrateur uniquement, soit pour l'ensemble du site. Vous voudrez
presque toujours utiliser cette dernière option.

<img
src="https://docs.joomla.org/images/thumb/6/6d/Enable_HTTPS_In_Global_Config-en.png/800px-Enable_HTTPS_In_Global_Config-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/6/6d/Enable_HTTPS_In_Global_Config-en.png/1200px-Enable_HTTPS_In_Global_Config-en.png 1.5x, https://docs.joomla.org/images/6/6d/Enable_HTTPS_In_Global_Config-en.png 2x"
data-file-width="1512" data-file-height="1012" width="800" height="535"
alt="Image Showing the Force HTTPS option in the Joomla 3.x default backend template" />

### Dans .htaccess

    RewriteEngine on
    RewriteCond %{SERVER_PORT} !^443$
    RewriteRule .* https://%{HTTP_HOST}%{REQUEST_URI} [QSA,R=301,L]

    Redirect permanent / https://www.yourdomainname.com

#### Exemples de .htaccess plus complexes

Par exemple, pour passer de HTTP à HTTPS sur toute page dont l'URL
contient "abc/def" ou "ghi", ajoutez quelque chose comme ceci :

Code :

    RewriteCond %{HTTPS} off
    RewriteRule ^(abc/def|ghi)(.*)/?$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,NC,L]

... et pour repasser de HTTPS à HTTP sur toute page dont l'URL contient
"home" ou "help", faites quelque chose comme ceci :

Code :

    RewriteCond %{HTTPS} on
    RewriteRule ^(home|help)(.*)/?$ http://%{HTTP_HOST}%{REQUEST_URI} [R=301,NC,L]

Si vous voulez forcer le SSL sur un dossier spécifique, vous pouvez
insérer le code ci-dessous dans un fichier .htaccess placé dans ce
dossier spécifique :

Code :

    RewriteEngine On 
    RewriteCond %{REQUEST_URI} folder 
    RewriteRule ^(.*)$ https://www.example.com/folder/$1 [R,L]

Veillez à remplacer la référence du dossier par le nom du dossier réel.
Veillez ensuite à remplacer www.example.com/folder par le nom de votre
domaine et le dossier sur lequel vous souhaitez forcer le SSL.

1.  <span id="cite_note-1">[↑](#cite_ref-1) <a
    href="https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html"
    class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html</a></span>
2.  <span id="cite_note-2">[↑](#cite_ref-2) <a
    href="https://www.blog.google/products/chrome/milestone-chrome-security-marking-http-not-secure/"
    class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://www.blog.google/products/chrome/milestone-chrome-security-marking-http-not-secure/</a></span>
