## Installer Vala
### Sur GNU/Linux
Sur la plupart des distributions Linux, il vous suffira d'installer le paquet `valac`, et si ce n'est déjà fait le paquet `build-essential`.

Pour **Debian** (avec root) : `aptitude install build-essential valac`
Pour **Ubuntu** : `sudo aptitude install build-essential valac`

Vous pouvez également passer par la compilation des sources, disponibles sur [les pages du projet Vala](http://live.gnome.org/Vala/Release). Cette solution est **fortement déconseillée** aux débutants et aux personnes ne maîtrisant pas l'Art de la Compilation, mais elle fonctionne aussi et permet d'accéder aux dernières versions.

### Sur Windows
Valac fonctionne sous Windows. Vous pouvez le compiler à partir des sources, ou utiliser l'installeur qui regroupe valac, gcc (mingw) et GTK+ : [vala 0.5.6](http://code.google.com/p/valide/downloads/detail?name=vala-0.5.6.exe).

## Programmer avec Eclipse
Il existe un plugin Vala pour Eclipse, baptisé Valable, disponible ici : [https://launchpad.net/valable (en)](https://launchpad.net/valable). Vous pouvez également trouver des instructions (en anglais) pour l'installation là : [http://www.internettablettalk.com/forums/showpost.php?p=218548&postcount=57 (en)](http://www.internettablettalk.com/forums/showpost.php?p=218548&postcount=57).

Le plugin n'a pas l'air terminé, et le développement a l'air au point mort…

## Programmer avec Val(a)IDE
Il existe un environnement de développement pour Vala, et codé en Vala, baptisé Val(a)IDE. Vous pouvez le retrouver sur la page [http://www.valaide.org/doku.php?id=:fr:start (fr)](http://www.valaide.org/doku.php?id=:fr:start).

### Sur Ubuntu
Il est nécessaire de compiler Vala en version 0.5.6, le paquet des dépôts étant en version 0.3.5, puis de compiler Valide ensuite.

### Sur Debian
Il existe un paquet [disponible ici](http://www.valaide.org/doku.php?id=:fr:start#telechargement).

## Programmer avec gEdit
On peut programmer en Vala avec gEdit et l'installation du plugin ValaToys. Ce plugin requiert actuellement la version 0.5.6 de Vala, et comme il n'existe pas actuellement de paquet (de même que pour la version 0.5.6 de Vala), il faut le compiler manuellement à partir des sources qui se trouvent [ici](http://code.google.com/p/vtg/downloads/list). Une fois installé, il faut aller dans les préférences, puis dans l'onglet « greffons » activer le plugin nommé « **Vala developer toys** » qui devrait se trouver dans la liste.

Le plugin n'a pas l'air entièrement fonctionnel et souffre de quelques bugs, mais le développement est très actif. Affaire à suivre…

## Programmer avec Geany

Il n'existe pas de plugin Vala pour Geany à l'heure actuelle, mais avec un petit peu de bidouille c'est désormais la meilleure option que j'ai trouvé. Toute l'astuce repose sur le fait que Geany ouvre les fichiers Vala en les considérant comme des fichiers C#, et qu'il est possible de personnaliser la commande à lancer au moment de la compilation. Geany n'étant pas le seul outil utilisable pour coder du C# (MonoDevelop le permet également, et très bien), cela n'est pas gênant de remplacer la commande de compilation de ces fichiers.

J'ai donc fabriqué un petit utilitaire (bien incomplet à ce jour), permettant de parser les fichiers Vala et de lancer le compilateur valac avec les options appropriés. Voici le code source :

```vala
using GLib;

class GeanyValaHelper : Object {

   public static void main (string[] args) {

      if (args.length > 1) {
         foreach (string s in args) {
            if (s.has_suffix(".vala")) {
               compile(s);
            }
         }
      } else {
         try {
            string filename;
            Dir dir = Dir.open(".");

            while ((filename = dir.read_name()) != null) {
               if (filename.has_suffix(".vala")) {
                  compile(filename);
               }
            }
         } catch (Error e) {

         }
      }
   }

   private static void compile(string filename) {

      try {
         string content;
         FileUtils.get_contents(filename, out content);
         content = replace(content, " |\n", "");

         string[] splitted_content = content.split(";");

         string cmd = "valac ";
         foreach (string s in splitted_content) {
            if (s.has_prefix("using") && getLib(s) != "GLib") {
               cmd += "--pkg "+getLib(s)+" ";
            }
         }
         cmd += "-o "+basename(filename, ".vala")+" "+filename;


         stdout.printf("Compiling : "+filename);
         Process.spawn_command_line_sync(cmd);
      } catch (Error e) {

      }
   }

   private static string getLib(string s) {

      string result = replace(s, " |\n|using", "");

      /*** Zone à compléter ***/

      if (result == "Gtk")
         result = "gtk+-2.0";
      else if (result == "Cairo")
         result = "cairo";

      return result;
   }

   private static string basename(string filename, string extension) {

      return replace(filename, extension, "");
   }

   private static string replace(string s, string pattern, string replacement) {

      string result = s;

      try {
         result = (new Regex(pattern)).replace(s, s.size(), 0, replacement);
      } catch (Error e) {

      }

      return result;
   }
}
```

Vous remarquerez la zone à compléter, avec le mapping entre les noms de librairies utilisés dans les clauses **using**, et les ceux pour le compilateur valac.

Vous pouvez compiler ce code, en supposant que vous l'ayez enregistré sous le nom **geany_vala_helper.vala** avec la commande :
```bash
valac -o geany_vala_helper geany_vala_helper.vala
```

Vous pouvez ensuite utiliser le binaire compilé par Geany, en allant dans le menu **Construire > Définir les includes** et les options, puis en remplaçant le champs **Compiler** par :
```
/le/chemin/complet/du/fichier/geany_vala_helper %f
```

**/!\\** N'oubliez pas de remplacer **/le/chemin/complet/du/fichier/** par la valeur qui convient dans votre cas.

Vous pouvez ensuite coder avec Geany : la coloration syntaxique est **à peu près correcte**, et vous pouvez compiler puis exécuter les fichiers d'un clic sur la barre d'outils. Vous ne bénéficiez pas, par contre, de débuggeur dignes de ce nom…
