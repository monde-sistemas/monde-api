# Tarefas

    GET api/v1/tasks

## Descrição
Retorna as tarefas cadastradas.

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros

  - **filter** - Filtra tarefas pelo valor informado:

  ```
    GET /api/v1/tasks?filter=valor-da-pesquisa
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
    "title": "Verificar Notificação",
    "assignee_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
    "due": "2016-06-30 19:27:08.644424",
    "done": false,
    "completed_at": "",
    "registered_at": "2016-07-01 19:27:08.651402",
    "category": "Geral",
    "history_tasks_ids": [1,2]
  }, {
    "id" : "{C73D41F9-EA1E-4A77-8A05-278B15AFC233}",
    "title": "Verificar E-mails",
    "assignee_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
    "due": "2016-06-30 19:27:08.644424",
    "done":  true,
    "completed_at": "2016-07-10 10:07:08.213221",
    "registered_at": "2016-07-01 19:27:08.651402",
    "category": "Geral",
    "history_tasks_ids": null
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

