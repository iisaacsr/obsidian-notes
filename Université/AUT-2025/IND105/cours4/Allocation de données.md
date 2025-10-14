
## Allocation

-  Allocation statique : Réalisé avant même l'exécution du programme
	Les variables globales (accessible n'importe où dans le programme)
-  Allocation dynamique : pendant l'exécution du programem
-  Allocation automatique : pendant l'exécution du programme

## Pile (stack)

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
-  LIFO : Permet de connaître l'endroit où chaque fonction active (dont l'exécution n'est pas terminée) doit retourner à la fin de son exécution
-  La pile stocke également les données associées à chaque fonction telles que variables locales, paramètres, etc..
-  Lorsqu'une fonction se termine, le bloc de la pile correspondant, nécessairement au sommet de celle-ci, est libéré.
	-  Variables placées dans la pile par cette fonction sont supprimés

## Tas (heap)

La mémoire sur le tas, plus grande et plus durable que sur la pile, requiert une gestion plus complexe et donc plus lente

Le tas est une zone de mémoire manipulable par le programmeur
-  Utilisée pour stocker des données allouées dynamiquement
-  Appel de `malloc`, `calloc`, `realloc`...
-  Gestion de la libération de la mémoire tas: via `free()` dès que vous n'en avez plus de besoin
	Évite les fuites de mémoire, qui provoquent la saturation de la mémoire machine

Les variables créées sur le tas sont accessibles par n'importe quelle fonction et n'importe où dans le programme, rendant leur portée globale

De plus, elles peuvent être redimensionnées à l'aide de la fonction `realloc()`

La taille des variables dans le tas n'est pas limitée, du moins seulement par la limite physique de la mémoire

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

#### Mémoire vive statique - SRAM

Inventé en 1964, c'est une mémoire volatile (a besoin de courant pour stocker les données)

Comparaison avec la mémoire dynamique
	Moins dense, plus onéreuse, moins énergivore et plus rapide

**Utilisation**:
-  Temps d'accès court, système faible consommation
-  Électronique automobile, système embarqué
-  Routeur, ordinateur, registre du CPU, mémoire cache, buffer de disque dur ...

Les mémoires SRAM sont plus grandes. Chaque cellule de mémoire SRAM nécessite de 4 à 6 transistors

Les transistors impliquent que les mémoire SRAM ont une capacité de stockage faible pour une surface donnée, **ce qui les rend plus coûteuses par bit**.

#### Mémoire vive dynamique

Mémoire volatile (elle a besoin de courant pour stocker les données)

**Il faut un rafraîchissement des données pour pouvoir les garder**
	Toutes les quelques millisecondes

Pour éviter cette perte de données
	Un circuit intégré à la mémoire lit périodiquement chaque bit de données puis le réécrit
	+ restauration de la charge du condensateur à son niveau initial

Ce processus de rafraîchissement se déroule automatiquement en arrière-plan tant que l'ordinateur est sous tension

Comparaison avec la mémoire statique : 
	Plus dense, moins onéreuse, énergivore et moins rapide

**Utilisation**
-  Stockage temporaire des programmes en cours (ordinateurs, smartphones)
-  Serveurs (gestion simultanée de plusieurs requêtes, etc...)

Stockage des bits : présence ou absence de charges électriques sur de petits condensateurs. Au fil du temps, les charges électriques des condensateurs se dissipent
	Perte des données

Chaque cellule de la DRAM est composée d'un **transistor** et d'un **condensateur**

Cela permet donc une mémoire très dense (1 transistor pour la DRAM vs 6 pour la SRAM)

Il existe des Dynamic RAM (DRAM)

-  **Asynchrone**
	Non synchronisé avec le processeur / bus
	A été utilisé dans les premiers systèmes informatiques

-  **Synchrone**
	Synchronisé avec le processeur via une horloge
	SDRAM (Synchronous DRAM)
	Ont largement remplacé la DRAM asynchrone
## Barrettes mémoires

-  SIMM (Single Inline Memory Module) (vieille RAM)
-  DIMM (Dual Inline Memory Module) ou barrette de mémoire vive (RAM)
	Comporte aussi de BUS de communications internes
#todo 

## [[Mémoire cache]]
