based on [this video](https://www.youtube.com/watch?v=cIbENsYBUhA)

#todo (liste de donnée séquentielle)
Une liste chainée est une structure de donnée séquentielle, qui va servir à
-  Ajouter des données
-  Rechercher des données par position
-  Supprimer des données
-  Etc..

Une liste chainée n'est pas strictement liée ensemble dans la mémoire, comme un [[Intro C lang#Tableaux|Tableau]], mais celle-ci est plutôt "éparpillée" un peu partout dans la mémoire.

À cause de ceci, chaque element **élément** (ou maillon / noeud) d'une liste chainée contient un **pointeur** vers la prochaine donnée de la liste.

Le premier élément de la liste chainée est nommé comme **tête** de la liste, tandis que le dernier est nommé comme **queue**, ayant un pointeur vers  `null` .

![[Pasted image 20250923210044.png]]

#### Insertion / suppression d'éléments

Différemment à un [[Intro C lang#Tableaux|Tableau]], qui ne permet pas d'insérer un nouvel élément (ou supprimer un élément) à un index aléatoire (au milieu), car on devrait décaler toute autre donnée entourant la donnée voulue, une liste chainée vient arranger ce problème grâce aux **pointeurs** dans chaque élément.

Lorsqu'on insère un élément dans une liste chainée, on a qu'à créer l'élément, ajouter le pointeur vers le prochain élément, et **changer le pointeur dans l'ancien élément pointant à celui qu'on décide vers l'élément créé**

-  Attention : L'élément **DOIT** pointer vers l'élément suivant **avant de changer le pointeur ancien vers le nouveau élément**, pour ne pas perdre l'addresse vers l'élément de la liste ! 

![[unnamed 1.jpg]]

## Liste doublement chainée

Une liste doublement chainée est similaire à une liste chainée, sauf qu'elle contient un **pointeur vers l'ancien élément** en plus du pointeur vers le prochain.

![[Liste_doublement_chaînée.png]]

## Misc

En général, l'**accès** et la **recherche** d'un élément est **meilleure** avec un tableau (globalement, à cause de la recherche d'un élément aléatoire non début ou fin), grâce à la recherche dichotomique #todo, mais un liste chainée est meilleure pour tout ce qui est **insertion**, ou **suppression**.



