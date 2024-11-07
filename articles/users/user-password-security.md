<!-- Filename: J5.x:Enhancing_Password_Security_with_Symbolic_Characters / Display title: Sécurité des mots de passe des utilisateurs   -->

## Introduction

Dans l'onglet *Options de mot de passe* du formulaire *Utilisateurs : Options*, les valeurs minimales pour *Nombres*, *Symboles*, *Majuscules* et *Minuscules* sont toutes définies par défaut à 0. Pour une meilleure sécurité, ces valeurs devraient être définies à 1. Les nouveaux mots de passe ou ceux modifiés doivent alors inclure au moins un de chacun de ces caractères.

## Symboles

L'*Open Worldwide Application Security Project* (OWASP) recommande que tous les caractères spéciaux disponibles sur un clavier standard des États-Unis soient reconnus et acceptés lors de la définition des exigences de mot de passe.

```
 !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
 ```

Ce n'est pas évident, mais cette liste inclut le caractère espace.

[OWASP : Caractères Spéciaux pour Mots de Passe](https://owasp.org/www-community/password-special-characters)

Avant la version 5.2, ces symboles pouvaient être utilisés dans les mots de passe, mais certains d'entre eux n'étaient pas reconnus comme des symboles aux fins de validation de mot de passe :
```
@[]£^+±~<>/'",.
``` 

*Traduit par openai.com*

