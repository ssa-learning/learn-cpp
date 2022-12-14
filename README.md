# Notes

J'ajouterai des trucs au fur et a mesure de mon apprentissage.

Je vous conseille aussi d'installer Obsidian pour lire ce MD.

## Bases

### Variables

```cpp
#include <iostream>

int main(void)
{
	// creer une variable
	int taille_cm = 180;
	float taille_penis_cm = 14.5f;

	// il est important de tjrs intialiser les variables
	// (les mettre a 0 si elle ont pas de valeur)
	// sinon bufferoverflow ou segmentation fault :(
	
	// exemples:
	
	// a faire
	int taille = 0;
	
	// a ne pas faire
	int taille;

	return 0;
}
```

### Types

| Types | Description | 
|:--------------|:-------------:|
| int | Un entier, un nombre. Ex: `15`
| float | Un nombre "flottant", a firgule. Ex: `15.5f`
| char | Un charactere ASCII. Ex: `65` ou `"A"`
| bool | Un boleen. Ex: `true` ou `false`
| double | Un nombre a virgule mais pas pareil qu'un float. Ex `15.5`

### Fonctions

```cpp
#include <iostream>

// arguments dans les ()
int addition(int a, int b)
{
	return a + b;
}

// surcharge de fonction (meme fonction mais type different)
float addition(float a, float b)
{
	return a + b;
}

```

### Tableaux

```cpp
#include <iostream>

int main(void)
{
	// creer un tableau
	int tablo[10] = {0};
	
	// assigner une valeur a un index
	tablo[0] = 30;

	// creer un tableau avec des valeurs qu'on choisis
	int tablo[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
	
	return 0;
}
```

### Pointeurs

```cpp
#include <iostream>

int main(void)
{
	// initialiser un poiteur (* = pointeur)
	// nullptr c'est un pointeur nul, qui n'a pas d'adresse,
	int* p_int = nullptr;

	// creer un poiteur sur une variable existante (& = addressof)
	char  a = 65;
	char* p_a = &a;

	// afficher l'adresse du pointeur
	std::cout << p_a << std::endl;
	// afficher la valeur a partir du pointeur (*p_a = valeur du pointeur)
	std::cout << *p_a << std::enfl;

	return 0;
}
```

Maintenant, a quoi servent les pointeurs:

```cpp
#include <iostream>

void foo(int a)
{
	a = 50;
}

int main(void)
{
	int a = 0;
	foo(a);

	std::cout << a << std::endl;
	return 0;
}
```

Ici, on veux changer la valeur de la variable `a` dans la fonction `main()` grace a la fonction `foo()`, sauf que si on execute ce code, lors de l'affichage de la variable `a`, celle-ci sera toujours egale a 0, tout simplement car la fonction `foo()` cree une "copie" de `a`. Pour remedier a cela, on va utiliser un pointeur sur la variable `a` de la fonction `main()`

```cpp
#include <iostream>

void foo(int* a)
{
	*a = 50;
}

int main(void)
{
	int a = 0;
	foo(&a);

	std::cout << a << std::endl;
	return 0;
}
```

Ce que ce code va faire, c'est tout simplement changer la valeur de `a` a l'adresse dans la memoire RAM ou elle se trouve. Dans le `main()` on donne l'adresse de `a` a `foo()` qui prend en argument cette fois ci pointeur et qui va, dans la fonction, changer la valeur de ce pointeur.

Attention, il ne faut pas modifier la valeur d'un pointeur nul (nullptr) ou d'un pointeur qui pointe a une adresse invalide car, sinon, on va "corrompre la memoire". Ce qui est TRES dangereux.
