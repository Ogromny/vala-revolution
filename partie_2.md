# Constructeurs et destructeurs

### Constructeurs

Vala ne supportes pas la surcharge de constructeur pour la même raison que la surcharge de méthode n'est pas autorisé, ce qui signifie qu'une classe ne peut avoir plusieurs constructeurs avec le même nom. 

Mais ne vous inquiétez pas ce n'est pas un problème puisque Vala supporte les constructeurs nommés.

Si vous voulez faire plusieurs constructeurs vous devez donc vous y prendre comme ceci:

```vala
public class Button: Object {

    public Button(){
        stdout.printf("Je suis dans le constructeur :)");
    }
    
    public Button.avec_label(string label) {
        stdout.printf("Je creer un bouton avec un label: %s", label);
    }
    
    public Button.avec_couleur(string couleur) {
        stdout.printf("Je creer un bouton avec la couleur %s", couleur);
    }
    
}
```

Et pour appeler un constructeur rien de plus simple:

```vala
new Button();
new Button.avec_label("My dick is very big :)");
new Button.avec_couleur("Rouge");
```

### Destructeurs

Pour faire un destructeur il n'y a rien de plus simple:

```vala
public class Button: Object {

    ~Button() {
        stdout.printf("Je suis dans le destructeur, et je vais m'auto-détruire dans quelques instant :|");    
    }
    
}
```


# Manipulation des éléments

    ### ???

# Éléments statiques

    ### ???

# Paramètres optionnels

Pour créer une fonction avec des un ou plusieurs paramètres il suffit simplement de placer un point d'interrogation ( ? ) comme ceci
```vala
void ma_fonction(string a, int? b){
    stdout.printf(a)
}

ma_fonction("salut", null);
ma_fonction("salut", 420);
```