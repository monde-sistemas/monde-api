## PUT /api/v1/people/:id

A alteração de cadastro é realizado enviando o seguinte JSON no corpo da requisição:

```
{
  "person": {
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
    "image": null,
    "type": "J"
  }
}
```

- Status code de alteração: `200 Ok`
- A resposta contém o cadastro alterado
- Status code de erro de validação: `422 Unprocessable Entity`

Caso algum erro de validação ocorra, será retornado o seguinte JSON:

```
{
  errors: {
    [
      "Nome não pode ficar em branco",
      "Nome deve conter ao menos 6 dígitos",
      "CPF é inválido"
    ]
  }
}
```