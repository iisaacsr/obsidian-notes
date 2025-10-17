
-  Organisation et architecture
-  Fonctionnalités
-  Modules

#### 4 fonctionnalités basiques

**-  Traitement des données**
	Traiter des données pouvant avoir différentes formes (entier, nombre flottants, pointeurs, chaine) ^a9cca2

**-  Stockage de données**
	Les données fixes doivent être stockée (programme, constantes, fichiers) 
	Les données temporaires doivent être stockées (variable, registre, pile)
	Données stockées pour futures utilisations ou mises à jour

**-  Mouvement de données**
	Mouvement interne à l'ordinateur (CPU, memoire. registres)
	Mouvement vers un appareil externe (vers ou depuis les périphériques)

**-  Contrôler les ressources en fonction des instructions**
	Unité de contrôle dirige les ressource de l'ordinateur en fonction des instructions (fonctionne selon le cycle *fetch-decode-execute*)

#### Description d'un ordinateur

Ordinateur = système complexe : **Système hiérarchique**

À chaque niveau, on retrouve les traces de composants (calcul, mémoire, interconnexion)

La fonction basqiue d'un ordinateur est l'exécution d'un programme, consistant à un ensemble d'instructions dans un programme

#### Définitions

**L'architecture** informatique fait référence à la conception, à la structure et au fonctionnement d'un système informatique.

L'ordinateur est composé de plusieurs composants
-  [[Architecture de Processeurs|Processeur (CPU)]]
-  [[Mémoire]]
-  [[Mémoire#Module Entrée-Sortie (I/O)|Périphérique entrée/sortie]]

L'architecture régit comment les composants interagissent ensemble et exécute des tâches. 

Architecture informatique = plusieurs niveaux d'abstraction :

**-  Niveau logique**
	 -  Niveau du circuit
	 -  Conception, mise en oeuvre du circuit électronique utilisant des portes logiques
	 -  Données représentées par des niveaux de tension
	 -  Algèbre booléenne, portes logiques, circuits séquentiels, bascules, verrous ...

**-  Niveau de la microarchitecture**
	-  Niveau de l'organisaation
	-  Disposition des composants, ainsi que leurs interconnexions
	-  Chemin de données, pipelines, mise en cache, hiérarchie mémoire, prédicition de branchement

**-  Niveau du jeu d'instructions**
	-  Les instructions possibles par le processeur (CISC, RISC)
	-  Types de données, modes d'adressages
	-  Registres

**-  Niveau du système d'exploitation**
	-  Gère les composants
	-  Gestion des processus / thread
	-  Gestion de la mémoire, mémoire virtuelle
	-  Gestion des stockages de données

**-  Niveau du langage d'assemblage**
	-  Liée au jeu d'instructions
	-  Instructions en langage assembleur, compréhensible par l'homme
	-  Langage assembleur, gestion mémoires, prise en charge de macro ...
	-  Assembleur : traduction du langage en code machine exécutable

#### Modules à haut niveau d'un ordinateur

-  [[Architecture de Processeurs|Processeur]] (CPU (Central Processing Unit))
-  [[Mémoire|Mémoire]] (RAM, ROM, Disk, cache, registres)
-  [[Mémoire#Module Entrée-Sortie (I/O)|Périphérique entrée/sortie (I/O)]]
	Ces modules peuvent être composée de plusieurs éléments (CPU par exemple)
-  Système de communication
	Pour que tout puisse communiquer ensemble (bus de communication)

Du haut-niveau vers le bas-niveau (se concentrant sur le CPU)

Le CPU est divisé en 3 modules
-  Registres (mémoire interne)
-  Unité arithmétique et logique (traitement)
	VAL-ALU
-  Unité de contrôle
	3 modules (commande et contrôle le fonctionemment du système, etc...)