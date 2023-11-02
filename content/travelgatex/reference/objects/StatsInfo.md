{
  "title": "StatsInfo",
  "description": "",
  "weight": 1,
  "fields": [
    {
      "typeString": "ID!",
      "name": "code",
      "url": "/travelgatex/reference/scalars/id",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "StatsInfoTypes!",
      "name": "type",
      "url": "/travelgatex/reference/enums/statsinfotypes",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int64!",
      "name": "hits",
      "url": "/travelgatex/reference/scalars/int64",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int!",
      "name": "time",
      "url": "/travelgatex/reference/scalars/int",
      "description": null,
      "isDeprecated": true,
      "args": null,
      "deprecationReason": "Added new fields averageTime and totalTime.",
      "descriptionSplitted": {
        "date": "2019-04-03",
        "first": "deprecated from",
        "second": "Added new fields averageTime and totalTime."
      },
      "deprecationDate": "2019-04-03",
      "typeName": "StatsInfo"
    },
    {
      "typeString": "Int64!",
      "name": "averageTime",
      "url": "/travelgatex/reference/scalars/int64",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int64!",
      "name": "totalTime",
      "url": "/travelgatex/reference/scalars/int64",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "[StatsAsset!]",
      "name": "assets",
      "url": "/travelgatex/reference/objects/statsasset",
      "description": null,
      "isDeprecated": false,
      "args": null
    }
  ],
  "requireby": null,
  "enumValues": null,
  "operator": "type",
  "typename": "StatsInfo",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}
