# Tarefas

    GET api/v2/tasks

## Descrição
Retorna as tarefas cadastradas.

***

## Autenticação
**[JWT](../authentication/POST_tokens.md)**

***

## Parâmetros

  - **filter** - Filtra tarefas pelo `título` informado:

  ```
    GET api/v2/tasks?filter[search]=título-da-tarefa
  ```

  - **situation** - Filtra pela situação(`done`: `finalizada`, `open`: `não concluída`):

  ```
    GET api/v2/tasks?filter[situation]=done
  ```

  - **assigned** - Filtra por como o usuário é vinculado a tarefa (`user_tasks`: `tarefas do usuário`,
  `author`: `criada pelo usuário` e `delegated`: `delegadas pelo usuário`):
  
  ```
    GET api/v2/tasks?filter[assigned]=user_tasks
    GET api/v2/tasks?filter[assigned]=author
    GET api/v2/tasks?filter[assigned]=delegated
  ```

  - **page** - navega entre a paginação:

  ```
    GET api/v2/tasks?page[number]=1
  ```

  - **per_page** - Sobrescreve o valor padrão(50) de registros por página:

  ```
    GET api/v2/tasks?page[number]=1&page[size]=5
  ```

  - **due_until** - Seleciona as tarefas que vencem até aquela data limite, o parâmetro `today` vai demonstrar todas as tarefas que vencem até o fim do dia de hoje

  ```
    GET api/v2/tasks?filter[due_until]=today
  ```

***

## Formato de retorno

  Veja [formato completo](../full_format.md#tarefas)

***

## Exemplo
  **Requisição (Auth: JWT)**

    GET https://web.monde.com.br/api/v2/tasks

  **Resposta**

  #### Status de retorno
    200 - Ok

  ``` json
  {
    "data": [
      {
        "id": "54850eaf-b4d4-4a33-96f1-361a844bec08",
        "type": "tasks",
        "links": {
          "self": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08"
        },
        "attributes": {
          "title": "Repudiandae officiis eveniet eos.",
          "number": 3670,
          "due": "2021-10-29T00:00:00.000-03:00",
          "visualized": false,
          "completed": false,
          "completed-at": null,
          "registered-at": "2021-10-28T16:37:14.787-03:00"
        },
        "relationships": {
          "category": {
            "links": {
              "self": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/relationships/category",
              "related": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/category"
            }
          },
          "person": {
            "links": {
              "self": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/relationships/person",
              "related": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/person"
            }
          },
          "assignee": {
            "links": {
              "self": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/relationships/assignee",
              "related": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/assignee"
            }
          },
          "author": {
            "links": {
              "self": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/relationships/author",
              "related": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/author"
            }
          },
          "task-historics": {
            "links": {
              "self": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/relationships/task-historics",
              "related": "http://web.monde.com.br/api/v2/tasks/54850eaf-b4d4-4a33-96f1-361a844bec08/task-historics"
            }
          }
        }
      }
    ],
    "links": {
      "first": "http://web.monde.com.br/api/v2/tasks?page%5Bnumber%5D=1&page%5Bsize%5D=50",
      "last": "http://web.monde.com.br/api/v2/tasks?page%5Bnumber%5D=1&page%5Bsize%5D=50"
    }
  }
  ```
  
***

## Erros
  Status code:
  - **401** - Não autenticado
  - **403** - Não autorizado
