
### Please keep in mind that this file is meant for Java. OOP should (and could) be replaced with Java any time


# OOP Datatypes

-  `int`
	Nombre entier
-  `double`
	Nombre rééel
-  `double[]` (array)
	Tableau de nombres réels
-  `Object`
	Donnée structurée qui est composée d'une ou plusieurs données plus simples (attributs)
	
	Permet de regrouper plusieurs données pour en faire un tout
	
	Un programmeur, compte bancaire, etc...
	
	Pour créer des `Object` de ce genre, le langage de prog ne ne fournit pas ceux-ci, **il faut les créer**
	
	Donc, on créée des v
-  `Class`
	Doit être dans un fichier nommé le même nom que celle-ci
	
	Donc, pour `Programmer`, le fichier doit être `Programmer.java`

[CamelCase, https://en.wikiversity.org/wiki/CamelCase]

String dans Java est une `Class`, pas un primitive type

# Déclaration de variables:

```java
*Programmeur* programmeur
```

#todo research this v

Quand on déclare une variable dans Java, le compiler détermine la quantité de mémoire à allocate pour la variable elle-même. Il, ensuite, détermine le nombre de valeurs possibles dans celle-ci, et il détermine les opérations possibles 


`int` is 4 bytes (4 octets).

#todo research this v

TOUTE ESPACE MÉMOIRE DANS JAVA EST 4 BYTEs ?

`int` is always signed (no need for `int` or `uint` like in c++)

Contrairement aux données primitives, la déclaration d'une variable `Object` ne créé pas d'`Object`
# Instanciation

Ce qui mène à l'<u>Instanciation</u>  <--- Opérateur `new`

```java
programmeur = *new* Programmeur();
```

Le compiler va aller chercher la classe `Programmeur`, réserver l'espace mémoire pour l'`Object` Programmeur (espace pour *chaque attribut*)

Donc, l'addresse mémorie que l'opérateur `new` retourne va être affectée à la variable `programmeur`

La variable `programmeur` **référence** l'`Object` (ou pointe) (il n'est pas le vrai `Object`)

Donc, chaque variable réference (détient l'addresse de) un `Object` .

Tous les objets `Programmeur` sont des références à la classe, l'objet `Programmeur`

# Accéder aux données 

Pour accéder aux données (attributs) d'un objet, on utilise l'opérateur point `.`

```java
public static void main (String[] args)
{
	Programmeur programmeur = new Programmeur();
	
	programmeur *.* nom = "Annie"
	
	System *.* out *.* println("Le nom du programmeur est " +                          programmeur *.* getNom() + " !");
}
```

# Encapsulation

L'accès direct aux attributs avec l'opérateur point `.` pose beaucoup de problèmes

  *Comment empêcher qu'on affecte des valeurs négatives au solde d'un compte ?*

J'améliore ma classe `Programmeur` pour  permettre à un `Programmeur` de maitriser plusieurs langages. 

L'attribut ``langage`` de `Programmeur` devient un tableau de `String` et s'appelle maintenant ``langages``

```java
public class Programmeur()
{
	String nom;
	String courriel;
	String[] langages;   <---- NEW
}
```

L'Encapsulation consiste à cacher les données (attributs) d'un `Object` au monde extérieure à l'`Object`

Pour cela, on déclare des **attributs privés**

```java
public class Programmeur()
{
	*private* String nom;
	*private* String courriel;
	*private* String[] langages;
}
```

Les attributs étant privés, on ne peut plus y accéder directement à l'extérieur de la classe.

# Méthodes d'accès

Les attributs étant maintenant privés, nous avons besoin d'y accéder ! Nous allons y accéder en utilisant les méthodes d'accès, qui sont fournies par la `Class`.

Il existe deux types de méthodes d'accès
- Méthodes d'accès en lecture (getters)
	Commence par get (`get____`)
- Méthodes d'accès en écriture (setters)
	Commence par set (`set____`)

```java
public class Programmeur
{
	private String nom;
	private String courriel;
	private String[] langages;
	
	public String getNom()
	{
		return nom;   <---- MÉTHODE GETTER	
	}
	
	public void setNom(String newName)
	{
		nom = newName;   <---- MÉTHODE SETTER	
	}
	
}

public static void main (String[] args)
{
	Programmeur programmeur = new Programmeur();
	
	programmeur.setNom("Karl");  <---- UTILISATION SETTER
	
	System.out.println("Le nom du programmeur est " +                      programmeur.getNom() + " !")   <-- UTILISATION GETTER
}

()

"Le nom du programmeur est Karl !"

()

```

En Java, les attributs sont initialisés par défaut (null).

-  Les objets sont initialisés à `null` par défaut
-  Les types numériques sont initialisés à `0`.
-  Les types caractéristiques sont initialisés à `""` (? #todo)

# Méthodes d'instance

Pour programmer et déboguer, la classe `Programmeur` doit fournir des méthodes d'instance `programmer`, et `déboguer`

```java
public class Programmeur
{
	private String nom;
	private String courriel;
	private String[] langages;
	
	...
	
	public void programmer()  <--- MÉTHODE D'INSTANCE
	{
		System.out.println("Je programme !");  
	}
}
```

## Valeurs et références

#todo maybe needs more development
 
Il existe une différence fondamentale entre les données primitives et les `Object` ; une variable primitive désigne la valeur de la donnée, tandis qu'un `Object` désigne l'adresse mémoire de l'`Object`

Donc, une variable de type `Object` est une référence vers un objet.

Donc,

*Une affectation de données primitives est une affectation de valeurs*, mais
*Une affection d'`Object` est une affectation de références*

# Constructeurs

Pour créer des objets, nous utilisons l'opérateur `new` . L'opérateur `new` invoque un **constructeur** de classe

Lorsqu'on en définit pas, le compiler

détermine un constructeur par défaut. Par contre, nous pouvons en définir un nous-même.

En Java, un `constructor` est une `method` qui : 
-  Doit porter le même nom que la `Class`
-  Ne `return` aucun résultat (même pas void)
-  Peut avoir des paramètres

```java
public class Programmeur
{
	private String nom;
	private String courriel;
	private String[] langages;
	
	public Programmeur()     <--- CONSTRUCTOR SANS PARAM
	{
		nom = "Karl";
		courriel = "karl@mail.com";
		lanages = ["cpp", "ex", "js"];
	}
	
	public Programmeur(String nom)   <-- CONSTRUCTOR W/PARAM
	{
		nom = nom;
		courriel = "karl@mail.com";
		lanages = ["cpp", "ex", "js"];
	}
}

public static void main (String[] args)
{
	Programmeur programmeur = new Programmeur();         // NO PARAM
	Programmeur prograammeur2 = new Programmeur("Karl"); // W/PARAM
}
```

# Recap

```java
package com.isylvainroy.classes

public class Programmeur
{
	// PARAMS

	private String nom;
	private String courriel;
	private String[] langages;
	
	// CONSTRUCTORS
	
	public Programmeur()
	{
		nom = "Karl";
		courriel = "karl@mail.com";
		lanages = ["cpp", "ex", "js"];
	}
	
	public Programmeur(String nom) 
	{
		nom = nom;
		courriel = "karl@mail.com";
		lanages = ["cpp", "ex", "js"];
	}
	
	// MÉTHODES D'ACCÈS
	
	public String getNom()
	{
		return nom;   <---- MÉTHODE GETTER	
	}
	
	public void setNom(String newName)
	{
		nom = newName;   <---- MÉTHODE SETTER	
	}
	
	// MÉTHODES D'INSTANCE
	
	public void programmer()
	{
		System.out.println("Je programme !");  
	}
}

```