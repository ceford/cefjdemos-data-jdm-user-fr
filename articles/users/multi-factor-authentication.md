<!-- Filename: J4.x:Multi-factor_Authentication / Display title: Authentification Multi-facteurs  -->

## Introduction

Le système d'authentification multifacteur de Joomla! est basé sur Akeeba Loginguard et une grande partie de cette documentation a été dérivée avec la permission d'Akeeba.

## Que fait-il ?

Il ajoute plusieurs méthodes optionnelles de vérification en deux étapes pour la connexion Joomla! Après vous être connecté avec seulement votre nom d'utilisateur et mot de passe, on vous demande de fournir votre seconde vérification, par exemple un code généré par Google Authenticator. Tant que vous ne fournissez pas une seconde vérification correcte, vous ne pourrez accéder à aucune page du site. Vous serez toujours redirigé vers la page "connexion captive". Cela est similaire à ce que fait Google lorsque vous essayez de vous connecter à GMail.

Cela diffère de la méthode originale d'authentification à deux facteurs Joomla! qui nécessitait que le second facteur d'authentification (par exemple, le code généré par Google Authenticator) soit saisi conjointement avec le nom d'utilisateur et le mot de passe.

Les avantages de la vérification en deux étapes sont :

- C'est moins déroutant pour l'utilisateur. Il n'est plus nécessaire d'avoir le champ "Clé secrète" qui embrouille les utilisateurs.
- Il peut fonctionner avec des méthodes de connexion sans mot de passe telles que la connexion sociale (par exemple, Facebook), le jeton matériel sécurisé, SSO (authentification unique), etc.
  Clarification : La vérification en deux étapes peut être configurée pour être demandée après qu'un utilisateur se soit connecté avec une méthode de connexion sans mot de passe. Elle ne met pas en œuvre de méthodes de connexion sans mot de passe.
- Il offre un meilleur contrôle d'accès. Vous pouvez définir les Options de l'utilisateur pour Exiger ou Désactiver l'authentification multi-facteurs par groupe d'utilisateurs.
- Il permet des méthodes d'authentification alternatives dans un seul compte. Vous pouvez avoir plusieurs méthodes d'authentification sur votre compte. Par exemple, vous pouvez configurer une application Google Authenticator et une YubiKey.
- Il prend en charge les méthodes qui ne nécessitent pas l'entrée d'un code. Par exemple les clés FIDO2, la vérification biométrique, etc. Celles-ci doivent interagir avec le navigateur et/ou le système d'exploitation via les API HTML5 natives.
- Il prend en charge les méthodes nécessitant une interaction de l'utilisateur. Par exemple, l'envoi d'un code par message push, SMS ou e-mail. Ces méthodes nécessitent de savoir quel utilisateur est en train d'être authentifié avant de pousser le code d'authentification à l'utilisateur.
- C'est gratuit. Contrairement aux services tiers fournissant une authentification multi-facteurs, vous n'avez pas à payer de frais de mise en place initiaux ni de frais de maintenance mensuels ou annuels pour chaque site ou utilisateur utilisant la vérification en deux étapes. Le logiciel est gratuit.

## Comment ça marche

Vous vous connectez à votre site normalement, par exemple en fournissant un nom d'utilisateur et un mot de passe. Il est important de noter que vous n'avez pas besoin de saisir vos informations d'authentification de second niveau à cette étape.

Le système détecte que vous êtes maintenant connecté mais que vous n'avez pas effectué l'authentification de second niveau. Il enregistre l'URL que vous étiez censé voir et vous redirige immédiatement vers la page de connexion captive. Toute tentative de navigation vers une autre page entraînera l'apparition de la page captive.

Les modules de votre site peuvent contenir des informations sensibles. Pour garantir la confidentialité, les modules sont désactivés de force lors de l'affichage. Cela signifie qu'aucune position de module ne sera rendue sur la page. N'oubliez pas que si vous remarquez que l'en-tête ou d'autres zones clés du design de votre site manquent sur la page de connexion captive.

Notez que les plugins, en revanche, ne sont PAS désactivés. Cela est dû au fait que Joomla rend extrêmement difficile la suppression de plugins spécifiques une fois qu'ils sont chargés, et que la plupart des plugins assurent des fonctionnalités essentielles sur votre site.

Après avoir fourni votre vérification de second niveau, un drapeau est défini dans la session utilisateur, indiquant que vous êtes pleinement autorisé à utiliser le site. De plus, vous serez redirigé vers l'URL qu'il avait enregistrée juste après votre connexion initiale.

## Authentification à deux facteurs versus connexions WebAuthn

Se connecter avec WebAuthn est l'option la plus sécurisée. Vous ne fournissez qu'un nom d'utilisateur qui est censé être considéré comme une information publique et non privilégiée. Le site crée un défi cryptographique qui est signé par le navigateur en utilisant un matériel sécurisé — un jeton de sécurité matériel externe ou le Trusted Platform Module / Secure Enclave de votre appareil — et renvoyé au serveur. Le serveur valide la signature. Cette validation utilise la cryptographie à clé publique avec le site ne stockant que la clé publique. Cela rend la connexion virtuellement infalsifiable et extrêmement sécurisée. Si vous utilisez cela, vous n'avez pas besoin d'un second facteur d'authentification — mais si vous le souhaitez vraiment, vous pouvez également utiliser WebAuthn pour ce faire.

En excluant l'utilisation de méthodes de connexion fédérées (comme se connecter avec votre compte de réseau social, un service de Single Sign-On, un serveur LDAP, etc.), une connexion conventionnelle avec un nom d'utilisateur + mot de passe n'est nulle part aussi sécurisée qu'une connexion WebAuthn. Entrer un nom d'utilisateur et un mot de passe peut être intercepté, volé ou deviné. Cela rend la confiance en un simple nom d'utilisateur et un mot de passe très problématique.

Pour l'authentification multifactorielle, vous ne fournissez que votre nom d'utilisateur et votre mot de passe. Une attaque de phishing réussie n'obtiendrait que ce premier facteur d'authentification mais pas votre second facteur d'authentification. Après une connexion réussie, vous êtes présenté avec une page captive. Vous ne pouvez rien faire d'autre sur le site tant que vous n'avez pas fourni votre second facteur. Étant donné que la saisie du second facteur est présentée sur sa propre page, elle peut être interactive (par exemple WebAuthn), asynchrone (par exemple réception d'un OTP par e-mail, message texte ou notification push) ou initiée par l'utilisateur (par exemple un TOTP ou un OTP Yubikey). Encore mieux, un utilisateur peut avoir plusieurs méthodes de second facteur activées sur son compte pour éviter des verrouillages accidentels du site. Par exemple, vous pouvez utiliser WebAuthn avec une clé de sécurité matérielle externe comme votre second facteur principal, le plus sécurisé. Vous pourriez également avoir un TOTP régulier configuré au cas où vous perdriez la clé ou oublieriez de l'emporter avec vous. Certaines méthodes de second facteur permettent plusieurs instances, par exemple, vous pouvez avoir plusieurs authentificateurs WebAuthn pour pouvoir utiliser l'authentificateur intégré dans votre ordinateur Windows, votre iPhone et votre tablette Android sans avoir à vous rappeler d'emporter une clé matérielle et des adaptateurs chaque fois que vous quittez votre bureau.

Récapitulons. Du plus sécurisé au moins sécurisé, vos options sont :

- WebAuthn comme méthode de connexion principale avec authentification multifactorielle secondaire.
- WebAuthn comme votre seule méthode de connexion.
- Nom d'utilisateur et mot de passe comme méthode de connexion principale avec authentification multifactorielle secondaire.
- Juste un nom d'utilisateur et un mot de passe comme votre seule méthode de connexion.

## Plugins

Chacun des facteurs de l'authentification multifactorielle est mis en œuvre via des plugins. Ils peuvent être activés ou désactivés selon les besoins. De nouveaux plugins peuvent être ajoutés lorsque de nouvelles méthodes apparaissent. Les plugins intégrés au noyau de Joomla incluent :

- **Code de vérification** : codes de vérification à six chiffres générés par une application d'authentification (Google Authenticator, Authy, LastPass Authenticator, etc.), un gestionnaire de mots de passe (1Password, BitWarden, Keeper, KeePassXC, Strongbox, etc.) ou, dans certains cas, leur navigateur.
- **YubiKey** : permet aux utilisateurs de votre site d'utiliser l'authentification multifactorielle en utilisant un token matériel sécurisé YubiKey. Les utilisateurs ont besoin de leur propre YubiKey disponible sur www.yubico.com.
- **Authentification Web** : prise en charge par tous les navigateurs modernes. La plupart des navigateurs offrent une authentification spécifique à l'appareil protégée par un mot de passe et/ou des données biométriques (capteur d'empreintes digitales, reconnaissance faciale, ...).
- **Code d'authentification par email** : utilisez des codes de sécurité à six chiffres, limités dans le temps, envoyés par email. Le paramètre par défaut est de 2 minutes.
- **Code fixe** : il est destiné aux tests et à l'illustration et est désactivé par défaut. Il ne doit pas être activé sur un site en production.

Notez qu'il existe un plugin séparé **Système - Connexion WebAuthn sans mot de passe** pour gérer la connexion à partir du bouton d'authentification Web dans le formulaire de connexion.

## Options des Utilisateurs

Le formulaire Options des Utilisateurs inclut un formulaire d'Authentification à Facteurs Multiples pour configurer le fonctionnement de l'authentification à facteurs multiples dans Joomla. Sélectionnez le bouton Basculer l'Aide En Ligne pour obtenir des informations sur chaque option.

![formulaire d'authentification à facteurs multiples des options des utilisateurs](../../../en/images/users/users-configuration-mfa.png)

## Profil Utilisateur

Le formulaire Administrateur / Utilisateurs : Modifier le Profil a des onglets séparés pour la Connexion WebAuthn et l'Authentification à Plusieurs Facteurs, mais ce dernier n'est visible que par le propriétaire du compte. Même les Super Utilisateurs ne voient pas cet onglet pour les autres utilisateurs.

Le formulaire Site / Modifier Votre Profil dispose des onglets de formulaire backend disposés l'un au-dessus de l'autre, ce qui peut être déroutant car l'Authentification Web apparaît deux fois, d'abord pour la connexion sans mot de passe et ensuite pour l'Authentification Multi-Facteurs. L'illustration suivante montre la partie du formulaire concernant l'Authentification à Plusieurs Facteurs après qu'une méthode a été créée. Cela active automatiquement la fonctionnalité et affiche l'option de créer des Codes de Secours.

![vue du site du formulaire d'authentification multi-facteurs de l'utilisateur](../../../en/images/users/multi-factor-authentication-site-profile.jpg)

Comme mentionné ci-dessus, vous pouvez essayer chacun en sélectionnant le bouton + Ajouter ..., mais sélectionnez Annuler dans le formulaire suivant si vous décidez de ne pas continuer.

*Traduit par openai.com*

