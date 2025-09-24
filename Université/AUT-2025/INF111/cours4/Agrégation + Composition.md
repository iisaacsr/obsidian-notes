
Dans le monde réel, on peut assembler des objets pour construire des objets plus complexes.

-  On assemble une carte mère, des barrettes de mémoire, un disque dur pour construire un ordinateur
-  On assemble des briques, portes, fenêtres pour construire un mur, une chambre, une maison

Similairement, dans la Programmation Orienté Objet, on peut assembler des `object` pour construire des `object` plus complexes. Il existe deux concepts similaires pour ceci : l'**aggrégation** et la **composition**.

La différence entre l'agrégation et la composition est reliée à la durée de vie des `object`; 

-  Dans l'agrégation, les agrégés peuvent exister sans l'agrégat. Donc la destruction de ce dernier n'entraine pas la destruction des agrégats. 
-  Dans la composition, les composants ne peuvent pas exister sans le composé. La destruction du composé entraine donc la destruction des composants. 

Dans des langages tels que Java, il n'y a pas de différence notable dans l'implémentation de l'agrégation et la composition. Nous ne ferons donc pas de distinction entre ces concepts dans la suite.

## Agrégation

Dans l'aggrégation, les `object` qu'on assemble pour construire un `object` complexe sont les **agrégats** tandis que l'`object` complexe construit est l'**agrégé**

-  Une bibliothèque contient des livres. Un livre peut exister sans la bibliothèque. Il y a donc une **relation d'agrégation** entre bibliothèque et livre
-  Dans une école, il y a des étudiants. Un étudiant peut exister sans être rattaché à l'école. C'est donc une **relation d'agrégation** entre école et étudiant

## Composition

Dans la composition, les objets qu'on assemble pour construire un `object` complexe sont les **composants** tandis que l'`object` complexe construit est le **composé**

-  Une maison contient des chambres. La destruction de la maison entraine la destruction des chambres (une chambre n'existe pas en dehors de la maison). Il y a donc une **relation de composition** entre la maison et la chambre.
-  Dans une banque, des opérations bancaires sont effectuées sur des comptes. Plusieurs opérations bancaires peuvent être rattachées à un compte. Mais, une opération bancaire ne peut pas exister sans être rattaché à un compte. Il y a donc une **relation de composition** entre compte bancaire et opération bancaire.

## Implémentation

L'agrégation / la composition implémente la relation "possède un" (has a ou **hasA**). Elle se traduit par la présence dans l'agrégé/composé d'attributs de type de l'agrégat/composant.

La plupart du temps, l'agrégé/composé est appelé à [[Collaboration|collaborer]] avec ses agrégats/composants

-  Nous avons une classe qui représente des compteurs

```java
public class Compteur {
	private int valeur;

	public int getValeur() {
		return valeur;
	}
	public void incrementer() {
		valeur++;
	}
}
```

-  Une `Voiture` **possède** un `Compteur`. Lorsque la voiture avance, son compteur augmente

```java
public class Voiture {
	private Compteur compteur;
	
	public void avancer(int distance) {
		for (int i=0;i<distance;i++) 
			compteur.incrementer();
	}

	public int getValeurCompteur() {
		return compteur.getValeur();
	}
}

```