
Considérons la classe `CompteBancaire` suivante : 

```java
public class CompteBancaire {
	private String numero;
	private double solde;
	
	public void crediter(double montant) {
		solde = solde + montant;
	}
}
```

Une [[OOP#Méthodes d'instance|méthode d'instance]] est appelée pour un objet donné. Par exemple, avec 2 objets de type `CompteBancaire`, 

```java
CompteBancaire cpt1 = new CompteBancaire(),
			   cpt2 = new CompteBancaire();
```

Lorsqu'on appelle `crediter(200)` pour `cpt1` et `cpt2`, leur solde est augmenté de 200. 

Il y a donc un paramètre implicite qui est l'objet qui lui fait appel. L'en-tête de la méthode `crediter()` montre un seul paramètre : `double montant`

Mais en réalité, il y en a **deux** :
-  `cpt1` : paramètre implicite
-  `200` : paramètre explicite

Il arrive qu'on ait besoin d'accéder au paramètre **implicite** (l'objet qui fait appel à la méthode)

En Java, cet objet est référencé par la référence prédéfinie `this`.

```java
public void crediter(double montant) {
	this.solde = this.solde + montant;
}
```

#### Utilisation

L'utilisation de `this` est **nécessaire** lorsque le paramètre d'une méthode ou d'un constructeur porte le **même nom que l'attribut de l'objet**

```java
public class CompteBancaire {
	private String numero;
	private double solde;
	
	public CompteBancaire(String numero) {
		this.numero = numero; // NÉCESSAIRE ICI
		solde = 0; // PAS NÉCESSAIRE
	}
}
```

Il arrive aussi qu'on utilise `this` pour faire **référence à l'objet dans son entièreté**

```java
public class CompteBancaire {
	private String numero;
	private double solde;
	
	@Override
	public String toString() {
		return "Compte numéro [" + numero + "] avec " + solde + "$";
	}
	
	public void afficher() {
		System.out.println(this);
	}
}
```