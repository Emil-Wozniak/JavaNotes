-	Dodać zależność
		org.springframework.boot
		spring-boot-starter-test

- 	Adnotacja przed klasa testującą Foo:

```java
//zapewnia TestContext framework
@RunWith(SpringJUnit4ClassRunner.class)
//zapewnia kontekst springa dla testów integracyjnych klasy Foo
@SpringBootTest(classes = Foo.class)
//@IntegrationTest i @WebAppConfiguiration
@WebIntegrationTest
class FooIT {
}
```
	

-	Autowireujemy kontekst:

`@Autowired
private WebApplicationContext context;
`

-	Tworzymy obiekt MockMVC

`private MockMvc mockMvc;`

-	Tworzymy metodę setUp:

```java
class FooIT {
    public void setUp() {
     //trzeba postawić kontekst springa
	this.mockMvc = MockMvcBuilders.webAppContextSetup(context).build();
    }
}
```
		