+++
title = "Concepts"
pagetitle = ""
description = "Basic concepts for all of the TravelgateX platform"
icon = "fa-question-circle" 
weight = 3
alwaysopen = false
+++

The TravelgateX platform and APIs all use a consistent set of basic concepts so that whatever API you use on our platform, you can be confident that it will work with the same definitions as all of the others you are familiar with. 

**Here is an overview of the key concepts of our platform.**

## Access
An `Access` is a set of credentials and the authentication configuration that enables a `Buyer` to access a `Supplier`. To gain access, a `Buyer` needs to confirm with TravelgateX that they have an agreement in place with each `Supplier` with whom they want to integrate.

## API Gateway
Our API gateway is stable, secure, fault tolerant and load balanced between many datacenters from four different cloud providers: Microsoft Azure, Google Cloud Platform, Hetzner and TotalUptime. We provide realtime details of our uptime and status [on our Status page](http://status.travelgatex.com) and work at maintaining a minimum 99.99% service performance level.

Our API gateway provides a single GraphQL endpoint which can be used to make queries against all of our APIs and travel services. This makes it easier for your clients (websites, applications and any other interface) to only call for the exact data that is needed, without parsing a heap of extra information in each API call. (Check out our [GraphQL resources](/learning-graphql/) to learn more!)

## Profile
An `Organization` uses profiles to determine what type of interaction is required on TravelgateX. At present, profiles are either a `Buyer` or a `Seller`.

## Buyer
A `Buyer Profile` uses the TravelgateX platform to book travel services such as hotels for their customers. Buyers include online travel agents, tour operators, niche travel service providers, and travel and pricing apps.

## Seller
A `Seller Profile` uses the TravelgateX platform to sell travel services such as hotels for their customers. Sellers include tour operators, niche travel service providers..

## Organization
An `Organization` is made up of `Partners`, `Resources`, `Settings`, `Permissions` and other `Metadata`.

## Partner
A `Partner` interacts with the TravelgateX API platform. A partners can be a User (that is, a person) or a Service Account (that is, an application). A partner is a member of an Organization, and can be a member of mutiple organizations.

## Supplier
 A `Supplier` uses the TravelgateX platfrom to make travel services available to buyers. Suppliers can be suppliers with realtime databases of hotel room vacancies, tours, car rental providers, adventure and activity service suppliers, travel insurance providers or other travel industry service suppliers.

## Context
A `Context` refers to the `Supplier` codes the request is using. It's a way of specifiying which `Supplier` codes are being used so they can be transformed and standardized.

## Common Resources
`Common resources` define common objects that are consistent across all of our API products.

## HUB
`HUB` is the command center of the TravelgateX platform. All connections pass through the HUB.

## Product
A `Product` is a TravelgateX platform API which is available for the consumption of Resources. We organize our APIs by similarity and common features. Our HotelX API is our first product now available for use in production environments.

 {{% alert theme="info" %}}Join us on [Slack](https://slack.travelgatex.com/) to talk with us about how to use TravelgateX APIs in your websites, apps, and products. 
 You can also contact us via our [Help Center](https://landing.travelgatex.com/helpcenter). 

 If you would like any new features or more information in our documentation, head to [TGX Community](https://community.travelgatex.com/)
