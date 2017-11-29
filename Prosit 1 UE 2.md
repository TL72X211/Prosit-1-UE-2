# Prosit-1-UE-2
Intégration et maintenance d’un serveur

Prosit 1 UE 2 – Intégration et maintenance d&#39;un serveur

**Mots Clés**

- GLD
- Windows Server
- Linux
- Intranet
- Serveur Sans OS
- Debian
- SI
- Analyser de performances
- Procédures d&#39;installation
- Plan pour ce cas de figure
- Panne
- Signalement

**Besoins**

-  Quoi :** Panne de serveur, plan de sauvegarde (plan de reprise d&#39;activités).
-  Comment :** Installation server + Ecrire un plan + Surveiller perf + paramétrer le serveur.
-  Porqué :** Pour rendre l&#39;infrastructure fonctionnelle et prévoir d&#39;autre problèmes.

**Contraintes**

- Utilisation de Linux (Debian 8.6)

**Problématique**

- Comment créer un plan permettant de gérer les pannes ?
- Comment installer un serveur Linux ?

 Bref,

- Comment rendre une infra fonctionnelle et éviter les pannes en établissant un plan ?

**Généralisation**

- MCO (Maintient en Conditions Opérationnels)

**Hypothèses**

- Il existe un monitor de perf sur linux qui s&#39;appel : System Monitor.
- On doit config l&#39;interface réseau.
- On doit (bien) nommer la machine.
- On doit télécharger des paquets.
- Connection a un DHCP.
- Faire plusieurs types de serveurs à tempo diff.
- Utiliser Apacheu 2.
- Disques en RAID
- Affecter un DNS
- Créer une image « Master ».
- Configurer les droits de plusieurs utilisateurs.
- Configurer un accès distant.

**Plan d&#39;action**

Etudes

- Installation d&#39;un serveur (Qu&#39;est-ce qu&#39;on va mettre dessus ? Dimensionnement)
 - Les applications (Serveur LAMP (Linux, Apache, MySQL, PHP))
 - Le type de Raid
 - Utilisateurs (Nombre, Droits)
 - Stockage (Sauvegarde)
 - Bande-Passante
 - Redondance

- Paramétrer un serveur (Infrastructure réseau, utilisateurs, accès distants, fréquences des MAJs, pare-feu, dimensionnement du serveur)
 - Instal raid
 - Creation Utilisateurs (adduser)
 - Gestion des droits (chgrp (changer groupe), chown (changer owner), chmod (changer les paramètres du fichier))
 - Config ip (nano /etc/network/interfaces, en static ou dhcp) + relancer le service
 - Nom machine (nano /etc/hosts
 - Ssh : apt-get install openssh-server
  - nano /etc/ssh/sshd_config
  - Ne pas autoriser root
  - Autoriser seulement certain users
  - Forger des clés ????
 - Crontab (crontab –e)
 - IPTab
 - FireWall (habitude a prendre, on ferme tous les ports et on ouvre ceux qu'on veut/connait)
  - Mise à jour = Nano /etc/apt/source.list
  - On autorise que les dossiers officiels

- Plan de reprise d&#39;activités
 - procédure appliquée de manière préventive visant en cas 
  - RTO = Return Time Objectif (Temps durant lequel un service peut rester indisponible)
  - RPO = Recovery Point Objective ("temps" de données qui peuvent-être perdues lors d'un incident)

- Sauvegardes (quoi, ou, comment, quand …)
 - Sauvegarde complète
 - Sauvegarde Incrémentielle (sauvegarde en regardant depuis la dernière sauvegarde si ça a changé)
 - Sauvegarde Différentielle (comme l'incrémentielle mais elle cumule tous les changements depuis la dernière sauvegarde **complète**)

- Raid
![Types de Raid](http://www.tonypickett.com/wp-content/uploads/2013/12/allraid.png)

- Solution de monitoring
 - Monit
 - Surveille les deamon (processus en cours de fonctionnement) et vérifie qu'ils fonctionnement correctement et si non, réagit en fonction
 - Permet de vérifier l'état des services et /ou disques / processeurs
 - Top
 - Htop (intéractif)


Réalisations

- Installation LinuxSS
- Ecrire un plan d&#39;installation
- Paramétrer le serveur
- Plan de reprise d&#39;action
- Installer solution de monitoring