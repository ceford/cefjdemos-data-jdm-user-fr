<!-- Filename: Semantic_HTML_Markup / Display title: Balises HTML sémantique -->

## HTML sémantique

### Qu'est-ce que le HTML sémantique ?

Le HTML sémantique est une façon d'utiliser le codage HTML pour créer ou
améliorer la structure d'une page. En d'autres termes, c'est une façon
d'utiliser le balisage HTML - les classes, les divs, les tags et ainsi
de suite - afin de compléter les mots ou ressources présents sur une
page. Cela aide les 'robots" et les visiteurs qui utilisent des lecteurs
d'écran à comprendre la structure et le contexte de l'information de la
page, ainsi que son importance, sa pertinence et la façon dont elle est
liée à d'autres ressources.

### Comment utiliser le balisage HTML sémantique

Il est important d'avoir une bonne compréhension du HTML sémantique si
vous développez des sites web ou rédigez du contenu web, puisque vous
aurez besoin d'utiliser régulièrement le balisage structurel.

On peut trouver un exemple de détournement du balisage sémantique
lorsqu'un article a été écrit en utilisant un texte normal, mais
l'auteur souhaite mettre en exergue une phrase. Il aime le style de la
balise H1, et de ce fait, applique cette balise H1 à la phrase en
question pour qu'elle soit 'plus jolie'. Malheureusement, c'est une
source de confusion pour un 'robot' de moteur de recherche et pour les
utilisateurs de lecteurs d'écran, car on leur indique que c'est le titre
principal de la page et non pas une simple mise en exergue d'un texte.

Le balisage HTML sémantique ne devrait être utilisé que pour structurer
une page uniquement - et non pas pour modifier son apparence (ce que se
fait à l'aide des feuilles de style en cascade (CSS) ou des styles
incorporés (inline))

### Un exemple de balisage HTML sémantique

A titre d'exemple, disons que nous avons un article :

    <h1>Utilisation des balises de titre</h1>
    <p>Ceci est un article sur l'importance des titres.</p>

    <h2>Pourquoi utiliser des balises de titre ?</h2>
    <p>Il est important d'utiliser des balises de titre afin d'indiquer aux robots des moteurs de recherche quelles sont les parties importantes de votre article.</p>

    <h3>Types de balise de titre</h3>
    <p>Vous pouvez utiliser un ensemble de balises de titre, mais elles doivent être ordonnées et structurées au sein de votre page. H1 doit correspondre au titre de votre page et H2 doit être utilisé pour les sous-titres de la page. Tous les titres contenus à l'intérieur de vos sous-titres doivent être ordonnancés avec H3, H4 et H5.</p>

    <h2>Est-il difficile d'implémenter les balises de titre ?</h2>
    <p>Rien de plus simple, il vous suffit d'utiliser le code HTML adéquat.</p>

    <h3>Utilisation des balises de titre sur des pages dynamiques</h3>
    <p>Sur des pages dynamiques, il suffit d'envelopper votre titre principal dans une balise H1 (par exemple, le titre d'une page de liste de catégories devrait être en H1) puis d'envelopper tous les titres suivants dans des balises H2.</p>

Ici, un 'robot' de moteur de recherche pourrait voir clairement la
structure - h1, h2, h3 - mais si nous avions simplement mis ces titres
en gras, soulignés ou avec une taille de police plus importante,
l'identification de la structure aurait été plus difficile. Il est
également possible d'identifier que le mot "importantes" est un mot mis
en exergue, ce qui signifie que c'est un élément important de la page.

Le HTML sémantique est également :

- Plus facile à lire (dans le code)
- Plus facile pour l'accessibilité - les lecteurs d'écran fonctionnent
  de façon similaire aux robots des moteurs de recherche pour identifier
  les principaux titres
- Potentiellement meilleur en optimisation pour les moteur de recherche

Dans l'exemple ci-dessous de résultats de recherche de Google, vous
pouvez voir comment les balises de titre sont utilisées par Google pour
identifier des liens secondaires contenus dans la page principale
pouvant être intéressant pour la personne effectuant une recherche sur
un terme (liens en bleu affichés sous la description). Une autre raison
de structurer correctement votre contenu !

<img src="https://docs.joomla.org/images/5/58/SEF-Titles.png"
decoding="async" data-file-width="532" data-file-height="105"
width="532" height="105" alt="SEF-Titles.png" />

### Microdonnées

Les microdonnées sont une forme plus avancée du balisage HTML sémantique
qui vous permet de donner encore plus d'informations contextuelles sur
le contenu et la structure de votre site web. Pour plus d'informations,
voir :
Microdonnées.

<a href="http://fr.wikipedia.org/wiki/HTML_s%C3%A9mantique"
class="extiw" title="fr.wp:HTML sémantique">Article Wikipédia sur le
HTML sémantique</a>
