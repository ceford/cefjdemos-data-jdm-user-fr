<!--
{
    "source": "https://docs.joomla.org/WebAuthn_Passwordless_Login",
    "title": "Connexion par cl\u00e9 d\u2019acc\u00e8s",
    "description": " ",
    "author": ""
}
-->

## Introduction

La connexion par clé d’accès, anciennement appelée authentification Web ou
WebAuthn en abrégé, permet à un utilisateur de se connecter à un site en
toute sécurité sans utiliser de mot de passe, même si un nom d’utilisateur
reste nécessaire. Elle utilise une cryptographie forte qui résiste
extrêmement bien aux problèmes les plus courants liés aux mots de passe :

* quelqu’un l’a deviné (attaque par force brute)
* quelqu’un l’a intercepté (attaque de l’homme du milieu)
* quelqu’un vous a trompé pour vous le faire divulguer (attaque par hameçonnage)
* quelqu’un l’a cassé après avoir obtenu une copie des données de votre base
de données (attaques par injection SQL)
* quelqu’un vous l’a volé.

La connexion par clé d’accès n’est pas seulement très sécurisée ; elle est
également très conviviale ! Vous n’avez plus besoin de mémoriser de longs
mots de passe ni d’utiliser un gestionnaire de mots de passe. Tout ce
dont vous avez besoin est un *authentificateur*, parfois aussi appelé une
*clé d’accès*.

Un authentificateur peut prendre de nombreuses formes, physiques ou
virtuelles. Il peut s’agir d’une clé matérielle séparée se connectant à
votre appareil via USB, Bluetooth ou NFC. Il peut s’agir de votre appareil
lui-même, qui déverrouille son authentificateur intégré à l’aide d’un code
PIN, d’un lecteur d’empreintes digitales, d’une reconnaissance faciale ou
d’une vérification biométrique similaire.

Cette fonctionnalité fonctionne déjà sur les appareils Android et
iOS/iPadOS, et nous travaillons également à l’activer sous Windows. Votre
téléphone peut même servir d’authentificateur — actuellement, cela est
possible avec les téléphones Android, mais cette fonctionnalité sera
également bientôt disponible sur les appareils iOS / iPadOS.

La connexion par clé d’accès ne fonctionne qu’avec HTTPS et uniquement
lorsque votre site utilise un certificat valide et approuvé pour cela. Ne
vous inquiétez pas, vous n’avez pas besoin de dépenser d’argent
supplémentaire ; les services gratuits tels que Let's Encrypt sont
généralement intégrés aux panneaux de contrôle des hébergeurs Web et
fonctionnent parfaitement avec la connexion par clé d’accès.

La connexion par clé d’accès utilise la cryptographie à clé publique, la
même technologie éprouvée qui protège vos sites avec HTTPS, sécurise vos
informations bancaires, etc. La clé privée ne quitte jamais
l’authentificateur. Votre site ne stocke qu’une clé publique. Même si vous
êtes victime d’une fuite de données, l’attaquant ne disposera que d’une clé
publique pratiquement inutilisable ; il lui faudrait des milliers à des
millions d’années de calcul CPU pour la casser, contre quelques minutes ou
heures nécessaires pour casser le hachage d’un mot de passe fixe que vous
pouvez mémoriser.

La connexion par clé d’accès est l’avenir de l’authentification. Simple,
sécurisée et sans tracas. Tout ce que les mots de passe fixes ne sont pas.

L’image suivante montre un appareil matériel inséré dans le port USB d’un
ordinateur portable. Il coûtait 15 £ en février 2022.

![photographie d’un appareil matériel](../../../en/images/users/passkey-login/01-hardware-device.jpg)

La connexion par clé d’accès utilise une extension système activée par
défaut. Un bouton **Se connecter avec une clé d’accès** sera présent dans
les écrans de connexion par défaut de Joomla 4 et des versions ultérieures,
comme illustré dans l’écran de connexion de l’administration :

![formulaire de connexion sécurisé de l’administration](../../../en/images/users/passkey-login/02-login-form.png)

## Configuration de l’utilisateur

L’utilisateur doit d’abord s’inscrire avec un nom d’utilisateur et un mot de
passe classiques. Après vous être connecté, accédez au formulaire du profil
utilisateur. Pour un administrateur :

- Sélectionnez **Menu utilisateur → Modifier le compte → Connexion par clé d’accès** pour afficher le formulaire, qui ne contient initialement aucun authentificateur enregistré.
- Sélectionnez **Ajouter une nouvelle clé d’accès**

La présentation exacte de l’étape suivante dépend de votre navigateur.
Généralement, vous verrez une alerte, un message ou une fenêtre vous
demandant de sélectionner un type d’authentificateur ou, si vous utilisez
un authentificateur matériel connecté à votre appareil, vous rappelant
d’appuyer sur le bouton de l’authentificateur matériel. Pour des raisons
de sécurité et d’ordre pratique, l’intervalle autorisé pour activer
l’authentificateur est relativement court : 60 secondes.

![invite matérielle de connexion sécurisée de l’administration](../../../en/images/users/passkey-login/03-hardware-prompt.png)

Une fois que vous avez déverrouillé votre authentificateur — en appuyant
sur un bouton, en scannant votre empreinte digitale ou votre visage, en
saisissant un code PIN ou une combinaison de ces méthodes selon votre
authentificateur — le message disparaît, l’authentificateur est enregistré
et l’écran se présente comme suit :

![authentificateur enregistré pour la connexion sécurisée de l’administration](../../../en/images/users/passkey-login/04-registered-authenticator.png)

Il est très important de noter que vous pouvez uniquement enregistrer ou
supprimer des authentificateurs sur votre propre compte utilisateur. Pour
des raisons de sécurité, même un super utilisateur ne peut pas enregistrer,
modifier ou ajouter des authentificateurs sur les comptes d’autres
utilisateurs.

### Authentificateurs

Vous pouvez utiliser n’importe quel authentificateur FIDO U2F ou FIDO2. FIDO U2F est une norme plus ancienne qui prend en charge une sélection plus limitée et moins sécurisée de méthodes cryptographiques. FIDO2 est la norme la plus récente, qui prend en charge des méthodes cryptographiques bien plus sécurisées, notamment la cryptographie sur courbes elliptiques, une méthode cryptographique considérée comme résistante même à l’informatique quantique (si et quand celle-ci devient une réalité pratique). De plus, les authentificateurs FIDO2 peuvent être configurés avec des protections supplémentaires telles qu’un code PIN ou un contrôle biométrique (par exemple, une empreinte digitale), ce qui signifie que même si vous perdez la possession physique de l’authentificateur, la personne qui le trouve ne pourra pas se connecter à vos sites.

Si vous cherchez à acheter un authentificateur matériel, vous pouvez rechercher « FIDO2 » sur votre marketplace préférée, telle qu’Amazon. Il existe un large choix.

Vous pouvez également utiliser une clé FIDO logicielle telle que Krypton comme authentificateur.

De nombreux appareils intègrent une authentification compatible FIDO2 :

- Windows 10 et 11 disposent de Windows Hello avec un code PIN, un lecteur d’empreintes digitales, une caméra de reconnaissance faciale ou une combinaison de clé matérielle et de code PIN.
- macOS dispose de TouchID sur tous les ordinateurs portables équipés du chipset T2 ou basés sur Apple Silicon utilisant le capteur TouchID intégré, ainsi que sur tous les ordinateurs de bureau basés sur Apple Silicon utilisant le nouveau clavier Apple Aluminium avec lecteur d’empreintes digitales.
- iOS / iPadOS dispose de TouchID sur tous les appareils équipés d’un lecteur d’empreintes digitales et de FaceID sur tous les appareils plus récents dotés d’une caméra infrarouge à projection de points pour FaceID.
- Certains appareils Android disposent d’un lecteur d’empreintes digitales ou d’une caméra de reconnaissance faciale. Ceux-ci peuvent également fonctionner comme authentificateurs FIDO2, sur Android 9 ou version ultérieure, en utilisant au moins Google Chrome.
- D’autres appareils peuvent également être disponibles. Par exemple, les téléphones Android utilisant
  [caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1)

### Navigateurs compatibles avec la connexion par clé d’accès

En pratique, si votre système d’exploitation et votre navigateur sont sortis après la mi-2020, vous ne devriez rencontrer aucun problème. Seuls quelques navigateurs très peu courants ne prennent pas encore en charge la connexion par clé d’accès.

## Authentification

Pour vous connecter, vous devez saisir votre nom d’utilisateur dans le champ Nom d’utilisateur du formulaire de connexion. Vous n’avez pas besoin de saisir votre mot de passe, mais si votre navigateur le saisit pour vous, laissez-le. Le mot de passe n’est PAS envoyé au serveur lorsque le formulaire est envoyé via le bouton d’authentification Web.

Il s’ensuit que vous pouvez vous connecter soit avec votre nom d’utilisateur et votre mot de passe, soit avec votre nom d’utilisateur et une clé d’accès.

## Comment désactiver le plugin

Si vous ne souhaitez pas autoriser la connexion par clé d’accès, accédez simplement à la liste des plugins, recherchez le plugin **Système - Connexion par clé d’accès (sans mot de passe)** dans le groupe Système et désactivez-le. Aucun paramètre n’est à configurer.

## Configuration requise du serveur

Pour que la connexion par clé d’accès fonctionne, les conditions préalables suivantes doivent être remplies :

- HTTPS avec un certificat valide et signé. La plupart des hébergeurs vous permettent d’utiliser gratuitement des certificats fournis par Let's Encrypt. Ceux-ci fonctionnent parfaitement avec la connexion par clé d’accès.
- L’extension OpenSSL pour PHP doit être installée et activée.
- L’extension GMP ou l’extension BCmath de PHP doit être installée et activée (l’une ou l’autre convient).
- La bibliothèque Sodium devrait idéalement être activée ; elle permet l’utilisation de la cryptographie sur courbes elliptiques avec les authentificateurs FIDO2 compatibles, laquelle, comme nous l’avons indiqué, constitue la méthode cryptographique la plus sécurisée.

## Questions fréquemment posées et résolution des problèmes

### Je ne vois pas le bouton *Se connecter avec une clé d’accès*

Vous n’accédez pas à votre site via HTTPS. La connexion par clé d’accès est uniquement disponible pour les sites HTTPS dotés d’un certificat valide. Il s’agit d’une mesure de sécurité intégrée à la norme de connexion par clé d’accès. Le plugin vérifie effectivement si le site est accessible via HTTPS en utilisant la classe Uri de Joomla. Dans de rares cas où le serveur indique un protocole incorrect, il se peut que vous ne voyiez pas le bouton même si votre site (prétend être) en HTTPS. Il en va de même si vous avez modifié votre fichier configuration.php et configuré le paramètre facultatif \$live_site avec un préfixe de protocole http:// au lieu de https://.

Notez également que les modules et composants de connexion tiers qui implémentent leur propre formulaire de connexion peuvent ne pas encore afficher ces boutons. Nous avons ajouté une nouvelle infrastructure pour les prendre en charge, comme nous avions dû le faire dans Joomla! 3.2 pour prendre en charge l’authentification à deux facteurs.

### Je dois toujours fournir un nom d’utilisateur. Le fonctionnement de la connexion par Passkey n’est-il pas censé supprimer les noms d’utilisateur ?

Pas vraiment. La spécification actuelle de la connexion par Passkey ne fournit pas de gestion des identités. Les navigateurs web exigent que nous leur envoyions une liste de clés publiques de connexion par Passkey acceptables pendant la phase de connexion. Cela signifie que nous avons besoin de votre nom d’utilisateur pour les récupérer.

Cela dit, l’utilisation de la connexion par Passkey montre enfin clairement que les noms d’utilisateur *ne doivent pas être considérés comme des secrets*. Ils sont considérés comme des informations publiques pouvant être librement transmises à un adversaire, tout comme les clés publiques stockées dans la base de données du site. Le seul secret est stocké dans l’authentificateur lui-même et ne le quitte jamais !

### J’ai enregistré un authentificateur, mais lorsque j’essaie de me connecter, un message m’indique que je ne l’ai pas fait. Est-ce un bug ?

C’est bien un bug, mais il ne vient pas du plugin de connexion par Passkey lui-même.

Un ou plusieurs plugins de votre site génèrent des notifications, avertissements ou erreurs PHP, ce qui corrompt la réponse envoyée par votre serveur. Par conséquent, le code JavaScript de la page ne peut pas analyser la réponse du serveur et ne sait pas si l’utilisateur a enregistré des authentificateurs.

Accédez à l’administration de votre site, puis à Système, Configuration globale, et définissez le paramètre Rapport d’erreurs sur Aucun. Dans la plupart des cas de dysfonctionnement des extensions natives et tierces, cela suffit. Sinon, examinez la sortie de la requête à l’aide des outils de développement de votre navigateur afin de déterminer ce qui corrompt la requête.

### Aucun message ne s’affiche dans Safari pour utiliser mon authentificateur

Cela ne devrait plus se produire avec iOS 13, iPadOS 13 et macOS Catalina, ou toute version ultérieure.

Il s’agit d’un bug de Safari dans les anciennes versions de Safari. Les anciennes versions de Safari n’intégraient la prise en charge de la connexion par Passkey qu’à titre expérimental et celle-ci n’était pas tout à fait terminée.

### Je ne peux pas utiliser de capteur biométrique (TouchID, empreinte digitale, Windows Hello)

Certains anciens navigateurs basés sur Chromium (à l’exception de Google Chrome proprement dit) ne prenaient pas entièrement en charge les authentificateurs intégrés. Ils se bloquaient ou se figeaient lorsque vous essayiez d’en utiliser un. Ces problèmes ont été corrigés dans ces navigateurs vers le milieu de l’année 2020.

Si vous utilisez Windows, n’oubliez pas que votre appareil DOIT être équipé d’une puce Trusted Platform Module (TPM), qui doit être activée dans le BIOS. Le simple fait de disposer d’un capteur biométrique compatible avec Windows Hello ne suffit pas. Il s’agit d’une mesure de sécurité intégrée à la norme de connexion par Passkey elle-même : les informations de l’authentificateur doivent être traitées à l’aide d’un matériel sécurisé et résistant aux altérations afin d’empêcher le détournement de clés (par exemple, un logiciel malveillant exécuté sur l’ordinateur ne peut pas voler la clé utilisée pour l’authentification).

Enfin, gardez à l’esprit que la prise en charge de Windows Hello est toujours en cours de développement et sera publiée avec Joomla 4.2.

### Si je peux utiliser un authentificateur logiciel, pourquoi devrais-je m’embêter avec un jeton matériel ?

La pierre angulaire de la connexion par Passkey est le secret absolu de la clé privée. Elle n’est connue que de l’authentificateur et il devrait être impossible de la communiquer au monde extérieur.

Dans le cas d’un authentificateur matériel, qu’il s’agisse d’un appareil matériel autonome ou d’un TPM / Secure Enclave intégré à votre appareil, cela est garanti par la nature même de ce matériel.

Un authentificateur logiciel génère une clé secrète et la stocke dans le système de fichiers. Cependant, il s’agit toujours d’une application logicielle ordinaire qui s’exécute au sein de votre système d’exploitation habituel, qu’il s’agisse de celui de votre téléphone ou de votre ordinateur. Il est donc vulnérable à plusieurs catégories d’attaques pouvant être utilisées pour dérober des informations à votre insu (failles de sécurité dans le logiciel lui-même, logiciels malveillants exploitant des vulnérabilités de type Spectre dans les processeurs modernes, etc.).

Ainsi, un authentificateur logiciel est beaucoup plus pratique et sécurisé qu’un mot de passe ordinaire, mais un authentificateur matériel offre le meilleur niveau de sécurité. Choisissez votre authentificateur en fonction de votre budget et de vos besoins en matière de sécurité.

Étant donné que le prix d’une clé FIDO (compatible avec la connexion par Passkey) est inférieur à 20 € sur Amazon, vous pouvez utiliser un authentificateur matériel dans la plupart des cas d’utilisation pratiques.

### Pourquoi les identifiants sont-ils chiffrés dans la base de données ? N’est-ce pas excessif ?

La seule chose stockée dans la base de données est la clé publique renvoyée par
l’authentificateur lorsque nous effectuons la cérémonie d’attestation (c’est
le nom officiel donné à l’enregistrement d’un authentificateur selon la
spécification de connexion par clé d’accès). Comme il s’agit d’une clé
publique, il n’est pas nécessaire de la protéger contre la lecture. Même si
un utilisateur non autorisé parvenait à lire ces informations, il ne pourrait
pas usurper l’authentificateur, par exemple en le clonant.

Cependant, si un utilisateur malveillant disposait d’un accès en écriture
uniquement à la table de base de données `#__webauthn_credentials`, sans
accès en lecture au système de fichiers et sans accès en écriture à aucune
autre table, il pourrait éventuellement **ajouter** son propre
authentificateur et ainsi usurper l’utilisateur ciblé sur le système. Il
s’agit d’une attaque très théorique, car il lui faudrait également connaître
l’identifiant utilisateur de la personne attaquée, ce qui est plus difficile
à déterminer sans certaines connaissances internes du site lui-même. De plus,
il est extrêmement improbable de disposer d’un accès en écriture à cette
seule table et non à l’ensemble de la base de données (auquel cas il serait
possible de créer un nouveau super utilisateur). Nous chiffrons néanmoins les
identifiants afin de rendre impossible la réussite de cette attaque, pourtant
entièrement théorique.

Nous savons parfaitement que si un utilisateur dispose d’un accès en lecture
au système de fichiers du serveur, il a accès à la clé de chiffrement et aux
informations de connexion à la base de données, qui sont toutes stockées dans
configuration.php. Cependant, dans ce cas, vous êtes déjà piraté : l’attaquant
peut lire configuration.php et sait donc comment se connecter à votre base de
données. Il peut alors faire ce qu’il veut sur votre site, notamment supprimer
tous les super utilisateurs existants et créer son propre compte de super
utilisateur. Il n’y a donc aucune raison d’essayer de résoudre cette
situation ; votre site serait entièrement compromis (piraté). La seule chose
qui pourrait vous sauver est de disposer de sauvegardes régulières, testées et
stockées hors site.

### J’ai configuré l’authentification à deux facteurs, mais je suis connecté sans fournir ma clé secrète. N’est-ce pas dangereux ?

Non, c’est intentionnel et prévu par la conception.

Lorsque nous avons ajouté l’authentification à deux facteurs (TFA) dans Joomla! 3.2, vous ne pouviez vous connecter à votre site qu’avec un nom d’utilisateur et un mot de passe. Les mots de passe peuvent être volés ou devinés. L’authentification à deux facteurs était donc le seul moyen d’assurer un niveau de sécurité minimal sur les cibles à haut risque et à forte valeur. C’était en 2013.

La connexion par clé d’accès est une solution d’authentification entièrement
différente, qui ne présente aucun des problèmes liés aux mots de passe fixes.
Elle utilise une cryptographie robuste et du matériel sécurisé pour rendre
pratiquement impossible le détournement des clés cryptographiques
d’authentification. Elle n’est pas non plus vulnérable à l’hameçonnage : vous
ne pouvez pas être trompé et amené à l’utiliser sur un site usurpateur, car
l’identifiant de connexion par clé d’accès est lié au nom de domaine exact
pour lequel il a été émis (oui, si vous utilisez plusieurs domaines pour
votre site ou si vous transférez votre site vers un autre domaine, vous devrez
réenregistrer tous vos authentificateurs de connexion par clé d’accès — vous
avez bien compris !). Par conséquent, l’authentification avec une clé d’accès
est extrêmement sécurisée et remplace les raisons qui avaient rendu
l’authentification à deux facteurs nécessaire. Cela signifie que si vous vous
authentifiez avec succès à l’aide d’une clé d’accès, la clé secrète TFA n’a
pas besoin d’être — et n’est donc pas — vérifiée.

Dans un monde idéal, vous ne pourriez vous connecter à votre site qu’avec une
clé d’accès. C’est une fonctionnalité sur laquelle nous travaillons, et vous
pourriez ne pas vouloir l’activer ; après tout, si votre nom de domaine change,
ou si vous perdez l’accès à tous vos authentificateurs de connexion par clé
d’accès ou les réinitialisez, vous seriez bloqué hors de votre site. Vous
devriez donc tout de même activer l’authentification à deux facteurs sur votre
compte utilisateur, puisque la connexion par mot de passe peut encore être
utilisée comme solution de secours pour vous connecter à votre site et doit
être protégée contre les attaques connues visant les mots de passe fixes.

### L’A2F n’est-elle pas suffisante ? Pourquoi avons-nous besoin de la connexion par clé d’accès ?

L’A2F seule est suffisante dans la plupart des cas, mais elle souffre de deux problèmes.

Premièrement, l’expérience utilisateur est assez peu pratique. Vous devez fournir
votre clé secrète, qui change constamment, avec votre nom d’utilisateur et votre
mot de passe. La plupart des gens utilisent TOTP (le code PIN à six chiffres qui
change toutes les 30 secondes), ce qui ralentit la connexion et tend à frustrer
les utilisateurs. L’utilisation d’une YubiKey est beaucoup plus rapide, mais
elle est également plus coûteuse et plus compliquée à déployer lorsque le site
compte plus de quelques utilisateurs. Une YubiKey a également une durée de vie
prévue d’environ 2 ans d’utilisation quotidienne lorsqu’elle génère des mots de
passe à usage unique (elle épuise la mémoire à écriture unique qu’elle utilise
pour suivre les signatures qu’elle a émises).

Deuxièmement, si vous utilisez TOTP, vous restez exposé à des problèmes de
sécurité tels que les enregistreurs de frappe, l’hameçonnage et la possibilité
que la clé secrète utilisée pour générer le TOTP soit dérobée. De plus, avec un
million de possibilités et trente secondes pour les essayer, il est concevable
qu’un attaquant puisse avoir de la chance, puisque Joomla ne verrouille pas
votre compte et n’applique pas de limitation du nombre de tentatives de
connexion échouées. Bien que ces protections puissent être mises en œuvre,
l’implémentation elle-même pourrait être exploitée pour créer une situation de
déni de service qui empêcherait un utilisateur légitime d’accéder à son site
pendant que l’attaquant s’affaire à s’y infiltrer. C’est un cas où le remède
serait pire que le mal.

La connexion par clé d’accès améliore considérablement l’expérience utilisateur.
Les principaux navigateurs ont adopté la connexion par clé d’accès et offrent
une expérience utilisateur convaincante, en guidant les utilisateurs afin qu’ils
utilisent correctement les authentificateurs. Se connecter avec une clé d’accès
est plus pratique, même par rapport à l’utilisation de la fonction de
remplissage automatique d’un gestionnaire de mots de passe. Avec les versions
récentes des systèmes d’exploitation mobiles, cette expérience, autrefois
légèrement déroutante, devient rapidement plus simple que ne l’ont jamais été
les mots de passe et l’A2F.

Là où la connexion par clé d’accès se distingue véritablement, c’est en matière
de sécurité. Grâce à l’utilisation de matériel sécurisé et à une validation
rigoureuse du nom de domaine du site, elle est pratiquement immunisée contre
les enregistreurs de frappe, l’hameçonnage et la compromission des clés. Elle
dispose même d’une protection intégrée contre le clonage des clés. Oui, vous
pouvez toujours perdre votre matériel — mais les authentificateurs FIDO2, qu’il
s’agisse de dispositifs externes ou intégrés, peuvent être verrouillés à l’aide
d’un code PIN ou de données biométriques. Globalement, utiliser la connexion par
clé d’accès avec des authentificateurs FIDO2 résiste davantage au vol et à la
perte que les clés de votre maison ou de votre voiture.

## Notes pour les développeurs

### Boutons de connexion supplémentaires

Le module de plugin et com_users utilisent désormais l’événement
onUserLoginButtons, défini et appelé dans
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons`, afin de récupérer les
définitions des boutons supplémentaires qui doivent être placés après le bouton
de connexion habituel.

Tous les développeurs qui implémentent un module de connexion ou, plus
généralement, un formulaire de connexion devraient également utiliser la méthode
statique publique
`Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` afin de récupérer ces
définitions et d’afficher ces boutons, pour rendre leurs logiciels entièrement
compatibles avec Joomla 4.

Les développeurs souhaitant implémenter des boutons personnalisés devraient
examiner la manière dont le plugin système de connexion par clé d’accès
implémente cette fonctionnalité. Ces boutons peuvent servir à implémenter des
services d’authentification unique tiers ou même à se connecter à l’aide de
services d’identité tiers tels que ceux proposés par les réseaux sociaux
populaires (Facebook, Google, Twitter, GitHub, etc.).

Cette modification n’a pas d’impact négatif sur la rétrocompatibilité. Les
modules de connexion et formulaires de connexion tiers continueront de
fonctionner normalement, même s’ils n’implémentent pas la fonctionnalité des
boutons de connexion supplémentaires, avec toutefois l’absence notable des
intégrations permises par cette fonctionnalité, comme l’authentification Web
elle-même. Autrement dit, ils ne cesseront pas de fonctionner (ce qui
constituerait une rupture de compatibilité ascendante), mais ils ne disposeront
pas de toutes les fonctionnalités.

### Autoriser com_ajax sur la page de connexion de l’administration

La page de connexion de l’administration autorise com_ajax dans
AdministratorApplication afin qu’il puisse être utilisé pour traiter les
requêtes des utilisateurs invités.

Cette modification n’entraîne aucun problème de rétrocompatibilité, tant que
les développeurs appliquent des pratiques saines et ne supposent pas que le
fait d’être appelé par com_ajax dans l’administration prouve que l’utilisateur
est connecté à l’administration. Ce serait une mauvaise pratique en matière de
sécurité. La pratique recommandée consiste à utiliser l’objet User de Joomla
pour déterminer s’il s’agit d’un utilisateur invité et, dans le cas contraire,
si l’utilisateur dispose de l’autorisation requise pour effectuer l’action
demandée via com_ajax. Autrement dit, si cette modification a cassé votre code,
celui-ci était déjà défectueux et devait de toute façon être remanié.

## Informations complémentaires

La documentation initiale de cette fonctionnalité se trouve dans la demande
d’extraction [PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Traduit par openai.com*