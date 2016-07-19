# Tarefa

    GET api/v1/tasks/:id

## Descrição
Retorna uma tarefa especifica através do `id` de cadastro.

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros

  - **id** - código identificador do cadastro

***

## Formato de retorno

  Veja [formato completo](v1/full_format.md#tarefas)

***

## Exemplo

  **Requisição (Auth: JWT)**

      GET https://web.monde.com.br/api/v1/tasks/{C73D41F9-EA1E-4A69-8A05-278B15AFC233}

  **Resposta**
  ``` json
  {
    "task": {
      "id" : "{C73D41F9-EA1E-4A69-8A05-278B15AFC233}",
      "title": "Verificar Notificação",
      "assignee_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
      "due": "2016-06-30 19:27:08.644424",
      "done": false,
      "completed_at": "",
      "registered_at": "2016-07-01 19:27:08.651402",
      "category": "Geral",
      "history_tasks_ids": [1,2]
    }
  }
  ```

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
