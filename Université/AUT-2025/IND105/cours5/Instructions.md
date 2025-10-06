La fonction de base d'un orrdinateur est l'exécution de programmes.

Dans sa forme la plus simple, un programme consiste en ces deux étapes : 

-  Le processeur lit séquentiellement une instruction dans la mémoire
-  Le processeur exécute l'instruction

L'exécution d'un programme consiste à répéter ces deux étapes autant de fois qu'il ne le faut

![[vue haut niveau instructions ind105.png]]

## Cycle d'exécution d'une instruction

![[cycle exécution instruction ind105.png]]

-  Le processeur charge (*fetch*) l'instruction depuis la mémoire
-  Le processeur décode l'instruction; c'est-à-dire l'étudie pour savoir quoi faire
-  Le processeur exécute l'instruction
-  Une quatrième étape existe : l'interruption

## Décodage d'une instruction

Une instruction suit une structure.

Le **code opération** ou **opcode** est la portion de la structure indiquant l'opération à effectuer

![[opcode instruction ind105.png]]

L'opcode est envoyé au décodeur qui détermine le type d'opérations à effectuer puis l'envoie au séquenceur (générant les signaux contrôlants et actionnant les unités participant a l'exécution)


## Exemple - Unité Arithmétique Logique

L'UAL est le composant du processeur faisant le traitement des informations

![[exemple ual ind105.png]]

## [[Jeu d'instructions]]

La taille allouée pour l'opcode indique un maximum pour le nombre d'instructions
 -  Sur `n` bits, il est possible de générer 2^n opcodes

Le nombre de combinaison d'opcodes indique le nombre d'instructions réalisables par le CPU.

Un jeu d'instructions correspond à la liste des instructions possibles par un processeur
-  Il peut être large ou réduit

#### Exemple

Si le processeur peut effectuer **4 opérations**
-  **LOAD-STORE-ADD-SUB**
-  Si l'instruction est codée sur 16 bits, deux bits sont nécessaires pour l'opcode
	-  00 - **LOAD**
	-  01 - **STORE**
	-  10 - **ADD**
	-  11 - **SUB**

## Types d'instructions

![[type instructions ind105.png]]

Différents types d'instructions existent, pour chaque famille d'instructions, plusieurs existent
-  Instruction d'affecation
-  Instruction arithmétique et logique
-  Instruction de comparaison
-  Instruction de branchement

#### Instructions d'affectation

Instruction modifiant le contenu d'un registre/case mémoire
-  Par une valeur
-  Par une adresse

Langage assembleur
-  MOV pour move

Transfert possible dans les deux sens (registre vers mémoire ou mémoire vers registre)

**Exemple**

-  `MOV AX, [0110]` copie le contenu de l'adresse 110H dans le registre AX
-  `MOV [0110], AX` copie le contenu du registre AX à l'adresse 110H

#### Instruction d'arithmétique et logique

Instruction effectuée par l'UAL #link 
-  Effectuée sur les bits de la donnée

Ces instructions comprennet
-  Instruction d'addition/soustraction
-  Décalage
-  Rotation
-  Logique (ET/OU)

**Instruction de décalage**

-  Décale d'un côté ou de l'autre les bits des registres accumulateurs
	
	-  Permet une multiplication par 2^n (décale vers la gauche)
	![[instruction décalage gauche.png]]
	-  Permet de diviser par 2^n (décalage vers la droite)
	![[décalage par la droite ind105.png]]
#### Instruction de comparaison

Compare le registre AX à une donnée

Permet d'implémenter des conditions IF, des boucles WHILE, etc...

Dans l'architecture x86, correspond à l'instruction **CMP**

#### Instruction de branchement

Permet de sauteur à une instruction non contigüe
-  S'il n'y avait pas cette instruction; le processeur passerait à l'Instruction contigüe en mémoire (PC = PC + 1)
-  Le registre Program Counter #link est mise à jour

Le registre IP repère l'instruction suivante
-  L'instruction de branchement change la valeur de IP
	-  Effectue l'Instructions voulue

Deux sortes de branchements
	-  Branchements conditionels (IF)
	-  Non conditonnés


## Interruption

Chaque ordinateur a un mécanisme par lequel d'autres modules (I/O, mémoire) peuvent interrompre le fonctionnement normal du processeur

Introduit pour améliorer l'efficience des instructions
-  L'arrêt temporaire permet l'exécution d'un programme prioritaire

Une interuption peut survenir de deux manières :

1.  Sollicitée par le matériel pour effectuer un traitement (lire une touche du clavier par exemple). **interuption matérielle**
	-  Le matériel déclenche une IRQ (interupt request) possédant un numéro propre au port auquel le matériel est connecté
	-  Chaque IRQ correspond à une interruption particulière

2.  Elle peut être sollicitée par un programme en cours d'exécution avec l'instruction `INT` (dans l'architecture x86). Il s'agit d'une **interruption logicielle**

L'interruption peut aussi venir du sytème
-  Reset
-  Faute matérielle générale

L'interuption peut aussi venir d'une **exception**
-  Division par 0
-  Tentative d'accès à de la mémoire protégée

Lorsque survient une interuption, le traitement de cette dernière se fait de cetter manière : 

1.  Terminer l'instruction en ours
2.  Déterminer s'il faut traiter l'interruption
3.  Sauvegarder le contexte
4.  Détermine l'adresse de routine de l'interruption
5.  Exécuter la routine

Après le traitement de l'interruption; et grâce à la sauvegarder de l'état, le programme peut reprende

1.  Restaurer le contexte
2.  Reprendre là où le processeur s'était arrêté

![[évolution program counter ind105.png]]

