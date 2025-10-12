
## Q1

Indiquez les 3 modules composant d'un ordinateur
[[Ordinateur (recap)#Définitions|reference]]
	- Mémoire
	- CPU
	- I/O 

## Q2

Indiquez les 3 composants d'un processeur
[[Architecture de Processeurs|reference]]
	-  Unité de contrôle
	-  Unité arithmétique logique (UAL)
	-  Registres

## Q3
[[Architecture de Harvard|Harvard ref]]
[[Architecture de von Neumann|von Neumann ref]]
Une instruction ayant besoin d’une donnée est stockée en mémoire. Indiquez dans quelle
mémoire se trouve la donnée et l’instruction pour l’architecture de von Neumann et pour
l’architecture de Harvard.
	-  Pour von Neumann : Dans la même mémoire (donc RAM ou ROM, tout dépendamment)
	-  Pour Harvard : Les données sont dans la RAM, les instructions dans la ROM

## Q4

Dessinez le schéma de l'architecture de von Neumann ayant les 3 modules et le bus

![[architecture von neumann ind105.png]]
## Q5

Dessinez le schéma de l'architecture de Harvard ayant les 3 modules et le bus

![[architecture de harvard ind105.png]]

# Mémoire

## Q6-Q7

Dessinez la hiérarchie mémoire avec : Les registres, la mémoire centrale (RAM), le disque
dur, la mémoire cache sur plusieurs niveaux.

![[hiérarchie mémoire ind105.png]]

-  Est-ce que le registre est plus rapide que le cache ?
	Oui

-  Quelle mémoire est la plus rapide entre la mémoire centrale et le disque dur ?
	La mémoire centrale (RAM)

-  Même question, pour le prix
	La RAM est plus chère que le disque dur (généralement)

-  Même question, pour la taille de la mémoire
	Le disque dur a plus de mémoire, est plus volumineux, puis la RAM, puis le cache, puis les registres

## Q8

Classez les éléments suivants dans un des modules de l’ordinateur :

-  Imprimante = Entrée / Sortie
-  Random Access Memory = Mémoire
-  Read Only Memory = Mémoire
-  Clavier = Entrée / Sortie
-  Souris = Entrée / Sortie
-  Registres = Processeur / Mémoire
-  ALU = Processeur

# Loi de Moore (co-fondateur de Intel)

La loi de Moore est une loi empirique sur l’évolution de la puissance de calcul des
ordinateurs et de la complexité du matériel informatique. Il y a un doublement du nombre de
transistors présent sur une puce de microprocesseur tout les deux ans.

Donc, loi de Moore =  `transistors * 2 = current year + 2`
## Q9

En quelle année arrivera t’on à 10,000,000,000,000 de transistors ?
	Environ en 2035

## Q10

La finesse de gravure des transistors est limitée, ainsi la miniaturisation des transistors com-
mence à atteindre une limite aujourd’hui. Quel procédé est envisagé pour augmenter le
nombre de transistors sur une puce (c’est-à-dire sur une même surface) ?

-  Rajoutent des couches (donc monte verticalement)

## Q11

On vient de voir qu’il existe une limite physique à la loi de Moore, pensez-vous à une autre
limite concernant la loi de Moore ?

-  Dissipation thermique (?)

## Q12


## Q13




## Q15

Par quel moyen peut-on accéder à une donnée en mémoire ?

Par l'adresse mémoire

## Q16

Dans une architecture ancienne, quelle est la relation entre le nombre d’adresse en mémoire
et le nombre de mot ?

