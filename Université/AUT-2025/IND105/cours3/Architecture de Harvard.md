
![[Pasted image 20250929093122.png]]

Mise en place pour la première fois en 1944 à Harvard, pour l'ordianteur **Mark I**

L'architecture de type Harvard se reconnait par sa **séparation mémoire entre instructions et données**

Le processeur sachant faire la distinction entre mémoire donnée et mémoire programme grâce aux deux bus de communication séparés.

En permettant un **accès parralèle** aux instructions et aux données, l'arhcitecture Harvard offre de meilleurs performance.

![[Pasted image 20250929091752.png]]

#### Exemples d'utilisation

-  Domaines où la **vitesse d'exécution est cruciale**
-  Particulièrement adaptée aux **systèmes embarqués** et au **traitement du signal numérique**

-  Processeur numérique de signal (DSP, *Digital Signal Processing*)
	-  Plusieurs espaces mémoire pour les données
	-  Ex: TMS320

-  Microcontrôleurs
	-  PIC and AVR by *Micropchip Technology*
## Architecture de Harvard modifiée

L'architecture de Harvard modifiée est un mélange des deux architectures précédentes (Harvard et [[Architecture de von Neumann|von Neumann]])

Il peut exister une architecture où
-  Les adresses ROM et RAM sont séparées (Harvard) mais la voie d'accès se fait sur le même bus (Von Neumann)

-  Les adresses ROM et RAM sont partagées (von Neumann) mais les voies d'accès aux instructions et données sont séparés (Harvard)
	-  Le cas de nos ordinateurs personnels jusqu'à un certain point dans la vue haut niveau (accès à la mémoire cache)

![[Pasted image 20250929095335.png]]
