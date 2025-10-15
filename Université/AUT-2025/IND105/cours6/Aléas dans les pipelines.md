
Le bon fonctionnement du pipeline peut être perturbé par plusieurs évènements (aléas)
-  *Pipeline hazard* en anglais

**Un aléa est une situation qui empêche l'instruction suivante de s'exécuter au cycle d'horloge prévu**

Un aléa peut engendre des bulles dans le déroulement temporel, où le pipeline est en position bloquante sur au moins un étage. 
-  Dans ce cas, le pipeline n'agit plus de manière normale durant ce laps de temps

Une bulle fait apparaître du retard qui se répercute dans le temps

Il y a 3 catégories d'aléas

-  Aléas structurels
-  Aélas de données
-  Aléas de contrôle / branchement

## Aléa structurel

L'aléa structurel intervient quand deux instructions dans des étages différents du pipeline nécessitant la même ressource

**Exemple** : des load/store et une instruction en cours de chargement
-  Load/store utilise la mémoire (écrire ou lire)
-  L'autre doit être également chargée

![[ind105 aléa structurel ex.png]]
[[Architecture de von Neumann]]

#### Potentielle solution

La mémoire séparée pour les données et les instructions est une solution. Aujourd'hui, les CPU ont des [[Mémoire cache|caches]], il peut y avoir un cache exclusivement pour les instructions et un cache uniquement pour les données
-  [[Architecture de Harvard#Architecture de Harvard modifiée|Architecture de Harvard modifiée]]
	 -  Correspondant à l'architecture utilisée aujourd'hui
	 -  Instruction cache et Data cache

## Aléas de données

La suite d'instruction exerce une influence sur les aléas de données

Un aléa de données intervient lorsqu'une instruction produit un résultat, et qu'une instruction suivante utilise ce résultat avant qu'il ait pu être écrit dans le banc de registres
-  Résultat pas à jour pour la seconde instruction
-  Seules certaines suites d'instruction vont induire des aléas de données

![[aléas de données ex ind105.png]]

#### Potentielle solution

Inefficace d'attendre qu'une donnée soit écrite dans les registres
-  Disponible plus tôt

Création de chemins supplémentaires entre les différents étages du pipeline
-  Passage des données plus rapidement d'une instruction à l'autre
-  **Forwarding**
	Chemins supplémentaires entre l'étage

Le résultat de l'instruction est disponible à la fin de l'étape EX. De plus, le résultat est utilisé aussi à l'étape EX de la 2ème instruction
-  Création d'un chemin de donnée de la sortie de EX vers l'entrée de EX

**Exemple** : 
![[solution aléas de donnée ind105.png]]


## Aléas de branchement

Les instructions sont stockées de manière contigües dans la mémoire

-  Le registre Program Counter est incrémenté de 1 et indique l'instruction suivante
-  Il existe **l'instruction de branchement** pour changer la valeur du registre Program Counter et sauter les instructions contigües

Lorsqu'un branchement est pris, l'adresse de celui-ci est calculée à l'étape EX et rangée dans le registre PC à l'étape WB

Toutes les instructions qui suivent l'instruction de branchement ne doivent pas être exécutées. 

Au niveau de pipeline, on obtient le diagramme d'exécution suivant : 

![[aléas branchement ind105.png]]

Pour les branchements conditionnels, l'adresse du branchement est soit le contenu d'un registre, soit la somme de PC et d'un offset

Dans les deux cas, cette valeur peut être rendue disponible à la fin de l'étape ID

Le prix à payer est l'ajout d'un nouvel additionneur dédie à ce calcul

La nouvelle adresse est alors écrite dans le registre PC à la fin de l'étape ID

## Prédiction de branchement

Après la prédiction, on commence l'instruction suivante

Si prédiction érronée

-  On commence des calculs inutiles
-  Vidage du pipeline pour reprendre dans un état correct : **flush**
-  Très coûteux en temps
-  Très pénalisant pour des pipelines profonds

Il faut un bon algorithme de prédiction de branchement

Principe de prédiction

![[prédiction aléas ind105.png|left]]

-  Mémoriser les adresses des branches du programme et regarder celles qui sont souvent atteintes
	Pour les prédire
-  Deux branches : lignes 3 et 5
-  Prédiction : lors du saut conditionnel à la ligne 2, on prendra la branche la plus souvent atteinte

Pour réaliser les prédictions de branchements
-  Tampon des branches cibles (BTB : Branch Target Buffer) : Contient les adresses des branches du programme
-  Table de l'historique des branchements (BHT : Branch History Table) : Mémoriser l'historique des choix de branchements faits précédemment pour faire des prédictions

Le fonctionnement dépend de l'algorithme utilisé

#### Exemple basique

2 bits associés à chaque branche

-  00 (N) : branchement jamais pris jusqu'à présent
-  01 (n) : branchement parfois pris jusqu'à présent
-  10 (p) : branchement souvent pris jusqu'à présent
-  11 (P) : branchement toujours pris jusqu'à présent

Mise à jour des BTB et BHT pendant l'exécution du programme

Pour plus d'efficacité des prédictions
-  Augmenter la taille du BTB et BHT
	Pour pouvoir gérer plus de branches (BTB)
	Pour avoir un historique plus long et précis (BHT)

Augmenter la qualité de la prédiction avec des algorithmes plus efficaces

Dans les 2 cas : augmentation du temps de la prédiction
-  Contraire au besoin de connaître plus tôt la prédiction
-  Limite la montée en fréquence du processeur

Efficacité des prédiction
-  En moyenne, autour de 90% des prédictions sont correctes

![[ind105 prédictions.png]]


## Conclusion

| Avantages pipeline long                                     | Inconvénients pipeline long                     |
| ----------------------------------------------------------- | ----------------------------------------------- |
| Plus d'instructions en exécution parallèle                  | Une erreur de prédiction est plus coûteuse      |
| Montée en fréquence du processeur facilitée                 | Plus d'opération en cours d'exécution à annuler |
| Gain en nombre d'instructions exécutées pour un temps donné |                                                 |
