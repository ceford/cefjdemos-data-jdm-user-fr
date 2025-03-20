<!-- Filename: J5.x:Schema_org / Display title: Introduction aux schémas -->

## Extraits Enrichis

Les extraits enrichis (également connus sous le nom de *résultats enrichis*) sont des résultats de recherche Google normaux avec des données supplémentaires affichées. Ces données supplémentaires sont généralement compilées à partir de données structurées trouvées dans le HTML d'une page. Les types courants d'extraits enrichis incluent les avis, les recettes et les événements. Les extraits enrichis peuvent aider les sites Web à se démarquer dans les résultats de recherche, à attirer plus de clics et à fournir aux utilisateurs une meilleure compréhension du contenu avant qu'ils ne cliquent.

Joomla implémente les Rich Snippets en utilisant JSON-LD. Il s'agit d'une notation JavaScript intégrée dans une balise `<script>` dans l'élément `<head>` d'une page HTML. Le balisage n'est pas intercalé avec le texte visible par l'utilisateur. Le contenu des extraits est saisi dans des champs de formulaire implémentés avec des plugins.

## Schema.org

>Schema.org est une activité collaborative et communautaire ayant pour mission de créer, maintenir et promouvoir des schémas pour les données structurées sur Internet, sur les pages web, dans les messages électroniques, et au-delà.

Les données structurées sont un format standardisé pour organiser et représenter l'information sur le web. Elles fournissent un moyen de décrire le contenu et la signification des données d'une manière structurée, facilitant ainsi la compréhension et le traitement de l'information par les moteurs de recherche et d'autres applications. Il y a plus d'informations détaillées sur le [site de Schema.org](https://schema.org/).

## Mise en œuvre de Joomla

Dans Joomla, les extraits enrichis sont générés en utilisant un balisage de données structurées basé sur les schémas Schema.org. Chaque type de schéma est implémenté sous forme de plugin séparé. Cela permet une architecture plus modulaire et extensible. Chaque plugin est responsable de la génération du balisage de schéma pour un type de contenu spécifique, ce qui offre plus de souplesse et d'options de personnalisation. Cela facilite la contribution des développeurs tiers au développement des capacités de données structurées de Joomla.

Pour commencer, allez à **Système -> Plugins** et activez le plugin *Système - Schema.org*. Si ce plugin n'est pas activé, il n'y aura pas d'onglet Schéma dans un formulaire de modification d'article même si tous les plugins individuels sont activés.

![List of schema plugins](../../../en/images/schemas/schema-plugins-list.png)

### Modifier le système - Plugin Schema.org

- **Type de base** Choisissez si votre site web représente une organisation ou une personne seule.
- **Nom** Entrez le nom de l'organisation ou de la personne que le site web représente.
- **Image** Ajoutez l'image de votre entreprise ou personnelle
- **Comptes de médias sociaux** Ajoutez les comptes de médias sociaux de votre entreprise ou personnels. Sélectionnez le bouton vert avec signe plus pour ajouter des lignes au formulaire.
- Sélectionnez **Enregistrer et fermer**.

![edit system schema org plugin](../../../en/images/schemas/edit-system-schema-org-plugin.png)

### Modifier un article

Allez dans l'un de vos articles et remplissez les champs du formulaire de schéma. Si le *Type de schéma* est défini sur *Aucun*, valeur par défaut, il n'y a pas de champs à remplir. Sélectionnez un schéma pour voir une liste de champs appropriés pour ce schéma. La capture d'écran suivante montre un article avec le schéma Article sélectionné :

![edit article scheme form](../../../en/images/schemas/schema-form-in-an-article.png)

### Sortie

Vous ne verrez rien lié au schéma sur la page web. Cependant, si vous regardez le code source de la page, vous verrez une entrée de script, comme dans l'exemple suivant :

```json
	<script type="application/ld+json">{
    "@context": "https://schema.org",
    "@graph": [
        {
            "@type": "Organization",
            "@id": "http://localhost/jcms-testing/#/schema/Organization/base",
            "name": "Joomla Documentation Team",
            "url": "http://localhost/jcms-testing/"
        },
        {
            "@type": "WebSite",
            "@id": "http://localhost/jcms-testing/#/schema/WebSite/base",
            "url": "http://localhost/jcms-testing/",
            "name": "JCMS Testing",
            "publisher": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            }
        },
        {
            "@type": "WebPage",
            "@id": "http://localhost/jcms-testing/#/schema/WebPage/base",
            "url": "http://localhost/jcms-testing/index.php/en/article-en-gb",
            "name": "Article (en-gb)",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebSite/base"
            },
            "about": {
                "@id": "http://localhost/jcms-testing/#/schema/Organization/base"
            },
            "inLanguage": "en-GB",
            "breadcrumb": {
                "@id": "http://localhost/jcms-testing/#/schema/BreadcrumbList/139"
            }
        },
        {
            "@type": "Article",
            "headline": "Article Schema Test",
            "description": "Latin text used to simulate layouts.",
            "author": {
                "@type": "person",
                "name": "Superman"
            },
            "@id": "http://localhost/jcms-testing/#/schema/com_content/article/1",
            "isPartOf": {
                "@id": "http://localhost/jcms-testing/#/schema/WebPage/base"
            }
        }
    ]
}</script>
```

Vous pouvez tester vos données structurées via la page [Testez vos données structurées](https://developers.google.com/search/docs/appearance/structured-data) de Google.

## Plugins disponibles

| Plugin | Description |
|--------|-------------|
| Plugin d'article | Le point de départ pour utiliser schema.org |
| Plugin de Blog | Pour le contenu des articles de blog |
| Plugin de Livre | Pour le contenu des livres |
| Plugin personnalisé | Pour l'entrée directe de code JSON-LD |
| Plugin d'événement | Pour le contenu des événements |
| Plugin d'offre d'emploi | Pour le contenu des offres d'emploi |
| Plugin d'organisation | Pour le contenu des entreprises et organisations |
| Plugin de personne | Pour le contenu des personnes |
| Plugin de recette | Pour le contenu des recettes |

*Traduit par openai.com*

