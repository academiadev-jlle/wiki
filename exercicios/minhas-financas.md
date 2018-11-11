# Minhas finanças

### Requisitos

* Java 8+
* Utilizar Maven ou Gradle
* Seguir os padrões REST
* Banco de dados H2
* Descrever as instruções para rodar o projeto no README.md
* Utilizar Git
* Utilizar **Springboot** versão 2.1.0

### Avaliação

* Clean Code
* Implementação da especificação
* README.md bem escrito
* Commits bem escritos

**Importante, nessa ordem:**

* Criar testes automatizados \(teste unitário e teste de integração\)
* Fazer uso de bibliotecas auxiliares
* CircleCI ou TravisCI
* Documentar a API com Swagger

### Especificação

Criar uma **API** Rest que ira gerenciar as finanças dos seus usuários. A **API** deve conter **endpoints** para:

* Criar um usuário
* Visualizar todos os usuários
* Ver detalhes de um usuário
* Criar um lançamento financeiro
* Buscar todos os lançamentos de um determinado usuário
* Buscar um determinado lançamento pelo usuário e pelo id
* Criar entidades para um usuário
* Visualizar entidades de um usuário
* Criar contas para um usuário
* Visualizar todas as contas de um usuário
* Visualizar uma determinada conta de um usuário
* Visualizar todos os lançamento de uma determinada conta de um determinado usuário
* Baixar uma determinada conta de um determinado usuário
* Estornar uma determina conta de um determinado usuário

### Endpoints

#### Usuários

{% api-method method="post" host="http://localhost:8080" path="/financas/usuario" %}
{% api-method-summary %}
Criar usuário
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="" type="object" required=false %}
  
`{   
  "nome": "Exemplo",  
  "email": "exemplo@exemplo.com",  
  "status": "ATIVO"  
}`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "id": "1",
    "nome": "Usuário exemplo",
    "email": "exemplo@exemplo.com",
    "status": "ATIVO",
    "created_at": "2018-11-01 11:59"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "status": 400,
    "message": "Não foi possível processar esta operação"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:8080" path="/financas/usuario" %}
{% api-method-summary %}
Buscar todos os usuários
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
[
    {
        "id": "1",
        "nome": "Usuário exemplo",
        "email": "exemplo@exemplo.com",
        "status": "ATIVO",
        "created_at": "2018-11-01 11:59"
    },
    {
        "id": "2",
        "nome": "Usuário 02",
        "email": "usu_92@exemplo.com",
        "status": "ATIVO",
        "created_at": "2018-11-01 11:59"
    }
]

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:8080" path="/financas/usuario/:id" %}
{% api-method-summary %}
Buscar usuário por id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "id": "1",
    "nome": "Usuário exemplo",
    "email": "exemplo@exemplo.com",
    saldo: {
        total: 15365.00
        receber: 3200.00
        pagar: 4000.00
    },
    "status": "ATIVO"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "status": 404,
    "message": "Usuário não encontrado"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Lançamento Financeiro

Um lançamento financeiro pode ser:

* A Pagar
* A Receber

{% api-method method="post" host="http://localhost:8080" path="/financas/usuario/:id/lancamento" %}
{% api-method-summary %}
Criar um lançamento financeiro
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="" type="object" required=false %}
  
`{  
   "descricao": "Lanchonete",  
   "observacao": "Esqueci o cartão",  
   "valor": 16.50,  
   "tipo": "RECEBER"  
}`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
   "usuario_id": 1,
   "id": 1,
   "descricao": "Lanchonete",
   "observacao": "Esqueci o cartão",
   "valor": 16.50,
   "tipo": "RECEBER",
   "baixa": null,
   "status": "ABERTO",
   "created_at": '2018-11-01 11:59'
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:8080" path="/financas/usuario/:id/lancamento" %}
{% api-method-summary %}
Buscar todos os lançamentos de um usuário
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:8080" path="/financas/usuario/:id/lancamento/:id" %}
{% api-method-summary %}
Buscar um lançamento por id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Entidade

Uma entidade pode ser do tipo:

* Cliente
* Fornecedor

{% api-method method="post" host="http://localhost:8080" path="/financas/usuario/:id/entidade" %}
{% api-method-summary %}
Criar uma entidade
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="object" required=false %}
`{  
   "nome": "Advocacia S.A",  
   "tipo": "FORNECEDOR"  
}`
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "id": 1,
    "nome": "Advocacia S.A",
    "usuario_id": 1,
    "status": "ATIVO",
    "tipo": "FORNECEDOR",
    "created_at": "2018-11-07 12:05"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:8080" path="/financas/usuario/:id/entidade" %}
{% api-method-summary %}
Buscar todas as entidades de um usuário
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:8080" path="/financas/usuario/:id/entidade:id" %}
{% api-method-summary %}
Buscar entidade por id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Conta

{% api-method method="post" host="http://localhost:8080" path="/financas/usuario/:id/conta" %}
{% api-method-summary %}
Criar uma conta
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="" type="string" required=false %}
{  
   "nome": "Banco do Brasil"  
}
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "id": 1,
    "saldo": 0.00,
    "status": "ATIVO",
    "created_at": "2018-11-01 11:50"
}

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost::8080" path="/financas/usuario/:id/conta/:id/lancamentos" %}
{% api-method-summary %}
Buscar todos os lançamento de uma conta
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:8080" path="/financas/usuario/:id/conta" %}
{% api-method-summary %}
Buscar todas as contas de um usuário
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://localhost:8080" path="/financas/usuario/:id/conta/:id" %}
{% api-method-summary %}
Buscar conta por id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="http://localhost:8080" path="/financas/usuario/:id/conta/:idconta/:idlancamento?do=baixar" %}
{% api-method-summary %}
Baixar um lançamento
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="do" type="string" required=false %}
Baixar
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "status": 200,
    "message: ("Lançamento {} com sucesso", pago, baixado)
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="http://localhost:8080" path="/financas/usuario/:id/conta/:idconta/:idlancamento?do=estornar" %}
{% api-method-summary %}
Estornar um lançamento
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "status": 200,
    "message: ("Lançamento {} com sucesso", pago, baixado)
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

