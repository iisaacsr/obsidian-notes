### Module: Processeur

Processeur ou CPU (Central Processing Unit)

Le CPU est composé de :
-  Unité de contrôle
	Contrôlant le CPU, donc l'ordinateur
-  Unité Arithmétique Logique (UAL)
	ALU (Arithmetic Logic Unit)
	Traitement des données
-  Registres
	Stockage interne des données
-  Interconnexion CPU
	Permet la communication entre les 3 modules précédents

Processeur : terme génériquement désignant l'unité de traitement central dans un système informatique, qu'il soit grand ou petit.

-  Applications : Serveurs, sytèmes informatiques haut de gamme
-  Puissance de traitement : Puissance de traitement plus élebée que les microprocesseur

Ce terme est si générique qu'on va aussi englober les systèmes sur une puce (system-on-chip)

#### Suite

La version la plus simple est un processeur avec un seul ALU
-  *single-processor*, *single-core*
-  Architecture SISD (Single Instruction Single Data)
-  Aucun parallélisme (multi-threading) possible

Ceci n'existe plus aujourd'hui (aucun ordi avec un seul ALU vraiment)

Si l'ordinateur a plusieurs processeurs résidant dans une mpeme puce, chaque unité de traitement (unité de contrôle, ALU, registres) est **un coeur**

#### Performance

Les performances d'un CPU sont déterminées par une combinaison de facteurs dont
-  Fréquence d'horloge
-  Architecture utilisée
-  Ensemble d'instructions
-  Efficacité

#### Multicore

CPU : Portion de l'ordinateur récupérant et exécutant les instructions. Il est consisté d'une unité de contrôle, ALU et de registres.

Coeur : Unité de traitement à l'intérieur d'une puce. Équivalent d'un CPU dans un système single-CPU.

Aujourd'hui, les CPU ont plusieurs coeurs (une i9 de génération actuelle a 24 coeurs.

### Microprocesseur

#todo maybe could add more

Microprocesseur est un processeur miniature et autonome conçu pour être intégré dans des appareils électroniques

Comme le "processeur" est un terme générique, un microprocesseur est souvent appelé processeur

### Signal d'horloge

Un signal d'horloge est un signal électrique oscillant utilisé en électronique numérique pour rythmer les actions d'un circuit.

Sa période, appelée **cycle d'horloge** (clock clycle), détermine la fréquence à laquelle les opérations du circuit sont exécutées (Fréquence d'horloge en Hz)

À chaque **cycle d'horloge**, des calculs peuvent être effectués en utilisant les sorties de bascules, assurant que les données sont valides pour le cycle suivant

Le choix de la durée du cycle d'horloge doit être fait en tenant compte du temps de réponse des portes logiques utilisées dans le circuit.

Aujourd'hui, le cycle d'horloge est approximativement le même pour des processeurs d'ordinateurs. (environ 3.5 GHz)

1 Hz = 1 seconde^-1

On pourrait aller plus haut, mais le processeur va surchauffer.

Le nombre d'instructions par seconde (IPS) était calculé en multipliant la fréquence d'horloge par IPC du processeur.

L'IPC (nombre d'instructions par cycle) représente le nombre d'instructions que le processeur peut exécuter lors d'un seul cycle d'horloge.

Le calcul de l'IPS se faisait en utilisant la formule

![[Pasted image 20250922095334.png]]


### Chemin de données

Le **chemin de donnée** est l'ensemble des composants dans lesqueles circulent les données dans le processeur.

Le chemin de donnée comprend
-  L'UAL
-  Les registres
-  L'unité de communication avec la mémoire
-  Le ou les bus

#### Chemin de données miniARM

![[Pasted image 20250922095458.png]]

### Registres

Les registres sont les zones de mémorisants de l'information internes au microprocesseur.

En d'autres termes, c'est la mémoire interne au processeur. Elle est la plus rapide, mais la plus petite. Elle est couteuse.

Chaque registre a son propre intérêt
-  Stocker l'instruction qui va suivre
-  Stocker des adresses
-  Stocker des données
-  Stockage temporaire
-  Stockage pour des instructions SIMD (single instruction multiple data)

##### Exemples

![[Pasted image 20250922100036.png]]

Registres d'instructions
-  CO (PC) : Compteur Ordinal (Program Counter)
-  RI (IR) : Registre d'instructions (Instruction Register)

Registres d'adresses
-  RAM (MAR) : Register Adresse Mémoire
-  SP : Stack Pointer
-  BP : Base Pointer

Registres généraux
-  AX, BX, CX, DX

Registres d'états
-  PSW Processor Status Word

### Unité de contrôle

L'unité de contrôle (control unit) dirige et coordonne le fonctionnement de toutes les autres parties de l'ordinateur (cerveau de l'ordinateur)
-  en gérant le flux d'instructions et de données entre les différents composants

##### Le cycle fetch-decode-execute

-  Récupérer des intructions de la mémoire
-  Décoder les instructions pour déterminer l'opération à effectuer
	Via l'opcode
-  Contrôler et coordonner l'exécution des opérations
	Signaux de contrôle

Gérer le flux de données entre les différentes unités de l'ordinateur

Contrôler et réguler la synchronisation des périphériques d'entrée et de sortie

### Unité arithmétique et logique

![[Pasted image 20250922104617.png]]

L'unité arithmétique et logique (UAL) se charge d'effectuer les calculs
-  ALU : Arithmetic Logical Unit

L'UAL est présent de dtout système
-  Traite les valeurs d'entrées à l'aide d'instructions (l'unité de contrôle déterminant l'opération)
-  Stocke la sortie dans une mémoire

![[Pasted image 20250922104300.png]]
#todo meaning of the letters

L'UAL comporte
 -  Circuit airthmétique
 -  Circuit logique
 -  Registres
 -  Circuit de comparaison

#todo p.43-44

##### Code instanciant un UAL

Créer son propre UAL en hardware est une tâche récurrente

La programmation hardware se fait à l'aide de langage HDL (Hardware Description Language)

Justement écrit en opcode

![[Pasted image 20250922104821.png]]

### Unité de calcul en virgule flottante

Une unité de calcule en virgule flottante (UVF, floating-point unit, FPU) est une partie d'un processeur, spécialiement conçue pour effectuer des opérations sur des nombres à virgule flottante.

Opérations supportées : 
-  +, *, -, / , *+, racine carrée..

Jusqu'au milieu des années 90, l'UVF était hors du processeur

### Multiplexeur

Un multiplexeur ou MUX est un circuit pour sélectionner l'une des multiples entrées pour la diriger vers l'unique sortie
-  Choix de l'entrée contrôlé par un signal de commande
Représenté par un boitier rectangulaire, très utilisé dans l'informatique et électronique

![[Pasted image 20250922104742.png]]
