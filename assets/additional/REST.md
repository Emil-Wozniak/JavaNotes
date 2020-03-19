
### BEZSTANOWOŚĆ
* Systemy zgodne z paradygmatem REST są bezstanowe, co oznacza, że ​​serwer nie musi nic wiedzieć o tym, w jakim stanie jest klient, i odwrotnie. 
* W ten sposób zarówno serwer, jak i klient mogą zrozumieć każdą otrzymaną wiadomość, nawet nie widząc poprzednich wiadomości.
 * To ograniczenie bezstanowości jest egzekwowane poprzez wykorzystanie zasobów, a nie poleceń. 
 * Zasoby to rzeczowniki w sieci - opisują każdy obiekt, dokument lub rzecz, która może być potrzebna do przechowywania lub wysyłania do innych usług. 
 * Ponieważ systemy REST oddziałują poprzez standardowe operacje na zasobach, nie polegają na implementacji interfejsów. Ograniczenia te pomagają aplikacjom RESTful osiągnąć niezawodność, szybką wydajność i skalowalność, jako komponenty, którymi można zarządzać, aktualizować i ponownie wykorzystywać bez wpływu na cały system, nawet podczas jego działania.

### KOMUNIKACJA MIĘDZY KLIENTEM A SERWEREM

* W architekturze REST klienci wysyłają żądania pobrania lub modyfikacji zasobów, a serwery wysyłają odpowiedzi na te żądania.

### WYKONYWANIE ŻĄDAN

Usługa REST wymaga, aby klient wysłał żądanie do serwera w celu pobrania lub zmodyfikowania danych na serwerze. Żądanie składa się zasadniczo z:

* czasownik HTTP, który określa rodzaj operacji do wykonania
* nagłówek, który pozwala klientowi przekazać informacje o żądaniu 
* ścieżka do zasobu 
* opcjonalna treść wiadomości zawierająca dane

### CZASOWNIKI HTTP

Istnieją 4 podstawowe czasowniki HTTP, których używamy w żądaniach interakcji z zasobami w systemie REST:

* GET - pobierz określony zasób (według identyfikatora) lub zbiór zasobów 
* POST - utwórz nowy zasób 
* PUT - zaktualizuj określony zasób (według identyfikatora) 
* DELETE - usuń określony zasób według identyfikatora

[Więcej nt. CRUD](https://www.codecademy.com/articles/what-is-crud)

### NAGŁÓWKI I PARAMETRY AKCEPTACJI

W nagłówku żądania klient wysyła typ zawartości, którą może otrzymać z serwera. 
Nazywa się to *Accept field* i zapewnia, że serwer nie wysyła danych, których klient nie może zrozumieć ani przetworzyć. 
Opcje dla typów zawartości to Typy MIME (od Multipurpose Internet Mail Extensions, o których więcej można przeczytać w [Dokumentach internetowych MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types).

Typy MIME, używane do określania typów zawartości w polu Akceptuj, składają się z typu i podtypu. Są one oddzielone ukośnikiem (/).

Na przykład plik tekstowy zawierający HTML zostałby określony jako typ `text/html`. 
Jeśli ten plik tekstowy zawiera zamiast tego CSS, byłby określony jako `text/css`. 
Ogólny plik tekstowy byłby oznaczony jako `text/plain`. 
Ta domyślna wartość, `text/plain`, nie jest jednak najważniejsza. 
Jeśli klient oczekuje `text/css` i otrzymuje `text/plain`, nie będzie w stanie rozpoznać treści.

Na przykład klient uzyskujący dostęp do zasobu o identyfikatorze 23 w zasobie artykułów na serwerze może wysłać żądanie GET w następujący sposób:

```
GET /articles/23
Accept: text/html, application/xhtml
```

### ŚCIEŻKI

Żądania muszą zawierać ścieżkę do zasobu, na którym należy wykonać operację.
W interfejsach API RESTful ścieżki powinny być zaprojektowane tak, aby pomóc klientowi wiedzieć, co się dzieje.

Konwencjonalnie pierwszą częścią ścieżki powinna być liczba mnoga zasobu. 
Dzięki temu zagnieżdżone ścieżki są łatwe do odczytania i łatwe do zrozumienia.

Ścieżka taka jak `fashionboutique.com/customers/223/orders/12` jest jasna w tym, na co wskazuje, nawet jeśli nigdy wcześniej nie widziałeś tej konkretnej ścieżki, ponieważ jest ona hierarchiczna i opisowa.
Widzimy, że uzyskujemy dostęp do zamówienia o identyfikatorze 12 dla klienta o identyfikatorze 223.



[Żródło](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
