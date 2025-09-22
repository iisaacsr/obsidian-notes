
Tous les nombres qu'on présente dans la réalité (le quotidien) sont écrit dans une base prédéfinie (décimale, 10)

Une base est un nombre b =/= 0 dont les puissances successives interviennent dans l'écriture de nombre dans la numération positionnelle de ces puissances

Donc,

![[Pasted image 20250915093411.png]]


Un entier peut s'écrire dans n'importe quelle base

![[Pasted image 20250915093350.png]]

### Nombres binaires (base binaire)

Un nombre binaire s'écrit à l'aide de bits (0 et 1)

![[Pasted image 20250915093613.png]]

Un nombre binaire est toujours composé d'un **bit de poids fort** et un **bit de poids faible**
-  Le bit de poids fort correspond au bit associé à la puissance la plus élevée
-  Le bit de poids faible correspond au bit associé à la plus petite puissance


### Nombre hexadécimaux (base hexadécimale)

La base 16 est composée de 16 chiffres : { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F }

Un nombre de base 16 pourra s'écrire `0xDA57 = (DA57)v16`

#todo 

Pour représenter une séquence binaire en séquence hexadécimale
-  Regrouper les bits par 4 (le groupe de poids fort peut contenir moins de 4 bits)
-  Si le groupe de poids fort a moins de 4 chiffre, rajouter des 0
	Exemple : `0010 1101 0101`

### Méthode pour passer d'une base à une autre

Les nombres peuvent s'écrire dans n'importe quelle base, alors il y existe des méthodes pour passer d'une base à une autre. 

![[Pasted image 20250915094651.png]]

## Entiers binaires signés et amplitude

Pour des entiers binaires signées, il va toujours y avoir un bit utilisé pour le signe, l'autre pour encoder l'entier (amplitude)
-  Bit de signe 0 : positif
-  Bit de signe 1 : négatif

![[Pasted image 20250915095708.png]]

### Entiers binaires Complément à 1

On représente un nombre négatif en **flippant tous les bits** de la représentation

![[Pasted image 20250915103633.png]]

## Entiers binaires Complément à 2

Autre méthode avec une étape supplémentaire par rapport au complément à 1
-  On calcule l'amplitude de l'entier (représentation binaire)
-  On flip tous les bits
-  On ajoute 1 au LSB (bit de poids faible)

![[Pasted image 20250915104042.png]]

## Addition en base binaire

-  On commence par les bits de poids faible
-  On converge vers les bits de poids fort
-  On propage les retenues (1+1) vers les bits de poids forts

## Soustraction en base binaire
   pas mal la même chose)
   
-  Convertir en base 2
-  Trouver le complément à deux des nombre à soustraire
-  Réaliser l'addition avec la notation en complément à 2
-  Ne pas prendre en compte le débordement

## Nombre à virgule en base binaire

La partie fractionnaire suit la même logique de la partie entière, chaque vit à la droite de la virgule est divisé par une puissance de deux négatives

## Nombre à virgule flottante

Écriture scientifique : produit entre un nombre a et une puissance de 10

![[Pasted image 20250915105804.png]]

## IEEE 754 (1985)

Spécification de deux formats de nombres binaires en virgule flottante
-  Un signe
-  Un exposant encodé avec un biais de 7 (simple) ou 10 (double) bits
-  Une mantisse

## Biais de l'exposant dans IEEE 754

Utilisé pour représenter des exposants négatifs = valeur proche de 0
Applications du biais en addiotionnant 2k^-1 -1 à l'exposant où k représente le nombre de bits utilisé pour l'exposant

![[Pasted image 20250915110225.png]]
![[Pasted image 20250915111042.png]]
## Puissances de 2

#misc

![[puissances-2.jpg]]


PEUT-ÊTRE FAIRE SLIDE 76