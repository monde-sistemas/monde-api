# Tarefas

    GET api/v1/tasks

## Descrição
Retorna as tarefas cadastradas.

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros

  - **filter** - Filtra tarefas pelo `título` informado:

  ```
    GET api/v1/tasks?filter=título-da-tarefa
  ```

  - **situation** - Filtra pela situação(`done`: `finalizada`, `open`: `não concluída`):

  ```
    GET api/v1/tasks?situation=done
  ```

  - **page** - navega entre a paginação:

  ```
    GET api/v1/tasks?page=1
  ```

  - **per_page** - Sobrescreve o valor padrão(50) de registros por página:

  ```
    GET api/v1/tasks?page=1&per_page=5
  ```

***

## Formato de retorno

  Veja [formato completo](../full_format.md#tarefas)

***

## Exemplo
  **Requisição (Auth: JWT)**

    GET https://web.monde.com.br/api/v1/tasks

  **Resposta**
``` json
{
  "tasks": [{
    "id" : "{C73D41F9-EA1E-4A69-8A05-278B15AFC233}",
    "number": 1,
    "title": "Verificar Notificação",
    "assignee_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
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
  }, {
    "id" : "{C73D41F9-EA1E-4A77-8A05-278B15AFC233}",
    "title": "Verificar E-mails",
    "assignee_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
    "due": "2016-06-30 19:27:08.644424",
    "done":  true,
    "completed_at": "2016-07-10 10:07:08.213221",
    "registered_at": "2016-07-01 19:27:08.651402",
    "category": "Geral",
    "task_historics": null
  }],
  "meta": {
    "pagination": {
      "per_page": 50,
      "total_pages": 1,
      "total_objects": 2
    }
  }
}
```

***

## Erros
  Status code:
  - **401** - Não autenticado

