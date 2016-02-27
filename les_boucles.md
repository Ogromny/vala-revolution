# Les boucles


# Boucle while

L'instruction **while** permet d'effectuer des boucles, qui sont utiles notamment pour effectuer des traitements répétitifs.

La syntaxe est la suivante :
```
while (condition) {
  // suite d'instructions qui sera répétée à chaque passage
}
```

C'est aussi une manière de soumettre des traitements conditionnels, mais n'oubliez pas de faire en sorte que la condition devienne fausse, sinon vous obtiendrez une boucle infinie qui peut saturer les ressources de votre ordinateur ! Les boucles infinies peuvent parfois être utiles, mais elles sont déconseillée à ce stade du cours, surtout si vous êtes débutant.

Voici un exemple :
```
int a = 6;

while (a > 0) {
  stdout.printf("%i\n", a); // cette ligne affichera successivement 6, 5, 4, 3, 2, 1
  a--; // On oublie pas de décrémenter a, ce qui permettra de sortir de la boucle quand a vaudra 0
}
```
# Boucle do while

La boucle **do while** est une variante de la boucle **while** où l'on écrit d'abord les instructions, puis les conditions de bouclage. Les instructions sont effectuées **au moins une fois**, puis répétées selon la condition.

La syntaxe est la suivante :
```
do {
  // suite d'instructions
} while (condition);
```
Voici des exemples :
```c
int i = 0;
do {
  stdout.printf("%i\n", i); // cette ligne affichera successivement 0, 1, 2, 3, 4, 5
  i++;
} while (i < 6);

// même si la condition est fausse, il y a au moins une exécution !
int i = 0;
do {
  stdout.printf("%i\n", i); // cette ligne affichera 0, mais ne sera pas exécutée ensuite
  i++;
} while (false);
```

# Boucle for

La boucle **for** est un peu plus complexe, car elle permet la déclaration, l'initialisation, l'utilisation puis la destruction automatique d'une variable temporaire. On doit également fournir une instruction à exécuter à chaque passage.

La syntaxe est la suivante :
```
for (Type variable = valeur ; condition ; instruction_à_exécuter_à_chaque_passage ) {
  stdout.printf("%i\n", a);
}
```

Dans certains langages, une ou plusieurs partie de la déclaration de la boucle **for** sont facultatives. Ce **n**'est **pas** le cas de Vala : **les 3 termes sont obligatoires**.

L'instruction à effectuer à chaque passage est en pratique toujours destinée à rendre la condition fausse au bout d'un moment, souvent l'incrémentation d'un compteur, mais ce n'est pas obligatoire.

Voici des exemples :
```cpp
// une version "traditionnelle"...
for (int a = 0 ; a < 6 ; a++ ) {
  stdout.printf("%i\n", a);
}

// ...et une un peu moins
for (int a = 0 ; a < 6 ; stdout.printf("coucou\n") ) {
  stdout.printf("%i\n", a);
  a++;
}
```

# Boucle foreach

La boucle **foreach** est une simplification de la boucle **for**, dans les cas spécifiques du parcours en bout en bout des tableaux, listes et tables de hachages. Elle permet d'avoir accès facilement à l'élément courant de l'objet parcouru, stocké dans une variable temporaire.

La syntaxe est la suivante :
```
foreach (Type variable_temporaire in objet_à_parcourir) {
  // suite d'instructions
}
```

La variable temporaire doit être de type compatible avec le type de l'objet à parcourir : par exemple, elle doit être de type **int** pour un tableau de **int**.

Les boucles foreach sont aussi utilisable avec les classes qui implémentent l'interface **Gee.Iterable**.

Voici un exemple :
```cpp
// déclaration d'un tableau de taille 6
int[] tableau = new int[6];

// les valeurs du tableau sont toutes à 0 pour le moment
// on change une des valeurs
tableau[3] = 2;

foreach (int entier in tableau) {
  stdout.printf("%i\n", entier); // cette ligne affichera successivement 0, 0, 0, 2, 0, 0
}
```

# Instruction break

L'instruction **break** sers à sortir prématurément d'une boucle dans laquelle elle est placée. Il s'agit d'une sortie de boucle sur un seul niveau, dans le cas ou il y a plusieurs niveaux de boucles.

Voici un exemple :
```c
int[] tableau = new int[6];
int[] tableau2 = new int[6];

tableau[3] = 2;
tableau2[1] = 1;

foreach (int entier in tableau) {
  stdout.printf("%i\n", entier);

  if (entier == 2) {
    stdout.printf("Sortie de la boucle principale\n");
    break;
  }

  foreach (int entier2 in tableau2) {
    stdout.printf("%i\n", entier2);

    if (entier2 == 1) {
      stdout.printf("Sortie de la boucle secondaire\n");
      break;
    }
  }
}
```

# Instruction continue

L'instruction **continue** permet de passer prématurément au tour suivant à l'intérieur d'une boucle.

Voici un exemple :
```c
for (int i = 0 ; i < 6 ; i++) {
  if (i == 3) continue;
  else stdout.printf("%i\n", i); // cette ligne affichera successivement 0, 1, 2, 4, 5
}
```
