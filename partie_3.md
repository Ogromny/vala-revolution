# Visibilités des éléments

Il existe 4 types de visibilité

| **type** | **effet** |
| --        | -- |
| _public_    | aucune restriction |
| _private_   | accés limité à la classe ou la structure |
| _protected_ | accés limité à la classe et à toutes les classes qui en héritent |
| _internal_  | accés limité exclusivement à toutes les classes definie dans le même package |

    Si aucune visibilité n'est indiqué, private sera implicitement ajouté

# Propriétés

Si vous avez déjà des bases en Java, l'exemple suivant devrait vous parler

```vala
class Personne: Object {

    private int age = 32;
    
    public int get_age () {
        return this.age;
    }
    
    public int set_age () {
        this.age = age;
    }

}
```

Ce code est valide mais n'est pas du tout adapté, Vala propose un système de propriétés bien plus puissant qu'un appel de fonction. Voyons l'exemple suivant:

```vala
class Personne: Object {

    private int _age = 32;
    
    public int age {
        get { return _age; }
        set { _age = value; }
    }

}
```

Il nous est également possible de définir une propriété en lui assignant une valeur par défaut, et le tout sur une seule ligne !

```vala
class Personne: Object {
    public int age { get; set; default = 32; }
}
```

En effet, il est possible de déclarer une propriété et de lui assigner une valeur par défaut

on peut l'utiliser comme ça

```vala
var wladimir = new Personne();
wladimir.age++; // wladimir a maintenant 33 ans
```

Il est également possible de réstreindre le champ d'action possible sur une propriété, par exemple en interdissant sa modification. Nous utiliserons pour cela le mot-clé `private` directement sur notre champ `set`

```vala
class Personne: Object {
    public int age { get; private set; default = 0; }
}
```

# Les espaces de noms

Un espace de nom permet d'englober une ou plusieurs classes afin de hierarchiser son code plus facilement. Cela permet également d'avoir un code plus propre, par exemple, lors de la création d'une librairie de fonctions destinée à être réutilisée par la suite.

Voici un petit exemple de ce à quoi ressemble un espace de nom. Nous avons donc utilisé le mot-clé `namespace` afin de déclarer le namespace `MaSuperLib`. Nous avons ensuite déclaré quelques propriétés et fonctions, afin d'avoir un petit code simple pour l'exemple.

```vala
namespace MaSuperLib {
    class Personne : GLib.Object {
        private string pseudo {
            get;
            set;
            default = "Personne_01";
        }
    
        public Personne (string pseudo) {
            this.pseudo = pseudo;
        }
        
        public void display_name () {
            info (@"Le nom de cette personne est $(this.pseudo).");
        }
    }
}
```

Afin d'importer une librarie contenue dans l'espace de nom `MaSuperLib` il nous faudrat utiliser le mot-clé `using`, les adeptes du C# comprendront surement son utilité. Importer une classe en Vala n'est pas pareil qu'en C#. Ainsi lorsque nous écrirons le code suivant, le compileur Vala va se charger d'inclure le fichier `MaSuperLib.vala` juste avant l'utilisation de la classe.

Inclure une classe en Vala est aussi simple que suit:
```vala
using MaSuperLib;
```

Si nous n'avions pas inclus la librairie `MaSuperLib` il nous aurait fallut préfixer chaque appel à nos classes et fonctions statiques dans cet espace de nom. Ce qui est non seulement inutile mais également long et s'avère être super chiant sur de très gros codes. Le code suivant est donc à éviter.

```vala
static int main (string [] args) {
    MaSuperLib.Personne jean = new MaSuperLib.Personne ("Jean Neymar");
    jean.display_name (); // Affiche: Le nom de cette personne est Jean Neymar.
    
    return 0;
}
```

Afin d'éviter toute forme de redondance il est préférable d'inclure notre espace de nom au début du fichier, afin d'avoir accès à ses membres d'une manière plus souple. Nous préfererons donc le code suivant :

```vala
using MaSuperLib;

static int main (string[] args) {
    Personne mairy = new Personne ("Mairy Gollez");
    mairy.display_name (); // Affiche: Le nom de cette personne est Mairy Gollez.
    
    return 0;
}
```

**Remarque:** L'espace de noms `GLib` est importé automatiquement par le compilateur, inutile donc de l'inclure manuellement.
    
Afin de clore ce chapitre, j'aimerai également vous faire part d'une petite fonctionnalité sympa de Vala. Il s'agit de pouvoir écrire un espace de noms dans un autre espace de noms, aussi appelé "nesting" en anglais. Ce n'est pas quelque chose que l'on utilise tous les jours mais cela peut s'avérer rapidement utile afin de maintenir une librairie complexe comportant plusieurs milliers de lignes de code.

Le nesting d'espace de nom est aussi simple que l'exemple suivant :
```vala
namespace A {
    
    namespace B {
        // Notre code pour le namespace A.B ici.
    }
    
    namespace C {
        // Notre code pour le namespace A.C ici.
    }
    
}
```