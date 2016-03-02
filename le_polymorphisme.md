# L'héritage

L'héritage permet de faire hériter une classe d'une autre classe, dans le but de lui affecter ses propres variables/méthodes

```vala
class SuperClass : GLib.Object {
    public void method_1() {
        stdout.printf("SuperClass.method_1()\n");
    }
}

class SubClass : SuperClass {
    public void method_1() {
        stdout.printf("SubClass.method_1()\n");
    }
}

SubClass o1 = new SubClass();
o1.method_1(); // SubClass.method_1()
SuperClass o2 = o1;
o2.method_1(); // SuperClass.method_1()
```

Pour empécher ce comportement il faut utiliser les mots-clefs `virtual` et `override`
```vala

```

# Les interfaces

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

# Les types génériques

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

# La redéfinition des méthodes (\*)

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
