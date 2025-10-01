
#todo complete this whole

## Tri à bulles

![[tri a bulles oop inf111.png]]

Le tri à bulles consiste à comparer deux à deux les éléments consécutifs du tableau et à les permuter si nécessaire.

On continue jusqu'à temps qu'il n'y ait plus de permutation

```java
static void triABulles(int tab[])
{
	int passage = 0;
	boolean permutationEffetuee = true;
	int i, temp;
	while (permutationEffetuee) {
		permutationEffetuee = false;
		passage++;
		for (i=0;i<tab.length-passage;i++) {
			if (tab[i]>tab[i+1]){
				temp = tab[i];
				tab[i] = tab[i+1];
				tab[i+1] = temp;
				permutationEffetuee = true;
			}
		}
	}
}
```

## Tri par sélection

![[tri par selection oop inf111.png]]

Le tri par sélection consiste à chercher le plus petit élément et le mettre en premier; puis à chercher le deuxième plus petit et le mettre en second

```java
static void triParSelection(int tab[])
{
	int i, j, temp, positionPlusPetit;
	for (i = 0; i < tab.length-1; ++i) {
		positionPlusPetit = i;
		for (j = i+1; j < tab.length; j++) {
			if (tab[j]<tab[positionPlusPetit])
			positionPlusPetit = j;
		}
	temp = tab[positionPlusPetit];
	tab[positionPlusPetit] = tab[i];
	tab[i] = temp;
	}
}
```


## Tri par insertion

![[tri par insertion oop inf111.png]]

Le tri par insertion consiste à prendre chaque élément et à l'insérer à la bonne position, comme un joueur de cartes qui trie les cartes de sa main

```java
static void triParInsertion(int tab[])
{
	int i, j, temp;
	for (i = 1; i < tab.length; ++i) {
		temp = tab[i];
		for (j = i; j > 0 && tab[j-1] > temp; j--) {
			tab[j] = tab[j-1];
		}
	tab[j] = temp;
	}
}

```