# Compte Rendu TP1 - Eloi Desbrosses

## Exercice 2
  ### Manuel
  
    **1. A l’aide du manuel, identifiez le rôle de la commande which.**
    
    Il est possible de consulter le manuel avec la commande ```man which```. Cela donne la page suivante:
    
    ```
    NAME
       which - locate a command
    SYNOPSIS
           which [-a] filename

    DESCRIPTION
           which  returns  the pathnames of the files (or links) which would be executed in the current environment, had its
           arguments been given as commands in a strictly POSIX-conformant shell.  It does this by searching  the  PATH  for
           executable files matching the names of the arguments. It does not canonicalize path names.

    OPTIONS
           -a     print all matching pathnames of each argument

    EXIT STATUS
           0      if all specified commands are found and executable

           1      if one or more specified commands is nonexistent or not executable

           2      if an invalid option is specified
    ```
    
    La manuel donne la définition suivante: 
    
    _"Which returns the pathnames of the files (or links) which would be executed in the current environment..."_
    
    Après avoir utiliser la commande ```which``` sans argument il semblerait que le système ne retourne aucun résultat ou erreur.
    
    Cepentant, en ajoutant un argument comme ```ls``` tel que ```which ls```, le système retourne un chemin tel que:
    
    ```/usr/bin/ls```
    
    En naviguant dans ce dossier, j'ai remarqué qu'un fichier dénomé "_ls_" était présent.
        
    J'en déduis donc que la commande ```which``` permet de localiser le fichier executé lors de l'utilisation d'une commande.
    
    **2. Quand on consulte cette page, comment peut-on rechercher, par exemple, le mot option ?**
    
    Il est possible de rechercher le mot "_option_" en commençant par rechercher les fonctionnalités du manuel à l'aide de l'aide intégré, accessible en tapant ```h```. Cela donne l'écran suivant:
    
    ```
                      SUMMARY OF LESS COMMANDS

      Commands marked with * may be preceded by a number, N.
      Notes in parentheses indicate the behavior if N is given.
      A key preceded by a caret indicates the Ctrl key; thus ^K is ctrl-K.

      h  H                 Display this help.
      q  :q  Q  :Q  ZZ     Exit.
     ---------------------------------------------------------------------------

                               MOVING

      e  ^E  j  ^N  CR  *  Forward  one line   (or N lines).
      y  ^Y  k  ^K  ^P  *  Backward one line   (or N lines).
      f  ^F  ^V  SPACE  *  Forward  one window (or N lines).
      b  ^B  ESC-v      *  Backward one window (or N lines).
      z                 *  Forward  one window (and set window to N).
      w                 *  Backward one window (and set window to N).
      ESC-SPACE         *  Forward  one window, but don't stop at end-of-file.
      d  ^D             *  Forward  one half-window (and set half-window to N).
      u  ^U             *  Backward one half-window (and set half-window to N).
      ESC-)  RightArrow *  Right one half screen width (or N positions).
      ESC-(  LeftArrow  *  Left  one half screen width (or N positions).
      ESC-}  ^RightArrow   Right to last column displayed.
      ESC-{  ^LeftArrow    Left  to first column.
      F                    Forward forever; like "tail -f".
      ESC-F                Like F but stop when search pattern is found.
      r  ^R  ^L            Repaint screen.
    ```
    
    Ont peut donc remarquer que en utilisant la combinaison ```ESC-F``` il est possible de déplacer un curseur sur un patterne recherché.
    
    Une fois la combinaison ```ESC-F``` effectué, une liste de commande est affiché et nous permet de définir un patterne de recherche.
    
    ```
                                  SEARCHING

      /pattern          *  Search forward for (N-th) matching line.
      ?pattern          *  Search backward for (N-th) matching line.
      n                 *  Repeat previous search (for N-th occurrence).
      N                 *  Repeat previous search in reverse direction.
      ESC-n             *  Repeat previous search, spanning files.
      ESC-N             *  Repeat previous search, reverse dir. & spanning files.
      ESC-u                Undo (toggle) search highlighting.
      &pattern          *  Display only matching lines
            ---------------------------------------------------
            A search pattern may be preceded by one or more of:
            ^N or !  Search for NON-matching lines.
            ^E or *  Search multiple files (pass thru END OF FILE).
            ^F or @  Start search at FIRST file (for /) or last file (for ?).
            ^K       Highlight matches, but don't move (KEEP position).
            ^R       Don't use REGULAR EXPRESSIONS.
    ```
    Pour définir un patterne de recherche pour le mot "_option_" il est nécessaire de tapper: ```/option```.
    
    Une fois la commande validé, un passage de la documentation est affiché avec le mot définis dans le patterne
    
    
    **3. Comment quitte-t-on le manuel ?**
    
    Il est possible de quitter la manuel à tout moment en utilisant la touche "_q_". Il peut être nécessaire de l'utiliser plus d'une fois pour sortir
    
    **4. Chaque section du manuel a une première page, qui présente le contenu de la section. Aﬀicher la première page de la section 6; de quoi parle cette section?**
    
    Il est possible d'afficher la première page (la page d'introduction) de la section 6 via la commande ```man 6 intro```. Cela nous donne le résultat suivant:

    ```
    NAME
           intro - introduction to games

    DESCRIPTION
           Section 6 of the manual describes the games and funny little programs available on the system.

    NOTES
       Authors and copyright conditions
           Look  at the header of the manual page source for the author(s) and copyright conditions.  Note that these can
           be different from page to page!

    COLOPHON
           This page is part of release 4.16 of the Linux man-pages project.  A description of the  project,  information
           about    reporting    bugs,    and    the    latest    version    of    this    page,    can   be   found   at
           https://www.kernel.org/doc/man-pages/.
    ``` 
      
      Cette section parle donc des "Jeux et petits programmes marrant disponible sur le système".
      
 ### Navigation dans l'arborescence des fichiers**
    **1. allez dans le dossier /var/log** 
    
    ```
    serveur@serveur:/$ cd /var/log/
    serveur@serveur:/var/log$
    ```

    **2. remontez dans le dossier parent (/var) en utilisant un chemin relatif**
    
    ```
    serveur@serveur:/var/log$ cd ..
    serveur@serveur:/var$
    ```
    
    **3. retournez dans le dossier personnel** 
    
    ```
    serveur@serveur:/var$ cd
    serveur@serveur:$
    ```
    
    **4. revenez au dossier précédent (/var)**
    
    ```
    serveur@serveur:$ cd -
    /var
    serveur@serveur:/var$
    ```
    
    **5. essayez d’accéder au dossier /root; que se passe-t-il?** 
    
    ```
    serveur@serveur:/var$ cd /root
    -bash: cd: /root: Permission denied
    serveur@serveur:/var$
    ```
    
    Une erreur est retourné par le système. Il semblerait que je ne possède pas la permission d'accéder à ce dossier.
    
    **6. essayez la commande sudo cd /root; que se passe-t-il? Expliquez**
    
    ```
    serveur@serveur:/var$ sudo cd /root
    [sudo] password for serveur:
    sudo: cd: command not found
    serveur@serveur:/var$
    ```
    
    Lors de l'utilisation de la commande ```sudo```, notre utilisateur obtient temporairement les droit d'accès du compte administrateur. La commande "_cd_" n'existe pas car le fichier nécessaire n'existe pas. Cela est prouvable via la commande ```sudo which cd```.
    
    Pour cela il est nécessaire d'exécuter le programme sudo à l'air de la commande ```sudo -s```. Une fois cela effectué la commande ```cd /root``` peut être exécuté sans problèmme. Pour sortir du mode administrateur il suffit de quitter le programme sudo à l'aide de ```exit```.

    **7. à partir de votre dossier personnel, créez l’arborescence suivante :**
    
    ```
    root@serveur:~# mkdir Dossier1
    root@serveur:~# touch Dossier1/Fichier1
    root@serveur:~# mkdir Dossier2
    root@serveur:~# mkdir Dossier2/Dossier2.1
    root@serveur:~# mkdir Dossier2/Dossier2.2
    root@serveur:~# touch Dossier2/Dossier2.2/Fichier2
    root@serveur:~# touch Dossier2/Dossier2.2/Fichier3
    ```
    
    **8. revenez dans votre dossier personnel; à l’aide de la commande rm, essayez de supprimer Fichier1, puis Dossier1; que se passe-t-il?** 
    
    ```
    root@serveur:~# rm Dossier1/Fichier1
    root@serveur:~# rm Dossier1
    rm: cannot remove 'Dossier1': Is a directory
    ```
    
    Il est impossible de supprimer un dossier à l'aide de la commande ```rm``` uniquement. Cela retourne une erreur.
    
    **9. quelle commande permet de supprimer un dossier?** 
    
    Il est possible de supprimer un dossier à l'aide de la commande:
    
    ```
    root@serveur:~# rm -d Dossier1
    ```
    
    **10. que se passe-t-il quand on applique cette commande à Dossier2?**
    
    ```
    root@serveur:~# rm -d Dossier2/
    rm: cannot remove 'Dossier2/': Directory not empty
    ```
    
    Il est impossible de supprimer le dossier car celui-ci n'est pas vide. Une erreur est ainsi retourné.
    
    **11. comment supprimer en une seule commande Dossier2 et son contenu**
    
    Cela est possible via la commande:
    
    ```
    root@serveur:~# rm -d -r Dossier2/
    ```
    
## Exercice 3

