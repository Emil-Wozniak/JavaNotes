1.	Czym jest **Spring**
	Spring jest lekkim frameworkiem służącym głównie do ułatwienia tworzenia aplikacji Java EE,
	ale jego składowe mogą być używane przy tworzeniu każdej aplikacji Java. IoC i DI są bardzo
	przydatne przy tworzeniu każdego programu.

2.	Zalety **Spring**
* Lekki
* Inversion of Control: przerzucenie odpowiedzialności za życie obiektów na kontener springowy
* Aspect Oriented Programming: Spring wspiera użycie AOP w celu dodatkowego oddzielenia logiki biznesowej od serwisów
* IoC Container: kontener odwrócenia kontroli - element Sprina, który ma za zadanie zarządzanie życiem obiektów - tworzenie ich i niszczenie wedle potrzeby
* Framework MVC: wysoce konfigurowywalny framework do tworzenia RESTfulowych serwisów webowych, obsługujący jsony i xml
* Transaction managemen: Spring pozwala zredukować ilość boilerplate kodu do obsługi JDBC. 
* Exception handling: Spring zapewnia wygodne API do obsługi wyjątków
	
3.	Przykładowe składowe elementy **Springa**:
* Core: element zapewniający podstawowe funkcjonalności Springa takie jak IoC oraz DI.
* JDBC: moduł udostępniający warstwę abstrakcji do obsługi JDBC i eliminuje potrzebę pisania kodu do obsługi róznych baz danych
* Integracja ORM: moduły umożliwiające obsługę object-relational mappinu przy użyciu, np. JPA lub Hibernate
* Web: moduł służący do obsługi aplikacji webowych. 
* MVC Framewoerk: framework do tworzenia aplikacji bazujących na wzorcu MVC
* AOP: moduł do obsługi Aspect Oriented Programing (AspectJ)

4.	Czym jest DI

	Dependency Injection jest aspektem IoC i jest to koncept w programowniu, polegający 
	na nie tworzeniu obiektów ręcznie, a zamiast tego określaniu jedynie jak mają być stworzone.

5. Czym jest **Spring Boot**

Jest rozszerzeniem **Frameworku Spring** które eliminuje boilerplate configurations aplikacji 

6. Jakie są zalety **Spring Boot**

![Spring Boot](https://twitter.com/springboot/photo)
* Rozważane zależności „startowe” w celu uproszczenia kompilacji i konfiguracji aplikacji
* Wbudowany serwer, aby uniknąć złożoności wdrażania aplikacji 
* Metryki, kontrola Helth i konfiguracja zewnętrzna
* Automatyczna konfiguracja dla funkcji *Spring* - w miarę możliwości

7. Czym jest [REST](assets/additional/REST.md)

* To aktonim od **RE**presentational **S**tate **T**ransfer
* REST to nie to samo co HTTP
* Styl [architektury oprogramowania](https://resources.sei.cmu.edu/library/asset-view.cfm?assetID=513817) zapewniający standardy między systemami komputerowymi w sieci, ułatwiający komunikację między systemami
* Systemy zgodne z REST, często nazywane systemami RESTful, charakteryzują się tym, że są bezstanowe i oddzielają problemy klienta i serwera.

