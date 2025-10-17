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

## Hiérarchie de la mémoire cache

![[cache hierarchy ind105.png]]

Pour trouver un compromis entre le prix et l'efficacité, plusieurs niveaux de cache sont utilisés
-  Les caches L1, L2, L3
-  Le cache L1 est plus rapide que le L3, il est plus petit
-  Le cache L1 est le plus près du CPU

Les hiérarchies de la mémoire cache utilise généralement de la SRAM (rapide, onéreuse, peu dense)

Il peut exister du cache avec du DRAM embarqué (eDRAM)

![[cache hierarchy literally ind105.png]]

Un niveau de cache peut être lié à un seul coeur.

Un autre niveau de cache peut être partagé entre les coeurs.

![[ind105 cache triangle.png]]

#### Accès d'une donnée dans le cache

On vérifie sa présence dans le L1, le L2, puis le L3. sinon, la donnée est prise dans la RAM

## Défaut de cache (cache miss)

Le défaut de cache peut avoir plusieurs origines
-  Premier accès d'une donnée au cache (la donnée n'étant pas de base dans le cache)
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

Il existe différent types de caches

Possible différence : comment associer le *tag* et sa position dans le cache
-  Association entre tag et ligne de cache

**Classification des caches**
-  Cache totalement associatif
-  Cache à correspondance établie
-  Cache N-associative
-  etc...

## Cache à correspondance établie

`bloc mémoire = adresse / taille LDC`

ou *direct-mapped cache*

Une adresse en mémoire ne peut se situer qu'à **un seul endroit dans le cache**
-  Réalisée avec une opération modulo
-  Ligne d'adresse en mémoire principale `j`
-  Adresse dans le cache `i`
-  Nombre de lignes de cache `L`

`i = j % L`

Le *tag*, calculé via l'adresse mémoire est comparé avec le tag dans cette ligne de cache
-  Si présent, on a cache hit

Sinon, c'est un cache miss et la donnée doit être récupérée via le RAM

![[cache a correspondance etablie ind105.png]]

**Avantages**

Taux de cache hit faible car à chaque fois qu'on rechercher un bloc avec le même *index* set, on doit remplacer la ligne de cache

 Réduction de la complexité pour chercher la donnée dans le cache
-  Consomattion d'énergie réduite car on sait où se trouve la donnée recherchée
-  Ainsi, la complexité matérielle est faible car une seule comparaison de tag est suffisante

**Désavantages**

Potentielle collision si deux données nécessaires retournent la même ligne de cache pour être positionnée
-  Car le cache est plus petit que la mémoire principale

## Cache totalement associatif

*Fully associative cache* - cache totalement associatif

Une ligne de mémoire principale peut être copiée dans n'importe quelle ligne de la mémoire cache.
 
Le *tag* de l'adresse est comparé au tag de toutes les lignes de la mémoire cache. En cas de *hit*, l'octet est retourné grâce à son *data index* (offset) dans le bloc de données

Pour trouver un mot dans un cache totalement associatif
-  Le tag est comparé à **tous** les tags associés dans chaque ligne de cache
-  Requiert aussi beaucoup de logiques et donc beaucoup d'énergie
-  Si le cache est grand, la recherche de la ligne de cache est trop complexe

Si le tag est présent, on a cache hit
-  Sinon, *cache miss* et la donnée doit être récupérée dans la RAM
-  Large variété d'[[#Algorithmes de remplacement de ligne de caches|algorithmes de remplacement]] (car on peut placer n'importe où)


![[cache totalement associatif ind105.png]]

**Avantages**

Peut offrir une flexibilité pour placer et remplacer les données ([[#Algorithmes de remplacement de ligne de caches|algorithmes de remplacement]])
-  Bon taux de cache hit

**Désavantages**

Complexe, coût élevé
-  On doit comparer **tous** les tags de **toutes** les lignes de cache pour trouver une donnée

Grandeur limitée
-  Un cache trop grand pourrait ralentir extrêmement (à cause de la recherche de donnée)

## Cache associatif par ensembles

ou **set-associative-cache**

La cache est divisée en `n` ensembles (*ways*) de lignes de cache

Un mot est mis d'abord dans un des ensembles puis est mis **dans n'importe quelle ligne de cache**.

![[cache totalement associatif ind105-1.png]]

#### Index

`index = bloc mémoire % nombre d'ensembles`

#### Cas spéciaux

Un cache à **correspondance établie** correspond au cas où il y a autant d'ensemble que de lignes de caches

Un cache **totalement associatif** correspond au cas à un seul ensemble


![[cache associatif par esnemble ind105.png]]

**Avantages**

Cette méthode essaie d'allier la vitesse de la cache à correspondance directe et l'efficacité de la cache totalement associative
-  Taux de *cache miss* relativement fiable

**Désavantages**

La consommation d'énergie est moins importante également par rapport à la cache totalement associative
-  Comparaison de quelques étiquettes uniquement au lieu de toutes les étiquettes

## Algorithmes de remplacement de ligne de caches

La cache peut trop se remplir. Dans le cas où il est plein, des lignes de caches doivent être **supprimées** pour pouvoir faire de la place.

Un type de cache ne peut pas avoir de mécanismes pour évincer des lignes de cache
-  Le cache à correspondance établie, car le remplacement est obligatoirement mis à un endroit précis dans le cache
-  Les autres caches peuvent avoir des algorithmes de remplacement

Les mécanismes de remplacement de ligne de cache doivent théoriquement évincer des données inutiles
-  Pour optimiser l'utilisation de la mémoire
-  Minimiser les défauts de pages

Il existe différents algorithmes de remplacement de lignes de caches

Les **algorithmes de remplacements pratiques** sont basés sur des **heuristiques** et des **prédictions** pour déterminer quelles informations conserver dans le cache
-  Ils ne peuvent pas atteindre le même niveau d'efficacité que l'algorithme optimal de Bèlàdy.

L'**efficacité** d'un algorithme de cache est généralement évalulée par l'expérimentation et la comparaison de ses performances par rapport à d'autres stratégies de mise en cache dans ces cas d'utilisation spécifiques.

#### Algorithme de Bèlady

C'est l'algorithme de remplacement le plus efficace.

Il consiste à toujours éliminer les informations qui ne seront pas nécessaires pendant le plus longtemps à venir
-  Notion de connaissance future

Ce résultat optimal est calculé en se basant sur la connaissance future des modèls d'accès à la mémoire, le rendant **théorique et non-praticable**


#### Remplacement aléatoire

(dans un cache totalement associatif qui est **plein** et qui a vécu un **cache miss**)

La ligne de cache est choisie (pour remplacement) au hasard.

-   Mécanisme naïf, certaines données utiles pourraient être rapatriées. 
-  Contre-intuitif

Néanmoins, le remplacement aléatoire montre des performances plutôt bonnes
-  Les défauts de cache ne suivent pas une logique temporelle
-  Ils sont aussi relativement peu nombreux

Dans le cas d'un petit cache, technique à proscrire
-  Les défauts de caches seront plus nombreux

**Exemple**  #todo

![[remplacement aléatoire cache ind105.png]]

#### Remplacement FIFO
ou *First In First Out*

![[remplacement FIFO ind105.png]]

La donnée la plus ancienne du cache est effacée
-  Simple à implémenter

Technique à proscrire dans le cas d'un [[Mémoire cache#Cache associatif par ensembles|cache associatif par ensembles]]
-  *Anomalie de Bélàdy*

**Exemple** #todo 

![[exemple remplacement FIFO ind105.png]]

#### Remplacement LRU
ou *Last Recently Used*

Supprime la donnée la moins utilisée récemment
-  Une donnée utilisée récemment a des fortes chances d'être de nouveau voulue ...
-  Ainsi, le LRU supprime la donnée la moins utilisée

Cette technique doit avoir un mécanisme qui étudie l'évolution du nombre d'utilisations des données
-  Complese à réaliser

##### Exemple

![[ind105 exemple LRU MRU LFU.png]]

#### Remplacement MRU
ou *Most Recently Used*

Supprime la donnée utilisée la plus récemment

##### Exemple

![[ind105 exemple LRU MRU LFU.png]]

#### Remplacement LFU
ou *Least Frequently Used*

Le remplacement LFU doit implémenter un compteur d'utiliastion pour chaque donnée

Le compteur se fait sur X dernières données

##### Exemple

![[ind105 exemple LRU MRU LFU.png]]

## Performance des mémoires caches

Analyse de la performance des mémoire caches : 

-  **Latence**
	Temps entre la demande d'une demande de donnée et l'arrivée de la première donnée

-  **Débit**
	Flux de données transmises

-  **Efficacité**
	Capacité à empêcher des accès mémoires RAM (dépend du taux du débit)


Taux de succès (hit ratio) Ts = pourcentage d'accès de méoire qui ne déclenche pas de défaut de cache

Taux de succès Td : = pourcentage d'accès de mémoire qui entraîne un défaut de cache

![[performance ind105 cache.png]]

Latence

Tc = latence cache
Tm = latence RAM

![[latence cache ind1-05.png]]