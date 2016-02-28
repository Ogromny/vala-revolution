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

    Le namespace GLib est importé par défaut
    
Les namespaces peuvent-être additionné

```vala
namespace A {
    
    namespace B {
        ...
    }
    
    namespace C {
        class Personne()...
    }
    
}

A.B.Personne wladimir = new A.B.Personne()
```