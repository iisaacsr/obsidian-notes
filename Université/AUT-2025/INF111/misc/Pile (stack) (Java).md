
![[pile (stack) java ind111.png]]


Une pile est une structure de données qui permet d'empiler les données les unes au dessus des autres (comme un pile de livre sur une table)

#### Opérations

**Empiler** (push)
-  Ajoute une donnée au sommet 

**Dépiler** (pop)
-  Retirer la donnée au sommet

**Consulter** (peek)
-  Consulte la donnée au sommet de la pile sans la retirer

**Vérifier** (isEmpty)
-  Vérifie si la pile est vide

**Taille** (size)
-  Consulte la taille de la pile (nombre de données empilées)


#### Exemples

-  Une pile d'appel des fonctions (call stack) dans la machine virtuelle Java
-  Une boîte de courriel
-  Historique des actions dans un environnement de dévelopmment


#### Implémentation

![[implementation stack java ind111.png]]
**Algorithmes**

```java
size() : 
	return sommet + 1;
isEmpty() :
	return sommet<0;
peek() :
	if(isEmpty())
		return null; // or exception
	return donnees[sommet];
push(object) :
	if(size() == donnees.length)
		return false; // or exception
	donnees[sommet] = object;
pop() :
	if(isEmpty())
		return null; // or exception
	x = donnees[sommet];
	donnees[sommet] = null;
	sommet--;
	return x;
```