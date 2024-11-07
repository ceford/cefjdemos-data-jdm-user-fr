<!-- Filename: https://magazine.joomla.org/all-issues/april-2021/best-practices-to-secure-your-joomla-website / Display title: Meilleures Pratiques  -->

## Articles de Sécurité

Il existe un nombre important d'articles disponibles sur la sécurité de Joomla datant de plusieurs années en arrière. Malheureusement, beaucoup d'entre eux ne sont plus à jour et sont peut-être trompeurs. Par exemple, il existe une série d'articles intitulée « Liste de Contrôle de Sécurité » qui ne sont pas tous réellement axés sur la sécurité.

Cet article est basé sur un article du Joomla! Community Magazine par Ahmad Moussa dans l'édition d'avril 2021.

## Bonnes pratiques pour sécuriser votre site web Joomla

Le système de gestion de contenu (CMS) Joomla est largement répandu sur Internet en raison de sa facilité d'utilisation et de sa popularité, étant le deuxième plus grand CMS téléchargé plus de 110 millions de fois. Mais, bien que populaire, Joomla, comme tous les autres sites web, applications, sites e-commerce ou autres CMS, comporte des risques de sécurité. Vous ne pouvez pas y échapper, mais heureusement, prendre les bonnes précautions dès le départ peut garantir la protection de votre site.

Nous avons compilé ce guide complet et étape par étape sur la sécurité Joomla pour vous. Il vise à fournir des étapes faciles à suivre pour améliorer la sécurité de votre site web Joomla. Donc, si sécuriser votre site Joomla contre toutes les attaques à venir est à votre ordre du jour, alors prenez le temps de le lire. Tous les conseils mentionnés dans cet article visent à vous assurer de mettre en œuvre les meilleures pratiques de sécurité et de maintenance pour protéger vos actifs les plus importants en ligne.

## 1. Choisissez des noms d'utilisateur et des mots de passe intelligents

Soyez prudent lors du choix de vos noms d'utilisateur et mots de passe pour l'administration de Joomla. N'utilisez pas "admin" comme nom d'utilisateur et choisissez un mot de passe complexe. C'est probablement l'une des meilleures façons de renforcer la sécurité de Joomla, et ironiquement, c'est l'une des plus simples.

Utiliser un mot de passe sécurisé est nécessaire pour une sécurité Joomla optimale. Assurez-vous que votre mot de passe de connexion est suffisamment long (8 à 14 caractères) et inclut des lettres, des chiffres et des symboles. Étant donné que les mots de passe sont sensibles à la casse, l'utilisation de lettres majuscules et minuscules le rend encore plus robuste. De plus, prenez l'habitude de changer les mots de passe administrateur au moins une fois par mois.

## 2. Pratiquez le principe du moindre privilège

Assurez-vous de bien comprendre les trois groupes de permissions distincts :

1. Managers : Ont le moins d'accès au backend de Joomla. Peuvent créer et modifier des catégories et des articles. Ont accès au gestionnaire de médias et peuvent télécharger et supprimer des médias. Ne peuvent pas installer ou supprimer des extensions.
2. Administrateurs : Ont tous les droits des Managers, ainsi que quelques permissions supplémentaires. Ont accès à la gestion des utilisateurs, au gestionnaire de menus et au gestionnaire d’extensions. Ne peuvent pas accéder au menu de configuration globale de Joomla.
3. Super Utilisateurs : Ont un accès complet au backend de Joomla. Ont tous les droits des Managers et des Administrateurs, ainsi que l'accès à la configuration globale. Seuls les Super Utilisateurs peuvent ajouter, modifier et supprimer des Super Utilisateurs.

Il est important de distribuer ces rôles soigneusement à votre groupe d'utilisateurs. Toute personne avec un rôle de Super Utilisateur est capable d'effectuer n'importe quelle action dans le système Joomla. Si vous déléguez des tâches à un membre de l'équipe qui nécessite moins de permissions, attribuez à son compte la description d'accès minimum.

## 3. Utiliser l'authentification multi-facteurs de Joomla

Il est fortement recommandé d'activer l'authentification multi-facteurs de Joomla, qui ajoute une couche supplémentaire de sécurité à votre site web Joomla. Traditionnellement, lorsque vous souhaitez vous connecter à votre site, vous devez fournir votre nom d'utilisateur et votre mot de passe afin de vous identifier dans le système. Le plus gros problème avec cette approche est que votre nom d'utilisateur et votre mot de passe peuvent être volés ou devinés. Par conséquent, les plugins d'authentification multi-facteurs de Joomla peuvent protéger votre site web des pirates en ajoutant une deuxième couche de sécurité. Il existe cinq méthodes différentes parmi lesquelles vous pouvez choisir après avoir entré votre nom d'utilisateur.

## 4. Restreindre l'accès au back-end administrateur de Joomla

Il est judicieux de limiter l'accès au back-end administrateur de Joomla en utilisant le filtrage IP, car c'est une ressource sensible. Cela peut également être fait pour d'autres dossiers sensibles de Joomla en suivant les étapes mentionnées ci-dessous :

Étape 1 : Commencez par créer un fichier .htaccess s'il n'est pas déjà présent dans le répertoire que vous souhaitez protéger.

Étape 2 : Ajoutez le code suivant au fichier .htaccess :
   ```
   Order Deny, Allow
   Deny from all
   Allow from xx.xx.xx.xx
   ```

Étape 3 : Remplacez xx.xx.xx.xx par l'adresse IP dédiée à partir de laquelle vous souhaitez autoriser l'accès.

Plus d'informations sur la restriction de l'accès aux répertoires par adresse IP en utilisant htaccess peuvent être trouvées dans cet article de la documentation de Joomla! Vous pouvez également utiliser des extensions de sécurité qui peuvent restreindre l'accès au back-end administrateur de Joomla en utilisant la fonction de filtrage IP et inclurent de nombreuses autres fonctionnalités qui renforcent la sécurité de votre site Joomla.

## 5. Utilisez des connexions FTP sécurisées

Assurez-vous que les connexions utilisées pour accéder aux fichiers de votre site web Joomla sont sécurisées. Vous devriez utiliser le chiffrement SFTP si votre hébergement le fournit, ou SSH. Si vous utilisez un client FTP, le port par défaut pour SFTP est généralement 22.

Certains clients FTP stockent les mots de passe en texte clair ou encodé sur votre ordinateur. Même certains mots de passe encodés peuvent être convertis à leur forme originale. Nous recommandons fortement de ne pas enregistrer les mots de passe FTP dans le client pour éviter d'être piraté.

## 6. Effectuer des Sauvegardes Régulières

Gagnez du temps en vous préparant au pire des scénarios dans le cas où votre site web serait attaqué. Il est donc conseillé de créer une sauvegarde complète et fonctionnelle de votre site Joomla. Une sauvegarde fonctionnelle peut restaurer votre site en quelques minutes après une cyberattaque.

Les deux principaux composants d'une sauvegarde sont :

- Le cœur de Joomla et d'autres fichiers importants
- La base de données

De plus, les méthodes de sauvegarde peuvent également être flexibles. Vous pouvez effectuer une sauvegarde de deux manières : Manuellement et Automatiquement, comme décrit ci-dessous :

### Processus Manuel

La sauvegarde manuelle du site Joomla nécessite deux composants : les fichiers et la base de données. Pour sauvegarder vos fichiers et dossiers Joomla, utilisez un utilitaire FTP ou le gestionnaire de fichiers si vous utilisez un hébergement tiers.

Les clients FTP peuvent télécharger tous les fichiers un par un sur votre machine locale. Cependant, ce processus peut être lent. Une fois les fichiers téléchargés, compressez le dossier en un seul fichier zip puis protégez-le par un mot de passe.

Quant à la base de données, elle peut être sauvegardée en exportant une copie de la base de données sur votre ordinateur. Connectez-vous à la base de données que vous souhaitez exporter en utilisant phpMyAdmin. Cliquez sur le nom de la base de données sur le côté gauche de la page. Une fois que vous avez cliqué sur votre base de données Joomla, vous devriez arriver à un écran avec un onglet intitulé “Export”. Sélectionnez l'onglet Export puis cliquez sur le bouton intitulé "Go". Ensuite, enregistrez-le dans un emplacement sécurisé.

### Processus Automatisé

Pour une sauvegarde automatisée, une extension Joomla comme Akeeba Backup peut vous aider. Installez l'extension Akeeba Backup sur votre site Joomla après l'avoir téléchargée depuis le site officiel du développeur. Une fois l'installation terminée, accédez au tableau de bord de l'extension puis sauvegardez votre site. Lorsque la sauvegarde est terminée, vous serez redirigé vers une page. Ici, cliquez sur “Gérer les Sauvegardes”. Cela ouvrira une page contenant toutes les sauvegardes. Vous pouvez télécharger la sauvegarde à partir d'ici et l'enregistrer localement.

## 7. Maintenez votre site Joomla à jour

Mettre à jour votre site Joomla peut assurer la sécurité et la stabilité du site. De plus, toutes les mises à jour ne sont pas des mises à jour de la version complète du site ; certaines mises à jour peuvent être mineures et ne concerner que des corrections de bugs, tandis que d'autres sont des mises à jour de version.

Joomla dispose d'une équipe de sécurité dédiée, connue pour déployer rapidement des correctifs. Ne pas corriger votre site Joomla peut le rendre vulnérable aux piratages.

Pour vérifier les mises à jour de votre site, vous pouvez faire ce qui suit :

Étape 1 : Connectez-vous à votre site Joomla en tant qu'administrateur

Étape 2 : Ensuite, accédez à Composants>Mise à jour de Joomla

Étape 3 : Joomla vérifiera maintenant si une nouvelle mise à jour est disponible. Si une nouvelle mise à jour est affichée, cliquez simplement sur l'option "Installer la mise à jour".

Avant de mettre à jour vers une nouvelle version de Joomla, certaines vérifications doivent être effectuées :

- Mise à jour des modèles : Vérifiez si vos modèles Joomla sont compatibles avec la nouvelle version de Joomla. Sinon, demandez à l'auteur du modèle de le mettre à jour ou utilisez une alternative.
- Mise à jour des extensions : Inspectez et assurez-vous que toutes les extensions Joomla sont compatibles avec la nouvelle version de Joomla. Supprimez toutes celles qui ne sont pas compatibles. Pour mettre à jour les extensions, accédez à Extensions>Gérer et cliquez sur mise à jour.
- Vider le cache : Après la mise à jour vers une nouvelle version de Joomla, videz le cache de votre site Joomla. Cela peut être fait à l'aide de la fonctionnalité intégrée de Joomla.

## 8. Utilisez des extensions et modèles tiers de confiance :

Il est recommandé d'utiliser un nombre minimum d'extensions sur votre site web pour obtenir le niveau de sécurité optimal de Joomla. L'utilisation d'extensions ou de modèles tiers non fiables peut présenter des vulnérabilités et affecter les performances de votre site Joomla. Toutes les extensions tierces ne sont pas gratuites et dénuées de problèmes; si vous avez la possibilité d'éviter une extension tierce, faites-le ! Choisissez et utilisez des extensions et modèles professionnels provenant d'entreprises réputées, et maintenez-les à jour pour protéger votre site web.

## 9. Mettre à jour la version PHP de votre site Joomla

Protégez votre site contre diverses attaques de piratage et renforcez la sécurité de votre site Joomla en mettant à jour la version PHP de votre site vers la dernière version stable. Assurez-vous de sélectionner une version PHP compatible avec vos modèles et extensions Joomla pour éviter de casser votre site. Il existe plusieurs façons de mettre à jour votre version PHP. Les principales sont couvertes dans un article du numéro de septembre 2020 de Joomla Community Magazine : Comment mettre à jour ma version PHP ?.

## 10. Renforcez les En-têtes de Sécurité HTTP

Il est fortement recommandé de mettre en œuvre ou de mettre à jour les en-têtes de sécurité HTTP, car ils offrent une couche de sécurité supplémentaire pour votre site Joomla en aidant à atténuer les attaques et les vulnérabilités de sécurité. Ces en-têtes ne nécessitent généralement qu'un petit changement de configuration sur votre serveur web. Ils indiquent à votre navigateur comment se comporter lors du traitement du contenu de votre site. Voici six en-têtes de sécurité HTTP courants à examiner :

- Politique de sécurité du contenu (Content-Security Policy)
- Protection X-XSS (X-XSS-Protection)
- Sécurité stricte des transports (Strict-Transport-Security)
- Options de cadre X (X-Frame-Options)
- Clés publiques (Public-Key-Pins)
- Type de contenu X (X-Content-Type)

## 11. Utilisez une extension de sécurité Joomla

Il est nécessaire de limiter les tentatives de connexion sur l'interface d'administration de Joomla pour éviter les attaques par force brute sur votre site Joomla. Cela peut être mis en œuvre par diverses extensions de sécurité Joomla qui protègent l'interface d'administration de votre site contre les tentatives de piratage. Vous pouvez trouver ces extensions dans la catégorie de la liste des extensions de sécurité Joomla.

## 12. Choisissez un Fournisseur d'Hébergement Sécurisé

Assurez-vous que le fournisseur d'hébergement que vous choisissez applique des mesures de sécurité pour Joomla. Si vous optez pour un hébergement partagé, assurez-vous que le subnetting est mis en œuvre en tenant compte de la sécurité de Joomla. Acheter un hébergement partagé à bas prix peut ne pas être une solution idéale, car votre site sera plus lent, sujet aux spams en raison d'un « mauvais voisinage » de sites ayant une faible réputation, et pourrait être compromis si d'autres sites sont piratés. De plus, lors du choix d'un plan d'hébergement, vérifiez divers paramètres tels que la personnalisation, le support, les avis, etc.

## 13. Utilisez SSL pour Renforcer la Sécurité de Joomla

Il est fortement recommandé d'installer un certificat SSL (Secure Socket Layer) sur votre site web, car il chiffrera la communication entre votre site Joomla et les navigateurs de vos visiteurs. Obtenez un certificat SSL auprès d'une autorité de certification vérifiée et assurez-vous que tout votre trafic HTTP est redirigé vers HTTPS. Pour ce faire, ajoutez le code suivant à votre fichier .htaccess :

```
# Redirection de HTTP vers HTTPS
RewriteEngine On RewriteCond %{HTTPS} off
RewriteCond %{HTTP:X-Forwarded-Proto} !https
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

## 14. Audit de sécurité Joomla fréquente

Il est extrêmement important de découvrir les vulnérabilités avant qu'un pirate ne le fasse afin de garder votre site Joomla sûr et sécurisé. Cela peut être réalisé en choisissant un outil d'audit de sécurité professionnel qui peut vous faire économiser beaucoup de temps dans la gestion de vos sites web. Des audits de sécurité méticuleux sont un excellent moyen d'améliorer la sécurité de Joomla. De nombreux services le font en automatisant des tâches telles que la création de sauvegardes du site, la détection de signes d'intrusion et la mise à jour en masse des extensions de confiance. Ils peuvent également analyser votre site pour vérifier l'utilisation des meilleures pratiques de sécurité et effectuer une analyse approfondie pour rechercher les menaces potentielles. Ces services utilisent un mélange optimisé de mécanismes manuels et automatisés pour découvrir les vulnérabilités de votre site Joomla.

## 15. Vérifier les messages post-installation

Il est fortement recommandé de lire tous les messages post-installation, car l'équipe Joomla vous fournit des informations importantes qui nécessitent votre attention après la mise à niveau ou après l'installation de Joomla pour la première fois. Ces messages contiennent principalement des configurations de sécurité Joomla ou des modifications de fichiers qui doivent être effectuées manuellement et qu'une mise à niveau ne peut pas modifier.

## 16. Apprenez à connaître les extensions vulnérables

Consultez toujours le site Web de la liste des extensions vulnérables et ses pages sur les réseaux sociaux afin de connaître les derniers risques de sécurité et les correctifs possibles. Il est recommandé de désinstaller toute extension figurant dans la liste des extensions vulnérables pour laquelle aucun correctif n’est connu. Assurez-vous de mettre à jour votre extension vulnérable dès que son correctif est disponible. Si votre site utilise une version vulnérable d'une extension qui n’a pas de mise à jour de correctif, il est alors recommandé de la remplacer.

## Conclusion

Étant donné qu'il y aura toujours des risques, la sécurité de Joomla restera un processus continu nécessitant une évaluation fréquente des vecteurs d'attaque possibles. Les propriétaires et administrateurs de sites Web devraient constamment améliorer la sécurité de leur site afin de réduire le risque de compromis.

*Traduit par openai.com*

