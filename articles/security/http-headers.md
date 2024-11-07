<!-- Filename: https://magazine.joomla.org/all-issues/may-2022/joomla-new-http-headers-plugin-for-j4 / Display title: En-têtes HTTP  -->

## Article de Magazine

Cet article est basé sur un article du Joomla! Community Magazine par Brendan Hedges dans l'édition de mai 2022.

Bien qu'il soit écrit pour Joomla 4, le contenu s'applique également à Joomla 5.

## Nouveau plugin d’en-têtes HTTP de Joomla pour J4

À la suite de l'article du mois dernier sur la sécurité, les mots de passe, et le plugin WebAuthn de Joomla, ce mois-ci, nous allons examiner une autre fonctionnalité de sécurité de Joomla lancée avec J4. Il s'agit du plugin d'en-têtes HTTP qui est désormais inclus dans les fonctions de base de Joomla.

L'Internet évolue constamment et Joomla reste toujours à la pointe. C'est pourquoi je le choisis comme plateforme de développement web préférée. Que votre site web soit un petit site familial ou une plateforme de commerce électronique complète avec des ventes de millions, le framework Joomla a quelque chose pour tout le monde et cherche toujours à intégrer de nouvelles technologies. Certaines sont même révolutionnaires.

>L'introduction du plugin d'en-têtes HTTP dans le noyau de Joomla 4 est un grand pas en avant pour aider à sécuriser votre site contre les attaques et les activités malveillantes.

Ce plugin de sécurité système aide les propriétaires de sites à configurer facilement les en-têtes de sécurité HTTP à partir de l'interface backend familière de Joomla, au lieu de fouiller dans le fichier htaccess ou d'autres fichiers de configuration. Ou, pire encore, votre Cpanel d'hébergement web.

Regardez comme c’est compliqué à configurer dans Cpanel et dites-moi que vous ne ferez pas d'erreur ! Et cela en supposant qu'une fois le framework installé dans Apache et les répertoires créés, vous connaissiez le format correct pour ajouter les en-têtes HTTP que vous souhaitez intégrer.

Combien de fois avez-vous essayé de mettre en œuvre une commande htaccess uniquement pour recharger votre site web et faire face à une erreur http500 ?

Le plus grand problème est que si vous ne perfectionnez pas le format de votre en-tête HTTP, vous risquez de casser votre site.

Même alors, ce qui fonctionne pour un site peut ne pas fonctionner pour un autre. Un bon exemple est mon fichier htaccess et la façon dont je configure le navigateur pour charger une version https sans www de mon site web :
```
## De www à sans www et mélange http à https
RewriteCond %{HTTPS} off [OR]
RewriteCond %{HTTP_HOST} ^www\. [NC]
RewriteRule ^ https://mywebsite.co.uk%{REQUEST_URI} [R=301,L,NE]
## Fin de www à sans www et mélange http à https
```

Cela a bien fonctionné pour mon ancien hébergeur. Mais lorsque j'ai changé d'hébergeur, cela a cessé de fonctionner. Cherchez l'erreur !

Le code htaccess que je dois maintenant utiliser pour obtenir le même résultat ressemble à ceci :
```
## De www à sans www et mélange http à https
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
RewriteRule ^(.*)$ https://%1/$1 [R=301,L]
RewriteCond %{ENV:HTTPS} !on
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
## Fin de www à sans www et mélange http à https
```

Confus, non ? Et si vous faites une seule erreur dans le formatage, BAM ! Vous avez cassé votre site web ! Eh bien, jusqu'à ce que vous corrigiez votre code.

C'est pourquoi garder les choses simples, en tant que partie intégrante de Joomla, signifie moins de frustration, moins de temps perdu à chercher vos erreurs sur Google et plus de temps pour célébrer pendant que vous vous détendez dans votre fauteuil pour admirer votre nouveau site web.

Alors, regardons ce que sont réellement les en-têtes HTTP, comment vous pouvez trouver le plugin et ce que vous pouvez en faire. Il vaut la peine de mentionner ici que cette fonction de Joomla est une fonction avancée de Joomla, qui convient mieux aux sites nécessitant des données sensibles, plutôt qu'au nouveau site que vous avez créé avec amour sur vos adorables chatons. Cependant, même les sites simples devraient être aussi sécurisés que possible pour empêcher que du code malveillant soit exécuté après que votre site ait été piraté.

## Que sont les en-têtes HTTP ?

Les en-têtes HTTP ne doivent pas être confondus avec la section &lt;head&gt; de votre document HTML. Ils sont complètement différents. Les en-têtes HTTP représentent le préambule entre votre serveur web et le navigateur. Un ensemble d'instructions qui indiquent au navigateur ce qu'il doit, ou plus important encore, ne doit pas afficher au visiteur.

Vous pouvez voir les en-têtes HTTP et la manière dont ils se rapportent à des objets HTML individuels dans les outils de développement de votre navigateur. Dans Google Chrome, ouvrez les outils de développement, puis l'onglet Réseau. Actualisez maintenant la page web et cliquez sur un élément HTML dans le volet de gauche. Cela affichera l'en-tête HTTP pour cet élément dans le volet de droite.

Vous pouvez voir dans l'image ci-dessous que l'image en surbrillance retourne un statut HTTP de 200, donc le navigateur l'a trouvée. Il y a également une gamme d'autres informations liées à cet élément, telles que la taille du fichier et les dates de modification.

![En-têtes http Joomla 1](../../../en/images/security/http-headers-dev-tools-headers.png "")

Si l'un de vos éléments HTML n'a pas pu s'afficher, vous pouvez également obtenir des indices sur la raison dans les en-têtes HTTP. Dans cet exemple, la deuxième image n'a pas pu s'afficher et l'on peut voir d'après les informations affichées dans le volet de droite qu'il n'y a pas d'informations d'en-tête HTTP.

Excepté le message cryptique :

**Politique de référent :** 'strict-origin-when-cross-origin'

'Strict-origin-when-cross-origin' signifie simplement que lorsqu'un élément HTML (une image dans ce cas) est servi depuis une source différente (pas votre serveur), la politique d'en-tête HTTP définie à ce moment-là doit être suivie. Dans cet exemple, les en-têtes HTTP, tels que définis dans le plugin Joomla, rejetteront toutes les images qui ne proviennent pas soit de ce site web, soit d'un autre site web spécifiquement 'inclus' dans les paramètres d'en-tête HTTP définis dans le plugin Joomla HTTP.

Ainsi, lorsque l'image est appelée depuis le document HTML, le navigateur la rejette et elle n'est pas chargée.

![En-têtes http Joomla 2](../../../en/images/security/http-headers-dev-tools-headers-reject.png "")

Ce qui est différent du fait de ne pas être trouvé et de retourner un message d'erreur HTTP 404 introuvable. Dans cette situation, l'image est toujours recherchée sur le serveur qui l'héberge, mais le navigateur ne l'a pas trouvée.

![En-têtes http Joomla 3](../../../en/images/security/http-headers-dev-tools-headers-not-found.png "")

## Ce que fait le plugin Joomla HTTP Headers

En plus d'indiquer au navigateur quoi afficher et de fournir des informations générales sur le document HTML, les en-têtes HTTP aident à atténuer les attaques et les vulnérabilités de sécurité que vous pourriez avoir sur votre site Joomla. C'est là que le plugin Joomla HTTP Headers entre en jeu. Il y parvient en affichant explicitement le contenu HTML en fonction de vos réglages dans le plugin Joomla HTTP Headers lui-même.

En ajoutant des en-têtes HTTP basés sur la sécurité supplémentaires à votre site Joomla avec le plugin HTTP Header, vous offrirez une couche de sécurité supplémentaire pour votre site Joomla.

Ceci est important, car par défaut, une page web HTML affichera tout son contenu à vos visiteurs, bon ou mauvais. Cela à moins qu'on ne lui dise explicitement de ne pas le faire dans les en-têtes HTTP de la page web. Le plugin permet de le faire en vous permettant de configurer les options de sécurité avancées disponibles dans la politique de sécurité du contenu pour votre site web. Le plugin peut être configuré différemment pour chaque site en fonction de vos besoins, il s'agit donc d'une arme véritablement flexible dans votre arsenal contre les hackers.

## Pourquoi ai-je besoin de ce plugin ?

Dans un monde idéal, vous n'en auriez pas besoin. Cependant, dans le monde où nous vivons, il y a bien trop de personnes peu scrupuleuses qui essaient de trouver des moyens de gagner de l'argent aux dépens des innocents et des imprudents. Dans notre monde, nous appelons ces personnes des hackers. Les hackers s'efforcent d'exploiter les vulnérabilités des logiciels pour en tirer profit, souvent au détriment du propriétaire du site web.

En utilisant le plugin HTTP Header de Joomla pour contrôler quel contenu est servi à vos visiteurs, vous réduisez les risques que les hackers puissent servir un contenu malveillant à vos visiteurs via des plugins obsolètes et vulnérables. Ce qui aide à empêcher les injections de scripts malveillants sur votre site.

**Alors, réfléchissons à cette situation hypothétique pendant une minute.**

Vous avez un joli site Joomla 3. Il a été créé il y a 5 ans et il est toujours aussi beau et fonctionnel. Tous vos composants, plugins et modules sont à jour. Parfait, n'est-ce pas ?

Eh bien, pas tout à fait, car lorsque vous avez créé votre site il y a 5 ans, vous avez installé le plugin à la mode Foo Bar pour afficher "FOO BAR" sur votre page d'accueil. Cela avait l'air cool au début, mais après un certain temps, vous avez changé d'avis et supprimé le shortcode {foo}FOO - BAR{/bar} de votre article d'accueil.

Mais, voici le problème : vous n'avez pas dépublié ou désinstallé le plugin lui-même et son utilisation a disparu de votre mémoire. **C'est quelque chose que NOUS AVONS TOUS tendance à faire, j'en suis sûr.**

Fast forward à aujourd'hui, 5 ans plus tard, ce plugin est toujours là, publié et actif sur votre site, mais il n'a pas été mis à jour depuis 5 ans parce que vous avez depuis longtemps oublié le plugin, ou l'auteur a arrêté de le supporter. Maintenant, un individu malveillant a réalisé que ce plugin présente une vulnérabilité de sécurité qui peut être exploitée pour lancer une attaque de **Cross Site Scripting (XSS)** sur votre site, et faire de vos visiteurs imprudents, des victimes.

Le cross-site scripting, également connu sous le nom de XSS, est une vulnérabilité de sécurité sur votre site web qui permet à un attaquant de compromettre les interactions de vos utilisateurs avec votre site désormais vulnérable.

L'attaquant/hacker utilise XSS pour exploiter votre site vulnérable et envoyer un script malveillant à votre utilisateur sans méfiance. Comme le script provient de votre site, le navigateur de votre utilisateur ne sait pas ou ne soupçonne pas que le script ne doit pas être fiable et exécute le script lorsque la page web se charge et s'ouvre.

Les scripts malveillants exécutés de cette manière peuvent causer de nombreux problèmes pour votre utilisateur, du vol des mots de passe et des noms d'utilisateur conservés dans les cookies, à envoyer votre utilisateur vers de faux sites de phishing. Les scripts peuvent même changer l'apparence de la page web que votre site sert et afficher de la publicité différente.

Utiliser le **plugin Headers HTTP de Joomla** aide à arrêter le cross-site scripting en s'assurant que seuls les scripts et le contenu que vous souhaitez servir à votre visiteur sont réellement servis. Tout le reste est bloqué.

Ainsi, dans l'exemple ci-dessus, vous auriez pu configurer le plugin HTTP Headers pour ne servir les fichiers JavaScript (script) de votre site qu'à partir d'un dossier spécifié, ou peut-être d'un CDN si vous en utilisez un, afin d'arrêter l'attaque.

Vous pourriez également empêcher le site d'exécuter du JavaScript en ligne intégré dans le HTML. Mais, sachez que selon la façon dont vous avez conçu le HTML de votre site, cela pourrait causer des problèmes plus tard.

Cela aiderait alors à empêcher le code JavaScript malveillant d'être exécuté sur votre site. Même si votre plugin vulnérable Foo Bar était à blâmer pour qu'un hacker puisse injecter du code malveillant sur votre site en premier lieu.

**Remarque :**

> Les points faibles courants sur les sites web qui sont sujets aux attaques XSS sont les formulaires d'entrée utilisateur (pages de connexion utilisateur, formulaires d'inscription à la newsletter, formulaires de contact, etc.) sans validation et chiffrement.

## Où se trouve le plugin HTTP Headers ?

Vous pouvez trouver le plugin HTTP Headers de Joomla avec tous les autres plugins Joomla, et il est accessible de la même manière à laquelle vous êtes habitué.

![Joomla http headers 4](../../../en/images/security/http-headers-plugins.png "")

## Utilisation du plugin HTTP Headers

Utiliser le plugin HTTP de Joomla est relativement simple, bien qu'il soit peut-être judicieux, avant de modifier les paramètres par défaut, de se familiariser avec certains des termes spéciaux liés à son utilisation. Cela dit, certains d'entre eux devraient déjà vous être familiers.

**Par exemple :**

Lorsque vous traitez des images, vous verrez le terme 'img-src', où 'img' se réfère aux images et 'src' à la source valide de l'image. Ce sont des termes que nous connaissons déjà grâce au HTML de base.

À la fin de cet article, il y a une liste de sites web utiles avec des informations supplémentaires pour vous aider à utiliser ce plugin Joomla.



## Paramètres du plugin d'en-têtes HTTP - ONGLET 2

### Strict-Transport-Security (HSTS)

**L'onglet de la politique de transport strict est désactivé par défaut.**

![Joomla http headers 12](../../../en/images/security/http-headers-plugins-headers-strict-transport-security.png "")

J'adore faire des recherches. Parce que parfois, vous tombez sur un vrai moment OMG ! C'est l'un de ces moments.

Wikipedia déclare :

> Netscape Communications a créé HTTPS en 1994 pour son navigateur Web Netscape Navigator. À l'origine, HTTPS était utilisé avec le protocole SSL. Au fur et à mesure que SSL s’est transformé en Transport Layer Security (TLS), HTTPS a été officiellement spécifié par le RFC 2818 en mai 2000. Google a annoncé en février 2018 que son navigateur Chrome marquerait les sites HTTP comme « Non sécurisé » après juillet 2018. Cette démarche visait à encourager les propriétaires de sites à mettre en place HTTPS, dans le but de rendre le World Wide Web plus sûr. » ……

Qui aurait cru que Netscape avait inventé les protocoles HTTPS il y a si longtemps ? Ce qui est encore plus surprenant, c'est le temps qu'il a fallu pour l'implémenter dans l'Internet que nous connaissons et aimons aujourd'hui.

Depuis des années, ils nous ont cajolés, intimidés, et enfin menacés, pour que nous implémentions HTTPS sur tous nos sites Web. La plupart d'entre nous ont capitulé et le web mondial est enfin sécurisé. Ou l'est-il vraiment ?

Il existe cependant quelques irréductibles, accros ou sites oubliés qui utilisent encore uniquement http pour diffuser leur contenu, bien qu'avec un avertissement « Ce site Web n'est pas sécurisé » de Google/Firefox, etc.

Une recherche rapide sur Google a révélé plusieurs listes obsolètes de ces sites coupables d’utiliser uniquement HTTP. Bien que depuis la publication de ces listes, de nombreux sites Web soient passés à HTTPS. Cependant, certains cas évidents ont été exclus d'organisations qui, selon vous, devraient savoir mieux.

Par exemple :

* NGINX (http://nginx.org/)
* GNU (http://www.gnu.org/)
* L'université de Washington (http://www.washington.edu/)

Selon w3techs.com, environ 20 % de tous les sites Web fonctionnent encore uniquement avec HTTP.

**Alors, pourquoi est-ce un problème ?**

C'est un problème car toutes les données envoyées depuis et reçues par le navigateur d'un utilisateur risquent d'être interceptées. Nous connaissons cela comme une **attaque de l'homme du milieu**. Cela peut ne pas sembler une considération importante si votre site Web concerne uniquement des photos de chats mignons.

![snapshot of cute kittens](../../../en/images/security/http-headers-plugins-headers-kittens.jpg "")

Mais même les sites Web les plus simples peuvent devenir victimes de pirates et d'attaquants qui mettront en œuvre le **click-jacking** et d'autres attaques inter-origine qui nuiront à vos utilisateurs.

Un site Web qui n'échange pas de données utilisateur ou d'informations de connexion **devrait tout de même utiliser HTTPS**.

**D'accord, revenons au sujet.**

Comme vous le savez déjà, l'objectif principal de HTTPS est d'introduire une connexion sécurisée entre le navigateur de l'utilisateur et votre serveur. Une connexion où tout échange de données se produit dans un environnement sécurisé qui ne peut pas être intercepté et copié par un tiers. Un homme du milieu.

![man in the middle attack](../../../en/images/security/http-headers-plugins-headers-man-in-middle.png "")

Mais saviez-vous qu'à moins que votre **certificat SSL HTTPS** n'utilise **TLS**, votre connexion 'sécurisée' n'est pas aussi sécurisée que vous pourriez l'espérer ? Les connexions HTTPS non-TLS sont encore **vulnérables aux attaques de l'homme du milieu**.

Bien qu'il s'agisse d'un ancien article de blog, cet article explique bien comment fonctionne une attaque de l'homme du milieu.

Les navigateurs ont largement adopté TLS.

Et TLS 1.3 n'est pas directement compatible avec les versions précédentes à moins qu'il ne soit exécuté en mode de compatibilité, ce qui pourrait poser problème à certains.

![tls certicate information](../../../en/images/security/http-headers-plugins-headers-tls.png "")

L'utilisation du plugin d'en-têtes HTTP de Joomla pour traiter Strict-Transport-Security (HSTS) aide à atténuer les attaques de l'homme du milieu en imposant l'utilisation de TLS dans le navigateur Web de vos visiteurs. TLS garantit que toutes les communications Web s'effectuent côté client à l'aide d'une couche de transport sécurisée.

**Utilisez-vous une redirection 301 pour servir la version non sécurisée HTTP de votre site Web à celle sécurisée HTTPS ?**

La plupart des gens le font. Les redirections 301 sont des instructions que la plupart des propriétaires de sites Web configurent dans leur fichier htaccess. Ils informent Google que la version du site Web qui doit être utilisée est celle HTTPS (sécurisée). Là où réside le problème est que **la 301 n'est qu'une redirection d'URL**, donc votre site Web fait toujours un élément de la connexion initiale sur HTTP.

Contrairement aux connexions entre un utilisateur et un serveur de site Web qui utilisent HSTS, où le serveur interagit automatiquement avec lui en utilisant uniquement HTTPS.

L'HSTS présente cependant une faiblesse, car la première connexion initiale entre le navigateur de l'utilisateur et le serveur du site Web se fait toujours via HTTP. Mais toutes les connexions suivantes sont automatiquement connectées via HTTPS jusqu'à ce que la date d'expiration de l'en-tête HTTP soit atteinte et que cet en-tête soit réinitialisé.

Ceci est différent d'une redirection 301 standard où chaque chargement de page comprend une demande http initiale pour initier la connexion https.

Il existe une solution à cette faiblesse dans les paramètres HSTS des en-têtes HTTP : activez 'Preload'.

Ce qui ajoutera le tag 'Preload' à l'en-tête de réponse.

Dans les paramètres, il y a aussi une liste de préchargement de liens**. C'est une liste qui est codée en dur dans de nombreux navigateurs modernes. La liste informe le navigateur que la connexion à example.com ne doit être effectuée que via HTTPS. Éliminant ainsi le besoin de faire même la connexion initiale via HTTP.

![hsts preload](../../../en/images/security/http-headers-plugins-headers-enter-domain.png "")

Une fois HSTS configuré dans le plugin d'en-têtes HTTP de Joomla, toutes les balises nécessaires sont ajoutées à l'en-tête de réponse HTTP. Cela informe tout navigateur d’utilisateur essayant de se connecter à votre serveur que toutes les connexions **doivent être faites avec HTTPS**, qu'elles soient spécifiées dans votre HTML, ou non.

En résumé, utiliser le plugin d'en-têtes HTTP de Joomla pour intégrer HSTS au lieu de s'appuyer sur des redirections 301 pour diffuser votre contenu via HTTPS est une amélioration importante de la sécurité. Une amélioration qui aide à arrêter **les attaques de l'homme du milieu**, et fournit à votre utilisateur un environnement sécurisé.

HSTS couvre l'ensemble du domaine, contrairement à une redirection 301 qui ne couvre qu'un chemin URI spécifique.

HSTS utilise un cache de navigateur distinct qui est généralement isolé, il ne peut donc pas être facilement ou accidentellement vidé.

HSTS peut être préchargé dans un navigateur. Cela garantit qu'un utilisateur ne se connecte à votre serveur qu'avec HTTPS, que ce soit la première fois qu'il visite le site ou non.

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
À Retenir

Activer : HSTS

Définir max-age : La valeur par défaut est de 1 an (31 536 000) secondes, mais certains recommandent de la définir à 2 ans (63 072 000) secondes.

Activer : Sous-domaines - Si vous avez des sous-domaines, assurez-vous d’avoir un certificat SSL valide pour les couvrir individuellement ou comme un générique à partir de votre domaine principal.

Activer : Preload

Enfin, soumettez votre domaine à la liste de préchargement HSTS.
</div>

## Paramètres du plugin HTTP Headers - ONGLET 3

### Politique de sécurité du contenu (Onglet 3)

**L'onglet Politique de Sécurité du Contenu est désactivé par défaut.**

Lorsque vous activez la Politique de Sécurité du Contenu de Joomla via le plugin HTTP Headers, vous informez le navigateur de votre visiteur exactement quels éléments charger depuis le serveur de votre site web. C'est un excellent moyen de s'assurer que vous ne délivrez que le contenu que vous souhaitez réellement diffuser.

![onglet politique de sécurité du contenu](../../../en/images/security/http-headers-plugins-headers-csp.png "")

Avoir une Politique de Sécurité du Contenu efficace est un moyen efficace pour stopper les attaques par **Cross-Site Scripting (XSS)** et **Click Jacking** provenant de votre site web.

Le Cross-Site Scripting, autrement connu comme une attaque **XSS**, est une attaque sur votre site web où un script malveillant est 'injecté' dans un site web inconscient et autrement de confiance. Les attaquants trouvent un point faible à exploiter, qui est généralement là où un utilisateur peut entrer des données.

Les composants obsolètes qui permettent l'entrée de l'utilisateur, les formulaires de commentaires non validés, par exemple, pourraient avoir des vulnérabilités pouvant être exploitées lors d'une attaque de type Cross Site Scripting. C'est pourquoi il est judicieux de toujours mettre à jour vos composants Joomla et de réduire ces opportunités.

**Donc, utiliser le formulaire de commentaires infecté comme exemple :**

Votre site web utilise un formulaire de commentaires à la fin d'un article pour recueillir les discussions des utilisateurs, comme le font de nombreux sites web. Ce qui est formidable.

Votre extension de commentaires de dodgy-joomla-extensions.com fonctionne très bien et vos utilisateurs l'adorent. Mais vous ne l'avez pas mis à jour depuis 5 ans et les développeurs l'ont abandonné depuis longtemps.

Maintenant, 5 ans plus tard, M. Hacker réalise qu'en raison d'une vulnérabilité dans le code du composant de commentaires, il peut cacher un mauvais morceau de code dans un commentaire qui semble autrement innocent.

Ce que ce code fait finalement varie, mais ce dont vous pouvez être sûr, c'est qu'à chaque fois que votre page d'article innocent se charge, avec les commentaires, ce mauvais code est également chargé et exécuté. Après tout, il fait partie du HTML, et le navigateur ne sait pas qu'il n'est pas censé être là ou de confiance.

Ainsi, le mauvais code s'exécute. Peut-être qu'il vérifie vos cookies. Peut-être qu'il vole des données sensibles conservées par le navigateur. Ou, peut-être qu'il charge des publicités de casinos en ligne, ou de sites pour adultes. Peut-être qu'il recharge complètement le HTML de votre page web innocente concernant ces adorables chatons depuis un fichier JavaScript externe pour voler les détails de carte de crédit de vos utilisateurs.

**En fait, à ce stade, un script peut être exécuté pour accomplir presque n'importe quoi.**

Une bonne Politique de Sécurité du Contenu aide à arrêter ce genre d'attaque, même si votre extension de commentaires compromise devient la cible de M. Hacker.

Elle le fait parce que le plugin Joomla HTTP Header délivre la CSP comme un en-tête de réponse HTTP, **qui dit explicitement au navigateur quoi charger**. Dans les paramètres de l'onglet CSP dans le plugin des en-têtes HTTP, vous pouvez cibler directement **28 directives politiques**. Les directives aident à sécuriser votre site web en utilisant uniquement des sources approuvées pour vos fichiers et contenus.

L'exemple d'attaque mentionné ci-dessus a fini par charger un fichier JavaScript provenant d'une source différente pour modifier la sortie HTML rendue à l'écran. Cela aurait pu être empêché en ajoutant la directive script-src 'self' à la CSP de Joomla dans le plugin.

![directive politique self](../../../en/images/security/http-headers-plugins-headers-policy-directive.png "")

Dans cet exemple, le navigateur ne chargera que les fichiers JavaScript dans le document HTML s'ils proviennent de votre domaine. Tous les autres fichiers JavaScript seront rejetés, y compris ceux de M. Hacker.

Bien que cela aide à sécuriser votre site web, cela peut aussi arrêter d'autres fichiers JavaScript légitimes que vous souhaitez charger lors de l'affichage de la page web. Ces fichiers externes peuvent être ajoutés en tant que sources autorisées dans la même directive. Par exemple, si vous utilisez bootstrap depuis un CDN, vous ajouteriez :
```
script-src 'self' https://cdn.jsdelivr.net
```
Dans cet exemple, si vous avez du mal à charger bootstrap depuis le CDN, https://cdn.jsdelivr.net, vous pourriez essayer d'ajouter l'URL complète au fichier bootstrap dont vous avez besoin. Vous formateriez donc votre directive ainsi : `script-src 'self' https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.min.js`.

![directive politique self](../../../en/images/security/http-headers-plugins-headers-policy-directive-self.png "")

Ajouter ces sources externes serait plus facile à mettre en œuvre sur un nouveau site web lorsque vous le construisez. Mais si vous parcourez votre HTML rendu avec les outils de développement, vous devriez pouvoir trouver tous les fichiers externes déjà utilisés sur votre site établi et les inclure dans votre CSP.

Lorsque vous ajoutez des directives à votre Politique de Sécurité du Contenu dans le Plugin des En-têtes HTTP, il existe une **série de valeurs de base** que vous pouvez utiliser pour définir ce qui doit être explicitement chargé par le navigateur. Voici les valeurs de base pour configurer votre première Politique de Sécurité du Contenu.

D'autres options sont disponibles pour certaines des directives plus avancées, une liste complète et des exemples de leur utilisation peuvent être trouvés sur le site Web du Guide de Référence Rapide de la Politique de Sécurité du Contenu (CSP).

* **'none'** bloque l'utilisation de ce type de ressource.
* **'self'** correspond à l'origine actuelle (mais pas aux sous-domaines).
* **'unsafe-inline'** permet l'utilisation de JS et CSS en ligne.
* **'unsafe-eval'** permet l'utilisation de mécanismes comme eval().

Voyons donc certaines de ces directives. Voici une liste de certaines des directives qui sont disponibles dans le plugin des en-têtes HTTP de Joomla, avec une brève description, grâce à la Politique de Sécurité du Contenu. Je vous recommande de visiter ce site pour plus d'informations et des exemples.

<dl>
<dt>default-src</dt>
<dd>La directive default-src définit la politique par défaut pour récupérer des ressources telles que JavaScript, Images, CSS, Polices, Requêtes AJAX, Cadres, Média HTML5.<br>
EXEMPLE DE POLITIQUE DEFAULT-SRC<br>
default-src 'self' https://cdn.example.com
</dd>
<dt>script-src</dt>
<dd>Définit des sources valides de JavaScript.<br>
EXEMPLE DE POLITIQUE SCRIPT-SRC<br>
script-src 'self' https://js.example.com
</dd>
<dt>style-src</dt>
<dd>Définit des sources valides de feuilles de style ou CSS.<br>
EXEMPLE DE POLITIQUE STYLE-SRC<br>
style-src 'self' css.example.com
</dd>
<dt>img-src</dt>
<dd>Définit des sources valides d'images.<br>
EXEMPLE DE POLITIQUE IMG-SRC<br>
img-src 'self' https://img.example.com https://example.com
</dd>
<dt>connect-src</dt>
<dd>S'applique à XMLHttpRequest (AJAX), WebSocket, fetch(), &lt;a ping&gt; ou EventSource. Si non autorisé, le navigateur simule un code de statut HTTP 400.<br>
EXEMPLE DE POLITIQUE CONNECT-SRC<br>
connect-src 'self'
</dd>
<dt>font-src</dt>
<dd>Définit des sources valides de ressources de polices (chargées via @font-face).<br>
EXEMPLE DE POLITIQUE FONT-SRC<br>
font-src https://font.example.com https://example.com
</dd>
<dt>object-src</dt>
<dd>Définit des sources valides de plugins, par exemple &lt;object&gt;, &lt;embed&gt; ou &lt;applet&gt;.<br>
EXEMPLE DE POLITIQUE OBJECT-SRC<br>
object-src 'self'
</dd>
<dt>media-src</dt>
<dd>Définit des sources valides pour l'audio et la vidéo, par exemple les éléments HTML5 &lt;audio&gt;, &lt;video&gt;.<br>
EXEMPLE DE POLITIQUE MEDIA-SRC<br>
media-src https://media.example.com
</dd>
<dt>frame-src</dt>
<dd>Définit des sources valides pour le chargement des cadres. Dans le CSP Niveau 2 frame-src a été déprécié au profit de la directive child-src. Le CSP Niveau 3 a retiré la dépréciation de frame-src et continuera à se référer à child-src si celle-ci n'est pas présente.<br>
EXEMPLE DE POLITIQUE FRAME-SRC<br>
frame-src 'self'
</dd>
<dt>sandbox</dt>
<dd>Active un bac à sable pour la ressource demandée similaire à l'attribut sandbox des iframe. Le bac à sable applique une politique de même origine, empêche les pop-ups, les plugins et l'exécution de scripts est bloquée. Vous pouvez garder la valeur du bac à sable vide pour garder toutes les restrictions en place, ou ajouter des valeurs : allow-forms allow-same-origin allow-scripts allow-pop-ups, allow-modals, allow-orientation-lock, allow-pointer-lock, allow-presentation, allow-popups-to-escape-sandbox, et allow-top-navigation.<br>
EXEMPLE DE POLITIQUE SANDBOX<br>
sandbox allow-forms allow-scripts
</dd>
<dt>report-uri</dt>
<dd>Instructs the browser to POST reports of policy failures to this URI. Utilisez également Content-Security-Policy-Report-Only comme nom d'en-tête HTTP pour demander au navigateur de n'envoyer que des rapports (ne bloque rien). Cette directive est dépréciée dans le CSP Niveau 3 au profit de la directive report-to.<br>
EXEMPLE DE REPORT-URI<br>
report-uri /some-report-uri
</dd>
<dt>child-src</dt>
<dd>Définit des sources valides pour les travailleurs web et les contextes de navigation imbriqués chargés à l'aide d'éléments tels que &lt;frame&gt; et &lt;iframe&gt;<br>
EXEMPLE DE POLITIQUE CHILD-SRC<br>
child-src 'self'
</dd>
<dt>form-action</dt>
<dd>Définit les sources valides pouvant être utilisées comme action HTML &lt;form&gt;.<br>
EXEMPLE DE POLITIQUE FORM-ACTION<br>
form-action 'self'
</dd>
<dt>frame-ancestors</dt>
<dd>Définit des sources valides pour intégrer la ressource en utilisant &lt;frame&gt; &lt;iframe&gt; &lt;object&gt; &lt;embed&gt; &lt;applet&gt;. Définir cette directive à 'none' devrait être équivalent à X-Frame-Options: DENY. Lorsque cette directive est active, et si le navigateur la prend en charge, elle remplacera les paramètres dans X-frame-options.<br>
EXEMPLE DE POLITIQUE FRAME-ANCESTORS<br>
frame-ancestors 'none'
</dd>
<dt>plugin-types</dt>
<dd>Définit des types MIME valides pour les plugins invoqués via &lt;object&gt; et &lt;embed&gt;. Pour charger une &lt;applet&gt;, vous devez spécifier application/x-java-applet.<br>
EXEMPLE DE POLITIQUE PLUGIN-TYPES<br>
plugin-types application/pdf
</dd>
<dt>base-uri</dt>
<dd>Définit un ensemble d'URL autorisées pouvant être utilisées dans l'attribut src d'une balise HTML base.<br>
EXEMPLE DE POLITIQUE BASE-URI<br>
base-uri 'self'
</dd>
<dt>report-to</dt>
<dd>Définit un nom de groupe de rapport défini par un en-tête de réponse HTTP Report-To. Voir l'API de Reporting pour plus d'informations.<br>
EXEMPLE DE DIRECTIVE REPORT-TO<br>
report-to groupName
</dd>
<dt>worker-src</dt>
<dd>Restreint les URLs qui peuvent être chargées en tant que Worker, Shared Worker ou Service Worker.<br>
EXEMPLE DE POLITIQUE WORKER-SRC<br>
worker-src 'none'
</dd>
<dt>manifest-src</dt>
<dd>Restreint les URLs que les manifests d'application peuvent être chargés.<br>
EXEMPLE DE POLITIQUE MANIFEST-SRC<br>
manifest-src 'none'
</dd>
<dt>prefetch-src</dt>
<dd>Définit des sources valides pour la prélecture et le préchargement des requêtes, par exemple via la balise link avec rel="prefetch" ou rel="prerender" :<br>
EXEMPLE DE POLITIQUE PREFETCH-SRC<br>
prefetch-src 'none'
</dd>
<dt>navigate-to</dt>
<dd>Restreint les URLs vers lesquelles le document peut naviguer par quelque moyen que ce soit. Par exemple, lorsqu'un lien est cliqué, un formulaire est soumis ou que window.location est invoqué. Si l'action de formulaire est présente, cette directive est ignorée pour les soumissions de formulaire. Statut de l'implémentation<br>
EXEMPLE DE POLITIQUE NAVIGATE-TO<br>
navigate-to https://example.com
</dd>
</dl>

Le plugin des en-têtes HTTP de Joomla vous offre également l'opportunité de **définir certains paramètres globaux dans l'onglet Politique de Sécurité du Contenu**.

![Joomla http headers 14](../../../en/images/security/http-headers-plugins-headers-csp-global.png "")

Vous pouvez choisir d'appliquer la CSP à votre site web, au site administrateur, ou aux deux avec le paramètre client.

L'option ‘Report-Only’ vous permet de tester vos directives et de les vérifier pour des erreurs avec les outils de développement avant la mise en production. C'est toujours amusant de retracer la raison des erreurs CSP dans la console de Google !

Ensuite, il y a le paramètre ‘Nonce’. Nonce, signifiant ‘nombre utilisé une fois’, est un système qui applique une chaîne générée aléatoirement à une balise &lt;script&gt; ou &lt;style&gt; incluse en ligne dans votre HTML via l'API Joomla. Ces instances sont généralement mises en œuvre par des développeurs tiers de composants / modules / plugins Joomla lorsque vous installez cette fonctionnalité supplémentaire sur votre site.

Dans l'image ci-dessous, vous pouvez voir la balise &lt;style&gt; avec un attribut nonce rel qui a été ajouté aux &lt;styles&gt; CSS ajoutés à mon document HTML par le composant Akeeba Backup.

![Joomla http headers 16](../../../en/images/security/http-headers-plugins-headers-akeeba-style.png "")

Il est intéressant de noter que le code JavaScript et CSS central de Joomla qui est ajouté au document HTML n'inclut pas actuellement de balise ‘nonce’. C'est parce qu'ils font **partie du ‘noyau’** plutôt que d'être ajoutés via l'API Joomla.

Si vous activez l’option ‘Nonce’ dans les paramètres de la CSP, vous permettez à ces scripts et styles en ligne d'être rendus par le navigateur comme ‘sûrs’. Vous devrez également définir la balise Joomla {nonce} dans votre directive de politique script-src à script-src 'self' {nonce}. En tant que solution de secours pour les anciens navigateurs qui ne prennent pas en charge les 'nonces', vous pouvez également ajouter {script-hashes} après l'espace réservé {nonce}, comme ceci script-src 'self' {nonce} {script-hashes} (faites attention à l'espacement). Mais, n'oubliez pas d'activer d'abord les **Hashs de Script**.

![Paramètres nonce de Joomla](../../../en/images/security/http-headers-plugins-headers-nonce-settings.png "")

Joomla génère aléatoirement la chaîne de texte ‘nonce’ et l'ajoute aux balises &lt;style&gt; et &lt;script&gt;. Lorsque vous activez l'option ‘nonce’ dans les paramètres du plugin, la chaîne de texte est transmise à l'en-tête HTTP. Le navigateur interprète alors l'en-tête HTTP et traite le &lt;script&gt; ou &lt;style&gt; correspondant. En même temps, il enlève la chaîne de texte Nonce du HTML rendu dans le navigateur.

![Style nonce de Joomla](../../../en/images/security/http-headers-plugins-headers-nonce-style.png "")

Cela, à son tour, empêche M. Hacker de pouvoir détourner la chaîne de texte nonce et de l'ajouter à son propre code injecté. Même si M. Hacker réussit à injecter son JavaScript néfaste dans votre HTML, le navigateur le bloquera.

### Hashs de Script

Nous savons tous que nous ne devrions pas inclure de JavaScript en ligne dans notre HTML, vous devriez l'écrire dans un fichier my-javascript.js et l'ajouter à la balise &lt;head&gt; ou le placer juste avant la balise &lt;/body&gt;. Mais nous sommes tous coupables de le faire de temps en temps.

Le problème, c'est que si vous faites cela, puis que vous ajoutez la directive CSP ‘script-src 'self'’, tout le JavaScript en ligne sera bloqué par défaut. Il est conçu pour fonctionner ainsi pour empêcher le JavaScript injecté de M. Hacker de pouvoir s'exécuter sur votre site web.

Il existe une dérogation pour cela avec la directive script-src 'unsafe-inline', qui permettra au JavaScript en ligne de M. Hacker de s'exécuter, ainsi qu'à votre code de confiance. Ce n'est pas la meilleure option, pour des raisons évidentes.

**Les Hashs de Script à la rescousse !**

Le plugin des en-têtes HTTP de Joomla collecte automatiquement tous les &lt;styles&gt; et &lt;scripts&gt; **passés via l'API Joomla** dans le site. Il génère ensuite les hashs respectifs et les transmet via l'en-tête HTTP. Le navigateur génère alors les hashs sur le site lui-même et confirme que les hashs correspondent. Si c'est le cas, les scripts sont exécutés, sinon ils sont bloqués.

Pour activer cette fonctionnalité du plugin, basculez le commutateur sur **'Activé'**. Ensuite, dans votre directive de politique script-src, ajoutez la valeur 'self' {script-hashes}. Si vous utilisez la fonctionnalité 'nonce', ainsi que les 'hashs de script', réglez la valeur de la directive comme dans l'exemple du nonce ci-dessus.

![Hashs de script Joomla](../../../en/images/security/http-headers-plugins-headers-csp-script-hashes.png "")

**Maintenant, c'est intelligent.**

Mais ce qui est encore mieux, c'est que nous pouvons utiliser la même idée pour traiter les hashs de script manuellement et les ajouter à notre directive script-src 'self'. Cela demandera un peu de travail pour être mis en place et maintenu mais pourrait vous sauver la mise si vous avez ajouté du JavaScript à un article ou un module personnalisé.

Il existe des moyens plus détaillés de le faire en utilisant un générateur de hash sha256, sha384 ou sha512. Mais comme la plupart des gens ne feront qu'ajouter de petits extraits de JavaScript à leur article ou module personnalisé, nous laisserons les outils de développement de Google faire le travail pour nous.

Le processus est simple. La seule différence est la manière dont nous générons le hash.

En supposant que vous avez activé le plugin des en-têtes HTTP de Joomla, la CSP est active et vous avez défini la directive script-src 'self' et vous l'avez enregistrée.

Étape 1 - Ajoutez votre JavaScript en ligne à votre article ou module personnalisé et enregistrez-le. N'oubliez pas de régler les paramètres de votre éditeur pour empêcher l'éditeur de retirer votre code lors de l'enregistrement.

Étape 2 - Accédez à votre page web avec votre script. Ouvrez les outils de développement et dans l'onglet console, vous verrez une erreur qui ressemble à :

Refus d'exécuter le script en ligne car il enfreint la directive suivante de Politique de Sécurité du Contenu : "script-src 'self'". Soit le mot-clé 'unsafe-inline', un hash ('sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='), soit un nonce ('nonce-...') est nécessaire pour permettre l'exécution en ligne.

![Erreur outils de développement sur les hashs de script Joomla](../../../en/images/security/http-headers-plugins-headers-csp-script-hashes-tools-error.png "")

Étape 3 - Maintenant, il vous suffit de copier/coller le hash du message d'erreur dans votre directive JavaScript dans le plugin et de le sauvegarder à nouveau :

script-src 'self' 'sha256-0Q1c1CuhLHV7WbNt+ltwJoCf3wF/O+MWqsXetkxWSm0='

![Script hash Joomla renommé](../../../en/images/security/http-headers-plugins-headers-csp-script-src-self-hash.png "")

Ensuite, rechargez votre page web et vérifiez à nouveau dans les outils de développement de Google. L'erreur aura maintenant disparu et le navigateur chargera votre script sur la page web.

**Note :** Il y a toujours une erreur affichée dans mon exemple car le JavaScript ajouté à mon article n'est pas complet. Mais, cela montre que le code en ligne essaie au moins de fonctionner.

Ajouter des hashs à votre code en ligne est un bon moyen de les autoriser explicitement dans l'en-tête HTTP afin qu'ils soient toujours exécutés, tandis que tout code en ligne qui n'est pas explicitement hashé et ajouté à votre CSP sera toujours bloqué. Ainsi, contrecarrant la tentative de M. Hacker de compromettre votre site web.

![Erreur outils de développement sur les hashs d'un script de Joomla sur un hash explicite manquant en ligne](../../../en/images/security/http-headers-plugins-headers-csp-script-src-self-hash-tools-error.png "")

**Note :**

Si vous modifiez votre JavaScript, vous devrez recalculer votre hash et modifier la valeur dans la directive CSP.

Si vous avez des problèmes pour que vos hashs fonctionnent, il y a 3 problèmes communs :
vous pouvez trouver des solutions sur la page Web Utiliser un hash avec CSP.

Strict Dynamic

Si vous activez l'option Strict Dynamic dans votre CSP, cela prendra l'autorité explicite que vous avez donnée à un script via un Hash, ou un Nonce, et l'appliquera à tout autre script directement lié à celui-ci, ou appelé depuis celui-ci. Cette action remplace également les directives par défaut comme 'self' ou 'unsafe-inline' appliquées dans vos directives CSP générales à ces scripts enfants. Elles seront ignorées.

Hashs de style

Le Hash de Style de la CSP fonctionne exactement de la même manière que les hashs de JavaScript ci-dessus, mais utilisez ceci si vous ajoutez des blocs &lt;style&gt; de CSS dans le corps de votre HTML. Tout comme l'utilisation des 'Hashs de Script', **activez** la fonctionnalité du plugin et définissez une Directive de Politique style-src pour y faire référence avec la valeur 'self' {style-hashes}.

![Hashs de style Joomla](../../../en/images/security/http-headers-plugins-headers-csp-style-hash.png "")

**Note :**

Si vous modifiez votre CSS en ligne, plutôt que celui créé par l'API Joomla, vous devrez recalculer votre hash et modifier la valeur dans la directive CSP.

Frame Ancestors ‘self’

Cette option dans le plugin permet à une page d'être encadrée, par exemple, dans une iframe, mais seulement à partir du même site.

Si vous souhaitez autoriser explicitement un autre site web à encadrer votre contenu, vous pouvez configurer une directive spécifique 'frame-src'.

![Joomla style hashes frame src](../../../en/images/security/http-headers-plugins-headers-csp-style-hash-frame-src.png "")

<div style="background-color: #eeffee; border: 1px solid #009900; padding: 1rem; ">
À retenir

Parfois, une bonne CSP est plus facile à construire sur un nouveau site web car vous développez avec les ressources externes nécessaires.

Il est important d'utiliser l'URL de base complète et correcte pour le domaine autorisé dans la Directive CSP. Par exemple : https://www.monwebsite.co.uk, ou https://www.unautresite.com

Il est également possible de cibler les sous-domaines avec la même CSP en utilisant des caractères génériques. Par exemple : https://*.example.org.

Tous les navigateurs ne prennent pas en charge toutes les directives.

CSP prend en charge les Hashs sha256, sha384 et sha512
</div>

## Remarque Finale / Conclusion :

En rédigeant cet article, j’ai pris conscience que je n’ai fait qu’effleurer la surface de ce vaste sujet.

J’adore découvrir des sujets que j’avais auparavant ignorés ou dont je n'avais pas connaissance. Êtes-vous pareil ?

La conclusion à laquelle je suis parvenu en recherchant le sujet des En-têtes HTTP, et en particulier l'utilisation du nouveau plugin J4 de Joomla pour les définir, est que nous devons tous maîtriser ce sujet. Il y a beaucoup trop de personnes (hackers) qui n’attendent qu’une occasion pour exploiter des sites web à la sécurité faible. Ne contribuez donc pas à ce que vos utilisateurs deviennent des victimes.

Amusez-vous à explorer le plugin Joomla HTTP Headers et apprenez comment il peut aider à sécuriser votre site web.

Je vous recommande de faire d'autres recherches sur ce sujet intéressant avant de commencer, cependant. Vous trouverez ci-dessous des liens pour débuter vos propres recherches. Vous aurez une bien meilleure compréhension de la manière dont fonctionne Internet et de comment votre site web interagit avec celui-ci.

### Pour Référence

Si vous devez réinitialiser le plugin, le plugin HTTP Headers a été installé avec les options suivantes définies :

Le plugin est activé par défaut.

* Les onglets HSTS et CSP sont désactivés par défaut.
* Les options X-Frame sont activées par défaut.
* La politique du référent est initialement définie sur : strict-origin-when-cross-origin.
* La politique de l'ouvreur d'origine croisée est initialement définie sur same-origin.

Si vous avez lu jusqu'ici et pensez "Ce n’est pas juste, et pour J3 alors ?", "Pourquoi ne pouvons-nous pas avoir les mêmes fonctionnalités dans Joomla 3 ?". Eh bien, la bonne nouvelle, c'est que vous le pouvez. Bien que vous deviez télécharger le plugin depuis le [JED].

Lorsque vous avez configuré vos en-têtes HTTP avec le plugin Joomla 4, vous pouvez tester vos en-têtes HTTP sur le site web Security Headers.

Quel a été votre score ?

Soyez conscient que l'activation du plugin HTTP Headers peut avoir des actions inattendues sur l'interface utilisateur.

Enfin, j’aimerais remercier Tobias Zulauf & Ced Keiflin pour leur contribution à la finalisation de cet article à temps !

<!--

### Lectures Supplémentaires :

Voici quelques-unes des pages web que j’ai utilisées pour rechercher cet article, elles regorgent d’informations utiles sur ce sujet.

* https://docs.joomla.org/J4.x:Http_Header_Management
* https://csp.withgoogle.com/docs/index.html
* https://content-security-policy.com/
* https://scotthelme.co.uk/content-security-policy-an-introduction/
* https://scotthelme.co.uk/csp-cheat-sheet/
* https://support.cpanel.net/hc/en-us/articles/1500001533562-How-to-add-nosniif-CORS-HSTS-Clickjack-and-X-Xss-Protection-headers-on-a-per-domain-basis
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy
* https://developer.mozilla.org/en-US/docs/Web/Security/Referer_header:_privacy_and_security_concerns
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cross-Origin-Opener-Policy
* https://web.dev/why-coop-coep/
* https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer
* https://developer.mozilla.org/en-US/docs/Web/API/Performance/now
* https://www.troyhunt.com/clickjack-attack-hidden-threat-right-in/
* https://scotthelme.co.uk/hsts-the-missing-link-in-tls/
* https://scotthelme.co.uk/wifi-pineapple-karma-sslstrip/
* https://help.upguard.com/en/articles/4581202-what-s-the-difference-between-using-hsts-and-doing-a-301-redirect
* https://content-security-policy.com/hash/
* https://content-security-policy.com/frame-ancestors/
* https://content-security-policy.com/nonce/

Icônes d'ordinateur créées par Freepik - Flaticon

Icônes de serveur créées par Freepik - Flaticon

Traduction allemande de cet article : https://www.jug-zueri.ch/artikel/das-http-headers-plugin-in-joomla-4

Traduction en russe de cet article, première partie : https://habr.com/ru/articles/697214/

Traduction en russe de cet article, deuxième partie : https://habr.com/ru/articles/704778/
-->

*Traduit par openai.com* 

