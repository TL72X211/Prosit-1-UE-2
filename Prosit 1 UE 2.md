#**« Serveur»**

## **CER UE2.1 : Serveur (29/11/2017)**

-**Mots Clés**

-  GED : gestion électronique des documents, procédé informatisé d&#39;organisation et gestion des information et documents électroniques
-  Windows Server : os pour serveur
-  Linux : OS opensource
-  Intranet : réseau local d&#39;une entreprise
-  Serveur Sans OS :
-  Debian : distribution linux
-  SI : système d&#39;information : ensemble organisé de ressources qui permet de collecter, stocker, traiter et distribuer
-  Analyser de performances
-  Procédures d&#39;installation
-  Plan pour ce cas de figure
-  Panne
-  Signalement

**Besoins**

-  Quoi : Panne de serveur, plan de sauvegarde (plan de reprise d&#39;activités).
- Comment : Installation server + Ecrire un plan + Surveiller perf + paramétrer le serveur.
-  Pourquoi : Pour rendre l&#39;infrastructure fonctionnelle et prévoir d&#39;autre problèmes.

**Contraintes**

-  Utilisation de Linux (Debian 8.6)

**Problématique**

-  Comment créer un plan permettant de gérer les pannes ?
-  Comment installer un serveur Linux ?

Retenue:

-  Comment rendre une infra fonctionnelle et éviter les pannes en établissant un plan ?

**Généralisation**

-  MCO (Maintient en Conditions Opérationnels)

**Hypothèses**

-  Il existe un monitor de perf sur linux qui s&#39;appel : System Monitor.
-  On doit config l&#39;interface réseau.
-  On doit (bien) nommer la machine.
-  On doit télécharger des paquets.
-  Connection a un DHCP.
-  Faire plusieurs types de serveurs à tempo diff.
-  Utiliser Apacheu 2.
-  Disques en RAID
-  Affecter un DNS
-  Créer une image « Master ».
-  Configurer les droits de plusieurs utilisateurs.
-  Configurer un accès distant.

**Plan d&#39;action**

Etudes

I. **Installation d&#39;un serveur (Qu&#39;est-ce qu&#39;on va mettre dessus ? Dimensionnement)**

Les partitions :

Le boot, le var, le root, du swap

II. **Paramétrer un serveur (Infrastructure réseau, utilisateurs, accès distants, fréquences des MAJs, pare-feu, dimensionnement du serveur)**

####Pour changer le nom de machine :

en su : nano /etc/hosts modif puis nano /etc/hostname et on le change aussi

####Config le ssh :

nano etc/ssh/shhd\_config

3eme paragraphe on enlève without password on met yes

Et on fait &quot;service ssh restart&quot;

####Modifier l&#39;IP

Ifconfig on trouve son ip

Nano /etc/network/interface

A la fin enlève dhcp et met static

On entre

address xxx.xxx.xxx.xx

netmask xxx.xxx.xxx.xxx

gateway xxx.xxx.xxx.xxx

####Afficher les connections : 
netstat -natp

####Utilisation/état des disques :
 df

III. **Plan de reprise d&#39;activités**

Abrégé PRA : document qui permet à une entreprise de prévoir les démarches à entreprendre pour reconstruire et remettre en route un système informatique en cas de sinistre important du centre informatique (incendie, panne, inondation)

Le PRA doit prévoir comment sera aculé le système endommagé sur un autre système de relai, qui doit intervenir et sous quel délai.

Il définit tout d&#39;abord le temps de mise en place du nouveau système (RTO : return time on Objective) et les données nécessaires à basculer sur le système de relais (celle vitales pour l&#39;entreprise) (RPO : return Point Objective, perte de données maximale admissible, exprimée en temps car il s&#39;agit du temps entre la dernière sauvegarde et l&#39;incident) ainsi que l&#39;infrastructure nécessaire à mettre en place pour répondre aux exigences.

IV. **Sauvegardes (quoi, ou, comment, quand …)**

But des sauvegardes :

Permettre de restaurer des fichiers individuels (qu&#39;on aurait suppr par accident)

Restaurer un bloc de système de fichiers entiers  (worst case scenario : system breakdown)

Fréquence de sauvegardes : dépends de la fréquence de changement des données

Les données à save :

L&#39;OS à backup aux mises à niveaux, installation de correctifs

Applications : à chaque installation, mise à niveau, suppression

Données d&#39;applications : dès que les applications qui les utilisent sont exe, voir tt les secondes

Données d&#39;utilisateur : dépends

Types de sauvegardes :

- Sauvegardes complètes

On copie colle bêtement mais on peut avoir à copier 100Go là où seul 10Mo ont changés…

- Sauvegardes incrémentielles

Vérifie si le fichier à été modifié entre maintenant et la dernière sauvegarde

- Sauvegardes différentielles

Semblable au incrémentielles au sens où seuls les fichiers modif sont sauvegardés

Ces sauvegardes sont cumulatives on n&#39;écrase pas les saves (avant la prochaine sauvegarde complète ) chaque sauvegarde différentielle contient tous les fichiers modifiés depuis la dernière sauvegarde complète, on peut donc tout restaurer avec la dernière sauvegarde complète et la dernière sauvegarde différentielle

V. **Raid**

RAID :  Redundant Array of Inexpensive (or Independent) Disks, ensemble de techniques de virtualisation de stockage permettant de répartir des données sur plusieurs disques durs pour améliorer soit les perf soit la sécurité ou la tolerance aux pannes

Un système RAID est :

- soit un système de redondance qui donne au stockage des données une certaine tolérance aux pannes matérielles (ex : RAID1).
- soit un système de répartition qui améliore ses performances (ex : RAID0).
- soit les deux à la fois, mais avec une moins bonne efficacité (ex : RAID5).

RAID matériel : utilise une carte ou un composant est dédié (en général un proco spécifique, de la mémoire, voir des batteries de secours)

Il offre à l&#39;OS une virtualisation complète du système de stockage (l&#39;OS ne voit qu&#39;un disque)

Avantages :

- Détecte les défauts, permet le remplacement à chaud des unités défectueuses, permet de reconstruire de manière transparente les disques défaillants
- Faible charge système
- La vérif des cohérences, les diagnostics et les maintenances se font en arrière-plan par le contrôleur

Inconvénients :

Les contrôleurs raid matériels utilisent leur propose système pour gérer les unités de stockage, un transfert de disque ne peut donc se faire qu&#39;avec des contrôleurs RAID identiques (firmware inclut)

Les contrôleurs d&#39;entrée de gamme on des proco bien moins puissant que les ordinateurs actuels, on peut donc avoir des perf inférieures à celles d&#39;un raid logiciel

Coût : entrée de gamme 200€ mais les plus perf &gt;1000€

Le contrôleur lui-même peut tomber en panne, le firmware peut contenir des erreurs

Le support (bugfix) interrompu par la sortie nouveau matériels rendent les anciens obsolètes

Il existe des systèmes de RAID logiciels où le contrôle du RAID est assuré par une couche logicielle

Avantages :

- Méthode la moins cher vu qu&#39;il n&#39;y a pas besoin de matériel dédié au contrôle du raid
- Compatible avec toutes les machines équipées du même logiciel de RAID

Inconvénients :

- On passe par une couche d&#39;abstraction, si elle est imparfaite elle peut manquer certaines fonctions importantes (détection de défaut ma triel par exemple)
- Monopolise le bus système (et un peu le proco), la baisse de perf est donc particulièrement visible en RAID1  où le système transfère plusieurs fois les mêmes données

Niveaux de raid :

RAID 0 :  « entrelacement de disques » ou « volume agrégé par bandes » (_striping_ )

Permet d&#39;augmenter les perf de la grappe en faisant travailler n disques durs en parallèle

La capacité est celle du plus petit élément \* le nombre d&#39;éléments (on risque de gaspiller l&#39;espace supplémentaire des disque plus grand si on ne prend pas des tailles égales)

Il est peu fiable car la perte d&#39;un disque entraîne la perte de toutes les données

RAID 1 : disques en miroir

On utilise n disques redondants où tous les disques contient à tout moment exactement les mêmes données

La capacité est celle de plus petit disque de la grappe

Coût : proportionnel au nombre de miroir

Les accès en lecture de l&#39;OS se font sur le disque le plus facilement accessible au moment donné. Les écritures sur la grappe se font de manière simultanée sur tous les disque afin qu&#39;ils soit interchangeables à tout moment

En cas de défaillance le contrôleur désactive le disque défaillant et une fois remplacé il reconstitue le miroir automatiquement ou sur intervention manuelle

RAID 5

combine la méthode du volume agrégé par bandes (_striping_) à une parité répartie

chaque bande est constituée de n bloc de donnée et de parité, si un disque mal fonctionne on perdra pour chaque bande un bloc de donnée ou un bloc de parité la perte des bloc de parité n&#39;est pas importante et on peut récupérer les blocs de données perdus par calcul avec les n-1 autres blocs de parité

le raid 5 ne supporte la perte que d&#39;un disque à la fois

il existe également d&#39;autres raids peu courants : raid2, raid3, raid4, raid6, raid dp

On peut également combiner des RAID (exemple un RAID 0 fait avec 2 RAID 1)

Saves sur linux :

Sbackup en graphique (pour les faibles et les assistés)

Tar en ligne de commandes :

tar -paramètres opérande1(archive.tar) opérande2(cible)

tar -cvzf /media/votre\_media/home\_de\_guest.tar.gz /home/guest

Le paramètre  **-c**  indique qu&#39;on veut créer une sauvegarde, le paramètre  **-v**  rend la commande un peu plus parlante et le paramètre  **-f**  signifie qu&#39;on doit assembler l&#39;archive dans un fichier. Et -z

Pour restaurer :

 tar -xvzf /media/votre\_media/home\_de\_guest.tar.gz home/guest

-x pour dire qu&#39;on extrait un fichier pour le restaurer

Save incrémentale :

touch -t 07290005 .comparaison

find ~ -newer .comparaison | tar -c -T - -f /media/votre\_media/incr.tar

on créé un fichier dont on fait croire que la date de création est le 29 07 a 00h05

on compare ensuite la date de création du fichier avec le reste du système t tout ce qui a été créé après le fichier .comparaison est envoyé à tar avec un pipe

save par ssh :

on se connecte au ssh

on utilise la commande scp (ssh copy)

scp /emplacement\_archive/backup.tar.gz utilisateur@serveurdistant.exemple.fr

VI. **Solution de monitoring**

Linux en ligne de commande :

Top

Htop , top en mieux (interactif)

Atop : daily log et indic les ressources ayant atteinte la charge critique

Iotop : pour les I/O

Réalisations

- **--** Installation Linux
- **--** Ecrire un plan d&#39;installation
- **--** Paramétrer le serveur
- **--** Plan de reprise d&#39;action
- **--** Installer solution de monitoring
