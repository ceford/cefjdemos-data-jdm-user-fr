<!-- Filename: J4.x:Module_Positions / Display title: Positions des modules -->

## Introduction

Les positions des modules de modèle sont définies dans un fichier templateDetails.xml et utilisées dans un fichier index.php de modèle. Plusieurs modules peuvent être assignés à une seule position, de sorte qu'il est rare de devoir créer plus de positions. Si vous souhaitez avoir plus de positions, vous devrez créer votre propre modèle, ce qui n'est pas abordé ici.

## Aperçu des positions de module

Il existe une option de modèle qui vous permet de voir les emplacements des modules dans les modèles de Site et d'Administrateur, y compris les positions qui n'ont pas de modules assignés. Pour activer cette fonctionnalité :

- Sélectionnez **Système** → **Modèles de site** dans le menu Administrateur.
- Sélectionnez le bouton `Options` dans la barre d'outils.
- Dans le formulaire Options du Modèle, réglez **Aperçu des positions de module** sur **Activé**.
- Enregistrez et fermez.

Pour voir les positions des modules, vous devez ajouter soit ?tp=1, soit &tp=1 à l'URL.

- Si l'URL ne contient pas de point d'interrogation, ajoutez ?tp=1.
- Si l'URL contient déjà un point d'interrogation, ajoutez &tp=1.

### Positions du modèle Administrateur Atum

![positions des modèles atum](../../../en/images/modules/template-positions-templates-page.png)

### Positions du modèle de site Cassiopeia

![positions des modèles cassiopeia](../../../en/images/modules/template-positions-site-page.png)

Vous pouvez également trouver ce schéma des positions des modules utile :

![schéma des positions du modèle cassiopeia](../../../en/images/modules/cassiopeia-template-positions.png)

## Sites de Production

N'oubliez pas de changer **Aperçu des Positions des Modules** à **Désactivé** sur les sites de production.

*Traduit par openai.com*

