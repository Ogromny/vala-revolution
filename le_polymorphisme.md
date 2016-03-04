# L'héritage

L'héritage permet de faire hériter une classe d'une autre classe, dans le but de lui affecter ses propres variables/méthodes

```vala
class SuperClass : GLib.Object {
    public void method_1 () {
        stdout.printf ("SuperClass.method_1()\n");
    }
}

class SubClass : SuperClass {
    public void method_1 () {
        stdout.printf ("SubClass.method_1()\n");
    }
}

SubClass o1 = new SubClass ();
o1.method_1(); // SubClass.method_1 ()
SuperClass o2 = o1;
o2.method_1(); // SuperClass.method_1 ()
```

Pour empécher ce comportement il faut utiliser les mots-clefs `virtual` et `override`
```vala
class SuperClass : GLib.Object {
    public virtual void method_1 () {
        stdout.printf ("SuperClass.method_1()\n");
    }
}

class SubClass : SuperClass {
    public override void method_1 () {
        stdout.printf ("SubClass.method_1()\n");
    }
}

SubClass o1 = new SubClass ();
o1.method_1 (); // SubClass.method_1()
SuperClass o2 = o1;
o2.method_1 (); // SubClass.method_1()
```

Si vous voulez utiliser les fonctionnalités d'une classe parentes dans la classes enfants il faudra utiliser le mots-clef `base`
```vala
public override void method_name () {
  base.method_name (); // appele de method_name de la classe parente
  ...
}
```

# Les interfaces

Les interfaces sont comme modèles pour classe, les interfaces sont abstraite c'est-à-dire qu'elles ne sont pas instantiables
```vala
public interface ITest {
  public abstract int couleur { get; set; }
  public abstract void dire_quelque_chose ();
}
```
    Il est recommandé de toujours nommer le nom de ses instances par I
    
voici comment utiliser les interfaces
```vala
public class Voiture: ITest {
  public int couleur { get; set; }
  public void dire_quelque_chose () {
    stdout.printf ("Vrrroom Vrroom");
  }
}
```

> Vous pouvez aussi `override` les `abstract`

# Cacher des méthodes

Vous pouvez aussi tout simplement décider de cacher une fonction en recréant une méthode avec le même nom _À ne pas confondre avec `override`_

```vala
class Foo : Object {
    public void my_method () { }
}

class Bar : Foo {
    public new void my_method () { }
}
```

utilisation

```vala
Bar bar = new Bar ();
bar.my_method (); // appele de la fonction my_method de la classe Bar
(bar as Foo).my_method (); // appele de la fonction my_method de la classe Foo
```