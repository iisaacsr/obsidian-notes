
Un jeu d'instructions (*instruction set*) est un ensemble d'instructions pouvant être exécuté par un processeur
-  [[Instructions|Instruction]] = format binaire spécifique opcode + opérande

Un jeu d'instruction agit au plus bas de la programmation
-  Langage machine

Comme le jeu d'instruction dépend du processeur
-  Il y en a un pour le processeur
-  Il y a plusieurs jeux d'instructions sur le marché

#### Exemples

-  X86
-  ARM
-  MIPS
-  PowerPC
-  RISC-V
-  POWER

Deux grandes familles de jeu d'instructions : CISC et RISC


## CISC

CISC pour *Complex Instruction Set Computer*
-  Jeu d'instructions offrant beaucoup d'instructions

Existence d'instructions très complexes
-  Permettant de combiner plusieurs opérations
-  Réduire le nombre d'instructions dans le programme

Par contre, il y a beaucoup de consommation de transitors et d'énergie causé par ce jeux d'Instructions, causant des difficultés de créations de processeurs CISC

Certains processeurs CISC comportent des instructions pour le traitement des chaines de caractères, des polynômes ou des complexes
-  Instructions complexes

Les architectures CISC permettent une variété de modes d'adressage complexes pour permettre des opérations plus flexibles et puissantes

## RISC

RISC pour *Reduced Instruction Set Computer*

Processeur avec un jeu d'instruction simple; évite l'existence d'instructions trop peu utilisés
-  Gain en terme de transistors
-  Consomattion thermique réduite

Il y a plus de jeux d'instructions RISC que CISC

#### Caractéristiques

**Nombre réduit de modes d'adressage**
-  Pas de mode d'adressage complexe
-  Mode d'adressaage : immédiat, direct, indirect et relatifs

**Nombre réduit de types de données
-  Les seuls types de données supportés sont les entiers de différentes tailles (8, 16, 32 et 64 bits) et des nombres flottants en simple et double précision

**Codage uniforme des instructions
-  Toutes les instructions sont codées avec un même nombre de bits
-  L'opcode se trouve à la même position pour toutes les instructions
	Facilite le décodage des instructions

**Registre indifférenciés et nombreux**
-  Beaucoup de registres généraux, facilitant l'allocation

**Limitation des accès mémoire**
-  Instructions spécifiques pour accéder à la mémoire
	-  Instructions de chargement et de rangement


## La famille x86

La famille x86 regroupe des microprocesseurs compatibles avec le jeu d'Instructions de l'Intel 8086

La conception des microprocesseurs 86 a évolué
-  Architecture de 32 bits vers 64 bits (extensions AMD64 et Intel 64)

La famille x86 est construite avec une architecture CISC

Elle domine le marché des ordinateurs de bureaux et des ordinateurs portables (laptops)

Elle domine aussi les archtectures pour les superordinateurs !

## La famille ARM

L'architecture **ARM** (*Advanced RISC Machine*)

Fabriquant de processeurs ARM : 
-  Apple, Fujitsu, Huawei, LG, NXP semiconductor, Nvidia, Parrot, Qualcomm, Samsung, STMicroelectronics, TI, Toshiba, Xilinx ...

L'architecture ARM domine le marché
-  Des smartphones
-  Tablettes
-  Console jeux vidéos portables

L'architecture ARM est fortement reliée au *system on chip*

