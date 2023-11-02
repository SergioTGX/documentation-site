{
  "title": "AlertTypeConfiguration",
  "description": "",
  "weight": 1,
  "fields": [
    {
      "typeString": "Int",
      "name": "historicalWindow",
      "url": "/travelgatex/reference/scalars/int",
      "description": "The time frame in minutes to be used to compare with the window time frame",
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int",
      "name": "offset",
      "url": "/travelgatex/reference/scalars/int",
      "description": "Time frame in minutes to set the beginning of historicalWindow",
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int",
      "name": "max_average",
      "url": "/travelgatex/reference/scalars/int",
      "description": "maximum average time allowed in miliseconds",
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "[Int!]",
      "name": "toCheck",
      "url": "/travelgatex/reference/scalars/int",
      "description": "Error codes to be Checked. By default  all error codes excepts 0",
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "[Int!]",
      "name": "toCompare",
      "url": "/travelgatex/reference/scalars/int",
      "description": "Error codes to be Compared with Checked codes. By default all error codes",
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "AlertPrice",
      "name": "price",
      "url": "/travelgatex/reference/objects/alertprice",
      "description": "Price contains the specific configuration for Price alert Type",
      "isDeprecated": false,
      "args": null
    }
  ],
  "requireby": [
    {
      "name": "AlertConfiguration",
      "description": null,
      "url": "/travelgatex/reference/objects/alertconfiguration"
    }
  ],
  "enumValues": null,
  "operator": "type",
  "typename": "AlertTypeConfiguration",
  "hideGithubLink": true
}
Depending on the talert type, typeConfiguration will use some fields 
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}

## Required by

{{% graphql-require-by %}}
