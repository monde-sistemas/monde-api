# Vendas Importadas

    GET api/v1/imported_sales

## Descrição
Retorna as vendas importadas.

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros

  - **date** - Filtra tarefas pelo data da venda:

  ```
    GET api/v1/imported_sales?date=2017-03-30
  ```

  - **integration_id** - Filtra pelo id da integração:

  ```
    GET api/v1/imported_sales?integration_id=67de30f7-4b84-4c34-845d-6f471c0e50a3
  ```

***

## Formato de retorno

  Veja [formato completo](../full_format.md#imported_sales)

***

## Exemplo

  **Requisição (Auth: JWT)**

    GET https://web.monde.com.br/api/v1/imported_sales

  **Resposta**
``` json
{
  "imported_sales": [
    {
      "id": "af5bd166-9861-4e41-b65d-1aa4e5bb1328",
      "integration_id": "7a41d0fa-d904-460b-85a9-2ff47a3e7cba",
      "date": "2017-03-03",
      "passenger": "Stig",
      "document": "1234455"
    }
  ]
}
```

***

## Erros
  Status code:
  - **401** - Não autenticado
  - **403** - Não autorizado
