{
  "title": "GroupData",
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
      "typeString": "GroupType!",
      "name": "type",
      "url": "/paymentx/reference/enums/grouptype",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "String",
      "name": "info",
      "url": "/paymentx/reference/scalars/string",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Group",
      "name": "parent",
      "url": "/paymentx/reference/objects/group",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "GroupConnection",
      "name": "children",
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
        },
        {
          "typeString": "GroupType",
          "name": "type",
          "url": "/paymentx/reference/enums/grouptype",
          "description": null
        },
        {
          "typeString": "String",
          "name": "codeStartsWith",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        }
      ]
    },
    {
      "typeString": "GroupConnection",
      "name": "descendents",
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
        },
        {
          "typeString": "String",
          "name": "codeStartsWith",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        }
      ]
    },
    {
      "typeString": "GroupConnection",
      "name": "parents",
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
          "typeString": "String",
          "name": "codeStartsWith",
          "url": "/paymentx/reference/scalars/string",
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
      "typeString": "Member",
      "name": "owner",
      "url": "/paymentx/reference/objects/member",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Boolean!",
      "name": "isEditable",
      "url": "/paymentx/reference/scalars/boolean",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int",
      "name": "productId",
      "url": "/paymentx/reference/scalars/int",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int",
      "name": "resourceId",
      "url": "/paymentx/reference/scalars/int",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "GroupConnection",
      "name": "siblings",
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
        },
        {
          "typeString": "String",
          "name": "codeStartsWith",
          "url": "/paymentx/reference/scalars/string",
          "description": null
        }
      ]
    },
    {
      "typeString": "MemberConnection",
      "name": "members",
      "url": "/paymentx/reference/objects/memberconnection",
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
          "typeString": "MemberType",
          "name": "type",
          "url": "/paymentx/reference/enums/membertype",
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
      "typeString": "APIConnection",
      "name": "apis",
      "url": "/paymentx/reference/objects/apiconnection",
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
    },
    {
      "typeString": "ManagedGroupConnection",
      "name": "managedGroups",
      "url": "/paymentx/reference/objects/managedgroupconnection",
      "description": null,
      "isDeprecated": false,
      "args": [
        {
          "typeString": "[ID!]",
          "name": "group",
          "url": "/paymentx/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "[ID!]",
          "name": "api",
          "url": "/paymentx/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "[ID!]",
          "name": "resource",
          "url": "/paymentx/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "[ID!]",
          "name": "role",
          "url": "/paymentx/reference/scalars/id",
          "description": null
        },
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
    },
    {
      "typeString": "MemberConnection",
      "name": "allMembers",
      "url": "/paymentx/reference/objects/memberconnection",
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
          "typeString": "MemberType",
          "name": "type",
          "url": "/paymentx/reference/enums/membertype",
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
      "typeString": "AccessConnection",
      "name": "accesses",
      "url": "/paymentx/reference/objects/accessconnection",
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
    },
    {
      "typeString": "SupplierConnection",
      "name": "suppliers",
      "url": "/paymentx/reference/objects/supplierconnection",
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
          "typeString": "[ID!]",
          "name": "accessID",
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
    },
    {
      "typeString": "ClientConnection",
      "name": "clients",
      "url": "/paymentx/reference/objects/clientconnection",
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
          "typeString": "[ID!]",
          "name": "name",
          "url": "/paymentx/reference/scalars/id",
          "description": null
        },
        {
          "typeString": "Boolean",
          "name": "isActive",
          "url": "/paymentx/reference/scalars/boolean",
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
      "typeString": "ProfileConnection",
      "name": "profiles",
      "url": "/paymentx/reference/objects/profileconnection",
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
      "name": "Group",
      "description": null,
      "url": "/paymentx/reference/objects/group"
    }
  ],
  "enumValues": null,
  "operator": "type",
  "typename": "GroupData",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}

## Required by

{{% graphql-require-by %}}
