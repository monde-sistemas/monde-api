# Pessoa

    DELETE /api/v2/people/:id

## Descrição
Exclui uma pessoa através do `id` de cadastro.

***

## Autenticação
**[JWT](../authentication/POST_tokens.md)**

***

## Parâmetros

  - **id** - código identificador do cadastro

***

## Exemplo

  **Requisição (Auth: JWT)**
  
    DELETE https://web.monde.com.br/api/v2/people/C73D41F9-EA1E-4A69-8A05-278B15AFC233
 
  **Resposta**
  #### Status de retorno

    204 - No Content

***

## Erros
  Status code:
  - **401** - Não autenticado
  - **404** - Registro não encontrado.
  - **422** - Erro de validação (ex.: Cadastro possui vínculo com algum outro cadastro, não permitindo excluir)

***

## Limite de Requisições

Este endpoint permite **3 requisições a cada 5 segundos**.

Ao atingir o limite, será retornado um erro com status `429 Too Many Requests`.

## Formato do erro de limite de requisições excedido

``` json
{
  "errors": [
    {
      "title": "Limite de requisições excedido",
      "detail": "Você excedeu o limite de requisições permitidas. Aguarde um momento antes de tentar novamente.",
      "code": "429",
      "status": "429"
    }
  ]
}
```
