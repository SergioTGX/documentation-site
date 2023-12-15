{
  "title": "ID",
  "description": "",
  "weight": 1,
  "fields": null,
  "requireby": [
    {
      "name": "MappeaMapSupplierInput",
      "description": null,
      "url": "/mappea/reference/inputobjects/mappeamapsupplierinput"
    },
    {
      "name": "MappeaSupplierConfirmedInput",
      "description": null,
      "url": "/mappea/reference/inputobjects/mappeasupplierconfirmedinput"
    },
    {
      "name": "SupplierDetected",
      "description": null,
      "url": "/mappea/reference/objects/supplierdetected"
    },
    {
      "name": "Supplier",
      "description": null,
      "url": "/mappea/reference/objects/supplier"
    },
    {
      "name": "SupplierData",
      "description": null,
      "url": "/mappea/reference/objects/supplierdata"
    },
    {
      "name": "Node",
      "description": null,
      "url": "/mappea/reference/interfaces/node"
    },
    {
      "name": "Provider",
      "description": null,
      "url": "/mappea/reference/objects/provider"
    },
    {
      "name": "AccessFilter",
      "description": null,
      "url": "/mappea/reference/inputobjects/accessfilter"
    },
    {
      "name": "Organization",
      "description": null,
      "url": "/mappea/reference/objects/organization"
    },
    {
      "name": "ClientFilter",
      "description": null,
      "url": "/mappea/reference/inputobjects/clientfilter"
    },
    {
      "name": "System",
      "description": null,
      "url": "/mappea/reference/objects/system"
    },
    {
      "name": "AdviseMessage",
      "description": null,
      "url": "/mappea/reference/objects/advisemessage"
    },
    {
      "name": "Access",
      "description": null,
      "url": "/mappea/reference/objects/access"
    },
    {
      "name": "AccessData",
      "description": null,
      "url": "/mappea/reference/objects/accessdata"
    },
    {
      "name": "Parameter",
      "description": null,
      "url": "/mappea/reference/objects/parameter"
    },
    {
      "name": "Client",
      "description": null,
      "url": "/mappea/reference/objects/client"
    },
    {
      "name": "ClientData",
      "description": null,
      "url": "/mappea/reference/objects/clientdata"
    },
    {
      "name": "Group",
      "description": null,
      "url": "/mappea/reference/objects/group"
    },
    {
      "name": "SupplierFilter",
      "description": null,
      "url": "/mappea/reference/inputobjects/supplierfilter"
    },
    {
      "name": "GroupData",
      "description": null,
      "url": "/mappea/reference/objects/groupdata"
    },
    {
      "name": "Member",
      "description": null,
      "url": "/mappea/reference/objects/member"
    },
    {
      "name": "GroupCommonData",
      "description": null,
      "url": "/mappea/reference/interfaces/groupcommondata"
    },
    {
      "name": "MemberData",
      "description": null,
      "url": "/mappea/reference/objects/memberdata"
    },
    {
      "name": "MacroPermission",
      "description": null,
      "url": "/mappea/reference/objects/macropermission"
    },
    {
      "name": "MacroPermissionData",
      "description": null,
      "url": "/mappea/reference/objects/macropermissiondata"
    },
    {
      "name": "Role",
      "description": null,
      "url": "/mappea/reference/objects/role"
    },
    {
      "name": "Resource",
      "description": null,
      "url": "/mappea/reference/objects/resource"
    },
    {
      "name": "API",
      "description": null,
      "url": "/mappea/reference/objects/api"
    },
    {
      "name": "RoleData",
      "description": null,
      "url": "/mappea/reference/objects/roledata"
    },
    {
      "name": "ResourceData",
      "description": null,
      "url": "/mappea/reference/objects/resourcedata"
    },
    {
      "name": "APIData",
      "description": null,
      "url": "/mappea/reference/objects/apidata"
    },
    {
      "name": "Operation",
      "description": null,
      "url": "/mappea/reference/objects/operation"
    },
    {
      "name": "OperationData",
      "description": null,
      "url": "/mappea/reference/objects/operationdata"
    },
    {
      "name": "ManagedGroup",
      "description": null,
      "url": "/mappea/reference/objects/managedgroup"
    },
    {
      "name": "ManagedGroupData",
      "description": null,
      "url": "/mappea/reference/objects/managedgroupdata"
    },
    {
      "name": "Profile",
      "description": null,
      "url": "/mappea/reference/objects/profile"
    },
    {
      "name": "ProfileData",
      "description": null,
      "url": "/mappea/reference/objects/profiledata"
    },
    {
      "name": "Entity",
      "description": null,
      "url": "/mappea/reference/objects/entity"
    },
    {
      "name": "OrganizationData",
      "description": null,
      "url": "/mappea/reference/objects/organizationdata"
    },
    {
      "name": "Domain",
      "description": null,
      "url": "/mappea/reference/objects/domain"
    },
    {
      "name": "Product",
      "description": null,
      "url": "/mappea/reference/objects/product"
    },
    {
      "name": "ProductData",
      "description": null,
      "url": "/mappea/reference/objects/productdata"
    },
    {
      "name": "DomainData",
      "description": null,
      "url": "/mappea/reference/objects/domaindata"
    },
    {
      "name": "SystemData",
      "description": null,
      "url": "/mappea/reference/objects/systemdata"
    }
  ],
  "enumValues": null,
  "operator": "scalar",
  "typename": "ID",
  "hideGithubLink": true
}
The `ID` scalar type represents a unique identifier, often used to refetch an object or as key for a cache. The ID type appears in a JSON response as a String; however, it is not intended to be human-readable. When expected as an input type, any string (such as `"4"`) or integer (such as `4`) input value will be accepted as an ID.
## GraphQL schema definition

{{% graphql-schema-scalar %}}

## Required by

{{% graphql-require-by %}}
