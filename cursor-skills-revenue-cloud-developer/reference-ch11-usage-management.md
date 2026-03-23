---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 11 — Usage Management

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 11 Usage Management
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions
Provide transparent, accurate, and efficient management of usage
data and estimated usage amount to enhance revenue
management capabilities.
In this chapter ...
• Usage Management
Standard Objects
• Usage Management
Fields on Standard
Objects
• Usage Management
Standard Invocable
Actions
• Usage Management
Business APIs
• Usage Management
Metadata API Types
1824

===== PAGE 1839 =====

Usage Management Standard Objects
The Usage Management data model provides objects and fields to set up and manage consumption of usage-based products.
ProductUsageGrant
Represents the details of a grant associated with a resource, product, or service, such as the purchased quantity, renewal and rollover
policy, and validity of the grant. This object is available in API version 62.0 and later.
ProductUsageResource
Represents the mapping of a product and its usage resources. This object is available in API version 64.0 and later.
ProductUsageResourcePolicy
Represents the policies applicable to the usage resource when it’s associated with a sellable product. These policies are derived from
the parent usage resource and can be overridden when setting up usage modeling.This object is available in API version 65 and
later.
TransactionUsageEntitlement
Represents the details of each usage entitlement that's granted with the purchased sellable product, such as quantity and date when
the entitlements were granted. This object is available in API version 63.0 and later.
UnitOfMeasure
Defines the units and systems of units used to account for quantities of a usage resource. This object is available for usage management
in API version 62.0 and later.
UnitOfMeasureClass
Represents a standard unit of measure dimension. This object is available in API version 63.0 and later.
UsageBillingPeriodItem
Represents the calculated overages for the usage entitlement and the amount that's charged for these overages. This object is
available in API version 63.0 and later.
UsageCmtAssetRelatedObj
Represents the relation between an asset for the commitment-based usage product and an asset, account, contract, or custom
object. This object is available in API version 64.0 and later.
UsageCommitmentPolicy
Represents the set of rules that determines how commitments are applied to a usage resource. This object is available in API version
65 and later.
UsageEntitlementAccount
Represents the entitlement account details related to the asset that holds the wallet with the granted units. This object is available
in API version 63.0 and later.
UsageEntitlementBucket
Represents a usage entitlement that's granted with the sellable product. This object is available in API version 63.0 and later.
UsageEntitlementEntry
Represents the usage entitlement details, such as the usage consumption, rollovers, and details of expired units for each tenure. This
object is available in API version 63.0 and later.
UsageGrantRenewalPolicy
Represents a policy about the rollover of a usage grant. This object is available in API version 62.0 and later.
UsageGrantRolloverPolicy
Represents a policy about the rollover of a usage grant.This object is available in API version 62.0 and later.
1825
Usage Management Standard ObjectsUsage Management

===== PAGE 1840 =====

UsageOveragePolicy
Represents the set of rules that determine the management of usage resource’s units consumed beyond the granted limit. This
object is available in API version 65 and later.
UsagePrdGrantBindingPolicy
Represents the association of a usage resource's grants with a sellable product. This object is available in API version 63.0 and later.
UsageRatableSummary
Represents the aggregation of the usage summaries that are used to calculate the rate at which the overages are charged. This
object is available in API version 63.0 and later.
UsageRatableSumCmtAssetRt
Represents the rate that’s calculated and applicable for the usage resource associated with the commitment assets related to an
anchor. This object is available in API version 65.0 and later.
UsageResource
Represents an entitlement granted to a user or party by a provider, such as data storage, computing power, bandwidth, or any other
product or service. Additionally, this object is used to represent resources consumed over time. This object is available in API version
62.0 and later.
UsageResourcePolicy
Represents the policies applicable to the usage resource whether it’s associated with a sellable product or not. This object is available
in API version 65 and later.
UsageResourceBillingPolicy
Represents information about how the usage is accumulated before rating a usage resource.This object is available in API version
62.0 and later.
UsageSummary
Represents the aggregation of the entries in the transaction journal for a usage entitlement for a specified period. This object is
available in API version 63.0 and later.
SEE ALSO:
Object Reference for the Salesforce Platform: Overview of Salesforce Objects and Fields
SOAP API Developer Guide: Introduction to SOAP API
ProductUsageGrant
Represents the details of a grant associated with a resource, product, or service, such as the purchased quantity, renewal and rollover
policy, and validity of the grant. This object is available in API version 62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
To create, update, and delete product usage grant records, you must have the Usage Management Design Time permission set license.
1826
ProductUsageGrantUsage Management

===== PAGE 1841 =====

Fields
DetailsField
Type
picklist
DrawdownOrder
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The order that's used to debit entitlement consumption from the usage entitlement
bucket.
Valid values are:
• ExpiringFirst
• GrantedFirst
• GrantedLast
This field is deprecated and will be retired in a future version.
Type
dateTime
EffectiveEndDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time until when the grant remains effective.
Type
dateTime
EffectiveStartDate
Properties
Create, Filter, Sort, Update
Description
The date and time when the grant becomes effective.
Type
string
Label
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The identifying label for the product usage grant.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
1827
ProductUsageGrantUsage Management

===== PAGE 1842 =====

DetailsField
Description
The date when this record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
picklist
OverageChargeable
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether to charge for overages.
Valid values are:
• No
• Yes
This field is deprecated and will be retired in a future version.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the product usage grant.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
ProductOfferId
Properties
Create, Filter, Group, Sort, Update
Description
The sellable product that grants the usage resource.
This field is a relationship field. Available in API versions 62.0 and 63.0.
1828
ProductUsageGrantUsage Management

===== PAGE 1843 =====

DetailsField
Relationship Name
ProductOffer
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product selling model associated with the product usage grant. This field is
available in API version 65.0 and later.
This field is a relationship field.
Relationship Name
ProductSellingModel
Refers To
ProductSellingModel
Type
string
ProductUsageGrantNum
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The number of each resource grant map that starts with one and is consecutive.
Type
reference
ProductUsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The product usage resource associated with the product usage grant. Available in
API version 64.0 and later.
This field is a relationship field.
Relationship Name
ProductUsageResource
Refers To
ProductUsageResource
Type
double
Quantity
1829
ProductUsageGrantUsage Management

===== PAGE 1844 =====

DetailsField
Properties
Create, Filter, Nillable, Sort, Update
Description
The quantity of the granted resource.
Type
reference
RenewalPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The grant renewal policy associated with the product usage grant.
This field is a relationship field.
Relationship Name
RenewalPolicy
Refers To
UsageGrantRenewalPolicy
Type
reference
RolloverPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The grant rollover policy associated with the product usage grant.
This field is a relationship field.
Relationship Name
RolloverPolicy
Refers To
UsageGrantRolloverPolicy
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the product usage grant.
Valid values are:
• Active
• Draft
• Inactive
1830
ProductUsageGrantUsage Management

===== PAGE 1845 =====

DetailsField
Type
picklist
Type
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of model that defines how the usage resource is consumed.
Valid values are:
• Commit
• Grant
The default value is Grant. Available in API version 64.0 and later.
Type
reference
UnitOfMeasureClassId
Properties
Create, Filter, Group, Sort, Update
Description
The unit of measure class associated with the product usage grant.
This field is a relationship field.
Relationship Name
UnitOfMeasureClass
Refers To
UnitOfMeasureClass
Type
reference
UnitOfMeasureId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The unit for measure associated with the product usage grant. This value when
specified, overrides the default unit of measure defined in the associated unit of
measure class.
This field is a relationship field.
Relationship Name
UnitOfMeasure
Refers To
UnitOfMeasure
Type
reference
UsageDefinitionProductId
1831
ProductUsageGrantUsage Management

===== PAGE 1846 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The sellable product associated with the usage resource that's used to retrieve tax
policy, calculate rating during overages, and other invoicing actions.
This field is a relationship field.
Relationship Name
UsageDefinitionProduct
Refers To
Product2
Type
picklist
UsageModelType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The ID of the unit of measure associated with the product. The type of usage model
for a product or service. Anchor  is the main subscription product or service. Pack
is the add-on product or service that grants additional usage resources for
consumption. Commit  is the product or service with a specific committed quantity
of consumption.
Valid values are:
• Anchor
• Pack
• Token Commitment
• Quantity Commitment
• Monetary Commitment
This field is available in API version 65.0 and later.
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource associated with the product usage grant.
This field is a relationship field. This field is deprecated and will be retired in a future
version.
Relationship Name
UsageResource
Refers To
UsageResource
1832
ProductUsageGrantUsage Management

===== PAGE 1847 =====

DetailsField
Type
int
ValidityPeriodTerm
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The period until when the resource grant is valid.
Type
picklist
ValidityPeriodUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The length of a validity period for the resource grant, when used with the
ValidityPeriodTerm  field.
Valid values are:
• Month
• None
• Year
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
ProductUsageGrantHistory
History is available for tracked fields of the object.
ProductUsageGrantOwnerSharingRule
Sharing rules are available for the object.
ProductUsageGrantShare
Sharing is available for the object.
ProductUsageResource
Represents the mapping of a product and its usage resources. This object is available in API version 64.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
1833
ProductUsageResourceUsage Management

===== PAGE 1848 =====

Special Access Rules
Fields
DetailsField
Type
dateTime
EffectiveEndDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the relationship between the product and the usage resource stops
being active, and any usage tracking or billing related to this relationship ends.
Type
dateTime
EffectiveStartDate
Properties
Create, Filter, Sort, Update
Description
The date and time when the relationship between the product and the usage resource
becomes active or effective, and any usage tracking or billing related to this relationship
begins.
Type
boolean
IsOptional
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the product usage resource is optional when the associated product is
one of the commitment usage model types (true) or not (false). The default value is
false. This field is available in API version 65.0 and later.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
1834
ProductUsageResourceUsage Management

===== PAGE 1849 =====

DetailsField
Description
The timestamp for when the current user last viewed a record related to this record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the product usage grant.
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
The sellable product that grants the usage resource.
This field is a relationship field.
Relationship Name
ProductOffer
Refers To
Product2
Type
string
ProductUsageResourceNum
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The number of each resource grant map that starts with one and is consecutive.
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the product usage resource record.
Valid values are:
1835
ProductUsageResourceUsage Management

===== PAGE 1850 =====

DetailsField
• Active
• Draft
• Inactive
Type
reference
TokenResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource of category Token  that’s associated with the selected usage resource.
This field is available in API version 65.0 and later.
This field is a relationship field.
Relationship Name
TokenResource
Refers To
UsageResource
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource associated with the product usage grant.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductUsageResourceChangeEvent
Change events are available for the object.
ProductUsageResourceFeed
Feed tracking is available for the object.
ProductUsageResourceHistory
History is available for tracked fields of the object.
1836
ProductUsageResourceUsage Management

===== PAGE 1851 =====

ProductUsageResourceOwnerSharingRule
Sharing rules are available for the object.
ProductUsageResourceShare
Sharing is available for the object.
ProductUsageResourcePolicy
Represents the policies applicable to the usage resource when it’s associated with a sellable product. These policies are derived from
the parent usage resource and can be overridden when setting up usage modeling.This object is available in API version 65 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Date and time when the current user last viewed or modified this record, a record related
to this record, or a list view.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Date and time when the current user last viewed or modified this record.
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product selling model associated with this policy.
This field is a relationship field.
1837
ProductUsageResourcePolicyUsage Management

===== PAGE 1852 =====

DetailsField
Relationship Name
ProductSellingModel
Refers To
ProductSellingModel
Type
reference
ProductUsageResourceId
Properties
Create, Filter, Group, Sort
Description
The product usage resource associated with this policy.
This field is a relationship field.
Relationship Name
ProductUsageResource
Relationship Type
Master-detail
Refers To
ProductUsageResource (the master object)
Type
reference
RatingFrequencyPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The rating frequency policy associated with the usage resource.
This field is a relationship field.
Relationship Name
RatingFrequencyPolicy
Refers To
RatingFrequencyPolicy
Type
reference
UsageAggregationPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage aggregation policy associated with the usage resource.
This field is a relationship field.
Relationship Name
UsageAggregationPolicy
1838
ProductUsageResourcePolicyUsage Management

===== PAGE 1853 =====

DetailsField
Refers To
UsageResourceBillingPolicy
Type
reference
UsageCommitmentPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage commitment policy associated with the usage resource.
This field is a relationship field.
Relationship Name
UsageCommitmentPolicy
Refers To
UsageCommitmentPolicy
Type
reference
UsageOveragePolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage overage policy associated with the usage resource.
This field is a relationship field.
Relationship Name
UsageOveragePolicy
Refers To
UsageOveragePolicy
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductUsageResourcePolicyFeed
Feed tracking is available for the object.
ProductUsageResourcePolicyHistory
History is available for tracked fields of the object.
TransactionUsageEntitlement
Represents the details of each usage entitlement that's granted with the purchased sellable product, such as quantity and date when
the entitlements were granted. This object is available in API version 63.0 and later.
1839
TransactionUsageEntitlementUsage Management

===== PAGE 1854 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
To create, update, and delete transaction usage entitlement records, you must have the Usage Management Run Time permission set
license.
Fields
DetailsField
Type
reference
AccountId
Properties
Create, Filter, Group, Sort, Update
Description
The account that's associated with the usage entitlement.
This field is a relationship field.
Relationship Name
Account
Refers To
Account
Type
picklist
ActionType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of action that resulted in the transaction usage entitlement.
Valid values are:
• Amend
• Cancellation
• New
• Ramp
• Renewal
Type
reference
AssetId
Properties
Create, Filter, Group, Nillable, Sort, Update
1840
TransactionUsageEntitlementUsage Management

===== PAGE 1855 =====

DetailsField
Description
The asset associated with the sellable product.
This field is a relationship field.
Relationship Name
Asset
Refers To
Asset
Type
picklist
ChargeForOverage
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The action to be taken when the entitlements are used beyond their grant values.
Valid values are:
• No—Don't charge for over consumption
• Yes—Charge for over consumption
Type
picklist
DrawdownOrder
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The order that's used to debit entitlement consumption from the usage entitlement bucket.
Valid values are:
• ExpiringFirst
• GrantedFirst
• GrantedLast
Type
dateTime
EffectiveEndDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the active transaction usage entitlement ends.
Type
dateTime
EffectiveStartDateTime
Properties
Create, Filter, Sort, Update
1841
TransactionUsageEntitlementUsage Management

===== PAGE 1856 =====

DetailsField
Description
The date and time when the transaction usage entitlement becomes active.
Type
double
EntitlementQuantity
Properties
Create, Filter, Sort, Update
Description
The entitlement quantity for the usage resource.
Type
picklist
EntitlementProcessingStatus
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Indicates whether the transaction usage entitlement has been processed by entitlement
service to be used in Billing. Available in API version 65.0 and later.
Possible values are:
• PENDING—Pending
• PROCESSED—Processed
The default value is PENDING.
Type
reference
EntitlementUomClassId
Properties
Filter, Group, Nillable, Sort
Description
The unit of measure class for the usage entitlement.
This field is a relationship field.
Relationship Name
EntitlementUomClass
Refers To
UnitOfMeasureClass
Type
reference
EntitlementUomId
Properties
Create, Filter, Group, Sort, Update
Description
The unit of measure to calculate the usage entitlement.
1842
TransactionUsageEntitlementUsage Management

===== PAGE 1857 =====

DetailsField
This field is a relationship field.
Relationship Name
EntitlementUom
Refers To
UnitOfMeasure
Type
string
ExternalOrderItem
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The custom or external order item that's associated with the entitlement.
Type
reference
GrantBindingTargetId
Properties
Create, Filter, Group, Sort, Update
Description
The target associated with the entitlements that are granted with the sellable product.
This field is a relationship field.
Relationship Name
GrantBindingTarget
Refers To
Account, Asset, BindingObjectCustomExt, Contract
Type
picklist
GrantType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the type of model that defines how the usage resource is consumed. Available in
API version 65.0 and later.
Possible values are:
• Commit
• Grant
The default value is Grant.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
1843
TransactionUsageEntitlementUsage Management

===== PAGE 1858 =====

DetailsField
Description
The date when this record was last referenced.
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
Autogenerated identifier for the transaction usage entitlement record.
Type
double
NetQuantity
Properties
Create, Filter, Sort, Update
Description
The total quantity that combines the amended quantity with the initial transaction quantity
in the order item.
Type
reference
OrderItemId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The order item that's associated with the entitlement.
This field is a polymorphic relationship field.
Relationship Name
OrderItem
Refers To
OrderItem, WorkOrderLineItem
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
1844
TransactionUsageEntitlementUsage Management

===== PAGE 1859 =====

DetailsField
Description
The ID of the owner of the transaction usage entitlement.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
PricebookEntryId
Properties
Create, Filter, Group, Sort, Update
Description
The price book entry that's associated with the sellable product.
This field is a relationship field.
Relationship Name
PricebookEntry
Refers To
PricebookEntry
Type
reference
ProductId
Properties
Filter, Group, Nillable, Sort
Description
The sellable product for which the entitlement is granted.
This field is a relationship field.
Relationship Name
Product
Refers To
Product2
Type
reference
RatingFrequencyPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The sellable product for which the entitlement is granted. Available in API version 64.0 and
later. This field is deprecated and will be retired in a future version.
This field is a relationship field.
1845
TransactionUsageEntitlementUsage Management

===== PAGE 1860 =====

DetailsField
Relationship Name
RatingFrequencyPolicy
Refers To
RatingFrequencyPolicy
Type
reference
TokenResourceId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage resource of category Token associated with the usage resource related to the
usage product added in the quote line item. Available in API version 65.0 and later.
This field is a relationship field.
Relationship Name
TokenResource
Refers To
UsageResource
Type
double
TransactionQuantity
Properties
Create, Filter, Sort, Update
Description
The transaction quantity in the order for the usage entitlement.
Type
reference
UsageAggregationPolicyId
Properties
Filter, Group, Nillable, Sort
Description
The usage aggregation policy for this entitlement. This field is deprecated and will be retired
in a future version.
This field is a relationship field.
Relationship Name
UsageAggregationPolicy
Refers To
UsageResourceBillingPolicy
Type
reference
UsageGrantRefreshPolicyId
1846
TransactionUsageEntitlementUsage Management

===== PAGE 1861 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage grant refresh policy that's associated with the transaction usage entitlement.
This field is a relationship field.
Relationship Name
UsageGrantRefreshPolicy
Refers To
UsageGrantRenewalPolicy
Type
reference
UsageGrantRolloverPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage grant rollover policy that's associated with the transaction usage entitlement.
This field is a relationship field.
Relationship Name
UsageGrantRolloverPolicy
Refers To
UsageGrantRolloverPolicy
Type
picklist
UsageModelType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The type of usage model for a product or service. Anchor  is the main subscription product
or service. Pack  is the add-on product or service that grants additional usage resources for
consumption. Commit  is the product or service with a specific committed quantity of
consumption.
Valid values are:
• Anchor
• Monetary Commitment
• Pack
• Quantity Commitment
• Token Commitment
Available in API version 64.0 and later.
1847
TransactionUsageEntitlementUsage Management

===== PAGE 1862 =====

DetailsField
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource record that's associated with the transaction usage entitlement.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Type
int
ValidityPeriodTerm
Properties
Create, Filter, Group, Sort, Update
Description
The duration for which the usage resource grant is valid, when used with the validity period
units.
Type
picklist
ValidityPeriodUnit
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The length of a validity period for the usage resource grant, when used with the validity
period term.
Valid values are:
• Month
• None
• Year
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
TransactionUsageEntitlementHistory
History is available for tracked fields of the object.
TransactionUsageEntitlementOwnerSharingRule
Sharing rules are available for the object.
1848
TransactionUsageEntitlementUsage Management

===== PAGE 1863 =====

TransactionUsageEntitlementShare
Sharing is available for the object.
UnitOfMeasure
Defines the units and systems of units used to account for quantities of a usage resource. This object is available for usage management
in API version 62.0 and later.
Examples of units of measure include Liter (for volume), Kilogram (for weight), and single units (such as Can, sachet, and packet).
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
double
ConversionFactor
Properties
Create, Filter, Nillable, Sort, Update
Description
The factor or rate that's used to convert this unit of measurement to the base unit.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
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
1849
UnitOfMeasureUsage Management

===== PAGE 1864 =====

DetailsField
Description
Autogenerated identifier for the unit of measure record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the unit of measure record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
int
Sequence
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The sequence number assigned to the unit of measure.
Type
picklist
Status
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The status of the unit of measure.
Valid values are:
• Active
• Draft
• Inactive
Type
picklist
Type
Properties
Create, Filter, Group, Sort, Update
Description
The type of the unit of measure. For example, weight, distance, period.
1850
UnitOfMeasureUsage Management

===== PAGE 1865 =====

DetailsField
Type
string
UnitCode
Properties
Create, Filter, Group, Sort, Update
Description
The code for the unit of measure.
Type
reference
UnitOfMeasureClassId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The unit of measure class associated with the unit of measure.
This field is a relationship field.
Relationship Name
UnitOfMeasureClass
Refers To
UnitOfMeasureClass
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UnitOfMeasureChangeEvent
Change events are available for the object.
UnitOfMeasureShare
Sharing is available for the object.
UnitOfMeasureClass
Represents a standard unit of measure dimension. This object is available in API version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
1851
UnitOfMeasureClassUsage Management

===== PAGE 1866 =====

Fields
DetailsField
Type
reference
BaseUnitOfMeasureId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The base unit of measure that's used to calculate and display quantities.
This field is a relationship field.
Relationship Name
BaseUnitOfMeasure
Refers To
UnitOfMeasure
Type
string
Code
Properties
Create, Filter, Group, Sort, Update
Description
The unique user-defined string for the unit of measure class.
Type
reference
DefaultUnitOfMeasureId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The default unit of measure that's used to calculate and display quantities. This measure can
be different from the base unit of measure and overridden by individual resources.
This field is a relationship field.
Relationship Name
DefaultUnitOfMeasure
Refers To
UnitOfMeasure
Type
string
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The description of the unit of measure class.
1852
UnitOfMeasureClassUsage Management

===== PAGE 1867 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
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
Autogenerated identifier for the unit of measure class record.
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the unit of measure class.
Valid values are:
• Active
• Draft
• Inactive
Type
picklist
Type
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of the unit of measure class.
Valid values are:
• Currency
1853
UnitOfMeasureClassUsage Management

===== PAGE 1868 =====

DetailsField
• Token
• Usage
The default value is Usage. Available in API version 64.0 and later.
This is a required field.
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UnitOfMeasureClassHistory
History is available for tracked fields of the object.
UsageBillingPeriodItem
Represents the calculated overages for the usage entitlement and the amount that's charged for these overages. This object is available
in API version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
To create, update, and delete transaction usage entitlement records, you must have the Usage Management Run Time permission set
license.
Fields
DetailsField
Type
reference
AccountId
Properties
Create, Filter, Group, Sort, Update
Description
The account that's associated with the billing period item.
This field is a relationship field.
Relationship Name
Account
Refers To
Account
1854
UsageBillingPeriodItemUsage Management

===== PAGE 1869 =====

DetailsField
Type
reference
AssetId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The asset that's associated with the usage billing period item.
This field is a relationship field.
Relationship Name
Asset
Refers To
Asset
Type
dateTime
EndDateTime
Properties
Create, Filter, Sort, Update
Description
The end date and time of the billing period.
Type
picklist
ErrorCode
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The error code when the billing request fails.
Valid value is:
• INTERNAL_ERROR
Type
string
ErrorDescription
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The error description that corresponds to the error code.
Type
reference
GrantBindingTargetId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The record that's associated with the usage entitlement account.
1855
UsageBillingPeriodItemUsage Management

===== PAGE 1870 =====

DetailsField
This field is a relationship field.
Relationship Name
GrantBindingTarget
Refers To
Account, Asset, BindingObjectCustomExt, Contract
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
currency
OverageAmount
Properties
Create, Filter, Sort, Update
Description
The amount calculated for the overage.
Type
double
OverageAmountDerived
Properties
Filter, Nillable, Sort
Description
The numeric value specified in the OverageAmount  field to process Data processing
Engine (DPE) jobs.
This field is a calculated field.
Type
double
OverageQuantity
Properties
Create, Filter, Sort, Update
1856
UsageBillingPeriodItemUsage Management

===== PAGE 1871 =====

DetailsField
Description
The quantity of the usage entitlement that was overused for the specified billing period.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the usage billing period item.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
dateTime
StartDateTime
Properties
Create, Filter, Sort, Update
Description
The start date and time of the billing period.
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the usage billing period item.
Valid values are:
• Invoiced
• InvoicingFailed
• LiableSummaryComplete
• New
• ReadyForInvoicing
• Inactive—Available in API version 65.0 and later.
Type
double
TotalUsedQuantity
Properties
Create, Filter, Sort, Update
1857
UsageBillingPeriodItemUsage Management

===== PAGE 1872 =====

DetailsField
Description
The total quantity of usage entitlement that was used for the billing period. This includes
granted and overused entitlements.
Type
reference
UoMId
Properties
Create, Filter, Group, Sort, Update
Description
The unit of measure for the overage quantity of usage entitlement.
This field is a relationship field.
Relationship Name
UoM
Refers To
UnitOfMeasure
Type
string
UsageBillingPeriodItemNum
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Autogenerated identifier for the usage billing period item record.
Type
reference
UsageEntitlementAccountId
Properties
Filter, Group, Nillable, Sort
Description
The usage entitlement account associated with the source usage entitlement bucket.
This field is a relationship field.
Relationship Name
UsageEntitlementAccount
Refers To
UsageEntitlementAccount
Type
reference
UsageEntitlementBucketId
Properties
Create, Filter, Group, Sort, Update
Description
The usage entitlement bucket that's associated with the billing period item.
1858
UsageBillingPeriodItemUsage Management

===== PAGE 1873 =====

DetailsField
This field is a relationship field.
Relationship Name
UsageEntitlementBucket
Refers To
UsageEntitlementBucket
Type
reference
UsageResourceId
Properties
Filter, Group, Nillable, Sort
Description
The usage resource associated with the usage entitlement bucket.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageBillingPeriodItemFeed
Feed tracking is available for the object.
UsageBillingPeriodItemHistory
History is available for tracked fields of the object.
UsageBillingPeriodItemShare
Sharing is available for the object.
UsageCmtAssetRelatedObj
Represents the relation between an asset for the commitment-based usage product and an asset, account, contract, or custom object.
This object is available in API version 64.0 and later.
Important: Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
1859
UsageCmtAssetRelatedObjUsage Management

===== PAGE 1874 =====

Fields
DetailsField
Type
reference
AssetId
Properties
Create, Filter, Group, Sort
Description
The asset associated with the commitment-based usage product.
This field is a relationship field.
Relationship Name
Asset
Relationship Type
Master-detail
Refers To
Asset (the master object)
Type
dateTime
EffectiveEndDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time until when the commitment for the related asset remains effective.
Type
dateTime
EffectiveStartDateTime
Properties
Create, Filter, Sort, Update
Description
The date and time when the commitment for the related asset becomes effective.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
1860
UsageCmtAssetRelatedObjUsage Management

===== PAGE 1875 =====

DetailsField
Description
The timestamp for when the current user last viewed a record related to this record.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Autogenerated identifier for the usage commitment asset related object record.
Type
reference
RelatedObjectId
Properties
Create, Filter, Group, Sort, Update
Description
The asset, account, or contract associated with the asset.
This field is a polymorphic relationship field.
Relationship Name
RelatedObject
Refers To
Account, Asset, Contract
Only Asset is supported in API version 64.0.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
UsageCmtAssetRelatedObjFeed
Feed tracking is available for the object.
UsageCmtAssetRelatedObjHistory
History is available for tracked fields of the object.
UsageCommitmentPolicy
Represents the set of rules that determines how commitments are applied to a usage resource. This object is available in API version 65
and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
1861
UsageCommitmentPolicyUsage Management

===== PAGE 1876 =====

Special Access Rules
Fields
DetailsField
Type
picklist
CommitmentRate
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The rate that’s applicable to the usage resource’s units consumed post the commitment is
utilized, but the commitment period is still active.
Valid values are:
• Bounded Object Rate
• Lowest Commitment Rate
The default value is Lowest Commitment Rate.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Date and time when the current user last viewed or modified this record, a record related
to this record, or a list view.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Date and time when the current user last viewed or modified this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the usage commitment policy.
1862
UsageCommitmentPolicyUsage Management

===== PAGE 1877 =====

UsageEntitlementAccount
Represents the entitlement account details related to the asset that holds the wallet with the granted units. This object is available in
API version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
AccountId
Properties
Create, Filter, Group, Sort, Update
Description
The account that's associated with the usage entitlement.
This field is a relationship field.
Relationship Name
Account
Refers To
Account
Type
int
BillDayOfMonth
Properties
Create, Filter, Group, Sort, Update
Description
The day of the month that the bill is generated on and that ends the billing period.
Type
dateTime
BillingPeriodEndDateTime
Properties
Create, Filter, Sort, Update
Description
The date and time when the billing period of the usage entitlements ends.
Type
dateTime
BillingPeriodStartDateTime
Properties
Create, Filter, Sort, Update
1863
UsageEntitlementAccountUsage Management

===== PAGE 1878 =====

DetailsField
Description
The date and time when the billing period of the usage entitlements starts.
Type
int
BillingPeriodTerm
Properties
Create, Filter, Group, Sort, Update
Description
The frequency at which the bill is generated.
Type
picklist
BillingPeriodUnit
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The unit to measure the billing frequency.
Valid value is:
• MONTH
Type
dateTime
EffectiveEndDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the usage entitlement account ends.
Type
dateTime
EffectiveStartDateTime
Properties
Create, Filter, Sort, Update
Description
The date and time when the usage entitlement account starts.
Type
reference
GrantBindingTargetId
Properties
Create, Filter, Group, Sort, Update
Description
The target that's associated with the usage entitlement account.
This field is a relationship field.
1864
UsageEntitlementAccountUsage Management

===== PAGE 1879 =====

DetailsField
Relationship Name
GrantBindingTarget
Refers To
Account, Asset, BindingObjectCustomExt, Contract
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
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
Autogenerated identifier for the usage entitlement account record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the usage entitlement account.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
PricebookEntryId
1865
UsageEntitlementAccountUsage Management

===== PAGE 1880 =====

DetailsField
Properties
Create, Filter, Group, Sort, Update
Description
The price book entry that's associated with the sellable product.
This field is a relationship field.
Relationship Name
PricebookEntry
Refers To
PricebookEntry
Type
reference
ProductId
Properties
Filter, Group, Nillable, Sort
Description
The sellable product for which the entitlements are granted.
This field is a relationship field.
Relationship Name
Product
Refers To
Product2
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageEntitlementAccountFeed
Feed tracking is available for the object.
UsageEntitlementAccountHistory
History is available for tracked fields of the object.
UsageEntitlementAccountShare
Sharing is available for the object.
UsageEntitlementBucket
Represents a usage entitlement that's granted with the sellable product. This object is available in API version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
1866
UsageEntitlementBucketUsage Management

===== PAGE 1881 =====

Fields
DetailsField
Type
double
BucketBalance
Properties
Create, Filter, Sort, Update
Description
The balance of the usage entitlement bucket after each transaction.
Type
reference
BucketBalanceUomId
Properties
Create, Filter, Group, Sort, Update
Description
The unit that's used to measure the usage entitlement bucket balance.
This field is a relationship field.
Relationship Name
BucketBalanceUom
Refers To
UnitOfMeasure
Type
int
CompletedRollovers
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The number of rollovers that were completed for the entitlements.
Type
double
ConsumedEntitlement
Properties
Create, Filter, Nillable, Sort, Update
Description
The entitlements that have been consumed from this bucket.
Type
dateTime
EffectiveEndDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the usage entitlement bucket period ends.
1867
UsageEntitlementBucketUsage Management

===== PAGE 1882 =====

DetailsField
Type
dateTime
EffectiveStartDateTime
Properties
Create, Filter, Sort, Update
Description
The date and time when the usage entitlement bucket becomes effective.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
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
Autogenerated identifier for the usage entitlement bucket record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the usage entitlement bucket.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
1868
UsageEntitlementBucketUsage Management

===== PAGE 1883 =====

DetailsField
Type
reference
ParentId
Properties
Create, Filter, Group, Sort, Update
Description
The parent record that's associated with the usage entitlement bucket.
This field is a polymorphic relationship field.
Relationship Name
Parent
Refers To
UsageEntitlementAccount, UsageEntitlementBucket
Type
double
ProvisionalBucketBalance
Properties
Create, Filter, Nillable, Sort, Update
Description
The provisional entitlement balance available in the usage bucket. Available in API version
66.0 and later.
Type
double
TotalAsOfBalance
Properties
Filter, Nillable, Sort
Description
The balance of the entitlements granted with the usage resource for a Usage entitlement
account.
Type
double
TotalConsumedEntitlement
Properties
Filter, Nillable, Sort
Description
The entitlements that have been consumed from this bucket.
Type
double
TotalProvisionalBalance
Properties
Filter, Nillable, Sort
1869
UsageEntitlementBucketUsage Management

===== PAGE 1884 =====

DetailsField
Description
The total provisional entitlement balance in the usage entitlement account as of the specified
date. Available in API version 66.0 and later.
Type
reference
TransactionUsageEntitlementId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The transaction usage entitlement associated with this usage entitlement bucket.
This field is a relationship field.
Relationship Name
TransactionUsageEntitlement
Refers To
TransactionUsageEntitlement
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource that's associated with the usage entitlement bucket.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageEntitlementBucketFeed
Feed tracking is available for the object.
UsageEntitlementBucketHistory
History is available for tracked fields of the object.
UsageEntitlementBucketShare
Sharing is available for the object.
1870
UsageEntitlementBucketUsage Management

===== PAGE 1885 =====

UsageEntitlementEntry
Represents the usage entitlement details, such as the usage consumption, rollovers, and details of expired units for each tenure. This
object is available in API version 63.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
double
ClosingBalance
Properties
Create, Filter, Sort, Update
Description
The quantity of the entitlement after adjusting the transaction quantity for the current
entitlement validity period.
Type
dateTime
EffectiveEndDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the usage entitlement entry ends.
Type
dateTime
EffectiveStartDateTime
Properties
Create, Filter, Sort, Update
Description
The date and time when the usage entitlement entry starts.
Type
reference
EntitlementBucketId
Properties
Create, Filter, Group, Sort, Update
Description
The usage entitlement bucket that's associated with the entitlement entry.
1871
UsageEntitlementEntryUsage Management

===== PAGE 1886 =====

DetailsField
This field is a relationship field.
Relationship Name
EntitlementBucket
Relationship Type
Master-detail
Refers To
UsageEntitlementBucket (the master object)
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
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
Autogenerated identifier for the usage entitlement entry record.
Type
double
OpeningBalance
Properties
Create, Filter, Sort, Update
Description
The starting quantity of the entitlement for the current entitlement validity period.
Type
reference
ParentEntitlementBucketId
Properties
Filter, Group, Nillable, Sort
1872
UsageEntitlementEntryUsage Management

===== PAGE 1887 =====

DetailsField
Description
The parent usage entitlement bucket record that's associated with the entitlement entry.
This field is a relationship field.
Relationship Name
ParentEntitlementBucket
Refers To
UsageEntitlementBucket
Type
dateTime
TransactionDate
Properties
Create, Filter, Sort, Update
Description
The date when the transaction usage entitlement entry was updated.
Type
double
TransactionQuantity
Properties
Create, Filter, Sort, Update
Description
The quantity of the entitlement used during the current entitlement validity period.
Type
picklist
TransactionReason
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The reason for the usage entitlement entry.
Valid values are:
• Amend
• Cancel
• Consumption
• Original
• Refresh
• Renew
• Rollover
Type
picklist
TransactionType
1873
UsageEntitlementEntryUsage Management

===== PAGE 1888 =====

DetailsField
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of transaction.
Valid values are:
• Credit
• Debit
• Expired
Type
reference
TransactionUsageEntitlementId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The transaction usage entitlement that's associated with this usage entitlement entry.
This field is a relationship field.
Relationship Name
TransactionUsageEntitlement
Refers To
TransactionUsageEntitlement
Type
reference
TransactionalBucketId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage entitlement bucket that's used to debit the consumption of entitlements.
This field is a relationship field.
Relationship Name
TransactionalBucket
Refers To
UsageEntitlementBucket
Type
reference
UomId
Properties
Create, Filter, Group, Sort, Update
Description
The unit of measure that's associated with the usage entitlement.
This field is a relationship field.
1874
UsageEntitlementEntryUsage Management

===== PAGE 1889 =====

DetailsField
Relationship Name
Uom
Refers To
UnitOfMeasure
Type
reference
UsageSummaryId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage summary that's associated with the usage entitlement. Available in API version
64.0 and later.
This field is a relationship field.
Relationship Name
UsageSummary
Refers To
UsageSummary
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageEntitlementEntryFeed
Feed tracking is available for the object.
UsageEntitlementEntryHistory
History is available for tracked fields of the object.
UsageEntitlementEntryOwnerSharingRule
Sharing rules are available for the object.
UsageEntitlementEntryShare
Sharing is available for the object.
UsageGrantRenewalPolicy
Represents a policy about the rollover of a usage grant. This object is available in API version 62.0 and later.
A usage grant renewal policy is used if you want to never renew a usage grant or renew on a specific frequency.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
1875
UsageGrantRenewalPolicyUsage Management

===== PAGE 1890 =====

Fields
DetailsField
Type
string
Code
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
A unique user-defined string for the usage grant renewal policy.
Type
boolean
IsRenewalAllowed
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the policy renewal is allowed (true) or not (false). If true, then the
policy can be renewed.
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
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
The name of the renewal policy record.
Type
int
RenewalFrequency
1876
UsageGrantRenewalPolicyUsage Management

===== PAGE 1891 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The frequency of the policy renewals, when used with the RenewalFrequencyUnit
field.
Type
picklist
RenewalFrequencyUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The renewal duration for a policy.
Valid values are:
• Month
• Quarter
• Year
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the renewal policy.
Valid values are:
• Active
• Draft
• Inactive
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageGrantRenewalPolicyFeed
Feed tracking is available for the object.
UsageGrantRenewalPolicyHistory
History is available for tracked fields of the object.
UsageGrantRolloverPolicy
Represents a policy about the rollover of a usage grant.This object is available in API version 62.0 and later.
1877
UsageGrantRolloverPolicyUsage Management

===== PAGE 1892 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
Code
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
A unique user-defined string for the usage grant rollover policy.
Type
boolean
IsRolloverAllowed
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the policy allows the rollover of the usage grant.
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
int
MaximumRolloverCount
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The maximum number of times that the usage grant can roll over.
1878
UsageGrantRolloverPolicyUsage Management

===== PAGE 1893 =====

DetailsField
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the rollover policy record.
Type
boolean
ShouldAllowRolloverExpiry
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the rollover for the associated usage grant is allowed to expire.
The default value is false.
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the status of the rollover policy.
Possible values are:
• Active
• Draft
• Inactive
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageGrantRolloverPolicyFeed
Feed tracking is available for the object.
UsageGrantRolloverPolicyHistory
History is available for tracked fields of the object.
UsageOveragePolicy
Represents the set of rules that determine the management of usage resource’s units consumed beyond the granted limit. This object
is available in API version 65 and later.
1879
UsageOveragePolicyUsage Management

===== PAGE 1894 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Date and time when the current user last viewed or modified this record, a record related
to this record, or a list view.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Date and time when the current user last viewed or modified this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the usage overage policy.
Type
picklist
OverageChargeable
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies whether the overconsumption beyond the granted quantity is to be charged.
Valid values are:
• No
• Yes
1880
UsageOveragePolicyUsage Management

===== PAGE 1895 =====

UsagePrdGrantBindingPolicy
Represents the association of a usage resource's grants with a sellable product. This object is available in API version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
GrantBindingTargetType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type of binding instance to which the grant is added.
Valid values are:
• Custom
• Product
• Contract
• Account
Type
picklist
GrantBindingType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of binding that indicates where the grant is added.
Valid values are:
• Self
• Target
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
1881
UsagePrdGrantBindingPolicyUsage Management

===== PAGE 1896 =====

DetailsField
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
Autogenerated identifier for the usage product grant binding policy.
Type
reference
Product2Id
Properties
Create, Filter, Group, Sort, Update
Description
The sellable product associated with the usage product grant binding policy.
This field is a relationship field.
Relationship Name
Product2
Refers To
Product2
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsagePrdGrantBindingPolicyFeed
Feed tracking is available for the object.
UsagePrdGrantBindingPolicyHistory
History is available for tracked fields of the object.
UsageRatableSummary
Represents the aggregation of the usage summaries that are used to calculate the rate at which the overages are charged. This object
is available in API version 63.0 and later.
1882
UsageRatableSummaryUsage Management

===== PAGE 1897 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
AccountId
Properties
Create, Filter, Group, Sort, Update
Description
The account that's associated with the ratable summary.
This field is a relationship field.
Relationship Name
Account
Refers To
Account
Type
reference
AssetId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The asset that's associated with the ratable summary.
This field is a relationship field.
Relationship Name
Asset
Refers To
Asset
Type
dateTime
EndDateTime
Properties
Create, Filter, Sort, Update
Description
The end date and time of the ratable period.
Type
picklist
ErrorCode
1883
UsageRatableSummaryUsage Management

===== PAGE 1898 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The code that represents the error encountered when the ratable summary is rated.
Valid value is:
• INTERNAL_ERROR
Type
string
ErrorDescription
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The error description that corresponds to the error code.
Type
reference
GrantBindingTargetId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The record that's associated with the usage ratable summary. Available in API version 64.0
and later.
This field is a relationship field.
Relationship Name
GrantBindingTarget
Refers To
Account, Asset, BindingObjectCustomExt, Contract
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
1884
UsageRatableSummaryUsage Management

===== PAGE 1899 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Autogenerated identifier for the usage ratable summary record.
Type
double
NetUnitRate
Properties
Create, Filter, Nillable, Sort, Update
Description
The rate that's used to calculate the amount for each unit of usage entitlement overage.
Type
reference
NetUnitRateUomId
Properties
Create, Filter, Group, Sort, Update
Description
The unit of measure for the net unit rate applied to the overage.
This field is a relationship field.
Relationship Name
NetUnitRateUom
Refers To
UnitOfMeasure
Type
double
OverageQuantity
Properties
Create, Filter, Sort, Update
Description
The quantity of the usage entitlements that were overused.
Type
reference
OverageQuantityUomId
Properties
Create, Filter, Group, Sort, Update
Description
The unit of measure that's used for overage quantity.
This field is a relationship field.
1885
UsageRatableSummaryUsage Management

===== PAGE 1900 =====

DetailsField
Relationship Name
OverageQuantityUom
Refers To
UnitOfMeasure
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the usage ratable summary.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
dateTime
RatingDecisionDateTime
Properties
Create, Filter, Sort, Update
Description
The date and time when the decision about rating consumption is done.
Type
string
RatingExecutionIdentifier
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the rating service execution that's used to retrieve waterfall logs.
Type
reference
RatingRequestId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID that invokes the rating service that's used to rate the usage ratable summary.
This field is a relationship field.
Relationship Name
RatingRequest
1886
UsageRatableSummaryUsage Management

===== PAGE 1901 =====

DetailsField
Refers To
RatingRequest
Type
reference
SourceUsageResourceId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage resource that’s rated in tokens when usage ratable summary is created. This field
is available in API version 65.0 and later.
This field is a relationship field.
Relationship Name
SourceUsageResource
Refers To
UsageResource
Type
dateTime
StartDateTime
Properties
Create, Filter, Sort, Update
Description
The start date and time of the ratable period.
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the ratable summary.
Valid values are:
• New
• RatingComplete
• RatingFailed
• SummaryCreated
• Inactive—Available in API version 65.0 and later.
Type
double
TierQuantity
Properties
Create, Filter, Sort, Update
1887
UsageRatableSummaryUsage Management

===== PAGE 1902 =====

DetailsField
Description
The quantity that impacts the net unit rate of a usage entitlement.
Type
reference
TierQuantityUomId
Properties
Create, Filter, Group, Sort, Update
Description
The unit of measure for the tier quantity.
This field is a relationship field.
Relationship Name
TierQuantityUom
Refers To
UnitOfMeasure
Type
double
TotalAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The total amount after calculating the overage based on the net unit rate.
Type
reference
UsageEntitlementAccountId
Properties
Filter, Group, Nillable, Sort
Description
The usage entitlement account that's associated with the source of the ratable summary.
This field is a relationship field.
Relationship Name
UsageEntitlementAccount
Refers To
UsageEntitlementAccount
Type
reference
UsageEntitlementBucketId
Properties
Create, Filter, Group, Sort, Update
Description
The usage entitlement bucket that's associated with the source of the ratable summary.
This field is a relationship field.
1888
UsageRatableSummaryUsage Management

===== PAGE 1903 =====

DetailsField
Relationship Name
UsageEntitlementBucket
Refers To
UsageEntitlementBucket
Type
reference
UsageResourceId
Properties
Filter, Group, Nillable, Sort
Description
The usage resource associated with the usage entitlement bucket.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageRatableSummaryHistory
History is available for tracked fields of the object.
UsageRatableSummaryOwnerSharingRule
Sharing rules are available for the object.
UsageRatableSummaryShare
Sharing is available for the object.
UsageRatableSumCmtAssetRt
Represents the rate that’s calculated and applicable for the usage resource associated with the commitment assets related to an anchor.
This object is available in API version 65.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
1889
UsageRatableSumCmtAssetRtUsage Management

===== PAGE 1904 =====

Special Access Rules
Fields
DetailsField
Type
reference
CommitmentAssetId
Properties
Create, Filter, Group, Sort, Update
Description
The asset ID associated with the Usage Ratable Summary.
This field is a relationship field.
Relationship Name
CommitmentAsset
Refers To
Asset
Type
picklist
ErrorCode
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the unique code generated when an error occurs.
Valid value is INTERNAL_ERROR.
Type
string
ErrorDescription
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Specifies the description of the error that occurred.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
Type
dateTime
LastViewedDate
1890
UsageRatableSumCmtAssetRtUsage Management

===== PAGE 1905 =====

DetailsField
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Name of the Usage Commitment Summary record.
Type
double
NetUnitRate
Properties
Create, Filter, Nillable, Sort, Update
Description
The calculated per-unit rate for usage after applying commitment-specific discounts during
the rating process.
Type
reference
UsageRatableSummaryId
Properties
Create, Filter, Group, Sort
Description
The usage ratable summary associated with the usage commitment summary record.
This field is a relationship field.
Relationship Name
UsageRatableSummary
Relationship Type
Master-detail
Refers To
UsageRatableSummary (the master object)
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
UsageRatableSumCmtAssetRtHistory
History is available for tracked fields of the object.
1891
UsageRatableSumCmtAssetRtUsage Management

===== PAGE 1906 =====

UsageResource
Represents an entitlement granted to a user or party by a provider, such as data storage, computing power, bandwidth, or any other
product or service. Additionally, this object is used to represent resources consumed over time. This object is available in API version
62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
Category
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The category of the usage resource that's used to organize and understand the product
grant maps.
Valid values are:
• Currency—Available in API version 65.0 and later.
• Usage
• Token—Available in API version 64.0 and later.
Type
string
Code
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The unique user-defined string for the usage resource.
Type
reference
DefaultUnitOfMeasureId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The default unit of measure for the given resource. The default value can be overridden with
an alternate default unit of measure for a given resource.
This field is a relationship field.
Relationship Name
DefaultUnitOfMeasure
1892
UsageResourceUsage Management

===== PAGE 1907 =====

DetailsField
Refers To
UnitOfMeasure
Type
string
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The description of the usage resource.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
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
The name of the usage resource record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the usage resource record.
This field is a polymorphic relationship field.
Relationship Name
Owner
1893
UsageResourceUsage Management

===== PAGE 1908 =====

DetailsField
Refers To
Group, User
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the usage resource.
Valid values are:
• Active
• Draft
• Inactive
Type
reference
TokenResourceId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage resource of Category Token  that’s used to charge this usage resource. For
example, you can select a usage resource Credits (Token category) to rate the usage resource
Data (Usage category). This field is available in API version 65.0 and later.
Relationship Name
TokenResource
Refers To
UsageResource
Type
reference
UnitOfMeasureClassId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The unit of measure class that's used with the resource to define the units in which this
resource is measured.
This field is a relationship field.
Relationship Name
UnitOfMeasureClass
Refers To
UnitOfMeasureClass
1894
UsageResourceUsage Management

===== PAGE 1909 =====

DetailsField
Type
reference
UsageDefinitionProductId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product associated with the usage resource to retrieve tax policy, calculate rating during
overages, and other invoicing actions.
This field is a relationship field.
Relationship Name
UsageDefinitionProduct
Refers To
Product2
Type
reference
UsageResourceBillingPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage resource billing policy that defines how the usage resource can be aggregated
before it's sent for rating.
This field is a relationship field. This field is deprecated and will be retired in a future version.
Relationship Name
UsageResourceBillingPolicy
Refers To
UsageResourceBillingPolicy
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageResourceFeed
Feed tracking is available for the object.
UsageResourceHistory
History is available for tracked fields of the object.
UsageResourceOwnerSharingRule
Sharing rules are available for the object.
UsageResourceShare
Sharing is available for the object.
1895
UsageResourceUsage Management

===== PAGE 1910 =====

UsageResourcePolicy
Represents the policies applicable to the usage resource whether it’s associated with a sellable product or not. This object is available
in API version 65 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Fields
DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Date and time when the current user last viewed or modified this record, a record related
to this record, or a list view.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Date and time when the current user last viewed or modified this record.
Type
reference
RatingFrequencyPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The rating frequency policy associated with the usage resource.
This field is a relationship field.
Relationship Name
RatingFrequencyPolicy
1896
UsageResourcePolicyUsage Management

===== PAGE 1911 =====

DetailsField
Refers To
RatingFrequencyPolicy
Type
reference
UsageAggregationPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage aggregation policy associated with the usage resource.
This field is a relationship field.
Relationship Name
UsageAggregationPolicy
Refers To
UsageResourceBillingPolicy
Type
reference
UsageCommitmentPolicyId
Properties
Create, Filter, Group, Sort, Update
Description
The usage commitment policy associated with the usage resource.
This field is a relationship field.
Relationship Name
UsageCommitmentPolicy
Refers To
UsageCommitmentPolicy
Type
reference
UsageOveragePolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage overage policy associated with the usage resource.
This field is a relationship field.
Relationship Name
UsageOveragePolicy
Refers To
UsageOveragePolicy
Type
reference
UsageResourceId
1897
UsageResourcePolicyUsage Management

===== PAGE 1912 =====

DetailsField
Properties
Create, Filter, Group, Sort
Description
The usage resource associated with the usage resource policy.
This field is a relationship field.
Relationship Name
UsageResource
Relationship Type
Master-detail
Refers To
UsageResource (the master object)
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
UsageResourcePolicyFeed
Feed tracking is available for the object.
UsageResourcePolicyHistory
History is available for tracked fields of the object.
UsageResourceBillingPolicy
Represents information about how the usage is accumulated before rating a usage resource.This object is available in API version 62.0
and later.
A usage resource billing policy object is used to configure the properties of usage resources related to how aggregation is performed
on the usage records before rating. Usage resource billing policies are defined at the usage resource level and can be reused across
multiple usage resources.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
Code
1898
UsageResourceBillingPolicyUsage Management

===== PAGE 1913 =====

DetailsField
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
A unique user-defined string for the usage resource billing policy.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
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
The name of the usage resource billing policy record.
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the policy.
Valid values are:
• Active
• Draft
• Inactive
Type
picklist
UsageAccumulationMethod
Properties
Create, Filter, Group, Restricted picklist, Sort, Update, Defaulted On Create
1899
UsageResourceBillingPolicyUsage Management

===== PAGE 1914 =====

DetailsField
Description
The method used to accumulate the usage.
Valid values are:
• Peak
• Sum
Type
picklist
UsageAccumulationPeriod
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The duration for which the usage is accumulated.
Valid values are:
• Daily
• Monthly
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageResourceBillingPolicyFeed
Feed tracking is available for the object.
UsageResourceBillingPolicyHistory
History is available for tracked fields of the object.
UsageSummary
Represents the aggregation of the entries in the transaction journal for a usage entitlement for a specified period. This object is available
in API version 63.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
AccountId
1900
UsageSummaryUsage Management

===== PAGE 1915 =====

DetailsField
Properties
Create, Filter, Group, Sort, Update
Description
The account that's associated with the sellable product that was purchased.
This field is a relationship field.
Relationship Name
Account
Refers To
Account
Type
reference
AssetId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The asset that's associated with the entitlement that was summarized.
This field is a relationship field.
Relationship Name
Asset
Refers To
Asset
Type
double
ConsumptionUnits
Properties
Create, Filter, Sort, Update
Description
The quantity that was used by the usage entitlement bucket.
Type
double
DebitedUnits
Properties
Create, Filter, Sort, Update
Description
The units that are debited from the associated usage entitlement bucket.
Type
dateTime
EndDateTime
Properties
Create, Filter, Sort, Update
1901
UsageSummaryUsage Management

===== PAGE 1916 =====

DetailsField
Description
The end date and time of the usage summary.
Type
reference
GrantBindingTargetId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The record that's associated with the usage summary. Available in API version 64.0 and later.
This field is a relationship field.
Relationship Name
GrantBindingTarget
Refers To
Account, Asset, BindingObjectCustomExt, Contract
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when this record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed a record related to this record.
Type
reference
LiableSummaryId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage billing period item that's associated with this usage summary.
This field is a relationship field.
Relationship Name
LiableSummary
Refers To
UsageBillingPeriodItem
1902
UsageSummaryUsage Management

===== PAGE 1917 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Autogenerated identifier for the usage summary record.
Type
double
OverageUnits
Properties
Create, Filter, Sort, Update
Description
The quantity that was overused by the usage entitlement bucket.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the usage summary.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
ParentUsageSummaryId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The parent usage summary that’s associated with this usage summary. This field is available
in API version 65.0 and later.
This field is a relationship field.
Relationship Name
ParentUsageSummary
Refers To
UsageSummary
Type
reference
RatableSummaryId
1903
UsageSummaryUsage Management

===== PAGE 1918 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ratable summary that's associated with this usage summary.
This field is a relationship field.
Relationship Name
RatableSummary
Refers To
UsageRatableSummary
Type
dateTime
StartDateTime
Properties
Create, Filter, Sort, Update
Description
The start date and time of the usage summary.
Type
picklist
Status
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the usage summary.
Valid values are:
• DrawdownComplete
• LiableSummaryComplete
• New
• RatableSummaryComplete
• Rated
• UsageSummaryComplete
• UsageSummaryInProgress
• Inactive—Available in API version 65.0 and later.
Type
reference
UomId
Properties
Create, Filter, Group, Sort, Update
Description
The unit of measure for the usage resource. This value overrides the default unit of measure
defined in the associated unit of measure class.
1904
UsageSummaryUsage Management

===== PAGE 1919 =====

DetailsField
This field is a relationship field.
Relationship Name
Uom
Refers To
UnitOfMeasure
Type
reference
UsageEntitlementAccountId
Properties
Filter, Group, Nillable, Sort
Description
The usage entitlement account that's associated with the usage summary.
This field is a relationship field.
Relationship Name
UsageEntitlementAccount
Refers To
UsageEntitlementAccount
Type
reference
UsageEntitlementBucketId
Properties
Create, Filter, Group, Sort, Update
Description
The usage entitlement bucket that's associated with the usage summary.
This field is a relationship field.
Relationship Name
UsageEntitlementBucket
Refers To
UsageEntitlementBucket
Type
reference
UsageResourceId
Properties
Filter, Group, Nillable, Sort
Description
The usage resource that's associated with the source of the usage entitlement bucket.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
1905
UsageSummaryUsage Management

===== PAGE 1920 =====

Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
UsageSummaryHistory
History is available for tracked fields of the object.
UsageSummaryOwnerSharingRule
Sharing rules are available for the object.
UsageSummaryShare
Sharing is available for the object.
Usage Management Fields on Standard Objects
Usage Management adds standard and custom fields to some standard Salesforce objects. These fields are available only in orgs where
Usage Management is enabled. This object is available in API version 63.0 and later.
Usage Management Fields on Product2
Standard and custom fields extend the standard Product2 object for use in Usage Management to represent information about
products.
Usage Management Fields on TransactionJournal
Standard and custom fields extend the standard Transaction Journal object for use in Usage Management to represent consumption
details of a usage resource that are recorded for creating usage summaries. This object is available for usage management in API
version 63.0 and later.
Usage Management Fields on Product2
Standard and custom fields extend the standard Product2 object for use in Usage Management to represent information about products.
Fields
DetailsField
Type
picklist
UsageModelType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type of usage model for a product or service.
Valid values are:
• Anchor—The main subscription product or service. Available in API version 62.0 and
later.
• Pack—The add-on product or service that grants additional usage resources for
consumption. Available in API version 62.0 and later.
1906
Usage Management Fields on Standard ObjectsUsage Management

===== PAGE 1921 =====

DetailsField
• Monetary Commitment—An agreement by a customer to spend a minimum
amount for a product or service in a defined period. Available in API version 65.0 and
later.
• Quantity Commitment—An agreement by a customer to use a minimum quantity
of a product or service in a defined period. Available in API version 65.0 and later.
• Token Commitement—An agreement by a customer to use a minimum quantity
of tokens for a product or service in a defined period. Available in API version 65.0 and
later.
Usage Management Fields on TransactionJournal
Standard and custom fields extend the standard Transaction Journal object for use in Usage Management to represent consumption
details of a usage resource that are recorded for creating usage summaries. This object is available for usage management in API version
63.0 and later.
Fields
DetailsField
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage resource that's associated with the transaction journal.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Type
reference
UsageSummaryId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage summary that's associated with the transaction journal. Available in API version
64.0 and later.
This field is a relationship field.
Relationship Name
UsageSummary
1907
Usage Management Fields on TransactionJournalUsage Management

===== PAGE 1922 =====

DetailsField
Refers To
UsageSummary
Type
picklist
UsageType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
The type of usage.
Valid value is UsageManagement.
Usage Management Standard Invocable Actions
Learn more about the standard invocable actions available with Usage Management.
Invoke Summary Creation Action
Invoke the service that creates various summaries, such as usage, ratable, and liable summaries where the usage amount is zero.
The service also checks and updates the billing period of the usage entitlement account if the billing period is expired.
Process Consumption Overages Action
Process consumption overages for the usage summary records with SummaryComplete  status. This action uses the entitlement
service to process the overages.
Refresh Usage Entitlement Bucket Action
Refresh entitlements by evaluating the usage entitlement bucket records and creating a new usage entitlement entry.
Retrigger Entitlement Creation Process Action
Retrigger entitlement creation process for failed or unprocessed assets.
SEE ALSO:
Actions Developer Guide: Overview
REST API Developer Guide: Invocable Actions Standard
Salesforce Help: Usage Management
Invoke Summary Creation Action
Invoke the service that creates various summaries, such as usage, ratable, and liable summaries where the usage amount is zero. The
service also checks and updates the billing period of the usage entitlement account if the billing period is expired.
This action is available in API version 63.0 and later.
1908
Usage Management Standard Invocable ActionsUsage Management

===== PAGE 1923 =====

Special Access Rules
The Invoke Summary Creation action is available in Enterprise, Developer, and Unlimited Editions where Usage Management is enabled.
To use this action, you need the Usage Management Run Time User permission.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/invokeSummaryCreationService
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
usageEntitlementAccountId
Description
Required.
ID of the usage entitlement account record that’s used to create summaries.
Outputs
None.
Example
POST
This example shows a sample request for the Invoke Summary Creation action.
{
"inputs": [
{
"usageEntitlementAccountId": "3ttDU00000000iZYAQ"
}
]
}
This example shows a sample response for the Invoke Summary Creation action.
{
"actionName": "invokeSummaryCreationService",
1909
Invoke Summary Creation ActionUsage Management

===== PAGE 1924 =====

"errors": null,
"isSuccess": true
}
SEE ALSO:
Salesforce Help: Permission Set Licenses, Personas, and User Permissions for Usage Management
Process Consumption Overages Action
Process consumption overages for the usage summary records with SummaryComplete  status. This action uses the entitlement
service to process the overages.
This action is available in API version 63.0 and later.
Special Access Rules
The Process Consumption Overages action is available in Enterprise, Developer, and Unlimited Editions where Usage Management is
enabled. To use this action, you need the Usage Management Run Time User permission.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/processConsumptionOverages
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
usageRatableSummaryId
Description
Required.
ID of the usage ratable summary record that contains the consumption details, and is used to
calculate consumption overages and create usage entitlement entry records.
Outputs
None.
1910
Process Consumption Overages ActionUsage Management

===== PAGE 1925 =====

Example
POST
This example shows a sample request for the Process Consumption Overages action.
{
"inputs": [
{
"usageRatableSummaryId": "3ttDU00000000iZYAQ"
}
]
}
This example shows a sample response for the Process Consumption Overages action.
{
"actionName": "processConsumptionOverages",
"errors": null,
"isSuccess": true
}
SEE ALSO:
Salesforce Help: Permission Set Licenses, Personas, and User Permissions for Usage Management
Refresh Usage Entitlement Bucket Action
Refresh entitlements by evaluating the usage entitlement bucket records and creating a new usage entitlement entry.
This action is available in API version 63.0 and later.
Special Access Rules
The Refresh Usage Entitlement Bucket action is available in Enterprise, Developer, and Unlimited Editions where Usage Management is
enabled. To use this action, you need the Usage Management Run Time User permission.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/refreshUsageEntitlementBucket
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearer token
1911
Refresh Usage Entitlement Bucket ActionUsage Management

===== PAGE 1926 =====

Inputs
DetailsInput
Type
string
transactionUsageEntitlementId
Description
Required.
ID of the transaction usage entitlement record that's associated with the usage entitlement
buckets that you need to refresh.
Outputs
None.
Example
POST
This example shows a sample request for the Refresh Usage Entitlement Bucket action.
{
"inputs": [
{
"transactionUsageEntitlementId": "3ttDU00000000iZYAQ"
}
]
}
This example shows a sample response for the Refresh Usage Entitlement Bucket action.
{
"actionName": "refreshUsageEntitlementBucket",
"errors": null,
"isSuccess": true
}
SEE ALSO:
Salesforce Help: Permission Set Licenses, Personas, and User Permissions for Usage Management
Retrigger Entitlement Creation Process Action
Retrigger entitlement creation process for failed or unprocessed assets.
Trigger the entitlement creation process again in these scenarios.
• Process failed assets in the asset to entitlement journey.
• Assetize or create wallets for assets without corresponding records in Usage Management.
This action is available in API version 65.0 and later.
1912
Retrigger Entitlement Creation Process ActionUsage Management

===== PAGE 1927 =====

Special Access Rules
The Retrigger Entitlement Creation Process action is available in Enterprise, Developer, and Unlimited Editions where Usage Management
is enabled. To use this action, you need the Usage Management Run Time User permission.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/retriggerEntlCreaProc
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
string
assetId
Description
Required.
ID of the asset for which you want to trigger the asset to entitlement process again.
Outputs
None.
Example
POST
Here's a sample request for the Retrigger Entitlement Creation Process action.
{
"inputs": [
{
"assetId": "02iSB000000JzZFYA0"
}
]
}
1913
Retrigger Entitlement Creation Process ActionUsage Management

===== PAGE 1928 =====

Here's a sample response for the Retrigger Entitlement Creation Process action.
[
{
"actionName": "retriggerEntlCreaProc",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": null,
"sortOrder": -1,
"version": 1
}
]
Usage Management Business APIs
Use the Usage Management Business APIs to get details of a usage-based product that’s associated with an asset, an order item, or a
quote line item.
This table lists the available Usage Management resources.
DescriptionResource
Get details of a usage-based
product associated with an
/asset-management/assets/assetId/usage-details (GET)
asset. This covers details of
grants, resources, and
configured rates for the product,
including negotiated rates in
case of a rate override.
Get details of a usage-based
product associated with an
order item.
/commerce/sales-orders/line-items/orderItemId/usage-details (GET)
Get details of a usage-based
product associated with a quote
line item.
/commerce/quotes/line-items/quoteLineItemId/usage-details (GET)
Get details of grants, resources,
rates, and any configured
/revenue/usage-management/binding-objects/bindingObjectId/actions/usage-details
(GET)
policies for a specified binding
object.
Get a comprehensive
breakdown of overage charges
/revenue/usage-management/consumption/actions/trace (POST)
and resource drawdown,
enabling you to view
information that's applicable to
specific invoice lines.
1914
Usage Management Business APIsUsage Management

===== PAGE 1929 =====

DescriptionResource
Validate cross-object
relationships and business rules
for usage-based products.
/revenue/usage-management/usage-products/actions/validate (POST)
Resources
Learn more about the available Usage Management API resources.
Request Bodies
Learn more about the available request bodies of Usage Management APIs.
Response Bodies
Learn more about the available response bodies of Usage Management APIs.
SEE ALSO:
Connect REST API Developer Guide: Introduction
Resources
Learn more about the available Usage Management API resources.
Asset Usage Details (GET)
Get details of a usage-based product associated with an asset. This covers details of grants, resources, and configured rates for the
product, including negotiated rates in case of a rate override.
Binding Object Usage Details (GET)
Get details of grants, resources, rates, and any configured policies for a specified binding object.
Consumption Traceabilities (POST)
Get a comprehensive breakdown of overage charges and resource drawdown, enabling you to view information that's applicable
to specific invoice lines.
Order Item Usage Details (GET)
Get details of a usage-based product associated with an order item.
Quote Line Item Usage Details (GET)
Get details of a usage-based product associated with a quote line item.
Usage Product Validation (POST)
Validate cross-object relationships and business rules for usage-based products.
Asset Usage Details (GET)
Get details of a usage-based product associated with an asset. This covers details of grants, resources, and configured rates for the
product, including negotiated rates in case of a rate override.
Here are the details that this API returns.
• Grants and resources for the product, if rates aren’t configured.
• Grants, resources, and any configured rates for the product. The rates are returned by the Rate Plan (GET) API.
1915
ResourcesUsage Management

===== PAGE 1930 =====

• Resources that include grants, if applicable, and any negotiated rates for the product in case of a rate override request.
This API doesn't return binding target rates. Use the Binding Object Usage Details API to retrieve binding target rates.
Resource
/asset-management/assets/assetId/usage-details
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/asset-management/assets/02iRM0000000tCdYAI/usage-details
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
63.0RequiredID of the asset.StringassetId
Query parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0RequiredDate that's used to search for the
applicable rate card entries.
StringeffectiveDate
63.0OptionalCustom fields that you can use to query
these objects.
String[]optionalFields
• AssetRateCardEntry
• AssetRateAdjustment
Response body for GET
Usage Details
Binding Object Usage Details (GET)
Get details of grants, resources, rates, and any configured policies for a specified binding object.
Use this API to display the details for a binding object during the selling journey. Additionally, display the details after assetization on
the selected binding objects.
The supported binding objects are Account, Contract, BindingObjectCustomExt, or Anchor Asset that's not bound to a target.
Resource
/revenue/usage-management/binding-objects/bindingObjectId/actions/usage-details
1916
ResourcesUsage Management

===== PAGE 1931 =====

Resource example
https://yourInstance.salesforce.com/services/data/v66.0/revenue/usage-management/binding-objects/1BRxx0000004C9EGAU/actions/usage-details?effectiveDate=2025-08-07
Available version
65.0
HTTP methods
GET
Path parameter for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
65.0RequiredID of the binding object.StringbindingObjectId
Query parameter for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
65.0RequiredDate filter that's used to retrieve the grants,
rates, and applicable policies as of the
specified date in yyyy-MM-dd  format.
StringeffectiveDate
Response body for GET
Binding Object Usage Detail
Consumption Traceabilities (POST)
Get a comprehensive breakdown of overage charges and resource drawdown, enabling you to view information that's applicable to
specific invoice lines.
This API provides an automated, clear, and traceable breakdown of all charges with details of specific rates, tiers, and discounts.
Resource
/revenue/usage-management/consumption/actions/trace
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/revenue/usage-management/consumption/actions/trace
Available version
66.0
HTTP methods
POST
1917
ResourcesUsage Management

===== PAGE 1932 =====

Request body for POST
JSON example
{
"liableSummaryIds": [
"1HG000000000001"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0RequiredList of liable summary IDs to trace the
consumption.
String[]liableSummaryIds
Response body for POST
Consumption Traceabilities
Order Item Usage Details (GET)
Get details of a usage-based product associated with an order item.
Here are the details that this API returns.
• Grants and resources for the product, if rates aren’t configured.
• Grants, resources, and any configured rates for the product. The rates are returned by the Rate Plan (GET) API.
• Resources that include grants, if applicable, and any negotiated rates for the product in case of a rate override request.
This API doesn't return binding target rates. Use the Binding Object Usage Details API to retrieve binding target rates.
Resource
/commerce/sales-orders/line-items/orderItemId/usage-details
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/commerce/sales-orders/line-items/802SG000003vZ15YAE/usage-details
https://yourInstance.salesforce.com/services/data
/v66.0/commerce/sales-orders/line-items/802SG000003vZ15YAE/usage-details?optionalFields=OrderItemRateCardEntry.MyCustomDate__c,OrderItemRateCardEntry.MyCustomNumber__c,OrderItemRateAdjustment.myCustomString__c
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
63.0RequiredID of the order item.StringorderItemId
1918
ResourcesUsage Management

===== PAGE 1933 =====

Query parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0OptionalDate that's used to search for the
applicable rate card entries.
StringeffectiveDate
63.0OptionalCustom fields that you can use to query
these objects.
String[]optionalFields
• OrderItemRateCardEntry
• OrderItemRateAdjustment
Response body for GET
Usage Details
Quote Line Item Usage Details (GET)
Get details of a usage-based product associated with a quote line item.
Here are the details that this API returns.
• Grants and resources for the product, if rates aren’t configured.
• Grants, resources, and any configured rates for the product. The rates are returned by the Rate Plan (GET) API.
• Resources that include grants, if applicable, and any negotiated rates for the product in case of a rate override request.
This API doesn't return binding target rates. Use the Binding Object Usage Details API to retrieve binding target rates.
Resource
/commerce/quotes/line-items/quoteLineItemId/usage-details
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/commerce/quotes/line-items/0QLXXXXXXXXXXXABC/usage-details
Available version
62.0
HTTP methods
GET
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
62.0OptionalDate that's used to search for the
applicable rate card entries.
StringeffectiveDate
62.0OptionalCustom fields that you can use to query
these objects.
String[]optionalFields
• QuoteLineRateCardEntry
1919
ResourcesUsage Management

===== PAGE 1934 =====

Available
Version
Required or
Optional
DescriptionTypeParameter
Name
• QuoteLineRateAdjustment
Response body for GET
Usage Details
Usage Product Validation (POST)
Validate cross-object relationships and business rules for usage-based products.
This API returns validation results with errors and warnings.
Resource
/revenue/usage-management/usage-products/actions/validate
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/revenue/usage-management/usage-products/actions/validate
Available version
66.0
HTTP methods
POST
Request body for POST
JSON example
{
"productIds": [
"01txx0000006i2gAAA",
"01txx0000006j2gAAA"
],
"startDate": "2024-01-01T00:00:00Z",
"endDate": "2024-12-31T23:59:59Z"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0RequiredList of product IDs to be validated. The
maximum limit is 10  valid product IDs.
String[]productIds
66.0OptionalStart date of the date range in which all
active records are validated.
StringstartDate
66.0OptionalEnd date of the date range in which all
active records are validated.
StringendDate
1920
ResourcesUsage Management

===== PAGE 1935 =====

Response body for POST
Usage Product Validation
Request Bodies
Learn more about the available request bodies of Usage Management APIs.
Consumption Traceabilities Input
Input representation of the details of the liable summary IDs that are used to trace the consumption.
Usage Product Validation Input
Input representation of the usage product validation request.
Consumption Traceabilities Input
Input representation of the details of the liable summary IDs that are used to trace the consumption.
JSON example
{
"liableSummaryIds": [
"1HG000000000001"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0RequiredList of liable summary IDs to trace the
consumption.
String[]liableSummaryIds
Usage Product Validation Input
Input representation of the usage product validation request.
JSON example
{
"productIds": [
"01txx0000006i2gAAA",
"01txx0000006j2gAAA"
],
"startDate": "2024-01-01T00:00:00Z",
"endDate": "2024-12-31T23:59:59Z"
}
1921
Request BodiesUsage Management

===== PAGE 1936 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0RequiredList of product IDs to be validated. The
maximum limit is 10  valid product IDs.
String[]productIds
66.0OptionalStart date of the date range in which all
active records are validated.
StringstartDate
66.0OptionalEnd date of the date range in which all
active records are validated.
StringendDate
Response Bodies
Learn more about the available response bodies of Usage Management APIs.
Asset Detail
Output representation of the details of a specific asset.
Billing Period
Output representation of the details of a specific billing period.
Binding Object Detail
Output representation of the list of records with the binding target details.
Binding Object Grant Detail
Output representation of the details of usage resource grants for a specified binding object.
Binding Object Rate Adjustments
Output representation of the details of binding target rate adjustments.
Binding Object Rate
Output representation of the details of Binding Object Rates object or Asset Rates object.
Binding Object Resource Grant And Policy Detail
Output representation of the details of resource grants and binding policies.
Binding Object Resource Policy Detail
Output representation of the details of a usage resource policy.
Binding Object Usage Detail
Output representation of the usage details of a binding object.
Consumption Source Detail
Output representation of the details of a specific consumption source.
Consumption Traceabilities
Output representation of the overage and resource drawdown details.
Errors
Output representation of the group of error messages with the same error code.
1922
Response BodiesUsage Management

===== PAGE 1937 =====

Error Details
Output representation of the top-level error detail when validation fails.
Error Message
Output representation of the details of records that failed with this specific error.
Error Warning Details
Output representation of the individual warning or error message with associated record details.
Consumption Traceabilities Data
Output representation of the list of asset details.
Fields Response
Output representation of the details of the optional fields on the usage-based selling-related objects.
Grant Detail
Output representation of the details of a grant from the ProductUsageGrant, LineItemUsageResourceGrant, or
TransactionUsageEntitlement objects.
Generic Error Details
Output representation of the error details encountered during the API request.
Lookup Detail
Output representation of the details of a usage resource record.
Policy Details
Output representation of the details of a policy.
Product Validation Result
Output representation of the validation result for a specific product.
Rate Adjustments
Output representation of the details of a rate adjustment.
Rate and Consumption Source Detail
Output representation of the details of a specific rate and its consumption source.
Rate Card Entry
Output representation of the details of a rate card entry.
Record Details
Output representation of the record details including ID and name.
Resource Detail
Output representation of the details of a specific usage resource.
Resource Policy Detail
Output representation of the details of a usage resource policy.
Usage Details
Output representation of the usage details of a quote, an order, or an asset.
Usage Details Error Response
Output representation of the details of an error related to usage details.
Usage Product Validation
Output representation of all the performed validations.
Usage Resource Grant And Policy Detail
Output representation of the details of a usage resource grant and policy.
1923
Response BodiesUsage Management

===== PAGE 1938 =====

Validation Error
Output representation of the validation errors grouped by rule name.
Validation Result
Output representation of the validation results grouped by rule name.
Validation Warning
Output representation of the validation warnings grouped by rule name.
Warnings
Output representation of a group of warning messages with the same warning code.
Warning Message
Output representation of the details of records that triggered this specific warning.
Asset Detail
Output representation of the details of a specific asset.
JSON example
{
"assets": [
{
"assetId": "ASSET1",
"usageEntitlementAccountId": "1EA000000000001",
"grantBindingTargetId": "1GB000000000001",
"billingPeriods": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"resources": [
{
"liableSummaryId": "1HG000000000001",
"usageResourceId": "1BX000000000004",
"usageResourceName": "SF Credits",
"usageResourceUomId": "1UM000000000001",
"usageResourceUomUnitCode": "CREDIT",
"resourceTotalOverageQuantity": 333.33,
"resourceTotalOverageAmount": 333.33,
"resourceTotalConsumption": 1500,
"rateAndConsumptionSources": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"rateUomId": "USD",
"ratableSummaryId": "URS3",
"ratingExecutionId": "1RE000000000001",
"overageQuantity": 333.33,
"overageAmount ": 333.33,
"totalConsumption": 1500,
"netUnitRate": 1,
"consumptionSources": [
{
"consumptionSourceId": "1AE000000000001",
1924
Response BodiesUsage Management

===== PAGE 1939 =====

"consumptionUnit": 500
},
{
"consumptionSourceId": "1CO000000000001",
"consumptionUnit": 375,
"commitRate": 1.5,
"targetRate": 2,
"cmtAssetRatableSummaryId": "URSCARID1"
},
{
"consumptionSourceId": "1CO000000000002",
"consumptionUnit": 125,
"commitRate": 0.75,
"targetRate": 1,
"cmtAssetRatableSummaryId": "URSCARID2"
}
]
}
]
}
]
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Unique identifier of the related asset.StringassetId
66.0Big, 66.0List of billing periods for the asset.Billing Period[]billingPeriods
66.0Big, 66.0ID of the object the consumption is bound
to.
StringgrantBinding
TargetId
66.0Big, 66.0ID of the account that holds the usage
entitlement.
StringusageEntitlement
AccountId
Billing Period
Output representation of the details of a specific billing period.
JSON example
{
"billingPeriods": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"resources": [
{
"liableSummaryId": "1HG000000000001",
1925
Response BodiesUsage Management

===== PAGE 1940 =====

"usageResourceId": "1BX000000000004",
"usageResourceName": "SF Credits",
"usageResourceUomId": "1UM000000000001",
"usageResourceUomUnitCode": "CREDIT",
"resourceTotalOverageQuantity": 333.33,
"resourceTotalOverageAmount": 333.33,
"resourceTotalConsumption": 1500,
"rateAndConsumptionSources": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"rateUomId": "USD",
"ratableSummaryId": "URS3",
"ratingExecutionId": "1RE000000000001",
"overageQuantity": 333.33,
"overageAmount ": 333.33,
"totalConsumption": 1500,
"netUnitRate": 1,
"consumptionSources": [
{
"consumptionSourceId": "1AE000000000001",
"consumptionUnit": 500
},
{
"consumptionSourceId": "1CO000000000001",
"consumptionUnit": 375,
"commitRate": 1.5,
"targetRate": 2,
"cmtAssetRatableSummaryId": "URSCARID1"
},
{
"consumptionSourceId": "1CO000000000002",
"consumptionUnit": 125,
"commitRate": 0.75,
"targetRate": 1,
"cmtAssetRatableSummaryId": "URSCARID2"
}
]
}
]
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0End date of the billing period.StringendDate
66.0Big, 66.0List of usage resources within the billing
period.
Resource Detail[]resources
1926
Response BodiesUsage Management

===== PAGE 1941 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Start date of the billing period.StringstartDate
Binding Object Detail
Output representation of the list of records with the binding target details.
JSON example
This example includes the details of a binding object.
{
"records": [
{
"bindingObjectRate": {
"id": "1QNSB0000001JyH4AU,1QNSB0000001JyI4AU",
"negotiatedRate": null,
"negotiatedRateAdjustments": [
{
"lowerBound": 101,
"name": null,
"rateAdjustmentId": "1DMSB000001N3C74AK",
"rateAdjustmentType": "Amount",
"rateAdjustmentValue": 10,
"tierUnitOfMeasure": "USD",
"upperBound": null
},
{
"lowerBound": 1,
"name": null,
"rateAdjustmentId": "1DMSB000001N3C64AK",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 30,
"tierUnitOfMeasure": "USD",
"upperBound": 100
}
],
"rate": 100,
"rateCardEntryId": "1CJSB000000207R4AQ,1CJSB000000207S4AQ",
"rateUnitOfMeasureName": "USD"
},
"bindingObjectResourceGrantAndPolicyDetail": {
"bindingObjectGrantDetail": [
{
"effectiveEndDate": "Sat Oct 04 23:59:59 GMT 2025",
"effectiveStartDate": "Fri Sep 05 00:00:00 GMT 2025",
"grantType": "Grant",
"id": "1B0SB0000000Eiv0AE",
"product": {
"id": "01tSB000006XMtqYAG"
},
"quantity": 100,
"record": {
1927
Response BodiesUsage Management

===== PAGE 1942 =====

"id": "02iSB000000IoETYA0"
},
"unitOfMeasure": {
"id": "0hESB0000003yfp2AA"
},
"usageRefreshPolicy": {
"id": "1BYSB0000001lOH4AY",
"negotiable": null
},
"usageRolloverPolicy": {
"id": "1BVSB000000A1xJ4AS",
"negotiable": null
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
}
],
"bindingObjectResourcePolicyDetail": {
"drawdownOrder": "ExpiringFirst",
"id": "1X2SB00000002WT0AY",
"ratingFrequencyPolicy": {
"id": "1HJSB0000000G3B4AU",
"negotiable": null
},
"usageAggregationPolicy": {
"id": "1cfSB0000001xHPYAY",
"negotiable": null
},
"usageCommitmentPolicy": {
"id": null,
"negotiable": null
},
"usageOveragePolicy": {
"id": "7UkSB00000002OP0AY",
"negotiable": null
}
}
},
"usageResource": {
"id": "1BRSB0000001x4h4AA"
}
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0Details about the Binding Object
Rates object or Asset Rates  object.
Binding Object Ratebinding
ObjectRate
65.0Big, 65.0Details about the resource grants and
binding policies.
Binding Object
Resource Grant and
Policy Detail
bindingObject
ResourceGrantAnd
PolicyDetail
1928
Response BodiesUsage Management

===== PAGE 1943 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0Details of the usage resource such as the ID
of the record.
Lookup DetailusageResource
Binding Object Grant Detail
Output representation of the details of usage resource grants for a specified binding object.
JSON example
This example includes the details of usage resource grants for a specified binding object.
{
"bindingObjectGrantDetail": [
{
"effectiveEndDate": "Sat Oct 04 23:59:59 GMT 2025",
"effectiveStartDate": "Fri Sep 05 00:00:00 GMT 2025",
"grantType": "Grant",
"id": "1B0SB0000000Eiv0AE",
"product": {
"id": "01tSB000006XMtqYAG"
},
"quantity": 100,
"record": {
"id": "02iSB000000IoETYA0"
},
"unitOfMeasure": {
"id": "0hESB0000003yfp2AA"
},
"usageRefreshPolicy": {
"id": "1BYSB0000001lOH4AY",
"negotiable": null
},
"usageRolloverPolicy": {
"id": "1BVSB000000A1xJ4AS",
"negotiable": null
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0Effective end date for the asset lifecycle.Stringeffective
EndDate
65.0Big, 65.0Effective start date for the asset lifecycle.Stringeffective
StartDate
65.0Big, 65.0Type of usage resource grant.StringgrantType
1929
Response BodiesUsage Management

===== PAGE 1944 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0ID of the Transaction Usage
Entitlement record responsible for the
grant.
Stringid
65.0Big, 65.0Details of the product.Lookup Detailproduct
65.0Big, 65.0Quantity of the binding object usage
resource grant.
Doublequantity
65.0Big, 65.0ID of the asset.Lookup Detailrecord
65.0Big, 65.0unit of measure of the usage resource.Lookup DetailunitOfMeasure
65.0Big, 65.0ID of the usage grant refresh policy.Policy DetailusageRefresh
Policy
65.0Big, 65.0ID of the usage grant rollover policy.Policy DetailusageRollover
Policy
65.0Big, 65.0Validity period term of the usage resource
grant.
DoublevalidityPeriod
Term
65.0Big, 65.0Validity period unit of the usage resource
grant.
StringvalidityPeriod
Unit
Binding Object Rate Adjustments
Output representation of the details of binding target rate adjustments.
JSON example
This example includes the details of binding target rate adjustments.
{
"negotiatedRateAdjustments": [
{
"lowerBound": 101,
"name": null,
"rateAdjustmentId": "1DMSB000001N3C74AK",
"rateAdjustmentType": "Amount",
"rateAdjustmentValue": 10,
"tierUnitOfMeasure": "USD",
"upperBound": null
},
{
"lowerBound": 1,
"name": null,
"rateAdjustmentId": "1DMSB000001N3C64AK",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 30,
"tierUnitOfMeasure": "USD",
"upperBound": 100
}
1930
Response BodiesUsage Management

===== PAGE 1945 =====

]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0Minimum quantity for the adjustment to be
applicable.
DoublelowerBound
65.0Small, 65.0Name of the tier or binding object rate
adjustment.
Stringname
65.0Small, 65.0ID of the binding object rate adjustment.StringrateAdjustmentId
65.0Small, 65.0Type of the binding object rate adjustment.StringrateAdjustmentType
65.0Small, 65.0Value of the binding object rate adjustment.DoublerateAdjustmentValue
65.0Small, 65.0Unit of measure that represents the tier or
binding object rate adjustment.
StringtierUnitOfMeasure
65.0Small, 65.0Maximum quantity for the adjustment to
be applicable.
DoubleupperBound
Binding Object Rate
Output representation of the details of Binding Object Rates object or Asset Rates object.
JSON example
This example includes the details of a binding object rate.
{
"bindingObjectRate": {
"id": "1QNSB0000001JyH4AU,1QNSB0000001JyI4AU",
"negotiatedRate": null,
"negotiatedRateAdjustments": [
{
"lowerBound": 101,
"name": null,
"rateAdjustmentId": "1DMSB000001N3C74AK",
"rateAdjustmentType": "Amount",
"rateAdjustmentValue": 10,
"tierUnitOfMeasure": "USD",
"upperBound": null
},
{
"lowerBound": 1,
"name": null,
"rateAdjustmentId": "1DMSB000001N3C64AK",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 30,
"tierUnitOfMeasure": "USD",
"upperBound": 100
}
1931
Response BodiesUsage Management

===== PAGE 1946 =====

],
"rate": 100,
"rateCardEntryId": "1CJSB000000207R4AQ,1CJSB000000207S4AQ",
"rateUnitOfMeasureName": "USD"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0ID of the Binding Object Rate
Card Entry or Asset Rate Card
Entry  object.
Stringid
65.0Big, 65.0Negotiated rate available in the Binding
Object Rate Card Entry  or
Asset Rate Card Entry  object.
Doublenegotiated
Rate
65.0Big, 65.0List of rate adjustments available in the
Binding Object Rate
Binding Object Rate
Adjustments[]
negotiatedRate
Adjustments
Adjustment  or Asset Rate
Adjustment.
65.0Big, 65.0Rate of the rate card entry associated to the
Binding Object Rate Card
Doublerate
Entry  or Asset Rate Card
Entry  object.
65.0Big, 65.0ID of the rate card entry associated to the
Binding Object Rate Card
StringrateCard
EntryId
Entry  or Asset Rate Card
Entry  object.
65.0Big, 65.0Rate unit of measure of the rates.StringrateUnitOf
MeasureName
Binding Object Resource Grant And Policy Detail
Output representation of the details of resource grants and binding policies.
JSON example
This example includes the details of resource grants and binding policies for a specified binding object.
{
"bindingObjectResourceGrantAndPolicyDetail": {
"bindingObjectGrantDetail": [
{
"effectiveEndDate": "Sat Oct 04 23:59:59 GMT 2025",
"effectiveStartDate": "Fri Sep 05 00:00:00 GMT 2025",
"grantType": "Grant",
"id": "1B0SB0000000Eiv0AE",
"product": {
"id": "01tSB000006XMtqYAG"
1932
Response BodiesUsage Management

===== PAGE 1947 =====

},
"quantity": 100,
"record": {
"id": "02iSB000000IoETYA0"
},
"unitOfMeasure": {
"id": "0hESB0000003yfp2AA"
},
"usageRefreshPolicy": {
"id": "1BYSB0000001lOH4AY",
"negotiable": null
},
"usageRolloverPolicy": {
"id": "1BVSB000000A1xJ4AS",
"negotiable": null
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
}
],
"bindingObjectResourcePolicyDetail": {
"drawdownOrder": "ExpiringFirst",
"id": "1X2SB00000002WT0AY",
"ratingFrequencyPolicy": {
"id": "1HJSB0000000G3B4AU",
"negotiable": null
},
"usageAggregationPolicy": {
"id": "1cfSB0000001xHPYAY",
"negotiable": null
},
"usageCommitmentPolicy": {
"id": null,
"negotiable": null
},
"usageOveragePolicy": {
"id": "7UkSB00000002OP0AY",
"negotiable": null
}
}
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0Details of the negotiated resource grants for
the specified binding object.
Binding Object Grant
Detail[]
bindingObject
GrantDetail
65.0Big, 65.0Detail of the binding policies.Binding Object
Resource Policy
Detail
bindingObject
ResourcePolicy
Detail
1933
Response BodiesUsage Management

===== PAGE 1948 =====

Binding Object Resource Policy Detail
Output representation of the details of a usage resource policy.
JSON example
This example includes the details of a usage resource policy.
{
"bindingObjectResourcePolicyDetail": {
"drawdownOrder": "ExpiringFirst",
"id": "1X2SB00000002WT0AY",
"ratingFrequencyPolicy": {
"id": "1HJSB0000000G3B4AU",
"negotiable": null
},
"usageAggregationPolicy": {
"id": "1cfSB0000001xHPYAY",
"negotiable": null
},
"usageCommitmentPolicy": {
"id": null,
"negotiable": null
},
"usageOveragePolicy": {
"id": "7UkSB00000002OP0AY",
"negotiable": null
}
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0Specifies the order or way to process the
drawdown. See Usage Management
StringdrawdownOrder
Essentials to know more about a drawdown
process.
65.0Big, 65.0ID of the Binding Object Usage
Resource Policy  record.
Stringid
65.0Big, 65.0Details of the rating frequency policy.Policy DetailratingFrequency
Policy
65.0Big, 65.0Details of the usage aggregation policy.Policy DetailusageAggregation
Policy
65.0Big, 65.0Details of the commitment policy of the
usage resource.
Policy DetailusageCommitment
Policy
65.0Big, 65.0Details of the overage policy of the usage
resource.
Policy DetailusageOverage
Policy
1934
Response BodiesUsage Management

===== PAGE 1949 =====

Binding Object Usage Detail
Output representation of the usage details of a binding object.
JSON example
This example shows a sample successful response.
{
"records": [
{
"bindingObjectRate": {
"id": "1QNSB0000001JyH4AU,1QNSB0000001JyI4AU",
"negotiatedRate": null,
"negotiatedRateAdjustments": [
{
"lowerBound": 101,
"name": null,
"rateAdjustmentId": "1DMSB000001N3C74AK",
"rateAdjustmentType": "Amount",
"rateAdjustmentValue": 10,
"tierUnitOfMeasure": "USD",
"upperBound": null
},
{
"lowerBound": 1,
"name": null,
"rateAdjustmentId": "1DMSB000001N3C64AK",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 30,
"tierUnitOfMeasure": "USD",
"upperBound": 100
}
],
"rate": 100,
"rateCardEntryId": "1CJSB000000207R4AQ,1CJSB000000207S4AQ",
"rateUnitOfMeasureName": "USD"
},
"bindingObjectResourceGrantAndPolicyDetail": {
"bindingObjectGrantDetail": [
{
"effectiveEndDate": "Sat Oct 04 23:59:59 GMT 2025",
"effectiveStartDate": "Fri Sep 05 00:00:00 GMT 2025",
"grantType": "Grant",
"id": "1B0SB0000000Eiv0AE",
"product": {
"id": "01tSB000006XMtqYAG"
},
"quantity": 100,
"record": {
"id": "02iSB000000IoETYA0"
},
"unitOfMeasure": {
"id": "0hESB0000003yfp2AA"
},
"usageRefreshPolicy": {
1935
Response BodiesUsage Management

===== PAGE 1950 =====

"id": "1BYSB0000001lOH4AY",
"negotiable": null
},
"usageRolloverPolicy": {
"id": "1BVSB000000A1xJ4AS",
"negotiable": null
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
}
],
"bindingObjectResourcePolicyDetail": {
"drawdownOrder": "ExpiringFirst",
"id": "1X2SB00000002WT0AY",
"ratingFrequencyPolicy": {
"id": "1HJSB0000000G3B4AU",
"negotiable": null
},
"usageAggregationPolicy": {
"id": "1cfSB0000001xHPYAY",
"negotiable": null
},
"usageCommitmentPolicy": {
"id": null,
"negotiable": null
},
"usageOveragePolicy": {
"id": "7UkSB00000002OP0AY",
"negotiable": null
}
}
},
"usageResource": {
"id": "1BRSB0000001x4h4AA"
}
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0List of errors encountered during the
processing of the API request.
Usage Detail Error
Response[]
errors
65.0Small, 65.0List of records that contains the binding
target details.
Binding Object
Detail[]
records
Consumption Source Detail
Output representation of the details of a specific consumption source.
1936
Response BodiesUsage Management

===== PAGE 1951 =====

JSON example
{
"consumptionSources": [
{
"consumptionSourceId": "1AE000000000001",
"consumptionUnit": 500
},
{
"consumptionSourceId": "1CO000000000001",
"consumptionUnit": 375,
"commitRate": 1.5,
"targetRate": 2,
"cmtAssetRatableSummaryId": "URSCARID1"
},
{
"consumptionSourceId": "1CO000000000002",
"consumptionUnit": 125,
"commitRate": 0.75,
"targetRate": 1,
"cmtAssetRatableSummaryId": "URSCARID2"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0ID for querying rating waterfall.StringcmtAssetRatable
SummaryId
66.0Big, 66.0Net unit rate at which drawdown is done
for commitment products.
DoublecommitRate
66.0Big, 66.0Object on which the consumption was
recorded.
Stringconsumption
SourceId
66.0Big, 66.0Recorded quantity of consumption.Doubleconsumption
Unit
66.0Big, 66.0Input unit rate which is used for
commitment products.
DoubletargetRate
Consumption Traceabilities
Output representation of the overage and resource drawdown details.
JSON example
{
"success": true,
"data": {
"assets": [
{
1937
Response BodiesUsage Management

===== PAGE 1952 =====

"assetId": "ASSET1",
"usageEntitlementAccountId": "1EA000000000001",
"grantBindingTargetId": "1GB000000000001",
"billingPeriods": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"resources": [
{
"liableSummaryId": "1HG000000000001",
"usageResourceId": "1BX000000000004",
"usageResourceName": "SF Credits",
"usageResourceUomId": "1UM000000000001",
"usageResourceUomUnitCode": "CREDIT",
"resourceTotalOverageQuantity": 333.33,
"resourceTotalOverageAmount": 333.33,
"resourceTotalConsumption": 1500,
"rateAndConsumptionSources": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"rateUomId": "USD",
"ratableSummaryId": "URS3",
"ratingExecutionId": "1RE000000000001",
"overageQuantity": 333.33,
"overageAmount ": 333.33,
"totalConsumption": 1500,
"netUnitRate": 1,
"consumptionSources": [
{
"consumptionSourceId": "1AE000000000001",
"consumptionUnit": 500
},
{
"consumptionSourceId": "1CO000000000001",
"consumptionUnit": 375,
"commitRate": 1.5,
"targetRate": 2,
"cmtAssetRatableSummaryId": "URSCARID1"
},
{
"consumptionSourceId": "1CO000000000002",
"consumptionUnit": 125,
"commitRate": 0.75,
"targetRate": 1,
"cmtAssetRatableSummaryId": "URSCARID2"
}
]
}
]
}
]
}
]
1938
Response BodiesUsage Management

===== PAGE 1953 =====

}
],
"error": null
}
}
Available VersionFilter Group and
Version
DescriptionTypezProperty Name
66.0Big, 66.0Payload that contains the traceability details.Consumption
Traceabilities Data[]
data
66.0Big, 66.0Error details if the request isn't successful.Generic Error
Details[]
error
66.0Big, 66.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
Errors
Output representation of the group of error messages with the same error code.
JSON example
This example shows a group of error messages with the same error code.
{
"errors": [
{
"errorCode": "EFFECTIVITY_MISMATCH",
"errorMessages": [
{
"errorMessage": "PUR and RCE effective date ranges must have overlap for proper
rating functionality",
"errorDetails": []
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Standardized error code. For example,
EFFECTIVITY_MISMATCH.
StringerrorCode
66.0Big, 66.0List of error messages for records that failed
with this error code.
Error Message[]errorMessages
Error Details
Output representation of the top-level error detail when validation fails.
1939
Response BodiesUsage Management

===== PAGE 1954 =====

JSON example
This example shows a sample error response.
{
"errors": [
{
"errorCode": "VALIDATION_FAILED",
"message": "Product validation completed with cross-entity errors",
"products": [
{
"productId": "01txx0000006i2gAAA",
"validationResult": {
"validationErrors": [],
"validationWarnings": []
}
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Standardized error code. For example,
VALIDATION_FAILED.
StringerrorCode
66.0Big, 66.0Human-readable error message that
describes the overall validation failure.
Stringmessage
66.0Big, 66.0List of product validation results.Product Validation
Result[]
products
Error Message
Output representation of the details of records that failed with this specific error.
JSON example
This example shows an error message with details.
{
"errorMessages": [
{
"errorMessage": "PUR and RCE effective date ranges must have overlap for proper
rating functionality",
"errorDetails": [
{
"relatedObjectAPIName": "ProductUsageRule",
"records": [
{
"id": "a0bxx0000004CqZAAU",
"name": "PUR-001"
}
]
1940
Response BodiesUsage Management

===== PAGE 1955 =====

}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Human-readable error message that
describes the validation failure.
StringerrorMessage
66.0Big, 66.0Details of records that failed with this
specific error.
Error Warning
Details[]
errorDetails
Error Warning Details
Output representation of the individual warning or error message with associated record details.
JSON example
This example shows error details with record information.
{
"errorDetails": [
{
"relatedObjectAPIName": "ProductUsageRule",
"records": [
{
"id": "a0bxx0000004CqZAAU",
"name": "PUR-001"
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0API name of the related object.StringrelatedObjectAPIName
66.0Big, 66.0Details of records that triggered the specific
warning or error.
Record Details[]records
Consumption Traceabilities Data
Output representation of the list of asset details.
JSON example
{
"data": {
"assets": [
1941
Response BodiesUsage Management

===== PAGE 1956 =====

{
"assetId": "ASSET1",
"usageEntitlementAccountId": "1EA000000000001",
"grantBindingTargetId": "1GB000000000001",
"billingPeriods": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"resources": [
{
"liableSummaryId": "1HG000000000001",
"usageResourceId": "1BX000000000004",
"usageResourceName": "SF Credits",
"usageResourceUomId": "1UM000000000001",
"usageResourceUomUnitCode": "CREDIT",
"resourceTotalOverageQuantity": 333.33,
"resourceTotalOverageAmount": 333.33,
"resourceTotalConsumption": 1500,
"rateAndConsumptionSources": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"rateUomId": "USD",
"ratableSummaryId": "URS3",
"ratingExecutionId": "1RE000000000001",
"overageQuantity": 333.33,
"overageAmount ": 333.33,
"totalConsumption": 1500,
"netUnitRate": 1,
"consumptionSources": [
{
"consumptionSourceId": "1AE000000000001",
"consumptionUnit": 500
},
{
"consumptionSourceId": "1CO000000000001",
"consumptionUnit": 375,
"commitRate": 1.5,
"targetRate": 2,
"cmtAssetRatableSummaryId": "URSCARID1"
},
{
"consumptionSourceId": "1CO000000000002",
"consumptionUnit": 125,
"commitRate": 0.75,
"targetRate": 1,
"cmtAssetRatableSummaryId": "URSCARID2"
}
]
}
]
}
]
}
1942
Response BodiesUsage Management

===== PAGE 1957 =====

]
}
]
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0List of assets for the specified liable
summaries.
Asset Detail[]assets
Fields Response
Output representation of the details of the optional fields on the usage-based selling-related objects.
JSON Example
"fields": {
"MyCustomDate__c": {
"displayValue": "2024-09-24",
"value": "2024-09-24T17:46:30.662Z"
},
"MyCustomNumber__c": {
"displayValue": "20.0",
"value": 20
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Big, 63.0Display value of a field.StringdisplayValue
63.0Big, 63.0Value of a field in its original data form.Objectvalue
Grant Detail
Output representation of the details of a grant from the ProductUsageGrant, LineItemUsageResourceGrant, or TransactionUsageEntitlement
objects.
JSON Example
{
"negotiatedGrantDetail": {
"grantType": "Grant",
"id": "1X6xx00000000OECAY",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"displayName": null,
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
1943
Response BodiesUsage Management

===== PAGE 1958 =====

},
"usageRolloverPolicy": {
"displayName": null,
"id": "1BVxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 12,
"validityPeriodUnit": "Month"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0Details about the grant type.StringgrantType
65.0Big, 65.0ID of the usage resource grant.Stringid
65.0Big, 65.0Quantity of the negotiated usage resource
grant.
Doublequantity
65.0Big, 65.0Specifies whether the grant is negotiable or
not.
StringusageGrant
Negotiable
65.0Big, 65.0ID of the usage grant refresh policy.Policy DetailusageRefresh
Policy
65.0Big, 65.0ID of the usage grant rollover policy.Policy DetailusageRollover
Policy
65.0Big, 65.0Validity period term of the grant.Doublevalidity
PeriodTerm
65.0Big, 65.0Validity period unit of the grant.Stringvalidity
PeriodUnit
Generic Error Details
Output representation of the error details encountered during the API request.
JSON example
{
"data": [],
"error": {
"errorCode": "INVALID_API_INPUT",
"message": "Liable summary IDs cannot be null or empty."
},
"success": false
}
1944
Response BodiesUsage Management

===== PAGE 1959 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Error code that represents the type of error.StringerrorCode
66.0Big, 66.0Detailed error message that specifies the
cause of failure.
Stringmessage
Lookup Detail
Output representation of the details of a usage resource record.
JSON example
This example includes the details of a usage resource.
{
"usageResource": {
"id": "1BRxx0000004C9EGAU"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0ID of the usage resource record.Stringid
Policy Details
Output representation of the details of a policy.
JSON example
This example includes the details for different policy types.
{
"bindingObjectGrantDetail": [
{
"effectiveEndDate": "Sat Oct 04 23:59:59 GMT 2025",
"effectiveStartDate": "Fri Sep 05 00:00:00 GMT 2025",
"grantType": "Grant",
"id": "1B0SB0000000Eiv0AE",
"product": {
"id": "01tSB000006XMtqYAG"
},
"quantity": 100,
"record": {
"id": "02iSB000000IoETYA0"
},
"unitOfMeasure": {
"id": "0hESB0000003yfp2AA"
},
"usageRefreshPolicy": {
"id": "1BYSB0000001lOH4AY",
"negotiable": null
1945
Response BodiesUsage Management

===== PAGE 1960 =====

},
"usageRolloverPolicy": {
"id": "1BVSB000000A1xJ4AS",
"negotiable": null
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0ID of the policy.Stringid
65.0Big, 65.0Indicates whether the policy is negotiable.
Valid values are:
Stringnegotiable
• Negotiable
• Non-Negotiable
Product Validation Result
Output representation of the validation result for a specific product.
JSON example
This example shows the product validation result.
{
"products": [
{
"productId": "01txx0000006i2gAAA",
"validationResult": {
"validationErrors": [],
"validationWarnings": []
}
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Unique product ID that's being validated.StringproductId
66.0Big, 66.0Validation results grouped by rule name.Validation ResultvalidationResult
Rate Adjustments
Output representation of the details of a rate adjustment.
1946
Response BodiesUsage Management

===== PAGE 1961 =====

JSON Example
"rateAdjustments": [
{
"fields": {},
"lowerBound": 0.0,
"name": null,
"negotiatedRateAdjustmentId": null,
"rateAdjustmentId": "1ENxx0000004C9BGAU",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 10.0,
"tierUnitOfMeasure": "USD",
"upperBound": 50.0
}
]
If the negotiable  property value that’s associated with a rate card entry is blank, then the data is derived from Product Catalog
Management. If it isn’t blank, then the data is derived from Rate Management.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Big, 63.0List of optional fields and their values that
belong to the rate adjustment object.
Map<String, Fields
Response>
fields
63.0Small, 63.0Minimum quantity for the adjustment to be
applicable.
DoublelowerBound
63.0Small, 63.0Name of the tier.Stringname
63.0Small, 63.0ID of the negotiated rate adjustment.StringnegotiatedRate
AdjustmentId
63.0Small, 63.0ID of the rate adjustment.StringrateAdjustment
Id
63.0Small, 63.0Type of the rate adjustment.StringrateAdjustment
Type
63.0Small, 63.0Value of the rate adjustment.DoublerateAdjustment
Value
63.0Small, 63.0Unit of measure representing the tier.StringtierUnitOf
Measure
63.0Small, 63.0Maximum quantity for the adjustment to
be applicable.
DoubleupperBound
Rate and Consumption Source Detail
Output representation of the details of a specific rate and its consumption source.
1947
Response BodiesUsage Management

===== PAGE 1962 =====

JSON example
{
"rateAndConsumptionSources": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"rateUomId": "USD",
"ratableSummaryId": "URS3",
"ratingExecutionId": "1RE000000000001",
"overageQuantity": 333.33,
"overageAmount ": 333.33,
"totalConsumption": 1500,
"netUnitRate": 1,
"consumptionSources": [
{
"consumptionSourceId": "1AE000000000001",
"consumptionUnit": 500
},
{
"consumptionSourceId": "1CO000000000001",
"consumptionUnit": 375,
"commitRate": 1.5,
"targetRate": 2,
"cmtAssetRatableSummaryId": "URSCARID1"
},
{
"consumptionSourceId": "1CO000000000002",
"consumptionUnit": 125,
"commitRate": 0.75,
"targetRate": 1,
"cmtAssetRatableSummaryId": "URSCARID2"
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Details on the consumption source.Consumption Source
Detail[]
consumptionSource
Details
66.0Big, 66.0End date for the specific rate period.StringendDate
66.0Big, 66.0Net unit rate.DoublenetUnitRate
66.0Big, 66.0Amount for the overage quantity.DoubleoverageAmt
66.0Big, 66.0Quantity of consumption that was rated as
overage.
DoubleoverageQty
66.0Big, 66.0Unique ID for the summary used in rating.Stringratable
SummaryId
1948
Response BodiesUsage Management

===== PAGE 1963 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Status of ratable summary.Stringratable
SummaryStatus
66.0Big, 66.0Unit of measure for the rate.StringrateUomId
66.0Big, 66.0Name of the rate unit of measureStringrateUomName
66.0Big, 66.0Execution ID of the rating.StringratingExecution
Id
66.0Big, 66.0ID of the source usage resource.StringsourceUsage
ResourceId
66.0Big, 66.0Name of the source usage resource.StringsourceUsage
ResourceName
66.0Big, 66.0Start date for the specific rate period.StringstartDate
66.0Big, 66.0Total quantity consumed for this rate.Doubletotal
Consumption
Rate Card Entry
Output representation of the details of a rate card entry.
JSON Example
{
"records": [
{
"bindingInstanceTargetType": "Product",
"bindingInstanceType": "Target",
"chargeForOverages": "Yes",
"fields": {},
"isOptional": false,
"name": "Paddle Board",
"negotiable": "Negotiable,Non-Negotiable",
"negotiatedRate": 20,
"negotiatedRateCardEntryId": "1ELxx0000004C9JGAU,1ELxx0000004C9KGAU",
"quantity": 15,
"rate": 5,
"rateAdjustments": [
{
"fields": {},
"lowerBound": 0,
"name": "Tier 1",
"negotiatedRateAdjustmentId": "1ENxx0000004C9BGAU",
"rateAdjustmentId": "1ENxx0000004C9BGAU",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 10,
"tierUnitOfMeasure": "USD",
"upperBound": 50
1949
Response BodiesUsage Management

===== PAGE 1964 =====

}
],
"rateCardEntryId": "1CJxx0000004C9IGAU,1CJxx0000004C9JGAU",
"rateUnitOfMeasureName": "USD",
"unitOfMeasure": "GB",
"usageResourceGrantAndPolicyDetail": {
"grantDetail": {
"grantType": "Grant",
"id": "1BXxx0000004C9lGAE",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedGrantDetail": {
"grantType": "Grant",
"id": "1X6xx00000000OECAY",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedResourcePolicyDetail": {
"id": "1X5xx00000000OECAY",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
1950
Response BodiesUsage Management

===== PAGE 1965 =====

"negotiable": null
}
},
"resourcePolicyDetail": {
"id": "7Suxx0000004C9kCAE",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
}
},
"usageResourceId": "1BRxx0000004C9CGAU"
}
]
}
If the negotiable  property value is blank, then the data is derived from Product Catalog Management. If it isn’t blank, then the data
is derived from Rate Management.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Big, 63.0Type of the target object that's associated
with this transaction.
Stringbinding
Instance
TargetType
63.0Big, 63.0Type of the binding instance. Valid values
are:
StringbindingInstance
Type
• Self
• Target
63.0Big, 63.0Specifies whether overage is permitted.
Valid values are:
StringchargeFor
Overages
• Yes
• No
• NA
63.0Big, 63.0List of optional fields and their values that's
associated with the rate card entry object.
Map<String, Fields
Response>
fields
1951
Response BodiesUsage Management

===== PAGE 1966 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0Indicates whether the product usage
resource is optional when the associated
BooleanisOptional
product is one of the commitment usage
model types (true) or not (false).
63.0Big, 63.0Name of the resource.Stringname
63.0Big, 63.0Type of the base rate and the tier rate, if
applicable. Valid values are:
Stringnegotiable
• Negotiable
• Non-Negotiable
63.0Big, 63.0User-overridden overage rate.Doublenegotiated
Rate
63.0Big, 63.0ID of the negotiated rate card entry and the
tier rate card entry, if applicable.
Stringnegotiated
RateCard
EntryId
63.0Big, 63.0Amount granted for the resource.Doublequantity
63.0Big, 63.0Base overage rate.Doublerate
63.0Big, 63.0List of tiers associated with the rate card
entry, if applicable.
Rate Adjustments[]rate
Adjustments
63.0Big, 63.0ID of the base rate card entry and the tier
rate card entry, if applicable.
StringrateCard
EntryId
64.0Big, 64.0Unit of measure for rates in the rate card
entry.
StringrateUnit
OfMeasureName
63.0Big, 63.0Unit of measure of the grant. For example,
Unit.
StringunitOfMeasure
65.0Big, 65.0ID of the usage resource.StringusageResource
Id
65.0Big, 65.0Details of a usage resource grant and policy.Usage Resource
Grant And Policy
Detail
usageResource
GrantAndPolicy
Detail
Record Details
Output representation of the record details including ID and name.
1952
Response BodiesUsage Management

===== PAGE 1967 =====

JSON example
This example shows the record details with ID and name.
{
"records": [
{
"id": "a0bxx0000004CqZAAU",
"name": "PUR-001"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Unique identifier of the object.Stringid
66.0Big, 66.0Display name of the object.Stringname
Resource Detail
Output representation of the details of a specific usage resource.
JSON example
{
"resources": [
{
"liableSummaryId": "1HG000000000001",
"usageResourceId": "1BX000000000004",
"usageResourceName": "SF Credits",
"usageResourceUomId": "1UM000000000001",
"usageResourceUomUnitCode": "CREDIT",
"resourceTotalOverageQuantity": 333.33,
"resourceTotalOverageAmount": 333.33,
"resourceTotalConsumption": 1500,
"rateAndConsumptionSources": [
{
"startDate": "2025-01-01",
"endDate": "2025-01-31",
"rateUomId": "USD",
"ratableSummaryId": "URS3",
"ratingExecutionId": "1RE000000000001",
"overageQuantity": 333.33,
"overageAmount ": 333.33,
"totalConsumption": 1500,
"netUnitRate": 1,
"consumptionSources": [
{
"consumptionSourceId": "1AE000000000001",
"consumptionUnit": 500
},
{
"consumptionSourceId": "1CO000000000001",
1953
Response BodiesUsage Management

===== PAGE 1968 =====

"consumptionUnit": 375,
"commitRate": 1.5,
"targetRate": 2,
"cmtAssetRatableSummaryId": "URSCARID1"
},
{
"consumptionSourceId": "1CO000000000002",
"consumptionUnit": 125,
"commitRate": 0.75,
"targetRate": 1,
"cmtAssetRatableSummaryId": "URSCARID2"
}
]
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Unique identifier for the consumption
summary.
StringliableSummaryId
66.0Big, 66.0Status of liable summary.StringliableSummary
Status
66.0Big, 66.0Details on rates and consumption sources.Rate And
Consumption Source
Detail[]
rateAnd
Consumption
Sources
66.0Big, 66.0Total quantity of consumption for the
resource.
DoubleresourceTotal
Consumption
66.0Big, 66.0Total amount for the overage.DoubleresourceTotal
OverageAmount
66.0Big, 66.0Total overage quantity.DoubleresourceTotal
OverageQuantity
66.0Big, 66.0ID of the specific usage resource.StringusageResource
Id
66.0Big, 66.0Name of the usage resource.StringusageResource
Name
66.0Big, 66.0Unit of measure ID for the usage resource.StringusageResource
UomId
66.0Big, 66.0Unit of measure code for the usage resource.StringusageResource
UomUnitCode
1954
Response BodiesUsage Management

===== PAGE 1969 =====

Resource Policy Detail
Output representation of the details of a usage resource policy.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0ID of the usage resource policy.Stringid
65.0Big, 65.0Details of the rating frequency policy.Policy DetailratingFrequency
Policy
65.0Big, 65.0Details of the usage aggregation policy.Policy DetailusageAggregation
Policy
65.0Big, 65.0Details of the usage commitment policy.Policy DetailusageCommitment
Policy
65.0Big, 65.0Details of the usage overage policy.Policy DetailusageOverage
Policy
Usage Details
Output representation of the usage details of a quote, an order, or an asset.
JSON example
This sample response shows resources that include grants, if applicable, and resources without rates when you retrieve the usage
details of an order item.
{
"records": [
{
"bindingInstanceTargetType": null,
"bindingInstanceType": null,
"chargeForOverages": "Yes",
"isOptional": false,
"fields": {},
"name": "API Calls",
"negotiable": ",",
"negotiatedRate": null,
"negotiatedRateCardEntryId": ",",
"quantity": 1000,
"rate": null,
"rateAdjustments": [],
"rateCardEntryId": ",",
"rateUnitOfMeasureName": "USD",
"unitOfMeasure": null,
"usageResourceGrantAndPolicyDetail": {
"grantDetail": {
"grantType": "Grant",
"id": "1BXxx0000004C9lGAE",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
1955
Response BodiesUsage Management

===== PAGE 1970 =====

"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedGrantDetail": {
"grantType": "Grant",
"id": "1X6xx00000000OECAY",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedResourcePolicyDetail": {
"id": "1X5xx00000000OECAY",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
},
"resourcePolicyDetail": {
"id": "7Suxx0000004C9kCAE",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
1956
Response BodiesUsage Management

===== PAGE 1971 =====

},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
}
},
"usageResourceId": "1BRxx0000004C9CGAU"
}
]
}
This example shows a sample response without negotiated rates when you retrieve the usage details of an order item.
{
"records": [
{
"bindingInstanceTargetType": "Product",
"bindingInstanceType": "Target",
"chargeForOverages": "Yes",
"isOptional": false,
"fields": {},
"name": "Paddle Board",
"negotiable": "Negotiable,Non-Negotiable",
"negotiatedRate": null,
"negotiatedRateCardEntryId": ",",
"quantity": 15,
"rate": 5,
"rateAdjustments": [
{
"fields": {},
"lowerBound": 0,
"name": null,
"negotiatedRateAdjustmentId": null,
"rateAdjustmentId": "1ENxx0000004C9BGAU",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 10,
"tierUnitOfMeasure": "USD",
"upperBound": 50
}
],
"rateCardEntryId": "1CJxx0000004C9IGAU,1CJxx0000004C9JGAU",
"rateUnitOfMeasureName": "USD",
"unitOfMeasure": "GB",
"usageResourceGrantAndPolicyDetail": {
"grantDetail": {
"grantType": "Grant",
"id": "1BXxx0000004C9lGAE",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
1957
Response BodiesUsage Management

===== PAGE 1972 =====

"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedGrantDetail": {
"grantType": "Grant",
"id": "1X6xx00000000OECAY",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedResourcePolicyDetail": {
"id": "1X5xx00000000OECAY",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
},
"resourcePolicyDetail": {
"id": "7Suxx0000004C9kCAE",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
1958
Response BodiesUsage Management

===== PAGE 1973 =====

},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
}
},
"usageResourceId": "1BRxx0000004C9CGAU"
}
]
}
This sample response shows negotiated rates when you retrieve the usage details of an order item. The negotiated rates are derived
from these objects for assets, order items, or quote line items.
• AssetRateCardEntry
• AssetRateAdjustment
• OrderItemRateCardEntry
• OrderItemRateAdjustment
• QuoteLineRateCardEntry
• QuoteLineRateAdjustment
{
"records": [
{
"bindingInstanceTargetType": "Product",
"bindingInstanceType": "Target",
"chargeForOverages": "Yes",
"isOptional": false,
"fields": {},
"name": "Paddle Board",
"negotiable": "Negotiable,Non-Negotiable",
"negotiatedRate": 20,
"negotiatedRateCardEntryId": "1ELxx0000004C9JGAU,1ELxx0000004C9KGAU",
"quantity": 15,
"rate": 5,
"rateAdjustments": [
{
"fields": {},
"lowerBound": 0,
"name": "Tier 1",
"negotiatedRateAdjustmentId": "1ENxx0000004C9BGAU",
"rateAdjustmentId": "1ENxx0000004C9BGAU",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 10,
"tierUnitOfMeasure": "USD",
"upperBound": 50
}
],
1959
Response BodiesUsage Management

===== PAGE 1974 =====

"rateCardEntryId": "1CJxx0000004C9IGAU,1CJxx0000004C9JGAU",
"rateUnitOfMeasureName": "USD",
"unitOfMeasure": "GB",
"usageResourceGrantAndPolicyDetail": {
"grantDetail": {
"grantType": "Grant",
"id": "1BXxx0000004C9lGAE",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedGrantDetail": {
"grantType": "Grant",
"id": "1X6xx00000000OECAY",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedResourcePolicyDetail": {
"id": "1X5xx00000000OECAY",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
1960
Response BodiesUsage Management

===== PAGE 1975 =====

},
"resourcePolicyDetail": {
"id": "7Suxx0000004C9kCAE",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
}
},
"usageResourceId": "1BRxx0000004C9CGAU"
}
]
}
This sample response shows details of the custom fields when you retrieve the usage details of an order item.
{
"records": [
{
"fields": {
"MyCustomDate__c": {
"displayValue": "2024-09-24",
"value": "2024-09-24T17:46:30.662Z"
},
"MyCustomNumber__c": {
"displayValue": "20.0",
"value": 20
}
},
"isOptional": false,
"bindingInstanceTargetType": "Product",
"bindingInstanceType": "Target",
"chargeForOverages": "Yes",
"name": "Therapy",
"negotiable": "Negotiable,Non-Negotiable",
"negotiatedRate": 20,
"negotiatedRateCardEntryId": "1ELxx0000004C9JGAU,1ELxx0000004C9KGAU",
"quantity": 15,
"rate": 5,
"rateAdjustments": [
{
"fields": {
"MyCustomString__c": {
1961
Response BodiesUsage Management

===== PAGE 1976 =====

"displayValue": "My Custom String",
"value": "MyCustomString"
}
},
"lowerBound": 0,
"name": "Tier 1",
"negotiatedRateAdjustmentId": "1ENxx0000004C9BGAU",
"rateAdjustmentId": "1ENxx0000004C9BGAU",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 10,
"tierUnitOfMeasure": "USD",
"upperBound": 50
}
],
"rateCardEntryId": "1CJxx0000004C9IGAU,1CJxx0000004C9JGAU",
"rateUnitOfMeasureName": "USD",
"unitOfMeasure": "GB",
"usageResourceGrantAndPolicyDetail": {
"grantDetail": {
"grantType": "Grant",
"id": "1BXxx0000004C9lGAE",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedGrantDetail": {
"grantType": "Grant",
"id": "1X6xx00000000OECAY",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedResourcePolicyDetail": {
"id": "1X5xx00000000OECAY",
"ratingFrequencyPolicy": {
"id": null,
1962
Response BodiesUsage Management

===== PAGE 1977 =====

"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
},
"resourcePolicyDetail": {
"id": "7Suxx0000004C9kCAE",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
}
},
"usageResourceId": "1BRxx0000004C9CGAU"
}
]
}
This sample response shows values for the type and target type of a binding instance if the BindingInstanceTargetId
value is available in the QuoteLineItem, OrderItem, and AssetStatePeriod objects. Additionally, the rate, negotiated rates, and rate
card entry values show the associated details of the binding object.
{
"records": [
{
"bindingInstanceTargetType": "Account",
"bindingInstanceType": "Target",
"chargeForOverages": "Yes",
"fields": {},
"isOptional": false,
"name": "Data Transfers",
"negotiable": "Non-Negotiable,Non-Negotiable",
"negotiatedRate": null,
1963
Response BodiesUsage Management

===== PAGE 1978 =====

"negotiatedRateCardEntryId": "1QNxx0000004CQmGAM,1QNxx0000004CLwGAM",
"quantity": 250,
"rate": 0.098765,
"rateAdjustments": [
{
"fields": {},
"lowerBound": 0,
"name": null,
"negotiatedRateAdjustmentId": null,
"rateAdjustmentId": "1Soxx0000004CAeCAM",
"rateAdjustmentType": "Percentage",
"rateAdjustmentValue": 0,
"tierUnitOfMeasure": "USD",
"upperBound": 121
}
],
"rateCardEntryId": "1CJxx0000004C9CGAU,1CJxx0000004C9GGAU",
"rateUnitOfMeasureName": "USD",
"unitOfMeasure": "GB",
"usageResourceGrantAndPolicyDetail": {
"grantDetail": {
"grantType": "Grant",
"id": "1BXxx0000004C9lGAE",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedGrantDetail": {
"grantType": "Grant",
"id": "1X6xx00000000OECAY",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedResourcePolicyDetail": {
"id": "1X5xx00000000OECAY",
1964
Response BodiesUsage Management

===== PAGE 1979 =====

"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
},
"resourcePolicyDetail": {
"id": "7Suxx0000004C9kCAE",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
}
},
"usageResourceId": "1BRxx0000004C9CGAU"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of errors encountered during the
processing of the API request.
Usage Detail Error
Response[]
errors
63.0Small, 63.0List of rate card entry records.Rate Card Entry[]records
Usage Details Error Response
Output representation of the details of an error related to usage details.
1965
Response BodiesUsage Management

===== PAGE 1980 =====

JSON Example
{
"errors": [
{
"referenceId": "MyOrderItem",
"errorCode": "INVALID_API_INPUT",
"message": "Something has failed"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Code associated with the error.StringerrorCode
63.0Small, 63.0Message associated with the error.Stringmessage
63.0Small, 63.0Unique ID that’s associated with the specific
error for tracking and reference purposes.
StringreferenceId
Usage Product Validation
Output representation of all the performed validations.
JSON example
This example shows the validation output with errors and warnings.
{
"errors": [
{
"errorCode": "VALIDATION_FAILED",
"message": "Product validation completed with cross-entity errors",
"products": [
{
"productId": "01txx0000006i2gAAA",
"validationResult": {
"validationErrors": [
{
"errors": [
{
"errorCode": "EFFECTIVITY_MISMATCH",
"errorMessages": [
{
"errorMessage": "PUR and RCE effective date ranges must have
overlap for proper rating functionality",
"errorDetails": [
{
"relatedObjectAPIName": "ProductUsageRule",
"records": [
{
"id": "a0bxx0000004CqZAAU",
"name": "PUR-001"
1966
Response BodiesUsage Management

===== PAGE 1981 =====

}
]
}
]
}
]
}
],
"ruleName": "Usage vs Rating Effectivity"
}
],
"validationWarnings": []
}
}
]
}
],
"success": false
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Indicates whether the product validation
passed (true) or failed (false).
Booleansuccess
66.0Big, 66.0List of top-level error details when validation
fails.
Error Details[]errors
Usage Resource Grant And Policy Detail
Output representation of the details of a usage resource grant and policy.
JSON Example
{
"usageResourceGrantAndPolicyDetail": {
"grantDetail": {
"grantType": "Grant",
"id": "1BXxx0000004C9lGAE",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedGrantDetail": {
1967
Response BodiesUsage Management

===== PAGE 1982 =====

"grantType": "Grant",
"id": "1X6xx00000000OECAY",
"quantity": 100,
"usageGrantNegotiable": "Negotiable",
"usageRefreshPolicy": {
"id": "1BYxx0000004C92GAE",
"negotiable": "Non-Negotiable"
},
"usageRolloverPolicy": {
"id": "1BVxx0000004C93GAE",
"negotiable": "Non-Negotiable"
},
"validityPeriodTerm": 1,
"validityPeriodUnit": "Month"
},
"negotiatedResourcePolicyDetail": {
"id": "1X5xx00000000OECAY",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
},
"resourcePolicyDetail": {
"id": "7Suxx0000004C9kCAE",
"ratingFrequencyPolicy": {
"id": null,
"negotiable": null
},
"usageAggregationPolicy": {
"id": null,
"negotiable": null
},
"usageCommitmentPolicy": {
"id": "7Pexx0000004C92CAE",
"negotiable": "Non-Negotiable"
},
"usageOveragePolicy": {
"id": null,
"negotiable": null
}
}
1968
Response BodiesUsage Management

===== PAGE 1983 =====

}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Big, 65.0Details about the grants from the
ProductUsageGrant object.
Grant DetailgrantDetail
65.0Big, 65.0Details about the negotiated grants from
the LineItemUsageResourceGrant or
TransactionUsageEntitlement object.
Grant Detailnegotiated
GrantDetail
65.0Big, 65.0Details about the policy from the
LineItemUsageResourcePolicy or
BindingObjectUsageResourcePolicy object.
Resource Policy
Detail
negotiated
Resource
PolicyDetail
65.0Big, 65.0Details about the policy from the
ProductUsageResourcePolicy object.
Resource Policy
Detail
resourcePolicy
Detail
Validation Error
Output representation of the validation errors grouped by rule name.
JSON example
This example shows a validation error grouped by rule name.
{
"validationErrors": [
{
"ruleName": "Usage vs Rating Effectivity",
"errors": [
{
"errorCode": "EFFECTIVITY_MISMATCH",
"errorMessages": []
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Name of the validation rule. For example,
Usage vs Rating Effectivity.
StringruleName
66.0Big, 66.0List of error code groups for this validation.Errors[]errors
Validation Result
Output representation of the validation results grouped by rule name.
1969
Response BodiesUsage Management

===== PAGE 1984 =====

JSON example
This example shows a validation result with errors and warnings.
{
"validationResult": {
"validationErrors": [
{
"ruleName": "Usage vs Rating Effectivity",
"errors": []
}
],
"validationWarnings": [
{
"ruleName": "Performance Optimization",
"warnings": []
}
]
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0List of validation errors grouped by rule
name.
Validation Error[]validationErrors
66.0Big, 66.0List of validation warnings grouped by rule
name.
Validation Warning[]validationWarnings
Validation Warning
Output representation of the validation warnings grouped by rule name.
JSON example
This example shows a validation warning grouped by rule name.
{
"validationWarnings": [
{
"ruleName": "Performance Optimization",
"warnings": [
{
"warningCode": "PERFORMANCE_SUBOPTIMAL",
"warningMessages": []
}
]
}
]
}
1970
Response BodiesUsage Management

===== PAGE 1985 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Name of the validation rule. For example,
Performance Optimization.
StringruleName
66.0Big, 66.0List of warning code groups for this
validation.
Warnings[]warnings
Warnings
Output representation of a group of warning messages with the same warning code.
JSON example
This example shows a group of warning messages with the same warning code.
{
"warnings": [
{
"warningCode": "PERFORMANCE_SUBOPTIMAL",
"warningMessages": [
{
"warningMessage": "PUR and RCE date ranges could be optimized for better
performance",
"warningDetails": []
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Standardized warning code. For example,
PERFORMANCE_SUBOPTIMAL.
StringwarningCode
66.0Big, 66.0List of warning messages for records that
triggered with this warning.
Warning Message[]warningMessages
Warning Message
Output representation of the details of records that triggered this specific warning.
JSON example
This example shows a warning message with details.
{
"warningMessages": [
{
"warningMessage": "PUR and RCE date ranges could be optimized for better
performance",
"warningDetails": [
1971
Response BodiesUsage Management

===== PAGE 1986 =====

{
"relatedObjectAPIName": "ProductUsageRule",
"records": [
{
"id": "a0bxx0000004CqZAAU",
"name": "PUR-001"
}
]
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Human-readable warning message that
describes the validation concern.
StringwarningMessage
66.0Big, 66.0Details of records that triggered this specific
warning.
Error Warning
Details[]
warningDetails
Usage Management Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
Flow for Usage Management
Represents the metadata associated with a flow. With Flow, you can create an application that navigates users through a series of
screens to query and update records in the database. You can also execute logic and provide branching capability based on user
input to build dynamic applications.
IndustriesUsageSettings
Represents the settings for Usage Management.
SEE ALSO:
Metadata API Developer Guide: Understanding Metadata API
Flow for Usage Management
Represents the metadata associated with a flow. With Flow, you can create an application that navigates users through a series of screens
to query and update records in the database. You can also execute logic and provide branching capability based on user input to build
dynamic applications.
FlowActionCall
Usage Management exposes additional actionType values for the FlowActionCall Metadata type.
1972
Usage Management Metadata API TypesUsage Management

===== PAGE 1987 =====

DescriptionField TypeField Name
Required.InvocableActionType
(enumeration of
type string)
actionType
The action type. Additional valid values only for Usage Management
include:
• invokeSummaryCreationService— Invoke the service
that creates various summaries, such as usage, ratable, and liable
summaries where the usage amount is zero. The service also checks
and updates the billing period of the usage entitlement account if
the billing period is expired.
• processConsumptionOverages— Process consumption
overages for the usage summary records with
SummaryComplete  status. This action uses the entitlement
service to process the overages.
• refreshUsageEntitlementBucket— Refresh entitlements
by evaluating the usage entitlement bucket records and creating a
new usage entitlement entry.
• retriggerEntlCreaProc— Retrigger entitlement creation
process for failed or unprocessed assets.
IndustriesUsageSettings
Represents the settings for Usage Management.
Parent Type and Manifest Access
This type extends the Metadata metadata type and inherits its fullName field.
In the package manifest, all the settings metadata types for the org are accessed using the “Settings” name. See Settings for more details.
File Suffix and Directory Location
IndustriesUsageSettings  values are stored in the IndustriesUsage.settings  file in the settings  folder. The
.settings  files are different from other named components, because there is only one settings file for each settings component.
Version
IndustriesUsageSettings components are available in API version 63.0 and later.
Fields
DescriptionField Name
Field Type
boolean
enableUsage
1973
IndustriesUsageSettingsUsage Management

===== PAGE 1988 =====

DescriptionField Name
Description
Indicates whether to create and access Usage Management objects to manage product
usage and determine rates based on usage (true) or not (false). The default value
is false.
Declarative Metadata Sample Definition
The following is an example of an IndustriesUsageSettings component.
<?xml version="1.0" encoding="UTF-8"?>
<IndustriesUsageSettings xmlns="http://soap.sforce.com/2006/04/metadata">
<enableUsage>true</enableUsage>
</IndustriesUsageSettings>
The following is an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>IndustriesUsage</members>
<name>Settings</name>
</types>
<version>[ftest]</version>
</Package>
Wildcard Support in the Manifest File
The wildcard character *  (asterisk) in the package.xml manifest file doesn’t apply to metadata types for feature settings. The wildcard
applies only when retrieving all settings, not for an individual setting. For details, see Settings. For information about using the manifest
file, see Deploying and Retrieving Metadata with the Zip File.
1974
IndustriesUsageSettingsUsage Management

===== PAGE 1989 =====

