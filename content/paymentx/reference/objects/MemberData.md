{
  "title": "MemberData",
  "description": "",
  "weight": 1,
  "fields": [
    {
      "typeString": "ID!",
      "name": "id",
      "url": "/paymentx/reference/scalars/id",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "ID!",
      "name": "code",
      "url": "/paymentx/reference/scalars/id",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "String",
      "name": "label",
      "url": "/paymentx/reference/scalars/string",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Boolean!",
      "name": "isActive",
      "url": "/paymentx/reference/scalars/boolean",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "MemberType!",
      "name": "type",
      "url": "/paymentx/reference/enums/membertype",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "GroupConnection",
      "name": "groups",
      "url": "/paymentx/reference/objects/groupconnection",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[ID!]",
          "name": "codes",
          "url": "/paymentx/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "GroupType",
          "name": "type",
          "url": "/paymentx/reference/enums/grouptype",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "first",
          "url": "/paymentx/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "last",
          "url": "/paymentx/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "String",
          "name": "before",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        },
        {
          "typeString": "String",
          "name": "after",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        }
      ]
    },
    {
      "typeString": "RoleConnection",
      "name": "roles",
      "url": "/paymentx/reference/objects/roleconnection",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[ID!]",
          "name": "codes",
          "url": "/paymentx/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "RoleType",
          "name": "type",
          "url": "/paymentx/reference/enums/roletype",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "first",
          "url": "/paymentx/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "last",
          "url": "/paymentx/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "String",
          "name": "before",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        },
        {
          "typeString": "String",
          "name": "after",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        }
      ]
    },
    {
      "typeString": "MacroPermissionsConnection",
      "name": "macroPermissions",
      "url": "/paymentx/reference/objects/macropermissionsconnection",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[ID!]",
          "name": "codes",
          "url": "/paymentx/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "first",
          "url": "/paymentx/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "Int",
          "name": "last",
          "url": "/paymentx/reference/scalars/int",
          "description": null
        },
        {
          "typeString": "String",
          "name": "before",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        },
        {
          "typeString": "String",
          "name": "after",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        }
      ]
    }
  ],
  "requireby": [
    {
      "name": "Member",
      "description": null,
      "url": "/paymentx/reference/objects/member"
    }
  ],
  "enumValues": null,
  "operator": "type",
  "typename": "MemberData",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}

## Required by

{{% graphql-require-by %}}
