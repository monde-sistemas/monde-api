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
- **due** - Data de vencimento, **timestamp**
- **category** - Categoria da tarefa, **string**
- **done** - Concluída, **boolean**
- **task_historics** - Históricos de tarefas:
  - **text** - Mensagem de histórico, **string**
  - **historic** - Registro do contéudo alterado na tarefa, **string**

***

## Formato de retorno

- **id** - Código identificador da tarefa, **guid**
- **title** - Título da tarefa, **string**
- **number** - Numeração sequêncial da tarefa, **integer**
- **assignee_id** - Código do responsável, **guid**
- **due** - Data de vencimento, **timestamp**
- **done** - Concluída, **boolean**
- **completed_at** - Data de conclusão, **timestamp**
- **registered_at** - Data de cadastro, **timestamp**
- **category** - Categoria da tarefa, **string**
- **task_historics** - Históricos de tarefas:
  - **id** - Código identificador do histórico da tarefa, **guid**
  - **task_id** - Código identificador da tarefa, **guid**
  - **date_time** - Momento do histórico, **timestamp**
  - **person_id** - Pessoa que criou o histórico, **guid**
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
    "due": "2016-06-30 19:27:08.644424",
    "category": "Feedback",
    "done": false,
    "task_historics": [{
      "text": "First comment",
      "historic": "'Pessoa' alterado de 'John' para 'Steve'"
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
  - **422** - Unprocessable Entity.
