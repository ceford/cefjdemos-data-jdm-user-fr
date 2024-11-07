<!-- Filename: Search_Engine_Friendly_URLs / Display title: URL conviviales pour les moteurs de recherche  -->

## Chemins et Itinéraires

Les URL SEF ont du sens à la fois pour les humains et pour les moteurs de recherche car elles expliquent le chemin vers la page spécifique à laquelle elles pointent. Un **chemin** est l'emplacement d'un fichier dans un arbre de répertoires ou sa simulation dans le code. En interne, la partie locale d'une URL SEF (la partie après le nom de domaine) est appelée un **itinéraire**. La création et le traitement des URL SEF sont donc appelés **routage**, et le code correspondant est appelé un **routeur**.

Les URL conviviales pour les moteurs de recherche peuvent être activées en suivant les étapes suivantes :
* Dans la **Configuration globale**
  - réglez l'option **URL conviviales pour les moteurs de recherche** sur **Oui**.
  - Réglez l'option **Utiliser la réécriture d'URL** sur **Oui**
  - Optionnel : Réglez l'option **Ajouter un suffixe à l'URL** sur **Oui**.
* À la racine du site, renommez htaccess.txt en .htaccess si vous utilisez un serveur Apache, ou consultez la documentation externe pour NginX ou d'autres serveurs.

Un exemple de routage peut être vu dans l'effet progressif de ces changements sur l'URL de la page Blog de la catégorie **Articles** dans les données d'exemple.

- Avec les URL SEF désactivées dans la Configuration globale et .htaccess désactivé, l'URL est quelque chose comme `https://www.example.com/index.php?option=com_content&view=category&layout=blog&id=16&Itemid=125` et le fil d'Ariane montre :<br>
 *Vous êtes ici : Accueil / Modèles d'exemple / Articles*
- Avec les URL SEF activées mais sans réécriture d'URL, cela devient :
  `https://www.example.com/index.php/sample-layouts/articles`
- Avec à la fois les URL SEF activées, la réécriture d'URL activée et .htaccess activé, cela devient
  `https://www.example.com/sample-layouts/articles.html` (Ajouter le suffixe à l'URL réglé sur Oui).

## Numéros dans les URL non-SEF

Dans la partie de l'URL qui indique `id=16&Itemid=125`, les chiffres sont les paramètres nécessaires pour localiser l'URL interne et afficher la page demandée. Dans ce cas, le premier chiffre est l'ID d'une catégorie et le second chiffre est l'ID de l'élément de menu Blog de la Catégorie pour cette catégorie.

*Traduit par openai.com*

