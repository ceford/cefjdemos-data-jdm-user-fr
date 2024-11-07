<!-- Filename: jdocmanual?manual=user&heading=performance&filename=accessibility-checker.md / Display title: Vérificateur d'accessibilité  -->

## Système - Vérificateur d'accessibilité Joomla

Il s'agit d'un plugin de base qui peut être utilisé pour vérifier l'accessibilité lors de la création de contenu d'articles. La capture d'écran suivante montre certains paramètres du plugin :

![Paramètres du formulaire du plugin](../../../en/images/performance/performance-jooa11y-plugin-form.png "Paramètres du plugin")

Avec l'option **Afficher Toujours** définie sur *Activé*, l'icône de rapport apparaît sur chaque page du site. Cela est utile pour le développement mais ne devrait jamais être laissé activé pour un site en ligne. Réglez-la sur **Désactivé** !

Avec l'option *Afficher Toujours* définie sur *Activé*, chaque page du site a une icône en bas à droite indiquant le nombre de problèmes. La capture d'écran suivante montre l'icône sélectionnée pour afficher un panneau d'information. Il inclut un Plan de Page, des commentaires de Lisibilité et des Avertissements, qui peuvent être sélectionnés un par un. Le premier problème a été sélectionné.

![Vérification de l'accessibilité du site](../../../en/images/performance/performance-jooa11y-site-display.png "Vérification de l'accessibilité du site")

Le formulaire *Articles : Modifier* a un bouton **Vérification d'accessibilité** dans la barre d'outils. Il montre la vérification pour un article individuel dans une fenêtre popup :

![Vérification de l'accessibilité de l'éditeur](../../../en/images/performance/performance-jooa11y-admin-display.png "Vérification de l'accessibilité de l'éditeur")

## Résolution des problèmes

L'outil Vérificateur d'accessibilité est conçu pour identifier les problèmes, mais il ne les corrige pas. Cela dépend de vous. Le vérificateur propose certains réglages que vous pouvez activer ou désactiver selon vos besoins. Ils incluent le contraste, les étiquettes de formulaire, les liens (avancés) AAA, la lisibilité AAA, le mode sombre et le filtre de couleur avec simulation de quatre types de déficience visuelle des couleurs.

Pour plus d'informations, consultez l'aperçu de Sa11y.

Par exemple, en ce qui concerne la lisibilité, il est indiqué :

>Sa11y peut estimer le score de lisibilité de tous les paragraphes et contenus de liste. Un bon score de lisibilité indique que votre écriture est compréhensible et facile à digérer. Il est basé sur la longueur moyenne des phrases et des mots sur votre page, en utilisant une formule connue sous le nom de test de facilité de lecture de Flesch (Wikipedia). Un "bon" score de lecture se situe entre 60 et 100. Parfois, il peut être difficile d'atteindre un bon score de lisibilité. La plupart de vos pages peuvent indiquer "difficile". Rappelez-vous que cette fonctionnalité est seulement utilisée pour estimer la lisibilité de votre contenu. Elle doit être utilisée uniquement comme référence et non comme une indication de conformité. Sa11y calcule le score de lisibilité en se basant sur tous les contenus de paragraphe (balises `<p>`) et de liste (balises `<li>`). Un score faible n'affecte pas l'état de réussite ou d'échec de Sa11y.

