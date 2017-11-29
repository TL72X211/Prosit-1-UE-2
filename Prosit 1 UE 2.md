
####Installation d'un serveur (Qu'est-ce qu'on va mettre dessus  Dimensionnement) 

####Paramétrer un serveur (Infrastructure réseau, utilisateurs, accès distants, fréquences des MAJs, pare-feu, dimensionnement du serveur) 

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

####Raid 

Le RAID permet de répartir des données sur plusieurs disques pour améliorer la sécurité, la tolérance aux pannes de l’ensemble du système. 

Il existe différent niveau de RAID 

-	Le 0  association minimum de deux disques ;
-	Le 1  deux disques en mirroring le contenu du disque 1 et copié sur le disque 2 ;
-	Le 5  minimum trois disques en redondance ;

####Solution de monitoring 

Monit





