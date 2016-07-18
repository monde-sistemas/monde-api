# Formatos

## Tarefas
- **id** - Código identificador da tarefa, **guid**
- **title** - Título da tarefa, **string**
- **number** - Numeração sequêncial da tarefa, **integer**
- **assignee_id** - Código do responsável, **guid**
- **due** - Data de vencimento, **timestamp**
- **completed_at** - Data de conclusão, **timestamp**
- **registered_at** - Data de cadastro, **timestamp**
- **category** - Categoria da tarefa, **string**

## Categoria de Tarefas
- **description** - Descrição da categoria, **string**

## Histórico de tarefa
- **id** - Código identificador do histórico da tarefa, **guid**
- **task_id** - Código identificador da tarefa, **guid**
- **date_time** - Momento do histórico, **timestamp**
- **person_id** - Pessoa que criou o histórico, **guid**
- **text** - Mensagem de histórico, **string**
- **history** - Contéudo alterado na tarefa, **string** 
