# Arquivo

    GET api/v1/file

## Descrição
Download de um arquivo para o s3

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros

- **category** - Categoria (integration, attachment), **string**
- **file** - Extensão do arquivo, **string**

***

## Formato de retorno

- **file** - Path do arquivo no s3, **string**
- **url** - URL para download do arquivo, **string**

#### Status de retorno

    200 - ok

***

## Exemplo
  **Requisição (Auth: JWT)**

    GET https://web.monde.com.br/api/v1/file?category=attachment&file=5d8fa5f2-06a1-4074-86ae-84256fc3d000/ce459d58-1c0a-4c37-908a-a673e956be54.gz

  **Resposta**
``` json
{
  "file": "5d8fa5f2-06a1-4074-86ae-84256fc3d000/ce459d58-1c0a-4c37-908a-a673e956be54.gz",
  "url": "https://monde-anexos.s3.amazonaws.com/123456?AWSAccessKeyId=ASD8787ASD&Expires=1421765182&Signature=ituYDgHJ3ns5s3YpjeesMhxpWzM%3D"
}
```

***

## Erros

  Status code:
  - **401** - Não autenticado
  - **403** - Não autorizado
  - **422** - Unprocessable Entity.
