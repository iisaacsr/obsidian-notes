
Crée une nouvelle classe en étendant une classe existante (une `Personne` est une classe existante (mère), une classe `Étudiant` est une classe fille (hérite de `Personne`))

Permet de récupérer dans la classe fille ce qui est défini dans la classe mère (la classe fille **hérite** des attributs et méthodes de la classe mère)
-  `nom`, `prenom`, `addresse` de `Personne` sont transmis par héritage à `Étudiant`

```java
Personne p;
p = new Etudiant();  //  <--- Fine pcq Etudiant hérite de Personne 
```

Par contre, une classe mère ne peut pas être instanciée en tant que la classe fille (une `Personne` n'est pas nécessairement un `Étudiant`)

Le but d'hériter d'une classe mère, est de rajouter des paramètres, méthodes à la classe fille qui ne serait pas attribué à la classe mère 
-  Un `Étudiant` pourrait avoir la méthode `etudier()`, le paramètre `note`, etc ...

En java, nous héritons en utilisant `extends` pour hériter d'une classe mère

```java
class Etudiant extends Personne
```

L'héritage crée des *familles d'objet* partageant le même type de base


![[animaux.gif]]

## Exemple

Voici une exemple de projet de base d'application mobile utilisant Java, où un peut voir que la classe `MainActivity` hérite de `AppCompatActivity`. C'est utile, parce qu'`AppCompatActivity` est une classe fondamentale pour toute application Android java, contenant des milliers de LOC qui gèrent plusieurs choses, comme le cycle de vie de l'activité (on peut voir avec `onCreate`), la gestion de vues, etc ...

```java
package com.stoudeft.monapplicationmobile;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class MainActivity extends AppCompatActivity {
	@override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main)
	}

}
```