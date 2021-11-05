## Autenticação

    POST api/v2/tokens

## Descrição
Esse método autentica o usuário e retorna o token de acesso caso o acesso seja válido.
É realizada por token (JWT), seguindo a RFC 7591.

## Parâmetros

- **type** - *Obrigatório* -	Tipo do recurso e deve ser sempre <code>auth</code>.
- **attributes[login]** - *Obrigatório* -	Login e endereço do usuário, ex: admin@suaagencia.monde.com.br (Para descobrir qual seu endereço veja https://link.monde.com.br/administracao-desktop-endereco-sistema.html)
- **attributes[password]** - *Obrigatório* -	Senha do usuário.
- **attributes[platform]** -	Plataforma que está acessando a API. Ex: "desktop", "mobile" e "web" (Padrão: "mobile")

## Exemplo

  **Requisição (Auth: JWT)**

    POST https://web.monde.com.br/api/v2/tokens
  
  ``` json
  {
    "data": {
      "type": "tokens",
      "attributes": {
        "login": "admin@mondesistemas.monde.com.br",
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
