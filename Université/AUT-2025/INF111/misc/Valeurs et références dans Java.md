
Il existe une différence fondamentale entre les données primitives et les `Object` ; une variable primitive désigne la valeur de la donnée, tandis qu'un `Object` désigne l'adresse mémoire de l'`Object`

Donc, une variable de type `Object` est une référence vers un objet.

## Exemple

*Une affectation de données primitives est une affectation de valeurs*

```java

	int a = 5;
	int b = a;
	
	a = 10;
	
	System.out.println(a); // Affiche 10
	System.out.println(b); // 'a' devient 10, mais b reste 5

```

*Une affection d'`Object` est une affectation de références*

Utilisons la classe [Programmeur](OOP.md#Recap)

```java

	Programmeur prog1 = new Programmeur()
	Programmeur prog2 = prog1;
	
	prog1.setNom("Karl"); // Modifie l'Object vers prog1 pointe (donc aussi prog2)
	
	System.out.println(prog1.nom); // Affiche 'Karl'
	System.out.println(prog2.nom); // Affiche aussi 'Karl'                                                            // (car c'est le même Object) 

```

