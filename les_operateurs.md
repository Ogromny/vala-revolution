# Opérateurs d'assignation
---
Opérateur | Rôle | Description  
--  |---              |--
=   | Affectation     |  Affecte le membre de droite au membre de gauche
+=  | Addition        | Additionne ou concatène le membre de droite au membre de gauche
-=  | Soustraction    | Soustrait le membre de droite au membre de gauche
\*=  | Multiplication  | Multiplie le membre de gauche
/=  | Division        | Divise le membre de gauche
%=  | Modulo          | Divise le membre de gauche et garde le reste
---

Voici des exemples d'utilisation :
```vala
int a = 2; // a vaut 2

a += 3; // a vaut 5

a -= 1; // a vaut 4

a *= 2; // a vaut 8

a /= 4; // a vaut 2

a = 37;

a %= 6; // a vaut 1

string b = "Coucou"; // b vaut "Coucou"

b += " Toi !"; // b vaut "Coucou Toi !"
```

# Opérateurs de calcul
---
Opérateur  | Rôle  | Description  
--|---|--
+  | Addition  | Additionne ou concatène deux valeurs
-  | Soustraction  | Soustrait deux valeurs  
*  | Multiplication  | Multiplie deux valeurs
/  | Division  | Divise deux valeurs
%  | Modulo  | Divise deux valeurs et garde le reste
---

Voici des exemples d'utilisation :
```vala
int a = 6;
int b = 14;
int c = 7;
int d;

d = a + b; // d vaut 6 + 14 = 20

d = b - c; // d vaut 14 - 7 = 7

d = c * 2; // d vaut 7 * 2 = 14

d = b / c; // d vaut 14 / 7 = 2

d = c % a; // d vaut 7 modulo 6 = 1

string texte = "Coucou" + " " + "Toi !"; // texte vaut "Coucou Toi !"
```

# Opérateurs de comparaison
---
Opérateur  | Rôle  | Description
--|---|--
==  | Égal  | Renvoi vrai si les deux membres sont égaux
!=  | Inégal  | Renvoi vrai si les deux membres ne sont pas égaux
<  | Strictement inférieur  | Renvoi vrai si le membre de gauche est strictement inférieur au membre de droite  
<=  | Inférieur ou égal  | Renvoi vrai si le membre de gauche est inférieur ou égal au membre de droite
\>  | Strictement supérieur  | Renvoi vrai si le membre de gauche est strictement supérieur au membre de droite
=>  | Supérieur ou égal  | Renvoi vrai si le membre de gauche est supérieur ou égal au membre de droite
---

Voici des exemples d'utilisation :
```vala
int a = 5;

if (a == 5)
  stdout.printf("Condition 1 vraie\n"); // ligne exécutée car a vaut 5
else
  stdout.printf("Condition 1 fausse\n"); // ligne ignorée

if (a != 7)
  stdout.printf("Condition 2 vraie\n"); // ligne éxécutée car a est différent de 7
else
  stdout.printf("Condition 2 fausse\n"); // ligne ignorée

if (a < 3)
  stdout.printf("Condition 3 vraie\n"); // ligne ignorée car a est plus grand que 3
else
  stdout.printf("Condition 3 fausse\n"); // ligne éxécutée

if ( a <= 5 )
  stdout.printf("Condition 4 vraie\n"); // ligne éxécuté car a est égal à 5
else
  stdout.printf("Condition 4 fausse\n"); // ligne ignorée

if ( a > 5 )
  stdout.printf("Condition 4 vraie\n"); // ligne ignorée car a est égal à 5
else
  stdout.printf("Condition 4 fausse\n"); // ligne éxécutée

if ( a >= 5 )
  stdout.printf("Condition 4 vraie\n"); // ligne exécutée car a est égal à 5
else
  stdout.printf("Condition 4 fausse\n"); // ligne ignorée
```

# Opérateurs logiques
---
Opérateur  | Rôle  | Description  
--|---|--
&&  | Et  | Renvoi vrai si les deux membres valent vrai
&#124;&#124;  | Ou  | Renvoi vrai si au moins un des membres vaut vrai
!  | Non  | Renvoi vrai si l'expression renvoit faux
---

Voici des exemples d'utilisation :
```vala
bool a = true;
bool b = true;
bool c = false;

if (a && b)
  stdout.printf("Condition 1 vraie\n"); // ligne exécutée car (a && b) vaut vrai
else
  stdout.printf("Condition 1 fausse\n"); // ligne ignorée

if (a || c)
  stdout.printf("Condition 2 vraie\n"); // ligne éxécutée car (a || d) vaut vrai
else
  stdout.printf("Condition 2 fausse\n"); // ligne ignorée

if (a && c)
  stdout.printf("Condition 3 vraie\n"); // ligne ignorée car (a && c) vaut faux
else
  stdout.printf("Condition 3 fausse\n"); // ligne éxécutée

if (a || b || c) // on peut enchainer les opérateurs logiques...
  stdout.printf("Condition 4 vraie\n"); // ligne éxécutée
else
  stdout.printf("Condition 4 fausse\n"); // ligne ignorée

if ( (a && b) || ( b && c) ) // ...et utiliser des parenthèses
  stdout.printf("Condition 5 vraie\n"); // ligne éxécutée
else
  stdout.printf("Condition 5 fausse\n"); // ligne ignorée
```

# Opérateurs d'incrémentation
---
Opérateur  | Rôle  | Description  
--|---|--
++  | Incrémentation  | Ajoute 1  
--  | Décrémentation  | Enlève 1
---

Voici des exemples d'utilisation :
```vala
int a = 6; // a vaut 6
a++; // a vaut 7
a--; // a vaut 6
```
