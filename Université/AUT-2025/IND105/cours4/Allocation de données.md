
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

## Mémoire cache

-  Les performances du CPU s'améliorent d'années en années
- **Problème** : La RAM est moins rapide que le processeur
	-  Le temps d'accès à la mémoire est du temps durant lequel le processeur n'exécute pas d'instruction
	-  Sauf s'il y a présence d'un pipeline

![[Pasted image 20250929110133.png]]

**Solution** : la mémoire cache, pour accéléer les performances de l'ordinateur

La cache est une mémoire intercalée entre la mémoire plus rapide (délai de propagant plus court)

Souvent fabriqué à partir de la SRAM, eDRAM (embedded DRAM)

#todo 

#### Généralité

Le cache est une mémoire proche du processeur, l'esapce est restreint

La cache est une mémoire rapide et une mémoire à faible capacitié
-  Un **choix** sur les données présentes doit être effectuée
-  La cache contient une cioue de certaines données présentes dans la RAM
-  Les autres données doivent être lues / écrites dans la RAM

#### Succès de cache

-  Si la donnée voulue est dans le cache, l'accès se fera **automatiquement** depuis la cache
- #todo 

#### Données présente dans le cache

#todo 

-  Le cache contient une copie de certaines données présentes dans la RAM

Elle se repose sur deux principes
-  Principe de localité spatiale
	Une adresse demandée à l'adresse **adr** engendra certainement un accès à la donnée à une adesse très proche de **adr**
-  Principe de localité temporelle
	Si on accède à une case mémoire ony accèder sans doute bientôt

Le cache contient une copie de certaines données présentes dans la RAM. Le choix sur les données préésentes  suit une logique algorithmique:
-  Algorythme de Bélàdyl algorithme LRUM algorithme LRU, etc...

Le défaut de cache peut avoir plusieurs origines
-  Premier accès au cache (la donnée n'étant pas de base dans le cache)
	On appelle ça un cold miss, impossible à éviter

Liée à la taille du cache (le cache est trop petit pour stocker les données utilisées,) les anciennes données peuvent être supprimées
-  On appelle ça un défaut de capacité ou Capacity Cache Miss


## Ligne de cache

![[Pasted image 20250929111604.png]]

Les lignes de cache sont plus grandes que des mots mémoire

Example d'ordre de grandeur :
- mot de 64 bits, c'est-à-dire une adresse retourne une série de 64 bits
-  Une ligne de cache = 128 octets
-  Un mot est 16 fois plus petit qu'une ligne de cache

Mémoire cache = invisible
-  Pas possible d'expliciter l'utilisation du cache
-  Le cache intercepte les accès mémoire
-  Exemple
	-  Interception d'une lecture dans une adresse
	-  Si le cache, a le contenu de cette adresse, la donnée sera envoyée par le cache

## Savoir si une donnée est dans le cache

![[Pasted image 20250929111802.png]]

-  Lors de la copie de la donnée dans le cache, une partie de l'adresse RAM associée est sauvegardée
	-  Une partie ? Oui, car la ligne de cache est plus grande que le mot
	-  C'est le **tag**
	-  Le **tag** permet de savoir si une donnée est dans le cache
	-  Le restant de l'adresse permet de décrire où est la donnée dans la ligne de cache


-  Correspondance 1-1 entre adresset et ligne de cache
	-  Plutôt correspondance multi-adresses pour une ligne de cache
	-  Car une ligne de cache est plus grande qu'un mot

-  Tableau de correspondance entre tags et lignes de cache
-  Lors d'un accès mémoire, le cache extrait le tag et l'adresse à lire ou écrire, et le compare avec les tags de chaque ligne de cache
-  Si une ligne contient ce tag, alors la donnée est dans le cache
	#todo
![[Pasted image 20250929112325.png]]

## Types de cache

#todo a lot of studying req (tag, index, offset)

## Cache à correspondance établie

bloc mémoire = adresse / taille LDC ou |LDC|

ou *direct-mapped cache*

-  Chaque mot de la mémoire principale a son endroit associé dans le cache
-  Ainsi une adresse en mémoire ne peut se situer qu'à un endroit dans le cache
	-  Réalisée avec une opération modulo
	-  Ligne d'adresse en mémoire principale *j*
	-  Adresse dans le cache *i*
		*i* = *j* modulo L
	-  L correspondant aux nombre de ligne de la cache

#todo 

## Cache totalement associatif

*Fully associative cache* - cache totalement associatif

Une ligne de mémoire principale peut être copiée dans n'importe quelle ligne de la mémoire cache.
 
Le *tag* de l'adresse est comparé au tag de toutes les lignes de la mémoire cache. En cas de *hit*, l'octet est retourné grâce à son *data index* (offset) dans le bloc de données

## Cache associatif par ensembles