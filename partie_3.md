# Visibilités des éléments

Il existe 4 types de visibilité

| **type** | **effet** |
| --        | -- |
| _public_    | aucune restriction |
| _private_   | accés limité à la classe ou la structure |
| _protected_ | accés limité à la classe et à toutes les classes qui en héritent |
| _internal_  | accés limité exclusivement à toutes les classes definie dans le même package |

    Si aucune visibilité n'est indiqué, private sera implicitement ajouté

# Accesseurs

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

# Propriétés

Si vous avez déjà des bases en Java, l'exemple suivant devrait vous parler

```vala
class Personne: Object {

    private int age = 32;
    
    public int get_age() {
        return this.age;
    }
    
    public int set_age() {
        this.age = age;
    }

}
```

ça marche mais Vala peut faire encore mieux

```vala
class Personne: Object {

    private int _age = 32;
    
    public int age {
        get { return _age; }
        set { _age = value; }
    }

}
```

mais Vala ne s'arrète pas là !

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

pour empêcher à l'utilisateur de pouvoir modifier l'âge d'un personnage on peut tout simplement mettre l'attribue set en private ou l'omettre ce qui aura le même effet

```vala
class Personne: Object {
    public int age { get; private set; default; }
}
```

# Les espaces de noms

Tout ce qui se trouve dans un namespace est dans le nom de ce namespace.
Tout ce qui se trouve en dehors de ce namespace est dans le namespace global

```vala
namespace MaSuperLib {
    class...
    
    fonction...
}
```

Pour importer un namespace 

```vala
using MaSuperLib {

}
```

Par exemple si le namespace Gtk est importé. Alors vous pourrez simplement écrire

```vala
using Gtk;

Window ma_fenetre = new Window();
```

à la place de

```vala
Gtk.Window ma_fenetre = new Gtk.Window();
```