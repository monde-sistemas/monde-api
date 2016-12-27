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
    "due": "2016-06-30 19:27:08.644424",
    "visualized": false,
    "completed_at": "",
    "registered_at": "2016-07-01 19:27:08.651402",
    "category": "Geral",
    "assignee": {
      "id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
      "name": "Nome do responsável"
    },
    "person": {
      "id":"{R22Q02F9-FH1E-4A69-1P12-278B15AFC634}",
      "name": "Nome do cliente"
    },
    "author": {
      "id":"{R22Q02F9-FH1E-4A69-1P12-278B15AFC634}",
      "name": "Nome do criou a tarefa"
    },
    "task_historics": [{
      "id": "{39D51EEE-1E10-4124-93E9-1D1CEB948E83}",
      "date_time": "2016-06-27T10:44:58.328-02:00",
      "task_id": "{59B03700-9F30-4C12-BAAC-0C0913028FF6}",
      "person": {
        "id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
        "name": "Nome do criador do histórico"
      },
      "text": null,
      "historic": "'Pessoa' alterado de 'John' para 'Steve'"
    },{
      "id": "{4A7843BC-23B5-416F-B716-C0E58D0D6C80}",
      "date_time": "2016-06-27T10:44:58.328-02:00",
      "task_id": "{59B03700-9F30-4C12-BAAC-0C0913028FF6}",
      "person": {
        "id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
        "name": "Nome do criador do histórico"
      },
      "text": "First comment",
      "historic": null
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
  - **403** - Não autorizado
  - **404** - Registro não encontrado.
