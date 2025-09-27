
## Q1

 -  Qu'est-ce que le bit de poids faible et le bit de poids fort ?
	[[Nombres binaires, Hexadécimaux#Nombres binaires (base binaire)|Référence]]
	-  Le bit de poids fort correspond au bit coresspondant à la plus haute puissance du nombre binaire
	-  Le bit de poids faible correspond au bit correspondant à la plus basse puissance du nombre binaire

## Q2

-  Indiquez la valeur du bit de poids faible pour un nombre pair, et pour un nombre impair.
	-  Le bit de poids faible pour un nombre pair serait `0` (un nombre pair binaire finit toujours par `2^n = 0`)
	-  Le bit de poids faible pour un nombre impair serait `1` (un nombre impair binaire finit toujours par `2^n = 1`)

## Q3

-  Donnez la représentation binaire de l’entier naturel 54 
	`0011 0100`
	 -  Combien de bits sont nécessaires ?
		 6 bits
	-  Quelle sera la valeur du bit de poids faible ?
		  0, parce qu'il est pair

## Q4

-  Quelle est la représentation binaire de l’entier naturel 821?
	`11 0011 0101`

## Q5

-  Quelle est la valeur décimale de la représentation binaire suivante : (1011 0011)
	`179`

## Q6

-  Écrivez une fonction C de2bi donnant la représentation binaire d’un nombre entier positif,
   ainsi que la fonction bi2de donnant l’entier positif d’une représentation binaire.
   
[[Nombres binaires, Hexadécimaux#Méthode pour passer d'une base à une autre|Référence]] (cette fonction en code)
```C
int main(int argc, char** argv) {
    int valeur = atoi(argv[1]); // string vers integer
    // init tableau
    int tab[SIZETAB]; // 32
    for(int i = 0; i < SIZETAB; i++)
        tab[i] = 0;
        
    de2bi(valeur, tab);
    
    for(int i = 0; i < SIZETAB; i++)
        printf("%d", tab[i]);
    return 1;
}

void de2bi(unsigned int nb, int* binary) {
    int current_bit = 32;
    while (nb != 0) {
        binary[--current_bit - 1] = nb % 2;  // le bit;
        nb = nb / 2;
    }
}
```

## Q7

- À quelle base correspond la représentation hexadécimale ?
	Base 16

## Q8

-  Indiquez tous les chiffres sur cette base, combien de bits sont nécessaires pour représenter
   un chiffre en hexadécimal
   [[Nombres binaires, Hexadécimaux#Nombre hexadécimaux (base hexadécimale)|Référence]]
	`0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F`
	
	4 bits sont nécessaires pour représenter un chiffre en hexadécimal

## Q9

-  Indiquez combien de chiffres hexadécimales sont nécessaire pour représenter un octet.
	Deux chiffres sont nécessaires (4 bits chaque)

## Q10

-  Indiquez la représentation binaire des nombres hexadécimale suivants
	-  (9AB7) = `1001 1010 1011 0111`
	-  (10E4FA04) = `0001 0000 1110 0100 1111 1010 0000 0100`
	-  (3F) = `0011 1111`

## Q11 

-  Réalisez la fonction transformant un nombre entier en héxadécimal

```c
int main(int argc, char** argv) {
    int valeur = (int)strtol(argv[1], NULL, 0); // string vers integer
    // init tableau
    int tab[SIZETAB]; // 32

    for(int i = 0; i < SIZETAB; i++)
        tab[i] = 0;
        
    hex2bi(valeur, tab);

    for(int i = 0; i < SIZETAB; i++)
        printf("%d", tab[i]);
    return 1;
}

void hex2bi(unsigned int nb, int* binary) {
    int current_bit = 32;
    while (nb != 0) {
        binary[--current_bit - 1] = nb % 2; // le bit;
        nb = nb / 2;
    }
}
```

## Q12

-  Quelle est la différence entre une représentation signée et une représentation non signée ? #todo
	La représentation signée a toujours un bit de signe précédant le bit de poids fort, tandis que la représentation non signée n'a pas ce bit de signe. 
	
	La différence est donc qu'un nombre binaire signé de 8 bit aurait seulement 7 bits pour développer le nombre, tandis qu'un nombre binaire non signé à 8 bit aurait les 8 buits pour développer le nombre

## Q13

-  Combien de bit est nécessaire pour représenter le signe ?
	Un bit

## Q14

-  Indiquez la valeur maximale possible pour un `char`, et un `unsigned char`.
	`unsigned char`= entre 0 et 255
	`char` = entre -127 et 127 (`0111 111`et `1111 1111`)

## Q15-16-17

-  Représentez l'entier -54 et -821 en signe-valeur absolue (Sign and Magnitude) (représenté en `short`)
	-54 = `11 0110`
	-  En short : `0000 0000 0011 0110`
	-  Sign & magnitude = `1000 0000 0011 0110`
	-  Complément de 1 = `1111 1111 1100 1001`
	-  Complément de 2 = `1111 1111 1100 1010`
	-821 = `0011 0011 0101`
	-  En short : `0000 0011 0011 0101`
	-  Sign & Magnitude = `1000 0011 0011 0101`
	-  Complément de 1 = `1111 1100 1100 1010`
	-  Complément de 2 = `1111 1100 1100 1011`

## Q18

-  Représentez l'entier -0 sur 4 bits avec les 3 méthodes
	-  Sign & Magnitude = `1000 0000 0000 0000`
	-  Complément à 1 = `1111 1111 1111 1111`
	-  Complément à 2 = `0000 0000 0000 0000`

## Q19

-  Indiquez l’entier relatif représenté, si la représentation est en Sign and Magnitude, complé-ment à 1 et complément à 2  pour la séquence suivante : `(9A)(hex)`
	-  9A en décimal = `1001 1010` (un nombré décimal = 4 bits)
	-  Complément à 1 = `0110 0101` = 101 = (-101)
	-  Complément à 2 = `0110 0110` = 102 = (-102) 
