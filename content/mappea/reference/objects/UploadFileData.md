{
  "title": "UploadFileData",
  "description": "",
  "weight": 1,
  "fields": [
    {
      "typeString": "String!",
      "name": "fileId",
      "url": "/mappea/reference/scalars/string",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "[SupplierDetected!]",
      "name": "suppliers",
      "url": "/mappea/reference/objects/supplierdetected",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int",
      "name": "numberOfLines",
      "url": "/mappea/reference/scalars/int",
      "description": null,
      "isDeprecated": false,
      "args": null
    },
    {
      "typeString": "Int",
      "name": "numberOfHotels",
      "url": "/mappea/reference/scalars/int",
      "description": null,
      "isDeprecated": false,
      "args": null
    }
  ],
  "requireby": [
    {
      "name": "UploadFileResponse",
      "description": null,
      "url": "/mappea/reference/objects/uploadfileresponse"
    }
  ],
  "enumValues": null,
  "operator": "type",
  "typename": "UploadFileData",
  "hideGithubLink": true
}
## GraphQL schema definition

{{% graphql-schema-type %}}

## Fields

{{% graphql-field %}}

## Required by

{{% graphql-require-by %}}
