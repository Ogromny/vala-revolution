# Condition if

La condition `if` est la plus utilisée des structures conditionnelles.

La syntaxe est la suivante :
```vala
// le bloc if obligatoire, unique et toujours au début
if (condition1) {
  // suite d'instructions exécutée si condition1 vaut vrai
}

// un ou plusieurs blocs "else if" tous facultatifs (vous pouvez ne pas en mettre)
else if (condition2) {
  // suite d'instructions exécutée si condition1 vaut faux et condition2 vaut vrai
}

// un bloc "else" facultatif, mais unique et toujours placé à la fin
else {
  // suite d'instructions exécutée si condition1 et condition2 valent faux tous les deux
}
```

Les blocs sont définis par le caractère ouvrant `{` et le caractère fermant `}`. Ils peuvent contenir plusieurs instructions, et d'autres blocs. Ils peuvent aussi être vides - `{}` est syntaxiquement correct -, ou ne contenir qu'une seule instruction qui peut être elle-même vide - `{;}` est aussi correct.

Voici un exemple :
```vala
if (false) {
  stdout.printf("Premier"); // Ces deux lignes seront ignorées car
  stdout.printf(" cas\n"); // false vaudra toujours faux
}

else if (true) {
  stdout.printf("Second cas\n"); // Ligne exécuté car la condition vaut vrai
}

else {
  stdout.printf("Dernier cas\n"); // Ligne ignoré car le second bloc sera exécuté avant
}
```

On remarquera que dans ce cas précis l'avertissement que le compilateur génère à propos des deux portions de code qui ne seront jamais exécutées :
```
test.vala:4.5-4.29: warning: unreachable code detected
    stdout.printf("Premier"); // Ces deux lignes seront ignorées car
    ^^^^^^^^^^^^^^^^^^^^^^^^^
test.vala:13.5-13.35: warning: unreachable code detected
    stdout.printf("Dernier cas\n"); // Ligne ignoré car le second bloc sera exécuté avant
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Compilation succeeded - 2 warning(s)
```

Dans le cas où il n'y a qu'une seule ligne dans un bloc, vous pouvez omettre les accolades (les symboles **{** et **}**) :
```
if (true) {
  stdout.printf("Coucou");
}
```
est équivalent à :
```
if (true)
  stdout.printf("Coucou");
```

# Condition switch

La condition **switch** est moins utilisée que la condition **if**, notamment parce qu'elle ne prend en charge que des situations restreintes : elle nécessite en effet l'évaluation d'une variable. Dans beaucoup de langages, cette variable ne peut être qu'un entier, mais Vala accepte également de traiter les cas ou cette variable est une chaine de caractère.

La syntaxe est la suivante :
```
switch (variable) {
  case valeur1:
    // suite d'instructions si variable == valeur1
    break;

  case valeur2:
    // suite d'instructions si variable == valeur2
    break;

  // d'autres blocs "case" peuvent être ajoutés...

  // ...et si aucun ne convient on peut (facultatif) ajouter le bloc "default"
  default:
    // suite d'instructions sinon
    break;
}
```
N'oubliez pas les deux points après la valeur : **case** valeur **:**

D'ordinaire, on place le bloc **default** à la fin du bloc **switch**, et cela est requis dans certains langages, mais Vala ne l'impose pas. Vous pouvez placer votre bloc **default** où vous voulez !

Voici deux exemples :
```
int a = 6;
string b = "coucou";

switch (a) {
  case 1:
    stdout.printf("1\n"); // Ligne ignorée car a ne vaut pas 1
    break;

  default:
    stdout.printf("default\n"); // Ligne ignorée car il y a un bloc en bas qui correspond
    break;

  case 2:
    stdout.printf("2\n"); // Ligne ignorée car a ne vaut pas 2
    break;

  case 6:
    stdout.printf("6\n"); // Ligne exécutée car a vaut 6
    break;
}

switch (b) {
  case "poire":
    stdout.printf("poire\n"); // Ligne ignorée car b ne vaut pas "poire"
    break;

  case "bouteille":
    stdout.printf("bouteille\n"); // Ligne ignorée car b ne vaut pas "bouteille"
    break;

  default:
    stdout.printf("default\n"); // Ligne exécutée car aucun bloc autre que "default" ne correspond
    break;

  case "souris":
    stdout.printf("souris\n"); // Ligne ignorée car b ne vaut pas "souris"
    break;
}
```
L'instruction **break;** sers à demander la sortie prématurée du bloc **switch** après le traitement d'un cas favorable. Elle est obligatoire en Vala, et le compilateur vous insultera furieusement si vous l'oubliez.
