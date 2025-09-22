Une des fonctionnalités de l'ordinateur est le stockage
-  Stockage de données
	Résultat arithmétique d'un programme, etc..
-  Stockage d'instructions
	Programme informatique

Le stockage des données et des instructions est soit ensemble
	Architecture de von Neumann
ou séparé
	Architecture de Harvard

### Module : Mémoire

Un élément de mémoire doit répondre à des contraintes
-  Importance du temps de réponse
	-  Puis-je me permettre d'attendre un peu plus longtemps pour avoir accès à la donnée ?
	-  (ex): Données dans un processus en cours vs Photos du dernier match à copier sur un disque dur
-  Taille
	Valeur codée en 64 bits vs le programme entier du OS

Ainsi, l'ordinateur doit être composé de plusieurs mémoires permettaant de s'ajuster au contraintes de la donnée traitée

##### Différents types de mémoire

Pour chaque type de mémoire, la mémoire 
	- Correspond à un besoin particulier de l'ordinateur
	- A un coût
	- A son temps de réponse
	- A une capacité

-  Mémoire vive (RAM)
-  Mémoire morte (ROM)
-  Mémoire volatile
	Besoin d'alimentation pour garder les données
-  Mémoire flash
	Clé USB, carte mémoire
-  Registres

Une mémoire volatile, ayant besoin d'être alimentée est soit
-  Statique
	Pas besoin d'être lues pour conserver leurs valeurs
-  Dynamiques
	Besoin d'un rafraîchissement de leurs données périodiquement. La donnée s'efface si non utilisée pendant un laps de temps donné
-  Une mémoire peut seulement être lue
	ROM (Read Only Memory)
-  Une mémoire peut être écrite
	Mémoire RAM (Random Access Memory)

![[Pasted image 20250922110831.png]]

##### Exemple caches

![[Pasted image 20250922110923.png]]

#### Capacité

La **capacité** correspond à la taille d'une mémoire. La mémoire est divisée en N mot mémoire
-  Possédant une taille fixe M
La capacité C correspond au nombre de mots multipliée par la taille d'un mote

`C = N * M`

La capacité C (en octet) correspond au nombre d'adresses

Pour accéder à la donnée en mémoire, cela se fait par l'adresse (comme en C avec le passage par référence)
-  Chaque adresse est unique
-  Une adresse est une suite de bit (exprimée en hex)

Chaque mot en mémoire est associé à son adresse (le nombre de mot est égal, l'adresse d'un mot suit une contrainte d'alignement)

S'il y a 300 adresses, il faut faire *ceil*(*log*2 300) bits pour coder 300 adresses (2 = exposant bas) #todo

Donc, il y aura 8,22(...) bits nécessaires pour coder 300 adresses (alors 9 bits)

*ceil* = partie entière supérieure
*floor* = partie entière

#todo p.70 prob study a lot

![[Pasted image 20250922114106.png]]

### Temps de réponse

Le temps de réponse est le temps pour le processeur d'accéder à la donnée stockée en mémoire
-  Elle dépend du niveau ou se trouve la donnée

Elle peut être soit exprimée en nombre de cycles d'horloge (1 cycle, 5 cycles..) ou en secondes (nombre de cycle divisé par la fréquence d'horloge)

On parle aussi de latence

#todo p.59

### Taille d'une mémoire

La taille d'une mémoire représente la quantité d'information possible à stocker

On parle de **capacité**.

La capacité est exprimée en bit ou en octet (8 bits), qu'on représente en décimal ou 2^10

![[Pasted image 20250922110223.png]]

![[Pasted image 20250922110438.png]]

### Bus de communications

#todo entire bus module

Différents types de bus
-  Bus d'adresses (transporte l'emplacement visé par la transaction)
	Controlé par le processeur, le nombre de lignes détermine la quantité maximum de mémoire que le CPU peut utiliser
-  Bus de données (transfert de données)
	Peut circuler dans les deux sens, mais une à la fois

### Module: Entrée-Sortie (I/O)

I/O est responsable des communications entre l'ordinateur et les périphériques externes

Le module entrée/sortie (Input/Output (I/O)) comprend
-  Des ports (USB, HDMI, Ethernet)
-  Des périphériques d'entrée (apportant l'information à l'ordinateur)
	Souris, micro...
-  Des périphériques de sortie (donnant l'information à l'utilisateur)
	Enceintes, imprimantes ...
-  Périphériques de stockage
-  I/O bus

La commande htop (ou top) sur Linux permet de voir plusieurs informations sur 2 des 3 modules

![[Pasted image 20250922114618.png]]