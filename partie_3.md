# Visibilités des éléments

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

# Accesseurs

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

# Propriétés

Si vous êtes un programmeur Java vous penserais probablement à quelque chose comme ça

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

oui oui vous avez bien lue, j'ai en même temps déclaré une variable et lui est assigné une valeur, et en même temps fais ça propriétés :)

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

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
