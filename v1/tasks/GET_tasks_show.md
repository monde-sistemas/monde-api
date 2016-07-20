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
      "number": 1,
      "title": "Verificar Notificação",
      "assignee_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
      "person_id": "{R22Q02F9-FH1E-4A69-1P12-278B15AFC634}",
      "due": "2016-06-30 19:27:08.644424",
      "done": false,
      "completed_at": "",
      "registered_at": "2016-07-01 19:27:08.651402",
      "category": "Geral",
      "task_historics": [{
        "id": "{F45D41F9-EA1E-4A69-8A05-278B15AFC456}",
        "task_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC233}",
        "date_time": "2016-06-30 19:27:08.844424",
        "person_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
        "text": "First comment",
        "historic": "'Pessoa' alterado de 'John' para 'Steve'"
      }]
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
