
## Processeur sans pipeline


![[ind105 cycles instruction cpu wo pipeline.png]]

Dans un processeur sans pipeline, **les étapes d'un cycle d'instruction** sont faites les unes à la suite des autres.
-  IF : Instruction Fetch, ID : Instruction Decode, EX : Execute, MEM : Memory Access, WB : Write Back

Pour commencer une nouvelle instruction, l'étape WB (write back) de la précédente doit être terminée
-  Cela crée donc un temps de **latence**
-  Chaque étape est effectuée en 1 cycle d'horloge (15 au total dans l'image)

**Le pipeline permet de ne pas attendre à la fin d'une instruction pour commencer les étapes d'une instruction suivante**


## Introduction

Un pipeline est une partie intégrante d'un processeur

IBM stretch : 1961
-  Début timide, gain d'intérêt fin des années 70. (processeur vectoriel)
-  Utilisé dans plusieurs entreprises en 1985

Un pipeline permet de commencer une instruction sans avoir à terminer la précédente. Chacune des étapes d'un pipeline est appelée [[#Étage d'un pipeline|étage]]. Le nombre d'étages est appelé [[#Profondeur d'un pipeline|profondeur]].

1989 = Premier pipeline dans l'architecture x86

Die du **Intel 80486** qui inclut le pipeline pour la première fois en **1989**. 

L'amélioration des performances entre le 386 et le 486 provient en très grande partie de ce pipelining.

C'est un pipeline de type [[#Pipeline RISC|RISC]]
-  5 étages, 1 cycle par étage

## Étage d'un pipeline

Découpage d'une instruction en plusieurs **étapes**.

Chaque étape = 1 étage du pipeline. La fréquence d'horloge est limitée par l'étape qui est la plus longue à réaliser
-  Ce qui est déjà le cas dans l'approche classique

## Pipeline RISC

Un pipeline de type RISC possède 5 étages pour traiter une instruction

1.  IF (Instruction Fetch) : Charge l'instruction à exécuter dans le pipeline
2.  ID (Instruction Decode) : Décode l'instruction
3.  EX (Execute) : Exécute l'instruction avec l'ALU
4.  MEM / MA (Memory) : Accès à la mémoire si nécessaire (read/write)
5.  WB (Write Back) : Stocke le résultat dans un registre
	La source de ce résultat peut être la mémoire (après un LOAD), l'unité de calcul (à la suite d'un calcul à l'étape EX) ou bien un registre (après un MOV)

Plus l'instruction est divisée en plusieurs étapes, plus le **facteur d'accélération** entre le pipeline et l'approche classique est élevé

![[ind105 cycles horloge.png]]

-  5 instructions exécutées en 9 cycles d'horloge contre 25

## Pipelines plus simples

Il existe des pipelines encore plus simples, 

Pipeline à 2 étages
-  Fetch : Charge (Fetch), décode l'Instruction (ID) et met à jour le registre Program Counter
-  Exec : Exécute l'instruction et réalise les accès mémoires
-  Utilisé sur certains microcontrôleurs

3 étages 
-  Fetch : Charge et met à jour le registre Program Counter
-  Decode : Décode l'instruction (Opcode + identification des registres utilisés)
-  Exec (arithmétique et mémoire)
-  Utilisé pour l'IBM stretch


## Réalisation d'un pipeline

![[pipeline realisation ind105.png]]

Les résultats de chaque étage sont échangés à travers les étages de 3 manières
-  Les pipelines synchrones
-  Les pipelines asynchrones
-  Les pipelines à vagues (pas utilisé)

La fréquence d'horloge est limitée par l'étape qui est la plus longue à réaliser (registre entre chaque étage)

#### Synchrone

![[piepeline synchrone ind105.png|left]]

Synchrone = étages liés à une fréquence d'horloge commune

Des registres tampons sont utilisés à chaque fin d'étage
-  Reliés à la fréquence d'horloge du processeur

Résultat de l'étage accessible à chaque coup d'horloge
-  L'étage prenant le plus de temps dicte le cycle d'horloge

**Technique la plus utilisée**

#### Asynchrone

![[ind105 async pipeline.png|left]]

Aucune horloge pour synchroniser les transferts entre étages
	Bus asynchrone

Synchronisation avec un signal de requête et acquittement
-  Requête : Travail fini pour l'étage précédent (résultat disponible)
-  Acquittement : L'étage a pris en compte la donnée

L'étage qui suit demande la donnée à l'étage précédent
-  Acknowledgement (acquittement)

L'étage précédent fournit la donnée

## Court-circuitage

![[court-circuitage ind105.png]]

Toutes les instructions n'ont pas obligatoirement besoin de passer par chaque étape de l'instruction
-  C'est le court-circuitage de certains étages

L'instruction doit passer par cet étage mais ne rien faire dedans
-  Inactivité
-  Soit via une instruction spéciale
-  Soit via une inactivation matérielle impliquant des MUX #todo(find multiplexeur)

## Chemin de données

![[chemin données ind105.png]]

Second étage (l'unité de décodage) : **Génère les signaux de de commande servant à configurer le chemin de données**, dans le second étage du pipeline
-  Rappel : chemin de donnée = Tous les éléments matériels par lequel passe les données lors d'une instruction

Passage des signaux de commande d'un étage à l'autre en utilisant des registres, va définir le chemin que va traverser la donnée dans le pipeline

## Signaux de contrôle

Un signal de contrôle est une ligne binaire (qui peut être 0 ou 1) générée par le système de contrôle du processeur qui dirige ou configure le comportement d'une unité fonctionnelle spécifique (comme l'ALU, les registres, ou la mémoire) à une étape donnée du pipeline.

Chaque instruction a sa propre suite de signaux de contrôle.

ALU:
-  RegRead =1, ALUOp = ADD, ALUSrc = Reg, RegWrite = 1, MemToReg = 0

Instruction de chargement (LOAD)
-  RegRead = 1, ALUOp = ADD, ALUSrc = Imm, MemRead = 1, RegWrite = 1, MemToReg = 1

| Signal de Contrôle | Description                                                                        | Étapes du Pipeline |
| ------------------ | ---------------------------------------------------------------------------------- | ------------------ |
| RegDst             | Sélection le registre de destination (registre cible pour les instructions R-type) | ID, WB             |
| ALUSrc             | Détermine la seconde source de l'ALU (mode d'adressage)                            | EX                 |
| MemToReg           | Sélectionne la source de la donnée à écrire dans le registre (ALU ou mémoire)      | WB                 |
| RegWrite           | Active l'écriture dans un registre de destination                                  | WB                 |
| MemRead            | Active la lecture de la mémoire                                                    | MA                 |
| MemWrite           | Acrive l'écriture dans la mémoire                                                  | MA                 |
| Branch             | Drapeau indiquant si l'Instruction est une branche (et si elle doit être prise)    | EX, MA             |
| Jump               | Drapeau si c'est une instruction de saut                                           | EX                 |
| ALUop              | Opération à effectuer par l'ALU                                                    | EX                 |
| PCsrc              | Sélectionne la source pour la MaJ de PC                                            | IF, MA             |
| ExtOp              | Indique si l'immédiat doit être signé ou pas                                       | ID                 |
| Zero               | Indique si ALU a sorti 0                                                           | EX                 |

## Profondeur d'un pipeline

Intérêts d'avoir un pipeline plus profond (plus d'étages) : 

- Plus d'instructions en cours d'exécution simultanée
	Moins de cycles pour un même nombre d'instructions

-  Permet une montée en fréquence du processeur
	Plus de cycles dans un même lapse de temps

Plus d'étages = temps de propagation plus courts entre les unités

La montée en fréquence est limitée par
-  Temps de propagation des signaux à travers une unité et entre les unités du CPU
-  La question de la dissipation de la chaleur

Avec la profondeur, on peut raccourcir le temps du cycle
-  **Augmenter la fréquence du processeur**

Donc, doit-on privilégier la profondeur du pipeline pour aller très très vite ? 

**Non**, car un pipeline profond pose plus de problèmes qu'in pipeline court :
-  [[Aléas dans les pipelines|Aléas]] de contrôles principalement
-  Un contrôle des chemins de données très complexes

**12 à 15 étapes dans les processeurs aujourd'hui**