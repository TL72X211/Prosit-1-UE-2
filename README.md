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
- Paramétrer un serveur (Infrastructure réseau, utilisateurs, accès distants, fréquences des MAJs, pare-feu, dimensionnement du serveur)

Voici la listes des paramétrages a effectuer lors du paramétrage:
	- Mise en place du raid
	- Création des utilisateurs (adduser)
	- Gestion des droits (chown - chgrp - chmod)
	- Configuration de l'addresse ip (nano /etc/network/interfaces)
	- Définir le nom d'utilisateur de la machine (nano /etc/hosts - nano /etc/hostname)
	- Mise en place de la gestion à distance (apt-get install openssh-server   -  nano /etc/ssh/ssd_config)
	- Mise en place du pare-feu (iptables)
	- Mise en place des sauvegardes (crontab -e)
	- Plannification des mises à jour 

- Plan de reprise d&#39;activités
- Sauvegardes (quoi, ou, comment, quand …)
- Raid
	- Raid 0
	- Raid 1
	- Raid 5
	- Raid 6
	- Raid 10
	- Raid 50
	- Raid 60

- Solution de monitoring
	- Monit

Une solution de monitoring permet de contrôler à distance l'état de certains services et de certains hardware comme les disques durs.

Réalisations

- Installation LinuxSS
- Ecrire un plan d&#39;installation
- Paramétrer le serveur
- Plan de reprise d&#39;action
- Installer solution de monitoring
