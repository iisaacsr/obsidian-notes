
Dans le monde réel, plusieurs objets collaborent entre eux pour réaliser des tâches.

-  Un client d'une banque peut créditer son compte bancaire avec un montant d'argent
-  Un enseignant peut évaluer le travail d'un étudiant pour un cours et lui attribuer une note
-  Une personne peut conduire une voiture et la déplacer d'un point A à B

Similairement, en Programmation Orienté Objet, plusieurs `object` collaborent ensemble pour fournir les fonctionnalités d'un programme

-  Une classe `Document` représente un document électronique (PNG, JPEG ...)
-  Une classe `Imprimante` implémente une méthode `imprimer()` qui permet d'imprimer un `Document`

```java
Document monCv = new Document();
Imprimante imprimante = new Imprimante();

if (imprimante.imprimer(monCv))
	System.out.println("Cv imprimé avec succès !");

```

On peut avoir des `object` `Personne` qui déplacent des voitures

```java
public class Voiture {

	public void avancer(Voiture v, int distance) {
		v.avancer(distance);
	}
}
```

Il y a collaboration dès qu'un `object` utilise un autre `object`. Généralement, la collaboration s'effectue par "**envoi de message**".

Dans les langages tels que Java, l'envoi d'un message s'effectue par appel de méthode : envoyer un message à un `object` consiste à appeler une méthode de l'`object`