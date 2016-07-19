# Tarefa

    DELETE api/v1/tasks/:id

## Descrição
Excluí uma tarefa através do `id` de cadastro.

***

## Autenticação
**[JWT](v1/authentication/POST_auth_token.md)**

***

## Parâmetros

  - **id** - código identificador do cadastro

***

## Formato de retorno

  Não possui.

#### Status de retorno

    204 - No Content

***

## Exemplo

**Requisição (Auth: JWT)**

        DELETE https://web.monde.com.br/api/v1/tasks/{C73D41F9-EA1E-4A69-8A05-278B15AFC233}

***

## Erros
  Os erros possuem um status code especifico, geralmente com alguma mensagem de erro no formato:
  ``` json
  {
    "errors": [
      "Registro não encontrado"
    ]
  }
  ```

  Status code:
  - **401** - Não autenticado
  - **404** - Registro não encontrado.
