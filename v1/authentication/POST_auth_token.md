## Autenticação

É realizada por token (JWT), seguindo a RFC 7591.

## POST /api/v1/auth/auth_token

Esse método autentica o usuário e retorna o token de acesso caso o acesso seja válido, o request deve ter o seguinte formato:

```
{
  "auth": {
    "login": "usuário@endereco.monde.com.br",
    "password": "senha",
    "client": "mobile/desktop"
  }
}
```

Caso a autenticação ocorra sem problemas, é retornado o token de acesso:

```
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9",
  "user_id": "{093480A5-DB9B-4516-A0DE-640CBAFE5DD2}",
  "name": "Nome Usuario"
}
```

- Status code será: `200 OK`
- Status code de não autenticação: `401 Unauthorized`. Esse código será retornado caso houver erro de autenticação e tentativa de acesso sem autenticação em algum método protegido da API
- Tempo de vida do token: `uma hora`

Para fazer uma requisição autenticada para a API, é necessário passar o token no header da requisição:

```
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9
```
