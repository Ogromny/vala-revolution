# Premier programme
Il est de tradition, lorsque l'on teste ou présente un langage, de faire un petit programme dont l'unique but est d'afficher “Hello, world !”. Voici le [Hello, world !](http://fr.wikipedia.org/wiki/Hello_World) de Vala :
```vala
void main () {
  stdout.printf("Hello, world !\n");
}
```

Si la compilation s'est bien passé, vous devez normalement lire dans la console, au moment de l'exécution, l'expression **Hello, world !**.

Dans toute la première partie, le code ci-dessus sera résumé à :
```vala
stdout.printf("Hello, world !");
```
La fonction `main()` sera **implicite**, mais n'oubliez pas de la rajouter lors de vos tests ! Il s'agit du point d'entrée de votre programme.

Le caratère **\n** à la fin de **Hello, world !** sers à effectuer un retour à la ligne.
Ce code ne fait appel ni à GLib, ni à la définition d'une classe. Vala se différencie donc sur ce point des langages qui, comme Java, imposent l'écriture d'une classe au minimum.

# Commentaires
La plupart des langages de programmation possède un système de commentaires, permettant d'écrire dans le code source des informations dont le compilateur (ou l'interpréteur) ne tiendra pas compte. Vala respecte en ce point la syntaxe héritée du langage C, reprise dans de nombreux autres langages, et vous permet ainsi de créer des commentaires :

- En ligne, grace aux caractères **//**. Tout ce qui ce trouve à droite de 2 symboles **/** accolés est ignoré, jusqu'à la fin de la ligne.
- En blocs, grâce aux caractères délimitants **/\*** (ouverture) et **\*/** (fermeture). Tout ce qui est à l'intérieur de ces délimiteurs sera ignoré, y compris si la zone s'étend sur plusieurs lignes.

```vala
// Je suis un commentaire sur une ligne.

/**
* Je suis un commentaire super long et donc forcément bah
* je suis sur plusieurs lignes :D.
**/
```

# Mots-clés
Comme tous les langages, Vala possède des mots-clés, qui ont une signification particulière pour le compilateur, et dont l'utilisation est interdite en dehors de celle prévue. Par exemple, le mot-clé **using** permet d'importer un espace de noms (namespace en anglais), afin que le code référencé dans cet espace de noms puisse être utilisé dans le code qui suit l'instruction.

## Liste des mots-clés en Vala
---
| abstract 	| do        	| lock      	| set       	|
|----------	|-----------	|-----------	|-----------	|
| while    	| base      	| else      	| namespace 	|
| signal   	| break     	| enum      	| null      	|
| static   	| callback  	| false     	| out       	|
| struct   	| case      	| for       	| override  	|
| switch   	| class     	| foreach   	| private   	|
| true     	| const     	| get       	| protected 	|
| using    	| construct 	| if        	| public    	|
| var      	| continue  	| in        	| ref       	|
| virtual  	| default   	| interface 	| return    	|
| weak     	|           	|           	|           	|
---

Certains langages permettent tout de même d'utiliser les mots-clés, en dehors de leur signification initiale, bien que cela soit déconseillé, et disposent d'un mécanisme permettant de faire la différence avec le mot-clé. En Vala, vous pouvez utiliser un mot-clé pour un nom de variable ou de classe en le préfixant par le caractère **@**. Vous pouvez donc appeler une variable ou une classe **@class**.

# Conventions
Il existe souvent des conventions d'écriture pour les codes sources, dépendants du langage dans lequel est codé le programme, de façon à uniformiser le travail de chaque développeur. Ces conventions peuvent être respectées ou non, sans interférer dans le fonctionnement du programme. Il est cependant largement préférable de s'y conformer lorsqu'elles existent, et spécialement lorsque l'on travaille en équipe.

- Vala n'impose pas de conventions particulières dans la structure arborescente d'un projet, bien que celles héritées du projet GNOME soient fortements encouragées.
- Les fichiers sources contiennent normalement une classe publique majeure, d'après laquelle le fichier tire son nom. Un choix courant étant d'utiliser ce nom en minuscules, préfixé par l'espace de nom (également en minuscules) de la classe. Dans les petits projets, l'espace de nom pouvant être redondant, il est généralement omis.
- Il est déconseillé, pour des raisons de clareté, d'inclure du code dans plusieurs espaces de noms à l'intérieur d'un seul fichier source. Un espace de nom peut cependant être divisé en plusieurs fichiers, et chaque application aura normallement un espace de nom principal, et éventuellement d'autres à l'intérieur de celui-ci.
- Les espaces de noms, tout comme les noms de classes, utilisent le style camel avec une majuscule au début : MonEspaceDeNoms, MaClasse.
- Les noms de méthodes sont en minuscules, et utilisent un tiret bas ( _ ou underscore) pour séparer les mots : ma_methode.
- Les noms de constantes sont en majuscules, et les mots également séparés par un tiret bas : MA_CONSTANTE.
- Bien qu'il semble n'y avoir à l'heure actuelle aucune convention pour les noms de variables, utiliser le même type de contruction que pour les méthodes semble être une voie s'intégrant bien dans le langage.
