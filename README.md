API do Monde "beta"
===================

Seja bem-vindo a documentaço da API do [Monde](https://www.monde.com.br/)! Se você quer desenvolver alguma integração com o Monde, está no lugar certo. Nossa API é bem recente e ainda dá acesso a poucas partes do sistema, mas pretendemos ir expandindo ela priorizando a necessidade dos clientes.

Apesar da simplicidade atual da API, ela já é usada dentro da Monde por todos os nossos aplicativos, principalmente para iOS e Android, mas também por nosso aplicativo Windows, portanto fique tranquilo que a API é uma iniciativa bem séria pra gente e trabalhamos duro para mantê-la o mais estável possível.

Como ainda estamos em fase beta, a documentação está menos detalhada do que gostaríamos, portanto se tiver dúvidas ou precisar de qualquer ajuda, [crie uma issue](../../issues) aqui no próprio repositório que responderemos o mais breve possível.

Sobre a API
------------
A API segue um estilo REST, e usa JSON para todas as requisições. Algumas informações rápidas para facilitar:

- Todas as requisições devem ser feitas para `https://web.monde.com.br/api/v1`
- Atualmente a autenticação é realizada por token (JWT), seguindo a RFC 7591.
- Toda requisição deve ser HTTPS e ter `Content-Type: application/json; charset=utf-8` adicionado ao Header.

Fazendo uma requisição
----------------------

O processo se dá em dois passos: **Autenticação** e **Requisição**. Sendo que a Autenticação não precisa ser realizada todo momento, e pode ser realizado apenas quando o token expirar(a cada 1 hora).

##### Passo 1 - Autenticação:

Já que o endpoint da autenticação é `auth/auth_token` Em cURL (para você tentar na sua shell), podemos fazer assim:


```
curl -H "Content-Type: application/json" \
     -X POST https://web.monde.com.br/api/v1/auth/auth_token \
     -d '{"auth": {"login": "usuario@endereco.monde.com.br", "password": "senha", "platform": "api"}}'
```

A resposta da requisição vai parecer com o que está abaixo:

```
{
  "token":   "SEU_TOKEN_DE_ACESSO",
  "user_id": "ID_DO_USUARIO",
  "name":    "John Snow"
}
```
**PS: Tome nota da chave está em `TOKEN_DE_ACESSO`**

##### Passo 2 - Requisição:

No nosso exemplo vamos listar todas as pessoas da nossa base.
Sabemos que o endpoint da API para fazer isso é o [**<code>GET</code> /people**](v1/people/GET_people.md) ([ver todos os endpoints](#endpoints-da-api)) e já temos nosso `TOKEN_DE_ACESSO`


```
export TOKEN_DE_ACESSO="SEU_TOKEN_DE_ACESSO"

curl -H "Content-Type: application/json charset=utf-8" \
     -H "Authorization: Bearer $TOKEN_DE_ACESSO" \
     -X GET https://web.monde.com.br/api/v1/people
```

A resposta da requisição vai parecer com o que está abaixo:

```
{
  "people": [
    {
      "id": "{338A833A-FE18-410E-9D31-8A8B9SDE4231}",
      "name": "Admin",
      "city_name": "Americana",
      "company_name": "Company One",
      "address": "1st Street",
      ...
      "email": "usuario@monde.com.br",
      "website": "https://www.site.com.br",
      "registered_at": "2016-04-05T10:52:59.978-03:00",
      "registered_by": "{338A833A-FE18-410E-9D31-8A8B9FBE4231}",
      "image": null,
      "type": "J"
    }
  ],
  "meta": {
    "pagination": {
      "per_page": 1,
      "total_pages": 4,
      "total_objects": 4
    }
  }
}
```

Paginação
-----------
Na resposta de toda requisição <code>GET</code> mostramos algumas informações para lhe auxiliar na paginação. Por padrão retornamos 50 registros por vez.

Exemplo:
```
{
 "..": [
 ...
],
...
"meta": {
    "pagination": {
      "per_page": 50,
      "total_pages": 4,
      "total_objects": 4
    }
  }
}
```
Para entender melhor:

- **per_page**: *Quantidade de registros na página*
- **total_pages**: *Quantidade total de páginas*
- **total_objects**: *Quantidade total de registros*


Erros e Códigos de resposta HTTP
---------------------------

Para análise dos erros da API veja o `código de resposta HTTP`, abaixo alguns códigos mais comuns e possíveis soluções:


- **200**: Tudo está correto.
- **201**: Registro criado com sucesso
- **301**: Redirecionamento (veja se o caminho está correto ou analise a documentação para saber se o seu endpoint não foi alterado)
- **401**: Não autorizado (seu usuário ou senha estão errados ou seu token pode ter expirado)
- **403**: Não permitida essa ação
- **404**: Não encontrado (possivelmente você errou o endpoint, ou algum header do endpoit, ou o registro no eciste)
- **422**: Erro na validação dos dados
- **500**: Algum problema pode estar acontecendo nos nossos servidores, nos avise que tentaremos resolver o mais rápido possível.


Formatos
-----------------------------

- **[Pessoas](v1/full_format.md#pessoas)**
- **[Tarefas](v1/full_format.md#tarefas)**
- **[Históricos de tarefa](v1/full_format.md#histórico-de-tarefa)**
- **[Categorias de Tarefa](v1/full_format.md#categorias-de-tarefa)**

Endpoints da API
----------------------------------

#### Autenticação
> Para autenticar no sistema e obter o Token

- **[<code>POST</code> auth/auth_token](v1/authentication/POST_auth_token.md)**

### Pessoas
> Trata as interações com Pessoas

- **[<code>GET</code> people](v1/people/GET_people.md)** - Lista as pessoas
- **[<code>GET</code> people/:id](v1/people/GET_people_show.md)** - Visualiza os dados da pessoa com o ID `:id`
- **[<code>POST</code> people](v1/people/POST_people.md)** - Cria um novo cadastro de pessoa
- **[<code>PUT</code> people/:id](v1/people/PUT_people_edit.md)** - Altera o cadastro da pessoa com ID `:id`
- **[<code>DELETE</code> people/:id](v1/people/DELETE_people.md)** - Deleta a pessoa de ID `:id`


#### Tarefas
> Trata as interações com as Tarefas

- **[<code>GET</code> tasks](v1/tasks/GET_tasks.md)** - Lista as tarefas
- **[<code>GET</code> tasks/:id](v1/tasks/GET_tasks_show.md)** - Visualiza os dados da tarefa com o ID `:id`
- **[<code>POST</code> tasks](v1/tasks/POST_tasks.md)** - Cria um novo cadastro de tarefa
- **[<code>PUT</code> tasks/:id](v1/tasks/PUT_tasks_edit.md)** - Altera o cadastro da tarefa com ID `:id`
- **[<code>DELETE</code> tasks/:id](v1/tasks/DELETE_tasks.md)** - Deleta a tarefa de ID `:id`

#### Categorias de Tarefa
> Trata sobre as categorias das Tarefas

- **[<code>GET</code> task_categories](v1/task_categories/GET_task_categories.md)** - Lista as categorias de tarefas
