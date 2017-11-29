
**« Server»**
CER UE2.1 : Server (29/11/2017)

**Mots Clés**
-	GED : Gestion électronique de documents
-	Windows Server :  systèmes d'exploitation orienté serveur de Microsoft (Windows NT. Windows 2000 Server)
-	Linux : Système d’exploitation gratuit sur la base de Unix
-	Intranet : Un intranet est un réseau informatique utilisé à l'intérieur d'une entreprise ou de toute autre entité organisationnelle qui utilise les mêmes protocoles qu'Internet.
-	Serveur Sans OS : Serveur sans système d’exploitation.
-	Debian : Système d’exploitation libre. La version du noyau 
-	SI : Système d’information, c’est l’ensemble des ressources qui permettent de collecter, stocker, traiter et distribuer l’information dans une entreprise.
-	Analyser de performances : Regarder les ressources physiques qu’utilisent l’ordinateur.
-	Procédures d’installation  
-	Plan pour ce cas de figure 
-	Panne
-	Signalement

**Besoins**
-	Quoi : Panne de serveur, plan de sauvegarde (plan de reprise d’activités).
-	Comment : Installation server + Ecrire un plan + Surveiller perf + paramétrer le serveur.
-	Porqué : Pour rendre l’infrastructure fonctionnelle et prévoir d’autre problèmes.

**Contraintes**
-	Utilisation de Linux (Debian 8.6)

**Problématique**
-	Comment créer un plan permettant de gérer les pannes ?
-	Comment installer un serveur Linux ?
 Bref,
-	Comment rendre une infra fonctionnelle et éviter les pannes en établissant un plan ?
**Généralisation**

-	MCO (Maintient en Conditions Opérationnels)
**Hypothèses**
-	Il existe un monitor de perf sur linux qui s’appel : System Monitor.
-	On doit config l’interface réseau.
-	On doit (bien) nommer la machine.
-	On doit télécharger des paquets.
-	Connection a un DHCP.
-	Faire plusieurs types de serveurs à tempo diff.
-	Utiliser Apache 2.
-	Disques en RAID
-	Affecter un DNS
-	Créer une image « Master ».
-	Configurer les droits de plusieurs utilisateurs.
-	Configurer un accès distant.

**Plan d’action**
Etudes 
-	Installation d’un serveur (Qu’est-ce qu’on va mettre dessus ? Dimensionnement)
-	Paramétrer un serveur (Infrastructure réseau, utilisateurs, accès distants, fréquences des MAJs, pare-feu, dimensionnement du serveur)
-	Plan de reprise d’activités
-	Sauvegardes (quoi, ou, comment, quand …)
-	Raid
-	Solution de monitoring
Réalisations
-	Installation Linux
-	Ecrire un plan d’installation
-	Paramétrer le serveur
-	Plan de reprise d’action
-	Installer solution de monitoring









**Table des matières**
CER UE2.1 : Server (29/11/2017)	1
1 – Choix du type de serveur :	4
2 – Mise en place du serveur LAMP :	6
3 – Paramétrage divers :	8
4 – Mise en place du SSH :	11
5 – Fréquences des MAJ et Pare-Feu :	11
6 – RSyn – La sauvegarde synchronisé :	12
7 – Le monitoring :	13
8 – Le plan de reprise d’activité :	13






















**1 – Choix du type de serveur :**
Prérequis matériel : 
 ![](http://www.noelshack.com/2017-48-3-1511967452-1.png)
-	Tout processeurs acceptés
-	Pentium 4 -> 4GHz au minimum
-	2 Go Mini (Sans bureau)
-	128 Mo RAM (mini) mais 512 Mo (Conseillé)
/var contient beaucoup d’informations sur l’état du système.
Les fichiers de dpkg contiennent des informations sur tous les paquets
{…}










**2 : Déterminer quel serveur on a besoin :**
![](http://www.noelshack.com/2017-48-3-1511967671-2.png)

On retrouve ensuite un côté applicatif, selon ce que l’on veut en faire :
-	Authentification
-	Base de données
-	Courier Electronique
-	Gestion d’un réseau
-	Gestion de versions
-	Messagerie Instantanée
-	Partage de bureau / périphériques
-	Sauvegarde
-	Serveur de jeu
-	Supervision
-	Dépôt logiciel
-	HTTP
-	Agrégateur de flux RSS et Atom
-	P2P (pair à pair)
-	Streaming Video
-	TFTP
-	Services Web
-	Galerie Photo Libre
https://doc.ubuntu-fr.org/serveur

Et enfin, on peut administrer le tout grâce à des outils de gestion :
 ![](http://www.noelshack.com/2017-48-3-1511967931-3.png)

**3 : Application à notre situation :**
Nous allons mettre en place un serveur Web LAMP :
C’est un serveur web qui fournit des sites internet, des applications, ou d’autres services accessibles depuis un navigateur web. C’est la configuration la plus courante pour un serveur Web.
 

**2 – Mise en place du serveur LAMP :**

Un tutoriel est très bien expliqué sur le lien : https://doc.ubuntu-fr.org/lamp
1 – Installer Linux (On met l’iso sous clé, puis au boot de la machine, on va dans le Bios, on change paramètre que l’ont doit lire la clé en premier. On redémarre la machine, on accède à l’installation de Linux). On peut mettre en place RAID 1 lors de l’installation (Deux disques dur, qui se dupliquent sur chaque action, permet d’avoir une sauvegarde).
2- Depuis le terminal Linux (sous administrateur)
-	Installer les paquets Apache, PHP, MySQL
sudo apt install apache2 php mysql-server libapache2-mod-php php-mysql

-	Module complémentaires PHP à installer
sudo apt install php-curl php-gd php-intl php-json php-mbstring php-mcrypt php-xml php-zip

On peut tester sous navigateur de se connecter au Localhost pour vérifier la validité.
3 – On configure Apache2 / MySQL
Apache 2 : https://doc.ubuntu-fr.org/apache2
MySQL : https://doc.ubuntu-fr.org/mysql
Ce sont des lignes de commande à rentrer, et des fichiers à modifier.

RAID 1 : C’est quoi ? 
Le RAID est un ensemble de techniques de virtualisation du stockage permettant de répartir des données sur plusieurs disques durs afin d'améliorer soit les performances, soit la sécurité ou la tolérance aux pannes de l'ensemble du ou des systèmes.
 
Le raid est très fortement conseillé à mettre en place lors de la création du serveur. On branche les deux disques durs, qui seront détectés lors de l’installation de LINUX. Il faudra alors lors de la configuration, en déclarer un comme un RAID.
 
Photo de la mise en place du RAID 1 lors de l’installation de Linux.

**3 – Paramétrage divers :**
Modification des mots de passes : 
https://www.it-connect.fr/la-commande-passwd-sous-linux%EF%BB%BF/
 
 
Vérifier les informations IP + Modifier son @IP en statique :
IP Config -> Consulter les interfaces et leurs @IP associés.
/etc/network/interfaces -> Modifier manuellement les informations d’@IP
    auto eth0
    iface eth0 inet static
        address 192.0.2.7
        netmask 255.255.255.0
        gateway 192.0.2.254

Sur une ligne : 	ifconfig <interface> <adresse ip>

MAJ APT :
Apt-get update 
Apt-get upgrade
Apt-get install <nompaquet>


Utilisateurs et droits :
https://openclassrooms.com/courses/reprenez-le-controle-a-l-aide-de-linux/les-utilisateurs-et-les-droits

Vérifier l’état d’un processus et le tuer :
Ps : processus liste
Top : processus liste en temps réel
W : indique quels utilisateurs sont sur la machine, et qu’est-ce qu’ils font
Kill : tuer un processus à partir de son PID. L’option -9 oblige à forcer l’arrêt (pouvant entrainer de la perde de données)
Vérifier les connexions réseaux en cours : 
Netstat : Consulter les ports ouverts/table routage…



Power :
Redémarrer : Reboot
Stop : halt

Vérifier l’état des disques durs :
df

Planifier une tâche journalière :
crontab -e

**On modifie tout à la fin du fichier, et on définit une heure et notre commande**
 
Il est conseillé de redémarrer le service -> service cron restart	
Ça permet à cron de mettre à jour la connaissance des instructions dans son fichier.
On peut par exemple faire des CP à des moments définit, comme les logs, pour les centraliser.
**4 – Mise en place du SSH :**
https://doc.ubuntu-fr.org/ssh

Connaître la version :
ssh -V

Installation:
apt-get install openssh-server

Dans /etc/ssh/sshd_config -> 
\#Change to yes to enable tunnelled clear text passwords
PasswordAuthentication yes

Démarrage : 
service ssh start

On peut aussi authentifier par un système de clé publique / privée (Il faut les générer)

Nb : Port SSH = 22
De nombreuses autres configurations existent.

On peut ensuite regarder son @IP avec Ipconfig, et s’y connecter depuis Putty ou Terraform.
**5 – Fréquences des MAJ et Pare-Feu :**
Fréquence de MAJ -> Toutes les semaines
Vérifier + MAJ
sudo do-release-upgrade --check-dist-upgrade-only


Pare Feu :
Iptables est un puissant firwewall intégré au noyau Linux. Il peut directement être configuré depuis le terminal -> https://wiki.archlinux.fr/iptables
On peut y configurer les @IP autorisés, et ceux interdites.*
On a aussi IPCop, Shorewall, UFW, Vuurmuur, pfSense, IPFire, SmoothWall,EndianConfigServer


**6 – RSyn – La sauvegarde synchronisé :**
https://doc.ubuntu-fr.org/rsync
rsync (pour remote synchronization ou synchronisation à distance), est un logiciel 1) de synchronisation de fichiers. Il est fréquemment utilisé pour mettre en place des systèmes de sauvegarde distante.
rsync travaille de manière unidirectionnelle c'est-à-dire qu'il synchronise, copie ou actualise les données d'une source (locale ou distante) vers une destination (locale ou distante) en ne transférant que les octets des fichiers qui ont été modifiés. (Bien que l’on puisse changer).
 
Lors de la construction, on peut prévoir un RAID :
http://www.jmax-hardware.com/forum/index.php?topic=3360.0
**7 – Le monitoring :**
https://doc.ubuntu-fr.org/monit
monit est un outil de surveillance de services locaux. Il vérifie la disponibilité des *daemons* présents sur le serveur qui l'accueille. En cas de panne, monit peut alerter l'administrateur du système. 
La particularité de monit par rapport à d'autres solutions similaires (Zabbix, Nagios) réside dans le fait qu'il est capable de déclencher des actions pour tenter de rétablir un service interrompu, comme par exemple relancer un serveur Apache si il ne répond plus ou vider la file d'attente d'un serveur Postfix en cas d'engorgement. 
**8 – Le plan de reprise d’activité :**
PER = plan reprise d’activité
C’est un document qui permet à une entreprise de prévoir par anticipation, les démarches à entreprendre pour reconstruire et remettre en route un SI en cas de sinistre important du centre informatique.
3 Questions importantes : 
•	quelles sont les activités essentielles à la survie de l’entreprise ;
•	quelles sont les données nécessaires à ces activités ;
•	quels sont les risques auxquels ces données sont exposées.
On a alors deux notions :
RTO : ( Return Time on Objection) : Temps maximal acceptable durant lequel une ressource informatique peut se trouver indisponible suite à un sinistre.
RPO : Perte de données maximale admissible. (Recovery Point Objective). Exprimée en Minutes / Heures, elle résulte de la différence entre la dernière sauvegarde et l’incident.
 
Conseils :
-	Pensez aux catastrophes
-	Sensibiliser votre personnel
-	Procéder à un inventaire applicatif
-	Etre en accord avec les contraintes réglementaires. (Il faut le tester régulièrement)


