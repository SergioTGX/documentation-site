{
  "title": "StatsConnection",
  "description": "",
  "weight": 1,
  "fields": [
    {
      "typeString": "[StatsEdge]",
      "name": "edges",
      "url": "/stats/reference/objects/statsedge",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "PageInfo!",
      "name": "pageInfo",
      "url": "/stats/reference/objects/pageinfo",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "[AdviseMessage!]",
      "name": "adviseMessage",
      "url": "/stats/reference/objects/advisemessage",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[AdviseMessageLevel]",
          "name": "level",
          "url": "/stats/reference/enums/advisemessagelevel",
          "description": null
        }
      ]
    }
  ],
  "requireby": [
    {
      "name": "StatsQuery",
      "description": null,
      "url": "/stats/reference/objects/statsquery"
    }
  ],
  "enumValues": null,
  "operator": "type",
  "typename": "StatsConnection",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}

## Required by

{{% graphql-require-by %}}
