## Spring Boot

* Aby dodać **Spring Boot** do projektu musimy dodać moduł **Spring Boot** jako parent naszego np wielomodułowego projektu

* **Spring Boot** initializer tworzy nowy jednomodłowy projekt **Spring Boot**

* Konfiguacja loggera w **Spring Boot** odbywa się za pomocą logback-spring.xml. Dodajemy:
```xml
<include resource="org/springframework/boot/logging/logback.base.xml"/>
```
i potem określamy loggery, np:
```xml
<cofiguration>
    <logger name="com.arek" level="DEBUG"/>
    <logger name="org.springframework" level="INFO"/>
</cofiguration>
```
* Usuwamy z naszego głównego pom.xml nasze parameters i dependecy bo to będzie w generowane przez SpringBoogIinit

* W głównym, konfigurującym pom.xml dodajemy **Spring Boot** jako parent przed tagami <module></module>
```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>${versja}</version>
</parent>
```
* W pom-ach innych modułów usuwamy wszystkie depndency, dodajemy:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter</artifactId>
</dependency>
```
* W pomie modułu zawierającego Main.java trzeba określić plugin do budowania .jar:
```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```
* Jeżeli do istniejącego projektu chcemy dodatkowo dołożyć SpringWeb, to w pom.xml:
```xml
<dependencies>
	<dependency>
		<groupId>nazwa.paczki</groupId>
		<artifactId>core</artifactId>
		<version>${project.version}</version>
	</dependency>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
	</dependency>
</dependencies>

```
oraz
```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

*  **Spring Boot** Dev Tools - pozwalają np szybko restartować aplikację po zmianie kodu:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
</dependency>
```
```
<scope>runtime</scope> zapewnia że te narzędzie będą dostępne podczas runtime.
nie będą dostępne w releasie.
```
* Jak mamy DevTools to wtedy dajemy Build Project (ctrl+f9) żeby przebudować projekto
Jeżeli zrobimy zmiany w klasach to zrestaruje to aplikację, jak w templatkach
to tylko odświeży
