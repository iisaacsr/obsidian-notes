
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
	-  (9AB7) = ``
	-  (10E4FA04)
	-  (3F)

## Q11 

-  Réalisez la fonction transformant un nombre entier en héxadécimal

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

## Q15

