# Généralités

Les tableaux permettent de contenir plusieurs éléments d'un même type au sein d'une unique variable. Ils sont de tailles fixes, et comme si l'on construisait une armoire en numérotant les étagères, les éléments sont repérés par leur place dans le tableau. **Ils sont à distinguer des collections**, qui elles sont de tailles variables et possèdent d'autres fonctionnalités !

# Déclaration des tableaux

La syntaxe est la suivante :
```vala
Type[] nom_du_tableau = new Type[taille_du_tableau]; // création d'un tableau avec taille_du_tableau cases
```

La valeur par défaut de chaque éléments du tableau dépend du type qui y est stocké : par exemple pour un tableau de `int`, la valeur par défaut sera 0, et ceci pour tous les éléments du tableau.

Voici un exemple :
```
int[] mon_tableau = new int[10]; // mon_tableau contient 10 éléments de type "int" qui valent tous 0
```

# Utilisation des tableaux

Une fois le tableau créé, il s'utilise comme n'importe quelle variable lorsqu'on le manipule en entier. Par exemple pour copier un tableau :
```
tableau1 = tableau2; // les valeurs de tableau2 sont recopiées dans tableau1
```

> /!\ **Attention** : tableau1 devient un **nouveau** tableau avec les valeurs de tableau2… et **sa taille**. Si tableau2 était de taille x avant, et tableau1 de taille y, tableau1 devient de taille x. La taille de tableau1 n'a pas réellement été modifiée, mais un nouveau tableau de la bonne taille a été créé, et auquel on accède désormais avec la variable tableau1.

Pour accéder aux éléments du tableau, on mentionne le numéro de la place de l'élément auquel on veut accéder, et les manipulations se font comme une variable simple.

Voici la syntaxe :
```
nom_du_tableau[numero_de_l_element]
```

Par exemple :
```
// création du tableau
int[] mon_tableau = new int[10];

// initialisation de quelques valeurs
mon_tableau[3] = 5;
mon_tableau[7] = 9;
```

>/!\ **Attention** : la numérotation des éléments des tableaux commencent **toujours** à **0**. Un tableau de taille 10 possède donc un élément numéro 9, mais **pas** d'élément numéro 10.

Le compilateur **ne** vous insulte **pas** lorsque vous tentez de manipuler un élément dont le numéro est supérieur à la taille du tableau. Le code suivant ne provoque pas d'erreur avec la version 0.5.6 de **valac** :
```
int[] array = new int[2];

array[0] = 0;
array[1] = 1;
array[42] = 42;

foreach (int element in array) {
   stdout.printf("%i\n", element);
}
```

La sortie donne :
```
0
1
```

Il doit s'agir d'un bug ou d'une vérification non implémentée pour le moment, mais en attendant plus d'infos **vous devez être** particulièrement **attentif** à votre code lorsque vous manipulez les tableaux.
