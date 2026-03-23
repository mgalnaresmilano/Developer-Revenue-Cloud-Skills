---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 7 — Product Configurator

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 7 Product Configurator
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions of Revenue Cloud
where Product Configurator
is enabled
Customize the components and attributes of a product to align
with specific business requirements.
In this chapter ...
• Product Configurator
Standard Objects
• Product Configurator
Business APIs
• Product Configurator
Standard Invocable
Actions
• Product Configurator
Metadata API Types
• Constraint Modeling
Language
870

===== PAGE 885 =====

Product Configurator Standard Objects
The Product Configurator data model provides objects and fields to manage the product configurator flow.
ExpressionSetConstraintObj
Represents the association between a Product object and the constraint model tags defined in a given constraint model. This object
is available in API version 63.0 and later.
ProductConfigurationFlow
Specifies the many-to-many relationship between Product Classification, Product, and Flow Definition objects. The flow definition
is used to configure standalone and bundled products of a specific product classification along with the product attributes, quantities,
and product selling models. This object is available in API version 60.0 and later.
ProductConfigFlowAssignment
A junction object that represents the many-to-many relationship between Product Configuration Flow, Product, and Product
Classification. This object is available in API version 60.0 and later.
ProductConfigurationRule
Represents the validation, inclusion, and exclusion rules for products in the context of the selling process. The selling process can
be quoting, configuration, or ordering. This object is available in API version 61.0 and later.
SEE ALSO:
Object Reference for the Salesforce Platform: Overview of Salesforce Objects and Fields
SOAP API Developer Guide: Introduction to SOAP API
ExpressionSetConstraintObj
Represents the association between a Product object and the constraint model tags defined in a given constraint model. This object is
available in API version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Special Access Rules
This object is available in orgs where Revenue Cloud is enabled.
Fields
DetailsField
Type
string
ConstraintModelTag
Properties
Create, Filter, Group, Sort, Update
871
Product Configurator Standard ObjectsProduct Configurator

===== PAGE 886 =====

DetailsField
Description
The product tag that is defined in the constraint model, for example, Laptop.
Type
picklist
ConstraintModelTagType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of the product tag that is defined in the constraint model.
Possible values are:
• Port
• Type
The default value is Type.
Type
reference
ExpressionSetId
Properties
Create, Filter, Group, Sort, Update
Description
The expression set associated with the expression set constraint object.
This field is a relationship field.
Relationship Name
ExpressionSet
Refers To
ExpressionSet
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The timestamp when the current user last accessed this record, a record related to this record,
or a list view.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp when the current user last viewed this record or list view. If this value is null,
the user accessed this record or list view (LastReferencedDate) but didn’t view it.
872
ExpressionSetConstraintObjProduct Configurator

===== PAGE 887 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the expression set constraint.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
For internal use only.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
ReferenceObjectId
Properties
Create, Filter, Group, Sort, Update
Description
The object associated with the expression set constraint object.
This field is a polymorphic relationship field.
Relationship Name
ReferenceObject
Refers To
Product2, ProductClassification, ProductRelatedComponent
ProductConfigurationFlow
Specifies the many-to-many relationship between Product Classification, Product, and Flow Definition objects. The flow definition is
used to configure standalone and bundled products of a specific product classification along with the product attributes, quantities,
and product selling models. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
873
ProductConfigurationFlowProduct Configurator

===== PAGE 888 =====

Fields
DetailsField
Type
string
FlowIdentifier
Properties
Create, Filter, Group, Sort, Update
Description
Stores the flow API name.
Type
Boolean
IsDefault
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates the default configurator flow.
The default value is false.
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Indicates the status of the product configuration flow. Possible values include Draft, Active,
and Inactive
Possible values are:
• Active
• Draft
• Inactive
The default value is Draft.
ProductConfigFlowAssignment
A junction object that represents the many-to-many relationship between Product Configuration Flow, Product, and Product Classification.
This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
874
ProductConfigFlowAssignmentProduct Configurator

===== PAGE 889 =====

Fields
DetailsField
Type
picklist
AssignmentType
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether the Product Configuration Flow is assigned to the primary product or
classification, or to dynamic components added within a bundle.
Valid values are:
• DynamicAdditionFlow
• PrimaryConfiguratorFlow
The default value is PrimaryConfiguratorFlow. Available in API version 65.0 and
later.
Type
reference
ProductClassificationId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product classification associated with the Product Configuration Flow.
This field is a relationship field.
Relationship Name
ProductClassification
Relationship Type
Lookup
Refers To
ProductClassification
Type
reference
ProductConfigurationFlowId
Properties
Create, Filter, Group, Sort
Description
The Product Configuration Flow associated with the Product Classification or Product.
This field is a relationship field.
Relationship Name
ProductConfigurationFlow
Relationship Type
Lookup
875
ProductConfigFlowAssignmentProduct Configurator

===== PAGE 890 =====

DetailsField
Refers To
ProductConfigurationFlow
Type
reference
ProductId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product associated with the Product Configuration Flow.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
ProductConfigurationRule
Represents the validation, inclusion, and exclusion rules for products in the context of the selling process. The selling process can be
quoting, configuration, or ordering. This object is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
ApiName
Properties
Filter, Group, Nillable, Sort
Description
Type
textarea
ConfigurationRuleDefinition
Properties
Create, Nillable, Update
876
ProductConfigurationRuleProduct Configurator

===== PAGE 891 =====

DetailsField
Description
The configuration rule criteria and actions.
Type
string
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The description of the configuration rule.
Type
dateTime
EffectiveFromDate
Properties
Filter, Nillable, Sort
Description
The date and time from which the configuration rules comes into effect.
Type
dateTime
EffectiveToDate
Properties
Filter, Nillable, Sort
Description
The date and time to which the configuration rules ceases to be in effect.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the configuration rule record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the configuration rule record was last viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
877
ProductConfigurationRuleProduct Configurator

===== PAGE 892 =====

DetailsField
Description
The name of the configuration rule.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the configuraion rule owner.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
picklist
ProcessScope
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The scope of the configuration rule.
Possible values are:
• Bundle
• Product
The default value is Product.
Type
picklist
RuleSubType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The segregation of products into subsets such that the configuration rules only apply to the
products that fall under the ambit of the selected rule subtype.
Possible values are:
• BundleProduct
• BundleProductClassification
• Product
• ProductClassification
878
ProductConfigurationRuleProduct Configurator

===== PAGE 893 =====

DetailsField
The default value is Product.
Type
picklist
RuleType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Indicates the industry vertical or the feature of the industry vertical that’s using the
configuration rule.
Possible values are:
• Configurator
• Promotions
The default value is Configurator.
Type
int
Sequence
Properties
Filter, Group, Nillable, Sort
Description
Indicates the order for executing the configuration rule. Rules with lower numbers run first
when multiple rules are triggered at once.
Type
picklist
Status
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort
Description
The lifecycle status of the configuration rule.
Possible values are:
• Active
• Draft
• Inactive
The default value is Draft.
Product Configurator Business APIs
Use the Product Configurator Business APIs to customize a product or a service according to your business-specific requirements.
Perform product configuration-related operations by using the Product Configurator Business APIs. Integrate these APIs with any front-end
application to access the configurator capabilities.
879
Product Configurator Business APIsProduct Configurator

===== PAGE 894 =====

This table lists the available Product Configurator resources.
DescriptionResource
Retrieve and update a product’s
configuration from a
/connect/cpq/configurator/actions/configure (POST)
configurator. Execute
configuration rules and notify
users of any violations for
changes to product bundle,
attributes, or product quantity
within a bundle. Additionally,
get pricing details for the
configured bundle.
Create a session for the product
configuration instance using the
/connect/cpq/configurator/actions/load-instance (POST)
transaction ID. Get the session
ID that includes the results of
actions, such as configuration
rules, qualification rules, and
pricing management.
Set a product configuration
instance. This API is used in
/connect/cpq/configurator/actions/set-instance (POST)
scenarios where the
configuration instance is
available in a different database
than Salesforce and the product
catalog management data is in
Salesforce.
Fetch the JSON representation
of a product configuration. Use
/connect/cpq/configurator/actions/get-instance (POST)
the response to display the
details of the product
configuration instance on the
Salesforce user interface, or save
the product configuration
instance to an external system.
Save a configuration instance
after a successful product
configuration.
/connect/cpq/configurator/actions/save-instance (POST)
Set the quantity of a product
through the runtime system.
/connect/cpq/configurator/actions/set-product-quantity (POST)
Add a node to the context
through the runtime system
/connect/cpq/configurator/actions/add-nodes (POST)
without using the Salesforce
user interface.
880
Product Configurator Business APIsProduct Configurator

===== PAGE 895 =====

DescriptionResource
Update nodes in a product
configuration.
/connect/cpq/configurator/actions/update-nodes (POST)
Delete nodes from a product
configuration.
/connect/cpq/configurator/actions/delete-nodes (POST)
Resources
Learn more about the available Product Configurator API resources.
Request Bodies
Learn more about the available Product Configurator API request bodies.
Response Bodies
Learn more about the available Product Configurator API response bodies.
SEE ALSO:
Connect REST API Developer Guide: Introduction
Salesforce Help: Product Configurator Permissions
Resources
Learn more about the available Product Configurator API resources.
Configuration (POST)
Retrieve and update a product’s configuration from a configurator. Execute configuration rules and notify users of any violations for
changes to product bundle, attributes, or product quantity within a bundle. Additionally, get pricing details for the configured bundle.
Saved Configuration (GET, POST)
Save and reuse a record's configurations, and get a list of the saved configurations for a record.
Saved Configuration (DELETE, PUT)
Update or delete a record's saved configuration by using the configuration ID.
Configuration Get Instance (POST)
Fetch the JSON representation of a product configuration. Use the response to display the details of the product configuration
instance on the Salesforce user interface, or save the product configuration instance to an external system.
Configuration Load Instance (POST)
Create a session for the product configuration instance using the transaction ID. Get the session ID that includes the results of actions,
such as configuration rules, qualification rules, and pricing management.
Configuration Save Instance (POST)
Save a configuration instance after a successful product configuration.
Configuration Set Instance (POST)
Set a product configuration instance. This API is used in scenarios where the configuration instance is available in a different database
than Salesforce and the product catalog management data is in Salesforce.
Configurator Add Nodes (POST)
Add a node to the context through the runtime system without using the Salesforce user interface.
881
ResourcesProduct Configurator

===== PAGE 896 =====

Configurator Delete Nodes (POST)
Delete nodes from a product configuration.
Configurator Update Nodes (POST)
Update nodes in a product configuration.
Product Set Quantity (POST)
Set the quantity of a product through the runtime system.
Configuration (POST)
Retrieve and update a product’s configuration from a configurator. Execute configuration rules and notify users of any violations for
changes to product bundle, attributes, or product quantity within a bundle. Additionally, get pricing details for the configured bundle.
Resource
/connect/cpq/configurator/actions/configure
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/configure
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
This example shows a sample to initiate a context based on a transaction ID.
{
"transactionLineId": "0QLDE000000IBXw4AO",
"transactionId": "0Q0xx0000000001GAA",
"correlationId": "c95246d4-102c-4ecd-a263-f74ac525d1e5",
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
This example shows a sample to add, update, or delete a node in an existing context.
{
"transactionLineId": "0QLDE000000IBXw4AO",
"transactionId": "0Q0DE000000ISHJs81",
"correlationId": "c95246d4-102c-4ecd-a263-f74ac525d1e5",
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
882
ResourcesProduct Configurator

===== PAGE 897 =====

"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"contextResponseType": "Full",
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"transactionContextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"addedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "sti2_id"],
"addedObject": {
"id": "ref_sti2_id",
"SalesTransactionSource": "sti2_id",
"PricebookEntry": "01uxx0000000001AAA",
"ProductSellingModel": "0jPxx0000000001AAA",
"businessObjectType": "QuoteLineItem",
"Quantity": 10,
"UnitPrice": 2.0,
"Product": "01txx0000000001AAA"
}
},
{
"path": ["0Q0DE000000ISHJs81", "ref_sti2_id","ref_stir1_id"],
"addedObject": {
"id": "ref_stir1_id",
"businessObjectType": "QuoteLineItemRelationship",
"MainItem": "0QLDE000000IBXw4AO",
"AssociatedItem": "ref_sti2_id",
"ProductRelatedComponent": "0dSxx0000000001AAA",
"ProductRelationshipType": "0yoxx0000000001AAA",
"AssociatedItemPricing": "IncludedInBundlePrice"
}
}
],
"updatedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"],
"updatedAttributes": {
"Quantity": 5
}
}
],
"deletedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"]
}
]
}
883
ResourcesProduct Configurator

===== PAGE 898 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of added context nodes that’s passed
to the product configurator.
Configurator
Added Node
Input[]
addedNodes
60.0OptionalOptions to pass to the configurator.Configurator
Options Input[]
configurator
Options
65.0Required for large
sales transactions
Specifies the type of transaction context
response. Valid values are:
Stringcontext
ResponseType
with more than
• Delta—Returns the sales
transaction items that are added or
updated.
1000 line items and
less than 15K line
items.
• Full—Returns all sales transaction
items in a transaction.
• None—Returns empty transaction
context response.
• Product—Returns the sales
transaction items related to the
product that's being configured.
60.0OptionalID that’s specified for traceability of logs.Stringcorrelation
Id
60.0OptionalList of deleted context nodes that’s
passed to the product configurator.
Configurator
Deleted Node
Input[]
deletedNodes
60.0OptionalDetails such as account ID, contact ID,
and context ID that are used for
executing qualification rules.
User Context
Input[]
qualification
Context
60.0OptionalID of the transaction context.Stringtransaction
ContextId
60.0RequiredID of the sales transaction that’s being
configured such as a quote or an order.
Stringtransaction
Id
60.0OptionalID of the top-level line item that’s being
configured.
Stringtransaction
LineId
60.0OptionalList of updated context nodes that’s
passed to the product configurator.
Configurator
Updated Node
Input[]
updatedNodes
884
ResourcesProduct Configurator

===== PAGE 899 =====

Response body for POST
Configuration Details
Saved Configuration (GET, POST)
Save and reuse a record's configurations, and get a list of the saved configurations for a record.
Resource
/connect/cpq/configurator/saved-configuration
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/saved-configuration
Available version
63.0
HTTP methods
GET, POST
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0RequiredID of the record whose saved
configurations must be retrieved.
StringreferenceRecordId
Response body for GET
Configuration List
Request body for POST
JSON example
{
"data":
"{&quot;LegalEntity&quot;:null,&quot;ProductName&quot;:&quot;Monitor&quot;,&quot;businessObjectType&quot;:&quot;QuoteLineItem&quot;,&quot;Product&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;ItemIsPrimarySegment&quot;:false,&quot;ListPrice&quot;:144.99,&quot;ValidationResult&quot;:null,&quot;StartDate&quot;:null,&quot;ContractVolumePasId&quot;:null,&quot;BillingTreatment&quot;:null,&quot;PeriodBoundaryStartMonth&quot;:null,&quot;SalesTransactionSourceAsset&quot;:null,&quot;id&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;PartnerDiscountPercent&quot;:10,&quot;PriceWaterFall&quot;:null,&quot;BillingFrequency&quot;:null,&quot;ProductCode&quot;:&quot;MO001&quot;,&quot;DerivedPricingAttribute&quot;:false,&quot;TaxTreatment&quot;:null,&quot;Subtotal&quot;:1739.88,&quot;ItemRampIdentifier&quot;:null,&quot;ItemSegmentName&quot;:null,&quot;SalesTransactionItemAttribute&quot;:[{&quot;AttributeKey&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;AttributeValue&quot;:&quot;1080p
Built-in
Display&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx0000000001AAA&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display&quot;,&quot;id&quot;:&quot;0zuxx000000000FAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;},{&quot;AttributeKey&quot;:&quot;0tjxx0000000009AAA&quot;,&quot;AttributeValue&quot;:&quot;24
Inch&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx000000000GAAQ&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display_Size&quot;,&quot;id&quot;:&quot;0zuxx000000000GAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;}],&quot;PricebookEntry&quot;:&quot;01uxx0000008yX0AAI&quot;,&quot;DiscountAmount&quot;:null,&quot;PricingTermCount&quot;:0,&quot;SubscriptionTermUnit&quot;:null,&quot;NetUnitPrice&quot;:144.99,&quot;ItemEffectiveGrantDate&quot;:null,&quot;ProductCategory&quot;:null,&quot;SalesTransactionAction&quot;:null,&quot;SalesTransactionActionType&quot;:null,&quot;SalesTransactionItemGroup&quot;:null,&quot;PeriodBoundaryDay&quot;:null,&quot;SalesTrxnItemDescription&quot;:null,&quot;LineItemDistributionType&quot;:null,&quot;ProrationPolicy&quot;:null,&quot;ContractDiscountType&quot;:null,&quot;TransactionType&quot;:null,&quot;ParentReference&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Discount&quot;:null,&quot;PricingTermUnit&quot;:null,&quot;ProductSellingModel&quot;:&quot;0jPxx0000000001EAA&quot;,&quot;PricingSource&quot;:null,&quot;StockKeepingUnit&quot;:null,&quot;PartnerUnitPrice&quot;:130.491,&quot;ItemTotalAdjustmentAmount&quot;:0,&quot;SalesTransactionItemSource&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;ContractAttributePasId&quot;:null,&quot;SubscriptionTerm&quot;:null,&quot;SellingModelType&quot;:&quot;OneTime&quot;,&quot;EndQuantity&quot;:12,&quot;NetTotalPrice&quot;:1739.88,&quot;TotalLineAmount&quot;:1739.88,&quot;ItemSegmentType&quot;:null,&quot;ProductBasedOn&quot;:&quot;11Bxx000002C1nqEAC&quot;,&quot;Deleted&quot;:false,&quot;BillingReference&quot;:null,&quot;ArePartialPeriodsAllowed&quot;:false,&quot;ItemRecordedPrice&quot;:null,&quot;CustomProductName&quot;:null,&quot;ItemSegmentIdentifier&quot;:null,&quot;SalesTransactionItemParent&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Quantity&quot;:12,&quot;PeriodBoundary&quot;:null,&quot;ContractDiscountValue&quot;:null,&quot;LineItemDiscountValue&quot;:null,&quot;ContractId&quot;:null,&quot;EndDate&quot;:null,&quot;ItemGroupSummarySubtotal&quot;:null,&quot;IsContracted&quot;:false,&quot;UnitPrice&quot;:144.99,&quot;StartQuantity&quot;:null,&quot;ContractPrice&quot;:null,&quot;TotalPrice&quot;:1739.88,&quot;LineItemDiscountType&quot;:null,&quot;ItemPath&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;productKey&quot;:[&quot;0QLxx0000004C9VGAU&quot;]}",
"description": "This configuration is saved for reuse.",
"name": "Favorite Configuration",
"referenceRecordId": "01txx0000006iCFAAY"
}
885
ResourcesProduct Configurator

===== PAGE 900 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalJSON object that contains the details of
the sales transaction, formatted as a
string.
Stringdata
63.0OptionalDescription of the saved configuration.Stringdescription
63.0OptionalName of the saved configuration.Stringname
63.0RequiredID of the record for which the
configuration must be saved.
StringreferenceRecord
Id
Response body for POST
Configuration Record Save
SEE ALSO:
Salesforce Help: Considerations to Save and Reuse Configurations
Saved Configuration (DELETE, PUT)
Update or delete a record's saved configuration by using the configuration ID.
Resource
/connect/cpq/configurator/saved-configuration/id
The id  parameter is the ID of the configuration that you want to update or delete.
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/saved-configuration/5KPxx0025063GSmSAX
Available version
63.0
HTTP methods
DELETE, PUT
Request body for PUT
JSON example
{
"data":
"{&quot;LegalEntity&quot;:null,&quot;ProductName&quot;:&quot;Monitor&quot;,&quot;businessObjectType&quot;:&quot;QuoteLineItem&quot;,&quot;Product&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;ItemIsPrimarySegment&quot;:false,&quot;ListPrice&quot;:144.99,&quot;ValidationResult&quot;:null,&quot;StartDate&quot;:null,&quot;ContractVolumePasId&quot;:null,&quot;BillingTreatment&quot;:null,&quot;PeriodBoundaryStartMonth&quot;:null,&quot;SalesTransactionSourceAsset&quot;:null,&quot;id&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;PartnerDiscountPercent&quot;:10,&quot;PriceWaterFall&quot;:null,&quot;BillingFrequency&quot;:null,&quot;ProductCode&quot;:&quot;MO001&quot;,&quot;DerivedPricingAttribute&quot;:false,&quot;TaxTreatment&quot;:null,&quot;Subtotal&quot;:1739.88,&quot;ItemRampIdentifier&quot;:null,&quot;ItemSegmentName&quot;:null,&quot;SalesTransactionItemAttribute&quot;:[{&quot;AttributeKey&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;AttributeValue&quot;:&quot;1080p
Built-in
Display&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx0000000001AAA&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display&quot;,&quot;id&quot;:&quot;0zuxx000000000FAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;},{&quot;AttributeKey&quot;:&quot;0tjxx0000000009AAA&quot;,&quot;AttributeValue&quot;:&quot;24
Inch&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx000000000GAAQ&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display_Size&quot;,&quot;id&quot;:&quot;0zuxx000000000GAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;}],&quot;PricebookEntry&quot;:&quot;01uxx0000008yX0AAI&quot;,&quot;DiscountAmount&quot;:null,&quot;PricingTermCount&quot;:0,&quot;SubscriptionTermUnit&quot;:null,&quot;NetUnitPrice&quot;:144.99,&quot;ItemEffectiveGrantDate&quot;:null,&quot;ProductCategory&quot;:null,&quot;SalesTransactionAction&quot;:null,&quot;SalesTransactionActionType&quot;:null,&quot;SalesTransactionItemGroup&quot;:null,&quot;PeriodBoundaryDay&quot;:null,&quot;SalesTrxnItemDescription&quot;:null,&quot;LineItemDistributionType&quot;:null,&quot;ProrationPolicy&quot;:null,&quot;ContractDiscountType&quot;:null,&quot;TransactionType&quot;:null,&quot;ParentReference&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Discount&quot;:null,&quot;PricingTermUnit&quot;:null,&quot;ProductSellingModel&quot;:&quot;0jPxx0000000001EAA&quot;,&quot;PricingSource&quot;:null,&quot;StockKeepingUnit&quot;:null,&quot;PartnerUnitPrice&quot;:130.491,&quot;ItemTotalAdjustmentAmount&quot;:0,&quot;SalesTransactionItemSource&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;ContractAttributePasId&quot;:null,&quot;SubscriptionTerm&quot;:null,&quot;SellingModelType&quot;:&quot;OneTime&quot;,&quot;EndQuantity&quot;:12,&quot;NetTotalPrice&quot;:1739.88,&quot;TotalLineAmount&quot;:1739.88,&quot;ItemSegmentType&quot;:null,&quot;ProductBasedOn&quot;:&quot;11Bxx000002C1nqEAC&quot;,&quot;Deleted&quot;:false,&quot;BillingReference&quot;:null,&quot;ArePartialPeriodsAllowed&quot;:false,&quot;ItemRecordedPrice&quot;:null,&quot;CustomProductName&quot;:null,&quot;ItemSegmentIdentifier&quot;:null,&quot;SalesTransactionItemParent&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Quantity&quot;:12,&quot;PeriodBoundary&quot;:null,&quot;ContractDiscountValue&quot;:null,&quot;LineItemDiscountValue&quot;:null,&quot;ContractId&quot;:null,&quot;EndDate&quot;:null,&quot;ItemGroupSummarySubtotal&quot;:null,&quot;IsContracted&quot;:false,&quot;UnitPrice&quot;:144.99,&quot;StartQuantity&quot;:null,&quot;ContractPrice&quot;:null,&quot;TotalPrice&quot;:1739.88,&quot;LineItemDiscountType&quot;:null,&quot;ItemPath&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;productKey&quot;:[&quot;0QLxx0000004C9VGAU&quot;]}",
"description": "This configuration is updated.",
886
ResourcesProduct Configurator

===== PAGE 901 =====

"name": "Updated Configuration"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredJSON object that contains the details of
the sales transaction, formatted as a
string.
Stringdata
63.0RequiredDescription of the configuration.Stringdescription
63.0RequiredName of the configuration.Stringname
Response body for PUT
Configuration Update
SEE ALSO:
Salesforce Help: Considerations to Save and Reuse Configurations
Configuration Get Instance (POST)
Fetch the JSON representation of a product configuration. Use the response to display the details of the product configuration instance
on the Salesforce user interface, or save the product configuration instance to an external system.
Resource
/connect/cpq/configurator/actions/get-instance
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/get-instance
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77"
}
887
ResourcesProduct Configurator

===== PAGE 902 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredTransaction context ID of the product
configuration instance that’s to be
fetched.
StringcontextId
Response body for POST
Configuration Get Instance
Configuration Load Instance (POST)
Create a session for the product configuration instance using the transaction ID. Get the session ID that includes the results of actions,
such as configuration rules, qualification rules, and pricing management.
Resource
/connect/cpq/configurator/actions/load-instance
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/load-instance
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"configuratorOptions":
{
"addDefaultConfiguration": true,
"executeConfigurationRules": true,
"executePricing": true,
"qualifyAllProductsInTransaction": true,
"validateAmendRenewCancel": true,
"validateProductCatalog": true
},
"qualificationContext": {
"accountId": "001DU000001nHUGYA2"
},
"transactionId": "0Q0DU0000000XoN0AU"
}
888
ResourcesProduct Configurator

===== PAGE 903 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configurator options to
execute.
Configurator
Options Input
configurator
Options
60.0OptionalID of the context mapping record.Stringcontext
MappingId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
60.0RequiredTransaction ID of the header entity that’s
used to create a session. For example, a
Quote or an Order.
Stringtransaction
Id
Response body for POST
Configuration Load Instance
Configuration Save Instance (POST)
Save a configuration instance after a successful product configuration.
Use the Configuration Save Instance API to save the changes to the source after a successful configuration. For example, save changes
to the quote line item of a product, which is the source used to load the configuration.
Resource
/connect/cpq/configurator/actions/save-instance
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/save-instance
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77"
}
889
ResourcesProduct Configurator

===== PAGE 904 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredTransaction context ID of the product
configuration instance that’s to be saved.
StringcontextId
Response body for POST
Configuration Save Instance
Configuration Set Instance (POST)
Set a product configuration instance. This API is used in scenarios where the configuration instance is available in a different database
than Salesforce and the product catalog management data is in Salesforce.
Resource
/connect/cpq/configurator/actions/set-instance
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/set-instance
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"configuratorOptions": {
"addDefaultConfiguration": true,
"executeConfigurationRules": true,
"executePricing": false,
"qualifyAllProductsInTransaction": false,
"validateAmendRenewCancel": false,
"validateProductCatalog": false
},
"contextMappingId": "11jEk000017YdyUIAS",
"qualificationContext": {
"accountId": "001DU000001nHUGYA2"
},
"transaction":
"{\"Quote\":[{\"QuoteLineItem\":[{\"businessObjectType\":\"QuoteLineItem\",\"id\":\"qli_1\"},{\"businessObjectType\":\"QuoteLineItem\",\"id\":\"qli_2\"},{\"businessObjectType\":\"QuoteLineItem\",\"id\":\"qli_3\"},{\"businessObjectType\":\"QuoteLineItem\",\"id\":\"qli_4\"}],\"businessObjectType\":\"Quote\",\"id\":\"aJSdm0000003m3JGAQ\"}]}"
}
890
ResourcesProduct Configurator

===== PAGE 905 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configurator options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context mapping record.Stringcontext
MappingId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
60.0RequiredTransaction JSON payload representing
an object in an external system that’s
used to create a session.
Stringtransaction
Response body for POST
Configuration Set Instance
Configurator Add Nodes (POST)
Add a node to the context through the runtime system without using the Salesforce user interface.
Resource
/connect/cpq/configurator/actions/add-nodes
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/add-nodes
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
891
ResourcesProduct Configurator

===== PAGE 906 =====

"contactId": "003xx00000000D7AAI"
},
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"addedNodes": [
{
"path": [
"0Q0xx0000004EvcCAE",
"ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589"
],
"addedObject": {
"id": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"SalesTransactionItemSource": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"SalesTransactionItemParent": "0Q0xx0000004EvcCAE",
"PricebookEntry": "01uxx00000090VuAAI",
"ProductSellingModel": "0jPxx00000001KHEAY",
"UnitPrice": 15.26,
"Quantity": 1,
"Product": "01txx0000006lfHAAQ",
"businessObjectType": "QuoteLineItem"
}
},
{
"path": [
"0Q0xx0000004EvcCAE",
"ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"ref_d85b036d_d305_4bb6_aba8_a1dff645a664"
],
"addedObject": {
"id": "ref_d85b036d_d305_4bb6_aba8_a1dff645a664",
"MainItem": "0QLxx0000004QdRGAU",
"AssociatedItem": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"ProductRelatedComponent": "0dSxx00000001p6EAA",
"ProductRelationshipType": null,
"AssociatedItemPricing": "NotIncludedInBundlePrice",
"AssociatedQuantScaleMethod": "Proportional",
"businessObjectType": "QuoteLineRelationship"
}
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredList of the nodes to be added.Configurator
Added Node
Input[]
addedNodes
60.0OptionalList of the configuration options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context object that’s being
considered.
StringcontextId
892
ResourcesProduct Configurator

===== PAGE 907 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
Response body for POST
Configurator Add Nodes
Configurator Delete Nodes (POST)
Delete nodes from a product configuration.
Resource
/connect/cpq/configurator/actions/delete-nodes
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/delete-nodes
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"deletedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"]
}
]
}
893
ResourcesProduct Configurator

===== PAGE 908 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configuration options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context object that’s being
considered.
StringcontextId
60.0RequiredList of the nodes to be deleted.Configurator
Deleted Node
Input[]
deletedNodes
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
Response body for POST
Configurator Delete Nodes
Configurator Update Nodes (POST)
Update nodes in a product configuration.
Resource
/connect/cpq/configurator/actions/update-nodes
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/update-nodes
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
894
ResourcesProduct Configurator

===== PAGE 909 =====

"contactId": "003xx00000000D7AAI"
},
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"updatedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"],
"updatedAttributes": {
"Quantity": 5
}
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configuration options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context object that’s being
considered.
StringcontextId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
60.0RequiredList of the nodes to be updated.Configurator
Updated Node
Input[]
updatedNodes
Response body for POST
Configurator Update Nodes
Product Set Quantity (POST)
Set the quantity of a product through the runtime system.
Resource
/connect/cpq/configurator/actions/set-product-quantity
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/configurator/actions/set-product-quantity
Available version
60.0
HTTP methods
POST
895
ResourcesProduct Configurator

===== PAGE 910 =====

Request body for POST
JSON example
{
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"quantity": 20,
"transactionLinePath": "Quote.QuoteLineItem.Quantity"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configuration options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context object that’s being
considered.
StringcontextId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
60.0RequiredValue of the product quantity.Integerquantity
60.0RequiredPath to the line item where the update
to the quantity is applied. For example,
Quote.QuoteLineItem.Quantity.
String[]transaction
LinePath
Response body for POST
Product Quantity Set Configurator
Request Bodies
Learn more about the available Product Configurator API request bodies.
Configuration Get Instance Input
Input representation of the request to get a product configuration instance.
896
Request BodiesProduct Configurator

===== PAGE 911 =====

Configuration Load Instance Input
Input representation of the request to load a product configuration instance.
Configuration Save Input
Input representation of the details to save a configuration.
Configuration Update Input
Input representation of the details to update a configuration.
Configuration Save Instance Input
Input representation of the request to save a product configuration instance.
Configuration Set Instance Input
Input representation of the request to set a product configuration instance.
Configurator Add Nodes Input
Input representation of the request to add nodes within a root node.
Configurator Added Node Input
Input representation of the nodes to be added to a product configuration.
Configurator Delete Nodes Input
Input representation of the request to delete nodes from a product configuration.
Configurator Deleted Node Input
Input representation of the nodes to be deleted from a product configuration.
Configurator Input
Input representation of the request to modify the product configuration.
Configurator Options Input
Input representation of the request to get the product configuration options that’s passed to the configurator.
Configurator Update Nodes Input
Input representation of the request to update the nodes in a product configuration.
Configurator Updated Node Input
Input representation of the nodes to be updated in a product configuration.
Product Quantity Set Configurator Input
Input representation of the request to set the quantity of a product.
User Context Input
Input representation of the request to get the context details of a user, which are used for qualification rules.
Configuration Get Instance Input
Input representation of the request to get a product configuration instance.
JSON example
{
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77"
}
897
Request BodiesProduct Configurator

===== PAGE 912 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredTransaction context ID of the product
configuration instance that’s to be fetched.
StringcontextId
Configuration Load Instance Input
Input representation of the request to load a product configuration instance.
JSON example
{
"configuratorOptions":
{
"addDefaultConfiguration": true,
"executeConfigurationRules": true,
"executePricing": true,
"qualifyAllProductsInTransaction": true,
"validateAmendRenewCancel": true,
"validateProductCatalog": true
},
"qualificationContext": {
"accountId": "001DU000001nHUGYA2"
},
"transactionId": "0Q0DU0000000XoN0AU"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configurator options to execute.Configurator
Options Input
configurator
Options
60.0OptionalID of the context mapping record.Stringcontext
MappingId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
60.0RequiredTransaction ID of the header entity that’s
used to create a session. For example, a
Quote or an Order.
StringtransactionId
Configuration Save Input
Input representation of the details to save a configuration.
898
Request BodiesProduct Configurator

===== PAGE 913 =====

JSON example
{
"data":
"{&quot;LegalEntity&quot;:null,&quot;ProductName&quot;:&quot;Monitor&quot;,&quot;businessObjectType&quot;:&quot;QuoteLineItem&quot;,&quot;Product&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;ItemIsPrimarySegment&quot;:false,&quot;ListPrice&quot;:144.99,&quot;ValidationResult&quot;:null,&quot;StartDate&quot;:null,&quot;ContractVolumePasId&quot;:null,&quot;BillingTreatment&quot;:null,&quot;PeriodBoundaryStartMonth&quot;:null,&quot;SalesTransactionSourceAsset&quot;:null,&quot;id&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;PartnerDiscountPercent&quot;:10,&quot;PriceWaterFall&quot;:null,&quot;BillingFrequency&quot;:null,&quot;ProductCode&quot;:&quot;MO001&quot;,&quot;DerivedPricingAttribute&quot;:false,&quot;TaxTreatment&quot;:null,&quot;Subtotal&quot;:1739.88,&quot;ItemRampIdentifier&quot;:null,&quot;ItemSegmentName&quot;:null,&quot;SalesTransactionItemAttribute&quot;:[{&quot;AttributeKey&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;AttributeValue&quot;:&quot;1080p
Built-in
Display&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx0000000001AAA&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display&quot;,&quot;id&quot;:&quot;0zuxx000000000FAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;},{&quot;AttributeKey&quot;:&quot;0tjxx0000000009AAA&quot;,&quot;AttributeValue&quot;:&quot;24
Inch&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx000000000GAAQ&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display_Size&quot;,&quot;id&quot;:&quot;0zuxx000000000GAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;}],&quot;PricebookEntry&quot;:&quot;01uxx0000008yX0AAI&quot;,&quot;DiscountAmount&quot;:null,&quot;PricingTermCount&quot;:0,&quot;SubscriptionTermUnit&quot;:null,&quot;NetUnitPrice&quot;:144.99,&quot;ItemEffectiveGrantDate&quot;:null,&quot;ProductCategory&quot;:null,&quot;SalesTransactionAction&quot;:null,&quot;SalesTransactionActionType&quot;:null,&quot;SalesTransactionItemGroup&quot;:null,&quot;PeriodBoundaryDay&quot;:null,&quot;SalesTrxnItemDescription&quot;:null,&quot;LineItemDistributionType&quot;:null,&quot;ProrationPolicy&quot;:null,&quot;ContractDiscountType&quot;:null,&quot;TransactionType&quot;:null,&quot;ParentReference&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Discount&quot;:null,&quot;PricingTermUnit&quot;:null,&quot;ProductSellingModel&quot;:&quot;0jPxx0000000001EAA&quot;,&quot;PricingSource&quot;:null,&quot;StockKeepingUnit&quot;:null,&quot;PartnerUnitPrice&quot;:130.491,&quot;ItemTotalAdjustmentAmount&quot;:0,&quot;SalesTransactionItemSource&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;ContractAttributePasId&quot;:null,&quot;SubscriptionTerm&quot;:null,&quot;SellingModelType&quot;:&quot;OneTime&quot;,&quot;EndQuantity&quot;:12,&quot;NetTotalPrice&quot;:1739.88,&quot;TotalLineAmount&quot;:1739.88,&quot;ItemSegmentType&quot;:null,&quot;ProductBasedOn&quot;:&quot;11Bxx000002C1nqEAC&quot;,&quot;Deleted&quot;:false,&quot;BillingReference&quot;:null,&quot;ArePartialPeriodsAllowed&quot;:false,&quot;ItemRecordedPrice&quot;:null,&quot;CustomProductName&quot;:null,&quot;ItemSegmentIdentifier&quot;:null,&quot;SalesTransactionItemParent&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Quantity&quot;:12,&quot;PeriodBoundary&quot;:null,&quot;ContractDiscountValue&quot;:null,&quot;LineItemDiscountValue&quot;:null,&quot;ContractId&quot;:null,&quot;EndDate&quot;:null,&quot;ItemGroupSummarySubtotal&quot;:null,&quot;IsContracted&quot;:false,&quot;UnitPrice&quot;:144.99,&quot;StartQuantity&quot;:null,&quot;ContractPrice&quot;:null,&quot;TotalPrice&quot;:1739.88,&quot;LineItemDiscountType&quot;:null,&quot;ItemPath&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;productKey&quot;:[&quot;0QLxx0000004C9VGAU&quot;]}",
"description": "This configuration is saved for reuse.",
"name": "Favorite Configuration",
"referenceRecordId": "01txx0000006iCFAAY"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalJSON object that contains the details of
the sales transaction, formatted as a string.
Stringdata
63.0OptionalDescription of the saved configuration.Stringdescription
63.0OptionalName of the saved configuration.Stringname
63.0RequiredID of the record for which the
configuration must be saved.
StringreferenceRecord
Id
Configuration Update Input
Input representation of the details to update a configuration.
JSON example
{
"data":
"{&quot;LegalEntity&quot;:null,&quot;ProductName&quot;:&quot;Monitor&quot;,&quot;businessObjectType&quot;:&quot;QuoteLineItem&quot;,&quot;Product&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;ItemIsPrimarySegment&quot;:false,&quot;ListPrice&quot;:144.99,&quot;ValidationResult&quot;:null,&quot;StartDate&quot;:null,&quot;ContractVolumePasId&quot;:null,&quot;BillingTreatment&quot;:null,&quot;PeriodBoundaryStartMonth&quot;:null,&quot;SalesTransactionSourceAsset&quot;:null,&quot;id&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;PartnerDiscountPercent&quot;:10,&quot;PriceWaterFall&quot;:null,&quot;BillingFrequency&quot;:null,&quot;ProductCode&quot;:&quot;MO001&quot;,&quot;DerivedPricingAttribute&quot;:false,&quot;TaxTreatment&quot;:null,&quot;Subtotal&quot;:1739.88,&quot;ItemRampIdentifier&quot;:null,&quot;ItemSegmentName&quot;:null,&quot;SalesTransactionItemAttribute&quot;:[{&quot;AttributeKey&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;AttributeValue&quot;:&quot;1080p
Built-in
Display&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx0000000001AAA&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display&quot;,&quot;id&quot;:&quot;0zuxx000000000FAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;},{&quot;AttributeKey&quot;:&quot;0tjxx0000000009AAA&quot;,&quot;AttributeValue&quot;:&quot;24
Inch&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx000000000GAAQ&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display_Size&quot;,&quot;id&quot;:&quot;0zuxx000000000GAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;}],&quot;PricebookEntry&quot;:&quot;01uxx0000008yX0AAI&quot;,&quot;DiscountAmount&quot;:null,&quot;PricingTermCount&quot;:0,&quot;SubscriptionTermUnit&quot;:null,&quot;NetUnitPrice&quot;:144.99,&quot;ItemEffectiveGrantDate&quot;:null,&quot;ProductCategory&quot;:null,&quot;SalesTransactionAction&quot;:null,&quot;SalesTransactionActionType&quot;:null,&quot;SalesTransactionItemGroup&quot;:null,&quot;PeriodBoundaryDay&quot;:null,&quot;SalesTrxnItemDescription&quot;:null,&quot;LineItemDistributionType&quot;:null,&quot;ProrationPolicy&quot;:null,&quot;ContractDiscountType&quot;:null,&quot;TransactionType&quot;:null,&quot;ParentReference&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Discount&quot;:null,&quot;PricingTermUnit&quot;:null,&quot;ProductSellingModel&quot;:&quot;0jPxx0000000001EAA&quot;,&quot;PricingSource&quot;:null,&quot;StockKeepingUnit&quot;:null,&quot;PartnerUnitPrice&quot;:130.491,&quot;ItemTotalAdjustmentAmount&quot;:0,&quot;SalesTransactionItemSource&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;ContractAttributePasId&quot;:null,&quot;SubscriptionTerm&quot;:null,&quot;SellingModelType&quot;:&quot;OneTime&quot;,&quot;EndQuantity&quot;:12,&quot;NetTotalPrice&quot;:1739.88,&quot;TotalLineAmount&quot;:1739.88,&quot;ItemSegmentType&quot;:null,&quot;ProductBasedOn&quot;:&quot;11Bxx000002C1nqEAC&quot;,&quot;Deleted&quot;:false,&quot;BillingReference&quot;:null,&quot;ArePartialPeriodsAllowed&quot;:false,&quot;ItemRecordedPrice&quot;:null,&quot;CustomProductName&quot;:null,&quot;ItemSegmentIdentifier&quot;:null,&quot;SalesTransactionItemParent&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Quantity&quot;:12,&quot;PeriodBoundary&quot;:null,&quot;ContractDiscountValue&quot;:null,&quot;LineItemDiscountValue&quot;:null,&quot;ContractId&quot;:null,&quot;EndDate&quot;:null,&quot;ItemGroupSummarySubtotal&quot;:null,&quot;IsContracted&quot;:false,&quot;UnitPrice&quot;:144.99,&quot;StartQuantity&quot;:null,&quot;ContractPrice&quot;:null,&quot;TotalPrice&quot;:1739.88,&quot;LineItemDiscountType&quot;:null,&quot;ItemPath&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;productKey&quot;:[&quot;0QLxx0000004C9VGAU&quot;]}",
"description": "This configuration is updated.",
"name": "Updated Configuration"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredJSON object that contains the details of
the sales transaction, formatted as a string.
Stringdata
899
Request BodiesProduct Configurator

===== PAGE 914 =====

Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredDescription of the configuration.Stringdescription
63.0RequiredName of the configuration.Stringname
Configuration Save Instance Input
Input representation of the request to save a product configuration instance.
JSON example
{
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredTransaction context ID of the product
configuration instance that’s to be saved.
StringcontextId
Configuration Set Instance Input
Input representation of the request to set a product configuration instance.
JSON example
{
"configuratorOptions": {
"addDefaultConfiguration": true,
"executeConfigurationRules": true,
"executePricing": false,
"qualifyAllProductsInTransaction": false,
"validateAmendRenewCancel": false,
"validateProductCatalog": false
},
"contextMappingId": "11jEk000017YdyUIAS",
"qualificationContext": {
"accountId": "001DU000001nHUGYA2"
},
"transaction":
"{\"Quote\":[{\"QuoteLineItem\":[{\"businessObjectType\":\"QuoteLineItem\",\"id\":\"qli_1\"},{\"businessObjectType\":\"QuoteLineItem\",\"id\":\"qli_2\"},{\"businessObjectType\":\"QuoteLineItem\",\"id\":\"qli_3\"},{\"businessObjectType\":\"QuoteLineItem\",\"id\":\"qli_4\"}],\"businessObjectType\":\"Quote\",\"id\":\"aJSdm0000003m3JGAQ\"}]}"
}
900
Request BodiesProduct Configurator

===== PAGE 915 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configurator options to execute.Configurator
Options Input
configurator
Options
60.0RequiredID of the context mapping record.Stringcontext
MappingId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
60.0RequiredTransaction JSON payload representing an
object in an external system that’s used to
create a session.
Stringtransaction
Configurator Add Nodes Input
Input representation of the request to add nodes within a root node.
JSON example
{
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"addedNodes": [
{
"path": [
"0Q0xx0000004EvcCAE",
"ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589"
],
"addedObject": {
"id": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"SalesTransactionItemSource": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"SalesTransactionItemParent": "0Q0xx0000004EvcCAE",
"PricebookEntry": "01uxx00000090VuAAI",
"ProductSellingModel": "0jPxx00000001KHEAY",
"UnitPrice": 15.26,
"Quantity": 1,
"Product": "01txx0000006lfHAAQ",
901
Request BodiesProduct Configurator

===== PAGE 916 =====

"businessObjectType": "QuoteLineItem"
}
},
{
"path": [
"0Q0xx0000004EvcCAE",
"ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"ref_d85b036d_d305_4bb6_aba8_a1dff645a664"
],
"addedObject": {
"id": "ref_d85b036d_d305_4bb6_aba8_a1dff645a664",
"MainItem": "0QLxx0000004QdRGAU",
"AssociatedItem": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"ProductRelatedComponent": "0dSxx00000001p6EAA",
"ProductRelationshipType": null,
"AssociatedItemPricing": "NotIncludedInBundlePrice",
"AssociatedQuantScaleMethod": "Proportional",
"businessObjectType": "QuoteLineRelationship"
}
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredList of the nodes to be added.Configurator Added
Node Input[]
addedNodes
60.0OptionalList of the configuration options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context object that’s being
considered.
StringcontextId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
Configurator Added Node Input
Input representation of the nodes to be added to a product configuration.
JSON example
{
"addedNodes": [
{
"path": [
"0Q0xx0000004EvcCAE",
"ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589"
],
"addedObject": {
902
Request BodiesProduct Configurator

===== PAGE 917 =====

"id": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"SalesTransactionItemSource": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"SalesTransactionItemParent": "0Q0xx0000004EvcCAE",
"PricebookEntry": "01uxx00000090VuAAI",
"ProductSellingModel": "0jPxx00000001KHEAY",
"UnitPrice": 15.26,
"Quantity": 1,
"Product": "01txx0000006lfHAAQ",
"businessObjectType": "QuoteLineItem"
}
},
{
"path": [
"0Q0xx0000004EvcCAE",
"ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"ref_d85b036d_d305_4bb6_aba8_a1dff645a664"
],
"addedObject": {
"id": "ref_d85b036d_d305_4bb6_aba8_a1dff645a664",
"MainItem": "0QLxx0000004QdRGAU",
"AssociatedItem": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"ProductRelatedComponent": "0dSxx00000001p6EAA",
"ProductRelationshipType": null,
"AssociatedItemPricing": "NotIncludedInBundlePrice",
"AssociatedQuantScaleMethod": "Proportional",
"businessObjectType": "QuoteLineRelationship"
}
}
]
}
This example shows a sample request for orders.
{
"addedNodes": [
{
"path": [
"0Q0xx0000004EvcCAE",
"ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589"
],
"addedObject": {
"id": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"SalesTransactionItemSource": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"SalesTransactionItemParent": "0Q0xx0000004EvcCAE",
"PricebookEntry": "01uxx00000090VuAAI",
"ProductSellingModel": "0jPxx00000001KHEAY",
"UnitPrice": 15.26,
"Quantity": 1,
"Product": "01txx0000006lfHAAQ",
"businessObjectType": "OrderItem"
}
},
{
"path": [
"0Q0xx0000004EvcCAE",
903
Request BodiesProduct Configurator

===== PAGE 918 =====

"ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"ref_d85b036d_d305_4bb6_aba8_a1dff645a664"
],
"addedObject": {
"id": "ref_d85b036d_d305_4bb6_aba8_a1dff645a664",
"MainItem": "0QLxx0000004QdRGAU",
"AssociatedItem": "ref_d3a3f8d2_e031_4517_ae28_69ce16cb6589",
"ProductRelatedComponent": "0dSxx00000001p6EAA",
"ProductRelationshipType": null,
"AssociatedItemPricing": "NotIncludedInBundlePrice",
"AssociatedQuantScaleMethod": "Proportional",
"businessObjectType": "OrderItemRelationship"
}
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredDetails of the object that’s being added.
This property supports fields of objects
Map<String,
Object>
addedObject
from the Sales Transaction context
definition, including custom objects and
fields in your extended context definition.
60.0RequiredPath to the node that’s being added. The
path includes the unique ID of the context
String[]path
node in the data structure. This ID must
match the ID of the sales transaction item
source such as a quote line or an order line
item.
Keep these considerations in mind when
setting the path  value.
• If the businessObjectType
property value is QuoteLineItem,
the path must contain 2 IDs. The first
ID is the quote ID, and the second ID
is the quote line item ID.
• If the businessObjectType
property value is QuoteLineItem,
the path must contain
SalesTransactionItemSource
and
SalesTransactionItemParent.
• If the businessObjectType
property value is
QuoteLineItemRelationship,
904
Request BodiesProduct Configurator

===== PAGE 919 =====

Available
Version
Required or
Optional
DescriptionTypeName
the path must contain 3 IDs. The first
ID is the quote ID. The second ID is the
quote line item ID. The third ID is the
quote line item relationship ID.
Configurator Delete Nodes Input
Input representation of the request to delete nodes from a product configuration.
JSON example
{
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"deletedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"]
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configuration options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context object that’s being
considered.
StringcontextId
60.0RequiredList of the nodes to be deleted.Configurator
Deleted Node
Input[]
deletedNodes
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
905
Request BodiesProduct Configurator

===== PAGE 920 =====

Configurator Deleted Node Input
Input representation of the nodes to be deleted from a product configuration.
JSON example
"deletedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"]
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredPath to the node that’s being deleted.String[]path
Configurator Input
Input representation of the request to modify the product configuration.
JSON example
This example shows a sample to initiate a context based on a transaction ID.
{
"transactionLineId": "0QLDE000000IBXw4AO",
"transactionId": "0Q0xx0000000001GAA",
"correlationId": "c95246d4-102c-4ecd-a263-f74ac525d1e5",
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
This example shows a sample to add, update, or delete a node in an existing context.
{
"transactionLineId": "0QLDE000000IBXw4AO",
"transactionId": "0Q0DE000000ISHJs81",
"correlationId": "c95246d4-102c-4ecd-a263-f74ac525d1e5",
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
906
Request BodiesProduct Configurator

===== PAGE 921 =====

"contextResponseType": "Full",
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"transactionContextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"addedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "sti2_id"],
"addedObject": {
"id": "ref_sti2_id",
"SalesTransactionSource": "sti2_id",
"PricebookEntry": "01uxx0000000001AAA",
"ProductSellingModel": "0jPxx0000000001AAA",
"businessObjectType": "QuoteLineItem",
"Quantity": 10,
"UnitPrice": 2.0,
"Product": "01txx0000000001AAA"
}
},
{
"path": ["0Q0DE000000ISHJs81", "ref_sti2_id","ref_stir1_id"],
"addedObject": {
"id": "ref_stir1_id",
"businessObjectType": "QuoteLineItemRelationship",
"MainItem": "0QLDE000000IBXw4AO",
"AssociatedItem": "ref_sti2_id",
"ProductRelatedComponent": "0dSxx0000000001AAA",
"ProductRelationshipType": "0yoxx0000000001AAA",
"AssociatedItemPricing": "IncludedInBundlePrice"
}
}
],
"updatedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"],
"updatedAttributes": {
"Quantity": 5
}
}
],
"deletedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"]
}
]
}
907
Request BodiesProduct Configurator

===== PAGE 922 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of added context nodes that’s passed
to the product configurator.
Configurator Added
Node Input[]
addedNodes
60.0OptionalOptions to pass to the configurator.Configurator
Options Input[]
configurator
Options
65.0Required for large
sales transactions
Specifies the type of transaction context
response. Valid values are:
Stringcontext
ResponseType
with more than
• Delta—Returns the sales transaction
items that are added or updated.
1000 line items and
less than 15K line
items.• Full—Returns all sales transaction
items in a transaction.
• None—Returns empty transaction
context response.
• Product—Returns the sales
transaction items related to the
product that's being configured.
60.0OptionalID that’s specified for traceability of logs.StringcorrelationId
60.0OptionalList of deleted context nodes that’s passed
to the product configurator.
Configurator
Deleted Node
Input[]
deletedNodes
60.0OptionalDetails such as account ID, contact ID, and
context ID that are used for executing
qualification rules.
User Context Input[]qualification
Context
60.0OptionalID of the transaction context.Stringtransaction
ContextId
60.0RequiredID of the sales transaction that’s being
configured such as a quote or an order.
StringtransactionId
60.0OptionalID of the top-level line item that’s being
configured.
Stringtransaction
LineId
60.0OptionalList of updated context nodes that’s passed
to the product configurator.
Configurator
Updated Node
Input[]
updatedNodes
SEE ALSO:
Salesforce Help: Context Service
Developer Documentation: Context Service
908
Request BodiesProduct Configurator

===== PAGE 923 =====

Configurator Options Input
Input representation of the request to get the product configuration options that’s passed to the configurator.
JSON example
"configuratorOptions":
{
"addDefaultConfiguration": true,
"executeConfigurationRules": true,
"executePricing": true,
"qualifyAllProductsInTransaction": true,
"validateAmendRenewCancel": true,
"validateProductCatalog": true
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalIndicates whether to add the default
configurations (true) or not (false).
BooleanaddDefault
Configuration
60.0OptionalIndicates whether to execute the
configuration rules (true) or not
(false).
Booleanexecute
Configuration
Rules
60.0OptionalIndicates whether to execute pricing
(true) or not (false).
Booleanexecute
Pricing
60.0OptionalName of the pricing procedure to use
during the API calls to Salesforce Pricing
Management.
Stringpricing
Procedure
60.0OptionalIndicates whether to run the qualification
rules on all the products in the context
(true) or not (false).
BooleanqualifyAll
ProductsIn
Transaction
60.0OptionalIndicates whether to return the product
catalog data (true) or not (false).
BooleanreturnProduct
CatalogData
Exclude this property or specify the
property value as false  if you’re using
the API without the Product Configurator
UI.
60.0OptionalIndicates whether to run the amend,
renew, cancel-related validations (true)
or not (false).
BooleanvalidateAmend
RenewCancel
60.0OptionalIndicates whether to run the validations
against the product catalog (true) or not
(false).
Booleanvalidate
Product
Catalog
909
Request BodiesProduct Configurator

===== PAGE 924 =====

Configurator Update Nodes Input
Input representation of the request to update the nodes in a product configuration.
JSON example
{
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"updatedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"],
"updatedAttributes": {
"Quantity": 5
}
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configuration options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context object that’s being
considered.
StringcontextId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
60.0RequiredList of the nodes to be updated.Configurator
Updated Node
Input[]
updatedNodes
Configurator Updated Node Input
Input representation of the nodes to be updated in a product configuration.
910
Request BodiesProduct Configurator

===== PAGE 925 =====

JSON example
"updatedNodes": [
{
"path": ["0Q0DE000000ISHJs81", "0QLDE000000IBXw4AO"],
"updatedAttributes": {
"Quantity": 5
}
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredPath to the node that’s being updated.String[]path
60.0RequiredDetails of the object that’s being updated.
This property supports fields of objects
Map<String,
Object>
updated
Attributes
from the Sales Transaction context
definition, including custom objects and
fields in your extended context definition.
Product Quantity Set Configurator Input
Input representation of the request to set the quantity of a product.
JSON example
{
"configuratorOptions": {
"executePricing": true,
"returnProductCatalogData": true,
"qualifyAllProductsInTransaction": true,
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"qualificationContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"quantity": 20,
"transactionLinePath": "Quote.QuoteLineItem.Quantity"
}
911
Request BodiesProduct Configurator

===== PAGE 926 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of the configuration options to
execute.
Configurator
Options Input
configurator
Options
60.0RequiredID of the context object that’s being
considered.
StringcontextId
60.0OptionalContext details that are used for the
qualification rules.
User Context Inputqualification
Context
60.0RequiredValue of the product quantity.Integerquantity
60.0RequiredPath to the line item where the update to
the quantity is applied. For example,
Quote.QuoteLineItem.Quantity.
String[]transaction
LinePath
User Context Input
Input representation of the request to get the context details of a user, which are used for qualification rules.
JSON example
"qualificationContext": {
"accountId": "001DU000001nHUGYA2",
"contactId": "003xx00000000D7AAI"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalID of the account in a user context.StringaccountId
60.0OptionalID of the contact in a user context.StringcontactId
60.0OptionalID of the context that represents the
created session.
StringcontextId
Response Bodies
Learn more about the available Product Configurator API response bodies.
Configuration Details
Output representation of the product configuration details.
Configuration Get Instance
Output representation of the request to retrieve the configuration instance.
912
Response BodiesProduct Configurator

===== PAGE 927 =====

Configuration Load Instance
Output representation of the details of the context or session that are returned with a load configuration request.
Configuration Save Details
Output representation of the details of a saved configuration.
Configuration Record Save
Output representation of the details of a saved configuration.
Configuration List
Output representation of the details of the saved configuration.
Configuration Save Instance
Output representation of the response that’s returned with a save configuration request.
Configuration Set Instance
Output representation of the details of the context or session that are returned with a set configuration request.
Configurator Add Nodes
Output representation of the configuration request details to add nodes.
Configurator Additional Fields
Output representation of the additional fields of a product configuration.
Configurator Attribute
Output representation of the attribute in a product configuration.
Configurator Attribute Category
Output representation of the attribute category in a product configuration.
Configurator Attribute Picklist
Output representation of the attribute picklist in a product configuration.
Configurator Attribute Picklist Value
Output representation of the values of an attribute picklist in a product configuration.
Configurator Delete Nodes
Output representation of the details of the configuration request to delete nodes.
Configurator Message
Output representation of the messages of a product configurator.
Configurator Price
Output representation of the pricing details in a product configuration.
Configurator Pricing Model
Output representation of the details of a pricing model in a product configuration.
Configurator Product Catalog
Output representation of the product catalog.
Configurator Product Classification
Output representation of the product classification in a product configuration.
Configurator Product Component Group
Output representation of the product component group in a product classification.
Configurator Product Recommendations
Output representation of the details of the product recommendations.
913
Response BodiesProduct Configurator

===== PAGE 928 =====

Configurator Product Related Component
Output representation of the product related component in a product configuration.
Configurator Product Selling Model
Output representation of the product selling model in a product configuration.
Configurator Product Selling Model Option
Output representation of the product selling model option in a product configuration.
Configurator Qualification Context
Output representation of the qualification context in a product configuration.
Configurator UI Treatment
Output representation of the details of the UI treatments of a product configurator. The details include the product configuration
rule actions to override the disable or hide behavior in the UI for product options, product attributes, and attribute picklist values.
Configurator Unit Of Measure
Output representation of the details of the unit of measure record.
Configurator Update Nodes
Output representation of the configuration request details to update nodes.
Configuration Update
Output representation of the details of the updated configuration.
Error Response
Output representation of the details of the error.
Product Quantity Set Configurator
Output representation of the request details to set product quantity.
Configuration Details
Output representation of the product configuration details.
JSON example
{
"catalogProducts": {
"additionalFields": [],
"attributeCategories": [
{
"attributes": [
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Load Capacity",
"code": "CAP",
"dataType": "NUMBER",
"defaultValue": "1500",
"description": "Server racks are designed to support a specific load capacity,
commonly measured in kilograms (kg) or pounds (lbs). Typical load capacities range from
500 kg (1102 lbs) to 1500 kg (3307 lbs) depending on the model.",
"id": "0tjxx00000001DpAAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
914
Response BodiesProduct Configurator

===== PAGE 929 =====

"isReadOnly": false,
"isRequired": false,
"label": "Load Capacity",
"name": "Load Capacity"
},
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Expansion Slots",
"code": "SLOTCAP",
"dataType": "NUMBER",
"defaultValue": "12",
"id": "0tjxx00000001H3AAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "Expansion Slots",
"name": "Expansion Slots"
},
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Memory",
"attributePicklist": {
"id": "0v5xx0000000001AAA",
"values": [
{
"code": "MEM",
"displayValue": "25",
"id": "0v6xx0000000001AAA",
"isBooleanValue": false,
"name": "25Mem",
"sequence": 0,
"textValue": "25"
},
{
"code": "50MEM",
"displayValue": "50",
"id": "0v6xx000000001eAAA",
"isBooleanValue": false,
"name": "50Mem",
"sequence": 1,
"textValue": "50"
},
{
"code": "100MEM",
"displayValue": "100",
"id": "0v6xx000000003FAAQ",
"isBooleanValue": false,
"name": "100Mem",
"sequence": 2,
"textValue": "100"
}
915
Response BodiesProduct Configurator

===== PAGE 930 =====

]
},
"dataType": "MULTIPICKLIST",
"defaultValue": "25",
"id": "0tjxx00000001IfAAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "Memory",
"name": "Memory"
}
],
"code": "SPEC",
"name": "Server Rack Specifications"
}
],
"description": "Introducing the Cisco Server Rack, a sleek and robust solution
designed to streamline your data center infrastructure. With its scalable design and
advanced cable management features, it ensures optimal performance, efficiency, and easy
maintenance for your critical network equipment.",
"displayUrl":
"https://www.cisco.com/content/dam/en/us/products/servers-unified-computing/ucs-c240-m4-rack-server/product-large.jpg",
"id": "01txx0000006jkuAAA",
"isActive": true,
"isAssetizable": true,
"isConfigurable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Server Rack NX44",
"nodeType": "bundleProduct",
"prices": [],
"productClassification": {
"id": "11Bxx000002CC02EAG"
},
"productCode": "RACK",
"productComponentGroups": [
{
"classifications": [],
"code": "SERVICE",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Service, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jmWAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
916
Response BodiesProduct Configurator

===== PAGE 931 =====

"isConfigurable": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Service - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "SERVICE",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jmWAAQ",
"childSellingModelId": "0jPxx000000004rEAA",
"doesBundlePriceIncludeChild": true,
"id": "0dSxx000000001dEAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000004rEAA",
"productComponentGroupId": "0y7xx000000001dAAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": [
{
"id": "0iOxx000000009hEAA",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000PpEAI",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
}
]
}
917
Response BodiesProduct Configurator

===== PAGE 932 =====

],
"description": "The services available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx000000001dAAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Services",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 1
},
{
"classifications": [],
"code": "WARRANTY",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Warranty, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jjIAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Warranty - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "WARRANTY",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jjIAAQ",
"childSellingModelId": "0jPxx000000001dEAA",
"doesBundlePriceIncludeChild": false,
"id": "0dSxx0000000001EAA",
"isComponentRequired": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"maxQuantity": 1,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000001dEAA",
"productComponentGroupId": "0y7xx0000000001AAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 0
},
"productSellingModelOptions": [
918
Response BodiesProduct Configurator

===== PAGE 933 =====

{
"id": "0iOxx000000001dEAA",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
},
{
"id": "0iOxx00000000HlEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000003FEAQ"
},
{
"id": "0iOxx00000000JNEAY",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000KzEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
},
{
"id": "0iOxx00000000MbEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
919
Response BodiesProduct Configurator

===== PAGE 934 =====

"id": "0jPxx000000006TEAQ",
"name": "Evergreen Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx000000006TEAQ"
}
]
}
],
"description": "The warranties available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx0000000001AAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Warranties",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 0
}
],
"productSellingModelOptions": [
{
"id": "0iOxx000000003FEAQ",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
},
{
"id": "0iOxx000000004rEAA",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000003FEAQ"
},
{
"id": "0iOxx000000006TEAQ",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
920
Response BodiesProduct Configurator

===== PAGE 935 =====

"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
}
],
"productType": "Bundle"
},
"uiTreatments": [
{
"details": {
"attributeId": "0tjxx0000000007AAA",
"prcId": "0dSxx0000000007EAA",
"stiId": "0QLxx0000004CU0GAM",
"attributePicklistValueId": "0v6xx0000000005AAA"
},
"uiTreatmentScope": "Bundle",
"uiTreatmentTarget": "Attribute_Picklist_Value",
"uiTreatmentType": "Hide"
},
{
"details": {
"stiId": "ref_f0f2da7b_c431_482d_bf4b_599052f3a2e1"
},
"uiTreatmentScope": "Product",
"uiTreatmentTarget": "Component",
"uiTreatmentType": "Disable"
}
],
"errors": [],
"success": true,
"productRecommendations": [
{
"referenceId": "CORE_BUNDLE_001",
"productIds": [
"01t000000001234",
"01t000000005678"
]
}
],
"transactionContext": {
"SalesTransaction": [
{
"Status": "Draft",
"Account": "001xx000003GeIxAAK",
"BillingCity": "San Francisco",
"Subtotal": 152500,
"LastPricedDate": "2023-08-22T05:55:39Z",
"businessObjectType": "Quote",
"TotalAmount": 152500,
"ShippingStreet": "415 Mission St",
"SalesTransactionItem": [
921
Response BodiesProduct Configurator

===== PAGE 936 =====

{
"ProrationPolicy": null,
"Discount": null,
"ProductSellingModel": "0jPxx000000001dEAA",
"Product": "01txx0000006jkuAAA",
"businessObjectType": "QuoteLineItem",
"BasisTransactionItem": null,
"PartnerUnitPrice": null,
"StartingUnitPriceSource": "System",
"ListPrice": 150000,
"ItemTotalAdjustmentAmount": 0,
"SalesTransactionItemSource": "0QLxx0000004CQmGAM",
"SubscriptionTerm": null,
"StartDate": null,
"NetTotalPrice": 150000,
"TotalLineAmount": 150000,
"PeriodBoundaryStartMonth": null,
"ListPriceTotal": 150000,
"PartnerDiscountPercent": null,
"id": "0QLxx0000004CQmGAM",
"PriceWaterFall": {
"currencyCode": "USD",
"executionEndTimestamp": "2023-09-18T20:11:15.016Z",
"executionId": "ruepwmHn2ZFvnQo5bjot",
"executionStartTimestamp": "2023-09-18T20:11:14.906Z",
"lineItemId": "0QLxx0000004CQmGAM",
"output": {
"NetUnitPrice": 150000,
"Subtotal": 0
},
"success": true,
"waterfall": [
{
"fieldToTagNameMapping": {
"NetUnitPrice": "ItemUnitPrice",
"AdjustmentValue": "ItemAdjustmentValue",
"Subtotal": "ItemTotalAdjustmentAmount",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionItemSource",
"InputUnitPrice": "ItemUnitPrice"
},
"inputParameters": {
"Quantity": 1,
"LineItemId": "0QLxx0000004CQmGAM",
"InputUnitPrice": 150000,
"AdjustmentType": "Amount"
},
"outputParameters": {
"NetUnitPrice": 150000,
"Subtotal": 0
},
"pricingElement": {
"adjustments": [
{
922
Response BodiesProduct Configurator

===== PAGE 937 =====

"AdjustmentType": "Amount"
}
],
"elementType": "MANUALDISCOUNT",
"name": "ManualDiscount"
},
"sequence": 1
}
]
},
"BillingFrequency": null,
"SalesTransactionItemParent": "0Q0xx0000004CAeCAM",
"StartingPriceTotal": 150000,
"Quantity": 1,
"PeriodBoundary": null,
"SalesTransactionItemAttribute": [
{
"AttributeKey": "0tjxx00000001H3AAI",
"AttributeValue": "30.0",
"AttributePicklistValue": null,
"IsPriceImpacting": true,
"businessObjectType": "QuoteLineItemAttribute",
"AttributeName": "Expansion Slots",
"AttributeDefinitionCode": "SLOTCAP",
"id": "0zuxx0000000001AAA",
"SalesTransactionItemAttrParent": "0QLxx0000004CQmGAM"
}
],
"EndDate": null,
"DiscountAmount": null,
"PricebookEntry": "01uxx0000009154AAA",
"PricingTermCount": 1,
"NetUnitPrice": 150000,
"UnitPrice": 150000,
"StartingUnitPrice": 150000,
"SalesTrxnItemRelationship": [
{
"ProductRelationshipType": "0yoxx00000001IfAAI",
"MainItemRole": "Bundle",
"AssociatedItem": "0QLxx0000004CQnGAM",
"ProductRelatedComponent": "0dSxx0000000001EAA",
"MainItem": "0QLxx0000004CQmGAM",
"AssociatedQuantScaleMethod": "Proportional",
"businessObjectType": "QuoteLineRelationship",
"AssociatedItemRole": "BundleComponent",
"SalesTrnItemRelationshipParent": "0Q0xx0000004CAeCAM",
"id": "0yQxx000000001dEAA",
"AssociatedItemPricing": "NotIncludedInBundlePrice"
}
],
"TotalPrice": 150000,
"PeriodBoundaryDay": null
},
{
923
Response BodiesProduct Configurator

===== PAGE 938 =====

"ProrationPolicy": null,
"Discount": null,
"ProductSellingModel": "0jPxx000000001dEAA",
"Product": "01txx0000006jjIAAQ",
"businessObjectType": "QuoteLineItem",
"BasisTransactionItem": null,
"PartnerUnitPrice": null,
"StartingUnitPriceSource": "System",
"ListPrice": 2000,
"ItemTotalAdjustmentAmount": 0,
"SalesTransactionItemSource": "0QLxx0000004CQnGAM",
"SubscriptionTerm": null,
"StartDate": null,
"NetTotalPrice": 2000,
"TotalLineAmount": 2000,
"PeriodBoundaryStartMonth": null,
"ListPriceTotal": 2000,
"PartnerDiscountPercent": null,
"id": "0QLxx0000004CQnGAM",
"PriceWaterFall": {
"currencyCode": "USD",
"executionEndTimestamp": "023-09-18T20:11:15.016Z",
"executionId": "ruepwmHn2ZFvnQo5bjot",
"executionStartTimestamp": "2023-09-18T20:11:14.906Z",
"lineItemId": "0QLxx0000004CQnGAM",
"output": {
"NetUnitPrice": 2000,
"Subtotal": 0
},
"success": true,
"waterfall": [
{
"fieldToTagNameMapping": {
"NetUnitPrice": "ItemUnitPrice",
"AdjustmentValue": "ItemAdjustmentValue",
"Subtotal": "ItemTotalAdjustmentAmount",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionItemSource",
"InputUnitPrice": "ItemUnitPrice"
},
"inputParameters": {
"Quantity": 1,
"LineItemId": "0QLxx0000004CQnGAM",
"InputUnitPrice": 2000,
"AdjustmentType": "Amount"
},
"outputParameters": {
"NetUnitPrice": 2000,
"Subtotal": 0
},
"pricingElement": {
"adjustments": [
{}
],
924
Response BodiesProduct Configurator

===== PAGE 939 =====

"elementType": "MANUALDISCOUNT",
"name": "ManualDiscount"
},
"sequence": 1
}
]
},
"BillingFrequency": null,
"SalesTransactionItemParent": "0Q0xx0000004CAeCAM",
"StartingPriceTotal": 2000,
"Quantity": 1,
"PeriodBoundary": null,
"EndDate": null,
"DiscountAmount": null,
"PricebookEntry": "01uxx000000913SAAQ",
"PricingTermCount": 1,
"NetUnitPrice": 2000,
"UnitPrice": 2000,
"StartingUnitPrice": 2000,
"TotalPrice": 2000,
"PeriodBoundaryDay": null
}
],
"BillingCountry": "US",
"BillingStreet": "415 Mission St",
"Pricebook": "01sxx0000005uDZAAY",
"ShippingPostalCode": "94105",
"SalesTransactionSource": "0Q0xx0000004CAeCAM",
"ShippingCountry": "US",
"ShippingCity": "San Francisco",
"ShippingState": "CA",
"BillingPostalCode": "94105",
"id": "0Q0xx0000004CAeCAM",
"BillToContact": null,
"Contract": null,
"BillingState": "CA"
}
]
},
"transactionContextId": "cda87acd-45ed-4913-903e-9dd33cec85a6",
"transactionContextMappingId": "11jxx0000004LwOAAU"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
61.0Small, 61.0Structure that contains the product catalog
data.
Configurator Product
Catalog[]
catalog
Products
60.0Small, 60.0List of errors that contains a message and
an error code.
ConnectApi.ErrorResponseerrors
925
Response BodiesProduct Configurator

===== PAGE 940 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Messages from the validation, Business Rules
Engine (BRE), or Salesforce Pricing calls.
Map<String,
Configurator
Message>>
messages
65.0Small, 65.0List of product recommendations.Configurator Product
Recommendations
product
Recommendations
60.0Small, 60.0Indicates whether the request is successful
(true) or not (false).
Booleansuccess
60.0Small, 60.0Serialized JSON representation of the
transaction context.
Map<String,
Object>
transaction
Context
60.0Small, 60.0ID of the transaction context.Stringtransaction
ContextId
60.0Small, 60.0ID of the context mapping.StringtransactionContext
MappingId
60.0Small, 60.0Map of the product IDs to the qualification
context.
Map<String,
Configurator
Qualification
Context>
transaction
Qualification
62.0Small, 62.0Details of the UI treatments that specify the
product configuration rule actions to
Configurator UI
Treatment[]
uiTreatments
override the disable or hide behavior in the
UI for product options, product attributes,
and attribute picklist values.
Configuration Get Instance
Output representation of the request to retrieve the configuration instance.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0List of errors, which contains an error code
and a message.
Error Responseerrors
60.0Small, 60.0Indicates whether the call was successful
(true) not (false).
Booleansuccess
60.0Small, 60.0Transaction JSON payload representing an
object in an external system that’s used to
create a session.
Map<String,
Object>
transaction
926
Response BodiesProduct Configurator

===== PAGE 941 =====

Configuration Load Instance
Output representation of the details of the context or session that are returned with a load configuration request.
JSON Example
{
"configuratorMessages": {},
"configuratorUITreatments": [
{
"details": {
"attributeId": "0tjxx0000000007AAA",
"prcId": "0dSxx0000000007EAA",
"stiId": "0QLxx0000004CU0GAM",
"attributePicklistValueId": "0v6xx0000000005AAA"
},
"uiTreatmentScope": "Bundle",
"uiTreatmentTarget": "Attribute_Picklist_Value",
"uiTreatmentType": "Hide"
},
{
"details": {
"stiId": "ref_f0f2da7b_c431_482d_bf4b_599052f3a2e1"
},
"uiTreatmentScope": "Product",
"uiTreatmentTarget": "Component",
"uiTreatmentType": "Disable"
}
],
"contextId": "831f07b01cf0cbd2d046adf5350420f85f0611b4b1e22e183921a063857a1377",
"errors": [],
"productQualifications": {
"01tDU000000EOTCYA4": {
"isQualified": true
}
},
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Map of the product IDs to the list of
configurator messages. Configurator
Map<String,
<Configurator
Message>>
configurator
Messages
messages are results from any validations,
Business Rules Engines (BRE) calls, or
Salesforce Pricing calls.
62.0Small, 62.0Details of the UI treatments that specify the
product configuration rule actions to
Configurator UI
Treatment[]
configurator
UITreatments
override the disable or hide behavior in the
UI for product options, product attributes,
and attribute picklist values.
60.0Small, 60.0ID of the transaction context.StringcontextId
927
Response BodiesProduct Configurator

===== PAGE 942 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0List of errors, which contains an error code
and a message.
Error Responseerrors
60.0Small, 60.0Map of the product IDs to the execution
results from qualification rules.
Map<String,
Configurator
Qualification
Context>
product
Qualifications
60.0Small, 60.0Indicates whether the call was successful
(true) not (false).
Booleansuccess
Configuration Save Details
Output representation of the details of a saved configuration.
JSON example
{
"savedConfigurations": [
{
"data":
"{&quot;LegalEntity&quot;:null,&quot;ProductName&quot;:&quot;Monitor&quot;,&quot;businessObjectType&quot;:&quot;QuoteLineItem&quot;,&quot;Product&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;ItemIsPrimarySegment&quot;:false,&quot;ListPrice&quot;:144.99,&quot;ValidationResult&quot;:null,&quot;StartDate&quot;:null,&quot;ContractVolumePasId&quot;:null,&quot;BillingTreatment&quot;:null,&quot;PeriodBoundaryStartMonth&quot;:null,&quot;SalesTransactionSourceAsset&quot;:null,&quot;id&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;PartnerDiscountPercent&quot;:10,&quot;PriceWaterFall&quot;:null,&quot;BillingFrequency&quot;:null,&quot;ProductCode&quot;:&quot;MO001&quot;,&quot;DerivedPricingAttribute&quot;:false,&quot;TaxTreatment&quot;:null,&quot;Subtotal&quot;:1739.88,&quot;ItemRampIdentifier&quot;:null,&quot;ItemSegmentName&quot;:null,&quot;SalesTransactionItemAttribute&quot;:[{&quot;AttributeKey&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;AttributeValue&quot;:&quot;1080p
Built-in
Display&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx0000000001AAA&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display&quot;,&quot;id&quot;:&quot;0zuxx000000000FAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;},{&quot;AttributeKey&quot;:&quot;0tjxx0000000009AAA&quot;,&quot;AttributeValue&quot;:&quot;24
Inch&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx000000000GAAQ&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display_Size&quot;,&quot;id&quot;:&quot;0zuxx000000000GAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;}],&quot;PricebookEntry&quot;:&quot;01uxx0000008yX0AAI&quot;,&quot;DiscountAmount&quot;:null,&quot;PricingTermCount&quot;:0,&quot;SubscriptionTermUnit&quot;:null,&quot;NetUnitPrice&quot;:144.99,&quot;ItemEffectiveGrantDate&quot;:null,&quot;ProductCategory&quot;:null,&quot;SalesTransactionAction&quot;:null,&quot;SalesTransactionActionType&quot;:null,&quot;SalesTransactionItemGroup&quot;:null,&quot;PeriodBoundaryDay&quot;:null,&quot;SalesTrxnItemDescription&quot;:null,&quot;LineItemDistributionType&quot;:null,&quot;ProrationPolicy&quot;:null,&quot;ContractDiscountType&quot;:null,&quot;TransactionType&quot;:null,&quot;ParentReference&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Discount&quot;:null,&quot;PricingTermUnit&quot;:null,&quot;ProductSellingModel&quot;:&quot;0jPxx0000000001EAA&quot;,&quot;PricingSource&quot;:null,&quot;StockKeepingUnit&quot;:null,&quot;PartnerUnitPrice&quot;:130.491,&quot;ItemTotalAdjustmentAmount&quot;:0,&quot;SalesTransactionItemSource&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;ContractAttributePasId&quot;:null,&quot;SubscriptionTerm&quot;:null,&quot;SellingModelType&quot;:&quot;OneTime&quot;,&quot;EndQuantity&quot;:12,&quot;NetTotalPrice&quot;:1739.88,&quot;TotalLineAmount&quot;:1739.88,&quot;ItemSegmentType&quot;:null,&quot;ProductBasedOn&quot;:&quot;11Bxx000002C1nqEAC&quot;,&quot;Deleted&quot;:false,&quot;BillingReference&quot;:null,&quot;ArePartialPeriodsAllowed&quot;:false,&quot;ItemRecordedPrice&quot;:null,&quot;CustomProductName&quot;:null,&quot;ItemSegmentIdentifier&quot;:null,&quot;SalesTransactionItemParent&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Quantity&quot;:12,&quot;PeriodBoundary&quot;:null,&quot;ContractDiscountValue&quot;:null,&quot;LineItemDiscountValue&quot;:null,&quot;ContractId&quot;:null,&quot;EndDate&quot;:null,&quot;ItemGroupSummarySubtotal&quot;:null,&quot;IsContracted&quot;:false,&quot;UnitPrice&quot;:144.99,&quot;StartQuantity&quot;:null,&quot;ContractPrice&quot;:null,&quot;TotalPrice&quot;:1739.88,&quot;LineItemDiscountType&quot;:null,&quot;ItemPath&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;productKey&quot;:[&quot;0QLxx0000004C9VGAU&quot;]}",
"description": "This configuration is for cline XYZ",
"id": "1Nyxx0000004CFUCA2",
"name": "Client XYZ Favorite",
"referenceRecordId": "01txx0000006iCFAAY"
},
{
"data":
"{&quot;LegalEntity&quot;:null,&quot;ProductName&quot;:&quot;Monitor&quot;,&quot;businessObjectType&quot;:&quot;QuoteLineItem&quot;,&quot;Product&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;ItemIsPrimarySegment&quot;:false,&quot;ListPrice&quot;:144.99,&quot;ValidationResult&quot;:null,&quot;StartDate&quot;:null,&quot;ContractVolumePasId&quot;:null,&quot;BillingTreatment&quot;:null,&quot;PeriodBoundaryStartMonth&quot;:null,&quot;SalesTransactionSourceAsset&quot;:null,&quot;id&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;PartnerDiscountPercent&quot;:10,&quot;PriceWaterFall&quot;:null,&quot;BillingFrequency&quot;:null,&quot;ProductCode&quot;:&quot;MO001&quot;,&quot;DerivedPricingAttribute&quot;:false,&quot;TaxTreatment&quot;:null,&quot;Subtotal&quot;:1739.88,&quot;ItemRampIdentifier&quot;:null,&quot;ItemSegmentName&quot;:null,&quot;SalesTransactionItemAttribute&quot;:[{&quot;AttributeKey&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;AttributeValue&quot;:&quot;1080p
Built-in
Display&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx0000000001AAA&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display&quot;,&quot;id&quot;:&quot;0zuxx000000000FAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;},{&quot;AttributeKey&quot;:&quot;0tjxx0000000009AAA&quot;,&quot;AttributeValue&quot;:&quot;24
Inch&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx000000000GAAQ&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display_Size&quot;,&quot;id&quot;:&quot;0zuxx000000000GAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;}],&quot;PricebookEntry&quot;:&quot;01uxx0000008yX0AAI&quot;,&quot;DiscountAmount&quot;:null,&quot;PricingTermCount&quot;:0,&quot;SubscriptionTermUnit&quot;:null,&quot;NetUnitPrice&quot;:144.99,&quot;ItemEffectiveGrantDate&quot;:null,&quot;ProductCategory&quot;:null,&quot;SalesTransactionAction&quot;:null,&quot;SalesTransactionActionType&quot;:null,&quot;SalesTransactionItemGroup&quot;:null,&quot;PeriodBoundaryDay&quot;:null,&quot;SalesTrxnItemDescription&quot;:null,&quot;LineItemDistributionType&quot;:null,&quot;ProrationPolicy&quot;:null,&quot;ContractDiscountType&quot;:null,&quot;TransactionType&quot;:null,&quot;ParentReference&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Discount&quot;:null,&quot;PricingTermUnit&quot;:null,&quot;ProductSellingModel&quot;:&quot;0jPxx0000000001EAA&quot;,&quot;PricingSource&quot;:null,&quot;StockKeepingUnit&quot;:null,&quot;PartnerUnitPrice&quot;:130.491,&quot;ItemTotalAdjustmentAmount&quot;:0,&quot;SalesTransactionItemSource&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;ContractAttributePasId&quot;:null,&quot;SubscriptionTerm&quot;:null,&quot;SellingModelType&quot;:&quot;OneTime&quot;,&quot;EndQuantity&quot;:12,&quot;NetTotalPrice&quot;:1739.88,&quot;TotalLineAmount&quot;:1739.88,&quot;ItemSegmentType&quot;:null,&quot;ProductBasedOn&quot;:&quot;11Bxx000002C1nqEAC&quot;,&quot;Deleted&quot;:false,&quot;BillingReference&quot;:null,&quot;ArePartialPeriodsAllowed&quot;:false,&quot;ItemRecordedPrice&quot;:null,&quot;CustomProductName&quot;:null,&quot;ItemSegmentIdentifier&quot;:null,&quot;SalesTransactionItemParent&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Quantity&quot;:12,&quot;PeriodBoundary&quot;:null,&quot;ContractDiscountValue&quot;:null,&quot;LineItemDiscountValue&quot;:null,&quot;ContractId&quot;:null,&quot;EndDate&quot;:null,&quot;ItemGroupSummarySubtotal&quot;:null,&quot;IsContracted&quot;:false,&quot;UnitPrice&quot;:144.99,&quot;StartQuantity&quot;:null,&quot;ContractPrice&quot;:null,&quot;TotalPrice&quot;:1739.88,&quot;LineItemDiscountType&quot;:null,&quot;ItemPath&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;productKey&quot;:[&quot;0QLxx0000004C9VGAU&quot;]}",
"description": "This configuration is for cline XYZ",
"id": "1Nyxx0000004CH6CAM",
"name": "Client XYZ Favorite",
"referenceRecordId": "01txx0000006iCFAAY"
}
]
}
928
Response BodiesProduct Configurator

===== PAGE 943 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0JSON object that contains the details of the
sales transaction, formatted as a string.
Stringdata
63.0Small, 63.0Description of the saved configuration.Stringdescription
63.0Small, 63.0ID of the saved configuration.Stringid
63.0Small, 63.0Name of the saved configuration.Stringname
63.0Small, 63.0ID of the record that the saved configuration
belongs to.
StringreferenceRecord
Id
Configuration Record Save
Output representation of the details of a saved configuration.
JSON example
This example shows a sample when the save operation is successful.
{
"errors": [],
"id": "1Nyxx0000004CNYCA2"
}
This example shows a sample when the save operation has errors.
{
"errors": [{
"code": "INTERNAL_SERVER_ERROR",
"message": "INVALID_REFERENCEOBJECTID"
}]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of errors that contains a message and
an error code.
Error Responseerrors
63.0Small, 63.0ID of the configuration that's saved.
This property isn't shown if the operation
has errors.
Stringid
Configuration List
Output representation of the details of the saved configuration.
929
Response BodiesProduct Configurator

===== PAGE 944 =====

JSON example
{
"errors": [],
"savedConfigurations": [
{
"data":
"{&quot;LegalEntity&quot;:null,&quot;ProductName&quot;:&quot;Monitor&quot;,&quot;businessObjectType&quot;:&quot;QuoteLineItem&quot;,&quot;Product&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;ItemIsPrimarySegment&quot;:false,&quot;ListPrice&quot;:144.99,&quot;ValidationResult&quot;:null,&quot;StartDate&quot;:null,&quot;ContractVolumePasId&quot;:null,&quot;BillingTreatment&quot;:null,&quot;PeriodBoundaryStartMonth&quot;:null,&quot;SalesTransactionSourceAsset&quot;:null,&quot;id&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;PartnerDiscountPercent&quot;:10,&quot;PriceWaterFall&quot;:null,&quot;BillingFrequency&quot;:null,&quot;ProductCode&quot;:&quot;MO001&quot;,&quot;DerivedPricingAttribute&quot;:false,&quot;TaxTreatment&quot;:null,&quot;Subtotal&quot;:1739.88,&quot;ItemRampIdentifier&quot;:null,&quot;ItemSegmentName&quot;:null,&quot;SalesTransactionItemAttribute&quot;:[{&quot;AttributeKey&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;AttributeValue&quot;:&quot;1080p
Built-in
Display&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx0000000001AAA&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display&quot;,&quot;id&quot;:&quot;0zuxx000000000FAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;},{&quot;AttributeKey&quot;:&quot;0tjxx0000000009AAA&quot;,&quot;AttributeValue&quot;:&quot;24
Inch&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx000000000GAAQ&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display_Size&quot;,&quot;id&quot;:&quot;0zuxx000000000GAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;}],&quot;PricebookEntry&quot;:&quot;01uxx0000008yX0AAI&quot;,&quot;DiscountAmount&quot;:null,&quot;PricingTermCount&quot;:0,&quot;SubscriptionTermUnit&quot;:null,&quot;NetUnitPrice&quot;:144.99,&quot;ItemEffectiveGrantDate&quot;:null,&quot;ProductCategory&quot;:null,&quot;SalesTransactionAction&quot;:null,&quot;SalesTransactionActionType&quot;:null,&quot;SalesTransactionItemGroup&quot;:null,&quot;PeriodBoundaryDay&quot;:null,&quot;SalesTrxnItemDescription&quot;:null,&quot;LineItemDistributionType&quot;:null,&quot;ProrationPolicy&quot;:null,&quot;ContractDiscountType&quot;:null,&quot;TransactionType&quot;:null,&quot;ParentReference&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Discount&quot;:null,&quot;PricingTermUnit&quot;:null,&quot;ProductSellingModel&quot;:&quot;0jPxx0000000001EAA&quot;,&quot;PricingSource&quot;:null,&quot;StockKeepingUnit&quot;:null,&quot;PartnerUnitPrice&quot;:130.491,&quot;ItemTotalAdjustmentAmount&quot;:0,&quot;SalesTransactionItemSource&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;ContractAttributePasId&quot;:null,&quot;SubscriptionTerm&quot;:null,&quot;SellingModelType&quot;:&quot;OneTime&quot;,&quot;EndQuantity&quot;:12,&quot;NetTotalPrice&quot;:1739.88,&quot;TotalLineAmount&quot;:1739.88,&quot;ItemSegmentType&quot;:null,&quot;ProductBasedOn&quot;:&quot;11Bxx000002C1nqEAC&quot;,&quot;Deleted&quot;:false,&quot;BillingReference&quot;:null,&quot;ArePartialPeriodsAllowed&quot;:false,&quot;ItemRecordedPrice&quot;:null,&quot;CustomProductName&quot;:null,&quot;ItemSegmentIdentifier&quot;:null,&quot;SalesTransactionItemParent&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Quantity&quot;:12,&quot;PeriodBoundary&quot;:null,&quot;ContractDiscountValue&quot;:null,&quot;LineItemDiscountValue&quot;:null,&quot;ContractId&quot;:null,&quot;EndDate&quot;:null,&quot;ItemGroupSummarySubtotal&quot;:null,&quot;IsContracted&quot;:false,&quot;UnitPrice&quot;:144.99,&quot;StartQuantity&quot;:null,&quot;ContractPrice&quot;:null,&quot;TotalPrice&quot;:1739.88,&quot;LineItemDiscountType&quot;:null,&quot;ItemPath&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;productKey&quot;:[&quot;0QLxx0000004C9VGAU&quot;]}",
"description": "This configuration is saved for reuse.",
"id": "1Nyxx0000004CFUCA2",
"name": "Favorite Configuration",
"referenceRecordId": "01txx0000006iCFAAY"
},
{
"data":
"{&quot;LegalEntity&quot;:null,&quot;ProductName&quot;:&quot;Monitor&quot;,&quot;businessObjectType&quot;:&quot;QuoteLineItem&quot;,&quot;Product&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;ItemIsPrimarySegment&quot;:false,&quot;ListPrice&quot;:144.99,&quot;ValidationResult&quot;:null,&quot;StartDate&quot;:null,&quot;ContractVolumePasId&quot;:null,&quot;BillingTreatment&quot;:null,&quot;PeriodBoundaryStartMonth&quot;:null,&quot;SalesTransactionSourceAsset&quot;:null,&quot;id&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;PartnerDiscountPercent&quot;:10,&quot;PriceWaterFall&quot;:null,&quot;BillingFrequency&quot;:null,&quot;ProductCode&quot;:&quot;MO001&quot;,&quot;DerivedPricingAttribute&quot;:false,&quot;TaxTreatment&quot;:null,&quot;Subtotal&quot;:1739.88,&quot;ItemRampIdentifier&quot;:null,&quot;ItemSegmentName&quot;:null,&quot;SalesTransactionItemAttribute&quot;:[{&quot;AttributeKey&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;AttributeValue&quot;:&quot;1080p
Built-in
Display&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx0000000001AAA&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display&quot;,&quot;id&quot;:&quot;0zuxx000000000FAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;},{&quot;AttributeKey&quot;:&quot;0tjxx0000000009AAA&quot;,&quot;AttributeValue&quot;:&quot;24
Inch&quot;,&quot;ParentReference&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;AttributePicklistValue&quot;:&quot;0v6xx000000000GAAQ&quot;,&quot;IsPriceImpacting&quot;:false,&quot;businessObjectType&quot;:&quot;QuoteLineItemAttribute&quot;,&quot;AttributeName&quot;:&quot;Display_Size&quot;,&quot;id&quot;:&quot;0zuxx000000000GAAQ&quot;,&quot;AttributeDefinitionCode&quot;:null,&quot;SalesTransactionItemAttrParent&quot;:&quot;0QLxx0000004C9VGAU&quot;}],&quot;PricebookEntry&quot;:&quot;01uxx0000008yX0AAI&quot;,&quot;DiscountAmount&quot;:null,&quot;PricingTermCount&quot;:0,&quot;SubscriptionTermUnit&quot;:null,&quot;NetUnitPrice&quot;:144.99,&quot;ItemEffectiveGrantDate&quot;:null,&quot;ProductCategory&quot;:null,&quot;SalesTransactionAction&quot;:null,&quot;SalesTransactionActionType&quot;:null,&quot;SalesTransactionItemGroup&quot;:null,&quot;PeriodBoundaryDay&quot;:null,&quot;SalesTrxnItemDescription&quot;:null,&quot;LineItemDistributionType&quot;:null,&quot;ProrationPolicy&quot;:null,&quot;ContractDiscountType&quot;:null,&quot;TransactionType&quot;:null,&quot;ParentReference&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Discount&quot;:null,&quot;PricingTermUnit&quot;:null,&quot;ProductSellingModel&quot;:&quot;0jPxx0000000001EAA&quot;,&quot;PricingSource&quot;:null,&quot;StockKeepingUnit&quot;:null,&quot;PartnerUnitPrice&quot;:130.491,&quot;ItemTotalAdjustmentAmount&quot;:0,&quot;SalesTransactionItemSource&quot;:&quot;0QLxx0000004C9VGAU&quot;,&quot;ContractAttributePasId&quot;:null,&quot;SubscriptionTerm&quot;:null,&quot;SellingModelType&quot;:&quot;OneTime&quot;,&quot;EndQuantity&quot;:12,&quot;NetTotalPrice&quot;:1739.88,&quot;TotalLineAmount&quot;:1739.88,&quot;ItemSegmentType&quot;:null,&quot;ProductBasedOn&quot;:&quot;11Bxx000002C1nqEAC&quot;,&quot;Deleted&quot;:false,&quot;BillingReference&quot;:null,&quot;ArePartialPeriodsAllowed&quot;:false,&quot;ItemRecordedPrice&quot;:null,&quot;CustomProductName&quot;:null,&quot;ItemSegmentIdentifier&quot;:null,&quot;SalesTransactionItemParent&quot;:&quot;0Q0xx0000004C92CAE&quot;,&quot;Quantity&quot;:12,&quot;PeriodBoundary&quot;:null,&quot;ContractDiscountValue&quot;:null,&quot;LineItemDiscountValue&quot;:null,&quot;ContractId&quot;:null,&quot;EndDate&quot;:null,&quot;ItemGroupSummarySubtotal&quot;:null,&quot;IsContracted&quot;:false,&quot;UnitPrice&quot;:144.99,&quot;StartQuantity&quot;:null,&quot;ContractPrice&quot;:null,&quot;TotalPrice&quot;:1739.88,&quot;LineItemDiscountType&quot;:null,&quot;ItemPath&quot;:&quot;01txx0000006i2aAAA&quot;,&quot;productKey&quot;:[&quot;0QLxx0000004C9VGAU&quot;]}",
"description": "This configuration is saved for reuse.",
"id": "1Nyxx0000004CH6CAM",
"name": "Configuration 2",
"referenceRecordId": "01txx0000006iCFAAY"
}
],
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of errors that contains a message and
an error code.
Error Responseerrors
63.0Small, 63.0Configuration details associated with the
referenceRecordID  request
parameter.
Configuration Save
Details
saved
Configurations
63.0Small, 63.0Indicates whether the operation is
successful (true) or not (false).
Booleansuccess
Configuration Save Instance
Output representation of the response that’s returned with a save configuration request.
930
Response BodiesProduct Configurator

===== PAGE 945 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0List of errors, which contains an error code
and a message.
Error Responseerrors
60.0Small, 60.0Indicates whether the call was successful
(true) not (false).
Booleansuccess
Configuration Set Instance
Output representation of the details of the context or session that are returned with a set configuration request.
JSON Example
{
"configuratorMessages": {},
"configuratorUITreatments": [
{
"details": {
"attributeId": "0tjxx0000000007AAA",
"prcId": "0dSxx0000000007EAA",
"stiId": "0QLxx0000004CU0GAM",
"attributePicklistValueId": "0v6xx0000000005AAA"
},
"uiTreatmentScope": "Bundle",
"uiTreatmentTarget": "Attribute_Picklist_Value",
"uiTreatmentType": "Hide"
},
{
"details": {
"stiId": "ref_f0f2da7b_c431_482d_bf4b_599052f3a2e1"
},
"uiTreatmentScope": "Product",
"uiTreatmentTarget": "Component",
"uiTreatmentType": "Disable"
}
],
"contextId": "831f07b01cf0cbd2d046adf5350420f85f0611b4b1e22e183921a063857a1377",
"errors": [],
"productQualifications": {
"01tDU000000EOTCYA4": {
"isQualified": true
}
},
"success": true
}
931
Response BodiesProduct Configurator

===== PAGE 946 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Map of the product IDs to the list of
configurator messages. Configurator
Map<String,
<Configurator
Message>>
configurator
Messages
messages are results from any validations,
Business Rules Engines (BRE) calls, or
Salesforce Pricing calls.
62.0Small, 62.0Details of the UI treatments that specify the
product configuration rule actions to
Configurator UI
Treatment[]
configurator
UITreatments
override the disable or hide behavior in the
UI for product options, product attributes,
and attribute picklist values.
60.0Small, 60.0ID of the transaction context.StringcontextId
60.0Small, 60.0List of errors, which contains an error code
and a message.
Error Responseerrors
60.0Small, 60.0Map of the product IDs to the execution
results from qualification rules.
Map<String,
Configurator
Qualification
Context>
product
Qualifications
60.0Small, 60.0Indicates whether the call was successful
(true) not (false).
Booleansuccess
Configurator Add Nodes
Output representation of the configuration request details to add nodes.
JSON Example
{
"configuratorMessages": {},
"configuratorUITreatments": [
{
"details": {
"attributeId": "0tjxx0000000007AAA",
"prcId": "0dSxx0000000007EAA",
"stiId": "0QLxx0000004CU0GAM",
"attributePicklistValueId": "0v6xx0000000005AAA"
},
"uiTreatmentScope": "Bundle",
"uiTreatmentTarget": "Attribute_Picklist_Value",
"uiTreatmentType": "Hide"
},
{
"details": {
"stiId": "ref_f0f2da7b_c431_482d_bf4b_599052f3a2e1"
},
"uiTreatmentScope": "Product",
"uiTreatmentTarget": "Component",
932
Response BodiesProduct Configurator

===== PAGE 947 =====

"uiTreatmentType": "Disable"
}
],
"errors": [],
"productQualifications": {
"01tDU000000EOTCYA4": {
"isQualified": true
}
},
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Map of the product IDs to the list of
configurator messages. Configurator
Map<String,
Configurator
Message>
configurator
Messages
messages are results from any validations,
Business Rules Engines (BRE) calls, or
Salesforce Pricing calls.
62.0Small, 62.0Details of the UI treatments that specify the
product configuration rule actions to
Configurator UI
Treatment[]
configurator
UITreatments
override the disable or hide behavior in the
UI for product options, product attributes,
and attribute picklist values.
60.0Small, 60.0List of errors, which contains an error code
and a message.
Error Responseerrors
60.0Small, 60.0Map of the product IDs to the qualification
rule execution results.
Map<String,
Configurator
Qualification
Context>
product
Qualifications
60.0Small, 60.0Indicates whether the call was successful
(true) not (false).
Booleansuccess
Configurator Additional Fields
Output representation of the additional fields of a product configuration.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0API name of the field.StringfieldApiName
60.0Small, 60.0Name of the field.StringfieldName
60.0Small, 60.0Value of the field.Stringvalue
933
Response BodiesProduct Configurator

===== PAGE 948 =====

Configurator Attribute
Output representation of the attribute in a product configuration.
JSON example
"attributeCategories": [
{
"attributes": [
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Load Capacity",
"code": "CAP",
"dataType": "NUMBER",
"defaultValue": "1500",
"description": "Server racks are designed to support a specific load capacity,
commonly measured in kilograms (kg) or pounds (lbs). Typical load capacities range from
500 kg (1102 lbs) to 1500 kg (3307 lbs) depending on the model.",
"id": "0tjxx00000001DpAAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": false,
"label": "Load Capacity",
"name": "Load Capacity"
},
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Expansion Slots",
"code": "SLOTCAP",
"dataType": "NUMBER",
"defaultValue": "12",
"id": "0tjxx00000001H3AAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "Expansion Slots",
"name": "Expansion Slots"
},
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Memory",
"attributePicklist": {
"id": "0v5xx0000000001AAA",
"values": [
{
"code": "MEM",
"displayValue": "25",
"id": "0v6xx0000000001AAA",
934
Response BodiesProduct Configurator

===== PAGE 949 =====

"isBooleanValue": false,
"name": "25Mem",
"sequence": 0,
"textValue": "25"
},
{
"code": "50MEM",
"displayValue": "50",
"id": "0v6xx000000001eAAA",
"isBooleanValue": false,
"name": "50Mem",
"sequence": 1,
"textValue": "50"
},
{
"code": "100MEM",
"displayValue": "100",
"id": "0v6xx000000003FAAQ",
"isBooleanValue": false,
"name": "100Mem",
"sequence": 2,
"textValue": "100"
}
]
},
"dataType": "MULTIPICKLIST",
"defaultValue": "25",
"id": "0tjxx00000001IfAAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "Memory",
"name": "Memory"
}
],
"code": "SPEC",
"name": "Server Rack Specifications"
}
],
"description": "Introducing the Cisco Server Rack, a sleek and robust solution
designed to streamline your data center infrastructure. With its scalable design and
advanced cable management features, it ensures optimal performance, efficiency, and easy
maintenance for your critical network equipment.",
"displayUrl":
"https://www.cisco.com/content/dam/en/us/products/servers-unified-computing/ucs-c240-m4-rack-server/product-large.jpg",
"id": "01txx0000006jkuAAA",
"isActive": true,
"isAssetizable": true,
"isConfigurable": true,
"isSoldOnlyWithOtherProds": false,
935
Response BodiesProduct Configurator

===== PAGE 950 =====

"name": "Cisco Server Rack NX44",
"nodeType": "bundleProduct",
"prices": [],
"productClassification": {
"id": "11Bxx000002CC02EAG"
},
"productCode": "RACK",
"productComponentGroups": [
{
"classifications": [],
"code": "SERVICE",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Service, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jmWAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Service - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "SERVICE",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jmWAAQ",
"childSellingModelId": "0jPxx000000004rEAA",
"doesBundlePriceIncludeChild": true,
"id": "0dSxx000000001dEAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000004rEAA",
"productComponentGroupId": "0y7xx000000001dAAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": [
{
"id": "0iOxx000000009hEAA",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
936
Response BodiesProduct Configurator

===== PAGE 951 =====

"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000PpEAI",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
}
]
}
],
"description": "The services available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx000000001dAAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Services",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 1
},
{
"classifications": [],
"code": "WARRANTY",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Warranty, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jjIAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Warranty - 1 Year",
937
Response BodiesProduct Configurator

===== PAGE 952 =====

"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "WARRANTY",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jjIAAQ",
"childSellingModelId": "0jPxx000000001dEAA",
"doesBundlePriceIncludeChild": false,
"id": "0dSxx0000000001EAA",
"isComponentRequired": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"maxQuantity": 1,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000001dEAA",
"productComponentGroupId": "0y7xx0000000001AAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 0
},
"productSellingModelOptions": [
{
"id": "0iOxx000000001dEAA",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
},
{
"id": "0iOxx00000000HlEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000003FEAQ"
},
{
"id": "0iOxx00000000JNEAY",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
938
Response BodiesProduct Configurator

===== PAGE 953 =====

"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000KzEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
},
{
"id": "0iOxx00000000MbEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000006TEAQ",
"name": "Evergreen Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx000000006TEAQ"
}
]
}
],
"description": "The warranties available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx0000000001AAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Warranties",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 0
}
],
"productSellingModelOptions": [
{
"id": "0iOxx000000003FEAQ",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
939
Response BodiesProduct Configurator

===== PAGE 954 =====

"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
},
{
"id": "0iOxx000000004rEAA",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000003FEAQ"
},
{
"id": "0iOxx000000006TEAQ",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
}
],
"productType": "Bundle"
},
"errors": [],
"success": true,
"transactionContext": {
"SalesTransaction": [
{
"Status": "Draft",
"Account": "001xx000003GeIxAAK",
"BillingCity": "San Francisco",
"Subtotal": 152500,
"LastPricedDate": "2023-08-22T05:55:39Z",
"businessObjectType": "Quote",
"TotalAmount": 152500,
"ShippingStreet": "415 Mission St",
"SalesTransactionItem": [
{
"ProrationPolicy": null,
"Discount": null,
"ProductSellingModel": "0jPxx000000001dEAA",
"Product": "01txx0000006jkuAAA",
"businessObjectType": "QuoteLineItem",
"BasisTransactionItem": null,
940
Response BodiesProduct Configurator

===== PAGE 955 =====

"PartnerUnitPrice": null,
"StartingUnitPriceSource": "System",
"ListPrice": 150000,
"ItemTotalAdjustmentAmount": 0,
"SalesTransactionItemSource": "0QLxx0000004CQmGAM",
"SubscriptionTerm": null,
"StartDate": null,
"NetTotalPrice": 150000,
"TotalLineAmount": 150000,
"PeriodBoundaryStartMonth": null,
"ListPriceTotal": 150000,
"PartnerDiscountPercent": null,
"id": "0QLxx0000004CQmGAM",
"PriceWaterFall": "{
"currencyCode":"USD",
"executionEndTimestamp":"2023-09-18T20:11:15.016Z",
"executionId":"ruepwmHn2ZFvnQo5bjot",
"executionStartTimestamp":"2023-09-18T20:11:14.906Z",
"lineItemId":"0QLxx0000004CQmGAM",
"output":{
"NetUnitPrice":150000.0,
"Subtotal":0.0
},
"success":true,
"waterfall":[
{
"fieldToTagNameMapping":{
"NetUnitPrice":"ItemUnitPrice",
"AdjustmentValue":"ItemAdjustmentValue",
"Subtotal":"ItemTotalAdjustmentAmount",
"Quantity":"ItemQuantity",
"LineItemId":"SalesTransactionItemSource",
"InputUnitPrice":"ItemUnitPrice"
},
"inputParameters":{
"Quantity":1.0,
"LineItemId":"0QLxx0000004CQmGAM",
"InputUnitPrice":150000.0,
"AdjustmentType":"Amount"
},
"outputParameters":{
"NetUnitPrice":150000.0,
"Subtotal":0.0
},
"pricingElement":{
"adjustments":[
{
"AdjustmentType":"Amount"
}
],
"elementType":"MANUALDISCOUNT",
"name":"ManualDiscount"
},
"sequence":1
941
Response BodiesProduct Configurator

===== PAGE 956 =====

}
]
}",
"BillingFrequency": null,
"SalesTransactionItemParent": "0Q0xx0000004CAeCAM",
"StartingPriceTotal": 150000,
"Quantity": 1,
"PeriodBoundary": null,
"SalesTransactionItemAttribute": [
{
"AttributeKey": "0tjxx00000001H3AAI",
"AttributeValue": "30.0",
"AttributePicklistValue": null,
"IsPriceImpacting": true,
"businessObjectType": "QuoteLineItemAttribute",
"AttributeName": "Expansion Slots",
"AttributeDefinitionCode": "SLOTCAP",
"id": "0zuxx0000000001AAA",
"SalesTransactionItemAttrParent": "0QLxx0000004CQmGAM"
}
],
"EndDate": null,
"DiscountAmount": null,
"PricebookEntry": "01uxx0000009154AAA",
"PricingTermCount": 1,
"NetUnitPrice": 150000,
"UnitPrice": 150000,
"StartingUnitPrice": 150000,
"SalesTrxnItemRelationship": [
{
"ProductRelationshipType": "0yoxx00000001IfAAI",
"MainItemRole": "Bundle",
"AssociatedItem": "0QLxx0000004CQnGAM",
"ProductRelatedComponent": "0dSxx0000000001EAA",
"MainItem": "0QLxx0000004CQmGAM",
"AssociatedQuantScaleMethod": "Proportional",
"businessObjectType": "QuoteLineRelationship",
"AssociatedItemRole": "BundleComponent",
"SalesTrnItemRelationshipParent": "0Q0xx0000004CAeCAM",
"id": "0yQxx000000001dEAA",
"AssociatedItemPricing": "NotIncludedInBundlePrice"
}
],
"TotalPrice": 150000,
"PeriodBoundaryDay": null
},
{
"ProrationPolicy": null,
"Discount": null,
"ProductSellingModel": "0jPxx000000001dEAA",
"Product": "01txx0000006jjIAAQ",
"businessObjectType": "QuoteLineItem",
"BasisTransactionItem": null,
"PartnerUnitPrice": null,
942
Response BodiesProduct Configurator

===== PAGE 957 =====

"StartingUnitPriceSource": "System",
"ListPrice": 2000,
"ItemTotalAdjustmentAmount": 0,
"SalesTransactionItemSource": "0QLxx0000004CQnGAM",
"SubscriptionTerm": null,
"StartDate": null,
"NetTotalPrice": 2000,
"TotalLineAmount": 2000,
"PeriodBoundaryStartMonth": null,
"ListPriceTotal": 2000,
"PartnerDiscountPercent": null,
"id": "0QLxx0000004CQnGAM",
"PriceWaterFall": "{
"currencyCode":"USD",
"executionEndTimestamp":"023-09-18T20:11:15.016Z",
"executionId":"ruepwmHn2ZFvnQo5bjot",
"executionStartTimestamp":"2023-09-18T20:11:14.906Z",
"lineItemId":"0QLxx0000004CQnGAM",
"output":{
"NetUnitPrice":2000.0,
"Subtotal":0.0
},
"success":true,
"waterfall":[
{
"fieldToTagNameMapping":{
"NetUnitPrice":"ItemUnitPrice",
"AdjustmentValue":"ItemAdjustmentValue",
"Subtotal":"ItemTotalAdjustmentAmount",
"Quantity":"ItemQuantity",
"LineItemId":"SalesTransactionItemSource",
"InputUnitPrice":"ItemUnitPrice"
},
"inputParameters":{
"Quantity":1.0,
"LineItemId":"0QLxx0000004CQnGAM",
"InputUnitPrice":2000.0,
"AdjustmentType":"Amount"
},
"outputParameters":{
"NetUnitPrice":2000.0,
"Subtotal":0.0
},
"pricingElement":{
"adjustments":[
{}
],
"elementType":"MANUALDISCOUNT",
"name":"ManualDiscount"
},
"sequence":1
}
]
}",
943
Response BodiesProduct Configurator

===== PAGE 958 =====

"BillingFrequency": null,
"SalesTransactionItemParent": "0Q0xx0000004CAeCAM",
"StartingPriceTotal": 2000,
"Quantity": 1,
"PeriodBoundary": null,
"EndDate": null,
"DiscountAmount": null,
"PricebookEntry": "01uxx000000913SAAQ",
"PricingTermCount": 1,
"NetUnitPrice": 2000,
"UnitPrice": 2000,
"StartingUnitPrice": 2000,
"TotalPrice": 2000,
"PeriodBoundaryDay": null
}
],
"BillingCountry": "US",
"BillingStreet": "415 Mission St",
"Pricebook": "01sxx0000005uDZAAY",
"ShippingPostalCode": "94105",
"SalesTransactionSource": "0Q0xx0000004CAeCAM",
"ShippingCountry": "US",
"ShippingCity": "San Francisco",
"ShippingState": "CA",
"BillingPostalCode": "94105",
"id": "0Q0xx0000004CAeCAM",
"BillToContact": null,
"Contract": null,
"BillingState": "CA"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the attribute category.Stringattribute
CategoryId
60.0Small, 60.0Name override value of the attribute.Stringattribute
NameOverride
60.0Small, 60.0Picklist values of the attribute.Configurator
Attribute Picklist[]
attribute
Picklist
60.0Small, 60.0Code of the attribute.Stringcode
60.0Small, 60.0Data type of the attribute.StringdataType
60.0Small, 60.0Default help text value of the attribute.Stringdefault
HelpText
60.0Small, 60.0Default value of the attribute.StringdefaultValue
60.0Small, 60.0Description of the attribute.Stringdescription
60.0Small, 60.0Display type of the attribute.StringdisplayType
944
Response BodiesProduct Configurator

===== PAGE 959 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the attribute.Stringid
60.0Small, 60.0Indicates if the attribute is cloneable (true)
or not (false).
BooleanisCloneable
60.0Small, 60.0Indicates if the attribute is configurable
(true) or not (false).
Booleanis
Configurable
60.0Small, 60.0Indicates if the attribute is encrypted
(true) or not (false).
BooleanisEncrypted
60.0Small, 60.0Indicates if the attribute is hidden (true)
or not (false).
BooleanisHidden
60.0Small, 60.0Indicates if this is a price impacting attribute
(true) or not (false).
BooleanisPrice
Impacting
60.0Small, 60.0Indicates if the attribute is read-only (true)
or not (false).
BooleanisReadOnly
60.0Small, 60.0Indicates if the attribute is required (true)
or not (false).
BooleanisRequired
60.0Small, 60.0Label of the attribute.Stringlabel
60.0Small, 60.0Maximum value for the product attribute.StringmaximumValue
60.0Small, 60.0Minimum value for the product attribute.StringminimumValue
60.0Small, 60.0Name of the attribute.Stringname
60.0Small, 60.0Sequence values of the attribute.Integersequence
60.0Small, 60.0Status of the attribute.Stringstatus
60.0Small, 60.0Step value for the attribute.StringstepValue
63.0Small, 63.0Details about the unit of measure associated
with an attribute.
Configurator Unit Of
Measure[]
unitOfMeasure
60.0Small, 60.0User value of the attribute.StringuserValue
60.0Small, 60.0Value decoder for the attribute.StringvalueDecoder
60.0Small, 60.0Value description of the attribute.Stringvalue
Description
Configurator Attribute Category
Output representation of the attribute category in a product configuration.
945
Response BodiesProduct Configurator

===== PAGE 960 =====

JSON example
"attributeCategories": [
{
"attributes": [
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Load Capacity",
"code": "CAP",
"dataType": "NUMBER",
"defaultValue": "1500",
"description": "Server racks are designed to support a specific load capacity,
commonly measured in kilograms (kg) or pounds (lbs). Typical load capacities range from
500 kg (1102 lbs) to 1500 kg (3307 lbs) depending on the model.",
"id": "0tjxx00000001DpAAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": false,
"label": "Load Capacity",
"name": "Load Capacity"
},
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Expansion Slots",
"code": "SLOTCAP",
"dataType": "NUMBER",
"defaultValue": "12",
"id": "0tjxx00000001H3AAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "Expansion Slots",
"name": "Expansion Slots"
},
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Memory",
"attributePicklist": {
"id": "0v5xx0000000001AAA",
"values": [
{
"code": "MEM",
"displayValue": "25",
"id": "0v6xx0000000001AAA",
"isBooleanValue": false,
"name": "25Mem",
"sequence": 0,
946
Response BodiesProduct Configurator

===== PAGE 961 =====

"textValue": "25"
},
{
"code": "50MEM",
"displayValue": "50",
"id": "0v6xx000000001eAAA",
"isBooleanValue": false,
"name": "50Mem",
"sequence": 1,
"textValue": "50"
},
{
"code": "100MEM",
"displayValue": "100",
"id": "0v6xx000000003FAAQ",
"isBooleanValue": false,
"name": "100Mem",
"sequence": 2,
"textValue": "100"
}
]
},
"dataType": "MULTIPICKLIST",
"defaultValue": "25",
"id": "0tjxx00000001IfAAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "Memory",
"name": "Memory"
}
],
"code": "SPEC",
"name": "Server Rack Specifications"
}
],
"description": "Introducing the Cisco Server Rack, a sleek and robust solution
designed to streamline your data center infrastructure. With its scalable design and
advanced cable management features, it ensures optimal performance, efficiency, and easy
maintenance for your critical network equipment.",
"displayUrl":
"https://www.cisco.com/content/dam/en/us/products/servers-unified-computing/ucs-c240-m4-rack-server/product-large.jpg",
"id": "01txx0000006jkuAAA",
"isActive": true,
"isAssetizable": true,
"isConfigurable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Server Rack NX44",
"nodeType": "bundleProduct",
"prices": [],
947
Response BodiesProduct Configurator

===== PAGE 962 =====

"productClassification": {
"id": "11Bxx000002CC02EAG"
},
"productCode": "RACK",
"productComponentGroups": [
{
"classifications": [],
"code": "SERVICE",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Service, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jmWAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Service - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "SERVICE",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jmWAAQ",
"childSellingModelId": "0jPxx000000004rEAA",
"doesBundlePriceIncludeChild": true,
"id": "0dSxx000000001dEAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000004rEAA",
"productComponentGroupId": "0y7xx000000001dAAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": [
{
"id": "0iOxx000000009hEAA",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
948
Response BodiesProduct Configurator

===== PAGE 963 =====

"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000PpEAI",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
}
]
}
],
"description": "The services available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx000000001dAAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Services",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 1
},
{
"classifications": [],
"code": "WARRANTY",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Warranty, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jjIAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Warranty - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
949
Response BodiesProduct Configurator

===== PAGE 964 =====

"productCode": "WARRANTY",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jjIAAQ",
"childSellingModelId": "0jPxx000000001dEAA",
"doesBundlePriceIncludeChild": false,
"id": "0dSxx0000000001EAA",
"isComponentRequired": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"maxQuantity": 1,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000001dEAA",
"productComponentGroupId": "0y7xx0000000001AAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 0
},
"productSellingModelOptions": [
{
"id": "0iOxx000000001dEAA",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
},
{
"id": "0iOxx00000000HlEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000003FEAQ"
},
{
"id": "0iOxx00000000JNEAY",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
950
Response BodiesProduct Configurator

===== PAGE 965 =====

},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000KzEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
},
{
"id": "0iOxx00000000MbEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000006TEAQ",
"name": "Evergreen Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx000000006TEAQ"
}
]
}
],
"description": "The warranties available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx0000000001AAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Warranties",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 0
}
],
"productSellingModelOptions": [
{
"id": "0iOxx000000003FEAQ",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
951
Response BodiesProduct Configurator

===== PAGE 966 =====

},
{
"id": "0iOxx000000004rEAA",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000003FEAQ"
},
{
"id": "0iOxx000000006TEAQ",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
}
],
"productType": "Bundle"
},
"errors": [],
"success": true,
"transactionContext": {
"SalesTransaction": [
{
"Status": "Draft",
"Account": "001xx000003GeIxAAK",
"BillingCity": "San Francisco",
"Subtotal": 152500,
"LastPricedDate": "2023-08-22T05:55:39Z",
"businessObjectType": "Quote",
"TotalAmount": 152500,
"ShippingStreet": "415 Mission St",
"SalesTransactionItem": [
{
"ProrationPolicy": null,
"Discount": null,
"ProductSellingModel": "0jPxx000000001dEAA",
"Product": "01txx0000006jkuAAA",
"businessObjectType": "QuoteLineItem",
"BasisTransactionItem": null,
"PartnerUnitPrice": null,
"StartingUnitPriceSource": "System",
"ListPrice": 150000,
952
Response BodiesProduct Configurator

===== PAGE 967 =====

"ItemTotalAdjustmentAmount": 0,
"SalesTransactionItemSource": "0QLxx0000004CQmGAM",
"SubscriptionTerm": null,
"StartDate": null,
"NetTotalPrice": 150000,
"TotalLineAmount": 150000,
"PeriodBoundaryStartMonth": null,
"ListPriceTotal": 150000,
"PartnerDiscountPercent": null,
"id": "0QLxx0000004CQmGAM",
"PriceWaterFall": "{
"currencyCode":"USD",
"executionEndTimestamp":"2023-09-18T20:11:15.016Z",
"executionId":"ruepwmHn2ZFvnQo5bjot",
"executionStartTimestamp":"2023-09-18T20:11:14.906Z",
"lineItemId":"0QLxx0000004CQmGAM",
"output":{
"NetUnitPrice":150000.0,
"Subtotal":0.0
},
"success":true,
"waterfall":[
{
"fieldToTagNameMapping":{
"NetUnitPrice":"ItemUnitPrice",
"AdjustmentValue":"ItemAdjustmentValue",
"Subtotal":"ItemTotalAdjustmentAmount",
"Quantity":"ItemQuantity",
"LineItemId":"SalesTransactionItemSource",
"InputUnitPrice":"ItemUnitPrice"
},
"inputParameters":{
"Quantity":1.0,
"LineItemId":"0QLxx0000004CQmGAM",
"InputUnitPrice":150000.0,
"AdjustmentType":"Amount"
},
"outputParameters":{
"NetUnitPrice":150000.0,
"Subtotal":0.0
},
"pricingElement":{
"adjustments":[
{
"AdjustmentType":"Amount"
}
],
"elementType":"MANUALDISCOUNT",
"name":"ManualDiscount"
},
"sequence":1
}
]
}",
953
Response BodiesProduct Configurator

===== PAGE 968 =====

"BillingFrequency": null,
"SalesTransactionItemParent": "0Q0xx0000004CAeCAM",
"StartingPriceTotal": 150000,
"Quantity": 1,
"PeriodBoundary": null,
"SalesTransactionItemAttribute": [
{
"AttributeKey": "0tjxx00000001H3AAI",
"AttributeValue": "30.0",
"AttributePicklistValue": null,
"IsPriceImpacting": true,
"businessObjectType": "QuoteLineItemAttribute",
"AttributeName": "Expansion Slots",
"AttributeDefinitionCode": "SLOTCAP",
"id": "0zuxx0000000001AAA",
"SalesTransactionItemAttrParent": "0QLxx0000004CQmGAM"
}
],
"EndDate": null,
"DiscountAmount": null,
"PricebookEntry": "01uxx0000009154AAA",
"PricingTermCount": 1,
"NetUnitPrice": 150000,
"UnitPrice": 150000,
"StartingUnitPrice": 150000,
"SalesTrxnItemRelationship": [
{
"ProductRelationshipType": "0yoxx00000001IfAAI",
"MainItemRole": "Bundle",
"AssociatedItem": "0QLxx0000004CQnGAM",
"ProductRelatedComponent": "0dSxx0000000001EAA",
"MainItem": "0QLxx0000004CQmGAM",
"AssociatedQuantScaleMethod": "Proportional",
"businessObjectType": "QuoteLineRelationship",
"AssociatedItemRole": "BundleComponent",
"SalesTrnItemRelationshipParent": "0Q0xx0000004CAeCAM",
"id": "0yQxx000000001dEAA",
"AssociatedItemPricing": "NotIncludedInBundlePrice"
}
],
"TotalPrice": 150000,
"PeriodBoundaryDay": null
},
{
"ProrationPolicy": null,
"Discount": null,
"ProductSellingModel": "0jPxx000000001dEAA",
"Product": "01txx0000006jjIAAQ",
"businessObjectType": "QuoteLineItem",
"BasisTransactionItem": null,
"PartnerUnitPrice": null,
"StartingUnitPriceSource": "System",
"ListPrice": 2000,
"ItemTotalAdjustmentAmount": 0,
954
Response BodiesProduct Configurator

===== PAGE 969 =====

"SalesTransactionItemSource": "0QLxx0000004CQnGAM",
"SubscriptionTerm": null,
"StartDate": null,
"NetTotalPrice": 2000,
"TotalLineAmount": 2000,
"PeriodBoundaryStartMonth": null,
"ListPriceTotal": 2000,
"PartnerDiscountPercent": null,
"id": "0QLxx0000004CQnGAM",
"PriceWaterFall": "{
"currencyCode":"USD",
"executionEndTimestamp":"023-09-18T20:11:15.016Z",
"executionId":"ruepwmHn2ZFvnQo5bjot",
"executionStartTimestamp":"2023-09-18T20:11:14.906Z",
"lineItemId":"0QLxx0000004CQnGAM",
"output":{
"NetUnitPrice":2000.0,
"Subtotal":0.0
},
"success":true,
"waterfall":[
{
"fieldToTagNameMapping":{
"NetUnitPrice":"ItemUnitPrice",
"AdjustmentValue":"ItemAdjustmentValue",
"Subtotal":"ItemTotalAdjustmentAmount",
"Quantity":"ItemQuantity",
"LineItemId":"SalesTransactionItemSource",
"InputUnitPrice":"ItemUnitPrice"
},
"inputParameters":{
"Quantity":1.0,
"LineItemId":"0QLxx0000004CQnGAM",
"InputUnitPrice":2000.0,
"AdjustmentType":"Amount"
},
"outputParameters":{
"NetUnitPrice":2000.0,
"Subtotal":0.0
},
"pricingElement":{
"adjustments":[
{}
],
"elementType":"MANUALDISCOUNT",
"name":"ManualDiscount"
},
"sequence":1
}
]
}",
"BillingFrequency": null,
"SalesTransactionItemParent": "0Q0xx0000004CAeCAM",
"StartingPriceTotal": 2000,
955
Response BodiesProduct Configurator

===== PAGE 970 =====

"Quantity": 1,
"PeriodBoundary": null,
"EndDate": null,
"DiscountAmount": null,
"PricebookEntry": "01uxx000000913SAAQ",
"PricingTermCount": 1,
"NetUnitPrice": 2000,
"UnitPrice": 2000,
"StartingUnitPrice": 2000,
"TotalPrice": 2000,
"PeriodBoundaryDay": null
}
],
"BillingCountry": "US",
"BillingStreet": "415 Mission St",
"Pricebook": "01sxx0000005uDZAAY",
"ShippingPostalCode": "94105",
"SalesTransactionSource": "0Q0xx0000004CAeCAM",
"ShippingCountry": "US",
"ShippingCity": "San Francisco",
"ShippingState": "CA",
"BillingPostalCode": "94105",
"id": "0Q0xx0000004CAeCAM",
"BillToContact": null,
"Contract": null,
"BillingState": "CA"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Attributes of the attribute category.Configurator
Attribute[]
attributes
60.0Small, 60.0Code of the attribute category.Stringcode
60.0Small, 60.0Description of the attribute category.Stringdescription
60.0Small, 60.0ID of the attribute category.Stringid
60.0Small, 60.0Name of the attribute category.Stringname
60.0Small, 60.0Status of the attribute category.Stringstatus
60.0Small, 60.0Total size of the attribute category.IntegertotalSize
60.0Small, 60.0Usage type of the attribute category.StringusageType
Configurator Attribute Picklist
Output representation of the attribute picklist in a product configuration.
956
Response BodiesProduct Configurator

===== PAGE 971 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Description of the attribute picklist.Stringdescription
60.0Small, 60.0ID of the attribute picklist.Stringid
60.0Small, 60.0Name of the attribute picklist.Stringname
60.0Small, 60.0Status of the attribute picklist.Stringstatus
60.0Small, 60.0Values of the attribute picklist.Configurator
Attribute Picklist
Value[]
values
Configurator Attribute Picklist Value
Output representation of the values of an attribute picklist in a product configuration.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Code of the attribute value.Stringcode
60.0Small, 60.0Description of the attribute value.Stringdescription
60.0Small, 60.0Display value of the attribute value.StringdisplayValue
60.0Small, 60.0ID of the attribute value.Stringid
60.0Small, 60.0Indicates if this attribute value is a boolean
value (true) or not (false).
BooleanisBoolean
Value
60.0Small, 60.0Label of the attribute value.Stringlabel
60.0Small, 60.0Name of the attribute value.Stringname
60.0Small, 60.0Sequence of the attribute value.Integersequence
60.0Small, 60.0Status of the attribute value.Stringstatus
60.0Small, 60.0Text value of the attribute value.StringtextValue
Configurator Delete Nodes
Output representation of the details of the configuration request to delete nodes.
JSON Example
{
"configuratorMessages": {},
"configuratorUITreatments": [
{
"details": {
"attributeId": "0tjxx0000000007AAA",
957
Response BodiesProduct Configurator

===== PAGE 972 =====

"prcId": "0dSxx0000000007EAA",
"stiId": "0QLxx0000004CU0GAM",
"attributePicklistValueId": "0v6xx0000000005AAA"
},
"uiTreatmentScope": "Bundle",
"uiTreatmentTarget": "Attribute_Picklist_Value",
"uiTreatmentType": "Hide"
},
{
"details": {
"stiId": "ref_f0f2da7b_c431_482d_bf4b_599052f3a2e1"
},
"uiTreatmentScope": "Product",
"uiTreatmentTarget": "Component",
"uiTreatmentType": "Disable"
}
],
"errors": [],
"productQualifications": {
"01tDU000000EOTCYA4": {
"isQualified": true
}
},
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Map of the product IDs to the list of
configurator messages. Configurator
Map<String,
Configurator
Message>
configurator
Messages
messages are results from any validations,
Business Rules Engine (BRE) calls, or
Salesforce Pricing calls.
62.0Small, 62.0Details of the UI treatments that specify the
product configuration rule actions to
Configurator UI
Treatment[]
configurator
UITreatments
override the disable or hide behavior in the
UI for product options, product attributes,
and attribute picklist values.
60.0Small, 60.0List of errors, which contains an error code
and a message.
Error Responseerrors
60.0Small, 60.0Map of the product IDs to the qualification
rule execution results.
Map<String,
Configurator
Qualification
Context>
product
Qualifications
60.0Small, 60.0Indicates whether the call was successful
(true) not (false).
Booleansuccess
958
Response BodiesProduct Configurator

===== PAGE 973 =====

Configurator Message
Output representation of the messages of a product configurator.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Category or type of the error message. Valid
values are:
Stringcategory
• ArcResolutionService
• ArcValidationService
• BundleValidation
• ConfigurationRules
• Pricing
60.0Small, 60.0Message that contains the error details.Stringmessage
60.0Small, 60.0Type of error message. Valid values are:StringmessageType
• Error
• Info
• Warning
60.0Small, 60.0Primary record ID that contains the error.Stringprimary
RecordId
60.0Small, 60.0Related record ID for the error, if any.Stringrelated
RecordId
Configurator Price
Output representation of the pricing details in a product configuration.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Currency ISO code of the price book entry.Stringcurrency
IsoCode
60.0Small, 60.0Date from when the price book entry is
effective.
StringeffectiveFrom
60.0Small, 60.0Date until when the price book entry is
effective.
StringeffectiveTo
60.0Small, 60.0Indicates if this price book entry is the
default pricing model (true) or not
(false).
BooleanisDefault
959
Response BodiesProduct Configurator

===== PAGE 974 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Indicates if this price book entry is selected
(true) or not (false).
BooleanisSelected
60.0Small, 60.0ID of the price book entry.Stringpricebook
EntryId
60.0Small, 60.0Pricebook2 ID of the price book entry.StringpricebookId
60.0Small, 60.0Pricing model details of the price book entry.Configurator Pricing
Model[]
pricingModel
60.0Small, 60.0Unit price of the price book entry.DoubleunitPrice
Configurator Pricing Model
Output representation of the details of a pricing model in a product configuration.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Frequency of the pricing model.Stringfrequency
60.0Small, 60.0ID of the pricing model.Stringid
60.0Small, 60.0Name of the pricing model.Stringname
60.0Small, 60.0Occurrence of the pricing model.Integeroccurrence
60.0Small, 60.0Type of the pricing model.Stringpricing
ModelType
60.0Small, 60.0Unit of measure for the pricing model.StringunitOfMeasure
Configurator Product Catalog
Output representation of the product catalog.
JSON example
"catalogProducts": {
"additionalFields": [],
"attributeCategories": [
{
"attributes": [
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Load Capacity",
"code": "CAP",
"dataType": "NUMBER",
"defaultValue": "1500",
960
Response BodiesProduct Configurator

===== PAGE 975 =====

"description": "Server racks are designed to support a specific load capacity,
commonly measured in kilograms (kg) or pounds (lbs). Typical load capacities range from
500 kg (1102 lbs) to 1500 kg (3307 lbs) depending on the model.",
"id": "0tjxx00000001DpAAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": false,
"label": "Load Capacity",
"name": "Load Capacity"
},
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Expansion Slots",
"code": "SLOTCAP",
"dataType": "NUMBER",
"defaultValue": "12",
"id": "0tjxx00000001H3AAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "Expansion Slots",
"name": "Expansion Slots"
},
{
"attributeCategoryId": "0v3xx0000000001AAA",
"attributeNameOverride": "Memory",
"attributePicklist": {
"id": "0v5xx0000000001AAA",
"values": [
{
"code": "MEM",
"displayValue": "25",
"id": "0v6xx0000000001AAA",
"isBooleanValue": false,
"name": "25Mem",
"sequence": 0,
"textValue": "25"
},
{
"code": "50MEM",
"displayValue": "50",
"id": "0v6xx000000001eAAA",
"isBooleanValue": false,
"name": "50Mem",
"sequence": 1,
"textValue": "50"
},
{
961
Response BodiesProduct Configurator

===== PAGE 976 =====

"code": "100MEM",
"displayValue": "100",
"id": "0v6xx000000003FAAQ",
"isBooleanValue": false,
"name": "100Mem",
"sequence": 2,
"textValue": "100"
}
]
},
"dataType": "MULTIPICKLIST",
"defaultValue": "25",
"id": "0tjxx00000001IfAAI",
"isCloneable": false,
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "Memory",
"name": "Memory"
}
],
"code": "SPEC",
"name": "Server Rack Specifications"
}
],
"description": "Introducing the Cisco Server Rack, a sleek and robust solution
designed to streamline your data center infrastructure. With its scalable design and
advanced cable management features, it ensures optimal performance, efficiency, and easy
maintenance for your critical network equipment.",
"displayUrl":
"https://www.cisco.com/content/dam/en/us/products/servers-unified-computing/ucs-c240-m4-rack-server/product-large.jpg",
"id": "01txx0000006jkuAAA",
"isActive": true,
"isAssetizable": true,
"isConfigurable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Server Rack NX44",
"nodeType": "bundleProduct",
"prices": [],
"productClassification": {
"id": "11Bxx000002CC02EAG"
},
"productCode": "RACK",
"productComponentGroups": [
{
"classifications": [],
"code": "SERVICE",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
962
Response BodiesProduct Configurator

===== PAGE 977 =====

"description": "Introducing the Cisco Rack Server NX44 Service, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jmWAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Service - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "SERVICE",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jmWAAQ",
"childSellingModelId": "0jPxx000000004rEAA",
"doesBundlePriceIncludeChild": true,
"id": "0dSxx000000001dEAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000004rEAA",
"productComponentGroupId": "0y7xx000000001dAAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": [
{
"id": "0iOxx000000009hEAA",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000PpEAI",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
963
Response BodiesProduct Configurator

===== PAGE 978 =====

"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
}
]
}
],
"description": "The services available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx000000001dAAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Services",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 1
},
{
"classifications": [],
"code": "WARRANTY",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Warranty, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jjIAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Warranty - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "WARRANTY",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jjIAAQ",
"childSellingModelId": "0jPxx000000001dEAA",
"doesBundlePriceIncludeChild": false,
"id": "0dSxx0000000001EAA",
"isComponentRequired": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"maxQuantity": 1,
"parentProductId": "01txx0000006jkuAAA",
964
Response BodiesProduct Configurator

===== PAGE 979 =====

"parentSellingModelId": "0jPxx000000001dEAA",
"productComponentGroupId": "0y7xx0000000001AAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 0
},
"productSellingModelOptions": [
{
"id": "0iOxx000000001dEAA",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
},
{
"id": "0iOxx00000000HlEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000003FEAQ"
},
{
"id": "0iOxx00000000JNEAY",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000KzEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
965
Response BodiesProduct Configurator

===== PAGE 980 =====

"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
},
{
"id": "0iOxx00000000MbEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000006TEAQ",
"name": "Evergreen Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx000000006TEAQ"
}
]
}
],
"description": "The warranties available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx0000000001AAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Warranties",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 0
}
],
"productSellingModelOptions": [
{
"id": "0iOxx000000003FEAQ",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
},
{
"id": "0iOxx000000004rEAA",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
966
Response BodiesProduct Configurator

===== PAGE 981 =====

"productSellingModelId": "0jPxx000000003FEAQ"
},
{
"id": "0iOxx000000006TEAQ",
"productId": "01txx0000006jkuAAA",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
}
],
"productType": "Bundle"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Additional fields for this product.Configurator
Additional Fields[]
additional
Fields
60.0Small, 60.0List of attribute categories. The categories
that aren’t categorized are specified in the
uncategorized entry in this list.
Configurator
Attribute Category[]
attribute
Categories
60.0Small, 60.0Availability date of this product.Stringavailability
Date
60.0Small, 60.0Description of this product.Stringdescription
60.0Small, 60.0Date when this product is discontinued.Stringdiscontinued
Date
60.0Small, 60.0Display URL of this product.StringdisplayUrl
60.0Small, 60.0End of life date for this product.StringendOfLifeDate
60.0Small, 60.0ID of the product.Stringid
60.0Small, 60.0Indicates whether this product is active
(true) or not (false).
BooleanisActive
60.0Small, 60.0Indicates whether this product is assetizable
(true) or not (false).
BooleanisAssetizable
60.0Small, 60.0Indicates whether the component is
required (true) or not (false).
BooleanisComponent
Required
60.0Small, 60.0Indicates whether the component is
configurable (true) or not (false).
Booleanis
Configurable
967
Response BodiesProduct Configurator

===== PAGE 982 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Indicates whether the component is a
default component (true) or not (false).
BooleanisDefault
Component
60.0Small, 60.0Indicates whether the quantity of the
component is editable ( true) or not
(false).
BooleanisQuantity
Editable
60.0Small, 60.0Indicates whether this product is sold only
with other products (true) or not
(false).
BooleanisSoldOnly
WithOtherProds
60.0Small, 60.0Name of the product.Stringname
60.0Small, 60.0Node type of the product.StringnodeType
60.0Small, 60.0List of prices from the product catalog.Configurator Price[]prices
60.0Small, 60.0Classification details of the product.Configurator Product
Classification[]
product
Classification
60.0Small, 60.0Code of the product.StringproductCode
60.0Small, 60.0List of product component groups for this
product.
Configurator Product
Component Group[]
product
ComponentGroups
60.0Small, 60.0Details of the product related component
of this product.
Configurator Product
Related
Component[]
product
RelatedComponent
60.0Small, 60.0List of product selling model options for this
product.
Configurator Product
Selling Model
Option[]
productSelling
ModelOptions
60.0Small, 60.0Type of product.StringproductType
60.0Small, 60.0Details of the qualification context of the
product.
Configurator
Qualification
Context[]
qualification
Context
60.0Small, 60.0Status of the product.Stringstatus
63.0Small, 63.0Details about the unit of measure associated
with a product.
Configurator Unit Of
Measure[]
unitOfMeasure
Configurator Product Classification
Output representation of the product classification in a product configuration.
JSON example
"productClassification": {
968
Response BodiesProduct Configurator

===== PAGE 983 =====

"id": "11Bxx000002CC02EAG"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the product classification.Stringid
Configurator Product Component Group
Output representation of the product component group in a product classification.
JSON example
"productComponentGroups": [
{
"classifications": [],
"code": "SERVICE",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Service, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jmWAAQ",
"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Service - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "SERVICE",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jmWAAQ",
"childSellingModelId": "0jPxx000000004rEAA",
"doesBundlePriceIncludeChild": true,
"id": "0dSxx000000001dEAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000004rEAA",
"productComponentGroupId": "0y7xx000000001dAAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
969
Response BodiesProduct Configurator

===== PAGE 984 =====

"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": [
{
"id": "0iOxx000000009hEAA",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000PpEAI",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
}
]
}
],
"description": "The services available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx000000001dAAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Services",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 1
},
{
"classifications": [],
"code": "WARRANTY",
"components": [
{
"additionalFields": [],
"attributeCategories": [],
"description": "Introducing the Cisco Rack Server NX44 Warranty, a
comprehensive protection plan designed to safeguard your valuable data infrastructure.
With extended coverage and rapid response times, this warranty ensures peace of mind
and uninterrupted performance for your critical business operations.",
"id": "01txx0000006jjIAAQ",
970
Response BodiesProduct Configurator

===== PAGE 985 =====

"isActive": true,
"isAssetizable": true,
"isComponentRequired": false,
"isConfigurable": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Cisco Rack Server Warranty - 1 Year",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {},
"productCode": "WARRANTY",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01txx0000006jjIAAQ",
"childSellingModelId": "0jPxx000000001dEAA",
"doesBundlePriceIncludeChild": false,
"id": "0dSxx0000000001EAA",
"isComponentRequired": false,
"isDefaultComponent": true,
"isQuantityEditable": true,
"maxQuantity": 1,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000001dEAA",
"productComponentGroupId": "0y7xx0000000001AAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 0
},
"productSellingModelOptions": [
{
"id": "0iOxx000000001dEAA",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000001dEAA",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000001dEAA"
},
{
"id": "0iOxx00000000HlEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000003FEAQ",
"name": "Termed Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000003FEAQ"
971
Response BodiesProduct Configurator

===== PAGE 986 =====

},
{
"id": "0iOxx00000000JNEAY",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000KzEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
},
{
"id": "0iOxx00000000MbEAI",
"productId": "01txx0000006jjIAAQ",
"productSellingModel": {
"id": "0jPxx000000006TEAQ",
"name": "Evergreen Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx000000006TEAQ"
}
]
}
],
"description": "The warranties available for the Cisco Server Rack NX44 product
provide comprehensive coverage and support for optimal performance and reliability,
ensuring peace of mind for your data center infrastructure.",
"id": "0y7xx0000000001AAA",
"maxBundleComponents": 1,
"minBundleComponents": 0,
"name": "Warranties",
"parentProductId": "01txx0000006jkuAAA",
"sequence": 0
}
]
972
Response BodiesProduct Configurator

===== PAGE 987 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0List of classifications for this product
component group.
Configurator Product
Classification[]
classifications
60.0Small, 60.0Code of the product component group.Stringcode
60.0Small, 60.0Components within the product
component group.
Configurator Product
Catalog[]
components
60.0Small, 60.0Description of the product component
group.
Stringdescription
60.0Small, 60.0ID of the product component group.Stringid
60.0Small, 60.0Maximum number of bundle components
within the product component group.
IntegermaxBundle
Components
60.0Small, 60.0Minimum number of bundle components
within the product component group.
IntegerminBundle
Components
60.0Small, 60.0Name of the product component group.Stringname
60.0Small, 60.0Parent Product2 ID of the product
component group.
Stringparent
ProductId
60.0Small, 60.0Sequence of the product component group.Integersequence
Configurator Product Recommendations
Output representation of the details of the product recommendations.
JSON Example
{
"productRecommendations": [
{
"referenceId": "CORE_BUNDLE_001",
"productIds": [
"01t000000001234",
"01t000000005678"
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0List of recommended product IDs.String[]productIds
65.0Small, 65.0Reference ID for the recommendation.StringreferenceId
973
Response BodiesProduct Configurator

===== PAGE 988 =====

Configurator Product Related Component
Output representation of the product related component in a product configuration.
JSON example
"productRelatedComponent": {
"childProductId": "01txx0000006jmWAAQ",
"childSellingModelId": "0jPxx000000004rEAA",
"doesBundlePriceIncludeChild": true,
"id": "0dSxx000000001dEAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01txx0000006jkuAAA",
"parentSellingModelId": "0jPxx000000004rEAA",
"productComponentGroupId": "0y7xx000000001dAAA",
"productRelationshipTypeId": "0yoxx00000001IfAAI",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"quoteVisibility": "Quote Document Only"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the child product in the bundle.Stringchild
ProductId
60.0Small, 60.0ID of the child product selling model record.StringchildSelling
ModelId
60.0Small, 60.0Indicates whether the price of the bundle
includes the child product (true) or not
(false).
BooleandoesBundle
Price
IncludeChild
60.0Small, 60.0ID of the product related component.Stringid
60.0Small, 60.0Indicates whether the component is
required in the bundle (true) or not
(false).
BooleanisComponent
Required
60.0Small, 60.0Indicates whether to select the component
in the bundle group by default (true) or
not (false).
BooleanisDefault
Component
60.0Small, 60.0Indicates whether to allow changes to the
quantity of the component in the bundle
(true) or not (false).
BooleanisQuantity
Editable
60.0Small, 60.0Maximum quantity of the product in the
opportunity, quote, or order line item.
DoublemaxQuantity
60.0Small, 60.0Minimum quantity of the product in the
opportunity, quote, or order line item.
DoubleminQuantity
974
Response BodiesProduct Configurator

===== PAGE 989 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the parent product.Stringparent
ProductId
60.0Small, 60.0ID of the parent product selling model
record.
StringparentSelling
ModelId
60.0Small, 60.0ID of the product classification record.Stringproduct
Classification
Id
60.0Small, 60.0ID of the product component group.Stringproduct
Component
GroupId
60.0Small, 60.0ID of the product relationship type record.Stringproduct
Relationship
TypeId
60.0Small, 60.0Quantity of the child products.Doublequantity
60.0Small, 60.0Method to scale the quantity of the child
product in relation to the quantity of the
parent. Valid values are:
StringquantityScale
Method
• Constant
• Proportional
64.0Small, 64.0Specifies whether a quote line item must
be shown on the transaction line editor or
quote document. Valid values are:
Stringquote
Visibility
• Always
• Transaction Line Editor
Only—Specifies whether to show a
quote line item on quote editor only.
• Quote Document
Only—Specifies whether to show a
quote line item on quote proposal only.
• Never
The API returns this property only if the
CoreCPQ permission set is available.
60.0Small, 60.0Order in which the child products are
displayed.
Integersequence
Configurator Product Selling Model
Output representation of the product selling model in a product configuration.
975
Response BodiesProduct Configurator

===== PAGE 990 =====

JSON example
"productSellingModel": {
"id": "0jPxx0000000085EAA",
"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the product selling model.Stringid
60.0Small, 60.0Name of the product selling model.Stringname
60.0Small, 60.0Pricing term of the product selling model.IntegerpricingTerm
60.0Small, 60.0Pricing term unit of the product selling
model.
Stringpricing
TermUnit
60.0Small, 60.0Selling model type of the product selling
model.
Stringselling
ModelType
60.0Small, 60.0Status of the product selling model.Stringstatus
Configurator Product Selling Model Option
Output representation of the product selling model option in a product configuration.
JSON example
"productSellingModelOptions": [
{
"id": "0iOxx000000009hEAA",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx000000004rEAA",
"name": "Termed Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000004rEAA"
},
{
"id": "0iOxx00000000PpEAI",
"productId": "01txx0000006jmWAAQ",
"productSellingModel": {
"id": "0jPxx0000000085EAA",
976
Response BodiesProduct Configurator

===== PAGE 991 =====

"name": "Evergreen Annually",
"pricingTerm": 1,
"pricingTermUnit": "Annual",
"sellingModelType": "Evergreen",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000085EAA"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the product selling model option.Stringid
60.0Small, 60.0ID of the product that’s associated with the
product selling model option.
StringproductId
60.0Small, 60.0Product selling model that’s associated with
the product selling model option.
Configurator Product
Selling Model[]
product
SellingModel
60.0Small, 60.0ID of the product selling model that’s
associated with the product selling model
option.
Stringproduct
Selling
ModelId
Configurator Qualification Context
Output representation of the qualification context in a product configuration.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Indicates whether the product is qualified
(true) or not (false).
BooleanisQualified
60.0Small, 60.0Reason for the qualification of this product.Stringreason
Configurator UI Treatment
Output representation of the details of the UI treatments of a product configurator. The details include the product configuration rule
actions to override the disable or hide behavior in the UI for product options, product attributes, and attribute picklist values.
JSON Example
[
{
"details": {
"attributeId": "0tjxx0000000007AAA",
"prcId": "0dSxx0000000007EAA",
"stiId": "0QLxx0000004CU0GAM",
"attributePicklistValueId": "0v6xx0000000005AAA"
},
977
Response BodiesProduct Configurator

===== PAGE 992 =====

"uiTreatmentScope": "Bundle",
"uiTreatmentTarget": "Attribute_Picklist_Value",
"uiTreatmentType": "Hide"
},
{
"details": {
"stiId": "ref_f0f2da7b_c431_482d_bf4b_599052f3a2e1"
},
"uiTreatmentScope": "Product",
"uiTreatmentTarget": "Component",
"uiTreatmentType": "Disable"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Key-value pair that specifies the items to
apply the rules on, which includes these
details.
Map<String,
Object>
details
• ID of the sales transaction item
• ID of the product-related component
• ID of the attribute
• ID of the attribute picklist value
62.0Small, 62.0Type of the UI treatment to be performed.
Valid values are:
StringuiTreatment
Scope
• Product—UI treatment is applicable
to a certain product only.
• Bundle—UI treatment is applicable
to the whole bundle.
62.0Small, 62.0Target of the UI treatment. Valid values are:StringuiTreatment
Target
• Component—Represents a product
option or bundle component.
• Quantity—Represents a quantity
field.
• Attribute—Represents a certain
attribute of the product.
• Attribute_Picklist_Value—Represents
one of the picklist values of a product
attribute.
62.0Small, 62.0Type of UI treatment to be performed. Valid
values are:
StringuiTreatment
Type
• Hide—Hide the associated target.
978
Response BodiesProduct Configurator

===== PAGE 993 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
• Disable—Disable the associated
target.
Configurator Unit Of Measure
Output representation of the details of the unit of measure record.
JSON Example
{
"unitOfMeasure": {
"id": "0hEXR00000000BJ2AY",
"name": "Litres",
"roundingMethod": "Down",
"scale": 2,
"unitCode": "Ltrs"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0ID of the unit of measure record.Stringid
63.0Small, 63.0Name of the unit of measure record.Stringname
63.0Small, 63.0Rounding method associated with the unit
of measure record.
Stringrounding
Method
63.0Small, 63.0Scale associated with the unit of measure
record.
Integerscale
63.0Small, 63.0Unit code associated with the unit of
measure record.
StringunitCode
Configurator Update Nodes
Output representation of the configuration request details to update nodes.
JSON Example
{
"configuratorMessages": {},
"configuratorUITreatments": [
{
"details": {
"attributeId": "0tjxx0000000007AAA",
"prcId": "0dSxx0000000007EAA",
"stiId": "0QLxx0000004CU0GAM",
"attributePicklistValueId": "0v6xx0000000005AAA"
979
Response BodiesProduct Configurator

===== PAGE 994 =====

},
"uiTreatmentScope": "Bundle",
"uiTreatmentTarget": "Attribute_Picklist_Value",
"uiTreatmentType": "Hide"
},
{
"details": {
"stiId": "ref_f0f2da7b_c431_482d_bf4b_599052f3a2e1"
},
"uiTreatmentScope": "Product",
"uiTreatmentTarget": "Component",
"uiTreatmentType": "Disable"
}
],
"errors": [],
"productQualifications": {
"01tDU000000EOTCYA4": {
"isQualified": true
}
},
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Map of the product IDs to the list of
configurator messages. Configurator
Map<String,
Configurator
Message>
configurator
Messages
messages are results from any validations,
Business Rules Engines (BRE) calls, or
Salesforce Pricing calls.
62.0Small, 62.0Details of the UI treatments that specify the
product configuration rule actions to
Configurator UI
Treatment[]
configurator
UITreatments
override the disable or hide behavior in the
UI for product options, product attributes,
and attribute picklist values.
60.0Small, 60.0List of errors, which contains an error code
and a message.
Error Responseerrors
60.0Small, 60.0Map of the product IDs to the qualification
rule execution results.
Map<String,
Configurator
Qualification
Context>
product
Qualifications
60.0Small, 60.0Indicates whether the call was successful
(true) not (false).
Booleansuccess
Configuration Update
Output representation of the details of the updated configuration.
980
Response BodiesProduct Configurator

===== PAGE 995 =====

JSON example
This example shows a sample when the update operation is successful.
{
"errors": [],
"success": true
}
This example shows a sample when the update operation has errors.
{
"errors": [
{
"code": "INTERNAL_SERVER_ERROR",
"message": "INVALID_REFERENCEOBJECTID"
}
],
"success": false
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of errors that contains a message and
an error code.
Error Responseerrors
63.0Small, 63.0Indicates whether the update operation is
successful (true) or not (false)
Booleansuccess
Error Response
Output representation of the details of the error.
JSON example
{
"errors": [
{
"code": "BAD_REQUEST",
"message": "MISSING_REFERENCEOBJECTID"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Code of the error.Stringcode
63.0Small, 63.0Description of the error.Stringmessage
981
Response BodiesProduct Configurator

===== PAGE 996 =====

Product Quantity Set Configurator
Output representation of the request details to set product quantity.
JSON Example
{
"configuratorMessages": {},
"configuratorUITreatments": [
{
"details": {
"attributeId": "0tjxx0000000007AAA",
"prcId": "0dSxx0000000007EAA",
"stiId": "0QLxx0000004CU0GAM",
"attributePicklistValueId": "0v6xx0000000005AAA"
},
"uiTreatmentScope": "Bundle",
"uiTreatmentTarget": "Attribute_Picklist_Value",
"uiTreatmentType": "Hide"
},
{
"details": {
"stiId": "ref_f0f2da7b_c431_482d_bf4b_599052f3a2e1"
},
"uiTreatmentScope": "Product",
"uiTreatmentTarget": "Component",
"uiTreatmentType": "Disable"
}
],
"errors": [],
"productQualifications": {
"01tDU000000EOTCYA4": {
"isQualified": true
}
},
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Map of the product IDs to the list of
configurator messages. Configurator
Map<String,
Configurator
Message>
configurator
Messages
messages are results from any validations,
Business Rules Engines (BRE) calls, or
Salesforce Pricing calls.
62.0Small, 62.0Details of the UI treatments that specify the
product configuration rule actions to
Configurator UI
Treatment[]
configurator
UITreatments
override the disable or hide behavior in the
UI for product options, product attributes,
and attribute picklist values.
60.0Small, 60.0List of errors, which contains an error code
and a message.
Error Responseerrors
982
Response BodiesProduct Configurator

===== PAGE 997 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Map of the product IDs to the qualification
rule execution results.
Map<String,
Configurator
Qualification
Context>
product
Qualifications
60.0Small, 60.0Indicates whether the call was successful
(true) not (false).
Booleansuccess
Product Configurator Standard Invocable Actions
Learn more about the standard invocable actions available with Product Configurator.
Run Config Rules Action
Run rules for a specific quote or order based on a context ID or transaction ID, and process other steps that are part of the configuration
directly within a Flow. This action decouples rule execution from configurations to enable independent execution of rules and for
easier retrieval of responses.
SEE ALSO:
Actions Developer Guide: Overview
REST API Developer Guide: Invocable Actions Standard
Run Config Rules Action
Run rules for a specific quote or order based on a context ID or transaction ID, and process other steps that are part of the configuration
directly within a Flow. This action decouples rule execution from configurations to enable independent execution of rules and for easier
retrieval of responses.
This action is available in API version 65.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/runConfigRules
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
983
Product Configurator Standard Invocable ActionsProduct Configurator

===== PAGE 998 =====

Inputs
DetailsInput
Type
string
transactionContextId
Description
Unique identifier for the transaction context.
Type
string
transactionId
Description
Required.
Unique identifier for the transaction.
Outputs
DetailsOutput
Type
Apex-defined
configRuleResult
Description
An runtime_industries_cpq.ConfigRuleResult record that contains the
configuration rule execution results including validation messages, product recommendations,
visibility rules, and errors from rule processing.
Type
string
transactionContextId
Description
Unique identifier for the transaction context.
Example
POST
This example shows a sample request to run rules for the specified quote based on the transaction context ID and transaction ID.
{
"inputs": [
{
"transactionContextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"transactionId": "0Q0DU0000005tJh0AI"
}
984
Run Config Rules ActionProduct Configurator

===== PAGE 999 =====

]
}
This example shows a sample successful response.
[
{
"actionName": "runConfigRules",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"transactionContextId":
"0000000p18dq18g0029175793402786243c3d5ea94c241f09c11388ac1b865f9",
"configRuleResult": {
"visibilityRules": [
{
"stiId": "0QLxx0000004CU0GAM",
"prcId": "PRC1",
"attributeId": "Color",
"attributePicklistValueId": "Red",
"target": "Attribute",
"scope": "Product",
"type": "Hide"
},
{
"stiId": "0QLxx0000004CU0GAM",
"prcId": "PRC2",
"attributeId": "Size",
"attributePicklistValueId": "Large",
"target": "Attribute",
"scope": "Bundle",
"type": "Disable"
}
],
"transactionContextId":
"0000000p18dq18g0029175793402786243c3d5ea94c241f09c11388ac1b865f9",
"productRecommendationRules": [
{
"referenceId": "CORE_BUNDLE_001",
"productIds": [
"01t000000001234",
"01t000000005678"
]
}
],
"messageRules": [
{
"stiId": "0QLxx0000004CU0GAM",
"severity": "INFO",
"messages": [
"Product configuration validated successfully"
]
},
985
Run Config Rules ActionProduct Configurator

===== PAGE 1000 =====

{
"stiId": "0QLxx0000004CU0GAM",
"severity": "INFO",
"messages": [
"All required attributes are configured"
]
},
{
"stiId": "0QLxx0000004CU0GAM",
"severity": "INFO",
"messages": [
"Bundle compatibility check passed"
]
}
],
"errors": []
}
},
"sortOrder": -1,
"version": 1
}
]
Here's a sample input to call this invocable action by using transactionContextId  property from Apex code.
// Create the invocable action with namespace
Invocable.Action action = Invocable.Action.createStandardAction('runConfigRules');
// Set input parameters using setInvocationParameter
String contextId = '008d27d7-e004-4906-a949-ee7d7c323c77';
System.debug('Setting transactionContextId parameter with value: ' + contextId);
// Use the exact parameter name format from the debug output
action.setInvocationParameter('transactionContextId', contextId);
// Debug the action parameters
System.debug('Action parameters: ' + action);
// Execute the action
System.debug('Invoking action...');
List<Invocable.Action.Result> results = action.invoke();
System.debug('Number of results: ' + results.size());
Product Configurator Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
Flow for Product Configurator
Represents the metadata associated with a flow. With Flow, you can create an application that navigates users through a series of
screens to query and update records in the database. You can also execute logic and provide branching capability based on user
input to build dynamic applications.
986
Product Configurator Metadata API TypesProduct Configurator

===== PAGE 1001 =====

ProductConfiguratorSettings
Represents the settings for Product Configurator.
SEE ALSO:
Metadata API Developer Guide: Understanding Metadata API
Flow for Product Configurator
Represents the metadata associated with a flow. With Flow, you can create an application that navigates users through a series of screens
to query and update records in the database. You can also execute logic and provide branching capability based on user input to build
dynamic applications.
FlowActionCall
Product Configurator exposes additional actionType values for the FlowActionCall Metadata type.
DescriptionField TypeField Name
Required.InvocableActionType
(enumeration of
type string)
actionType
The action type. Additional valid values only for Product Configurator
include:
• runConfigRules— Run rules for a specific quote or order based
on a context ID or transaction ID, and process other steps that are
part of the configuration directly within a Flow. This action decouples
rule execution from configurations to enable independent execution
of rules and for easier retrieval of responses.
ProductConfiguratorSettings
Represents the settings for Product Configurator.
Parent Type and Manifest Access
This type extends the Metadata metadata type and inherits its fullName field.
In the package manifest, all the settings metadata types for the org are accessed using the “Settings” name. See Settings for more details.
File Suffix and Directory Location
ProductConfiguratorSettings  values are stored in the ProductConfiguratorSettings.settings  file in the
settings  folder. The .settings  files are different from other named components, because there is only one settings file for each
settings component.
Version
ProductConfiguratorSettings components are available in API version 60.0 and later.
987
Flow for Product ConfiguratorProduct Configurator

===== PAGE 1002 =====

Fields
DescriptionField Name
Field Type
boolean
enableProductConfigurator
Description
Indicates whether to enable Product Configurator at run time to customize product
components and attributes during the sales process (true) or not (false). The
default value is false.
Declarative Metadata Sample Definition
Here's an example of a ProductConfiguratorSettings component.
<?xml version="1.0" encoding="UTF-8"?>
<ProductConfiguratorSettings xmlns="http://soap.sforce.com/2006/04/metadata">
<enableProductConfigurator>true</enableProductConfigurator>
</ProductConfiguratorSettings>
Here's an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>ProductConfigurator</members>
<name>Settings</name>
</types>
<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
The wildcard character *  (asterisk) in the package.xml manifest file doesn’t apply to metadata types for feature settings. The wildcard
applies only when retrieving all settings, not for an individual setting. For details, see Settings. For information about using the manifest
file, see Deploying and Retrieving Metadata with the Zip File.
Constraint Modeling Language
Constraint Modeling Language (CML) is a domain-specific language that defines models for complex systems. For product configuration,
constraint models describe real-world entities and their relationships to each other.
Constraint models enforce business logic declaratively, without the need for extensive code in a general-purpose programming language.
The constraint engine compiles CML code into a constraint model and uses the model to construct a product configuration that complies
with the specified constraints.
To build a constraint model in CML, use this basic workflow.
• Create global properties and settings which are header-level declarations in CML that define the foundational, fixed values for the
entire constraint model. They are crucial for setting up the core configuration environment and ensuring reusability across the model.
988
Constraint Modeling LanguageProduct Configurator

===== PAGE 1003 =====

• Create variables to define the properties or characteristics of a type. Variables can hold different kinds of data, such as strings, numbers,
or lists, and can be calculated from other variables and values. In Revenue Cloud, variables represent product fields, product attributes,
and sometimes context tags. See Create a Context Definition in Salesforce Help.
• Define types, which represent entities or objects in the model. Types are the building blocks of CML. They're similar to classes in
object-oriented programming. In Revenue Cloud, types represent standalone products, bundles, product components, and product
classes.
• Define relationships that describe how different types are associated with each other. In Revenue Cloud, relationships represent the
product structure in a bundle. For example, the root product has a relationship with its components.
• Apply constraints to define logical restrictions, and enforce rules and conditions on types, variables, and relationships.
Note:  To define a constraint for a child product in a bundle, you must include the entire bundle in the constraint model. For
example, if you define a constraint for a laptop, and the laptop is a child product in the Laptop Pro Bundle, you must include the
Laptop Pro Bundle in the constraint model for the constraint on the laptop to run.
See Constraint Model Example: Modeling a Generator Set on page 990 and CML Core Concepts on page 990.
Use Constraint Modeling Language (CML) to create and edit constraint models with Constraint Rules Engine in Product Configurator in
Salesforce.
• Use Constraint Builder With Constraint Rules Engine
• Define Constraints and Rules with the Visual Builder
• Use Code to Define Constraints and Rules in the CML Editor
Modeling a Generator Set
The Constraint Model for a Generator Set examples use CML to define a technical power configuration, illustrating concepts such
as calculated variables, enforcement of external standards, and component selection based on requirements.
Core Concepts
Constraint Modeling Language (CML) includes components that cover high-level global configurations to specific data types and
constraints.
Core Concept Examples
These examples illustrate core Constraint Modeling Language (CML) concepts including type, relationships, constraints, and so on.
Annotation Examples
Constraint Modeling Language (CML) annotations are labels that you add to parts of a model, such as types, variables, relationships,
and constraints. Annotations control how these elements are shown and how they behave in the configurator. Annotations help
fine-tune the configurator and the constraint engine without changing the actual structure of the model.
Constraint Modeling Language (CML) Best Practices
To prevent performance degradation or unexpected behaviors when the constraint engine executes CML code, follow these practices
when writing code.
Business-Centric Constraint Modeling Language (CML) Guidelines
Constraint Modeling Language (CML) must accurately calculate the total sum or aggregate of specific attributes like quantity or
userCount across child components, especially in complex configurations requiring group-level aggregation
Debugging Constraint Modeling Language (CML)
To debug constraint models and troubleshoot performance issues, enable debug logging in Apex and set the debug log level to
FINE.
Model Structure
The tables on the following pages show the structure for the constraint model in Core Concept Examples.
989
Constraint Modeling LanguageProduct Configurator

===== PAGE 1004 =====

Modeling a Generator Set
The Constraint Model for a Generator Set examples use CML to define a technical power configuration, illustrating concepts such as
calculated variables, enforcement of external standards, and component selection based on requirements.
The examples on page 1042 correspond to the CML core concepts on page 990 linked here. See the Generator Set examples for code
samples that use the core concepts.
• Global Properties and Settings— VOLTAGE_REGEX  is a global constant that defines a fixed regular expression pattern used for
validation or parsing throughout the model.
• Types— GeneratorSet  is the root type that represents the main entity. GeneralModel  represents a related component
type.
• Variables—The GeneratorSet  type defines variables like requiredKW  (the user's power requirement), Voltage, and
calculated variables like surgeLoadKW  and Voltage3  (derived from parsing the Voltage string).
• Relationships—The GeneralModels  relation connects the GeneratorSet  type to its possible configurations
(GeneralModel).
• Constraints—Constraints enforce critical business rules and safety standards, such as ensuring the selected generator model's power
meets the required threshold, or restricting configuration options (such as Voltage) based on the specified compliance standards
(Listing-UL 2200).
Core Concepts
Constraint Modeling Language (CML) includes components that cover high-level global configurations to specific data types and
constraints.
See these topics for information on each core concept and the ways they work together.
Note:  CML supports single-line code comments with // and block comments with /* */.
Global Properties and Settings
Header-level declarations define the global properties and settings for a model, including constants, properties, and external values
that set up the foundation of the CML code.
Variables
Variables are the properties or characteristics defined within a type. Variables can hold different types of data and can be calculated
from other values.
Types
In Constraint Modeling Language (CML), you define types to represent entities or objects in the model. Types are the foundational
building blocks of CML. A type encapsulates the property, relationships, constraint, and rules for the entity.
Relationships
Relationships in Constraint Modeling Language (CML) define how different product types are associated with each other, forming
the structural hierarchy of a product bundle. Relationships are also referred to as ports.
Constraints
Constraints enforce rules and conditions on types, variables, and relationships. Use constraints to define logical restrictions and
ensure consistency within the model.
990
Modeling a Generator SetProduct Configurator

===== PAGE 1005 =====

Global Properties and Settings
Header-level declarations define the global properties and settings for a model, including constants, properties, and external values that
set up the foundation of the CML code.
Use these declarations to create reusable components and configuration settings that you can reference throughout the model.
Global Constants
Use global constants to define values that remain fixed throughout the model. These constants can be numeric values, strings, lists, or
other supported data types. Use constants to create standardized settings or options that you can reference multiple times. See Example
1: Use Regex Global Variable on page 990.
In the example, MAX_COUNT  is a global constant that is hard-coded to 100: define MAX_COUNT 100.
Regex (regular expressions) can be used to define global constants. The generalized abstract syntax structure for regex expressions is
define <CONSTANT_NAME> "^<REGEX_PATTERN_STRING>$".
Regex Pattern Components
This table lists regex components and their details.
GeneralizationDescriptionRegex Component
Ensures strict adherence to the required
format.
Anchors that ensure the pattern matches
the entire string, from the beginning (^) to
the end ($).
^ and $
Allows extraction of specific data fields from
a string.
Capturing Groups used to isolate portions
of the matched string. You can reference
the captured parts later by using $1, $2, and
()
so on, in functions such as regexpreplace.
See String Variable Functions and Operators
on page 994.
Defines the permitted characters and
minimum occurrences for the data fields.
Character Class and Quantifier that matches
one or more (+) digits or characters.
+
Matches fixed delimiters in the input string.Literal Character matching the forward slash
separator present in the input data.
/
In the example, VOLTAGE_REGEX  is a global constant that defines a fixed regular expression pattern used for validation or parsing
throughout the model define VOLTAGE_REGEX "^([0-9]+)/([0-9]+)$".
For more on the usage of global properties, see External Variables on page 999.
Variables
Variables are the properties or characteristics defined within a type. Variables can hold different types of data and can be calculated from
other values.
991
Core ConceptsProduct Configurator

===== PAGE 1006 =====

Variable Domains and Domain Restrictions
A variable can have a fixed domain that defines a set of permitted values. You can specify the domain as a list of discrete values, a
continuous range, or a combination.
Variable Data Types
Variables support multiple data types including boolean, date, decimal, and so on. Variables without a domain definition may remain
unbound, leading to errors.
Mathematical Functions (Numerical Derivation)
Mathematical functions and operators are used to calculate derived values based on arithmetic relationships between variables.
String Variable Functions and Operators
Constraint Modeling Language (CML) provides string manipulation and conversion functions, and string comparison and validation
operators.
Variable Annotations
You can annotate variables with properties such as configurable, defaultValue, domainComputation, and relatedAttributes.
External Variables
External variables are global Constraint Modeling Language (CML) variables defined within a virtual CML type.
Variable Domains and Domain Restrictions
A variable can have a fixed domain that defines a set of permitted values. You can specify the domain as a list of discrete values, a
continuous range, or a combination.
Variable Domains and Domain Restrictions
A variable can have a fixed domain that defines a set of permitted values. You can specify the domain as:
• A list of discrete values
• A continuous range
• A combination of ranges and discrete values
For more information, see domainComputation in Variable Annotations on page 996.
Example
This example defines a SwitchgearBay  type with three variables, each having a fixed domain.
• BayType  can be one of the specified string values.
• Bay_Number  can be any integer between 1 and 9 (inclusive).
• Total_Power_Required_kW  can be any integer between 1 and 100000 (inclusive).
type SwitchgearBay {
string BayType = ["load", "lv", "mv"];
int Bay_Number = [1..9];
int Total_Power_Required_kW = [1..100000];
}
Variable Data Types
Variables support multiple data types including boolean, date, decimal, and so on. Variables without a domain definition may remain
unbound, leading to errors.
992
Core ConceptsProduct Configurator

===== PAGE 1007 =====

Defaulting ExampleDescriptionData Type
@(defaultValue="true")
boolean isActive;
Only true, false, or null can be assigned as a
value.
boolean
date shipDate =
["2023-01-01",
"2023-12-31"];
If there's no defaultValue specified,
the variable defaults to the first value in the
A value that indicates a particular day, the
same as local date in Java.
date
domain. See the Constraints using Format
Specifiers (%s, %d) and Dates example on
page 1042.
double(2) percentage =
[0.00..100.00];
If there's no defaultValue specified, the
variable defaults to the first value in the
domain.
A 64-bit number that includes a decimal
point, the same as double in Java.
double(n)
decimal(2) TaxRate = 0.08;A fixed-point numeric value with n decimal
places. Note: The decimal variable data type
decimal(n)
isn't supported for the quantity field in
quote line items. Use the integer data type
for the quantity field.
@(defaultValue = "5") int
defaultQty = [1..10];
If there's no defaultValue  specified,
the variable defaults to the first value in the
domain.
Integer. A 32-bit number that doesn't
include a decimal point, the same as int in
Java.
int
@(defaultValue = "Red")
string color = ["Red",
"Green", "Blue"];
If there's no defaultValue  specified,
the attribute defaults to the first value in the
domain.
Any set of characters surrounded by double
quotes (")
string
@(defaultValue = '["Red",
"Green"]') string[]
selectedColors;
If there's no defaultValue  specified,
the attribute picklist defaults to the first
value in the domain.
Used in multi-select picklists for the user to
select more than one item from multiple
options. For example, if a user selects "Red",
"Green", and "Blue" values in a color picker,
this variable holds those selected values.
string[]
993
Core ConceptsProduct Configurator

===== PAGE 1008 =====

Mathematical Functions (Numerical Derivation)
Mathematical functions and operators are used to calculate derived values based on arithmetic relationships between variables.
CML Keyword/Operator [Source]PurposeFunction/Operator
+, -, *, /, %, ^Perform standard arithmetic: addition (+),
subtraction (-), multiplication (*), division
(/), modulo (% or mod), and power (^).
Arithmetic Operators
ceilReturns the smallest integer greater than or
equal to the argument (rounds up).
ceil()
Usage Example
surgeLoadKW == requiredKW * 1.25);
ceil(totalItems / itemsPerCrate)
See Arithmetic Calculations and Functions on page 1042 and examples here on page 1101.
String Variable Functions and Operators
Constraint Modeling Language (CML) provides string manipulation and conversion functions, and string comparison and validation
operators.
The functions can be used to modify strings, extract information, or convert strings to numeric types. The operators can be used to
validate string values against sets or regular expressions.
Syntax, Examples, and Additional
Details
PurposeFunction
strlen(inputString)
strlen("Hello"  returns 5.
Returns the length of the string as an
integer.
strlen()
substr(inputString,
startIndex)  or
Returns a substring from the input string.substr()
substr(inputString,
startIndex, endIndex)
The index starts with 0. The character at
startIndex  is included, and the
character at endIndex  is excluded.
strconcat(separator,
stringArgsToConcatenate)
Concatenates multiple strings using a
specified separator.
strconcat()
strconcat("-", "a", "b")
results in "a-b".
names = join(name)An aggregate function that concatenates
string values across related components,
join()
typically using a separator. The separator is
a comma by default.
994
Core ConceptsProduct Configurator

===== PAGE 1009 =====

Syntax, Examples, and Additional
Details
PurposeFunction
trim(strToTrim)Returns the string after removing any
leading or trailing spaces.
trim()
strsplit(stringToSplit,
separator)
Splits a string into an array of strings around
a given separator.
strsplit()
strcontain(inputString,
searchString)
Returns a boolean value (true or false) to
specify whether the input string contains
the specified search string.
strcontain()
strshare(string1, string2,
delimiter)
Splits two strings using a delimiter (comma
by default) and returns true if the resulting
lists have any elements in common.
strshare()
strformat("%d person",
quantity)
Specifiers include %d  for integer, %s  for
string, %.2f for decimal or float, and %b
for boolean.
Returns a formatted string based on
parameters and format specifiers.
strformat()
strtoint(inputString,
defaultValue)
If the string can't be parsed as an integer
(for example, it contains text or a decimal
Converts a string to an integer.strtoint()
point), the provided defaultValue is
returned.
strtofloat(inputString,
defaultValue)
If the conversion fails, the provided
defaultValue  is returned. The
Converts a string to a decimal (floating
point) value.
strtofloat()
resulting decimal attribute must be declared
with the intended precision. For example,
decimal(3).
regexpreplace(InputString,
RegexPattern,
ReplacementGroup)
This function is commonly used to derive
numeric data from complex, formatted
Take an input string and a defined Regular
Expression (regex). Replace the entire input
string with a specific captured group from
the regex match.
regexpreplace()
strings before they are converted into
integers or decimals.
string splitStr1 = get(0,
strsplit("hello constraint
Used to retrieve an element at a specified
index (starting at 0) from an array or list
generated by a function like strsplit.
get(index, array)
engine", " ")); // returns
hello
995
Core ConceptsProduct Configurator

===== PAGE 1010 =====

Syntax, Examples, and Additional
Details
PurposeFunction
Using Get with Table Constraint—If your
table constraint output for three columns
is stored in a string[] variable named
picklistValues, you would access the first
row's attributes like this (assuming the
columns are stored in a predictable
sequence):
// Retrieve the first
element (Row 0, Column 0)
string value0_0 = get(0,
picklistValues); // Retrieve
the second element (Row 0,
Column 1)
String Comparison and Validation Operators
The in operator checks if the value of a string attribute is present within a defined set or array of strings.
Example
color in ["red", "blue"]
Variable Annotations
You can annotate variables with properties such as configurable, defaultValue, domainComputation, and relatedAttributes.
In this example, the gc_runningKw  variable is annotated to indicate that it's not configurable and has a default value of 0.00.
Note:  This example requires an enclosing type.
@(configurable = false, defaultValue = 0.00)
decimal(2) gc_runningKw;
DescriptionValuesProperty
Allows the engine to recalculate a value
even if a value was already received from
core.
true, falseallowOverride
This annotation helps save on performance
by allowing early calculation.
Indicates whether the variable is
configurable (true) or not (false).
true, falseconfigurable
If the configurable annotation isn’t explicitly
specified, the engine sets it implicitly as
true  for the variable.
996
Core ConceptsProduct Configurator

===== PAGE 1011 =====

DescriptionValuesProperty
If the configurable annotation is explicitly
specified as true, the variable is indicated
as configurable. The engine can set the
value to the variable according to the
defined logic, and users can modify it.
If the configurable annotation is explicitly
specified as false, the engine cannot set
a value to the variable, and users can't
update it. The variable value in this case is
set through the PCM default.
See examples here on page 1048.
Indicates the default value for the variable.literaldefaultValue
The configurator uses the default value
defined in PCM (in Product Attribute
Definition). If no PCM default is available,
the configurator uses the first value in the
variable domain as the initial value.
If no default value is defined in PCM and a
defaultValue is specified in CML, the
configurator uses the value defined in CML
as the initial value of the variable.
See examples here on page 1048.
domainComputation is a CML annotation
that specifies how the domain of a model
true, falsedomainComputation
element is determined, either by using a
fixed domain or by computing the domain
dynamically during configuration.
If domainComputation is not explicitly
specified, the engine sets it implicitly as false
for the variable. If the domainComputation
is specified as true, the variable domain is
dynamically determined based on the
configuration and constraint logic. If the
domainComputation is specified as false,
the variable domain is fixed.
See examples here on page 1048.
Sets an initial value for the calculated
variable if the expression value can't be
calculated.
true, falsenullAssignable
997
Core ConceptsProduct Configurator

===== PAGE 1012 =====

DescriptionValuesProperty
Indicates whether the constraint engine can
override the variable’s value (whether set
true, falsePeelable
by default or user selection) to resolve a
conflict (true) or not (false).
If set to true, the engine treats the value
as a "soft selection." When a configuration
conflict occurs, the engine attempts to
"peel" (unbind) this variable and retry the
solution. If a valid configuration is found, the
engine automatically changes the value to
satisfy constraints, rather than displaying an
error message to the user. If not explicitly
set, or set to false, the engine treats the
value as a "hard selection." If the value
causes a conflict with a constraint, the
engine will not attempt to change it
automatically. Instead, it will stop and
display a conflict error message to the user,
requiring manual intervention to resolve the
issue.
See examples here on page 1048.
Used to represent the group cardinality for
relationships under a type, either for
integerproductGroup
specified relationships, or for all relationships
(using`*`).
We recommend using
maxInstanceQty  and
minInstanceQty  type annotations
instead of productGroup. See Type
Annotations on page 1003.
relatedAttributesannotation is required to
reset the domain to the original domain for
domain computation.
string valuerelatedAttributes
If relatedAttributes annotation is not
specified, the engine updates the variable
domain according to domainComputation
and constraint logic. If the relatedAttributes
annotation is specified with one or multiple
values (separated by comma), the variable
domain is reset to the original domain.
See examples here on page 1048.
998
Core ConceptsProduct Configurator

===== PAGE 1013 =====

DescriptionValuesProperty
Indicates the sequence in which variables
are configured.
integersequence
If a sequence value is not explicitly defined,
the configurator implicitly determines the
order based on the variable declaration
order in the CML model.
If a sequence value is explicitly defined, the
configurator uses the sequence number to
control the order in which variables are
configured. Variables with lower sequence
values are assigned first.
See examples here on page 1048.
Sets the variable status to default.true, falsesetDefault
Data source defined in the model.string valuesource
Sets the domain of the current variable to
be the domain of the source variable.
Variable name in stringsourceAttribute
Defines the strategy to configure the
variable.
descending, ascending, stringstrategy
• If the strategy is ascending, the engine
tries values from low to high.
• If the strategy is descending, the engine
tries values from high to low.
See example here on page 1048.
To create an external variable linked to a
Sales Transaction header, use the tagName
string valuetagName
annotation with the contextPath annotation
to reference context tags on
SalesTransactionItem within a type. See
contextPath in External Variable Annotations
on page 999.
External Variables
External variables are global Constraint Modeling Language (CML) variables defined within a virtual CML type.
See virtual in Type Annotations on page 1003. The values for external variables are usually set by the environment that launches the
constraint solver engine. Use external variables to import runtime data from the context header (such as Quote or Sales Transaction)
into the configuration model, with the contextPath annotation to denote header fields, or with tagName annotation to denote lineItem
fields. See External Variable Annotations section.
If the external variable isn't mapped to any external data source, it must have a default value. Otherwise, it may remain unbound and
cause errors.
999
Core ConceptsProduct Configurator

===== PAGE 1014 =====

Here's a basic declaration syntax.
extern int MAX_VALUE = 9999;
extern decimal(2) threshold = 1.5;
Example: Using External Variables with Context Path Annotation
In this example, the constraint engine needs access to the quote header (Sales Transaction) field, which defines the shipping location
to enforce region-specific compliance requirements. The contextPath  annotation is used to map the field
(SalesTransaction.ShippingCountry) to an external CML variable (ShippingCountry).
Note:  The CML variable name can be different from the context path value.
// External variable declaration with context path annotation
@(contextPath = "SalesTransaction.ShippingCountry")
extern string ShippingCountry; // ShippingCountry Value is pulled from the Quote/Order
header
See the full example in Using ContextPath and tagName annotations on page 1042.
External Variable Annotations
Here are the details of external variable annotations.
DescriptionPossible ValueAnnotation
References sales transaction values directly
from their context definition, such as
"SalesTransaction.<ST_FIELD>", where the
sales transaction field is pulled directly from
the context definition.
contextPath
account name, sales transaction total, or
address. The contextPath annotation can
only be used for header fields.
To create a variable linked to a
SalesTransactionItem, use the tagName
annotation to reference context tags on
SalesTransactionItem within a type. See
tagName in Variable Annotations on page
996.
Types
In Constraint Modeling Language (CML), you define types to represent entities or objects in the model. Types are the foundational
building blocks of CML. A type encapsulates the property, relationships, constraint, and rules for the entity.
A type is similar to a class in object-oriented programming. You can define relationships that represent associations between different
types. See Relationships on page 1006.
Generic Structure of a Type
This table explains the generic structure of types with examples.
1000
Core ConceptsProduct Configurator

===== PAGE 1015 =====

ExamplePurposeElement
type Product {}
Or optionally:
@annotation_name("annotation
Defines the entity name, optionally
preceded by annotations and optionally
followed by inheritance, if applicable.
Declaration
parameters") type Product:
BaseProduct {}
int requiredKW =
[101..10000]; string color =
["Red", "Blue"];
Defines the properties or characteristics of
the entity, including data type and domain.
Variables (Attributes)
relation items :
LineItem[1..10] {}
Defines one-to-many associations with
other types, specifying cardinality (the
quantity range) and optionally, the
configuration order.
Relations
constraint(condition);
require(condition, items
[type]);
Enforces business logic and restrictions that
must be satisfied by the entity's variables
and relationships.
Constraints and Rules
Example: Basic Type Declaration with Variables
This example shows the declaration of the main GeneratorSet  type. It defines several core attributes (variables) that characterize
the product.
type GeneratorSet{
// Declaration only (inherits LineItem properties)
// Attributes with explicit domains
int requiredKW = [101..10000];
string Voltage = ["220/380", "240/416", "255/440", "277/480", "347/600", "2400/4160",
"7200/12470", "7621/13200", "7976/13800];
string DutyRating = ["Prime Power (PRP)", "Continuous Power (COP)", "Data Center Continuous
(DCC)", "Emergency Standby Power (ESP)"];
}
Type Hierarchies
Constraint Modeling Language (CML) supports inheritance and overriding, which allow you to create hierarchies between types. By
establishing these hierarchies, constraint models become more modular and efficient.
Type Annotations
You can annotate types to add information. Type annotations are metadata applied to a type declaration to provide instructions to
the constraint engine regarding how instances of that type should be handled, instantiated, or used in the configuration structure.
Type Hierarchies
Constraint Modeling Language (CML) supports inheritance and overriding, which allow you to create hierarchies between types. By
establishing these hierarchies, constraint models become more modular and efficient.
1001
Core ConceptsProduct Configurator

===== PAGE 1016 =====

How Hierarchies Function
• Inheritance: This mechanism enables a specialized child type to automatically share common variables (attributes) and relationships
defined in its parent type. By inheriting from a base type, child types don't need to redefine shared properties, which ensures
consistency across the model.
• Overriding: While child types inherit the structure of the parent, they can override or specialize those properties. For example, a
parent type might define a variable with a broad range of possible values, while a child type overrides that variable with a fixed value
specific to that individual product.
Practical Examples of Hierarchy
• Simple Product Extension: A BaseProduct  might define an id  and name. A PhysicalProduct  can then inherit from
BaseProduct  to gain those fields while adding its own unique characteristics, such as weight  or color.
• Multi-Level Nesting: Hierarchies can extend through multiple layers. For instance, a Room  type can be the parent to a Bedroom
type, and a MasterBedroom  can further inherit from the Bedroom  type, carrying all properties down the chain.
• Abstract Base Models: In complex configurations such as a GeneratorSet, a parent type such as GeneralModel  defines
the necessary attributes (such as powerKW  and dB), while specific child types such as GeneralModel900  or
GeneralModel1200  inherit those attributes and override them with their specific ratings.
Core Benefits
By establishing these hierarchies, constraint models become more modular and efficient. You can create header-level declarations and
base types to serve as a foundation for the entire model, allowing you to reference reusable components multiple times rather than
writing redundant code for every product variation. This structural organization allows the constraint engine to effectively enforce
business logic and validate configurations across all related types.
Example 1: Simple Product Extension
In this pattern, a specialized type inherits from a broader base type. In the provided generator set model, the GeneratorSet  type
inherits from LineItem, gaining any properties defined at the line-item level while adding its own specific configuration fields like
requiredKW  and Voltage.
// The ultimate base type in the system
type LineItem;
// Child type extending LineItem with generator-specific attributes
type GeneratorSet : LineItem {
int requiredKW = [101..10000];
string Voltage = ["220/380", "240/416", "255/440"];
string DutyRating;
}
Example 2: Multi-Level Nesting
CML supports hierarchies with multiple layers of depth. In this example, properties flow from the top-level LineItem  down to the
GeneratorSet, and finally to a highly specialized EmergencyGenerator. Each level inherits all attributes from the levels above
it.
type LineItem;
// Level 2: Adds basic generator capacity attributes
type GeneratorSet : LineItem {
int requiredKW = [101..10000];
1002
Core ConceptsProduct Configurator

===== PAGE 1017 =====

decimal(2) surgeLoadKW = requiredKW * 1.25; // Calculation shared down the chain
}
// Level 3: Specialized version inheriting everything from GeneratorSet and LineItem
type EmergencyGenerator : GeneratorSet {
// Automatically inherits requiredKW and surgeLoadKW
string DutyRating = "Emergency Standby Power (ESP)"; // Specific fixed rating
}
Example 3: Abstract Base Models (Polymorphism & Overriding)
This pattern uses an abstract type as a structural blueprint. Specific components (the "General Models") inherit from this blueprint and
override its generic attributes with fixed, real-world ratings.
// Base model acting as a blueprint for all engine options
type GeneralModel{
int powerKW = [100..2000]; // Broad domain
int dB = [60..100];
}
// Specific product type that overrides parent domains with fixed values
type GeneralModel900 : GeneralModel {
int powerKW = 900; // Overrides broad range with exact value
int dB = 78;
}
// Another specialized model with different fixed properties
type GeneralModel1500 : GeneralModel {
int powerKW = 1500;
int dB = 83;
}
Type Annotations
You can annotate types to add information. Type annotations are metadata applied to a type declaration to provide instructions to the
constraint engine regarding how instances of that type should be handled, instantiated, or used in the configuration structure.
DescriptionPossible ValuesAnnotation
If true, specifies whether the indicated
type refers to the transaction header (such
true, falsevirtual
as Quote or Order) or to a logical container
(sub group of the Quote or Order). If the
value is false, then it’s the default
behavior for types and doesn’t need to be
explicitly specified.
Used with virtual = true, the
groupBy  annotation organizes child
Variable namegroupBy
products—the individual instances
populating a relationship—into virtual
containers based on a shared attribute
value.
1003
Core ConceptsProduct Configurator

===== PAGE 1018 =====

DescriptionPossible ValuesAnnotation
See Relationships on page 1006 and the
Grouping Generators by Voltage example
on page 1042
.
Specifies the maximum cardinality for a
component in a group. See Group Type on
page 1030.
IntegermaxInstanceQty
Specifies the minimum cardinality for a
component in a group. See Group Type on
page 1030.
IntegerminInstanceQty
Specifies the data source defined in the
model.
Stringsource
Specifies whether the type should be split
or not.
true, false, nonesplit
• If split=true, there can be multiple
instances of the type, and the quantity
of each instance is always 1.
• If split=false, there is only one
instance in the relationship. If the user
adds more instances, the engine adds
more quantity to the existing instance.
• If split=none  (the default), there
are multiple instances of the same type
in the relationship, with different
quantities.
The split=true  annotation isn't
supported for child products within a
dynamic bundle. See examples here on
page 1048.
Specifies the maximum number of times a
single instance of a specific type can be
Integersharingcount
shared or reused across different
relationships within the configuration
model.
This annotation is used in conjunction with
the @(split=true) annotation. When a
type is marked for splitting, the constraint
engine can process multiple instances in
parallel to improve performance.
The sharingCount tells the engine
exactly how many times it can "split" or
1004
Core ConceptsProduct Configurator

===== PAGE 1019 =====

DescriptionPossible ValuesAnnotation
reuse that instance to satisfy the
configuration requirements without
generating entirely new, unique instances.
It's a critical tool for managing large-scale
configurations (for example, models with
over 1,000 components). By setting a
sharing limit, you reduce the number of
variables the engine must instantiate, which
helps prevent performance degradation and
system timeouts.The sharingCount
annotation works with the
@(sharing=true) annotation applied
to Relations. The relation annotation enables
the general capability to share components
across instances, while the
sharingCount  on the child type sets
the numerical limit for that behavior.
See Relationship Annotations on page 1010
and the Sharing Accessories in a Generator
Set example on page 1042.
Creating a Virtual Container (@virtual = true)
In this example, the @virtual = true  annotation is applied to a logical container type, System, which is primarily used to define
relationships. These relationships aggregate data across line items in the quote that forms a sub-group called system. See Relationships
on page 1006.
@(virtual = true)
type System {
// This relation gathers all GeneratorSet line items on the sales transaction
@(sourceContextNode = "SalesTransaction.SalesTransactionItem")
relation generators : GeneratorSet[0..10];
// This variable aggregates the surge load (calculated inside GeneratorSet) from all
collected generators
int totalQuotedLoad = generators.sum(surgeLoadKW);
}
type GeneratorSet {
// The attribute calculated here is aggregated in the virtual 'System' type above
@(configurable = false)
int requiredKW = [101..10000];
string DutyRating = ["Prime Power (PRP)", "Continuous Power (COP)", "Data Center Continuous
(DCC)", "Emergency Standby Power (ESP)"];
decimal(2) surgeLoadKW = requiredKW * 1.25;
}
1005
Core ConceptsProduct Configurator

===== PAGE 1020 =====

Relationships
Relationships in Constraint Modeling Language (CML) define how different product types are associated with each other, forming the
structural hierarchy of a product bundle. Relationships are also referred to as ports.
Here is a comprehensive overview of relationships, their syntax, purpose, and key features, particularly utilizing examples relevant to the
Generator Set model.
Definition and Syntax of Relationships
Relationships define the one-to-many connections between a parent type (such as a bundle) and its component types (children).
• Keyword: The keyword used is relation.
• Syntax: A basic relationship declaration includes the relation name, the target type, and cardinality bounds.
relation <relation name> : <Target Type>[min..max] { /* Optional content */ }
• Purpose: Relationships represent the product structure in a bundle. For example, the root product (GeneratorSet) has relationships
with its components (MainAlternators, TemperatureSensors).
Note:  Specifying the smallest required cardinality (quantity range) is a best practice to avoid unnecessary testing of value
combinations, which improves performance.
Omit Unnecessary Relationships
When using the visual builder or the CML editor to create a CML code for a bundle, the system by default imports all the relationships
for the selected bundle from the structure defined in Product Catalog Management (PCM). In large and complex CML code, some of
these relationships may not be relevant to any constraint and can be potentially omitted.
To enable import of a subset of bundle components, add this property at the top of the constraint model CML file.
property allowMissingRelations = "true";
If your PCM bundle contains many different relations but your CML code defines only one, the engine will validate the model but this
often results in a configuration run-time failure. By setting allowMissingRelations = "true", you do not have to define
every relation found in the PCM (such as GeneralModels in the Relationship Ordering example) if they do not require specific configuration
logic in your CML file.
Here’s an example with allowMissingRelations property.
// 1. Enable skipping of unneeded relations from the Product Catalog (PCM)
property allowMissingRelations = "true";
type ConciseGeneratorBundle {
// Define only the specific accessory needed for this logic
relation enclosures : Enclosure;
// A simple variable to trigger the logic
int requiredKW = [100..5000];
// Logic: High power requirements force a specific enclosure type
// This omits other accessories like filters, batteries, and heaters [2, 3].
constraint(requiredKW > 2000 -> enclosures[ReinforcedEnclosure] == 1,
"Power levels above 2000kW require a Reinforced Enclosure.");
}
1006
Core ConceptsProduct Configurator

===== PAGE 1021 =====

// 2. Define the accessory and its specific subtype
type Enclosure ;
type ReinforcedEnclosure : Enclosure;
For more information, see Constraints on page 1013.
To ensure run-time stability without the allowMissingRelations property, you must manually define every single relation and type present
in the PCM bundle, even if you don't intend to write logic for them. This creates large CML files with a high number of variables and
components, which lead to performance degradation, and even timeout issues.
Note:  This code isn’t recommended.
// EXPENSIVE FIX: Mirroring everything
type GeneratorSet {
relation engineModels : EngineModel; // Unused in CML logic
relation alternators : Alternator; // Unused in CML logic
relation fuelFilters : FuelFilter; // Unused in CML logic
relation starterMotors : StarterMotor; // Unused in CML logic
relation enclosures : Enclosure; // The only one we need
// ... potentially 15+ more relations ...
constraint(requiredKW > 2000 -> enclosures[ReinforcedEnclosure] == 1);
}
type Enclosure ;
type ReinforcedEnclosure : Enclosure;
Order Keyword
The order()  keyword is used within a relation  declaration to define the specific sequence in which the constraint engine
evaluates and attempts to instantiate the child subtypes available in that relationship. This controls the prioritization of component
selection.
Example: Relationship Ordering
// --- Component Subtypes (Specific Generator Models) ---
// Define a base type for generator models with a power attribute
type GeneralModel {
int powerKW = [0..3000]; // Explicit domain
}
// Specific subtypes that inherit from GeneralModel
type GeneralModel2500 : GeneralModel {
int powerKW = 2500;
}
type GeneralModel1750 : GeneralModel {
int powerKW = 1750;
}
type GeneralModel900 : GeneralModel {
int powerKW = 900;
}
// --- Parent Type (GeneratorSet) ---
type GeneratorSet {
// Required power defined by the parent (non-configurable)
@(configurable = false)
1007
Core ConceptsProduct Configurator

===== PAGE 1022 =====

int requiredKW = [100..3000];
// Relation Declaration using order()
// Cardinality requires exactly one model to be selected.
// order() sets the selection priority (2500 KW model is checked before 1750 KW model).
relation GeneralModels : GeneralModel order(GeneralModel2500, GeneralModel1750,
GeneralModel900);
}
Relationship Variable Functions
CML variable functions are fundamental tools used to perform both aggregation (summarizing data from related components) and
complex mathematical calculations on attribute values (variables) within a configuration model. These functions are crucial for
enforcing dimensional validity and calculating derived attributes.
Relationship Annotations
You can annotate relationships by using annotations, such as configurable, allowNewInstance, closeRelation, sourceContextNode,
and so on.
Relationship Variable Functions
CML variable functions are fundamental tools used to perform both aggregation (summarizing data from related components) and
complex mathematical calculations on attribute values (variables) within a configuration model. These functions are crucial for enforcing
dimensional validity and calculating derived attributes.
You can use functions such as count(), min(), max(), sum()  and total()  to calculate values from all variables with the
same name in the descendants of the current type. Aggregate functions are used primarily as relationship attributes within a relation
to calculate values across multiple instances of a component type (descendants).
CML Keyword [Source]PurposeFunction
countCounts the number of component instances
within a relationship that match a specific
logical condition.
count()
max, minReturns the maximum or minimum value
of an attribute found across all instances in
a relationship.
max() / min()
sumCalculates the sum of a specific numeric
variable across all instances in a relationship.
sum()
Note: executes multiplication of a variable
value by a product quantity.
totalCalculates the sum of a specific numeric
variable across all instances in a relationship.
total()
Note: Unlike the sum() function, does not
execute multiplication of a variable value
by line item quantity.
1008
Core ConceptsProduct Configurator

===== PAGE 1023 =====

Example: Using Aggregate Functions
type LineItem;
type GeneratorSet : LineItem {
relation modelclassification : ModelClassification {
sumPowerKW = sum(powerKW);
maxPowerKW = max(powerKW);
highPowerModelsAmount = count(powerKW > 500);
}
relation warranties : Warranty {
totalCoverageDays = total(coverageDays);
}
constraint(modelclassification.sumPowerKW > 2500 && modelclassification.sumPowerKW < 3500);
message(true, "The maximum `powerKW` from selected GeneralModels is: {}",
modelclassification.maxPowerKW);
constraint(warranties[Warranty] == modelclassification.highPowerModelsAmount);
message(true, "Effective Warranty coverage days: {}", warranties.totalCoverageDays);
}
type ModelClassification : LineItem {
int powerKW = [900, 1750, 2500];
}
type GeneralModel1750 : ModelClassification {
int powerKW = 1750;
}
type GeneralModel2500 : ModelClassification {
int powerKW = 2500;
}
type GeneralModel900 : ModelClassification {
int powerKW = 900;
}
type Warranty {
int coverageDays;
}
type Warranty_PRP : Warranty {
int coverageDays = 50;
}
type Warranty_DCC : Warranty {
int coverageDays = 100;
}
type Warranty_ESP : Warranty {
int coverageDays = 200;
}
sum()
In the example, the sum()  function aggregates the powerKW  variable values of the selected products in the
modelClassification  relationship. The model includes a constraint that enforces the selection rule based on the calculated
total: the sum  of powerKW for the selected products must be between 2500 and 3500.
constraint(modelclassification.sumPowerKW > 2500 && modelclassification.sumPowerKW < 3500);
As a result, the engine selects two products from the modelClassification  relation (GeneralModel1750  and
GeneralModel900), since their calculated sum of powerKW  values (2650) satisfies the constraint.
1009
Core ConceptsProduct Configurator

===== PAGE 1024 =====

max()
In the example, the max()  function returns the maximum powerKW  variable value among the selected products in the
modelClassification  relationship. The model defines a message that displays the maximum powerKW  value in the Product
Configurator.
message(true, "The maximum `powerKW` from selected GeneralModels is: {}",
modelclassification.maxPowerKW);
As a result, because the previously described sum() function and constraint selected two products (GeneralModel1750  and
GeneralModel900), the maximum returned value is 1750.
count()
In the example, the count()  function calculates the amount of selected modelClassification  relationship products that
contain the powerKW  variable value greater than 500. The model includes a constraint that enforces the selection of warranties
product for each GeneralModel  counted by the function.
constraint(warranties[Warranty] == modelclassification.highPowerModelsAmount);
As a result, based on the previous sum()  description, the engine selects two products (GeneralModel1750  and
GeneralModel900). Since both products meet the count() condition (powerKW  > 500), the engine adds one of the warranties
product with quantity 2.
total()
In the example, the total()  function aggregates the values of the coverageDays  variable for the selected products of the
warranties  relationship. The model defines a message that displays the calculated total in the Product Configuration.
message(true, "Effective Warranty coverage days: {}", warranties.totalCoverageDays);
As a result, based on previously described count() example, the system selects one of the warranties product (e.g.,
Warranty_DCC) with a quantity of 2 and calculates the total value of its coverageDays  variable (100).
A key difference between total()  and sum()  functions is that for total()  the engine ignores the warranties product
quantity. The system does not multiply the quantity of the selected warranty by the coverageDays  variable value when computing
the overall total.
See also Arithmetic Calculations and Functions on page 1042 and examples here on page 1101.
Relationship Annotations
You can annotate relationships by using annotations, such as configurable, allowNewInstance, closeRelation, sourceContextNode, and
so on.
You can annotate relationships, as in this example, with configurable=true.
// 1. Define the target type
type Component;
// 2. Define the parent type to hold the relation
type System {
// 3. Add the relation with cardinality and proper nesting
@(configurable = true)
relation components : Component[0..10];
}
1010
Core ConceptsProduct Configurator

===== PAGE 1025 =====

Here are the details of relationship annotations.
DescriptionValuesAnnotation
Enables require rule constraints to work on
relationships that are otherwise closed. Must
true, falseallowNewInstance
be set to true to enable require rule
constraints on closed relationships.
If the value is true, prevents the addition of
new line items to the relationship. false is
true, falsecloseRelation
the default value and allows the addition of
new line items to the relationship.
See examples here on page 1048.
Avoids creating a component number
variable if it is set to false.
true, falsecompNumberVar
Disable cardinality constraint in the
relationship to optimize the performance.
true, falsedisableCardinalityConstraint
domainComputation  is a Constraint
Modeling Language (CML) annotation that
true, falsedomainComputation
specifies how the domain of a model
element is determined, either by using a
fixed domain or by computing the domain
dynamically during configuration.
If domainComputation is not explicitly
specified, the engine sets it implicitly as
true  for the relationship.
If the domainComputation is specified as
true, the relationship domain is
dynamically determined based on the
configuration and constraint logic.
If the domainComputation is specified
as false, the relationship domain is fixed.
See examples here on page 1048.
Indicates if generic instance is allowed in
the relationship or not. Generic instance is
true, falsegeneric
used to prompt the user that they need to
select a product in the relationship.
Avoids creating cardinality variables for none
leaf type (a node with no children) in the
relationship to optimize the performance.
true, falsenoneLeafCardVar
Aggregates values from child elements to
parent elements.
true, falsepropagateUp
1011
Core ConceptsProduct Configurator

===== PAGE 1026 =====

DescriptionValuesAnnotation
If propagateUp is not specified, the engine
sets it implicitly as false for the relationship.
If the propagateUp annotation is specified
as true, the engine aggregates values from
children to parent elements (upward
propagation). The engine cannot modify
this value from the parent level (e.g. via
constraint), so the children relation domain
will not be affected.
If the propagateUp is specified as false, both
upward and downward propagations are
applicable. The engine aggregates values
from children to parent elements (upward
propagation). Meanwhile the engine can
modify this value (e.g. via constraint) from
the parent level. The value is propagated
downward and might affect the relation
domain (downward propagation).
See examples here on page 1048.
Sets a relationship and all child relationships
to read-only, to prevent the engine or user
from modifying.
true, falsereadOnly
relatedAttributes  is a CML
annotation that resets the domain to the
original one for domainComputation.
string valuerelatedAttributes
If domainComputation is not explicitly
specified, the engine sets it implicitly as
true  for the relationship.
If the domainComputation is specified
as true, the relationship domain is
dynamically determined based on the
configuration and constraint logic.
If the domainComputation is specified
as false, the relationship domain is fixed.
See examples here on page 1048.
Related relationships whose cardinality
variables must be unbound for domain
computation.
string valuerelatedRelationships
Indicates the sequence in which the
relationship is configured and executed.
integersequence
1012
Core ConceptsProduct Configurator

===== PAGE 1027 =====

DescriptionValuesAnnotation
Indicates if the relationship is shared or not.
If the relationship is shared, the engine
true, falsesharing
connects the instance from another
relationship to this relationship instead of
instantiating the instance in the relationship
itself.
Indicates if all types in the relationship must
be singleton or none.
true, falsesingleton
Data source defined in the model.stringsource
Sets the domain of the current relationship
to the domain of the source attribute.
Variable name in stringsourceAttribute
For cases that use a virtual container,
specifies the path in the context service for
the instances in the relationship.
stringsourceContextNode
Constraints
Constraints enforce rules and conditions on types, variables, and relationships. Use constraints to define logical restrictions and ensure
consistency within the model.
For more information about the supported constraints, see:
• Logical Constraints on page 1016
• Table Constraints on page 1021
• Using Proxy Variables with Constraints on Types and Relationships on page 1023
• Group Type on page 1030
• Message Rule on page 1034
• Preference Rule on page 1034
• Require Rule on page 1035
• Require Rule vs Constraint on page 1035
• SetDefault Rule on page 1036
• Exclude Rule on page 1036
• Action Rule on page 1037
• Hide/Disable Rule on page 1037
• Recommendation Rule on page 1039
• Set Product Selling Model in a Constraint on page 1041
Supported Logic Operators
These logic operators are supported in CML.
1013
Core ConceptsProduct Configurator

===== PAGE 1028 =====

Arithmetic Operators
• Multiplication (*)
• Division (/)
• Remainder (%)
• Addition (+)
• Subtraction (-)
Relational Operators
• Greater than (>)
• Greater than or equal to (>=)
• Less than (<)
• Less than or equal to (<=)
Equality Operators
• Equal (==)
• Not equal (!=)
Logic Operators
• Not (!)
• And (&&)
• XOR/Exclusive or (^)
• Or (||)
• Bi-conditional (<->)
• Conditional (?:)
• Implication (->)
Operator Precedence
In resolving equations, operator precedence determines the order in which operations are performed. Operators in CML have precedence
in this order:
• Arithmetic operators have the first precedence.
• Relational operators have the second precedence.
• Equality operators have the third precedence.
• Logic operators have a lower precedence than equality operators, in decreasing order as listed, with Implication having the lowest
precedence.
Constraint Annotation
Here are the details of abort, a constraint annotation.
1014
Core ConceptsProduct Configurator

===== PAGE 1029 =====

DescriptionPossible ValuesAnnotation
Specifies that, if this constraint fails, abort
search and return false for configuration.
true, falseabort
Logical Constraints
A logical constraint defines a statement that must hold true logically. The constraint can be any logical expression by using a logical
operator.
Table Constraints
The table constraint in Constraint Modeling Language (CML) is used to define a set of valid combinations of values for two or more
attributes. These combinations are specified in rows within the constraint definition.
Proxy Variables with Constraints on Types and Relationships
Use proxy variables to reference the variables of related types, including parent, root, and sibling types.
Group Type
In Constraint Modeling Language (CML), a Group Type is used to logically containerize related components within a bundle
configuration, primarily when product component groups are imported from Product Catalog Management (PCM).
Message Rule
The message rule displays a message to users based on specified conditions.
Preference Rule
The preference rule encourages the constraint solver to satisfy the condition, but doesn't enforce it if the condition can't be met.
Require Rule
The require rule requires certain components to be included in a relationship when specified conditions are met.
Require Rule vs Constraint
In Constraint Modeling Language (CML), constraint() and require() can both enforce behavior, but they operate differently: constraint
focuses on logical consistency, require focuses on physical presence of products.
SetDefault Rule
The setDefault rule allows component selection with attribute values and quantity, similar to the require rule.
Exclude Rule
The exclude rule is used to automatically remove a specific type in a relationship if a certain condition is met.
Action Rule
The CML Action Rule is defined using the rule() keyword. Its primary purpose is to execute a designated action, specified as a string
literal, when a condition is met.
Hide or Disable Rule
The Hide or Disable Rule uses the rule() keyword to conditionally remove an element from the selection menu (hide) or preserve it
in the menu while preventing user selection (disable).
Recommendation Rule
The recommend keyword is used within a Constraint Modeling Language (CML) rule to display suggestions for related products in
the Product Configurator. The rule defines the condition under which a specific product type or relation should be suggested to the
user.
1015
Core ConceptsProduct Configurator

===== PAGE 1030 =====

Set Product Selling Model in a Constraint
Use the productSellingModel tagname to write a constraint that sets the Product Selling Model (PSM) for a type. You can define a
PSM as one time, time-deferred (subscription with end date), or evergreen (recurring subscription with no preset end date). The
PSM is updated for new line items at runtime, based on the constraint.
Logical Constraints
A logical constraint defines a statement that must hold true logically. The constraint can be any logical expression by using a logical
operator.
For example, the statement c0 ? c1 : c2  means that if c0  is true, then c1  needs to be true, otherwise c2  needs to be true.
Constraint Syntax Patterns
Here are the details of the constraint syntax patterns.
• constraint(logic expression);: The simplest form, enforcing a logic statement.
• constraint(logic expression, string literal | string variable);: Includes an optional failure
explanation that is displayed if the constraint is violated.
• constraint(logic expression, string literal | string variable, arg, …, arg);: Includes a
failure explanation with additional arguments to be interpolated into the string of the failure explanation.
If a constraint is violated, it takes an optional string variable or string literal as the failure explanation. The failure explanation could be in
a string format with additional arguments. CML supports two string formats. One is the standard string format and another is a string
with {} placeholder, to be replaced with the actual argument value.
Key Components of the Constraint Syntax
Here are the details of the key components of the constraint syntax.
Code SampleDescriptionComponent
Basic
constraint(generator.sum(quantity)
> 20);
This can be a basic mathematical expression
(using operators like +, -, * , /) or a relational
expression (using ==, !=, >, <, and so on).
It can also include logical operators such as
AND (&&), OR (||), NOT (!), the implication
Logic Expression
operator (->), or the bi-directional operator
(< - >).
With Explanation
constraint(x + y <= 100,
"Total must not exceed
100");
This optional string literal or variable
provides a human-readable reason for the
violation. CML supports two formatting
styles for these strings:
Failure Explanation
• Java string format (for example, using
%d or %s).
• Placeholder format using {}
1016
Core ConceptsProduct Configurator

===== PAGE 1031 =====

Code SampleDescriptionComponent
With Explanation and Arguments
constraint(requiredKW <=
2500, "The required capacity
Arguments are used to replace the
placeholders in the failure explanation string
with actual values at runtime.
Arguments (arg)
of {} kW exceeds the
maximum supported limit of
2500 kW.",requiredKW);
See the complete example in Constraints using Format Specifiers (%s, %d) and Dates on page 1042.
Constraint Example
In this example, the first constraint specifies that, if the DutyRating  value isn't Prime Power (PRP), then the quantity of
Warranty_PRP (Warranties subtype) must be 0. Similarly in the second constraint, if DutyRating  value isn't Data
Center Continuous (DCC)  then the quantity of Warranty_DCC  must be 0. Lastly, in the third constraint, if DutyRating
value isn't Emergency Standby Power (ESP), then the quantity of Warranty_ESP  must be 0.
type Warranty;
type Warranty_PRP : Warranty;
type Warranty_DCC : Warranty;
type Warranty_ESP : Warranty;
type GeneratorSet {
string DutyRating = ["Prime Power (PRP)", "Continuous Power (COP)", "Data Center Continuous
(DCC)", "Emergency Standby Power (ESP)"];
relation Warranties : Warranty[3];
constraint(DutyRating != "Prime Power (PRP)" -> Warranties[Warranty_PRP] == 0);
constraint(DutyRating != "Data Center Continuous (DCC)" -> Warranties[Warranty_DCC] == 0);
constraint(DutyRating != "Emergency Standby Power (ESP)" -> Warranties[Warranty_ESP] ==
0);
}
Example: Constraints Using String and Logical Operators
This example demonstrates how a GeneratorSet uses string functions to extract a numeric voltage value, and then uses logical operators
(->, &&, ||) to enforce safety and certification requirements.
Explanation of Operators Used in the Example
Here are the details of the operators used in the example.
Usage in ExampleCategoryOperator/Function
Converts the extracted voltage string to the
integer Voltage3.
String Functionstrtoint()
Replaces the full Voltage string with only
the second matched group (the high
String Functionregexpreplace()
voltage number) using the defined
VOLTAGE_REGEX.
1017
Core ConceptsProduct Configurator

===== PAGE 1032 =====

Usage in ExampleCategoryOperator/Function
Checks if the DutyRating  string
contains the substring "Power".
String Functionstrcontain()
Defines a conditional rule: If the condition
on the left is true, the condition on the right
must be true.
Logical Implication->
Requires both conditions (high requiredKW
AND duty rating contains "Power") to be
true.
Logical AND&&
Requires standardsAndCompliance
to be "Listing-UL 2200" or
"Certification-CSA".
Logical OR||
Used to check if the string value is "Not
Equal" to a specific string literal.
Comparison/Relational!=
// --- Constants (Required for String Manipulation) ---
define VOLTAGE_REGEX "^(+)/(+)$"
// --- Base Type and Configuration Attributes ---
type Warranty;
type Warranty_ESP : Warranty;
type GeneratorSet {
// String input attribute for user selection
string Voltage = ["277/480", "2400/4160", "7976/13800"];
// String input attribute for operational mode
string DutyRating = ["Prime Power (PRP)", "Continuous Power (COP)", "Emergency Standby
Power (ESP)"];
// String input attribute for compliance
string standardsAndCompliance = ["Certification-CSA", "Listing-UL 2200"];
// Required KW (Int attribute)
int requiredKW = [101..10000];
// warranties for generator set
relation Warranties : Warranty[3];
// 1. STRING OPERATORS/FUNCTIONS: Deriving Numeric Data
// We use strtoint() combined with regexpreplace() to extract the second number (the
high voltage)
// from the Voltage string (e.g., extracting 480 from "277/480").
int Voltage3 = strtoint(regexpreplace(Voltage, VOLTAGE_REGEX, "$2"), 0);
// Prime Power or Continuous Power using strcontain
boolean NonstandbyPower = !strcontain(DutyRating, "ESP");
// 2. LOGICAL OPERATOR (Implication ->): Certification Validation
// Constraint: If the standard is UL 2200 (precondition), THEN Voltage3 must be <= 600
(postcondition).
1018
Core ConceptsProduct Configurator

===== PAGE 1033 =====

constraint(
standardsAndCompliance == "Listing-UL 2200" -> Voltage3 <= 600,
"The UL 2200 standard covers stationary engine generator assemblies rated at 600
volts or less."
);
// 3. LOGICAL OPERATORS (AND &&, OR ||) and STRING FUNCTION (strcontain)
// Constraint: If the required power is high AND the unit is used for Prime Power OR
Continuous Power,
// THEN a specific standard must be selected.
constraint(
(requiredKW >= 5000 && NonstandbyPower)
->
(standardsAndCompliance == "Listing-UL 2200" || standardsAndCompliance ==
"Certification-CSA"), "High power and continuous use requires a major compliance
standard.");
// 4. LOGICAL OPERATOR (Implication ->) and String Comparison (!=)
// Constraint: If the Duty Rating is NOT Emergency Standby Power, THEN a specific
warranty (Warranties[Warranty_ESP]) must be excluded/zero.
constraint(
DutyRating != "Emergency Standby Power (ESP)" -> Warranties[Warranty_ESP] == 0,
"The DutyRating when not equal to Emergency Standby Power, implies that the Warranty
must be 0."
);
}
How User Input Order Affects Constraint Engine Behavior
The constraint engine is architecturally designed to never override or modify a user-selected value when evaluating constraints, except
in the specific case of an exclude  rule. If a constraint violation occurs due to user input, the engine generates an error message rather
than attempting to fix the value itself.
Example: Constraint Evaluation Based on Input Order (Generator Set)
The order in which a user configures attributes for a product (such as a GeneratorSet) determines whether the constraint engine
performs an automatic update or enforces a validation error.
Consider a constraint within the GeneratorSet  type that links the operational requirement (DutyRating) to the required
certification (standardsAndCompliance).
type GeneratorSet {
// Attribute 1 (Precondition): User selects operational mode
string DutyRating = ["Prime Power (PRP)", "Continuous Power (COP)"];
// Attribute 2 (Dependent): Certification standard
string standardsAndCompliance = ["Certification-CSA", "Listing-UL 2200"];
// Constraint: If the unit is configured for Prime Power, it must have UL 2200 Listing.
constraint(
DutyRating == "Prime Power (PRP)" -> standardsAndCompliance == "Listing-UL 2200",
"Prime Power Duty Rating requires UL 2200 Listing"
);
}
1019
Core ConceptsProduct Configurator

===== PAGE 1034 =====

The outcomes depend on the user's input sequence.
Constraint Engine ResultUser Input SequenceScenario
The constraint engine recognizes the
precondition is met and updates the
The user first sets DutyRating  to
"Prime Power (PRP)".
Scenario 1: Successful Update (Precondition
first)
dependent attribute, setting
standardsAndCompliance  to
"Listing-UL 2200". The constraint is
validated.
The existing user-selected value
("Certification-CSA") violates the
The user first sets
standardsAndCompliance  to
Scenario 2: Constraint Violation (Conflicting
Value first)
constraint. The constraint engine will not"Certification-CSA", and then sets
override the user's prior selection to changeDutyRating  to "Prime Power
(PRP)". it to "Listing-UL 2200". Instead, the
engine displays an error.
To resolve the error in Scenario 2, the user must manually adjust one of their selections: either change the DutyRating  (precondition)
or manually update the standardsAndCompliance (dependent value) to "Listing-UL 2200".
Left-Hand Side and Right-Hand Side Behavior in Constraint Resolution
Operator precedence and constraint engine resolution process determines whether the left-hand side (LHS) or right-hand side (RHS) of
a constraint changes or is constrained to maintain logical validity. Variable origin, which means whether variables are user-selected,
calculated, or restricted by system limitations, can also affect the outcome for the LHS or RHS in an expression.
These examples show how different user inputs lead to different outcomes for the LHS and RHS in the same expression.
Example 1. Implication Operator (->): Directional Enforcement
type Order {
int quantity = [1..1000];
boolean requiresApproval;
constraint bulkOrderApproval (
quantity >= 100 -> requiresApproval == true
);
}
The implication constraint A -> B  (if A, then B) is the primary method for defining a mandatory outcome. The engine evaluates the
LHS (A) first. If the quantity  is 150 (LHS TRUE), then the engine forces requiresApproval  (RHS) to be TRUE.
OutcomeScenario
The user sets a quantity greater than or equal to 100 on the LHS,
which makes the condition true. The engine sets or changes the
value of requiresApproval, the RHS, to true.
Scenario A: LHS is True, RHS Changes
The user manually sets requiresApproval, the RHS variable, to false.
Since the implication true -> false is forbidden, the LHS condition
Scenario B: RHS is False, LHS is Constrained to be False
must be false to satisfy the constraint. The engine constrains
quantity on the LHS to be less than 100 to make the LHS false.
1020
Core ConceptsProduct Configurator

===== PAGE 1035 =====

Example 2. Bi-conditional (<->): Symmetrical Equivalence
type BulkOrderSystem {
int quantity = [1..1000];
boolean requiresApproval;
boolean isBulkOrder;
constraint bulkOrderStatus (
isBulkOrder <-> (quantity >= 100 && requiresApproval),
"Bulk order status requires 100+ quantity AND management approval."
);
}
The bi-conditional constraint A <->  B (A if and only if B) requires that the LHS and RHS must share the same Boolean truth value. Either
side can act as the driver, forcing the other side to change. In the example above:
• A is the boolean variable isBulkOrder.
• B is the complex condition (quantity >= 100 && requiresApproval).
OutcomeScenario
If the user manually sets the attribute isBulkOrder to true (making
the LHS true), the engine immediately forces the RHS (quantity >=
Scenario A: LHS Drives RHS
100 && requiresApproval) to also be true, ensuring that both
quantity is at least 100 and requiresApproval is set to true.
If the user selects a configuration where the quantity is high (for
example, 500) and then sets requiresApproval to false (making the
Scenario B: RHS Drives LHS
RHS condition false), the engine immediately forces the LHS
attribute isBulkOrder to false to maintain equivalence.
Exception: The exclude Rule
The only scenario where the constraint engine intentionally overrides user input is when processing the exclude  rule. If a user selects
a component or sets an attribute value that violates an exclude  rule, the engine will automatically override that user input to satisfy
the exclusion constraint. In all other constraint types (like implication constraints shown previously), the engine relies on the user to fix
the error. For more information, see Exclude Rule on page 1036.
Table Constraints
The table constraint in Constraint Modeling Language (CML) is used to define a set of valid combinations of values for two or more
attributes. These combinations are specified in rows within the constraint definition.
The table constraint has this syntax:
table(variable, …, variable, {value, .. value}, …, {value, …, value});
Each row inside {} defines a valid combination of values.
Example: Table Constraint
In this example:
• Variables: The attributes Voltage  and DutyRating  are listed as the columns for the table.
1021
Core ConceptsProduct Configurator

===== PAGE 1036 =====

• Table Rows: Each row defined within the curly braces ({}) specifies a valid combination. For instance, {"7976/13800",
"Continuous Power (COP)"}  is a valid pairing.
• Enforcement: If a user attempts to select a high voltage ("7976/13800") while choosing a Prime Power rating ("Prime Power
(PRP)"), the table constraint is violated, and the engine displays the error message: "Selected Voltage is not compatible with the
required Duty Rating."
// --- Component Types ---
type GeneratorSet {
// 1. Attributes whose values must align according to the table
string Voltage = ["220/380", "277/480", "7976/13800"];
string DutyRating = ["Prime Power (PRP)", "Continuous Power (COP)", "Emergency Standby
Power (ESP)"];
// 2. Table Constraint
// Defines valid combinations where Voltage and DutyRating are mutually dependent.
constraint validOperationalModes(
table(
Voltage,
DutyRating,
{"220/380", "Prime Power (PRP)"},
{"220/380", "Continuous Power (COP)"},
{"220/380", "Emergency Standby Power (ESP)"},
{"277/480", "Prime Power (PRP)"},
{"277/480", "Emergency Standby Power (ESP)"},
{"7976/13800", "Continuous Power (COP)"}
),
"Selected Voltage is not compatible with the required Duty Rating."
);
}
Import Data from a Salesforce Object to Populate a Table Constraint
Import data from a standard or custom Salesforce object to use in a table constraint in a constraint model. The imported data populates
the columns and rows in the table constraint in CML, and saves you the step of manually entering the data.
To import data from a Salesforce object, first assign Read, Create, Edit, and Delete permissions for the object to the Constraint Rules
Engine Licenseless permission set. See Import Data from Salesforce Objects to Use in Constraint Models in Salesforce Help.
In CML, use the SalesforceTable keyword and the syntax shown here to import data from a Salesforce object. This example uses the
GeneratorSet type to constrain the calculated running capacity (gc_runningKw) based on a user's selection of the nominal
output (Nominal_Power_Output), referencing an external Salesforce custom object named PowerCst__c.
Example: Imported Table Constraint
type GeneratorSet {
// 1. Attribute storing the user-selected power output (String)
string Nominal_Power_Output = ["100 kW", "300 kW", "500 kW", "700 kW"];
// 2. Attribute storing the resulting Running kW (Decimal, calculated)
@(configurable = false, defaultValue = "0")
decimal(2) gc_runningKw;
// Constraint ensures the pairing of Nominal_Power_Output and gc_runningKw is found in the
imported Salesforce table.
constraint(
table(
Nominal_Power_Output, gc_runningKw,
1022
Core ConceptsProduct Configurator

===== PAGE 1037 =====

SalesforceTable("PowerCst__c","Nominal__c,Running__c")
)
);
}
Explanation of the Imported Table
The table constraint ensures that the selected values for Nominal_Power_Output  and gc_runningKw  must form one of the
valid combinations defined in the external source.
• Table (Nominal_Power_Output, gc_runningKw, ...): These are the CML attributes whose values must correlate. They define
the columns of the required combination table.
• Salesforce Table ("PowerCst__c", "Nominal__c,Running__c"): This function keyword directs the constraint engine
to import data from the Salesforce custom object PowerCst__c.
• Field Mapping: The fields specified ("Nominal__c,Running__c") define the columns in the Salesforce object that correspond
to the CML attributes listed in the table function. Nominal__c maps to Nominal_Power_Output, and Running__c maps to
gc_runningKw.
Proxy Variables with Constraints on Types and Relationships
Use proxy variables to reference the variables of related types, including parent, root, and sibling types.
The supported proxy variables include:
• Cardinality
• Parent
• this.quantity
Cardinality
Cardinality is a fundamental concept in Constraint Modeling Language (CML), controlling the quantity of product instances allowed in
a defined relationship. It is crucial for ensuring product structure validity and optimizing performance.
The cardinality  proxy variable refers to the cardinality of a relationship, that is, the quantity of instances of the same type in a
relationship. The first parameter is the type name. The second, optional parameter is the port name. This variable differs from the
this.quantity proxy variable, which refers to the quantity of the current instance.
Use this format:
cardinality(<type name>, <relation name>) or cardinality(<type name>)
Each parameter value can be a string or a string variable. If the relation name isn't specified, the engine searches all ports to find the
type.
The cardinality bounds are defined within the relation declaration using square brackets, formatted as [minimum..maximum].
Cardinality Examples
These examples illustrate how cardinality is defined and managed in the Generator Set model, focusing on standard definition, conditional
enforcement, and reading the quantity.
1023
Core ConceptsProduct Configurator

===== PAGE 1038 =====

Example 1: Using Cardinality Full Syntax
type Heater ;
type GeneratorSet {
//Define the relation and specify the smallest cardinality required for performance
relation Heaters : Heater[0..10];
//Declare a variable to hold the count
int totalHeaterCount = [0..10];
// This counts instances of type "Heater" specifically within the "Heaters" relation.
int InstancesofHeater = cardinality(Heater, Heaters);
constraint(totalHeaterCount == InstancesofHeater);
// Optional message to display the count to the user
message(totalHeaterCount> 0, "Current configuration includes {} heaters.", totalHeaterCount,
"Info");
}
See Message Rule on page 1034.
Example 2: Using Cardinality Partial Syntax
type Heater ;
type OutputTerminal ;
// Main Generator Set type
type GeneratorSet {
// Define multiple relations that might contain specific types, each with a specified
cardinality
relation Heaters : Heater[2];
relation OutputTerminals : OutputTerminal[0..99];
// Define derived attributes with an explicit domain
int totalHeatersFound = [0..100];
int totalTerminalsFound = [0..100];
// Partial cardinality SYNTAX
// The engine searches all relations to find the specified type
// Counts all instances of "Heater" across the entire GeneratorSet
int AllHeaterInstances = cardinality(Heater);
constraint(totalHeatersFound == AllHeaterInstances);
// Counts all instances of "OutputTerminal" across all relations
int AllOutputTerminals = cardinality(OutputTerminal);
constraint(totalTerminalsFound == AllOutputTerminals);
// Optional message for user visibility
message(totalHeatersFound > 0, "System found {} heaters in this configuration.",
totalHeatersFound, "Info");
}
Example 3: Defining Cardinality in Relations
This example shows how the Generator Set uses different cardinality ranges to define fixed requirements, optional components, and
minimum quantities for necessary components.
type GeneratorSet {
// 1. Fixed Cardinality: Exactly one General Model (component) is required.
// means min=1 and max=1.
relation GeneralModels : GeneralModel [1..1];
// 2. Bounded Optional Cardinality: Between 0 and 5 Temperature Sensors are allowed.
1024
Core ConceptsProduct Configurator

===== PAGE 1039 =====

// [0..5] means the component is optional but limited.
relation TemperatureSensors : TemperatureSensor[0..5];
// 3. Minimum Required Cardinality: At least 1 Test record is required, up to 99.
// [1..99] enforces inclusion.
relation Testing : Test[1..99];
}
type GeneralModel;
type TemperatureSensor;
type Test ;
Key Concepts:
• Syntax: Cardinality is specified immediately after the component type in the relation declaration.
• Best Practice: Specifying the smallest required range, such as [1..1] or [0..5], ensures the constraint engine tests fewer combinations,
which prevents performance degradation.
Example 4: Enforcing Conditional Cardinality via require()
Cardinality can be dynamically enforced based on attributes of the parent product using the require()  constraint keyword. For
more information, see Require Rule on page 1035.
type GeneratorSet {
int requiredKW = [101..10000];
string standardsAndCompliance = ["Certification-CSA", "Listing-UL 2200"];
// Relation for mandatory installation accessories
relation Accessories : Accessory[1..99];
relation Testing : Test[1..99];
// Conditional Requirement based on power level:
// If the required power is over 5000 kW, exactly 5 specific Accessory instances are
required.
require(
requiredKW > 5000,
Accessories [Accessory] == 5,
"High capacity generators require exactly 5 specialized accessory kits."
);
// Conditional Requirement based on compliance standard:
// If UL 2200 is selected, exactly 2 Test records must be included.
require(
standardsAndCompliance == "Listing-UL 2200",
Testing [Test] == 2,
"UL 2200 listing mandates exactly two certification tests."
);
}
type Accessory;
type Test;
This pattern (require(condition, relation[type] == N, ...)) allows the CML model to enforce a precise fixed
number of child components when a quantity threshold or attribute condition is met on the parent.
Cardinality vs. Count
The cardinality()  keyword is a proxy variable used to refer to the size of a relationship. The count() keyword is an aggregate
function that counts matching components or attribute conditions within a relation. Both can be used to read quantities for validation
or aggregation rules.
1025
Core ConceptsProduct Configurator

===== PAGE 1040 =====

Example for Similarity
Both cardinality()  and count()  can be used to determine the total quantity of items in a relationship. In this scenario, they
return the same value because the count()  condition covers all possible active instances.
type Accessory{
boolean isPresent = true;
}
type Bundle {
relation items : Accessory[0..10];
int totalByCount = [0..10];
// Similarity: Both can read the headcount of the relation
// Use the proxy variable to set an attribute
int totalByCardinality = cardinality(Accessory, items);
// Use count() aggregate function within a constraint
constraint(totalByCount == items.count(isPresent == true));
}
Example for Difference
The core difference is that cardinality is a proxy variable representing the headcount or size of the relation, whereas count is a function
used to evaluate specific attribute conditions or filters within those instances.
type Accessory {
int weight = [1..100];
boolean isEssential;
}
type Bundle {
relation items : Accessory[1..20];
// 1. Declare variables with explicit domains
int totalHeadcount = cardinality(Accessory,items);
int heavyItemsCount = [0..20];
int essentialItemsCount = [0..20];
// DIFFERENCE 1: Cardinality (Proxy Variable)
// Cardinality refers to the relationship size (how many instances are present).
// It does not look at the values of the attributes within the instances.
// DIFFERENCE 2: Count (Aggregate Function)
// Count MUST use a logical expression to evaluate conditions within the relation.
// It filters the instances based on attribute logic before returning a total.
// Example: Counting only accessories that weigh more than 50kg
constraint(heavyItemsCount == items.count(weight > 50));
// Example: Counting only accessories marked as 'essential'
constraint(essentialItemsCount == items.count(isEssential == true));
// Business Logic using both:
message(
heavyItemsCount > (totalHeadcount / 2),
"Warning: More than half of your accessories ({}) are heavy items.",
heavyItemsCount
);
}
For more information, see Message Rule on page 1034.
1026
Core ConceptsProduct Configurator

===== PAGE 1041 =====

Parent
The parent()  proxy variable is used to enable components at any level of the product hierarchy (child, grandchild, etc.) to access
the attributes (variables) defined by their ancestor types. This mechanism facilitates the flow of configuration data and calculated values
from the top of the bundle down to its components.
The parent()  keyword functions as a proxy variable used to reference attributes residing in the immediate parent or any ancestor
type in the configuration model.
PurposeSyntaxVariable Name
Retrieves the value of an attribute from a
parent or ancestor type.
parent(<ancestor variable
name>, <level>)
parent()
Key Characteristics
• Targeting Ancestors: The first parameter is the name of the attribute in the ancestor type that you wish to reference.
• Level Parameter: The second parameter (<level>) is optional and specifies how many levels up the hierarchy the engine should
search. If omitted, it typically references the immediate parent. The level index for the parent()  function effectively starts from
0 (implicit) for the immediate parent.
• Level 0 (Default): When you use parent(attributeName), the engine references the attribute in the immediate parent.
• Level n: When you specify parent(attributeName, 1), the engine reaches one level beyond the immediate parent, to
the grandparent.
• Data Flow: parent()  ensures that the data flows unidirectionally, where the child reads attributes calculated or defined by the
parent, thereby helping to prevent complex circular dependencies.
• Single Inheritance: CML follows a single inheritance model, where a type can only extend one other type at a time.
• Same Variable Name: In CML, reusing the same variable name between a parent bundle and its child accessories is a standard
architectural pattern for cascading values down a product hierarchy. This allows a child component to automatically inherit or
synchronize its properties with the parent type, ensuring configuration consistency.
Example: Standards and Compliance Synchronization
In this example, the standardsAndCompliance  selection made at the bundle level is automatically passed down to every
accessory within that bundle.
type AccessoryBundle {
// 1. Define the attribute at the Bundle level
string standardsAndCompliance = ["Certification-CSA", "Listing-UL 2200"];
// Relation to accessories
relation accessories : Accessory[1..10];
}
type Accessory {
// 2. Reuse the same variable name
// The parent() function targets the attribute in the immediate parent
string standardsAndCompliance = parent(standardsAndCompliance);
// Business Logic: If the inherited standard is UL 2200, price is affected
decimal(2) testingFee = [0.00..500.00];
constraint(standardsAndCompliance == "Listing-UL 2200" -> testingFee == 250.00);
}
1027
Core ConceptsProduct Configurator

===== PAGE 1042 =====

The parent()  proxy variable is essential for cascading configuration data and constraints down the product hierarchy, allowing child
components to reference attributes defined by their ancestors.
Example: Parent Attribute Reference
This example utilizes attributes found on the GeneratorSet  type (the parent) and demonstrates how related components (like
TemperatureSensor) access those values using the parent() proxy variable. Here is the hierarchy context.
Key Attribute UsageCardinalityChild TypeRelation NameParent Type
Defines primary inputs
(requiredKW) and a
[0..5]TemperatureSensorTemperatureSensorsRoot GeneratorSet
derived attribute
(ULComplianceEnforced)
based on the
standardsAndCompliance
selection.
Uses the parent()
proxy variable to
Not ApplicableNot ApplicableNot ApplicableChild
TemperatureSensor
reference the(Instance within
requiredKW attributeGeneratorSet
relation) from its ancestor
(GeneratorSet). A
constraint ensures the
component's capacity
(maxOperatingKW)
meets the requirement
inherited from the parent.
Inherits functionality from
TemperatureSensor.
Not ApplicableNot ApplicableNot ApplicableGrandchild
StatorTemperatureSensor
Uses parent() to retrieve(Subtype of
TemperatureSensor) the calculated
ULComplianceEnforced
boolean from the
GeneratorSet.
Enforces a conditional
installation rule using the
Implication Operator (->).
// --- Parent Type (GeneratorSet) ---
type GeneratorSet {
// Attributes defined by the parent
int requiredKW = [101..10000]; // Required power rating
string standardsAndCompliance = ["Certification-CSA", "Listing-UL 2200"]; // Compliance
choice
// Derived status: True if UL 2200 is selected (precondition for compliance checks)
boolean ULComplianceEnforced = standardsAndCompliance == "Listing-UL 2200";
// Relation to child components
1028
Core ConceptsProduct Configurator

===== PAGE 1043 =====

relation TemperatureSensors : TemperatureSensor[0..5];
}
// --- Child Component Type (TemperatureSensor) ---
type TemperatureSensor {
// Temperature sensors may have a model that defines max operating KW
int maxOperatingKW = [1000..10000];
// Retrieve the required KW value from the immediate parent (GeneratorSet)
int parentRequiredKW = parent(requiredKW);
// Constraint ensures the sensor can handle the power defined by the parent
constraint(maxOperatingKW >= parentRequiredKW, "Sensor capacity must meet the required KW
set by the generator set.");
}
// --- Specific Sensor Type (Grandchild) ---
type StatorTemperatureSensor : TemperatureSensor {
// Retrieve the boolean compliance flag from the immediate parent (GeneratorSet)
boolean enforceULCompliance = parent(ULComplianceEnforced);
// Constraint ensures that if UL Compliance is enforced by the parent,
// this sensor must meet a specific installation requirement (e.g., must be shielded)
string installationMethod = ["Standard", "Shielded"];
constraint(enforceULCompliance -> installationMethod == "Shielded",
"UL Compliance requires a shielded temperature sensor installation."
);
}
// Note: To reference a value further up the hierarchy, the optional level parameter can
be used:
// int grandParentValue = parent(requiredKW, 1); // Accesses attribute 1 level up
Explanation of Parent Reference
• Direct Reference (Immediate Parent): In the TemperatureSensor  type, int parentRequiredKW =
parent(requiredKW);  accesses the requiredKW  attribute defined in the immediately superior type, which is
GeneratorSet.
• Unidirectional Data Flow: The parent()  proxy variable is critical for enabling unidirectional data flow, where calculated or defined
values in the parent are read by children to enforce constraints. The engine ensures that parent aggregation and calculation are
complete before the parent()  function executes in the child component.
this.quantity
this.quantity  is a proxy variable used specifically to access the quantity of the current instance (the specific product line item)
within a configuration.
Key Characteristics and Usage
• Scope: It refers only to the quantity of the specific instance in which it is used. It is used at the component level to determine the
quantity of that item chosen by the user or set by the constraint engine.
• Calculation Rule: The this.quantity  proxy variable can be used only within a calculation rule.
• Distinction from cardinality(): this.quantity  differs from the cardinality()  proxy variable, which refers to the
total number of instances of a specific type within a relationship and includes the quantity of other instances of the same type.
• Read-Only/Validation: When accessing quantity in CML, attributes like this.quantity, or external equivalents like
lineItemQuantity  or ItemEndQuantity, are treated as read-only and should be used only in calculation or evaluation
rules. It is not recommended to use it to drive component creation, which should be done via cardinality.
1029
Core ConceptsProduct Configurator

===== PAGE 1044 =====

Example: Using this.quantity for Calculation
In the Generator Set configuration, a component like the NaturalGasReformer  may use this.quantity  to define a local
attribute representing how many units were selected, which is then used for internal calculations (like total capacity or total weight
contribution).
type LineItem;
type NaturalGasReformer : LineItem {
// 1. Definition: The LineItemQuantity attribute captures the quantity of this specific
instance.
// The CML syntax dictates defining an attribute (LineItemQuantity) that equals
this.quantity.
int LineItemQuantity = this.quantity;
// Placeholder: Attribute representing unit capacity per reformer unit
int unitCapacityKW = 100;
// 2. Calculation: Used in a calculation rule to determine total capacity based on the
quantity selected for this line item instance.
int totalReformerCapacity = LineItemQuantity * unitCapacityKW;
}
Group Type
In Constraint Modeling Language (CML), a Group Type is used to logically containerize related components within a bundle configuration,
primarily when product component groups are imported from Product Catalog Management (PCM).
The Group Type uses specific annotations to control the total quantity of components selected from that group, regardless of the
individual component type.
Bundles and Group Types (also known as Product Component Groups or PCGs) represent different levels of a product hierarchy and
serve distinct functional roles in configuration logic.
Conceptual Hierarchy
• Bundles are high-level parent products that contain multiple child products sold together as a package. In CML, they are defined as
"root types" that encapsulate the properties, relationships, and constraints for the entire entity.
• Group Types are structural containers within a bundle. They act as intermediate folders that organize related components imported
from Product Catalog Management (PCM). Instances of these Group Types are declared as variables inside the root Bundle type.
Role in Cardinality and Selection
• Bundles establish the primary relationship between a root product and its broad categories of components.
• Group Types are specifically designed to enforce cardinality rules for a collection of products. They use the @(minInstanceQty)
and @(maxInstanceQty)  annotations to control exactly how many instances can be selected from a specific set of options
(for example, "select at least 1 but no more than 2 accessories"). While the selected component can have a high quantity, the Group
Type restricts the number of unique instances chosen from that group.
Syntactic Implementation
• Accessing Components: For standard bundles, you reference components directly via their relation name. For components within
a Group Type, you must use dot notation starting with the group variable name defined in the root type (for example,
accessoryGroup.mouse.Wireless == true).
1030
Core ConceptsProduct Configurator

===== PAGE 1045 =====

• Constraint Limitations: You cannot write a constraint directly on a Group Type's attribute to apply it to all components within that
group; constraints must reference the specific child components.
• Identification: Group Types are automatically identified by a Group suffix and the presence of instance cardinality annotations during
the import from PCM.
Note:  The following examples are partial. See the complete code in the final CML code sample.
Example 1: Defining Generator Set Group Types
We can define two group types for a Generator Set configuration: CoreModelGroup  (mandatory selection of a primary generator
model) and EnclosureGroup  (optional selection of a specific enclosure type).
For the CoreModelGroup, setting minInstanceQty  to 1 and maxInstanceQty  to 1 means that at least 1 is required, and
a maximum of 1 is permitted.
@(minInstanceQty=1, maxInstanceQty=1)
type CoreModelGroup {
// Relation holds the actual Generator Model products
relation generalModel : GeneralModel[0..9999];
}
type GeneralModel : LineItem {
int powerKW;
}
For the EnclosureGroup, setting minInstanceQty  to 0 and maxInstanceQty  to 1 means that selecting an enclosure is
optional, but if selected, the user can add at most one instance of an enclosure component (such as WeatherproofEnclosure).
@(minInstanceQty=0, maxInstanceQty=1)
type EnclosureGroup {
relation enclosure : Enclosure;
relation cabinetHeater : ControlCabinetHeater;
}
type Enclosure : LineItem;
type ControlCabinetHeater : LineItem;
Example 2: Referencing Group Types in the Root Bundle
Once defined, instances of these group types are used as variables within the root type, which represents the entire bundle. In this
example, the coreModelGroup  and enclosureGroup  are instances of the respective group types, defined within the root
type GeneratorSetBundle.
type GeneratorSetBundle {
CoreModelGroup coreModelGroup;
EnclosureGroup enclosureGroup;
}
Example 3: Writing Constraints on Group Components
To write constraints or rules that reference components inside a group, use dot notation starting with the group variable name defined
in the root type.
1031
Core ConceptsProduct Configurator

===== PAGE 1046 =====

This example shows how a constraint might be defined within the GeneratorSetBundle  type to enforce business logic on
components within the groups.
// If the selected generator model has a powerKW greater than 1500,
// then a Control Cabinet Heater must be included in the Enclosure Group.
constraint(coreModelGroup.generalModel.powerKW > 1500 ->
enclosureGroup.cabinetHeater[ControlCabinetHeater] == 1);
// Require an Enclosure component if the set requires seismic certification.
require(seismicCertification == "IBC Seismic Certification",
enclosureGroup.enclosure[Enclosure],
"Enclosure required for seismic certification");
Final CML Code Sample with Group Types
This structure defines the complete model, showing the component hierarchy and the relationship constraints.
Key Attribute UsageCardinalityChild TypeRelation NameParent Type
The group type defined
by
Group Cardinality: 1CoreModelGroupcoreModelGroup
(Group Instance)
GeneratorSetBundle
@minInstanceQty=1,
maxInstanceQty=1.
This enforces that exactly
one component choice
must be made from the
internal generalModel
relation.
The group type defined
by
Group Cardinality: [0..1]EnclosureGroupenclosureGroup
(Group Instance)
GeneratorSetBundle
@minInstanceQty=0,
maxInstanceQty=1.
This enforces that
selecting components
from this group is
optional (min 0) and at
most one total
component instance can
be selected (max 1).
/**
* The Root Bundle: GeneratorSetBundle
* This type holds instances of the defined Group Types and the definition of seismic
certification */
type GeneratorSetBundle {
string seismicCertification = ["IBC Seismic Certification", "OSHPD Seismic Certification"];
CoreModelGroup coreModelGroup;
EnclosureGroup enclosureGroup;
// Constraint 1: If the selected GeneralModel has a powerKW greater than 1500,
// then a Control Cabinet Heater must be included in the Enclosure Group.
constraint(coreModelGroup.generalModel.powerKW > 1500 ->
1032
Core ConceptsProduct Configurator

===== PAGE 1047 =====

enclosureGroup.cabinetHeater[ControlCabinetHeater] == 1);
// Constraint 2: Require an Enclosure component if the set requires seismic certification.
require(seismicCertification == "IBC Seismic Certification",
enclosureGroup.enclosure[Enclosure],
"Enclosure required for seismic certification");
// Action Rule Example: Disable a specific enclosure type if the core model is low power
(e.g., 900kW).
rule(coreModelGroup.generalModel.powerKW == 900, "disable", "relation",
"enclosureGroup.enclosure", "type", "ReinforcedEnclosure");
}
/**
* Group Type 1: Core Model Group (Mandatory, Single Select)
* Min/Max Instance Quantity controls the selection rules for components within this group.
*/
@(minInstanceQty=1, maxInstanceQty=1)
type CoreModelGroup {
// Relation holds the actual Generator Model products
relation generalModel : GeneralModel[0..9999];
}
/**
* Group Type 2: Enclosure and Accessories Group (Optional)
* minInstanceQty=0 means selection is optional. maxInstanceQty=1 limits the selection to
a single enclosure or accessory component instance.
*/
@(minInstanceQty=0, maxInstanceQty=1)
type EnclosureGroup {
relation enclosure : Enclosure;
relation cabinetHeater : ControlCabinetHeater;
}
/**
* Component Types (Children)
*/
type GeneralModel {
int powerKW;
}
type Enclosure {
@(defaultValue = "false")
boolean Weatherproof;
}
type ReinforcedEnclosure : Enclosure; // Subtype of Enclosure
type ControlCabinetHeater;
Key Considerations
When reviewing Group Types in the context of the Generator Set model, keep these architectural points in mind.
• Group Cardinality Enforcement: The annotations @(minInstanceQty)  (minimum instance quantity) and
@(maxInstanceQty)  (maximum instance quantity) are defined on the Group Type itself (ElectricalSafetyGroup).
These annotations control the overall cardinality for all the components contained within that group, regardless of the individual
relation cardinality defined (for example [0..1], [1..2]).
• Root Reference: The GeneratorSetBundle includes the groups as variables (coreModelGroup and enclosureGroup).
• Constraint Syntax for Group Components: Constraints access attributes or components inside the groups using dot notation starting
with the group variable name (for example, coreModelGroup.generalModel.powerKW).
1033
Core ConceptsProduct Configurator

===== PAGE 1048 =====

• Limitation on Group Attributes: You cannot write a constraint directly on a group's attribute and expect it to apply to all components
within that group (for example, constraint(enclosureGroup.color == "Black")) is not a valid constraint).
Message Rule
The message rule displays a message to users based on specified conditions.
Message rules have this syntax:
message(logical expression, string literal | string variable, argument, .., argument,
severity);
message(logical expression, string literal | string variable, severity);
message(logical expression, string literal | string variable);
A message rule can take optional arguments to generate the message and indicate the severity of the message as the last argument.
Message severity can be Info, Warning, or Error. Without an explicit message severity argument, the message will be treated
as Info.
Understand the behaviour of each message severity type at runtime.
• The Info  message type doesn't require the user to take any action in order to continue with the current task. Info messages display
a gray banner.
• The Warning  message type allows the user to continue working on the current task, but blocks them from taking the next step
until they take action to address the issue described in the message. Warning messages display a yellow banner.
• The Error  message type blocks the user from continuing with the current task until they fix the error described in the message.
Error messages display a red banner. Note: An Error message doesn't block a user working in the Transaction Line Editor (Transaction
Line Table, or TLT). In that component, the user can still make changes and save the quote, even when the quote contains conditions
that trigger an Error message.
Message format can be a Java string, or a string with {} as a placeholder. The constraint solver replaces each {} with arguments specified
after the string, in the order they are written.
Example
In this example, if requiredKW  is greater than 2500, a message is displayed that the specified required kW is larger than the
supported options and must be changed.
type GeneratorSet {
int requiredKW = [101..10000];
message(requiredKW > 2500, "The required kW is above what the current options can support.
Please adjust to 2500 kW or select a new generator set that meets your requirements.");
}
Preference Rule
The preference rule encourages the constraint solver to satisfy the condition, but doesn't enforce it if the condition can't be met.
The system tries to satisfy the condition in a preference rule, but if for some reason it can't, the system delivers a failure message to the
user with Info  severity.
The preference rule has this syntax.
preference(logic expression, string literal | string variable, argument, .., argument);
preference(logic expression, string literal | string variable);
preference(logic expression);
1034
Core ConceptsProduct Configurator

===== PAGE 1049 =====

A preference rule can include an optional explanation message for failure. The message is of Info  severity, meaning it does not block
the user from continuing with the action.
In this example, the preference rule encourages the user to mention the dBMax  value as 90  and the requiredKW value as 500.
type GeneratorSet {
int requiredKW = [101..10000];
int dBMax = [0..140];
preference(dBMax == 90, "90 preferred for dbMax");
preference(requiredKW == 500,"50 preferred for requiredKW");
}
Require Rule
The require rule requires certain components to be included in a relationship when specified conditions are met.
Required components can have attributes and quantity specified. The require rule can include an optional explanation message, for the
rule failure explanation.
In certain scenarios, you can independently add a type at the header level. This means you can include a specific type even if it isn't
explicitly defined as part of any of the relationships you've configured. This capability offers flexibility in managing and including necessary
types that might not always fall under a specific relationship structure.
Note:  When you assign a require rule to a virtual bundle (a bundle related to the sales transaction, where the parent product has
no associated price), set one Product Selling Model Option on the required product to Default. For more information on Product
Selling Model Options, see Manage Product Selling Model in Revenue Cloud.
The require rule has this syntax:
require(logic expression, relationship[type]{var=value,…,var=value}==integer value,
"Explanation message");
In this example, the require rule specifies that if the number of engineers is more than 0, installation is required. The installation will be
automatically added upon adding an engineer.
type GeneratorSet {
relation engineers : engineer[0..99];
relation installation : install[0..5];
require(engineers[engineer] > 0, installation[install], "Installation is required if
engineers are present");
}
type engineer{}
type install{}
Require Rule vs Constraint
In Constraint Modeling Language (CML), constraint() and require() can both enforce behavior, but they operate differently: constraint
focuses on logical consistency, require focuses on physical presence of products.
Here's a comparison between constraint()  and require().
require()constraint()Feature
Forces a product to be present.Validates if a condition is met (LHS) and
operates on the result (RHS).
Primary goal
1035
Core ConceptsProduct Configurator

===== PAGE 1050 =====

require()constraint()Feature
Adds the required product to the quote.Resolves the constraint or displays an error
if there are no options to resolve.
Engine action
SetDefault Rule
The setDefault rule allows component selection with attribute values and quantity, similar to the require rule.
Unlike the require rule, the setDefault rule applies a default configuration status and uses a triggering mechanism to control when the
solver attempts to satisfy the rule. The setDefault rule can include an optional explanation message.
The setDefault has this syntax, similar to the require rule.
setDefault(condition, expression, message);
When the setDefault rule evaluates the condition:
• If the condition is false, the solver ignores the expression and doesn't display a message, regardless of whether any part of the
condition is changed.
• If the condition is true, the solver performs one of these actions.
• If any part of the condition is changed or the parent component is new, the solver attempts to satisfy the expression. If the solver
can't satisfy the expression, an explanation message is displayed (if included).
• If no part of the condition is changed, the solver evaluates the expression without attempting to satisfy it. If the expression evaluates
to false, an explanation message is displayed (if included).
The key difference between the setDefault rule and the require rule is that the setDefault rule attempts to satisfy the expression only
when a condition is changed. If no condition is changed, the setDefault rule performs a passive evaluation. The require rule always
attempts to satisfy the expression when the condition is true.
In this scenario, we use the requiredKW attribute (the user's power requirement) as the condition and the Accessories relation as the
target for the recommended cardinality.
type Accessory;
type GeneratorSet {
int requiredKW = [101..10000];
relation Accessories : Accessory[1..99];
/**
* @Title High Power Accessory Recommendation
* The setDefault constraint specifies that 2 accessory units are
* recommended when the required power capacity is greater than 2000 kW.
*/
setdefault(
requiredKW > 2000,
Accessories[Accessory] == 2,
"2 specialized accessory kits are recommended for power levels above 2000 kW"
);
}
Exclude Rule
The exclude rule is used to automatically remove a specific type in a relationship if a certain condition is met.
1036
Core ConceptsProduct Configurator

===== PAGE 1051 =====

The exclude rule has this syntax.
exclude(logic expression, relationship[type],"Explanation message");
The type must be leaf type, a node without children.
In the exclude rule, if a user sets attribute values in Product Catalog Management (PCM) that violate the rule requirements, the constraint
engine overrides the user input in order to validate the constraint. This behavior is different than other constraints, in which the constraint
engine doesn't override user input, but displays an error if user input violates the constraint. See How User Input Order Affects Constraint
Engine Behavior section in Logical Constraints on page 1016.
In this example, the exclude rule automatically removes the Heater_120  heater from the type GeneratorSet  if the Voltage3
is greater than or equal to 4160.
type GeneratorSet {
int Voltage3 = [120..13800];
relation Heaters : Heater_120 [1..3];
exclude(Voltage3 >= 4160, Heaters[Heater_120]);
}
type Heater_120 {}
Action Rule
The CML Action Rule is defined using the rule() keyword. Its primary purpose is to execute a designated action, specified as a string literal,
when a condition is met.
This action is typically handled by external systems, such as the Product Configurator API or custom code, to manage business processes,
workflows, or complex constraints that fall outside the constraint engine's primary scope.
Action rules have this syntax.
rule(condition, action, arg, ..., arg)
rule(<condition>, <action>, "attribute", <attribute>);
rule(<condition>, <action>, "attribute", <attribute>, "value", [<attribute values>]);
rule(<condition>, <action>, "relation", <relation>, "type", <type>);
condition  is any logic expression such as a constraint in CML.
action  is a string literal that specifies an action that can be interpreted by the Product Configurator API. The Product Configurator
API supports these actions.
• Hide: hide attribute, attribute value, product option
• Disable: disable attribute, attribute value, product option
• args are a list of arguments needed to execute the action. An argument is a pair including a string literal and an identifier, a literal,
or a domain, enclosed in brackets [ ] to specify multiple values. The string literal specifies what kind of argument follows. The identifier
attribute can be defined in the type. The engine retrieves the argument value and passes it to the caller to execute the action.
Hide or Disable Rule
The Hide or Disable Rule uses the rule() keyword to conditionally remove an element from the selection menu (hide) or preserve it in
the menu while preventing user selection (disable).
This functionality can be applied.
• On a bundle, hide a component to remove it from the selection menu, or disable a component to preserve it in the menu but prevent
users from selecting options for it.
1037
Core ConceptsProduct Configurator

===== PAGE 1052 =====

• On an individual product, hide an attribute to remove it from the selection menu, or disable an attribute to preserve it in the menu
but prevent users from selecting options for it.
• On an attribute, hide or disable an attribute value to preserve it in the menu but prevent users from selecting options for it. For
attribute values, the hide and disable rules have the same behavior.
Note:  In Visual Builder in Salesforce, for attribute values, only the hide rule is enabled. When you apply the hide rule to an attribute
value in Visual Builder, the value appears in the menu but selections are disabled.
The hide and disable rules use this syntax, where action  is replaced by either hide  or disable.
rule(logic expression, action, actionScope, actionTarget)
rule(logic expression, action, actionScope, actionTarget, actionClassification,
actionValueTarget)
Example: Hiding and Disabling Features
In the example in this section, rules rely on specific variables to define the scope and target of the action.
DescriptionExample from Generator
Set
PurposeVariable in Rule
The logical test that triggers the
action.
requiredKW <= 500Condition upon which the rule
occurs.
logic expression
(Declaration)
Determines if the element is
removed from view or made
unselectable.
"hide", "disable"Designates whether the rule is
hide or disable.
action
Specifies if the target is a variable
property or a component
relationship.
"attribute",
"relation"
Designates whether the rule acts
on an attribute or relation scope.
actionScope
The Constraint Modeling
Language (CML) name of the
attribute or relation.
"Voltage",
"StarterMotors"
Designates the specific variable
or relation that the rule acts on.
actionTarget
Used when targeting
components within a relation
"type", "value"Designates whether the rule acts
on a type or a value.
actionClassification
(type) or specific options within
an attribute domain (value).
The specific string value or type
name to hide or disable.
"7976/13800",
"StarterMotor_Advanced"
Designates the specific type or
value that the rule acts on.
actionValueTarget
// --- Component Definitions (For relations referenced below) ---
type LineItem;
type EngineModel : LineItem;
type StarterMotor : LineItem;
type OutputTerminal : LineItem;
type OutputTerminals2HoleLugNEMA : OutputTerminal; // Specific terminal type
type GeneratorSet : LineItem {
// Attributes subject to hide/disable rules
int requiredKW = [101..10000];
1038
Core ConceptsProduct Configurator

===== PAGE 1053 =====

string Voltage = ["220/380", "240/416", "4160/7200", "7976/13800"]; // Voltage is the
attribute being hidden/disabled
string specialApplication = ["None - Standard", "Motor Starting"]; // specialApplication
attribute contains a value to hide
// Relations subject to hide/disable rules
relation StarterMotors : StarterMotor; // Relation target (component) to hide/disable
relation OutputTerminals : OutputTerminal[0..99]; // Relation being acted upon
// 1. Disable a Component (Type) in a Relation
// If requiredKW is too low (<= 500 kW), the advanced starter motor component is disabled
(visible but unselectable).
rule(
requiredKW <= 500,
"disable",
"relation",
"StarterMotors",
"type",
"StarterMotor_Advanced" );
// 2. Hide an Attribute
// If the Generator is configured for a special purpose (Motor Starting), hide the Voltage
attribute entirely.
rule(
specialApplication == "Motor Starting",
"hide",
"attribute",
"Voltage"
);
// 3. Hide a Specific Attribute Value
// If the power requirement is low (< 2000 kW), hide the high voltage option (7976/13800)
from the Voltage attribute domain.
rule(
requiredKW < 2000,
"hide",
"attribute",
"Voltage",
"value",
"7976/13800"
);
// 4. Disable a Component Type (Alternate Syntax using the component name)
// Disable the OutputTerminals2HoleLugNEMA component if the required KW is high.
rule(
requiredKW >= 5000,
"disable",
"relation",
"OutputTerminals",
"type",
"OutputTerminals2HoleLugNEMA"
);
}
type StarterMotor_Advanced : StarterMotor; // Subtype used in the rule
Recommendation Rule
The recommend keyword is used within a Constraint Modeling Language (CML) rule to display suggestions for related products in the
Product Configurator. The rule defines the condition under which a specific product type or relation should be suggested to the user.
1039
Core ConceptsProduct Configurator

===== PAGE 1054 =====

You can recommend a type, a relation, or both in the same rule. The recommendation rule can be added inside a standalone product,
a product bundle, or a virtual container.
Unlike action rules that are interpreted directly by the Product Configurator API, when the condition is met, the engine forces a UI change
(hiding or disabling a product option, attribute, or value). Recommendations are not automatically applied to the UI by the configuration
engine alone. To suggest types or relations (products/bundles), typically for up-selling or cross-selling based on their current selections
at runtime, use the Run Config Rules action within a Salesforce Flow. See Run Config Rules Action in the Revenue Cloud Developer Guide.
• Use an action rule when a selection makes another option invalid or irrelevant. For example, if a user selects a basic warranty, you
should "hide" or "disable" the premium support options to prevent a conflicting or impossible setup.
• Use a recommendation rule when you want to nudge the user toward a beneficial add-on. For example, if a user buys a high-end
generator, you "recommend" a maintenance service contract. This does not block the user if they choose not to add it.
Here are 3 examples demonstrating how to implement product recommendation rules.
Example 1: Recommending a Type (Based on Attribute Selection)
This rule is placed within the GeneratorSet  type. If a user selects an extremely high voltage, the configuration engine recommends
a specialized engineer component required for installation or commissioning.
type GeneratorSet {
// Attribute input
string Voltage = ["277/480", "7976/13800"];
// Relation to the component type being recommended
relation engineers : engineer[0..99];
// Recommend Engineer Specialist (type) for High Voltage
rule(
Voltage == "7976/13800", "recommend", "type", "EngineerSpecialist"
);
}
// Recommended type
type EngineerSpecialist ;
type engineer;
Example 2: Recommending a Relation (Based on Component Quantity)
This rule recommends adding items to an existing relation (Accessories) if the user selects a high-end component (such as the
most robust enclosure, Enclosure_SA3).
type GeneratorSet {
// Relations defined in the GeneratorSet
relation Enclosures : Enclosure;
relation Accessories : Accessory[1..99]; // The relation being recommended
// Recommend Accessories when maximum sound dB is chosen
rule(
Enclosures[Enclosure_SA3] == 1,
"recommend",
"relation",
"Accessories");
}
type Enclosure ;
type Enclosure_SA3 : Enclosure;
type Accessory ;
1040
Core ConceptsProduct Configurator

===== PAGE 1055 =====

Example 3: Recommending a Type (From a Virtual/System Container)
This rule is applied at the Quote or System level (using a virtual  type) and recommends a system integration product if multiple
generators are being configured, reflecting the requirement that large projects often need central control components.
@(virtual = true)
type Quote {
// Relation referencing all GeneratorSet instances on the quote
@(sourceContextNode = "SalesTransaction.SalesTransactionItem")
relation lineItems : GeneratorSet[0..10];
// Recommend Switchgear for multi-unit orders
rule(
lineItems[GeneratorSet] > 1,
"recommend",
"type",
"Switchgear"
);
}
type GeneratorSet;
type Switchgear;
Set Product Selling Model in a Constraint
Use the productSellingModel tagname to write a constraint that sets the Product Selling Model (PSM) for a type. You can define a PSM
as one time, time-deferred (subscription with end date), or evergreen (recurring subscription with no preset end date). The PSM is
updated for new line items at runtime, based on the constraint.
You can’t use a Constraint Modeling Language (CML) constraint to update the PSM for an existing quote line. For more information on
product selling models, see Manage Product Selling Model in Revenue Cloud in Salesforce Help.
Constraint Example
Using the GeneratorSet  model, a constraint can be defined that sets the PSM based on a specific operational attribute chosen by
the user, such as the DutyRating. This assumes that different duty ratings correspond to different billing models (for example,
permanent installation versus temporary rental).
This example sets the PSM to a specific ID (for example, PSM_EVERGREEN_ID) if the user selects the "Continuous Power (COP)" duty
rating.
//Global variable PSM ID
define PSM_EVERGREEN_ID "a00Tx000000Qz1g"
type GeneratorSet {
// Use the productSellingModel tag from the context definition
@(tagName = "ProductSellingModel")
string productSellingModel;
string DutyRating = ["Prime Power (PRP)", "Continuous Power (COP)", "Emergency Standby
Power (ESP)"];
// Set PSM based on Duty Rating
constraint(
DutyRating == 'Continuous Power (COP)' -> productSellingModel == PSM_EVERGREEN_ID
);
}
1041
Core ConceptsProduct Configurator

===== PAGE 1056 =====

Core Concept Examples
These examples illustrate core Constraint Modeling Language (CML) concepts including type, relationships, constraints, and so on.
For an explanation of the constraint model structure in these examples, see Model Structure on page 1107.
Example 1: Use Regex Global Variable
// Global Constant: Regex used to parse voltage strings
define VOLTAGE_REGEX "^([11-19]+)/([11-19]+)$"
type LineItem;
type GeneratorSet : LineItem {
// Core attributes
@(configurable = false)
int requiredKW = [101..10000]; // Required power capacity
string Voltage = ["220/380", "240/416", "277/480", "7976/13800"];
string standardsAndCompliance = ["Certification-CSA", "Listing-UL 2200"];
// Calculated attributes
// Surge load is 1.25 times the required KW
decimal(2) surgeLoadKW = requiredKW * 1.25;
// Voltage3 extracts the secondary voltage (e.g., 380 or 416) for checks
int Voltage3 = strtoint(regexpreplace(Voltage, VOLTAGE_REGEX, "$2"), 0);
// Relation to model components
relation GeneralModels : GeneralModel[11];
// Constraint 1: Ensure model capacity meets the required KW
constraint(GeneralModels[GeneralModel].powerKW >= requiredKW,
"Selected Generator Model is insufficient for the required power.");
// Constraint 2: UL 2200 standard restricts voltage to 600V or less (Implication rule)
constraint(standardsAndCompliance == "Listing-UL 2200" -> Voltage3 <= 600,
"The UL 2200 standard covers stationary engine generator assemblies rated at 600
volts or less.");
}
// Component type definition (GeneralModel is a product component)
type GeneralModel : LineItem {
int powerKW = [900, 1200, 1500, 1750, 2500];
int dB = [20..23];
}
Key Technical Details
• The GeneratorSet  type is related to the GeneralModel  type through a single relation.
1042
Core Concept ExamplesProduct Configurator

===== PAGE 1057 =====

Key Attribute UsageCardinalityChild TypeRelation NameParent Type
Constrained by
requiredKW  on the
parent type.
Not ApplicableGeneralModelGeneralModelsGeneratorSet
• Parent Type (GeneratorSet): Defined as a LineItem  component, the GeneratorSet  holds configuration parameters
such as the user's power requirement (requiredKW), the specified voltage (Voltage), and compliance standards
(standardsAndCompliance). It also includes calculated attributes like surgeLoadKW  and Voltage3.
• Child Type (GeneralModel): Defined as a LineItem  component, the GeneralModel  specifies the technical attributes of
the selected generator configuration, including its power output (powerKW) and noise rating (dB).
• Cardinality: The relation GeneralModels : GeneralModel specifies the quantity bounds for the component, indicating
that exactly 11 instances of the GeneralModel  type must be included in this configuration.
Example 2: Use Groupby Annotation to Create Virtual Group
Using Groupby annotation for types, this model creates a virtual VoltageGroup  for every unique voltage (for example, "220/380",
"480/277") found in the transaction.
// 1. The physical product type
type GeneratorSet {
@(configurable = false)
int requiredKW = [101..10000];
string Voltage = ["220/380", "240/416", "255/440", "277/480"];
// Calculation with explicit domain for best practice
decimal(2) surgeLoadKW = [126.25..12500.00];
constraint(surgeLoadKW == requiredKW * 1.25);
}
// 2. The virtual container grouped by the "Voltage" attribute
@(split=true, virtual=true, groupBy=Voltage)
type VoltageGroup {
string Voltage; // The attribute used for grouping
decimal(2) groupTotalSurgeKW = [0.00..99999.99];
// Map instances to this group from the transaction line items
@(sourceContextNode="SalesTransaction.SalesTransactionItem")
relation generators : GeneratorSet[0..50];
// Aggregation: Sum only the surge load of generators in THIS voltage group
constraint(groupTotalSurgeKW == generators.sum(surgeLoadKW));
// Business Rule: Limit total surge load per voltage branch
message(groupTotalSurgeKW > 10000, "Warning: Surge load for Voltage {} exceeds branch
capacity!", Voltage);
}
// 3. The top-level system managing the groups
@(virtual = true)
1043
Core Concept ExamplesProduct Configurator

===== PAGE 1058 =====

type GeneratorSystem {
relation generators : GeneratorSet[0..100];
relation voltageGroups : VoltageGroup[1..10];
decimal(2) systemTotalKW = voltageGroups.sum(groupTotalSurgeKW);
}
Key Technical Details
• groupBy=Voltage: The engine scans all GeneratorSet  instances and creates one virtual VoltageGroup  for each
unique voltage value detected (for example, one group for all "220/380" units, another for all "277/480" units).
• sourceContextNode: This tells the virtual group to pull its "children" (the generators) from the specific path in the Salesforce
context where quote line items are stored.
• Bottom-Up Aggregation: Each VoltageGroup  independently calculates its groupTotalSurgeKW  based strictly on the
generators assigned to it by the groupBy logic.
• Explicit Domains: Following best practices, the surgeLoadKW and groupTotalSurgeKW  use explicit domains (for example,
[0.00..99999.99]) to prevent "NullPointer" or initialization errors during solving.
Example 3: Use Sharingcount Annotation to Reuse Accessory Instances
In this example, we apply sharingcount annotation to the Accessory  type to allow the engine to reuse accessory instances across
the configuration up to a specified limit.
// 1. Define the component type with split and sharingCount
// split=true enables parallel solving by splitting quantity into multiple instances
// sharingCount=5 allows a single Accessory instance to be reused 5 times in the model
@(split = true, sharingCount = 5)
type Accessory {
string category;
decimal(2) weight;
}
type GeneratorSet {
@(configurable = false)
int requiredKW = [101..10000];
// 2. Define the relationship with the sharing annotation
// @(sharing = true) allows the engine to satisfy this relation by
// "pointing" to existing instances instead of creating new ones
@(sharing = true)
relation Accessories : Accessory[1..99];
}
Key Technical Details
• Parallel Solving: By setting split = true, the engine can process the 99 possible accessories in parallel rather than sequentially,
which is critical for large-scale generator configurations.
• Resource Management: The sharingCount = 5  tells the solver that it doesn't need to instantiate 99 unique Accessory
objects; it can reuse the same object definition up to five times across different parts of the configuration graph.
1044
Core Concept ExamplesProduct Configurator

===== PAGE 1059 =====

• Relationship Requirement: For sharingCount  to take effect, the Relation (the port) must also be annotated with @(sharing
= true)  to grant the engine permission to reuse instances.
Example 4: Use contextPath and tagName Annotations
// 1. GLOBAL EXTERN DECLARATIONS
// Unifying contextPath (header field) and tagName (context identifier)
@(contextPath = "SalesTransaction.ShippingCountry", tagName = "Region_Identifier")
extern string ShippingCountry = "International";
@(contextPath = "SalesTransaction.ProjectUrgency", tagName = "Priority_Level")
extern string ProjectUrgency = "Standard";
// 2. PHYSICAL PRODUCT TYPE
type GeneratorSet {
// Core technical attributes
@(configurable = false)
int requiredKW = [101..10000];
string DutyRating = ["Prime Power (PRP)", "Emergency Standby Power (ESP)"];
// Technical calculation with explicit domain (Best Practice)
decimal(2) surgeLoadKW = [126.25..12500.00];
constraint(surgeLoadKW == requiredKW * 1.25);
// 3. LOGIC INTEGRATING EXTERNAL DATA
// Using contextPath/tagName data to drive technical warnings
message(ShippingCountry == "US",
"Regional Notice: Generator must comply with US-specific UL 2200 standards.");
message(ProjectUrgency == "Critical" && requiredKW > 5000,
"High Priority Alert: Large scale power requirement in a Critical project
requires site inspection.",
requiredKW, "Warning");
}
Key Technical Details
• External Variable (extern): These are declared outside of any type to hold values supplied by the environment (Salesforce).
• contextPath  Annotation: This maps the variable directly to a header-level field in the Sales Transaction.
• tagName  Annotation: This links the variable to a specific Context Tag identifier within the Salesforce Context Definition.
Note:  Rules depending on these external variables (such as the ShippingCountry  message) only re-evaluate when a Line
Item change occurs (For example, updating requiredKW), not solely when the header field changes.
1045
Core Concept ExamplesProduct Configurator

===== PAGE 1060 =====

Example 5: Use Format Specifiers (%s, %d) and Dates in Constraints
In this example, we define a generator configuration that validates the required power (requiredKW) against the duty rating and
voltage, providing specific feedback when a mismatch occurs.
type GeneratorSet {
// 1. Core Technical Attributes with explicit domains
@(configurable = true)
int requiredKW = [101..10000];
string DutyRating = ["Prime Power (PRP)", "Continuous Power (COP)",
"Data Center Continuous (DCC)", "Emergency Standby Power (ESP)"];
string Voltage = ["220/380", "277/480", "347/600", "2400/4160"];
string standardsAndCompliance = ["Certification-CSA", "Listing-UL 2200"];
// Date Attribute Definition
// Date variables represent a specific day.
// You can define a fixed domain for a date as a range between two dates.
date requestedDeliveryDate = ["2024-01-01", "2025-12-31"];
// Message Rule with Multiple Arguments using placeholders
message(requiredKW > 5000 && DutyRating == "Emergency Standby Power (ESP)",
"High Capacity Alert: The %s rating for %d kW requires an additional cooling
system.",
DutyRating, requiredKW, "Warning");
// Constraint with Multiple Arguments using placeholders
constraint(Voltage == "2400/4160" && standardsAndCompliance == "Listing-UL 2200",
"Configuration Error: Voltage %s cannot be used with %s standards due to
safety limits.",
Voltage, standardsAndCompliance);
// Dates can be used in logical expressions with comparison operators like < or >=.
message(requestedDeliveryDate < "2024-09-01" && requiredKW > 7000,
"Schedule Warning: Delivery for %d kW units on %s may require expedited
manufacturing.",
requiredKW, requestedDeliveryDate, "Info");
}
Key Technical Details
• Multiple Arguments: You can pass several variables after the string literal. The engine maps them to the placeholders in the exact
order they appear.
• Format Specifiers
• %s  is used for string variables (for example, DutyRating  or Voltage).
• %d  is used for integer variables (for example, requiredKW).
• Placeholder Usage: Alternatively, you can use the {} syntax, which the constraint engine automatically replaces with the actual
argument values during runtime evaluation.
1046
Core Concept ExamplesProduct Configurator

===== PAGE 1061 =====

• Comparison Logic with Dates: You can treat dates as comparable values in constraint or message rules to enforce scheduling
logic (for example, ensuring a delivery date is not too early for a complex build).
Example 6: Use Arithmetic Calculations and Functions
This example demonstrates using aggregate functions (a virtual type for transaction-level aggregation) and mathematical functions
within the GeneratorSet  type for precise quantity calculation.
// --- Component Definition —
type GeneratorSet {
int requiredKW = [101..10000];
int quantity = [1..10];
// BEST PRACTICE: Define derived attributes with an explicit domain
decimal(2) surgeLoadKW = [0.00..12500.00];
// BEST PRACTICE: Put calculations inside of constraints
constraint(surgeLoadKW == requiredKW * 1.25);
}
// --- Accessory Definition ---
type Accessory {
int weight_kg = [1..100];
}
// --- Virtual System Type (Aggregation Context) ---
@(virtual = true)
type System {
@(sourceContextNode = "SalesTransaction.SalesTransactionItem")
relation generators : GeneratorSet[0..10];
relation shipmentbatch : ShipmentBatch [0..10];
// BEST PRACTICE: Attributes must have explicit domains
decimal(2) totalQuotedLoad = [0.00..125000.00];
int highPowerCount = [0..10];
// Aggregate calculations in separate constraints
constraint(totalQuotedLoad == generators.sum(surgeLoadKW));
// VARIATION: Condition-based count
// count() requires a logical expression
constraint(highPowerCount == generators.count(requiredKW > 5000));
// Ensuring Shipment batch crates are similar to the number of generators
message(
shipmentbatch.requiredCrates != generators[GeneratorSet],
"The Shipment items ({}) must match the number of Generators ({})",
shipmentbatch.requiredCrates, generators[GeneratorSet],
"Error"
);
}
type ShipmentBatch {
int totalItems = [1..100];
int itemsPerCrate = 10;
// BEST PRACTICE: Define derived attributes for the relation in the parent type
int totalWeight = [0..1000];
int accessoryCount = [0..10];
// Aggregates within the relation block
relation accessories : Accessory[0..10] {
accessoryWeight = sum(weight_kg);
accessoryCount = count(weight_kg > 0);
}
1047
Core Concept ExamplesProduct Configurator

===== PAGE 1062 =====

// Mapping relation attributes to parent variables via constraints
constraint(totalWeight == accessories.accessoryWeight);
constraint(accessoryCount == accessories.accessoryCount);
int requiredCrates = [0..100];
// Mathematical Function Example: CEIL
constraint calculateCeil(requiredCrates == ceil(totalItems / itemsPerCrate));
}
Key Considerations for Calculations and Aggregations
When implementing these functions in CML, follow these architectural best practices for robustness and performance.
• Explicit domains are required: All the derived attributes that result from a calculation or aggregation must have an explicit variable
domain definition. This practice ensures accurate aggregation and helps prevent runtime errors.
• Separate calculation from declaration: Define the aggregation or calculation in a separate constraint rather than using an inline
derived attribute declaration (for example, int total = items.sumPrice;). This separation helps avoid issues where
domains may not initialize correctly.
• Correct Pattern: Define the relation aggregate (totalQty = sum(quantity);) and then enforce the result via a constraint
(constraint(totalItemCount == items.totalQty);).
Annotation Examples
Constraint Modeling Language (CML) annotations are labels that you add to parts of a model, such as types, variables, relationships, and
constraints. Annotations control how these elements are shown and how they behave in the configurator. Annotations help fine-tune
the configurator and the constraint engine without changing the actual structure of the model.
The examples explain what each annotation does, where it can be used in the model, what kinds of values it supports, and how it behaves
when the configurator runs and evaluates constraints. CML code samples show how the annotation works in practice.
closeRelation Annotation
closeRelation is a CML annotation that controls addition of new line items to the relationship by the engine.
configurable Annotation
configurable  is a CML annotation that controls whether a model element can be configured.
defaultValue Annotation
The defaultValue  annotation is used on a variable to define the value it should start with when configuration begins.
domainComputation Annotation
domainComputation  is a CML annotation that specifies how the domain of a model element is determined, either by using a
fixed domain or by computing the domain dynamically during configuration.
peelable Annotation
The peelable  annotation is used to create soft selection values and allow the engine to modify these selections to satisfy a
constraint.
propagateUp Annotation
propagateUp  is a Constraint Modeling Language (CML) annotation that controls aggregation propagation between children
and parent elements.
relatedAttributes Annotation
relatedAttributes  is a Constraint Modeling Language (CML) annotation that resets the domain to the original one for
domainComputation.
1048
Annotation ExamplesProduct Configurator

===== PAGE 1063 =====

sequence Annotation
The sequence  annotation defines the execution and configuration order of elements in a Constraint Modeling Language (CML)
model.
split Annotation
split  is a Constraint Modeling Language (CML) annotation that specifies whether the instances of the type should be split or not.
closeRelation Annotation
closeRelation is a CML annotation that controls addition of new line items to the relationship by the engine.
closeRelationAnnotation
RelationshipApplicable to
true, falseValue Type/Values
If closeRelation  is not specified, the engine sets it implicitly
as false for the relationship.
Description
If closeRelation is specified as true, the engine prevents the
addition of new line items to the relationship.
If closeRelation  is specified as false, the engine allows the
addition of new line items to the relationship.
Example 1
In this example, the closeRelation  annotation isn’t specified for the relationship (mainalternatorclassification).
The model contains the constraint.
type LineItem;
type GeneratorSet : LineItem {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
relation mainalternatorclassification : MainAlternatorClassification;
constraint(dutyRating == "Continuous Power (COP)" ->
mainalternatorclassification[Alternator_240] >= 1);
}
type MainAlternatorClassification : LineItem;
type Alternator_220 : MainAlternatorClassification;
type Alternator_440 : MainAlternatorClassification;
type Alternator_240 : MainAlternatorClassification;
Example 2
In this example, the closeRelationannotation is defined as false for the relationship (mainalternatorclassification).
The model contains the constraint.
type LineItem;
type GeneratorSet : LineItem {
@(defaultValue = "Emergency Standby Power (ESP)")
1049
Annotation ExamplesProduct Configurator

===== PAGE 1064 =====

string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
@(closeRelation = false)
relation mainalternatorclassification : MainAlternatorClassification;
constraint(dutyRating == "Continuous Power (COP)" ->
mainalternatorclassification[Alternator_240] >= 1);
}
type MainAlternatorClassification : LineItem;
type Alternator_220 : MainAlternatorClassification;
type Alternator_440 : MainAlternatorClassification;
type Alternator_240 : MainAlternatorClassification;
Example Description and Configurator Result
In example 1, the mainalternatorclassification relation is not specified with the closeRelation annotation, but
the system considers it as false  by default. In example 2, the relation is explicitly defined with false. As a result, if the user updates
the dutyRating  variable to "Continuous Power (COP)", the system adds the Alternator_240  product according
to annotation and constraint logic and allows addition of other products from the mainalternatorclassification  relation
(Alternator_220,Alternator_440). The system does not allow to unselect the Alternator_240  product specified in
the constraint while the "Continuous Power (COP)"  is selected. If the user updates the dutyRating  variable to another
value (For example, Emergency Standby Power (ESP)"), the engine removes the Alternator_240 product, but the
user can add/select/unselect all products from the relationship manually.
Example 3
In this example, the closeRelation annotation is specified as true for the relationship (mainalternatorclassification).
The model contains the constraint
type LineItem;
type GeneratorSet : LineItem {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
@(closeRelation = true)
relation mainalternatorclassification : MainAlternatorClassification;
constraint(dutyRating == "Continuous Power (COP)" ->
mainalternatorclassification[Alternator_240] >= 1);
}
type MainAlternatorClassification : LineItem;
type Alternator_220 : MainAlternatorClassification;
type Alternator_440 : MainAlternatorClassification;
type Alternator_240 : MainAlternatorClassification;
In example 3, the mainalternatorclassification relation is specified with the closeRelation  annotation as true.
As a result, if a user updates the dutyRating variable to "Continuous Power (COP)", the engine resets it back to "Emergency
Standby Power (ESP)"  to prevent adding the Alternator_240  product according to the annotation. The user can add
all mainalternatorclassification  products manually (including the Alternator_240  product specified in the
constraint).
1050
Annotation ExamplesProduct Configurator

===== PAGE 1065 =====

Table 8: closeRelation Configuration Settings
UI BehaviorEngine ActionUser Action"closeRelation"
annotation
Applicable toProduct Group
Structure
Associated
Example
Display product
specified in
Add the product
according to the
constraint. Allow
Change variable
value specified in
constraint
condition
not specifiedRelationshipIndividual
product
N/A
constraint as
pre-selected: if aaddition of other
products to the
relationship
User unselects it,
the product
returns back to
selected state.
User can select
other products
from the
relationship
Products from
the relation are
Reset the variable
value back to the
Change variable
value specified in
TRUERelationshipIndividual
product
N/A
not added ordefault value toconstraint
condition selected
(including the
avoid addition
the relation
product specifiedproduct specified
in the constraint in constraint).
User can
manually select
any products
from the
relationship
Display product
specified in
Add the product
according to the
constraint. Allow
Change variable
value specified in
constraint
condition
FALSERelationshipIndividual
product
N/A
constraint as
pre-selected: if aaddition of other
products to the
relationship
User unselects it,
the product
returns back to
selected state.
User can select
other products
from the
relationship
Display product
specified in
Add the product
according to the
constraint. Allow
Change variable
value specified in
constraint
condition
not specifiedRelationshipProduct
Classification
Example 1
constraint as
pre-selected: if aaddition of other
products to the User unselects it,
relationship from
1051
Annotation ExamplesProduct Configurator

===== PAGE 1066 =====

UI BehaviorEngine ActionUser Action"closeRelation"
annotation
Applicable toProduct Group
Structure
Associated
Example
browse products
pop up
the product
returns back to
selected state.
User can add
other products
from the
relationship in
browse products
pop up
Display product
specified in
Add the product
according to the
constraint. Allow
Change variable
value specified in
constraint
condition
FALSERelationshipProduct
Classification
Example 2
constraint as
pre-selected: if aaddition of other
products to the User unselects it,
relationship from the product
browse products
pop up
returns back to
selected state.
User can add
other products
from the
relationship in
browse products
pop up
Products from
the relation are
Reset the variable
value back to the
Change variable
value specified in
TRUERelationshipProduct
Classification
Example 3
not added ordefault value toconstraint
condition selected
(including the
avoid addition
the relation
product specifiedproduct specified
in the constraint in constraint).
User can
manually browse
and add any
products from
the relationship
configurable Annotation
configurable  is a CML annotation that controls whether a model element can be configured.
configurable  annotation specification: Variable
1052
Annotation ExamplesProduct Configurator

===== PAGE 1067 =====

configurableAnnotation
VariableApplicable to
true, falseValue Type/Values
If the configurable  annotation is not explicitly specified, the
engine sets it implicitly as true for the variable.
Description
If the configurable annotation is explicitly specified as true,
the variable is indicated as configurable. The engine sets the value
to the variable.
If the configurable  annotation is explicitly specified as false,
the engine doesn't set a value to the variable.
Example 1
In this example, the configurable annotation is not specified for the variable (Cable Entry) of the VoltageConnection child products.
The defaultValue  is not defined.
type GeneratorSet {
relation voltageConnections : VoltageConnection[1..999999];
}
type VoltageConnection {
string cableEntry = ["Top Entry", "Bottom Entry", "Side Entry"];
}
Example Description and Configurator Result
In this example, the configurable  annotation is not explicitly specified for the variable cableEntry, but the system considers
it as configurable = true  by default. As a result, the system sets the "Top Entry" (the first value in the ["Top Entry",
"Bottom Entry", "Side Entry"]  CML domain) as the initial value for the configurable Cable Entry variable.
Example 2
In this example, the configurable  annotation is specified as true  for the variable (Cable Entry) of the VoltageConnection child
products. The defaultValue  is not specified.
type GeneratorSet {
relation voltageConnections : VoltageConnection[1..999999];
}
type VoltageConnection {
@(configurable = true)
string cableEntry = ["Top Entry", "Bottom Entry", "Side Entry"];
}
Example Description and Configurator Result
In this example, the configurable  annotation is true  for the variable. As a result, the system specifies the variable as configurable
and sets the "Top Entry"  (the first value in the ["Top Entry", "Bottom Entry", "Side Entry"]  CML domain)
as the initial value for the Cable Entry.
1053
Annotation ExamplesProduct Configurator

===== PAGE 1068 =====

Example 3
In this example, the configurable  annotation is specified as false  for the variable (Cable Entry) of the VoltageConnection child
products. The defaultValue  is not specified
type GeneratorSet {
relation voltageConnections : VoltageConnection[1..999999];
}
type VoltageConnection {
@(configurable = false)
string cableEntry = ["Top Entry", "Bottom Entry", "Side Entry"];
}
Example Description and Configurator Result
In this example, the configurable  annotation is false  for the variable. As a result, the engine doesn't configure the variable
with an initial value, and it is displayed empty on the Product Configuration UI.
Example 4
In this example, the configurable  is false  and defaultValue  annotation is true  for the variable (Cable Entry) of the
VoltageConnection child products.
type GeneratorSet {
relation voltageConnections : VoltageConnection[1..999999];
}
type VoltageConnection {
@(configurable = true, defaultValue = "Side Entry")
string cableEntry = ["Top Entry", "Bottom Entry", "Side Entry"];
}
Example Description and Configurator Result
In this example, the system indicates the variable as configurable  and sets the "Side Entry"  as the initial value for the
Cable Entry  defined in the defaultValue annotation.
Example 5
In this example, the configurable  and defaultValue  annotations are specified for the variable (Cable Entry) of the
VoltageConnection child products.
type GeneratorSet {
relation voltageConnections : VoltageConnection[1..999999];
}
type VoltageConnection {
@(configurable = false, defaultValue = "Side Entry")
string cableEntry = ["Top Entry", "Bottom Entry", "Side Entry"];
}
Example Description and Configurator Result
In this example, the system sets the "Side Entry"  as the initial value for the Cable Entry  according to the defaultValue
annotation.
1054
Annotation ExamplesProduct Configurator

===== PAGE 1069 =====

Table 9: configurable Configuration Settings
UI BehaviorEngine ActionUser Action"CONFIGURABLE"
annotation
Applicable toProduct Group
Structure
Associated
Example
Display defined
by engine
Set the first value
from the variable
Configure the
product
containing
variable
not specifiedVariableIndividual
product
Example 1
variable value as
the default value
domain as initial
value.
If the User
changes the
variable value
manually, reset it
back to the first
value from the
variable domain.
If the default
value is defined
in PCM, reset it
back to the first
value from the
variable domain
Display defined
by engine
Set the first value
from the variable
Configure the
product
containing
variable
TRUEVariableIndividual
product
Example 2
Example 4 variable value as
the default value
domain as initial
value
If the User
changes the
variable value
manually, reset it
back to the first
value from the
variable domain.
If the default
value is defined
in PCM, reset it
back to the first
value from the
variable domain
If the
defaultValue
annotation is
specified for the
variable, set it as
initial value
1055
Annotation ExamplesProduct Configurator

===== PAGE 1070 =====

UI BehaviorEngine ActionUser Action"CONFIGURABLE"
annotation
Applicable toProduct Group
Structure
Associated
Example
Display defined
by engine or PCM
Set emptiness for
the variable as
Configure the
product
containing
variable
FALSEVariableIndividual
product
Example 3
Example 5 variable value as
the default value
initial value (If the
default value is
specified in PCM
for the variable,
set it as initial
value instead of
emptiness).
If the
defaultValue
annotation is
specified for the
variable, set it as
initial value
(despite of the
PCM default
value)
defaultValue Annotation
The defaultValue  annotation is used on a variable to define the value it should start with when configuration begins.
defaultValueAnnotation
VariableApplicable to
LiteralValue Type/Values
The configurator uses the default value defined in PCM (Product
Attribute Definition). If no PCM default is available, the configurator
uses the first value in the variable domain as the initial value.
Description
If no default value is defined in PCM and a defaultValue is specified
in CML, the configurator uses the value defined in CML as the initial
value of the variable.
Example 1
In this example, neither PCM nor CML defines a default value for the Cable Entry variable.
type GeneratorSet {
relation voltageConnections : VoltageConnection[1..999999];
}
type VoltageConnection {
1056
Annotation ExamplesProduct Configurator

===== PAGE 1071 =====

string cableEntry = ["Top Entry", "Bottom Entry", "Side Entry"];
}
Example Description and Configurator Result
The configurator sets "Top Entry"  as the initial value for Cable Entry, because it is the first value in the variable domain
["Top Entry", "Bottom Entry", "Side Entry".
Example 2
In this example, PCM (Product Attribute Definition) defines "Bottom Entry"  as the default value for Cable Entry, and no
defaultValue  annotation is defined for this variable in CML.
type GeneratorSet {
relation voltageConnections : VoltageConnection[1..999999];
}
// This annotation is added automatically if PCM has a default before the product is added
to CML. If the product already exists in CML, the annotation is added or updated only
after running Sync.
@(defaultValue = "Bottom Entry")
type VoltageConnection {
string cableEntry = ["Top Entry", "Bottom Entry", "Side Entry"];
}
Example Description and Configurator Result
The configurator sets the "Bottom Entry"  as the initial value for the Cable Entry  of the VoltageConnection  child
products.
As a best practice, define the default value in PCM and use the Sync function in CML to keep the model aligned whenever PCM settings
are updated.
Example 3
In this example, a defaultValue  annotation with "Side Entry"  is defined in CML, and no default value is defined in PCM for
the Cable Entry variable.
type GeneratorSet {
relation voltageConnections : VoltageConnection[1..999999];
}
type VoltageConnection {
@(defaultValue = "Side Entry")
string cableEntry = ["Top Entry", "Bottom Entry", "Side Entry"];
}
Example Description and Configurator Result
The configurator sets the "Side Entry" annotation value as the initial value for Cable Entry.
Note:  We recommend that you define default values in PCM (Product Attribute Definition) whenever possible, as this approach
promotes consistency across products and simplifies maintenance.
1057
Annotation ExamplesProduct Configurator

===== PAGE 1072 =====

The defaultValue annotation in CML should be used only when a default value is not suitable to be defined in PCM due to specific
modeling requirements.
When a default value is defined in PCM but the CML model has not been synced, the configurator still applies the PCM default. However,
the value displayed in the CML model may become inconsistent with PCM.
To avoid such inconsistencies, it is recommended to run the Sync action in CML after updating default values in PCM, so that the CML
model remains aligned with the latest PCM settings.
defaultValue Configuration Settings
Table 10: defaultValue Configuration Settings
Example UI
Result
Initial Value
Behavior
defaultValue
Specified
Configurable
Value
Configurable
Specified
Associated
Example
Automatically set to
"Top Entry"
Uses the first value in
the domain
Nodefault = TRUENoExample 1
Automatically set to
"Bottom Entry"
Uses the first value in
the domain
NoTRUEYesExample 2
Field remains emptyNo initial value is setNoFALSEYesExample 3
Automatically set to
"Side Entry"
Uses the value
defined in
defaultValue
YesTRUEYesN/A
Automatically set to
"Side Entry"
Still uses the value
defined in
defaultValue
YesFALSEYesN/A
domainComputation Annotation
domainComputation  is a CML annotation that specifies how the domain of a model element is determined, either by using a fixed
domain or by computing the domain dynamically during configuration.
domainComputation  annotation specification: Variable and Relationship
domainComputationAnnotation
Variable and RelationshipApplicable to
true, falseValue Type/Values
If domainComputation annotation is not
explicitly specified, the engine sets it
Description
implicitly as false for the variable, and
true for a relationship
If the domainComputation annotation is specified as true,
the variable or relationship domain is dynamically determined
based on the configuration and constraint logic.
1058
Annotation ExamplesProduct Configurator

===== PAGE 1073 =====

domainComputationAnnotation
If the domainComputation annotation is specified as false,
the variable domain is fixed.
Example 1
In this example, the domainComputation  annotation is not specified for the variable (voltage) of the GeneratorSet  type.
The model contains the constraints.
type GeneratorSet {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
string voltage = ["220/380", "240/416", "347/600", "255/440", "277/480", "2400/4160",
"7200/12470", "7621/13200", "7976/13800"]
constraint(dutyRating == "Continuous Power (COP)" -> voltage != "220/380");
constraint(dutyRating == "Data Center Continuous (DCC)" -> voltage == "255/440");
}
Example 2
In this example, the domainComputation annotation is explicitly specified as false for the variable (voltage) of the GeneratorSet
type. The model contains the constraints.
type GeneratorSet {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
@(domainComputation = false)
string voltage = ["220/380", "240/416", "347/600", "255/440", "277/480", "2400/4160",
"7200/12470", "7621/13200", "7976/13800"];
constraint(dutyRating == "Continuous Power (COP)" -> voltage != "220/380");
constraint(dutyRating == "Data Center Continuous (DCC)" -> voltage == "255/440");
}
Example Description and Configurator Result
In example 1, the domainComputation  annotation is not explicitly specified for the voltage  variable, but the system considers
it as false  by default. In example 2, the domainComputation  annotation is explicitly defined as false. As a result, the system
remains the variable domain unchanged (["220/380", "240/416", "347/600", "255/440", "277/480",
"2400/4160", "7200/12470", "7621/13200", "7976/13800"])  and executes the constraints:
If the dutyRating  is selected with the "Continuous Power (COP)"  value, the voltage  is pre-populated with the next
possible value from the variable domain ("240/416")  to satisfy the constraint.
If the dutyRating  is selected with the "Data Center Continuous (DCC)"  value, the voltage  is pre-populated with
the "255/440"  value to satisfy the constraint.
1059
Annotation ExamplesProduct Configurator

===== PAGE 1074 =====

Example 3
In this example, the domainComputation  annotation is explicitly specified as true  for the variable (voltage) of the
GeneratorSet  type. The model contains the constraints.
type GeneratorSet {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
@(domainComputation = true)
string voltage = ["220/380", "240/416", "347/600", "255/440", "277/480", "2400/4160",
"7200/12470", "7621/13200", "7976/13800"];
constraint(dutyRating == "Continuous Power (COP)" -> voltage != "220/380");
constraint(dutyRating == "Data Center Continuous (DCC)" -> voltage == "255/440");
}
Example Description and Configurator Result
In example 3, the domainComputation  annotation is explicitly specified as true  for the voltage  variable. As a result, the
system updates the variable domain based on the constraint logic.
If the dutyRating  is selected with the "Continuous Power (COP)"  value, the voltage is pre-populated with the next
possible value from the variable domain ("240/416")  to satisfy the constraint. The variable domain is updated to exclude the
"220/380" value.
If the dutyRating  is selected with the "Data Center Continuous (DCC)"  value, the voltage  is pre-populated with
the "255/440"  value to satisfy the constraint. The variable domain is updated to contain only the "255/440" value.
Example 4
In this example, the domainComputation annotation is not specified for the relationship (temperatureSensors). The model contains
the constraints.
type GeneratorSet {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
relation temperatureSensors : TemperatureSensor[0..1];
constraint(dutyRating == "Continuous Power (COP)" ->
temperatureSensors[BearingTemperatureSensor] == 0);
constraint(dutyRating == "Data Center Continuous (DCC)" ->
temperatureSensors[StatorTemperatureSensor] == 0);
}
type TemperatureSensor;
type BearingTemperatureSensor : TemperatureSensor;
type StatorTemperatureSensor : TemperatureSensor;
Example 5
In this example, the domainComputation  annotation is explicitly specified as true  for the relationship (temperatureSensors).
The model contains the constraints.
type GeneratorSet {
@(defaultValue = "Emergency Standby Power (ESP)")
1060
Annotation ExamplesProduct Configurator

===== PAGE 1075 =====

string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
@(domainComputation = true)
relation temperatureSensors : TemperatureSensor[0..1];
constraint(dutyRating == "Continuous Power (COP)" ->
temperatureSensors[BearingTemperatureSensor] == 0);
constraint(dutyRating == "Data Center Continuous (DCC)" ->
temperatureSensors[StatorTemperatureSensor] == 0);
}
type TemperatureSensor;
type BearingTemperatureSensor : TemperatureSensor;
type StatorTemperatureSensor : TemperatureSensor;
Example Description and Configurator Result
In example 4, the domainComputation  annotation is not explicitly specified for the temperatureSensors relationship, but
the system considers it as true  by default. In example 5, the domainComputation  annotation is explicitly specified as true
for the relationship. As a result, the system updates the relationship domain based on the constraint logic.
• If the dutyRating  is selected with the "Continuous Power (COP)"  value, the system re-computes the relationship
domain and excludes the BearingTemperatureSensor  product to satisfy the constraint. The
StatorTemperatureSensor  product remains and can be selected in scope of the GeneratorSet  bundle product;
• If the dutyRating  is selected with the "Data Center Continuous (DCC)"  value: the system re-computes the
relationship domain and excludes the StatorTemperatureSensor  product to satisfy the constraint. The
BearingTemperatureSensor  product remains and can be selected in scope of the GeneratorSet  bundle product.
Example 6
In this example, the domainComputation  annotation is explicitly specified as false  for the relationship
(temperatureSensors). The model contains the constraints.
type GeneratorSet {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
@(domainComputation = false)
relation temperatureSensors : TemperatureSensor[0..1];
constraint(dutyRating == "Continuous Power (COP)" ->
temperatureSensors[BearingTemperatureSensor] == 0);
constraint(dutyRating == "Data Center Continuous (DCC)" ->
temperatureSensors[StatorTemperatureSensor] == 0);
}
type TemperatureSensor;
type BearingTemperatureSensor : TemperatureSensor;
type StatorTemperatureSensor : TemperatureSensor;
Example Description and Configurator Result
In example 6, the domainComputation  annotation is explicitly specified as false  for the relationship. As a result, the system
remains the relationship domain unchanged and executes the constraints:
1061
Annotation ExamplesProduct Configurator

===== PAGE 1076 =====

If the dutyRating  is selected with the "Continuous Power (COP)"  value, the system displays both
BearingTemperatureSensor  and StatorTemperatureSensor  products in scope of the GeneratorSet  bundle
product. The BearingTemperatureSensor  product cannot be selected based on the constraint.
If the dutyRating  is selected with the "Data Center Continuous (DCC)"  value, the system displays both
BearingTemperatureSensor  and StatorTemperatureSensor  products in scope of the GeneratorSet bundle product.
The StatorTemperatureSensor  product cannot be selected based on the constraint.
domainComputation Configuration Settings
Table 11: defaultValue Configuration Settings
Constraint ModelActual Engine
Behavior
Actual UI
Behavior
User Action"domainComputation"
annotation
Applicable to
type
GeneratorSet
Remain the full
voltage domain.
Always show the full
voltage domain
regardless of the
Case 1: Duty Rating =
any except specified
in constraints (e.g.
not specifiedstring voltage
{Case 1: Duty Rating
= any except
Duty Rating
selection.
"Prime Power (PRP)",
"Emergency Standby
Power (ESP)"):
@(defaultValue
=
"Emergency
specified in
constraints (e.g.
"Prime Power (PRP)",• Initial value for the
voltage = the value
Standby
Power"Emergency
Standby Power
(ESP)"):
specified in the
@defaultValue
(ESP)")
string
dutyRating =
• If the configuration
is saved with initial
annotation
("220/380") ["Emergency
Standby
(default) voltage• The user can select a
different voltage value
Power
(ESP)",
"Prime Power
value ("220/380"):
attributeName":"voltage","cfgStatus":"Default"(e.g. "240/416",
(PRP)",
• If the configuration
is saved with User
"255/440" etc.). The
system remains User
selected voltage
"Continuous
Power
(COP)",selected voltage
value (e.g.• The user can save
the configuration with
"Data Center
Continuous
(DCC)"];
"255/440"):
attributeName":"voltage","cfgStatus":"Default"both values: initial
Case 2: Duty Rating
= "Continuous
Power (COP)"
voltage or
user-selected voltage
Case 2: Duty Rating =
"Continuous Power
(COP)"
@(defaultValue
=
"220/380")
string
voltage =
• If the configuration
is saved with
initial/reverted to• Initial value for the
voltage = next
["220/380",
"240/416",initial voltage value
("240/416"):
"attributeName":"voltage","cfgStatus":"Engine"
possible value from
the domain to satisfy
"347/600",
"255/440",
the constraint
("240/416")
"277/480",
"2400/4160",Case 3: Duty Rating
= "Data Center
Continuous (DCC)"
1062
Annotation ExamplesProduct Configurator

===== PAGE 1077 =====

Constraint ModelActual Engine
Behavior
Actual UI
Behavior
User Action"domainComputation"
annotation
Applicable to
• Warning: If the user
selects a different
• If the configuration
is saved with initial
"7200/12470",
("220/380")/othervoltage (e.g. "7621/13200",
constraint"220/380", "255/440",
"7976/13800"];specified("255/440")/reverted"2400/4160" etc.), the
to constraintsystem reverts it to
specified voltagethe initial value
("240/416") constraint(dutyRatingvalues ("220/380",
"255/440"):
"attributeName":"voltage","cfgStatus":"Default"
• The user can save
the configuration with
the initial voltage
==
"Continuous
Power (COP)"
-> voltagevalue (the !=configuration cannot "220/380");
be saved with other
voltage due to
reverting) constraint(dutyRating
== "DataCase 3: Duty Rating =
"Data Center
Continuous (DCC)"
Center
Continuous
(DCC)" ->
• Initial value for the
voltage = specified
voltage ==
"255/440" ||
voltage ==value in constraint
"220/380");
}that comes first in the
domain ("220/380")
• The user can select a
different vaild voltage
specified in constraint
("255/440"). The
system remains User
selected voltage
• If the user selects a
voltage that not vaild
in the constraint (e.g.
"240/416",
"2400/4160" etc.), the
system will revert it to
one of the values
defined in constraint
("220/380" or
"255/440")
• The user can save
the configuration with
the specified in
constraint voltage
1063
Annotation ExamplesProduct Configurator

===== PAGE 1078 =====

Constraint ModelActual Engine
Behavior
Actual UI
Behavior
User Action"domainComputation"
annotation
Applicable to
value (the
configuration cannot
be saved with other
voltage due to
reverting)
type
GeneratorSet
Update voltage
domain based on
Duty Rating
Show updated
voltage domain
based on Duty
Rating selection and
constraint logic.
Case 1: Duty Rating =
any except specified
in constraints (e.g.
"Prime Power (PRP)",
"Emergency Standby
Power (ESP)"):
TRUEstring voltage
{
@(defaultValue
=
"Emergency
selection and
constraint logic.
Case 1: Duty Rating
= any except• Display the full
voltage domain
Standby
Powerspecified in
constraints (e.g.• Initial value for the
voltage = the value
(ESP)")
string
dutyRating =
"Prime Power (PRP)",
"Emergencyspecified in the ["EmergencyStandby Power
(ESP)"):
@defaultValue
annotation
("220/380")
Standby
Power
(ESP)",
"Prime Power
• Remain the full
voltage domain• The user can select a
different voltage value
(PRP)",
"Continuous• If the configuration
is saved with initial(e.g. "240/416", Power
(default) voltage"255/440" etc.). The (COP)",
value ("220/380"):
attributeName":"voltage","cfgStatus":"Default"
system remains User
selected voltage
"Data Center
Continuous
(DCC)"];• If the configuration
is saved with User
• The user can save
the configuration with
selected voltageboth values: initial @(defaultValue
value (e.g.voltage or User
selected voltage
=
"220/380",
domainComputation
"255/440"):
attributeName":"voltage","cfgStatus":"Default"Case 2: Duty Rating =
"Continuous Power
(COP)"
= true)
string
voltage =
Case 2: Duty Rating
= "Continuous
Power (COP)"• Display updated
voltage domain
["220/380",
"240/416",
"347/600",
• Update voltage
domain accordingaccording to the "255/440",to the constraintconstraint (the "277/480",
(exclude the
"220/380" value)
"220/380" is not
shown)
"2400/4160",
"7200/12470",• If the configuration
is saved with
• Initial value for the
voltage = next "7621/13200",initial/revertedpossible value from
voltage valuethe domain to satisfy
1064
Annotation ExamplesProduct Configurator

===== PAGE 1079 =====

Constraint ModelActual Engine
Behavior
Actual UI
Behavior
User Action"domainComputation"
annotation
Applicable to
the constraint
("240/416")
("240/416"):
"attributeName":"voltage","cfgStatus":"Engine"
"7976/13800"];
Case 3: Duty Rating
= "Data Center
Continuous (DCC)"
• Warning: If the user
selects a different
voltage (e.g.
constraint(dutyRating
==
"255/440", "Continuous• If the configuration
is saved with initial"2400/4160" etc.), the
system reverts it to
Power (COP)"
-> voltage("220/380")/reverted
the initial value
("240/416")
!=
"220/380");to "220/380"
constraint specified
voltage value:
"attributeName":"voltage","cfgStatus":"Engine"
• The user can save
the configuration with
the initial ("240/416")
constraint(dutyRating
== "Data
voltage value (the Center
Continuousconfiguration cannot
(DCC)" ->be saved with other
voltage ==voltage due to
reverting) "255/440" ||
voltage ==
Case 3: Duty Rating =
"Data Center
Continuous (DCC)"
"220/380");
}
• Display updated
voltage domain
according to the
constraint (only
"220/380" and
"255/440" are shown,
other values are
excluded)
• Initial value for the
voltage = specified
value in constraint
that comes first in the
domain ("220/380")
• Warning: If the user
selects a different
voltage specified in
constraint ("255/440"),
the system reverts it
to the initial value
("220/380")
• The user can save
the configuration with
the initial voltage
1065
Annotation ExamplesProduct Configurator

===== PAGE 1080 =====

Constraint ModelActual Engine
Behavior
Actual UI
Behavior
User Action"domainComputation"
annotation
Applicable to
value (the
configuration cannot
be saved with the
"255/440" voltage due
to reverting)
type
GeneratorSet
Same as not
specified
Same as not
specified
Case 1: Duty Rating =
any except specified
in constraints (e.g.
FALSEstring voltage
{Remain the full
voltage domain.
Always show the full
voltage domain"Prime Power (PRP)",
"Emergency Standby
Power (ESP)"):
@(defaultValue
=
"Emergency
Case 1: Duty Rating
= any except
regardless of the
Duty Rating
selection.• Initial value for the
voltage = the value
Standby
Power
specified in
constraints (e.g.
specified in the (ESP)")
string"Prime Power (PRP)",
"Emergency@defaultValue
annotation
("220/380")
dutyRating =
["Emergency
Standby
Standby Power
(ESP)"):
• The user can select a
different voltage value
Power
(ESP)",
"Prime Power
• If the configuration
is saved with initial
(default) voltage(e.g. "240/416",
"255/440" etc.). The (PRP)",
"Continuousvalue ("220/380"):
attributeName":"voltage","cfgStatus":"Default"system remains User
selected voltage Power
(COP)",• If the configuration
is saved with User• The user can save
the configuration with
"Data Center
Continuous
(DCC)"];selected voltage
value (e.g.both values: initial
voltage or User
selected voltage @(defaultValue
"255/440"):
attributeName":"voltage","cfgStatus":"Default"
Case 2: Duty Rating =
"Continuous Power
(COP)"
=
"220/380",
domainComputation
= false)
Case 2: Duty Rating
= "Continuous
Power (COP)"
• If the configuration
is saved with
• Initial value for the
voltage = next
possible value from
string
voltage =
["220/380",initial/reverted to
the domain to satisfy "240/416",initial voltage value
the constraint
("240/416")
"347/600",
"255/440",
"277/480",
("240/416"):
"attributeName":"voltage","cfgStatus":"Engine"
Case 3: Duty Rating
= "Data Center
Continuous (DCC)"
• Warning: If the user
selects a different
voltage (e.g.
"220/380", "255/440",
"2400/4160",
"7200/12470",
"7621/13200",• If the configuration
is saved with initial
"2400/4160" etc.), the
system reverts it to
1066
Annotation ExamplesProduct Configurator

===== PAGE 1081 =====

Constraint ModelActual Engine
Behavior
Actual UI
Behavior
User Action"domainComputation"
annotation
Applicable to
"7976/13800"];("220/380")/other
constraint
specified("255/440")/reverted
the initial value
("240/416")
• The user can save
the configuration with constraint(dutyRating
to constraint
specified voltagethe initial voltage ==values ("220/380",value (the "Continuous"255/440"):
"attributeName":"voltage","cfgStatus":"Default"
configuration cannot
be saved with other
voltage due to
reverting)
Power (COP)"
-> voltage
!=
"220/380");
Case 3: Duty Rating =
"Data Center
Continuous (DCC)"
constraint(dutyRating
== "Data
Center• Initialvalue for the
voltage = specified Continuous
(DCC)" ->
value in constraint voltage ==
that comes first in the
domain ("220/380")
"255/440" ||
voltage ==
"220/380");
}
• The user can select a
different voltage
specified in constraint
("255/440"). The
system remains User
selected voltage
• If the user selects a
voltage that not
specified in the
constraint (e.g.
"240/416",
"2400/4160" etc.), the
system will revert it to
one of the values
defined in constraint
("220/380" or
"255/440")
• The user can save
the configuration with
the specified in
constraint voltage
value (the
configuration cannot
be saved with other
voltage due to
reverting)
1067
Annotation ExamplesProduct Configurator

===== PAGE 1082 =====

peelable Annotation
The peelable  annotation is used to create soft selection values and allow the engine to modify these selections to satisfy a constraint.
peelableAnnotation
VariableApplicable to
true, falseValue Type/Values
Indicates whether the constraint engine can override the variable's
value (whether set by default or user selection) to resolve a conflict.
Description
• If peelable  annotation is set to true, the engine treats
the value as a "soft selection." When a configuration conflict
occurs, the engine attempts to "peel" (unbind) this variable
and retry the solution. If a valid configuration is found, the
engine automatically changes the value to satisfy constraints
rather than displaying an error message.
• If peelable  annotation is set to false, the engine treats
the value as a "hard selection." If the value causes a conflict
with a constraint, the engine will not attempt to change it
automatically. Instead, it will stop and display a conflict error
message to the user, requiring manual intervention to resolve
the issue.
Example 1: peelable = true (Soft Selection)
In this scenario, the ServiceLevel  defaults to "Standard". Because it is marked peelable = true, the Constraint Engine
treats this value as a "soft pick." It is authorized to override this value automatically if a conflict arises with another selection.
type CloudSubscription {
// User adds 5TB of storage
int storageTB = [1..3];
/*
* peelable=true: The engine acts as a "negotiator."
* If a constraint needs to change this value, the engine is allowed
* to "peel" (remove) the user's selection and apply the required value.
*/
@(defaultValue = "Standard", peelable = true)
string ServiceLevel = ["Standard", "Premium"];
// Constraint: 5TB or more requires Premium Service
constraint(storageTB >= 5 -> ServiceLevel == "Premium", "High storage requires Premium
service");
}
1068
Annotation ExamplesProduct Configurator

===== PAGE 1083 =====

Example 2: peelable = false (Hard Selection)
In this scenario, peelable  is omitted (defaulting to false) or explicitly set to false. The engine treats the value "Standard"
as a "hard constraint" or a firm user commitment. It is not authorized to change it automatically.
type CloudSubscription {
// User adds 5TB of storage
int storageTB = [1..3];
/*
* peelable=false (Default): The engine acts as a "validator."
* It respects the current value as a hard fact.
* It cannot change "Standard" to "Premium" on its own.
*/
@(defaultValue = "Standard", peelable = false)
string ServiceLevel = ["Standard", "Premium"];
// Constraint: 5TB or more requires Premium Service
constraint(storageTB >= 5 -> ServiceLevel == "Premium", "High storage requires Premium
service");
}
Example Description and Configurator Result
In example 1, the ServiceLevel  attribute is specified with the peelable  annotation set to true. In example 2, the annotation
is not specified, so the system considers it as false by default. As a result, if the user updates the storageTB  variable to 5, the system
automatically changes the ServiceLevel  to "Premium"  in example 1 according to constraint logic, effectively "peeling" the
default "Standard" value to resolve the conflict. The system allows this override without displaying an error message to the user.
In example 2, the system does not allow the engine to override the default "Standard"  value automatically. Consequently, the
system displays a conflict error message, and the user must manually update the ServiceLevel  to "Premium"  to satisfy the
constraint.
Example 3: System-Driven Soft Selection (configurable = false, peelable = true)
In this example, the Voltage  is set to a high voltage (" 2400/4160") by default. The annotation configurable = false
prevents the user from manually changing this value in the UI. However, peelable = true is added to allow the constraint engine
to override this default if a specific compliance standard is selected.
type GeneratorSet {
string standardsAndCompliance = ["None", "Listing-UL 2200"];
/*
* configurable=false: The user cannot change this directly.
* peelable=true: The engine is authorized to change the default
* to resolve conflicts with the standardsAndCompliance selection.
*/
@(defaultValue = "2400/4160", configurable = false, peelable = true)
string Voltage = ["220/380", "277/480", "2400/4160"];
// Constraint: UL 2200 listing requires a specific low voltage (277/480)
1069
Annotation ExamplesProduct Configurator

===== PAGE 1084 =====

constraint(standardsAndCompliance == "Listing-UL 2200" -> Voltage == "277/480");
}
Example Description and Configurator Result
In example 3, the Voltage  is specified with configurable set to false, preventing user interaction, but peelable is set to true.
Initially, the system sets the voltage to "2400/4160". If the user updates the standardsAndCompliance  variable to
"Listing-UL 2200", the system detects a conflict with the default voltage. Because the variable is peelable, the system automatically
"peels" the default "2400/4160" value and changes it to "277/480" to satisfy the constraint. The transition happens silently without
a conflict error, even though the user cannot manually edit the field.
Example 4: System-Driven Hard Constraint (configurable = false, peelable = false)
In this example, the EmissionsTier  is set to "Tier 3" by default. It is marked configurable = false  (system-controlled)
and peelable  is omitted (defaults to false), treating the default value as a hard constraint.
type GeneratorSet {
string Location = ["US", "International"];
/*
* configurable=false: The user cannot change this.
* peelable=false (Default): The engine treats "Tier 3" as a hard fact.
*/
@(defaultValue = "Tier 3", configurable = false)
string EmissionsTier = ["Tier 3", "Tier 4 Final"];
// Constraint: US Location requires Tier 4 Final
constraint(Location == "US" -> EmissionsTier == "Tier 4 Final", "US requires Tier 4
Final emissions");
}
Example Description and Configurator Result
In example 4, the EmissionsTier  is specified with configurable set to false, and peelable  is not specified (defaulting to
false). As a result, the system considers the default value "Tier 3" as a hard constraint that cannot be overridden. If the user updates
the Location variable to "US", the constraint engine attempts to enforce "Tier 4 Final" but finds it cannot overwrite the fixed
"Tier 3" value. Consequently, the system displays a conflict error message stating "US requires Tier 4 Final emissions,"
and the configuration enters an invalid state because the user cannot manually change the EmissionsTier to resolve it.
Example 5: Auto-Correcting User Input (`configurable = true`, `peelable = true`)
In this example, the `EnclosureType` is user-selectable (`configurable = true`) and defaults to "Standard". It is marked
with `peelable = true`. This allows the engine to override even an explicit user selection if a subsequent choice makes the enclosure
invalid.
type GeneratorAccessories {
/*
* configurable=true: User explicitly selects 'Standard'.
* peelable=true: Grants permission to override the User's selection
* to resolve conflicts with the Environment.
*/
1070
Annotation ExamplesProduct Configurator

===== PAGE 1085 =====

@(defaultValue = "Standard", configurable = true, peelable = true)
string EnclosureType = ["Standard", "Heated", "Reinforced"];
string Environment = ["Indoor", "Arctic"];
// Constraint: Arctic requires Heated Enclosure
constraint(Environment == "Arctic" -> EnclosureType == "Heated");
}
Example Description and Configurator Result
In example 5, the `EnclosureType` is specified with `configurable` set to `true` and `peelable` set to `true`. Initially,
the system allows the user to confirm the selection of "Standard". If the user subsequently updates the `Environment` variable
to "Arctic", the system detects that "Standard" is invalid. Typically, the engine protects user selections and would throw an error.
However, because `EnclosureType` is peelable, the system treats the user's choice as a "soft pick." It automatically "peels" the
"Standard" selection and changes it to "Heated" to satisfy the logic. The user sees their previous selection update automatically to
match the new environment requirement, preventing a "dead end" configuration state.
Example 6: Upstream Correction (`sequence`, `peelable = true`)
In this example, the `Voltage` is configured early in the process (Sequence 1) with a default value of "Low". It is marked with
`peelable = true` to allow downstream selections to override this initial setting.
type GeneratorSet {
/*
* sequence=1: Evaluated first. Defaults to 'Low'.
* peelable=true: Allows 'Application' (seq=2) to force a change to this value.
*/
@(defaultValue = "Low", sequence = 1, peelable = true)
string Voltage = ["Low", "Medium", "High"];
/*
* sequence=2: Evaluated after Voltage is set.
* The user picks 'DataCenter', which requires High Voltage.
*/
@(sequence = 2)
string Application = ["Residential", "DataCenter"];
// Constraint: DataCenter application forces High Voltage
constraint(Application == "DataCenter" -> Voltage == "High");
}
Example Description and Configurator Result
In example 6, the `Voltage` attribute is specified with `sequence` set to 1  and `peelable` set to `true`. As a result, the system
initially sets the value to "Low" before evaluating the `Application` attribute. If the user updates the `Application` variable
to "DataCenter" (which runs at sequence 2), the system detects a conflict between the established "Low" voltage and the constraint
requirement for "High" voltage. Because `Voltage` is peelable, the system automatically "peels" the default "Low" value and changes
it to "High" to satisfy the constraint. The transition happens silently without a conflict error, effectively allowing a later user choice to
correct an earlier default assumption.
1071
Annotation ExamplesProduct Configurator

===== PAGE 1086 =====

Example 7: Guided Fallback (‘strategy`, `peelable = true`)
In this example, the `ServiceTier` defaults to "Bronze" (the lowest value). It is marked with `peelable = true` and
`strategy = "descending"`. If a constraint forces a change from the default, the strategy directs the engine to try the highest
possible valid values first.
type ServicePlan {
/*
* defaultValue="Bronze": Start cheap.
* peelable=true: Allow upgrade if needed.
* strategy="descending": If peeled, try 'Platinum' next (Max value),
* instead of creeping up to 'Silver'.
*/
@(defaultValue = "Bronze", strategy = "descending", peelable = true)
string ServiceTier = ["Bronze", "Silver", "Gold", "Platinum"];
int UserCount = [1..1000];
// Constraint: > 100 users requires Premium tiers (Gold or Platinum)
constraint(UserCount > 100 -> ServiceTier in ["Gold", "Platinum"]);
}
Example Description and Configurator Result
In example 7, the `ServiceTier` is specified with `strategy` set to "descending" and `peelable` set to `true`. Initially,
the system sets the value to "Bronze". If the user updates the `UserCount` variable to 150, the constraint requires `ServiceTier`
to be either "Gold" or "Platinum". Because the variable is peelable, the system removes the "Bronze" selection. Instead of testing
the next closest value ("Silver"), the "descending" strategy instructs the engine to attempt resolution starting from the top of
the domain. Consequently, the system automatically selects "Platinum" (the highest valid option) rather than "Gold". The user sees
the plan upgrade immediately to the highest tier without an error message.
propagateUp Annotation
propagateUp  is a Constraint Modeling Language (CML) annotation that controls aggregation propagation between children and
parent elements.
propagateUpAnnotation
RelationshipApplicable to
true, falseValue Type/Values
If propagateUp is not specified, the engine sets it implicitly as false
for the relationship.
Description
• If the propagateUp annotation is specified as true, the engine
aggregates values from children to parent elements (upward
propagation). The engine cannot modify this value from the
parent level (e.g. via constraint), so the children relation domain
will not be affected.
• If the propagateUp is specified as false, both upward and
downward propagations are applicable. The engine aggregates
1072
Annotation ExamplesProduct Configurator

===== PAGE 1087 =====

propagateUpAnnotation
values from children to parent elements (upward propagation).
Meanwhile the engine can modify this value (e.g. via constraint)
from the parent level. The value is propagated downward and
might affect the relation domain (downward propagation).
Example 1
In this example, the propagateUp  annotation is not specified for the relationship (warranties). The model contains technical
variable (coverageDays) and constraint.
type GeneratorSet {
relation warranties : Warranty {
totalDays = sum(coverageDays);
}
constraint(warranties.totalDays <= 299);
}
type Warranty {
int coverageDays = 100;
}
type Warranty_PRP : Warranty;
type Warranty_DCC : Warranty;
type Warranty_ESP : Warranty;
Example 2
In this example, the propagateUp  annotation is defined as false for the relationship (warranties). The model contains
technical variable (coverageDays) and constraint.
type GeneratorSet {
@(propagateUp = false)
relation warranties : Warranty {
totalDays = sum(coverageDays);
}
constraint(warranties.totalDays <= 299);
}
type Warranty {
int coverageDays = 100;
}
type Warranty_PRP : Warranty;
type Warranty_DCC : Warranty;
1073
Annotation ExamplesProduct Configurator

===== PAGE 1088 =====

type Warranty_ESP : Warranty;
Example Description and Configurator Result
In example 1, the warranties  relation is not specified with the propagateUp annotation, and the system considers it as false
by default. In example 2, the relation is explicitly defined with a false  annotation value. Each product of the warranties  relation
is assigned with the technical coverageDays  variable equalled to 100. The totalDays  calculates the coverageDays  sum
of selected warranties products. As a result, the system validates the constraint and relation domain in the following way:
• The user selects one warranties  product (e.g. Warranty_PRP). The system calculates the totalDays  aggregated value
for the relation (equal to 100). The system validates the constraint on the parent based on the calculated aggregation variable. The
constraint is satisfied (100<= 299). The system also verifies the possibility to add extra products to the relation. The capacity of the
constraint allows to add one more product to the relation, so the system will not reduce the relation domain.
• The user selects the second warranties  product (e.g. Warranty_DCC). The system calculates the totalDays  aggregated
value for the relation (equal to 200). The system validates the constraint on the parent based on the calculated aggregation variable.
The constraint is satisfied (200<= 299). The system verifies the possibility to add extra products to the relation. The capacity of the
constraint (300<= 299) does not allow to add one more product to the relation, so the system will reduce the relation domain.
• The user unselects one of the selected warranties  products (e.g. Warranty_PRP). The system calculates the totalDays
aggregated value for the relation (equal to 100). The system validates the constraint on the parent based on the calculated aggregation
variable. The constraint is satisfied (100<= 299). The system verifies the possibility to add extra products to the relation. The capacity
of the constraint allows to add one more product to the relation, so the system will not reduce the relation domain (both
Warranty_DCC  and Warranty_ESP  products are available for selection).
Example 3
In this example, the propagateUp  annotation is specified for the relationship (warranties) as true. The model contains
technical variable (coverageDays) and constraint.
type GeneratorSet {
@(propagateUp = true)
relation warranties : Warranty {
totalDays = sum(coverageDays);
}
constraint(warranties.totalDays <= 299);
}
type Warranty {
int coverageDays = 100;
}
type Warranty_PRP : Warranty;
type Warranty_DCC : Warranty;
type Warranty_ESP : Warranty;
1074
Annotation ExamplesProduct Configurator

===== PAGE 1089 =====

Example Description and Configurator Result
In example 3, the relation is specified with propagateUp  annotation as true  value. Each product of the warranties  relation
is assigned with the technical coverageDays  variable equalled to 100. The totalDays  calculates the coverageDays  sum
of selected warranties products. As a result, the system validates the constraint and relation domain in the following way:
The user selects one warranties  product (e.g. Warranty_PRP). The system calculates the totalDays  aggregated value for
the relation (equal to 100). The system validates the constraint on the parent based on the calculated aggregation variable. The constraint
is satisfied (100<=299);
The user selects the second warranties  product (e.g. Warranty_DCC). The system calculates the totalDays  aggregated
value for the relation (equal to 200). The system validates the constraint on the parent based on the calculated aggregation variable.
The constraint is satisfied (200<=299);
The user selects the third warranties  product (e.g. Warranty_ESP). The system calculates the totalDays  aggregated value
for the relation (equal to 300). The system validates the constraint on the parent based on the calculated aggregation variable. The
constraint is not satisfied (300<=299). The system rejects the selection of one of the warranties products to satisfy the constraint.
As a best practice, use the propagateUp = true  for models with few relationships and rare constraint violations, since it minimizes
propagation work and avoids extra domain updates. Meanwhile, set the propagateUp = false  for large product structures or
frequent violations, since bidirectional propagation prevents invalid states early and reduces expensive backtracking.
propagateUp Configuration Settings
Table 12: propagateUp Configuration Settings
UI BehaviorEngine ActionUser Action"propagateUp"
annotation
Applicable toProduct Group
Structure
Associated
Example
Displays the
selected
Calculates the
aggregation
Selects or
deselects the
products
not specifiedRelationshipIndividual
product
Example 1
products. When
constraint
variable value on
the relation,
capacity is usedvalidation of the
up, in addition toconstraint,
the selectedlimitation of the
products therelation domain
limited list of thewhen the
available to beconstraint
added productscapacity is used
up will be
displayed(if any)
Displays the
selected
Calculates the
aggregation
Selects or
deselects the
products
FALSERelationshipIndividual
product
Example 2
products. When
constraint
variable value on
the relation,
capacity is usedvalidation of the
up, in addition toconstraint,
the selectedlimitation of the
products therelation domain
limited list of thewhen the
available to beconstraint
1075
Annotation ExamplesProduct Configurator

===== PAGE 1090 =====

UI BehaviorEngine ActionUser Action"propagateUp"
annotation
Applicable toProduct Group
Structure
Associated
Example
capacity is used
up
added products
will be
displayed(if any)
Displays the
selected
Calculates the
aggregation
Selects or
deselects the
products
TRUERelationshipIndividual
product
Example 3
products. No
limitations for the
variable value on
the relation,
list of available
products
validation of the
constraint,
rejection of the
user selection
when the
constraint
validation is failed
Displays the
selected
Calculates the
aggregation
Selects or
deselects the
products
not specifiedRelationshipProduct
Classification
N/A
products. No
limitations for the
variable value on
the relation,
list of availablevalidation of the
products in theconstraint. The
browse popup for
the classification
engine might
replace one of
the previously
selected products
with a newly
selected
Displays the
selected
Calculates the
aggregation
Selects or
deselects the
products
FALSERelationshipProduct
Classification
N/A
products. No
limitations for the
variable value on
the relation,
list of availablevalidation of the
products in theconstraint. The
browse popup for
the classification
engine might
replace one of
the previously
selected products
with a newly
selected
Displays the
selected
Calculates the
aggregation
Selects or
deselects the
products
TRUERelationshipProduct
Classification
N/A
products. No
limitations for the
variable value on
the relation,
list of availablevalidation of the
products in theconstraint,
1076
Annotation ExamplesProduct Configurator

===== PAGE 1091 =====

UI BehaviorEngine ActionUser Action"propagateUp"
annotation
Applicable toProduct Group
Structure
Associated
Example
rejection of the
user selection
browse popup for
the classification
when the
constraint
validation is failed
relatedAttributes Annotation
relatedAttributes  is a Constraint Modeling Language (CML) annotation that resets the domain to the original one for
domainComputation.
relatedAttributes  annotation specification: Variable
relatedAttributesAnnotation
Variable and RelationshipApplicable to
StringValue Type/Values
For VariablesDescription
If relatedAttributes annotation is not specified, the engine
updates the variable domain according to domainComputation
and constraint logic.
If the relatedAttributes  annotation is specified with one
or multiple values (separated by comma), the variable domain is
reset to the original domain.
For relationships
If domainComputation  is not explicitly specified, the engine
sets it implicitly as true for the relationship.
If the domainComputation  is specified as true, the
relationship domain is dynamically determined based on the
configuration and constraint logic.
If the domainComputation  is specified as false, the
relationship domain is fixed.
Example 1
In this example, the relatedAttributes  annotation is not specified for the variables (controlLanguage,
controlPlacement, commissioningScope) of the Control  type. The domainComputation  annotation is defined
for the variables. The model contains the constraints.
type GeneratorSet {
relation controls : Control;
}
1077
Annotation ExamplesProduct Configurator

===== PAGE 1092 =====

type Control {
@(domainComputation = true, defaultValue = "English")
string controlLanguage = ["English", "Danish", "French"];
@(domainComputation = true, defaultValue = "Left")
string controlPlacement = ["Left", "Right", "Top"];
@(domainComputation = true, defaultValue = "None")
string commissioningScope = ["None", "Remote Support", "On-site Commissioning"];
constraint(controlPlacement == "Right" -> commissioningScope != "Remote Support");
constraint(controlLanguage== "Danish" -> commissioningScope != "On-site Commissioning");
Example Description and Configurator Result
In example 1, the variables of the Control  type are not specified with the relatedAttributes  annotation, but defined with
the domainComputation  annotation. As a result, the system updates the variable domain based on the constraint logic.
If the controlPlacement  is selected with the "Right" value, the commissioningScope  variable domain is updated to
exclude the "Remote Support" value;
If the controlLanguage  is selected with the “Danish" value, the commissioningScope  variable domain is updated to
exclude the "On-site Commissioning" value.
Example 2
In this example, the relatedAttributes  annotation is specified for the variable with one value. The domainComputation
annotation is defined for the variables. The model contains the constraints.
type GeneratorSet {
relation controls : Control;
}
type Control {
@(domainComputation = true, defaultValue = "English")
string controlLanguage = ["English", "Danish", "French"];
@(domainComputation = true, defaultValue = "Left")
string controlPlacement = ["Left", "Right", "Top"];
@(domainComputation = true, defaultValue = "None", relatedAttributes =
"controlPlacement")
string commissioningScope = ["None", "Remote Support", "On-site Commissioning"];
constraint(controlPlacement == "Right" -> commissioningScope != "Remote Support");
constraint(controlLanguage== "Danish" -> commissioningScope != "On-site Commissioning");
}
1078
Annotation ExamplesProduct Configurator

===== PAGE 1093 =====

Example 3
In this example, the relatedAttributes  annotation is specified for the variable with one value. The domainComputation
annotation is defined for the variables. The model contains the constraints.
type GeneratorSet {
relation controls : Control;
}
type Control {
@(domainComputation = true, defaultValue = "English")
string controlLanguage = ["English", "Danish", "French"];
@(domainComputation = true, defaultValue = "Left")
string controlPlacement = ["Left", "Right", "Top"];
@(domainComputation = true, defaultValue = "None", relatedAttributes = "controlLanguage")
string commissioningScope = ["None", "Remote Support", "On-site Commissioning"];
constraint(controlPlacement == "Right" -> commissioningScope != "Remote Support");
constraint(controlLanguage== "Danish" -> commissioningScope != "On-site Commissioning");
}
Example Description and Configurator Result
In Example 2, the relatedAttributes  annotation is defined with the "controlPlacement" value for the
commissioningScope  variable. As a result, the system controls the domain for the commissioningScope differently
depending on controlPlacement  or controlLanguage  variable selection.
If the controlPlacement is selected with the "Right" value, the commissioningScope variable domain remains unchanged,
because the controlPlacement  is listed in the relatedAttributes  annotation.
If the controlLanguage is selected with the “Danish" value, the commissioningScope variable domain is updated to exclude
the "On-site Commissioning" value according to the constraint, because the controlLanguage  is not listed in the
relatedAttributes  annotation.
In example 3, the relatedAttributes  annotation is defined with the "controlLanguage" value for the
commissioningScope  variable. As a result, the system controls the domain for the commissioningScope differently
depending on controlPlacement  or controlLanguage  variable selection.
If the controlPlacement  is selected with the "Right" value, the commissioningScope  variable domain is updated to
exclude the "Remote  Support" value according to the constraint, because the controlPlacement  is not listed in the
relatedAttributes  annotation.
If the controlLanguage is selected with the "Danish" value, the commissioningScope variable domain remains unchanged,
because the controlLanguage  is listed in the relatedAttributes  annotation.
1079
Annotation ExamplesProduct Configurator

===== PAGE 1094 =====

Example 4
In this example, the relatedAttributes  annotation is specified for the variable with several values (separated by comma). The
domainComputation annotation is defined for the variables. The model contains the constraints.
type GeneratorSet {
relation controls : Control;
}
type Control {
@(domainComputation = true, defaultValue = "English")
string controlLanguage = ["English", "Danish", "French"];
@(domainComputation = true, defaultValue = "Left")
string controlPlacement = ["Left", "Right", "Top"];
@(domainComputation = true, defaultValue = "None", relatedAttributes = "controlPlacement,
controlLanguage")
string commissioningScope = ["None", "Remote Support", "On-site Commissioning"];
constraint(controlPlacement == "Right" -> commissioningScope != "Remote Support");
constraint(controlLanguage== "Danish" -> commissioningScope != "On-site Commissioning");
}
Example Description and Configurator Result
In example 4, the relatedAttributes  annotation is defined with the "controlPlacement" and "controlLanguage"
values for the commissioningScope variable. As a result, the system remains the commissioningScope variable domain unchanged.
If the controlPlacement is selected with the "Right" value, the commissioningScope variable domain remains unchanged,
because the controlPlacement  is listed in the relatedAttributes  annotation.
If the controlLanguage is selected with the "Danish" value, the commissioningScope variable domain remains unchanged,
because the controlLanguage  is listed in the relatedAttributes  annotation.
Example 5
In this example, the relatedAttributes  annotation is not specified for the relationship (temperatureSensors). The
domainComputation  annotation is defined for the relationship. The model contains the constraints.
type GeneratorSet {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
@(domainComputation = true)
relation temperatureSensors : TemperatureSensor[0..1];
constraint(dutyRating == "Continuous Power (COP)" ->
temperatureSensors[BearingTemperatureSensor] == 0);
constraint(dutyRating == "Data Center Continuous (DCC)" ->
temperatureSensors[StatorTemperatureSensor] == 0);
}
1080
Annotation ExamplesProduct Configurator

===== PAGE 1095 =====

type TemperatureSensor;
type BearingTemperatureSensor : TemperatureSensor;
type StatorTemperatureSensor : TemperatureSensor;
Example Description and Configurator Result
In example 5, the temperatureSensors  relation is not specified with the relatedAttributes  annotation, but defined
with the domainComputation  as true. As a result, the system updates the relationship domain based on the constraint logic.
If the dutyRating  is selected with the "Continuous Power (COP)" value, the system re-computes the relationship domain
and excludes the BearingTemperatureSensor  product to satisfy the constraint. The StatorTemperatureSensor
product remains and can be selected in scope of the GeneratorSet  bundle product.
If the dutyRating  is selected with the "Data Center Continuous (DCC)" value, the system re-computes the relationship
domain and excludes the StatorTemperatureSensor product to satisfy the constraint. The BearingTemperatureSensor
product remains and can be selected in scope of the GeneratorSet  bundle product.
Example 6
In this example, the relatedAttributes  annotation is specified for the relationship (temperatureSensors). The
domainComputation  annotation is defined for the relationship. The model contains the constraints.
type GeneratorSet {
@(defaultValue = "Emergency Standby Power (ESP)")
string dutyRating = ["Emergency Standby Power (ESP)", "Prime Power (PRP)", "Continuous
Power (COP)", "Data Center Continuous (DCC)"];
@(domainComputation = true, relatedAttributes = 'dutyRating')
relation temperatureSensors : TemperatureSensor[0..1];
constraint(dutyRating == "Continuous Power (COP)" ->
temperatureSensors[BearingTemperatureSensor] == 0);
constraint(dutyRating == "Data Center Continuous (DCC)" ->
temperatureSensors[StatorTemperatureSensor] == 0);
}
type TemperatureSensor;
type BearingTemperatureSensor : TemperatureSensor;
type StatorTemperatureSensor : TemperatureSensor;
Example Description and Configurator Result
In example 6, the temperatureSensors  relation is specified with the relatedAttributes  annotation containing the
dutyRating  value, the domainComputation  annotation is defined as true. As a result, the system remains the relationship
domain unchanged and executes the constraints.
1081
Annotation ExamplesProduct Configurator

===== PAGE 1096 =====

If the dutyRating  is selected with the "Continuous Power (COP)" value, the system displays both
BearingTemperatureSensor  and StatorTemperatureSensor  products in scope of the GeneratorSet  bundle
product. The BearingTemperatureSensor  product cannot be selected based on the constraint.
If the dutyRating  is selected with the “Data Center Continuous (DCC)" value, the system displays both
BearingTemperatureSensor  and StatorTemperatureSensor  products in scope of the GeneratorSet  bundle
product. The StatorTemperatureSensor  product cannot be selected based on the constraint.
relatedAttributes Configuration Settings
Table 13: relatedAttributes Configuration Settings
UI BehaviorEngine
Action
User Action"domainComputation"
annotation
"relatedAttributes"
annotation
Applicable
to
Product
Group
Structure
Associated
Example
Display
updated
Update the
variable
Change
variable value
TRUEnot specifiedVariableIndividual
product
Example 1
variable
domain
(specified with
domainComputation)
domain based
specified in
constraint
condition
on
domainComputation
and constraint
logic
Display original
variable
domain
Reset variable
(specified in
relatedAttributes)
domain to the
Change
variable value
specified in
constraint
TRUEspecified (with
one variable)
VariableIndividual
product
Example 2
Example 3
original
domain
condition and
relatedAttributes
Display original
variable
domain
Reset variable
(specified in
relatedAttributes)
domain to the
Change
variable values
specified in
constraint
TRUEspecified (with
several
variables)
VariableIndividual
product
Example 4
original
domain
conditions and
relatedAttributes
Display
updated
Update the
relationship
Change
variable value
TRUEnot specifiedRelationshipIndividual
product
Example 5
relationship
domain
(specified with
domainComputation)
domain based
specified in
constraint
condition
on
domainComputation
and constraint
logic
1082
Annotation ExamplesProduct Configurator

===== PAGE 1097 =====

UI BehaviorEngine
Action
User Action"domainComputation"
annotation
"relatedAttributes"
annotation
Applicable
to
Product
Group
Structure
Associated
Example
Display original
relationship
Reset
relationship
domain to the
Change
variable value
specified in
TRUEspecifiedRelationshipIndividual
product
Example 6
domain
(products).original
domain
constraint
condition and
relatedAttributes If the product
is allowed
according to
constraint: the
product can be
selected
If the product
is not allowed
according to
constraint:
selected
product
returns back to
unselected
state
Display
updated
Update the
relationship
• Change
variable value
TRUEnot specifiedRelationshipProduct
Classification
N/A
relationship(specified withspecified in
domain. If thedomainComputation)constraint
variable isdomain basedcondition >
changed againonAdd products
by the User,domainComputationon browse
the value isand constraint
logic
popup from
product
classification
reverted to the
initial value
• Add products
on browse
popup from
product
classification >
Change
variable value
specified in
constraint
condition
• If the variable
of constraint
• If the variable
of constraint
• Change
variable value
TRUEspecifiedRelationshipProduct
Classification
N/A
condition iscondition isspecified in
1083
Annotation ExamplesProduct Configurator

===== PAGE 1098 =====

UI BehaviorEngine
Action
User Action"domainComputation"
annotation
"relatedAttributes"
annotation
Applicable
to
Product
Group
Structure
Associated
Example
constraint
condition >
changed first:
display
changed first:
update the
Add products updatedrelationship
on browse relationship(specified with
popup from domain. If thedomainComputation)
product
classification
variable is
changed again
domain based
on constraint
logic•Add products
on browse
by the user, the
value is
reverted to the
initial value
• if products
are added first
from browse
popup from
product
popup: remainclassification > • if products
are added firsttheChange
from browserelationshipvariable value
popup: displaydomain
unchanged
specified in
constraint
condition
added
products as
selected. If
constraint
variable is
changed again
by the user, the
value is
reverted to the
initial value
sequence Annotation
The sequence  annotation defines the execution and configuration order of elements in a Constraint Modeling Language (CML)
model.
sequence  annotation specification: Variable and Relationship
sequenceAnnotation
Variable and RelationshipApplicable to
integer Example: 1, 2, 10Value Type/Values
If a sequence value is not explicitly defined, the configurator
implicitly determines the order based on the variable or relationship
Description
declaration order in the CML model. If a sequence value is explicitly
defined, the configurator uses the sequence number to control
the order in which variables or relationships are configured.
Variables or Relationships with lower sequence values are assigned
first.
1084
Annotation ExamplesProduct Configurator

===== PAGE 1099 =====

Example 1
In this example, the sequence  annotation is not explicitly specified. The defaultValue  is defined for 3 variables
(controlPlacement, commissioningScope, and controlLanguage) of the Control  products. The model contains
a constraint.
type GeneratorSet {
relation controls : Control[1..999999];
}
type Control {
@(defaultValue = "Left")
string controlPlacement = ["Left", "Right", "Top"];
@(defaultValue = "None")
string commissioningScope = ["None", "Remote Support", "On-site Commissioning"];
@(defaultValue = "English")
string controlLanguage = ["English", "Danish", "French"];
constraint(controlPlacement == "Left" && controlLanguage == "English" -> commissioningScope
== "Remote Support");
}
Example Description and Configurator Result
The model defines 3 variables with defaultValue annotation.
controlPlacement = "Left"
commissioningScope = "None"
controlLanguage = "English"
Even when sequence is not explicitly specified for the variables, the engine assigns it implicitly based on the variable declaration order
in the CML type. For this example, the sequence for the variables is:
controlPlacement: sequence = 1 (highest priority)
commissioningScope: sequence = 2
controlLanguage: sequence = 3 (lowest priority)
The constraint specifies that a type with controlPlacement == "Left"  and controlLanguage == "English"  will
have a commissioningScope == "Remote Support":.
constraint(controlPlacement == "Left" && controlLanguage == "English" -> commissioningScope
== "Remote Support");
For any constraint, the engine enforces logical equivalence between the left-hand side (before ->) and the right-hand side (after ->): if
the left side evaluates to true, the right side must also be true (and vice versa).
In this example, the engine resolves the true -> false constraint (to be false -> false): it modifies the controlLanguage with the highest
sequence.
As a result, the Product Configurator will have next values for the variables:
controlPlacement = "Left"
commissioningScope = "None"
controlLanguage = "Danish"
1085
Annotation ExamplesProduct Configurator

===== PAGE 1100 =====

Example 2
In this example, the sequence annotation is explicitly specified and the defaultValue is defined for 3 variables (controlPlacement,
controlLanguage, commissioningScope) of the Control products. The model contains a constraint.
type GeneratorSet {
relation controls : Control[1..999999];
}
type Control{
@(defaultValue = "Left", sequence = 1)
string controlPlacement = ["Left", "Right", "Top"];
@(defaultValue = "English", sequence = 3)
string controlLanguage = ["English", "Danish", "French"];
@(defaultValue = "None", sequence = 2)
string commissioningScope = ["None", "Remote Support", "On-site Commissioning"];
constraint(controlPlacement == "Left" && controlLanguage == "English" -> commissioningScope
== "Remote Support");
}
Example Description and Configurator Result
This example is similar to Example 1, but the sequence annotation is specified explicitly for the variables to control solver priority:
controlPlacement: sequence = 1 (highest priority)
controlLanguage: sequence = 3 (lowest priority)
commissioningScope: sequence = 2
The constraint specifies that a type with controlPlacement == "Left"  and controlLanguage == "English"  will
have a commissioningScope == "Remote Support":.
constraint(controlPlacement == "Left" && controlLanguage == "English" -> commissioningScope
== "Remote Support");
• Following the same logical equivalence for constraints described in Example 1 and considering the default values specified in the
Example 2, the left side of the constraint is true (controlPlacement = "Left" and controlLanguage = "English"),
while the right side is false (commissioningScope = "None").
• Because the commissioningScope  has higher priority than the controlLanguage, the engine avoids changing the
commissioningScope  and instead resolves the constraint by making the left side false.
• The controlPlacement  has the highest priority sequence than the controlLanguage, so the engine modifies the
controlLanguage as the most efficient way to satisfy the constraint.
Available values for the controlLanguage: ["English", "Danish", "French"]. To make the left side of the constraint
false, the engine selects the first non-matching value (specified in CML domain): "Danish".
As a result, the Product Configurator will have next values for the variables.
controlPlacement = "Left"
controlLanguage = "Danish"
commissioningScope = "None"
1086
Annotation ExamplesProduct Configurator

===== PAGE 1101 =====

Example 3
In this example, the sequence annotation is explicitly specified and the defaultValue is defined for 3 variables (controlPlacement,
controlLanguage, and commissioningScope) of the Control products. The model contains a constraint.
type GeneratorSet {
relation controls : Control[1..999999];
}
type Control{
@(defaultValue = "Left", sequence = 1)
string controlPlacement = ["Left", "Right", "Top"];
@(defaultValue = "English", sequence = 2)
string controlLanguage = ["English", "Danish", "French"];
@(defaultValue = "None", sequence = 3)
string commissioningScope = ["None", "Remote Support", "On-site Commissioning"];
constraint(controlPlacement == "Left" && controlLanguage == "English" -> commissioningScope
== "Remote Support");
}
Example Description and Configurator Result
This example is similar to Example 2, but the lowest priority sequence is specified for the commissioningScope. This is a trigger
for the engine to modify the commissioningScope  first to resolve the true -> false constraint to be true -> true).
As a result, the Product Configurator will have next values for the variables:
controlPlacement = "Left"
controlLanguage = "English"
commissioningScope = "Remote Support"
Example 4
In this example, the sequence annotation is not explicitly specified for 3 relations (voltageConnections, controls, and
alternators). The model contains a constraint.
type GeneratorSet {
relation voltageConnections : VoltageConnection[0..999999];
relation controls : Control[1..999999];
relation alternators : Alternator[1..999999];
int alternatorsQty = controls[Control] + voltageConnections[VoltageConnection];
constraint(alternators[Alternator] > 0 -> alternators[Alternator] == alternatorsQty,
"alternators[Alternator] = controls[Control] + voltageConnections[VoltageConnection]");
}
type Alternator;
type VoltageConnection;
1087
Annotation ExamplesProduct Configurator

===== PAGE 1102 =====

type Control;
Example Description and Configurator Result
Even when sequence is not explicitly specified for the relations, the engine sets it implicitly based on the relation declaration order in
the CML type. For this example, the sequence for the relations is:
relation voltageConnections: sequence = 1 (highest priority)
relation controls: sequence = 2
relation alternators: sequence = 3 (lowest priority)
Note:  Use mindful sequencing in CML for variables and relations to avoid backtracking issues. Define them in the order you expect
the engine to modify them during constraint resolution.
In this example, the CML model works without conflicts because the relations are implicitly defined with the correct sequence. The
voltageConnections  and controls relations are evaluated first, then the alternatorsQty  is calculated from their quantities.
Finally, the alternators  relation is adjusted based on that result. Because the alternators  is processed last, the engine avoids
backtracking and errors.
Example 5
In this example, the sequence  annotation is explicitly specified for 3 relations (voltageConnections, controls, and
alternators). The model contains a constraint.
type GeneratorSet {
@(sequence=3)
relation alternators : Alternator[1..999999];
@(sequence=1)
relation voltageConnections : VoltageConnection[0..999999];
@(sequence=2)
relation controls : Control[1..999999];
int alternatorsQty = controls[Control] + voltageConnections[VoltageConnection];
constraint(alternators[Alternator] > 0 -> alternators[Alternator] == alternatorsQty,
"alternators[Alternator] = controls[Control] + voltageConnections[VoltageConnection]");
}
type Alternator;
type VoltageConnection;
type Control;
Example Description and Configurator Result
This example is similar to Example 4, but the sequence is explicitly specified for the relations to control the processing priority and
ensure the engine evaluates and modifies them in the correct order during configuration.
1088
Annotation ExamplesProduct Configurator

===== PAGE 1103 =====

sequence Configuration Settings
Table 14: sequence Configuration Settings
UI BehaviorEngine ActionUser Action"sequence"
annotation
Applicable toProduct Group
Structure
Associated
Example
Display
appropriate
Assign the
sequence for the
Configure the
product
not specifiedVariableN/AExample 1
variable valuesvariables basedcontaining
variables based on
sequence and
constraint logic
on the variable
declaration order
in the type.
Enforce logical
equivalence
between
left-hand side
and right-hand
side for the
constraint by
modifying the
variable with the
highest sequence
Display
appropriate
Assign the
sequence for the
Configure the
product
specifiedVariableN/AExample 2
Example 3 variable values
based on
variables based
on defined
containing
variables
sequence and
constraint logic
sequence
annotation.
Enforce logical
equivalence
between
left-hand side
and right-hand
side for the
constraint by
modifying the
variable with the
highest sequence
Display adjusted
relationships
Assign the
sequence for the
Configure the
bundle product
not specifiedRelationshipIndividual
product
Example 4
based on therelationshipscontaining
relationshipbased on therelationship
products sequence and
constraint logic
relation
declaration order
in the type.
Execute the
constraint
(according to
1089
Annotation ExamplesProduct Configurator

===== PAGE 1104 =====

UI BehaviorEngine ActionUser Action"sequence"
annotation
Applicable toProduct Group
Structure
Associated
Example
assigned
sequence)
Display adjusted
relationships
Assign the
sequence for the
Configure the
bundle product
specifiedRelationshipIndividual
Product
Example 5
based on therelationshipscontaining
relationshipbased on definedrelationship
products sequence and
constraint logic
sequence
annotation.
Execute the
constraint
(according to
specified
sequence)
Display adjusted
relationships
Assign the
sequence for the
Configure the
bundle product
not specifiedRelationshipProduct
Classification
N/A
based on therelationshipscontaining
relationshipbased on therelationship
products sequence and
constraint logic
relation
declaration order
in the type.
Execute the
constraint
(according to
assigned
sequence)
Display adjusted
relationships
Assign the
sequence for the
Configure the
bundle product
specifiedRelationshipProduct
Classification
N/A
based on therelationshipscontaining
relationshipbased on definedrelationship
products sequence and
constraint logic
sequence
annotation.
Execute the
constraint
(according to
specified
sequence)
split Annotation
split  is a Constraint Modeling Language (CML) annotation that specifies whether the instances of the type should be split or not.
splitAnnotation
TypeApplicable to
1090
Annotation ExamplesProduct Configurator

===== PAGE 1105 =====

splitAnnotation
true, falseValue Type/Values
If split is not specified, there are multiple instances of the same
type in the relationship with different quantities.
Description
If the split is specified as true, there can be multiple instances
of the type, and the quantity of each instance is always 1.
If the split is specified as false, there is only one instance in the
relationship.
If the user adds more instances, the engine adds more quantity to
the existing instance.
Example 1
In this example, the split annotation is not specified for the type (Model).
type FESBAGeneratorSet {
relation models : Model;
}
type Model;
Example Description and Configurator Result
In this example, the system allows the multiple instances of the Model type with different quantities defined by the user.
Example 2
In this example, the split annotation is specified as true  for the type (Model).
type FESBAGeneratorSet {
relation models : Model;
}
@(split = true)
type Model;
Example Description and Configurator Result
In this example, the annotation split = true  specifies that the multiple Model instances are split into individual items with fixed
quantity 1.
Example 3
In this example, the split annotation is specified as false  for the type (Model).
type FESBAGeneratorSet {
relation models : Model;
}
@(split = false)
type Model;
1091
Annotation ExamplesProduct Configurator

===== PAGE 1106 =====

Example Description and Configurator Result
In this example, the system allows one instance of the Model type with different quantity defined by the user.
Note:  If there are multiple products of type Model (e.g., FESBA 900kW  and FESBA 1500kW), the user can add both models
to the configuration and adjust the quantity for each one. However, the user cannot add additional separate instances of the same
product (e.g., to configure unique instances with different variable values).
split Configuration Settings
Table 15: split Configuration Settings
UI Behavioruser ActionEngine Action"split" annotationProduct Group
Structure
N/AN/AAdd multiple productsTRUEProduct Classification
Multiple instances
created (qty = 1 each).
Selecting or adding the
product multiple times
manually
N/ATRUEProduct Classification
User can add more
instances, but can't
change quantity per
instance.
One instance created
with qty > 1. User can
N/AAdd multiple productsFALSEProduct Classification
change the quantity of
this instance, but can't
add more instances.
One instance created
with qty = 1. User can
Selecting or adding the
product multiple times
manually
N/AFALSEProduct Classification
change the quantity of
this instance, but can't
add more instances.
One instance created
with qty > 1. User can
N/AAdd multiple products(empty)Product Classification
change quantity and can
add more instances.
One instance created
with qty = 1. User can
Selecting or adding the
product multiple times
manually
N/A(empty)Product Classification
change quantity and can
add more instances.
Multiple line items
created, but Configurator
N/AAdd multiple productsTRUEIndividual Product
displays only one
instance. Users cannot
modify quantity for that
instance.
1092
Annotation ExamplesProduct Configurator

===== PAGE 1107 =====

UI Behavioruser ActionEngine Action"split" annotationProduct Group
Structure
One instance created
with qty = 1. Users
cannot change quantity.
Selecting or adding the
product manually
N/ATRUEIndividual Product
One instance created
with qty > 1. Users can't
Add multiple productsFALSEIndividual Product
modify quantity for that
instance.
One instance created
with qty = 1. Users can
Selecting or adding the
product manually
N/AFALSEIndividual Product
modify quantity for that
instance.
One instance created
with qty > 1. Users can't
Add multiple products(empty)Individual Product
modify quantity for that
instance.
One instance created
with qty = 1. Users can
Selecting or adding the
product manually
N/A(empty)Individual Product
modify quantity for that
instance.
Constraint Modeling Language (CML) Best Practices
To prevent performance degradation or unexpected behaviors when the constraint engine executes CML code, follow these practices
when writing code.
For tips on troubleshooting, see Debugging Constraint Modeling Language (CML) on page 1104.
Relationship Cardinality: Specify the Smallest Range Required
In a relationship, cardinality is the quantity of instances of the same type. Specify the smallest required cardinality for a variable, to avoid
testing unneeded combinations of values. If you specify a higher cardinality than required, or don't specify cardinality, the constraint
engine tests more combinations, which impacts performance.
This example doesn't specify cardinality. The constraint engine tries to set a quantity with 1, 2, 3, all the way up to 9,999:
relation engine : Engine;
This example specifies minimum and maximum cardinality as 0 and 1, so the constraint engine sets the quantity to 1. The engine tests
fewer combinations to find a solution.
relation engine : Engine[0..1];
1093
Constraint Modeling Language (CML) Best PracticesProduct Configurator

===== PAGE 1108 =====

Decimals and Doubles: Consider the Impact of Scale on Performance
In a decimal or double, scale is the number of digits that follow the decimal point. Using decimals and doubles in expressions can cause
performance problems due to the number of permutations.
In this example, myNumber is a double with a scale of 2. The value can be 0.00, 0.01, 0.02, all the way up to 2.99, which can impact
constraint engine performance:
double(2) myNumber = [0..3];
In this example, myNumber is an integer. The value can only be 0, 1, 2 or 3, which has less impact on constraint engine performance:
int myNumber = [0..3];
Variable Domains: Keep Domains as Small as Possible
A variable domain is the set of all possible values that the variable can take. In this example, the variable color has a domain with three
values:
string color = ["Red", "Yellow", "Green"];
The larger the domain, the more possible values for the variable, which means more combinations for the engine to test. A large domain
can impact performance and lead to slower searches, errors, or unexpected behaviors.
Calculating Values: Put Calculations Inside of Constraints
To calculate a value, put the calculation inside of a constraint, instead of in an inline expression.
For example, to calculate area, use this constraint:
constraint(area == length * width)
Avoid this example, which calculates the area with an inline expression, and can impact performance:
area = length * width.
Relationships: Combine Relationships to Reduce Performance Impact
Creating multiple relationships on a type can impact performance. When possible, combine relationships to improve performance.
When possible, avoid this example, which includes separate relationships for Mouse and Keyboard, two accessories in a product bundle:
relation mouse : Mouse;
relation keyboard : Keyboard;
Follow this example, which uses one relationship for Accessories, which can include Mouse, Keyboard, and other accessories.
relation accessories : Accessories;
Sequence: Use the Sequence Variable Annotation to Specify the Order of Execution
If a constraint model includes multiple attributes and relationships that should follow a certain order of execution, use the sequence
variable annotation to specify the order. The constraint engine follows sequence designations in satisfying constraint requirements and
resolving constraint violations.
1094
Constraint Modeling Language (CML) Best PracticesProduct Configurator

===== PAGE 1109 =====

In this example, for the Desktop type, the sequence annotation directs the constraint engine to set the default values for attributes in
this order:
• Display: sequence=1
• Windows_Processor: sequence=2
• Display_Size: sequence=3
type Desktop {
@(defaultValue = "1080p Built-in Display", sequence=1)
string Display = ["1080p Built-in Display", "4k Built-in Display", "2k Built-in
Display"];
@(defaultValue = "15 Inch", sequence=3)
string Display_Size = ["15 Inch", "24 Inch", "13 Inch", "27 Inch"];
@(defaultValue = "i5-CPU 4.4GHz", sequence=2)
string Windows_Processor = ["i5-CPU 4.4GHz", "i7-CPU 4.7GHz", "Intel Core i9 5.2 GHz"];
constraint(Display == "1080p Built-in Display" && Display_Size == "15 Inch" ->
Windows_Processor == "i7-CPU 4.7GHz");
}
For Desktop, Display is set to 1080p, Windows_Processor to i5-CPU, and Display_Size to 15 Inch.
The constraint specifies that a type with Display of 1080p and Display_Size of 15 Inch must have a Windows_Processor of i7-CPU.
constraint(Display == "1080p Built-in Display" && Display_Size == "15 Inch" ->
Windows_Processor == "i7-CPU 4.7GHz");
The Windows_Processor default value of i5-CPU for Desktop violates the constraint. In order to satisfy the constraint and resolve the
violation, the constraint engine uses a different Display_Size for Desktop, such as 24 Inch.
If the user manually updates Display_Size for Desktop to 15 Inch in the Product Configurator, the constraint engine updates
Windows_Processor to i7-CPU to satisfy the constraint.
Sequence and Configurable
Using the configurable  property with the sequence  variable affects how the solver handles attributes. When configurable is
set to true, the user can set attribute values, and the solver doesn't override user input unless no other solution exists. When
configurable  is set to false, the solver sets attribute values.
In this example for type A, attribute1  is set to configurable = true. The user can set the value, and the solver doesn't
override the user input unless no other solution exists. When the left-hand side of the rule is true, the constraint doesn't change
attribute1  to "Enum3".
type A : System {
@(defaultValue = "Enum1", domainComputation = "true", configurable = true, sequence =
48)
string attribute1 = ["Enum1", "Enum2", "Enum3"];
@(configurable = false, defaultValue = "0", sequence = 30)
decimal(2) attribute2 = f(x, y, z);
constraint((attribute2 > 3 && attribute2 <= 5) -> attribute1 == "Enum3", "message");
}
1095
Constraint Modeling Language (CML) Best PracticesProduct Configurator

===== PAGE 1110 =====

In this example for type B, attribute1  is set to configurable = false. The solver propagates values to satisfy constraints.
When the left-hand side of the rule is true, the constraint automatically sets attribute1  to "Enum3".
type B : System {
@(defaultValue = "Enum1", domainComputation = "true", configurable = false, sequence
= 48)
string attribute1 = ["Enum1", "Enum2", "Enum3"];
@(configurable = false, defaultValue = "0", sequence = 30)
decimal(2) attribute2 = f(x, y, z);
constraint((attribute2 > 3 && attribute2 <= 5) -> attribute1 == "Enum3", "message");
Use mindful sequencing in CML to avoid backtracking by the solver when looking for a solution, as in this example.
type LaptopProBundle {
//relation mouse : Mouse[1..20];
//The relation mouse has the highest sequence
relation warranty : Warranty[0..10];
relation software : Software;
relation printerBundle : PrinterBundle;
relation laptop : Laptop[1..10];
relation mouse : Mouse[1..20];
//Put highest sequence last to avoid backtracking
int mouseQty = laptop[Laptop] + warranty[Warranty];
constraint(mouse[Mouse] > 0 -> mouse[Mouse] == mouseQty,
"mouse[Mouse] = laptop[Laptop] + warranty[Warranty]");
Automatically Add a Product: Define as a Separate Constraint
If you need to automatically add a product, and also set attributes on the product, define these procedures as separate constraints, as
in this example.
constraint(laptop[Laptop] > 0, warranty[Warranty] > 0);
constraint(warranty[Warranty] > 0, warranty[Warranty].type == “Premium”);
Avoid this example, which automatically adds a product and sets attributes on the product, in the same constraint.
constraint(laptop[Laptop] > 0, warranty[Warranty] > 0 && warranty[Warranty].type ==
"Premium");
Access Quantity in CML: Cardinality and Attribute Constraints
There are two ways to access quantity in CML:
A cardinality constraint creates or validates the presence of components. The constraint engine adds or removes instances to satisfy the
conditions of the constraint.
An attribute constraint, such as lineItemQuantity or ItemEndQuantity, only reads or validates. The constraint engine validates the
expression, but doesn't configure to satisfy the conditions of the constraint
For best performance, follow these guidelines:
1096
Constraint Modeling Language (CML) Best PracticesProduct Configurator

===== PAGE 1111 =====

• Use a cardinality constraint whenever possible. Use lineItemQuantity  or ItemEndQuantity  only when a cardinality
constraint can't meet the business need.
• Treat lineItemQuantity  and ItemEndQuantity  as read-only. Use only in calculation or evaluation rules.
• Keep scope in mind. When a product can have multiple instances, read lineItemQuantity  or ItemEndQuantity  per
instance. Avoid reading the attribute at a parent or aggregate scope where it can be unbound or ambiguous.
• Don't use lineItemQuantity  or ItemEndQuantity  to create components. Drive component creation by cardinality,
not by attribute references.
Use constraint patterns similar to these examples. Do this.
constraint(mouse[Mouse] == warranty[Warranty])
Avoid this.
constraint(mouse[Mouse].lineItemQuantity == warranty[Warranty].lineItemQuantity)
Do this.
constraint(mouse[Mouse] == 3)
Avoid this.
constraint(mouse[Mouse].lineItemQuantity == 3)
Pricing Fields Not Supported in CML
Pricing fields, such as ListPrice, NetUnitPrice, and others, are not supported in CML and should not be used in constraint models. CML is
designed to enforce configuration logic for products, not to perform pricing calculations. Attempting to reference or manipulate pricing
fields in CML code leads to errors and unexpected behaviors in the constraint engine. Use dedicated pricing or calculation mechanisms
outside of the CML constraint model for such functionality.
Configure Child or Grandchild Products Based on Parent Product
Use the parent  keyword to configure child and grandchild products dynamically based on the parent product. Control visibility or
availability for the child or grandchild using the keyword.
Note:  The parent  keyword isn't supported with Group Type.
In this example, grandchild products are excluded based on which parent product they belong to.
type LineItem;
/*
* Parent 1: Industrial Bundle
* Sets the context 'ApplicationType' to "Industrial"
*/
type IndustrialGeneratorBundle : LineItem {
relation enclosurePackage : EnclosurePackage[1..999];
relation enclosurePackage1 : EnclosurePackage[1..999];
relation enclosurePackage2 : EnclosurePackage;
string ApplicationType = "Industrial";
1097
Constraint Modeling Language (CML) Best PracticesProduct Configurator

===== PAGE 1112 =====

}
/*
* Parent 2: Residential Bundle
* Sets the context 'ApplicationType' to "Residential"
*/
type ResidentialGeneratorBundle : LineItem {
relation enclosurePackage3 : EnclosurePackage[1..999];
relation enclosurePackage4 : EnclosurePackage;
string ApplicationType = "Residential";
}
/*
* Shared Component: Enclosure Package
* Uses parent() to read the ApplicationType and excludes items accordingly.
*/
type EnclosurePackage : LineItem {
relation soundInsulation : SoundInsulation[0..999];
relation weatherProofing : WeatherProofing[0..999];
relation heater : Heater[0..999];
relation lighting : InternalLighting[0..999];
// Retrieve the context tag from the parent bundle
string parentApp = parent(ApplicationType);
message(true, parentApp);
// Logic 1: Exclude Lighting and Heater for BOTH bundles
exclude(parentApp == "Industrial" || parentApp == "Residential",
lighting[InternalLighting]);
exclude(parentApp == "Industrial" || parentApp == "Residential", heater[Heater]);
// Logic 2: Residential (Basic) excludes Sound Insulation
exclude(parentApp == "Residential", soundInsulation[SoundInsulation]);
// Logic 3: Industrial (Pro) excludes Weather Proofing
exclude(parentApp == "Industrial", weatherProofing[WeatherProofing]);
}
// --- Sub-components ---
type SoundInsulation : LineItem {
@(defaultValue = "Foam")
string Material = ["Foam", "Fiberglass"];
}
type WeatherProofing : LineItem {
@(defaultValue = "Standard")
string Grade = ["Standard", "Marine"];
}
type Heater : LineItem;
1098
Constraint Modeling Language (CML) Best PracticesProduct Configurator

===== PAGE 1113 =====

type InternalLighting : LineItem;
PCG Group Relations: Follow Order in Constraints
Order the Product Component Group (PCG) group relations in the way they appear in the constraints. Specify the groups used in the
LHS of the constraints first, followed by those in the RHS.
In this example, the order of PCG groups is incorrect as Test1Group  is part of the LHS and should be declared first.
type TestParent : LineItem {
Test2Group test2group;
Test1Group test1group;
constraint(test1group.testchild1[TestChild1] > 0 -> test2group.testchild2[TestChild2]
== test1group.testchild1[TestChild1]);
}
This example shows the correct order of PCG groups, where Test1Group  is declared first because it is part of the LHS.
type Test20260204Parent : LineItem {
Test1Group test1group;
Test2Group test2group;
constraint(test1group.testchild1[TestChild1] > 0 -> test2group.testchild2[TestChild2]
== test1group.testchild1[TestChild1]);
}
Relations Without PCG: Follow Order in Constraints
Order of relations matter for constraint evaluation. Specify the relations used in the LHS of the constraints first, followed by those in the
RHS.
Relation Aggregates: Stabilize Preferences Using Staged Variables
To improve solver stability and prevent backtracking, avoid referencing relation aggregates directly within preferences when the
preferences also influence the same relation. Instead, stage these aggregates through local variables and state anchors.
In this example, the preferences and the calculated quantity depend directly on live relation aggregates.
relation ml : ModelTraining {
totalNumSubscriptions = total(NumSubscriptions);
subCount = count(Sublicense == true);
}
preference(ml[ModelTraining] > 0 && ml.subCount == 0 -> ml[ModelTraining] == parentQty);
preference(ml[ModelTraining] > 0 && ml.subCount > 0 -> ml[ModelTraining] ==
calculatedQuantity);
constraint(calculatedQuantity == ((ml.totalNumSubscriptions + 99) / 100) * 100);
When the solver evaluates preferences that depend directly on a relation's own aggregates, it creates a tight feedback loop:
1099
Constraint Modeling Language (CML) Best PracticesProduct Configurator

===== PAGE 1114 =====

Relation Quantity   Relation Aggregates   Preference Guards/Targets   Relation Quantity (loop repeats)
The feedback loop can cause the solver to oscillate or backtrack repeatedly before finding a stable solution.
This example shows the stabilized pattern. It introduces staged variables that act as anchors to separate the relation aggregates from
the preference logic.
relation ml : ModelTraining {
totalNumSubscriptions = total(NumSubscriptions);
subCount = count(Sublicense == true);
}
// Stage 1: Convert relation conditions into stable booleans
boolean hasSub;
constraint(hasSub <-> (ml.subCount > 0));
// Stage 2: Copy relation aggregates into local variables
int localTotalNumSubscriptions;
constraint(localTotalNumSubscriptions == ml.totalNumSubscriptions);
// Stage 3: Perform calculations by using the local variables
int calculatedQuantity;
constraint(calculatedQuantity == ((localTotalNumSubscriptions + 99) / 100) * 100);
// Stage 4: Use the staged variables in the preferences
preference(ml[ModelTraining] > 0 && hasSub == false -> ml[ModelTraining] == parentQty);
preference(ml[ModelTraining] > 0 && hasSub == true -> ml[ModelTraining] ==
calculatedQuantity);
With this pattern, instead of solving everything simultaneously, the solver logic processes a pipeline:
Relation   Aggregates   Anchored State/Local Variables   Derived Calculations   Preferences
This process reduces oscillation and makes the solving path more deterministic.
Dependent Logic: Use Configurable Variable Annotation to Prevent Premature Default
Assignment
To ensure preference rules correctly set target attributes based on calculated values, use the @(configurable=false) annotation
on the target attribute. This prevents a race condition where the engine assigns a default value during initialization before your calculation
and preference rules execute.
When an inline expression is used, CML evaluates the model top-down. If the target attribute is declared before the inline calculation,
the engine immediately assigns a default value to the attribute. As a result, any subsequent preference()  rules are ignored because
the engine treats the existing default value as an established selection and avoids overwriting it with the calculated value. Annotating
the target attribute with @(configurable=false)) forces the engine to leave the variable as null  until the calculation and
preference rules are executed.
In this example, the engine processes ShippingMethod  first and immediately assigns the default value "Standard" to it. Later, when
the calculation for totalWeight  returns a value high enough to require the “Freight” shipping method, the engine ignores this
preference rule because the ShippingMethod  variable is already bound to "Standard".
type Order : LineItem {
int quantity = [1..100];
int weightPerUnit = [10..50];
1100
Constraint Modeling Language (CML) Best PracticesProduct Configurator

===== PAGE 1115 =====

// Problem: Engine assigns "Standard" immediately during initialization
@(defaultValue = "Standard")
string ShippingMethod = ["Standard", "Freight"];
// Calculated Attribute via Inline Expression
// The calculation happens after the default is already set
int totalWeight = quantity * weightPerUnit;
// This rule is ignored because ShippingMethod is already bound to "Standard"
preference(totalWeight > 1000 -> ShippingMethod == "Freight");
}
In this example, using the @(configurable=false)  annotation ensures the ShippingMethod  attribute remains as null
until the calculation completes and the rules execute.
Note:  Provide a second preference rule for the fallback condition (else) to ensure a value is always set.
ype Order : LineItem {
int quantity = [1..100];
int weightPerUnit = [10..50];
// Solution: Prevent premature default assignment
@(configurable=false)
string ShippingMethod = ["Standard", "Freight"];
// Calculated Attribute via Inline Expression
int totalWeight = quantity * weightPerUnit;
// Rule 1: Handle the specific condition (high weight)
preference(totalWeight > 1000 -> ShippingMethod == "Freight");
// Rule 2: Handle the fallback (low weight)
preference(totalWeight <= 1000 -> ShippingMethod == "Standard");
}
Business-Centric Constraint Modeling Language (CML) Guidelines
Constraint Modeling Language (CML) must accurately calculate the total sum or aggregate of specific attributes like quantity or userCount
across child components, especially in complex configurations requiring group-level aggregation
The main modeling obstacles when performing aggregation in CML involve:
• Initialization Errors: Preventing runtime errors, such as NullPointerException, which can occur if derived aggregate attributes
lack explicit domains.
• Circular Dependencies: Avoiding calculation loops where the parent and children mutually rely on aggregated totals, often involving
the total() function. If these loops are not broken, the aggregated variable becomes "not bound", which causes the solution to
fail.
1101
Business-Centric Constraint Modeling Language (CML)
Guidelines
Product Configurator

===== PAGE 1116 =====

User Workflow
As a sales representative, when I am configuring a bundle product in the Configurator window, I modify the quantities or specific attributes
of the individual child components. I expect the constraint engine to immediately and accurately calculate the overall aggregated totals
for the parent product, such as the totalItemCount or sumOfUsers.
Business-Centric CML Examples
These Constraint Modeling Language (CML) structures implement quantity aggregation and resolve calculation dependencies.
Business-Centric CML Examples
These Constraint Modeling Language (CML) structures implement quantity aggregation and resolve calculation dependencies.
Example 1: Derived Aggregates (Total Quantity or Sum)
This CML example shows how to model bundle rollups by separating aggregation from validation, ensuring correct calculation order,
solver stability, and business-rule consistency
type LineItem;
type GeneratorSet : LineItem {
int totalItemPowerKW = modelclassification.totalPowerKW;
// Aggregate `powerKW`
relation modelclassification : ModelClassification[0..10] {
totalPowerKW = sum(powerKW);
}
message(true, "GeneratorSet totalItemPowerKW = {} kW (calculated roll-up). Sum of selected
ModelClassification powerKW values = {} kW.", totalItemPowerKW,
modelclassification.totalPowerKW);
}
type ModelClassification : LineItem {
int powerKW = [900, 1750, 2500];
}
type GeneralModel1750 : ModelClassification {
int powerKW = 1750;
}
type GeneralModel2500 : ModelClassification {
int powerKW = 2500;
}
type GeneralModel900 : ModelClassification {
int powerKW = 900;
}
Example Description and Configurator Result
In example 1, the GeneratorSet  type contains the totalItemPowerKW  variable that is assigned with the totalPowerKW.
The model specifies a relationship based on the product classification (modelClassification). This relationship includes
aggregation using the sum() function that calculates the totalPowerKW  from the products selected in the
1102
Business-Centric Constraint Modeling Language (CML)
Guidelines
Product Configurator

===== PAGE 1117 =====

modelClassification  during bundle configuration. The model contains a message for displaying the totalItemPowerKW
with the modelClassification.totalPowerKW  on the Product Configuration.
message(true, "GeneratorSet totalItemPowerKW = {} kW (calculated roll-up). Sum of selected
ModelClassification powerKW values = {} kW.", totalItemPowerKW,
modelclassification.totalPowerKW);
As a result, the engine calculates the totalPowerKW  of user selected products in the modelClassification  and assigns
this value to the totalItemPowerKW. The system displays both values in the information message on the Product Configuration.
Example 2: Resolving Circular Dependencies
This pattern breaks unsolvable loops by enforcing unidirectional data flow (Parent dictates Child quantity based on Child aggregates).
type LineItem;
type GeneratorSet : LineItem {
// RELATION: THE "READ" PHASE
// Data flows UP from children to the parent via the port attribute
relation voltageclassification : VoltageClassification[1..10] {
sumOfChildPower = total(power);
}
// Explicit domain ensures the solver initializes correctly for calculations
decimal(2) totalDistributionValue = [0.00..1000.00];
// CONSTRAINT 1: THE "CALCULATION" PHASE
// @(sequence = 1) ensures the engine reads child data and calculates first
@(sequence = 1)
constraint calcTotalDistribution(totalDistributionValue ==
voltageclassification.sumOfChildPower / 100);
// CONSTRAINT 2: THE "WRITE/ENFORCE" PHASE
// @(sequence = 2) ensures this happens last to push values DOWN to children
@(sequence = 2)
constraint setChildQuantity(voltageclassification[VoltageClassification] ==
totalDistributionValue * 2);
}
type VoltageClassification : LineItem {
int power = [1..100];
}
type VoltageConnection_220_380 : VoltageClassification;
type VoltageConnection_240_416 : VoltageClassification;
type VoltageConnection_255_440 : VoltageClassification;
Example Description and Configurator Result
In example 2, the relationship includes aggregation using the total()  function that calculates the sumOfChildPower  from the
selected products in the voltageclassification. The GeneratorSet type contains the totalDistributionValue
with the explicit domain ([0.00..1000.00]). The model contains two constraints with corresponding @sequence  annotation to enforce
the logical order for calculation of the calcTotalDistribution  (using child products data) and defining the quantity for the
voltageclassification  child items.
1103
Business-Centric Constraint Modeling Language (CML)
Guidelines
Product Configurator

===== PAGE 1118 =====

Example 3: Grouped Aggregation (Sum of Users Across Regions)
This advanced pattern uses the @(groupBy=attribute) annotation to create virtual components (RegionGroup) for aggregation,
referencing the source data relation in the parent type (SubscriptionOrder.licenses) using the sourceContextNode
annotation.
// 1. Base Product Type (e.g., Regional License)
type RegionalLicense {
int regionId = [0..100]; // Attribute for grouping
int userCount = [0..100];
}
// 2. Virtual Group Type (Performs grouping and user sum)
@(split=true, virtual=true, groupBy=regionId)
type RegionGroup {
int regionId;
int groupTotalUsers; // Sum of userCount for this region
// Relation to licenses matching this region group
@(sourceContextNode="SubscriptionOrder.licenses")
relation licenses: RegionalLicense[0..100];
// Constraint: Calculate the aggregate user count within this group
constraint(groupTotalUsers == licenses.sum(userCount));
}
// 3. Parent Order Management (Aggregates all region totals)
@(virtual=true)
type SubscriptionOrder {
// Overall total users is calculated by referencing the group totals
int totalUsers = regionGroups.groupTotalUsers;
relation licenses: RegionalLicense[0..500];
relation regionGroups: RegionGroup[1..10];
}
Example Description and Configurator Result
In example 3, the licenses  relationship that is brought as an external source by
@(sourceContextNode="SubscriptionOrder.licenses"), includes an aggregation using the sum()  function that
calculates the groupTotalUsers  from the selected products in the RegionalLicense. The RegionGroup  type contains
the groupTotalUsers  variable that serves the aggregation. The SubscriptionOrder  type contains the aggregate metric
totalUsers which is calculated by summing all groupTotalUsers. The model contains one core constraint on RegionGroup
to enforce that groupTotalUsers  equals the sum of all userCount  from its member licenses.
Debugging Constraint Modeling Language (CML)
To debug constraint models and troubleshoot performance issues, enable debug logging in Apex and set the debug log level to FINE.
For more information on debug logging in Salesforce, see these topics in Salesforce Help:
• Set Up Debug Logging
• Debug Log
• Debug Log Levels
Use the Apex log to get information about configurator engine performance when running a constraint model, including performance
degradation or unexpected behavior. To improve performance, modify the constraint model based on information in the log.
For tips on writing trouble-free CML, see Constraint Modeling Language (CML) Best Practices on page 1093.
1104
Debugging Constraint Modeling Language (CML)Product Configurator

===== PAGE 1119 =====

About the Apex Debugging Log File
The Apex debugging log file contains three sections: RLM_CONFIGURATOR_BEGIN, RLM_CONFIGURATOR_STATS, and
RLM_CONFIGURATOR_END.
Use the Apex Debugging Log File
To find possible reasons for the performance problems and identify solutions, look at the RLM_CONFIGURATOR_STATS section of
the log file.
About the Apex Debugging Log File
The Apex debugging log file contains three sections: RLM_CONFIGURATOR_BEGIN, RLM_CONFIGURATOR_STATS, and
RLM_CONFIGURATOR_END.
RLM_CONFIGURATOR_BEGIN
JSON representation of the request payload to ExecuteConstraintsRESTService.
"contextProperties" : { },
"rootLineItems" : [ {
"attributes" : { },
"properties" : { },
"ruleActions" : null,
"attributeDomains" : { },
"portDomainsToHide" : { },
"lineItems" : [ {} ]
} ],
"orgId" : "00Dxx0000006H2F"
}
RLM_CONFIGURATOR_STATS
Key statistics of the request execution by the constraint engine, as in this example.
"rootId" : "0QLxx0000004D1uGAE", //Root ID that is being configured
"Product" : "SFDC License", //Root product name
"Total Execution Time" : "2ms", //Total solver time
"Constraints Execution Stats" : "Distinct: 18 Total: 70", //Number of distinct and total
constraint satisfaction attempts
"Solving goal AndGoal([ConfigureComponentGoal(RootProduct RootProduct_0)]) took " : "2ms",
//Total solver time for the goal
"Configurator Stats" : "Total Time 2ms", //Total time
"Number of Component" : "6", //Number of components instantiated
"Number of Variables" : "42", //Number of variables instantiated
"Number of Constraints" : "13", //Number of constraints instantiated
"Number of Backtracks" : "0", //Number of backtracks solver did for the last choice point
"Constraints Violation Stats" : "Distinct: 0 Total: 0", //Distinct and total number of
constraint violations followed by a list of top 10
"ChoicePoint Backtracking Stats" : "Distinct: 0 Total: 0" // Distinct and total number
of backtracked choice points followed by a list of top 10
}
1105
Debugging Constraint Modeling Language (CML)Product Configurator

===== PAGE 1120 =====

RLM_CONFIGURATOR_END
JSON representation of the response payload from ExecuteConstraintsRESTService.
"id" : "0QLxx0000004D1uGAE",
"rootId" : null,
"parentId" : null,
"cfgStatus" : "User",
"name" : "RootProduct",
"relation" : null,
"source" : "SalesTransaction.SalesTransactionItem",
"qty" : 1,
"actionCode" : null,
"modelName" : "Support_instance_variable_in_CML",
"productId" : "01txx0000006iP2AAI",
"productRelatedComponentId" : null,
"attributes" : {}, "properties" : {},
"ruleActions" : [ {} ], "attributeDomains" : {}, "portDomainsToHide" : {},
"lineItems" : [ {} ]
}
Use the Apex Debugging Log File
To find possible reasons for the performance problems and identify solutions, look at the RLM_CONFIGURATOR_STATS section of the
log file.
See the values for Total Execution Time, Constraints Violation Stats, and ChoicePoint Backtracking Stats.
For example, consider how the constraint engine performs with this sample constraint model. In the constraint model, the value of the
volts variable is greater than 110/10000 (volts = power/amps * 9999;). The constraint engine must backtrack the power
variable to find a value that satisfies the constraint, starting with 0.01, 0.02, and so on until it reaches a valid value.
relation laptops : Laptop[1..9999];
@(sequence = 1)
decimal(2) power = [0..500];
@(sequence = 1)
int amps = [1..5];
decimal(2) volts = (power / amps) * laptops[Laptop];
constraint(volts > 110);
In the log file for this constraint model, see the execution statistics for Total Execution Time, Constraints Violation Stats, and ChoicePoint
Backtracking Stats:
"rootId" : "ref_a67c6632_fa1f_40b4_8093_226a9ab8a4d0",
"Product" : "Laptop",
"Total Execution Time" : "676ms",
"Constraints Execution Stats" : "Distinct: 2 Total: 132006",
"Solving goal AndGoal([ConfigureComponentGoal(Laptop Laptop_0)]) took " : "677ms",
"Configurator Stats" : "Total Time 677ms",
"Number of Component" : "1",
"Number of Variables" : "4",
"Number of Constraints" : "1",
"Number of Backtracks" : "49500",
"Constraints Violation Stats" : "Distinct: 1 Total: 41250",
"IntComparison(GT,[DecimalVar(volts)])" : "41250",
"ChoicePoint Backtracking Stats" : "Distinct: 2 Total: 98999",
1106
Debugging Constraint Modeling Language (CML)Product Configurator

===== PAGE 1121 =====

"VariableChoicePoint(DecimalVar(power))" : "49500",
"VariableChoicePoint(IntVar(amps))" : "49499"
Optimally, execution time for a constraint model is less than 100 milliseconds, with fewer than 1,000 backtracks and no violations. Values
for the constraint model example are significantly higher, indicating that the constraint engine is performing inefficiently. To improve
performance in this example, reduce the domain of the power variable without reducing the solution space. For example, define the
domain as [110..500]  instead of [0..500]. This change reduces the number of backtracks the constraint engine performs to
find a solution.
Model Structure
The tables on the following pages show the structure for the constraint model in Core Concept Examples.
See Core Concept Examples on page 1042.
CommentsTypeConfigurable
or Static
API Name
OR CML
Variable
Product
Attribute
Product
Type
Name
ProductProduct
Group
Level
GeneratorSetGenerator
Set
Bundle0
intCONFIGURABLErequiredKWRequired KW
requiredKW
* 1.25
decimalEXPRESSIONsurgeLoadKWSurge Load
KW
surgeLoadKW
- requiredKW
decimalEXPRESSIONreserveCapacityKWReserve
Capacity KW
Picklist
Voltage
["220/380","240/416","255/440","277/480","347/600","2400/4160","7200/12470","7621/13200","7976/13800"]
CONFIGURABLEvoltageVoltage
Picklist
DutyRating
CONFIGURABLEdutyRatingDuty Rating
["Prime
Power",
"Continuous
Power",
"Data Center
Continuous",
"Emergency
Standby
Power"]
Picklist
standardsAndCompliance
standardsAndComplianceStandards
and
Compliance ["Certification-CSA",
"Listing-UL
2200"]
intCONFIGURABLEdBMaxmax dB level
1107
Model StructureProduct Configurator

===== PAGE 1122 =====

CommentsTypeConfigurable
or Static
API Name
OR CML
Variable
Product
Attribute
Product
Type
Name
ProductProduct
Group
Level
Picklist
Power
nominalPowerOutputNominal
Power
Output Output
Picklist ["100
kW", "300
kW", "500
kW", "700
kW"]
General1
GeneralModelGeneral -
Model
2
powerKW
>=
Needs.requiredKW
Picklist
powerKW
[900, 1750,
2500]
STATICpowerKWPower KW
Picklist dB
[78, 90, 94]
STATICdBdB
GeneralModel900General
Model 900
GeneralModel1750General
Model 1750
GeneralModel2500General
Model 2500
VoltageConnectionGeneral -
Voltage
Connection
2
voltage ==
Needs.voltage
Picklist
voltage
["220/380",
STATICvoltageVoltage
"240/416",
"255/440"]
Picklist
cableEntry
CONFIGURABLEcableEntryCable Entry
["Top Entry",
"Bottom
Entry", "Side
Entry"]
1108
Model StructureProduct Configurator

===== PAGE 1123 =====

CommentsTypeConfigurable
or Static
API Name
OR CML
Variable
Product
Attribute
Product
Type
Name
ProductProduct
Group
Level
VoltageConnection_220_380220/380,3
Phase,Wye,4
Wire
VoltageConnection_240_416240/416,3
Phase,Wye,4
Wire
VoltageConnection_255_440255/440,3
Phase,Wye,4
Wire
Alternator1
MainAlternatorAlternator -
Main
Alternator
2
Needs.voltage
== voltage
Picklist
Voltage
STATICvoltage
constraint(Needs.dutyRating=="Prime
Power"->PRP==true)
booleanSTATICPRP
constraint(Needs.dutyRating=="Continuous
Power"->COP==true)
booleanSTATICCOP
constraint(Needs.dutyRating=="Data
Center
Continuous"->DCC==true)
booleanSTATICDCC
constraint(Needs.dutyRating=="Emergency
Standby
Power"->ESP==true)
booleanSTATICESP
FESBA_B595_2Alt-60Hz,Wye,220/380V,150/125/105C-SD/P/C,40C
amb
FESBA_B715_2Alternator-60Hz,Wye,240/416
Volt,105/80C-StbyPrm
FESBA_B691_2Alt-60Hz,Wye,440V,150/125SP,40C
amb
Alternator -
Heater
2
TemperatureSensorAlternator -
Temperature
Sensors
2
1109
Model StructureProduct Configurator

===== PAGE 1124 =====

CommentsTypeConfigurable
or Static
API Name
OR CML
Variable
Product
Attribute
Product
Type
Name
ProductProduct
Group
Level
STATICmaxOperatingKWMax
Operating
KW
EXPRESSIONparentRequiredKWParent
Required KW
StatorTemperatureSensorTemp
Sens-Stator,
2 RTD/Ph
BearingTemperatureSensorBearing,1
RTD NDE
OutputTerminalAlternator -
Output
Terminals
2
OutputTerminals2HoleLugNEMAOutput
Terminals-2-Hole
Lug, NEMA
Engine1
EngineModelEngine -
Engine
Model
2
FESBA_2940Engine -
QSK60-G6
StarterMotorEngine -
Starter Motor
2
FESBA_A334-2Electric
Starter Motor
- 24V DC
FuelFilterEngine - Fuel
Filter
2
FESBA_3090Fuel
Filters-Engine,
Standard
FESBA_C278-2Fuel
Filters-Engine,
Duplex
Control1
1110
Model StructureProduct Configurator

===== PAGE 1125 =====

CommentsTypeConfigurable
or Static
API Name
OR CML
Variable
Product
Attribute
Product
Type
Name
ProductProduct
Group
Level
ControlControl -
Control Main
2
Picklist
["Left",
CONFIGURABLEcontrolPlacementControl
Placement
"Right",
"Top"]
Picklist
["None",
CONFIGURABLEcommissioningScopeCommissioning
Scope
"Remote
Support",
"On-site
Commissioning"]
Picklist
["English",
CONFIGURABLEcontrolLanguageControl
Language
"Danish",
"French"]
FESBA_H704_2PowerCommand
3.3
FESBA_KX21_2PowerCommand
3.3 with MLD
ControlCabinetHeaterControl -
Control
2
Cabinet
Heater
FESBA_A460_2120/240VAC
compatible
Services1
WarrantyServices -
Warranty
2
Warranty_PRPWarranty PRP
Warranty_DCCWarranty
DCC
Warranty_ESPWarranty ESP
MaintenanceServices -
Maintenance
2
int [12..60]CONFIGURABLEmaintenanceDurationMaintenance
Duration
1111
Model StructureProduct Configurator

===== PAGE 1126 =====

CommentsTypeConfigurable
or Static
API Name
OR CML
Variable
Product
Attribute
Product
Type
Name
ProductProduct
Group
Level
Picklist
["Standard",
"Premium"]
CONFIGURABLEcoverageLevelCoverage
Level
StandardMaintenanceKitStandard
Maintenance
Kit
TestServices -
Testing
2
StandardFactoryTestTest -
Standard
Factory
TestRecordTest
Record-Certified
IndependentLaboratoryTestTest-Independent
Laboratory
WitnessTestTest -
Witness
WitnessTestServiceTest-Extended,
Standby
Load, 2
Accessories1
AccessoryAccessories -
Main
2
PicklistCONFIGURABLEcategoryCategory
weightWeight
EnclosureAccessories -
Enclosure
2
Picklist
dBReduction
[0, 1, 3, 6, 9]
STATICdBReductiondB Reduction
Enclosure_NoneEnclosure
None
Enclosure_WeatherEnclosure
Weather
Enclosure_SA1Enclosure
SA1
1112
Model StructureProduct Configurator

===== PAGE 1127 =====

CommentsTypeConfigurable
or Static
API Name
OR CML
Variable
Product
Attribute
Product
Type
Name
ProductProduct
Group
Level
Enclosure_SA2Enclosure
SA2
Enclosure_SA3Enclosure
SA3
Install & Misc1
installInstall & Misc
- Installation
2
1113
Model StructureProduct Configurator

===== PAGE 1128 =====

