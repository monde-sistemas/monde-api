## Autenticação

    POST api/v2/tokens

## Descrição
Esse método autentica o usuário e retorna o token de acesso caso o acesso seja válido.

**As credenciais usadas aqui são as de um usuário comum do sistema** — o mesmo login e a mesma senha com que a pessoa entra no Monde. Não existe credencial exclusiva de API: basta usar um usuário já existente no cadastro de usuários da própria agência (ou criar um novo por lá, dedicado à integração). O usuário utilizado precisa ter [permissão de acesso total](https://monde.movidesk.com/kb/article/226178/permissoes-de-acesso) ao sistema.

A autenticação é realizada por token (JWT), seguindo a RFC 7591.

## Como montar o login

O `login` enviado na requisição é sempre a identificação do usuário seguida do endereço do sistema da agência:

    <identificação do usuário>@<endereço do sistema>

O endereço do sistema é o mesmo usado para acessar o Monde. Para descobrir o endereço correto da sua agência, consulte [este artigo](https://link.monde.com.br/administracao-desktop-endereco-sistema.html).

Já a identificação do usuário depende de a agência ter ou não migrado para o [login por e-mail](https://ajuda.monde.com.br/pt-BR/articles/15135321-principais-duvidas-sobre-o-login-por-e-mail-no-monde):

- **Agência ainda não migrada** — use o login do usuário:

      admin@suaagencia.monde.com.br

- **Agência já migrada para o login por e-mail** — use o e-mail de acesso do usuário, completo, no lugar do login. Como o endereço do sistema continua no final, o valor fica com duas arrobas — é assim mesmo:

      agente@viagem.com.br@suaagencia.monde.com.br

Na dúvida, use a mesma identificação com que esse usuário entra na tela de login do Monde, acrescentando `@<endereço do sistema>` no final.

## Parâmetros

- **type** - *Obrigatório* -	Tipo do recurso e deve ser sempre <code>tokens</code>.
- **attributes[login]** - *Obrigatório* -	Identificação do usuário (login ou e-mail de acesso) mais o endereço utilizado para a configuração do Monde, conforme a seção [Como montar o login](#como-montar-o-login). Exemplo: `admin@suaagencia.monde.com.br`.
- **attributes[password]** - *Obrigatório* -	Senha do usuário, a mesma utilizada para acessar o Monde.

## Exemplo

  **Requisição (Auth: JWT)**

    POST https://web.monde.com.br/api/v2/tokens

  ``` json
  {
    "data": {
      "type": "tokens",
      "attributes": {
        "login": "admin@suaagencia.monde.com.br",
        "password": "u4K2EJwGFL"
      }
    }
  }
  ```

  **Requisição de uma agência que já migrou para o login por e-mail**

  ``` json
  {
    "data": {
      "type": "tokens",
      "attributes": {
        "login": "agente@viagem.com.br@suaagencia.monde.com.br",
        "password": "u4K2EJwGFL"
      }
    }
  }
  ```

  **Resposta**

  #### Status de retorno

    200 - Ok

  ``` json
  {
    "data": {
      "id": "832d21f1-6d54-4322-ae25-93cd4ba749ff",
      "type": "tokens",
      "links": {
        "self": "http://web.monde.com.br/api/v2/tokens/832d21f1-6d54-4322-ae25-93cd4ba749ff"
      },
      "attributes": {
        "login": "admin",
        "token": "eyJhbGciOiJIUzI1NiJ9.eyJ1aWQiOiI4MzJkMjFmMS02ZDU0LTQzMjItYWUyNS05M2NkNGJhNzQ5ZmYiLCJpc3N1ZXIiOiJNb25kZSIsInNjaGVtYSI6Im1vbmRlc2lzdGVtYXMiLCJleHAiOjE2MzU0NTM0MzR9.HVW91M7lSA07syCxPPdVJOSi8M7Z9nGQ5ZxPz-JyriA"
      }
    }
  }
  ```

- Status code de não autenticação: `401 Unauthorized`. Esse código será retornado caso houver erro de autenticação e tentativa de acesso sem autenticação em algum método protegido da API
- Tempo de vida do token: `uma hora`

Para fazer uma requisição autenticada para a API, é necessário passar o token no header da requisição:

```
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9
```

## Erros
  Status code:
  - **401** - Não autenticado (credenciais inválidas)
  - **429** - Limite de requisições excedido (1 requisição a cada 3 segundos)
