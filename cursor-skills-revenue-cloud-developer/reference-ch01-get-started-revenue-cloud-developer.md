---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 1 — Get Started with Revenue Cloud Developer Resources

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 1 Get Started with Revenue Cloud Developer
Resources
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions
Get a single, unified system to automate your CRM processes. Use
the developer sources of Revenue Cloud to automate the backend
work to support the end-to-end revenue solution.
Revenue Cloud provides extensible and API-first business
components of the product-to-cash processes. Learn more about
the developer resources that are available for these components.
Product Catalog Management
Create and manage an entire product portfolio with components such as attributes, product classifications,
simple and bundled products, and rules.
• Use standard objects and fields to manage products, rules, and catalogs.
• Use business APIs to serve catalog definitions to users or applications.
• Use metadata API types to access and manage the metadata types, such as product specification
type and product specification record types.
• Use tooling API objects to retrieve and manage smaller pieces of metadata types through SOQL
capabilities. Use REST or SOAP to access metadata.
• Use Product Discovery business APIs, which are composite APIs, to search products or to discover
catalogs, products, and categories.
Salesforce Pricing
Create a reliable pricing solution for your users through customized price adjustment schedules. Get
accurate pricing for your entire product portfolio.
• Use standard objects and fields to manage pricing processes such as product management, and the
calculation and application of discounts.
• Use business APIs to get unified pricing experiences across product lines.
• Use invocable actions to invoke the pricing Connect API by providing the pricing, context, and price
waterfall details.
• Use metadata API types to work with the metadata associated with Flows and Salesforce Pricing
settings.
1

===== PAGE 16 =====

• Use tooling API objects to retrieve and manage smaller pieces of metadata types through SOQL
capabilities such as pricing action parameters, pricing procedure output map, and pricing recipe
details. Use REST or SOAP to access metadata.
Product Configurator
Customize the components and attributes of a product to meet the business requirement expectations.
• Use standard objects to manage product-related information.
• Use the business APIs to retrieve and update a product’s configuration from a configurator or to
access configurator capabilities by integrating with any front-end application.
• Use constraint modeling language on page 988 to enforce business logic declaratively, without the
need for extensive code in a general-purpose programming language.
Transaction Management
Manage subscription lifecycles from quotes and orders to contracts, assets, amendments, and renewals.
Get insights into customer assets and see a consolidated list of all assets that belong to an account.
• Use standard objects and fields to manage transactions and details of a customer asset. Use the
QuoteSaveEvent platform event to notify subscribers after saving of a quote is processed.
• Use business APIs to place, clone, or supplement a sales transaction. You can also initiate amendment,
renewal, or cancellation of assets by using APIs.
• Use invocable actions to create and activate an order from a quote, or to initiate amendment, renewal,
or cancellation of assets through invocable actions.
• Use metadata API types to work with the metadata associated with Flows.
• Use built-in Apex classes and interfaces grouped by namespace.
Usage Management
Ensure transparent, accurate, and efficient management of usage data and estimated usage amount.
• Use standard objects and fields to set up and manage consumption of usage-based products.
• Use metadata API types to work with the metadata associated with Usage Management.
• Use business APIs to get details of a usage-based product that’s associated with an asset, an order
item, or a quote line item.
• Use invocable actions to invoke usage summaries, process consumption overages, and refresh usage
entitlements.
Rate Management
Quote and price products based on predefined rates for future use of the product or service.
• Use standard objects and fields to manage rates and discounts for a product's resource consumption.
• Use metadata API types to work with the metadata associated with Rate Management settings.
• Use business APIs to get details of a rate plan and persisted rating waterfall.
2
Get Started with Revenue Cloud Developer Resources

===== PAGE 17 =====

• Use invocable action to invoke the rating service to rate the usage records.
Dynamic Revenue Orchestrator
Get visibility into a product’s fulfillment journey. Also, get a view of the entire fulfillment design processes.
• Use standard objects to manage details of a product’s fulfillment.
• Use invocable actions to submit an order or a sales transaction to Dynamic Revenue Orchestrator
for fulfillment.
• Use metadata API types to work with the metadata associated with Flows.
• Use callout step types to make HTTP calls to an external system.
Billing
Get an integrated and extensible subscription and usage-based billing solution. Automate processes
such as payment processing, invoice generation, and usage-based billing.
• Use standard objects to manage billing and tax configurations, credit memos, and invoices.
• Use platform events types to know more about standard platform events.
• Use invocable actions to manage credit application, billing schedules, and invoices.
• Use business APIs to manage credit application and to handle billing scenarios.
• Use built-in Apex classes to access the same capabilities that are available in the Billing Business
APIs.
• Use metadata API types to work with the metadata associated with Billing settings and Flows.
See the RevenueManagementSettings on page 4 metadata type to set up Revenue Cloud through
configuration settings.
SEE ALSO:
Business Rules Engine
Context Service
Salesforce Contracts
3
Get Started with Revenue Cloud Developer Resources

===== PAGE 18 =====

