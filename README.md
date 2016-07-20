# Documentação da API do Monde

Endereço da API: https://web.monde.com.br/api

Deve ser adicionado o content type JSON ao Header da requisição:

```
Content-Type: application/json; charset=utf-8
```

## <code>V1</code>

### Formatos
- **[Pessoas](v1/full_format.md#pessoas)**
- **[Tarefas](v1/full_format.md#tarefas)**
- **[Históricos de tarefa](v1/full_format.md#histórico-de-tarefa)**
- **[Categorias de Tarefa](v1/full_format.md#categorias-de-tarefa)**

### Endpoints

#### Autenticação
- **[<code>POST</code> auth/auth_token](v1/authentication/POST_auth_token.md)**

#### Pessoas
- **[<code>GET</code> people](v1/people/GET_people.md)**
- **[<code>GET</code> people/:id](v1/people/GET_people_show.md)**
- **[<code>POST</code> people](v1/people/POST_people.md)**
- **[<code>PUT</code> people/:id](v1/people/PUT_people_edit.md)**
- **[<code>DELETE</code> people/:id](v1/people/DELETE_people.md)**


#### Tarefas
- **[<code>GET</code> tasks](v1/tasks/GET_tasks.md)**
- **[<code>GET</code> tasks/:id](v1/tasks/GET_tasks_show.md)**
- **[<code>POST</code> tasks](v1/tasks/POST_tasks.md)**
- **[<code>PUT</code> tasks/:id](v1/tasks/PUT_tasks_edit.md)**
- **[<code>DELETE</code> tasks/:id](v1/tasks/DELETE_tasks.md)**

#### Categorias de Tarefa
- **[<code>GET</code> task_categories](v1/task_categories/GET_task_categories.md)**
