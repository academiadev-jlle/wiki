# Qual nome colocar?

Escrever testes unitários não é mais optativo no desenvolvimento de software. Escrever um bom teste faz com que tenhamos um sistema com bugs reduzidos drasticamente. Mas na hora de documentar, qual seria o melhor nome para o meu teste?

### BDD -   Behavior-Driven Design/Development

O BDD é uma técnica de teste onde basicamente escrevemos umas historinha com três frases.

_**Dado** uma condição  
**Quando** eu executo uma ação  
**Então** o resultado é esse_

Dessa forma fica fácil de qualquer pessoa mesmo fora do projeto conseguir entender o que queremos. Mas como aplicar ao teste?

```java
@Test
@Transactional
public void dadoBoletos_quandoNaoTenhoBoletosNaBase_entaoRetornaZeroBoletos() throws Exception {
	mvc.perform(get("/bankslips").contentType(MediaType.APPLICATION_JSON_UTF8_VALUE)).andExpect(status().isOk()).andExpect(jsonPath("$", hasSize(0)));
}
```

Desta forma se em algum momento este teste quebrar, fica fácil de entender o objetivo do teste para corrigí-lo.

