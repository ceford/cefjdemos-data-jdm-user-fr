<!-- Filename: J4.x:Assorted_Issues / Display title: Divers Problèmes  -->

## Problème de redirection après la mise à niveau vers la version 4.0.6

C'est un bug ! Ligne 243 de *plugins/system/redirect/redirect.php* :

       $db->updateObject('#__redirect_links', $redirect, 'id');

devrait être

       $this->db->updateObject('#__redirect_links', $redirect, 'id');

## Une page s'affiche sans style

Cause possible : une section gzip dans le fichier *.htaccess* compresse les fichiers CSS et JavaScript déjà compressés.

Voir cette section du fichier *.htaccess* :

    ## Ces directives ne sont activées que si le module mod_headers d'Apache est activé.
    ## Cette section vérifiera si un fichier .gz existe et, le cas échéant, le diffusera
    ##     directement ou comprimera à la volée tout fichier.
    ## Si votre site commence à avoir un aspect étrange après avoir activé cela, et que vous voyez
    ##     ERR_CONTENT_DECODING_FAILED dans l'onglet réseau de la console de votre navigateur,
    ##     cela signifie que votre serveur compresse déjà les fichiers CSS et JavaScript et que vous n'avez pas besoin de ce bloc
    ##     activé dans votre fichier .htaccess

    ...

Si présent, commentez ou supprimez.  

## La liste des modules du site est vide

Cause possible : la taille du tampon de tri MySQL peut être trop petite.

En utilisant phpMyAdmin, allez à **Accueil**→**Variables**→**Taille du tampon de tri**.

Elle devrait être d'au moins 256K et de préférence 512K. Sur certains services d'hébergement partagé, elle peut être réglée à 128K. Demandez au service d'hébergement de l'augmenter.

## Échec de la mise à jour après la mise à niveau vers 4.0.4

Cause : un changement essentiel dans la procédure de mise à jour affectant un petit nombre d'utilisateurs.

Recherchez cette ligne dans *.htaccess* :

```plaintext
RewriteRule ^administrator/components/com_joomlaupdate/restore\.php$ - [L]
```

Changez-la en :

```plaintext
RewriteRule ^administrator\/components\/com_joomlaupdate\/extract\.php$ - [L]
```

Pour plus d'informations, consultez :

<a
href="https://www.joomla.org/announcements/release-news/5850-changes-to-update-process-that-you-need-to-be-aware-of.html"
rel="noreferrer noopener">Changements
dans le processus de mise à jour que vous devez connaître</a>

## Articles visibles dans la base de données et le frontend mais pas visibles dans le backend

Cela se produit lorsque des articles sont importés directement dans la base de données, ce qui fonctionnait bien dans Joomla 3 mais pas dans Joomla 4. La solution d'un utilisateur est la suivante :

    J'ai importé des articles directement dans la base de données dans la table #__content comme je le faisais souvent dans Joomla 3.
    Cependant, dans Joomla 4, ils n'étaient pas visibles.

    Dans Contenu > Catégories, les compteurs d'articles de la catégorie comptaient les articles importés.
    Mais ils n'étaient pas visibles dans Contenu > Articles.

    Je l'ai résolu en créant les références nécessaires dans la table #__workflow_associations pour chaque article importé :
    item_id = ID de l'article, stage_id = 1 et extension = com_content.article.

Avec cela d'un autre utilisateur :

Cette requête devrait vous aider. Remplacez \#\_\_ par votre propre préfixe de base de données.

Cette requête empêche les doublons dans la table des associations de workflow

    INSERT INTO #__workflow_associations (item_id, stage_id, extension)
    SELECT c.id as item_id, '1', 'com_content.article' FROM #__content AS c
    WHERE NOT EXISTS (SELECT wa.item_id FROM #__workflow_associations AS wa WHERE wa.item_id = c.id);

*Traduit par openai.com*

