# Compte Rendu TP1 - Eloi Desbrosses

## Exercice 2
  ### Manuel
  
  **1. A l’aide du manuel, identifiez le rôle de la commande which.**
    
  Il est possible de consulter le manuel avec la commande ```man which```. Cela donne la page suivante:
    
  ```
NOM
       which - Localiser une commande

SYNOPSIS
       which [-a] nom_de_fichier...

DESCRIPTION
       which renvoie le chemin des fichiers (ou liens) qui seraient exécutés dans l'environnement courant si ses ar‐
       guments avaient été donnés comme commandes dans un interpréteur de commandes strictement  conforme  à  POSIX.
       Pour  ce faire, which cherche dans la variable PATH les fichiers exécutables correspondant aux noms des argu‐
       ments. which ne normalise pas les chemins.

OPTIONS
       -a     affiche tous les chemins correspondant à chaque argument.

VALEUR DE RETOUR
       0      si toutes les commandes spécifiées sont trouvées et exécutables.

       1      si une (ou plusieurs) commande spécifiée n'existe pas ou n'est pas exécutable.

       2      si une option non valable est spécifiée.

TRADUCTION
       Ce document est une traduction, réalisée par Laëtitia Groslong <lgr@tartine.org>.

       Elle a été reprise avec po4a par Nicolas FRANÇOIS le 29 octobre 2004.

       L'équipe de traduction a fait le maximum pour réaliser une adaptation française de qualité.

       La version anglaise la plus à jour de ce document est toujours consultable en ajoutant l'option « -L C » à la
       commande man.

       N'hésitez  pas  à signaler à l'auteur ou à la liste de traduction <debian-l10-french@lists.debian.org>, selon
       le cas, toute erreur dans cette page de manuel.
  ```
    
  La manuel donne la définition suivante: 
    
  _"which renvoie le chemin des fichiers (ou liens) qui seraient exécutés dans l'environnement courant"_

  Après avoir utiliser la commande ```which``` sans argument il semblerait que le système ne retourne aucun résultat ou erreur.

  Cepentant, en ajoutant un argument comme ```ls``` tel que ```which ls```, le système retourne un chemin tel que:

  ```/usr/bin/ls```
    
  En naviguant dans ce dossier, j'ai remarqué qu'un fichier dénomé "_ls_" était présent.

  J'en déduis donc que la commande ```which``` permet de localiser le fichier executé lors de l'utilisation d'une commande.

  **2. Quand on consulte cette page, comment peut-on rechercher, par exemple, le mot option ?**

  Il est possible de rechercher le mot "_option_" en commençant par rechercher les fonctionnalités du manuel à l'aide de l'aide intégré, accessible en tapant ```h```. Ci-dessous ce trouve une partie de l'écran de résultat:
    
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
         Look at the header of the manual page source for the author(s) and copyright conditions.  Note that these can
         be different from page to page!

  COLOPHON
         This page is part of release 4.16 of the Linux man-pages project.  A description of the project,  information
         about    reporting    bugs,    and    the    latest    version    of    this    page,   can   be   found   at
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

  ### Commandes importantes
  1. Quelle commande permet d’aﬀicher l’heure? A quoi sert la commande time?
  
  Il est possible d'afficher l'heure via la commande ```date```. Cela à pour effet d'afficher la date complète à laquelle le système est paramétré:
  
  ```
  serveur@serveur:~$ date
  lundi 9 septembre 2019, 18:46:40 (UTC+0000)
  ```
  
  Il est cependant possible d'obtenir uniquement l'heure en passant à la commande ```date``` le format de la date désiré:
  
   ```
   serveur@serveur:~$ date +%H:%M:%S
   18:48:45
   ```
   
   La commande ```time``` permet d'exécuter la commande passé en paramètre puis d'afficher le temps d'exécution de celle-ci. Par exemple:
   
   ```
   serveur@serveur:~$ time man which
   real    0m4,291s
   user    0m0,268s
   sys     0m0,017s
   ```
  
  2. Dans votre dossier personnel, tapez successivement les commandes ls puis la; que peut-on en déduire sur les fichiers commençant par un point? 
  
  ```
  serveur@serveur:~$ ls
  serveur@serveur:~$ la
  .bash_logout  .bashrc  .cache  .gnupg  .profile
  serveur@serveur:~$
  ```
  
  D'après les résultats des deux commandes, ont peut en déduire que les fichiers commençant par un point sont caché ou du moins non affiché par la commande de base ```ls```.

  3. Où se situe le programme ls? 
  
  ```
  serveur@serveur:~$ which ls
  /usr/bin/ls
  ```
  
  À partir de la commande ```which``` précédement étudié, il est possible d'en déduire que le programme ls ce situe dans le fichier du même nom et est disponible dans les dossiers ```/usr/bin/```.
  
  4. Que fait la commande ll? (indice : la commande alias peut vous aider).
  
  ```
  serveur@serveur:~$ ll
  total 28
  drwxr-xr-x 4 serveur serveur 4096 sept.  9 17:36 ./
  drwxr-xr-x 3 root    root    4096 sept.  9 17:31 ../
  -rw-r--r-- 1 serveur serveur  220 avril  4 03:11 .bash_logout
  -rw-r--r-- 1 serveur serveur 3771 avril  4 03:11 .bashrc
  drwx------ 2 serveur serveur 4096 sept.  9 17:36 .cache/
  drwx------ 3 serveur serveur 4096 sept.  9 17:36 .gnupg/
  -rw-r--r-- 1 serveur serveur  807 avril  4 03:11 .profile
  serveur@serveur:~$ alias
  alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
  alias egrep='egrep --color=auto'
  alias fgrep='fgrep --color=auto'
  alias grep='grep --color=auto'
  alias l='ls -CF'
  alias la='ls -A'
  alias ll='ls -alF'
  alias ls='ls --color=auto'
  ```
  
  D'après le résultat des deux commandes, ont peut premièrement en conclure que la commande ```ll``` est un alias de la comande ```ls -alF``` ce qui est un raccourcis pour ```ls -a -l -F```.
  
  Cette alias permet de lister tous les fichiers d'un emplacement sous la forme d'une liste contenant les droits du fichier, l'utilisateur ayant créer le fichier ainsi que la date de création/dernière modification.

  5. Quelle commande permet d’aﬀicher les fichiers contenus dans le dossier /bin? 
  
  ```
  serveur@serveur:~$ ls /bin
  ```
  
  6. Que fait la commande ls ..? 
  
  La commande ```ls ..``` permet de lister les éléments du noeud supérieur de l'emplacement ou la commande a été effectué. Les ```..``` permettent de sélectionner le noeud supérieur relativement par rapport à l'emplacement actuel.
  
  7. Quelle commande donne le chemin complet du dossier courant? 
  
  Il s'agit de la commande ```pwd```:
  
  ```
  serveur@serveur:~$ pwd
  /home/serveur 
  ```
  
  8. Que fait la commande echo 'yo' > plop exécutée 2 fois? 
  
  ```
  serveur@serveur:~$ echo 'yo' > plop
  serveur@serveur:~$ cat plop
  yo
  serveur@serveur:~$ echo 'yo' > plop
  serveur@serveur:~$ cat plop
  yo
  ```
  
  D'après le retour de la commande. J'en déduis que le mot 'yo' à été écrit dans le fichier "plop". Cependant lors de la deuxième exécution, un deuxième 'yo' ne s'est pas rajouté mais à écraser le premier.

  9. Que fait la commande echo 'yo' >> plop exécutée 2 fois? 
  
  ```
  serveur@serveur:~$ echo 'yo' >> plop
  serveur@serveur:~$ cat plop
  yo
  serveur@serveur:~$ echo 'yo' >> plop
  serveur@serveur:~$ cat plop
  yo
  yo
  ```
  
  D'après le retour de la commande, J'en déduis que l'opérateur ```>>``` redirige le retour d'une commande en la rajoutant à un fichier. Cela peut créer le fichier si nécessaire.

  10. A quoi sert la commande file? Essayez la sur des fichiers de types différents. 
  
  ```
  serveur@serveur:~$ wget https://bit.ly/2k6gyug picture
  --2019-09-09 20:22:36--  https://bit.ly/2k6gyug
  Resolving bit.ly (bit.ly)... 67.199.248.10, 67.199.248.11
  Connecting to bit.ly (bit.ly)|67.199.248.10|:443... connected.
  ...
  FINISHED --2019-09-09 20:22:36--
  Total wall clock time: 0,8s
  Downloaded: 1 files, 32K in 0,009s (3,46 MB/s)
  serveur@serveur:~$ ls
  2k6gyug  plop
  serveur@serveur:~$ file 2k6gyug
  2k6gyug: JPEG image data, JFIF standard 1.01, aspect ratio, density 1x1, segment length 16, baseline, precision 8, 698x641, components 3
  serveur@serveur:~$ file plop
  plop: ASCII text
  ```
  
  Après avoir télécharger une image et utiliser la commande ```file``` sur celle-ci ainsi que sur le fichier précédemment créer, j'en déduis que la commande file permet d'obtenir plus d'information sur le type de fichier passé en paramètre.

  11. Créez un fichier toto qui contient la chaîne Hello Toto !; créer ensuite un lien titi vers ce fichier avec lacommande ```ln toto titi```. Modifiez à présent le contenu de toto et aﬀichez le contenu de titi. Qu’observe-t-on? Supprimez le fichier toto; quelle conséquence cela a-t-il sur titi?
  
  ```
  serveur@serveur:~$ nano toto
  serveur@serveur:~$ ln toto titi
  serveur@serveur:~$ ls
  titi  toto
  serveur@serveur:~$ nano toto
  serveur@serveur:~$ cat titi
  Hello Tata !
  serveur@serveur:~$ rm toto
  serveur@serveur:~$ ls
  titi
  serveur@serveur:~$ cat titi
  Hello Tata !
  ```
  
  Une fois le lien créer entre toto et titi, toutes les modifications effectué dans le fichier toto seront effectué dans le fichier titi. En revanche, lors de la suppression du fichier toto, le fichier titi ne change pas et reste tel quel.
  
  12. Créez à présent un lien symbolique tutu sur titi avec la commande ```ln -s titi tutu```. Modifiez le contenu de titi; quelle conséquence pour tutu? Et inversement? Supprimez le fichier titi; quelle conséquence cela a-t-il sur tutu? 
  
  ```
  serveur@serveur:~$ ln -s titi tutu
  serveur@serveur:~$ ls
  titi  tutu
  serveur@serveur:~$ nano titi
  serveur@serveur:~$ ls
  titi  tutu
  serveur@serveur:~$ cat tutu
  Hello Tutu !
  serveur@serveur:~$ nano tutu
  serveur@serveur:~$ cat tutu
  Hello World !
  serveur@serveur:~$ cat titi
  Hello World !
  serveur@serveur:~$ rm titi
  serveur@serveur:~$ ls
  tutu
  serveur@serveur:~$ cat tutu
  cat: tutu: No such file or directory
  serveur@serveur:~$
  ```
  
  L'utilisation du paramètre ```-s``` rend le lien symbolique. Cela signifie que les changements opérer dans un fichier sont refléter dans l'autre fichier, dans les deux sens. De plus, lors de la suppression du fichier titi, le fichier tutu devient inexistant.

  13. Aﬀichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et reprendre le défilement à l’écran? 
  
  Les raccourcis claviers permettant d'interrompte et de reprendre le défilement à l'écran sont 
  
  ```CTRL + S``` Pour interrompre le défilement
  
  ```CTRL + Q``` Pour reprendre le défilement

  14. Aﬀichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les lignes 10 à 20. 
  
  ```
  serveur@serveur:~$ head -5 /var/log/syslog
  Sep  9 17:31:22 serveur kernel: [    0.000000] Linux version 5.0.0-27-generic (buildd@lgw01-amd64-016) (gcc version 8.3.0 (Ubuntu 8.3.0-6ubuntu1)) #28-Ubuntu SMP Tue Aug 20 19:53:07 UTC 2019 (Ubuntu 5.0.0-27.28-generic 5.0.21)
  Sep  9 17:31:22 serveur kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-27-generic root=UUID=b79bdec1-94ea-4a1f-9b18-ed0a73e182b9 ro maybe-ubiquity
  Sep  9 17:31:22 serveur kernel: [    0.000000] KERNEL supported cpus:
  Sep  9 17:31:22 serveur kernel: [    0.000000]   Intel GenuineIntel
  Sep  9 17:31:22 serveur kernel: [    0.000000]   AMD AuthenticAMD
  serveur@serveur:~$ tail -15 /var/log/syslog
  Sep  9 17:46:29 serveur systemd[1]: systemd-tmpfiles-clean.service: Succeeded.
  Sep  9 17:46:29 serveur systemd[1]: Started Cleanup of Temporary Directories.
  Sep  9 17:56:29 serveur systemd[1]: Starting Message of the Day...
  Sep  9 17:56:29 serveur 50-motd-news[2086]:  * Congrats to the Kubernetes community on 1.16 beta 1! Now available
  Sep  9 17:56:29 serveur 50-motd-news[2086]:    in MicroK8s for evaluation and testing, with upgrades to RC and GA
  Sep  9 17:56:29 serveur 50-motd-news[2086]:      snap info microk8s
  Sep  9 17:56:29 serveur systemd[1]: motd-news.service: Succeeded.
  Sep  9 17:56:29 serveur systemd[1]: Started Message of the Day.
  Sep  9 18:17:02 serveur CRON[2139]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
  Sep  9 19:17:01 serveur CRON[2348]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
  Sep  9 20:17:01 serveur CRON[2422]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
  Sep  9 20:22:36 serveur systemd-resolved[841]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
  Sep  9 20:22:36 serveur systemd-resolved[841]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
  Sep  9 20:52:49 serveur systemd[1]: session-3.scope: Succeeded.
  Sep  9 20:53:09 serveur systemd[1]: Started Session 7 of user serveur.
  serveur@serveur:~$ sed -n '10,20p' /var/log/syslog
  Sep  9 17:31:22 serveur kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
  Sep  9 17:31:22 serveur kernel: [    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
  Sep  9 17:31:22 serveur kernel: [    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
  Sep  9 17:31:22 serveur kernel: [    0.000000] BIOS-provided physical RAM map:
  Sep  9 17:31:22 serveur kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
  Sep  9 17:31:22 serveur kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
  Sep  9 17:31:22 serveur kernel: [    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
  Sep  9 17:31:22 serveur kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffeffff] usable
  Sep  9 17:31:22 serveur kernel: [    0.000000] BIOS-e820: [mem 0x000000007fff0000-0x000000007fffffff] ACPI data
  Sep  9 17:31:22 serveur kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
  Sep  9 17:31:22 serveur kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
  ```
  
  15. Que fait la commande dmesg | less? 
  
  La commande ```dmesg``` permet d'obtenir tous les messages du noyaux kernel et la commande ```less``` permet de réduire les données d'un fichier ou d'une chaine de caractère pour devenir plus lisible.
  La combinaison de ces deux commandes via l'opérateur ```|``` permet d'obtenir tous les messages du noyaux kernel de manière simplifié afin d'être plus lisible.
  
  16. Aﬀichez à l’écran le fichier /etc/passwd; que contient-il? Quelle commande permet d’aﬀicher la page de manuel de ce fichier? 
  
  ```
  serveur@serveur:~$ cat /etc/passwd
  root:x:0:0:root:/root:/bin/bash
  daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
  bin:x:2:2:bin:/bin:/usr/sbin/nologin
  sys:x:3:3:sys:/dev:/usr/sbin/nologin
  sync:x:4:65534:sync:/bin:/bin/sync
  games:x:5:60:games:/usr/games:/usr/sbin/nologin
  man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
  lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
  mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
  news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
  uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
  proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
  www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
  backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
  list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
  irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
  gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
  nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
  systemd-timesync:x:100:102:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
  systemd-network:x:101:103:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
  systemd-resolve:x:102:104:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
  messagebus:x:103:106::/nonexistent:/usr/sbin/nologin
  syslog:x:104:109::/home/syslog:/usr/sbin/nologin
  _apt:x:105:65534::/nonexistent:/usr/sbin/nologin
  uuidd:x:106:110::/run/uuidd:/usr/sbin/nologin
  landscape:x:107:114::/var/lib/landscape:/usr/sbin/nologin
  pollinate:x:108:1::/var/cache/pollinate:/bin/false
  sshd:x:109:65534::/run/sshd:/usr/sbin/nologin
  systemd-coredump:x:999:999:systemd Core Dumper:/:/sbin/nologin
  serveur:x:1000:1000:serveur:/home/serveur:/bin/bash
  lxd:x:998:100::/var/snap/lxd/common/lxd:/bin/false
  ```
  
  Il est possible d'afficher la page manuel de ce fichier via la commande ```man passwd```
  
  17. Aﬀichez seulement la première colonne triée par ordre alphabétique inverse
  
  18. Quelle commande nous donne le nombre d’utilisateurs? 
  
    ```[commande de la question précédente] | wc -l```
    
  19. Combien de pages de manuel comportent le mot-clé conversion dans leur description? 
  
  ```
  serveur@serveur:~$ man -k conversion |wc -l
  4
  ```
  
  20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine 
  
  ```
  find / -name passwd
  ```
  
  21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null 
  
  ```
  find / -name passwd >> ~/list_passwd_files.txt 2>> /dev/null
  ```
  
  22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu précédemment 
  
  ```
  serveur@serveur:~$ grep "ll" -r
  .bash_logout:# ~/.bash_logout: executed by bash(1) when login shell exits.
  .bashrc:# ~/.bashrc: executed by bash(1) for non-login shells.
  .bashrc:# If set, the pattern "**" used in a pathname expansion context will
  .bashrc:# match all files and zero or more directories and subdirectories.
  .bashrc:    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
  .bashrc:alias ll='ls -alF'
  .bashrc:# You may want to put all your additions into a separate file like
  .profile:# ~/.profile: executed by the command interpreter for login shells.
  .profile:# for ssh logins, install and configure the libpam-umask package.
  .bash_history:ll
  ```

  D'après le résultat de la commande précédente, l'alias ll est donc définis dans le fichier .bashrc.

  23. Utilisez la commande locate pour trouver le fichier history.log.
  
  ```
  serveur@serveur:~$ locate history.log
  /var/log/apt/history.log
  ```

  24.Créer un fichier dans votre dossier personnel puis utilisez locate pour letrouver. Apparaît-il?Pourquoi?
  
  ```
  serveur@serveur:~$ touch fichier
  serveur@serveur:~$ ls
  fichier
  serveur@serveur:~$ locate fichier
  serveur@serveur:~$ updatedb
  updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'
  serveur@serveur:~$
  ```
  
  la commande ```locate``` ne trouve pas le nouveau fichier créer. Cela est normal car selon le manuel: _"locate  reads  one or more databases prepared by updatedb(8) and writes file names matching atleast one of the PATTERNs to standard output, one per line."_. Comme la base n'a pas été mis à jour via la commande ```updatedb``` le fichier n'est pas trouvé.
  
  
  ### Travailler avec plusieurs shells
  
  On peut utiliser jusqu’à 6 shells en parallèle. Ils portent les noms ttyX (où X va de 1 à 6) et sont accessibles via Alt + F
  
## Exercice 3 Découverte de l’éditeur de texte nano

