+++
title = "Supplier, Access, Client and Context"
pagetitle = "Supplier, Access, Client and Context"
description = "Learn about entities used in HotelX"
icon = "fa-exchange"
weight = 1
alwaysopen = false
+++

Previously, we introduced an overarching definition of the main Core Entities applying to Travelgate-X APIs [core concepts that apply to all TravelgateX APIs](/getting-started/concepts/). 

Here, we want to dig in further on how those concepts are applied to Hotel-X API.

### Supplier

A party that supplies accommodation services through a Supplier API implementation. Each `Supplier` has a `Supplier` code. These are unique values and they are used consistently throughout all TravelgateX implementations. 

### Access

Accesses are displayed as numeric codes in Hotel-X and represent `Supplier` configurations for a given credential. Those configurations include:

* URLs 

* Credentials 

* Markets 

* Rate Types 

* Specific `Supplier` settings 

An access is used by just a client exclusively. The same supplier has different access depends on the number of clients connected to him, even if the configuration is almost the same.

### Client

A party that buys accommodation services through Hotel-X API implementation.`Client` codes are consistent throughout all TravelgateX implementations. These codes are used to identify the business that is making the request and to confirm that the business has a configuration assigned to it.

### Context

`Context` is the way how a client/supplier define hotel, board and room codes among others. Each `Profile` (either a `Buyer` or `Supplier`) can manage their own contexts or reuse existing ones. Different buyers or sellers can also manage the same codes context. For example, the `Supplier`[SmyRooms](https://app.travelgatex.com/network/smyrooms/) uses LOGI contexts for their implementations.

`Context` applies to:

* Hotel Codes 

* Board Codes 

* Room Codes 

With our built-in solution, you are able to use your own context when requesting a Hotel-X operation. If you are a `Buyer`, you can map your context against your `Seller`/Supplier contexts.

Should you be using the aggregator mode, we recommend that you use you own `Context`- in doing so, all supplier mappings will be solved/unified.

{{% alert theme="info" %}}For more information on setting contexts, check out our [Plugin guide on Mapping](https://docs.travelgatex.com/connectiontypesbuyers/hotel-x/plugins/mapping/).{{% /alert %}}
