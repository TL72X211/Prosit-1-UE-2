

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

