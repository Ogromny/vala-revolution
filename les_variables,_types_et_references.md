# Déclaration des variables
Avant de pouvoir utiliser des variables, il faut les **déclarer**. Le compilateur a en effet besoin de connaître le type de variable dont il s'agit, et également le nom associé que vous allez utiliser pour la désigner.

Mais rassurez-vous, rien de bien compliqué, pour déclarer une variable, il suffit donc de respecter la syntaxe :

```vala
Type_De_Variable nom_de_variable ;
```

Voila, c'est tout, vous pouvez ensuite utiliser la variable **nom_de_variable**. Vous pouvez par exemple décider de l'**initialiser** tout de suite, c'est-à-dire lui assigner une première valeur. Par exemple :

```vala
string texte;
texte = "Coucou";
```
Bien entendu, vous pouvez décider d'initialiser la variable plus tard, par exemple au sein d'une méthode en récupérant un paramètre :

```vala
string texte;

public void init(string param) {
   texte = param;
}
```
Cela dit, dans de nombreux cas il sera souhaitable de l'initialiser tout de suite, et il est possible dans ce cas de condenser les 2 lignes nécessaires en une seule. En voici un exemple :

```vala
string texte = "Coucou";
```

# Types de données primitifs

Vous venez de voir en action le type `string`  c'est-à-dire en français **chaîne de caractères**. Comme son nom l'indique, il s'agit d'une chaîne formée de plusieurs caractères, ce qui était donc particulièrement indiqué pour stocker le texte **Coucou**. Il existe cependant d'autres types de données primitifs, c'est-à-dire définis par le langage.

## Liste des types primitifs
---
| char 	    | int8        | size_t      | uint16      |
|----------	|-----------	|-----------	|-----------	|
| bool    	| int16      	| ssize_t    	| uint32 	    |
| double   	| int32     	| string     	| uint64      |
| enum    	| int64      	| uchar     	| ulong      	|
| float   	| long      	| uint       	| unichar   	|
| int   	  | short     	| uint8     	| ushort    	|
---

# Distinction entre référence et valeur

Lorsqu'il stocke un résultat, l'ordinateur procède comme si l'on déchargeait un sac dans un ou plusieurs casiers, selon la place que prend le contenu.

* Une valeur est une variable directement associée à son contenu, c'est à dire qu'elle dispose de ses propres casiers.

* Une référence sur une variable, bien qu'étant manipulé comme la variable, ne contient comme information que l'emplacement en mémoire où est stocké le contenu de la variable (les numéros des casiers utilisés).

# Manipulation des références

Habituellement, les paramètres passées à une méthode sont passés en tant que valeur, et l'on récupère ainsi une variable locale. Pour préciser qu'un paramètre doit être passé par référence, on doit ajouter le mot-clé `ref` devant.

```vala
ma_methode(ref param)
```

Dans le cas ou les performances comptent beaucoup, l'opération sera probablement plus rapide en utilisant une référence, car sans recopie en mémoire.

Un aspect intéressant du langage est abordé avec le mot-clé `out`, qui permet de spécifier que le paramètre passé est utilisé pour stocker une valeur de retour.

Un autre aspect intéressant est constitué par les références faibles, signalés par le mot-clé `weak` : lorsqu'il n'existe plus que des références faibles, ou plus de références, l'objet en mémoire est détruit.

Enfin, on peut vouloir **transférer**, et non pas **recopier** une référence, et on peut le faire en utilisant le symbole `#` avant le nom de la variable de laquelle on veut récupérer la référence. Exemple :

```vala
Foo foo = #bar;
```

Ici, foo va récupérer la référence de bar, et bar pointera désormais sur **null**. Le compteur de référence reste inchangé avec cette opération.

Depuis la version 0.5.4, le symbole **#** a été remplacé par le mot-clé **owned** et **weak** par **unowned**.
