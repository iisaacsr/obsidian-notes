-  Les performances du CPU s'améliorent d'années en années
- **Problème** : La RAM est moins rapide que le processeur
	-  Le temps d'accès à la mémoire est du temps durant lequel le processeur n'exécute pas d'instruction
	-  Sauf s'il y a présence d'un pipeline

![[Pasted image 20250929110133.png]]

**Solution** : la mémoire cache, pour accélérer les performances de l'ordinateur

La cache est une mémoire intercalée entre la mémoire plus rapide (délai de propagant plus court)

Souvent fabriqué à partir de la SRAM, eDRAM (embedded DRAM)

![[Pasted image 20250929145416.png]]
#### Généralité

Le cache est une mémoire proche du processeur, donc l'espace est restreint

La cache est une mémoire rapide, mais une mémoire à faible capacitié
-  Un **choix** sur les données présentes doit être effectuée
-  La cache contient une cioue de certaines données présentes dans la RAM
-  Les autres données doivent être lues / écrites dans la RAM

#### Succès de cache

-  Si la donnée voulue est dans le cache, l'accès se fera **automatiquement** depuis la cache
	-  On appelle cela le succès de cache, ou le **cache hit**
	- On le veut le plus élevé possible

-  Si la donnée n'est pas dans la cache, on l'accède depuis la RAM
	-  On appelle cela un Défaut de cache, ou **cache hit**
	-  On le veut le plus bas possible

#### Données présente dans le cache

-  Le cache contient une copie de certaines données présentes dans la RAM

Elle se repose sur deux principes
-  Principe de localité spatiale
	Une adresse demandée à l'adresse **adr** engendra certainement un accès à la donnée à une adresse très proche de **adr**
-  Principe de localité temporelle
	Si on accède à une case mémoire ony accèder sans doute bientôt
	
-  **Localité spatiale**
	Les données de la mémoire sont mémorisées dans le cache par bloc de données; ce bloc s’appelle [[Mémoire cache#Ligne de cache|Ligne de cache]]. Il est plus grand qu’un mot mémoire.

![[Pasted image 20250929150013.png]]

Le cache contient une copie de certaines données présentes dans la RAM. Le choix sur les données préésentes suit une logique algorithmique:
-  Algorithme de Bélàdyl algorithme LRUM algorithme LRU, etc... (*algorithme de remplacement de ligne de cache*)
-  Une mise à jour des données présentes dans le cache se fait lors d'un accès dans la RAM (cache miss)

## Défaut de cache (cache miss)

Le défaut de cache peut avoir plusieurs origines
-  Premier accès au cache (la donnée n'étant pas de base dans le cache)
	On appelle ça un cold miss, impossible à éviter

Liée à la taille du cache (le cache est trop petit pour stocker les données utilisées), les anciennes données peuvent être supprimées
-  On appelle ça un défaut de capacité ou **Capacity Cache Miss**
-  Pour une même capacité de cache, le pourcentage dépend de l'*algorithme de remplacement*


## Ligne de cache

Les lignes de cache sont plus grandes que des mots mémoire

Example d'ordre de grandeur :
- mot de 64 bits, c'est-à-dire une adresse retourne une série de 64 bits
-  Une ligne de cache = 128 octets
-  Un mot est 16 fois plus petit qu'une ligne de cache

Comment la mémoire cache voit la RAM ?
-  Découpage de la RAM en morceau = de la taille d'une ligne de cache
	(pas égale à un mot)

#### Accès à la mémoire cache

![[Pasted image 20250929111604.png]]

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


-  Correspondance 1-1 entre adresse et ligne de cache
	-  Plutôt correspondance multi-adresses pour une ligne de cache
	-  Car une ligne de cache est plus grande qu'un mot

-  Tableau de correspondance entre tags et lignes de cache
-  Lors d'un accès mémoire, le cache extrait le tag et l'adresse à lire ou écrire, et le compare avec les tags de chaque ligne de cache

-  Si une ligne contient ce tag, alors la donnée est dans le cache
	La ligne de cache est lue depuis le cache et envoyée à un multiplexeur qui sélectionne la donnée à lire dans la ligne de cache (des fois une ligne de cache comportant plusieurs mots mémoires)

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