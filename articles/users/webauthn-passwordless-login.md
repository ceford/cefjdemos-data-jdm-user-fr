<!-- Filename: WebAuthn_Passwordless_Login / Display title: Connexion WebAuthn -->

## Connexion sans mot de passe WebAuthn

L'authentification Web, ou WebAuthn en abrégé, permet à un utilisateur de se connecter en toute sécurité à un site sans utiliser de mot de passe — bien qu'un nom d'utilisateur soit toujours nécessaire. Elle utilise une cryptographie robuste d'une manière extrêmement résistante aux problèmes les plus courants liés aux mots de passe :
* quelqu'un l'a deviné (attaque par force brute)
* quelqu'un l'a intercepté (attaque de l'homme du milieu)
* quelqu'un vous a trompé pour que vous le divulguiez (attaque de phishing)
* quelqu'un l'a craqué après avoir obtenu une copie des données de votre base de données (attaques par injection SQL)
* quelqu'un l'a volé.

WebAuthn n'est pas seulement très sécurisé ; c'est aussi très convivial ! Vous n'avez plus besoin de vous souvenir de longs mots de passe ou d'utiliser un gestionnaire de mots de passe. Tout ce dont vous avez besoin est un *authentificateur*, parfois aussi appelé une *clé d'accès*.

Un authentificateur peut avoir de nombreuses formes, physiques ou virtuelles. Il peut s'agir d'une clé matérielle séparée se connectant à votre appareil via USB, Bluetooth ou NFC. Il peut s’agir de votre appareil lui-même, déverrouillant son authentificateur intégré avec un code PIN, un lecteur d'empreintes digitales, une reconnaissance faciale ou une vérification biométrique similaire.

Cette fonctionnalité fonctionne déjà sur les appareils Android et iOS/iPadOS et nous travaillons à la rendre disponible sur Windows également. Cela peut même être votre téléphone — actuellement, cela est possible avec les téléphones Android, mais cette fonctionnalité arrive également sur les appareils iOS / iPadOS.

WebAuthn ne fonctionne qu'en HTTPS et uniquement lorsque votre site utilise un certificat valide et de confiance pour cela. Ne vous inquiétez pas, vous n'avez pas besoin de dépenser de l'argent supplémentaire ; des services gratuits comme Let’s Encrypt sont généralement intégrés dans les panneaux de contrôle d'hébergement web et fonctionnent parfaitement avec WebAuthn.

WebAuthn utilise la cryptographie à clé publique, la même technologie éprouvée qui sécurise vos sites avec HTTPS, vos informations bancaires, etc. La clé privée ne quitte jamais l'authentificateur. Votre site ne stocke qu'une clé publique. Même si vous subissez une fuite de données, l'attaquant se retrouvera avec une clé publique pratiquement inutile ; il leur faudrait des milliers à des millions d'années CPU pour la craquer contrairement aux quelques minutes ou heures nécessaires pour craquer le hash d'un mot de passe fixe que vous pouvez mémoriser.

WebAuthn est l'avenir de l'authentification. Facile, sécurisé et sans tracas. Tout ce que les mots de passe fixes ne sont pas.

L'image suivante montre un appareil matériel inséré dans le port USB d'un ordinateur portable. Il a coûté 15 £ en février 2022.

![photographie de l'appareil matériel](../../../en/images/users/passwordless-login-hardware-device.jpg)

WebAuthn utilise un plugin système qui est activé par défaut. Un bouton **Web Authentication** sera présent dans les écrans de connexion par défaut de Joomla 4 et versions ultérieures, comme illustré dans l'écran de connexion Administrateur :

![formulaire de connexion administrateur sécurisé](../../../en/images/users/passwordless-login-login-form.jpg)

## Configuration de l'utilisateur

L'utilisateur doit d'abord s'inscrire avec un Nom d'utilisateur et un Mot de passe normaux. Après s'être connecté, allez au formulaire de Profil Utilisateur. Pour un Administrateur :

- Sélectionnez **Menu Utilisateur → Modifier le Compte → Connexion par Authentification Web W3C
  (WebAuthn)** pour faire apparaître le formulaire, initialement sans
  authentificateurs enregistrés.
- Sélectionnez **Ajouter un nouvel authentificateur**

La présentation exacte de l'étape suivante dépend de votre navigateur.
En général, vous verrez une alerte, un message ou une fenêtre vous demandant de sélectionner
un type d'authentificateur ou, si vous utilisez un authentificateur matériel
rattaché à votre appareil, vous rappelant d'appuyer sur le bouton de l'
authentificateur matériel. Pour des raisons de sécurité et pratiques, il y a un
intervalle de temps relativement court autorisé pour activer l'authentificateur :
60 secondes.

![invite de connexion sécurisée pour l’administrateur avec authentificateur matériel](../../../en/images/users/passwordless-login-hardware-propmpt.png)

Une fois que vous déverrouillez votre authentificateur – en appuyant sur un bouton, en scannant votre
empreinte digitale / visage, en entrant un code PIN ou une combinaison des options ci-dessus
en fonction de votre authentificateur – le message disparaît, l'
authentificateur est enregistré et l'écran apparaît comme suit :

![authentificateur enregistré pour la connexion sécurisée de l’administrateur](../../../en/images/users/passwordless-login-registered-authenticator.png)

Il est très important de noter que vous pouvez uniquement enregistrer ou supprimer
des authentificateurs sur votre propre compte utilisateur. Pour des raisons de sécurité, même un
Super Utilisateur n'est pas autorisé à enregistrer, modifier ou ajouter
des authentificateurs sur les comptes d'autres utilisateurs.

### Authenticator

Vous pouvez utiliser n'importe quel authentificateur FIDO U2F ou FIDO2. L'U2F de FIDO est une norme plus ancienne
qui prend en charge une sélection plus limitée et moins sécurisée de
méthodes cryptographiques. FIDO2 est la norme plus récente qui prend en charge des
méthodes cryptographiques beaucoup plus sécurisées, y compris la Cryptographie à Courbe
Elliptique, une méthode cryptographique qui est réputée résister même à
l'ordinateur quantique (si et quand cela devient une réalité pratique). De plus, les
authentificateurs FIDO2 peuvent être configurés pour avoir des protections supplémentaires telles qu'un
code PIN ou un contrôle biométrique (par ex. scan d'empreinte digitale) ce qui signifie que même
si vous perdez la possession physique de l'authentificateur, celui qui le trouve
ne peut pas se connecter à vos sites.

Si vous cherchez à acheter un authentificateur matériel, vous pouvez rechercher
"FIDO2" sur votre marché préféré, tel qu'Amazon. Il y a un large
choix à votre disposition.

Vous pouvez également utiliser une clé FIDO logicielle comme Krypton
comme votre authentificateur.

De nombreux appareils disposent d'une authentification compatible FIDO2 intégrée :

- Windows 10 et 11 disposent de Windows Hello avec un code PIN, un lecteur
  d'empreintes digitales, une caméra de reconnaissance faciale ou une combinaison de clé
  matérielle et de PIN. Le support de Windows Hello est en cours d'ajout au plugin avec une
  version cible de Joomla 4.2.0.
- macOS dispose de TouchID sur tous les ordinateurs portables avec la puce T2
  ou ceux basés sur Apple Silicon utilisant le capteur TouchID intégré, ainsi que
  tous les ordinateurs de bureau basés sur Apple Silicon utilisant le nouveau clavier
  en aluminium d'Apple avec un lecteur d'empreintes digitales.
- iOS / iPadOS dispose de TouchID sur tous les appareils avec un lecteur d'empreintes digitales et
  FaceID sur tous les appareils récents avec une caméra de projection de points
  infrarouges FaceID.
- Certains appareils Android disposent d'un lecteur d'empreintes digitales ou d'une caméra de
  reconnaissance faciale. Ceux-ci peuvent également fonctionner comme des authentificateurs FIDO2, sur
  Android 9 ou plus récent utilisant Google Chrome, au minimum.
- D'autres appareils peuvent également être disponibles. Par exemple, les téléphones Android utilisant
  ![caBLE](https://groups.google.com/a/fidoalliance.org/g/fido-dev/c/go6GoFW27Dw/m/9flCLR5pBQAJ?pli=1)

### Navigateurs compatibles WebAuthn

Les navigateurs basés sur Chromium et Firefox prennent en charge WebAuthn depuis début 2019.

Safari et tous les navigateurs iOS/iPadOS (qui sont, en fait, Safari avec une
interface différente) prennent en charge pleinement WebAuthn depuis la sortie
d'iOS/iPadOS 13 fin 2019.

Pratiquement, si votre système d'exploitation et navigateur ont été publiés
après mi-2020 vous ne devriez rencontrer aucun problème. Seuls quelques
navigateurs très peu communs ne prennent toujours pas en charge WebAuthn.

## Authentification

Pour vous connecter, vous devez entrer votre nom d'utilisateur dans le champ Nom d'utilisateur du formulaire de connexion. Vous n'avez pas besoin de saisir votre mot de passe, mais si votre navigateur le remplit pour vous, laissez-le. Le mot de passe n'est PAS envoyé au serveur lorsque le formulaire est soumis via le bouton Authentification Web.

Il en résulte que vous pouvez vous connecter soit avec votre nom d'utilisateur et votre mot de passe, soit avec votre nom d'utilisateur et l'authentification Web.

## Comment désactiver le plugin

Si vous ne souhaitez pas autoriser WebAuthn, rendez-vous simplement dans la liste des plugins, trouvez Système - Connexion sans mot de passe WebAuthn dans le groupe Système et désactivez-le. Il n'y a pas de paramètres à définir.

## Exigences du serveur

Pour que WebAuthn fonctionne, les conditions préalables suivantes doivent être remplies :

- HTTPS avec un certificat valide et signé. La plupart des hébergeurs vous permettent d'utiliser gratuitement des certificats émis par Let's Encrypt. Ceux-ci fonctionnent parfaitement avec WebAuthn.
- L'extension OpenSSL pour PHP doit être installée et activée.
- L'extension PHP GMP ou l'extension PHP BCmath doit être installée et activée (l'une ou l'autre suffira).
- La bibliothèque Sodium devrait idéalement être activée ; elle permet l'utilisation de la cryptographie à courbes elliptiques sur les authentificateurs FIDO2 compatibles, ce qui, comme nous l'avons dit, est la méthode cryptographique la plus sécurisée.

## Questions Fréquemment Posées et Dépannage

### Je ne vois pas le bouton de connexion “Authentification Web”

Vous n'accédez pas à votre site sous HTTPS. WebAuthn n'est disponible que pour les sites HTTPS avec un certificat valide. C'est une précaution de sécurité intégrée dans la norme WebAuthn. Le plugin vérifie en fait si le site est accédé via HTTPS en utilisant la classe Uri de Joomla. Dans de rares cas où le serveur ment sur le protocole, vous pourriez ne pas voir le bouton même si votre site (prétend être) HTTPS. Même chose si vous avez modifié votre fichier configuration.php et configuré le paramètre optionnel \$live_site avec un préfixe de protocole http:// au lieu de https://.

Notez également que les modules de connexion tiers et les composants implémentant leur propre formulaire de connexion peuvent ne pas encore afficher ces boutons. Nous avons ajouté une nouvelle infrastructure pour les prendre en charge, un peu comme ce que nous avons dû faire dans Joomla! 3.2 pour prendre en charge l'Authentification à Deux Facteurs.

### Je dois toujours fournir un nom d'utilisateur. WebAuthn n'est-il pas censé se débarrasser des noms d'utilisateur ?

Pas vraiment, non. La spécification actuelle de WebAuthn ne prévoit pas la gestion des identités. Les navigateurs Web nous demandent d'envoyer une liste de clés publiques WebAuthn acceptables pendant la phase de connexion. Cela signifie que nous avons besoin de votre nom d'utilisateur pour les récupérer.

Cela dit, utiliser WebAuthn clarifie enfin que les noms d'utilisateur *ne doivent pas être considérés comme des secrets*. Ils sont considérés comme des informations publiques qui peuvent être librement transmises à un adversaire, tout comme les clés publiques stockées dans la base de données du site. Le seul secret est stocké dans l'authentificateur lui-même et ne quitte jamais l'authentificateur !

### J'ai enregistré un authentificateur mais lorsqu'on essaie de se connecter, cela m'indique que je ne l'ai pas fait. Est-ce un bug ?

C'est un bug, mais pas avec le plugin WebAuthn lui-même.

Un ou plusieurs plugins sur votre site génèrent des notices, avertissements ou erreurs PHP, corrompant ainsi la réponse renvoyée par votre serveur. En conséquence, le JavaScript sur la page ne peut pas analyser la réponse du serveur et n'est pas sûr que des authentificateurs soient enregistrés par l'utilisateur.

Allez dans l'interface d'administration de votre site, Système, Configuration Globale et réglez le Rapport d'Erreurs sur Aucun. Dans la plupart des cas de mauvais comportement des plugins cœur et 3PD cela suffit. Sinon, veuillez examiner la sortie de la requête en utilisant les outils de développement de votre navigateur pour voir ce qui corrompt la requête.

### Il n'y a pas d'invite sur Safari pour utiliser mon authentificateur

Cela ne devrait plus se produire avec iOS 13, iPadOS 13 et macOS Catalina ou toute version ultérieure.

C'est un bug Safari dans les anciennes versions de Safari. Les anciennes versions de Safari n'incluaient le support de WebAuthn que comme une fonctionnalité expérimentale et pas tout à fait terminée.

### Je ne peux pas utiliser un capteur biométrique (TouchID, empreinte digitale, Windows Hello)

Certains anciens navigateurs basés sur Chromium (à l'exception de Google Chrome proprement dit) n'avaient pas un support complet pour les authentificateurs intégrés. Ils se bloquaient ou se figeaient lorsque vous essayiez d'en utiliser un. Ces problèmes ont été corrigés dans ces navigateurs vers la mi-2020.

Si vous utilisez Windows, veuillez vous rappeler que votre appareil DOIT avoir une puce Trusted Platform Module (TPM) et qu'elle doit être activée dans le BIOS. Juste avoir un capteur biométrique compatible Windows Hello ne suffit pas. C'est une précaution de sécurité dans la norme WebAuthn elle-même : les informations d'authentification doivent être traitées en utilisant du matériel sécurisé et résistant aux altérations pour empêcher la subversion des clés (par exemple, un malware exécuté sur l'ordinateur ne peut pas voler la clé utilisée pour l'authentification).

Enfin, gardez à l'esprit que le support Windows Hello est toujours en cours de développement et sera publié avec Joomla 4.2.

### Si je peux utiliser un authentificateur logiciel, pourquoi devrais-je m'embêter avec un token matériel ?

Le pivot de WebAuthn est le secret absolu de la clé privée. Elle est uniquement connue de l'authentificateur et il devrait être impossible de la communiquer au monde extérieur.

Dans le cas d'un authentificateur matériel, qu'il s'agisse d'un dispositif matériel discret ou d'une TPM/Enclave Sécurisée intégrée à votre appareil, cela est intrinsèque à la nature même de ce matériel.

Un authentificateur logiciel génère une clé secrète et la stocke dans le système de fichiers. Cependant, il reste une application logicielle régulière qui s'exécute dans votre système d'exploitation habituel, qu'il s'agisse de votre téléphone ou de votre ordinateur. En conséquence, elle est susceptible d'être la cible de plusieurs types d'attaques qui peuvent être utilisés pour voler des informations de manière subreptice (problèmes de sécurité dans le logiciel lui-même, logiciels malveillants utilisant des vulnérabilités de type Spectre dans les processeurs modernes, etc.).

Ainsi, un authentificateur logiciel est bien plus pratique et sécurisé qu'un mot de passe régulier mais un authentificateur matériel offre la meilleure sécurité. Choisissez votre authentificateur en fonction de votre budget et de vos besoins en matière de sécurité.

Considérant que le prix d'une clé FIDO – qui est compatible avec WebAuthn – est inférieur à 10 € sur Amazon, vous pouvez utiliser un authentificateur matériel dans la plupart des cas pratiques.

### Pourquoi les informations d'identification sont-elles chiffrées dans la base de données ? Est-ce que ce n'est pas exagéré ?

La seule chose stockée dans la base de données est la clé publique retournée par l'authentificateur lorsque nous effectuons la cérémonie d'attestation (c'est le nom formel de l'enregistrement d'un authentificateur selon la spécification WebAuthn). Étant une clé publique, elle n'a pas besoin d'être protégée contre la lecture. Même si un utilisateur non autorisé pouvait lire cette information, il ne serait pas capable d'usurper l'authentificateur, par exemple en le clonant.

Cependant, si un utilisateur malveillant avait un accès en écriture uniquement à la table de base de données `#__webauthn_credentials`, sans accès en lecture au système de fichiers et sans accès en écriture à aucune autre table, il pourrait concevoir **ajouter** son propre authentificateur, pouvant ainsi se faire passer pour l'utilisateur ciblé sur le système. Il s'agit d'une attaque très théorique car il leur faudrait également connaître l'identifiant utilisateur de l'utilisateur qu'ils attaquent, ce qui est plus difficile à déduire sans une certaine connaissance interne du site lui-même. En outre, avoir un accès en écriture juste à cette table et non à l'ensemble de la base de données (auquel cas ils pourraient créer un nouvel Utilisateur Super) est extrêmement improbable. Cependant, nous chiffrons les informations d'identification pour rendre impossible même cette attaque entièrement théorique.

Nous sommes pleinement conscients que si un utilisateur a un accès en lecture au système de fichiers du serveur, il a accès à la clé de chiffrement et aux informations de connexion à la base de données, toutes stockées dans configuration.php. Cependant, dans ce cas, vous êtes déjà piraté : l'attaquant peut lire configuration.php et sait donc comment se connecter à votre base de données. Dans ce cas, il peut faire ce qu'il veut de votre site, y compris supprimer tous les Utilisateurs Super existants et créer son propre compte d'Utilisateur Super. Par conséquent, il n'y a aucune raison d'essayer de traiter cette situation ; vous seriez complètement compromis (piraté). La seule chose qui pourrait être une planche de salut est des sauvegardes régulières, testées et hors site.

### J'ai configuré l'Authentification à Deux Facteurs mais je suis connecté sans fournir ma clé secrète. N'est-ce pas non sécurisé ?

Non, c'est intentionnel et par conception.

Lorsque nous avons ajouté l'Authentification à Deux Facteurs (TFA) dans Joomla! 3.2, vous ne pouviez vous connecter à votre site qu'avec un nom d'utilisateur et un mot de passe. Les mots de passe peuvent être volés ou devinés. Par conséquent, la TFA était le seul moyen de fournir un minimum de sécurité sur des cibles à haut risque et à haute valeur. C'était en 2013.

WebAuthn est une solution d'authentification entièrement différente qui n'a aucun des problèmes des mots de passe fixes. Elle utilise une cryptographie forte et du matériel sécurisé pour rendre pratiquement impossible la subversion des clés cryptographiques d'authentification. Elle est également inviolable, c'est-à-dire que vous ne pouvez pas être dupé en l'utilisant sur un site usurpateur, car l'information d'identification WebAuthn est liée au nom de domaine exact pour lequel elle a été délivrée (oui, si vous utilisez plusieurs domaines pour votre site ou transférez votre site vers un autre domaine, vous devrez réenregistrer tous vos authentificateurs WebAuthn – vous avez bien lu !). En conséquence, l'authentification avec WebAuthn est incroyablement sécurisée et remplace les raisons qui nécessitaient la TFA. Cela signifie que si vous vous authentifiez avec succès en utilisant WebAuthn, le secret de la TFA n'a pas besoin d'être – et n'est donc pas – vérifié du tout.

Dans un monde idéal, vous ne pourriez vous connecter à votre site qu'avec WebAuthn. C'est une fonctionnalité sur laquelle nous travaillons et que vous pourriez ne pas vouloir activer ; après tout, si votre nom de domaine change ou si vous perdez l'accès à ou réinitialisez tous vos authentificateurs WebAuthn, vous seriez verrouillé hors de votre site. Par conséquent, vous devriez toujours activer la TFA sur votre compte utilisateur sur la base que la connexion par mot de passe peut toujours être utilisée comme une solution de secours pour vous connecter à votre site et doit être protégée contre les attaques connues contre les mots de passe fixes.

### La TFA n'est-elle pas suffisante ? Pourquoi avons-nous besoin de WebAuthn ?

La TFA seule est suffisante dans la plupart des cas, mais elle souffre de deux problèmes.

Premièrement, elle offre une expérience utilisateur assez maladroite. Vous devez fournir votre clé secrète en constante évolution avec votre nom d'utilisateur et votre mot de passe. La plupart des gens utilisent TOTP (le code PIN à six chiffres qui change toutes les 30 secondes) ce qui ralentit l'accès et tend à frustrer les utilisateurs. Utiliser une YubiKey est beaucoup plus rapide, mais aussi plus coûteux et plus compliqué à fournir lorsque vous avez plus de quelques utilisateurs sur le site. Une YubiKey a également une durée de vie prévue d'environ 2 ans d'utilisation quotidienne lorsque vous générez des mots de passe à usage unique (elle épuise la mémoire écriture unique qu'elle utilise pour garder une trace des signatures qu'elle a émises).

Deuxièmement, si vous utilisez TOTP, vous êtes toujours susceptible d'être victime de problèmes de sécurité tels que les enregistreurs de frappe, le phishing et la possibilité que la clé secrète utilisée pour générer le TOTP soit volée. De plus, avec un million de possibilités et trente secondes pour les essayer, il est concevable qu'un attaquant puisse avoir de la chance puisque Joomla ne verrouille pas votre compte et n'applique pas non plus de limitation de taux pour les tentatives de connexion échouées. Bien que ces protections puissent être mises en œuvre, leur mise en œuvre elle-même pourrait être utilisée pour créer une situation de déni de service qui bloque un utilisateur légitime hors de son site tandis que l'attaquant s'infiltre. C'est un cas où le remède est pire que le mal.

WebAuthn améliore grandement l'expérience utilisateur. Les principaux navigateurs ont adopté WebAuthn et offrent une expérience utilisateur convaincante, guidant les utilisateurs dans l'utilisation des authentificateurs avec succès. Se connecter avec WebAuthn est plus pratique même par rapport à l'utilisation de la fonction de remplissage automatique d'un gestionnaire de mots de passe. Avec les récentes versions des systèmes d'exploitation mobiles, même cette expérience, autrefois légèrement déroutante, devient rapidement plus facile que les mots de passe et la TFA ne l'ont jamais été.

Là où WebAuthn excelle vraiment, c'est sur le front de la sécurité. En utilisant du matériel sécurisé et une validation forte du nom de domaine du site, il est pratiquement immunisé contre les enregistreurs de frappe, le phishing et la subversion des clés. Il a même une protection intégrée contre le clonage des clés. Oui, vous pouvez toujours perdre votre matériel – mais les authentificateurs FIDO2, qu'ils soient des appareils externes ou intégrés, peuvent être verrouillés avec un code PIN ou des données biométriques. Dans l'ensemble, utiliser WebAuthn avec des authentificateurs FIDO2 est plus résistant au vol et à la perte que vos clés de maison ou de voiture.

## Notes du Développeur

### Boutons de connexion supplémentaires

Le module plugin et com_users utilisent maintenant l'événement onUserLoginButtons, défini et appelé dans `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons`, pour récupérer les définitions de tous les boutons supplémentaires qui doivent être placés après le bouton de connexion régulier.

Tous les développeurs qui implémentent un module de connexion ou, plus généralement, un formulaire de connexion, devraient également utiliser la méthode publique et statique `Joomla\CMS\Helper\AuthenticationHelper::getLoginButtons` pour récupérer ces définitions et afficher ces boutons afin de rendre leur logiciel pleinement compatible avec Joomla 4.

Les développeurs souhaitant implémenter des boutons personnalisés devraient examiner comment le plugin système WebAuthn implémente cette fonctionnalité. De tels boutons peuvent être utilisés pour implémenter des services de connexion unique tiers ou même pour se connecter en utilisant des services d'identité tiers tels que ceux offerts par des réseaux sociaux populaires (Facebook, Google, Twitter, GitHub, etc.).

Ce changement n'affecte pas négativement la compatibilité ascendante. Les modules de connexion tiers et les formulaires de connexion continueront à fonctionner normalement, même s'ils n'implémentent pas la fonctionnalité des boutons de connexion supplémentaires, incluant l'absence notable d'intégrations offertes par cette fonctionnalité telles que l'authentification Web elle-même. Autrement dit, ils ne cesseront pas de fonctionner (ce qui serait une rupture de compatibilité ascendante), mais ils ne disposeront pas de toutes les fonctionnalités.

### Autorisation de com_ajax sur la page de connexion du backend

La page de connexion de l'administrateur autorise com_ajax dans l'AdministratorApplication pour qu'elle puisse être utilisée pour traiter les requêtes par les utilisateurs invités.

Ce changement ne cause aucun problème de compatibilité ascendante tant que les développeurs utilisent des pratiques sensées et ne supposent pas qu'être appelé par com_ajax dans le backend est une preuve que l'utilisateur est connecté au backend. Cela serait une mauvaise pratique de sécurité. La pratique raisonnable consiste à utiliser l'objet utilisateur de Joomla pour détecter s'il s'agit d'un utilisateur invité et si ce n'est pas le cas, vérifier si l'utilisateur dispose de l'autorisation requise pour effectuer l'action demandée via com_ajax. Autrement dit, si ce changement a cassé votre code, c'est que votre code était déjà défectueux et devait être retravaillé de toute façon.

## Informations complémentaires

La documentation initiale de cette fonctionnalité se trouve dans la demande de tirage à l'adresse suivante : [PR #28094](https://github.com/joomla/joomla-cms/pull/28094)

*Traduit par openai.com*

