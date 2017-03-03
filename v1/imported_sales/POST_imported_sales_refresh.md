# Atualizar/Importar vendas

    POST api/v1/imported_sales/refresh

## Descrição
Retorna as vendas importadas.

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros

``` json
  {
    "date": "2017-03-30",
    "integration_id": "7a41d0fa-d904-460b-85a9-2ff47a3e7cba"
  }
```

***

## Retorno

  Este endpoint sempre vai retornar um 303-Redirect. O primeiro redirect vai ser para o endpoint `async_process`, que por sua vez vai redirecionar para o endpoint `imported_sales` assim que a importação for finalizada.

***

## Exemplo

  **Requisição (Auth: JWT)**

    POST https://web.monde.com.br/api/v1/imported_sales/refresh

  **Resposta**
    REDIRECT GET https://web.monde.com.br/api/v1/async_process/3d3b1cc0-aea1-4c24-adb2-a2fe015554b3


***

## Erros
  Status code:
  - **401** - Não autenticado
  - **403** - Não autorizado
