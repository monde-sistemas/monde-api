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
    "integration_id": "7a41d0fa-d904-460b-85a9-2ff47a3e7cba",
    "document": "AI6WDX"
  }
```

***

## Retorno

  Este endpoint sempre vai retornar um 202-Accepted contendo no header location uma URL para consulta do status do processo. Essa URL irá apontar para o endpoint `async_process`, que por sua vez vai redirecionar para o endpoint `imported_sales` assim que a importação for finalizada.

***

## Exemplo

  **Requisição (Auth: JWT)**

    POST https://web.monde.com.br/api/v1/imported_sales/refresh

  **Resposta**
```
Status: 202 Accepted
Location: https://web.monde.com.br/api/v1/async_process/1a5c02ce-12d3-4f83-858b-64a53a816ad8
```


***

## Erros
  Status code:
  - **401** - Não autenticado
  - **403** - Não autorizado
