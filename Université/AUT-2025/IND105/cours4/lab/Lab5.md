
## Q1

 Qu’est ce qu’une mémoire volatile ? Indiquez si la mémoire RAM est une mémoire volatile.
	Une mémoire volatile est une mémoire qui nécessite du courant pour stocker / avoir accès à des données. Donc, la RAM est une mémoire volatile (elle ne stocke rien sans être alimentée)

## Q2

Qu’est ce qu’une mémoire dynamique ? Qu’est ce qu’une mémoire statique ?
	La mémoire dynamique est une mémoire volatile qui a besoin d'un rafraichissement de donnée périodiquement, sous risque de s'effacer si non utilisé assez récemment
	.
	La mémoire statique est aussi une mémoire volatile, mais elle n'a pas besoin d'un rafraichissement de donnée périodique (les données n'ont pas besoin d'être lues pour être stockées pendant un moment)

## Q3
[[Allocation de données#Mémoire vive statique - SRAM|ref]]
Comparez les deux mémoires DRAM et SRAM
	SRAM : La SRAM est moins dense, plus onéreuse, moins énergivore et plus rapide
	DRAM : La DRAM est plus dense, moins onéreuse, énergivore et moins rapide

## Q4

Donnez la définition de la capacité de la mémoire
	La capacité correspond à la taille d'une mémoire, de la mémoire. 

## Q5

Donnez la définition d'un mot mémoire
	Un mot mémoire est l'unité de lecteur / écriture d'un processeur. Sa taille dépend de l'architecture
	.
	Notion d'alignement : Mot de 8o peut seulement être sur des adresses divisibles par 8

# Adressage

Une mémoire est composée d’un nombre M d’adresses mémoires, la taille d’un mot mé-
moire est noté B, la capacité mémoire sera notée C. Dans la suite, nous faisons face à une
architecture récente.

## Q6

[[Mémoire#Capacité|reference]]

Sachant que la dernière adresse de la mémoire est 0x7FFF, indiquez la capacité mémoire C
pour une taille de mot

(a) B = 1o
	0x7FFF + 1 = 0x8000 adresses (commence à 0)
	donc, 0x8000 = 32 768
	alors, la capacité mémoire est de 32 768 octets ou 32 Ko (divisé par 1024)

(b) B = 4o
	encore 32 768 octets (architecture récente, on s'en fout de la taille de mots, on calcule avec l'adresse)

(c) B = 8o
	encore 32 768 octets (architecture récente, on s'en fout de la taille de mots, on calcule avec l'adresse)

## Q7

Une mémoire de `C = 1Tio = 2^40 o` a des tailles de mot de `B = 8 octets`, combien d’adresses
M a cette mémoire ? Indiquez la première et dernière adresse des mots
	.

## Q9 (dont do)


# Architecture de mémoire caches

## Q10
Qu’est ce qu’une ligne de cache, est-elle généralement plus petite ou plus grande qu’un mot
mémoire ?
	 Elle est généralement plus grande qu'un mot mémoire (elle est un segment unitaire mémoire qui englobe des mots mémoire)


## Q12

Indiquez les grandeurs relatives dans un cache à trois niveaux L1 L2 et L3.

-  En terme de taille
	`L1 < L2 < L3`

-  En terme de rapidité
	`L1>L2>L3`

## Q14

Indiquez l’architecture de cache où seulement une ligne de cache doit être vérifiée pour
savoir si la donnée est présente.

Dans la suite, la mémoire principale possède 2^32 adresses. Dans une architecture à corre-
spondance établie avec un cache possédant 128 lignes de caches, de 256 octets chacune.

-  [[Mémoire cache#Cache à correspondance établie|Cache à correspondance établie]]
## Q15

Indiquez la taille du cache en octet

`nb lignes de cache * taille d'une ldc`

-  128 * 256o = 32 768 octets ou 32 Ko
## Q16

Indiquez le nombre de bloc mémoire dans la RAM vue par la mémoire cache.

`taille de la mémoire (C) / taille ligne de cache`

-  2^32 / 256 ou 2^8 octets = 2^24 octets

## Q17

Indiquez le nombre de bits dans le champ tag, offset et index.

-  Offset = Savoir quel octet est demandé dans la LDC
	donc, `taille offset = log2(taille LDC)` ou log2(256) = 8

-  Index = Caractère de numéro de la LDC
	`taille index = log2(nombre LDC)` ou log2(128) = 7

-  Tag = Caractérise si ma donnée est présente
	`taille de l'adresse - index - offset` ou 32 - 8 - 7 = 17 bit

donc [8b = offset, 7b = index, 17b = tag]

## Q18 

Représentez une adresse de la mémoire principale, par exemple : `0x9847DA45`, mentionnez
l’offset, l’index et le tag.


donc, offset = `0x45`
donc, index =  (entre DA)
donc, tag = 0x984...

just redo it in binary man the teacher is lazy

## Q19

Dans le cache à correspondance établie à l’adresse , indiquez les cache miss et cache
hit pour ces deux séquences d’accès mémoire

i dont get it

## Q20

Indiquez une architecture de mémoire cache ne pouvant pas utiliser d’algorithmes de rem-
placement

-  [[Mémoire cache#Cache à correspondance établie|Cache à correspondance établie]]

## Q21 

Remplissez le tableau suivant avec un algorithme First In First Out (FIFO)

(see cahier)

## Q22

6 *cold miss* (il y a 6 données à insérer

## Q23

3 capacity cache miss (could be wrong)

## Q24

10 / 15 taux de défaut (10 miss sur 15)