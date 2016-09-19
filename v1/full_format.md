# Formatos

## Pessoas
- **id** - Código identificador da pessoa, **guid**
- **name** - Nome da pessoa, **string**
- **city_name** - Nome da cidade, **string**
- **company_name** - Razão social, **string**
- **address** - Endereço, **string**
- **number** - Número do endereço, **string**
- **complement** - Complemento do endereço, **string**
- **district** - Bairro, **string**
- **zip** - CEP, **string**
- **birth_date** - Data de nascimento, **date**
- **cpf** - CPF, **string**
- **rg** - RG, **string**
- **passport_number** - Número do passaporte, **string**
- **passport_expiration** - Data vencimento do passaporte, **date**
- **gender** - sexo, **string**
- **business_phone** - Telefone comercial, **string**
- **home_phone** - Telefone residencial, **string**
- **mobile_phone** - Telefone celular, **string**
- **cnpj** - CNPJ, **string**
- **state_inscription** - Inscrição estadual, **string**
- **city_inscription** - Inscrição municipal, **string**
- **phone** - Telefone, **string**
- **fax** - Fax, **string**
- **email** - E-mail, **string**
- **website** - Site, **string**
- **observations** - Observações, **string**
- **registered_at** - Data de registro, **timestamp**
- **registered_by** - Quem registrou, **guid**
- **type** - Tipo de cadastro, **string**

## Tarefas
- **id** - Código identificador da tarefa, **guid**
- **title** - Título da tarefa, **string**
- **number** - Numeração sequêncial da tarefa, **integer**
- **assignee** - Responsável da tarefa
  - **id** - Código identificador, **guid**
  - **name** - Nome do responsável, **string**
- **person** - Pessoa relacionada a tarefa
  - **id** - Código identificador, **guid**
  - **name** - Nome da pessoa, **string**
- **due** - Data de vencimento, **timestamp**
- **visualized** - Tarefa foi visualizada pelo responsável, **boolean**
- **completed_at** - Data de conclusão, **timestamp**
- **registered_at** - Data de cadastro, **timestamp**
- **category** - Categoria da tarefa, **string**

## Categorias de Tarefa
- **description** - Descrição da categoria, **string**

## Histórico de tarefa
- **id** - Código identificador do histórico da tarefa, **guid**
- **task_id** - Código identificador da tarefa, **guid**
- **date_time** - Momento do histórico, **timestamp**
- **person** - Pessoa que criou o histórico
  - **id** - Código identificador, **guid**
  - **name** - Nome do responsável, **string**
- **text** - Mensagem de histórico, **string**
- **historic** - Registro do contéudo alterado na tarefa, **string**
