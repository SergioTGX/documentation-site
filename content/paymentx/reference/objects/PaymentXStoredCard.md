{
  "title": "PaymentXStoredCard",
  "description": "",
  "weight": 1,
  "fields": [
    {
      "typeString": "ID!",
      "name": "code",
      "url": "/paymentx/reference/scalars/id",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "PaymentXStoredCardData",
      "name": "storedCardData",
      "url": "/paymentx/reference/objects/paymentxstoredcarddata",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "DateTime!",
      "name": "createdAt",
      "url": "/paymentx/reference/scalars/datetime",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "DateTime!",
      "name": "updatedAt",
      "url": "/paymentx/reference/scalars/datetime",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "[AdviseMessage!]",
      "name": "adviseMessage",
      "url": "/paymentx/reference/objects/advisemessage",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[AdviseMessageLevel]",
          "name": "level",
          "url": "/paymentx/reference/enums/advisemessagelevel",
          "description": null
        }
      ]
    }
  ],
  "requireby": [
    {
      "name": "PaymentXStoredCardEdge",
      "description": null,
      "url": "/paymentx/reference/objects/paymentxstoredcardedge"
    },
    {
      "name": "PaymentXQuery",
      "description": null,
      "url": "/paymentx/reference/objects/paymentxquery"
    },
    {
      "name": "PaymentXMutation",
      "description": null,
      "url": "/paymentx/reference/objects/paymentxmutation"
    }
  ],
  "enumValues": null,
  "operator": "type",
  "typename": "PaymentXStoredCard",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}

## Required by

{{% graphql-require-by %}}
