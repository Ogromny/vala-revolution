# Introduction à la POO

Le développement de la puissance des machines a entrainé la complexification des tâches demandées aux programmes informatiques, et par conséquent la complexification de ces derniers. Cependant, une nouvelle approche a révolutionné le monde de la programmation, permettant notamment de réutiliser de gros morceaux de code, tout en simplifiant l'écriture des programmes complexes. Cette approche, on l'appelle la **programmation orientée objet** (POO). Elle consiste en l'assemblage de briques logicielles qu'on appelle **objets**, représentant tout ce que vous pouvez imaginer (une voiture, du vent, la beauté, une date…). Chacun de ces objets est une structure mêlant des **données** et des **traitements**, et les différents types de structures sont appellées **classes**. Pour ceux qui connaissent le C mais pas la POO, les **classes** sont une sorte d'évolution des **structures** du langage C.

Dans la suite de ces 3 chapitres consacrés aux classes, nous allons prendre pour exemple une classe **Chat** représentant un chat (qui fait « miaou », pas un chat de discution). Nous allons donc apprendre à créer un objet **Chat**, qui va naitre, faire « miaou », attraper des souris, et même mourrir… Pour ajouter une dose de surréalisme, notre chat sera rouge foncé avec des rayures noires façon zèbre, de 3 centimètres de largeur en moyenne. De quoi vous convaincre qu'on peut vraiment faire n'importe quoi avec les objets ! :\-D

# Classes

Pour créer une classe, c'est très simple, il vous suffit d'écrire :
```
class NomDeLaClasse {
  // ici on placera notre code
}
```

Pour notre chat, nous ouvrons donc un nouveau fichier dans lequel nous allons écrire :
```
class Chat {

}
```

# Méthodes

Il est très bien notre chat, mais pour le moment il ne fait rien. Pour qu'il fasse quelque chose, il faut lui ajouter une ou plusieurs **méthodes**. Une méthode, c'est exactement le même principe qu'une fonction : la différence se situe dans le fait qu'une fonction est écrite en dehors d'une classe, et qu'une méthode est nécessairement à l'intérieur d'une classe.

Une méthode peut renvoyer un résultat, d'un type particulier (**int** ou **string** par exemple). Il faut indiquer ce type de cette valeur de retour. Si la méthode ne renvoie rien, le type à indiquer est **void**.

Pour écrire une méthode, voici la syntaxe :
```
class UneClasse {

  Type_de_retour nom_de_la_methode () {
    // méthode sans paramètres
  }

  Type_de_retour nom_de_la_deuxieme_methode (Type param1, Type2 param2) {
    // méthode avec 2 paramètres (vous pouvez en mettre d'autres pareillement)
  }
}
```

Vous n'avez pas le droit d'avoir 2 méthodes de noms identiques à l'intérieur de la même classe, contrairement à d'autres langages qui le permettent comme Java.

Nous allons donc ajouter à notre chat la possibilité de dire « Miaou ! » :
```
class Chat {

  void miaou () { // la méthode ne renvoie rien, on utilise donc void comme type de retour
    stdout.printf ("Miaou !\n");
  }
}
```

Puis nous lui donnons la possibilité d'attraper des souris :
```
class Chat {

  void miaou () { // la méthode ne renvoie rien, on utilise donc void comme type de retour
    stdout.printf ("Miaou !\n");
  }

  void attrape_une_souris () { // la méthode ne renvoie rien, on utilise donc void comme type de retour
    stdout.printf ("Le chat s'approche lentement, puis se met à courrir et attrape une souris !\n");
    stdout.printf ("Le félin a encore frappé...\n");
  }
}
```

# Méthode main

Comme pour les fonctions à l'intérieur d'un fichier, vous pouvez mettre plusieurs méthodes à l'intérieur d'une classe. Mais comment savoir par où commencer l'exécution alors ? C'est très simple : par convention, on commence par la méthode ou la fonction qui s'appelle **main**. Cela signifie également qu'il est interdit de nommer une méthode main dans votre programme, en dehors de celle prévue comme point d'entrée.

Notre classe **Chat** devient donc exécutable après l'ajout de méthode main, comme ceci :
```
class Chat {

  void miaou () { // la méthode ne renvoie rien, on utilise donc void comme type de retour
    stdout.printf ("Miaou !\n");
  }

  void attrape_une_souris () { // la méthode ne renvoie rien, on utilise donc void comme type de retour
    stdout.printf ("Le chat s'approche lentement, puis se met à courrir et attrape une souris !\n");
    stdout.printf ("Le félin a encore frappé...\n");
  }

  static void main () {
    stdout.printf ("Démarrage du programme\n");
  }
}
```

Le code compile, moyennant un avertissement, et vous devez voire apparaitre « Démarrage du programme » à l'exécution. L'avertissement nous signale que la méthode **miaou()** n'est pas utilisée : dans notre cas, c'est normal.

Notez le mot-clé **static** employé avant **void** dans la méthode main. Son emploi sera détaillé plus loin. Il n'est pas possible de s'en passer ici, sauf si l'on écris la méthode à l'extérieur d'une classe.


Il est également possible d'écrire une deuxième méthode main dans une autre classe si l'on emploie pas static : celle-ci n'aura alors rien à voir et ne jouera pas le rôle de point d'entrée du programme.

# Attributs

Notre chat peut désormais attraper des souris, mais il n'est toujours pas rouge foncé comme nous le voulions. Pour cela, il faut lui donner des attributs ; rouge foncé étant l'attribut **couleur**. Pour créer un attribut, il suffit d'écrire dans le corps de la classe :
```
Type_de_l_attribut nom_de_l_attribut;
```

Il s'agit d'une simple déclaration de variable en fait, et d'ailleurs vous pouvez l'initialiser en même temps :
```
Type_de_l_attribut nom_de_l_attribut = valeur;
```

Dans notre exemple, on obtient :
```
class Chat {

  string couleur = "rouge foncé"; // le chat est rouge foncé
  bool rayures = true; // le chat a des rayures
  string type_rayures = "zebre"; // les rayures sont de type "zebre"
  string couleur_rayures = "noir"; // les rayures sont noires
  int largeur_rayures = 3; // les rayures font 3 cm de largeur

  void miaou () { // la méthode ne renvoie rien, on utilise donc void comme type de retour
    stdout.printf ("Miaou !\n");
  }

  void attrape_une_souris () { // la méthode ne renvoie rien, on utilise donc void comme type de retour
    stdout.printf ("Le chat s'approche lentement, puis se met à courrir et attrape une souris !\n");
    stdout.printf ("Le félin a encore frappé...\n");
  }

  static void main () {
    stdout.printf ("Démarrage du programme\n");
  }
}
```

Le compilateur signale toujours des avertissements à cause des éléments non utilisés : c'est **normal**, car nous ne les utilisons pas encore à ce stade.

Vous pourrez par la suite créer une classe “Rayure”, et ainsi gérer les attributs des rayures (couleur, largeur, type…) avec cette classe.
