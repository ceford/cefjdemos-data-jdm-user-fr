<!-- Filename: Content_editors / Display title: Éditeurs de contenu  -->

## Introduction

Joomla a deux éditeurs par défaut décrits dans des articles distincts :

- [TinyMCE](jdocmanual?article=user/editors/tinymce-plugin) est l'éditeur par 
  défaut.
- [CodeMirror](jdocmanual?article=user/editors/codemirror-plugin) est conçu 
  pour éditer le code source brut en HTML et PHP.

## Aucun éditeur

Si *Éditeur - Aucun* est sélectionné dans un profil utilisateur, alors tous les champs de zone de texte requièrent l'entrée de balises HTML dans les champs qui en ont besoin. Cela est peu pratique pour modifier le contenu d'un article ou d'un module personnalisé, mais cela peut être utile dans certaines circonstances, par exemple, pour créer un lien PayPal. Dans un article, vous pouvez utiliser le bouton *Aperçu* de la barre d'outils pour voir comment le HTML s'affichera une fois rendu.

TinyMCE reformate automatiquement et supprime certaines balises HTML lorsqu'un fichier est enregistré. Cela peut entraîner un dysfonctionnement du HTML complexe. Si cela se produit, vous pouvez temporairement changer l'éditeur en *Éditeur - Aucun* pour créer le contenu souhaité. Notez que si vous souhaitez modifier ce contenu à l'avenir, vous devrez vous assurer de sélectionner à nouveau *Éditeur - Aucun*. Sinon, si vous ouvrez et enregistrez le contenu avec TinyMCE, vous risquez de perdre votre HTML personnalisé.

