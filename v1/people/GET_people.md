# Pessoas

    GET api/v1/people

## Descrição
Retorna as pessoas cadastradas.

***

## Autenticação
**[JWT](../authentication/POST_auth_token.md)**

***

## Parâmetros

  - **filter** - Filtra pessoas, nos campos `nome`, `razão social`, `cpf` e `cnpj`:

  ```
    GET /api/v1/people?filter=valor-da-pesquisa
  ```

  - **only_users** -  Quando `true` retorna todos as pessoas que são usuários:

  ```
    GET /api/v1/people?only_users=true
  ```

  - **page** - navega entre a paginação:

  ```
    GET api/v1/people?page=1
  ```

  - **per_page** - Sobrescreve o valor padrão(50) de registros por página:

  ```
    GET api/v1/people?page=1&per_page=5
  ```

***

## Formato de retorno

  Veja [formato completo](../full_format.md#pessoas)

***

## Exemplo
  **Requisição (Auth: JWT)**

    GET https://web.monde.com.br/api/v1/people

  **Resposta**
``` json
{
  "people": [
    {
      "id": "{338A833A-FE18-410E-9D31-8A8B9FBE4231}",
      "name": "Admin",
      "city_name": "Americana",
      "company_name": "Company One",
      "address": "1st Street",
      "number": "899",
      "complement": "Casa",
      "district": "St. John",
      "zip": "89999000",
      "birth_date": "2016-04-05",
      "cpf": null,
      "rg": null,
      "passport_number": null,
      "passport_expiration": null,
      "gender": null,
      "business_phone": "49368990000",
      "home_phone": "4936222190",
      "mobile_phone": "4991782812",
      "cnpj": "74982815000150",
      "state_inscription": "1234567890",
      "city_inscription": "1234567890",
      "phone": null,
      "fax": null,
      "email": "usuario@monde.com.br",
      "website": "https://www.site.com.br",
      "observations": "nothing to note",
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

***

## Erros
  Status code:
  - **401** - Não autenticado
