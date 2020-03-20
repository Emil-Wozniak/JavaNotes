## Integration Testing of Spring Data JPA Repositories

1. Testy jednostkowe

-	Operują na pustych danych, sprawdzają tylko
	poprawność wyołania metod???

-	adnotacja `@WebMvcTest` nad klasą testu
```java
@Autowired
MockMvc mockMvc;
// dzięki temu możemu budować mocki elementów mvc
```

-	Adnotacją `@MockBean` oznaczamy beany których będziemy potrzebować,
	np. repozytoria lub serwisy
```java
mock.perform(
	MockMvcRequestBuilder.get("/all/")
	//w nawiasach nazwa metody mvc którą chcemy testować
	.accept(MediaType.APPLICATION_JSON)
    .andReturn();
```
