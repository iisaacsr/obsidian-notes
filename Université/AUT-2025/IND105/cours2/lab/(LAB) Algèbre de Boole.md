
## Q1

Comment se traduit une valeur binaire sur un circuit électrique ?
	 {1,0} donc {vrai, faux}

## Q2

Qu'est-ce qu'une table de vérité?
	Une table de vérité est un tableau qui récapitule toute les possibilités d'une loi, d'un ensemble de portes logiques.

## Q3

Combien de possibilités pour un circuit électrique comportant *n* entrées ? 
	2^n
	(0 ou 1 pour **chaque entrée possible**)

## Q4
#todo [this](https://pressbooks.etsmtl.ca/circuitslogiques/chapter/circuits-logiques-combinatoires-et-sequentiels-7/)
Qu'est-ce qu'un circuit combinatoire ?
	 Un circuit combinatoire est un circuit avec des sorties basées seulement sur les entrées,

## Q5

Qu'est-ce qu'un circuit séquentiel ?
	Un circuit séquentiel contient aussi des entrées et des sorties, mais la valeur des sorties **dépend de la valeur actuelle et passée des entrées**


## Q6

Qu'est-ce qu'une loi composée ?
	Une loi composée est une loi qui combine plusieurs opérations logique pour atteindre un résultat
	I.E : `NOR`, `NAND`, `XNOR`

## Q7

Quel est le type utilisé en C pour représenter les valeurs true et false ? Doit-on inclure un
fichier d’en tête en C ?
	`bool`, et nous avons besoin d'inclure la librairie `<stdbool>` pour la représentation.


### Table de vérité des portes élémentaires

## Q8

La loi `NON` retourne l'inverse de l'entité `A`. Établissez la table de vérité de la loi `NON`, i.e A.

|  A  | NA  |
| :-: | :-: |
|  1  |  0  |
|  0  |  1  |

## Q9

La loi OU retourne VRAI si une des deux entrées {A, B} est vrai ou les deux sont vraies.
Etablissez la table de vérité de la loi OU, i.e., A + B.

|  A  |  B  | A + B |
| :-: | :-: | :---: |
|  0  |  1  |   1   |
|  1  |  0  |   1   |
|  1  |  1  |   1   |
|  0  |  0  |   0   |

## Q10

La loi `ET` retourne `VRAI` si les deux entrées sont vraies. Établissez la table de vérité de la
loi ET, i.e., A · B.

|  A  |  B  | A · B |
| :-: | :-: | :---: |
|  0  |  1  |   0   |
|  1  |  0  |   0   |
|  1  |  1  |   1   |
|  0  |  0  |   0   |

## Q11

Établissez la table de vérité de NON ET, i.e., A · B, en se basant sur les définitions.

|  A  |  B  | A · B | N A · B |
| :-: | :-: | :---: | :-----: |
|  0  |  1  |   0   |    1    |
|  1  |  0  |   0   |    1    |
|  1  |  1  |   1   |    0    |
|  0  |  0  |   0   |    1    |

## Q12

Établissez la table de vérité de `NON OU`, i.e., `A + B` en se basant sur les définitions.

|  A  |  B  | A + B | N A + B |
| :-: | :-: | :---: | :-----: |
|  0  |  1  |   1   |    0    |
|  1  |  0  |   1   |    0    |
|  1  |  1  |   1   |    0    |
|  0  |  0  |   0   |    1    |

## Q13

La loi XOR (OU exclusif) retourne VRAI si et seulement une des deux entrées vaut 1.

-  Quelle opération catégorise `XOR` en binaire ?
	Un `OU` exclusif

-  Établir la table de vérité

|  A  |  B  | A ⊕  B |
| :-: | :-: | :----: |
|  0  |  1  |   1    |
|  1  |  0  |   1    |
|  1  |  1  |   0    |
|  0  |  0  |   0    |

## Q14-15 useless


## Q16

Simplifiez les expressions suivantes (avec ou sans tables de vérités)

1.  A' · B + A · B
	B · (A' + A) (A' + A donne tjrs 1)
	`B`

2.  A + A · B
	A · B

3. (A · B · C) + (A · B · C')
	A · B

## Q17

Réalisez la table de vérité d'un `XOR` à 3 entrées {A, B, C}

|  A  |  B  |  C  | A ⊕  B ⊕ C |
| :-: | :-: | :-: | :--------: |
|  0  |  0  |  1  |     1      |
|  0  |  1  |  0  |     1      |
|  1  |  0  |  0  |     1      |
|  1  |  1  |  0  |     0      |
|  1  |  1  |  1  |     1      |
|  0  |  1  |  1  |     0      |
|  0  |  0  |  0  |     0      |
|  1  |  0  |  1  |     0      |

## Q18

Calculez à l’aide de table de vérité A' · B + A · B', l’opérateur `ET` est prioritaire
-  Faites un lien avec la loi XOR
	Cette table correspond à la loi `XOR` sans utiliser de `XOR` (donc, c'est juste un `OU`exclusif)

|  A  | A'  |  B  | B'  | A' · B + A · B' |
| :-: | :-: | :-: | :-: | :-------------: |
|  0  |  1  |  0  |  1  |        0        |
|  0  |  1  |  1  |  0  |        1        |
|  1  |  0  |  0  |  1  |        1        |
|  1  |  0  |  1  |  0  |        0        |

## Q19-20 

Décrivez les deux opérations
	S est un additionneur. On peut voir cela avec les résultats de `A ⊕ B ⊕ R = S`

![[q19 boole algebre.png]]

1. S = `A ⊕ B ⊕ R`
2. Rs = `(A · B) + ((A ⊕ B) · R)`

|  A  |  B  |  R  | A ⊕ B ⊕ R = S | A · B | (A ⊕ B) · R | (A · B) + ((A ⊕ B) ·R) = Rs |
| :-: | :-: | :-: | :-----------: | :---: | :---------: | :-------------------------: |
|  0  |  0  |  0  |       0       |   0   |      0      |              0              |
|  1  |  1  |  1  |       1       |   1   |      0      |              1              |
|  1  |  0  |  0  |       1       |   0   |      0      |              0              |
|  1  |  1  |  0  |       0       |   1   |      0      |              1              |
|  0  |  0  |  1  |       1       |   0   |      1      |              1              |
|  0  |  1  |  0  |       1       |   0   |      0      |              0              |
|  0  |  1  |  1  |       0       |   0   |      1      |              1              |

## Q22

Réalisez la table de vérité de ce circuit séquentiel.

![[Q22 circuit sequentiel alg boole lab.png]]

|  R  | R'  |  S  | S'  | R' ·' (S' ·' (S' · R')) | Q = (Q' · S')' | Q' = Q · R' |
| :-: | :-: | :-: | :-: | :---------------------: | :------------: | :---------: |
|  0  |  1  |  1  |  0  |                         |                |             |
|  1  |  0  |  0  |  1  |                         |                |             |
|  1  |  0  |  1  |  0  |                         |                |             |
|  0  |  1  |  0  |  1  |                         |                |             |
