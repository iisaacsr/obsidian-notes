
Exemple programme en C
```C
#include <stdio.h> <--- prototype des fonctions

int main(int argc, char *argv[]){           //  <---- ou void
	printf("Hello, world! \n");
	return 0;
}
```

### To compile :

Pour compiler notre code C, nous allons utiliser un compiler appelé GCC, ou GNU Compiler Collection. Il sert pratiquement, à décompiler notre code source (C, dans ce cas) en code système. 

GCC supporte plusieurs langages différents ! (cpp, objective-c, fortran, golang etc...)

	Using `gcc`

In `cmd`

```
gcc helloWorld.c
```

Returns a `.out` file

```
./a.out

()
Hello World !
()
```

You can also do `gcc -O1`, `-O2`, `-O3` (not zero, o) to optimise your code at compile time. . Don't do it for debug though, because the optimization slows down compile time, to favour optimized code.

The base GCC command will be with the `-O0` tag, which will be the one closest to our source code, which will be faster compiling, and what we want for debug.

#### make & Makefiles (misc)

`make` est un outil servant à build des programmes et librairies par du code source en lisant des fichier qu'on appelle des `Makefiles`.

Un fichier `Makefile` est un fichier text spécifique, servant à indiquer des règles de build. Chaque règle a :

-  Quelle **cible** build, (un fichier `.exe`, une library, etc... )
-  Les **dépendances** de la cible, (fichiers sources, fichiers headers, etc...)
-  Les **arguments d'extra** pour le build, par exemple
```cmd
gcc -c ma_source_1 -o ma_source_o
```

`make` et la création de `Makefile`s  sert à automatiser la compilation du code (C, dans notre cas), et personnaliser rapidement notre commande de build sans devoir le faire manuellement à chaque fois

## Étapes de compilation

#todo read on this

 1.  `#include`
 2.  `#define`
 3. `#ifdef`
 4. `#ifndef`


Le langage C est un langage typé. Le type d'une variable est spécificé dans le code source.

Une variable est constituée de 3 éléments:
 -  Son type
 -  Le nom
 -  Sa valeur

```C
#include <stdio.h>

int main(int argc, char *argv[]){           
	printf("Hello, %s!\n, name");
	return 0;
}
```

## Typing #todo 

char = 1 octet, short (dépend de l'architecture), int (dépend de l'architecture), long (dépend de l'architecture), long long (dépend de l'architecture)

float = simple précision, double = double précision,

bool `<stdbool>`, void* (pointeur générique), size_t (type compteur, pretty much an unsigned long. should use it in a for loop)

** `sizeof()` returns size of a var


```C
int main(int argc, char *argv[]){           
	bool istrue = true;
	
	printf("Size of Integer" : %d\n, sizeof(a));
	printf("Size of Short" : %d\n, sizeof(b));
	printf("Size of Long" : %d\n, sizeof(c));	
	printf("Size of Character" : %d\n, sizeof(d));
	printf("Size of Float" : %d\n, sizeof(e));
	printf("Size of Boolean" : %d\n, sizeof(f));	
}
```

```
()

Size of Integer : 4
Size of Short : 2
Size of Logn : 8
Size of Charater : 4
Size of Float : 1
Size of Boolean : 1

()
```

## Include logic 

```C
#include <zlib.h>
#include <stdio.h>

int main(int argc, char *argv[]){           
	printf("zlib version: %s\n, zlibVersion()");
	return 0;
}
```

Would fail, running like seen up top.

You have to do this to include a lib

```
gcc -01 helloWorld.c -lz
```

## Misc

```C
int main(int argc, char *argv[]){           
	double a = 1.0;
	double b = 1.0;
	double c = 1.0;
	
	printf(a + b + c);	
}

()

3.0000000000003; // <------ This is because doubles are not displayed properly                  // in C. Be careful. Same with floats.   
()
```

#todo lookup `typedef()` 


### Tableaux

Un tableau est une structure permettant de stocker plusieurs valeurs de même type dans une zone de mémoire configurée. 

Chaque élément est indentifié par un index (0,1,2,3,4) et la taille de tableau est fixe une fois définie.

Un tableau n'existe pas dans la RAM. C'est plusieurs données avec des addresses l'une à côté de l'autres dans la RAM.

***Il a pas d'***`ArrayIndexOutOfBoundsException` ***avec C. Il faut faire attention (faille de sécurité) !***

#todo 

```C
int main(void)
{
	int tab[-94, 76, -49, -53, 22]
	int n = sizeof(tab) / sizeof(tab[0])); // (length) ?  #todo

	for (int i = -; i < n; i ++)
	{
		printf("tab[%d] - %d\n", i, tab[i]);
	}
	
	return 0;
}

()

tab[0] = -94
tab[1] = 76
...

()
```


## Comment la mémoire est allouée ?

#todo BIG DESC needed

-  Code machine (Text Segment) ->
-  Données initialisées  ->
- Données non initialisées ^ (Variables statiques/ globales)
- Mémoire dynamique (Heap -> Stack) ->
- Arguments de la ligne de commande et variables d'environnement

#### Allocation statique :

-  Ambiguë avec l'allocation automatique
Une allocation statique se produit lorsqu'on utilise le mot clé static, lorsque la variable est globale.
Elle est allouée dans la section des variables statiques

```C
static int tab[1, 2, 3, 4]
```

#### Allocation automatique #todo

-  Parfois appelée aussi statique parce que la taille est déterminée à la compilation
-  Dans touts les exemples que nous avons vu c'était des allocaitons statiques.
L'espace mémoire est allouée sur la pile du système

#### Allocation dynamique

-  La mémoire allouée avec la fonction `malloc()` se trouve dans le *heap*.
La mémoire doit être libérée manuellement avec la fonction `free()`

```C
int *tab = malloc(7*sizeof(int));
```

- `void* malloc()` 
	alloue un bloc de mémoire sans l'initialiser, le contenu de ce bloc est donc indeterminé après la `malloc()`
- `void* calloc()`
	alloue un bloc mémoire de taille N* size et l'initialise à 0 bit à bit.
- `void* realloc()`
	(reallocation) permet de modifier dynamiquement la taille d'un bloc mémoire précédemment alloué avec `malloc()`, `calloc()` ou `realloc()`
- `void free` 
	désalloue la mémoire précédemment allouée à l'aide de l'une des 3 fonctions

## Pointeurs

Un pointeur est une variable qui contient une addresse mémoire

Il peut être
- Réassigné pour pointer ailleurs
- NULL
- Incrémenté et décrémenté

```C
int tab[] = {1, 2, 3, 4 ,5}
int* p = tab;
printf("Premier élément: %d\n", p[0]);
```


#todo this is wrong? change it
```C
for(int *p = tab; p = (val); p++) 

// In this case, p++ (on the Array) would go up one index, as we are going up // one point of the pointer (mem address) !
```

## Double pointeur

C'est un pointeur qui pointe sur un autre pointeur.

```C
int x = 42 // Une variable entière
int *p = &x // Un pointeur vers x
int **pp = &p // Un pointeur vers p
```

Il y a deux grandes utilisations : 
-  Modifier un pointeur dans une fonction (comme allouer un nouvel espace mémoire)
- Tableau à plusieurs dimentions

```C
int** mat; // Chaque ligne est un pointeur vers un int
```


## String

En C, une chaîne de caractères (string) est implémentée comme un tableau de char terminé par un caractère spécial `\0` (appelé caractère null ou null terminator)

Ce n'est pas un type natif du langage 

Exemple : 

[B]  [o]  [n]  [j]  [o]  [u]  [r]  [!]  [\0]

#todo
- `size_t strlen(const char *s)`:
	Retourne la longueur (en nombre de chars) de la chaine s, sans compter le cractère nul
- `char *strcpy(char *dest, const char *src)`
- `char *strcat (char *dest, const char *src`

## Structures (struct)
#todo
Une structure est un regroupement de plusieurs types de variables.

```C
struct Point {
	int x;
	int y;
}
```

### Struct en paramètre d'une fonction

La structure est passée par copie, c'est-à-dire qu'une nouvelle structure est créée et que chacun de ses champs est copié.

**Attention** : Si un des champs est un pointeur, seule l'adresse est copiée. Ainsi, si le contenu de la mémoire pointée est modifé, ce changement affectera à la fois l'original et la copie, car ils partagent la même zone mémoire.