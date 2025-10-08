
Il se peut qu'on veuille qu'un attribut ou un méthode soit rattachée à la classe plutôt qu'aux instances.

-  On veut imposer des frais d'opération de débit sur un compte : on prélève des frais de 2$ si le solde du compte est inférieur à 1000$.

```java
public class CompteBancaire {
	private String numero;
	private String titulaire;
	private double solde;
	private static double fraisOperation = 2; // 2$

	public static double getFraisOperation() {
		return fraisOperation;
	}
	
	public void debiter(double montant) {
		if (this.solde < 1000)
			this.solde -= fraisOperation;
		this.solde = this.solde + montant;
	}
}
```

Nous rattachons l'attribut `fraisOperation` à la classe, plutôt qu'à l'instance, ce qui **évite du code dupliqué**.

Si on veut appeler la méthode `getFraisOperation` à partir de la classe (sans avoir besoin d'un objet), nous devons rendre la méthode statique.

```java
double frais = CompteBancaire.getFraisOperation();
```