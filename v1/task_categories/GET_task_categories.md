# Categorias de Tarefa

    GET api/v1/task_categories

## Descrição
Retorna as categorias de tarefas cadastradas.

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros
  Não possui

***

## Formato de retorno

  - **description** - Descrição da categoria, **string**

***

## Erros
  Status code:
  - **401** - Não autenticado

***

## Exemplo
  **Requisição (Auth: JWT)**

    https://web.monde.com.br/api/v1/task_categories

  **Resposta**
``` json
{
  "task_categories": [{
    "description": "Geral"
  }, {
    "description": "Feedback"
  }]
}
```
