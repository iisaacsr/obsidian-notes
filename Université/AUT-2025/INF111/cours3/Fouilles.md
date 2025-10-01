
## Fouille séquentielle

La fouille séquentielle consiste à parcourir séquentiellement la structure de données jusqu'à ce qu'on trouve l'élément cherché ou qu'on traverse toute la structure.

```java
int i, position = -1;
double tableau[] = {2.9, 8.6, 7.6, 7.2, 5.0, 2.5, 6.4, 11.1, 13.3, 10.5};
double valeurCherchee;
boolean trouvee;
valeurCherchee = scanner.nextDouble();
i=0;
trouvee = false;
while (i<tableau.length && !trouvee) {
	if (tableau[i] == valeurCherchee) {
		position = i;
		trouvee = true;
	}
	i++;
}
if (trouvee)
	System.out.println("La valeur "+valeurCherchee+" est à la position "               +position);
else
	System.out.println("La valeur "+valeurCherchee+" n'existe pas.");
```

## Fouille dichotomique (binaire)

Les éléments doivent être préalablement triés.

```java
double tableau[] = {2.5, 2.9, 5.0, 6.4, 7.2, 7.6, 8.6, 10.5, 11.1, 13.3};
double valeurCherchee = scanner.nextDouble();
boolean trouvee = false;
int debut = 0;
int fin = tableau.length-1;
int milieu = -1;
while (debut<=fin && !trouvee) {
	milieu = (debut+fin)/2;
	if (tableau[milieu] == valeurCherchee) {
		trouvee = true;
	}
	else if (tableau[milieu] > valeurCherchee) {
		fin = milieu-1;
	}
	else {
		debut = milieu+1;
	}
}
if (trouvee)
	System.out.println("La valeur "+valeurCherchee+" est à la position "+milieu);
else
	System.out.println("La valeur "+valeurCherchee+" n'existe pas.")
```


## Fouille séquentielle ordonnée

Si le tableau est trié, on peut arrêter la recherche dès qu'on arrive à un élément plus grand que celui qu'on cherche

```java
int i;
double tableau[] = {2.5, 2.9, 5.0, 6.4, 7.2, 7.6, 8.6, 10.5, 11.1, 13.3};
double valeurCherchee;
System.out.print("\nQuelle valeur cherchez-vous ? ");
valeurCherchee = scanner.nextDouble();
i=0;
while (i<tableau.length && tableau[i] < valeurCherchee) {
	i++;
}
if (i == tableau.length || tableau[i] > valeurCherchee)
	System.out.println("La valeur "+valeurCherchee+" n'existe pas.");
else
	System.out.println("La valeur "+valeurCherchee+" est à la position "+i)
```