
Une `interface` est similaire à une classe qui ne contient que des méthodes abstraites. Elle permet de spécifier (ou imposer) les méthodes qu'une catégorie d'objets doit fournir.
-  Une `interface` contient **seulement** des méthodes / paramètres `abstract` (ou des constantes).

```java
public interface Message {
	void lire();
	String getExpediteur();
}
```

Dans ce cas ^, cette `interface` pourrait être utile dans le cas d'une application du genre Outlook, où on a plusieurs styles de messages (courriels, messages vidéos, messages audio, etc...)

Une classe peut implémenter une `interface`; elle doit alors définir toutes les méthodes de l'`interface`

```java
public class MessageTexte implements Message {
	@Override
	public void lire()
		// lecture du message texte ...
	@Override
	public String getExpediteur(){
		// ...
	}	
}
```

