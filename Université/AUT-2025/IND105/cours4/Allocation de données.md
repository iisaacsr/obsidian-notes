
## Allocation

-  Allocation statique : Réalisé avant même l'exécution du programme
	Les variables globales (accessible n'importe où dans le programme)
-  Allocation dynamique : pendant l'exécution du programem
-  Allocation automatique : pendant l'exécution du programme
## Pile

![[Pasted image 20250929105157.png]]

Une structure de donnée de type pile est une structure du type **dernier arrivé, premier sorti**
-  Base de la pile (Adresse fixe)
-  Sommet de la pile (adresse changeante)

La pile est incluse dans l'espace d'adressage de la RAM
-  La pile est gérée par le microprocesseur
-  Register esp pour indiquer l'adresse au sommet de la pile

Instruction **push** : ajoute une donnée au sommet de la pile (empile)

Instruction **pop** : Retire la donnée au sommet de la pile

#### Utilisation

Chaque appel de fonction implique la création d'un nouveau bloc au sommet de la pile, correspondant à la fonction en question
-  PIFO : Permet de connaître l'endroit où chaque fontion active (dont l'exécution n'est pas terminée) doit retourne à la fin de son exécution
-  La pile stocke également les données associées à chaque fonction telles que variables locales, paramètres, etc..
-  Lorsqu'une fonction se termine, le bloc de la pile correspondant, nécessairement au sommet de celle-ci, est libéré.
	-  Variables placées dans la pile par cette fonction sont supprimés

## Tas #todo


## Mémoire vive (RAM)

*Random Access Memory* (RAM) = Mémoire vive

 Espace mémoire utilisé comme mémoire à court terme pour enregistrer les données traitées par un appareil information
 -  Le processeur

Plus un ordinateur dispose de RAM, plus il est capable de jongler avec les donneées à un moment donné

Le RAM et le processeur fonctionnent de manière **synchrone**
-  Fonctionnent de manière complémentaire pour garantir que sa puissance et ses performances réponded à vos besoins

De maniére générale, la RAM est rapide

La RAM peut être
-  Statique
	-  Les données ne seront pas chargées
	-  SRAM ou *static* RAM
-  Dynamique
	-  Les données seront rafraîchies
	-  DRAM

#### Mémoire vie statique

Inventé en 1964, c'est une mémoire volatile (a besoin de courant pour stocker les données)

#todo 

#### Mémoire vie dynamique

#todo 

## Barrettes mémoires

-  SIMM (Single Inline Memory Module) (vieille RAM)
-  DIMM (Dual Inline Memory Module) ou barrette de mémoire vive (RAM)
	Comporte aussi de BUS de communications internes
#todo 

## [[Mémoire cache]]
