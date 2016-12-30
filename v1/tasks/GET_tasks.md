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

  - **assigned** - Filtra por como o usuário é vinculado a tarefa (`user_tasks`: `tarefas do usuário`,
  `author`: `criada pelo usuário`):

  ```
    GET api/v1/tasks?assigned=user_tasks
    GET api/v1/tasks?assigned=author
  ```

  - **page** - navega entre a paginação:

  ```
    GET api/v1/tasks?page=1
  ```

  - **per_page** - Sobrescreve o valor padrão(50) de registros por página:

  ```
    GET api/v1/tasks?page=1&per_page=5
  ```

  - **due_until** - Seleciona as tarefas que vencem até aquela data limite, o parâmetro `today` vai demonstrar todas as tarefas que vencem até o fim do dia de hoje

  ```
    GET api/v1/tasks?page=1&per_page=1&due_until=today
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
  }, {
    "id" : "{C73D41F9-EA1E-4A77-8A05-278B15AFC233}",
    "title": "Verificar E-mails",
    "due": "2016-06-30 19:27:08.644424",
    "visualized":  true,
    "completed_at": "2016-07-10 10:07:08.213221",
    "registered_at": "2016-07-01 19:27:08.651402",
    "category": "Geral",
    "assignee": {
      "id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
      "name": "Nome do responsável"
    },
    "person": null,
    "author": {
      "id":"{R22Q02F9-FH1E-4A69-1P12-278B15AFC634}",
      "name": "Nome do criou a tarefa"
    },
    "task_historics": []
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
  - **403** - Não autorizado
