{
  "title": "APIData",
  "description": "",
  "weight": 1,
  "fields": [
    {
      "typeString": "ID!",
      "name": "code",
      "url": "/mappea/reference/scalars/id",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "ID!",
      "name": "id",
      "url": "/mappea/reference/scalars/id",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Boolean!",
      "name": "isEditable",
      "url": "/mappea/reference/scalars/boolean",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "String",
      "name": "label",
      "url": "/mappea/reference/scalars/string",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "GroupConnection",
      "name": "groups",
      "url": "/mappea/reference/objects/groupconnection",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[ID!]",
          "name": "codes",
          "url": "/mappea/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "GroupType",
          "name": "type",
          "url": "/mappea/reference/enums/grouptype",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "first",
          "url": "/mappea/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "last",
          "url": "/mappea/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "String",
          "name": "before",
          "url": "/mappea/reference/scalars/string",
          "description": null
        },
        {
          "typeString": "String",
          "name": "after",
          "url": "/mappea/reference/scalars/string",
          "description": null
        }
      ]
    },
    {
      "typeString": "ResourceConnection",
      "name": "resources",
      "url": "/mappea/reference/objects/resourceconnection",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[ID!]",
          "name": "codes",
          "url": "/mappea/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "first",
          "url": "/mappea/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "last",
          "url": "/mappea/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "String",
          "name": "before",
          "url": "/mappea/reference/scalars/string",
          "description": null
        },
        {
          "typeString": "String",
          "name": "after",
          "url": "/mappea/reference/scalars/string",
          "description": null
        }
      ]
    },
    {
      "typeString": "OperationConnection",
      "name": "operations",
      "url": "/mappea/reference/objects/operationconnection",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[ID!]",
          "name": "codes",
          "url": "/mappea/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "OperationType",
          "name": "type",
          "url": "/mappea/reference/enums/operationtype",
          "description": null
        },
        {
          "typeString": "[OperationType!]",
          "name": "types",
          "url": "/mappea/reference/enums/operationtype",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "first",
          "url": "/mappea/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "last",
          "url": "/mappea/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "String",
          "name": "before",
          "url": "/mappea/reference/scalars/string",
          "description": null
        },
        {
          "typeString": "String",
          "name": "after",
          "url": "/mappea/reference/scalars/string",
          "description": null
        }
      ]
    },
    {
      "typeString": "[AdviseMessage!]",
      "name": "adviseMessageCatalog",
      "url": "/mappea/reference/objects/advisemessage",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[AdviseMessageLevel]",
          "name": "level",
          "url": "/mappea/reference/enums/advisemessagelevel",
          "description": null
        }
      ]
    }
  ],
  "requireby": [
    {
      "name": "API",
      "description": null,
      "url": "/mappea/reference/objects/api"
    }
  ],
  "enumValues": null,
  "operator": "type",
  "typename": "APIData",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}

## Required by

{{% graphql-require-by %}}
