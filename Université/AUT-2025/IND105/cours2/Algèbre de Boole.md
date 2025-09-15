
Un domaine booléeen est un ensemble mathématique des deux éléments `B = {VRAI,FAUX}`. Nous utiliserons la représentation binaire, c'est à dire `B = {1,0}`.

## Portes logiques

Les portes logiques sont des circuits qui possèdent des sorties et des entrées sur lesquelles on va récupérer des bits.

Les entrées ne sont rien d'autre que des "fils" conducteurs sur lesquels on envoie un bit

Le cirucit électronique va calculer le bit à placer sur chaque sortie, via des portes logiques. Le circuit est un ensemble de portes logiques.

Tous les composants d'un ordinateur sont fabriqués avec ce genre de circuits.

Les 8 portes majeures sont

-  Registre
	-  NON
	-  ET
	-  NAND
	-  OU
	-  NOR
	-  OU eXclusif (XOR)
	-  XNOR
-  Buffer
	-  NOT
	-  AND
	-  NAND
	-  OR
	-  NOR
	-  XOR
	-  XNOR

Les circuits logiques peuvent être séquentiels ou combinatoires
-  Combinatoire
	Sorties basées seulement sur les entrées
-  Séquentielles
	Sorties basées sur les entrées et les valeurs passées


# Les circuits de logique

- ## Buffer
	Un buffer d'un bit est un composant électronique utilisé pour stocker temporairement un bit d'information (0 ou 1)
	
	Il est utile pour synchroniser les signaux dans un circuit
	
	![[Pasted image 20250915112019.png]]
- ## NO / NON
	NON donne l'opposé de A
	![[Pasted image 20250915112211.png]]
- ## ET / AND
	A **ET** B est VRAI si et seulement si A est VRAI et
	 B est VRAI 
	![[Pasted image 20250915112323.png]]
- ## OU / OR
	a **OU** b est VRAI si et seulement a est VRAI OU b est VRAI 
	![[Pasted image 20250915112438.png]]
- ## O eXclusif / XOR
	A **XOR** B est VRAI si et seulement si a est différent de b
	![[Pasted image 20250915112600.png]]


# Lois composés 

Une loi est dite composée si elle combine plusieurs opérations logiques pour aboutir au résultat.
-  OR avec NON --> NOR
-  AND avec NON -- > NAND

# Les circuits de logiques composés

- ## Non ou / NOR
	A **NOR** B est VRAI si et seulement A **OU** B est **FAUX**
	![[Pasted image 20250915112848.png]]
- ## NAND
	A **NAND** B est VRAI si et seulement A **ET** B est FAUX.
	![[Pasted image 20250915112942.png]]
- ## XNOR
	A **XNOR** B est VRAI si et seulement si A **XOR** B est faux 
	![[Pasted image 20250915113043.png]]


## Circuits séquentiels

Comme pour les circuits combinatoires, les circuits séquentiels possèdent des entrées et des sorties. Par contre, la valeur des sorties dépend de la valeur des entrées actuelles et passées.


## Bascule

#todo 

Une bascule est un circuit logique qui peut maintenir les valeurs de ses sorties malgré les changements de valeurs d'entrées, c'est-à-dire comportant un état "mémoire"

Il y a deux catégories de bascules principales 
-  Bascule synchrone
-  Bascule asynchrone

L'état d'une bascule est modifié UNIQUEMENT au moment du changement dans son signal de contrôle. Ce changement est appelé **transition** et déclenche la bascule.

![[Pasted image 20250915113824.png]]

## Verrou

#todo 

Un verrou est une bascule asynchrone. Les verrous (latch) sont des bascules dont la sortie dépend **uniquement** du niveau logique des entrées. Son évolution dépend uniquement de la succession des combinaisons appliquées.

Les verrous permettent de mémoriser des valeurs binaires
-  Les changements d'état activés par un signal de contrôle (Enable)
-  Sortie globale du circuit séquentiel soit imprévisible

La conception des bascules vise à corriger ce problème, en établissant un instant précis et prévisible de déclenchement où les valeurs d'entrée seront prises en compte systématiquement