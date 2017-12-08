
####Installation d'un serveur (Qu'est-ce qu'on va mettre dessus  Dimensionnement) 
Lors de l'installation du serveur nous devons partitionner le disque en 4 : un pour le boot, un pour le root, un pour le var et le dernier pour le swap.
####Paramétrer un serveur (Infrastructure réseau, utilisateurs, accès distants, fréquences des MAJs, pare-feu, dimensionnement du serveur) 
Afin de paramétrer notre serveur nous pouvons effectuer différente action tel que :
	- La modification du nom de serveur en faisant la manipulation suivante : (en administrateur) "nano /etc/hosts" de la on modifie le nom puis on fait "nano /etc/hostname" et on change ici aussi le nom.
	- Configurer le ssh avec : "nano etc/ssh/sshd_config" dans le 3° paragraphe il faut enlevé "without password" et on met "yes" ensuite il faut faire "service ssh restart".
	- Modifier l'addresse IP avec : "ifconfig" pour trouve l'IP ensuite, il faut faire "nano /etc/network/interface" dedans il nous faut remplacer "dhcp" par "static" ensuite il nous faut rentrer "address xxx.xxx.xxx.xxx netmask xxx.xxx.xxx.xxx gateway xxx.xxx.xxx.xxx"
	- Aficher les connections avec : netstat -natp
	- Afficher état/utilisation disque : df
####Plan de reprise d'activités 
Document permettant à une entreprise de prévoir les démarches à entreprendre pour reconstruire et remettre en route un système informatique en cas de sinistre dans le centre informatique.
Il est rédigé en tenant compte de tous les incidents susceptibles d’engendrer un sinistre  incendie, panne, dégâts des eaux. Il doit prévoir comment sera basculé le système sinistré sur un système relais ainsi que quelle personne intervient et dans quel délai.
Tout d’abord le PRA définit le temps à respecter pour la mise en place du nouveau système et la nature des données devant être basculées sur le système relais. Ensuite le PRA doit prévoir l’infrastructure nécessaire à mettre en place afin de répondre aux exigences. 

####Sauvegardes (quoi, ou, comment, quand …) 
Les sauvegardes ont deux buts précis  permettre la restauration de fichiers individuels et la restauration en bloc systèmes de fichiers entiers.

Le premier permet la restauration d’un fichier unique lors, par exemple d’une mauvaise manipulation qui conduit à la suppression d’un fichier.

Le deuxième permet de restaurer entièrement le système lors de panne matérielle.

Chaque type de données possèdent des besoins de sauvegarde 

-	Système d’exploitation  ces datas ne changent que lors de mises à niveau, lors de l’installation de correctifs de bug ou lorsque des modifications sont nécessaire pour un logiciel.
-	Logiciels d’applications  changent lors de toute installation, mise à jour ou suppression d’applications.
-	Données d’applications  changent lors de l’utilisation de celle-ci par l’application.
-	Données utilisateurs  changent en fonction des modes d’utilisations des utilisateurs.

Pour effectuer une sauvegarde nous allons avoir besoin d’un logiciel qui doit être capables la copie des éléments sur le support de sauvegarde mais aussi d’interfacer parfaitement avec les besoins demandés.
Il faut donc prendre en considération les fonctionnalités telle que  la programmation des sauvegardes à un moment précis, la gestion de l’emplacement, de la rotation et de l’utilisation des supports de sauvegarde, la collaboration des différents opérateurs afin de savoir si le bon support est disponible, la localisation facile par les opérateurs du support contenant une sauvegarde précise d’un fichier donné.
De là deux choix sont alors envisageable  l’achat d’une solution développée commercialement ou la création d’un système de sauvegarde développé spécialement pour ce serveur.
Pour bien choisir une méthode de sauvegarde il faut prendre en considération ces trois points  

-	Très difficile de changer de logiciel de sauvegarde c'est-à-dire que une fois implémenté le logiciel de sauvegarde est utilisé pour une longue durée. Le changement de logiciel implique soit la conversion des archives afin qu’elles soient compatibles avec le nouveau logiciel soit la conservation du logiciel original afin d’accéder aux sauvegardes des archives.

-	Le logiciel doit être fiable à 100% (faire la sauvegarde des éléments sélectionner au moment voulu).
-	La restauration des sauvegardes doit être fiable à 100%.

Il existe plusieurs types de sauvegardes tels que 

-	Les sauvegardes complètes  sauvegarde tous les individuels sur un support de sauvegarde. Les données sauvegardées ne changent jamais et chaque sauvegarde complète créée sera identique à la précédente. Enregistre aveuglément toutes les informations sur le support qu’elles aient changé ou non.
-	Les sauvegardes incrémentielles  vérifient si le moment de la modification est postérieur à la dernière sauvegarde effectuée. Si ce n’est pas le cas, le fichier ne sera pas sauvegardé et si ça l’est, le fichier sera sauvegardé. Souvent utilisé avec une sauvegarde complète (une complète par semaine et incrémentielles tous les jours).
-	Les sauvegardes différentielles  semblable à la sauvegarde incrémentielle car dans les deux cas seuls les fichiers modifiés récemment seront sauvegarder. Cependant les sauvegardes différentielles sont cumulatives c'est-à-dire que lorsqu’un fichier a été modifié il sera toujours sauvegardé jusqu’à la prochaine sauvegarde complète.

Il existe différent support de sauvegarde dont les plus connus sont 

-	Bande  support bon marché, capacité de stockage relativement bonne. A des inconvénients tel que l’usure de la bande et l’accès aux données se fait de manière séquentielle. Il faut alors effectuer un suivi des bandes (changer quand elles sont usées.
-	Disque  plus rapide de tous les supports de stockage en masse. Cependant ça peut être un facteur critique lorsque le temps disponible de sauvegarde dans le centre de données est limité et que la quantité de données est élevées. Ce n’est pourtant pas le meilleur des supports de sauvegarde pour 4 raisons  les disques ne sont généralement pas amovibles, ils sont coûteux, ils sont fragiles, ne sont pas des supports d’archives.
-	Réseaux  il ne peut servir de support de sauvegarde sans technologies de stockage de masse. Par exemple, en reliant le lien réseaux rapide à un centre de données.

Pour sauvegarder sous Linux il nous faut utiliser Tar :
	-Sauvegarde :  tar -paramètres opérande1(archive.tar) opérande 2(cible)
	exemple : tar -cvzf /media/notre_media/home_guest.tar.gz /home/guest
		Le paramètre -c indique la création d'une sauvegarde, le paramètre -v rend la commande parlante, le paramètre -f signifie l'assemblage de l'archive dans un fichier et -z ajoute la compression Gzip.
	- Restauration : tar -xvzf /media/notre_media/home_guest.tar.gz home/guest
		Le paramètre -x indique la restauration.
	- Sauvegarde incrémentale : touch -t 12080025 .comparaison -> on créé un fichier avec une date de création au 08/12 a 00:25.
						   find ~ - newer .comparaison | tar -c -X - -f /media/notre_media/incr.tar on compare la date de création du fichier avec le reste du système X. Tout ce qui a été créé après le fichier est envoyé au tar.
	- Sauvegarde depuis le ssh avec : Il faut au préalable se connecter au ssh, ensuite nous devrons utiliser la commande scp (ssh copy) : scp /emplacement_archive/save.tar.gz user@servDist.exemple.fr

####Raid 

Le RAID (Redundant Array of Independent Disks) est un ensemble de techniques de virtualisation du stockage permettant de répartir des données sur plusieurs disques durs afin d'améliorer les performances, la sécurité ou la tolérance aux pannes de l'ensemble du système. 

Il existe plusieurs types de RAID les deux les plus connus sont :

- Le RAID logiciel : le RAID est contrôlé par une couche logiciel du SE. Cette couche se situe entre la couche d'abstraction matérielle et la couche du systèmes de fichiers. 
	* Les avantages de ce type de RAID sont : 
>* Méthode de RAID la moins chère car elle ne demande pas de matériel supplémentaire;
>* Méthode possédant une grande souplesse d'administration;
>* Méthode présentant l'avantage de la compatibilité entre toutes les machines possédant le même logiciel de RAID;

	* Les inconvénients de ce type de RAID sont:
		>* Le fait que cette méthode repose sur la couche d'abstraction matérielle des périphériques composant le RAID;
		>* La gestion du RAID monopolise des ressources systèmes qui pourraient être utilisé à d'autre fins;
		>* L'utilisation du RAID sur le disque système n'est pas toujours possible;

- Le RAID matériel : Une carte ou un composant est dédié à la gestion des opérations. Le contrôleur RAID peut être interne à l'unité centrale ou déporté dans une baie de stockage. Un contrôleur RAID est en général doté d'un processeur spécifique, de mémoire, éventuellement d'une batterie de secours et est capable de gérer tous les aspects du système de stockage RAID grâce au microcode (microprogrammation) embarqué.
* Les avantages :
	>* Les contrôleur RAID matériels permettent la détection des défauts le remplacement des unités défectueuses à chaud et offrent la possibilité de reconstruire de manière transparente les disque défaillant;
	>* La charge système est allégée;
	>* Les vérifications de cohérence, les diagnostics et les maintenances sont effectués par le contrôleur en arrière-plan;
	
* Les inconvénients :
	>* 
Il existe différents niveaux de RAID:
	- Le RAID 0 : configuration RAID permettant d'augmenter les performances en faisant travailler n disques durs en parallèle;
	- Le RAID 1 : utilisation de n (minimum 2) disques redondants, chaque disque de la grappe contenant à tout moment exactement les mêmes données, on appelle cela du mirroring;
	- Le RAID 5 : nécessite 3 disque et assure la redondance des données en stockant des informations de parité grâce à la copie en miroir lui permettant d'exploiter l'espace disponible plus efficacement que le RAID 1. Il supporte la perte d'un disque;
####Solution de monitoring 





