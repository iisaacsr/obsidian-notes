
Le **langage machine** est la suite de bits qui est interprétée par le CPU exécutant un programme. C'est le seul langage qu'il puisse traiter. Il est composé d'instructions et de données à traiter **codées en binaire.**

Le **langage assembleur** est le langage de plus bas niveau représentant le langage machine de manière compréhensible pour un être humain.

![[assembly lang ind105.png]]

Le langage assembleur représente le langage machine de manière lisible pour les humains.

Les combinaisons de bits de langage machine sont exprimées par des **symboles mnénomiques**
-  `MOV`, `ADD`, `CMP`, etc..

Un programme assembleur convertir les mnénomiques et valeurs en langage machine, créant des fichiers exécutables

Le langage assembleur n'est pas unique
-  Dépend du processeur utilisé
-  Un par type de processeur

En langage assembleur, on appelle **procédure** un sous-programme qui permet d'effectuer un ensemble d'instructions par simple appel de la procédure
-  Appelé **fonction** dans d'autres langages
-  Une procédure peut faire appel à elle-même, on parle alors de procédure récursive

Un programme en assembleur peut être divisé en 3 sections

-  La section **data**
	Déclaration des données initialisées

-  La section **bss**
	Réservation de mémoire pour des variables non initialisées

-  La section **text**
	Contient le code exécutable et commence par une étiquette pour indiquer l'entrée du programem
