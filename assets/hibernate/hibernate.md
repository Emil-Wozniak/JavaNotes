## Hibernate
1. Co to jest **JPA**? 

To standard typu ORM (Object-Relational Mapping).

2. co to jest ORM?

Oznacza mapowanie z modelu obiektowego (tu dostarczonego przez Java).
```java
@Entity
@Data
class Employee { 
 @Id
 private Long id;
 private String name;
 private int salary;
 }
```

 
3. Co to jest **Hibernate**?

To zbiór implementacji standardu JPA
