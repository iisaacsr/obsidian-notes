
Les tableaux peuvent être crés dynamiquement (c'est-à dire, leur taille peuvent être fixée à l'exécution). Mais, une fois créé, la taille du tableau ne peut plus changer.

Pour avoir une structure de données similaire à un tableau, mais dont la taille augmente au besoin, on peut utiliser des vecteurs.

Il existe plusieurs classes qui permettente de créer des Vecteurs. Parmi ces classes, `ArrayList` est une des plus utilisées.

Un `ArrayList` encapsule un tableau dans lequel sont stockées les données insérées dans le `ArrayList`. Lorsque le tableau est plein, l'`ArrayList` grandit automatiquement.

## Utilisation

Quoiqu'on peut stocker plusieurs objets de types différents, un **vecteur stocke habituellement des objets de la même famille.** 

À la déclaration d'une variable de type `ArrayList`, on doit (quoique pas obligé), **spécifier le type d'objets qu'on y stocke**.

```java
ArrayList<CompteBancaire> v1;
```

Puis à l'instanciation; 

```java
v1 = new ArrayList<>();
```

Donc, dans cet `ArrayList`, nous ne pouvons stocker **que des objets de type `CompteBancaire`.**

#### Types primitifs

Pour créer un vecteur qui stocke des données primitives, on utilise les **classes enveloppes**. 

```java
ArrayList<Integer> v2 = new ArrayList<>();

v2.add(32); // donc, pour ajouter des int
```


## Principales méthodes

Dans la liste ci-dessous, `E` représente le type des éléments stockées dans le vecteur.
#### Insertion

```java
boolean add(E e);
void add(int index, E element);
void addElement(E obj);
void insertElementAt(E obj, int index);
```
#### Accéder aux éléments

```java
E firstElement();
E lastElement();
E get(int index);
E elementAt(int index);
Object[] toArray();
Enumeration<e> elements();
```
#### Supprimer des éléments

```java
E remove(int index);
boolean remove(Object o);
boolean removeElement(Object obj);
void removeElementAt(int index);
```
#### Vider le vecteur

```java
void removeAllElements();
void clear();
```
#### Tester l'état du vecteur

```java
boolean isEmpty();
int size();
boolean contains(Object o);
```
#### Recherche

```java
int indexOf(Object o);
int indexOf(Object o, int index);
int lastIndexOf(Object o);
int lastIndexOf(Object o, int index);
```
#### Remplacer des éléments

```java
E set(int index, E element);
void setElementAt(E obj, int index);
```

## Itérateurs

Pour parcourir tous les éléments d'un vecteur, on peut utiliser une boucle `for` classique.

Par contre, il y a un moyen plus efficace, qui permet de **garder la position de parcours** afin de trouver rapidement l'élément suivant à l'itération suivante.

```java
ArrayList<CompteBancaire> v1 = new ArrayList<>();

//...

ListIterator<CompteBancaire> iterator = v1.listIterator();
CompteBancaire cpt;

while (iterateur.hasNext()) {
	cpt = iterateur.next();
	System.out.println("Solde du compte : " + cpt.getSolde()) + "$";
}
```

On instancie pas nous-même un itérateur. C'est le vecteur qui nous le fournit à l'aide de sa méthode `listIterator()`.

À sa création, l'itérateur se place avant le premier élément. Il faut appeler `next()` pour obtenir l'élément suivant du vecteur, à commencer par le premier : 

![[vector func java inf111.png]]

S'il n'y a pas d'élément suivant, l'appel `next()` déclenche une exception de type `NoSuchElementException`. Il faut donc **toujours vérifier l'existence de l'élément suivant** avant d'appeler `next()`. On utilise la méthode `hasNext()` pour cela.

#### For each

On peut aussi parcourir un vecteur à l'aide d'une stucture `for each`. À l'instar de l'itérateur, la streucture garde la position courante grâce à une variable d'itération

```java
ArrayList<CompteBancaire> v1 = new ArrayList<>();

//...

for (CompteBancaire cp : v1) {
	System.out.println("Solde : " + cpt.getSolde() + "$";)
}
```