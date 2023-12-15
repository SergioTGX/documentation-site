{
  "title": "PaymentXStoredCardData",
  "description": "",
  "weight": 1,
  "fields": [
    {
      "typeString": "Group!",
      "name": "instance",
      "url": "/travelgatex/reference/objects/group",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "PointOfSale!",
      "name": "pointOfSale",
      "url": "/travelgatex/reference/objects/pointofsale",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "String!",
      "name": "bookingReference",
      "url": "/travelgatex/reference/scalars/string",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Date",
      "name": "checkOut",
      "url": "/travelgatex/reference/scalars/date",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Date",
      "name": "checkIn",
      "url": "/travelgatex/reference/scalars/date",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "String",
      "name": "cardType",
      "url": "/travelgatex/reference/scalars/string",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Holder",
      "name": "holder",
      "url": "/travelgatex/reference/objects/holder",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "CardNumber",
      "name": "number",
      "url": "/travelgatex/reference/scalars/cardnumber",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "CVC",
      "name": "CVC",
      "url": "/travelgatex/reference/scalars/cvc",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "PaymentXExpireDate",
      "name": "expire",
      "url": "/travelgatex/reference/objects/paymentxexpiredate",
      "description": null,
      "isDeprecated": false,
      "args": null
    }
  ],
  "requireby": [
    {
      "name": "PaymentXStoredCard",
      "description": null,
      "url": "/travelgatex/reference/objects/paymentxstoredcard"
    }
  ],
  "enumValues": null,
  "operator": "type",
  "typename": "PaymentXStoredCardData",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}

## Required by

{{% graphql-require-by %}}
