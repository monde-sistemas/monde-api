# Documentação da API do Monde

## Autenticação

É realizada por Basic Auth

## GET /api/v1/people

Esse método retorna uma lista de pessoas cadastradas:

```
{
  "people": [
    {
      "id": "{338A833A-FE18-410E-9D31-8A8B9FBE4231}",
        "name": "Admin",
        "city": "Americana",
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

- Status code de sucesso: `200 OK`

### Filtro

Para filtrar alguma pessoa por nome, cpf, razão social ou cnpj:

```
/api/v1/people?filter=valor-pesquisa
```

### Paginação

Para utilizar a paginação, utilize a chave `page` na paginação:

```
/api/v1/people?page=1
```

Para sobrescrever o valor padrão(50) de registros por página, utilize a chave `per_page` na query:

```
/api/v1/people?page=1&per_page=5
```

## POST /api/v1/people

Para criar um novo cadastro de pessoa envie o json no seguinte formato:

```
{
  "person": [
    {
        "name": "Admin",
        "city": "Americana",
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
        "sate_inscription": "1234567890",
        "city_inscription": "1234567890",
        "phone": null,
        "fax": null,
        "email": "usuario@monde.com.br",
        "website": "https://www.site.com.br",
        "observations": "nothing to note",
        "image": null,
        "type": "J"
    }
  ]
}
```

- Status code de criação: `201 Created`.
- Status code de erro de validação: `422 Unprocessable Entity`

Caso algum erro de validação ocorra, será retornado o seguinte JSON:

```
{
  errors: {
    name: [
      "não pode ficar em branco",
      "deve conter ao menos 6 dígitos"
    ],
    cpf: [
      "campo inválido"
    ]
  }
}
```

## PUT /api/v1/people/:id

A alteração de cadastro é realizado enviando o seguinte JSON no corpo da requisição:

```
{
  "person": [
    {
        "name": "Admin",
        "city": "Americana",
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
        "image": null,
        "type": "J"
    }
  ]
}
```

- Status code de alteração: `204 No Content`
- Status code de erro de validação: `422 Unprocessable Entity`

Caso algum erro de validação ocorra, será retornado o seguinte JSON:

```
{
  errors: {
    name: [
      "não pode ficar em branco",
      "deve conter ao menos 6 dígitos"
    ],
    cpf: [
      "campo inválido"
    ]
  }
}
```

## GET /api/v1/people/:id

Busca uma pessoa pelo seu código identificador, retornando o seguinte JSON:

```
{
  "person": [
    {
        "name": "Admin",
        "city": "Americana",
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
        "image": null,
        "type": "J"
    }
  ]
}
```

- Status code de busca: `200 OK`
- Status code de não encontrado: `404 Not Found`

## DELETE /api/v1/people/:id

Apaga o cadastro de pessoa pelo seu código identificador.

- Status code de exclusão: `204 No Content`
- Status code de não encontrado: `404 Not Found`
