
####Installation d'un serveur (Qu'est-ce qu'on va mettre dessus  Dimensionnement) 

####Param�trer un serveur (Infrastructure r�seau, utilisateurs, acc�s distants, fr�quences des MAJs, pare-feu, dimensionnement du serveur) 

####Plan de reprise d'activit�s 
Document permettant � une entreprise de pr�voir les d�marches � entreprendre pour reconstruire et remettre en route un syst�me informatique en cas de sinistre dans le centre informatique.
Il est r�dig� en tenant compte de tous les incidents susceptibles d�engendrer un sinistre  incendie, panne, d�g�ts des eaux. Il doit pr�voir comment sera bascul� le syst�me sinistr� sur un syst�me relais ainsi que quelle personne intervient et dans quel d�lai.
Tout d�abord le PRA d�finit le temps � respecter pour la mise en place du nouveau syst�me et la nature des donn�es devant �tre bascul�es sur le syst�me relais. Ensuite le PRA doit pr�voir l�infrastructure n�cessaire � mettre en place afin de r�pondre aux exigences. 

####Sauvegardes (quoi, ou, comment, quand �) 
Les sauvegardes ont deux buts pr�cis  permettre la restauration de fichiers individuels et la restauration en bloc syst�mes de fichiers entiers.

Le premier permet la restauration d�un fichier unique lors, par exemple d�une mauvaise manipulation qui conduit � la suppression d�un fichier.

Le deuxi�me permet de restaurer enti�rement le syst�me lors de panne mat�rielle.

Chaque type de donn�es poss�dent des besoins de sauvegarde 

-	Syst�me d�exploitation  ces datas ne changent que lors de mises � niveau, lors de l�installation de correctifs de bug ou lorsque des modifications sont n�cessaire pour un logiciel.
-	Logiciels d�applications  changent lors de toute installation, mise � jour ou suppression d�applications.
-	Donn�es d�applications  changent lors de l�utilisation de celle-ci par l�application.
-	Donn�es utilisateurs  changent en fonction des modes d�utilisations des utilisateurs.

Pour effectuer une sauvegarde nous allons avoir besoin d�un logiciel qui doit �tre capables la copie des �l�ments sur le support de sauvegarde mais aussi d�interfacer parfaitement avec les besoins demand�s.
Il faut donc prendre en consid�ration les fonctionnalit�s telle que  la programmation des sauvegardes � un moment pr�cis, la gestion de l�emplacement, de la rotation et de l�utilisation des supports de sauvegarde, la collaboration des diff�rents op�rateurs afin de savoir si le bon support est disponible, la localisation facile par les op�rateurs du support contenant une sauvegarde pr�cise d�un fichier donn�.
De l� deux choix sont alors envisageable  l�achat d�une solution d�velopp�e commercialement ou la cr�ation d�un syst�me de sauvegarde d�velopp� sp�cialement pour ce serveur.
Pour bien choisir une m�thode de sauvegarde il faut prendre en consid�ration ces trois points  

-	Tr�s difficile de changer de logiciel de sauvegarde c'est-�-dire que une fois impl�ment� le logiciel de sauvegarde est utilis� pour une longue dur�e. Le changement de logiciel implique soit la conversion des archives afin qu�elles soient compatibles avec le nouveau logiciel soit la conservation du logiciel original afin d�acc�der aux sauvegardes des archives.

-	Le logiciel doit �tre fiable � 100% (faire la sauvegarde des �l�ments s�lectionner au moment voulu).
-	La restauration des sauvegardes doit �tre fiable � 100%.

Il existe plusieurs types de sauvegardes tels que 

-	Les sauvegardes compl�tes  sauvegarde tous les individuels sur un support de sauvegarde. Les donn�es sauvegard�es ne changent jamais et chaque sauvegarde compl�te cr��e sera identique � la pr�c�dente. Enregistre aveugl�ment toutes les informations sur le support qu�elles aient chang� ou non.
-	Les sauvegardes incr�mentielles  v�rifient si le moment de la modification est post�rieur � la derni�re sauvegarde effectu�e. Si ce n�est pas le cas, le fichier ne sera pas sauvegard� et si �a l�est, le fichier sera sauvegard�. Souvent utilis� avec une sauvegarde compl�te (une compl�te par semaine et incr�mentielles tous les jours).
-	Les sauvegardes diff�rentielles  semblable � la sauvegarde incr�mentielle car dans les deux cas seuls les fichiers modifi�s r�cemment seront sauvegarder. Cependant les sauvegardes diff�rentielles sont cumulatives c'est-�-dire que lorsqu�un fichier a �t� modifi� il sera toujours sauvegard� jusqu�� la prochaine sauvegarde compl�te.

Il existe diff�rent support de sauvegarde dont les plus connus sont 

-	Bande  support bon march�, capacit� de stockage relativement bonne. A des inconv�nients tel que l�usure de la bande et l�acc�s aux donn�es se fait de mani�re s�quentielle. Il faut alors effectuer un suivi des bandes (changer quand elles sont us�es.
-	Disque  plus rapide de tous les supports de stockage en masse. Cependant �a peut �tre un facteur critique lorsque le temps disponible de sauvegarde dans le centre de donn�es est limit� et que la quantit� de donn�es est �lev�es. Ce n�est pourtant pas le meilleur des supports de sauvegarde pour 4 raisons  les disques ne sont g�n�ralement pas amovibles, ils sont co�teux, ils sont fragiles, ne sont pas des supports d�archives.
-	R�seaux  il ne peut servir de support de sauvegarde sans technologies de stockage de masse. Par exemple, en reliant le lien r�seaux rapide � un centre de donn�es.

####Raid 

Le RAID permet de r�partir des donn�es sur plusieurs disques pour am�liorer la s�curit�, la tol�rance aux pannes de l�ensemble du syst�me. 

Il existe diff�rent niveau de RAID 

-	Le 0  association minimum de deux disques ;
-	Le 1  deux disques en mirroring le contenu du disque 1 et copi� sur le disque 2 ;
-	Le 5  minimum trois disques en redondance ;

####Solution de monitoring 

Monit





