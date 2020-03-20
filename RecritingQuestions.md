1.	Czy można przekazywać **Optional** w argumentach metody?

Nie powinno się. Używanie tak Optionali zaciemnia zapis metody, sprawia że działanie metody zależy od wartości optionala,
optional w porównaniu do nullowalnych argumentów jest bardziej kosztowny, **Optional** może reprezentować aż 
trzy różne stany: *null*, *non-null* ale isPresent = false, oraz *non-null* opakowujący właściwą wartość.

2.	Skoro nie to jak można obsłużyć zmienną która może być nullem?

Najbardziej eleganckim rozwiązaniem jest stworzenie overloadowanej metody, obsługującej wariant logiki z argumentem null.
```java
@AllArgConstructor
class Foo {

// never accept null value from API
@NonNull private final Bar bar; // This never should be Optional
@NonNull private final Baz baz;

// use method to remove null value
void isMyVarNUll(var myVar) {if (myVar != null) doSomething();}

// filter null value for list 
void isNullInList (List<Integer> list) {list.filter(Objects::nonNull);}

// wrap return value in Optional 
Optional<String> makingYouCheck(Foo foo) {/* stuff */}
void isThingScrewBecauseOfNull(Foo foo ){makingYouCheck(foo).orElseThrow(ScrewYouException::new);}

// return empty List instead of null 
List<String> findSomething() {
    if (someCondition) {return Collections.emptyList();}
    // stuff
    }
}
```

3. Jaka lista jeżeli chcę dodawać dane zawsze na początku?

Klasa `LinkedList` posiada w sobie metody `addFirst()` oraz `addLast()` 

4.	Co to jest `LinkedList`?

Podwójnie łączona lista danych - każdy jej node przechowuje informacje o swojej zawartości, jak i odnośniki do node przed i za nim.

5.	Co wprowadziła Java 8?

*  	Streamy
*  	Wyrażenia lambda
*  	Interfejsy funkcyjne
* 	Try-with-resources
* 	Optionale
* 	Typy generyczne

6.	Trzy interfejsy funkcyjne i opisać je

*  	`Function`: przyjmuje jeden argument i zwraca jeden argument
* 	`Customer`: przyjmuje jeden argument i nie zwraca nic
* 	`Predicate`: przyjmuje jeden argument i wywołuje na nim test logiczny

7.	Map vs flatMap w Streamach

* 	Map służy do mapowania wartości w streamie na inne wartości przy użyciu interfejsu funkcyjnego *Function*
* 	flatMap używamy w momencie kiedy musimy "spłaszczyć" rezultat działania, tzn: jeżeli mamy np. nested stream, 
kolekcję lub optional `Optional.of(Optional.of(foo))` lub `List<List<String>>` to używając flatMap możemy to spłaszczyć 
do `Optional.of(foo)` i `List<String>`

8.	Jak sprawić żeby obiekt był Immutable?

* 	Ustawić pola jako `private final`
* 	Gettery zwracające nie bezpośrednią referncję do obiektu, ale jego kopię (klon)
* 	Ustawić klase jako `final`
* 	Nie tworzyć setterów do pól
* 	Inicjalizacja pól z argumentów konstruktora powinna odbywać się przez deep copy tych arugmentów na pola

9. Jak przekazać do obiektu immutable przez konstruktor np. mapę?

Aby wypełnić immutable pole taką mapą należy jej zawartość skopiować do tego pola (deep copy)

10.	Jak działa `HashMap`?

* `HashMap` przy inicjalizacji tworzy serię pustych bucketów (domyślnie 16), 
z których każdy może mieć jeden lub więcej nodów połączonych jak `LinkedList`.

* Przy dodawaniu elementu `HashMap` oblicza `hashCode` klucza i potem używając
`index = hash & (n-1)`  gdzie `n` to ilość bucketów (klucz `null` wyląduje w bucket 0)
ustala index bucketa, do którego wrzuci dany obiekt.

    Każdy node będzie zawierał: 
    *  key
    *  hashcode
    *  value
    *  next /* referencja do następnego node */

11.	`HashMap` zadanie

a) Czy można dodać do `HashMap` dwa klucze o tym samym hashu?

b) Czy możemy zmienić `hashcode` już istniejącego w mapie obiektu?

c) Co się wtedy stanie?

ad a) Można dodać, trafią wtedy do tego samego bucketa i połączą się w `LinkedList`.

ab b,c)	Możemy, ale nie powinno się tego robić, bo psuje to mapę i obiekt o zmienionym
hashcode nie będzie już dostępny. Najlepiej jeżeli obiekty używane jako klucze będą immutable.

12.	Jak definiujemy beany w Springu? Jaki jest ich domyślny scope?

**Beany** to obiekty stanowiące kręgosłup aplikacji i będący zarządzany przez Kontener IoC Springa

**Bean** jest inicjalizowany, gromadzony i zarządzany przez Spring IoC Container

**Bean** domyślny zakres Beanów to *singleton* 

Bean można zadeklarować na 2 sposoby:
* w konfiguracji XML
```xml
<beans>
    <bean name="transferService" class="com.acme.TransferServiceImpl"/>
</beans>
```
* za pomocą **Wstrzykiwania zależności** poprzez adnotację `@Bean` , `@Component`, `@Configuration` i `@Service`
```java
@Configuration
public class AppConfig {
    @Bean
    public TransferService transferService() {
        return new TransferServiceImpl();
    }
}
```

13.	Dlaczego powstał **Spring Boot**?


14.	Różnica między Post a Put, czy Putem możemy umiesczać nowe dane na serwerze?
15.	Annotacje @Controller, @Repository, @Service - co oznaczają pod maską?
16.	Obsługa wyjątków w Springu
17.	Optimistic vs Pesimistic locking w Hibernate
18.	Kiedy Hibernate rzuca LazyInitializationException
19.	Kiedy używać indeksowania baz danych
20.	Wady indeksowania
21.	Jakie kody komunkatów HTTP znasz
22. Czym różnią się kody 400 od kodów 500?
23. Co oznacza S w skrócie SOLID
24.	Jak zbadać czy klasa narusza S
25.	Czym się różni Spy od Mock
26.	Jeżeli metoda nic nie zwraca to jak ją obsłużyć w testach?
27.	Jak sprawdzić czy metoda która nic nie zwraca została wywołana w teście?
28.	Dlaczego JIT Compiler JVM nazywa się HotSpot

Bo cały czas analizuje kod programu szukając `hot spotów` czyli fragmentów kodu
wykonywanych często lub powtarzających się i te elementy `just-in-time` kompiluje
do kodu maszynowego

29.	Aspect Oriented Programming w Springu

30.	Czy w Javie występuje polimortizm pól 

Nie, pola są chowane, metody overridowane
