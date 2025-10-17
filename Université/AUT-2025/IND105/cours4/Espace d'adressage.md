
## Adresse mémoire

L'adresse représente un emplacements unique où la donnée peut être lue

Pour différencier les adresses, chaque adresse est une suite de bits unique, exprimé en hexacédimal.

#### Architecture ancienne

**Dans les architectures anciennes**, l'adresse correspond à un [[#Mot mémoire]] d'une certaine taille.

Un mot mémoire possède une adresse qui lui est propre.

## Architecture récente

Dans les architectures récentes (Intel, ARM), l'adresse correspond à un octet en mémoire

La taille de mémoire adressable dépend donc du nombre de bits utilisés pour l'adresse (**les mots mémoires font plus que 1 octet**)

## Mot mémoire

Un mot mémoire est l'unité de lecture / écriture du processeur.
-  Sa taille dépend de l'architecture

La taille du mot mémoire influence la quantité de données qui peuvent être transférés en une seule opération
-  Impact direct sur les performances du système

 Une mémoire avec une taille de mot de 64 bits peut transférer deux fois plus de données en une seule opération qu'une mémoire avec une taille de mot de 32 bits.

-  Une architecture de 64 bits a des mots mémoire de taille 64 bits (8 octets)
-  Une architecture de 32 bits a des mots mémoire de taille 32 bits
-  L'adresse d'un mot doit être un multiple de sa taille (contrainte d'alignement)

[De l'octet aut mot mémoire (vidéo)](https://www.youtube.com/watch?v=qDGjg5YNSJk)
#### Exemple

Si l'espace mémoire est composé de 
-  64 Ki o = 65536 octets
-  65536 adresses
-  Chaque adresse étant unique, il faut donc ![[Pasted image 20250929103954.png]]
-  bits pour générer une adresse unique

-  Ou 4 chiffres hexadécimaux

#todo 

## Espace d'adressage

L'espace d'adressage est la plage d'adresse mémoire (emplacement mémoire) qu'un ordinateur utilise pour accéder aux données stockées en mémoire.

Bornée entre deux adresse
-  La plus petite
-  Ainsi que la plus grand
-  Exprimée en hexadécimale

#todo 

L'espace d'adressage est divisée en plusieurs parties contigues
