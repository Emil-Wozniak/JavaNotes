1. ZALEŻNOŚCI

* Narzędzia do testowania spring boota: `spring-boot-starter-test`
	
2. PISANIE TESTÓW
* Aby używać adnotacji Mockito trzeba:
```java
class TestClassWithMockito {

    @Rule 
    public MockitoRule rule = MockitoJUnit.rule();
    /* LUB */
    //Wrzucić w setup @Before lub @BeforeEach:
    @BeforeEach
    void before(){
	MockitoAnnotations.initMocks(StockServiceTest.class);}
    } 	
```
3. MOCKOWANIE

* Przez to że mock nie ma w sobie logiki musimy mu hardcodować to co ma zwrócić:
```java
class TestClass {
    @Test    
    void testMock() {
	when(mockName.foo(args)).thenReturn(oczekiwanyReturn);
    }
}
````
np. hardkodujemy co repozytorium ma zwrócić przy danych argumentach.
Najczęściej chcemy żeby zwróciło jakiegoś stuba.

-	Mockujemy np. metody z repozytoriów, które będą wywoływane
	przez serwisy

-	Z mocków najczęsciej dummy obiekty - stuby.
	Są to, znowu, hardcodowane obiekty które będziemy wrzucać
	do mocków.

-	Właściwą klasę, której metody testujemy, musimy zainicjalizować,
 żeby mieć dostęp do logiki w niej zawartej, 
 inaczej nie moglibyśmy wywołać metody do testowania.

Mockito pozwala nam zainicjalizowac ją adnotacją: `@InjectMocks`

Dzięki tej adnotacji, tworzymy nowy obiekt z danej klasy i jeżeli
potrzebuje on jakichś zależności i mamy je zmockowane w teście
to zostaną one wstrzyknięte.

-	Wywołujemy testowaną metodę i porównujemy jej rezultat z oczekiwaniami.
