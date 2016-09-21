# Tarefa

    PUT api/v1/tasks/:id

## Descrição
Altera um cadastro de tarefa através do `id` de cadastro.

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros

- **id** - código identificador do cadastro
- **title** - Título da tarefa, **string**
- **assignee_id** - Código do responsável, **guid**
- **person_id** - Pessoa relacionada a tarefa, **guid**
- **due** - Data de vencimento, **timestamp**
- **category** - Categoria da tarefa, **string**
- **visualized** - Tarefa foi visualizada pelo responsável, **boolean**
- **task_historics** - Históricos de tarefas:
  - **text** - Mensagem de histórico, **string**

***

## Formato de retorno

- **id** - Código identificador da tarefa, **guid**
- **title** - Título da tarefa, **string**
- **number** - Numeração sequêncial da tarefa, **integer**
- **assignee** - Responsável da tarefa
  - **id** - Código identificador, **guid**
  - **name** - Nome do responsável, **string**
- **person** - Pessoa relacionada a tarefa
  - **id** - Código identificador, **guid**
  - **name** - Nome da pessoa, **string**
- **author** - Pessoa que criou a tarefa
  - **id** - Código identificador, **guid**
  - **name** - Nome da pessoa, **string**
- **due** - Data de vencimento, **timestamp**
- **visualized** - Tarefa foi visualizada pelo responsável, **boolean**
- **completed_at** - Data de conclusão, **timestamp**
- **registered_at** - Data de cadastro, **timestamp**
- **category** - Categoria da tarefa, **string**
- **task_historics** - Históricos de tarefas:
  - **id** - Código identificador do histórico da tarefa, **guid**
  - **task_id** - Código identificador da tarefa, **guid**
  - **date_time** - Momento do histórico, **timestamp**
  - **person** - Pessoa que criou o histórico
    - **id** - Código identificador, **guid**
    - **name** - Nome da pessoa, **string**
  - **text** - Mensagem de histórico, **string**
  - **historic** - Registro do contéudo alterado na tarefa, **string**

#### Status de retorno

    200 - Ok

***

## Exemplo
  **Requisição (Auth: JWT)**

    PUT https://web.monde.com.br/api/v1/tasks/{C73D41F9-EA1E-4A69-8A05-278B15AFC233}

``` json
{
  "task": {
    "title": "Task One",
    "assignee_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
    "person_id": "{R22Q02F9-FH1E-4A69-1P12-278B15AFC634}",
    "due": "2016-06-30 19:27:08.644424",
    "category": "Feedback",
    "visualized": false,
    "task_historics": [{
      "text": "First comment"
    }]
  }
}
```

  **Resposta**
``` json
{
  "task": {
    "id" : "{C73D41F9-EA1E-4A69-8A05-278B15AFC233}",
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
      "name": "Nome de quem criou a tarefa"
    },
    "task_historics": [{
      "id": "{F45D41F9-EA1E-4A69-8A05-278B15AFC456}",
      "task_id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC233}",
      "date_time": "2016-06-30 19:27:08.844424",
      "person": {
        "id": "{C73D41F9-EA1E-4A69-8A05-278B15AFC244}",
        "name": "Nome do criador do histórico"
      },
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
      "Título é obrigatório",
      "Categoria é obrigatório"
    ]
  }
  ```

  Status code:
  - **401** - Não autenticado
  - **403** - Não autorizado
  - **422** - Unprocessable Entity.
