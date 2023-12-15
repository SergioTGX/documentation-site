{
  "title": "ChargeType",
  "description": "",
  "weight": 1,
  "fields": null,
  "requireby": [
    {
      "name": "Supplement",
      "description": null,
      "url": "/travelgatex/reference/objects/supplement"
    },
    {
      "name": "Surcharge",
      "description": null,
      "url": "/travelgatex/reference/objects/surcharge"
    }
  ],
  "enumValues": [
    {
      "name": "INCLUDE",
      "description": null,
      "isDeprecated": false,
      "deprecationReason": null
    },
    {
      "name": "EXCLUDE",
      "description": null,
      "isDeprecated": false,
      "deprecationReason": null
    }
  ],
  "operator": "enum",
  "typename": "ChargeType",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-enum %}}

## Required by

{{% graphql-require-by %}}
