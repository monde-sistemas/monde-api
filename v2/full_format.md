# Formatos

## Pessoas
- **id** - Código identificador da pessoa, **guid**
- **name** - Nome completo da pessoa, **string**
- **city** - Cidade em que reside., **relationship**
- **company-name** - Razão social, **string**
- **address** - Endereço, **string**
- **number** - Número do endereço, **string**
- **complement** - Complemento do endereço, **string**
- **district** - Bairro, **string**
- **zip** - CEP, **string**
- **birth-date** - Data de nascimento, **date**
- **cpf** - CPF, **string**
- **rg** - RG, **string**
- **passport-number** - Número do passaporte, **string**
- **passport-expiration** - Data vencimento do passaporte, **date**
- **gender** - sexo, **string**
- **business-phone** - Telefone comercial, **string**
- **phone** - Telefone de contato da pessoa, **string**
- **mobile-phone** - Telefone celular, **string**
- **cnpj** - CNPJ, **string**
- **state-inscription** - Inscrição estadual, **string**
- **city-inscription** - Inscrição municipal, **string**
- **email** - E-mail de contato, **string**
- **website** - Web site, **string**
- **observations** - Observações, **string**
- **registered_at** - Data de registro, **timestamp**
- **registered_by** - Quem registrou, **guid**
- **kind** - Tipo de cadastro, **string**

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
- **author** - Pessoa que criou a tarefa
  - **id** - Código identificador, **guid**
  - **name** - Nome da pessoa, **string**
- **due** - Data de vencimento, **timestamp**
- **visualized** - Tarefa foi visualizada pelo responsável, **boolean**
- **completed-at** - Data de conclusão, **timestamp**
- **registered-at** - Data de cadastro, **timestamp**
- **category** - Categoria da tarefa, **relationship**

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

## Vendas Importadas
- **id** - Código da venda, **uuid**
- **integration_id** - Código da integração, **uuid**
- **date** - Data da venda, **date**
- **passenger** - Passageiro, **string**
- **document** - Documento de identificação, **string**
- **data** - Dados importados, **json**

## Processos Assíncronos
- **status** - Status do processo (processing, done, error, internal_error) , **string**
- **error** - Descrição do erro quando disponível (HTTP 422), **string**