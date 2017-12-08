
## **« Server»**
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


## Installation d'un serveur



## Paramétrage d'un serveur

Pour bien commencer le paramétrage d'un serveur web, on suit les étapes suivantes :

* Mise en place d'un RAID numérique si il n'a pas été fait au niveau physique auparavent
* Ajout des utilisateurs qui sont suceptible d'utiliser le serveur
* Ajout des différents droits sur la machine en fonction des utilisateurs créés juste avant
* Configuration de l'interface réseau
* Définir le nom d'hôte de la machine
* Mise en place d'un accès à distance de la machine
* Configuration du pare-feu
* Création des mises à jours automatique ainsi que leur planification


## Plan de reprise d'activité

Le plan de reprise d'activité(PRA - ang DRP) est un processus documenté ou un ensemble de procédures permettant de récupérer et de protéger une infrastructure informatique d'entreprise en cas de sinistre. Un tel plan, généralement documenté sous forme écrite, spécifie les procédures qu'une organisation doit suivre en cas de catastrophe. C'est "une déclaration complète des actions cohérentes à prendre avant, pendant et après une catastrophe". La catastrophe pourrait être naturelle, environnementale ou artificielle. Les catastrophes d'origine humaine pourraient être intentionnelles (par exemple, un acte terroriste) ou involontaires (c'est-à-dire accidentelles, comme la casse d'un barrage artificiel).
Les organisations ne peuvent pas toujours éviter les catastrophes, mais avec une planification minutieuse, les effets d'une catastrophe peuvent être minimisés. L'objectif d'un plan de reprise d'activité est de minimiser les temps d'arrêt et la perte de données. L'objectif principal est de protéger l'organisation dans le cas où tout, ou partie de ses opérations et / ou services informatiques sont rendus inutilisables. Le plan minimise la perturbation des opérations et assure qu'un certain niveau de stabilité organisationnelle et une récupération ordonnée après une catastrophe prévaudront. La minimisation des temps d'arrêt et de la perte de données est mesurée en fonction de deux concepts: l'objectif de temps de récupération (RTO) et l'objectif de point de récupération (RPO).

![](https://image.prntscr.com/image/iZA7IbhkSQeqKi9uLfV9jg.png)

## Sauvegardes 

Les sauvegardes sont des étapes très importantes dans une entreprise ayant besoin d'archives, ou même dans le cadre du PRA. 
Le choix d'une technique de sauvegarde nécessite de prendre en compte :
* la capacité du support (le volume d'informations à stocker) ;
* la vitesse de transfert des données ;
* la fiabilité du support (notamment après une longue période de stockage) ;
* la simplicité de classement ;
* la facilité à restaurer les données ;
* la granularité permise par telle ou telle stratégie, c'est-à-dire la capacité à revenir à un instant donné sur l'état d'une composante du système sauvegardé ;
* les contraintes éventuellement imposées par un PRA ou un PCA ;
* et bien sûr le coût de l'ensemble.

Il existe plusieurs types de sauvegardes :
* Sauvegarde complète, qui sauvegarde la totalité des fichiers présent sur le serveur
* Sauvegarde Incrémentielle
* Sauvegarde Différentielle

L'incrémentielle se base sur la sauvegarde précédente, la différentielle se base sur sa sauvegarde complète. L'incrémentielle nécessite moins d'espace de stockage, mais demande un temps de restauration plus long. La différentielle nécessite plus d'espace de stockage, mais demande un temps de restauration plus court.

En établissement le PRA en amont, nous pouvons déterminer quel est la meilleure planification de sauvegardes en fonction du type de sauvegarde.

## Raid

En informatique, l'acronyme RAID (redundant array of inexpensive disks, maintenant redundant array of independent disks) fait référence à un système de stockage de données utilisant plusieurs disques durs pour partager ou répliquer des données entre les disques. En fonction de la configuration du RAID (niveau de RAID), l'avantage du RAID est d'améliorer l'intégrité des données, la tolérance aux pannes, le débit ou la capacité par rapport aux unités simples.

RAID-5 comprend un tableau de parité en rotation. (Cela signifie que s'il y a 4 disques dans un tableau, les données sont écrites sur 3 des unités de disque et l'espace sur le 4ème disque est utilisé pour la parité - ou un moyen de valider les données de sorte que si un lecteur tombe en panne, les données peuvent être reconstruites sur les 3 disques restants.) Ainsi, toutes les opérations de lecture et d'écriture peuvent se chevaucher. RAID-5 stocke les informations de parité mais pas les données redondantes (mais les informations de parité peuvent être utilisées pour reconstruire les données). RAID-5 nécessite au moins trois et généralement cinq disques pour la baie. Il est préférable pour les systèmes multi-utilisateurs dans lesquels les performances ne sont pas critiques ou qui effectuent peu d'opérations d'écriture.

RAID-1 (aussi appelé Mirroring) : La mise en miroir consiste en au moins 2 unités de disque qui dupliquent le stockage des données. Plus souvent, vous verrez 2 unités de disque ou sur chaque tableau afin que les données en double sont envoyées au second tableau de disques. En tant que tel, si une unité de disque tombe en panne dans la première matrice, le système bascule sur la deuxième matrice de disques fonctionnels, ce qui permet au système de continuer à fonctionner. Cela vous permet d'effectuer une opération continue pendant que vous attendez que le disque défectueux soit réparé et que vous rétablissiez Mirroring.

## Solution de monitoring 

Le monitoring est un service qui permet de constater en temps réel ou sur un temps donné les paramètres des différentes ressources de l'ordinateur, utilisation du processeur, de la ram, du réseau, des disques, etc, etc ...
