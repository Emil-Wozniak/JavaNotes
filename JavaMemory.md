## STACK
* Stack i Heap
* Każdy thread ma swój stack
* Po wyjściu z danego codeblocku ze stacka usuwane są elementy pamięci, które ten codeblock wykorzystywał

## HEAP
* W heapie zawiera się wszystko co nie jest w stackach
* *Wszystkie* obiekty znajdują się w heapie, proste zmienne na stackach 

## OGÓLNE
* Proste obiekty (`int`, `double`, ... itd) podawane w metodzie zawsze będą *kopią* tego co się podaje np.
```java
class Foo { 

    static void foo(int bar){
  		bar = bar * 100;
  	}

    public static void main(String[] args) {

  	int localInt = 5; 	// 	localInt jest równe 5
  	foo(localInt);		// 	localInt cały czas równe 5 bo na stacku tworzona
  				//	jest jej kopia i dopiero ta kopia jest podawana do metody
    }
}
```
* Oznacza to że Java jest "pass by value" w przeciwieństiwie do "pass by reference".
Do metody przekazywana jest kopia wartości argumentu, a nie referencja do jego miejsca w pamięci

* Jeżeli przekazujemy obiekt to do metody kopiowany jest tylko pointer (referencja)	do tego obiektu, nie sam obiekt. 

## ESCAPING REFERNECES

* Błąd przy enkapsulacji danych 
    * Przekazywanie np. getterem pointera np. do całej oryginalej kolekcji
    * Lub do obiektu którego bezpośrednia modyfikacja nie może być dopuszczalna

* Rozwiązania:
	*	Przy kolekcjach - zwracać Collections.unmodifiable() wersje kolekcji
	*	Przy obiektach - można zrobić myk i stworzyć interfejst opisujący dany obiekt,
		ale posiadający jedynie metody do odczytu danych, nie zapisu i to go zwracać
		w getterze.
