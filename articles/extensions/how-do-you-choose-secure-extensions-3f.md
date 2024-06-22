<!-- Filename: How_do_you_choose_secure_extensions%3F / Display title: Comment choisir des extensions sécurisées ? -->

La chose la plus importante que toute personne doit faire est de prendre
les bonnes décisions quant aux extensions que l'on choisi ou non
d'utiliser sur un site. Une fois qu'une extension nuisible ou non
sécurisée est installée, vous devriez considérer l'ensemble de votre
site comme étant compromis. Il n'existe **aucun moyen** de protéger ou
d’empêcher composant d'accéder aux tables de base de données auxquelles
il ne devrait pas accéder. Il est impossible d'empêcher ce même
composant d'envoyer toutes les informations qu'il aura récupéré à un
autre site web. Une fois qu'un composant non sûr ou malveillant est
installé, l'ensemble de votre site devient non sécurisé.

## Quelques conseils faciles pour bien choisir les extensions que vous allez installer

- A quand remonte la dernière version ?

Si elle a plus d'un an, considérez le projet comme ayant été abandonné
et trouvez une autre extension. Il ne faut pas installer des composants
trop anciens.

- De quel type de version est le composant ? (Stable, Release Candidate
  (RC), Bêta, Alpha).

Pour les sites en production, vous devriez utiliser uniquement les
versions Stables. Si vous ne pouvez pas attendre qu'une version Stable
soit disponible, les versions Release Candidate sont les seules autres
options à envisager. Il n'est pas conseillé d'utiliser des extensions en
version Bêta ou Alpha sur un site en production. Cela signifie en effet
que ces versions contiennent encore des anomalies et n'ont pas encore
fait l'objet de suffisamment de tests et pourraient même inclure des
failles de sécurité qui n'ont pas fait l'objet de correctifs.

- Est-ce que l'extension a bonne réputation en matière de sécurité ?

C'est évidemment une considération un peu plus subjective, mais elle
reste très valable pour évaluer la fiabilité future. Cela nécessite un
peu d'investigations et de recherches. Consultez les pages de
téléchargement et les archives des développeurs. Existe-t-il de
nombreuses mises à jour de sécurité ou des correctifs ? Existe-t-il de
nombreux rapports de failles de sécurité pour cette extension ? Le
développeur est-il expérimenté et conscient des questions de sécurité ?
Que pensent les autres membres de la communauté de cette extension ?

- Existe-t-il une communauté pour le support de cette extension ?

Ceci est très important au regard de la facilité d'utilisation et des
questions de sécurité. S'il existe une communauté qui prend en charge
l'extension, il y aura plus de chances que les anomalies de sécurité
soient connues et résolues. Une communauté de suivi signifie que les
gens souhaitent continuer à utiliser l'extension et qu'ils s'inquiètent
du devenir de celle-ci. C'est une chance de plus que les questions de
sécurité soient trouvées, révélées, et traitées rapidement.

- Existe-il une version compatible avec la version la plus récente de
  Joomla ?

Ce point est important dans une période de transition entre deux
versions prises en charge de Joomla. Il est important de savoir si
l'extension est compatible avec la version actuelle de Joomla, lorsque
l'ancienne version va arriver en fin de vie. La mise à jour de Joomla!
est beaucoup plus facile si une extension est compatible avec la version
la plus récente de Joomla.

- L'extension est-elle généralement exempte d'anomalies ?

Bien qu'il soit presque impossible pour une extension d'être
complètement exempte d'anomalies, plus le nombre d'anomalies est faible,
mieux c'est. S'il y a des anomalies dans le logiciel, cela signifie que
le logiciel contient des erreurs. Plus il existe d'anomalies, plus le
risque de rencontrer des erreurs et des problèmes de sécurité est élevé.
Les problèmes de sécurité sont souvent le résultat de l'existence de
plusieurs anomalies ou de mauvaises pratiques. Par exemple, les récentes
vulnérabilités d'extensions tierces qui permettent des inclusions de
code sont le résultat de :

## Mauvaises pratiques

- Avoir PHP Register Globals d'activé.
- L'utilisation d'extensions obsolètes ou abandonnées.
- L'absence d'autres contrôles de sécurité activé pour PHP. (url_fopen
  off, open_basedir restrictions, désactivation de PHP functions)
- Une mauvaise configuration des permissions de fichier.
- Aucune demande de filtrage ou de logiciel "pare-feu". (telles que les
  règles de mod_rewrite ou mod_security modules d'Apache)

## Anomalies

- Ne pas intégrer les déclarations defined('\_VALID_MOS') or die...
- Les déclarations include() mal construites.

## Choses importantes à retenir

**Bien que le noyau Joomla! soit sûr lorsqu'il est configuré
correctement, les différentes extensions tierces peuvent présenter
différentes qualités**. A moins que vous ayez une confiance absolue dans
le développeur de l'extension, il convient de toujours inspecter le code
avant de l'installer. La liste suivante est celle des sujets qui doivent
vous préoccuper.

1\. Quelle est la complexité de l'extension ?

Plus elle est grande, plus elle est susceptible de rencontrer des
problèmes et donc, plus vous devriez y apporter de l'attention. Si vous
ne comprenez pas ce qu'elle implique, vous ne devriez pas l'utiliser.

2\. L'extension doit-elle lire ou écrire des fichiers sur votre
serveur ?

Les programmes qui lisent les fichiers peuvent, même par inadvertance,
violer les restrictions d'accès que vous avez mis en place ou donner des
informations aux hackers. Les programmes qui écrivent des fichiers ont
le potentiel de modifier ou d'endommager les fichiers existants, ou
encore d'introduire des chevaux de Troie.

3\. Est-ce que l'extension interagit avec d'autres programmes de votre
système ?

Par exemple, de nombreuses extensions permettent d'envoyer un courriel
en réponse à un formulaire de saisie provoquant ainsi l'ouverture d'une
connexion avec le programme sendmail. Cette extension opère-t-elle cette
action de manière sûre ?

4\. Est-ce que l'extension fonctionne avec des privilèges 'suid'
(set-user-id) ?

En général, ceci est particulièrement dangereux. Les extensions doivent
avoir d'excellentes raisons pour utiliser cette technique.

5\. L'extension doit-elle valider l'ensemble des entrées de
l'utilisateur, tels que les champs de formulaire et les URL ?

6\. Check here, if the extension is listed as  vulnerable
extension

6\. L'extension utilise-t-elle des noms de chemin d'accès explicites
lors de l'appel de programmes externes ?

S'appuyer sur la variable d'environnement PATH pour résoudre les
questions de chemin d'accès est une pratique à risque.

7\. L'extension est-elle sécurisée contre l'accès direct via l'URL ?

Par exemple :
`www.votresite.com/components/com_mauvaise_extension.php?mauvais_code_a_cet_emplacement`

8\. L'extension est-elle sécurisée contre les inclusions de fichiers ?

9\. L'extension est-elle sécurisée contre les injections SQL ?

10\. L'extension est-elle sécurisée contre le Cross Site Scripting
(XSS) ?

11\. Est-ce que l'extension de besoin que PHP register_globals ou que
Joomla! RG Emulation soient sur 'ON' ?

Si oui, alors il est probablement que cela soit en violation du numéro 7
ci-dessus.

12\. Est-ce que l'extension octroie des droits d'accès à la base de
données plus élevés à des utilisateurs non privilégiés ?

Par exemple, est-ce qu'elle permet aux invités ou aux utilisateurs
enregistrés de consulter des données que seuls les éditeurs ou les
administrateurs devraient être en mesure de voir ?

### Informations complémentaires

- Voir : <a
  href="http://extensions.joomla.org/support/knowledgebase/item/choosing-secure-extensions"
  class="external text" target="_blank" rel="noreferrer noopener">Comment
  choisir des extensions sécurisées sur le site du JED</a>
- See:
  <a href="https://extensions.joomla.org/vulnerable-extensions/about/"
  class="external text" target="_blank"
  rel="noreferrer noopener">Vulnerable Extension List</a>
