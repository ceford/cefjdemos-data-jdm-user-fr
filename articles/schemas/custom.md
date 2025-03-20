<!-- Filename: Localhost / Display title: Schema.org - Personnalisé -->

## Objectif

Le plugin de schéma personnalisé est utilisé pour saisir des informations personnalisées au format JSON-LD brut. Ce n'est pas un type de Schema Org.

Ouvrez un formulaire d'édition d'article et sélectionnez l'onglet Schéma pour choisir un type de schéma et définir les données pour ce type. Si un type de schéma n'est pas présent dans la liste, il se peut que son plugin soit désactivé. Les valeurs à saisir dans chaque champ sont généralement évidentes.

Voici un exemple d'extrait enrichi fait main :

```json
{
  "@context": "https://schema.org",
  "@type": "WebPage",
  "name": "Your Article Title",
  "description": "A brief description of the article.",
  "timeRequired": "PT5M"
}
```

La propriété *timeRequired* représente le temps de lecture estimé au format de durée ISO 8601. Dans ce cas, PT5M signifie *5 minutes*.

## Exemple de capture d'écran

Voici un exemple de champ de schéma personnalisé dans un formulaire de modification d'article.

![A custom schema edit form](../../../en/images/schemas/edit-schema-custom.png)

*Traduit par openai.com*

