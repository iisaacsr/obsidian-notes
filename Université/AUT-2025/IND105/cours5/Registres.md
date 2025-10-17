
Les registres sont les zones de mémorisation de l'Information **internes au microprocesseur**
-  En d'autres termes, c'est la mémoire interne au processeur

La mémoire est petite, mais très rapide

#### Comment sont-ils réalisés ?

Un registre est un ensemble de [[Algèbre de Boole#Bascule|bascules]](mémoire élémentaire à 1 bit), synchronisé par une horloge

Un régime de `N` bits comporte donc `N` bascules


**Variantes de régistres**

-  Les registres à décalage (bits entrent d'un côté et sortent de l'autre)
	-  De type SISO, SIPO, et PISO

-  Registres de mémorisation (stockent et traitent les données)
	-  Ce qu'on trouvent dans un processeur
	-  De type PIPO

**Caractéristiques d'un registre**

-  Capacité
	Nombre de bits qu'il peut stocker

-  Mode d'écriture
	-  Écriture sortie
		Bit par bit sur un seul fil conducteur
	-  Écriture parallèle
		Génération de `N` bits avec par un bus de `N` bits (`N` fils)

- Mode de lecture
	-  Lecture série
		Bit par bit (une seule sortie)
	-  Lecture parallèle
		Exploitation globale du mot (`N` sorties)

#### Types de registres

![[types de registres ind105.png]]


## Registres de mémorisation

Les **registres de mémorisation** permet la mémorisation de `N` bits.

L'information sur `N` bits est écrite au moyen d'un signal d'horloge des bascules W

L'information peut être lu via un signal de validation R

#### Exemple

Le registre mémorise les états des entrées E0, E1, E2 et E3 en synchronisme avec le signal d'écriture W (horloge)
-  Conservés jusqu'au prochain signal d'horloge W

Les données mémorisées peuvent être lues sur les sorties Q0, Q1, Q2 et Q3
-  Via un signal de validation R

![[registre pipo ind105.png]]


## Registres à décalage

Un **registre à décalage** est un ensemble de bascules relieés une à une

À chaque front montant d'horloge, le nombre représenté par ces bascules et mis à jour

Le registre de décalage permet d'insérer une donnée dans le registre, ou la lire, bit par bit

#### Exemple

Registre de 4 bits à entrée série et sortie parallèle réalisé avec des bascules D.

Le signal R (read) n'est pas obligatoire, il permet juste de commander la lecture des sorties en même temps, de façon à éviter la lecture au moment du chargement

![[registre SIPO ind105.png]]


Un registre peut contenir

-  une instruction,
-  une adresse de stockage
-  une séquence de bit (donnée)
-  plusieurs séquence de bits (registre SIMD)

Chaque régistre a donc son propre intérêt

**Registres spéciaux**

-  Registres **PC** #important et IR (pour les instructions)
-  Registres MAR (le registre d'adresses) et le MBR (le registre de données) permettant la communication avec les autres modules via le bus
-  Registres liés à l'entrée sortie (I/O)

**Registres généraux**

-  Registres plus généraux (concernant les instructions arithmétiques)


![[cpu avec registres ind105.png]]

## Registre PC - Compteur Ordinal

Le registre PC (*Program Counter*) est un registre d'adresse

Le registre PC contient l'adresse de la prochaine instruction

Elle est incrémentée après chaque instruction par le processeur
-  Car les instructions sont stockées en mémoire de manière contigües
-  Le registre PC peut prendre une autre valeur avec une instruction spéciale
	L'instruction de branchement


## Registre IR

#todo

## Registres MAR

#todo 

## Registres MBR / MDR

#todo 

## Registres I/O AR et I/O BR

#todo 

## Registre ACC

Le registre ACC (Accumulator) est utilisé pour la manipulation des données (mémoire temporaire)

Il contient une valeur requise par une opération arithmétique
-  Le registre ACC sert pour l'ALU #link

## Registres liés à la pile

Le pointeur de pile indique la position du prochain emplacement mémoire disponible dans la pile

Registre pointant vers le sommet de la pile
-  Registre **esp** (Extended Stack Pointer)

Registre indiquant la position de la base de la pile
-  Registre **ebp** (Extended Base Pointer)