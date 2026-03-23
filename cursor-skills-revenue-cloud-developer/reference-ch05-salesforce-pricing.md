---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 5 — Salesforce Pricing

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 5 Salesforce Pricing
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions of Revenue Cloud
where Salesforce Pricing is
enabled
Create customized price adjustment methods and pricing
procedures. Determine the discounts to apply to your products
and services by using price adjustment methods. Get visibility into
the pricing calculation process by using pricing procedures.
SEE ALSO:
Salesforce Help: Permissions for Salesforce Pricing
In this chapter ...
• Salesforce Pricing
Standard Objects
• Salesforce Pricing
Fields on Standard
Objects
• Salesforce Pricing
Business APIs
• Salesforce Pricing
Apex Reference
• Salesforce Pricing
Standard Invocable
Actions
• Salesforce Pricing
Metadata API Types
• Salesforce Pricing
Tooling API Objects
582

===== PAGE 597 =====

Salesforce Pricing Standard Objects
The Salesforce Pricing data model provides objects and fields to manage pricing processes, such as product management and calculation
and application of discounts.
AttributeAdjustmentCondition
Represents the condition applied to an attribute that determines the price of a product or service being sold. This object is available
in API version 60.0 and later.
AttributeBasedAdjRule
Represents the attribute conditions in a rule associated with the attribute based adjustment made for a product or service being
sold. This object is available in API version 60.0 and later.
AttributeBasedAdjustment
Represents the association between the product selling model and the price adjustment for product or service being sold based on
its attributes. This object stores information about the attributes that define the price of the product or service, the discounts applied,
along with its value for a given date range. This object is available in API version 60.0 and later.
AttributeDefinition
Represents a product, asset, or object attribute, for example, a hardware specification or software detail. This object is available in
API version 60.0 and later.
BundleBasedAdjustment
Represents the association between the product selling model and the price adjustment for a product or service being sold as a
bundle. This object stores information of the product or service's price, the discounts applied, along with its value for a given date
range. This object is available in API version 60.0 and later.
CostBook
Represents the cost book that contains multiple cost book entries. This object is available in API version 61.0 and later.
ContractItemPrice
Represents the price of a product on the contract. This object is available in API version 61.0 and later.
CostBookEntry
Represents the total cost of a product or service that’s determined based on various factors that affect a product's price. For example,
when a product is manufactured, the weight of the raw material can be a cost factor based on the amount of material required and
its shipping cost. This object is available in API version 61.0 and later.
PriceAdjustmentSchedule
Represents a series of tiered discounts based on the number of items purchased.  This object is available in API version 60.0 and later.
PriceAdjustmentTier
Represents a discount tier in a price adjustment schedule.  This object is available in API version 60.0 and later.
PriceBook2
Represents a price book that contains the list of products that your org sells. This object is available in API version 60.0 and later.
PriceBookEntry
Represents a product entry (an association between a Pricebook2 and Product2) in a price book. This object is available in API version
60.0 and later.
PriceBookEntryDerivedPrice
Represents the price of a product that’s derived from another source such as a product or an asset. This object is available in API
version 61.0 and later.
583
Salesforce Pricing Standard ObjectsSalesforce Pricing

===== PAGE 598 =====

PriceRevisionPolicy
Represents the guidelines and methods used to modify product or service prices, often incorporating formulas based on price revision
entries and various adjustments. For example, a policy might dictate that prices are revised based on a formula that considers the
regional Consumer Price Index (CPI) with a specific adjustment percentage, effective from a defined date, and categorized as either
a flat adjustment or one directly based on the price revision entry data. This object is available in API version 65.0 and later.
PricingAdjBatchJob
Represents the collective update of multiple records on their prices and other adjustments.  This object is available in API version
62.0 and later.
PricingAdjBatchJobLog
Represents the report that contains a list of failed adjustment requests along with an error message that describes the reason for
failure. This object is available in API version 62.0 and later.
PricingAPIExecution
Represents the pricing resolution for an pricing element determined using strategy name and formula. This object is available in API
version 63.0 and later.
PricingProcedureResolution
Represents a selection for a pricing procedure to execute a pricing process from a list of pricing procedures available. This object is
available in API version 60.0 and later.
PricingProcessExecution
Represents a record generated during the execution of a discovery or pricing procedure. Multiple procedures may be performed
within a single API call, with each recorded in a Pricing API Execution record. This object is available in API version 63.0 and later.
ProductPriceHistoryLog
Stores historical pricing data based on the product's price range. This object is available in API version 62.0 and later.
ProductPriceRange
Represents the price range of a product determined by using a product selling model that’s stored in the relevant price book. This
object is available in API version 62.0 and later.
ProductSellingModel
Defines one method by which a product can be sold; for example, as a one-time sale, an evergreen subscription, or a termed
subscription. If the product is sold on subscription, this object defines the subscription’s term. A product can have multiple product
selling models.  This object is available in API version 60.0 and later.
ProductSellingModelDataTranslation
Represents the translated values of the data stored within the ProductSellingModel record’s fields. This object is available in API
version 61.0 and later.
ProductSellingModelOption
A junction object between Product Selling Model and Product2. This object is available in API version 60.0 and later.
ProcedurePlanCriterion
The procedure plan option associated with the procedure plan criterion record. This object is available in API version 67.0 and later.
ProrationPolicy
Represents the proration policy associated with a Product Selling Model Option that determines how a product's price is calculated
based on subscription duration or billing periods. This object is available in API version 67.0 and later.
SEE ALSO:
Object Reference for the Salesforce Platform: Overview of Salesforce Objects and Fields
SOAP API Developer Guide: Introduction to SOAP API
584
Salesforce Pricing Standard ObjectsSalesforce Pricing

===== PAGE 599 =====

AttributeAdjustmentCondition
Represents the condition applied to an attribute that determines the price of a product or service being sold. This object is available in
API version 60.0 and later.
Supported Calls
create(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(),
search(), update(), upsert()
Fields
DetailsField
Type
reference
AttributeBasedAdjRuleId
Properties
Create, Filter, Group, Sort
Description
Specifies the attribute adjustment rule record for which the condition is to be applied.
This field is a relationship field.
Relationship Name
AttributeBasedAdjRule
Relationship Type
Lookup
Refers To
AttributeBasedAdjRule
Type
reference
AttributeDefinitionId
Properties
Create, Filter, Group, Sort, Update
Description
Specifies the attribute definition record for which the condition is to be applied.
This field is a relationship field.
Relationship Name
AttributeDefinition
Relationship Type
Lookup
Refers To
AttributeDefinition
Type
picklist
BooleanValue
585
AttributeAdjustmentConditionSalesforce Pricing

===== PAGE 600 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the boolean value of the operator.
Possible values are:
• False
• True
Type
dateTime
DateTimeValue
Properties
Create, Filter, Nillable, Sort, Update
Description
The date time value of the attribute.
Type
date
DateValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date value of the attribute.
Type
double
DoubleValue
Properties
Create, Filter, Nillable, Sort, Update
Description
The double value of the attribute.
Type
int
IntegerValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The integer value of the attribute.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
586
AttributeAdjustmentConditionSalesforce Pricing

===== PAGE 601 =====

DetailsField
Description
The timestamp for when the current user last referred to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Name of the attribute adjustment condition.
Type
picklist
Operator
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Operator used by the attribute.
Possible values are:
• doesnotexistin—Does Not Exist In
• equals—Equals
• existsin—Exists In
• greaterorequal—Greater Or Equal
• greaterthan—Greater Than
• lessorequal—Less Or Equal
• lessthan—Less Than
• matches—Matches
• notequals—Not Equals
The default value is equals.
Type
reference
ProductId
Properties
Create, Filter, Group, Sort, Update
587
AttributeAdjustmentConditionSalesforce Pricing

===== PAGE 602 =====

DetailsField
Description
The ID of the product associated with the attribute adjustment condition.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Type
string
StringValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The string value of the attribute.
Type
picklist
UsageType
Properties
Filter, Group, Restricted picklist, Sort
Description
The type of record where the attribute adjustment condition is used.
Possible values are:
• Pricing
• Rating
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
AttributeAdjustmentConditionFeed on page 2727
Feed tracking is available for the object.
AttributeAdjustmentConditionHistory on page 2734
History is available for tracked fields of the object.
AttributeBasedAdjRule
Represents the attribute conditions in a rule associated with the attribute based adjustment made for a product or service being sold.
This object is available in API version 60.0 and later.
588
AttributeBasedAdjRuleSalesforce Pricing

===== PAGE 603 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
int
AttributeCount
Properties
Filter, Group, Nillable, Sort
Description
The number of attributes.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the attribute based adjustment rule was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
Name of the attribute based adjustment rule.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
ID of the owner of the attribute based adjustment rule.
This field is a polymorphic relationship field.
589
AttributeBasedAdjRuleSalesforce Pricing

===== PAGE 604 =====

DetailsField
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
picklist
UsageType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of record where the attribute-based adjustment rule is used.
Possible values are:
• Pricing
• Rating
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
AttributeBasedAdjRuleFeed on page 2727
Feed tracking is available for the object.
AttributeBasedAdjRuleHistory on page 2734
History is available for tracked fields of the object.
AttributeBasedAdjRuleShare on page 2738
Sharing is available for the object.
AttributeBasedAdjustment
Represents the association between the product selling model and the price adjustment for product or service being sold based on its
attributes. This object stores information about the attributes that define the price of the product or service, the discounts applied, along
with its value for a given date range. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
590
AttributeBasedAdjustmentSalesforce Pricing

===== PAGE 605 =====

Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of pricing adjustment being made.
Possible values are:
• Amount
• Override
• Percentage
Type
double
AdjustmentValue
Properties
Create, Filter, Sort, Update
Description
The value of the adjustment being made based on the adjustment type.
Type
reference
AttributeBasedAdjRuleId
Properties
Create, Filter, Group, Sort
Description
The attribute based adjustment rule associated with this attribute based adjustment record.
This field is a relationship field.
Relationship Name
AttributeBasedAdjRule
Relationship Type
Lookup
Refers To
AttributeBasedAdjRule
Type
int
AttributeCount
Properties
Filter, Group, Nillable, Sort
Description
The number of attributes.
591
AttributeBasedAdjustmentSalesforce Pricing

===== PAGE 606 =====

DetailsField
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
ISO code of the currency. Must be one of the valid alphabetic, three-letter currency ISO codes
defined by the ISO 4217 standard, such as USD, GBP, or JPY. Must be unique within your
organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
The date and time when the price list entry comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time till when the price list entry remains effective.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the attribute based adjustment was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
592
AttributeBasedAdjustmentSalesforce Pricing

===== PAGE 607 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Name of the attribute based adjustment.
Type
reference
PriceAdjustmentScheduleId
Properties
Create, Filter, Group, Sort
Description
The price adjustment schedule associated with the attribute based adjustment record.
This field is a relationship field.
Relationship Name
PriceAdjustmentSchedule
Relationship Type
Lookup
Refers To
PriceAdjustmentSchedule
Type
int
PricingTerm
Properties
Filter, Group, Nillable, Sort
Description
The number of pricing term units in the pricing term. Used with PricingTermUnit to define
the length of the pricing term. For example, if PricingTermUnit is Months and this field is 1,
the subscription is priced monthly.If the selling model is one-time, this field must be null.
Type
picklist
PricingTermUnit
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The unit of time used to define the pricing term. Used with PricingTerm to define the length
of the pricing term. For example, if this field is Months and PricingTerm is 1, the subscription
is priced monthly. If the selling model is one-time, this field must be null.
Possible values are:
• Annual—Years
• Months
593
AttributeBasedAdjustmentSalesforce Pricing

===== PAGE 608 =====

DetailsField
• Quarterly
• Semi-Annual
Type
reference
ProductId
Properties
Create, Filter, Group, Sort
Description
The ID of the product associated with the product attribute set.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID of the ProductSellingModel record associated with this attribute based adjustment
record.
This field is a relationship field.
Relationship Name
ProductSellingModel
Relationship Type
Lookup
Refers To
ProductSellingModel
Type
picklist
SellingModelType
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Indicates whether the product is sold as a one-time sale, an evergreen subscription, or a
subscription with a defined term.
Possible values are:
• Evergreen
594
AttributeBasedAdjustmentSalesforce Pricing

===== PAGE 609 =====

DetailsField
• OneTime—One Time
• TermDefined—Term-Defined
The default value is OneTime.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
AttributeBasedAdjustmentFeed on page 2727
Feed tracking is available for the object.
AttributeBasedAdjustmentHistory on page 2734
History is available for tracked fields of the object.
AttributeDefinition
Represents a product, asset, or object attribute, for example, a hardware specification or software detail. This object is available in API
version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
Code
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
Code for the attribute definition. This field is unique within your organization.
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only if the multicurrency feature is enabled. Contains the ISO code for any currency
allowed by the organization.
Possible values are:
595
AttributeDefinitionSalesforce Pricing

===== PAGE 610 =====

DetailsField
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
picklist
DataType
Properties
Create, Filter, Group, Restricted picklist, Sort
Description
The data type of the attribute definition.
Possible values are:
• Checkbox
• Currency
• Date
• Datetime
• Multipicklist
• Number
• Percent
• Picklist
• Text
Type
textarea
DefaultHelpText
Properties
Create, Nillable, Update
Description
The default help text for this attribute.
Type
string
DefaultValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The default value for this attribute.
Type
textarea
Description
Properties
Create, Nillable, Update
596
AttributeDefinitionSalesforce Pricing

===== PAGE 611 =====

DetailsField
Description
Description of this attribute.
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort
Description
The unique name of the attribute definition record.
This name must begin with a letter and use only alphanumeric characters and underscores.
It can't include spaces, end with an underscore, or have two consecutive underscores.
Type
boolean
IsActive
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates that the attribute definition is active. Active attributes definitions can be selected
for products.
The default value is false.
Type
boolean
IsRequired
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the attribute definition is required for a product.
The default value is false.
Type
string
Label
Properties
Create, Filter, Group, Sort, Update
Description
The label for the attribute.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
597
AttributeDefinitionSalesforce Pricing

===== PAGE 612 =====

DetailsField
Description
The date the attribute definition was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the attribute definition was last viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the attribute.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner of the attribute definition.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
reference
PicklistId
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID of the attribute picklist with the valid values for this attribute.
This field is a relationship field.
Relationship Name
Picklist
598
AttributeDefinitionSalesforce Pricing

===== PAGE 613 =====

DetailsField
Relationship Type
Lookup
Refers To
AttributePicklist
Type
string
SourceSystemIdentifier
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The identifier of the attribute definition in an external system.
Type
textarea
ValueDescription
Properties
Create, Nillable, Update
Description
The default value description for this attribute.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
AttributeDefinitionFeed on page 2727
Feed tracking is available for the object.
AttributeDefinitionHistory on page 2734
History is available for tracked fields of the object.
AttributeDefinitionShare on page 2738
Sharing is available for the object.
BundleBasedAdjustment
Represents the association between the product selling model and the price adjustment for a product or service being sold as a bundle.
This object stores information of the product or service's price, the discounts applied, along with its value for a given date range. This
object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
599
BundleBasedAdjustmentSalesforce Pricing

===== PAGE 614 =====

Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of pricing adjustment being made.
Possible values are:
• Amount
• Override
• Percentage
Type
double
AdjustmentValue
Properties
Create, Filter, Sort, Update
Description
The type of pricing adjustment being made.
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
ISO code of the currency. Must be one of the valid alphabetic, three-letter currency ISO codes
defined by the ISO 4217 standard, such as USD, GBP, or JPY. Must be unique within your
organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
The date and time when the bundle based adjustment comes into effect.
600
BundleBasedAdjustmentSalesforce Pricing

===== PAGE 615 =====

DetailsField
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time till when the bundle based adjustment remains effective.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the bundle based adjustment was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the bundle based adjustment was last viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the bundle based adjustment record.
Type
reference
ParentProductId
Properties
Create, Filter, Group, Sort
Description
Represents the immediate parent in the product bundle that the price is configured for.
This field is a relationship field.
Relationship Name
ParentProduct
Relationship Type
Lookup
Refers To
Product2
601
BundleBasedAdjustmentSalesforce Pricing

===== PAGE 616 =====

DetailsField
Type
reference
ParentProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort
Description
The immediate parent node of a product selling model when nodes are represented in a
hierarchial structure.
This field is a relationship field.
Relationship Name
ParentProductSellingModel
Relationship Type
Lookup
Refers To
ProductSellingModel
Type
reference
PriceAdjustmentScheduleId
Properties
Create, Filter, Group, Sort
Description
The price adjustment schedule associated with the bundle based adjustment record.
This field is a relationship field.
Relationship Name
PriceAdjustmentSchedule
Relationship Type
Lookup
Refers To
PriceAdjustmentSchedule
Type
int
PricingTerm
Properties
Filter, Group, Nillable, Sort
Description
The number of pricing term units in the pricing term. Used with PricingTermUnit to define
the length of the pricing term. For example, if PricingTermUnit is Months and this field is 1,
the subscription is priced monthly.If the selling model is one-time, this field must be null.
Type
picklist
PricingTermUnit
602
BundleBasedAdjustmentSalesforce Pricing

===== PAGE 617 =====

DetailsField
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The unit of time used to define the pricing term. Used with PricingTerm to define the length
of the pricing term. For example, if this field is Months and PricingTerm is 1, the subscription
is priced monthly. If the selling model is one-time, this field must be null.
Possible values are:
• Annual—Years
• Months
• Quarterly
• Semi-Annual
Type
reference
ProductId
Properties
Create, Filter, Group, Sort
Description
The ID of the product associated with the product bundle set.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID of the ProductSellingModel record associated with this bundle based adjustment
record.
This field is a relationship field.
Relationship Name
ProductSellingModel
Relationship Type
Lookup
Refers To
ProductSellingModel
603
BundleBasedAdjustmentSalesforce Pricing

===== PAGE 618 =====

DetailsField
Type
reference
RootBundleId
Properties
Create, Filter, Group, Sort
Description
Represents the structural root product in a product's bundle that the price is configured for.
This field is a relationship field.
Relationship Name
RootBundle
Relationship Type
Lookup
Refers To
Product2
Type
reference
RootProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort
Description
The root product selling model. The primary or base product selling method.
This field is a relationship field.
Relationship Name
RootProductSellingModel
Relationship Type
Lookup
Refers To
ProductSellingModel
Type
picklist
SellingModelType
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Indicates whether the product is sold as a one-time sale, an evergreen subscription, or a
subscription with a defined term.
Possible values are:
• Evergreen
• OneTime—One Time
• TermDefined—Term-Defined
The default value is OneTime.
604
BundleBasedAdjustmentSalesforce Pricing

===== PAGE 619 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
BundleBasedAdjustmentFeed on page 2727
Feed tracking is available for the object.
BundleBasedAdjustmentHistory on page 2734
History is available for tracked fields of the object.
CostBook
Represents the cost book that contains multiple cost book entries. This object is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
Date and time when the cost book comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
Date and time till when the cost book is no longer in effect.
Type
boolean
IsDefault
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the cost book is default (true) or not (false).
The default value is true.
605
CostBookSalesforce Pricing

===== PAGE 620 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Timestamp for when the current user last referred to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Timestamp for when the current user last viewed a record related to this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
Name of the cost book.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
ID of the user who created the record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
CostBookFeed on page 2727
Feed tracking is available for the object.
606
CostBookSalesforce Pricing

===== PAGE 621 =====

CostBookHistory on page 2734
History is available for tracked fields of the object.
CostBookShare on page 2738
Sharing is available for the object.
ContractItemPrice
Represents the price of a product on the contract. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
ContractId
Properties
Create, Filter, Group, Sort
Description
The contract record associated with this contract item price record.
This field is a relationship field.
Relationship Name
Contract
Relationship Type
Master-detail
Refers To
Contract (the master object)
Type
picklist
CurrencyIsoCode
Properties
Defaulted on create, Filter, Group, Restricted picklist, Sort
Description
Contains the ISO code for any currency allowed by the organization. Available only if the
multicurrency feature is enabled.
Valid value is:
• USD—U.S. Dollar
607
ContractItemPriceSalesforce Pricing

===== PAGE 622 =====

DetailsField
The default value is USD.
Type
picklist
DiscountType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The unit of the discount.
Valid values are:
• AdjustmentAmount
• AdjustmentPercentage
Type
double
DiscountValue
Properties
Create, Filter, Nillable, Sort, Update
Description
The value of the discount.
Type
dateTime
EndDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time till when the contract item price is no longer in effect.
Type
reference
ItemId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the line item record associated with this contract item price record.
This field is a polymorphic relationship field.
Relationship Name
Item
Relationship Type
Lookup
Refers To
Product2, ProductCategory
608
ContractItemPriceSalesforce Pricing

===== PAGE 623 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last referred to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the contract item price record.
Type
currency
Price
Properties
Create, Filter, Nillable, Sort, Update
Description
The unit price of the product that’s being sold as part of the contract.
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the product selling model record associated with this contract item price record.
This field is a relationship field.
Relationship Name
ProductSellingModel
Relationship Type
Lookup
Refers To
ProductSellingModel
609
ContractItemPriceSalesforce Pricing

===== PAGE 624 =====

DetailsField
Type
picklist
SellingModelType
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Specifies whether the line item is sold as a one-time sale, an evergreen subscription, or a
subscription with a defined term.
Valid values are:
• Evergreen
• OneTime
• TermDefined
The default value is OneTime.
Type
dateTime
StartDate
Properties
Create, Filter, Sort, Update
Description
The date and time when the contract item price comes into effect.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ContractItemPriceFeed on page 2727
Feed tracking is available for the object.
ContractItemPriceHistory on page 2734
History is available for tracked fields of the object.
CostBookEntry
Represents the total cost of a product or service that’s determined based on various factors that affect a product's price. For example,
when a product is manufactured, the weight of the raw material can be a cost factor based on the amount of material required and its
shipping cost. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
610
CostBookEntrySalesforce Pricing

===== PAGE 625 =====

Fields
DetailsField
Type
currency
Cost
Properties
Create, Filter, Sort, Update
Description
Total cost of the product.
Type
reference
CostBookId
Properties
Create, Filter, Group, Sort
Description
ID of the Cost Book record with which this record is associated.
This field is a relationship field.
Relationship Name
CostBook
Relationship Type
Master-detail
Refers To
CostBook (the master object)
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
ISO code for any currency allowed by the organization. Available only for organizations with
the multicurrency feature enabled.
Valid values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
textarea
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
611
CostBookEntrySalesforce Pricing

===== PAGE 626 =====

DetailsField
Description
Description of this cost book entry record.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
Date and time when the cost book entry comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
Date and time till when the cost book entry is no longer in effect.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Timestamp for when the current user last referred to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Timestamp for when the current user last viewed a record related to this record.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Name of the cost book entry.
Type
reference
ProductId
Properties
Create, Filter, Group, Sort
612
CostBookEntrySalesforce Pricing

===== PAGE 627 =====

DetailsField
Description
Required. ID of the Product2 record with which this record is associated. This field must be
specified when creating Product2 records. This field can’t be changed in an update.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
CostBookEntryFeed on page 2727
Feed tracking is available for the object.
CostBookEntryHistory on page 2734
History is available for tracked fields of the object.
PriceAdjustmentSchedule
Represents a series of tiered discounts based on the number of items purchased.  This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
AdjustmentMethod
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The method for applying tiered pricing. Possible values are:
• Range—All items receive the discount of the highest tier the quantity falls in.
• Slab—Items receive the discount defined for the tier they fall in.
613
PriceAdjustmentScheduleSalesforce Pricing

===== PAGE 628 =====

DetailsField
Possible values are:
• Range
• Slab
The default value is Range.
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only if the multicurrency feature is enabled. Contains the ISO code for any currency
allowed by the organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
textarea
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Text description of the price adjustment schedule.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the price adjustment schedule comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the price adjustment schedule remains effective.
Type
boolean
IsActive
614
PriceAdjustmentScheduleSalesforce Pricing

===== PAGE 629 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the price adjustment schedule is active (true) or not (false). You can change
this field’s value as often as necessary. Label is Active. Default value is False.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Indicates whether the price adjustment schedule has been archived (true) or not (false). This
field is read-only.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
Required. The name of the price adjustment schedule. This field is read-only. Label is Price
Adjustment Schedule Name.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The Salesforce ID of the sales representative who owns the price adjustment schedule.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
615
PriceAdjustmentScheduleSalesforce Pricing

===== PAGE 630 =====

DetailsField
Refers To
Group, User
Type
reference
Pricebook2Id
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The price book associated with this price adjustment schedule record.
This field is a relationship field.
Relationship Name
Pricebook2
Relationship Type
Lookup
Refers To
Pricebook2
Type
picklist
ScheduleType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of price adjustment schedule.
Possible values are:
• Attribute
• Bundle
• Custom
• Term
• Volume
The default value is Volume.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PriceAdjustmentScheduleShare on page 2738
Sharing is available for the object.
616
PriceAdjustmentScheduleSalesforce Pricing

===== PAGE 631 =====

PriceAdjustmentTier
Represents a discount tier in a price adjustment schedule.  This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type of price adjustment.
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only if the multicurrency feature is enabled. Contains the ISO code for any currency
allowed by the organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the price adjustment tier comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
617
PriceAdjustmentTierSalesforce Pricing

===== PAGE 632 =====

DetailsField
Description
The date and time when the price adjustment tier remains effective.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Indicates when the user last referred to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
double
LowerBound
Properties
Create, Filter, Sort, Update
Description
The minimum quantity the discount can be applied to. It must be a positive integer and less
than or equal to the upper bound of the tier.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the price adjustment tier.
Type
reference
PriceAdjustmentScheduleId
Properties
Create, Filter, Group, Sort
Description
The ID of the price adjustment schedule that the discount is applied to.
This field is a relationship field.
618
PriceAdjustmentTierSalesforce Pricing

===== PAGE 633 =====

DetailsField
Relationship Name
PriceAdjustmentSchedule
Relationship Type
Lookup
Refers To
PriceAdjustmentSchedule
Type
int
PricingTerm
Properties
Filter, Group, Nillable, Sort
Description
The number of pricing term units in the pricing term. Used with PricingTermUnit to define
the length of the pricing term. For example, if PricingTermUnit is Months and this field is 1,
the subscription is priced monthly.If the selling model is one-time, this field must be null.
Type
picklist
PricingTermUnit
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The unit of time used to define the pricing term. Used with PricingTerm to define the length
of the pricing term. For example, if this field is Months and PricingTerm is 1, the subscription
is priced monthly. If the selling model is one-time, this field must be null.
Possible values are:
• Annual—Years
• Months
Type
reference
Product2Id
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the product associated with the price adjustment tier.
This field is a relationship field.
Relationship Name
Product2
Relationship Type
Lookup
Refers To
Product2
619
PriceAdjustmentTierSalesforce Pricing

===== PAGE 634 =====

DetailsField
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the ProductSellingModel record associated with this price adjustment tier record.
This field is a relationship field.
Relationship Name
ProductSellingModel
Relationship Type
Lookup
Refers To
ProductSellingModel
Type
picklist
SellingModelType
Properties
Defaulted on create, Filter, Group, Restricted picklist, Sort
Description
Indicates whether the product is sold as a one-time sale, an evergreen subscription, or a
subscription with a defined term.
Possible values are:
• Evergreen
• OneTime—One Time
• TermDefined—Term-Defined
The default value is OneTime.
Type
picklist
TierType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The unit of the discount. Possible values are:
• AdjustmentAmount—An amount discounted from an item’s list price
• AdjustmentPercentage—A percentage discounted from an item’s list price
Possible values are:
• AdjustmentAmount—Amount
• AdjustmentPercentage—Percentage
• OverrideAmount—Override
620
PriceAdjustmentTierSalesforce Pricing

===== PAGE 635 =====

DetailsField
Type
double
TierValue
Properties
Create, Filter, Sort, Update
Description
The value of the discount.
Type
double
UpperBound
Properties
Create, Filter, Nillable, Sort, Update
Description
The maximum quantity the discount can be applied to. Must be a positive integer. Not
inclusive. Set this value one digit higher than the quantity you want the tier to include. For
example, if a tier’s upper bound is 99, set the value of UpperBound to 100. For the last tier,
the value is optional.
Usage
To use PriceAdjustmentTiers, associate them with a PriceAdjustmentSchedule.
Tiers can’t overlap, and no gaps are allowed between tiers.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PriceAdjustmentTierFeed on page 2727
Feed tracking is available for the object.
PriceAdjustmentTierHistory on page 2734
History is available for tracked fields of the object.
PriceBook2
Represents a price book that contains the list of products that your org sells. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
621
PriceBook2Salesforce Pricing

===== PAGE 636 =====

Fields
DetailsField
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only if the multicurrency feature is enabled. Contains the ISO code for any currency
allowed by the organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
string
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Text description of the price book.
Type
boolean
IsActive
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the price book is active (true) or not (false). Inactive price books are hidden
in many areas in the user interface. You can change this field’s value as often as necessary.
Label is Active.
The default value is false.
Type
boolean
IsArchived
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the price book has been archived (true) or not (false). This field is read
only.
The default value is false.
622
PriceBook2Salesforce Pricing

===== PAGE 637 =====

DetailsField
Type
boolean
IsStandard
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the price book is the standard price book for the org (true) or not (false).
Every org has one standard price book—all other price books are custom price books.
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
Required. Name of this object. This field is read-only for the standard price book. 
Type
dateTime
ValidFrom
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when a price book is initially valid. If this field is null, the price book is valid
immediately when active.
Type
dateTime
ValidTo
623
PriceBook2Salesforce Pricing

===== PAGE 638 =====

DetailsField
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when a price book is valid to. If this field is null, the price book is valid
until it’s deactivated.
Usage
A price book is a list of products that your org sells.
• Each org has one standard price book that defines the standard or generic list price for each product or service that it sells.
• An org can have multiple custom price books to use for specialized purposes, such as for discounts, different channels or markets,
or select accounts or opportunities. While your client application can create, delete, and update custom price books, your client
application can only update the standard price book.
• For some orgs, the standard price book is the only price needed. If you set up other price books, you can reference the standard
price book when setting up list prices in custom price books.
Use this object to query standard and custom price books that have been configured for your org. A common use of this object is to
allow your client application to obtain valid Pricebook2 object IDs for use when configuring PricebookEntry records via the API.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PriceBook2ChangeEvent on page 2725
Change events are available for the object.
PriceBook2History on page 2734
History is available for tracked fields of the object.
PriceBookEntry
Represents a product entry (an association between a Pricebook2 and Product2) in a price book. This object is available in API version
60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
Fields
Note:  Salesforce Object Search Language (SOSL) allows you to search records across standard and custom objects. When filtering
records in the PriceBookEntry object using SOSL, you can only sort by fields related to Product2.
624
PriceBookEntrySalesforce Pricing

===== PAGE 639 =====

DetailsField
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort
Description
Available only for organizations with the multicurrency feature enabled. Contains the ISO
code for any currency allowed by the organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
boolean
IsActive
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this price book entry is active (true) or not (false). Although you can never
delete PricebookEntry records, your client application can set this flag to false.
Inactive PricebookEntry records are hidden in many areas in the user interface. You can
change this flag on a PricebookEntry record as often as necessary.
The default value is false.
Type
boolean
IsArchived
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the PricebookEntry has been archived (true) or not (false). This field is set
to true when the Product2 record it’s associated with is archived, or when the Pricebook2
record is archived. This field is read only.
The default value is false.
Type
string
Name
Properties
Filter, Group, Nillable, Sort
Description
Name of this price book entry record. This read-only field references the value in the Name
field of the Product2 record.
625
PriceBookEntrySalesforce Pricing

===== PAGE 640 =====

DetailsField
Type
reference
Pricebook2Id
Properties
Create, Filter, Group, Sort
Description
Required. ID of the Pricebook2 record with which this record is associated. This field must
be specified when creating Pricebook2 records. It can’t be changed in an update.
This field is a relationship field.
Relationship Name
Pricebook2
Relationship Type
Lookup
Refers To
Pricebook2
Type
reference
Product2Id
Properties
Create, Filter, Group, Sort
Description
Required. ID of the Product2 record with which this record is associated. This field must be
specified when creating Product2 records. It can’t be changed in an update.
This field is a relationship field.
Relationship Name
Product2
Relationship Type
Lookup
Refers To
Product2
Type
string
ProductCode
Properties
Filter, Group, Nillable, Sort
Description
Product code for this record. This read-only field references the value in the ProductCode field
of the associated Product2 record.
Type
reference
ProductSellingModelId
626
PriceBookEntrySalesforce Pricing

===== PAGE 641 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID of the related product selling model. 
This field is a relationship field.
Relationship Name
ProductSellingModel
Relationship Type
Lookup
Refers To
ProductSellingModel
Type
currency
UnitPrice
Properties
Create, Filter, Sort, Update
Description
Required. Unit price for this price book entry. You can specify a value only
if UseStandardPrice is set to false. 
Type
boolean
UseStandardPrice
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this price book entry uses the standard price defined in the standard
Pricebook2 record (true) or not (false). If set to true, then the UnitPrice field is read-only, and
the value is the same as the UnitPrice value in the corresponding PricebookEntry in the
standard price book (that is, the PricebookEntry record whose Pricebook2Id refers to the
standard price book and whose Product2Id and CurrencyIsoCode are the same as this record).
For PricebookEntry records associated with the standard Pricebook2 record, this field must
be set to true.
The default value is false.
Usage
Use this object to define the association between your organization’s products (Product2) and your organization’s standard price book
or to custom price books ( Pricebook2). Create one PricebookEntry record for each standard or custom price and currency combination
for a product in a Pricebook2.
When creating these records, you must specify the IDs of the associated Pricebook2 record and Product2 record. Once these records are
created, your client application can’t update these IDs.
627
PriceBookEntrySalesforce Pricing

===== PAGE 642 =====

This object is defined only for those organizations that have products enabled as a feature. If the organization doesn’t have the products
feature enabled, then the PricebookEntry object doesn’t appear in the describeGlobal call, and you can’t access it.
If you delete a PriceBookEntry that is referenced by a line item, the line item is unaffected, but the PriceBookEntry is archived and
unavailable from the API. Deleted PriceBookEntry records can’t be recovered.
You must load the standard price for a product before you’re permitted to load its custom prices.
Create PriceBookEntry records by using this sObject API.
https://yourInstance.salesforce.com/services/data/v66.0/sobjects/PricebookEntry
This example shows a sample request that specifies the details of a price book entry.
{
"ProductSellingModelId": "0jPxx0000000005EAA",
"Product2Id": "01tLT00000A0YTlYAN",
"IsActive": true,
"Pricebook2Id": "01s1W000000SYXNQA4",
"UnitPrice": "100.00"
}
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PriceBookEntryChangeEvent on page 2725
Change events are available for the object.
PriceBookEntryHistory on page 2734
History is available for tracked fields of the object.
PriceBookEntryDerivedPrice
Represents the price of a product that’s derived from another source such as a product or an asset. This object is available in API version
61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
ContributingProductId
Properties
Create, Filter, Group, Nillable, Sort
628
PriceBookEntryDerivedPriceSalesforce Pricing

===== PAGE 643 =====

DetailsField
Description
Source product from which the derived price is calculated. The source product is associated
with the derived price product.
This field is a relationship field.
Relationship Name
ContributingProduct
Relationship Type
Lookup
Refers To
Product2
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
ISO code for any currency allowed by the organization. Available only if the multicurrency
feature is enabled.
Valid values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
picklist
DerivedPricingScope
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Scope of the product based on which the derived price is calculated.
Valid values are:
• Both
• NonTransactional
• Transactional
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
629
PriceBookEntryDerivedPriceSalesforce Pricing

===== PAGE 644 =====

DetailsField
Description
Date and time when the derived pricing comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
Date and time when the derived pricing is no longer in effect.
Type
string
Formula
Properties
Create, Filter, Sort, Update
Description
Coded format of the formula used to calculate the derived price of a product from another
product or asset.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Timestamp for when the current user last referred to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Timestamp for when the current user last viewed this record. If this value is null, it’s possible
that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Name of the derived price record.
Type
reference
OwnerId
630
PriceBookEntryDerivedPriceSalesforce Pricing

===== PAGE 645 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
ID of the user who created the record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
reference
PricebookEntryId
Properties
Create, Filter, Group, Sort
Description
Price book entry associated with the source product.
This field is a relationship field.
Relationship Name
PricebookEntry
Relationship Type
Lookup
Refers To
PricebookEntry
Type
reference
PricebookId
Properties
Create, Filter, Group, Nillable, Sort
Description
Price book associated with the source product.
This field is a relationship field.
Relationship Name
Pricebook
Relationship Type
Lookup
Refers To
Pricebook2
631
PriceBookEntryDerivedPriceSalesforce Pricing

===== PAGE 646 =====

DetailsField
Type
picklist
PricingSource
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Pricing type used to calculate the derived price of the product.
Valid values are:
• Header
• Product
Type
reference
ProductId
Properties
Filter, Group, Sort
Description
Product associated with the derived pricing.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Filter, Group, Sort
Description
Product selling model associated with this record.
This field is a relationship field.
Relationship Name
ProductSellingModel
Relationship Type
Lookup
Refers To
ProductSellingModel
632
PriceBookEntryDerivedPriceSalesforce Pricing

===== PAGE 647 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PriceBookEntryDerivedPriceFeed on page 2727
Feed tracking is available for the object.
PriceBookEntryDerivedPriceHistory on page 2734
History is available for tracked fields of the object.
PriceBookEntryDerivedPriceShare on page 2738
Sharing is available for the object.
PriceRevisionPolicy
Represents the guidelines and methods used to modify product or service prices, often incorporating formulas based on price revision
entries and various adjustments. For example, a policy might dictate that prices are revised based on a formula that considers the regional
Consumer Price Index (CPI) with a specific adjustment percentage, effective from a defined date, and categorized as either a flat adjustment
or one directly based on the price revision entry data. This object is available in API version 65.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
date
EffectiveFrom
Properties
Create, Filter, Group, Sort, Update
Description
The date and time when the price revision policy comes into effect.
Type
date
EffectiveTo
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date and time when the price revision policy is no longer in effect.
Type
string
Formula
Properties
Create, Filter, Group, Sort, Update
633
PriceRevisionPolicySalesforce Pricing

===== PAGE 648 =====

DetailsField
Description
The coded format of the formula used to calculate the revised price of a product from a
quote and order, or contract.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the price revision policy.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
ID of the user who created the record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
picklist
PolicyType
634
PriceRevisionPolicySalesforce Pricing

===== PAGE 649 =====

DetailsField
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of price revision policy.
Valid values are:
• Flat—You can’t define a price index-based formula for revision.
• PriceIndex—Price Index
Type
picklist
Region
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The region where the price revision policy is valid.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PriceRevisionPolicyFeed on page 2727
Feed tracking is available for the object.
PriceRevisionPolicyHistory on page 2734
History is available for tracked fields of the object.
PriceRevisionPolicyShare on page 2738
Sharing is available for the object.
PricingAdjBatchJob
Represents the collective update of multiple records on their prices and other adjustments.  This object is available in API version 62.0
and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
635
PricingAdjBatchJobSalesforce Pricing

===== PAGE 650 =====

Fields
DetailsField
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the updated value can be considered for a pricing adjustment batch
job.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time until when the updated value is effective and can be considered for a
pricing adjustment batch job.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Indicates whether the pricing adjustment batch job has been archived (true) or not
(false). This field is read-only.
Type
dateTime
LastTriggeredDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the pricing adjustment batch job was last triggered.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
636
PricingAdjBatchJobSalesforce Pricing

===== PAGE 651 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the pricing adjustment batch job.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The Salesforce ID of the sales representative who owns the pricing procedure resolution.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
long
ProcessedRecordsCount
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The total number of records that were successfully updated.
Type
long
RecordCount
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The total number of records that have been processed.
Type
textarea
RecordList
Properties
Create
Description
The list of record IDs eligible for a pricing adjustment batch job.
637
PricingAdjBatchJobSalesforce Pricing

===== PAGE 652 =====

DetailsField
Type
boolean
ShouldSkipBulkRetry
Properties
Create, Filter, Group, Nillable, Sort
Description
For internal use only.
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The processing status of the pricing adjustment batch job.
Valid values are:
• Completed
• Failed
• InProgress
• New
• PartiallyCompleted
• Rerun
Type
picklist
TargetObject
Properties
Create, Filter, Group, Restricted picklist, Sort
Description
The target object of the pricing adjustment batch job.
Valid values are:
• AttributeBasedAdjustment
• BundleBasedAdjustment
• PriceAdjustmentTier
• PricebookEntry
Type
picklist
UpdateType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of update being made by the pricing adjustment batch job.
Valid values are:
638
PricingAdjBatchJobSalesforce Pricing

===== PAGE 653 =====

DetailsField
• Amount
• Override
• Percentage
Type
double
UpdateValue
Properties
Create, Filter, Sort, Update
Description
The numerical value of the update.
Usage
To execute a pricing adjustment batch job through an API request, make a POST request to the
/services/data/v66.0/sobjects/PricingAdjBatchJob  resource. Here's a sample request payload.
{
"TargetObject": "PriceAdjustmentTier",
"UpdateType": "Amount",
"UpdateValue": "10",
"RecordList": "84YDU00000010ig2AA,84YDU00000010ig2AB,84YDU00000010ig2AC",
"EffectiveFrom": "2024-08-01T10:07:09.000+0000",
"EffectiveTo": "2024-08-05T10:07:09.000+0000"
}
You can specify a comma-separated list of record IDs that are eligible for a pricing adjustment batch job.
To rerun a pricing adjustment batch job, make a PATCH request to the
/services/data/v66.0/sobjects/PricingAdjBatchJob/pricingAdjBatchJobID resource. Here's a sample
request payload.
{
"Status": "Rerun"
}
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PricingAdjBatchJobFeed on page 2727
Feed tracking is available for the object.
PricingAdjBatchJobHistory on page 2734
History is available for tracked fields of the object.
PricingAdjBatchJobShare on page 2738
Sharing is available for the object.
639
PricingAdjBatchJobSalesforce Pricing

===== PAGE 654 =====

PricingAdjBatchJobLog
Represents the report that contains a list of failed adjustment requests along with an error message that describes the reason for failure.
This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
double
AdjustedValue
Properties
Create, Filter, Nillable, Sort, Update
Description
The adjusted value of a record. The stored value is used even if another pricing adjustment
batch job is triggered again.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the failed versioned record is generated. This is only applicable for
Price Adjustment records.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time until when the failed versioned record is available. This is applicable only
for Price Adjustment records.
Type
string
ErrorCode
Properties
Create, Filter, Group, Nillable, Sort, Update
640
PricingAdjBatchJobLogSalesforce Pricing

===== PAGE 655 =====

DetailsField
Description
The error code for the failure during the record update process.
Type
textarea
ErrorMessage
Properties
Create, Update
Description
The error message that’s generated for the failure during the record update process.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Indicates whether the pricing adjustment batch job has been archived (true) or not
(false). This field is read-only.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Required. The name of the pricing adjustment batch job.
Type
reference
PricingAdjBatchJobId
Properties
Create, Filter, Group, Sort
Description
The pricing adjustment batch job associated with the pricing adjustment batch job log.
This field is a relationship field.
641
PricingAdjBatchJobLogSalesforce Pricing

===== PAGE 656 =====

DetailsField
Relationship Name
PricingAdjBatchJob
Relationship Type
Master-detail
Refers To
PricingAdjBatchJob (the master object)
Type
string
TargetRecord
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The ID of the record for which a pricing adjustment error was generated.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PricingAdjBatchJobLogFeed
Feed tracking is available for the object.
PricingAdjBatchJobLogHistory on page 2734
History is available for tracked fields of the object.
PricingAPIExecution
Represents the pricing resolution for an pricing element determined using strategy name and formula. This object is available in API
version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
ApiEndpoint
Properties
Create, Filter, Group, Nillable, Sort, Update
642
PricingAPIExecutionSalesforce Pricing

===== PAGE 657 =====

DetailsField
Description
The unique API endpoint that is called.
Type
picklist
ApiType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the API type of the pricing API execution.
Possible values are:
• NGP
The default value is NGP.
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only if the multicurrency feature is enabled. Contains the ISO code for any currency
allowed by the organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
string
ExecutionKey
Properties
Create, Filter, Group, Sort, Update
Description
The unique execution ID generated each time a pricing API runs.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
643
PricingAPIExecutionSalesforce Pricing

===== PAGE 658 =====

DetailsField
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The Salesforce ID of the sales representative who owns the pricing procedure resolution.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
string
ReferenceKey
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Optional. The reference ID that a consuming workstream must pass in the API to search for
specific logs in the Pricing Operations Console.
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the API response.
644
PricingAPIExecutionSalesforce Pricing

===== PAGE 659 =====

DetailsField
Possible values are:
• Failure
• Partial_Success—Partial Success
• Success
The default value is Success.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PricingAPIExecutionFeed on page 2727
Feed tracking is available for the object.
PricingAPIExecutionHistory on page 2734
History is available for tracked fields of the object.
PricingAPIExecutionShare on page 2738
Sharing is available for the object.
PricingProcedureResolution
Represents a selection for a pricing procedure to execute a pricing process from a list of pricing procedures available. This object is
available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only if the multicurrency feature is enabled. Contains the ISO code for any currency
allowed by the organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
645
PricingProcedureResolutionSalesforce Pricing

===== PAGE 660 =====

DetailsField
• USD—U.S. Dollar
The default value is USD.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
The date and time when the pricing procedure resolution comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time till when the pricing procedure resolution remains effective.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Indicates whether the pricing procedure resolution has been archived (true) or not (false).
This field is read-only.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Required. The name of the pricing procedure resolution.
Type
reference
OwnerId
646
PricingProcedureResolutionSalesforce Pricing

===== PAGE 661 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The Salesforce ID of the sales representative who owns the pricing procedure resolution.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
reference
PricingProcedureId
Properties
Create, Filter, Group, Sort
Description
The pricing procedure record associated with this pricing procedure resolution.
This field is a relationship field.
Relationship Name
PricingProcedure
Relationship Type
Lookup
Refers To
ExpressionSet
Type
picklist
ProcedureType
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The pricing data store associated with this pricing recipe field mappings.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PricingProcedureResolutionFeed on page 2727
Feed tracking is available for the object.
647
PricingProcedureResolutionSalesforce Pricing

===== PAGE 662 =====

PricingProcedureResolutionHistory on page 2734
History is available for tracked fields of the object.
PricingProcedureResolutionShare on page 2738
Sharing is available for the object.
PricingProcessExecution
Represents a record generated during the execution of a discovery or pricing procedure. Multiple procedures may be performed within
a single API call, with each recorded in a Pricing API Execution record. This object is available in API version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only if the multicurrency feature is enabled. Contains the ISO code for any currency
allowed by the organization.
Possible values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
string
ExecutionKey
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The unique execution ID generated each time a pricing API runs.
Type
picklist
ExecutionType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
648
PricingProcessExecutionSalesforce Pricing

===== PAGE 663 =====

DetailsField
Description
The type of execution defined internally within the pricing API.
Possible values are:
• Api_Execution—Api Execution
• Discovery
• Discovery_Line—Discovery Line
• Pricing
• Pricing_Line—Pricing Line
The default value is Pricing.
Type
string
ExecutionTypeKey
Properties
Create, Filter, Group, Sort, Update
Description
The unique execution type ID generated internally for procedure executions, such as pricing
or discovery procedures.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
textarea
Message
Properties
Create, Nillable, Update
Description
The message generated upon running a pricing process.
649
PricingProcessExecutionSalesforce Pricing

===== PAGE 664 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The Salesforce ID of the sales representative who owns the pricing procedure resolution.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the status of the execution type.
Possible values are:
• Failure
• Partial_Success—Partial Success
• Success
The default value is Success.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
PricingProcessExecutionFeed on page 2727
Feed tracking is available for the object.
PricingProcessExecutionHistory on page 2734
History is available for tracked fields of the object.
650
PricingProcessExecutionSalesforce Pricing

===== PAGE 665 =====

PricingProcessExecutionShare on page 2738
Sharing is available for the object.
ProductPriceHistoryLog
Stores historical pricing data based on the product's price range. This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
ISO code for any currency allowed by the organization. Available only for organizations with
the multicurrency feature enabled.
Valid values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
date
Date
Properties
Create, Filter, Group, Sort, Update
Description
The date when the product price history log record is created.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
651
ProductPriceHistoryLogSalesforce Pricing

===== PAGE 666 =====

DetailsField
Description
Indicates whether the product price history log has been archived (true) or not (false).
This field is read-only.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Required. The name of the product price history log.
Type
reference
ProductPriceRangeId
Properties
Create, Filter, Group, Sort
Description
The product price range associated with this product price history log record.
This field is a relationship field.
Relationship Name
ProductPriceRange
Relationship Type
Master-detail
Refers To
ProductPriceRange (the master object)
Type
currency
TrackedPrice
Properties
Create, Filter, Sort, Update
Description
The price for a product recorded for a particular date.
652
ProductPriceHistoryLogSalesforce Pricing

===== PAGE 667 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductPriceHistoryLogFeed on page 2727
Feed tracking is available for the object.
ProductPriceHistoryLogHistory on page 2734
History is available for tracked fields of the object.
ProductPriceRange
Represents the price range of a product determined by using a product selling model that’s stored in the relevant price book. This object
is available in API version 62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
ISO code for any currency allowed by the organization. Available only for organizations with
the multicurrency feature enabled.
Valid values are:
• BHD—Bahraini Dinar
• JPY—Japanese Yen
• USD—U.S. Dollar
The default value is USD.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Indicates whether the product price range has been archived (true) or not (false). This
field is read-only.
653
ProductPriceRangeSalesforce Pricing

===== PAGE 668 =====

DetailsField
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, it’s
possible that this record was referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Required. The name of the product price range.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The Salesforce ID of the sales representative who owns the product price range.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
ProductId
Properties
Create, Filter, Group, Sort, Update
Description
The product for which the price range is being determined.
This field is a relationship field.
Relationship Name
Product
Refers To
Product2
Type
reference
ProductSellingModelId
654
ProductPriceRangeSalesforce Pricing

===== PAGE 669 =====

DetailsField
Properties
Filter, Group, Nillable, Sort
Description
The product selling model used to determine the price range of the product.
This field is a relationship field.
Relationship Name
ProductSellingModel
Refers To
ProductSellingModel
Type
currency
RecordedPrice
Properties
Filter, Nillable, Sort
Description
The selected price of the product over a range of prices.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductPriceRangeFeed on page 2727
Feed tracking is available for the object.
ProductPriceRangeHistory on page 2734
History is available for tracked fields of the object.
ProductPriceRangeShare on page 2738
Sharing is available for the object.
ProductSellingModel
Defines one method by which a product can be sold; for example, as a one-time sale, an evergreen subscription, or a termed subscription.
If the product is sold on subscription, this object defines the subscription’s term. A product can have multiple product selling models. 
This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
655
ProductSellingModelSalesforce Pricing

===== PAGE 670 =====

Fields
DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Indicates when the user last referred to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Indicates when the user last viewed this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name given to the product selling model.
Type
int
PricingTerm
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The number of pricing term units in the pricing term. Used with PricingTermUnit to define
the length of the pricing term. For example, if PricingTermUnit is Months and this field is 1,
the subscription is priced monthly.If the selling model is one-time, this field must be null.
Type
picklist
PricingTermUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The unit of time used to define the pricing term. Used with PricingTerm to define the length
of the pricing term. For example, if this field is Months and PricingTerm is 1, the subscription
is priced monthly. If the selling model is one-time, this field must be null.
Possible values are:
• Months
656
ProductSellingModelSalesforce Pricing

===== PAGE 671 =====

DetailsField
• Quarterly
• Semi-Annual
• Annual
Type
picklist
SellingModelType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Indicates whether the product is sold as a one-time sale, an evergreen subscription, or a
subscription with a defined term.
Possible values are:
• Evergreen
• OneTime
• TermDefined
The default value is OneTime.
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the product selling model.
Possible values are:
• Active
• Draft
• Inactive
The default value is Draft.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductSellingModelFeed on page 2727
Feed tracking is available for the object.
ProductSellingModelHistory on page 2734
History is available for tracked fields of the object.
657
ProductSellingModelSalesforce Pricing

===== PAGE 672 =====

ProductSellingModelDataTranslation
Represents the translated values of the data stored within the ProductSellingModel record’s fields. This object is available in API version
61.0 and later.
Supported Calls
create(), delete(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(),
undelete(), update(), upsert()
Special Access Rules
• Your organization must be using Enterprise, Unlimited, or Developer edition.
• Translation Workbench and data translation must be enabled in your org.
• To view this object, you must have the “View Setup and Configuration” permission.
Fields
DetailsField
Type
boolean
IsOutOfDate
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the translation is out-of-date (true) or current (false). A translation
is out-of-date if the parent Product2 record is updated after the last translation was filed.
Type
picklist
Language
Properties
Create, Filter, Group, Restricted picklist, Sort
Description
The language for these translated values.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The translated value for the ProductSellingModel record name. This field is required to
translate the text in other fields.
Type
reference
ParentId
658
ProductSellingModelDataTranslationSalesforce Pricing

===== PAGE 673 =====

DetailsField
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the ProductSellingModel record associated with the data that’s being translated.
This field is a relationship field.
Relationship Name
Parent
Relationship Type
Lookup
Refers To
ProductSellingModel
Usage
Use this object to translate the data stored in a ProductSellingModel record into the different languages supported by Salesforce. If data
translation is enabled for custom fields on the ProductSellingModel object, additional ProductSellingModelDataTranslation fields exist
for translating the data contained within those fields.
You can’t use a custom external id field in an upsert call for a ProductSellingModelDataTranslation object.
ProductSellingModelOption
A junction object between Product Selling Model and Product2. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
textarea
Description
Properties
Create, Nillable, Update
Description
The description of the product selling model option.
Type
string
DisplayName
659
ProductSellingModelOptionSalesforce Pricing

===== PAGE 674 =====

DetailsField
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the product selling model option to display to customers.
Type
int
Increment
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The number of pricing term units that can be used to increase a subscription term.
Type
boolean
IsDefault
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indcates the default product selling model for a product. Setting a default is optional. A
product can only have one default product selling model.
The default value is false. This field requires Industries EPC.
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
the user might have only accessed this record or list view but not viewed it.
Type
int
Maximum
Properties
Create, Filter, Group, Nillable, Sort, Update
660
ProductSellingModelOptionSalesforce Pricing

===== PAGE 675 =====

DetailsField
Description
The maximum number of pricing term units for a subscription term.
Type
int
Minimum
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The minimum number of pricing term units for a subscription term.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the product selling model option.
Type
reference
Product2Id
Properties
Create, Filter, Group, Sort
Description
The ID of the Product2 record associated with this ProductSellingModelOption record.
This field is a relationship field.
Relationship Name
Product2
Relationship Type
Lookup
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Sort
Description
The ID of the ProductSellingModel record associated with
this ProductSellingModelOption record.
This field is a relationship field.
Relationship Name
ProductSellingModel
661
ProductSellingModelOptionSalesforce Pricing

===== PAGE 676 =====

DetailsField
Relationship Type
Lookup
Refers To
ProductSellingModel
Type
reference
ProrationPolicyId
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID of the ProrationPolicy record associated with this ProductSellingModelOption record.
This field is a relationship field.
Relationship Name
ProrationPolicy
Relationship Type
Lookup
Refers To
ProrationPolicy
ProcedurePlanCriterion
The procedure plan option associated with the procedure plan criterion record. This object is available in API version 67.0 and later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Fields
DetailsField
Type
string
ActualValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The user-defined value that is compared to the value of the SObject field value.
Type
picklist
DataType
662
ProcedurePlanCriterionSalesforce Pricing

===== PAGE 677 =====

DetailsField
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The data type of the field from the selected object.
Type
string
FieldPath
Properties
Create, Filter, Group, Sort, Update
Description
The path of the field used in a procedure in relation to the object that the field belongs to.
Type
string
ObjectField
Properties
Create, Filter, Group, Sort, Update
Description
The object field value used to resolve the procedure plan option.
Type
picklist
Operator
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the operator used by the procedure plan criterion.
Possible values are:
• Equals
• GreaterThan
• GreaterThanOrEquals
• In
• IsNotNull
• IsNull
• LessThan
• LessThanOrEquals
• NotEquals
• NotIn
Type
reference
ProcedurePlanOptionId
663
ProcedurePlanCriterionSalesforce Pricing

===== PAGE 678 =====

DetailsField
Properties
Create, Filter, Group, Sort
Description
This field is a relationship field.
Relationship Name
ProcedurePlanOption
Relationship Type
Master-detail
Refers To
ProcedurePlanOption (the master object)
Type
int
Sequence
Properties
Create, Filter, Group, Sort
Description
The sequence in which the conditions defined in the procedure plan criteria are processed.
ProrationPolicy
Represents the proration policy associated with a Product Selling Model Option that determines how a product's price is calculated
based on subscription duration or billing periods. This object is available in API version 67.0 and later.
Supported Calls
create(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(),
search()
Fields
DetailsField
Type
boolean
ArePartialPeriodsAllowed
Properties
Create, Defaulted on create, Filter, Group, Sort
Description
Indicates whether partial periods should be allowed for standard time periods.
The default value is false.
664
ProrationPolicySalesforce Pricing

===== PAGE 679 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the proration policy was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the proration policy was last viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort
Description
The name of the proration policy.
Type
picklist
ProrationPolicyType
Properties
Create, Filter, Group, Restricted picklist, Sort
Description
The type of proration policy to be used.
Possible values are:
• StandardTimePeriods—Standard Time Periods
Type
picklist
RemainderStrategy
Properties
Create, Filter, Group, Restricted picklist, Sort
Description
The type of remainder strategy to be used.
665
ProrationPolicySalesforce Pricing

===== PAGE 680 =====

Salesforce Pricing Fields on Standard Objects
Salesforce Pricing adds standard fields to some standard Salesforce objects of other features to represent information specific to pricing.
These fields are available only in orgs where Salesforce Pricing is enabled.
IndexRate
Standard fields extend the IndexRate object for use in Salesforce Pricing to represent information for a given rate. This object is
available in API version 65.0 and later.
IndexRate
Standard fields extend the IndexRate object for use in Salesforce Pricing to represent information for a given rate. This object is available
in API version 65.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
Region
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Specified the region associated with the given rate.
Type
picklist
UsageType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the usage type associated with the given rate.
Possible values are:
• Pricing
666
Salesforce Pricing Fields on Standard ObjectsSalesforce Pricing

===== PAGE 681 =====

Salesforce Pricing Business APIs
Perform pricing request, create context instance, sync pricing data, and manage pricing recipes and pricing waterfall details by using
Salesforce Pricing Business APIs.
This table lists the available Salesforce Pricing resources.
DescriptionResource
Perform a pricing request by
using the instance ID of a
context.
/connect/core-pricing/price-contexts/contextid (POST)
Create and hydrate context
instance in a single request.
/connect/core-pricing/pricing (POST)
Provide a comprehensive
response that contains final
pricing details per line items
and related errors, if any.
Sync pricing data to ensure that
the lookup tables contain the
latest pricing data.
/connect/core-pricing/sync/pricingSyncOrigin (GET)
Get the mapping details of
pricing recipes to the associated
pricing recipe table.
/connect/core-pricing/recipe (GET)
Create a mapping between the
pricing recipe and the Decision
/connect/core-pricing/recipe/mapping (POST)
Tables. Post recipes with lookup
tables or procedures.
Create revisions of a pricing
request with versions for
adjustment entities.
/connect/core-pricing/versioned-revise-details (POST)
Get the persisted price waterfall
that stores the process logs.
/connect/core-pricing/waterfall/lineItemId/executionId (GET)
Price waterfall provides insights
into every step of the pricing
process.
Create a log of price waterfall.
Price waterfall provides insights
/connect/core-pricing/waterfall (POST)
into every step of the pricing
process.
Get the source product for the
Price Book Entry (PBE) derived
pricing.
/connect/core-pricing/pbeDerivedPricingSourceProduct (POST)
667
Salesforce Pricing Business APIsSalesforce Pricing

===== PAGE 682 =====

DescriptionResource
Get the log details of a pricing
API execution record by using
the execution ID.
/connect/core-pricing/apiexecutionlogs/executionId (GET)
Get the execution details of a
pricing process by using the
execution ID.
/connect/core-pricing/pricing-process-execution/executionId (GET)
Get the pricing execution details
for the line items of a pricing
/connect/core-pricing/pricing-process-execution/lineitems/executionId/executionType
(GET)
process by using the execution
ID and execution type.
Get details of the pricing
simulation input variables along
with associated data.
/connect/core-pricing/simulationInputVariablesWithData (GET)
This section lists the available Procedure Plan Definition-related resources. Use procedure plan definitions to define criteria for all pricing
process-related requirements in one central location, and to set up the procedures based on these requirements.
DescriptionResource
Get the records of procedure
plan definitions. Additionally,
/connect/procedure-plan-definitions (GET, POST)
create a record of a procedure
plan definition.
Get, update, or delete a
procedure plan definition
record by using the record ID.
/connect/procedure-plan-definitions/procedurePlanDefinitionId (GET,
PATCH, DELETE)
Evaluate a procedure plan
definition based on a primary
/connect/procedure-plan-definitions/evaluate (POST)
object to check for prerequisites
such as usage type and context
mapping details.
Evaluate a procedure plan
definition based on the name
/connect/procedure-plan-definitions/evaluate/procedurePlanDefinitionName
(POST)
of a definition to check for
prerequisites such as usage type
and context mapping details.
Create records of a procedure
plan version with details.
/connect/procedure-plan-definitions/procedurePlanDefinitionId/version
(POST)
Get, update, or delete a
procedure plan definition
/connect/procedure-plan-definitions/versions/procedurePlanVersionId
(GET, PATCH, DELETE)
version record by using the
record ID.
668
Salesforce Pricing Business APIsSalesforce Pricing

===== PAGE 683 =====

Resources
Learn more about the available Salesforce Pricing resources.
Request Bodies
Learn more about the available Salesforce Pricing API request bodies.
Response Bodies
Learn more about the available Salesforce Pricing API response bodies.
SEE ALSO:
Connect REST API Developer Guide: Introduction
Resources
Learn more about the available Salesforce Pricing resources.
PBE Derived Pricing (POST)
Get the source product for the Price Book Entry (PBE) derived pricing.
Price Context (POST)
Perform a pricing request by using the instance ID of a context.
Pricing (POST)
Create and hydrate context instance in a single request. Provide a comprehensive response that contains final pricing details per
line items and related errors, if any.
API Execution Logs (GET)
Get the log details of a pricing API execution record by using the execution ID.
Pricing Process Execution (GET)
Get the execution details of a pricing process by using the execution ID.
Pricing Process Execution for Line Items (GET)
Get the pricing execution details for the line items of a pricing process by using the execution ID and execution type.
Pricing Data Sync (GET)
Sync pricing data to ensure that the lookup tables contain the latest pricing data.
Pricing Recipe (GET)
Get the mapping details of pricing recipes to the associated pricing recipe table.
Pricing Recipe Mapping (POST)
Create a mapping between the pricing recipe and the Decision Tables. Post recipes with lookup tables or procedures.
Pricing Versioned Revision Details (POST)
Create revisions of a pricing request with versions for adjustment entities.
Pricing Waterfall (GET)
Get the persisted price waterfall that stores the process logs. Price waterfall provides insights into every step of the pricing process.
Pricing Waterfall (POST)
Create a log of price waterfall. Price waterfall provides insights into every step of the pricing process.
Procedure Plan Definitions (GET, POST)
Get the records of procedure plan definitions. Additionally, create a record of a procedure plan definition.
669
ResourcesSalesforce Pricing

===== PAGE 684 =====

Procedure Plan Definition By ID (GET, PATCH, DELETE)
Get, update, or delete a procedure plan definition record by using the record ID.
Procedure Plan Evaluation By Object (POST)
Evaluate a procedure plan definition based on a primary object to check for prerequisites such as usage type and context mapping
details.
Procedure Plan Evaluation By Definition Name (POST)
Evaluate a procedure plan definition based on the name of a definition to check for prerequisites such as usage type and context
mapping details.
Procedure Plan Version (POST)
Create records of a procedure plan version with details.
Procedure Plan Version Details (GET, PATCH, DELETE)
Get, update, or delete a procedure plan definition version record by using the record ID.
Pricing Simulation Input Variables With Data (GET)
Get details of the pricing simulation input variables along with associated data.
PBE Derived Pricing (POST)
Get the source product for the Price Book Entry (PBE) derived pricing.
Resource
/connect/core-pricing/pbeDerivedPricingSourceProduct
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/pbeDerivedPricingSourceProduct
Available version
61.0
HTTP methods
POST
Request body for POST
JSON example
{
"productId":"01txx0000006i2SAAQ",
"pricebookEntryId":"01uxx0000008yYcAAI",
"effectiveFrom":"2020-01-01T22:53:20.000Z",
"effectiveTo":"2021-01-01T22:53:20.000Z"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0RequiredDate from when the price book entry is
effective.
Stringeffective
From
670
ResourcesSalesforce Pricing

===== PAGE 685 =====

Available
Version
Required or
Optional
DescriptionTypeName
61.0RequiredDate until when the price book entry is
effective.
StringeffectiveTo
61.0RequiredID of the price book entry.Stringpricebook
EntryId
61.0RequiredID of the price book.StringproductId
Response body for POST
PBE Derived Pricing
Price Context (POST)
Perform a pricing request by using the instance ID of a context.
If price waterfall is disabled from Salesforce Pricing Setup in your org, this API doesn't return the waterfall details. You can use the Price
Waterfall API to retrieve the waterfall details if price waterfall persistence is enabled in Salesforce Pricing Setup.
Resource
/connect/core-pricing/price-contexts/contextid
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/price-contexts/0U3RM00000000SR0AY
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"configurationOverrides": {
"skipWaterfall": true,
"useSessionScopedContext": true,
"persistContext": true,
"taggedData": false
}
"procedureName": "ES1"
}
671
ResourcesSalesforce Pricing

===== PAGE 686 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalParameters to override pricing
configuration.
Configuration
Override Input
configuration
Overrides
60.0OptionalName of the pricing procedure.Stringprocedure
Name
Response body for POST
Pricing Response
Pricing (POST)
Create and hydrate context instance in a single request. Provide a comprehensive response that contains final pricing details per line
items and related errors, if any.
If price waterfall is disabled from Salesforce Pricing Setup in your org, this API doesn't return the waterfall details. You can use the Price
Waterfall API to retrieve the waterfall details if price waterfall persistence is enabled in Salesforce Pricing Setup.
Resource
/connect/core-pricing/pricing
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/pricing
Available version
60.0
Requires Chatter
No
HTTP methods
POST
Request body for POST
JSON example
{
"contextDefinitionId": "11Oxx0000006PdxEAE",
"contextMappingId": "11jxx0000004LDDAA2",
"jsonDataString": {
"Cart": [
{
"id": "cart_1001",
"cart_id": "cart_1001",
"PriceBookId": "PriceBookId_1001",
"businessObjectType": "Cart",
"CartItem": [
{
"id": "lineItem_1001",
672
ResourcesSalesforce Pricing

===== PAGE 687 =====

"line_item_id": "lineItem_1001",
"Quantity": 7,
"PriceType": "OneTime",
"Frequency": "",
"UOM": "",
"businessObjectType": "CartItem",
"product_id": "01txx0000006i44AAA",
"UnitPrice": 6.8,
"NetUnitPrice": 0,
"Attribute": [
{
"name": "Color",
"code": "RED",
"isPriceImpacting": true,
"businessObjectType": "Attribute",
"id": "Attribute_1001",
"attribute_id": "Attribute_1001"
},
{
"name": "Size",
"code": "10INCH",
"isPriceImpacting": true,
"businessObjectType": "Attribute",
"id": "Attribute_1002",
"attribute_id": "Attribute_1002"
}
]
},
{
"id": "lineItem_1002",
"line_item_id": "lineItem_1002",
"quantity": 3,
"PriceType": "OneTime",
"Frequency": "",
"UOM": "",
"businessObjectType": "CartItem",
"product_id": "01txx0000006i2SAAQ",
"unitprice": 6,
"NetUnitPrice": 0,
"Attribute": [
{
"name": "Color",
"code": "BLUE",
"isPriceImpacting": true,
"businessObjectType": "Attribute",
"id": "Attribute_1003",
"attribute_id": "Attribute_1003"
},
{
"name": "Size",
"code": "6INCH",
"isPriceImpacting": true,
"businessObjectType": "Attribute",
"id": "Attribute_1004",
673
ResourcesSalesforce Pricing

===== PAGE 688 =====

"attribute_id": "Attribute_1004"
}
]
}
]
}
]
},
"pricingProcedureId": "9QMxx0000004CKKGA2",
"configurationOverrides": {
"skipWaterfall": true,
"useSessionScopedContext": true,
"persistContext": true,
"referenceKey": "referenceKey-12345",
"displayContext" : false,
"taggedData": false,
"isHighVolumeLineItems": false
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalParameters to override the pricing
configuration.
Configuration Override
Input
configuration
Overrides
60.0RequiredID of the context definition that
defines the structure of the input
data.
Stringcontext
DefinitionId
60.0RequiredID of the context mapping that
maps the input data to the context
instance.
Stringcontext
MappingId
60.0RequiredData to hydrate the context, which
must be in JSON format and
StringjsonData
String
passed as String. Pass the JSON
data as String by using the
stringify() method to convert the
object to string.
The keys in the
jsonDataString  property
must be in accordance to the
contextMappingId property
sent in the request.
60.0OptionalID or API name of the pricing
procedure used for calculating the
Stringpricing
ProcedureId
prices. A pricing procedure is
674
ResourcesSalesforce Pricing

===== PAGE 689 =====

Available
Version
Required or
Optional
DescriptionTypeName
represented as an Expression Set
Definition in the system.
If you’re an Experience Cloud user,
specify the name of the pricing
procedure.
Response body for POST
Pricing Output
API Execution Logs (GET)
Get the log details of a pricing API execution record by using the execution ID.
Resource
/connect/core-pricing/apiexecutionlogs/executionId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/apiexecutionlogs/29646938297972
Available version
63.0
HTTP methods
GET
Path parameter for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0RequiredID of the pricing process execution record.StringexecutionId
Response body for GET
Pricing Execution Waterfall Response
Pricing Process Execution (GET)
Get the execution details of a pricing process by using the execution ID.
Resource
/connect/core-pricing/pricing-process-execution/executionId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/pricing-process-execution/29646938297972
675
ResourcesSalesforce Pricing

===== PAGE 690 =====

Available version
63.0
HTTP methods
GET
Path parameter for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0RequiredID of the pricing process execution record.
The ID is generated each time a pricing
process is executed.
StringexecutionId
Query parameter for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0OptionalType of execution that's defined internally
within the pricing API.
Valid values are:
StringexecutionType
• API_Execution
• Discovery—Discovery procedure
• Discovery_Line—Discovery
procedure for the line items.
• Pricing—Pricing procedure
• Pricing_Line—Pricing
procedure for the line items.
If the executionType parameter isn't
specified, the API retrieves records for all
the execution types that are associated
with the specified execution ID.
Response body for GET
Pricing Process Execution Response
Pricing Process Execution for Line Items (GET)
Get the pricing execution details for the line items of a pricing process by using the execution ID and execution type.
Resource
/connect/core-pricing/pricing-process-execution/lineitems/executionId/executionType
676
ResourcesSalesforce Pricing

===== PAGE 691 =====

Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/pricing-process-execution/lineitems/29646938297972/Pricing_Line
Available version
63.0
HTTP methods
GET
Path parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0RequiredID of the pricing process execution record.StringexecutionId
63.0RequiredType of the execution that's defined
internally within the pricing API. Valid
values are:
StringexecutionType
• Pricing_Line
• Discovery_Line
Response body for GET
Pricing Process Execution Details for Line Items
Pricing Data Sync (GET)
Sync pricing data to ensure that the lookup tables contain the latest pricing data.
To partially synchronize pricing data, use the Decision Table Refresh Action in a Flow. See Decision Table Refresh Action.
Resource
/connect/core-pricing/sync/pricingSyncOrigin
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/sync/syncData
Available version
60.0
HTTP methods
GET
Response body for GET
Pricing Generic Response
Pricing Recipe (GET)
Get the mapping details of pricing recipes to the associated pricing recipe table.
677
ResourcesSalesforce Pricing

===== PAGE 692 =====

Resource
/connect/core-pricing/recipe
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/recipe
Available version
60.0
HTTP methods
GET
Response body for GET
Pricing Recipe Response
Pricing Recipe Mapping (POST)
Create a mapping between the pricing recipe and the Decision Tables. Post recipes with lookup tables or procedures.
Resource
/connect/core-pricing/recipe/mapping
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/recipe/mapping
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"recipeId" : "12Gxx0000005J9MEAU",
"pricingRecipeLookUpTableInputRepresentations": [
{
lookupId: “12Gxx0000005J9MEAU”,
pricingComponentType: “CustomDiscount”
},
{
lookupId: “12Gxx0000005J9MEAU”,
pricingComponentType: “CustomDiscount”
}
],
"pricingRecipeProcedureInputRepresentation" : {
"procedureId" : "9QLxx0000004C92GAE"
}
}
678
ResourcesSalesforce Pricing

===== PAGE 693 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredInput representation of the recipe
mapping.
Pricing Recipe
LookUp Table
Input[]
pricing
RecipeLookUp
TableInput
Representations
60.0RequiredInput representation of the procedure
that’s used in the pricing recipe.
Pricing Recipe
Procedure Input
pricing
Recipe
Procedure
Input
Representation
60.0RequiredID of the pricing recipe.StringrecipeId
Response body for POST
Pricing Recipe Post
Pricing Versioned Revision Details (POST)
Create revisions of a pricing request with versions for adjustment entities.
Resource
/connect/core-pricing/versioned-revise-details
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/versioned-revise-details
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
This example shows the input for versioned revision details for attribute-based adjustment.
{
"entityName":"AttributeBasedAdjustment",
"id":"entityId",
"priceAdjustmentId":"priceAdjustmentScheduleId",
"productId":"ProductId",
"productSellingModelId":"PsmId",
"adjustmentType":"AdjustmentType",
"adjustmentValue":"AdjustmentValue(Numeric)"",
"effectiveFrom":"EffectiveFrom date",
679
ResourcesSalesforce Pricing

===== PAGE 694 =====

"effectiveTo":"EffectiveTo Date",
"additionalFieldsToValueMap":{
"attributeBasedAdjRuleId":"AttributeBasedAdjRuleId"
}
}
This example shows the input for versioned revision details for bundle-based adjustment.
{
"entityName": "BundleBasedAdjustment",
"id": "entityId",
"priceAdjustmentScheduleId": "priceAdjustmentScheduleId",
"productId": "ProductId",
"productSellingModelId": "PsmId",
"adjustmentType": "AdjustmentType",
"adjustmentValue": "AdjustmentValue(Numeric)",
"effectiveFrom":"EffectiveFrom date",
"effectiveTo":"EffectiveTo Date",
"additionalFieldsToValueMap": {
"rootBundleId": "RootBundleId",
"parentProductId": "ParentProductId"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalMap containing the additional fields
specific to the entity.
Map<String,
String>
additional
Fields
ToValueMap
60.0RequiredAdjustment type such as, percentage,
amount, or override.
Stringadjustment
Type
60.0RequiredValue for the adjustment.Stringadjustment
Value
60.0RequiredDate from when the adjustment is
effective.
Stringeffective
From
60.0OptionalDate until when the adjustment is
effective.
StringeffectiveTo
60.0RequiredName of the entity such as
AttributeBasedAdjustment entity or
BundleBasedAdjustment entity.
StringentityName
60.0RequiredID of the record.Stringid
60.0RequiredID of the price adjustment schedule
record.
Stringprice
Adjustment
ScheduleId
680
ResourcesSalesforce Pricing

===== PAGE 695 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredProduct ID of the record.StringproductId
60.0OptionalProduct selling model ID associated to
the record.
Stringproduct
Selling
ModelId
Response body for POST
Pricing Versioned Revision Details
Pricing Waterfall (GET)
Get the persisted price waterfall that stores the process logs. Price waterfall provides insights into every step of the pricing process.
If price waterfall persistence is disabled from Salesforce Pricing Setup in your org, this API doesn't return the waterfall details. You can
view the waterfall details in the Pricing API or Price Context API response if price waterfall is enabled in Salesforce Pricing Setup.
Advanced Price Logs
You can set up advanced price logs to capture exception details for complex pricing elements. The API response captures input and
output values to trace any exceptions. Refer to the diagnostic data available in the price waterfall details to identify and fix performance
issues. See Advanced Price Logs.
Resource
/connect/core-pricing/waterfall/lineItemId/executionId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/waterfall/Gold/2yHdNNEFOZr9jAe4gHS7?tagsToFilter=UnitPrice
Available version
60.0
HTTP methods
GET
Query parameters
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalComma-separated tags to filter.StringtagsToFilter
62.0OptionalUsage type of the waterfall log record.
Valid values are:
StringusageType
• Pricing
• Discovery
• Rating—Specifies that the record
type is Rating. If this value is
681
ResourcesSalesforce Pricing

===== PAGE 696 =====

Available
Version
Required or
Optional
DescriptionTypeName
specified, the API creates a log of
rating waterfall. See Rating Waterfall.
The default value is Pricing.
Response body for GET
Line Item Waterfall Response
Pricing Waterfall (POST)
Create a log of price waterfall. Price waterfall provides insights into every step of the pricing process.
Resource
/connect/core-pricing/waterfall
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/waterfall
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"currencyCode": "USD",
"executionEndTimestamp": "2023-07-31T20:11:29.625Z",
"executionId": "executionId1",
"executionStartTimestamp": null,
"lineItemId": "item1",
"output": {
"Subtotal": 38.25,
"ListPrice": 10,
"NetUnitPrice": 7.65
},
"waterfall": [{
"fieldToTagNameMapping": {
"Product2Id": "ItemProduct",
"Subtotal": "Subtotal",
"Pricebook2Id": "Pricebook",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionSource",
"ListPrice": "ItemListPrice"
},
"inputParameters": {
682
ResourcesSalesforce Pricing

===== PAGE 697 =====

"Product2Id": "01txx0000006i44AAA",
"Pricebook2Id": "01sxx0000005q9xAAA",
"Quantity": 5,
"LineItemId": "item1"
},
"outputParameters": {
"Subtotal": 50,
"ListPrice": 10
},
"pricingElement": {
"adjustments": [{
"AdjustmentValue": "95.00",
"AdjustmentType": "Amount"
}],
"description": null,
"elementType": "ListPrice",
"name": "List Price"
},
"sequence": 1
},
{
"fieldToTagNameMapping": {
"PriceAdjustmentScheduleId": "ItemDescription",
"NetUnitPrice": "ItemNetUnitPrice",
"Product2Id": "ItemProduct",
"LowerBound": "ItemQuantity",
"UpperBound": "ItemQuantity",
"Subtotal": "Subtotal",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionSource",
"InputUnitPrice": "ItemListPrice"
},
"inputParameters": {
"PriceAdjustmentScheduleId": "84Xxx0000004CGSEA2",
"Product2Id": "01txx0000006i44AAA",
"LowerBound": 5,
"UpperBound": 5,
"Quantity": 5,
"LineItemId": "item1",
"InputUnitPrice": 10
},
"outputParameters": {
"NetUnitPrice": 8.5,
"Subtotal": 42.5
},
"pricingElement": {
"adjustments": [{
"AdjustmentValue": "15.00",
"AdjustmentType": "Percentage"
}],
"description": null,
"elementType": "VolumeDiscount",
"name": "Volume Discount"
},
683
ResourcesSalesforce Pricing

===== PAGE 698 =====

"sequence": 2
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalContext definition version ID of the
pricing procedure.
Stringcontext
Definition
VersionId
60.0OptionalContext mapping ID of the pricing
procedure.
Stringcontext
MappingId
60.0OptionalCurrency code such as, USD or INR.StringcurrencyCode
60.0OptionalEnd timestamp of procedure execution.StringexecutionEnd
Timestamp
60.0RequiredExecution ID for a particular execution of
a pricing procedure.
StringexecutionId
60.0OptionalStart timestamp of procedure execution.Stringexecution
Start
Timestamp
60.0RequiredLine item ID for which the price is being
calculated.
StringlineItemId
60.0OptionalOutput of the pricing procedure.Map<String,
Object>
output
60.0RequiredDetails of the pricing waterfall.Pricing Waterfall
Input[]
waterfall
Response body for POST
Pricing Generic Response
Procedure Plan Definitions (GET, POST)
Get the records of procedure plan definitions. Additionally, create a record of a procedure plan definition.
Resource
/connect/procedure-plan-definitions
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/
procedure-plan-definitions?isTemplate=true
684
ResourcesSalesforce Pricing

===== PAGE 699 =====

Available version
62.0
HTTP methods
GET, POST
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
62.0OptionalIndicates whether to return a list of
file-based definitions (true) or not
BooleanisTemplate
(false). This API request returns a list of
database-based definitions, by default.
Response body for GET
Procedure Plan Definitions
Request body for POST
JSON example
This example shows a sample request to create a procedure plan definition record by using the Procedure Plan Definitions (POST)
API.
{
"description": "Definition for Quote",
"developerName": "Quote_Definition_Sample",
"name": "Quote_Definition_Sample",
"processType": "Default",
"primaryObject": "BusinessHours",
"procedurePlanDefinitionVersions": [
{
"active": false,
"contextDefinition": "SalesTransactionContext__stdctx",
"readContextMapping": "QuoteEntitiesMapping",
"saveContextMapping": "QuoteEntitiesMapping",
"effectiveFrom": "2024-07-15T10:15:30.000Z",
"developerName": "Quote_Definition_V1",
"rank": 1
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalDescription of the procedure plan
definition.
Stringdescription
62.0Required if you’re
invoking the
Developer name of the procedure plan
definition.
Stringdeveloper
Name
685
ResourcesSalesforce Pricing

===== PAGE 700 =====

Available
Version
Required or
Optional
DescriptionTypeName
Procedure Plan
Definitions API
(POST).
62.0OptionalName of the procedure plan definition.Stringname
62.0Required if you’re
invoking the
Source object that’s used to create a
procedure with rule-based criteria. This
Stringprimary
Object
Procedure Planproperty value must be a valid object
Definitions APIname and must be unique in the
ProcedurePlanDefinition object. (POST) and if you’re
creating a
procedure with
rule-based criteria.
62.0RequiredList of versions of a procedure plan
definition.
Procedure Plan
Definition Version
Input[]
procedurePlan
Definition
Versions
63.0RequiredSpecifies the business processes that
need a procedure plan for each sObject
and definition. Valid values are:
StringprocessType
• Billing
• DRO
• DeepClone
• ProductDiscovery
• Revenue Cloud
These values can be used based on the
available license. If unspecified, the value
is set to Default.
62.0Required if you’re
invoking the
ID of the procedure plan definition
record.
StringrecordId
Procedure Plan
Definition By ID API
(PATCH).
Response body for POST
Procedure Plan Generic
Procedure Plan Definition By ID (GET, PATCH, DELETE)
Get, update, or delete a procedure plan definition record by using the record ID.
686
ResourcesSalesforce Pricing

===== PAGE 701 =====

Resource
/connect/procedure-plan-definitions/procedurePlanDefinitionId
The procedurePlanDefinitionId  property value is the ID or name of the procedure plan definition record to perform the
request for.
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/procedure-plan-definitions/1FNxx0000004EsOGAU
Available version
62.0
HTTP methods
DELETE, GET, PATCH
You can delete a procedure plan definition only if it doesn’t include any active procedure plan version.
Response body for GET
Procedure Plan Definition
Request body for PATCH
JSON example
This example shows a sample request to update a procedure plan definition by using the Procedure Plan Definition By ID (PATCH)
API.
Note:  The properties that aren’t specified in the input are deleted when updating the record.
{
"description": "Default definition patch update",
"developerName": "Quote_Definition",
"name": "Quote_Definition",
"primaryObject": "Quote",
"recordId": "1FNxx0000004EsOGAU"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalDescription of the procedure plan
definition.
Stringdescription
62.0Required if you’re
invoking the
Developer name of the procedure plan
definition.
Stringdeveloper
Name
Procedure Plan
Definitions API
(POST).
62.0OptionalName of the procedure plan definition.Stringname
62.0Required if you’re
invoking the
Source object that’s used to create a
procedure with rule-based criteria. This
Stringprimary
Object
Procedure Planproperty value must be a valid object
Definitions API
687
ResourcesSalesforce Pricing

===== PAGE 702 =====

Available
Version
Required or
Optional
DescriptionTypeName
(POST) and if you’re
creating a
name and must be unique in the
ProcedurePlanDefinition object.
procedure with
rule-based criteria.
62.0RequiredList of versions of a procedure plan
definition.
Procedure Plan
Definition Version
Input[]
procedurePlan
Definition
Versions
63.0RequiredSpecifies the business processes that
need a procedure plan for each sObject
and definition. Valid values are:
StringprocessType
• Billing
• DRO
• DeepClone
• ProductDiscovery
• Revenue Cloud
These values can be used based on the
available license. If unspecified, the value
is set to Default.
62.0Required if you’re
invoking the
ID of the procedure plan definition
record.
StringrecordId
Procedure Plan
Definition By ID API
(PATCH).
Response body for PATCH
Procedure Plan Definition
Procedure Plan Evaluation By Object (POST)
Evaluate a procedure plan definition based on a primary object to check for prerequisites such as usage type and context mapping
details.
Resource
/connect/procedure-plan-definitions/evaluate
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/
procedure-plan-definitions/evaluate
Available version
62.0
688
ResourcesSalesforce Pricing

===== PAGE 703 =====

HTTP methods
POST
Request body for POST
JSON example
This example shows a sample request to evaluate a procedure plan definition by using a primary object.
{
"idList": ["a01DU000000BylcYAC"],
"evaluationDate": "2024-07-08T10:15:30.000Z",
"processType": "Default",
"sectionType": ["PricingProcedure"],
"subSectionType": ["Revenue"]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredDate when the evaluation is applicable.
This property value must be within the
StringevaluationDate
date range when the procedure plan
definition is effective.
62.0Required only if
you’re invoking the
List of record IDs of the procedure plan
definitions to be evaluated.
String[]idList
Procedure Plan
Evaluation By
Object (POST) API.
63.0OptionalSpecifies the business processes that
need a procedure plan for each sObject
StringprocessType
and definition. Valid values based on the
available are:
• Billing
• DRO
• DeepClone
• ProductDiscovery
• Revenue Cloud
These values can be used based on the
available license. If unspecified, the value
is set to Default.
If a procedure plan definition exist in the
org with processType  value as
null, modify the value to Default.
689
ResourcesSalesforce Pricing

===== PAGE 704 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalName of section to be evaluated. Valid
values are:
String[]sectionType
• PricingProcedure
• ProductDiscoveryProcedure
• ProductQualificationProcedure
• PricingDiscoveryProcedure
• DiscountSpreadServiceProcedure
• RatingProcedure
• Custom
• RatingDiscoveryProcedure
62.0OptionalName of subsection to be evaluated.String[]subSectionType
The combination of the sectionType  and subSectionType  property values must be unique for every procedure plan
version.
Response body for POST
Procedure Plan Evaluation Response
Procedure Plan Evaluation By Definition Name (POST)
Evaluate a procedure plan definition based on the name of a definition to check for prerequisites such as usage type and context mapping
details.
Resource
/connect/procedure-plan-definitions/evaluate/procedurePlanDefinitionName
Resource example
https://yourInstance.salesforce.com/services/data
/v66.0/connect/procedure-plan-definitions/evaluate/Sample_Definition
Available version
62.0
HTTP methods
POST
Request body for POST
JSON example
This example shows a sample request to evaluate a procedure plan definition by using a definition name.
{
"evaluationDate": "2024-07-08T10:15:30.000Z",
"processType": "Default",
"sectionType": ["PricingProcedure"],
690
ResourcesSalesforce Pricing

===== PAGE 705 =====

"subSectionType": ["Revenue"]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredDate when the evaluation is applicable.
This property value must be within the
StringevaluationDate
date range when the procedure plan
definition is effective.
62.0Required only if
you’re invoking the
List of record IDs of the procedure plan
definitions to be evaluated.
String[]idList
Procedure Plan
Evaluation By
Object (POST) API.
63.0OptionalSpecifies the business processes that
need a procedure plan for each sObject
StringprocessType
and definition. Valid values based on the
available are:
• Billing
• DRO
• DeepClone
• ProductDiscovery
• Revenue Cloud
These values can be used based on the
available license. If unspecified, the value
is set to Default.
If a procedure plan definition exist in the
org with processType  value as
null, modify the value to Default.
62.0OptionalName of section to be evaluated. Valid
values are:
String[]sectionType
• PricingProcedure
• ProductDiscoveryProcedure
• ProductQualificationProcedure
• PricingDiscoveryProcedure
• DiscountSpreadServiceProcedure
• RatingProcedure
• Custom
• RatingDiscoveryProcedure
62.0OptionalName of subsection to be evaluated.String[]subSectionType
691
ResourcesSalesforce Pricing

===== PAGE 706 =====

The combination of the sectionType  and subSectionType  property values must be unique for every procedure plan
version.
Response body for POST
Procedure Plan Evaluation Response
Procedure Plan Version (POST)
Create records of a procedure plan version with details.
Resource
/connect/procedure-plan-definitions/procedurePlanDefinitionId/version
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/
procedure-plan-definitions/1FNxx0000004EsOGAU/version
Available version
62.0
HTTP methods
POST
Request body for POST
JSON example
{
"active": false,
"developerName": "sample_version_input",
"effectiveFrom": "2024-07-09T00:00:00.000Z",
"contextDefinition": "SalesTransactionContext__stdctx",
"procedurePlanSections": [
{
"isInherited": false,
"procedurePlanOptions": [
{
"saveContextMapping": "AssetToSalesTransactionMapping",
"expressionSetDefinition": "9QAZ60000004ECOOA2",
"expressionSetLabel": "Revenue_Default_Pricing_Procedure",
"expressionSetApiName": "Revenue Default Pricing Procedure",
"logic": "1 AND 2 AND 3",
"priority": 1,
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"literalValue": "test",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 2,
"fieldObject": "BillingPostalCode",
692
ResourcesSalesforce Pricing

===== PAGE 707 =====

"fieldPath": "BillingPostalCode",
"literalValue": "sample",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 3,
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"literalValue": "2024-07-14",
"operator": "LessThan",
"dataType": "Date"
}
]
}
],
"resolutionType": "RuleBased",
"sectionType": "PricingProcedure",
"sequence": 1,
"subSectionType": "PricingProcedure",
"recordId": "1FRZ60000008OIAOA2"
}
],
"rank": 1,
"readContextMapping": "ProductDiscoveryContextMapping",
"saveContextMapping": "OrderEntitiesMapping"
}
Note:  The properties that aren’t specified in the input are deleted when updating the record.
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIndicates whether this procedure plan
definition version is active (true) or not
Booleanactive
(false). You can’t edit or delete a
procedure plan version that’s in the active
state.
62.0RequiredContext definition that’s associated with
the procedure plan definition version
record.
Stringcontext
Definition
62.0RequiredUnique developer name of the procedure
plan definition version.
Stringdeveloper
Name
62.0RequiredDate and time from when the procedure
plan definition version comes into effect.
Stringeffective
From
62.0RequiredDate and time from when the procedure
plan definition version is no longer in
effect.
StringeffectiveTo
693
ResourcesSalesforce Pricing

===== PAGE 708 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0This property is
read-only.
Template this procedure plan definition
version is created from.
Stringinherited
From
62.0RequiredProcedure setup sections for a procedure
plan definition. Each section enables the
Procedure Plan
Section Input[]
procedure
PlanSections
setup of a procedure type by using a
rule-based criteria.
Keep these considerations in mind when
you modify this property.
• You can edit or delete a procedure
plan section if it isn’t associated with
an active procedure plan version.
• You can create a procedure plan
section with rule-based resolution
type if the primary object isn’t empty
in the definition.
62.0RequiredCurrent rank of the procedure plan
definition version that’s used to decide
Integerrank
the sequence of execution of a procedure
plan definition version.
62.0OptionalMapping that’s used to read data from
the mapped object and populate the
context definition.
StringreadContext
Mapping
This property value must be associated
with a context definition.
62.0RequiredID of the procedure plan definition
version record.
StringrecordId
62.0OptionalMapping that’s used to save data from
the context definition and populate the
mapped object.
StringsaveContext
Mapping
This property value must be associated
with a context definition.
62.0OptionalStatus of the procedure plan definition
version record.
Stringstatus
Response body for POST
Procedure Plan Generic
694
ResourcesSalesforce Pricing

===== PAGE 709 =====

Procedure Plan Version Details (GET, PATCH, DELETE)
Get, update, or delete a procedure plan definition version record by using the record ID.
Resource
/connect/procedure-plan-definitions/versions/procedurePlanVersionId
The procedurePlanVersionId  property value is the ID or name of the procedure plan version record to perform the request
for.
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/
procedure-plan-definitions/versions/1Cvxx0000004E1ACAU
Available version
62.0
HTTP methods
DELETE, GET, PATCH
You can’t delete a procedure plan version if it’s the only procedure plan version in a procedure plan definition.
Response body for GET
Procedure Plan Definition Version
Request body for PATCH
JSON example
{
"active": false,
"developerName": "sample_version_input",
"effectiveFrom": "2024-07-09T00:00:00.000Z",
"contextDefinition": "SalesTransactionContext__stdctx",
"procedurePlanSections": [
{
"isInherited": false,
"procedurePlanOptions": [
{
"saveContextMapping": "AssetToSalesTransactionMapping",
"expressionSetDefinition": "9QAZ60000004ECOOA2",
"expressionSetLabel": "Revenue_Default_Pricing_Procedure",
"expressionSetApiName": "Revenue Default Pricing Procedure",
"logic": "1 AND 2 AND 3",
"priority": 1,
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"literalValue": "test",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 2,
"fieldObject": "BillingPostalCode",
695
ResourcesSalesforce Pricing

===== PAGE 710 =====

"fieldPath": "BillingPostalCode",
"literalValue": "sample",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 3,
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"literalValue": "2024-07-14",
"operator": "LessThan",
"dataType": "Date"
}
]
}
],
"resolutionType": "RuleBased",
"sectionType": "PricingProcedure",
"sequence": 1,
"subSectionType": "PricingProcedure",
"recordId": "1FRZ60000008OIAOA2"
}
],
"rank": 1,
"readContextMapping": "ProductDiscoveryContextMapping",
"saveContextMapping": "OrderEntitiesMapping"
}
Note:  The properties that aren’t specified in the input are deleted when updating the record.
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIndicates whether this procedure plan
definition version is active (true) or not
Booleanactive
(false). You can’t edit or delete a
procedure plan version that’s in the active
state.
62.0RequiredContext definition that’s associated with
the procedure plan definition version
record.
Stringcontext
Definition
62.0RequiredUnique developer name of the procedure
plan definition version.
Stringdeveloper
Name
62.0RequiredDate and time from when the procedure
plan definition version comes into effect.
Stringeffective
From
62.0RequiredDate and time from when the procedure
plan definition version is no longer in
effect.
StringeffectiveTo
696
ResourcesSalesforce Pricing

===== PAGE 711 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0This property is
read-only.
Template this procedure plan definition
version is created from.
Stringinherited
From
62.0RequiredProcedure setup sections for a procedure
plan definition. Each section enables the
Procedure Plan
Section Input[]
procedure
PlanSections
setup of a procedure type by using a
rule-based criteria.
Keep these considerations in mind when
you modify this property.
• You can edit or delete a procedure
plan section if it isn’t associated with
an active procedure plan version.
• You can create a procedure plan
section with rule-based resolution
type if the primary object isn’t empty
in the definition.
62.0RequiredCurrent rank of the procedure plan
definition version that’s used to decide
Integerrank
the sequence of execution of a procedure
plan definition version.
62.0OptionalMapping that’s used to read data from
the mapped object and populate the
context definition.
StringreadContext
Mapping
This property value must be associated
with a context definition.
62.0RequiredID of the procedure plan definition
version record.
StringrecordId
62.0OptionalMapping that’s used to save data from
the context definition and populate the
mapped object.
StringsaveContext
Mapping
This property value must be associated
with a context definition.
62.0OptionalStatus of the procedure plan definition
version record.
Stringstatus
Response body for PATCH
Procedure Plan Generic
697
ResourcesSalesforce Pricing

===== PAGE 712 =====

Pricing Simulation Input Variables With Data (GET)
Get details of the pricing simulation input variables along with associated data.
Resource
/connect/core-pricing/simulationInputVariablesWithData
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/simulationInputVariablesWithData?expressionSetVersionId=9QMxx0000004CDsGAM&entityId=0Q0xx0000004C92CAE&contextDefinitionId=SalesTransactionContext__stdctx&contextMappingId=QuoteEntitiesMapping
Available version
64.0
HTTP methods
GET
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
64.0RequiredID or developer name of the context
definition.
Stringcontext
DefinitionId
64.0RequiredID or name of the context mapping that's
used.
StringcontextMapping
Id
64.0RequiredID of a quote or an order.StringentityId
64.0RequiredID of the expression set that starts with
9QM.
StringexpressionSet
VersionId
Response body for GET
Pricing Simulation Input Variables With Data
Request Bodies
Learn more about the available Salesforce Pricing API request bodies.
Adjustment Details Input
Input representation of the adjustment details.
Configuration Override Input
Input representation of the details to override for a Pricing API configuration.
PBE Derived Pricing Input
Input representation of the request to get the source product for the Price Book Entry (PBE) derived pricing.
Pricing Input
Input representation of the details of a Pricing API request.
Pricing Recipe Input
Input representation to set up a pricing recipe page.
698
Request BodiesSalesforce Pricing

===== PAGE 713 =====

Pricing Recipe LookUp Table Input
Input representation of the lookup tables for the setup page recipe.
Pricing Recipe Procedure Input
Input representation of the procedure for the setup page recipe.
Pricing Request Input
Input representation of a pricing request.
Pricing Versioned Revision Details Input
Input representation of the versioned revision details.
Pricing Waterfall Input
Input representation of the pricing waterfall details.
Pricing Waterfall Log Input
Input representation of the request to create an explainability action log.
Procedure Plan Criterion Input
Input representation of the details of a procedure plan criterion.
Procedure Plan Definition Input
Input representation of the details of a procedure plan definition.
Procedure Plan Definition Version Input
Input representation of the details of a procedure plan definition version.
Procedure Plan Evaluation Input
Input representation of the details used to evaluate a procedure plan definition.
Procedure Plan Section Input
Input representation of the details of a procedure plan section.
Procedure Plan Option Input
Input representation of the details of a procedure plan option.
Adjustment Details Input
Input representation of the adjustment details.
JSON example
"pricingElement": {
"adjustments": [{
"AdjustmentValue": "15.00",
"AdjustmentType": "Percentage"
}],
"description": null,
"elementType": "VolumeDiscount",
"name": "Volume Discount"
}
699
Request BodiesSalesforce Pricing

===== PAGE 714 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalDetails of the pricing element.Map<String,
Object>[]
adjustments
60.0OptionalDescription of the pricing element.Stringdescription
60.0OptionalType of the pricing element.StringelementType
60.0OptionalName of the pricing element.Stringname
Configuration Override Input
Input representation of the details to override for a Pricing API configuration.
JSON example
"configurationOverrides": {
"skipWaterfall": true,
"useSessionScopedContext": true,
"persistContext": true,
"referenceKey": "referenceKey-12345",
"displayContext" : false,
"taggedData": false,
"isHighVolumeLineItems": false
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalName of the discovery procedure to use
to fetch the details of assets.
Stringdiscovery
Procedure
61.0OptionalIndicates whether the context structure
for pricing must be displayed (true) or
not (false).
Booleandisplay
Context
63.0OptionalIndicates whether the pricing API returns
pricing details for more than 100 line items
(true) or not (false).
BooleanisHighVolume
LineItems
60.0OptionalIndicates whether the context must be
persisted as per the mapping (true) or
not (false).
Booleanpersist
Context
63.0OptionalReference ID that a consuming workstream
provides in the API to search for specific
logs in the Pricing Operations Console.
StringreferenceKey
700
Request BodiesSalesforce Pricing

===== PAGE 715 =====

Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalIndicates whether the discovery procedure
must be skipped (true) or not (false).
BooleanskipDiscovery
60.0OptionalIndicates whether the price waterfall must
be skipped in the output response (true)
or not (false).
BooleanskipWaterfall
60.0OptionalIndicates whether the JSON data string can
specify tags in the input instead of
attributes (true) or not (false).
BooleantaggedData
60.0OptionalIndicates whether a session scoped
context must be created (true) or
BooleanuseSession
ScopedContext
request scoped context (false). The
default is false.
PBE Derived Pricing Input
Input representation of the request to get the source product for the Price Book Entry (PBE) derived pricing.
JSON example
{
"productId":"01txx0000006i2SAAQ",
"pricebookEntryId":"01uxx0000008yYcAAI",
"effectiveFrom":"2020-01-01T22:53:20.000Z",
"effectiveTo":"2021-01-01T22:53:20.000Z"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0RequiredDate from when the price book entry is
effective.
StringeffectiveFrom
61.0RequiredDate until when the price book entry is
effective.
StringeffectiveTo
61.0RequiredID of the price book entry.Stringpricebook
EntryId
61.0RequiredID of the price book.StringproductId
Pricing Input
Input representation of the details of a Pricing API request.
701
Request BodiesSalesforce Pricing

===== PAGE 716 =====

JSON example
{
"contextDefinitionId": "11Oxx0000006PdxEAE",
"contextMappingId": "11jxx0000004LDDAA2",
"jsonDataString": {
"Cart": [
{
"id": "cart_1001",
"cart_id": "cart_1001",
"PriceBookId": "PriceBookId_1001",
"businessObjectType": "Cart",
"CartItem": [
{
"id": "lineItem_1001",
"line_item_id": "lineItem_1001",
"Quantity": 7,
"PriceType": "OneTime",
"Frequency": "",
"UOM": "",
"businessObjectType": "CartItem",
"product_id": "01txx0000006i44AAA",
"UnitPrice": 6.8,
"NetUnitPrice": 0,
"Attribute": [
{
"name": "Color",
"code": "RED",
"isPriceImpacting": true,
"businessObjectType": "Attribute",
"id": "Attribute_1001",
"attribute_id": "Attribute_1001"
},
{
"name": "Size",
"code": "10INCH",
"isPriceImpacting": true,
"businessObjectType": "Attribute",
"id": "Attribute_1002",
"attribute_id": "Attribute_1002"
}
]
},
{
"id": "lineItem_1002",
"line_item_id": "lineItem_1002",
"quantity": 3,
"PriceType": "OneTime",
"Frequency": "",
"UOM": "",
"businessObjectType": "CartItem",
"product_id": "01txx0000006i2SAAQ",
"unitprice": 6,
"NetUnitPrice": 0,
702
Request BodiesSalesforce Pricing

===== PAGE 717 =====

"Attribute": [
{
"name": "Color",
"code": "BLUE",
"isPriceImpacting": true,
"businessObjectType": "Attribute",
"id": "Attribute_1003",
"attribute_id": "Attribute_1003"
},
{
"name": "Size",
"code": "6INCH",
"isPriceImpacting": true,
"businessObjectType": "Attribute",
"id": "Attribute_1004",
"attribute_id": "Attribute_1004"
}
]
}
]
}
]
},
"pricingProcedureId": "9QMxx0000004CKKGA2",
"configurationOverrides": {
"skipWaterfall": true,
"useSessionScopedContext": true,
"persistContext": true,
"referenceKey": "referenceKey-12345",
"displayContext" : false,
"taggedData": false,
"isHighVolumeLineItems": false
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalParameters to override the pricing
configuration.
Configuration Override
Input
configuration
Overrides
60.0RequiredID of the context definition that
defines the structure of the input
data.
Stringcontext
DefinitionId
60.0RequiredID of the context mapping that
maps the input data to the context
instance.
Stringcontext
MappingId
60.0RequiredData to hydrate the context, which
must be in JSON format and passed
StringjsonData
String
as String. Pass the JSON data as
703
Request BodiesSalesforce Pricing

===== PAGE 718 =====

Available
Version
Required or
Optional
DescriptionTypeName
String by using the stringify()
method to convert the object to
string.
The keys in the
jsonDataString  property
must be in accordance to the
contextMappingId  property
sent in the request.
60.0OptionalID or API name of the pricing
procedure used for calculating the
Stringpricing
ProcedureId
prices. A pricing procedure is
represented as an Expression Set
Definition in the system.
If you’re an Experience Cloud user,
specify the name of the pricing
procedure.
Pricing Recipe Input
Input representation to set up a pricing recipe page.
JSON example
{
"recipeId" : "12Gxx0000005J9MEAU",
"pricingRecipeLookUpTableInputRepresentations": [
{
lookupId: “12Gxx0000005J9MEAU”,
pricingComponentType: “CustomDiscount”
},
{
lookupId: “12Gxx0000005J9MEAU”,
pricingComponentType: “CustomDiscount”
}
],
"pricingRecipeProcedureInputRepresentation" : {
"procedureId" : "9QLxx0000004C92GAE"
}
}
704
Request BodiesSalesforce Pricing

===== PAGE 719 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredInput representation of the recipe
mapping.
Pricing Recipe
LookUp Table
Input[]
pricing
RecipeLookUp
TableInput
Representations
60.0RequiredInput representation of the procedure
that’s used in the pricing recipe.
Pricing Recipe
Procedure Input
pricingRecipe
Procedure
Input
Representation
60.0RequiredID of the pricing recipe.StringrecipeId
Pricing Recipe LookUp Table Input
Input representation of the lookup tables for the setup page recipe.
JSON example
"pricingRecipeLookUpTableInputRepresentations": [
{
lookupId: “12Gxx0000005J9MEAU”,
pricingComponentType: “CustomDiscount”
},
{
lookupId: “12Gxx0000005J9MEAU”,
pricingComponentType: “CustomDiscount”
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalID of the decision table.StringlookupTableId
60.0OptionalPricing component types such as volume
discount, custom discount, attribute-based
discount, and bundle-based discount.
Stringpricing
ComponentType
Pricing Recipe Procedure Input
Input representation of the procedure for the setup page recipe.
705
Request BodiesSalesforce Pricing

===== PAGE 720 =====

JSON example
"pricingRecipeProcedureInputRepresentation" : {
"procedureId" : "9QLxx0000004C92GAE"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredID of the expression set.StringprocedureId
Pricing Request Input
Input representation of a pricing request.
JSON example
{
"configurationOverrides": {
"skipWaterfall": true,
"useSessionScopedContext": true,
"persistContext": true,
"taggedData": false
}
"procedureName": "ES1"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalParameters to override pricing
configuration.
Configuration
Override Input
configuration
Overrides
60.0OptionalName of the pricing procedure.StringprocedureName
Pricing Versioned Revision Details Input
Input representation of the versioned revision details.
JSON example
This example shows the input for versioned revision details for attribute-based adjustment.
{
"entityName":"AttributeBasedAdjustment",
"id":"entityId",
"priceAdjustmentId":"priceAdjustmentScheduleId",
706
Request BodiesSalesforce Pricing

===== PAGE 721 =====

"productId":"ProductId",
"productSellingModelId":"PsmId",
"adjustmentType":"AdjustmentType",
"adjustmentValue":"AdjustmentValue(Numeric)"",
"effectiveFrom":"EffectiveFrom date",
"effectiveTo":"EffectiveTo Date",
"additionalFieldsToValueMap":{
"attributeBasedAdjRuleId":"AttributeBasedAdjRuleId"
}
}
This example shows the input for versioned revision details for bundle-based adjustment.
{
"entityName": "BundleBasedAdjustment",
"id": "entityId",
"priceAdjustmentScheduleId": "priceAdjustmentScheduleId",
"productId": "ProductId",
"productSellingModelId": "PsmId",
"adjustmentType": "AdjustmentType",
"adjustmentValue": "AdjustmentValue(Numeric)",
"effectiveFrom":"EffectiveFrom date",
"effectiveTo":"EffectiveTo Date",
"additionalFieldsToValueMap": {
"rootBundleId": "RootBundleId",
"parentProductId": "ParentProductId"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalMap containing the additional fields
specific to the entity.
Map<String,
String>
additional
FieldsToValue
Map
60.0RequiredAdjustment type such as, percentage,
amount, or override.
Stringadjustment
Type
60.0RequiredValue for the adjustment.Stringadjustment
Value
60.0RequiredDate from when the adjustment is
effective.
StringeffectiveFrom
60.0OptionalDate until when the adjustment is
effective.
StringeffectiveTo
60.0RequiredName of the entity such as
AttributeBasedAdjustment entity or
BundleBasedAdjustment entity.
StringentityName
707
Request BodiesSalesforce Pricing

===== PAGE 722 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredID of the record.Stringid
60.0RequiredID of the price adjustment schedule record.Stringprice
Adjustment
ScheduleId
60.0RequiredProduct ID of the record.StringproductId
60.0OptionalProduct selling model ID associated to the
record.
Stringproduct
Selling
ModelId
Pricing Waterfall Input
Input representation of the pricing waterfall details.
JSON example
"waterfall": [{
"fieldToTagNameMapping": {
"Product2Id": "ItemProduct",
"Subtotal": "Subtotal",
"Pricebook2Id": "Pricebook",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionSource",
"ListPrice": "ItemListPrice"
},
"inputParameters": {
"Product2Id": "01txx0000006i44AAA",
"Pricebook2Id": "01sxx0000005q9xAAA",
"Quantity": 5,
"LineItemId": "item1"
},
"outputParameters": {
"Subtotal": 50,
"ListPrice": 10
},
"pricingElement": {
"adjustments": [{
"AdjustmentValue": "95.00",
"AdjustmentType": "Amount"
}],
"description": null,
"elementType": "ListPrice",
"name": "List Price"
},
"sequence": 1
},
{
"fieldToTagNameMapping": {
708
Request BodiesSalesforce Pricing

===== PAGE 723 =====

"PriceAdjustmentScheduleId": "ItemDescription",
"NetUnitPrice": "ItemNetUnitPrice",
"Product2Id": "ItemProduct",
"LowerBound": "ItemQuantity",
"UpperBound": "ItemQuantity",
"Subtotal": "Subtotal",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionSource",
"InputUnitPrice": "ItemListPrice"
},
"inputParameters": {
"PriceAdjustmentScheduleId": "84Xxx0000004CGSEA2",
"Product2Id": "01txx0000006i44AAA",
"LowerBound": 5,
"UpperBound": 5,
"Quantity": 5,
"LineItemId": "item1",
"InputUnitPrice": 10
},
"outputParameters": {
"NetUnitPrice": 8.5,
"Subtotal": 42.5
},
"pricingElement": {
"adjustments": [{
"AdjustmentValue": "15.00",
"AdjustmentType": "Percentage"
}],
"description": null,
"elementType": "VolumeDiscount",
"name": "Volume Discount"
},
"sequence": 2
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalMappings of field to tag names.Map<String,
String>
fieldTo
TagName
Mapping
60.0OptionalInput parameters of the pricing element.Map<String,
Object>
input
Parameters
60.0OptionalOutput parameters of the pricing element.Map<String,
Object>
output
Parameters
60.0OptionalDetails of the pricing element.Adjustment Details
Input
pricing
Element
709
Request BodiesSalesforce Pricing

===== PAGE 724 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalSequence of the pricing element
execution.
Integersequence
Pricing Waterfall Log Input
Input representation of the request to create an explainability action log.
JSON example
{
"currencyCode": "USD",
"executionEndTimestamp": "2023-07-31T20:11:29.625Z",
"executionId": "executionId1",
"executionStartTimestamp": null,
"lineItemId": "item1",
"output": {
"Subtotal": 38.25,
"ListPrice": 10,
"NetUnitPrice": 7.65
},
"waterfall": [{
"fieldToTagNameMapping": {
"Product2Id": "ItemProduct",
"Subtotal": "Subtotal",
"Pricebook2Id": "Pricebook",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionSource",
"ListPrice": "ItemListPrice"
},
"inputParameters": {
"Product2Id": "01txx0000006i44AAA",
"Pricebook2Id": "01sxx0000005q9xAAA",
"Quantity": 5,
"LineItemId": "item1"
},
"outputParameters": {
"Subtotal": 50,
"ListPrice": 10
},
"pricingElement": {
"adjustments": [{
"AdjustmentValue": "95.00",
"AdjustmentType": "Amount"
}],
"description": null,
"elementType": "ListPrice",
"name": "List Price"
},
"sequence": 1
},
710
Request BodiesSalesforce Pricing

===== PAGE 725 =====

{
"fieldToTagNameMapping": {
"PriceAdjustmentScheduleId": "ItemDescription",
"NetUnitPrice": "ItemNetUnitPrice",
"Product2Id": "ItemProduct",
"LowerBound": "ItemQuantity",
"UpperBound": "ItemQuantity",
"Subtotal": "Subtotal",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionSource",
"InputUnitPrice": "ItemListPrice"
},
"inputParameters": {
"PriceAdjustmentScheduleId": "84Xxx0000004CGSEA2",
"Product2Id": "01txx0000006i44AAA",
"LowerBound": 5,
"UpperBound": 5,
"Quantity": 5,
"LineItemId": "item1",
"InputUnitPrice": 10
},
"outputParameters": {
"NetUnitPrice": 8.5,
"Subtotal": 42.5
},
"pricingElement": {
"adjustments": [{
"AdjustmentValue": "15.00",
"AdjustmentType": "Percentage"
}],
"description": null,
"elementType": "VolumeDiscount",
"name": "Volume Discount"
},
"sequence": 2
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalContext definition version ID of the pricing
procedure.
Stringcontext
Definition
VersionId
60.0OptionalContext mapping ID of the pricing
procedure.
Stringcontext
MappingId
60.0OptionalCurrency code such as, USD or INR.StringcurrencyCode
711
Request BodiesSalesforce Pricing

===== PAGE 726 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalEnd timestamp of procedure execution.StringexecutionEnd
Timestamp
60.0RequiredExecution ID for a particular execution of
a pricing procedure.
StringexecutionId
60.0OptionalStart timestamp of procedure execution.Stringexecution
Start
Timestamp
60.0RequiredLine item ID for which the price is being
calculated.
StringlineItemId
60.0OptionalOutput of the pricing procedure.Map<String,
Object>
output
60.0RequiredDetails of the pricing waterfall.Pricing Waterfall
Input[]
waterfall
Procedure Plan Criterion Input
Input representation of the details of a procedure plan criterion.
JSON example
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"literalValue": "test",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 2,
"fieldObject": "BillingPostalCode",
"fieldPath": "BillingPostalCode",
"literalValue": "sample",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 3,
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"literalValue": "2024-07-14",
"operator": "LessThan",
"dataType": "Date"
}
]
712
Request BodiesSalesforce Pricing

===== PAGE 727 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredSequence to be followed to process the
conditions defined in the procedure plan
option.
Integercondition
Sequence
This property value must be unique within
a procedure plan option.
62.0RequiredData type of the field from the selected
object.
StringdataType
62.0RequiredValue of the object field that’s used to
resolve the procedure plan option.
StringfieldObject
This property value must belong to the
primary object that’s associated with the
procedure plan definition, at a maximum
two levels up in the hierarchy.
62.0RequiredPath of the field that’s used in a procedure
in relation to the object that the field
belongs to.
StringfieldPath
The field path must end with the object
field that’s associated with the procedure
plan criterion.
62.0OptionalUser-defined value that’s compared to the
value of the sObject field value.
StringliteralValue
62.0RequiredOperator that’s used by the procedure plan
criterion.
Stringoperator
62.0RequiredID of the procedure plan criterion record.StringrecordId
Procedure Plan Definition Input
Input representation of the details of a procedure plan definition.
JSON example
This example shows a sample request to create a procedure plan definition record by using the Procedure Plan Definitions (POST)
API.
{
"description": "Definition for Quote",
"developerName": "Quote_Definition_Sample",
"name": "Quote_Definition_Sample",
"processType": "Default",
"primaryObject": "BusinessHours",
713
Request BodiesSalesforce Pricing

===== PAGE 728 =====

"procedurePlanDefinitionVersions": [
{
"active": false,
"contextDefinition": "SalesTransactionContext__stdctx",
"readContextMapping": "QuoteEntitiesMapping",
"saveContextMapping": "QuoteEntitiesMapping",
"effectiveFrom": "2024-07-15T10:15:30.000Z",
"developerName": "Quote_Definition_V1",
"rank": 1
}
]
}
This example shows a sample request to update a procedure plan definition by using the Procedure Plan Definition By ID (PATCH)
API.
Note:  The properties that aren’t specified in the input are deleted when updating the record.
{
"description": "Default definition patch update",
"developerName": "Quote_Definition",
"name": "Quote_Definition",
"primaryObject": "Quote",
"recordId": "1FNxx0000004EsOGAU"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalDescription of the procedure plan
definition.
Stringdescription
62.0Required if you’re
invoking the
Developer name of the procedure plan
definition.
StringdeveloperName
Procedure Plan
Definitions API
(POST).
62.0OptionalName of the procedure plan definition.Stringname
62.0Required if you’re
invoking the
Source object that’s used to create a
procedure with rule-based criteria. This
StringprimaryObject
Procedure Planproperty value must be a valid object
Definitions APIname and must be unique in the
ProcedurePlanDefinition object. (POST) and if you’re
creating a
procedure with
rule-based criteria.
62.0RequiredList of versions of a procedure plan
definition.
Procedure Plan
Definition Version
Input[]
procedurePlan
Definition
Versions
714
Request BodiesSalesforce Pricing

===== PAGE 729 =====

Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredSpecifies the business processes that need
a procedure plan for each sObject and
definition. Valid values are:
StringprocessType
• Billing
• DRO
• DeepClone
• ProductDiscovery
• Revenue Cloud
These values can be used based on the
available license. If unspecified, the value
is set to Default.
62.0Required if you’re
invoking the
ID of the procedure plan definition record.StringrecordId
Procedure Plan
Definition By ID API
(PATCH).
Procedure Plan Definition Version Input
Input representation of the details of a procedure plan definition version.
JSON example
{
"active": false,
"developerName": "sample_version_input",
"effectiveFrom": "2024-07-09T00:00:00.000Z",
"contextDefinition": "SalesTransactionContext__stdctx",
"procedurePlanSections": [
{
"isInherited": false,
"procedurePlanOptions": [
{
"saveContextMapping": "AssetToSalesTransactionMapping",
"expressionSetDefinition": "9QAZ60000004ECOOA2",
"expressionSetLabel": "Revenue_Default_Pricing_Procedure",
"expressionSetApiName": "Revenue Default Pricing Procedure",
"logic": "1 AND 2 AND 3",
"priority": 1,
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"literalValue": "test",
"operator": "Equals",
715
Request BodiesSalesforce Pricing

===== PAGE 730 =====

"dataType": "Text"
},
{
"conditionSequence": 2,
"fieldObject": "BillingPostalCode",
"fieldPath": "BillingPostalCode",
"literalValue": "sample",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 3,
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"literalValue": "2024-07-14",
"operator": "LessThan",
"dataType": "Date"
}
]
}
],
"resolutionType": "RuleBased",
"sectionType": "PricingProcedure",
"sequence": 1,
"subSectionType": "PricingProcedure",
"recordId": "1FRZ60000008OIAOA2"
}
],
"rank": 1,
"readContextMapping": "ProductDiscoveryContextMapping",
"saveContextMapping": "OrderEntitiesMapping"
}
Note:  The properties that aren’t specified in the input are deleted when updating the record.
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIndicates whether this procedure plan
definition version is active (true) or not
Booleanactive
(false). You can’t edit or delete a
procedure plan version that’s in the active
state.
62.0RequiredContext definition that’s associated with
the procedure plan definition version
record.
Stringcontext
Definition
62.0RequiredUnique developer name of the procedure
plan definition version.
StringdeveloperName
716
Request BodiesSalesforce Pricing

===== PAGE 731 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredDate and time from when the procedure
plan definition version comes into effect.
StringeffectiveFrom
62.0RequiredDate and time from when the procedure
plan definition version is no longer in
effect.
StringeffectiveTo
62.0This property is
read-only.
Template this procedure plan definition
version is created from.
StringinheritedFrom
62.0RequiredProcedure setup sections for a procedure
plan definition. Each section enables the
Procedure Plan
Section Input[]
procedure
PlanSections
setup of a procedure type by using a
rule-based criteria.
Keep these considerations in mind when
you modify this property.
• You can edit or delete a procedure
plan section if it isn’t associated with
an active procedure plan version.
• You can create a procedure plan
section with rule-based resolution type
if the primary object isn’t empty in the
definition.
62.0RequiredCurrent rank of the procedure plan
definition version that’s used to decide the
Integerrank
sequence of execution of a procedure plan
definition version.
62.0OptionalMapping that’s used to read data from the
mapped object and populate the context
definition.
StringreadContext
Mapping
This property value must be associated
with a context definition.
62.0RequiredID of the procedure plan definition version
record.
StringrecordId
62.0OptionalMapping that’s used to save data from the
context definition and populate the
mapped object.
StringsaveContext
Mapping
This property value must be associated
with a context definition.
62.0OptionalStatus of the procedure plan definition
version record.
Stringstatus
717
Request BodiesSalesforce Pricing

===== PAGE 732 =====

Procedure Plan Evaluation Input
Input representation of the details used to evaluate a procedure plan definition.
JSON example
This example shows a sample request to evaluate a procedure plan definition by using a primary object.
{
"idList": ["a01DU000000BylcYAC"],
"evaluationDate": "2024-07-08T10:15:30.000Z",
"processType": "Default",
"sectionType": ["PricingProcedure"],
"subSectionType": ["Revenue"]
}
This example shows a sample request to evaluate a procedure plan definition by using a definition name.
{
"evaluationDate": "2024-07-08T10:15:30.000Z",
"processType": "Default",
"sectionType": ["PricingProcedure"],
"subSectionType": ["Revenue"]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredDate when the evaluation is applicable.
This property value must be within the
StringevaluationDate
date range when the procedure plan
definition is effective.
62.0Required only if
you’re invoking the
List of record IDs of the procedure plan
definitions to be evaluated.
String[]idList
Procedure Plan
Evaluation By Object
(POST) API.
63.0OptionalSpecifies the business processes that need
a procedure plan for each sObject and
StringprocessType
definition. Valid values based on the
available are:
• Billing
• DRO
• DeepClone
• ProductDiscovery
• Revenue Cloud
These values can be used based on the
available license. If unspecified, the value
is set to Default.
718
Request BodiesSalesforce Pricing

===== PAGE 733 =====

Available
Version
Required or
Optional
DescriptionTypeName
If a procedure plan definition exist in the
org with processType value as null,
modify the value to Default.
62.0OptionalName of section to be evaluated. Valid
values are:
String[]sectionType
• PricingProcedure
• ProductDiscoveryProcedure
• ProductQualificationProcedure
• PricingDiscoveryProcedure
• DiscountSpreadServiceProcedure
• RatingProcedure
• Custom
• RatingDiscoveryProcedure
62.0OptionalName of subsection to be evaluated.String[]subSectionType
The combination of the sectionType  and subSectionType  property values must be unique for every procedure plan
version.
Procedure Plan Section Input
Input representation of the details of a procedure plan section.
JSON example
"procedurePlanSections": [
{
"isInherited": false,
"procedurePlanOptions": [
{
"saveContextMapping": "AssetToSalesTransactionMapping",
"expressionSetDefinition": "9QAZ60000004ECOOA2",
"expressionSetLabel": "Revenute_Default_Pricing_Procedure",
"expressionSetApiName": "Revenue Default Pricing Procedure",
"logic": "1 AND 2 AND 3",
"priority": 1,
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"literalValue": "test",
"operator": "Equals",
"dataType": "Text"
},
719
Request BodiesSalesforce Pricing

===== PAGE 734 =====

{
"conditionSequence": 2,
"fieldObject": "BillingPostalCode",
"fieldPath": "BillingPostalCode",
"literalValue": "sample",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 3,
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"literalValue": "2024-07-14",
"operator": "LessThan",
"dataType": "Date"
}
]
}
],
"resolutionType": "RuleBased",
"sectionType": "PricingProcedure",
"sequence": 1,
"subSectionType": "PricingProcedure",
"recordId": "1FRZ60000008OIAOA2"
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0This property is
read-only.
Indicates whether the procedure plan
section is inherited from a template
(true) or not (false).
BooleanisInherited
62.0RequiredList of procedure plan options that defines
a group of criteria.
Procedure Plan
Option Input[]
procedurePlan
Options
You can edit or delete a procedure plan
option only if it isn’t associated with an
active procedure plan version.
62.0RequiredID of the procedure plan section record.StringrecordId
62.0RequiredType of resolution used to filter the
procedure. You can’t edit this property
Stringresolution
Type
value if the procedure plan section
includes a procedure plan option record.
62.0RequiredType of section. Valid values are:StringsectionType
• PricingProcedure
• ProductDiscoveryProcedure
720
Request BodiesSalesforce Pricing

===== PAGE 735 =====

Available
Version
Required or
Optional
DescriptionTypeName
• ProductQualificationProcedure
• PricingDiscoveryProcedure
• DiscountSpreadServiceProcedure
• RatingProcedure
• Custom
• RatingDiscoveryProcedure
62.0RequiredSequence to be followed for the
processing of the procedures. This property
Integersequence
value must be greater than 0 and must be
unique for a procedure plan section
associated with a procedure plan version.
62.0RequiredProcedure subsection added to the
procedure plan definition.
StringsubSection
Type
Procedure Plan Option Input
Input representation of the details of a procedure plan option.
JSON example
"procedurePlanOptions": [
{
"saveContextMapping": "AssetToSalesTransactionMapping",
"expressionSetDefinition": "9QAZ60000004ECOOA2",
"expressionSetLabel": "Revenute_Default_Pricing_Procedure",
"expressionSetApiName": "Revenue Default Pricing Procedure",
"logic": "1 AND 2 AND 3",
"priority": 1,
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"literalValue": "test",
"operator": "Equals",
"dataType": "Text"
},
{
"conditionSequence": 2,
"fieldObject": "BillingPostalCode",
"fieldPath": "BillingPostalCode",
"literalValue": "sample",
"operator": "Equals",
"dataType": "Text"
},
{
721
Request BodiesSalesforce Pricing

===== PAGE 736 =====

"conditionSequence": 3,
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"literalValue": "2024-07-14",
"operator": "LessThan",
"dataType": "Date"
}
]
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalAPI name of the expression set.StringexpressionSet
ApiName
62.0RequiredExpression set definition that’s associated
with this procedure plan option record.
StringexpressionSet
Definition
62.0OptionalLabel of the expression set that’s
associated with this procedure plan option
record.
StringexpressionSet
Label
62.0OptionalComputation logic for the conditions
applied to a procedure plan option.
Stringlogic
This property value must be blank if the
resolution type is default.
62.0RequiredPriority for the specified criteria. This
property value must be greater than 0 and
Integerpriority
must be unique within a procedure plan
section.
62.0OptionalDetails of the rule-based criteria for the
procedure.
Procedure Plan
Criterion Input[]
procedurePlan
Criterion
You can edit or delete a procedure plan
criterion only if it isn’t associated with an
active procedure plan version.
62.0OptionalMapping that’s used to read from the
mapped object and populate the context
definition.
StringreadContext
Mapping
This property value must be associated
with a context definition.
62.0RequiredID of the procedure plan option record.StringrecordId
722
Request BodiesSalesforce Pricing

===== PAGE 737 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalMapping that’s used to save data from the
context definition and populate the
mapped object.
StringsaveContext
Mapping
This property value must be associated
with a context definition.
Response Bodies
Learn more about the available Salesforce Pricing API response bodies.
Adjustment Details
Output representation of a pricing adjustment request.
API Execution Log Response
Output representation of the execution log of a pricing waterfall request.
Line Item Waterfall Response
Output representation of the line item waterfall response.
PBE Derived Pricing
Output representation of the response that includes the source product for the Price Book Entry (PBE) derived pricing.
Pricing Error Response
Output representation of the pricing error response.
Pricing Execution Waterfall Response
Output representation of the execution process that's associated with a pricing waterfall.
Pricing Generic Response
Output representation of a pricing data sync request.
Pricing Output
Output representation of a Salesforce pricing request.
Pricing Recipe LookUp Table Response
Output representation of a pricing recipe lookup table.
Pricing Recipe
Output representation of the pricing recipe information table.
Pricing Recipe Post
Output representation of the pricing recipe after the API request.
Pricing Recipe Response
Output representation of the pricing recipe.
Pricing Response
Output representation of the pricing request.
Pricing Result
Output representation of the pricing result.
723
Response BodiesSalesforce Pricing

===== PAGE 738 =====

Pricing Result Error
Output representation of the pricing result error.
Pricing Versioned Revision Details
Output representation of the versioned revision details.
Pricing Waterfall Response
Output representation of a pricing waterfall request.
Procedure Plan Criterion
Output representation of the details of a procedure plan criterion.
Procedure Plan Definition
Output representation of the details of a single procedure plan definition.
Procedure Plan Definition Version
Output representation of the version details of a procedure plan definition.
Procedure Plan Definitions
Output representation of the details of procedure plan definitions.
Procedure Plan Generic
Output representation of the details of the created procedure plan definition record.
Procedure Plan Generic Error
Output representation of the error details related to the procedure plan definitions.
Procedure Plan Option
Output representation of the details of a procedure plan option.
Procedure Plan Section
Output representation of the details of a procedure plan section.
Procedure Plan Section Evaluation Runtime
Output representation of the results from the procedure plan evaluation.
Procedure Plan Evaluation
Output representation of the evaluation details of a procedure plan definition.
Procedure Plan Evaluation Response
Output representation of the evaluation details of a procedure plan definition.
Procedure Plan Evaluation Result
Output representation of the evaluation result of a procedure plan definition.
Pricing Process Execution Details for Line Items
Output representation of the pricing process execution details for the line items along with the error details and response generation
status.
Line Item Details Response
Output representation of the pricing process execution details for the line items.
Pricing Process Execution Response
Output representation of the details of a pricing process execution.
Pricing Process Execution List
Output representation of the execution details for different types of the pricing processes.
Pricing Simulation Input Variables With Data
Output representation of the pricing simulation variables with data.
724
Response BodiesSalesforce Pricing

===== PAGE 739 =====

Adjustment Details
Output representation of a pricing adjustment request.
JSON example
"pricingElement": {
"adjustments": [{
"adjustmentType": null,
"adjustmentValue": null
}],
"name": "List Price",
"elementType": "ListPrice"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Details of the pricing element.Map<String,
Object>[]
adjustments
60.0Small, 60.0Description of the pricing element.Stringdescription
60.0Small, 60.0Type of the pricing element.StringelementType
60.0Small, 60.0Name of the pricing element.Stringname
API Execution Log Response
Output representation of the execution log of a pricing waterfall request.
JSON example
{
"message": {The Pricing API execution was successful.},
"pricingElement": {
"adjustments": [
{
"adjustmentType": null,
"adjustmentValue": null
}
],
"name": "List Price",
"elementType": "ListPrice"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Message of the API execution.String []message
725
Response BodiesSalesforce Pricing

===== PAGE 740 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Details of the price adjustment of a pricing
element.
Adjustment DetailspricingElement
Line Item Waterfall Response
Output representation of the line item waterfall response.
JSON example
{
"currencyCode": "USD",
"error": null,
"executionEndTimestamp": "2023-07-31T20:11:29.625Z",
"executionId": "gdLVwn2x1uats2xWMAjV",
"executionStartTimestamp": null,
"lineItemId": "item1",
"success": true,
"usageType":"Pricing",
"output": {
"quantity": "10",
"netUnitPrice": "10",
"subtotal": "100"
},
"waterfall": []
}
This sample response includes diagnostic data if you’ve enabled Advanced Logging settings under Salesforce Pricing from Setup.
{
"apiExecutionId": "395526033950891",
"contextDefinitionVersionId": "11OSG000000Eiu12AC",
"contextMappingId": "11jSG00001YqfHVYAZ",
"currencyCode": "USD",
"executionEndTimestamp": "2026-02-17T10:43:46.197Z",
"executionId": "395527509949481",
"executionStartTimestamp": "2026-02-17T10:43:44.063Z",
"id": "0QLSG000001OXv84AG",
"lineItemId": "0QLSG000001OXv84AG",
"output": {
"NetUnitPrice": 20,
"TotalSubscriptionPrice": 40,
"Subtotal": 40,
"diagnosticData": {
"lineItemId": "0QLSG000001OXv84AG",
"exceptionDetails": {},
"inputParams": {
"ContributingNetUnitPrice": [
100
],
"ContributingSubTotal": [
100
726
Response BodiesSalesforce Pricing

===== PAGE 741 =====

],
"DerivedFormula": [
"PERCENTAGE(ListPrice,10)",
"PERCENTAGE(ListPrice,10)"
],
"PRODUCT_REFERENCE_IDS": null,
"Subtotal": 40,
"Quantity": 2,
"TransactionalListPrice": 0,
"ContractId": null,
"CurrencyIsoCode": "USD",
"ContributingSource": [
"Product",
"Product"
],
"isDerivedProcessed": true,
"IsDerived": true,
"NetUnitPrice": 20,
"ContributingId": [
"02iSG000001fenKYAQ",
"0QLSG000001OXv74AG"
],
"HeaderTotal": 100,
"ContributingScope": [
"NonTransactional",
"Transactional"
],
"Non-TransactionalListPrice": [
100
],
"ContributingProduct": [
"01tSG00000CC6NhYAL",
"01tSG00000CC6NhYAL"
],
"LineItemId": "0QLSG000001OXv84AG",
"hasError": false,
"lineItemDetailId": "0QLSG000001OXv84AG",
"lineItemDetailIndex": 1
},
"contributorCount": 2,
"contributingLines": [
{
"ContributingNetUnitPrice": 100,
"DerivedFormula": "PERCENTAGE(ListPrice,10)",
"ContributingSubTotal": 100,
"ContributingId": "0QLSG000001OXv84AG",
"ContributingScope": "NonTransactional",
"HeaderTotal": 100,
"isSkipped": false,
"Non-TransactionalListPrice": 100,
"ContributingProduct": "01tSG00000CC6NhYAL",
"TransactionalListPrice": 0,
"hasError": false,
"ContributingSource": "Product"
727
Response BodiesSalesforce Pricing

===== PAGE 742 =====

},
{
"ContributingNetUnitPrice": null,
"DerivedFormula": "PERCENTAGE(ListPrice,10)",
"ContributingSubTotal": null,
"ContributingId": "0QLSG000001OXv84AG",
"ContributingScope": "Transactional",
"HeaderTotal": 100,
"isSkipped": false,
"Non-TransactionalListPrice": null,
"ContributingProduct": "01tSG00000CC6NhYAL",
"TransactionalListPrice": 0,
"hasError": false,
"ContributingSource": "Product"
}
]
},
"isParallelExecution": true,
"SubscriptionNetUnitPrice": 20,
"section-1-output": 40,
"section-0-output": 40
},
"success": true,
"usageType": "Pricing",
"waterfall": [
{
"fieldToTagNameMapping": {
"ContributingNetUnitPrice": "ContributorUnitPrice",
"ContributingSubTotal": "ContributorTotalPrice",
"DerivedFormula": "ContributorFormulaInput",
"Subtotal": "ItemNetTotalPrice",
"Quantity": "LineItemQuantity",
"TransactionalListPrice": "ListPrice",
"ContractId": "ItemContract",
"CurrencyIsoCode": "CurrencyIsoCode",
"PriceWaterfall": "price_water_fall",
"ContributingSource": "ContributorSource",
"IsDerived": "DerivedPricingAttribute",
"NetUnitPrice": "NetUnitPrice",
"ContributingId": "Contributor",
"ContributingScope": "ContributorScope",
"HeaderTotal": "TotalAmount",
"Non-TransactionalListPrice": "ContributorListPrice",
"ContributingProduct": "ContributorProduct",
"LineItemId": "LineItem"
},
"hideWaterfall": false,
"inputParameters": {
"ContributingNetUnitPrice": [
100
],
"ContributingSubTotal": [
100
],
728
Response BodiesSalesforce Pricing

===== PAGE 743 =====

"DerivedFormula": [
"PERCENTAGE(ListPrice,10)",
"PERCENTAGE(ListPrice,10)"
],
"Quantity": 2,
"TransactionalListPrice": 0,
"ContractId": null,
"CurrencyIsoCode": "USD",
"ContributingSource": [
"Product",
"Product"
],
"IsDerived": true,
"ContributingId": [
"02iSG000001fenKYAQ",
"0QLSG000001OXv74AG"
],
"HeaderTotal": 100,
"ContributingScope": [
"NonTransactional",
"Transactional"
],
"Non-TransactionalListPrice": [
100
],
"diagnosticData": {
"lineItemId": "0QLSG000001OXv84AG",
"exceptionDetails": {},
"inputParams": {
"ContributingNetUnitPrice": [
100
],
"ContributingSubTotal": [
100
],
"DerivedFormula": [
"PERCENTAGE(ListPrice,10)",
"PERCENTAGE(ListPrice,10)"
],
"PRODUCT_REFERENCE_IDS": null,
"Subtotal": 40,
"Quantity": 2,
"TransactionalListPrice": 0,
"ContractId": null,
"CurrencyIsoCode": "USD",
"ContributingSource": [
"Product",
"Product"
],
"isDerivedProcessed": true,
"IsDerived": true,
"NetUnitPrice": 20,
"ContributingId": [
"02iSG000001fenKYAQ",
729
Response BodiesSalesforce Pricing

===== PAGE 744 =====

"0QLSG000001OXv74AG"
],
"HeaderTotal": 100,
"ContributingScope": [
"NonTransactional",
"Transactional"
],
"Non-TransactionalListPrice": [
100
],
"ContributingProduct": [
"01tSG00000CC6NhYAL",
"01tSG00000CC6NhYAL"
],
"LineItemId": "0QLSG000001OXv84AG",
"hasError": false,
"lineItemDetailId": "0QLSG000001OXv84AG",
"lineItemDetailIndex": 1
},
"contributorCount": 2,
"contributingLines": [
{
"ContributingNetUnitPrice": 100,
"DerivedFormula": "PERCENTAGE(ListPrice,10)",
"ContributingSubTotal": 100,
"ContributingId": "0QLSG000001OXv84AG",
"ContributingScope": "NonTransactional",
"HeaderTotal": 100,
"isSkipped": false,
"Non-TransactionalListPrice": 100,
"ContributingProduct": "01tSG00000CC6NhYAL",
"TransactionalListPrice": 0,
"hasError": false,
"ContributingSource": "Product"
},
{
"ContributingNetUnitPrice": null,
"DerivedFormula": "PERCENTAGE(ListPrice,10)",
"ContributingSubTotal": null,
"ContributingId": "0QLSG000001OXv84AG",
"ContributingScope": "Transactional",
"HeaderTotal": 100,
"isSkipped": false,
"Non-TransactionalListPrice": null,
"ContributingProduct": "01tSG00000CC6NhYAL",
"TransactionalListPrice": 0,
"hasError": false,
"ContributingSource": "Product"
}
]
},
"ContributingProduct": [
"01tSG00000CC6NhYAL",
"01tSG00000CC6NhYAL"
730
Response BodiesSalesforce Pricing

===== PAGE 745 =====

],
"LineItemId": "0QLSG000001OXv84AG"
},
"outputParameters": {
"Subtotal": 40,
"diagnosticData": {
"lineItemId": "0QLSG000001OXv84AG",
"exceptionDetails": {},
"inputParams": {
"ContributingNetUnitPrice": [
100
],
"ContributingSubTotal": [
100
],
"DerivedFormula": [
"PERCENTAGE(ListPrice,10)",
"PERCENTAGE(ListPrice,10)"
],
"PRODUCT_REFERENCE_IDS": null,
"Subtotal": 40,
"Quantity": 2,
"TransactionalListPrice": 0,
"ContractId": null,
"CurrencyIsoCode": "USD",
"ContributingSource": [
"Product",
"Product"
],
"isDerivedProcessed": true,
"IsDerived": true,
"NetUnitPrice": 20,
"ContributingId": [
"02iSG000001fenKYAQ",
"0QLSG000001OXv74AG"
],
"HeaderTotal": 100,
"ContributingScope": [
"NonTransactional",
"Transactional"
],
"Non-TransactionalListPrice": [
100
],
"ContributingProduct": [
"01tSG00000CC6NhYAL",
"01tSG00000CC6NhYAL"
],
"LineItemId": "0QLSG000001OXv84AG",
"hasError": false,
"lineItemDetailId": "0QLSG000001OXv84AG",
"lineItemDetailIndex": 1
},
"contributorCount": 2,
731
Response BodiesSalesforce Pricing

===== PAGE 746 =====

"contributingLines": [
{
"ContributingNetUnitPrice": 100,
"DerivedFormula": "PERCENTAGE(ListPrice,10)",
"ContributingSubTotal": 100,
"ContributingId": "0QLSG000001OXv84AG",
"ContributingScope": "NonTransactional",
"HeaderTotal": 100,
"isSkipped": false,
"Non-TransactionalListPrice": 100,
"ContributingProduct": "01tSG00000CC6NhYAL",
"TransactionalListPrice": 0,
"hasError": false,
"ContributingSource": "Product"
},
{
"ContributingNetUnitPrice": null,
"DerivedFormula": "PERCENTAGE(ListPrice,10)",
"ContributingSubTotal": null,
"ContributingId": "0QLSG000001OXv84AG",
"ContributingScope": "Transactional",
"HeaderTotal": 100,
"isSkipped": false,
"Non-TransactionalListPrice": null,
"ContributingProduct": "01tSG00000CC6NhYAL",
"TransactionalListPrice": 0,
"hasError": false,
"ContributingSource": "Product"
}
]
},
"NetUnitPrice": 20
},
"pricingElement": {
"adjustments": [
{
"NetUnitPrice": 10,
"ContributingId": "02iSG000001fenKYAQ",
"ContributingScope": "NonTransactional",
"ContributingProduct": "01tSG00000CC6NhYAL",
"ContributingSource": "Product"
},
{
"NetUnitPrice": 10,
"ContributingId": "0QLSG000001OXv74AG",
"ContributingScope": "Transactional",
"ContributingProduct": "01tSG00000CC6NhYAL",
"ContributingSource": "Product"
}
],
"elementType": "DerivedPricing",
"name": "Derived Price"
},
"profileAccess": [],
732
Response BodiesSalesforce Pricing

===== PAGE 747 =====

"sequence": 3,
"tasksInfo": [
{
"executionEndTimestamp": "2026-02-17T10:43:46.077280883Z",
"executionStartTimestamp": "2026-02-17T10:43:46.037719198Z",
"taskName": "DerivedPrice-DerivedCalculate"
},
{
"executionEndTimestamp": "2026-02-17T10:43:45.657762503Z",
"executionStartTimestamp": "2026-02-17T10:43:45.657283237Z",
"taskName": "DerivedPrice-UpdateCalculationPayload"
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Context definition version ID of the pricing
procedure.
Stringcontext
Definition
VersionId
60.0Small, 60.0Context mapping ID of the record.Stringcontext
MappingId
60.0Small, 60.0Currency code. For example, USD or INR.StringcurrencyCode
60.0Small, 60.0Details of any errors.Pricing Error
Response
error
60.0Small, 60.0End timestamp of procedure execution.StringexecutionEnd
Timestamp
60.0Small, 60.0Execution ID of a particular execution of a
pricing procedure.
StringexecutionId
60.0Small, 60.0Start timestamp of procedure execution.Stringexecution
Start
Timestamp
60.0Small, 60.0Line item ID for which the price is being
calculated.
StringlineItemId
60.0Small, 60.0Output of the pricing procedure.Map<String,
Object>
output
60.0Small, 60.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
62.0Small, 62.0Usage type of the waterfall log record.StringusageType
60.0Small, 60.0Details of the price waterfall.Pricing Waterfall
Response[]
waterfall
733
Response BodiesSalesforce Pricing

===== PAGE 748 =====

PBE Derived Pricing
Output representation of the response that includes the source product for the Price Book Entry (PBE) derived pricing.
JSON example
{
"productId":"01txx0000006i2SAAQ",
"pricebookEntryId":"01uxx0000008yYcAAI",
"effectiveFrom":"2020-01-01T22:53:20.000Z",
"effectiveTo":"2021-01-01T22:53:20.000Z"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
61.0Small, 61.0Displays the error while processing the
request.
Pricing Error
Response[]
error
61.0Small, 61.0Indicates whether the request is successful
(true) or not (false).
BooleanisSuccess
61.0Small, 61.0ID of the source product.Stringsource
ProceductId
Pricing Error Response
Output representation of the pricing error response.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Indicates the error code.StringerrorCode
60.0Small, 60.0Specifies the message stating the reason for
the error, if any.
Stringmessage
Pricing Execution Waterfall Response
Output representation of the execution process that's associated with a pricing waterfall.
JSON example
{
"apiExecutionId": "263369316770986",
"apiExecutionLogRepresentationList": [
{
"message": [
"The Pricing API couldn't be run. Try again, and if the issue persists, ask your
admin for help."
]
}
],
"executionId": "263369316895959",
734
Response BodiesSalesforce Pricing

===== PAGE 749 =====

"referenceKey": "referenceKey-ABCD",
"success": false,
"usageType": "Api_Execution"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
Small, 63.0Small, 63.0Unique execution ID that's generated each
time a pricing API is executed.
StringapiExecutionId
63.0Small, 63.0List of API execution logs.API Execution Log
Response[]
apiExecution
LogRepresentation
List
Small, 63.0Small, 63.0Error details of the pricing execution
process.
Pricing Error
Response
error
Small, 63.0Small, 63.0Unique ID that's generated each time a
pricing process is executed.
StringexecutionId
Small, 63.0Small, 63.0The reference ID that a consuming
workstream provides in the API to search
StringreferenceKey
for the specific logs in the Pricing Operations
Console.
Small, 63.0Small, 63.0Indicates whether the API execution is
successful (true) or not (false).
Booleansuccess
Small, 63.0Small, 63.0Usage type of the API execution.StringusageType
Pricing Generic Response
Output representation of a pricing data sync request.
JSON example
{
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Details from the pricing error response.Pricing Error
Response
error
60.0Small, 60.0Indicates whether the request is successful
(true) or not (false).
Booleansuccess
735
Response BodiesSalesforce Pricing

===== PAGE 750 =====

Pricing Output
Output representation of a Salesforce pricing request.
JSON example
{
"apiExecutionId": "612228038743152",
"pricingExecutionId": "612229738898095",
"pricingResult": {
"subtotal": [
{
"dataPath": [
"cart_1001",
"lineItem_1002"
],
"value": 300.0,
"errors": [],
"isSuccess": true
},
{
"dataPath": [
"cart_1001",
"lineItem_1001"
],
"value":400.0,
"errors": [],
"isSuccess": true
}
],
"netunitprice": [
{
"dataPath": [
"cart_1001",
"lineItem_1002"
],
"value": xx,
"errors": [],
"isSuccess": true
},
{
"dataPath": [
"cart_1001",
"lineItem_1001"
],
"value": xx,
"errors": [],
"isSuccess": true
}
]
},
"pricingResultErrors": [],
"status": "Completed",
}
736
Response BodiesSalesforce Pricing

===== PAGE 751 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Unique ID that's generated each time a
pricing API is executed.
StringapiExecutionId
60.0Small, 60.0Displays the error encountered when the
request is processed. For example, a pricing
procedure isn’t found.
Pricing Error
Response
error
63.0Small, 63.0Unique ID that's generated each time a
pricing process is executed.
StringpricingExecutionId
60.0Small, 60.0Represents the outcomes associated with
the output tags defined in the contextual
Pricing ResultpricingResult
definition for which the pricing engine
establishes values. The initial attribute name
is substituted for the output tag's
designation. For instance, if the original
attribute name specified in the Context
Definition is "Subtotal," but during
contextual setup, the output tag is denoted
as "Total Price," the API output exhibits the
initial attribute name "Subtotal" in the
response.
60.0Small, 60.0Errors from the pricing request, if any.Pricing Result Error[]pricingResult
Errors
60.0Small, 60.0Status of the pricing request. Valid values
are:
Stringstatus
• Completed  — Pricing is completed
for all the line items.
• Partially Completed  —
Pricing is completed for some line items.
• Failed — Pricing isn’t completed for
the line items.
Pricing Recipe LookUp Table Response
Output representation of a pricing recipe lookup table.
JSON example
"decisionTables": [
{
"id": "0lDxx00000000T3EAI",
"isInternal": true,
"pricingComponentType": "ListPrice"
},
737
Response BodiesSalesforce Pricing

===== PAGE 752 =====

{
"id": "0lDxx00000000T4EAI",
"isInternal": true,
"pricingComponentType": "VolumeDiscount"
},
{
"id": "0lDxx00000000HlEAI",
"isInternal": false,
"pricingComponentType": "CustomDiscount"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the pricing recipe table mapping.Stringid
60.0Small, 60.0Indicates if the decision table is available
(true) or not (false).
BooleanisInternal
60.0Small, 60.0Price component types such as, custom
discount, volume discount, attribute-based
Stringpricing
ComponentType
discount, bundle-based discount, and list
price.
Pricing Recipe
Output representation of the pricing recipe information table.
JSON example
"recipes": [
{
"active": false,
"createdBy": "autoproc@00dxx0000006gmjea2",
"createdOn": "2023-07-15T13:12:38.000Z",
"decisionTables": [
{
"id": "0lDxx00000000T3EAI",
"isInternal": true,
"pricingComponentType": "ListPrice"
},
{
"id": "0lDxx00000000T4EAI",
"isInternal": true,
"pricingComponentType": "VolumeDiscount"
},
{
"id": "0lDxx00000000HlEAI",
"isInternal": false,
"pricingComponentType": "CustomDiscount"
}
],
738
Response BodiesSalesforce Pricing

===== PAGE 753 =====

"developerName": "NGPDefaultRecipe",
"id": "12Gxx0000005Ka4EAE",
"name": "NGPDefaultRecipe",
"procedureCreatedBy": "",
"procedureCreatedOn": "2023-09-19T11:39:18.983Z",
"procedureId": "",
"procedureName": ""
}]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Indicates whether the recipe is active
(true) or not (false).
Booleanactive
60.0Small, 60.0Details on who created the recipe.StringcreatedBy
60.0Small, 60.0Date when the recipe was created.StringcreatedOn
60.0Small, 60.0Decision tables linked to the recipe.Pricing Recipe
LookUp Table
Response []
decision
Tables
60.0Small, 60.0API name of the recipe.StringdeveloperName
60.0Small, 60.0ID of the recipe.Stringid
60.0Small, 60.0Name of the recipe.Stringname
60.0Small, 60.0Details on who created the procedure.Stringprocedure
CreatedBy
60.0Small, 60.0Date when the procedure was created.Stringprocedure
CreatedOn
60.0Small, 60.0ID of the procedure.StringprocedureId
60.0Small, 60.0Name of the procedure.StringprocedureName
Pricing Recipe Post
Output representation of the pricing recipe after the API request.
JSON example
{
isSuccess : true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Details from the pricing error response.Pricing Error
Response
error
739
Response BodiesSalesforce Pricing

===== PAGE 754 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Indicates whether the response was
calculated successfully (true) or not
(false).
BooleanisSuccess
Pricing Recipe Response
Output representation of the pricing recipe.
JSON example
{
"recipes": [
{
"active": false,
"createdBy": "autoproc@00dxx0000006gmjea2",
"createdOn": "2023-07-15T13:12:38.000Z",
"decisionTables": [
{
"id": "0lDxx00000000T3EAI",
"isInternal": true,
"pricingComponentType": "ListPrice"
},
{
"id": "0lDxx00000000T4EAI",
"isInternal": true,
"pricingComponentType": "VolumeDiscount"
},
{
"id": "0lDxx00000000HlEAI",
"isInternal": false,
"pricingComponentType": "CustomDiscount"
}
],
"developerName": "NGPDefaultRecipe",
"id": "12Gxx0000005Ka4EAE",
"name": "NGPDefaultRecipe",
"procedureCreatedBy": "",
"procedureCreatedOn": "2023-09-19T11:39:18.983Z",
"procedureId": "",
"procedureName": ""
}],
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Representation of the pricing recipe.Pricing Recipe
Output
Representation[]
recipes
740
Response BodiesSalesforce Pricing

===== PAGE 755 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Indicates if the request is successful (true)
or not (false).
Booleansuccess
Pricing Response
Output representation of the pricing request.
JSON example
{
"success": true,
"executionId": "zu81o5hBCrFzyd5LWZk"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Errors while processing the request, if any.Pricing Error
Response
error
60.0Small, 60.0Auto-generated alphanumeric string for
correlation to extract async waterfall and
context persistence status.
StringexecutionId
60.0Small, 60.0Indicates if the request is successful (true)
or not (false).
Booleansuccess
Pricing Result
Output representation of the pricing result.
JSON example
"pricingResult": {
"subtotal": [
{
"dataPath": [
"cart_1001",
"lineItem_1002"
],
"value": 300.0,
"errors": [],
"isSuccess": true
},
{
"dataPath": [
"cart_1001",
"lineItem_1001"
],
741
Response BodiesSalesforce Pricing

===== PAGE 756 =====

"value":400.0,
"errors": [],
"isSuccess": true
}
],
"netunitprice": [
{
"dataPath": [
"cart_1001",
"lineItem_1002"
],
"value": xx,
"errors": [],
"isSuccess": true
},
{
"dataPath": [
"cart_1001",
"lineItem_1001"
],
"value": xx,
"errors": [],
"isSuccess": true
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Includes the entire data route for the specific
element starting from the root node. The
StringdataPath
request must include the ID to construct the
accurate data route.
For example, if a jsonDataString
property comprises a Cart [Id = Cart1] and
its associated Cart Item [Id = CartItem1],
then the data route for CartItem appears as
[Cart1, CartItem1].
60.0Small, 60.0Displays processing errors related to the
element as recognized by the data path.
Pricing Error
Response[]
errors
60.0Small, 60.0Displays if processing of the element for the
specified data path is successful or not.
BooleanisSuccess
60.0Small, 60.0Displays the value of the element into
consideration. Element is uniquely identify
by the data path.
Objectvalue
742
Response BodiesSalesforce Pricing

===== PAGE 757 =====

Pricing Result Error
Output representation of the pricing result error.
JSON example
"pricingResultErrors": {
"Aggregateprice": [
{
"dataPath": [
"cart_1001",
],
"errors": [
{
“errorCode”: “Dummy”
“message”:
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Includes the entire data route for the specific
element starting from the root node. The
String[]dataPath
request must include the ID to construct the
accurate data route.
For example, if a jsonDataString
property comprises a Cart [Id = Cart1] and
its associated Cart Item [Id = CartItem1],
then the data route for CartItem appears as
[Cart1, CartItem1].
60.0Small, 60.0Displays processing errors related to the
element as recognized by the data path.
Pricing Error
Response
errors
Pricing Versioned Revision Details
Output representation of the versioned revision details.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Details from the pricing error response.Pricing Error
Response
error
60.0Small, 60.0Indicates whether the request is successful
(true) or not (false).
Booleansuccess
743
Response BodiesSalesforce Pricing

===== PAGE 758 =====

Pricing Waterfall Response
Output representation of a pricing waterfall request.
JSON example
{
"inputParameters": {
"productId": "01txx0000006i2SAAQ",
"pricebookId": "01sxx0000005ptpAAA",
"pricingModelType": "OneTime"
},
"fieldToTagNameMapping": {
"Product2Id": "ItemProduct",
"Subtotal": "Subtotal",
"Pricebook2Id": "Pricebook",
"Quantity": "ItemQuantity",
"LineItemId": "SalesTransactionSource",
"ListPrice": "ItemListPrice"
},
"sequence": 0,
"outputParameters": {
"listPrice": "10"
},
"pricingElement": {
"adjustments": [
{
"adjustmentType": null,
"adjustmentValue": null
}
],
"name": "List Price"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Mappings of field to tag names.Map<String, String>fieldTo
TagName
Mapping
60.0Small, 60.0Parameters of pricing element input.Map<String,
Object>
input
Parameters
60.0Small, 60.0Parameters of pricing element output.Map<String,
Object>
output
Parameters
60.0Small, 60.0Details of the price adjustment of a pricing
element.
Adjustment Detailspricing
Element
60.0Small, 60.0Sequence of pricing element execution.Integersequence
744
Response BodiesSalesforce Pricing

===== PAGE 759 =====

Procedure Plan Criterion
Output representation of the details of a procedure plan criterion.
JSON example
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"dataType": "Text",
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"isSuccess": true,
"literalValue": "test",
"operator": "Equals",
"recordId": "1FiZ60000004C9cKAE"
},
{
"conditionSequence": 2,
"dataType": "Text",
"fieldObject": "BillingPostalCode",
"fieldPath": "BillingPostalCode",
"isSuccess": true,
"literalValue": "pramit",
"operator": "Equals",
"recordId": "1FiZ60000004C9dKAE"
},
{
"conditionSequence": 3,
"dataType": "Date",
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"isSuccess": true,
"literalValue": "2024-07-14",
"operator": "LessThan",
"recordId": "1FiZ60000004C9eKAE"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Sequence to be followed to process the
conditions defined in the procedure plan
option.
Integercondition
Sequence
62.0Small, 62.0Data type of the field from the selected
object.
StringdataType
62.0Small, 62.0Details of the error encountered during the
processing of the API request.
Procedure Plan
Generic Error[]
error
62.0Small, 62.0Value of the object field that’s used to
resolve the procedure plan option.
StringfieldObject
745
Response BodiesSalesforce Pricing

===== PAGE 760 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Path of the field that’s used in a procedure
in relation to the object that the field
belongs to.
StringfieldPath
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccess
62.0Small, 62.0User-defined value that’s compared to the
value of the sObject field value.
StringliteralValue
62.0Small, 62.0Operator that’s used by the procedure plan
criterion.
Stringoperator
62.0Small, 62.0ID of the procedure plan criterion record.StringrecordId
Procedure Plan Definition
Output representation of the details of a single procedure plan definition.
JSON example
This example shows a sample response for the Procedure Plan Definition By ID (GET) request.
{
"description": "Default Definition",
"developerName": "Quote_Definition",
"name": "Quote_Definition",
"primaryObject": "Quote",
"procedurePlanDefinitionVersions": [
{
"active": false,
"contextDefinition": "11Oxx0000006PZ7EAM",
"effectiveFrom": "2024-02-03T10:15:30.000Z",
"effectiveTo": "2024-02-03T10:15:30.000Z",
"readContextMapping": "MedicalHistoryMapping",
"recordId": "1Cvxx0000004E1ACAU",
"saveContextMapping": "MedicalHistoryMapping",
"success": true,
"processType": "Default"
}
],
"recordId": "1FNxx0000004GkWGAU",
"processType": "Default",
"success": true
}
This example shows a sample response for the Procedure Plan Definition By ID (PATCH) request.
{
"procedurePlanDefinitionVersions":[],
"recordId":"1FNDU00000000EX4AY",
"processType": "Default",
746
Response BodiesSalesforce Pricing

===== PAGE 761 =====

"success":true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Description for the procedure plan
definition.
Stringdescription
62.0Small, 62.0Developer name of the procedure plan
definition.
StringdeveloperName
62.0Small, 62.0Details of the error encountered during the
processing of the API request.
Procedure Plan
Generic Error[]
error
62.0Small, 62.0Name of the procedure plan definition.Stringname
62.0Small, 62.0Object that’s associated with the procedure
plan definition.
StringprimaryObject
62.0Small, 62.0Details of the versions of a procedure plan
definition.
Procedure Plan
Definition Version[]
procedurePlan
Definition
Versions
63.0Small, 63.0Business processes that's specified that
requires a procedure plan for each sObject
and definition.
StringprocessType
62.0Small, 62.0ID of the procedure plan definition record.StringrecordId
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
Procedure Plan Definition Version
Output representation of the version details of a procedure plan definition.
JSON example
"procedurePlanDefinitionVersions": [
{
"active": false,
"developerName": "sample_test",
"effectiveFrom": "2024-07-09T00:00:00.000Z",
"contextDefinition": "SalesTransactionContext__stdctx",
"procedurePlanSections": [],
"rank": 1,
"readContextMapping": "ProductDiscoveryContextMapping",
"recordId": "1CvZ60000008OIaKAM",
"success": true,
"processType": "Default"
}
]
747
Response BodiesSalesforce Pricing

===== PAGE 762 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Indicates whether the procedure plan
definition version is active (true) or not
(false).
Booleanactive
62.0Small, 62.0Context definition that’s associated with the
procedure plan definition version.
Stringcontext
Definition
62.0Small, 62.0Developer name of the procedure plan
definition version.
StringdeveloperName
62.0Small, 62.0Date and time from when the procedure
plan definition version is effective.
StringeffectiveFrom
62.0Small, 62.0Date and time until when the procedure
plan definition version is effective.
StringeffectiveTo
62.0Small, 62.0Details of the error encountered during the
processing of the API request.
Procedure Plan
Generic Error[]
error
62.0Small, 62.0Name of the template the procedure plan
definition is extended from.
StringinheritedFrom
62.0Small, 62.0List of sections of the procedure plan
definition that you can organize in any
Procedure Plan
Section[]
procedure
PlanSections
order. Each section must include a
procedure or a set of procedures to be
executed for a specific criteria.
64.0Small, 64.0Business processes that's specified that
requires a procedure plan for each sObject
and definition.
StringprocessType
62.0Small, 62.0Rank or the order of sequence to follow for
the processing of the procedure plan
definition version.
Integerrank
62.0Small, 62.0Mapping that’s used to read data from the
mapped object and populate the context
definition.
StringreadContext
Mapping
62.0Small, 62.0ID of the procedure plan definition version
record.
StringrecordId
62.0Small, 62.0Mapping that’s used to save data from the
context definition and populate the mapped
object.
StringsaveContext
Mapping
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
748
Response BodiesSalesforce Pricing

===== PAGE 763 =====

Procedure Plan Definitions
Output representation of the details of procedure plan definitions.
JSON example
{
"isSuccess": true,
"procedurePlanDefinitions": [
{
"description": "test description",
"developerName": "sample_test",
"name": "sample_test",
"primaryObject": "Account",
"procedurePlanDefinitionVersions": [
{
"active": false,
"developerName": "sample_test",
"effectiveFrom": "2024-07-09T00:00:00.000Z",
"contextDefinition": "SalesTransactionContext__stdctx",
"procedurePlanSections": [],
"rank": 1,
"readContextMapping": "ProductDiscoveryContextMapping",
"recordId": "1CvZ60000008OIaKAM",
"success": true
}
],
"recordId": "1FNZ60000004CAHOA2",
"success": true
},
{
"developerName": "PriceAdjustmentSchedule",
"name": "PriceAdjustmentSchedule",
"primaryObject": "PriceAdjustmentSchedule",
"procedurePlanDefinitionVersions": [
{
"active": false,
"developerName": "PriceAdjustmentSchedule",
"effectiveFrom": "2024-07-10T00:00:00.000Z",
"contextDefinition": "SalesTransactionContext__stdctx",
"procedurePlanSections": [],
"rank": 1,
"recordId": "1CvZ6000000CaRbKAK",
"success": true
}
],
"recordId": "1FNZ6000000CaSAOA0",
"success": true
}
]
}
749
Response BodiesSalesforce Pricing

===== PAGE 764 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Details of the error encountered during the
processing of the API request.
Procedure Plan
Generic Error[]
error
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccess
62.0Small, 62.0Details of a single procedure plan definition.Procedure Plan
Definition[]
procedure
PlanDefinitions
Procedure Plan Generic
Output representation of the details of the created procedure plan definition record.
JSON example
This example shows a sample response of the details of a procedure plan definition record, created by using the Procedure Plan
Definitions (POST) API.
{
"isSuccess":true,
"recordId":"1FNDU00000000EX4AY"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Details of the error encountered during the
processing of the API request.
Procedure Plan
Generic Error[]
error
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccess
62.0Small, 62.0ID of the created procedure plan definition
record.
StringrecordId
Procedure Plan Generic Error
Output representation of the error details related to the procedure plan definitions.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Code indicating the type of error.StringerrorCode
62.0Small, 62.0Message stating the reason for the error, if
any.
Stringmessage
Procedure Plan Option
Output representation of the details of a procedure plan option.
750
Response BodiesSalesforce Pricing

===== PAGE 765 =====

JSON example
"procedurePlanOptions": [
{
"expressionSetApiName": "Revenue_Mgmt_Default_Pricing_Procedure",
"expressionSetDefinition": "9QAZ60000004ECOOA2",
"expressionSetLabel": "Revenue Management Default Pricing Procedure",
"isSuccess": true,
"logic": "1 AND 2 AND 3",
"primaryObject": "Account",
"priority": 1,
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"dataType": "Text",
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"isSuccess": true,
"literalValue": "test",
"operator": "Equals",
"recordId": "1FiZ60000004C9cKAE"
},
{
"conditionSequence": 2,
"dataType": "Text",
"fieldObject": "BillingPostalCode",
"fieldPath": "BillingPostalCode",
"isSuccess": true,
"literalValue": "pramit",
"operator": "Equals",
"recordId": "1FiZ60000004C9dKAE"
},
{
"conditionSequence": 3,
"dataType": "Date",
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"isSuccess": true,
"literalValue": "2024-07-14",
"operator": "LessThan",
"recordId": "1FiZ60000004C9eKAE"
}
],
"recordId": "1FYZ6000000000fOAA",
"saveContextMapping": "AssetToSalesTransactionMapping"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Details of the error encountered during the
processing of the API request.
Procedure Plan
Generic Error[]
error
751
Response BodiesSalesforce Pricing

===== PAGE 766 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0API name of the expression set.Stringexpression
SetApiName
62.0Small, 62.0Expression set definition that’s associated
with this procedure plan option record.
StringexpressionSet
Definition
62.0Small, 62.0Label of the expression set that’s associated
with this procedure plan option record.
Stringexpression
SetLabel
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccess
62.0Small, 62.0Computation logic for the conditions
applied to a procedure plan option.
Stringlogic
62.0Small, 62.0Source object that’s used to create a
procedure with rule-based criteria.
StringprimaryObject
62.0Small, 62.0Priority for the specified criteria.Integerpriority
62.0Small, 62.0Details of the rule-based criteria for the
procedure.
Procedure Plan
Criterion[]
procedure
PlanCriterion
62.0Small, 62.0Mapping that’s used to read from the
mapped object and populate the context
definition.
StringreadContext
Mapping
62.0Small, 62.0ID of the procedure plan option record.StringrecordId
62.0Small, 62.0Mapping that’s used to save data from the
context definition and populate the mapped
object.
StringsaveContext
Mapping
Procedure Plan Section
Output representation of the details of a procedure plan section.
JSON example
"procedurePlanSections": [
{
"isInherited": false,
"isSuccess": true,
"procedurePlanOptions": [
{
"expressionSetApiName": "Revenue_Mgmt_Default_Pricing_Procedure",
"expressionSetDefinition": "9QAZ60000004ECOOA2",
"expressionSetLabel": "Revenue Management Default Pricing Procedure",
"isSuccess": true,
"logic": "1 AND 2 AND 3",
"primaryObject": "Account",
752
Response BodiesSalesforce Pricing

===== PAGE 767 =====

"priority": 1,
"procedurePlanCriterion": [
{
"conditionSequence": 1,
"dataType": "Text",
"fieldObject": "BillingCountry",
"fieldPath": "BillingCountry",
"isSuccess": true,
"literalValue": "test",
"operator": "Equals",
"recordId": "1FiZ60000004C9cKAE"
},
{
"conditionSequence": 2,
"dataType": "Text",
"fieldObject": "BillingPostalCode",
"fieldPath": "BillingPostalCode",
"isSuccess": true,
"literalValue": "pramit",
"operator": "Equals",
"recordId": "1FiZ60000004C9dKAE"
},
{
"conditionSequence": 3,
"dataType": "Date",
"fieldObject": "LastActivityDate",
"fieldPath": "LastActivityDate",
"isSuccess": true,
"literalValue": "2024-07-14",
"operator": "LessThan",
"recordId": "1FiZ60000004C9eKAE"
}
],
"recordId": "1FYZ6000000000fOAA",
"saveContextMapping": "AssetToSalesTransactionMapping"
}
],
"recordId": "1FRZ60000008OIAOA2",
"resolutionType": "RuleBased",
"sectionType": "PricingProcedure",
"sequence": 1,
"subSectionType": "PricingProcedure"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Details of the error encountered during the
processing of the API request.
Procedure Plan
Generic Error[]
error
62.0Small, 62.0Indicates whether the procedure plan
section is inherited from a template (true)
or not (false).
BooleanisInherited
753
Response BodiesSalesforce Pricing

===== PAGE 768 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccess
62.0Small, 62.0List of procedure plan options.Procedure Plan
Option[]
procedure
PlanOptions
62.0Small, 62.0ID of the procedure plan option record.StringrecordId
62.0Small, 62.0Type of resolution that’s used to filter the
procedure.
Stringresolution
Type
62.0Small, 62.0Type of section. Valid values are:StringsectionType
• PricingProcedure
• ProductDiscoveryProcedure
• ProductQualificationProcedure
• PricingDiscoveryProcedure
• DiscountSpreadServiceProcedure
• RatingProcedure
• Custom
• RatingDiscoveryProcedure
62.0Small, 62.0Sequence that’s followed for the processing
of the procedures.
Integersequence
62.0Small, 62.0Subsection that’s added to the procedure
plan definition.
StringsubSection
Type
Procedure Plan Section Evaluation Runtime
Output representation of the results from the procedure plan evaluation.
JSON example
"procedurePlanSections": [
{
"expressionSetApiName": "pricingProcedure_usageType_3",
"expressionSetDefinitionId": "9QAZ60000004Ef6OAE",
"expressionSetLabel": "pricingProcedure_usageType_3",
"sectionType": "PricingProcedure",
"sequence": 1,
"subSectionType": "Section1",
"usageType": "DefaultPricing"
},
{
"expressionSetApiName": "productQualification_usageType_3",
"expressionSetDefinitionId": "9QAZ60000004EfFOAU",
"expressionSetLabel": "productQualification_usageType_3",
"sectionType": "ProductQualificationProcedure",
754
Response BodiesSalesforce Pricing

===== PAGE 769 =====

"sequence": 3,
"subSectionType": "Section2",
"usageType": "ProductQualification"
},
{
"expressionSetApiName": "rating_usageType_2",
"expressionSetDefinitionId": "9QAZ60000004EfHOAU",
"expressionSetLabel": "rating_usageType_2",
"sectionType": "RatingProcedure",
"sequence": 2,
"subSectionType": "Section3",
"usageType": "DefaultRating"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0API name of the expression set.Stringexpression
SetApiName
62.0Small, 62.0ID of the expression set definition.StringexpressionSet
DefinitionId
62.0Small, 62.0Label of the expression set.Stringexpression
SetLabel
62.0Small, 62.0Mapping that’s used to read data from the
mapped object and populate the context
definition.
StringreadContext
Mapping
62.0Small, 62.0Mapping that’s used to save data from the
context definition and populate the mapped
object.
StringsaveContext
Mapping
62.0Small, 62.0Name of the evaluated section. Valid values
are:
StringsectionType
• PricingProcedure
• ProductDiscoveryProcedure
• ProductQualificationProcedure
• PricingDiscoveryProcedure
• DiscountSpreadServiceProcedure
• RatingProcedure
• Custom
• RatingDiscoveryProcedure
62.0Small, 62.0Sequence that’s followed for the processing
of the procedures.
Integersequence
62.0Small, 62.0Name of the evaluated subsection.StringsubSection
Type
755
Response BodiesSalesforce Pricing

===== PAGE 770 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Usage type of the procedure.StringusageType
Procedure Plan Evaluation
Output representation of the evaluation details of a procedure plan definition.
JSON example
"procedurePlanEvaluations":[
{
"errorMessage":"",
"id":"a01DU000000BylcYAC",
"isSuccess":true,
"primaryObject":"SignallingCustomEvaluation__c",
"result":{
"contextDefinition":"11ODU00000008Sw2AI",
"procedurePlanSections":[]
}
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Message indicating the error details, if any.StringerrorMessage
62.0Small, 62.0ID of the object used for evaluation.Stringid
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccess
62.0Small, 62.0Name of the object used for evaluation.StringprimaryObject
62.0Small, 62.0Results from the procedure plan evaluation.Procedure Plan
Evaluation Result[]
result
Procedure Plan Evaluation Response
Output representation of the evaluation details of a procedure plan definition.
JSON example
{
"isSuccess":true,
"procedurePlanEvaluations":[
{
"errorMessage":"",
"id":"a01DU000000BylcYAC",
"isSuccess":true,
"primaryObject":"SignallingCustomEvaluation__c",
756
Response BodiesSalesforce Pricing

===== PAGE 771 =====

"result":{
"contextDefinition":"11ODU00000008Sw2AI",
"procedurePlanSections":[]
}
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Message indicating the error details, if any.StringerrorMessage
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccess
62.0Small, 62.0Name of the procedure plan definition.Stringprocedure
PlanDefinition
Name
62.0Small, 62.0Evaluation details of the procedure plan.Procedure Plan
Evaluation[]
procedurePlan
Evaluations
Procedure Plan Evaluation Result
Output representation of the evaluation result of a procedure plan definition.
JSON example
"result":{
"contextDefinition":"11ODU00000008Sw2AI",
"procedurePlanSections":[]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Context definition that’s associated with the
procedure plan evaluation.
Stringcontext
Definition
62.0Small, 62.0Results from the procedure plan evaluation.Procedure Plan
Section Evaluation
Runtime[]
procedure
PlanSections
Pricing Process Execution Details for Line Items
Output representation of the pricing process execution details for the line items along with the error details and response generation
status.
JSON example
{
757
Response BodiesSalesforce Pricing

===== PAGE 772 =====

"error": {},
"isSuccess": true,
"lineItemDetailsList": [
{
"lineItemId": "LineItem1",
"status": "Success"
},
{
"lineItemId": "LineItem2",
"status": "Success"
},
{
"lineItemId": "LineItem3",
"status": "Failure"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Error encountered during the processing of
the API request.
Pricing Error
Response
error
63.0Small, 63.0Indicates whether the response was
generated successfully (true) or not
(false).
BooleanisSuccess
63.0Small, 63.0List of the line items for which the pricing
process is executed.
Line Item Details
Response []
lineItemDetails
List
Line Item Details Response
Output representation of the pricing process execution details for the line items.
JSON example
{
"lineItemDetailsList": [
{
"lineItemId": "LineItem1",
"status": "Success"
},
{
"lineItemId": "LineItem2",
"status": "Success"
},
{
"lineItemId": "LineItem3",
"status": "Failure"
}
]
}
758
Response BodiesSalesforce Pricing

===== PAGE 773 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0ID of the line item that the pricing process
is executed for.
StringlineItemId
63.0Small, 63.0Specifies whether the pricing process
execution for the line item is successful or
has failed. Valid values are:
Stringstatus
• Success
• Failure
Pricing Process Execution Response
Output representation of the details of a pricing process execution.
JSON example
{
"error": {},
"isSuccess": true,
"pricingProcessExecutionList": [
{
"executionId": "12345",
"executionType": "Pricing_Line",
"executionTypeId": "111_LineItem1",
"message": "The Pricing API execution was successful.",
"status": "Success"
},
{
"executionId": "12345",
"executionType": "Api_Execution",
"executionTypeId": "333",
"status": "Partial_Success"
},
{
"executionId": "12345",
"executionType": "Discovery",
"executionTypeId": "222",
"status": "Success"
},
{
"executionId": "12345",
"executionType": "Pricing",
"executionTypeId": "111",
"status": "Failure"
},
{
"executionId": "12345",
"executionType": "Discovery_Line",
"executionTypeId": "222_LineItem1",
"status": "Partial_Success"
759
Response BodiesSalesforce Pricing

===== PAGE 774 =====

},
{
"executionId": "12345",
"executionType": "Pricing_Line",
"executionTypeId": "111_LineItem2",
"status": "Failure"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Error encountered during the processing of
the API request.
Pricing Error
Response
error
63.0Small, 63.0Indicates whether the response was
generated successfully (true) or not
(false).
BooleanisSuccess
63.0Small, 63.0List of the execution details of the pricing
process.
Pricing Process
Execution List []
pricingProcess
ExecutionList
Pricing Process Execution List
Output representation of the execution details for different types of the pricing processes.
JSON example
{
"pricingProcessExecutionList": [
{
"executionId": "12345",
"executionType": "Pricing_Line",
"executionTypeId": "111_LineItem1",
"message": "The Pricing API execution was successful.",
"status": "Success"
},
{
"executionId": "12345",
"executionType": "Api_Execution",
"executionTypeId": "333",
"status": "Success"
},
{
"executionId": "12345",
"executionType": "Discovery",
"executionTypeId": "222",
"status": "Success"
},
{
"executionId": "12345",
"executionType": "Pricing",
760
Response BodiesSalesforce Pricing

===== PAGE 775 =====

"executionTypeId": "111",
"status": "Failure"
},
{
"executionId": "12345",
"executionType": "Discovery_Line",
"executionTypeId": "222_LineItem1",
"status": "Success"
},
{
"executionId": "12345",
"executionType": "Pricing_Line",
"executionTypeId": "111_LineItem2",
"status": "Failure"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Unique ID that's generated each time a
pricing process is executed.
StringexecutionId
63.0Small, 63.0Type of the execution that's defined
internally within the pricing API.
StringexecutionType
63.0Small, 63.0Unique execution type ID that's generated
internally for process executions, such as
pricing or discovery procedures.
StringexecutionTypeId
63.0Small, 63.0Message that's generated when a pricing
process is executed.
Stringmessage
63.0Small, 63.0Execution process status for a line item. Valid
values are:
Stringstatus
• Failure
• Partial_Success—Applies to
Pricing  and Discovery
procedures when execution for some
line items fails.
• Success
Pricing Simulation Input Variables With Data
Output representation of the pricing simulation variables with data.
JSON example
{
"error": "",
"simulationInputJsonWithData": "{\"SalesTransaction\": [{\"PriceBooks\":
761
Response BodiesSalesforce Pricing

===== PAGE 776 =====

\"01sxx0000005ptpAAA\",\"SalesTransactionItem\": [{\"LineItemQuantity\":
4,\"ProductSellingModel\": null,\"Product\": \"01txx0000006i2SAAQ\",\"LineItem\":
\"0QLxx0000004C92GAE\"},{\"LineItemQuantity\": 3,\"ProductSellingModel\":
null,\"Product\": \"01txx0000006i2TAAQ\",\"LineItem\": \"0QLxx0000004C93GAE\"}]}]}",
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
64.0Small, 64.0Returns the cause of error, if any. For a
successful request, this API returns an empty
string.
Stringerror
64.0Small, 64.0Resultant simulation input variables with
quote or order data such as ID, which was
specified in the query parameters.
StringsimulationInput
JsonWithData
64.0Small, 64.0Indicates whether the request was
successful (true) or not (false).
Booleansuccess
Salesforce Pricing Apex Reference
Use built-in Apex classes and interfaces grouped by namespace.
RevSignaling Namespace
The RevSignaling Namespace includes properties and methods to extend the standard procedure plan implementation through
custom logic. Using this extension support, you can tailor implementations to your unique requirements.
SEE ALSO:
Apex Developer Guide: Getting Started with Apex
RevSignaling Namespace
The RevSignaling Namespace includes properties and methods to extend the standard procedure plan implementation through custom
logic. Using this extension support, you can tailor implementations to your unique requirements.
Usage
To use this namespace, enable the Procedure Plan Orchestration for Pricing toggle from the Revenue Settings page from Setup.
The RevSignaling  namespace includes these classes.
ProcedurePlan Class
Represents the instance of the current pricing procedure plan that you're working on.
SignalingApexProcessor Interface
Defines the context-driven orchestration logic based on procedure plan instance and contextual instance.
762
Salesforce Pricing Apex ReferenceSalesforce Pricing

===== PAGE 777 =====

TransactionRequest Class
Represents the transaction request to the signaling Apex processor.
TransactionResponse Class
Represents the transaction response from the signaling Apex processor.
TransactionStatus Enum
Specifies the status of the transaction request.
ProcedurePlan Class
Represents the instance of the current pricing procedure plan that you're working on.
Namespace
RevSignaling on page 762
ProcedurePlan Properties
Learn more about the properties that are available with the ProcedurePlan class.
ProcedurePlan Properties
Learn more about the properties that are available with the ProcedurePlan class.
The ProcedurePlan  class includes these properties.
prevStepOutput
Output of the previous step that's executed and passed to the next step.
prevStepOutput
Output of the previous step that's executed and passed to the next step.
Signature
public Map<String,ANY> prevStepOutput {get; set;}
RevSignaling.ProcedurePlan, prevStepOutput
Property Value
Type: Map<String,Object>
SignalingApexProcessor Interface
Defines the context-driven orchestration logic based on procedure plan instance and contextual instance.
Namespace
RevSignaling on page 762
763
RevSignaling NamespaceSalesforce Pricing

===== PAGE 778 =====

Usage
Here's a sample implementation of the SignalingApexProcessor interface.
public class SignalingApexProcessorImpl implements RevSignaling.SignalingApexProcessor {
public RevSignaling.TransactionResponseexecute(RevSignaling.TransactionRequestrequest)
{
System.debug('Executing SampleValidClass...');
System.debug('Procedure Plan: ' + request.procedurePlanInstance);
System.debug('Context Instance: ' + request.ctxInstanceId);
// Add your logic here
// Return the response
RevSignaling.TransactionResponse response = new RevSignaling.TransactionResponse();
response.status = RevSignaling.TransactionStatus.SUCCESS;
response.message = 'Apex method was successfully executed!';
return response;
}
}
Refer to Customize Your Pricing Procedures With Apex Hooks for additional samples that cover unique pricing scenarios by implementing
this interface.
SignalingApexProcessor Methods
The SignalingApexProcessor method executes the specified transaction request, which returns the corresponding response.
SignalingApexProcessor Example Implementation
Refer to the example implementation of the SignalingApexProcessor interface to define a context-driven orchestration logic.
SignalingApexProcessor Methods
The SignalingApexProcessor method executes the specified transaction request, which returns the corresponding response.
The SignalingApexProcessor  class includes these methods.
execute(var1)
Executes the parameter that's specified in the instance of a transaction request.
execute(var1)
Executes the parameter that's specified in the instance of a transaction request.
Signature
public RevSignaling.TransactionResponse execute(RevSignaling.TransactionRequest var1)
RevSignaling.SignalingApexProcessor, execute, [RevSignaling.TransactionRequest],
RevSignaling.TransactionResponse
764
RevSignaling NamespaceSalesforce Pricing

===== PAGE 779 =====

Parameters
var1
Type: RevSignaling.TransactionRequest on page 765
Instance of the TransactionRequest class containing the execution parameter.
Return Value
Type: RevSignaling.TransactionResponse on page 767
Response from the orchestration.
SignalingApexProcessor Example Implementation
Refer to the example implementation of the SignalingApexProcessor interface to define a context-driven orchestration logic.
This is an example implementation of the RevSignaling.SignalingApexProcessor  interface.
public class SignalingApexProcessorImpl implements RevSignaling.SignalingApexProcessor {
public RevSignaling.TransactionResponseexecute(RevSignaling.TransactionRequestrequest)
{
System.debug('Executing SampleValidClass...');
System.debug('Procedure Plan: ' + request.procedurePlanInstance);
System.debug('Context Instance: ' + request.ctxInstanceId);
// Add your logic here
// Return the response
RevSignaling.TransactionResponse response = new RevSignaling.TransactionResponse();
response.status = RevSignaling.TransactionStatus.SUCCESS;
response.message = 'Apex method was successfully executed!';
return response;
}
}
TransactionRequest Class
Represents the transaction request to the signaling Apex processor.
Namespace
RevSignaling on page 762
TransactionRequest Constructors
Learn more about the available constructors with the TransactionRequest class.
TransactionRequest Properties
Learn more about the properties that are available with the TransactionRequest class.
765
RevSignaling NamespaceSalesforce Pricing

===== PAGE 780 =====

TransactionRequest Constructors
Learn more about the available constructors with the TransactionRequest class.
The TransactionRequest  class includes these constructors.
TransactionRequest(procedurePlanInstance, ctxInstanceId)
Creates an instance of the TransactionRequest class to specify the procedure plan and context instance ID.
TransactionRequest(procedurePlanInstance, ctxInstanceId)
Creates an instance of the TransactionRequest class to specify the procedure plan and context instance ID.
Signature
public TransactionRequest(RevSignaling.ProcedurePlanprocedurePlan, String ctxInstanceId)
RevSignaling.TransactionRequest, newinstance, [RevSignaling.ProcedurePlan, String],
RevSignaling.TransactionRequest
Parameters
procedurePlan
Type: RevSignaling.ProcedurePlan on page 763
Instance of the procedure plan.
ctxInstanceId
Type: String
ID of the context.
TransactionRequest Properties
Learn more about the properties that are available with the TransactionRequest class.
The TransactionRequest  class includes these properties.
ctxInstanceId
Set the context ID.
procedurePlanInstance
Set the instance of the procedure plan.
ctxInstanceId
Set the context ID.
Signature
public String ctxInstanceId {get; set;}
RevSignaling.TransactionRequest, ctxInstanceId
766
RevSignaling NamespaceSalesforce Pricing

===== PAGE 781 =====

Property Value
Type: String
procedurePlanInstance
Set the instance of the procedure plan.
Signature
public RevSignaling.ProcedurePlan procedurePlanInstance {get; set;}
RevSignaling.TransactionRequest, procedurePlanInstance
Property Value
Type: RevSignaling.ProcedurePlan on page 763
TransactionResponse Class
Represents the transaction response from the signaling Apex processor.
Namespace
RevSignaling on page 762
TransactionResponse Properties
Learn more about the properties that are available with the TransactionResponse class.
TransactionResponse Properties
Learn more about the properties that are available with the TransactionResponse class.
The TransactionResponse  class includes these properties.
message
Get the message from the transaction response.
status
Get the status of the request from the transaction response.
message
Get the message from the transaction response.
Signature
public String message {get; set;}
RevSignaling.TransactionResponse, message
767
RevSignaling NamespaceSalesforce Pricing

===== PAGE 782 =====

Property Value
Type: String
status
Get the status of the request from the transaction response.
Signature
public RevSignaling.TransactionStatus status {get; set;}
RevSignaling.TransactionResponse, status
Property Value
Type: RevSignaling.TransactionStatus on page 768
TransactionStatus Enum
Specifies the status of the transaction request.
Enum Values
The RevSignaling.TransactionStatus  enum includes these values.
DescriptionValue
The transaction request has failed.FAILED
RevSignaling.TransactionStatus,
FAILED
The transaction request was successful.SUCCESS
RevSignaling.TransactionStatus,
SUCCESS
Salesforce Pricing Standard Invocable Actions
Learn more about the standard invocable actions available with Salesforce Pricing.
Run Salesforce Headless Pricing Action
Invoke the Pricing Connect API by providing the pricing data and details of a context, pricing procedure, and price waterfall.
768
Salesforce Pricing Standard Invocable ActionsSalesforce Pricing

===== PAGE 783 =====

Run Salesforce Pricing Action
Invoke the Pricing Connect API by providing the context, pricing procedure, and price waterfall details.
SEE ALSO:
Actions Developer Guide: Overview
REST API Developer Guide: Invocable Actions Standard
Run Salesforce Headless Pricing Action
Invoke the Pricing Connect API by providing the pricing data and details of a context, pricing procedure, and price waterfall.
This action is available in API version 60.0 and later.
Special Access Rules
The Run Salesforce Headless Pricing action is available in Enterprise, Unlimited, and Developer Editions where Salesforce Pricing is
enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/runSalesforceHeadlessPricing
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearer token
Inputs
DetailsInput
Type
string
contextDefinitionId
Description
Required.
ID of the context definition record that’s used to build the pricing data.
Type
string
contextMappingId
Description
Required.
769
Run Salesforce Headless Pricing ActionSalesforce Pricing

===== PAGE 784 =====

DetailsInput
ID of the context-mapping record that identifies which Salesforce object and mappings to use
to build the pricing data.
Type
string
discoveryProcedure
Description
Name of the discovery procedure that’s used to execute the discovery process.
Type
boolean
displayContext
Description
Indicates whether to display the context structure for pricing (true) or not (false).
Type
string
effectiveDate
Description
Date when the pricing rules, as specified in the pricing procedure, are applied.
The effectiveDate  parameter determines which pricing procedure to execute when
multiple active versions of pricing procedures are available with different date ranges.
Type
boolean
isHighVolumeLineItems
Description
Indicates whether the pricing API returns pricing details for more than 100 line items (true) or
not (false).
Type
boolean
isSkipWaterfall
Description
Indicates whether to generate the price waterfall data (true) or not (false).
Type
boolean
persistContext
Description
Indicates whether to store the context (true) or not (false).
Type
string
pricingData
Description
Required.
770
Run Salesforce Headless Pricing ActionSalesforce Pricing

===== PAGE 785 =====

DetailsInput
JSON data that’s used to build the pricing data. The JSON must be escaped. If you're using this
data within a Flow, then the JSON data must not be escaped.
Type
string
pricingProcedureId
Description
Required.
ID or API name of the pricing procedure used for calculating the prices. A pricing procedure is
represented as an Expression Set Definition in the system.
If you’re an Experience Cloud user, specify the name of the pricing procedure.
Type
boolean
skipDiscovery
Description
Indicates whether to skip executing the discovery procedure (true) or not (false).
Type
boolean
taggedData
Description
Indicates whether the associated context node contains a key (true) or not (false).
Type
boolean
useSessionScopedContext
Description
Indicates whether to store the context in a session (true) or a request (false).
Outputs
DetailsOutput
Type
string
contextDetails
Description
Context structure for pricing that’s generated when the displayContext  parameter is set
to true.
Type
string
executionId
Description
ID of the executed pricing data.
771
Run Salesforce Headless Pricing ActionSalesforce Pricing

===== PAGE 786 =====

DetailsOutput
Type
string
pricingProcessErrors
Description
Errors that are generated due to context tags in a pricing process.
Type
string
pricingProcessStatus
Description
Status of the pricing process, which is executed as an API call.
Type
string
pricingResult
Description
Outcome of the executed pricing process that’s based on the output tags defined in the associated
context definition.
Example
POST
This sample request is for the Run Salesforce Headless Pricing action.
{
"inputs": [
{
"contextMappingId": "11jSB000002Bn13YAC",
"contextDefinitionId": "11OSB0000000WSv2AM",
"pricingProcedureId": "9QLSB0000001lT74AI",
"discoveryProcedure": "ES1",
"displayContext": true,
"effectiveDate": "2023-11-16T12:20:00.000Z",
"isHighVolumeLineItems": true,
"skipDiscovery": true,
"taggedData": false,
"pricingData":
"{\"SalesTransaction\":{\"businessObjectType\":\"SalesTransaction\",\"Pricebook\":\"01sDE0000000LoeYAE\",\"CurrencyIsoCode\":\"USD\",\"SalesTransactionItem\":[{\"businessObjectType\":\"SalesTransactionItem\",\"Product\":\"01tDE000000FU99YAG\",\"ProductSellingModel\":\"0jPDE000000042K2AQ\",\"Quantity\":5,\"StartDate\":\"2023-11-16T12:20:00.000Z\",\"SalesTransactionItemSource\":\"LINE_ITEM1\"}]}}",
"isSkipWaterfall": false,
"persistContext": true,
"useSessionScopedContext": false
}
]
}
This sample response is for the Run Salesforce Headless Pricing action.
{
"actionName": "runSalesforceHeadlessPricing",
772
Run Salesforce Headless Pricing ActionSalesforce Pricing

===== PAGE 787 =====

"errors": null,
"isSuccess": true,
"outputValues": {
"contextDetails": {
"SalesTransaction": [
{
"PriceBooks": "01sxx0000005q3VAAQ",
"Subtotal": 587.2095,
"PriceAdjustmentSchedule": "84Xxx0000004CMxEAM",
"EffectiveDate": "2024-02-12T00:00:00.000Z",
"SalesTransactionItem": [
{
"LineItemQuantity": 5,
"ProductSellingModel": "0jPxx000000009hEAA",
"DerivedPricingAttribute": false,
"Product": "01txx0000006iLwAAI",
"LineItem": "LineItem1",
"NetUnitPrice": 117.4419,
"SalesTrxnAdjustmentGroup": [
{
"AdjustmentType": "Percentage",
"AdjustmentValue": 10
}
]
}
]
}
]
},
"executionId": "1708488641379821",
"pricingProcessStatus": "Completed",
"pricingResult": {
"StartDate": [
{
"value": 1700137200000,
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5",
"CTX_d3b9ffd5-2be7-4366-92d8-c2bcf03b69ed"
],
"errors": [],
"isSuccess": true
}
],
"NetUnitPrice": [
{
"value": 115,
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5",
"CTX_d3b9ffd5-2be7-4366-92d8-c2bcf03b69ed"
],
"errors": [],
"isSuccess": true
}
],
773
Run Salesforce Headless Pricing ActionSalesforce Pricing

===== PAGE 788 =====

"ProductSellingModel": [
{
"value": "0jPDE000000042K2AQ",
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5",
"CTX_d3b9ffd5-2be7-4366-92d8-c2bcf03b69ed"
],
"errors": [],
"isSuccess": true
}
],
"Pricebook": [
{
"value": "01sDE0000000LoeYAE",
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5"
],
"errors": [],
"isSuccess": true
}
],
"NetTotalPrice": [
{
"value": 1150,
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5",
"CTX_d3b9ffd5-2be7-4366-92d8-c2bcf03b69ed"
],
"errors": [],
"isSuccess": true
}
],
"Subtotal": [
{
"value": 1150,
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5"
],
"errors": [],
"isSuccess": true
}
],
"Quantity": [
{
"value": 10,
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5",
"CTX_d3b9ffd5-2be7-4366-92d8-c2bcf03b69ed"
],
"errors": [],
"isSuccess": true
}
],
"Product": [
774
Run Salesforce Headless Pricing ActionSalesforce Pricing

===== PAGE 789 =====

{
"value": "01tDE000000FU99YAG",
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5",
"CTX_d3b9ffd5-2be7-4366-92d8-c2bcf03b69ed"
],
"errors": [],
"isSuccess": true
}
],
"CurrencyIsoCode": [
{
"value": "USD",
"dataPath": [
"CTX_ece1667e-7a09-40ab-9718-23bdc179a0a5"
],
"errors": [],
"isSuccess": true
}
]
}
},
"version": 1
}
SEE ALSO:
Salesforce Help: Invoke Salesforce Headless Pricing in a Flow
Run Salesforce Pricing Action
Invoke the Pricing Connect API by providing the context, pricing procedure, and price waterfall details.
This action is available in API version 60.0 and later. You can use this action with Flows only. To use this action with an API tool such as
Postman, see Run Salesforce Headless Pricing Action.
Special Access Rules
The Run Salesforce Pricing action is available in Developer, Enterprise, and Unlimited Editions where Salesforce Pricing is enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/runSalesforcePricing
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearer token
775
Run Salesforce Pricing ActionSalesforce Pricing

===== PAGE 790 =====

Inputs
DetailsInput
Type
string
contextInstanceId
Description
Required.
ID of the context data that’s used to build the pricing procedure. Get the context instance ID by
invoking the Context Service API. See Context Service (POST).
Type
string
discoveryProcedure
Description
Name of the discovery procedure that’s used to execute the discovery process of the pricing
data.
Type
string
effectiveDate
Description
Date when the pricing rules, as specified in the pricing procedure, are applied.
The effectiveDate  parameter determines which pricing procedure to execute when
multiple active versions of pricing procedures are available with different date ranges.
Type
boolean
isDeveloperName
Description
Indicates whether the input value in a procedure must use the API name of the pricing (true)
or the field name (false).
Type
boolean
isSkipWaterfall
Description
Indicates whether the price waterfall data must be generated (true) or not (false).
Type
string
pricingProcedureName
Description
Required.
Name of the pricing procedure record that’s used to execute the pricing process.
776
Run Salesforce Pricing ActionSalesforce Pricing

===== PAGE 791 =====

DetailsInput
Type
boolean
skipDiscovery
Description
Indicates whether to skip executing the discovery procedure (true) or not (false).
Outputs
DetailsOutput
Type
string
executionId
Description
ID of the executed pricing data.
Example
POST
This sample request is for the Run Salesforce Pricing action.
{
"inputs": [
{
"contextInstanceId": "32f2c894-ba5e-41c0-91e4-2ab5826f579b",
"pricingProcedureName": "PricingAction",
"isSkipWaterfall": false,
"skipDiscovery": false,
"isDeveloperName": true,
"effectiveDate": "2023-11-16T12:20:00.000Z",
"discoveryProcedure": "ES1"
}
]
}
This sample response is for the Run Salesforce Pricing action.
{
"actionName": "runSalesforcePricing",
"errors": null,
"isSuccess": true,
"outputValues": {
"executionId": "2QTurzG2NRQ5bgrjvvqyh"
},
777
Run Salesforce Pricing ActionSalesforce Pricing

===== PAGE 792 =====

"version": 1
}
SEE ALSO:
Salesforce Help: Invoke Salesforce Pricing in a Flow
Salesforce Pricing Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
Flow for Salesforce Pricing
Represents the metadata associated with a flow. With Flow, you can create an application that navigates users through a series of
screens to query and update records in the database. You can also execute logic and provide branching capability based on user
input to build dynamic applications.
IndustriesPricingSettings
Represents the settings for Salesforce Pricing.
PricingActionParameters
Represents the pricing action that's associated with a context definition and pricing procedure.
PricingRecipe
Represents the data models or sets of objects of a particular cloud that the pricing data store consumes during design time and run
time.
ProcedureOutputResolution
Represents the pricing resolution for a pricing element determined by using strategy name and formula.
SEE ALSO:
Metadata API Developer Guide: Understanding Metadata API
Flow for Salesforce Pricing
Represents the metadata associated with a flow. With Flow, you can create an application that navigates users through a series of screens
to query and update records in the database. You can also execute logic and provide branching capability based on user input to build
dynamic applications.
FlowActionCall
Salesforce Pricing exposes additional actionType values for the FlowActionCall Metadata type.
DescriptionField TypeField Name
Required.InvocableActionType
(enumeration of
type string)
actionType
The action type. Additional valid values only for Salesforce Pricing include:
778
Salesforce Pricing Metadata API TypesSalesforce Pricing

===== PAGE 793 =====

DescriptionField TypeField Name
• runSalesforcePricing— Invoke the Pricing Connect API
by providing the context, pricing procedure, and price waterfall
details.
• runSalesforceHeadlessPricing— Invoke the Pricing
Connect API by providing the pricing data and details of a context,
pricing procedure, and price waterfall.
IndustriesPricingSettings
Represents the settings for Salesforce Pricing.
Parent Type and Manifest Access
This type extends the Metadata metadata type and inherits its fullName field.
In the package manifest, all the settings metadata types for the org are accessed using the “Settings” name. See Settings for more details.
File Suffix and Directory Location
IndustriesPricingSettings  values are stored in the IndustriesPricingSettings.settings  file in the
settings  folder. The .settings  files are different from other named components, because there’s only one settings file for each
settings component.
Version
IndustriesPricingSettings components are available in API version 60.0 and later.
Special Access Rules
This metadata type is available with Salesforce Pricing.
Fields
DescriptionField Name
Field Type
boolean
enableDebugPriceLogs
Description
Indicates whether to use price logs to diagnose and resolve pricing issues (true) or
not (false). The default value is false. Available in API version 63.0 and later.
Field Type
boolean
enableHighAvailability
779
IndustriesPricingSettingsSalesforce Pricing

===== PAGE 794 =====

DescriptionField Name
Description
Reserved for internal use.
Field Type
boolean
enableHighestPriceCompliance
Description
Indicates whether to track the maximum price of a product over a period of 30 days
(true) or not (false). The default value is false. Available in API version 64.0
and later.
Field Type
boolean
enableLowestPriceCompliance
Description
Indicates whether to track the minimum price of a product over a period of 30 days
(true) or not (false). The default value is false. Available in API version 62.0
and later.
Field Type
boolean
enablePricingProcParallelization
Description
Indicates whether to run pricing elements in parallel within a pricing procedure to
optimize the performance of the pricing execution process (true) or not (false).
The default value is false. Available in API version 64.0 and later.
Field Type
boolean
enablePricingWaterfall
Description
Indicates whether to enable Price Waterfall (true) or not (false). The default value
is false. Price Waterfall provides insights that include price breakups and reasons
for every step of the pricing process.
Field Type
boolean
enablePricingWaterfallPersistence
Description
Indicates whether to enable Price Waterfall Persistence (true) or not (false). The
default value is false. Price Waterfall Persistence stores the process logs that provide
insights into the internal pricing processes.
Field Type
boolean
enableSalesforcePricing
Description
Indicates whether to enable Salesforce Pricing (true) or not (false). The default
value is false.
780
IndustriesPricingSettingsSalesforce Pricing

===== PAGE 795 =====

Declarative Metadata Sample Definition
This example shows a sample IndustriesPricingSettings component.
<IndustriesPricingSettings xmlns="http://soap.sforce.com/2006/04/metadata">
<enableDebugPriceLogs>true</enableDebugPriceLogs>
<enableHighAvailability>true</enableHighAvailability>
<enableHighestPriceCompliance>true</enableHighestPriceCompliance>
<enableLowestPriceCompliance>true</enableLowestPriceCompliance>
<enablePricingProcParallelization>true</enablePricingProcParallelization>
<enablePricingWaterfall>true</enablePricingWaterfall>
<enablePricingWaterfallPersistence>true</enablePricingWaterfallPersistence>
<enableSalesforcePricing>true</enableSalesforcePricing>
</IndustriesPricingSettings>
This example shows a sample package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>IndustriesPricing</members>
<name>Settings</name>
</types>
<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
The wildcard character *  (asterisk) in the package.xml manifest file doesn’t apply to metadata types for feature settings. The wildcard
applies only when retrieving all settings, not for an individual setting. For details, see Settings. For information about using the manifest
file, see Deploying and Retrieving Metadata with the Zip File.
PricingActionParameters
Represents the pricing action that's associated with a context definition and pricing procedure.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Parent Type
This type extends the Metadata metadata type and inherits its fullName field.
File Suffix and Directory Location
PricingActionParameters components have the suffix .pricingActionParameters  and are stored in the
pricingActionParameters  folder.
Version
PricingActionParameters components are available in API version 60.0 and later.
781
PricingActionParametersSalesforce Pricing

===== PAGE 796 =====

Special Access Rules
This metadata type is available with Salesforce Pricing.
Fields
DescriptionField Name
Field Type
string
contextDefinition
Description
Required.
Context definition record that's associated with the pricing action.
Field Type
string
contextMapping
Description
Required.
Context mapping record that's associated with the pricing action.
Field Type
string
developerName
Description
Required.
Unique name of the pricing action parameter record.
The name must begin with a letter and use only alphanumeric characters and
underscores. The name must not include spaces, end with an underscore, or have two
consecutive underscores.
Field Type
dateTime
effectiveFrom
Description
Required.
Date and time from when the pricing action becomes effective.
Field Type
dateTime
effectiveTo
Description
Date and time till when the pricing action is in effect.
Field Type
string
masterLabel
782
PricingActionParametersSalesforce Pricing

===== PAGE 797 =====

DescriptionField Name
Description
Required.
Master label of the pricing action parameter.
Field Type
string
objectName
Description
Name of the object that's associated with the pricing action. Valid values are:
• Case
• Contract
• Opportunity
• Order
• Quote
• SalesAgreement
• WorkOrder
Field Type
string
pricingProcedure
Description
Pricing procedure record that's associated with this pricing action.
Declarative Metadata Sample Definition
The following is an example of a PricingActionParameters component.
<PricingActionParameters xmlns="http://soap.sforce.com/2006/04/metadata">
<developerName>CMEDefaultActionParameters</developerName>
<objectName>ORDER</objectName>
<pricingProcedure>PP</pricingProcedure>
<effectiveFrom>2024-04-08T07:32:00.000Z</effectiveFrom>
<effectiveTo>2024-04-11T07:32:00.000Z</effectiveTo>
<contextDefinition>SalesTransactionContext__stdctx</contextDefinition>
<contextMapping>SalesAgreementEntitiesMapping</contextMapping>
<masterLabel>PAP_test</masterLabel>
</PricingActionParameters>
The following is an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>*</members>
<name>PricingActionParameters</name>
</types>
783
PricingActionParametersSalesforce Pricing

===== PAGE 798 =====

<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
This metadata type supports the wildcard character *  (asterisk) in the package.xml  manifest file. For information about using the
manifest file, see Deploying and Retrieving Metadata with the Zip File.
PricingRecipe
Represents the data models or sets of objects of a particular cloud that the pricing data store consumes during design time and run
time.
Parent Type
This type extends the Metadata metadata type and inherits its fullName field.
File Suffix and Directory Location
PricingRecipe components have the suffix .pricingRecipe  and are stored in the pricingRecipe  folder.
Version
PricingRecipe components are available in API version 60.0 and later.
Special Access Rules
This metadata type is available with Salesforce Pricing.
Fields
DescriptionField Name
Field Type
ExpressionSetDefinition
defaultPricingProcedure
Description
Expression set definition that's associated with this pricing recipe setting.
Field Type
string
defaultPricingProcedureDeveloperName
Description
For internal use only.
Field Type
string
defaultPricingProcedureId
784
PricingRecipeSalesforce Pricing

===== PAGE 799 =====

DescriptionField Name
Description
ID of the pricing procedure of the pricing recipe.
Field Type
string
developerName
Description
Required.
API name of the pricing recipe.
Field Type
boolean
isActive
Description
Indicates whether the pricing recipe is active (true) or not (false).
The default value is false
Field Type
boolean
isInternal
Description
Indicates whether the price recipe record is created internally by the Salesforce platform
(true) or not (false).
The default value is false
Field Type
string
masterLabel
Description
Required.
Name for pricing recipe that's defined when the pricing recipe is created.
Field Type
PricingRecipeTableMapping[]
pricingRecipeTableMapping
Description
Mapping of the pricing components of a lookup table with the chosen pricing recipe.
PricingRecipeTableMapping
Represents the mapping of the lookup table with the chosen pricing recipe.
DescriptionField Name
Field Type
boolean
isInternal
785
PricingRecipeSalesforce Pricing

===== PAGE 800 =====

DescriptionField Name
Description
Indicates whether the price recipe field mapping record is created internally by the
Salesforce platform (true) or not (false).
The default value is false.
Field Type
DecisionTable
lookupTable
DecisionMatrixDefinition
Description
Lookup table that's associated with either a decision matrix or decision table.
Field Type
string
lookupTableDeveloperName
Description
For internal use only.
Field Type
string
pricingComponentType
Description
Pricing component field data that the decision table is built on.
Valid values are:
• AttributeDiscount
• BundleDiscount
• DerivedPricing
• ListPrice
• PriceAdjustmentMatrix
• PromotionsDiscount
• VolumeDiscount
• VolumeTierDiscount
• DiscountDistributionService. This value is available in API version
60.0 and later.
• MinimumPrice. Available in API version 62.0 and later.
Field Type
PricingProcedureOutputMap[]
pricingProcedureOutputMapList
Description
List of the mappings of the outputs of the pricing procedures to the associated lookup
tables. Available in API version 60.0 and later.
Field Type
string
pricingRecipe
786
PricingRecipeSalesforce Pricing

===== PAGE 801 =====

DescriptionField Name
Description
Required.
Pricing data store that's associated with this pricing recipe field mapping.
PricingProcedureOutputMap
Represents the mapping of the outputs of the pricing procedures to the associated lookup tables. Each record specifies the output
mapping of the associated lookup table based on the pricing component type specified in the PricingRecipeTableMapping object.
DescriptionField Name
Field Type
string
fieldName
Description
For internal use only.
Field Type
boolean
isPricingRecipeActive
Description
Indicates whether the associated pricing recipe is active (true) or not (false).
The default value is false.
Field Type
string
outputFieldName
Description
Field name that contains the output type that's generated from the pricing element.
Field Type
string
outputFieldNameString
Description
Derived field that references a specific column in a decision table or decision matrix.
Field Type
string
outputType
Description
Output type that's generated from a pricing element.
Valid values are:
• AdjustmentType
• AdjustmentValue
• CustomOutput
• HashOutput
787
PricingRecipeSalesforce Pricing

===== PAGE 802 =====

DescriptionField Name
• UnitPrice
Field Type
PricingElementType (enumeration of type string)
pricingElementType
Description
Type of pricing element, which is a derived field from
PricingRecipeTableMapping.PricingComponentType.
Valid values are:
• AssetDiscovery
• AttributeDiscount
• BundleDiscount
• DerivedPricing
• DiscountDistributionService
• ListPrice
• MinimumPrice
• PriceAdjustmentMatrix
• PriceRevision
• PromotionsDiscount
• RuleFetch
• VolumeDiscount
• VolumeTierDiscount
Declarative Metadata Sample Definition
The following is an example of a PricingRecipe component.
<PricingRecipe xmlns="http://soap.sforce.com/2006/04/metadata">
<defaultPricingProcedureId> </defaultPricingProcedureId>
<developerName>CMEDefaultRecipe</developerName>
<isActive>false</isActive>
<isInternal>false</isInternal>
<masterLabel>CMEDefaultRecipe</masterLabel>
<pricingRecipeTableMapping>
<isInternal>false</isInternal>
<lookupTableDeveloperName>Bundle_Based_Adjustment_Decision_Table</lookupTableDeveloperName>
<pricingComponentType>CUSTOMDISCOUNT</pricingComponentType>
<fileBasedDecisionTableName>Bundle Based Adjustment
Entries</fileBasedDecisionTableName>
<pricingProcedureOutputMapList>
<fieldName>AdjustmentValue</fieldName>
<isPricingRecipeActive>false</isPricingRecipeActive>
<outputFieldName>0lPxx000000000f</outputFieldName>
788
PricingRecipeSalesforce Pricing

===== PAGE 803 =====

<outputFieldNameString>false</outputFieldNameString>
<outputType>AdjustmentValue</outputType>
<pricingElementType>BundleDiscount</pricingElementType>
</pricingProcedureOutputMapList>
<pricingProcedureOutputMapList>
<fieldName>AdjustmentType</fieldName>
<isPricingRecipeActive>false</isPricingRecipeActive>
<outputFieldName>0lPxx000000000m</outputFieldName>
<outputFieldNameString>false</outputFieldNameString>
<outputType>AdjustmentType</outputType>
<pricingElementType>BundleDiscount</pricingElementType>
</pricingProcedureOutputMapList>
<pricingRecipe>CMEDefaultRecipe</pricingRecipe>
</pricingRecipeTableMapping>
</PricingRecipe>
The following is an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>*</members>
<name>PricingRecipe</name>
</types>
<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
This metadata type supports the wildcard character *  (asterisk) in the package.xml  manifest file. For information about using the
manifest file, see Deploying and Retrieving Metadata with the Zip File.
ProcedureOutputResolution
Represents the pricing resolution for a pricing element determined by using strategy name and formula.
Parent Type
This type extends the Metadata metadata type and inherits its fullName field.
File Suffix and Directory Location
ProcedureOutputResolution components have the suffix .procedureOutputResolution  and are stored in the
procedureOutputResolution  folder.
Version
ProcedureOutputResolution components are available in API version 63.0 and later.
789
ProcedureOutputResolutionSalesforce Pricing

===== PAGE 804 =====

Special Access Rules
This metadata type is available with Salesforce Pricing.
Fields
DescriptionField Name
Field Type
string
developerName
Description
Required.
API name of the procedure output resolution.
Field Type
string
formula
Description
Required.
Stores the encoded formula as text.
Field Type
boolean
isActive
Description
Required.
Indicates whether the strategy is active (true) or not (false).
Field Type
boolean
isInternal
Description
Reserved for internal use.
Field Type
string
masterLabel
Description
Required.
A user-friendly name for the procedure output resolution, which is defined when the
ProcedureOutputResolution record is created.
Field Type
string
pricingElement
Description
Required.
790
ProcedureOutputResolutionSalesforce Pricing

===== PAGE 805 =====

DescriptionField Name
Pricing element on which the procedure output resolution is defined.
Declarative Metadata Sample Definition
Here's an example of a ProcedureOutputResolution component.
<?xml version="1.0" encoding="UTF-8"?>
<ProcedureOutputResolution xmlns="http://soap.sforce.com/2006/04/metadata">
<developerName>ProcedureOutputResolution</developerName>
<isActive>false</isActive>
<isInternal>false</isInternal>
<masterLabel>Procedure Output Resolution</masterLabel>
<pricingElement>ListPrice</pricingElement>
<formula>MAX(ListPrice)</formula>
</ProcedureOutputResolution>
Here's an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>*</members>
<name>ProcedureOutputResolution</name>
</types>
<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
This metadata type supports the wildcard character *  (asterisk) in the package.xml  manifest file. For information about using the
manifest file, see Deploying and Retrieving Metadata with the Zip File.
Salesforce Pricing Tooling API Objects
Tooling API exposes metadata used in developer tooling that you can access through REST or SOAP. Tooling API’s SOQL capabilities for
many metadata types allow you to retrieve smaller pieces of metadata.
PricingActionParameters
Represents a pricing action associated to a context definition and a pricing procedure. This object is available in API version 60.0 and
later.
PricingProcedureOutputMap
Represents the mapping of the outputs of the pricing procedures to the associated lookup tables. Each record specifies the output
mapping of the associated lookup table based on the pricing component type specified in the Pricing Recipe Table Mapping object.
This object is available in API version 60.0 and later.
791
Salesforce Pricing Tooling API ObjectsSalesforce Pricing

===== PAGE 806 =====

PricingRecipe
Represents one out of various data models or sets of entities of a particular cloud that'll be consumed by the pricing data store during
design and run time. This object is available in API version 60.0 and later.
PricingRecipeTableMapping
Represents the mapping of pricing components of a lookup table with the chosen pricing recipe. This object is available in API
version 60.0 and later.
ProcedureOutputResolution
Represents the pricing resolution for an pricing element determined using strategy name and formula. This object is available in API
version 63.0 and later.
ProcedurePlanCriterion
Represents a criterion within a procedure plan option record. This object is available in API version 62.0 and later.
ProcedurePlanDefinition
Represents the setup of a unified procedure from a list of multiple procedures that can be sequenced in any order based on business
needs. Each procedure plan definition contains sections and subsections where procedures can be configured by using a lookup
table or rule-based criteria. This object is available in API version 62.0 and later.
ProcedurePlanDefinitionVersion
Represents the versions for a procedure plan definition. Multiple versions under a procedure plan definition must be active at a time,
which can be resolved at run time using the rank field. This object is available in API version 62.0 and later.
ProcedurePlanOption
Represents the selection criteria of how a procedure can be configured for a selected procedure plan section record. This object is
available in API version 62.0 and later.
ProcedurePlanSection
Represents various procedure setup sections for a procedure plan definition. Each section enables the setup of a procedure of a type
that can be further determined by using a rule-based criteria or it can be set based on a selected lookup table. This object is available
in API version 62.0 and later.
ProcedurePlanVariable
Represents the setup for any adhoc user-defined variable that can be linked to a procedure plan definition record. This object is
available in API version 62.0 and later.
SEE ALSO:
Tooling API Developer Guide: Introducing Tooling API
PricingActionParameters
Represents a pricing action associated to a context definition and a pricing procedure. This object is available in API version 60.0 and
later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
792
PricingActionParametersSalesforce Pricing

===== PAGE 807 =====

Fields
DetailsField
Type
string
ContextDefinition
Properties
Create, Filter, Group, Sort, Update
Description
The context definition record associated with the pricing action.
Type
string
ContextMapping
Properties
Create, Filter, Group, Sort, Update
Description
The context mapping record that's associated with the pricing action.
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The unique name of the pricing action parameter record.
This name must begin with a letter and use only alphanumeric characters and underscores.
It can't include spaces, end with an underscore, or have two consecutive underscores.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
The date and time when the pricing action comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time till when the pricing action is in effect.
Type
picklist
Language
793
PricingActionParametersSalesforce Pricing

===== PAGE 808 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The language of the pricing action parameter.
Possible values are:
• da—Danish
• de—German
• en_US—English
• es—Spanish
• es_MX—Spanish (Mexico)
• fi—Finnish
• fr—French
• it—Italian
• ja—Japanese
• ko—Korean
• nl_NL—Dutch
• no—Norwegian
• pt_BR—Portuguese (Brazil)
• ru—Russian
• sv—Swedish
• th—Thai
• zh_CN—Chinese (Simplified)
• zh_TW—Chinese (Traditional)
Type
string
MasterLabel
Properties
Create, Filter, Group, Sort, Update
Description
The master label of the pricing action parameter.
Type
string
NamespacePrefix
Properties
Filter, Group, Nillable, Sort
Description
The namespace prefix that is associated with this object. Each Developer Edition org that
creates a managed package has a unique namespace prefix. Limit: 15 characters. You can
refer to a component in a managed package by using
the namespacePrefix__componentName notation.
794
PricingActionParametersSalesforce Pricing

===== PAGE 809 =====

DetailsField
The namespace prefix can have one of the following values.
• In Developer Edition organizations, the namespace prefix is set to the namespace prefix
of the organization for all objects that support it. There’s an exception if an object is in
an installed managed package. In that case, the object has the namespace prefix of the
installed managed package. This field’s value is the namespace prefix of the Developer
Edition organization of the package developer.
• In organizations that are Developer Edition organizations, NamespacePrefix is only set
for objects that are part of an installed managed package. There’s no namespace prefix
for all other objects.
Type
picklist
ObjectName
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the object associated to the pricing action.
Possible values are:
• Case
• Contract
• Opportunity
• Order
• Quote
• SalesAgreement
• WorkOrder
Type
string
PricingProcedure
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The pricing procedure record associated with this pricing action.
PricingProcedureOutputMap
Represents the mapping of the outputs of the pricing procedures to the associated lookup tables. Each record specifies the output
mapping of the associated lookup table based on the pricing component type specified in the Pricing Recipe Table Mapping object.
This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
795
PricingProcedureOutputMapSalesforce Pricing

===== PAGE 810 =====

Fields
DetailsField
Type
boolean
IsPricingRecipeActive
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates if the pricing recipe is active (true) or not (false).
The default value is false.
Type
reference
LookupField
Properties
Filter, Group, Nillable, Sort
Description
Definition of the fields that are used for this lookup.
Type
reference
OutputFieldNameId
Properties
Create, Filter, Group, Sort, Update
Description
The field name containing the output type generated from the pricing element.
This field is a polymorphic relationship field.
Relationship Name
OutputFieldName
Relationship Type
Lookup
Refers To
CalculationMatrixColumn, DecisionTableParameter
Type
string
OutputFieldNameString
Properties
Filter, Group, Nillable, Sort
Description
This is a derived field that references a specific column in a decision table or decision matrix.
Type
picklist
OutputType
796
PricingProcedureOutputMapSalesforce Pricing

===== PAGE 811 =====

DetailsField
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The output type generated from a pricing element.
Possible values are:
• AdjustmentType—Adjustment Type
• AdjustmentValue—Adjustment Value
• CustomOutput—Custom Output
• HashOutput—Hash Output
• UnitPrice—Unit Price
• UpperBound—Unit Price
• LowerBound—Unit Price
• TierValue—Unit Price
• TierType—Unit Price
Type
picklist
PricingComponentType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The pricing component field data on which the decision table is built.
Possible values are:
• AttributeDiscount—Attribute Based Discount
• BundleDiscount—Bundle Based Discount
• DerivedPricing
• DiscountDistributionService—Discount Distribution Service
• ListPrice—List Price
• PriceAdjustmentMatrix
• PromotionsDiscount
• VolumeDiscount—Volume Based Discount
• VolumeTierDiscount—Tier Discount
• RuleFetch
• AssetDiscovery
Type
reference
PricingRecipeTableMappingId
Properties
Create, Filter, Group, Sort, Update
797
PricingProcedureOutputMapSalesforce Pricing

===== PAGE 812 =====

DetailsField
Description
The mapping of pricing components of a lookup table with the chosen pricing recipe.
This field is a relationship field.
Relationship Name
PricingRecipeTableMapping
Relationship Type
Lookup
Refers To
PricingRecipeTableMapping
PricingRecipe
Represents one out of various data models or sets of entities of a particular cloud that'll be consumed by the pricing data store during
design and run time. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Special Access Rules
Fields
DetailsField
Type
picklist
BusinessVertical
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The business vertical associated with the procedure output resolution record.
Possible values are:
• RLM
Type
reference
DefaultPricingProcedureId
Properties
Create, Filter, Group, Nillable, Sort, Update
798
PricingRecipeSalesforce Pricing

===== PAGE 813 =====

DetailsField
Description
The expression set definition or Salesforce flow definition associated with this pricing recipe
settings.
This field is a relationship field.
Relationship Name
DefaultPricingProcedure
Relationship Type
Lookup
Refers To
ExpressionSetDefinition
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The developer name of the pricing recipe.
Type
boolean
IsActive
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the pricing recipe is active (true) or not (false).
The default value is false.
Type
boolean
IsInternal
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates if the price recipe record is created internally by the Salesforce platform (true) or
not (false).
The default value is false.
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The languages in which pricing recipe is supported.
799
PricingRecipeSalesforce Pricing

===== PAGE 814 =====

DetailsField
Possible values are:
• da—Danish
• de—German
• en_US—English
• es—Spanish
• es_MX—Spanish (Mexico)
• fi—Finnish
• fr—French
• it—Italian
• ja—Japanese
• ko—Korean
• nl_NL—Dutch
• no—Norwegian
• pt_BR—Portuguese (Brazil)
• ru—Russian
• sv—Swedish
• th—Thai
• zh_CN—Chinese (Simplified)
• zh_TW—Chinese (Traditional)
Type
string
MasterLabel
Properties
Create, Filter, Group, Sort, Update
Description
A user-friendly name for pricing recipe, which is defined when the pricing recipe is created.
Type
string
NamespacePrefix
Properties
Filter, Group, Nillable, Sort
Description
The namespace prefix that is associated with this object. Each Developer Edition org that
creates a managed package has a unique namespace prefix. Limit: 15 characters. You can
refer to a component in a managed package by using
the namespacePrefix__componentName notation.
The namespace prefix can have one of the following values.
• In Developer Edition organizations, the namespace prefix is set to the namespace prefix
of the organization for all objects that support it. There’s an exception if an object is in
an installed managed package. In that case, the object has the namespace prefix of the
800
PricingRecipeSalesforce Pricing

===== PAGE 815 =====

DetailsField
installed managed package. This field’s value is the namespace prefix of the Developer
Edition organization of the package developer.
• In organizations that are Developer Edition organizations, NamespacePrefix is only set
for objects that are part of an installed managed package. There’s no namespace prefix
for all other objects.
PricingRecipeTableMapping
Represents the mapping of pricing components of a lookup table with the chosen pricing recipe. This object is available in API version
60.0 and later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Fields
DetailsField
Type
string
FileBasedDecisionTableName
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Name of the file-based decision table.
Type
boolean
IsInternal
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates if the price recipe field mapping record is created internally by the Salesforce
platform (true) or not (false).
The default value is false.
Type
reference
LookupTableId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The lookup table associated with the mapped fields.
This field is a polymorphic relationship field.
801
PricingRecipeTableMappingSalesforce Pricing

===== PAGE 816 =====

DetailsField
Relationship Name
LookupTable
Relationship Type
Lookup
Refers To
DecisionMatrixDefinition, DecisionTable
Type
Pricing Element Type enumerated list
PricingComponentType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The pricing component field data on which the decision table is built.
Possible values are:
• AttributeDiscount—Attribute Based Discount
• BundleDiscount—Bundle Based Discount
• DerivedPricing
• ListPrice—List Price
• PriceAdjustmentMatrix
• PromotionsDiscount
• VolumeDiscount—Volume Based Discount
• VolumeTierDiscount—Tier Discount
• DiscountDistributionService. This value is available in API version 60.0 and
later.
• MinimumPrice. This value is available in API version 62.0 and later.
• RuleFetch. This value is available in API version 64.0 and later.
• AssetDiscovery. This value is available in API version 64.0 and later.
Type
reference
PricingRecipeId
Properties
Create, Filter, Group, Sort
Description
The pricing data store associated with this pricing recipe field mappings.
This field is a relationship field.
Relationship Name
PricingRecipe
Relationship Type
Lookup
802
PricingRecipeTableMappingSalesforce Pricing

===== PAGE 817 =====

DetailsField
Refers To
PricingRecipe
ProcedureOutputResolution
Represents the pricing resolution for an pricing element determined using strategy name and formula. This object is available in API
version 63.0 and later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Fields
DetailsField
Type
picklist
BusinessVertical
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The business vertical associated with the procedure output resolution record.
Possible values are:
• RLM
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The name of the procedure output resolution.
Type
string
Formula
Properties
Create, Filter, Group, Sort, Update
Description
The formula function used to determine the minimum or maximum price of a product. The
supported operations are MIN and MAX.
803
ProcedureOutputResolutionSalesforce Pricing

===== PAGE 818 =====

DetailsField
Type
boolean
IsActive
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the procedure output resolution is active (true) or not (false). Only active
procedure output resolutions can be applied to a procedure.
The default value is false.
Type
boolean
IsInternal
Properties
Create, Defaulted on create, Filter, Group, Sort
Description
Indicates if the procedure output resolution record is created internally by the Salesforce
platform (true) or not (false).
The default value is false.
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The languages in which pricing recipe is supported.
Possible values are:
• da—Danish
• de—German
• en_US—English
• es—Spanish
• es_MX—Spanish (Mexico)
• fi—Finnish
• fr—French
• it—Italian
• ja—Japanese
• ko—Korean
• nl_NL—Dutch
• no—Norwegian
• pt_BR—Portuguese (Brazil)
• ru—Russian
804
ProcedureOutputResolutionSalesforce Pricing

===== PAGE 819 =====

DetailsField
• sv—Swedish
• th—Thai
• zh_CN—Chinese (Simplified)
• zh_TW—Chinese (Traditional)
Type
string
MasterLabel
Properties
Create, Filter, Group, Sort, Update
Description
A user-friendly name for procedure output resolution, which is defined when the procedure
output resolution record is created.
Type
string
NamespacePrefix
Properties
Filter, Group, Nillable, Sort
Description
The namespace prefix that is associated with this object. Each Developer Edition org that
creates a managed package has a unique namespace prefix. Limit: 15 characters. You can
refer to a component in a managed package by using
the namespacePrefix__componentName notation.
The namespace prefix can have one of the following values.
• In Developer Edition organizations, the namespace prefix is set to the namespace prefix
of the organization for all objects that support it. There’s an exception if an object is in
an installed managed package. In that case, the object has the namespace prefix of the
installed managed package. This field’s value is the namespace prefix of the Developer
Edition organization of the package developer.
• In organizations that are Developer Edition organizations, NamespacePrefix is only set
for objects that are part of an installed managed package. There’s no namespace prefix
for all other objects.
Type
picklist
PricingElement
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the pricing element on which the procedure output resolution is defined.
Possible values are:
• ListPrice—List Price
• MinimumPrice—Price Tracking
• PriceAdjustmentMatrix—Price Adjustment Matrix
805
ProcedureOutputResolutionSalesforce Pricing

===== PAGE 820 =====

ProcedurePlanCriterion
Represents a criterion within a procedure plan option record. This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
Fields
DetailsField
Type
string
ActualValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The user-defined value that’s compared to the value of the sObject field value.
Type
picklist
DataType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The data type of the field from the selected object.
Type
string
FieldPath
Properties
Create, Filter, Group, Sort, Update
Description
The path of the field used in a procedure in relation to the object that the field belongs to.
Type
string
ObjectField
Properties
Create, Filter, Group, Sort, Update
806
ProcedurePlanCriterionSalesforce Pricing

===== PAGE 821 =====

DetailsField
Description
The Salesforce object field value used to resolve the procedure plan option.
Type
picklist
Operator
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The operator used by the procedure plan criterion.
Valid values are:
• Equals
• GreaterThan
• GreaterThanOrEquals
• In
• IsNotNull
• IsNull
• LessThan
• LessThanOrEquals
• NotEquals
• NotIn
Type
reference
ProcedurePlanOptionId
Properties
Create, Filter, Group, Sort
Description
The procedure plan option associated with the procedure plan criterion record.
This field is a relationship field.
Relationship Name
ProcedurePlanOption
Relationship Type
Master-detail
Refers To
ProcedurePlanOption (the master object)
Type
int
Sequence
Properties
Create, Filter, Group, Sort
807
ProcedurePlanCriterionSalesforce Pricing

===== PAGE 822 =====

DetailsField
Description
The sequence in which the conditions defined in the procedure plan criteria are processed.
ProcedurePlanDefinition
Represents the setup of a unified procedure from a list of multiple procedures that can be sequenced in any order based on business
needs. Each procedure plan definition contains sections and subsections where procedures can be configured by using a lookup table
or rule-based criteria. This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
Fields
DetailsField
Type
textarea
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The description of the procedure plan definition.
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The unique name of the procedure plan definition record.
This name must begin with a letter and use only alphanumeric characters and underscores.
It can't include spaces, end with an underscore, or have two consecutive underscores.
Type
picklist
Language
808
ProcedurePlanDefinitionSalesforce Pricing

===== PAGE 823 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The language of the procedure plan definition.
Valid values are:
• da—Danish
• de—German
• en_US—English
• es—Spanish
• es_MX—Spanish (Mexico)
• fi—Finnish
• fr—French
• it—Italian
• ja—Japanese
• ko—Korean
• nl_NL—Dutch
• no—Norwegian
• pt_BR—Portuguese (Brazil)
• ru—Russian
• sv—Swedish
• th—Thai
• zh_CN—Chinese (Simplified)
• zh_TW—Chinese (Traditional)
Type
string
MasterLabel
Properties
Create, Filter, Group, Sort, Update
Description
The master label of the procedure plan definition.
Type
string
NamespacePrefix
Properties
Filter, Group, Nillable, Sort
Description
The namespace prefix that is associated with this object. Each Developer Edition org that
creates a managed package has a unique namespace prefix. Limit: 15 characters. You can
refer to a component in a managed package by using
the namespacePrefix__componentName notation.
809
ProcedurePlanDefinitionSalesforce Pricing

===== PAGE 824 =====

DetailsField
The namespace prefix can have one of the following values.
• In Developer Edition organizations, the namespace prefix is set to the namespace prefix
of the organization for all objects that support it. There’s an exception if an object is in
an installed managed package. In that case, the object has the namespace prefix of the
installed managed package. This field’s value is the namespace prefix of the Developer
Edition organization of the package developer.
• In organizations that are Developer Edition organizations, NamespacePrefix is only set
for objects that are part of an installed managed package. There’s no namespace prefix
for all other objects.
Type
string
PrimaryObject
Properties
Create, Filter, Group, idLookup, Nillable, Sort
Description
The object associated to the procedure plan definition. The fields in the object are used as
variables in the procedure plan criterion.
Type
picklist
ProcessType
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Identify the business processes that need a procedure plan for each SObject and definition.
Possible values are:
• Billing
• DRO
• DeepClone—Deep Clone
• Default
• ProductDiscovery—Product Discovery
• RLM
The default value is Default.
ProcedurePlanDefinitionVersion
Represents the versions for a procedure plan definition. Multiple versions under a procedure plan definition must be active at a time,
which can be resolved at run time using the rank field. This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
810
ProcedurePlanDefinitionVersionSalesforce Pricing

===== PAGE 825 =====

Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
Fields
DetailsField
Type
picklist
ContextDefinition
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The context definition associated with the procedure plan definition record.
Valid values are:
• 11ODU00000007Zx2AI
• 11ODU000000084F2AQ
• CollectionPlanEvent__stdctx
• CommerceCartContextDefinition__stdctx
• SalesTransactionContext__stdctx
• TestContextService__stdctx
• TestDynamicAttribute__stdctx
• TestExtendedDefinition__stdctx
Type
string
DefaultReadContextMapping
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The default read context mapping used to read from the mapped object and populate the
context definition.
Type
string
DefaultSaveContextMapping
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The save context mapping used to save from the context definition and populate the mapped
object.
811
ProcedurePlanDefinitionVersionSalesforce Pricing

===== PAGE 826 =====

DetailsField
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The unique name of the procedure plan definition version record.
This name must begin with a letter and use only alphanumeric characters and underscores.
It can't include spaces, end with an underscore, or have two consecutive underscores.
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
The date and time when the procedure plan definition comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the procedure plan definition is no longer in effect.
Type
string
InheritedFrom
Properties
Create, Filter, Group, idLookup, Nillable, Sort
Description
The template from which this procedure plan definition is created.
Type
boolean
IsActive
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates if this procedure plan definition version is active (true) or not (false).
The default value is false.
Type
reference
ProcedurePlanDefinitionId
812
ProcedurePlanDefinitionVersionSalesforce Pricing

===== PAGE 827 =====

DetailsField
Properties
Create, Filter, Group, Sort
Description
The procedure plan definition associated with this procedure plan definition version record.
This field is a relationship field.
Relationship Name
ProcedurePlanDefinition
Relationship Type
Master-detail
Refers To
ProcedurePlanDefinition (the master object)
Type
int
Rank
Properties
Create, Filter, Group, Sort, Update
Description
The current rank of the procedure plan definition version that’s used to determine which
procedure plan definition version is executed .
ProcedurePlanOption
Represents the selection criteria of how a procedure can be configured for a selected procedure plan section record. This object is
available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
Fields
DetailsField
Type
reference
ApexClassId
813
ProcedurePlanOptionSalesforce Pricing

===== PAGE 828 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The Apex class associated with the procedure plan option record.
This field is a relationship field.
Relationship Name
ApexClass
Refers To
ApexClass
Type
string
ApexClassName
Properties
Filter, Group, Nillable, Sort
Description
The name of the Apex class associated with the procedure plan option record.
Type
string
CriteriaLogic
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The computation logic for the various conditions applied to an option.
Type
reference
CtxDefinitionOutputFieldId
Properties
Filter, Group, Nillable, Sort
Description
The context definition field that’s associated with the decision table.
This field is a relationship field.
Relationship Name
CtxDefinitionOutputField
Refers To
DecisionTableParameter
Type
reference
CtxMappingOutputFieldId
Properties
Filter, Group, Nillable, Sort
814
ProcedurePlanOptionSalesforce Pricing

===== PAGE 829 =====

DetailsField
Description
The context mapping field that’s associated with the decision table.
This field is a relationship field.
Relationship Name
CtxMappingOutputField
Refers To
DecisionTableParameter
Type
reference
DecisionTableId
Properties
Filter, Group, Nillable, Sort
Description
The decision table associated with the pricing procedure.
This field is a relationship field.
Relationship Name
DecisionTable
Refers To
DecisionTable
Type
string
ExpressionSetApiName
Properties
Filter, Group, Nillable, Sort
Description
The API name of the expression set.
Type
reference
ExpressionSetDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The expression set definition associated with the procedure plan option record.
This field is a relationship field.
Relationship Name
ExpressionSetDefinition
Refers To
ExpressionSetDefinition
Type
string
ExpressionSetLabel
815
ProcedurePlanOptionSalesforce Pricing

===== PAGE 830 =====

DetailsField
Properties
Filter, Group, Nillable, Sort
Description
The label of the expression set definition.
Type
reference
ExpressionSetOutputFieldId
Properties
Filter, Group, Nillable, Sort
Description
The expression set output field that’s associated with the decision table.
This field is a relationship field.
Relationship Name
ExpressionSetOutputField
Refers To
DecisionTableParameter
Type
string
PrimaryObject
Properties
Filter, Group, Nillable, Sort
Description
The procedure plan definition associated with the procedure plan option record.
Type
int
Priority
Properties
Create, Filter, Group, Sort
Description
The order in which the options are executed.
Type
reference
ProcedurePlanSectionId
Properties
Create, Filter, Group, Sort
Description
The procedure plan section associated with the procedure plan option record.
This field is a relationship field.
Relationship Name
ProcedurePlanSection
816
ProcedurePlanOptionSalesforce Pricing

===== PAGE 831 =====

DetailsField
Relationship Type
Master-detail
Refers To
ProcedurePlanSection (the master object)
Type
string
ReadContextMapping
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The read context mapping used to read from the mapped object and populate the context
definition.
Type
string
SaveContextMapping
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The save context mapping used to save from the context definition and populate the mapped
object.
ProcedurePlanSection
Represents various procedure setup sections for a procedure plan definition. Each section enables the setup of a procedure of a type
that can be further determined by using a rule-based criteria or it can be set based on a selected lookup table. This object is available in
API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
817
ProcedurePlanSectionSalesforce Pricing

===== PAGE 832 =====

Fields
DetailsField
Type
string
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The description of the procedure plan section.
Type
boolean
IsInherited
Properties
Create, Defaulted on create, Filter, Group, Sort
Description
Indicates if the section is inherited from a template (true) ot not (false).
The default value is false.
Type
string
Phase
Properties
Create, Filter, Nillable, Sort, Update
Description
The phase associated with the procedure plan section record.
Type
reference
ProcedurePlanVersionId
Properties
Create, Filter, Group, Sort
Description
The procedure plan version associated with this procedure plan section record.
This field is a relationship field.
Relationship Name
ProcedurePlanVersion
Relationship Type
Master-detail
Refers To
ProcedurePlanDefinitionVersion (the master object)
Type
picklist
ResolutionType
818
ProcedurePlanSectionSalesforce Pricing

===== PAGE 833 =====

DetailsField
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of resolution used to filter the procedure.
Valid values are:
• Default
• RuleBased
Type
picklist
SectionType
Properties
Create, Filter, Group, Restricted picklist, Sort
Description
The type of procedure section.
Valid values are:
• Custom
• PricingDiscoveryProcedure
• PricingProcedure
• ProductDiscoveryProcedure
Type
int
Sequence
Properties
Create, Filter, Group, Sort, Update
Description
The sequence in which the procedures are processed.
Type
string
SubSectionType
Properties
Create, Filter, Group, Sort
Description
The procedure subsection added to the procedure plan definition.
ProcedurePlanVariable
Represents the setup for any adhoc user-defined variable that can be linked to a procedure plan definition record. This object is available
in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
819
ProcedurePlanVariableSalesforce Pricing

===== PAGE 834 =====

Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
Fields
DetailsField
Type
picklist
DataType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The data type of the input procedure plan variable.
Type
string
DefaultValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The default value for the user-defined procedure plan variable.
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The unique name of the procedure plan variable record.
This name must begin with a letter and use only alphanumeric characters and underscores.
It can't include spaces, end with an underscore, or have two consecutive underscores.
Type
string
Label
Properties
Create, Filter, Group, Sort, Update
Description
The label of the procedure plan variable.
Type
reference
ProcedurePlanVersionId
820
ProcedurePlanVariableSalesforce Pricing

===== PAGE 835 =====

DetailsField
Properties
Create, Filter, Group, Sort
Description
The procedure plan version associated with the procedure plan variable record.
This field is a relationship field.
Relationship Name
ProcedurePlanVersion
Relationship Type
Master-detail
Refers To
ProcedurePlanDefinitionVersion (the master object)
821
ProcedurePlanVariableSalesforce Pricing

===== PAGE 836 =====

