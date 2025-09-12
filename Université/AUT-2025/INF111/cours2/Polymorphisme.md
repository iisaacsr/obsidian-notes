
Polymorphisme = *poly* + *morphe* = plusieurs formes. La polymorphisme sert aux objets de se comporter différement selon le contexte. Il est intimement lié au concept d'héritage.

Le polymorphisme contient plusieurs sous-concepts; 

-  [Surcharge (Overloading)](#Surchage(overloading))
-  [Redéfinition (Overriding)](#Redéfinition(overriding))
-  Méthodes virtuelles et liaison dynamique
-  [Classes et méthodes abstraites (`abstract`)](#Méthodes(abstraites))

![[polymorphism.png]]

```java
Car car;

car = new Maruti()
	// car = new Brezza();

car.speed();   // <-- dans ce cas, on retourne 60km/h (vu que c'est une Maruti)
```

## Surchage (overloading)

Plusieurs méthodes de même nom dans une même classe (à condition que chacun ait une signature différente.) 
-  Surchage de constructeurs
-  Surchage de méthodes

Le compilateur détermine quelle version de la méthode surchargée doit être appelée en se basant sur les types, et le nombre d'arguments passés lors de l'appel. 

**Le type de retour n'est pas pris en compte dans la signature pour la surchage**

```java
public Car() {  // <--- Constructeur par défaut
}

public Car(int speed) {   // <--- Surchage de constructeur
 this.speed = speed;
}

public Car(int speed, String name) {  // <--- Surchage de constructeur
 this.speed = speed;
 this.name = name;
}

public double distance(Car car) {
	return Math.sqrt(Math.pow(abscisse.p.ab))
}

public double distance(Car currentCar, car otherCar) {
	// ...
}

// etc...
```

## Redéfinition (overriding)

On redéfinit une méthode d'une classe afin d'adapter à nos besoins, sans changer le comportement de tout autre objet avec instance de la classe mère (donc, on override souvent des méthodes / classes de la classe mère dans la classe fille)

```java
package com.stoudeft.monapplicationmobile;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

	@Override        // <------ redéfinition de override de AppCompatActivity
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main)
		
		System.out.println("new mobile app")
	}

}
```

## Méthodes abstraites

```java
public abstract class Forme { 
    public abstract double zone(); 
    public abstract double perimetre(); 
}

public class Cercle extends Forme {
    private double rayon;

    public Cercle(double rayon) {
        this.rayon = rayon;
    }

    @Override
    public double zone() {
        return Math.PI * rayon * rayon;
    }

    @Override
    public double perimetre() {
        return 2 * Math.PI * rayon;
    }
}
```

Une méthode abstraite est une méthode qu'on ne peut pas définir : on connait sa signature, mais pas on implémentation

Lorsqu'une méthode est abstraite, la classe devient donc abstraite (on a une méthode qu'on ne peut pas définir)

Alors, nous ne pouvons pas l'instancier (car elle n'a pas de raison d'être instanciée, la classe fille devrait l'être à la place !)

![[formes1.jpg]]
