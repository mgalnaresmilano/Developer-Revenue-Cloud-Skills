---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 8 — Transaction Management

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 8 Transaction Management
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions of Revenue Cloud
where Transaction
Management is enabled
Configure, price, and sell products with Transaction Management
in Revenue Cloud. Transaction Management supports subscription
lifecycles and ensures end-to-end integrity of your quotes and
orders.
SEE ALSO:
Salesforce Help: Permissions for Quote and Order Capture
In this chapter ...
• Transaction
Management
Standard Objects
• Transaction
Management Fields
on Standard Objects
• Transaction
Management Tooling
API Objects
• Transaction
Management
Platform Event
• Transaction
Management
Business APIs
• Transaction
Management Apex
Reference
• Transaction
Management
Standard Invocable
Actions
• Transaction
Management
Metadata API Types
1114

===== PAGE 1129 =====

Transaction Management Standard Objects
The Transaction Management data model provides objects and fields to manage transactions.
Asset
Represents an item of commercial value, such as a product sold by your company or a competitor, that a customer has purchased.
AssetAction
Represents a change made to a lifecycle-managed asset. The fields can’t be edited. This object is available in API version 50.0 and
later.
AssetActionSource
Represents an optional way to record what transactions caused changes to lifecycle-managed assets. Use it to trace financial and
other information about asset actions. This object supports Salesforce order products and work order line items, and transaction IDs
from other systems. The fields can’t be edited. This object is available in API version 50.0 and later.
AssetActionSrcPriceAdjustment
Each row represents a junction between an asset and the calculated price adjustment that's applied to an asset. This object is available
in API version 66.0 and later.
AssetContractRelationship
Represents a relationship between an asset and a contract. This object is available in API version 60.0 and later.
AssetDowntimePeriod
Represents a period during which an asset is not able to perform as expected. Downtime periods include planned activities, such
as maintenance, and unplanned events, such as mechanical breakdown. This object is available in API version 49.0 and later.
AssetOwnerSharingRule
Represents the rules for sharing an Asset with users other than the owner. This object is available in API version 33.0 and later.
AssetRateAdjustment
Stores the tier rate adjustments for the asset rate card entries. This object is available in API version 62.0 and later.
AssetRateCardEntry
Stores the negotiated rate card entries that are associated with an asset in Revenue Cloud. This object is available in API version 62.0
and later.
AssetRelationship
Represents a non-hierarchical relationship between assets due to an asset modification; for example, a replacement, upgrade, or
other circumstance. In Revenue Lifecycle Management, this object represents an asset or assets grouped in a bundle or set. This
object is available in API version 41.0 and later.
AssetShare
Represents a sharing entry on an Asset. This object is available in API version 33.0 and later.
AssetStatePeriod
Represents a time span when an asset has the same quantity, amount, and monthly recurring revenue (MRR). An asset has as many
asset state periods as there are changes to it (asset actions) during its lifecycle. The dashboard and related pages show the current
asset state period. The fields can’t be edited. This object is available in API version 50.0 and later.
AssetStatePeriodAttribute
Represents a virtual object that holds the key-value pair of the asset attribute in a specified asset state period. This object is a child
object of AssetStatePeriod. This object is available in API version 60.0 and later.
1115
Transaction Management Standard ObjectsTransaction Management

===== PAGE 1130 =====

AssetTag
Associates a word or short phrase with an Asset.
AssetTokenEvent
The documentation has moved to AssetTokenEvent in the Platform Events Developer Guide.
AssetWarranty
Defines the warranty terms applicable to an asset along with any exclusions and extensions. This object is available in API version
50.0 and later.
BindingObjUsageRsrcPlcy
Represents the policies that are used for the usage resource that's associated with an asset or a binding object. This object is available
in API version 65.0 and later.
ContractItemPrice
Represents an object that’s used to capture a price for a product on a contract. This object is available in API version 61.0 and later.
ContractItemPriceAdjTier
Represents the tiers of a price adjustment to a product on a contract. This object is available in API version 63.0 and later.
ContractItemPriceHistory
Represents the history of changes to the values in the fields of a ContractItemPrice object. This object is available in API version 61.0
and later.
OrderDeliveryMethod
Shows the customizations and options that a buyer selected for their delivery method. This object is available in API version 48.0
and later.
OrderItemAttribute
Represents a virtual object that stores an attribute specified for an order item.This object is available in API version 60.0 and later.
OrderItemDetail
Represents the breakdown details of an order product. Revenue Cloud generates these records to capture pricing and quantity
changes, such as negative quantity reductions, early renewals, derived pricing or repricing during an amendment, and bundle or
product attribute reconfigurations. This object is available in API version 60.0 and later.
OrderItemRateAdjustment
Represents the negotiated rate adjustment for an order product. This object is available in API version 62.0 and later.
OrderItemRateCardEntry
Represents the catalog and negotiated rates of a usage metric associated with an order item that's used to charge overage
consumption. This object is available in API version 62.0 and later.
OrderItemUsageRsrcGrant
Represents the negotiated grants for the usage resource that's associated with the usage product added in the order item. This
object is available in API version 65.0 and later.
OrderItemUsageRsrcPlcy
Represents the policies that are used for the usage resource that's associated with the usage product added in the order item. This
object is available in API version 65.0 and later.
SalesTransactionType
Represents the type of the sales transaction. This object is available in API version 61.0 and later.
QuoteAction
Indicates the type of sales transaction that’s being quoted; for example, a renewal sale. This object is available in API version 59.0
and later.
1116
Transaction Management Standard ObjectsTransaction Management

===== PAGE 1131 =====

QuoteLineDetail
Represents the breakdown details of a quote line item. Revenue Cloud generates these records to capture pricing and quantity
changes, such as negative quantity reductions, early renewals, derived pricing or repricing during an amendment, and bundle or
product attribute reconfigurations. This object is available in API version 60.0 and later.
QuoteLineGroup
Stores the group information for line items in a quote. It also stores the aggregated line field information (subtotal). It contains a
parent-child relationship to quote. This object is available in API version 61.0 and later.
QuoteLineItemAttribute
Represents a virtual object that stores an attribute specified for a quote line item. This object is available in API version 59.0 and later.
QuotLineItmUseRsrcGrant
Represents the negotiated grants for the usage resource that's associated with the usage product added in the quote line item. This
object is available in API version 65.0 and later.
QuotLineItmUsageRsrcPlcy
Represents the policies that are used for the usage resource that's associated with the usage product added in the quote line item.
This object is available in API version 65.0 and later.
QuoteLineRateAdjustment
Represents the negotiated rate adjustment for a quote line item. This object is available in API version 62.0 and later.
QuoteLineRateCardEntry
Represents the catalog and negotiated rates of a usage resource associated with a quote line item that's used to charge overage
consumption. This object is available in API version 62.0 and later.
SEE ALSO:
Object Reference for the Salesforce Platform: Overview of Salesforce Objects and Fields
SOAP API Developer Guide: Introduction to SOAP API
Asset
Represents an item of commercial value, such as a product sold by your company or a competitor, that a customer has purchased.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
AccountId
Properties
Create, Filter, Group, Nillable, Sort, Update
1117
AssetTransaction Management

===== PAGE 1132 =====

DetailsField
Description
(Required) ID of the Account associated with this asset. Must be a valid account ID. Required
if ContactId  isn’t specified.
This field is a relationship field.
Relationship Name
Account
Relationship Type
Lookup
Refers To
Account
Type
address
Address
Properties
Filter, Nillable
Description
Represents the physical address or geolocation of the asset.
Type
int
AssetLevel
Properties
Filter, Group, Nillable, Sort
Description
The asset’s position in an asset hierarchy. If the asset has no parent or child assets, its level
is 1. Assets that belong to a hierarchy have a level of 1 for the root asset, 2 for the child assets
of the root asset, 3 for their children, and so forth. On assets created before the introduction
of this field, the asset level defaults to –1. After the asset record is updated, the asset level is
calculated and automatically updated.
Type
reference
AssetProvidedById
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The account that provided the asset, typically a manufacturer.
This field is a relationship field.
Relationship Name
AssetProvidedBy
Relationship Type
Lookup
1118
AssetTransaction Management

===== PAGE 1133 =====

DetailsField
Refers To
Account
Type
reference
AssetServicedById
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The account in charge of servicing the asset.
This field is a relationship field.
Relationship Name
AssetServicedBy
Relationship Type
Lookup
Refers To
Account
Type
reference
AssetTypeId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The asset type associated with the asset.
This field is a relationship field.
This field is available in API version 62.0 and later for users with the Health Cloud Appointment
Management permission set.
Relationship Name
AssetType
Relationship Type
Lookup
Refers To
AssetType
Type
percent
Availability
Properties
Filter, Nillable, Sort
Description
The percentage of expected uptime where the asset was available for use.
1119
AssetTransaction Management

===== PAGE 1134 =====

DetailsField
Type
double
AveragetimetoRepair
Properties
Create, Filter, Nillable, Sort, Update
Description
Represents the number of hours it typically takes to repair an asset after a failure.
Type
double
AveragetimeBetweenFailure
Properties
Create, Filter, Nillable, Sort, Update
Description
Represents the number of hours that typically elapses before the asset is likely to fail again.
Type
double
AverageUptimePerDay
Properties
Create, Filter, Nillable, Sort, Update
Description
The average number of hours per day the asset is expected to be available for use.
Type
string
City
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The city detail for the address.
Type
picklist
ConsequenceOfFailure
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The business impact associated with the asset’s failure. Using this field, you can address the
asset’s health and take action using Flows. To enable this field, use Object Manager to update
the field availability. Make sure that the field is visible for field-level security and for page
layout. To learn more, see What Determines Field Access. The picklist values aren’t predefined
in orgs created before Winter ’22 that aren’t Field Service enabled. This field is available in
API version 53.0 and later.
Possible values are:
• Insignificant
1120
AssetTransaction Management

===== PAGE 1135 =====

DetailsField
• Minor
• Moderate
• Major
• Critical
Type
reference
ContactId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Required if AccountId  isn’t specified. ID of the Contact associated with this asset. Must
be a valid contact ID that has an account parent (but doesn’t need to match the asset’s
AccountId).
This field is a relationship field.
Relationship Name
Contact
Relationship Type
Lookup
Refers To
Contact
Type
String
Country
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The country detail for the address.
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Three-letter ISO 4217 currency code associated with the invoice. The default value is USD.
This field is available in API version 55.0 and later. This field is available when CPQ Plus,
Salesforce Billing, or Revenue Cloud is enabled.
Type
currency
CurrentAmount
Properties
Filter, Nillable, Sort
1121
AssetTransaction Management

===== PAGE 1136 =====

DetailsField
Description
Reserved for future use.
This field is available in API version 50.0 and later. This field is available when CPQ Plus,
Salesforce Billing, or Revenue Cloud is enabled.
Type
dateTime
CurrentLifecycleEndDate
Properties
Filter, Nillable, Sort
Description
Represents the end of the period shown as current. System-populated field inherited from
the end date of the current asset state period. If that field is empty, as with an evergreen
subscription, the Current Lifecycle End Date field is also empty.
This field is available in API version 50.0 and later. This field is available when CPQ Plus,
Salesforce Billing, or Revenue Cloud is enabled.
Type
currency
CurrentMrr
Properties
Filter, Nillable, Sort
Description
The asset’s monthly recurring revenue during the current asset state period. System-populated
field inherited from the monthly recurring revenue on the current asset state period. If no
asset state period is current, the value is 0. Label is Current Monthly Recurring Revenue.
This field is available in API version 50.0 and later. This field is available when CPQ Plus,
Salesforce Billing, or Revenue Cloud is enabled.
Type
double
CurrentQuantity
Properties
Filter, Nillable, Sort
Description
The asset’s quantity during the current asset state period. System-populated field inherited
from the quantity on the current asset state period. If no asset state period is current, the
value is 0.
This field is available in API version 50.0 and later. This field is available when CPQ Plus,
Salesforce Billing, or Revenue Cloud is enabled.
Type
textarea
Description
Properties
Create, Nillable, Update
1122
AssetTransaction Management

===== PAGE 1137 =====

DetailsField
Description
Description of the asset.
Type
picklist
DigitalAssetStatus
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Status of digital tracking of the asset. The default picklist includes the following values:
• On
• Off
• Warning
• Error
Type
string
ExternalIdentifier
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the matching record in an external system. This field is available in API version 49.0
and later.
Type
picklist
GeocodeAccuracy
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Accuracy level of the geocode for the address.
Type
boolean
HasLifecycleManagement
Properties
Defaulted on create, Filter, Group, Sort
Description
True if this asset is a lifecycle-managed asset, otherwise false. You can’t switch an asset to a
lifecycle-managed asset or the reverse. This field is system populated.
The default value is false.
This field is available in API version 50.0 and later. This field is available when CPQ Plus,
Salesforce Billing, or Revenue Cloud is enabled.
1123
AssetTransaction Management

===== PAGE 1138 =====

DetailsField
Type
date
InstallDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Date when the asset was installed.
Type
boolean
IsCompetitorProduct
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this Asset represents a product sold by a competitor (true) or not
(false). The default value is false. Its UI label is Competitor Asset.
Type
boolean
IsInternal
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates that the asset is produced or used internally (true) or not (false). The default
value is false. Its UI label is Internal Asset.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date and time that the asset was last modified. Its UI label is Last Modified Date.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date and time that the asset was last viewed.
Type
double
Latitude
Properties
Create, Filter, Group, Nillable, Sort, Update
1124
AssetTransaction Management

===== PAGE 1139 =====

DetailsField
Description
Used with Longitude to specify the precise geolocation of the address.
Type
dateTime
LifecycleEndDate
Properties
Filter, Nillable, Sort
Description
Represents the end of the asset’s lifecycle. System-populated field inherited from the end
date of the final asset state period. If that field is empty, as with an evergreen subscription,
the lifecycle has no end date. This field is available in API version 50.0 and later. This field is
available when CPQ Plus, Salesforce Billing, or Revenue Cloud is enabled.
Type
dateTime
LifecycleStartDate
Properties
Filter, Nillable, Sort
Description
Represents the beginning of the asset’s lifecycle. System-populated field inherited from the
start date of the earliest asset state period. This field can’t be edited. When a new asset action
affects the start date of an asset state period, the period is deleted and a new one is generated.
This field is available in API version 50.0 and later. This field is available when CPQ Plus,
Salesforce Billing, or Revenue Cloud is enabled.
Type
reference
LocationId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The asset’s location. Typically, this location is the place where the asset is stored, such as a
warehouse or van.
If you have access to the location entity, it doesn’t necessarily mean you can access the
location id field. To access the location, you must have userHasLocation  user access.
Type
double
Longitude
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Used with Latitude to specify the precise geolocation of the address.
Type
date
ManufactureDate
1125
AssetTransaction Management

===== PAGE 1140 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date when the asset was manufactured. This field is available from API version 49.0 and
later.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
(Required) Name of the asset. Label is Asset Name.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The asset’s owner. By default, the asset owner is the user who created the asset record. Its
UI label is Asset Owner.
This field is a relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
User
Type
reference
ParentId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The asset’s parent asset. Its UI label is Parent Asset.
This field is a relationship field.
Relationship Name
Parent
Relationship Type
Lookup
Refers To
Asset
1126
AssetTransaction Management

===== PAGE 1141 =====

DetailsField
Type
string
PostalCode
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The postal code for the address.
Type
currency
Price
Properties
Create, Filter, Nillable, Sort, Update
Description
Price paid for this asset.
Type
picklist
PricingSource
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Pricing source to use when amending or renewing an asset.
Valid values are:
• LastTransaction—Last Transaction
• PriceBookListPrice—Price Book or List Price
Available in API version 60.0 and later.
Type
reference
Product2Id
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
(Optional) ID of the Product2 associated with this asset. Must be a valid Product2 ID. Its UI
label is Product.
This field is a relationship field.
Relationship Name
Product2
Relationship Type
Lookup
Refers To
Product2
1127
AssetTransaction Management

===== PAGE 1142 =====

DetailsField
Type
string
ProductCode
Properties
Filter, Group, Nillable, Sort
Description
The product code of the related product.
Type
string
ProductDescription
Properties
Filter, Sort, Nillable
Description
The product description of the related product.
Type
picklist
ProductFamily
Properties
Filter, Group, Sort, Nillable
Description
The product family of the related product.
Type
date
PurchaseDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Date on which this asset was purchased.
Type
double
Quantity
Properties
Create, Filter, Nillable, Sort, Update
Description
Quantity purchased or installed. The Quantity field value isn’t set by Customer Asset Lifecycle
Management. Instead, you can populate the field as you need.
Type
picklist
QuantityIncreasePricingType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
1128
AssetTransaction Management

===== PAGE 1143 =====

DetailsField
Description
Specify which pricing type to use when the quantity of this asset is increased. Its UI label is
Pricing Type for Quantity Increase. This field is available in API version 56.0 and later. This
field is available when Revenue Cloud is enabled.
Possible values are:
• LastNegotiatedPrice—Available in API version 58.0 and later.
• ListPrice
Type
reference
RecordTypeId
Properties
Create, Filter, Group, Sort, Update
Description
The unique identifier for the asset.
This field is a relationship field.
Relationship Name
RecordType
Relationship Type
Lookup
Refers To
RecordType
Type
percent
Reliability
Properties
Filter, Nillable, Sort
Description
The percentage of expected uptime where the asset wasn’t subject to unplanned downtime.
Type
picklist
RenewalPricingType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The price used when renewing a subscription. Its UI label is Pricing Type for Renewal. This
field is available in API version 55.0 and later. This field is available when Revenue Cloud is
enabled.
Possible values are:
• LastNegotiatedPrice
• ListPrice
1129
AssetTransaction Management

===== PAGE 1144 =====

DetailsField
Type
double
RenewalTerm
Properties
Create, Filter, Nillable, Sort, Update
Description
With Renewal Term Unit, defines the default subscription term for renewal quotes. This field
is available in API version 55.0 and later. This field is available when Revenue Cloud is enabled.
Type
picklist
RenewalTermUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The unit of time for a subscription term. This field is available in API version 55.0 and later.
This field is available when Revenue Cloud is enabled.
Possible values are:
• Annual—Available in API version 58.0 and later. —UI label is Years.
• Months
Type
reference
RootAssetId
Properties
Filter, Group, Nillable, Sort
Description
(Read only) The top-level asset in an asset hierarchy. Depending on where an asset lies in
the hierarchy, its root could be the same as its parent. Its UI label is Root Asset.
This field is a relationship field.
Relationship Name
RootAsset
Relationship Type
Lookup
Refers To
Asset
Type
reference
SalesStoreId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
ID of the RetailStore or WebStore associated with this Asset.
This field is a polymorphic relationship field.
1130
AssetTransaction Management

===== PAGE 1145 =====

DetailsField
To access this field, your org must have a Salesforce Order Management license or a B2B
Commerce License.
This field is available in API v60.0 and later.
Relationship Name
SalesStore
Relationship Type
Lookup
Refers To
RetailStore, WebStore
Type
string
SerialNumber
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Serial number for this asset.
Type
string
State
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The state detail for the address.
Type
picklist
Status
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Customizable picklist of values. The default picklist includes the following values:
• Purchased
• Shipped
• Installed
• Registered
• Obsolete
Type
picklist
StatusReason
Properties
Create, Filter, Group, Nillable, Sort, Update
1131
AssetTransaction Management

===== PAGE 1146 =====

DetailsField
Description
The explanation of the device status. This field is available from API version 49.0 and later.
Possible values are:
• Not Ready
• Off
• Offline
• Online
• Paused
• Standby
Type
string
StockKeepingUnit
Properties
Filter, Group, Nillable, Sort
Description
The SKU assigned to the related product.
Type
textarea
Street
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The street detail for the address.
Type
double
SumDowntime
Properties
Filter, Nillable, Sort
Description
Accumulated downtime (planned and unplanned), determined as follows:
• When only UptimeRecordStart is set, the sum of all downtime from
UptimeRecordStart
• When UptimeRecordStart  and UptimeRecordEnd  are set, the sum of all
downtime from UptimeRecordStart  to UptimeRecordEnd
Otherwise, downtime isn’t accumulated.
Type
double
SumUnplannedDowntime
Properties
Filter, Nillable, Sort
1132
AssetTransaction Management

===== PAGE 1147 =====

DetailsField
Description
Accumulated unplanned downtime, determined as follows:
• When only UptimeRecordStart is set, the sum of all unplanned downtime from
UptimeRecordStart
• When UptimeRecordStart  and UptimeRecordEnd  are set, the sum of all
unplanned downtime from UptimeRecordStart  to UptimeRecordEnd
Otherwise, unplanned downtime isn’t accumulated.
Type
currency
TotalLifecycleAmount
Properties
Filter, Nillable, Sort
Description
The total amount of revenue for the asset, including revenue from each stage in the asset
lifecycle. This field is available when CPQ Plus, Salesforce Billing, or Revenue Cloud is enabled.
Type
dateTime
UptimeRecordEnd
Properties
Create, Filter, Nillable, Sort, Update
Description
The date until which SumDowntime and SumUnplannedDowntime are accumulated.
Type
dateTime
UptimeRecordStart
Properties
Create, Filter, Nillable, Sort, Update
Description
The date from which SumDowntime and SumUnplannedDowntime are accumulated.
Type
date
UsageEndDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Date when usage for this asset ends or expires.
Type
string
Uuid
Properties
Create, Filter, Group, Nillable, Sort, Update
1133
AssetTransaction Management

===== PAGE 1148 =====

DetailsField
Description
The unique ID for the asset. This field is available in API version 49.0 and later.
Usage
Use this object to track products sold to customers. With asset tracking, a client application can quickly determine which products were
previously sold or are currently installed at a specific account. You can also create hierarchies of up to 10,000 assets.
For example, suppose that your company wants to renew and upsell opportunities on products sold in the past. Similarly, your company
can track competitive products in a customer environment where products can be replaced or swapped out.
Asset tracking is also useful for product support, providing detailed information to assist with product-specific support issues. For example,
the PurchaseDate  or SerialNumber  can indicate whether a given product has certain maintenance requirements, including
product recalls. Similarly, the UsageEndDate  can indicate when the asset was removed from service or when a license or warranty
expires.
If an application creates an Asset record, it must specify a Name  and either an AccountId, ContactId, or both.
With REST API, use the getRelatedListInfo function to get information about related lists on the asset. Note that when requesting
information about PrimaryAssets, the response is labeled Related Assets, and the response for RelatedAssets  is
labeled Primary Assets.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, those objects are available in the same API versions as
this object. Otherwise, they’re available in the specified API version and later.
AssetChangeEvent (API version 44.0)
Change events are available for the object.
AssetFeed
Feed tracking is available for the object.
AssetHistory
History is available for tracked fields of the object.
AssetOwnerSharingRule
Sharing rules are available for the object.
AssetShare
Sharing is available for the object.
AssetAction
Represents a change made to a lifecycle-managed asset. The fields can’t be edited. This object is available in API version 50.0 and later.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(), search()
1134
AssetActionTransaction Management

===== PAGE 1149 =====

Special Access Rules
To use Customer Asset Lifecycle Management APIs, you must have the Access Customer Asset Lifecycle Management APIs permission
and Read access to the Asset, Asset Action, Asset Action Source, and Asset State Period objects.
Fields
DetailsField
Type
dateTime
ActionDate
Properties
Filter, Sort
Description
The date when an asset action change is recorded. This date can differ from the start date
of the related asset state period. For example, suppose that a customer cancels a subscription
in June, and the subscription expires in October. The date the customer cancels the
subscription (June) is the action date of the asset action. The cancellation's effective date
(October) is the start date of the asset state period.
Type
currency
ActualTaxChange
Properties
Filter, Nillable, Sort
Description
The rollup of actual tax from all asset action sources. This field is populated by the system.
Label is Change in Actual Tax.
This field is a calculated field.
Type
currency
AdjustmentAmountChange
Properties
Filter, Nillable, Sort
Description
The rollup of adjustment amount from all asset action sources. This field is populated by the
system. Label is Change in Adjustment Amount.
This field is a calculated field.
Type
currency
Amount
Properties
Filter, Sort
Description
The delta in the total asset amount resulting from an asset action.
1135
AssetActionTransaction Management

===== PAGE 1150 =====

DetailsField
Type
string
AssetActionNumber
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The ID of the asset action. Label is Name.
Type
reference
AssetId
Properties
Filter, Group, Sort
Description
The ID of the related lifecycle-managed asset. Label is Asset.
This field is a relationship field.
Relationship Name
Asset
Relationship Type
Lookup
Refers To
Asset
Type
boolean
CanRollBack
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the last asset action can be rolled back (true). If this property is set to
false, the asset and the last asset action can’t be rolled back.
The default value is false. This field is available in API version 65.0 and later.
Type
picklist
CategoryEnum
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The business category of the asset action, for use in reporting. Asset action totals are broken
out by the picklist values on this required field, and those totals are in turn reflected on assets.
These categories are available and aren’t customizable. Label is Business Category.
Possible values are:
• Cancellations
• Cross-Sells
1136
AssetActionTransaction Management

===== PAGE 1151 =====

DetailsField
• Downgrades  Indicates a transition to a lower-level version or tier of an asset.
• Downsells  Indicates a negative quantity amendment or a decreased Line Item total
price with no change in quantity.
• Initial Sale  Indicates that the asset is initially purchased by an account.
• Other
• Renewals
• Swaps  Indicates the exchange of one asset for another. Applies to both swapped-out
and swapped-in actions.
• Terms And Conditions Changes
• Transfers  Indicates that an asset is transferred from one account to another.
• Upgrades  Indicates a transition to a higher-level version or tier of an asset.
• Upsells  Indicates a positive quantity amendment or an increased Line Item total
price with no change in quantity.
Type
currency
EstimatedTaxChange
Properties
Filter, Nillable, Sort
Description
The rollup of estimated tax from all asset action sources. This field is populated by the system.
Label is Change in Estimated Tax.
This field is a calculated field.
Type
currency
MrrChange
Properties
Filter, Sort
Description
The delta in the asset’s monthly recurring revenue resulting from an asset action. For example,
suppose that the MRR during an asset state period is $200 and the next asset action adds
$100. Then this field’s value is $100. Label is Change in Monthly Recurring Revenue.
Type
currency
ProductAmountChange
Properties
Filter, Nillable, Sort
Description
The rollup of product amount from all asset action sources. This field is populated by the
system. Label is Change in Product Amount.
This field is a calculated field.
1137
AssetActionTransaction Management

===== PAGE 1152 =====

DetailsField
Type
double
QuantityChange
Properties
Filter, Sort
Description
The delta in the asset quantity resulting from an asset action. For example, suppose that the
asset quantity during an asset state period is 20 and the next asset action adds 10. Then this
field’s value is 10. Label is Change in Quantity.
Type
reference
RolledbackAssetAction
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The last asset action rolled back in the current rollback transaction. This field is available in
API version 65.0 and later.
Type
currency
SubtotalChange
Properties
Filter, Nillable, Sort
Description
The rollup of subtotal from all asset action sources. This field is populated by the system.
Label is Change in Subtotal.
This field is a calculated field.
Type
picklist
Subtype
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The subtype of the action on the asset.
Valid values are:
• DowngradeFrom—Available in API version 66.0 and later.
• DowngradeTo—Available in API version 66.0 and later.
• FieldAmendment
• Rollback
• StartDateAdjustment
• SwapIn—Available in API version 66.0 and later.
• SwapOut—Available in API version 66.0 and later.
• TransferFrom
1138
AssetActionTransaction Management

===== PAGE 1153 =====

DetailsField
• TransferTo
• UpgradeFrom—Available in API version 66.0 and later.
• UpgradeTo—Available in API version 66.0 and later.
This field is available in API version 65.0 and later.
Type
currency
TotalAmount
Properties
Filter, Nillable, Sort
Description
The sum of the current and previous asset action amount. This field is populated by the
system.
This field is a calculated field.
Type
currency
TotalCancellationsAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Cancellations.
This field is populated by the system.
Type
currency
TotalCrossSellsAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Cross-Sells. This
field is populated by the system.
Type
currency
TotalDowngradesAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Downgrades. This
field is populated by the system and is available in API version 66.0 and later.
Type
currency
TotalDownsellsAmount
Properties
Filter, Nillable, Sort
1139
AssetActionTransaction Management

===== PAGE 1154 =====

DetailsField
Description
The sum of current and previous asset action amounts categorized as Downsells. This
field is populated by the system.
Type
currency
TotalInitialSaleAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Initial Sale.
This field is populated by the system.
Type
currency
TotalMrr
Properties
Filter, Nillable, Sort
Description
The sum of the monthly recurring revenue for the current and previous asset action. This
field is populated by the system. Label is Total Monthly Recurring Revenue.
Type
currency
TotalOtherAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Other. This field is
populated by the system.
Type
double
TotalQuantity
Properties
Filter, Nillable, Sort
Description
The sum of the changes in quantity for the current and previous asset action. This field is
populated by the system.
Type
currency
TotalRenewalsAmount
Properties
Filter, Nillable, Sort
1140
AssetActionTransaction Management

===== PAGE 1155 =====

DetailsField
Description
The sum of current and previous asset action amounts categorized as Renewals. This field
is populated by the system.
Type
currency
TotalSwapsAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Swaps. This field is
populated by the system and is available in API version 66.0 and later.
Type
currency
TotalTermsAndConditionsAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Terms and
Conditions Changes. This field is populated by the system. Label is Total Terms
and Conditions Changes Amount.
Type
currency
TotalTransfersAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Transfers. This
field is populated by the system.
Type
currency
TotalUpgradesAmount
Properties
Filter, Nillable, Sort
Description
The sum of current and previous asset action amounts categorized as Upgrades. This field
is populated by the system and is available in API version 66.0 and later.
Type
currency
TotalUpsellsAmount
Properties
Filter, Nillable, Sort
1141
AssetActionTransaction Management

===== PAGE 1156 =====

DetailsField
Description
The sum of current and previous asset action amounts categorized as Upsells. This field
is populated by the system.
Type
picklist
Type
Properties
Filter, Group, Restricted picklist, Sort
Description
The REST API used to generate the asset action. This field is populated by the system.
Valid values are:
• Cancel
• Change
• Convert
• Generate
AssetActionSource
Represents an optional way to record what transactions caused changes to lifecycle-managed assets. Use it to trace financial and other
information about asset actions. This object supports Salesforce order products and work order line items, and transaction IDs from other
systems. The fields can’t be edited. This object is available in API version 50.0 and later.
Supported Calls
createable(), deletable(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(),
query(), retrieve(), search(), undeletable(), updateable().
Special Access Rules
To use Customer Asset Lifecycle Management APIs, you must have the Access Customer Asset Lifecycle Management APIs permission
and Read access to the Asset, Asset Action, Asset Action Source, and Asset State Period objects.
Fields
DetailsField
Type
currency
ActualTax
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The region-specific tax amount determined at time of the order.
1142
AssetActionSourceTransaction Management

===== PAGE 1157 =====

DetailsField
This field is not used for price and tax calculations.
Type
currency
AdjustmentAmount
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
An adjustment to the product amount, such as a discount.
Type
reference
AssetActionId
Properties
Createable, Filter, Group, Sort
Description
The related asset action, that is, the change caused by an asset action source transaction.
This field is a relationship field.
Relationship Name
AssetAction
Relationship Type
Lookup
Refers To
AssetAction
Type
string
AssetActionSourceNumber
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The ID of the asset action source. Label is Name.
Type
string
BillingReference
Properties
Filter, Group, Nillable, Sort
Description
The ID of the OrderItem or OrderItemDetail record that this AssetActionSource record is
created for.
Type
percent
Discount
1143
AssetActionSourceTransaction Management

===== PAGE 1158 =====

DetailsField
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
The discount, expressed as a percentage, that's applied to the asset.
This field is available in API version 62.0 and later.
Type
currency
DiscountAmount
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The discount, expressed as currency, that's applied to the asset.
This field is available in API version 62.0 and later.
Type
dateTime
EffectiveGrantDate
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The date when the resources associated with the asset were granted.
This field is available in orgs that have Revenue Cloud when Rate Management is enabled.
This field is available in API version 62.0 and later.
Type
dateTime
EndDate
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The end date of the service or change.
Type
currency
EstimatedTax
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The estimate of the region-specific tax amount made at time of the transaction.
Type
string
ExternalReference
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
1144
AssetActionSourceTransaction Management

===== PAGE 1159 =====

DetailsField
Description
The ID of an asset action source transaction originating in a system outside of Salesforce.
Type
string
ExternalReferenceDataSource
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
A system outside of Salesforce that contains asset action source transactions.
Type
reference
LegalEntityId
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
The ID of the legal entity record associated with the asset action source transaction.
This field is a relationship field.
This field is available in API version 62.0 and later.
Relationship Name
LegalEntity
Relationship Type
Lookup
Refers To
LegalEntity
Type
currency
ListPrice
Properties
Creatable, Filter, Nillable, Sort, Updateable
Description
List price for the order product. Value is inherited from the associated PriceBookEntry upon
order product creation.
Type
currency
NetUnitPrice
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The final adjusted unit price, inclusive of all adjustments, but exclusive of tax. The unit price
after all price adjustments are applied.
1145
AssetActionSourceTransaction Management

===== PAGE 1160 =====

DetailsField
Type
currency
ObligatedAmount
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
When a line amount is prorated, this amount shows the service amount that’s been consumed.
Type
int
OriginalLineNumber
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
The number of the original order item detail line. Salesforce uses this information to create
a record to amend, renew, or cancel an order. This field is available in API version 64.0 and
later.
Relationship Name
OrderItemDetail
Relationship Type
Lookup
Refers To
LineNumber
Type
picklist
PeriodBoundary
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
Boundary delimiters for periods. It determines when a period starts and/or ends.
Valid values are:
• AlignToCalendar
• Anniversary
• DayOfPeriod
• LastDayOfPeriod
Type
int
PeriodBoundaryDay
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The number specifying the day number when Period Boundary is a specific day in a
week/month/year. It only applies when PeriodBoundary is set to "day of period.”
1146
AssetActionSourceTransaction Management

===== PAGE 1161 =====

DetailsField
Type
picklist
PeriodBoundaryStartMonth
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
Field is populated based on input in the StartDate, PeriodBoundary, and PeriodBoundaryDay
when BillingFrequency2 is Annual or by manual user entry. Possible values are:
1-January
2-February
3-March
4-April
5-May
6-June
7-July
8-August
9-September
10-October
11-November
12-December
Type
reference
PricebookEntryId
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
PricebookEntry is used as a lookup for price information in order to pre-populate OrderItem's
ListPrice and UnitPrice.
Type
double
PricingTermCount
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
Number of pricing terms is this subscription product.
Type
currency
ProductAmount
Properties
Createable, Filter, Nillable, Sort, Updateable
1147
AssetActionSourceTransaction Management

===== PAGE 1162 =====

DetailsField
Description
The product amount after the asset action source transaction.
Type
reference
ProductSellingModelId
Properties
Creatable, Filter, Group, Nillable, Sort, Updateable
Description
Specifies the product selling model type. Foreignkey to ProductSellingModel entity.
Type
reference
ProrationPolicyId
Properties
Creatable, Filter, Group, Nillable, Sort, Updateable
Description
The ID of the ProrationPolicy used for pricing.
Type
double
Quantity
Properties
Creatable, Filter, Nillable, Sort, Updateable
Description
The product quantity or the change in product quantity after the asset action source
transaction.
Type
reference
ReferenceEntityItemId
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
The ID of an asset action source transaction originating in Salesforce. The transaction can be
an order product or a work order line item.
This field is a polymorphic relationship field.
Relationship Name
ReferenceEntityItem
Relationship Type
Lookup
Refers To
OrderItem, WorkOrderLineItem
1148
AssetActionSourceTransaction Management

===== PAGE 1163 =====

DetailsField
Type
string
SegmentIdentifier
Properties
Filter, Group, Nillable, Sort
Description
The ID of the ramp segment associated with the asset action source transaction.
This field is available in API version 62.0 and later.
Type
dateTime
StartDate
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The start date of the service or change.
Type
currency
Subtotal
Properties
Filter, Nillable, Sort
Description
The sum of the product amount and the adjustment amount.
This field is a calculated field.
Type
reference
TaxTreatmentId
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
Lookup to Tax Treatment entity. It's used to calculate tax.
Type
currency
TotalLineAmount
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The price of the line before any price adjustments were applied. SalesTransactionItem:
ProratedStartingTotal / StartingPriceTotal. Note: TotalPrice is computed using the UnitPrice,
which includes discounts (price adjustments), while TotalLineAmount doesn’t include price
adjustments.
1149
AssetActionSourceTransaction Management

===== PAGE 1164 =====

DetailsField
Type
currency
TotalPrice
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
Calculated by the pricing engine for ARC. Summation of TotalAdjustmentAmount plus
TotalLineAmount for this item.
Type
dateTime
TransactionDate
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The date of a source transaction, such as an order date.
Type
currency
UnitPrice
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The unit price of the item before any discounts or tax calculation.
AssetActionSrcPriceAdjustment
Each row represents a junction between an asset and the calculated price adjustment that's applied to an asset. This object is available
in API version 66.0 and later.
Supported Calls
create(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
Fields
DetailsField
Type
double
AdjustmentValue
Properties
Create, Filter, Nillable, Sort
Description
The value of the price adjustment that was applied to the asset.
1150
AssetActionSrcPriceAdjustmentTransaction Management

===== PAGE 1165 =====

DetailsField
Type
dateTime
AppliedPriceAdjustmentDate
Properties
Create, Filter, Sort
Description
The date and time on which the price adjustment was applied to the asset.
Type
reference
AssetActionSourceId
Properties
Create, Filter, Group, Sort
Description
The ID of the asset action source related to the asset for which the price adjustment was
applied.
This field is a relationship field.
Relationship Name
AssetActionSource
Relationship Type
Master-detail
Refers To
AssetActionSource (the master object)
Type
reference
AssetId
Properties
Filter, Group, Nillable, Sort
Description
The ID of the asset that this price adjustment applies to.
This field is a relationship field.
Relationship Name
Asset
Refers To
Asset
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the asset price adjustment record.
1151
AssetActionSrcPriceAdjustmentTransaction Management

===== PAGE 1166 =====

DetailsField
Type
reference
PriceAdjustmentCauseId
Properties
Create, Filter, Group, Sort
Description
The ID of the record that caused the price adjustment.
This field is a polymorphic relationship field.
Relationship Name
PriceAdjustmentCause
Refers To
Promotion
Type
picklist
PriceAdjustmentSource
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Specifies the source of price adjustment.
Possible values are:
• Discretionary—Reserved for future use.
• Promotion
• Rule—Reserved for future use.
• System—Reserved for future use.
Type
int
PrioritySequence
Properties
Create, Filter, Group, Nillable, Sort
Description
The priority sequence of the applied price adjustment.
AssetContractRelationship
Represents a relationship between an asset and a contract. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
1152
AssetContractRelationshipTransaction Management

===== PAGE 1167 =====

Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
Fields
DetailsField
Type
reference
AssetId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the asset related to the contract.
This field is a relationship field.
Relationship Name
Asset
Relationship Type
Lookup
Refers To
Asset
Type
reference
ContractId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the contract related to the asset.
This field is a relationship field.
Relationship Name
Contract
Relationship Type
Lookup
Refers To
Contract
Type
dateTime
EndDate
Properties
Create, Filter, Sort, Update
Description
The end date and time of the relationship between contract and asset.
1153
AssetContractRelationshipTransaction Management

===== PAGE 1168 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The timestamp when the current user last accessed this record, a record related to this record,
or a list view. The associated UI label is Last Modified Date.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp when the current user last viewed this record or list view. If this value is null,
the user accessed this record or list view (LastReferencedDate) but didn’t view it.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The auto-generated number assigned to AssetContractRelationship. (Read Only)
Type
dateTime
StartDate
Properties
Create, Filter, Sort, Update
Description
The start date and time of the relationship between contract and asset.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
AssetContractRelationshipFeed
Feed tracking is available for the object.
AssetContractRelationshipHistory
History is available for tracked fields of the object.
1154
AssetContractRelationshipTransaction Management

===== PAGE 1169 =====

AssetDowntimePeriod
Represents a period during which an asset is not able to perform as expected. Downtime periods include planned activities, such as
maintenance, and unplanned events, such as mechanical breakdown. This object is available in API version 49.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
AssetDowntimePeriodNumber
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The unique number of this asset downtime period record.
Type
reference
AssetId
Properties
Create, Filter, Group, Sort
Description
The ID of the asset this asset downtime period record is for.
Type
textarea
Description
Properties
Create, Nillable, Update
Description
The description of this asset downtime period.
Type
picklist
DowntimeType
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type of this asset downtime period. Possible values are:
• Planned
• Unplanned
1155
AssetDowntimePeriodTransaction Management

===== PAGE 1170 =====

DetailsField
Type
dateTime
EndTime
Properties
Create, Filter, Sort, Update
Description
The time this asset downtime period ended.
Type
boolean
IsExcluded
Properties
Defaulted on create, Filter, Group, Sort
Description
Whether this asset downtime period is excluded from the calculation of accumulated
downtime and accumulated unplanned downtime, and therefore not included in availability
and reliability calculations.
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
The timestamp for when the current user last viewed this record. If this value is null, this
record might only have been referenced (LastReferencedDate) and not viewed.
Type
dateTime
StartTime
Properties
Create, Filter, Sort, Update
Description
The time this asset downtime period started.
AssetOwnerSharingRule
Represents the rules for sharing an Asset with users other than the owner. This object is available in API version 33.0 and later.
1156
AssetOwnerSharingRuleTransaction Management

===== PAGE 1171 =====

Note:  To enable access to this object for your org, contact Salesforce customer support. However, we recommend that you
instead use Metadata API to programmatically update owner sharing rules because it triggers automatic sharing rule recalculation.
The SharingRules Metadata API type is enabled for all orgs.
Supported Calls
create(), delete(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(), update(),
upsert()
Special Access Rules
Customer Portal users can’t access this object.
Fields
DetailsField
Type
picklist
AssetAccessLevel
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
A value that represents the type of sharing being allowed. The possible values are:
• Read
• Edit
Type
textarea
Description
Properties
Create, Filter, Nillable, Sort, Update
Description
A description of the sharing rule. Maximum size is 1000 characters.
Type
string
DeveloperName
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The unique name of the object in the API. This name can contain only underscores
and alphanumeric characters, and must be unique in your org. It must begin with a
letter, not include spaces, not end with an underscore, and not contain two
consecutive underscores. In managed packages, this field prevents naming conflicts
on package installations. With this field, a developer can change the object’s name
in a managed package and the changes are reflected in a subscriber’s organization.
Corresponds to Rule Name in the user interface.
1157
AssetOwnerSharingRuleTransaction Management

===== PAGE 1172 =====

DetailsField
Note:  When creating large sets of data, always specify a unique
DeveloperName  for each record. If no DeveloperName  is specified,
performance may slow while Salesforce generates one for each record.
Type
reference
GroupId
Properties
Create, Filter, Group, Sort
Description
The ID representing the source group. Cases owned by users in the source group
trigger the rule to give access.
Type
string
Name
Properties
Create, Filter, Group, Sort, Update
Description
Label of the sharing rule as it appears in the user interface. Limited to 80 characters.
Corresponds to Label on the user interface.
Type
reference
UserOrGroupId
Properties
Create, Filter, Group, Sort
Description
The ID representing the target user or group. Target users or groups are given access.
Usage
Use this object to manage the sharing rules for assets. General sharing uses this object.
AssetRateAdjustment
Stores the tier rate adjustments for the asset rate card entries. This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
1158
AssetRateAdjustmentTransaction Management

===== PAGE 1173 =====

Special Access Rules
This object is available in orgs where Revenue Cloud is enabled.
Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Filter, Group, Restricted picklist, Sort
Description
The type of rate adjustment.
Valid values are:
• Amount—Adjusts rate by using a specific amount.
• Override—Adjusts rate by using the override rate.
• Percentage—Adjusts rate by using a percentage.
Type
double
AdjustmentValue
Properties
Filter, Sort
Description
The value of the adjustment.
Type
reference
AssetRateCardEntryId
Properties
Filter, Group, Sort
Description
The ID of the parent asset rate card entry record associated with the asset rate adjustment.
This field is a relationship field.
Relationship Name
AssetRateCardEntry
Relationship Type
Master-detail
Refers To
AssetRateCardEntry (the master object)
Type
double
LowerBound
1159
AssetRateAdjustmentTransaction Management

===== PAGE 1174 =====

DetailsField
Properties
Filter, Nillable, Sort
Description
The minimum quantity for the adjustment to be applicable.
Type
string
Name
Properties
Filter, Group, idLookup, Sort
Description
The name of the asset rate adjustment.
Type
double
UpperBound
Properties
Filter, Nillable, Sort
Description
The maximum quantity for the adjustment to be applicable.
AssetRateCardEntry
Stores the negotiated rate card entries that are associated with an asset in Revenue Cloud. This object is available in API version 62.0 and
later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
Special Access Rules
This object is available in orgs where Revenue Cloud is enabled.
Fields
DetailsField
Type
reference
AssetId
1160
AssetRateCardEntryTransaction Management

===== PAGE 1175 =====

DetailsField
Properties
Filter, Group, Sort
Description
The ID of the asset rate card entry record.
This field is a relationship field.
Relationship Name
Asset
Relationship Type
Master-detail
Refers To
Asset (the master object)
Type
string
BindingObjectFormula
Properties
Filter, Group, Nillable, Sort
Description
The formula that returns the ID of the associated binding object, if specified. If binding object
isn't added, the formula returns the asset ID of the asset related to this asset rate card entry.
This field is read-only. Available in API version 65.0 and later.
Type
reference
BindingObjectId
Properties
Filter, Group, Nillable, Sort
Description
The ID of the binding object associated with the asset rate card entry. Available in API version
65.0 and later.
This field is a relationship field.
Relationship Name
BindingObject
Refers To
Asset
Type
double
BindingObjectRateOrder
Properties
Filter, Nillable, Sort
Description
The order that determines the applicable binding object rate when multiple rates are defined
for an Anchor binding object within a effective period. Available in API version 65.0 and later.
1161
AssetRateCardEntryTransaction Management

===== PAGE 1176 =====

DetailsField
Type
picklist
CurrencyIsoCode
Properties
Defaulted on create, Filter, Group, Restricted picklist, Sort
Description
The ID of the binding object associated with the asset rate card entry.
Possible values are:
• AED - UAE Dirham
• AUD - Australian Dollar
• BRL - Brazilian Real
• CAD - Canadian Dollar
• EUR - Euro
• GBP - British Pound
• INR - Indian Rupee
• JPY - Japanese Yen
• SEK - Swedish Krona
• USD - U.S. Dollar
The default value is USD. Available in API version 65.0 and later.
Type
dateTime
EndDate
Properties
Filter, Nillable, Sort
Description
The date when the rate card's time period becomes inactive. The rate card becomes inactive
at 11:59:00 PM on the end date.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
An auto-generated number assigned to the asset rate card entry. Read-only.
Type
double
NegotiatedRate
Properties
Filter, Sort
Description
The base negotiated rate used to charge overage consumption.
1162
AssetRateCardEntryTransaction Management

===== PAGE 1177 =====

DetailsField
Type
reference
RateCardEntryId
Properties
Filter, Group, Nillable, Sort
Description
The ID of the rate card entry record containing the catalog rates that's associated with the
asset rate card entry.
This field is a relationship field.
Relationship Name
RateCardEntry
Refers To
RateCardEntry
Type
reference
RateCardId
Properties
Filter, Group, Nillable, Sort
Description
The ID of the rate card record that's associated with the asset rate card entry.
This field is a relationship field.
Relationship Name
RateCard
Refers To
RateCard
Type
reference
RateUnitOfMeasureId
Properties
Filter, Group, Nillable, Sort
Description
The ID of the unit of measure record that's associated with the asset rate card entry.
This field is a relationship field.
Relationship Name
RateUnitOfMeasure
Refers To
UnitOfMeasure
Type
dateTime
StartDate
Properties
Filter, Sort
1163
AssetRateCardEntryTransaction Management

===== PAGE 1178 =====

DetailsField
Description
The date when the rate card's time period becomes active. The rate card becomes active at
12:00:00 AM on the start date.
Type
reference
UsageResourceId
Properties
Filter, Group, Nillable, Sort
Description
The ID of the usage resource record that's associated with the asset rate card entry.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
AssetRelationship
Represents a non-hierarchical relationship between assets due to an asset modification; for example, a replacement, upgrade, or other
circumstance. In Revenue Lifecycle Management, this object represents an asset or assets grouped in a bundle or set. This object is
available in API version 41.0 and later.
Asset relationships appear in the Primary Assets and Related Assets related lists on asset records in the UI.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Some fields are available only in Revenue Cloud. Field availability is noted in the field detail column.
Fields
DetailsField Name
Type
reference
AssetId
Properties
Create, Filter, Group, Sort
1164
AssetRelationshipTransaction Management

===== PAGE 1179 =====

DetailsField Name
Description
The unique identifier of the new asset, which is the asset that is taking the place
of the existing asset.
This field is a relationship field.
Relationship Name
Asset
Relationship Type
Lookup
Refers To
Asset
Type
string
AssetRelationshipNumber
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
An auto-generated number identifying the asset relationship.
Type
picklist
AssetRole
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Describes the position of the main asset relative to the other assets in the
relationship.
This field is available in API version 58.0 and later. This field is available in orgs
with Revenue Cloud.
Possible values are:
• Add-on—The main asset is an add-on.
• Bundle—The main asset is the bundle parent.
• Set—The asset is the main asset in the set.
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Three-letter ISO 4217 currency code associated with the asset. The default value
is USD.
1165
AssetRelationshipTransaction Management

===== PAGE 1180 =====

DetailsField Name
Type
dateTime
FromDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date when the new asset was installed.
Type
string
GroupingKey
Properties
Filter, Group, idLookup, Nillable, Sort
Description
Read-only field used to indicate the bundle that an asset belongs to. For example,
if two assets have the same GroupingKey value, then it means that the assets are
bundled together.
This field is available in API v.60.0 and later. This field is available in orgs with
Revenue Cloud.
Type
reference
ProductRelationshipTypeId
Properties
Filter, Group, Nillable, Sort
Description
The unique identifier of the record that describes the relationship between the
main and associated assets.
This field is available in API version 58.0 and later. This field is available in orgs
with Revenue Cloud.
This field is a relationship field.
Relationship Name
ProductRelationshipType
Relationship Type
Lookup
Refers To
ProductRelationshipType
Type
reference
ProductRelatedComponent
Properties
Filter, Group, Nillable, Sort
Description
The product related component that’s associated with the asset relationship.
1166
AssetRelationshipTransaction Management

===== PAGE 1181 =====

DetailsField Name
This field is a relationship field.
This field is available in API 60.0 and later in Revenue Cloud.
Relationship Name
ProductRelatedComponent
Relationship Type
Lookup
Refers To
ProductRelatedComponent
Type
reference
RelatedAssetId
Properties
Create, Filter, Group, Sort, Update
Description
The existing asset that is being modified.
This field is a relationship field.
Relationship Name
RelatedAsset
Relationship Type
Lookup
Refers To
Asset
Type
picklist
RelatedAssetPricing
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Specifies whether the price of the related asset is included in the bundle price.
Valid values are:
• IncludedInBundlePrice
• NotIncludedInBundlePrice
This field is available in API version 59.0 and later in Revenue Cloud.
Type
picklist
RelatedAssetQtyScaleMethod
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Specifies how the quantity of the related asset changes relative to the quantity
of the parent asset. Valid values are:
1167
AssetRelationshipTransaction Management

===== PAGE 1182 =====

DetailsField Name
• Constant
• Proportional
This field is available in API version 59.0 and later in Revenue Cloud.
Type
picklist
RelatedAssetRole
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Describes the position of the associated asset relative to other assets in the
relationship.
This field is available in API version 58.0 and later. This field is available in orgs
with Revenue Cloud.
Valid values are:
• Add-on—The main asset is an add-on.
• Bundle—The main asset is the bundle parent.
• Set—The asset is the main asset in the set.
• Simple—The asset is purchased individually and isn’t associated with
variations.
• Variation Parent——The main asset is the variation parent.
Type
picklist
RelationshipType
Properties
Create, Defaulted on create, Filter, Group, Nillable, Sort, Update
Description
The type of relationship between the existing asset and the new asset. This field
comes with three values—Replacement, Upgrade, and Crossgrade—, but you
can create more values in Setup.
Possible values are:
• Crossgrade—The new asset is a crossgrade of an existing asset. For
example, changing a subscription to a plan with the same service, but that
runs for a longer amount of time.
• Replacement—The new asset is replacing an existing asset. For example,
a customer’s faulty widget that was under warranty is being replaced with
a new one.
• Upgrade—The new asset is an upgrade of an existing asset. For example,
upgrading a customer’s existing subscription plan to a new plan with more
services.
The default value is Replacement.
1168
AssetRelationshipTransaction Management

===== PAGE 1183 =====

DetailsField Name
Type
dateTime
ToDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date when the modified asset is uninstalled.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
AssetRelationshipChangeEvent (API version 62.0)
Change events are available for the object.
AssetRelationshipFeed
Feed tracking is available for the object.
AssetRelationshipHistory
History is available for tracked fields of the object.
AssetRelationshipOwnerSharingRule (API version 58.0)
Sharing rules are available for the object.
AssetRelationshipShare (API version 58.0)
Sharing is available for the object.
AssetShare
Represents a sharing entry on an Asset. This object is available in API version 33.0 and later.
You can only create, edit, and delete sharing entries for standard objects whose RowCause  field is set to Manual. Sharing entries
for standard objects with different RowCause  values are created as a result of your Salesforce org’s sharing configuration and are
read-only. For some sharing mechanisms, such as sharing sets, sharing entries aren’t stored at all.
Note:  While Salesforce currently maintains read-only sharing entries for multiple sharing mechanisms, it’s possible that we’ll stop
storing certain share records to improve performance. As a best practice, don’t create customizations that rely on the availability
of these sharing entries. Any changes to sharing behavior will be communicated before they occur.
Supported Calls
describeSObjects(), query(), retrieve()
Special Access Rules
Customer Portal users can’t access this object.
1169
AssetShareTransaction Management

===== PAGE 1184 =====

Fields
The properties available for some fields depend on the default organization-wide sharing settings. The properties listed are true for the
default settings of such fields.
DetailsField
Type
picklist
AssetAccessLevel
Properties
Filter, Group, Restricted picklist, Sort
Description
Level of access that the User or Group has to the Asset. The possible values are:
• Read
• Edit
• All  This value is not valid for creating or deleting records.
This field must be set to an access level that is higher than the organization’s default access
level for cases.
Type
reference
AssetId
Properties
Filter, Group, Sort
Description
ID of the Asset associated with this sharing entry. This field can't be updated.
This is a relationship field.
Relationship Name
Asset
Relationship Type
Lookup
Refers To
Asset
Type
boolean
IsDeleted
Properties
Defaulted on create, Filter
Description
Indicates whether the object has been moved to the Recycle Bin (true) or not (false).
Label is Deleted.
Type
picklist
RowCause
1170
AssetShareTransaction Management

===== PAGE 1185 =====

DetailsField
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Reason that this sharing entry exists. If you’re creating a sharing entry, the only permitted
value is Manual. If no value is specified, the field defaults to Manual. All other RowCause
values are read-only. After the sharing entry is created, this field can’t be edited.
Valid values include:
• Manual—The User or Group has access because a user with “All” access manually
shared the Asset with them.
• Owner—The User is the owner of the Asset.
• Rule—The User or Group has access via an Asset sharing rule.
• GuestRule—The User or Group has access via an Asset guest user sharing rule.
• LpuImplicit—The User has access to records owned by high-volume Experience
Cloud site users via a share group.
Type
reference
UserOrGroupId
Properties
Filter, Group, Sort
Description
ID of the User or Group that has been given access to the Asset. This field can't be updated.
This is a polymorphic relationship field.
Relationship Name
UserOrGroup
Relationship Type
Lookup
Refers To
Group, User
Usage
This object allows you to determine which users and groups can view and edit Asset records owned by other users.
If you attempt to create a new record that matches an existing record, request updates any modified fields and returns the existing
record.
AssetStatePeriod
Represents a time span when an asset has the same quantity, amount, and monthly recurring revenue (MRR). An asset has as many asset
state periods as there are changes to it (asset actions) during its lifecycle. The dashboard and related pages show the current asset state
period. The fields can’t be edited. This object is available in API version 50.0 and later.
1171
AssetStatePeriodTransaction Management

===== PAGE 1186 =====

Supported Calls
createable(), deletable(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(),
query(), retrieve(), search(), updateable().
Special Access Rules
To use Customer Asset Lifecycle Management APIs, you must have the Access Customer Asset Lifecycle Management APIs permission
and Read access to the Asset, Asset Action, Asset Action Source, and Asset State Period objects.
Fields
DetailsField
Type
currency
Amount
Properties
Createable, Filter, Sort, Updateable
Description
An asset’s total amount during an asset state period. Revenue Cloud doesn't set or use this
field's value currently.
Type
reference
AssetId
Properties
Createable, Filter, Group, Sort
Description
The asset related to an asset state period. Label is Asset.
This field is a relationship field.
Relationship Name
Asset
Relationship Type
Lookup
Refers To
Asset
Type
string
AssetStatePeriodNumber
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The ID of the asset state period. Label is Name.
1172
AssetStatePeriodTransaction Management

===== PAGE 1187 =====

DetailsField
Type
picklist
BillingFrequency
Properties
Createable, Filter, Group, Nillable, Restricted picklist, Sort, Updateable
Description
The time period that indicates how often the line item is billed.
Possible values are:
• Annual
• Monthly
• Quarterly
• Semi-Annual
Available in API version 65.0 and later.
Type
reference
BindingInstanceTargetId
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
The ID of a custom product target for a usage-based quote line item, order Item, or asset
allocation.
This field is a polymorphic relationship field.
Relationship Name
BindingInstanceTarget
Refers To
Account, Asset, BindingObjectCustomExt, Contract
Type
percent
Discount
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
Editable number from 0 to 100. Available in API version 65.0 and later.
Type
currency
DiscountAmount
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The fixed amount discount to apply to the line item. Available in API version 65.0 and later.
1173
AssetStatePeriodTransaction Management

===== PAGE 1188 =====

DetailsField
Type
dateTime
EndDate
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The end date and time of an asset state period. On an asset that is an evergreen subscription,
the last asset state period has no end date.
Type
reference
LegalEntityId
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
The ID of the related legal entity.
This field is a relationship field.
Relationship Name
LegalEntity
Refers To
LegalEntity
Type
currency
Mrr
Properties
Createable, Filter, Sort, Updateable
Description
An asset’s monthly recurring revenue during an asset state period.
Type
reference
PriceRevisionPolicy
Properties
Createable, Filter, Group, Sort, Updateable
Description
Specifies the price uplift policy associated with this asset state period.
This field is a relationship field.
This field is available in API version 65.0 and later.
Relationship Name
Price Revision Policy
Relationship Type
Lookup
Refers To
PriceRevisionPolicy
1174
AssetStatePeriodTransaction Management

===== PAGE 1189 =====

DetailsField
Type
double
Quantity
Properties
Createable, Filter, Sort, Updateable
Description
The total quantity of an asset during an asset state period.
Type
string
RampIdentifier
Properties
Filter, Group, Nillable, Sort
Description
The ramp record used to group order item segments for this asset state period.
This field is available in orgs that have Revenue Cloud when the Ramp Deals setting is enabled.
This field is available in API version 62.0 and later.
Type
string
SegmentIdentifier
Properties
Filter, Group, Nillable, Sort
Description
The order item segment for this asset state period.
This field is available in orgs that have Revenue Cloud when the Ramp Deals setting is enabled.
This field is available in API version 62.0 and later.
Type
string
SegmentName
Properties
Createable, Filter, Group, Nillable, Sort, Updateable
Description
The name of the order item segment for this asset state period.
This field is available in orgs that have Revenue Cloud when the Ramp Deals setting is enabled.
This field is available in API version 62.0 and later.
Type
picklist
SegmentType
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Updateable
Description
The period for the order item segment for this asset state period. Valid values are:
1175
AssetStatePeriodTransaction Management

===== PAGE 1190 =====

DetailsField
• Custom
• Free Trial
• Yearly
The default value is Yearly.
This field is available in orgs that have Revenue Cloud when the Ramp Deals setting is enabled.
This field is available in API version 62.0 and later.
Type
dateTime
StartDate
Properties
Createable, Filter, Sort, Updateable
Description
The start date and time of an asset state period.
Type
currency
UnitPrice
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
The price per unit for the line item. Available in API version 65.0 and later. Revenue Cloud
won't populate this field in API version 66.0 and later.
Type
percent
UnitPriceUplift
Properties
Createable, Filter, Nillable, Sort, Updateable
Description
Indicates the percentage increase of a line item's unit price. Available in API version 65.0 and
later.
AssetStatePeriodAttribute
Represents a virtual object that holds the key-value pair of the asset attribute in a specified asset state period. This object is a child object
of AssetStatePeriod. This object is available in API version 60.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
describeLayout(), describeSObjects(), query(), retrieve()
1176
AssetStatePeriodAttributeTransaction Management

===== PAGE 1191 =====

Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud with the Access Lifecycle-Managed Assets
user permission. This object is editable only through API and not the UI.
Fields
DetailsField
Type
reference
AssetStatePeriodId
Properties
Filter, Group, Sort
Description
The asset state period that's associated with the asset attribute.
This field is a relationship field.
Relationship Name
AssetStatePeriod
Relationship Type
Master-detail
Refers To
AssetStatePeriod (the master object)
Type
reference
AttributeDefinitionId
Properties
Filter, Group, Sort
Description
The attribute definition that's associated with the asset state period attribute.
This field is a relationship field.
Relationship Name
AttributeDefinition
Relationship Type
Lookup
Refers To
AttributeDefinition
Type
string
AttributeName
Properties
Filter, Group, idLookup, Nillable, Sort
Description
The name of the asset attribute.
1177
AssetStatePeriodAttributeTransaction Management

===== PAGE 1192 =====

DetailsField
Type
reference
AttributePicklistValueId
Properties
Filter, Group, Nillable, Sort
Description
The value specified in the picklist type field that corresponds to the attribute in the
AttributePicklistValue object.
This field is a relationship field.
Relationship Name
AttributePicklistValue
Relationship Type
Lookup
Refers To
AttributePicklistValue
Type
string
AttributeValue
Properties
Filter, Group, Nillable, Sort
Description
The value of the asset state period attribute. For example, a shirt can have the value of blue,
which indicates the shirt's color, or it can have the value of small, which indicates the
shirt's size.
You can use this field to filter records only if the DataType value in the related
AttributeDefinitionId record is Text. If the DataType value is Picklist, use
the value in the AttributePicklistValueId field for filtering. You can’t use this
field to filter records if the DataType value is Checkbox, Currency, Date, Datetime,
Multipicklist, Number, or Percent.
Usage
This object doesn’t support custom fields, validation rules, or triggers. In SOQL queries, you can filter records by using Id  and
AttributeDefinition. You can’t use AttributeValue  in the WHERE clause.
AssetTag
Associates a word or short phrase with an Asset.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve()
1178
AssetTagTransaction Management

===== PAGE 1193 =====

Fields
DetailsField Name
Type
reference
ItemId
Properties
Create, Filter
Description
ID of the tagged item.
Type
string
Name
Properties
Create, Filter
Description
Name of the tag. If this value does not already exist, a new TagDefinition is created and
becomes the parent of this Tag object. Otherwise, a TagDefinition with the same name
becomes the parent of this Tag object. Parent relationships are created automatically.
Type
reference
TagDefinitionId
Properties
Filter
Description
ID of the parent TagDefinition object that owns the tag.
Type
picklist
Type
Properties
Create, Filter, Restricted picklist
Description
Defines the visibility of a tag.
Valid values:
• Public—The tag can be viewed and manipulated by all users in an organization.
• Personal—The tag can be viewed or manipulated only by a user with a matching
OwnerId.
Usage
AssetTag stores the relationship between its parent TagDefinition and the Asset being tagged. Tag objects act as metadata, allowing
users to describe and organize their data.
1179
AssetTagTransaction Management

===== PAGE 1194 =====

When a tag is deleted, its parent TagDefinition will also be deleted if the name is not being used; otherwise, the parent remains. Deleting
a TagDefinition sends it to the Recycle Bin, along with any associated tag entries.
AssetTokenEvent
The documentation has moved to AssetTokenEvent in the Platform Events Developer Guide.
AssetWarranty
Defines the warranty terms applicable to an asset along with any exclusions and extensions. This object is available in API version 50.0
and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
AssetId
Properties
Create, Filter, Group, Sort
Description
The ID of the asset this warranty term applies to.
Type
string
AssetWarrantyNumber
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The identifier of the asset warranty record.
Type
date
EndDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date on which this warranty term expires.
Type
picklist
ExchangeType
1180
AssetTokenEventTransaction Management

===== PAGE 1195 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The type of exchange offered by this warranty term.
Type
textarea
Exclusions
Properties
Create, Nillable, Update
Description
Description of any exclusions.
Type
percent
ExpensesCovered
Properties
Create, Filter, Nillable, Sort, Update
Description
The percentage of expenses covered.
Type
date
ExpensesCoveredEndDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date on which cover for expenses ends.
Type
boolean
IsTransferable
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Defines whether the warranty term can be transferred to a new owner.
Type
percent
LaborCovered
Properties
Create, Filter, Nillable, Sort, Update
Description
The percentage of labor covered.
Type
date
LaborCoveredEndDate
1181
AssetWarrantyTransaction Management

===== PAGE 1196 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date on which cover for labor ends.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date when the asset warranty term was last modified. Its label in the user interface is
Last Modified Date.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date when the asset warranty term was last viewed.
Type
percent
PartsCovered
Properties
Create, Filter, Nillable, Sort, Update
Description
The percentage of parts covered.
Type
date
PartsCoveredEndDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date on which cover for parts ends.
Type
reference
Pricebook2Id
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the price book item associated with this asset warranty term.
1182
AssetWarrantyTransaction Management

===== PAGE 1197 =====

DetailsField
Type
date
StartDate
Properties
Create, Filter, Group, Sort, Update
Description
The date on which cover under this warranty term starts.
Type
reference
WarrantyTermId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the warranty term this asset warranty term extends.
Type
picklist
WarrantyType
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The type of the warranty.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
AssetWarrantyChangeEvent
Change events are available for the object.
BindingObjUsageRsrcPlcy
Represents the policies that are used for the usage resource that's associated with an asset or a binding object. This object is available
in API version 65.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
1183
BindingObjUsageRsrcPlcyTransaction Management

===== PAGE 1198 =====

Fields
DetailsField
Type
reference
BindingObjectId
Properties
Create, Filter, Group, Sort, Update
Description
The object that's bounded with the quote line policy or order policy.
This field is a polymorphic relationship field.
Relationship Name
BindingObject
Refers To
Account, Asset, BindingObjectCustomExt, Contract
Type
picklist
DrawdownOrder
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the order that's used to debit consumption of entitlements related to the usage
resource from the usage entitlement bucket.
Valid values are:
• ExpiringFirst
• GrantedFirst
• GrantedLast
Type
dateTime
EffectiveEndDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time until when the policy remains effective.
Type
dateTime
EffectiveStartDate
Properties
Create, Filter, Sort, Update
Description
The date and time when the policy becomes effective.
1184
BindingObjUsageRsrcPlcyTransaction Management

===== PAGE 1199 =====

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
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The auto-generated identifier for the quote line item usage resource policy record. For
example, BOURP-000004.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the binding object usage resource policy.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
RatingFrequencyPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The rating frequency policy associated with the usage resource.
This field is a relationship field.
1185
BindingObjUsageRsrcPlcyTransaction Management

===== PAGE 1200 =====

DetailsField
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
1186
BindingObjUsageRsrcPlcyTransaction Management

===== PAGE 1201 =====

DetailsField
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource associated with the usage product.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
ContractItemPrice
Represents an object that’s used to capture a price for a product on a contract. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations. 
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
Fields
DetailsField
Type
picklist
AdjustmentMethod
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Method used to apply discount.
Valid values are:
• Range—Apply the discount to all items after you reach the discount tier. For example,
suppose that you give a 10% discount for 50 or more items. If a customer orders 50
products, and the type is range, apply the 10% discount to all 50 items.
1187
ContractItemPriceTransaction Management

===== PAGE 1202 =====

DetailsField
• Slab—Apply discounts in tiers. For example, suppose that you order 30 products, and
the type is slab, you can apply a 10% discount to units 1–9, a 20% discount to units
10–19, and a 30% discount to units 20–30.
Type
reference
ContractId
Properties
Create, Filter, Group, Sort
Description
ID of the contract.
This field is a relationship field.
Relationship Name
Contract
Relationship Type
Master-detail
Refers To
Contract (the master object)
Type
picklist
DiscountType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type of discount applied, a percentage of the price or an amount.
Valid values are:
• AdjustmentAmount
• AdjustmentPercentage
Type
double
DiscountValue
Properties
Create, Filter, Nillable, Sort, Update
Description
The value of the discount applied, based on the discount type.
Type
dateTime
EndDate
Properties
Create, Filter, Nillable, Sort, Update
Description
End date and time of the relationship between the contract and contract item price.
1188
ContractItemPriceTransaction Management

===== PAGE 1203 =====

DetailsField
Type
reference
ItemId
Properties
Create, Filter, Group, Sort, Update
Description
ID of the product or product category related to a price in a contract.
This field is a polymorphic relationship field.
Relationship Name
Item
Relationship Type
Lookup
Refers To
Product2, ProductCategory
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
Timestamp when the current user last accessed this record, a record related to this record,
or a list view.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
Timestamp when the current user last viewed this record or list view. If this value is null, the
user accessed this record or list view (LastReferencedDate) but didn’t view it.
Type
currency
ListPrice
Properties
Filter, Nillable
Description
The list price of the product. This value is read-only and inherited from the price book related
to the contract when the contract item price is created. Use the list price to compare the
advertised price to prices that customers receive during contract negotiations. This field is
available in API version 66.0 and later.
Type
string
Name
1189
ContractItemPriceTransaction Management

===== PAGE 1204 =====

DetailsField
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Auto-generated number assigned to the contract item price. (Read only)
Type
currency
Price
Properties
Create, Filter, Nillable, Sort, Update
Description
Unit price for the product sold as part of the contract.
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Product selling model for the product associated with the price.
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
Selling mode type to specify whether the product sold is a one-time sale, an evergreen
subscription, or a subscription with a defined term.
Valid values are:
• Evergreen
• OneTime
• TermDefined
The value derived from the product selling model.
Type
dateTime
StartDate
1190
ContractItemPriceTransaction Management

===== PAGE 1205 =====

DetailsField
Properties
Create, Filter, Sort, Update
Description
Start date and time of the relationship between the contract and contract item price.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ContractItemPriceHistory on page 1193
History is available for tracked fields of the object.
ContractItemPriceAdjTier
Represents the tiers of a price adjustment to a product on a contract. This object is available in API version 63.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Special Access Rules
This object is available with Revenue Cloud.
Fields
DetailsField
Type
reference
ContractItemPriceId
Properties
Create, Filter, Group, Sort
Description
The contract item price ID associated with the contract item price adjustment tier.
This field is a relationship field.
Relationship Name
ContractItemPrice
1191
ContractItemPriceAdjTierTransaction Management

===== PAGE 1206 =====

DetailsField
Relationship Type
Master-detail
Refers To
ContractItemPrice (the master object)
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
Timestamp when the current user last viewed this record or list view. If this value is null, the
user accessed this record or list view (LastReferencedDate) but didn’t view it.
Type
double
LowerBound
Properties
Create, Filter, Sort, Update
Description
The minimum quantity for the adjustment to be applicable.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the record.
Type
picklist
TierType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of adjustment tier.
1192
ContractItemPriceAdjTierTransaction Management

===== PAGE 1207 =====

DetailsField
Valid values are:
• AdjustmentAmount
• AdjustmentPercentage
• OverrideAmount
Type
double
TierValue
Properties
Create, Filter, Sort, Update
Description
The price adjustment value.
Type
double
UpperBound
Properties
Create, Filter, Nillable, Sort, Update
Description
The maximum quantity for the adjustment to be applicable.
Associated Objects
This object has associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
ContractItemPriceAdjTierFeed
Feed tracking is available for the object.
ContractItemPriceAdjTierHistory
History is available for tracked fields of the object.
ContractItemPriceHistory
Represents the history of changes to the values in the fields of a ContractItemPrice object. This object is available in API version 61.0 and
later.
Supported Calls
describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
1193
ContractItemPriceHistoryTransaction Management

===== PAGE 1208 =====

Fields
DetailsField
Type
reference
ContractItemPriceId
Properties
Filter, Group, Sort
Description
ID of the ContractItemPrice record.
This field is a relationship field.
Relationship Name
ContractItemPrice
Relationship Type
Lookup
Refers To
ContractItemPrice
Type
picklist
DataType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Data type of the field that was changed.
Valid values are:
• Address
• AnyType
• AutoNumber
• Base64
• BitVector
• Boolean
• Content
• Currency
• DataCategoryGroupReference
• DateOnly
• DateTime
• Division
• Double
• DynamicEnum
• Email
• EncryptedBase64
1194
ContractItemPriceHistoryTransaction Management

===== PAGE 1209 =====

DetailsField
• EncryptedText
• EntityId
• EnumOrId
• ExternalId
• Fax
• File
• HtmlMultiLineText
• HtmlStringPlusClob
• InetAddress
• Json
• Location
• MultiEnum
• MultiLineText
• Namespace
• Percent
• PersonName
• Phone
• Raw
• RecordType
• SfdcEncryptedText
• SimpleNamespace
• StringPlusClob
• Switchable_PersonName
• Text
• TimeOnly
• Url
• YearQuarter
Type
picklist
Field
Properties
Filter, Group, Restricted picklist, Sort
Description
Name of the field that was changed.
Possible values are:
• AdjustmentMethod
• Contract
• DiscountType
1195
ContractItemPriceHistoryTransaction Management

===== PAGE 1210 =====

DetailsField
• DiscountValue
• EndDate
• Item
• Name
• Price
• ProductSellingModel
• StartDate
• created
• customPersonMerged
• feedEvent
• individualMerged
• locked—Record locked.
• ownerAccepted—Owner (Accepted)
• ownerAssignment—Owner (Assignment)
• unlocked—Record unlocked.
Type
anyType
NewValue
Properties
Nillable, Sort
Description
New value of the field that was changed.
Type
anyType
OldValue
Properties
Nillable, Sort
Description
Latest value of the field before it was changed.
OrderDeliveryMethod
Shows the customizations and options that a buyer selected for their delivery method. This object is available in API version 48.0 and
later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
1196
OrderDeliveryMethodTransaction Management

===== PAGE 1211 =====

Special Access Rules
To access Commerce Orders entities, your org must have a Salesforce Order Management license. Commerce Orders entities are available
only in Lightning Experience.
Fields
DetailsField
Type
picklist
Carrier
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The carrier that the buyer chose for their delivery method. Developers must add values to
this field.
Type
picklist
ClassOfService
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The carrier class of service that the buyer chose for their delivery method. Developers must
add values to this field.
Type
textarea
Description
Properties
Create, Nillable, Update
Description
Description of the delivery method.
Type
boolean
IsActive
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Assign new delivery groups to active delivery methods.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
1197
OrderDeliveryMethodTransaction Management

===== PAGE 1212 =====

DetailsField
Description
The timestamp for when the current user last viewed a record related to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp for when the current user last viewed this record. If this value is null, this
record might only have been referenced (LastReferencedDate) and not viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
Required. Default name of this record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The user who owns an order delivery method record.
Type
reference
ProductId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Optional. This product represents a delivery charge order product for a delivery using this
delivery method. For example, you could create a product that represents an overnight
express charge and assign it to an overnight express delivery method.
Type
string
ReferenceNumber
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Reference number for an external delivery method.
1198
OrderDeliveryMethodTransaction Management

===== PAGE 1213 =====

DetailsField
Type
reference
ShippingCarrierMethod
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Optional. A specific shipping service provided by a shipping carrier, such as Ground, 2Day,
and NextDay. Depends on the range of transit times available for each carrier.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
OrderDeliveryMethodChangeEvent (API version 62.0)
Change events are available for the object.
OrderItemAttribute
Represents a virtual object that stores an attribute specified for an order item.This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), query(), retrieve(), update(), upsert()
Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
Fields
DetailsField
Type
reference
AttributeDefinitionId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the attribute definition for this order item attribute.
This field is a relationship field.
Relationship Name
AttributeDefinition
Relationship Type
Lookup
1199
OrderItemAttributeTransaction Management

===== PAGE 1214 =====

DetailsField
Refers To
AttributeDefinition
Type
string
AttributeName
Properties
Filter, Group, idLookup, Nillable, Sort
Description
The name given to order item attribute.
Type
reference
AttributePicklistValueId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the attribute picklist value if the attribute is a picklist type.
This field is a relationship field.
Relationship Name
AttributePicklistValue
Relationship Type
Lookup
Refers To
AttributePicklistValue
Type
string
AttributeValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Stores the value of the order item attribute. For example 5-TB storage.
You can use this field to filter records only if the DataType value in the related
AttributeDefinitionId record is Text. If the DataType value is Picklist, use
the value in the AttributePicklistValueId field for filtering. You can’t use this
field to filter records if the DataType value is Checkbox, Currency, Date, Datetime,
Multipicklist, Number, or Percent.
Type
string
ExternalId
Properties
Create, Filter, Group, Nillable, Sort, Update
1200
OrderItemAttributeTransaction Management

===== PAGE 1215 =====

DetailsField
Description
An auto-generated ID of the attribute record saved in an external system (for example an
HBase database).
Type
boolean
IsPriceImpacting
Properties
Defaulted on create, Filter, Group, Sort
Description
The pricing impacting the status of the attribute.
The default value is false.
Type
reference
OrderItemId
Properties
Create, Filter, Group, Sort
Description
The parent order item associated with the order item attribute.
This field is a relationship field.
Relationship Name
OrderItem
Relationship Type
Lookup
Refers To
OrderItem
OrderItemDetail
Represents the breakdown details of an order product. Revenue Cloud generates these records to capture pricing and quantity changes,
such as negative quantity reductions, early renewals, derived pricing or repricing during an amendment, and bundle or product attribute
reconfigurations. This object is available in API version 60.0 and later.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
1201
OrderItemDetailTransaction Management

===== PAGE 1216 =====

Fields
DetailsField
Type
string
BillingReference
Properties
Filter, Group, Nillable, Sort
Description
Reference to the original order item for which this amend or cancel record is created.
Type
dateTime
EffectiveFrom
Properties
Filter, Nillable, Sort
Description
The date when the transaction becomes effective.
Type
dateTime
EffectiveTo
Properties
Filter, Nillable, Sort
Description
The date when the transaction ends.
Type
int
LineNumber
Properties
Filter, Group, Nillable, Sort
Description
The line number of the detail record.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the record.
Type
currency
NetUnitPrice
Properties
Filter, Sort
1202
OrderItemDetailTransaction Management

===== PAGE 1217 =====

DetailsField
Description
The unit price of the item that's calculated after applying any discounts and before tax
calculation.
Type
reference
OrderItemId
Properties
Filter, Group, Sort
Description
The ID of the related order item.
This field is a relationship field.
Relationship Name
OrderItem
Relationship Type
Lookup
Refers To
OrderItem
Type
string
PriceWaterfallIdentifier
Properties
Filter, Group, Nillable, Sort
Description
The price waterfall identifier generated by Salesforce Pricing that's associated with the pricing
of the detail record.
Type
double
Quantity
Properties
Filter, Sort
Description
The quantity specified for the item in the detail record.
Type
date
ReferenceDate
Properties
Filter, Group, Nillable, Sort
Description
The reference date of the item. For example, the start date of the subscription that's associated
with the detail record.
1203
OrderItemDetailTransaction Management

===== PAGE 1218 =====

DetailsField
Type
string
ReferenceNumber
Properties
Filter, Group, Nillable, Sort
Description
The reference number of the item. For example, the order number that's associated with the
detail record.
Type
currency
TotalLineAmount
Properties
Filter, Sort
Description
The net total price of the order product, before price adjustments, inclusive of quantity and
subscription term.
Type
currency
TotalPrice
Properties
Filter, Sort
Description
The total price of the item in the detail record that's calculated using the quantity, net unit
price, and after applying the pricing terms.
Type
currency
UnitPrice
Properties
Filter, Sort
Description
The unit price of the item before any discounts or tax calculation.
OrderItemRateAdjustment
Represents the negotiated rate adjustment for an order product. This object is available in API version 62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
1204
OrderItemRateAdjustmentTransaction Management

===== PAGE 1219 =====

Special Access Rules
This object is available with Revenue Cloud.
Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the type of rate adjustment.
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
The value of the adjustment.
Type
double
LowerBound
Properties
Create, Filter, Sort, Update
Description
The minimum quantity for the adjustment to be applicable.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the order item rate adjustment.
Type
reference
OrderItemRateCardEntryId
1205
OrderItemRateAdjustmentTransaction Management

===== PAGE 1220 =====

DetailsField
Properties
Create, Filter, Group, Sort
Description
The parent order item rate card entry associated with the order item rate adjustment.
This field is a relationship field.
Relationship Name
OrderItemRateCardEntry
Relationship Type
Master-detail
Refers To
OrderItemRateCardEntry (the master object)
Type
double
UpperBound
Properties
Create, Filter, Nillable, Sort, Update
Description
The quantity below which the adjustment must be applicable. For example, if you want the
adjustment to be applicable when the quantity is 99 or less, set this value to 100.
OrderItemRateCardEntry
Represents the catalog and negotiated rates of a usage metric associated with an order item that's used to charge overage consumption.
This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
Special Access Rules
This object is available with Revenue Cloud.
1206
OrderItemRateCardEntryTransaction Management

===== PAGE 1221 =====

Fields
DetailsField
Type
boolean
IsChosenRate
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this rate is the chosen rate for the associated binding target and usage
resource (true) or not (false). The default value is false. Available in API version 64.0
and later.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
An auto-generated number assigned to the order item rate card entry record.
Type
double
NegotiatedRate
Properties
Create, Filter, Nillable, Sort, Update
Description
The base negotiated rate used to charge overage consumption.
Type
reference
OrderItemId
Properties
Create, Filter, Group, Sort
Description
The parent order item associated with the order item rate card entry.
This field is a relationship field.
Relationship Name
OrderItem
Relationship Type
Master-detail
Refers To
OrderItem (the master object)
Type
reference
RateCardEntryId
1207
OrderItemRateCardEntryTransaction Management

===== PAGE 1222 =====

DetailsField
Properties
Create, Filter, Group, Sort
Description
The rate card entry containing catalog rates that's associated with the order item rate card
entry.
This field is a relationship field.
Relationship Name
RateCardEntry
Refers To
RateCardEntry
Type
reference
RateCardId
Properties
Filter, Group, Nillable, Sort
Description
The rate card associated with the order item rate card entry.
This field is a relationship field.
Relationship Name
RateCard
Refers To
RateCard
Type
reference
RateUnitOfMeasureId
Properties
Filter, Group, Nillable, Sort
Description
The standard unit of measure containing the unit for the negotiated rate that's associated
with the order item rate card entry.
This field is a relationship field.
Relationship Name
RateUnitOfMeasure
Refers To
UnitOfMeasure
Type
reference
UsageResourceId
Properties
Filter, Group, Nillable, Sort
1208
OrderItemRateCardEntryTransaction Management

===== PAGE 1223 =====

DetailsField
Description
The usage resource associated with the order item rate card entry.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
OrderItemUsageRsrcGrant
Represents the negotiated grants for the usage resource that's associated with the usage product added in the order item. This object
is available in API version 65.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
Fields
DetailsField
Type
double
GrantQuantity
Properties
Create, Filter, Nillable, Sort, Update
Description
The granted or negotiated quantity of a usage resource associated with the usage product.
Type
picklist
GrantType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the type of model that defines how the usage resource is consumed.
Valid values are:
• Commit
• Grant
1209
OrderItemUsageRsrcGrantTransaction Management

===== PAGE 1224 =====

DetailsField
The default value is Grant.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The auto-generated identifier for the order item usage resource grant record. For example,
OIURG-00004 or OIURG-4567.
Type
reference
OrderItemId
Properties
Create, Filter, Group, Sort
Description
The order item associated with the usage product.
This field is a relationship field.
Relationship Name
OrderItem
Relationship Type
Master-detail
Refers To
OrderItem (the master object)
Type
reference
ProductUsageGrantId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product usage grant associated with the order item.
This field is a relationship field.
Relationship Name
ProductUsageGrant
Refers To
ProductUsageGrant
Type
reference
TokenResourceId
Properties
Create, Filter, Group, Nillable, Sort, Update
1210
OrderItemUsageRsrcGrantTransaction Management

===== PAGE 1225 =====

DetailsField
Description
The usage resource of category Token associated with the usage resource related to the
usage product added in the order item.
This field is a relationship field.
Relationship Name
TokenResource
Refers To
UsageResource
Type
reference
UsageGrantRefreshPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage grant refresh policy associated with the usage resource related to the usage
product added in the order item.
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
The usage grant rollover policy associated with the usage resource related to the usage
product added in the order item.
This field is a relationship field.
Relationship Name
UsageGrantRolloverPolicy
Refers To
UsageGrantRolloverPolicy
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource associated with the usage product that's added in the order item.
1211
OrderItemUsageRsrcGrantTransaction Management

===== PAGE 1226 =====

DetailsField
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Type
int
ValidityPeriodTerm
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The duration for which the usage resource grant is valid, when used with the validity period
units.
Type
picklist
ValidityPeriodUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The length of a validity period for the usage resource grant, when used with the validity
period term.
Valid values are:
• Month
• None
• Year
OrderItemUsageRsrcPlcy
Represents the policies that are used for the usage resource that's associated with the usage product added in the order item. This object
is available in API version 65.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
1212
OrderItemUsageRsrcPlcyTransaction Management

===== PAGE 1227 =====

Fields
DetailsField
Type
picklist
DrawdownOrder
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the order that's used to debit consumption of entitlements related to the usage
resource from the usage entitlement bucket.
Valid values are:
• ExpiringFirst
• GrantedFirst
• GrantedLast
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
An auto-generated number assigned to the order item for usage product grant record. For
example, OIURG-4567
Type
reference
OrderItemId
Properties
Create, Filter, Group, Sort
Description
The order item associated with the usage product.
This field is a relationship field.
Relationship Name
OrderItem
Relationship Type
Master-detail
Refers To
OrderItem (the master object)
Type
reference
ProductUsageResourcePolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
1213
OrderItemUsageRsrcPlcyTransaction Management

===== PAGE 1228 =====

DetailsField
Description
The product usage resource policy associated with the usage resource related to the usage
product added in the order item.
This field is a relationship field.
Relationship Name
ProductUsageResourcePolicy
Refers To
ProductUsageResourcePolicy
Type
reference
RatingFrequencyPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The rating frequency policy associated with the usage resource related to the usage product
added in the order item.
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
The usage aggregation policy associated with the usage resource related to the usage product
added in the order item.
This field is a relationship field.
Relationship Name
UsageAggregationPolicy
Refers To
UsageResourceBillingPolicy
Type
reference
UsageCommitmentPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
1214
OrderItemUsageRsrcPlcyTransaction Management

===== PAGE 1229 =====

DetailsField
Description
The usage commitment policy associated with the usage resource related to the usage
product added in the order item.
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
The usage overage policy associated with the usage resource related to the usage product
added in the order item.
This field is a relationship field.
Relationship Name
UsageOveragePolicy
Refers To
UsageOveragePolicy
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource associated with the usage product that's added in the order item.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
SalesTransactionType
Represents the type of the sales transaction. This object is available in API version 61.0 and later.
1215
SalesTransactionTypeTransaction Management

===== PAGE 1230 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
Fields
DetailsField
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
the user might have only accessed this record or list view but not viewed it directly.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the sales transaction type.
QuoteAction
Indicates the type of sales transaction that’s being quoted; for example, a renewal sale. This object is available in API version 59.0 and
later.
If a quote doesn't have a quote action, Salesforce treats it as a quote of the Add  type. When such a quote is used to create an order,
Salesforce automatically creates an order action of the Add  type.
1216
QuoteActionTransaction Management

===== PAGE 1231 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Special Access Rules
This object is available in orgs with Revenue Cloud. It’s also available in Industries Automotive and Industries Field Service.
Fields
DetailsField
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
ISO code of the currency. Use only one of the valid alphabetic, three-letter currency ISO codes
defined by the ISO 4217 standard, such as USD, GBP, or JPY. Must be unique within your
organization. Label is Currency ISO Code.
The default value is USD.
See Supported Currencies (ICU) for a list of currency codes Salesforce supports. This field is
available in Revenue Cloud in API version 66.0 and later.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The timestamp when the current user last accessed this record indirectly, for example, through
a list view or related record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The timestamp when the current user last viewed this record or list view. If this value is null,
the user accessed this record or list view indirectly, but didn’t view it.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
1217
QuoteActionTransaction Management

===== PAGE 1232 =====

DetailsField
Description
The name given to the quote action.
Type
reference
QuoteId
Properties
Create, Filter, Group, Sort
Description
The quote related to this quote action.
This field is a relationship field.
Relationship Name
Quote
Relationship Type
Lookup
Refers To
Quote
Type
reference
SourceAssetId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The asset changed by this sales transaction. For example, if the quote action is a quantity
amendment, this field contains the ID of the asset that’s amended.
This field is a relationship field.
Relationship Name
SourceAsset
Relationship Type
Lookup
Refers To
Asset
Type
picklist
Subtype
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The subtype of the action on the quote line item.
Valid values are:
• DowngradeFrom—Available in API version 66.0 and later.
1218
QuoteActionTransaction Management

===== PAGE 1233 =====

DetailsField
• DowngradeTo—Available in API version 66.0 and later.
• FieldAmendment
• Rollback
• StartDateAdjustment
• SwapIn—Available in API version 66.0 and later.
• SwapOut—Available in API version 66.0 and later.
• TransferFrom
• TransferTo
• UpgradeFrom—Available in API version 66.0 and later.
• UpgradeTo—Available in API version 66.0 and later.
This field is available with Revenue Cloud in API version 64.0 and later.
Type
picklist
Type
Properties
Create, Filter, Group, Restricted picklist, Sort
Description
The type of sales transaction that the related quote is for.
Valid values are:
• Add
• Amend
• Association—Available in API version 66.0 and later.
• Cancel
• No Change
• Renew
• Transfer—Available with Revenue Cloud in API version 65.0 and later.
QuoteLineDetail
Represents the breakdown details of a quote line item. Revenue Cloud generates these records to capture pricing and quantity changes,
such as negative quantity reductions, early renewals, derived pricing or repricing during an amendment, and bundle or product attribute
reconfigurations. This object is available in API version 60.0 and later.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
1219
QuoteLineDetailTransaction Management

===== PAGE 1234 =====

Fields
DetailsField
Type
string
BillingReference
Properties
Filter, Group, Nillable, Sort
Description
Reference to the original order item for which this amend or cancel record is created.
Type
dateTime
EffectiveFrom
Properties
Filter, Nillable, Sort
Description
The date when the transaction becomes effective.
Type
dateTime
EffectiveTo
Properties
Filter, Nillable, Sort
Description
The date when the transaction ends.
Type
int
LineNumber
Properties
Filter, Group, Nillable, Sort
Description
The line number of the detail record.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the record.
Type
currency
NetUnitPrice
Properties
Filter, Sort
1220
QuoteLineDetailTransaction Management

===== PAGE 1235 =====

DetailsField
Description
The unit price of the item that's calculated after applying any discounts and before tax
calculation.
Type
string
PriceWaterfallIdentifier
Properties
Filter, Group, Nillable, Sort
Description
The price waterfall identifier generated by Salesforce Pricing that's associated with the pricing
of the detail record.
Type
double
Quantity
Properties
Filter, Sort
Description
The quantity specified for the item in the detail record.
Type
reference
QuoteLineItemId
Properties
Filter, Group, Sort
Description
The ID of the related quote line.
This field is a relationship field.
Relationship Name
QuoteLineItem
Relationship Type
Lookup
Refers To
QuoteLineItem
Type
date
ReferenceDate
Properties
Filter, Group, Nillable, Sort
Description
The reference date of the item. For example, the start date of the subscription that's associated
with the detail record.
1221
QuoteLineDetailTransaction Management

===== PAGE 1236 =====

DetailsField
Type
string
ReferenceNumber
Properties
Filter, Group, Nillable, Sort
Description
The reference number of the item. For example, the order number that's associated with the
detail record.
Type
currency
TotalLineAmount
Properties
Filter, Sort
Description
The net total price of the order product, before price adjustments, inclusive of quantity and
the subscription term.
Type
currency
TotalPrice
Properties
Filter, Sort
Description
The total price of the item in the detail record that's calculated using the quantity, net unit
price, and after applying the pricing terms.
Type
currency
UnitPrice
Properties
Filter, Sort
Description
The unit price of the item before any discounts or tax calculation.
QuoteLineGroup
Stores the group information for line items in a quote. It also stores the aggregated line field information (subtotal). It contains a
parent-child relationship to quote. This object is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
1222
QuoteLineGroupTransaction Management

===== PAGE 1237 =====

Fields
DetailsField
Type
string
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The description of the group.
Type
percent
Discount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional discount percentage, specified by the sales representative at the group level.
Type
currency
DiscountAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional discount amount, specified by the sales representative at the group level.
Type
date
EndDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The end date of the group ramp segment.
Type
boolean
IsRamped
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the group is a group ramp segment, which is a period in a group ramp
deal with specific prices and volume.
The default value is false.
Type
percent
Margin
1223
QuoteLineGroupTransaction Management

===== PAGE 1238 =====

DetailsField
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin percentage, specified by the sales representative at the group level.
Type
currency
MarginAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin amount, specified by the sales representative at the group level. This
amount can also be considered as the summary margin amount calculated by subtracting
the total cost from the summary subtotal.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the group.
Type
reference
ParentQuoteLineGroupId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the parent group for a nested quote line group.
This field is a relationship field.
Relationship Name
ParentQuoteLineGroup
Refers To
QuoteLineGroup
Type
reference
QuoteId
Properties
Create, Filter, Group, Sort
Description
The ID of the related quote.
This field is a relationship field.
1224
QuoteLineGroupTransaction Management

===== PAGE 1239 =====

DetailsField
Relationship Name
Quote
Relationship Type
Master-detail
Refers To
Quote (the master object)
Type
picklist
SegmentType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The duration type of the segment.
Possible values are:
• Custom
• Yearly
Type
int
SortOrder
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Type
date
StartDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The start date of the group ramp segment.
Type
currency
SummarySubtotal
Properties
Create, Filter, Nillable, Sort, Update
Description
The aggregated subtotal amount of nested group lines.
Type
currency
SummaryTotalAmount
Properties
Create, Filter, Nillable, Sort, Update
1225
QuoteLineGroupTransaction Management

===== PAGE 1240 =====

DetailsField
Description
The aggregated total amount of nested group lines before any discounts are applied.
Type
percent
TotalAdjustment
Properties
Filter, Nillable, Sort
Description
The total discount percentage applied at the group level. This percentage is calculated by
using the formula: (Summary Total Amount - Summary Subtotal) / Summary Total Amount.
Type
currency
TotalAdjustmentAmount
Properties
Filter, Nillable, Sort
Description
The total discount amount at the group level. This amount is calculated by subtracting the
summary subtotal from the summary total amount.
Type
currency
TotalCost
Properties
Filter, Nillable, Sort
Description
The aggregated total cost of nested group lines.
Type
percent
TotalMargin
Properties
Filter, Nillable, Sort
Description
The summary margin percentage at the line item level. This percentage is calculated by using
the formula: (Summary Subtotal - Total Cost) / Summary Subtotal.
Type
currency
TotalMarginAmount
Properties
Filter, Nillable, Sort
Description
The summary margin amount calculated at the group level.
1226
QuoteLineGroupTransaction Management

===== PAGE 1241 =====

DetailsField
Type
picklist
Type
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type of quote line group.
Possible values are:
• AssetDowngrade
• AssetSwap
• AssetUpgrade
• CPQQuoteGroup—CPQ Line Grouping
• RampScheduleGroup
The default value is CPQQuoteGroup.
QuoteLineItemAttribute
Represents a virtual object that stores an attribute specified for a quote line item. This object is available in API version 59.0 and later.
Note:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain terms
to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), query(), retrieve(), update(), upsert()
Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
Fields
DetailsField
Type
reference
AttributeDefinitionId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the attribute definition for this quote line item attribute.
This field is a relationship field.
1227
QuoteLineItemAttributeTransaction Management

===== PAGE 1242 =====

DetailsField
Relationship Name
AttributeDefinition
Refers To
AttributeDefinition
Type
string
AttributeName
Properties
Filter, Group, idLookup, Nillable, Sort
Description
The name of the quote line item attribute.
Type
reference
AttributePicklistValueId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the attribute picklist value if the attribute is a picklist type.
This field is a relationship field.
Relationship Name
AttributePicklistValue
Refers To
AttributePicklistValue
Type
string
AttributeValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The value of the quote line item attribute. For example 5-TB storage.
You can use this field to filter records only if the DataType value in the related
AttributeDefinitionId record is Text. If the DataType value is Picklist, use
the value in the AttributePicklistValueId field for filtering. You can’t use this
field to filter records if the DataType value is Checkbox, Currency, Date, Datetime,
Multipicklist, Number, or Percent.
Type
string
ExternalId
Properties
Create, Filter, Group, Nillable, Sort, Update
1228
QuoteLineItemAttributeTransaction Management

===== PAGE 1243 =====

DetailsField
Description
An auto-generated ID of the attribute record saved in an external system, such as an HBase
database.
Type
boolean
IsPriceImpacting
Properties
Defaulted on create, Filter, Group, Sort
Description
The pricing impacting the status of the attribute.
The default value is false.
Type
reference
QuoteLineItemId
Properties
Create, Filter, Group, Sort
Description
The associated parent quote line item.
This field is a relationship field.
Relationship Name
QuoteLineItem
Relationship Type
Master-detail
Refers To
QuoteLineItem (the master object)
Usage
This object doesn’t support custom fields, validation rules, or triggers. In SOQL queries, you can filter records by using Id  and
AttributeDefinition. You can’t use AttributeValue  in the WHERE clause.
QuotLineItmUseRsrcGrant
Represents the negotiated grants for the usage resource that's associated with the usage product added in the quote line item. This
object is available in API version 65.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
1229
QuotLineItmUseRsrcGrantTransaction Management

===== PAGE 1244 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), update(), upsert()
Fields
DetailsField
Type
double
GrantQuantity
Properties
Create, Filter, Nillable, Sort, Update
Description
The granted or negotiated quantity of a usage resource associated with the usage product.
Type
picklist
GrantType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the type of model that defines how the usage resource is consumed.
Valid values are:
• Commit
• Grant
The default value is Grant.
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
1230
QuotLineItmUseRsrcGrantTransaction Management

===== PAGE 1245 =====

DetailsField
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The auto-generated identifier for the quote line item usage resource grant record. For example,
QLIURG-00004 or QLIURG-4567.
Type
reference
ProductUsageGrantId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product usage grant associated with the quote line item.
This field is a relationship field.
Relationship Name
ProductUsageGrant
Refers To
ProductUsageGrant
Type
reference
QuoteLineItemId
Properties
Create, Filter, Group, Sort
Description
The quote line item associated with the usage product.
This field is a relationship field.
Relationship Name
QuoteLineItem
Relationship Type
Master-detail
Refers To
QuoteLineItem (the master object)
Type
reference
TokenResourceId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage resource of category Token associated with the usage resource related to the
usage product added in the order item.
This field is a relationship field.
1231
QuotLineItmUseRsrcGrantTransaction Management

===== PAGE 1246 =====

DetailsField
Relationship Name
TokenResource
Refers To
UsageResource
Type
reference
UsageGrantRefreshPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage grant refresh policy associated with the usage resource related to the usage
product added in the quote line item.
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
The usage grant rollover policy associated with the usage resource related to the usage
product added in the quote line item.
This field is a relationship field.
Relationship Name
UsageGrantRolloverPolicy
Refers To
UsageGrantRolloverPolicy
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource associated with the usage product that's added as the quote line item.
This field is a relationship field.
Relationship Name
UsageResource
1232
QuotLineItmUseRsrcGrantTransaction Management

===== PAGE 1247 =====

DetailsField
Refers To
UsageResource
Type
int
ValidityPeriodTerm
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The duration for which the usage resource grant is valid, when used with the validity period
units.
Type
picklist
ValidityPeriodUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The length of a validity period for the usage resource grant, when used with the validity
period term.
Valid values are:
• Month
• None
• Year
QuotLineItmUsageRsrcPlcy
Represents the policies that are used for the usage resource that's associated with the usage product added in the quote line item. This
object is available in API version 65.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), update(), upsert()
Fields
DetailsField
Type
picklist
DrawdownOrder
1233
QuotLineItmUsageRsrcPlcyTransaction Management

===== PAGE 1248 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the order that's used to debit consumption of entitlements related to the usage
resource from the usage entitlement bucket.
Valid values are:
• ExpiringFirst
• GrantedFirst
• GrantedLast
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
The auto-generated identifier for the quote line item usage resource policy record. For
example, QLIURP-00004 or QLIURP-4567.
Type
reference
ProductUsageResourcePolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product usage resource policy associated with the quote line item.
This field is a relationship field.
Relationship Name
ProductUsageResourcePolicy
1234
QuotLineItmUsageRsrcPlcyTransaction Management

===== PAGE 1249 =====

DetailsField
Refers To
ProductUsageResourcePolicy
Type
reference
QuoteLineItemId
Properties
Create, Filter, Group, Sort
Description
The quote line item associated with the usage product.
This field is a relationship field.
Relationship Name
QuoteLineItem
Relationship Type
Master-detail
Refers To
QuoteLineItem (the master object)
Type
reference
RatingFrequencyPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The rating frequency policy associated with the usage resource related to the usage product
added in the quote line item.
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
The usage aggregation policy associated with the usage resource related to the usage product
added in the quote line item.
This field is a relationship field.
Relationship Name
UsageAggregationPolicy
1235
QuotLineItmUsageRsrcPlcyTransaction Management

===== PAGE 1250 =====

DetailsField
Refers To
UsageResourceBillingPolicy
Type
reference
UsageCommitmentPolicyId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The usage commitment policy associated with the usage resource related to the usage
product added in the quote line item.
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
The usage overage policy associated with the quote line item.
This field is a relationship field.
Relationship Name
UsageOveragePolicy
Refers To
UsageOveragePolicy
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
The usage resource associated with the usage product that's added in the quote line item.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
1236
QuotLineItmUsageRsrcPlcyTransaction Management

===== PAGE 1251 =====

QuoteLineRateAdjustment
Represents the negotiated rate adjustment for a quote line item. This object is available in API version 62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
Special Access Rules
This object is available with Revenue Cloud.
Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies the type of rate adjustment.
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
The value of the adjustment.
Type
double
LowerBound
Properties
Create, Filter, Sort, Update
Description
The minimum quantity for the adjustment to be applicable.
Type
string
Name
1237
QuoteLineRateAdjustmentTransaction Management

===== PAGE 1252 =====

DetailsField
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the quote line rate adjustment record.
Type
reference
QuoteLineRateCardEntryId
Properties
Create, Filter, Group, Sort
Description
The parent quote line rate card entry associated with the quote line rate adjustment.
This field is a relationship field.
Relationship Name
QuoteLineRateCardEntry
Relationship Type
Master-detail
Refers To
QuoteLineRateCardEntry (the master object)
Type
double
UpperBound
Properties
Create, Filter, Nillable, Sort, Update
Description
The quantity below which the adjustment must be applicable. For example, if you want the
adjustment to be applicable when the quantity is 99 or less, set this value to 100.
QuoteLineRateCardEntry
Represents the catalog and negotiated rates of a usage resource associated with a quote line item that's used to charge overage
consumption. This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), update(), upsert()
1238
QuoteLineRateCardEntryTransaction Management

===== PAGE 1253 =====

Fields
DetailsField
Type
boolean
IsChosenRate
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this rate is the chosen rate for the associated binding target and usage
resource (true) or not (false). The default value is false. Available in API version 64.0
and later.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
An auto-generated number assigned to the quote line rate card entry record.
Type
double
NegotiatedRate
Properties
Create, Filter, Nillable, Sort, Update
Description
The base negotiated rate used to charge overage consumption.
Type
reference
QuoteLineItemId
Properties
Create, Filter, Group, Sort
Description
The parent quote line item associated with the quote line rate card entry.
This field is a relationship field.
Relationship Name
QuoteLineItem
Relationship Type
Master-detail
Refers To
QuoteLineItem (the master object)
Type
reference
RateCardEntryId
1239
QuoteLineRateCardEntryTransaction Management

===== PAGE 1254 =====

DetailsField
Properties
Create, Filter, Group, Sort
Description
The rate card entry containing catalog rates that's associated with the quote line rate card
entry.
This field is a relationship field.
Relationship Name
RateCardEntry
Refers To
RateCardEntry
Type
reference
RateCardId
Properties
Filter, Group, Nillable, Sort
Description
The rate card associated with the quote line rate card entry.
This field is a relationship field.
Relationship Name
RateCard
Refers To
RateCard
Type
reference
RateUnitOfMeasureId
Properties
Filter, Group, Nillable, Sort
Description
The standard unit of measure containing the unit for the negotiated rate that's associated
with the quote line rate card entry.
This field is a relationship field.
Relationship Name
RateUnitOfMeasure
Refers To
UnitOfMeasure
Type
reference
UsageResourceId
Properties
Filter, Group, Nillable, Sort
1240
QuoteLineRateCardEntryTransaction Management

===== PAGE 1255 =====

DetailsField
Description
The usage resource associated with the quote line rate card entry.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Transaction Management Fields on Standard Objects
Transaction Management adds standard and custom fields to some standard Salesforce objects. These fields are available only in orgs
where Transaction Management is enabled.
Transaction Management Fields on Object State Definition
Standard and custom fields extend the standard Object State Definition object for use in Transaction Management to represent the
object state model for a particular status field for an entity.  This object is available in API version 60.0 and later.
Transaction Management Fields on Object State Transition
Standard and custom fields extend the standard Object State Transition object for use in Transaction Management to define the
valid transition between two statuses. This object is available in API version 60.0 and later.
Transaction Management Fields on Object State Value
Standard and custom fields extend the standard Object State Transition object for use in Transaction Management This object is
available in API version 60.0 and later.
Transaction Management Fields on Order
Standard and custom fields extend the standard Order object for use in Transaction Management.
Transaction Management Fields on Order Item
Standard and custom fields extend the standard Order Item object for use in Transaction Management.
Transaction Management Fields on Order Item Group
Standard and custom fields extend the standard Order Item Group object for use in Transaction Management.
Transaction Management Fields on Order Action
Standard and custom fields extend the standard Order Action object for use in Transaction Management. This object is available in
API version 55.0 and later.
Transaction Management Fields on Order Item Relationship
Standard and custom fields extend the standard Order Item Relationship object for use in Transaction Management. This object is
available in API version 58.0 and later.
Transaction Management Fields on Quote
Standard and custom fields extend the standard Quote object for use in Transaction Management to represent information about
quotes. This object is available in API version 60.0 and later.
Transaction Management Fields on Quote Line Group
Standard and custom fields extend the standard Quote Line Group object for use in Transaction Management.
1241
Transaction Management Fields on Standard ObjectsTransaction Management

===== PAGE 1256 =====

Transaction Management Fields on Quote Line Item
Standard and custom fields extend the standard Quote Line Item object for use in Transaction Management to represent information
about line items in a quote. This object is available in API version 60.0 and later.
Transaction Management Fields on Quote Document
Standard and custom fields extend the standard Quote Document object for use in Transaction Management to represent information
about quote documents. This object is available in API version 61.0 and later.
Transaction Management Fields on Object State Definition
Standard and custom fields extend the standard Object State Definition object for use in Transaction Management to represent the
object state model for a particular status field for an entity.  This object is available in API version 60.0 and later.
Fields
DetailsField
Type
string
AppUsageType
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
This field indicates under which AppUsageType the transition applies to. For example,
ObjectStateDefinition associated with “Revenue Lifecycle Management” AppUsageType will
apply to quotes, assets, or orders associated with “Revenue Lifecycle Management”.
Transaction Management Fields on Object State Transition
Standard and custom fields extend the standard Object State Transition object for use in Transaction Management to define the valid
transition between two statuses. This object is available in API version 60.0 and later.
Fields
DetailsField
Type
reference
CustomPermissionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the associated custom permission.
This field is a relationship field.
Relationship Name
CustomPermission
1242
Transaction Management Fields on Object State DefinitionTransaction Management

===== PAGE 1257 =====

DetailsField
Relationship Type
Lookup
Refers To
CustomPermission
Transaction Management Fields on Object State Value
Standard and custom fields extend the standard Object State Transition object for use in Transaction Management This object is available
in API version 60.0 and later.
Fields
DetailsField
Type
reference
CustomPermissionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the associated custom permission.
This field is a relationship field.
Relationship Name
CustomPermission
Relationship Type
Lookup
Refers To
CustomPermission
Transaction Management Fields on Order
Standard and custom fields extend the standard Order object for use in Transaction Management.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Order for fields on the Salesforce platform object.
1243
Transaction Management Fields on Object State ValueTransaction Management

===== PAGE 1258 =====

Fields
DetailsField
Type
picklist
AdjustmentDistributionLogic
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies how the overall discount amount distributes among all the order line items that
have prices associated with them.
The amount distributed is either the value specified in the AppliedDiscountAmount
field or the difference between the values in the calculated TotalAmount  and the
user-specified TotalAmountOverride  fields.
Valid values are:
• Equal—Distributes the discount amount equally among all the order items.
• Proportionate—Distributes the discount amount in proportion to the
ListPriceTotal  values of the order items.
Available in API version 65.0 and later.
Type
percent
AppliedDiscount
Properties
Create, Filter, Nillable, Sort, Update
Description
The discount amount that’s distributed among all the order items that have prices associated
with them. This amount is distributed based on the logic specified in the
AdjustmentDistributionLogic  field. Available in API version 65.0 and later.
Type
currency
AppliedDiscountAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The percent discount applied to each order item. Available in API version 65.0 and later.
Type
picklist
CalculationStatus
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The status of the price and tax calculations for the order.
Valid values are:
1244
Transaction Management Fields on OrderTransaction Management

===== PAGE 1259 =====

DetailsField
• CompletedWithPricing—Indicates that pricing is complete and tax will now be
calculated.
• CompletedWithTax—Indicates that pricing and tax calculation are complete.
• CompletedWithoutPricing—Indicates that pricing and tax calculation were
skipped. For a sales rep, this value appears as Unknown  on the order page.
• ConfigurationFailed—Indicates that configuration failed. Available in API
version 62.0
• ConfigurationInProgress—Indicates that the configuration is in progress.
Available in API version 62.0
• GroupRampConfigurationFailed—Indicates that the checks for group ramps
have failed. Available in API version 65.0 and later.
• OrderRequestFailed—Indicates that the requested order changes weren’t saved.
Available in API version 62.0
• OrderRequestPartiallySaved—Indicates that the requested order changes
were partially saved. Available in API version 62.0
• PriceCalculationFailed—Indicates that pricing failed.
• ReconciliationFailed—Indicates that the arrangement of order data failed.
Available in API version 62.0
• ReconciliationInProgress—Indicates that the arrangement of data is in
progress. For a sales rep, this value appears as Saving  on the order page. Available in
API version 62.0
• SaveFailedOrIncomplete—Indicates that the recent changes to the order
weren’t saved. For a sales rep, this value appears as Some Records Weren’t
Saved  on the order page.
• TaxCalculationFailed—Indicates that pricing is complete but tax calculation
failed.
• TaxCalculationWaiting—Indicates that pricing is complete and a request sent
to the tax engine, but tax calculation isn’t complete.
This read-only field is available in API version 61.0 and later.
Type
percent
DiscountPercent
Properties
Filter, Nillable, Sort
Description
The percentage of discount applied to the order. The discount percent calculation is
((TotalRoundedLineAmount - TotalAmount) / TotalRoundedLineAmount) * 100. Available
in API version 60.0 and later.
Type
reference
FulfillmentPlanId
1245
Transaction Management Fields on OrderTransaction Management

===== PAGE 1260 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The unique ID of the fulfillment plan associated with the order.
This field is a relationship field.
This field is available only in orgs where Dynamic Revenue Orchestrator is enabled. Available
in API version 60.0 and later.
Relationship Name
FulfillmentPlan
Relationship Type
Lookup
Refers To
FulfillmentPlan
Type
dateTime
LastPricedDate
Properties
Filter, Nillable, Sort
Description
The date when the order price was last calculated. Available in API version 60.0 and later.
Type
picklist
OrchestrationSbmsStatus
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The status of order submission for orchestration.
This field is available only in orgs where Dynamic Revenue Orchestrator is enabled.
Valid values are:
• Completed
• Rejected
• Submitted
This read-only field is available in API version 61.0 and later.
Type
picklist
OriginalActionType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Specifies the action that created the order.
1246
Transaction Management Fields on OrderTransaction Management

===== PAGE 1261 =====

DetailsField
Valid values are:
• Amend—Indicates that the order was created to amend assets.
• Cancel—Indicates that the order was created to cancel assets.
• Renew—Indicates that the order was created to renew assets.
• Transfer—Indicates that the order was created to transfer assets.
Available in API version 61.0 and later.
Type
reference
SalesTransactionTypeId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The foreign key to the Sales Transaction Type object. Available in API version 61.0 and later.
This field is a relationship field.
Relationship Name
SalesTransactionType
Relationship Type
Lookup
Refers To
SalesTransactionType
Type
currency
TotalAmountOverride
Properties
Create, Filter, Nillable, Sort, Update
Description
The value that the TotalAmount  field must be set to by applying overall discounts.
Transaction Management calculates the overall discount amount by finding the difference
between the value in the calculated TotalAmount  field and the value in this field. It then
uses the logic specified in the AdjustmentDistributionLogic  field to distribute
the discount amount among all the order items that have prices associated with them.
Available in API version 65.0 and later.
Type
currency
TotalRoundedLineAmount
Properties
Filter, Nillable, Sort
Description
The total amount of all line items in an order without pricing adjustments, such as discounts
or tax calculations. Available in API version 60.0 and later.
1247
Transaction Management Fields on OrderTransaction Management

===== PAGE 1262 =====

DetailsField
Type
picklist
TransactionType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the type of order being processed.
The valid value is:
• AdvancedConfigurator—Indicates that the order must be processed by using
the configuration rules and constraints set up in Constraint Rules Engine.
Available in API version 61.0 and later.
Type
picklist
ValidationResult
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether the order was configured and priced.
Orders can be activated only after they’re configured and priced.
Valid values are:
• MissingContributor—Indicates that the order contains a derived product but
not its pricing source.
• TransactionIncomplete—Indicates that the order wasn’t configured and priced.
Available in API version 61.0 and later.
Transaction Management Fields on Order Item
Standard and custom fields extend the standard Order Item object for use in Transaction Management.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Order Item for fields on the Salesforce platform object.
Fields
DetailsField
Type
string
CustomProductName
Properties
Create, Filter, Group, Nillable, Sort, Update
1248
Transaction Management Fields on Order ItemTransaction Management

===== PAGE 1263 =====

DetailsField
Description
The custom name of a product that's used to override the product name. The maximum
supported length is 80 characters. Available in API version 61.0 and later.
Type
percent
Discount
Properties
Create, Filter, Nillable, Sort, Update
Description
The manual discount percentage for the order item. Available in API version 60.0 and later.
Type
currency
DiscountAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The manual discount amount for the order item. Available in API version 60.0 and later.
Type
date
EffectiveGrantDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date on which the resources associated with the order item are granted.
Type
dateTime
EndDateTime
Properties
Filter, Nillable, Sort
Description
The end date and time of the order item, which is calculated by using the values in the
EndDate, EndTime, and ServiceEndTimeZone  fields.
If the EndTime  field doesn’t have a value, 23:59:59 is used for the calculation. If the
ServiceEndTimeZone  field doesn’t have a value, GMT is used for the calculation.
Available in API version 65.0 and later.
Type
double
EndQuantity
Properties
Filter, Nillable, Sort
1249
Transaction Management Fields on Order ItemTransaction Management

===== PAGE 1264 =====

DetailsField
Description
The revised quantity of the item after adjusting changes. The field is read-only. It’s calculated
by adding the Start Quantity and the Quantity fields. Available in API version 60.0 and later.
Type
time
EndTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The end time of the order item. Available in API version 65.0 and later.
Type
percent
Margin
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin percentage, specified by the sales representative at the line item level.
Available in API version 65.0 and later.
Type
currency
MarginAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin amount, specified by the sales representative at the line item level.
Available in API version 65.0 and later.
Type
currency
NetTotalPrice
Properties
Create, Filter, Nillable, Sort, Update
Description
The total price after applying all price adjustments. Available in API version 60.0 and later.
Type
reference
OrderItemGroupId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The order item group associated with the order item.
This field is a relationship field.
1250
Transaction Management Fields on Order ItemTransaction Management

===== PAGE 1265 =====

DetailsField
Relationship Name
OrderItemGroup
Refers To
OrderItemGroup
Type
percent
PartnerDiscountPercent
Properties
Create, Filter, Nillable, Sort, Update
Description
The discount percentage given to the partner for the order item. Available in API version
60.0 and later.
Type
currency
PartnerUnitPrice
Properties
Create, Filter, Nillable, Sort, Update
Description
The unit price after applying the discount given to the partner for the order item. Available
in API version 60.0 and later.
Type
string
PriceWaterfallIdentifier
Properties
Filter, Group, Nillable, Sort
Description
The price waterfall identifier generated by Salesforce Pricing that's associated with the pricing
of this order item record. Available in API version 60.0 and later.
Type
dateTime
ServiceDateTime
Properties
Filter, Nillable, Sort
Description
The start date and time of the order item, which is calculated by using the values in the
ServiceDate, ServiceTime, and ServiceEndTimeZone  fields.
If the ServiceTime  field doesn’t have a value, 00:00:00 is used for the calculation. If the
ServiceEndTimeZone  field doesn’t have a value, GMT is used for the calculation.
Available in API version 65.0 and later.
Type
picklist
ServiceEndTimeZone
1251
Transaction Management Fields on Order ItemTransaction Management

===== PAGE 1266 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The time zone for the order item's start and end dates, times, and datetimes. Available in API
version 65.0 and later.
Type
time
ServiceTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The start time of the order item. Available in API version 65.0 and later.
Type
double
StartQuantity
Properties
Create, Filter, Nillable, Sort, Update
Description
The quantity available on the order item start date. Available in API version 60.0 and later.
Type
picklist
Status
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The status of the order item. Available in API version 60.0 and later.
Type
int
SubscriptionTerm
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The number of terms in the subscription for the item.
The unit of the subscription term is stored in the PricingTermUnit field of this order item’s
related product selling model record (OrderItem.ProductSellingModel.PricingTermUnit).
Available in API version 61.0 and later.
Type
percent
TotalAdjustment
Properties
Filter, Nillable, Sort
1252
Transaction Management Fields on Order ItemTransaction Management

===== PAGE 1267 =====

DetailsField
Description
The total discount percentage applied at the line item level. This percentage is calculated
by using the formula: (Total Line Amount - Net Total Price) / Total Line Amount. Available in
API version 65.0 and later.
Type
currency
TotalCost
Properties
Filter, Nillable, Sort
Description
The total cost of all products sold in the order, calculated by multiplying the quantity by the
unit cost. Available in API version 65.0 and later.
Type
percent
TotalMargin
Properties
Filter, Nillable, Sort
Description
The effective margin percentage at the line item level. This percentage is calculated by using
the formula: (Net Total Price - Total Cost) / Net Total Price. Available in API version 65.0 and
later.
Type
currency
TotalMarginAmount
Properties
Filter, Nillable, Sort
Description
The effective margin amount at the line item level. This amount is calculated by subtracting
total cost from net total price. Available in API version 65.0 and later.
Type
currency
UnitCost
Properties
Create, Filter, Nillable, Sort, Update
Description
The unit cost of a product being sold as part of the order. Available in API version 65.0 and
later.
Type
picklist
ValidationResult
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
1253
Transaction Management Fields on Order ItemTransaction Management

===== PAGE 1268 =====

DetailsField
Description
Specifies whether the order item was configured and priced.
An order can be activated only after all its order items are configured and priced.
Valid value is:
• Warning—Indicates that the order item isn’t configured and priced.
Available in API version 60.0 and later.
Transaction Management Fields on Order Item Group
Standard and custom fields extend the standard Order Item Group object for use in Transaction Management.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Order Item Group for fields on the Salesforce platform
object.
Fields
DetailsField
Type
percent
Discount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional discount percentage, specified by the sales representative at the group level.
Available in API version 65.0 and later.
Type
currency
DiscountAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional discount amount, specified by the sales representative at the group level.
Available in API version 65.0 and later.
Type
date
EndDate
Properties
Create, Filter, Group, Nillable, Sort, Update
1254
Transaction Management Fields on Order Item GroupTransaction Management

===== PAGE 1269 =====

DetailsField
Description
The end date of the group.
If the IsRamped  field is set to true, Transaction Management sets this date as the end
date of all the line items in the group that have the Term-Defined product selling model.
Available in API version 65.0 and later.
Type
boolean
IsRamped
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the group is a group ramp segment, which is a period in a group ramp
schedule with specific products, quantities, and discounts.
You can use this field from Revenue Cloud only when the Ramp Deals for Groups in Quotes
and Orders setting is turned on.
The default value is false.
Available in API version 65.0 and later.
Type
percent
Margin
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin percentage, specified by the sales representative at the group level.
Available in API version 65.0 and later.
Type
currency
MarginAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin amount, specified by the sales representative at the group level. This
amount can also be considered as the summary margin amount calculated by subtracting
the total cost from the summary subtotal. Available in API version 65.0 and later.
Type
reference
ParentOrderItemGroupId
Properties
Create, Filter, Group, Nillable, Sort, Update
1255
Transaction Management Fields on Order Item GroupTransaction Management

===== PAGE 1270 =====

DetailsField
Description
The ID of the parent group for a nested quote line group. Available in API version 65.0 and
later.
This field is a relationship field.
Relationship Name
ParentOrderItemGroup
Refers To
OrderItemGroup
Type
picklist
SegmentType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The duration type of the segment. You can use this field from Revenue Cloud only when the
Ramp Deals for Groups in Quotes and Orders setting is turned on.
Valid values are:
• Custom
• Yearly
Available in API version 65.0 and later.
Type
date
StartDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The start date of the group.
If the IsRamped  field is set to true, Transaction Management sets this date as the start
date of all the line items in the group.
Available in API version 65.0 and later.
Type
currency
SummaryTotalAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The aggregated total amount of nested group lines before any discounts are applied. Available
in API version 65.0 and later.
1256
Transaction Management Fields on Order Item GroupTransaction Management

===== PAGE 1271 =====

DetailsField
Type
percent
TotalAdjustment
Properties
Filter, Nillable, Sort
Description
The total discount percentage applied at the group level. This percentage is calculated by
using the formula: (Summary Total Amount - Summary Subtotal) / Summary Total Amount.
Available in API version 65.0 and later.
Type
currency
TotalAdjustmentAmount
Properties
Filter, Nillable, Sort
Description
The total discount amount at the group level. This amount is calculated by subtracting the
summary subtotal from the summary total amount. Available in API version 65.0 and later.
Type
currency
TotalCost
Properties
Filter, Nillable, Sort
Description
The aggregated total cost of nested group lines. Available in API version 65.0 and later.
Type
percent
TotalMargin
Properties
Filter, Nillable, Sort
Description
The summary margin percentage at the line item level. This percentage is calculated by using
the formula: (Summary Subtotal - Total Cost) / Summary Subtotal. Available in API version
65.0 and later.
Type
currency
TotalMarginAmount
Properties
Filter, Nillable, Sort
Description
The summary margin amount calculated at the group level. Available in API version 65.0 and
later.
1257
Transaction Management Fields on Order Item GroupTransaction Management

===== PAGE 1272 =====

Transaction Management Fields on Order Action
Standard and custom fields extend the standard Order Action object for use in Transaction Management. This object is available in API
version 55.0 and later.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Order Action for fields on the Salesforce platform object.
Fields
DetailsField
Type
picklist
Type
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The business action that created the order product.
Valid values are:
• Add
• Amend
• Cancel
• No Change—A child product was added to the bundle, but the top-level product in
the bundle was otherwise unchanged.
• Renew
Transaction Management Fields on Order Item Relationship
Standard and custom fields extend the standard Order Item Relationship object for use in Transaction Management. This object is
available in API version 58.0 and later.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Order Item Relationship for fields on the Salesforce platform
object.
Fields
DetailsField
Type
reference
ProductRelatedComponentId
1258
Transaction Management Fields on Order ActionTransaction Management

===== PAGE 1273 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID of the product that is included in a product bundle, a set, or a product and an add-on.
This field is a relationship field.
Relationship Name
ProductRelatedComponent
Relationship Type
Lookup
Refers To
ProductRelatedComponent
Transaction Management Fields on Quote
Standard and custom fields extend the standard Quote object for use in Transaction Management to represent information about quotes.
This object is available in API version 60.0 and later.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Quote for fields on the Salesforce platform object.
Fields
DetailsField
Type
picklist
AdjustmentDistributionLogic
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies how the overall discount amount is distributed among all the quote line items that
have prices associated with them.
The amount distributed is either the value specified in the AppliedDiscountAmount
field or the difference between the values in the calculated TotalPrice  and the
user-specified TotalPriceOverride  fields.
Valid values are:
• Equal—Distributes the discount amount equally among all the quote line items.
• Proportionate—Distributes the discount amount in proportion to the
ListPriceTotal  values of the quote line items.
Available in API version 65.0 and later.
1259
Transaction Management Fields on QuoteTransaction Management

===== PAGE 1274 =====

DetailsField
Type
percent
AppliedDiscount
Properties
Create, Filter, Nillable, Sort, Update
Description
The percent discount applied to each quote line item. Available in API version 65.0 and later.
Type
currency
AppliedDiscountAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The discount amount that’s distributed among all the quote line items that have prices
associated with them. This amount is distributed based on the logic specified in the
AdjustmentDistributionLogic  field. Available in API version 65.0 and later.
Type
dateTime
LastPricedDate
Properties
Filter, Nillable, Sort
Description
The date when the quote is last priced.
Type
picklist
OriginalActionType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Specifies the action that created the quote.
Valid values are:
• Amend—Indicates that the quote was created to amend assets.
• Cancel—Indicates that the quote was created to cancel assets.
• Renew—Indicates that the quote was created to renew assets.
• Transfer—Indicates that the quote was created to transfer assets.
Available in API version 61.0 and later.
Type
reference
PartnerAccountId
Properties
Create, Filter, Group, Nillable, Sort, Update
1260
Transaction Management Fields on QuoteTransaction Management

===== PAGE 1275 =====

DetailsField
Description
ID of the related partner account.
This field is a relationship field.
Relationship Name
PartnerAccount
Relationship Type
Lookup
Refers To
Account
Type
currency
TotalPriceOverride
Properties
Create, Filter, Nillable, Sort, Update
Description
The value that the TotalPrice  field must be set to by applying overall discounts.
Transaction Management calculates the overall discount amount by finding the difference
between the value in the calculated TotalPrice  field and the value in this field. It then
uses the logic specified in the AdjustmentDistributionLogic  field to distribute
the discount amount among all the quote line items that have prices associated with them.
Available in API version 65.0 and later.
Type
currency
TotalPriceWithTax
Properties
Filter, Nillable, Sort
Description
The sum of TotalPrice  and TotalTaxAmount.
This field is available only when you turn on Add Estimated Tax to Quotes and Orders settings
and enable Revenue Cloud in your Revenue Cloud org.
Available in API version 64.0 and later.
Type
currency
TotalTaxAmount
Properties
Filter, Nillable, Sort
Description
The total amount of all taxes.
This field is available only when you turn on Add Estimated Tax to Quotes and Orders settings
and enable Revenue Cloud in your Revenue Cloud org.
Available in API version 64.0 and later.
1261
Transaction Management Fields on QuoteTransaction Management

===== PAGE 1276 =====

DetailsField
This field is a calculated field.
Type
picklist
TransactionType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the type of quote being processed.
Valid value is:
• AdvancedConfigurator—Indicates that the transaction must be processed by
using the configuration rules and constraints set up in Constraint Rules Engine.
Available in API version 62.0 and later.
Type
picklist
ValidationResult
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether the quote was configured and priced.
Quotes can be activated only after they’re configured and priced.
Valid values are:
• MissingContributor—Indicates that the quote contains a derived product but
not its pricing source.
• TransactionIncomplete—Indicates that the quote wasn’t configured and
priced.
Available in API version 61.0 and later.
Transaction Management Fields on Quote Line Group
Standard and custom fields extend the standard Quote Line Group object for use in Transaction Management.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Quote Line Group for fields on the Salesforce platform
object.
1262
Transaction Management Fields on Quote Line GroupTransaction Management

===== PAGE 1277 =====

Fields
DetailsField
Type
percent
Discount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional discount percentage, specified by the sales representative at the group level.
Available in API version 65.0 and later.
Type
currency
DiscountAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional discount amount, specified by the sales representative at the group level.
Available in API version 65.0 and later.
Type
date
EndDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The end date of the group.
If the IsRamped  field is set to true, Transaction Management sets this date as the end
date of all the line items in the group that have the Term-Defined product selling model.
Available in API version 65.0 and later.
Type
boolean
IsRamped
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the group is a group ramp segment, which is a period in a group ramp
schedule with specific products, quantities, and discounts.
You can use this field from Revenue Cloud only when the Ramp Deals for Groups in Quotes
and Orders setting is turned on.
The default value is false.
Available in API version 65.0 and later.
1263
Transaction Management Fields on Quote Line GroupTransaction Management

===== PAGE 1278 =====

DetailsField
Type
percent
Margin
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin percentage, specified by the sales representative at the group level.
Available in API version 65.0 and later.
Type
currency
MarginAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin amount, specified by the sales representative at the group level. This
amount can also be considered as the summary margin amount calculated by subtracting
the total cost from the summary subtotal. Available in API version 65.0 and later.
Type
reference
ParentQuoteLineGroupId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the parent group for a nested quote line group. Available in API version 65.0 and
later.
This field is a relationship field.
Relationship Name
ParentQuoteLineGroup
Refers To
QuoteLineGroup
Type
picklist
SegmentType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The duration type of the segment. You can use this field from Revenue Cloud only when the
Ramp Deals for Groups in Quotes and Orders setting is turned on.
Valid values are:
• Custom
• Yearly
Available in API version 65.0 and later.
1264
Transaction Management Fields on Quote Line GroupTransaction Management

===== PAGE 1279 =====

DetailsField
Type
date
StartDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The start date of the group.
If the IsRamped  field is set to true, Transaction Management sets this date as the start date
of all the line items in the group.
Available in API version 65.0 and later.
Type
currency
SummaryTotalAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
The aggregated total amount of nested group lines before any discounts are applied. Available
in API version 65.0 and later.
Type
percent
TotalAdjustment
Properties
Filter, Nillable, Sort
Description
The total discount percentage applied at the group level. This percentage is calculated by
using the formula: (Summary Total Amount - Summary Subtotal) / Summary Total Amount.
Available in API version 65.0 and later.
Type
currency
TotalAdjustmentAmount
Properties
Filter, Nillable, Sort
Description
The total discount amount at the group level. This amount is calculated by subtracting the
summary subtotal from the summary total amount. Available in API version 65.0 and later.
Type
currency
TotalCost
Properties
Filter, Nillable, Sort
Description
The aggregated total cost of nested group lines. Available in API version 65.0 and later.
1265
Transaction Management Fields on Quote Line GroupTransaction Management

===== PAGE 1280 =====

DetailsField
Type
percent
TotalMargin
Properties
Filter, Nillable, Sort
Description
The summary margin percentage at the line item level. This percentage is calculated by using
the formula: (Summary Subtotal - Total Cost) / Summary Subtotal. Available in API version
65.0 and later.
Type
currency
TotalMarginAmount
Properties
Filter, Nillable, Sort
Description
The summary margin amount calculated at the group level. Available in API version 65.0 and
later.
Transaction Management Fields on Quote Line Item
Standard and custom fields extend the standard Quote Line Item object for use in Transaction Management to represent information
about line items in a quote. This object is available in API version 60.0 and later.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Quote Line Item for fields on the Salesforce platform
object.
Fields
DetailsField
Type
currency
DiscountAmount
Properties
Create, Filter, Nillable, Sort, Update
Description
Specifies the fixed amount discount to apply to the quote line item.
Type
date
EffectiveGrantDate
Properties
Create, Filter, Group, Nillable, Sort, Update
1266
Transaction Management Fields on Quote Line ItemTransaction Management

===== PAGE 1281 =====

DetailsField
Description
The date on which the resources associated with the quote line item are granted.
Type
dateTime
EndDateTime
Properties
Filter, Nillable, Sort
Description
The end date and time of the quote line item, which is calculated by using the values in the
EndDate, EndTime, and StartEndTimeZone  fields.
If the EndTime  field doesn’t have a value, 23:59:59 is used for the calculation. If the
StartEndTimeZone  field doesn’t have a value, GMT is used for the calculation.
Available in API version 65.0 and later.
Type
double
EndQuantity
Properties
Filter, Nillable, Sort
Description
The quantity available on the quote line item end date. The field is read-only. It is calculated
by adding the Start Quantity and the existing Quantity fields.
Type
time
EndTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The end time of the quote line item. Available in API version 65.0 and later.
Type
percent
Margin
Properties
Create, Filter, Nillable, Sort, Update
Description
The optional margin percentage, specified by the sales representative at the line item level.
Available in API version 65.0 and later.
Type
currency
MarginAmount
Properties
Create, Filter, Nillable, Sort, Update
1267
Transaction Management Fields on Quote Line ItemTransaction Management

===== PAGE 1282 =====

DetailsField
Description
The optional margin amount, specified by the sales representative at the line item level.
Available in API version 65.0 and later.
Type
percent
PartnerDiscountPercent
Properties
Create, Filter, Nillable, Sort, Update
Description
The discount percentage given to the partner for the quote line.
Type
currency
PartnerUnitPrice
Properties
Create, Filter, Nillable, Sort, Update
Description
The unit price after discount given to the partner for the quote line.
Type
string
PriceWaterfallIdentifier
Properties
Filter, Group, Nillable, Sort
Description
The price waterfall identifier generated by Salesforce Pricing that's associated with the pricing
of the detail record.
Type
dateTime
StartDateTime
Properties
Filter, Nillable, Sort
Description
The start date and time of the quote line item, which is calculated by using the values in the
StartDate, StartTime, and StartEndTimeZone  fields.
If the StartTime  field doesn’t have a value, 00:00:00 is used for the calculation. If the
StartEndTimeZone  field doesn’t have a value, GMT is used for the calculation.
Available in API version 65.0 and later.
Type
picklist
StartEndTimeZone
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
1268
Transaction Management Fields on Quote Line ItemTransaction Management

===== PAGE 1283 =====

DetailsField
Description
The time zone for the quote line item's start and end dates, times, and datetimes. Available
in API version 65.0 and later.
Type
time
StartTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The start time of the quote line item. Available in API version 65.0 and later.
Type
double
StartQuantity
Properties
Create, Filter, Nillable, Sort
Description
The quantity available on the quote line item start date.
Type
percent
TotalAdjustment
Properties
Filter, Nillable, Sort
Description
The total discount percentage applied at the line item level. This percentage is calculated
by using the formula: (Total Line Amount - Net Total Price) / Total Line Amount. Available in
API version 65.0 and later.
Type
currency
TotalCost
Properties
Filter, Nillable, Sort
Description
The total cost of all products sold in the order, calculated by multiplying the quantity by the
unit cost. Available in API version 65.0 and later.
Type
percent
TotalMargin
Properties
Filter, Nillable, Sort
1269
Transaction Management Fields on Quote Line ItemTransaction Management

===== PAGE 1284 =====

DetailsField
Description
The effective margin percentage at the line item level. This percentage is calculated by using
the formula: (Net Total Price - Total Cost) / Net Total Price. Available in API version 65.0 and
later.
Type
currency
TotalMarginAmount
Properties
Filter, Nillable, Sort
Description
The effective margin amount at the line item level. This amount is calculated by subtracting
total cost from net total price. Available in API version 65.0 and later.
Type
currency
UnitCost
Properties
Create, Filter, Nillable, Sort, Update
Description
The unit cost of a product being sold as part of the order. Available in API version 65.0 and
later.
Type
picklist
ValidationResult
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether the quote line item is configured and priced.
A quote can be activated only after all its quote line items are configured and priced.
Valid value is:
• Warning—Indicates that the quote line item isn’t configured and priced.
Available in API version 60.0 and later.
Transaction Management Fields on Quote Document
Standard and custom fields extend the standard Quote Document object for use in Transaction Management to represent information
about quote documents. This object is available in API version 61.0 and later.
Special Access Rules
To view these fields, you must have the Revenue Cloud Advanced license. See Quote Document for fields on the Salesforce platform
object.
1270
Transaction Management Fields on Quote DocumentTransaction Management

===== PAGE 1285 =====

Fields
DetailsField
Type
String
Document Template
Properties
Create, Filter, Group, Nillable, Sort
Description
The template ID used for generating the quote document.
Type
Picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The status of the quote document.
Possible values are:
• Completed
• Failed
• Generating
• In Progress
• None
• Queued
The default value is None.
Transaction Management Tooling API Objects
Tooling API exposes metadata used in developer tooling that you can access through REST or SOAP. Tooling API’s SOQL capabilities for
many metadata types allow you to retrieve smaller pieces of metadata.
TransactionProcessingType
Represents the settings to configure the processing constraints for a request.. This object is available in API version 63.0 and later.
TransactionProcessingType
Represents the settings to configure the processing constraints for a request.. This object is available in API version 63.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Refer to the Usage section to learn more about creating Transaction Processing Type records based on your requirements. See the setup
details to specify the default rule engine on the Revenue Settings page.
1271
Transaction Management Tooling API ObjectsTransaction Management

===== PAGE 1286 =====

Supported SOAP API Calls
create(), describeSObjects(), query(), retrieve()
Supported REST API Methods
GET, HEAD, POST, Query
Fields
DetailsField
Type
string
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The description of the transaction processing configuration to help Salesforce admins with
configuration in their orgs.
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
Required. The unique name of the object in the API. This name can contain only underscores
and alphanumeric characters, and must be unique in your org. It must begin with a letter,
not include spaces, not end with an underscore, and not contain two consecutive underscores.
In managed packages, this field prevents naming conflicts on package installations. With
this field, a developer can change the object’s name in a managed package and the changes
are reflected in a subscriber’s organization. Label is Record Type Name.
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Nillable, Update
Description
The language of the TransactionProcessingType object.
Valid values are:
• da—Danish
• de—German
• en_US—English
• es—Spanish
• es_MX—Spanish (Mexico)
1272
TransactionProcessingTypeTransaction Management

===== PAGE 1287 =====

DetailsField
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
The label for the TransactionProcessingType object.
Type
string
PricingPreference
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether to execute the price calculation step for each sales transaction record.
Valid values are:
• Force—Reprices all lines.
• System—Performs a delta pricing request on the unprocessed lines when Delta Pricing
is enabled in the org.
• Skip—Skips the pricing request on all lines.
Available in API version 65.0 and later.
Type
string
RatingPreference
Properties
Description
Specifies whether catalog rates are fetched and saved during quote creation. Valid value is
Fetch. Use this value to retrieve and save catalog rates for usage resources associated with
1273
TransactionProcessingTypeTransaction Management

===== PAGE 1288 =====

DetailsField
each sales transaction record. If this value isn't specified, catalog rates aren't saved by default
when a quote line item is added to a quote.
Available in API version 66.0 and later if Rate Management is enabled.
Type
picklist
RuleEngine
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
The rule engine to be used for processing rules.
Valid values are:
• AdvancedConfigurator
• StandardConfigurator
Type
picklist
SaveType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Specifies how the transaction results are processed when saved for Salesforce administrators
to adjust the user experience as desired. Valid values are:
• Standard
• Large—Reserved for future use.
Type
picklist
TaxPreference
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether to execute or skip the tax calculation step for each sales transaction record.
Valid value is Skip. If this value isn't specified, then tax calculation request is performed by
default. Available in API version 65.0 and later.
Usage
Create transaction type records by calling this resource through a POST method.
/services/data/v66.0/tooling/sobjects/TransactionProcessingType
1274
TransactionProcessingTypeTransaction Management

===== PAGE 1289 =====

Here's a sample payload that specifies the rule engine to use and steps to skip for each sales transaction record.
{
"SaveType": "Standard",
"Description": "Setup for Transaction Processing Type",
"DeveloperName": "SkipPricingAndTaxStep",
"MasterLabel": "SkipPricingAndTaxStep",
"RuleEngine": "StandardConfigurator",
"PricingPreference": "Skip",
"TaxPreference": "Skip"
}
Here's a sample payload that specifies a value for rating preference and the steps to skip for each sales transaction record.
{
"SaveType": "Standard",
"Description": "Setup for Transaction Processing Type",
"DeveloperName": "SkipPricingAndTaxStep",
"MasterLabel": "SkipPricingAndTaxStep",
"RuleEngine": "StandardConfigurator",
"PricingPreference": "Skip",
"TaxPreference": "Skip",
"RatingPreference": "Fetch"
}
Transaction Management Platform Event
EDITIONS
Available in: Lightning
Experience
Available in all Salesforce
orgs where the admin
settings for products related
to the use case are enabled.
The Salesforce org must
have a Revenue Cloud or
Subscription Management
license.
Use the QuoteSaveEvent event to notify subscribers after saving of a quote is processed.
CreateAssetOrderEvent
Notifies subscribers that the process started by the
/actions/standard/createOrUpdateAssetFromOrder  or
/actions/standard/createOrUpdateAssetFromOrderItem request is
complete. If the process is successful, use this event to learn about the new assets. If the request
isn't successful, use this event to learn about the errors and how to fix them. This object is
available in API version 55.0 and later.
PlaceOrderCompletedEvent
Notifies subscribers of an order being created or updated by invoking the Place Order API or
the Place Sales Transaction API. This object is available in API version 63.0 and later.
QuoteSaveEvent
Notifies subscribers that the process started by the Place Quote or Place Sales Transaction API request is complete. If the process is
successful, use this event to learn about the updated quote. If the request isn't successful, use this event to learn about the errors
and how to fix them. This object is available in API version 60.0 and later.
QuoteToOrderCompletedEvent
Notifies subscribers when the /actions/standard/createOrderFromQuote  REST request is complete. If the request
is successful, use this event to learn about the Order record. If the request isn’t successful, use this event to learn about the errors
associated with the request. This object is available in API version 56.0 and later.
1275
Transaction Management Platform EventTransaction Management

===== PAGE 1290 =====

CreateAssetOrderEvent
Notifies subscribers that the process started by the /actions/standard/createOrUpdateAssetFromOrder  or
/actions/standard/createOrUpdateAssetFromOrderItem request is complete. If the process is successful, use this
event to learn about the new assets. If the request isn't successful, use this event to learn about the errors and how to fix them. This
object is available in API version 55.0 and later.
Supported Calls
describeSObjects()
Supported Subscribers
Supported?Subscriber
Apex Triggers
Flows
Processes
Pub/Sub API
Streaming API (CometD)
Subscription Channel
/event/CreateAssetOrderEvent
Event Delivery Allocation Enforced
No
Special Access Rules
This object is available if Subscription Management or Revenue Cloud is enabled in your org. Users must have Read access on this event
to receive or view event notifications.
Fields
DetailsField
Type
CreateAssetOrderDtlEvent on page 1279
AssetDetails
Properties
Nillable
Description
A list of AssetDetail records created as a result of a successful request.
1276
CreateAssetOrderEventTransaction Management

===== PAGE 1291 =====

DetailsField
Each AssetDetail contains an order item ID, asset ID, and IsSuccess flag. If the request failed,
the AssetDetail also contains an error code and error message.
Type
string
CorrelationIdentifier
Properties
Nillable
Description
Reserved for future use.
Type
string
EventUuid
Properties
Nillable
Description
A universally unique identifier (UUID) that identifies a platform event message.
Type
boolean
IsLastEvent
Properties
Defaulted on create
Description
Indicates whether this event is the final event in the request (true) or not (false). If
true, then there are no more events associated with the request. This field is populated
only in the final event in the request.
The default value is false.
This field is available in API version 62.0 and later.
Type
string
OrderIdentifier
Properties
Nillable
Description
The ID of the order associated with this event. Available with Revenue Cloud in API version
64.0 and later.
Type
string
ReplayId
Properties
Nillable
1277
CreateAssetOrderEventTransaction Management

===== PAGE 1292 =====

DetailsField
Description
Represents an ID value that is populated by the system and refers to the position of the event
in the event stream. Replay ID values aren’t guaranteed to be contiguous for consecutive
events. A subscriber can store a replay ID value and use it on resubscription to retrieve missed
events that are within the retention window.
Type
string
RequestIdentifier
Properties
Nillable
Description
Id of the request that triggered the event.
Example:  A user successfully runs a createOrUpdateAssetFromOrder  request on an order with two order items. The
published createAssetOrderEvent contains this information.
• RequestId: 0001
• AssetDetail
– OrderItemId: 802XX0000000001
– AssetId: 02iXX000000001
– IsSuccess: True
• AssetDetail
– OrderItemId: 802XX0000000001
– AssetId: 02iXX000000002
– IsSuccess: True
Example:  A user runs a createOrUpdateAssetFromOrder  request on an order with two order items, but doesn't have
Create access on assets. The request fails, and the published createAssetOrderEvent contains this information.
• RequestId: 0002
• AssetDetail
– OrderItemId: 802XX0000000001
– IsSuccess: False
– ErrorCode: INSUFFICIENT_ACCESS
– ErrorMessage: User doesn’t have Create Access to asset.
• AssetDetail
– OrderItemId: 802XX0000000001
– IsSuccess: False
– ErrorCode: INSUFFICIENT_ACCESS
– ErrorMessage: User doesn’t have Create Access to asset.
1278
CreateAssetOrderEventTransaction Management

===== PAGE 1293 =====

CreateAssetOrderDtlEvent
Contains information about an attempt to create or update an asset as a result of
/actions/standard/createOrUpdateAssetFromOrder. If the request was successful, the event shows information
about the asset. If the request failed, the event shows error information. This object is included in an CreateAssetOrderEvent
message. You can't subscribe to CreateAssetOrderDtlEvent  directly. This object is available in API version 55.0 and later.
CreateAssetOrderDtlEvent
Contains information about an attempt to create or update an asset as a result of
/actions/standard/createOrUpdateAssetFromOrder. If the request was successful, the event shows information
about the asset. If the request failed, the event shows error information. This object is included in an CreateAssetOrderEvent
message. You can't subscribe to CreateAssetOrderDtlEvent  directly. This object is available in API version 55.0 and later.
Supported Calls
describeSObjects()
Supported Subscribers
Supported?Subscriber
Apex Triggers
Flows
Processes
Pub/Sub API
Streaming API (CometD)
Subscription Channel
/event/CreateAssetOrderDtlEvent
Special Access Rules
This object is available if Revenue Cloud is installed in your org. Users must have Read access on this event to receive or view event
notifications.
Fields
DetailsField
Type
reference
AssetId
Properties
Nillable
1279
CreateAssetOrderEventTransaction Management

===== PAGE 1294 =====

DetailsField
Description
The ID of the asset that was created or updated.
This field is a relationship field.
Relationship Name
Asset
Relationship Type
Lookup
Refers To
Asset
Type
string
ErrorCode
Properties
Nillable
Description
Reference code for the type of error that occurred.
Type
string
ErrorMessage
Properties
Nillable
Description
Information about the error that occurred after the request was made.
Type
string
EventUuid
Properties
Nillable
Description
A universally unique identifier (UUID) that identifies a platform event message.
Type
boolean
IsSuccess
Properties
Defaulted on create
Description
Indicates whether the request to create the asset for the order item was successful (true) or
not (false).
The default value is false. Available in API version 61.0 and later.
1280
CreateAssetOrderEventTransaction Management

===== PAGE 1295 =====

DetailsField
Type
reference
OrderItemId
Properties
Description
The ID of the order item used in the request. Available in API version 61.0 and later.
This field is a relationship field.
Relationship Name
OrderItem
Relationship Type
Lookup
Refers To
OrderItem
Type
string
ReplayId
Properties
Nillable
Description
Represents an ID value that is populated by the system and refers to the position of the event
in the event stream. Replay ID values aren’t guaranteed to be contiguous for consecutive
events. A subscriber can store a replay ID value and use it on resubscription to retrieve missed
events that are within the retention window.
PlaceOrderCompletedEvent
Notifies subscribers of an order being created or updated by invoking the Place Order API or the Place Sales Transaction API. This object
is available in API version 63.0 and later.
Supported Calls
describeSObjects()
Supported Subscribers
Supported?Subscriber
Apex Triggers
Flows
Processes
Pub/Sub API
1281
PlaceOrderCompletedEventTransaction Management

===== PAGE 1296 =====

Supported?Subscriber
Streaming API (CometD)
Subscription Channel
/event/PlaceOrderCompletedEvent
Event Delivery Allocation Enforced
Yes
Fields
DetailsField
Type
string
AppUsageTypes
Properties
Nillable
Description
Tag that represents the application that's using the order and determines how an order is
processed. For example, the AppUsageTypes  field value for Revenue Cloud orders is
RevenueLifecycleManagement.
Type
string
CorrelationIdentifier
Properties
Nillable
Description
Reserved for future use.
Type
string
EventUuid
Properties
Nillable
Description
A universally unique identifier (UUID) that identifies a platform event message.
Type
boolean
HasErrors
Properties
Defaulted on create
1282
PlaceOrderCompletedEventTransaction Management

===== PAGE 1297 =====

DetailsField
Description
Indicates whether errors occurred when creating or updating the order (true) or not
(false).
The default value is false.
Type
reference
OrderId
Properties
Nillable
Description
ID of the order record.
This field is a relationship field.
Relationship Name
Order
Refers To
Order
Type
string
ReplayId
Properties
Nillable
Description
Represents an ID value that is populated by the system and refers to the position of the event
in the event stream. Replay ID values aren’t guaranteed to be contiguous for consecutive
events. A subscriber can store a replay ID value and use it on resubscription to retrieve missed
events that are within the retention window.
Type
string
RequestIdentifier
Properties
Nillable
Description
ID of the request that triggered the event.
QuoteSaveEvent
Notifies subscribers that the process started by the Place Quote or Place Sales Transaction API request is complete. If the process is
successful, use this event to learn about the updated quote. If the request isn't successful, use this event to learn about the errors and
how to fix them. This object is available in API version 60.0 and later.
1283
QuoteSaveEventTransaction Management

===== PAGE 1298 =====

Supported Calls
describeSObjects()
Supported Subscribers
Supported?Subscriber
Apex Triggers
Flows
Processes
Streaming API (CometD)
Streaming API Subscription Channel
/event/QuoteSaveEvent
Special Access Rules
This object is available in orgs with Subscription Management or Revenue Cloud.
Fields
DetailsField
Type
string
CorrelationIdentifier
Properties
Nillable
Description
Reserved for future use.
Type
string
EventUuid
Properties
Nillable
Description
A universally unique identifier (UUID) that identifies a platform event message.
Type
boolean
HasErrors
Properties
Defaulted on create
1284
QuoteSaveEventTransaction Management

===== PAGE 1299 =====

DetailsField
Description
The default value is false.
Possible values are:
• false
• true
Type
reference
QuoteId
Properties
Nillable
Description
The ID of the quote associated with this event. This field is a relationship field.
Type
string
ReplayId
Properties
Nillable
Description
Represents an ID value that is populated by the system and refers to the position of the event
in the event stream. Replay ID values aren’t guaranteed to be contiguous for consecutive
events. A subscriber can store a replay ID value and use it on resubscription to retrieve missed
events that are within the retention window.
Type
string
RequestIdentifier
Properties
Nillable
Description
ID of the request that triggered the event.
QuoteToOrderCompletedEvent
Notifies subscribers when the /actions/standard/createOrderFromQuote  REST request is complete. If the request is
successful, use this event to learn about the Order record. If the request isn’t successful, use this event to learn about the errors associated
with the request. This object is available in API version 56.0 and later.
Supported Calls
describeSObjects()
1285
QuoteToOrderCompletedEventTransaction Management

===== PAGE 1300 =====

Supported Subscribers
Supported?Subscriber
Apex Triggers
Flows
Processes
Pub/Sub API
Streaming API (CometD)
Subscription Channel
/event/QuoteToOrderCompletedEvent
Event Delivery Allocation Enforced
No
Special Access Rules
This object is available with Revenue Cloud.
DetailsField
Type
string
CorrelationIdentifier
Properties
Nillable
Description
Reserved for future use.
Type
string
EventUuid
Properties
Nillable
Description
A universally unique identifier (UUID) that identifies a platform event message.
Type
boolean
HasErrors
Properties
Defaulted on create
1286
QuoteToOrderCompletedEventTransaction Management

===== PAGE 1301 =====

DetailsField
Description
Contains true  if errors occurred during the process; otherwise false. The default value
is false.
Type
string
OrderId
Properties
Nillable
Description
The ID of the order created from the quote. If the process failed, this field is null.
Type
string
OrderNumber
Properties
Nillable
Description
The user-friendly, unique number assigned to the order created from the quote.
Type
QuoteToOrderErrDtlEvent[]
QuoteToOrderErrorDetailEvents
Properties
Nillable
Description
Contains a list of error messages and error codes if the request failed.
Type
string
ReplayId
Properties
Nillable
Description
Represents an ID value that is populated by the system and refers to the position of the event
in the event stream. Replay ID values aren’t guaranteed to be contiguous for consecutive
events. A subscriber can store a replay ID value and use it on resubscription to retrieve missed
events that are within the retention window.
Type
string
RequestIdentifier
Properties
Nillable
Description
The unique ID returned in the actions/standard/createOrderFromQuote
response. Use this ID to identify the event for a specific request.
1287
QuoteToOrderCompletedEventTransaction Management

===== PAGE 1302 =====

Transaction Management Business APIs
Use the Transaction Management Business APIs to fetch instant pricing data on a quote or an order, to create a quote, or to create an
order.
This table lists the available Transaction Management resources.
DescriptionResource
Initiate and execute the
amendment of a quote or an
order.
/connect/revenue-management/assets/actions/amend (POST)
Initiate and execute the
cancellation of an asset.
/connect/revenue-management/assets/actions/cancel (POST)
Initiate and execute the renewal
of an asset.
/connect/revenue-management/assets/actions/renew (POST)
Fetch instant pricing data on
the quote or order line data grid
/industries/cpq/quotes/actions/get-instant-price (POST)
and associated summary
component. It offers capabilities
to either create a context or
update the existing one based
on the provided context ID.
Place orders with integrated
pricing, configuration, and
/commerce/sales-orders/actions/place (POST)
validation, and manage them
throughout their entire lifecycle.
Additionally, update an order or
insert order items.
Create a quote to discover and
price products and services.
/commerce/quotes/actions/place (POST)
Additionally, insert, update, or
delete a quote line item.
Create a ramp deal for a
customer on a product. Sales
/connect/revenue-management/sales-transaction-contexts/resourceId/actions/ramp-deal-create
(POST)
reps can use ramp deals to
provide yearly deals to a
customer, resulting in long-term
revenue and customer
relationship. A customer can
create, update, or view multiple
segments of periods for their
subscription term with different
attributes for each segment.
Modify a ramp deal in scenarios
where a segment has updates
/connect/revenue-management/sales-transaction-contexts/resourceId/actions/ramp-deal-update
(POST)
1288
Transaction Management Business APIsTransaction Management

===== PAGE 1303 =====

DescriptionResource
such as quantity, discount, or
date change.
View a ramp deal related to a
quote line item or an order item.
/connect/revenue-management/sales-transaction-contexts/resourceId/actions/ramp-deal-view
(GET)
Delete a ramp deal to convert a
ramped product to include a
/connect/revenue-management/sales-transaction-contexts/resourceId/actions/ramp-deal-delete
(POST)
single quote line item or order
item.
Create a sales transaction, such
as an order or a quote, with
/connect/rev/sales-transaction/actions/place (POST)
integrated pricing and
configuration. Additionally,
update an order or a quote, and
insert and delete order or quote
line items to calculate the
estimated tax.
Create a clone of a sales
transaction, such as a quote or
/connect/rev/sales-transaction/actions/clone (POST)
an order. You can also clone a
quote line item or an order item
record with its related records
and configurations.
Create a supplemental order or
change orders after they are
/connect/rev/sales-transaction/actions/place-supplemental-transaction
(POST)
submitted for processing, such
as during the fulfillment
process.
Retrieve sales transaction data
efficiently from an initialized or
a hydrated context.
/connect/revenue/transaction-management/sales-transactions/actions/read
(POST)
Preview the approval levels of a
record and associated level
/connect/advanced-approvals/approval-submission/preview (POST)
details, approval chains,
approvers, and conditions
before you submit the record
for an approval.
Get eligible promotions for line
items within a quote or an
order.
/revenue/transaction-management/sales-transactions/actions/get-eligible-promotions
(POST)
Create an amendment that
trades a quantity of one product
/revenue/transaction-management/assets/actions/swap (POST)
for another. This change is
1289
Transaction Management Business APIsTransaction Management

===== PAGE 1304 =====

DescriptionResource
tracked as a swap request with
linked asset actions and a
net-zero order total where
applicable.
Create an amendment that
moves a lower-tier product to
/revenue/transaction-management/assets/actions/upgrade (POST)
a higher-tier product. This
change is tracked as an upgrade
request with linked asset actions
and quote or order line linkage
for reporting and auditing.
Create an amendment that
moves a higher-tier product to
/revenue/transaction-management/assets/actions/downgrade (POST)
a lower-tier product. This
change is tracked as a
downgrade request with linked
asset actions and quote or order
line linkage for reporting and
auditing.
Resources
Learn more about the available Quote and Order Capture resources.
Request Bodies
Learn more about the available API request bodies.
Response Bodies
Learn more about the available response bodies.
SEE ALSO:
Connect REST API Developer Guide: Introduction
Resources
Learn more about the available Quote and Order Capture resources.
Asset Amendment (POST)
Initiate and execute the amendment of a quote or an order.
Asset Cancellation (POST)
Initiate and execute the cancellation of an asset.
Asset Renewal (POST)
Initiate and execute the renewal of an asset.
1290
ResourcesTransaction Management

===== PAGE 1305 =====

Clone Sales Transaction (POST)
Create a clone of a sales transaction, such as a quote or an order. You can also clone a quote line item or an order item record with
its related records and configurations.
Get Eligible Promotions (POST)
Get eligible promotions for line items within a quote or an order.
Initiate Downgrade (POST)
Create an amendment that moves a higher-tier product to a lower-tier product. This change is tracked as a downgrade request with
linked asset actions and quote or order line linkage for reporting and auditing.
Initiate Swap (POST)
Create an amendment that trades a quantity of one product for another. This change is tracked as a swap request with linked asset
actions and a net-zero order total where applicable.
Initiate Upgrade (POST)
Create an amendment that moves a lower-tier product to a higher-tier product. This change is tracked as an upgrade request with
linked asset actions and quote or order line linkage for reporting and auditing.
Instant Pricing (POST)
Fetch instant pricing data on the quote or order line data grid and associated summary component. It offers capabilities to either
create a context or update the existing one based on the provided context ID.
Place Order (POST)
Place orders with integrated pricing, configuration, and validation, and manage them throughout their entire lifecycle. Additionally,
update an order or insert order items.
Place Quote (POST)
Create a quote to discover and price products and services. Additionally, insert, update, or delete a quote line item.
Place Sales Transaction (POST)
Create a sales transaction, such as an order or a quote, with integrated pricing and configuration. Additionally, update an order or a
quote, and insert and delete order or quote line items to calculate the estimated tax.
Place Supplemental Transaction (POST)
Create a supplemental order or change orders after they are submitted for processing, such as during the fulfillment process.
Preview Approval (POST)
Preview the approval levels of a record and associated level details, approval chains, approvers, and conditions before you submit
the record for an approval.
Read Sales Transaction (POST)
Retrieve sales transaction data efficiently from an initialized or a hydrated context.
Retrieve Sales Transaction API Errors (GET)
Retrieve any asynchronous error details associated with a sales transaction request.
Create Ramp Deal (POST)
Create a ramp deal for a customer on a product. Sales reps can use ramp deals to provide yearly deals to a customer, resulting in
long-term revenue and customer relationship. A customer can create, update, or view multiple segments of periods for their
subscription term with different attributes for each segment.
Delete Ramp Deal (POST)
Delete a ramp deal to convert a ramped product to include a single quote line item or order item.
Update Ramp Deal (POST)
Modify a ramp deal in scenarios where a segment has updates such as quantity, discount, or date change.
1291
ResourcesTransaction Management

===== PAGE 1306 =====

View Ramp Deal (GET)
View a ramp deal related to a quote line item or an order item.
Asset Amendment (POST)
Initiate and execute the amendment of a quote or an order.
Special Access Rules
To use this API, you need the InitiateAmend API permission set.
Resource
/connect/revenue-management/assets/actions/amend
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue-management/assets/actions/amend
Available version
62.0
HTTP methods
POST
Request body for POST
JSON example
{
"assetIds": [
"02iSG0000003NMhYAM",
"02iSG0000006DvSYAU"
],
"amendmentStartDate": "2023-10-04T00:00:00",
"contractId": "800SG00000CFpepYAD",
"opportunityId": "006SG000004W5tVYAS",
"outputRecordId": "801SG00000DX1jWYAT",
"outputRecordType": "Quote",
"quantityChange": 5
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIDs of the assets that you want to add to
the amendment record.
String[]assetIds
62.0RequiredStart date of the amendment.StringamendmentStart
Date
62.0OptionalID of the Contract record that you want
to sync with the amendment quote.
StringcontractId
62.0OptionalID of the Opportunity record that you
want to sync with the amendment quote.
Stringopportunity
Id
1292
ResourcesTransaction Management

===== PAGE 1307 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalID of the quote or order record that you
want to add the assets to.
StringoutputRecord
Id
62.0RequiredType of amendment record that you
want to create.
Stringoutput
RecordType
62.0RequiredQuantity to add to or reduce from the
asset's existing quantity.
Doublequantity
Change
Response body for POST
Amendment
Asset Cancellation (POST)
Initiate and execute the cancellation of an asset.
Special Access Rules
To use this API, you need the InitiateCancellation API permission set.
Resource
/connect/revenue-management/assets/actions/cancel
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue-management/assets/actions/cancel
Available version
62.0
HTTP methods
POST
Request body for POST
JSON example
{
"assetIds": [
"02iSG0000003NMhYAM",
"02iSG0000006DvSYAU"
],
"cancellationDate": "2023-10-04T00:00:00",
"contractId": "800SG00000CFpepYAD",
"opportunityId": "006SG000004W5tVYAS",
"outputRecordId": "801SG00000DX1jWYAT",
"outputRecordType": "Quote"
}
1293
ResourcesTransaction Management

===== PAGE 1308 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIDs of the assets that you want to cancel.
All assets in a request must belong to the
same price book.
String[]assetIds
62.0RequiredEffective date of the cancellation.Stringcancellation
Date
62.0OptionalID of the Contract record that you want
to sync with the cancellation quote.
StringcontractId
62.0OptionalID of the Opportunity record that you
want to sync with the cancellation quote.
Stringopportunity
Id
62.0OptionalID of the quote or order that you want to
cancel.
Stringoutput
RecordId
62.0RequiredType of cancellation record that you want
to create.
Stringoutput
RecordType
Response body for POST
Cancellation
Asset Renewal (POST)
Initiate and execute the renewal of an asset.
Special Access Rules
To use this API, you need the InitiateRenewal API permission set.
Resource
/connect/revenue-management/assets/actions/renew
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue-management/assets/actions/renew
Available version
62.0
HTTP methods
POST
Request body for POST
JSON example
{
"assetIds": [
"02iSG0000003NMhYAM",
"02iSG0000006DvSYAU"
1294
ResourcesTransaction Management

===== PAGE 1309 =====

],
"contractId": "800SG00000CFpepYAD",
"opportunityId": "006SG000004W5tVYAS",
"outputRecordId": "801SG00000DX1jWYAT",
"outputRecordType": "Quote",
"renewalEndDate": "2024-10-03T23:59:59",
"renewalStartDate": "2023-10-04T00:00:00"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIDs of the assets that you want to renew.String[]assetIds
62.0OptionalID of the Contract record that you want
to sync with the renewal of the Quote or
Order record.
StringcontractId
62.0OptionalID of the Opportunity record that you
want to sync with the renewal quote.
Stringopportunity
Id
62.0OptionalID of the Quote or Order record that you
want to renew.
Stringoutput
RecordId
62.0RequiredType of renewal record that you want to
create.
Stringoutput
RecordType
62.0OptionalEnd date of the renewal process for the
assets.
Stringrenewal
EndDate
62.0OptionalStart date of the renewal process for the
assets. Required for early asset renewals
Stringrenewal
StartDate
and renewing expired assets, using
today’s date or a future date.
Response body for POST
Renewal
Clone Sales Transaction (POST)
Create a clone of a sales transaction, such as a quote or an order. You can also clone a quote line item or an order item record with its
related records and configurations.
This API supports the cloning of records for these objects.
• Quote
• QuoteLineItem
• OrderItem
• QuoteLineGroup
• Order
1295
ResourcesTransaction Management

===== PAGE 1310 =====

• OrderItemGroup
You can clone all items in a quote line group or order item group when the record to clone is a quote line group or an order item group
record.
Resource
/connect/rev/sales-transaction/actions/clone
Resource example
https://<varname>yourInstance</varname>.salesforce.com/services/data/v64.0/connect/rev/sales-transaction/actions/clone
Available version
64.0
HTTP methods
POST
Request body for POST
JSON example
This is a sample request to clone a record within a sales transaction.
{
"recordIds": ["0QLxx0000004CBYGA2"],
"salesTransactionId": "0Q0xx0000004CE0CAM"
}
This is a sample request to clone all line items in a ramped group within a sales transaction.
{
"recordIds": ["0QLxx0000004CBYGA2"],
"salesTransactionId": "0Q0xx0000004CE0CAM",
"options": {
"lineScope": "AllLines"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
64.0RequiredID of the record to be cloned. You can
specify a single record ID only.
String[]recordIds
64.0RequiredID of the sales transaction related to the
record IDs to clone.
StringsalesTransactionId
65.0OptionalSpecifies options to clone a ramp
segment within a sales transaction. You
can clone only the last ramp segment.
Clone Options
Input
options
Response body for POST
Clone Sales Transaction
1296
ResourcesTransaction Management

===== PAGE 1311 =====

Get Eligible Promotions (POST)
Get eligible promotions for line items within a quote or an order.
This API accepts line item IDs and sales transaction ID as the input and then initializes the context by filtering on the specific line items.
Resource
/revenue/transaction-management/sales-transactions/actions/get-eligible-promotions
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/revenue/transaction-management/sales-transactions/actions/get-eligible-promotions
Available version
66.0
HTTP methods
POST
Request body for POST
JSON example
{
"salesTransactionId": "0Q0xx0000004EOECA2",
"lineItemIds": [
"0QLxx0000004E7eGAE",
"0QLxx0000004GCeGAM",
"0QLxx0000004E7gGAE"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0RequiredList of line item IDs to evaluate for
promotions. The object type is
String[]lineItemIds
auto-determined from the sales
transaction ID.
66.0RequiredThe sales transaction ID, such as an order
ID or a quote ID, for the promotion
evaluation.
StringsalesTransactionId
Response body for POST
Get Eligible Promotions
Initiate Downgrade (POST)
Create an amendment that moves a higher-tier product to a lower-tier product. This change is tracked as a downgrade request with
linked asset actions and quote or order line linkage for reporting and auditing.
Use this API to move to a lower-tier or lower-value product. For example, from Sales Cloud Unlimited to Sales Cloud Enterprise, or to a
product in a restricted-use or professional edition.
1297
ResourcesTransaction Management

===== PAGE 1312 =====

This API creates an amendment quote and order with downgrade-specific order actions and quote action subtypes. After assetization,
the original asset receives an asset action with business category as Downgrade (or equivalent). This step indicates that the downgrade-from
product and the new asset is created with an asset action (downgraded to), with relationships between the two. This step also enables
sales reps to process downgrades and makes sure that downgrades are auditable and reportable separately from cancellations and new
sales.
Resource
/revenue/transaction-management/assets/actions/downgrade
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/revenue/transaction-management/assets/actions/downgrade
Available version
66.0
HTTP methods
POST
Request body for POST
JSON example
{
"swapStartDate": "2025-12-01T00:00:00Z",
"outputRecordType": "Quote",
"swapGroups": {
"groups": [
{
"referenceId": "DOWNGRADE-001",
"outGroup": {
"swapAssets": [
{
"assetId": "02ixx0000004HOAAA2",
"quantity": 1
}
]
},
"inGroup": {
"graphId": "downgradeRequest",
"records": [
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"Product2Id": "01txx0000006iVlAAI",
"PricebookEntryId": "01uxx0000008ym4AAA",
"UnitPrice": 1049,
"Quantity": "1",
"StartDate": "2022-09-22"
}
}
]
1298
ResourcesTransaction Management

===== PAGE 1313 =====

}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalID of the contract record for the
downgrade action.
StringcontractId
66.0OptionalID of the opportunity record for the
downgrade action.
StringopportunityId
66.0RequiredOutput record type for the downgrade
action.
StringoutputRecordType
66.0RequiredList of swap groupings that contain the
asset details for the downgrade action.
Swap Group[]swapGroups
66.0RequiredAmendment start date for the
downgrade action.
StringswapStartDate
Response body for POST
Initiate Downgrade Response
SEE ALSO:
Salesforce Help: Swap, Upgrade, or Downgrade Assets
Initiate Swap (POST)
Create an amendment that trades a quantity of one product for another. This change is tracked as a swap request with linked asset
actions and a net-zero order total where applicable.
Use this API when you must exchange one product for another of equivalent or different value. For example, you can reduce Sales Cloud
Enterprise licenses and add Data Cloud Credits in a single amendment.
The API creates an amendment quote and order with swap-specific order actions and quote action subtypes. When the order is assetized,
the source asset gets an asset action with business category as Swap  (reduced quantity). The new asset is created with an asset action
that identifies it as swapped in, with relationships that link the swapped-from and swapped-to assets. These operations make swaps
auditable and reportable separately from cancellations and new sales. They also support use cases such as trading unused licenses for
credits or moving spend between products while preserving contract intent.
Resource
/revenue/transaction-management/assets/actions/swap
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/revenue/transaction-management/assets/actions/swap
1299
ResourcesTransaction Management

===== PAGE 1314 =====

Available version
66.0
HTTP methods
POST
Request body for POST
JSON example
{
"swapStartDate": "2025-12-01T00:00:00Z",
"outputRecordType": "Quote",
"swapGroups": {
"groups": [
{
"referenceId": "SWAP-001",
"outGroup": {
"swapAssets": [
{
"assetId": "02ixx0000004HOAAA2",
"quantity": 1
}
]
},
"inGroup": {
"graphId": "swapRequest",
"records": [
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"Product2Id": "01txx0000006iVlAAI",
"PricebookEntryId": "01uxx0000008ym4AAA",
"UnitPrice": 1049,
"Quantity": "1",
"StartDate": "2022-09-22"
}
}
]
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalID of the contract record for the swap
action.
StringcontractId
1300
ResourcesTransaction Management

===== PAGE 1315 =====

Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalID of the opportunity record for the swap
action.
StringopportunityId
66.0RequiredOutput record type for the swap action.StringoutputRecordType
66.0RequiredList of swap groupings that contain the
asset details for the swap action.
Swap Group[]swapGroups
66.0RequiredAmendment start date for the swap
action.
StringswapStartDate
Response body for POST
Initiate Swap Response
SEE ALSO:
Salesforce Help: Swap, Upgrade, or Downgrade Assets
Initiate Upgrade (POST)
Create an amendment that moves a lower-tier product to a higher-tier product. This change is tracked as an upgrade request with linked
asset actions and quote or order line linkage for reporting and auditing.
Use this API to move to a higher-tier or higher-value product. For example, from Sales Cloud Enterprise to Sales Cloud Unlimited, or from
a product in an Enterprise edition to an Unlimited edition.
This API creates an amendment quote and order with upgrade-specific order actions and quote action subtypes. After assetization, the
original asset receives an asset action with business category as Upgrade  (or equivalent). This step indicates that the upgrade-from
product and the new asset is created with an asset action (upgraded to), with relationships between the two. This step also enables
sales reps to process upgrades and makes sure that upgrades are distinguishable in reporting and analytics from cancellations plus new
sales.
Resource
/revenue/transaction-management/assets/actions/upgrade
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/revenue/transaction-management/assets/actions/upgrade
Available version
66.0
HTTP methods
POST
Request body for POST
JSON example
{
"swapStartDate": "2025-12-01T00:00:00Z",
"outputRecordType": "Quote",
1301
ResourcesTransaction Management

===== PAGE 1316 =====

"swapGroups": {
"groups": [
{
"referenceId": "UPGRADE-001",
"outGroup": {
"swapAssets": [
{
"assetId": "02ixx0000004HOAAA2",
"quantity": 1
}
]
},
"inGroup": {
"graphId": "upgradeRequest",
"records": [
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"Product2Id": "01txx0000006iVlAAI",
"PricebookEntryId": "01uxx0000008ym4AAA",
"UnitPrice": 1049,
"Quantity": "1",
"StartDate": "2026-03-22"
}
}
]
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalID of the contract record for the upgrade
action.
StringcontractId
66.0OptionalID of the opportunity record for the
upgrade action.
StringopportunityId
66.0RequiredOutput record type for the upgrade
action.
StringoutputRecordType
66.0RequiredList of swap groupings that contain the
asset details for the upgrade action.
Swap Group[]swapGroups
66.0RequiredAmendment start date for the upgrade
action.
StringswapStartDate
1302
ResourcesTransaction Management

===== PAGE 1317 =====

Response body for POST
Initiate Upgrade Response
SEE ALSO:
Salesforce Help: Swap, Upgrade, or Downgrade Assets
Instant Pricing (POST)
Fetch instant pricing data on the quote or order line data grid and associated summary component. It offers capabilities to either create
a context or update the existing one based on the provided context ID.
You can also group quote line items or order items based on location, work types, or departments, if groups are enabled for your org.
Groups provide a visualization of the products to view large quotes.
Resource
/industries/cpq/quotes/actions/get-instant-price
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/industries/cpq/quotes/actions/get-instant-price
Available version
60.0
Requires Chatter
No
HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "1234567",
"contextId": "",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
"Name": "Test Quote Proration Pricing",
"OpportunityId": "006xx000001a4ISAAY",
"Pricebook2Id": "01sxx0000005ptpAAA"
}
},
{
"referenceId": "refQuoteLine",
"record": {
"attributes": {
"type": "QuoteLineItem",
1303
ResourcesTransaction Management

===== PAGE 1318 =====

"method": "POST"
},
"QuoteId": "refQuote",
"PricebookEntryId": "01uxx0000008zHmAAI",
"Product2Id": "01txx0000006jmWAAQ",
"Quantity": 2,
"UnitPrice": 25,
"StartDate": "2022-09-28",
"EndDate": "2028-09-27",
"PeriodBoundary": "ANNIVERSARY",
"BillingFrequency": "ANNUAL"
}
}
]
}
This example shows a sample request to specify grouping of lines based on criteria.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004DOSCA2",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "0QLxx0000004F3gGAE",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PUT"
},
"Quantity": 5
}
}, {
"referenceId": "0QLxx0000004F3hGAE",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PUT"
},
"Quantity": 2
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
1304
ResourcesTransaction Management

===== PAGE 1319 =====

"method": "POST",
"action": "GroupBy",
"criteria": {
"Quantity": 5
}
},
"Name": "record"
}
}, {
"referenceId": "GroupId2",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"Quantity": 2
}
},
"Name": "record1",
}
}
]
}
This example shows a sample request for the initial grouping of the quote with the quote lines assigned to the first group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupAll"
},
"Name": "sample"
}
}
]
}
1305
ResourcesTransaction Management

===== PAGE 1320 =====

This example shows a sample request to ungroup a quote but retain the quote lines.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "0QLxx0000004CBYGA2",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PUT"
},
"Quantity": 2,
"QuoteLineGroupId": null
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"action": "Ungroup"
}
}
}
]
}
This example shows a sample request to create a new group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
1306
ResourcesTransaction Management

===== PAGE 1321 =====

"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST"
},
"Name": "sample"
}
}
]
}
This example shows a sample request to delete a group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"action": "DeleteGroup"
},
"Name": "sample"
}
}
]
}
This example shows a sample request to move a group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
1307
ResourcesTransaction Management

===== PAGE 1322 =====

},
{
"referenceId": "0QLxx0000004CBYGA2",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PUT"
},
"Quantity": 2
"QuoteLineGroupId": "{@GroupId2}"
}
},
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
59.0OptionalThe ID generated by the context service.
If no context ID is provided, a new
context is created.
StringcontextId
59.0OptionalClient-generated ID for tracking multiple
related API requests.
StringcorrelationId
59.0RequiredList of pricing data to be fetched.Object with
Reference Input[]
records
Response body for POST
Instant Pricing
Place Order (POST)
Place orders with integrated pricing, configuration, and validation, and manage them throughout their entire lifecycle. Additionally,
update an order or insert order items.
You can also group order items based on location, work types, or departments, if groups are enabled for your org. Groups provide a
visualization of the products to view large quotes.
This API supports a maximum of 300 transaction line items.
Note:  This API has been deprecated as of API version 63.0. In API version 63.0 and later, use the new Place Sales Transaction API.
Special Access Rules
You need the PlaceOrder API permission set to use this API.
Resource
/commerce/sales-orders/actions/place
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/commerce/sales-orders/actions/place
1308
ResourcesTransaction Management

===== PAGE 1323 =====

Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"pricingPref": "System",
"configurationInput": "RunAndAllowErrors",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"graph": {
"graphId": "graphId",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "POST",
"Id": "POST"
}
}
},
{
"referenceId":"refOrderItem",
"record":{
"attributes":{
"type":"OrderItem",
"method":"POST"
},
"OrderId":"@{refOrder.id}",
"OrderActionId":"@{refOrderAction.id}",
"ListPrice":"144.99",
"Quantity":3,
"PricebookEntryId":"01uxx0000008yXPAAY",
"Product2Id":"01txx0000006i2UAAQ",
"UnitPrice":"199.49"
}
}
]
}
}
This example shows a sample request to define grouping of order items.
{
"pricingPref": "system",
1309
ResourcesTransaction Management

===== PAGE 1324 =====

"graph": {
"graphId": "placeOrder",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "801xx000003GZ9bAAG"
}
}
},
{
"referenceId": "refOlg1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST"
},
"Name": "New Group",
"OrderId": "@{refOrder.id}"
}
}
]
}
}
This example shows a sample request to ungroup order items.
{
"pricingPref": "system",
"graph": {
"graphId": "placeOrder",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "refOrder"
}
}
},
{
"referenceId": "refOlg1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "DELETE",
"id": "refOlg1",
"action": "Ungroup"
}
}
1310
ResourcesTransaction Management

===== PAGE 1325 =====

}
]
}
}
This example shows a sample request to create a new group.
{
"pricingPref": "system",
"graph": {
"graphId": "placeOrder",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "refOrder"
}
}
},
{
"referenceId": "refOlg",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST"
},
"Name": "New Group",
"OrderId": "@{refOrder.id}"
}
}
]
}
}
This example shows a sample request to delete a group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "refOrder"
}
}
},
{
"referenceId": "refOlg",
1311
ResourcesTransaction Management

===== PAGE 1326 =====

"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "DELETE",
"id": "refOlg",
"action": "DeleteGroup"
}
}
}
]
}
This example shows a sample request to group order items based on criteria.
{
"pricingPref": "system",
"graph": {
"graphId": "placeOrder",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "refOrder"
}
}
},
{
"referenceId": "g0",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"BillingFrequency2": null
}
},
"Name": "Billing Frequency: ",
"OrderId": "@{refOrder.id}"
}
},
{
"referenceId": "g1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"BillingFrequency2": "Monthly"
}
},
1312
ResourcesTransaction Management

===== PAGE 1327 =====

"Name": "Billing Frequency: Monthly",
"OrderId": "@{refOrder.id}"
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalRate card entries defined in the catalog
that must be fetched for order items with
Stringcatalog
RatesPref
usage-based pricing during the order
creation process. Valid values are:
• Fetch—Retrieves the rate card
entries defined in the catalog for
order items during the order creation
process.
• Skip—Skips the retrieval of rate
card entries for order items during
the order creation process.
The default value is Skip.
This property is available when the
Usage-Based Selling feature is enabled.
60.0OptionalConfiguration input for the place order
process. Valid values are:
Stringconfiguration
Input
• RunAndAllowErrors—Specifies
to run the configuration and to
proceed order ingestion upon
encountering any configuration
errors.
• RunAndBlockErrors—Specifies
to run configuration and to block
order ingestion upon encountering
any configuration errors.
• Skip—Specifies to skip
configuration.
The default value is
RunAndBlockErrors.
60.0OptionalConfiguration options during the
ingestion process.
Configuration
Options Input[]
configuration
Options
60.0RequiredThe sObject graph of the order payload
to be ingested. You can perform create,
Object Graph Inputgraph
1313
ResourcesTransaction Management

===== PAGE 1328 =====

Available
Version
Required or
Optional
DescriptionTypeName
update, or delete operations on objects
from the Sales Transaction context
definition by using this property.
Additionally, perform create, update, or
delete operations on custom objects and
fields in your extended context definition.
60.0OptionalPricing preference during the create order
process. Valid values are:
StringpricingPref
• Force—Specifies to force pricing
during the order ingestion process.
• Skip—Specifies to skip pricing
during the order ingestion process.
• System—Specifies the system to
determine whether a pricing
calculation is required.
The default value is System.
Response body for POST
Place Order
Place Quote (POST)
Create a quote to discover and price products and services. Additionally, insert, update, or delete a quote line item.
You can also group quote line items based on location, work types, or departments, if groups are enabled for your org. Groups provide
a visualization of the products to view large quotes.
This API supports a maximum of 300 transaction line items.
Note:  This API has been deprecated as of API version 63.0. In API version 63.0 and later, use the new Place Sales Transaction API.
Special Access Rules
You need the Create on Quotes user permission to create quotes.
Resource
/commerce/quotes/actions/place
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/commerce/quotes/actions/place
Available version
60.0
HTTP methods
POST
1314
ResourcesTransaction Management

===== PAGE 1329 =====

Request body for POST
JSON example
This example shows a sample request to create a quote.
{
"pricingPref": "System",
"configurationInput": "RunAndAllowErrors",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}, "graph": {
"graphId": "createQuote",
"records": [{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
"opportunityId": "---",
"quoteProp1": "value1",
"quoteProp2": "value2"
}
},
{
"referenceId": "refQuoteLineItem1",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteLineItemProp1": "value1",
"QuoteLineItemProp2": "value2"
}
},
{
"referenceId": "refQuoteLineItemAttribute",
"record": {
"attributes": {
"type": "QuoteLineItemAttribute",
"method": "POST"
},
"QuoteLineItemId": "@{refQuoteLineItem1.id}",
"AttributeDefinitionId": "0tjxx0000000001AAA"
}
}
]
}
}
1315
ResourcesTransaction Management

===== PAGE 1330 =====

This example shows a sample request to insert, update, or delete a quote line item.
{
"pricingPref": "System",
"configurationInput": "skip",
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004E2mCAE"
},
"Name": "Quote_Acme"
}
},
{
"referenceId": "refQuoteLineItemToCreate1",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "0Q0xx0000004E2mCAE",
"PricebookEntryId": "01uxx0000008yXPAAY",
"Product2Id": "01txx0000006i2UAAQ",
"Quantity": 2.0,
"UnitPrice": 800.0,
"PeriodBoundary": "Anniversary",
"BillingFrequency": "Monthly",
"StartDate": "2024-03-11"
}
},
{
"referenceId": "refQuoteLineItemToPatch2",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH",
"id": "0Q0xx0000004E2mCAE"
},
"Quantity": 2.0,
"UnitPrice": 600.0
}
},
{
"referenceId": "refQuoteLineItemToDelete3",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "DELETE",
"id": "0Q0xx0000004E2mYLK"
1316
ResourcesTransaction Management

===== PAGE 1331 =====

}
}
}
]
}
}
This example shows a sample request to define grouping of quote line items.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
"graphId": "groupLines",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From Place Quote API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"Quantity": 1
}
},
"Name": "From Place Quote API Group",
"QuoteId": "@{refQuote.id}"
}
},
{
"referenceId": "refQuoteItem1",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH",
"id":"0QLxx0000004DJcGAM"
},
"QuoteLineGroupId": "@{refQlg1.id}",
"Quantity": 1
}
}
]
1317
ResourcesTransaction Management

===== PAGE 1332 =====

}
}
This example shows a sample request for the initial grouping of the quote with the quote lines assigned to the first group.
{
"pricingPref": "Force",
"graph": {
"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CAmCAM"
}
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupAll"
},
"Name": "From PQ API Group",
"QuoteId": "@{refQuote.id}"
}
}
]
}
}
This example shows a sample request to ungroup a quote but retain the quote lines.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From Place Quote API"
}
},
1318
ResourcesTransaction Management

===== PAGE 1333 =====

{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "{GroupId}",
"action": "Ungroup"
}
}
}
]
}
}
This example shows a sample request to create a new group.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From Place Quote API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST"
},
"Name": "From PQ API Group",
"QuoteId": "@{refQuote.id}"
}
}
]
}
}
This example shows a sample request to delete a group.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
1319
ResourcesTransaction Management

===== PAGE 1334 =====

"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From Place Quote API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "{GroupId}",
"action": "DeleteGroup"
}
}
}
]
}
}
This example shows a sample request to move a group.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From PlaceQuote Api"
}
},
{
"referenceId": "0QLxx0000004CBYGA2",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH"
"id": "0QLxx0000004CBYGA2"
},
1320
ResourcesTransaction Management

===== PAGE 1335 =====

"Quantity": 2,
"QuoteLineGroupId": "@{GroupId2}"
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalRate card entries defined in the catalog
that must be fetched for quote line items
Stringcatalog
RatesPref
with usage-based pricing during the
quote creation process. Valid values are:
• Fetch—Retrieves the rate card
entries defined in the catalog for
quote line items during the quote
creation process.
• Skip—Skips the retrieval of rate
card entries for quote line items
during the quote creation process.
The default value is Skip.
This property is available when the
Usage-Based Selling feature is enabled.
60.0OptionalConfiguration input for the place quote
process. Valid values are:
Stringconfiguration
Input
• RunAndAllowErrors
• RunAndBlockErrors
• Skip
The default value is
RunAndBlockErrors.
60.0OptionalConfiguration options during the
ingestion process.
Configuration
Options Input
configuration
Options
60.0RequiredThe sObject graph representing the
quote structure. You can perform create,
Object Graph Inputgraph
update, or delete operations on objects
from the Sales Transaction context
definition by using this property.
Additionally, perform create, update, or
delete operations on custom objects and
fields in your extended context definition.
1321
ResourcesTransaction Management

===== PAGE 1336 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalPricing preference during the quote
process. Valid values are:
StringpricingPref
• Force
• Skip
• System
The default value is System.
Response body for POST
Place Quote
Place Sales Transaction (POST)
Create a sales transaction, such as an order or a quote, with integrated pricing and configuration. Additionally, update an order or a
quote, and insert and delete order or quote line items to calculate the estimated tax.
You can also group order or quote line items based on location, work types, or departments, if groups are enabled for your org. Groups
provide a visualization of the products to view large quotes.
Keep these considerations in mind when you use this API.
• You can add up to 1000 quote line items for a quote, and 1000 order products for an order. For complex flows that involve a large
volume of records, ensure that the number of line items that are sent to this API are within this limit.
• A quote can have up to 3000 quote line item attributes, and an order can have up to 3000 order line item attributes.
• This API doesn't support creation of amendment, renewal, or cancellation quote or order. Use the amendment, renewal, or cancellation
APIs or invocable actions.
Resource
/connect/rev/sales-transaction/actions/place
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/rev/sales-transaction/actions/place
Available version
63.0
HTTP methods
POST
Request body for POST
JSON example
This is a sample request to create a sales transaction for a quote. This example also skips tax calculation by specifying a value for
the optional taxPref  property.
{
"pricingPref": "System",
"catalogRatesPref": "Skip",
"configurationPref": {
1322
ResourcesTransaction Management

===== PAGE 1337 =====

"configurationMethod": "Skip",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}
},
"taxPref": "Skip",
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708"
},
"graph": {
"graphId": "createQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"method": "POST",
"type": "Quote"
},
"Name": "Quote_Acme",
"Pricebook2Id": "01sDU000000JvhbYAC"
}
},
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "@{refQuote.id}",
"Product2Id": "01tDU000000F7b8YAC",
"PricebookEntryId": "01uDU000000fxt2YAA",
"UnitPrice": 100,
"Quantity": "1",
"StartDate": "2024-10-29",
"EndDate": "2025-03-01",
"PeriodBoundary": "Anniversary"
}
}
]
}
}
This sample request assigns a TransactionProcessingType record to a quote without any additional preferences. In this example,
the TransactionType value for a record is set to a TransactionProcessingType record. See TransactionProcessingType on page
1271 tooling object for more details.
{
"pricingPref": "Force",
"contextDetails": {
"contextId": "f1c9e3e1c335f7959a88de09d3a867cc2b95e08709b99de8e2edeb8f5039e8ed",
1323
ResourcesTransaction Management

===== PAGE 1338 =====

"scope": "Session"
},
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
"OpportunityId": "006xx000001a2oWAAQ",
"PriceBook2Id": "01sxx0000005ptpAAA",
"TransactionType": "SkipPricingAndRunTax",
"Name": "Quote_No_Tax_System"
}
},
{
"referenceId": "refQLI1",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "@{refQuote.id}",
"UnitPrice": 49.99,
"Product2Id": "01txx0000006i2aAAA",
"PricebookEntryId": "01uxx0000008yX0AAI",
"Quantity": 10
}
}
]
}
}
This is a sample request to insert, update, or delete a quote line item.
{
{
"pricingPref": "System",
"catalogRatesPref": "Skip",
"configurationPref": {
"configurationMethod": "Skip",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}
},
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708"
},
1324
ResourcesTransaction Management

===== PAGE 1339 =====

"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"method": "PATCH",
"type": "Quote",
"id": "801xx000003GZ9bAAG"
}
}
},
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH",
"id": "402xx000003KY5vJGH"
},
"Quantity": "5"
}
}
]
}
}
This is a sample request to define grouping of quote line items.
{
"pricingPref": "Force",
"catalogRatesPref": "Skip",
"configurationPref": {
"configurationMethod": "Skip",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}
},
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708"
},
"graph": {
"graphId": "groupQuoteLines",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"method": "PATCH",
"type": "Quote",
"id": "801xx000003GZ9bAAG"
1325
ResourcesTransaction Management

===== PAGE 1340 =====

}
}
},
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH",
"id": "402xx000003KY5vJGH"
},
"QuoteLineGroupId": "@{refQuote.id}"
}
}
]
}
}
This is s a sample request for the initial grouping of the quote with all the quote lines assigned to the first group.
{
"pricingPref": "Force",
"catalogRatesPref": "Skip",
"graph": {
"graphId": "groupQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CAmCAM"
}
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupAll"
},
"Name": "From PST API Group",
"QuoteId": "@{refQuote.id}"
}
}
]
}
}
1326
ResourcesTransaction Management

===== PAGE 1341 =====

This is a sample request to ungroup a quote but retain the quote lines.
{
"catalogRatesPref": "Skip",
"pricingPref": "Force",
"graph": {
"graphId": "ungroupQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "Grouped Quote with PST API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "402xx000003KY5vJGH",
"action": "Ungroup"
}
}
}
]
}
}
This is a sample request to create a new group.
{
"catalogRatesPref": "Skip",
"pricingPref": "Force",
"graph": {
"graphId": "createGroup",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "Grouped Quote with PST API"
}
},
{
"referenceId": "refQlg1",
1327
ResourcesTransaction Management

===== PAGE 1342 =====

"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST"
},
"Name": "From PQ API Group",
"QuoteId": "@{refQuote.id}"
}
}
]
}
}
This example shows a sample request to delete a group.
{
"catalogRatesPref": "Skip",
"pricingPref": "Force",
"graph": {
"graphId": "deleteGroup",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "Grouped Quote with PST API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "402xx000003KY5vJGH",
"action": "DeleteGroup"
}
}
}
]
}
}
This is a sample request to group order items based on criteria.
{
"catalogRatesPref": "Skip",
"pricingPref": "Force",
"graph": {
"graphId": "groupOrderItems",
"records": [
1328
ResourcesTransaction Management

===== PAGE 1343 =====

{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "0Q0xx0000004C99CAE"
}
}
},
{
"referenceId": "refOlg1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"BillingFrequency2": null
}
},
"Name": "Billing Frequency: ",
"OrderId": "@{refOrder.id}"
}
},
{
"referenceId": "g1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"BillingFrequency2": "Monthly"
}
},
"Name": "Billing Frequency: Monthly",
"OrderId": "@{refOrder.id}"
}
}
]
}
}
This is a sample request to save changes to a ramp deal by using context ID. The context ID is returned by the Ramp Deal APIs.
See Create Ramp Deal (POST).
{
"pricingPref": "Force",
"contextDetails": {
"contextId": "f1c9e3e1c335f7959a88de09d3a867cc2b95e08709b99de8e2edeb8f5039e8ed",
"scope": "Session"
},
"graph": {
1329
ResourcesTransaction Management

===== PAGE 1344 =====

"graphId": "updateQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004DQ4CAM"
}
}
}
]
}
}
To see examples that specify actions to create ramp deals for groups, see Group Ramp Action Input on page 1388.
To see examples that apply to usage-based products, see Usage-Based Product Input on page 1398.
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalRate card entries defined in the catalog
that must be fetched for sales items with
StringcatalogRates
Pref
usage-based pricing during the creation
of the sales transaction. Valid values are:
• Fetch—Retrieves the rate card
entries defined in the catalog for sales
items during the creation of the sales
transaction.
• Skip—Skips the retrieval of rate
card entries for sales items during the
creation of the sales transaction.
The default value is Skip.
This property is available when the
Usage-Based Selling feature is enabled.
63.0OptionalConfiguration preference during the
quote process. These preferences ensure
Configurator
Preference Input
configuration
Pref
that quotes are defined as per the
requirement.
63.0Required if the
graph  property
isn’t specified.
Context details that are created for a sales
transaction.
Context InputcontextDetails
63.0Required if the
contextDetails
The sObject graph of the sales transaction
to be ingested. You can perform create,
Object Graph Inputgraph
1330
ResourcesTransaction Management

===== PAGE 1345 =====

Available
Version
Required or
Optional
DescriptionTypeName
property isn’t
specified.
update, or delete operations on objects
from the Sales Transaction context
definition by using this property.
Additionally, perform create, update, or
delete operations on custom objects and
fields in your extended context definition.
To create custom objects that are at the
grandchildren level from a line item, you
must create the hierarchy of objects until
the grandchild object in the same
request.
65.0OptionalSpecifies the action that you want to
perform on group ramp segments. You
StringgroupRampAction
can also convert a non-ramped group
into a ramped group. Valid values are:
• AddProducts—Adds rampable
products to group ramp segments.
• DeleteProducts—Deletes
ramped products.
• EditGroup—Converts a
non-ramped group into a group
ramp segment, or edit group ramp
segment attributes such as name and
description, except the start and end
dates.
• EditRampSchedule—Edits
details of the group ramp segments,
including start and end dates.
• DeleteSegment—Deletes the
first or last segment in a group ramp
schedule.
• ConvertToNonRampedGroup—Converts
the first or last group ramp segment
into a non-ramped group.
To add or delete ramped line items from
multiple group ramp segments, specify
the applicable values in the graph
property. See Group Ramp Action Input
on page 1388 to refer to examples.
1331
ResourcesTransaction Management

===== PAGE 1346 =====

Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalPricing preference during the creation of
a sales transaction. Valid values are:
StringpricingPref
• Force—Enforces pricing during
the creation of sales transactions.
• Skip—Skips pricing during the
creation of sales transactions.
• System—Determines whether a
pricing calculation is required.
The default value is System.
65.0OptionalSpecifies whether to execute or skip the
tax calculation step for each sales
StringtaxPref
transaction record. Valid value is Skip.
If you don't specify this value, then tax
calculation request is performed by
default.
Response body for POST
Place Sales Transaction
Place Supplemental Transaction (POST)
Create a supplemental order or change orders after they are submitted for processing, such as during the fulfillment process.
Keep these considerations in mind when you use this API.
• The original order must not be assetized.
• If Billing is enabled and configured for the order, verify that the original order hasn't been billed.
• If Dynamic Revenue Orchestration (DRO) is enabled and configured for the order, ensure the original order hasn't reached the point
of no return milestone. If point of no return milestone hasn't been reached, the fulfillment plan is frozen.
Resource
/connect/rev/sales-transaction/actions/place-supplemental-transaction
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/rev/sales-transaction/actions/place-supplemental-transaction
Available version
64.0
HTTP methods
POST
1332
ResourcesTransaction Management

===== PAGE 1347 =====

Request body for POST
JSON example
This sample creates a supplemental order, which is a clone of the original order. The supplemental order is related to the original
order.
{
"relatedSalesTransactionId": "801S70000001VKgIAM"
}
This sample overrides a field value of an order line item to supplement the order item with ID value as 802SG000003vZ15YAE.
{
"relatedSalesTransactionId": "801S70000001VKgIAM",
"pricingPref": "System",
"supplementalGraph": {
"graphId": "1",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "801S70000001VKgIAM"
},
"EffectiveDate": "2025-03-01",
"QuoteId": "0Q0xx0000004DQ4CAM"
}
},
{
"referenceId": "refOrderItem",
"record": {
"attributes": {
"type": "OrderItem",
"method": "PATCH",
"id": "802SG000003vZ15YAE"
},
"QuoteLineItemId": "0Q0xx0000004E2mYLK"
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
64.0OptionalPricing preference for this supplemental
transaction or order ingestion process.
Valid values are:
StringpricingPref
1333
ResourcesTransaction Management

===== PAGE 1348 =====

Available
Version
Required or
Optional
DescriptionTypeName
• Force—Enforces pricing during
the creation of sales transactions.
• Skip—Skips pricing during the
creation of sales transactions.
• System—Determines whether a
pricing calculation is required.
If pricingPref  value is defined as
either Force  or System, the
supplemental order can have a different
pricing from the original order.
64.0RequiredRelated or the original sales transaction
upon which a supplemental transaction
is created.
StringrelatedSales
TransactionId
64.0OptionalThe sObject graph that represents a
payload with the additional changes to
be ingested.
Object Graph Inputsupplemental
Graph
The attribute's HTTP method must be
PATCH. The attribute ID must be the ID
of the original order or order item that
you want to supplement.
Response body for POST
Supplemental Transaction
Preview Approval (POST)
Preview the approval levels of a record and associated level details, approval chains, approvers, and conditions before you submit the
record for an approval.
For example, a sales rep working on a quote can preview the approval levels for a quote before submitting the quote for approval.
Resource
/connect/advanced-approvals/approval-submission/preview
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/advanced-approvals/approval-submission/preview
Available version
65.0
HTTP methods
POST
1334
ResourcesTransaction Management

===== PAGE 1349 =====

Request body for POST
JSON example
{
"flowApiName": "QuoteApprovals",
"objectApiName": "Quote",
"recordId": "0Q0DU0000005HZC0A2"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
65.0RequiredAPI name of the auto-launched flow.StringflowApiName
65.0RequiredAPI name of the object to preview the
approvals for.
StringobjectApiName
65.0RequiredID of the record to preview the approvals
for.
StringrecordId
Response body for POST
Preview Approval
Read Sales Transaction (POST)
Retrieve sales transaction data efficiently from an initialized or a hydrated context.
Resource
/connect/revenue/transaction-management/sales-transactions/actions/read
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue/transaction-management/sales-transactions/actions/read
Available version
65.0
HTTP methods
POST
Request body for POST
JSON example
{
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"queryTags": [
"Quote",
"QuoteLineItem",
"Product"
]
}
1335
ResourcesTransaction Management

===== PAGE 1350 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
65.0RequiredID of the context to retrieve the data
records.
StringcontextId
65.0OptionalList of objects that must be retrieved from
the context.
List<String>queryTags
Response body for POST
Read Sales Transaction
Retrieve Sales Transaction API Errors (GET)
Retrieve any asynchronous error details associated with a sales transaction request.
This API returns detailed error status and a retryable payload from Place Sales Transaction API that runs asynchronously. Also, view any
blocking errors that prevent a subrequest from persisting. This request doesn’t return any non-blocking warnings, such as configuration
or tax warnings.
You can view the list of rollbackedReferenceIds, which shows synthetic or reference IDs that roll back when the batch fails.
Resource
connect/revenue/transaction-management/sales-transactions/actions/place/trackerId/errors
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue/transaction-management/sales-transactions/actions/place/16PRM0000004DBq/errors
Available version
66.0
HTTP methods
GET
Request parameter for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
66.0OptionalIndicates whether to return a subset of the
original Place Sales Transaction API
BooleanincludeRetryable
Payload
payload errors (true) or not (false).
The default value is false.
Response body for GET
Sales Transaction Async Error
1336
ResourcesTransaction Management

===== PAGE 1351 =====

Create Ramp Deal (POST)
Create a ramp deal for a customer on a product. Sales reps can use ramp deals to provide yearly deals to a customer, resulting in long-term
revenue and customer relationship. A customer can create, update, or view multiple segments of periods for their subscription term
with different attributes for each segment.
This API request creates segments based on the specified input properties such as term, segment type, and trial details. The API response
includes the context ID and the updated context object for the sales transaction. You must call the Place Sales Transaction API by
specifying this context ID to apply the ramp deal updates. See Place Sales Transaction API.
Note:  This API is applicable when you're working with line ramps. To work with ramp deals for groups, you must use the Place
Sales Transaction API and specify the groupRampActions  property.
Resource
/connect/revenue-management/sales-transaction-contexts/resourceId/actions/ramp-deal-create
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue-management/sales-transaction-contexts/0QLxx0000004CfIGAU/actions/ramp-deal-create
Available version
62.0
HTTP methods
POST
Path parameter for POST
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredID of the quote line item, order item, or
context.
StringresourceId
Request body for POST
JSON example
{
"transactionId": "0Q0xx0000004C92CAE",
"transactionLineId": "0QLxx0000004C9VGAU",
"subscriptionTerm": 14,
"subscriptionTermUnit": "MONTHS",
"trialTerm": 45,
"trialTermUnit": "DAYS",
"segmentType": "YEARLY",
"executionSettings": {
"executePricing": true,
"executeConfigRules": false
}
}
1337
ResourcesTransaction Management

===== PAGE 1352 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalSettings to run the pricing or
configuration rules.
Execution Settings
Input[]
execution
Settings
62.0RequiredType of segment that the user wants to
create. Valid values are:
StringsegmentType
• FREE_TRIAL
• CUSTOM
• YEARLY
62.0RequiredSubscription length of the term-defined
product.
Integersubscription
Term
62.0RequiredUnit of time for the subscription length.
Valid value is:
Stringsubscription
TermUnit
• MONTHS
62.0RequiredID of the sales transaction that’s
configured, such as quote or order.
Stringtransaction
Id
62.0RequiredQuote line item ID or order item ID that
the price ramp is created for.
Stringtransaction
LineId
62.0OptionalLength of the trial period, if any.IntegertrialTerm
62.0Optional. Required
if trialTerm
Unit of time for the trial period. Valid
value is:
StringtrialTerm
Unit
property is
specified.• DAYS
Response body for POST
Ramp Deal Service
Delete Ramp Deal (POST)
Delete a ramp deal to convert a ramped product to include a single quote line item or order item.
This API request deletes the segments related to the product. The API response includes the updated context with the context ID. You
must call the Place Sales Transaction (POST) API by specifying this context ID to apply the ramp deal updates. See Place Sales Transaction
(POST) API.
Note:  This API is applicable when you're working with line ramps. To work with ramp deals for groups, you must use the Place
Sales Transaction API and specify the groupRampActions  property.
1338
ResourcesTransaction Management

===== PAGE 1353 =====

Resource
/connect/revenue-management/sales-transaction-contexts/resourceId/actions/ramp-deal-delete
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue-management/sales-transaction-contexts/0QLxx0000004CfIGAU/actions/ramp-deal-delete
Available version
62.0
HTTP methods
POST
Path parameter for POST
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredID of the context.StringresourceId
Request body for POST
JSON example
{
"rampDealIds": [
"0Q0xx0000004CDxCAM",
"0QLxx0000004CSOGA2"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredRamp identifier on the quote line item or
order item.
String[]rampDealIds
Response body for POST
Ramp Deal Service
Update Ramp Deal (POST)
Modify a ramp deal in scenarios where a segment has updates such as quantity, discount, or date change.
Update a ramp deal in these scenarios.
• A segment has quantity or discount changes.
• A trial segment or custom segment has a date change. A custom segment is an added or deleted segment. In this scenario, you can
update a ramp deal during the initial sale before assetization.
1339
ResourcesTransaction Management

===== PAGE 1354 =====

This API request returns the updated context with the context ID. You must call the Place Sales Transaction (POST) API by specifying this
context ID to apply the ramp deal updates. See Place Sales Transaction (POST) API.
Note:  This API is applicable when you're working with line ramps. To work with ramp deals for groups, you must use the Place
Sales Transaction API and specify the groupRampActions  property.
Resource
/connect/revenue-management/sales-transaction-contexts/resourceId/actions/ramp-deal-update
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue-management/sales-transaction-contexts/4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9/actions/ramp-deal-update
Available version
62.0
HTTP methods
POST
Path parameter for POST
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredID of the context data that’s used to build
the pricing procedure. Get the context
StringresourceId
instance ID by invoking the Context Service
API. See Context Service (POST).
Request body for POST
JSON example
{
"executionSettings": {
"executePricing": true,
"executeConfigRules": false
},
"addedNodes": [
{
"contextNodePath": [
"4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9",// Context
ID
"0Q0xx0000004CPACA2", //Quote or Order ID
"RandomUUID" // random UUID for Quote Line Item or Order Item ID
],
"contextNode": {
"Discount": 10,
"Quantity": 5,
"ItemSegmentName": "Year 5",
"StartDate":"2024-09-07T00:00:00.000Z",
"EndDate":"2024-09-07T00:00:00.000Z"
}
}
1340
ResourcesTransaction Management

===== PAGE 1355 =====

],
"updatedNodes": [
{
"contextNodePath": [
"4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9",// Context
ID
"0Q0xx0000004CPACA2", //Quote or Order ID
"0QLxx0000004CfIGAU" // Quote Line ID or Order Line ID to update
],
"contextNode": {
"Discount": 10,
"Quantity": 5
}
}
],
"deletedNodes": [
{
"contextNodePath": [
"4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9",
"0Q0xx0000004CPACA2",
"0QLxx0000004CfIGAU" // Quote Line Item ID to delete
]
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredDetails of the nodes to be added.Context Node
Input[]
addedNodes
62.0RequiredDetails of the nodes to be deleted.Context Node
Input[]
deletedNodes
62.0OptionalSettings to run the pricing or
configuration rules.
Execution Settings
Input[]
execution
Settings
62.0RequiredDetails of the nodes to be updated.Context Node
Input[]
updatedNodes
Response body for POST
Ramp Deal Service
View Ramp Deal (GET)
View a ramp deal related to a quote line item or an order item.
This API request retrieves the segments if the ramp deal already exists.
Note:  This API is applicable when you're working with line ramps. To work with ramp deals for groups, you must use the Place
Sales Transaction API and specify the groupRampActions  property.
1341
ResourcesTransaction Management

===== PAGE 1356 =====

Resource
/connect/revenue-management/sales-transaction-contexts/resourceId/actions/ramp-deal-view
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/revenue-management/sales-transaction-contexts/0QLxx0000004CSOGA2/actions/ramp-deal-view?transactionId=0Q0xx0000004CDxCAM&transactionLineId=0QLxx0000004CSOGA2
Available version
62.0
HTTP methods
GET
Path parameter for GET
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredID of the quote line item, order item, or
context.
StringresourceId
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
62.0RequiredID of the quote or order required to
hydrate the context and retrieve the quote
lines.
StringtransactionId
62.0RequiredID of the quote or order line required to
retrieve the segmented details.
Stringtransaction
LineId
Response body for GET
Ramp Deal Service
Request Bodies
Learn more about the available API request bodies.
Amendment Input
Input representation of the details of the request to create an amendment record.
Cancellation Input
Input representation of the details of the request to cancel a quote or an order.
Create Ramp Deal Input
Input representation of the request to create a ramp deal.
1342
Request BodiesTransaction Management

===== PAGE 1357 =====

Clone Options Input
Input representation of the options to clone a sales transaction.
Clone Sales Transaction Input
Input representation of the request to clone records within a sales transaction.
Configuration Options Input
Input representation for the configuration options.
Configurator Preference Input
Input representation of the configuration preference for the place sales transaction request.
Context Input
Input representation of the context that's associated with a sales transaction for a quote or an order.
Context Node Input
Input representation of the details of the context nodes for ramp segments.
Delete Ramp Deal Input
Input representation of the request to delete a ramp deal.
Eligible Promotions Input
Input representation of the request to get eligible promotions for line items. This representation includes the details to accept line
item IDs and a sales transaction ID.
Execution Settings Input
Input representation of the execution settings for a ramp deal.
Initiate Downgrade Input
Input representation of the details of the request to initiate a downgrade action.
Initiate Swap Input
Input representation of the details of the request to initiate a swap action.
Initiate Upgrade Input
Input representation of the details of the request to initiate an upgrade action. The response includes the ID of the sales transaction
that the upgrade action creates.
Instant Pricing Input
Input representation to fetch the instant pricing details.
Object Graph Input
Input representation of an sObject with a graph ID.
Object Input Map
Input representation of an sObject record in a key-value map format.
Object with Reference Input
Input representation of a list of records to be inserted or updated. To update a record, specify the record ID.
Place Order Input
Input representation of the request to create or update an order.
Preview Approval Input
Input representation of the details of the request to preview an approval.
Place Quote Input
Input representation of the request to create or update a quote.
1343
Request BodiesTransaction Management

===== PAGE 1358 =====

Read Sales Transaction Input
Input representation of the filter criteria details to read a sales transaction.
Renewal Input
Input representation of the details of the request to initiate the renewal of an asset.
Sales Transaction Input
Input representation of the details of the request to place a sales transaction, such as a quote or an order.
Supplemental Transaction Input
Input representation of the details of the request to create a supplemental order.
Swap Group Input
Input representation of the details of the swap groupings for swap operations.
Update Ramp Deal Input
Input representation of the request to update a ramp deal.
Usage-Based Product Input
Understand the sample request structure to specify and manage usage-based products within a sales transaction.
Amendment Input
Input representation of the details of the request to create an amendment record.
JSON example
{
"assetIds": [
"02iSG0000003NMhYAM",
"02iSG0000006DvSYAU"
],
"amendmentStartDate": "2023-10-04T00:00:00",
"contractId": "800SG00000CFpepYAD",
"opportunityId": "006SG000004W5tVYAS",
"outputRecordId": "801SG00000DX1jWYAT",
"outputRecordType": "Quote",
"quantityChange": 5
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIDs of the assets that you want to add to
the amendment record.
String[]assetIds
62.0RequiredStart date of the amendment.StringamendmentStart
Date
62.0OptionalID of the Contract record that you want to
sync with the amendment quote.
StringcontractId
62.0OptionalID of the Opportunity record that you want
to sync with the amendment quote.
StringopportunityId
1344
Request BodiesTransaction Management

===== PAGE 1359 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalID of the quote or order record that you
want to add the assets to.
StringoutputRecord
Id
62.0RequiredType of amendment record that you want
to create.
Stringoutput
RecordType
62.0RequiredQuantity to add to or reduce from the
asset's existing quantity.
Doublequantity
Change
Cancellation Input
Input representation of the details of the request to cancel a quote or an order.
JSON example
{
"assetIds": [
"02iSG0000003NMhYAM",
"02iSG0000006DvSYAU"
],
"cancellationDate": "2023-10-04T00:00:00",
"contractId": "800SG00000CFpepYAD",
"opportunityId": "006SG000004W5tVYAS",
"outputRecordId": "801SG00000DX1jWYAT",
"outputRecordType": "Quote"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIDs of the assets that you want to cancel.
All assets in a request must belong to the
same price book.
String[]assetIds
62.0RequiredEffective date of the cancellation.Stringcancellation
Date
62.0OptionalID of the Contract record that you want to
sync with the cancellation quote.
StringcontractId
62.0OptionalID of the Opportunity record that you want
to sync with the cancellation quote.
StringopportunityId
62.0OptionalID of the quote or order that you want to
cancel.
Stringoutput
RecordId
62.0RequiredType of cancellation record that you want
to create.
Stringoutput
RecordType
1345
Request BodiesTransaction Management

===== PAGE 1360 =====

Create Ramp Deal Input
Input representation of the request to create a ramp deal.
JSON example
{
"transactionId": "0Q0xx0000004C92CAE",
"transactionLineId": "0QLxx0000004C9VGAU",
"subscriptionTerm": 14,
"subscriptionTermUnit": "MONTHS",
"trialTerm": 45,
"trialTermUnit": "DAYS",
"segmentType": "YEARLY",
"executionSettings": {
"executePricing": true,
"executeConfigRules": false
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalSettings to run the pricing or configuration
rules.
Execution Settings
Input[]
execution
Settings
62.0RequiredType of segment that the user wants to
create. Valid values are:
StringsegmentType
• FREE_TRIAL
• CUSTOM
• YEARLY
62.0RequiredSubscription length of the term-defined
product.
Integersubscription
Term
62.0RequiredUnit of time for the subscription length.
Valid value is:
Stringsubscription
TermUnit
• MONTHS
62.0RequiredID of the sales transaction that’s
configured, such as quote or order.
StringtransactionId
62.0RequiredQuote line item ID or order item ID that
the price ramp is created for.
Stringtransaction
LineId
62.0OptionalLength of the trial period, if any.IntegertrialTerm
62.0Optional. Required
if trialTerm
property is specified.
Unit of time for the trial period. Valid value
is:
StringtrialTermUnit
• DAYS
1346
Request BodiesTransaction Management

===== PAGE 1361 =====

Clone Options Input
Input representation of the options to clone a sales transaction.
JSON example
This is a sample request to clone all line items in a ramped group within a sales transaction.
{
"recordIds": ["0QLxx0000004CBYGA2"],
"salesTransactionId": "0Q0xx0000004CE0CAM",
"options": {
"lineScope": "AllLines"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
65.0OptionalID of the record type related to the record
to clone.
StringrecordTypeId
65.0OptionalSpecifies the scope for cloning a ramp
segment. You can clone only the last ramp
StringlineScope
segment. This property determines which
line items must be cloned and added to
the cloned segment. Valid values are:
• AllLines—Specifies whether all
line items in a ramped group must be
cloned.
• RampedLinesOnly—Specifies
whether only the ramped line items
must be cloned.
A segment identifier is created for the
newly cloned line items, ensuring date
continuity between the existing and
cloned segment.
Clone Sales Transaction Input
Input representation of the request to clone records within a sales transaction.
JSON example
This is a sample request to clone a record within a sales transaction.
{
"recordIds": ["0QLxx0000004CBYGA2"],
"salesTransactionId": "0Q0xx0000004CE0CAM"
}
1347
Request BodiesTransaction Management

===== PAGE 1362 =====

This is a sample request to clone all line items in a ramped group within a sales transaction.
{
"recordIds": ["0QLxx0000004CBYGA2"],
"salesTransactionId": "0Q0xx0000004CE0CAM",
"options": {
"lineScope": "AllLines"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
64.0RequiredID of the record to be cloned. You can
specify a single record ID only.
String[]recordIds
64.0RequiredID of the sales transaction related to the
record IDs to clone.
StringsalesTransactionId
65.0OptionalSpecifies options to clone a ramp segment
within a sales transaction. You can clone
only the last ramp segment.
Clone Options Inputoptions
Configuration Options Input
Input representation for the configuration options.
JSON example
{
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalIndicates whether to automatically add
default configurations to the order (true)
or not (false).
BooleanaddDefault
Configuration
60.0OptionalIndicates whether the order must adhere
to configuration rules during processing
(true) or bypass them (false).
Booleanexecute
Configuration
Rules
1348
Request BodiesTransaction Management

===== PAGE 1363 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalIndicates whether to run validations
related to amend, renew, or cancel
processes (true) or not (false).
BooleanvalidateAmend
RenewCancel
60.0OptionalIndicates whether the order must be
validated against the product catalog
(true) or not (false).
Booleanvalidate
Product
Catalog
Configurator Preference Input
Input representation of the configuration preference for the place sales transaction request.
JSON example
{
"configurationPref": {
"configurationMethod": "Skip",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalConfiguration method for the place sales
transaction request. Valid values are:
Stringconfiguration
Method
• Force—Specifies to enforce the
predefined configuration process
during the sales transaction process.
• Skip—Specifies to skip the
configuration process during the
quote creation process.
• System—Specifies the system to
determine whether the configuration
process is required.
The default value is Skip.
63.0OptionalConfiguration options during the ingestion
process.
Configuration
Options Input
configuration
Options
1349
Request BodiesTransaction Management

===== PAGE 1364 =====

Context Input
Input representation of the context that's associated with a sales transaction for a quote or an order.
JSON example
{
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalID of the context that represents the
created session for the sales transaction.
StringcontextId
This property is supported only for a
PATCH request.
If the contextId  property isn’t
specified, the Place Sales Transaction API
generates the context ID for the sales
transaction.
Context Node Input
Input representation of the details of the context nodes for ramp segments.
JSON example
"updatedNodes": [
{
"contextNodePath": [
"4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9", // ContextId
"0Q0xx0000004CPACA2", //Quote or OrderId
"0QLxx0000004CfIGAU" // Quote Line ID or Order Line ID to update
],
"contextNode": {
"Discount": 10,
"Quantity": 5
}
},
{
"contextNodePath": [
"4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9",
"0Q0xx0000004CPACA2",
"2b6401d144904e10aa"
],
"contextNode": {
"Discount": 20,
"Quantity": 15
1350
Request BodiesTransaction Management

===== PAGE 1365 =====

}
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredDetails of the context node to be added,
updated, or deleted.
Map<String,
Object>
contextNode
62.0RequiredPath to the context node to be added,
updated, or deleted.
String[]contextNode
Path
Delete Ramp Deal Input
Input representation of the request to delete a ramp deal.
JSON example
{
"rampDealIds": [
"0Q0xx0000004CDxCAM",
"0QLxx0000004CSOGA2"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredRamp identifier on the quote line item or
order item.
String[]rampDealIds
Eligible Promotions Input
Input representation of the request to get eligible promotions for line items. This representation includes the details to accept line item
IDs and a sales transaction ID.
JSON example
{
"salesTransactionId": "0Q0xx0000004EOECA2",
"lineItemIds": [
"0QLxx0000004E7eGAE",
"0QLxx0000004GCeGAM",
"0QLxx0000004E7gGAE"
]
}
1351
Request BodiesTransaction Management

===== PAGE 1366 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0RequiredList of line item IDs to evaluate for
promotions. The object type is
String[]lineItemIds
auto-determined from the sales
transaction ID.
66.0RequiredThe sales transaction ID, such as an order
ID or a quote ID, for the promotion
evaluation.
StringsalesTransactionId
Execution Settings Input
Input representation of the execution settings for a ramp deal.
JSON example
"executionSettings": {
"executePricing": true,
"executeConfigRules": false
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalIndicates whether to run configuration
rules (true) or not (false). The default
value is true.
Booleanexecute
ConfigRules
62.0OptionalIndicates whether to run pricing request
(true) or not (false). The default value
is true.
Booleanexecute
Pricing
Initiate Downgrade Input
Input representation of the details of the request to initiate a downgrade action.
JSON example
{
"swapStartDate": "2025-12-01T00:00:00Z",
"outputRecordType": "Quote",
"swapGroups": {
"groups": [
{
"referenceId": "DOWNGRADE-001",
"outGroup": {
"swapAssets": [
1352
Request BodiesTransaction Management

===== PAGE 1367 =====

{
"assetId": "02ixx0000004HOAAA2",
"quantity": 1
}
]
},
"inGroup": {
"graphId": "downgradeRequest",
"records": [
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"Product2Id": "01txx0000006iVlAAI",
"PricebookEntryId": "01uxx0000008ym4AAA",
"UnitPrice": 1049,
"Quantity": "1",
"StartDate": "2022-09-22"
}
}
]
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalID of the contract record for the
downgrade action.
StringcontractId
66.0OptionalID of the opportunity record for the
downgrade action.
StringopportunityId
66.0RequiredOutput record type for the downgrade
action.
StringoutputRecordType
66.0RequiredList of swap groupings that contain the
asset details for the downgrade action.
Swap Group[]swapGroups
66.0RequiredAmendment start date for the downgrade
action.
StringswapStartDate
Initiate Swap Input
Input representation of the details of the request to initiate a swap action.
1353
Request BodiesTransaction Management

===== PAGE 1368 =====

JSON example
{
"swapStartDate": "2025-12-01T00:00:00Z",
"outputRecordType": "Quote",
"swapGroups": {
"groups": [
{
"referenceId": "SWAP-001",
"outGroup": {
"swapAssets": [
{
"assetId": "02ixx0000004HOAAA2",
"quantity": 1
}
]
},
"inGroup": {
"graphId": "swapRequest",
"records": [
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"Product2Id": "01txx0000006iVlAAI",
"PricebookEntryId": "01uxx0000008ym4AAA",
"UnitPrice": 1049,
"Quantity": "1",
"StartDate": "2022-09-22"
}
}
]
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalID of the contract record for the swap
action.
StringcontractId
66.0OptionalID of the opportunity record for the swap
action.
StringopportunityId
66.0RequiredOutput record type for the swap action.StringoutputRecordType
1354
Request BodiesTransaction Management

===== PAGE 1369 =====

Available
Version
Required or
Optional
DescriptionTypeName
66.0RequiredList of swap groupings that contain the
asset details for the swap action.
Swap Group[]swapGroups
66.0RequiredAmendment start date for the swap action.StringswapStartDate
Initiate Upgrade Input
Input representation of the details of the request to initiate an upgrade action. The response includes the ID of the sales transaction that
the upgrade action creates.
JSON example
{
"swapStartDate": "2025-12-01T00:00:00Z",
"outputRecordType": "Quote",
"swapGroups": {
"groups": [
{
"referenceId": "UPGRADE-001",
"outGroup": {
"swapAssets": [
{
"assetId": "02ixx0000004HOAAA2",
"quantity": 1
}
]
},
"inGroup": {
"graphId": "upgradeRequest",
"records": [
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"Product2Id": "01txx0000006iVlAAI",
"PricebookEntryId": "01uxx0000008ym4AAA",
"UnitPrice": 1049,
"Quantity": "1",
"StartDate": "2026-03-22"
}
}
]
}
}
]
}
}
1355
Request BodiesTransaction Management

===== PAGE 1370 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalID of the contract record for the upgrade
action.
StringcontractId
66.0OptionalID of the opportunity record for the
upgrade action.
StringopportunityId
66.0RequiredOutput record type for the upgrade action.StringoutputRecordType
66.0RequiredList of swap groupings that contain the
asset details for the upgrade action.
Swap Group[]swapGroups
66.0RequiredAmendment start date for the upgrade
action.
StringswapStartDate
Instant Pricing Input
Input representation to fetch the instant pricing details.
JSON example
{
"correlationId": "1234567",
"contextId": "",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
"Name": "Test Quote Proration Pricing",
"OpportunityId": "006xx000001a4ISAAY",
"Pricebook2Id": "01sxx0000005ptpAAA"
}
},
{
"referenceId": "refQuoteLine",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "refQuote",
"PricebookEntryId": "01uxx0000008zHmAAI",
"Product2Id": "01txx0000006jmWAAQ",
"Quantity": 2,
"UnitPrice": 25,
"StartDate": "2022-09-28",
1356
Request BodiesTransaction Management

===== PAGE 1371 =====

"EndDate": "2028-09-27",
"PeriodBoundary": "ANNIVERSARY",
"BillingFrequency": "ANNUAL"
}
}
]
}
This example shows a sample request to specify grouping of lines based on criteria.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004DOSCA2",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "0QLxx0000004F3gGAE",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PUT"
},
"Quantity": 5
}
}, {
"referenceId": "0QLxx0000004F3hGAE",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PUT"
},
"Quantity": 2
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"Quantity": 5
}
},
"Name": "record"
}
1357
Request BodiesTransaction Management

===== PAGE 1372 =====

}, {
"referenceId": "GroupId2",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"Quantity": 2
}
},
"Name": "record1",
}
}
]
}
This example shows a sample request for the initial grouping of the quote with the quote lines assigned to the first group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupAll"
},
"Name": "sample"
}
}
]
}
This example shows a sample request to ungroup a quote but retain the quote lines.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
1358
Request BodiesTransaction Management

===== PAGE 1373 =====

"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "0QLxx0000004CBYGA2",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PUT"
},
"Quantity": 2,
"QuoteLineGroupId": null
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"action": "Ungroup"
}
}
}
]
}
This example shows a sample request to create a new group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST"
},
"Name": "sample"
}
}
1359
Request BodiesTransaction Management

===== PAGE 1374 =====

]
}
This example shows a sample request to delete a group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "GroupId1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"action": "DeleteGroup"
},
"Name": "sample"
}
}
]
}
This example shows a sample request to move a group.
{
"contextId": "",
"correlationId": "",
"records": [
{
"referenceId": "0Q0xx0000004CAgCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PUT"
}
}
},
{
"referenceId": "0QLxx0000004CBYGA2",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PUT"
},
"Quantity": 2
1360
Request BodiesTransaction Management

===== PAGE 1375 =====

"QuoteLineGroupId": "{@GroupId2}"
}
},
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
59.0OptionalThe ID generated by the context service.
If no context ID is provided, a new context
is created.
StringcontextId
59.0OptionalClient-generated ID for tracking multiple
related API requests.
StringcorrelationId
59.0RequiredList of pricing data to be fetched.Object with
Reference Input[]
records
Object Graph Input
Input representation of an sObject with a graph ID.
JSON example
{
"graph": {
"graphId": "1",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "POST"
}
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredThe ID of the graph.StringgraphId
60.0RequiredList of the records to be ingested.Object with
Reference Input on
page 1363[]
records
1361
Request BodiesTransaction Management

===== PAGE 1376 =====

Object Input Map
Input representation of an sObject record in a key-value map format.
JSON example
{
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "402xx000003KY5vJGH"
},
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
60.0RequiredConfiguration input for the
record process. Valid values are:
Map <String,
String>
attributes
• type—Type of sales
transaction such as Quote
or Order.
• method—HTTP methods
such as POST, PATCH, and
DELETE.
• id—Unique identifier for
the record. Required for
PATCH and DELETE
operations.
• criteria—Criteria to
group order or quote line
items. For example, group
order or quote line items
based on a monthly billing
frequency.
• action—Action to
group order or quote line
items. Valid values are:
– GroupBy
– Group
– Ungroup
1362
Request BodiesTransaction Management

===== PAGE 1377 =====

Available
Version
Required or
Optional
DescriptionTypeName
– GroupAll
– DeleteGroup
Object with Reference Input
Input representation of a list of records to be inserted or updated. To update a record, specify the record ID.
This is a sample request to create a sales transaction for an order line item.
JSON example
{
"referenceId": "refOrderItem0",
"record": {
"attributes": {
"type": "OrderItem",
"method": "POST"
},
"OrderId": "@{refOrder.id}",
"OrderActionId": "@{refOrderAction.id}",
"PricebookEntryId": "01uRM000000igZG",
"Quantity": 2
}
}
This is a sample request to update an order line item.
JSON example
{
"referenceId": "refOrderItem0",
"record": {
"attributes": {
"type": "OrderItem",
"method": "PATCH",
"id": "402xx000003KY5vJGH"
},
"OrderId": "@{refOrder.id}",
"OrderActionId": "@{refOrderAction.id}",
"PricebookEntryId": "01uRM000000igZG",
"Quantity": 2,
"UnitPrice": 800
}
}
1363
Request BodiesTransaction Management

===== PAGE 1378 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredReference ID that maps to the response
and can be used as a reference in later
StringreferenceId
subrecords. This property value starts with
a letter or number only and can contain
letters, numbers, and underscores. It's also
case-sensitive when used for referencing.
60.0RequiredDetails of a record to be ingested.Object Input Map
on page 1362
records
Place Order Input
Input representation of the request to create or update an order.
JSON example
{
"pricingPref": "System",
"configurationInput": "RunAndAllowErrors",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
},
"graph": {
"graphId": "graphId",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "POST",
"Id": "POST"
}
}
},
{
"referenceId":"refOrderItem",
"record":{
"attributes":{
"type":"OrderItem",
"method":"POST"
},
"OrderId":"@{refOrder.id}",
"OrderActionId":"@{refOrderAction.id}",
"ListPrice":"144.99",
1364
Request BodiesTransaction Management

===== PAGE 1379 =====

"Quantity":3,
"PricebookEntryId":"01uxx0000008yXPAAY",
"Product2Id":"01txx0000006i2UAAQ",
"UnitPrice":"199.49"
}
}
]
}
}
This example shows a sample request to define grouping of order items.
{
"pricingPref": "system",
"graph": {
"graphId": "placeOrder",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "801xx000003GZ9bAAG"
}
}
},
{
"referenceId": "refOlg1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST"
},
"Name": "New Group",
"OrderId": "@{refOrder.id}"
}
}
]
}
}
This example shows a sample request to ungroup order items.
{
"pricingPref": "system",
"graph": {
"graphId": "placeOrder",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
1365
Request BodiesTransaction Management

===== PAGE 1380 =====

"id": "refOrder"
}
}
},
{
"referenceId": "refOlg1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "DELETE",
"id": "refOlg1",
"action": "Ungroup"
}
}
}
]
}
}
This example shows a sample request to create a new group.
{
"pricingPref": "system",
"graph": {
"graphId": "placeOrder",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "refOrder"
}
}
},
{
"referenceId": "refOlg",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST"
},
"Name": "New Group",
"OrderId": "@{refOrder.id}"
}
}
]
}
}
This example shows a sample request to delete a group.
{
"contextId": "",
1366
Request BodiesTransaction Management

===== PAGE 1381 =====

"correlationId": "",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "refOrder"
}
}
},
{
"referenceId": "refOlg",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "DELETE",
"id": "refOlg",
"action": "DeleteGroup"
}
}
}
]
}
This example shows a sample request to group order items based on criteria.
{
"pricingPref": "system",
"graph": {
"graphId": "placeOrder",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "refOrder"
}
}
},
{
"referenceId": "g0",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"BillingFrequency2": null
}
},
"Name": "Billing Frequency: ",
1367
Request BodiesTransaction Management

===== PAGE 1382 =====

"OrderId": "@{refOrder.id}"
}
},
{
"referenceId": "g1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"BillingFrequency2": "Monthly"
}
},
"Name": "Billing Frequency: Monthly",
"OrderId": "@{refOrder.id}"
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalRate card entries defined in the catalog
that must be fetched for order items with
Stringcatalog
RatesPref
usage-based pricing during the order
creation process. Valid values are:
• Fetch—Retrieves the rate card
entries defined in the catalog for order
items during the order creation
process.
• Skip—Skips the retrieval of rate card
entries for order items during the order
creation process.
The default value is Skip.
This property is available when the
Usage-Based Selling feature is enabled.
60.0OptionalConfiguration input for the place order
process. Valid values are:
Stringconfiguration
Input
• RunAndAllowErrors—Specifies
to run the configuration and to
proceed order ingestion upon
encountering any configuration errors.
• RunAndBlockErrors—Specifies
to run configuration and to block order
1368
Request BodiesTransaction Management

===== PAGE 1383 =====

Available
Version
Required or
Optional
DescriptionTypeName
ingestion upon encountering any
configuration errors.
• Skip—Specifies to skip
configuration.
The default value is
RunAndBlockErrors.
60.0OptionalConfiguration options during the ingestion
process.
Configuration
Options Input[]
configuration
Options
60.0RequiredThe sObject graph of the order payload to
be ingested. You can perform create,
Object Graph Inputgraph
update, or delete operations on objects
from the Sales Transaction context
definition by using this property.
Additionally, perform create, update, or
delete operations on custom objects and
fields in your extended context definition.
60.0OptionalPricing preference during the create order
process. Valid values are:
StringpricingPref
• Force—Specifies to force pricing
during the order ingestion process.
• Skip—Specifies to skip pricing
during the order ingestion process.
• System—Specifies the system to
determine whether a pricing
calculation is required.
The default value is System.
Preview Approval Input
Input representation of the details of the request to preview an approval.
JSON example
{
"flowApiName": "QuoteApprovals",
"objectApiName": "Quote",
"recordId": "0Q0DU0000005HZC0A2"
}
1369
Request BodiesTransaction Management

===== PAGE 1384 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
65.0RequiredAPI name of the auto-launched flow.StringflowApiName
65.0RequiredAPI name of the object to preview the
approvals for.
StringobjectApiName
65.0RequiredID of the record to preview the approvals
for.
StringrecordId
Place Quote Input
Input representation of the request to create or update a quote.
JSON example
This example shows a sample request to create a quote.
{
"pricingPref": "System",
"configurationInput": "RunAndAllowErrors",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}, "graph": {
"graphId": "createQuote",
"records": [{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
"opportunityId": "---",
"quoteProp1": "value1",
"quoteProp2": "value2"
}
},
{
"referenceId": "refQuoteLineItem1",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteLineItemProp1": "value1",
"QuoteLineItemProp2": "value2"
}
},
{
1370
Request BodiesTransaction Management

===== PAGE 1385 =====

"referenceId": "refQuoteLineItemAttribute",
"record": {
"attributes": {
"type": "QuoteLineItemAttribute",
"method": "POST"
},
"QuoteLineItemId": "@{refQuoteLineItem1.id}",
"AttributeDefinitionId": "0tjxx0000000001AAA"
}
}
]
}
}
This example shows a sample request to insert, update, or delete a quote line item.
{
"pricingPref": "System",
"configurationInput": "skip",
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004E2mCAE"
},
"Name": "Quote_Acme"
}
},
{
"referenceId": "refQuoteLineItemToCreate1",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "0Q0xx0000004E2mCAE",
"PricebookEntryId": "01uxx0000008yXPAAY",
"Product2Id": "01txx0000006i2UAAQ",
"Quantity": 2.0,
"UnitPrice": 800.0,
"PeriodBoundary": "Anniversary",
"BillingFrequency": "Monthly",
"StartDate": "2024-03-11"
}
},
{
"referenceId": "refQuoteLineItemToPatch2",
"record": {
"attributes": {
"type": "QuoteLineItem",
1371
Request BodiesTransaction Management

===== PAGE 1386 =====

"method": "PATCH",
"id": "0Q0xx0000004E2mCAE"
},
"Quantity": 2.0,
"UnitPrice": 600.0
}
},
{
"referenceId": "refQuoteLineItemToDelete3",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "DELETE",
"id": "0Q0xx0000004E2mYLK"
}
}
}
]
}
}
This example shows a sample request to define grouping of quote line items.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
"graphId": "groupLines",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From Place Quote API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"Quantity": 1
}
},
"Name": "From Place Quote API Group",
"QuoteId": "@{refQuote.id}"
}
},
1372
Request BodiesTransaction Management

===== PAGE 1387 =====

{
"referenceId": "refQuoteItem1",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH",
"id":"0QLxx0000004DJcGAM"
},
"QuoteLineGroupId": "@{refQlg1.id}",
"Quantity": 1
}
}
]
}
}
This example shows a sample request for the initial grouping of the quote with the quote lines assigned to the first group.
{
"pricingPref": "Force",
"graph": {
"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CAmCAM"
}
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupAll"
},
"Name": "From PQ API Group",
"QuoteId": "@{refQuote.id}"
}
}
]
}
}
This example shows a sample request to ungroup a quote but retain the quote lines.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
1373
Request BodiesTransaction Management

===== PAGE 1388 =====

"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From Place Quote API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "{GroupId}",
"action": "Ungroup"
}
}
}
]
}
}
This example shows a sample request to create a new group.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From Place Quote API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST"
},
"Name": "From PQ API Group",
1374
Request BodiesTransaction Management

===== PAGE 1389 =====

"QuoteId": "@{refQuote.id}"
}
}
]
}
}
This example shows a sample request to delete a group.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "From Place Quote API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "{GroupId}",
"action": "DeleteGroup"
}
}
}
]
}
}
This example shows a sample request to move a group.
{
"pricingPref": "Force",
"configurationInput": "skip",
"graph": {
"graphId": "test",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
1375
Request BodiesTransaction Management

===== PAGE 1390 =====

"id":"0Q0xx0000004C99CAE"
},
"Name": "From PlaceQuote Api"
}
},
{
"referenceId": "0QLxx0000004CBYGA2",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH"
"id": "0QLxx0000004CBYGA2"
},
"Quantity": 2,
"QuoteLineGroupId": "@{GroupId2}"
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalRate card entries defined in the catalog
that must be fetched for quote line items
Stringcatalog
RatesPref
with usage-based pricing during the quote
creation process. Valid values are:
• Fetch—Retrieves the rate card
entries defined in the catalog for quote
line items during the quote creation
process.
• Skip—Skips the retrieval of rate card
entries for quote line items during the
quote creation process.
The default value is Skip.
This property is available when the
Usage-Based Selling feature is enabled.
60.0OptionalConfiguration input for the place quote
process. Valid values are:
Stringconfiguration
Input
• RunAndAllowErrors
• RunAndBlockErrors
• Skip
The default value is
RunAndBlockErrors.
1376
Request BodiesTransaction Management

===== PAGE 1391 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalConfiguration options during the ingestion
process.
Configuration
Options Input
configuration
Options
60.0RequiredThe sObject graph representing the quote
structure. You can perform create, update,
Object Graph Inputgraph
or delete operations on objects from the
Sales Transaction context definition by
using this property. Additionally, perform
create, update, or delete operations on
custom objects and fields in your extended
context definition.
60.0OptionalPricing preference during the quote
process. Valid values are:
StringpricingPref
• Force
• Skip
• System
The default value is System.
Read Sales Transaction Input
Input representation of the filter criteria details to read a sales transaction.
JSON example
{
"contextId": "008d27d7-e004-4906-a949-ee7d7c323c77",
"queryTags": [
"Quote",
"QuoteLineItem",
"Product"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
65.0RequiredID of the context to retrieve the data
records.
StringcontextId
65.0OptionalList of objects that must be retrieved from
the context.
List<String>queryTags
1377
Request BodiesTransaction Management

===== PAGE 1392 =====

Renewal Input
Input representation of the details of the request to initiate the renewal of an asset.
JSON example
{
"assetIds": [
"02iSG0000003NMhYAM",
"02iSG0000006DvSYAU"
],
"contractId": "800SG00000CFpepYAD",
"opportunityId": "006SG000004W5tVYAS",
"outputRecordId": "801SG00000DX1jWYAT",
"outputRecordType": "Quote",
"renewalEndDate": "2024-10-03T23:59:59",
"renewalStartDate": "2023-10-04T00:00:00"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredIDs of the assets that you want to renew.String[]assetIds
62.0OptionalID of the Contract record that you want to
sync with the renewal of the Quote or
Order record.
StringcontractId
62.0OptionalID of the Opportunity record that you want
to sync with the renewal quote.
StringopportunityId
62.0OptionalID of the Quote or Order record that you
want to renew.
Stringoutput
RecordId
62.0RequiredType of renewal record that you want to
create.
Stringoutput
RecordType
62.0OptionalEnd date of the renewal process for the
assets.
Stringrenewal
EndDate
62.0OptionalStart date of the renewal process for the
assets. Required for early asset renewals
Stringrenewal
StartDate
and renewing expired assets, using today’s
date or a future date.
Sales Transaction Input
Input representation of the details of the request to place a sales transaction, such as a quote or an order.
1378
Request BodiesTransaction Management

===== PAGE 1393 =====

JSON example
This is a sample request to create a sales transaction for a quote. This example also skips tax calculation by specifying a value for the
optional taxPref  property.
{
"pricingPref": "System",
"catalogRatesPref": "Skip",
"configurationPref": {
"configurationMethod": "Skip",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}
},
"taxPref": "Skip",
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708"
},
"graph": {
"graphId": "createQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"method": "POST",
"type": "Quote"
},
"Name": "Quote_Acme",
"Pricebook2Id": "01sDU000000JvhbYAC"
}
},
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "@{refQuote.id}",
"Product2Id": "01tDU000000F7b8YAC",
"PricebookEntryId": "01uDU000000fxt2YAA",
"UnitPrice": 100,
"Quantity": "1",
"StartDate": "2024-10-29",
"EndDate": "2025-03-01",
"PeriodBoundary": "Anniversary"
}
}
]
}
}
1379
Request BodiesTransaction Management

===== PAGE 1394 =====

This sample request assigns a TransactionProcessingType record to a quote without any additional preferences. In this example, the
TransactionType value for a record is set to a TransactionProcessingType record. See TransactionProcessingType on page 1271 tooling
object for more details.
{
"pricingPref": "Force",
"contextDetails": {
"contextId": "f1c9e3e1c335f7959a88de09d3a867cc2b95e08709b99de8e2edeb8f5039e8ed",
"scope": "Session"
},
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
"OpportunityId": "006xx000001a2oWAAQ",
"PriceBook2Id": "01sxx0000005ptpAAA",
"TransactionType": "SkipPricingAndRunTax",
"Name": "Quote_No_Tax_System"
}
},
{
"referenceId": "refQLI1",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "@{refQuote.id}",
"UnitPrice": 49.99,
"Product2Id": "01txx0000006i2aAAA",
"PricebookEntryId": "01uxx0000008yX0AAI",
"Quantity": 10
}
}
]
}
}
This is a sample request to insert, update, or delete a quote line item.
{
{
"pricingPref": "System",
"catalogRatesPref": "Skip",
"configurationPref": {
"configurationMethod": "Skip",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
1380
Request BodiesTransaction Management

===== PAGE 1395 =====

"executeConfigurationRules": true,
"addDefaultConfiguration": true
}
},
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708"
},
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"method": "PATCH",
"type": "Quote",
"id": "801xx000003GZ9bAAG"
}
}
},
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH",
"id": "402xx000003KY5vJGH"
},
"Quantity": "5"
}
}
]
}
}
This is a sample request to define grouping of quote line items.
{
"pricingPref": "Force",
"catalogRatesPref": "Skip",
"configurationPref": {
"configurationMethod": "Skip",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
"addDefaultConfiguration": true
}
},
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708"
},
"graph": {
"graphId": "groupQuoteLines",
"records": [
1381
Request BodiesTransaction Management

===== PAGE 1396 =====

{
"referenceId": "refQuote",
"record": {
"attributes": {
"method": "PATCH",
"type": "Quote",
"id": "801xx000003GZ9bAAG"
}
}
},
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "PATCH",
"id": "402xx000003KY5vJGH"
},
"QuoteLineGroupId": "@{refQuote.id}"
}
}
]
}
}
This is s a sample request for the initial grouping of the quote with all the quote lines assigned to the first group.
{
"pricingPref": "Force",
"catalogRatesPref": "Skip",
"graph": {
"graphId": "groupQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CAmCAM"
}
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST",
"action": "GroupAll"
},
"Name": "From PST API Group",
"QuoteId": "@{refQuote.id}"
}
}
1382
Request BodiesTransaction Management

===== PAGE 1397 =====

]
}
}
This is a sample request to ungroup a quote but retain the quote lines.
{
"catalogRatesPref": "Skip",
"pricingPref": "Force",
"graph": {
"graphId": "ungroupQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "Grouped Quote with PST API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "402xx000003KY5vJGH",
"action": "Ungroup"
}
}
}
]
}
}
This is a sample request to create a new group.
{
"catalogRatesPref": "Skip",
"pricingPref": "Force",
"graph": {
"graphId": "createGroup",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "Grouped Quote with PST API"
1383
Request BodiesTransaction Management

===== PAGE 1398 =====

}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "POST"
},
"Name": "From PQ API Group",
"QuoteId": "@{refQuote.id}"
}
}
]
}
}
This example shows a sample request to delete a group.
{
"catalogRatesPref": "Skip",
"pricingPref": "Force",
"graph": {
"graphId": "deleteGroup",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id":"0Q0xx0000004C99CAE"
},
"Name": "Grouped Quote with PST API"
}
},
{
"referenceId": "refQlg1",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "402xx000003KY5vJGH",
"action": "DeleteGroup"
}
}
}
]
}
}
This is a sample request to group order items based on criteria.
{
"catalogRatesPref": "Skip",
1384
Request BodiesTransaction Management

===== PAGE 1399 =====

"pricingPref": "Force",
"graph": {
"graphId": "groupOrderItems",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "0Q0xx0000004C99CAE"
}
}
},
{
"referenceId": "refOlg1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"BillingFrequency2": null
}
},
"Name": "Billing Frequency: ",
"OrderId": "@{refOrder.id}"
}
},
{
"referenceId": "g1",
"record": {
"attributes": {
"type": "OrderItemGroup",
"method": "POST",
"action": "GroupBy",
"criteria": {
"BillingFrequency2": "Monthly"
}
},
"Name": "Billing Frequency: Monthly",
"OrderId": "@{refOrder.id}"
}
}
]
}
}
This is a sample request to save changes to a ramp deal by using context ID. The context ID is returned by the Ramp Deal APIs. See
Create Ramp Deal (POST).
{
"pricingPref": "Force",
"contextDetails": {
"contextId": "f1c9e3e1c335f7959a88de09d3a867cc2b95e08709b99de8e2edeb8f5039e8ed",
1385
Request BodiesTransaction Management

===== PAGE 1400 =====

"scope": "Session"
},
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004DQ4CAM"
}
}
}
]
}
}
To see examples that specify actions to create ramp deals for groups, see Group Ramp Action Input on page 1388.
To see examples that apply to usage-based products, see Usage-Based Product Input on page 1398.
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalRate card entries defined in the catalog
that must be fetched for sales items with
StringcatalogRates
Pref
usage-based pricing during the creation
of the sales transaction. Valid values are:
• Fetch—Retrieves the rate card
entries defined in the catalog for sales
items during the creation of the sales
transaction.
• Skip—Skips the retrieval of rate card
entries for sales items during the
creation of the sales transaction.
The default value is Skip.
This property is available when the
Usage-Based Selling feature is enabled.
63.0OptionalConfiguration preference during the quote
process. These preferences ensure that
quotes are defined as per the requirement.
Configurator
Preference Input
configuration
Pref
63.0Required if the
graph  property
isn’t specified.
Context details that are created for a sales
transaction.
Context InputcontextDetails
1386
Request BodiesTransaction Management

===== PAGE 1401 =====

Available
Version
Required or
Optional
DescriptionTypeName
63.0Required if the
contextDetails
The sObject graph of the sales transaction
to be ingested. You can perform create,
Object Graph Inputgraph
property isn’t
specified.
update, or delete operations on objects
from the Sales Transaction context
definition by using this property.
Additionally, perform create, update, or
delete operations on custom objects and
fields in your extended context definition.
To create custom objects that are at the
grandchildren level from a line item, you
must create the hierarchy of objects until
the grandchild object in the same request.
65.0OptionalSpecifies the action that you want to
perform on group ramp segments. You
StringgroupRampAction
can also convert a non-ramped group into
a ramped group. Valid values are:
• AddProducts—Adds rampable
products to group ramp segments.
• DeleteProducts—Deletes
ramped products.
• EditGroup—Converts a
non-ramped group into a group ramp
segment, or edit group ramp segment
attributes such as name and
description, except the start and end
dates.
• EditRampSchedule—Edits
details of the group ramp segments,
including start and end dates.
• DeleteSegment—Deletes the first
or last segment in a group ramp
schedule.
• ConvertToNonRampedGroup—Converts
the first or last group ramp segment
into a non-ramped group.
To add or delete ramped line items from
multiple group ramp segments, specify
the applicable values in the graph
property. See Group Ramp Action Input
on page 1388 to refer to examples.
1387
Request BodiesTransaction Management

===== PAGE 1402 =====

Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalPricing preference during the creation of
a sales transaction. Valid values are:
StringpricingPref
• Force—Enforces pricing during the
creation of sales transactions.
• Skip—Skips pricing during the
creation of sales transactions.
• System—Determines whether a
pricing calculation is required.
The default value is System.
65.0OptionalSpecifies whether to execute or skip the
tax calculation step for each sales
StringtaxPref
transaction record. Valid value is Skip. If
you don't specify this value, then tax
calculation request is performed by default.
Group Ramp Action Input
Understand the sample request to specify group ramp actions during initial sale.
Group Ramp Action Input
Understand the sample request to specify group ramp actions during initial sale.
Keep these considerations in mind when you specify ramp actions.
• Use the Clone Sales Transaction API to clone a ramp segment, and specify the clone option.
• Use the Place Sales Transaction API to specify a group ramp action by using the groupRampAction property. You can refer to
the sections in this topic for examples.
JSON example to edit a group
This is a sample request that creates the first ramp segment. This request accepts IDs of a quote and quote line group. Additionally,
the request accepts attributes of quote line group such as IsRamped, SegmentType, StartDate, and EndDate. A ramp
segment is created with a ramp identifier and segment identifier added to all the quote line items available in the ramp segment.
This process converts a group into a segment, which becomes the first segment in the ramp schedule. A quote can contain a single
ramp schedule only. To create another segment in the ramp schedule, use the Clone Sales Transaction API.
{
"groupRampAction": "EditGroup",
"pricingPref": "System",
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "0Q0xx0000004CYqCAM",
"record": {
"attributes": {
1388
Request BodiesTransaction Management

===== PAGE 1403 =====

"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CYqCAM"
}
}
},
{
"referenceId": "1C9xx0000004CVcCAM",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "PATCH",
"id": "1C9xx0000004CVcCAM"
},
"StartDate": "2025-05-01",
"EndDate": "2025-06-30",
"SortOrder": 1,
"IsRamped": true,
"SegmentType": "Custom"
}
}
]
}
}
JSON example to edit a ramp segment
This is a sample request to edit multiple ramp segments simultaneously, maintaining date continuity among ramp segments.
{
"groupRampAction": "EditRampSchedule",
"pricingPref": "System",
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "0Q0xx0000004CYqCAM",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CYqCAM"
}
}
},
{
"referenceId": "1C9xx0000004CVcCAM",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "PATCH",
"id": "1C9xx0000004CVcCAM"
},
"StartDate": "2025-05-01",
"EndDate": "2025-06-30"
}
1389
Request BodiesTransaction Management

===== PAGE 1404 =====

},
{
"referenceId": "1C9xx0000004CVcAAM",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "PATCH",
"id": "1C9xx0000004CVcAAM"
},
"StartDate": "2025-07-01",
"EndDate": "2025-08-30"
}
},
{
"referenceId": "1C9xx0000004CVcBAM",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "PATCH",
"id": "1C9xx0000004CVcBAM"
},
"StartDate": "2025-09-01",
"EndDate": "2025-10-30"
}
}
]
}
}
JSON example to add a product
This is a sample request to add a product to the current and subsequent segments. A ramp identifier and segment identifier are
added to the quote line items.
{
"groupRampAction": "AddProducts",
"pricingPref": "System",
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "0Q0xx0000004CKKCA2",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CKKCA2"
}
}
},
{
"referenceId": "1C9xx0000004CCGCA2",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "PATCH",
1390
Request BodiesTransaction Management

===== PAGE 1405 =====

"id": "1C9xx0000004CCGCA2"
}
}
},
{
"referenceId": "ref_01txx0000006iCXAAY_0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST",
"id": "ref_01txx0000006iCXAAY_0"
},
"QuoteId": "@{0Q0xx0000004CKKCA2.id}",
"Id": "ref_01txx0000006iCXAAY_0",
"UnitPrice": 2000,
"Product2Id": "01txx0000006iCXAAY",
"PricebookEntryId": "01uxx0000008yciAAA",
"Quantity": 1,
"StartDate": "2025-05-28T00:00:00.000Z",
"BillingFrequency": null,
"PeriodBoundary": null,
"QuoteLineGroupId": "1C9xx0000004CCGCA2"
}
},
{
"referenceId": "1C9xx0000004CCGCAB",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "PATCH",
"id": "1C9xx0000004CCGCAB"
}
}
},
{
"referenceId": "ref_01txx0000006iCXABY_0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST",
"id": "ref_01txx0000006iCXABY_0"
},
"QuoteId": "@{0Q0xx0000004CKKCA2.id}",
"Id": "ref_01txx0000006iCXAAY_0",
"UnitPrice": 2000,
"Product2Id": "01txx0000006iCXAAY",
"PricebookEntryId": "01uxx0000008yciAAA",
"Quantity": 1,
"StartDate": "2025-05-28T00:00:00.000Z",
"BillingFrequency": null,
"PeriodBoundary": null,
"QuoteLineGroupId": "1C9xx0000004CCGCAB"
}
}
1391
Request BodiesTransaction Management

===== PAGE 1406 =====

]
}
}
JSON example to delete a product
This is a sample request to delete a product from the current and subsequent ramp segments.
{
"pricingPref": "System",
"groupRampAction": "DeleteProducts",
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "0Q0SG000000L5r70AC",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0SG000000L5r70AC"
}
}
},
{
"referenceId": "0QLSG000000WuTh4AK",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "DELETE",
"id": "0QLSG000000WuTh4AK"
}
}
},
{
"referenceId": "0QLSG000000WuTh4BK",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "DELETE",
"id": "0QLSG000000WuTh4AK"
}
}
}
]
}
}
JSON example to delete a segment
This is a sample request to delete the first and last segment in a ramp schedule. The API throws an error if the specified segment
isn't the first and last segment, ensuring there are no gaps between quote line items in different ramp segments.
{
"pricingPref": "System",
"groupRampAction": "DeleteSegment",
"graph": {
1392
Request BodiesTransaction Management

===== PAGE 1407 =====

"graphId": "updateQuote",
"records": [
{
"referenceId": "0Q0xx0000004CfICAU",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CfICAU"
}
}
},
{
"referenceId": "1C9xx0000004FjcCAE",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "DELETE",
"id": "1C9xx0000004FjcCAE",
"action": "DeleteGroup"
}
}
}
]
}
}
JSON example to remove a segment from a ramp schedule
This is a sample request to remove the first or last ramp segment in a ramp schedule. This request removes the ramp-specific fields
from a quote line group such as IsRamped  and SegmentType. Additionally, this request removes the RampIdentifier
and SegmentIdentifier  fields from a quote line item.
{
"pricingPref": "System",
"groupRampAction": "ConvertToNonRampedGroup",
"graph": {
"graphId": "updateQuote",
"records": [
{
"referenceId": "0Q0xx0000004CfICAU",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CfICAU"
}
}
},
{
"referenceId": "1C9xx0000004FjcCAE",
"record": {
"attributes": {
"type": "QuoteLineGroup",
"method": "PATCH",
1393
Request BodiesTransaction Management

===== PAGE 1408 =====

"id": "1C9xx0000004FjcCAE"
}
}
}
]
}
}
Supplemental Transaction Input
Input representation of the details of the request to create a supplemental order.
JSON example
This sample creates a supplemental order, which is a clone of the original order. The supplemental order is related to the original
order.
{
"relatedSalesTransactionId": "801S70000001VKgIAM"
}
This sample overrides a field value of an order line item to supplement the order item with ID value as 802SG000003vZ15YAE.
{
"relatedSalesTransactionId": "801S70000001VKgIAM",
"pricingPref": "System",
"supplementalGraph": {
"graphId": "1",
"records": [
{
"referenceId": "refOrder",
"record": {
"attributes": {
"type": "Order",
"method": "PATCH",
"id": "801S70000001VKgIAM"
},
"EffectiveDate": "2025-03-01",
"QuoteId": "0Q0xx0000004DQ4CAM"
}
},
{
"referenceId": "refOrderItem",
"record": {
"attributes": {
"type": "OrderItem",
"method": "PATCH",
"id": "802SG000003vZ15YAE"
},
"QuoteLineItemId": "0Q0xx0000004E2mYLK"
}
}
]
}
}
1394
Request BodiesTransaction Management

===== PAGE 1409 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
64.0OptionalPricing preference for this supplemental
transaction or order ingestion process.
Valid values are:
StringpricingPref
• Force—Enforces pricing during the
creation of sales transactions.
• Skip—Skips pricing during the
creation of sales transactions.
• System—Determines whether a
pricing calculation is required.
If pricingPref  value is defined as
either Force  or System, the
supplemental order can have a different
pricing from the original order.
64.0RequiredRelated or the original sales transaction
upon which a supplemental transaction is
created.
StringrelatedSales
TransactionId
64.0OptionalThe sObject graph that represents a
payload with the additional changes to be
ingested.
Object Graph Inputsupplemental
Graph
The attribute's HTTP method must be
PATCH. The attribute ID must be the ID of
the original order or order item that you
want to supplement.
Swap Group Input
Input representation of the details of the swap groupings for swap operations.
JSON example
{
"swapGroups": {
"groups": [
{
"referenceId": "SWAP-001",
"outGroup": {
"swapAssets": [
{
"assetId": "02ixx0000004HOAAA2",
"quantity": 1
}
]
1395
Request BodiesTransaction Management

===== PAGE 1410 =====

},
"inGroup": {
"graphId": "swapRequest",
"records": [
{
"referenceId": "refQuoteLine0",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"Product2Id": "01txx0000006iVlAAI",
"PricebookEntryId": "01uxx0000008ym4AAA",
"UnitPrice": 1049,
"Quantity": "1",
"StartDate": "2022-09-22"
}
}
]
}
}
]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0RequiredGroup of products to include in the swap
operation. These objects are supported.
ObjectinGroup
• QuoteLineItem
• OrderItem
66.0RequiredGroup of assets to exclude from the swap
operation. This API doesn’t support string
Swap Group[]outGroup
values for properties, such as quantity and
price.
66.0RequiredReference ID to refer to the swap group
details that this operation represents.
StringreferenceId
Update Ramp Deal Input
Input representation of the request to update a ramp deal.
JSON example
{
"executionSettings": {
"executePricing": true,
1396
Request BodiesTransaction Management

===== PAGE 1411 =====

"executeConfigRules": false
},
"addedNodes": [
{
"contextNodePath": [
"4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9", // Context
ID
"0Q0xx0000004CPACA2", //Quote or Order ID
"RandomUUID" // random UUID for Quote Line Item or Order Item ID
],
"contextNode": {
"Discount": 10,
"Quantity": 5,
"ItemSegmentName": "Year 5",
"StartDate":"2024-09-07T00:00:00.000Z",
"EndDate":"2024-09-07T00:00:00.000Z"
}
}
],
"updatedNodes": [
{
"contextNodePath": [
"4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9", // Context
ID
"0Q0xx0000004CPACA2", //Quote or Order ID
"0QLxx0000004CfIGAU" // Quote Line ID or Order Line ID to update
],
"contextNode": {
"Discount": 10,
"Quantity": 5
}
}
],
"deletedNodes": [
{
"contextNodePath": [
"4f23961a5c98806f89305e064c67b397e93f1bb8a2a7a3a80db506f1d4110ee9",
"0Q0xx0000004CPACA2",
"0QLxx0000004CfIGAU" // Quote Line Item ID to delete
]
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredDetails of the nodes to be added.Context Node
Input[]
addedNodes
62.0RequiredDetails of the nodes to be deleted.Context Node
Input[]
deletedNodes
1397
Request BodiesTransaction Management

===== PAGE 1412 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalSettings to run the pricing or configuration
rules.
Execution Settings
Input[]
execution
Settings
62.0RequiredDetails of the nodes to be updated.Context Node
Input[]
updatedNodes
Usage-Based Product Input
Understand the sample request structure to specify and manage usage-based products within a sales transaction.
JSON example to create a quote record with default rates and default grants
The example shows a sample request to creates these records with these updates.
• Quote—Creates the main quote record with default rates and default grants.
• Quote Line Item—Adds a product to the quote.
• Rate Card Entry—Links default pricing from rate card. When NegotiatedRate  property value is null, the rate card
price is used.
• Usage Grant—Allocates all default grants.
{
"pricingPref": "system",
"configurationPref": {
"configurationMethod": "skip",
"configurationOptions": {
"validateProductCatalog": false,
"validateAmendRenewCancel": false,
"executeConfigurationRules": false,
"addDefaultConfiguration": false
}
},
"graph": {
"graphId": "graphId",
"records": [
{
"referenceId": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
"Name": "Q-2024-001",
"QuoteAccountId": "001xx000003DHP0AAO",
"OpportunityId": "006xx000004TmiGAAS",
"Status": "Draft",
"Pricebook2Id": "01sxx0000001SGEAA2"
}
},
{
"referenceId": "refQuoteLineItem",
"record": {
1398
Request BodiesTransaction Management

===== PAGE 1413 =====

"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "@{refQuote.id}",
"Product2Id": "01txx0000001SGEAA2",
"StartDate": "2024-10-29",
"PeriodBoundary": "Anniversary",
"EndDate": "2027-03-01",
"PricebookEntryId": "01uxx0000001SGEAA2",
"UnitPrice": 100,
"Quantity": 1
}
},
{
"referenceId": "refRateCardEntry",
"record": {
"attributes": {
"type": "QuoteLineRateCardEntry",
"method": "POST"
},
"RateCardEntryId": "1CJxx0000004CXEGA2",
"NegotiatedRate": null,
"QuoteLineItemId": "@{refQuoteLineItem.id}"
}
}
]
}
}
JSON example to specify negotiated grants
This example shows a sample response to create a QuotLineItmUseRsrcGrant record that links a quote line item to a product usage
grant for usage-based products. This request performs these updates.
• Associates a usage grant with a quote line item.
• Allocates a quantity of usage resources.
• Applies a usage policy that defines how the resources can be consumed.
• Links to a base product usage grant that defines the grant structure.
{
"pricingPref": "system",
"configurationPref": {
"configurationMethod": "skip",
"configurationOptions": {
"validateProductCatalog": false,
"validateAmendRenewCancel": false,
"executeConfigurationRules": false,
"addDefaultConfiguration": false
}
},
"graph": {
"graphId": "graphId",
"records": [
{
1399
Request BodiesTransaction Management

===== PAGE 1414 =====

"referenceId": "ref1CJxx0000004CXGGA2",
"record": {
"attributes": {
"type": "QuotLineItmUseRsrcGrant",
"method": "POST"
},
"GrantQuantity": 4,
"ProductUsageResourcePolicyId": "7Suxx0000004C92CAE",
"QuoteLineItemId": "0QLxx0000004CnMGAU",
"ProductUsageGrantId": "1BXxx0000004C92GAE"
}
}
]
}
}
This example shows a sample response to update the previously created QuotLineItmUseRsrcGrant record with additional units,
which is specified by using the GrantQuantity  property. The quote line item now has 97 units of usage resource allocation.
{
"pricingPref": "system",
"configurationPref": {
"configurationMethod": "skip",
"configurationOptions": {
"validateProductCatalog": false,
"validateAmendRenewCancel": false,
"executeConfigurationRules": false,
"addDefaultConfiguration": false
}
},
"graph": {
"graphId": "graphId",
"records": [
{
"referenceId": "ref1X6xx000000003GCAQ",
"record": {
"attributes": {
"method": "PATCH",
"type": "QuotLineItmUseRsrcGrant",
"id": "1X6xx000000003GCAQ"
},
"GrantQuantity": 97
}
}
]
}
}
JSON example to specify tiered pricing and usage grants
This example shows a sample request to update an existing quote with tiered pricing and usage grants. This request sets up a
multi-tier rate structure and updates a usage grant quantity along with these additional updates.
• Creates a base rate card entry with a negotiated rate of 10. Sets the base price for the quote line item.
• Creates a second rate card entry for tiered pricing without any negotiated rate. The default rate card is used. This rate card entry
is the base for tier adjustments.
1400
Request BodiesTransaction Management

===== PAGE 1415 =====

• Creates a tier adjustment for quantities 0 through 50 and adds $5 adjustment to the base rate.
• Creates a tier adjustment for quantities 50 through 100 and adds an adjustment of $10.
• Updates an existing usage resource grant record to set grant quantity to 150 units.
For example, if an order is placed for 75 units, the base rate is $10. As tier 2 is applicable for this order, an adjustment of $10 is
applicable. The final price per unit is $20 with a total of $1500 for 75 units.
{
"pricingPref": "system",
"configurationPref": {
"configurationMethod": "skip",
"configurationOptions": {
"validateProductCatalog": false,
"validateAmendRenewCancel": false,
"executeConfigurationRules": false,
"addDefaultConfiguration": false
}
},
"graph": {
"graphId": "graphId",
"records": [
{
"referenceId": "refLineItemParent",
"record": {
"attributes": {
"type": "Quote",
"method": "PATCH",
"id": "0Q0xx0000004CXEGA2"
}
}
},
{
"referenceId": "ref1",
"record": {
"attributes": {
"type": "QuoteLineRateCardEntry",
"method": "POST"
},
"RateCardEntryId": "1CJxx0000004CXEGA2",
"NegotiatedRate": 10,
"QuoteLineItemId": "0QLxx0000004Eh6GAE"
}
},
{
"referenceId": "refTierRateCardEntry0",
"record": {
"attributes": {
"type": "QuoteLineRateCardEntry",
"method": "POST"
},
"RateCardEntryId": "1CJxx0000004CXFGA2",
"QuoteLineItemId": "0QLxx0000004Eh6GAE"
}
},
1401
Request BodiesTransaction Management

===== PAGE 1416 =====

{
"referenceId": "refTier0",
"record": {
"attributes": {
"type": "QuoteLineRateAdjustment",
"method": "POST"
},
"Name": "Tier 1",
"AdjustmentType": "Amount",
"AdjustmentValue": 5,
"LowerBound": 0,
"UpperBound": 50,
"QuoteLineRateCardEntryId": "@{refTierRateCardEntry0.id}"
}
},
{
"referenceId": "refTier1",
"record": {
"attributes": {
"type": "QuoteLineRateAdjustment",
"method": "POST"
},
"Name": "Tier 2",
"AdjustmentType": "Amount",
"AdjustmentValue": 10,
"LowerBound": 50,
"UpperBound": 100,
"QuoteLineRateCardEntryId": "@{refTierRateCardEntry0.id}"
}
},
{
"referenceId": "refTier2",
"record": {
"attributes": {
"type": "QuoteLineRateAdjustment",
"method": "POST"
},
"Name": "Tier 3",
"AdjustmentType": "Amount",
"AdjustmentValue": 15,
"LowerBound": 100,
"UpperBound": 150,
"QuoteLineRateCardEntryId": "@{refTierRateCardEntry0.id}"
}
},
{
"referenceId": "refGt2xzdUP",
"record": {
"attributes": {
"type": "QuotLineItmUseRsrcGrant",
"method": "PATCH",
"id": "1X6xx000000003GCAQ"
},
"GrantQuantity": 150
1402
Request BodiesTransaction Management

===== PAGE 1417 =====

}
}
]
}
}
Response Bodies
Learn more about the available response bodies.
Amendment
Output representation of the details of an amendment record.
ARC Base Error
Output representation of the error response related to the amendment, renewal, or cancellation of assets.
Cancellation
Output representation of the details of a cancellation record.
Clone Sales Transaction
Output representation for the result of cloning records within a sales transaction.
Clone Sales Transaction Error Response
Output representation of the errors that occur during the clone sales transaction operation.
Eligible Promotions Response
Output representation of the details of the eligible promotions.
Initiate Downgrade Response
Output representation of the request to initiate a downgrade action.
Initiate Swap Response
Output representation of the request to initiate a swap action. The response includes the ID of the sales transaction that the swap
action creates.
Initiate Upgrade Response
Output representation of the request to initiate an upgrade action. The response includes the ID of the sales transaction that the
upgrade action creates.
Instant Pricing
Output representation containing the results of the instant pricing request.
Object Reference
Output representation of an sObject with a reference ID along with any potential error.
Place Order Error Response
Output representation of the error response for the place order request.
Place Order Response
Output representation of the request to create or update an order.
Place Quote Error Response
Output representation of the error responses of a place quote request.
Place Quote
Output representation of the request to create or update a quote.
1403
Response BodiesTransaction Management

===== PAGE 1418 =====

Sales Transaction Async Error
Output representation of the details of errors encountered during the async processing of the Place Sales Transaction API request.
Preview Approval
Output representation of the details of a preview approval request.
Preview Approval Chain Item
Output representation of the details of an approval chain item for a specific group.
Preview Approval Error
Output representation of the error details associated with the Preview Approval API.
Preview Approval Item
Output representation of the details of a specific approval item with an approval chain.
Promotion Coupon
Output representation of the details of a coupon that's eligible for the recommended promotion.
Promotion Coupon Availability
Output representation of the details of the coupon that's eligible for the promotion. Additionally, this representation specifies the
reason for any coupon ineligibility.
Promotion Details Response
Output representation of the eligible promotion and its details. This representation includes details of any coupons, eligibility rules,
and terms and conditions.
Promotion Limit
Output representation of the details of the promotion limit of an eligible promotion.
Promotion Reward Details
Output representation of the details of the rewards of an eligible promotion rule.
Promotion Rules List
Output representation of the details of the rules of an eligible promotion.
Ramp Deal Service Error Response
Output representation of the details of errors encountered during the processing of the API request.
Ramp Deal Service
Output representation of the details of a created, updated, or deleted ramp deal.
Read Sales Transaction
Output representation of the request to read a sales transaction.
Read Sales Transaction Records
Output representation of the details of a map of keys and associated values. The keys are record type names, such as a Quote or
QuoteLineItem, and values are lists of records of that type.
Renewal
Output representation of the details of a renewal record.
Sales Transaction
Output representation of the request to create a sales transaction.
Sales Transaction Context
Output representation of the context details that are associated with a sales transaction.
Sales Transaction Error Response
Output representation of the error details associated with the API request.
1404
Response BodiesTransaction Management

===== PAGE 1419 =====

Sales Transaction Record
Generic output representation for any sales transaction record type.
Supplemental Transaction Error Response
Output representation of the error details associated with the Place Supplemental Transaction API.
Supplemental Transaction
Output representation of the details of the created supplemental order.
Amendment
Output representation of the details of an amendment record.
JSON example
{
"amendmenRecordId": "0Q0xx0000004NsSCAU",
"errors": [
{
"errorCode": "REQUIRED_FIELD_MISSING",
"errorMessage": "Specify a value for quantityChange, and try again."
}
],
"requestId": "16Pxx0000004NIy",
"success": true
}
Properties
Available
Version
Filter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0ID of the amendment record that’s created
for a quote or an order.
Stringamendment
RecordId
62.0Small, 62.0Error responses if the creation of an
amendment record fails.
ARC Base Error on
page 1405[]
errors
62.0Small, 62.0Request ID that’s used to track an async
request.
StringrequestId
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
ARC Base Error
Output representation of the error response related to the amendment, renewal, or cancellation of assets.
"errors": [
{
"errorCode": "REQUIRED_FIELD_MISSING",
"errorMessage": "Specify a value for quantityChange, and try again."
}
]
1405
Response BodiesTransaction Management

===== PAGE 1420 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Big, 62.0Code for the resultant error.StringerrorCode
62.0Big, 62.0Error message for the resultant error.StringerrorMessage
Cancellation
Output representation of the details of a cancellation record.
JSON example
{
"cancellationRecordId": "0Q0xx0000004NsSCAU",
"errors": [
{
"errorCode": "REQUIRED_FIELD_MISSING",
"errorMessage": "Specify a value for quantityChange, and try again."
}
],
"requestId": "16Pxx0000004NIy",
"success": true
}
Properties
Available
Version
Filter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0ID of the cancellation record that’s created
for a quote or an order.
Stringcancellation
RecordId
62.0Small, 62.0Error responses if the creation of a
cancellation record fails.
ARC Base Error on
page 1405[]
errors
62.0Small, 62.0Request ID that’s used to track the async
request.
StringrequestId
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
Clone Sales Transaction
Output representation for the result of cloning records within a sales transaction.
JSON example
This example shows a sample of a successful response.
{
"requestId": "9356bcbf04f06e22360a09807c13e1d4e395",
"salesTransactionId": "0Q0SG000000ACxf0AG",
"errors": [],
1406
Response BodiesTransaction Management

===== PAGE 1421 =====

"success": true
}
This example shows a sample error response.
{
"requestId": "9356bcbf04f06e22360a09807c13e1d4e395",
"salesTransactionId": "0Q0SG000000ACxf0AG",
"errors": [
{
"errorCode": "INVALID_API_INPUT",
"message": "Specify only one record",
"referenceId": "0QLxx0000004CBYGA2"
}
],
"success": false
}
Properties
Available VersionDescriptionTypeName
64.0Request ID of the process that can be used to query
the async status.
StringrequestId
64.0ID of the quote line item, order item, quote line
group, or order item group record.
StringsalesTransactionId
64.0Indicates whether the synchronous part of the
processing is successful (true) or not (false).
Booleansuccess
64.0List of errors encountered during synchronous
processing.
Clone Sales Transaction
Error Response[]
errors
Clone Sales Transaction Error Response
Output representation of the errors that occur during the clone sales transaction operation.
JSON example
{
"errors": [
{
"errorCode": "INVALID_API_INPUT",
"message": "Specify only one record",
"referenceId": "0QLxx0000004CBYGA2"
}
]
}
Properties
Available VersionDescriptionTypeName
64.0Code associated with the error.StringerrorCode
1407
Response BodiesTransaction Management

===== PAGE 1422 =====

Available VersionDescriptionTypeName
64.0Message associated with the error.Stringmessage
64.0Reference ID associated with the error.StringreferenceId
Eligible Promotions Response
Output representation of the details of the eligible promotions.
JSON example
{
"eligiblePromotions": [
{
"additionalPromotionFields": {},
"couponDetails": {
"coupon": {
"couponCode": "COUPON_002",
"endDateTime": null,
"startDateTime": "2025-10-08T19:00:00.000Z",
"status": "Active"
},
"couponAvailabilityMessage": null
},
"currencyIsoCode": "USD",
"description": "15% on Accessories",
"displayName": "Comms Manual Promotion 15% on Accessories",
"endDateTime": null,
"isAutomatic": false,
"priorityNumber": null,
"promotionCode": null,
"promotionEligibleRules": [
{
"ruleName": "CommsAutoPromotionRule",
"rulePriority": 1,
"ruleRewards": [
{
"rewardDetails": {
"discountLevel": "Line",
"discountType": "PercentageOff",
"discountValue": "10.0",
"discountAppliedAt": "LineItem",
"discountCategory": "Accessories"
},
"rewardType": "ProvideDiscount"
}
]
}
],
"promotionId": "0c8DX00000001UeYAI",
"promotionLimits": [],
"startDateTime": "2025-07-01T17:02:00.000Z",
"termsAndCondition": "&lt;p&gt;test&lt;/p&gt;"
1408
Response BodiesTransaction Management

===== PAGE 1423 =====

},
{
"additionalPromotionFields": {},
"couponDetails": {
"coupon": {
"couponCode": "COUPON_001",
"endDateTime": null,
"startDateTime": null,
"status": "Active"
},
"couponAvailabilityMessage": null
},
"currencyIsoCode": "USD",
"description": "Promo_Printer_Child",
"displayName": "Promo_Printer_Child",
"endDateTime": null,
"isAutomatic": false,
"priorityNumber": null,
"promotionCode": null,
"promotionEligibleRules": [
{
"ruleName": "Rule001",
"rulePriority": 1,
"ruleRewards": [
{
"rewardDetails": {
"discountLevel": "Line",
"discountProduct": "Printer Paper",
"discountType": "AmountOff",
"discountValue": "2.0",
"discountAppliedAt": "LineItem"
},
"rewardType": "ProvideDiscount"
}
]
}
],
"promotionId": "0c8DX00000001h5YAA",
"promotionLimits": [],
"startDateTime": "2025-11-03T12:44:00.000Z",
"termsAndCondition": "&lt;p&gt;Promo_Printer_Child&lt;/p&gt;"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0List of eligible promotions for the specified
line items.
Promotion Details
Response
eligiblePromotions
1409
Response BodiesTransaction Management

===== PAGE 1424 =====

Initiate Downgrade Response
Output representation of the request to initiate a downgrade action.
JSON example
{
"salesTransactionId": "0Q09Q000005IkEPSA0"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Small, 66.0ID of the sales transaction that’s created by
the swap, upgrade, or downgrade action.
StringsalesTransactionId
Initiate Swap Response
Output representation of the request to initiate a swap action. The response includes the ID of the sales transaction that the swap action
creates.
JSON example
{
"salesTransactionId": "0Q09Q000005IkEPSA0"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Small, 66.0ID of the sales transaction that’s created by
the swap action.
StringsalesTransactionId
Initiate Upgrade Response
Output representation of the request to initiate an upgrade action. The response includes the ID of the sales transaction that the upgrade
action creates.
JSON example
{
"salesTransactionId": "0Q09Q000005IkEPSA0"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Small, 66.0ID of the sales transaction that’s created by
the swap, upgrade, or downgrade action.
StringsalesTransactionId
1410
Response BodiesTransaction Management

===== PAGE 1425 =====

Instant Pricing
Output representation containing the results of the instant pricing request.
Sample Response
{
"correlationid": "123",
"contextid": "abcl23",
"records": [
{
"referenceid": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
"quantity": "2"
},
"error": {
"errorCode": "INVALID_API_INPUT",
"message": "Reference Id format is irrelevant."
}
}
],
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
59.0Small, 59.0Context ID returned by the context service.StringcontextId
59.0Small, 59.0Client-generated ID for tracking multiple
related API calls.
StringcorrelationId
59.0Small, 59.0List of records related to pricing results.Object Reference[]records
59.0Small, 59.0Indicates whether the fetching of instant
pricing is successful (true) or not
(false).
Booleansuccess
Object Reference
Output representation of an sObject with a reference ID along with any potential error.
Sample Response
{
"referenceid": "refQuote",
"record": {
"attributes": {
"type": "Quote",
"method": "POST"
},
1411
Response BodiesTransaction Management

===== PAGE 1426 =====

"quantity": "2"
},
"error": {
"errorCode": "INVALID_API_INPUT",
"message": "Reference Id format is irrelevant."
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
59.0Small, 59.0ID that identifies the specific Salesforce
object that’s returned in the API response.
StringreferenceId
59.0Small, 59.0The sObject record data represented as a
map of attribute names to their values.
Map<String,
Object>
record
59.0Small, 59.0Detailed information about any error
associated with the sObject in the response.
https://developer.salesforce.com/docs/atlas.en-us.chatterapi.meta/chatterapi/connect_responses_error_response.htm[]error
Place Order Error Response
Output representation of the error response for the place order request.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Code representing the type of error
encountered during the place order create
request.
StringerrorCode
60.0Small, 60.0Message stating the reason for the error, if
any.
Stringmessage
60.0Small, 60.0Reference ID associated with the specific
error instance for tracking and reference
purposes.
StringreferenceId
Place Order Response
Output representation of the request to create or update an order.
JSON example
{
"requestId": "16PRM0000004DBq",
"orderId": "801S70000001VKgIAM",
"success": true,
"errors": [],
"statusURL": "/services/data/vXX.X/sobjects/AsyncOperationTracker/16PRM0000004DBq"
}
1412
Response BodiesTransaction Management

===== PAGE 1427 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0List of errors encountered during the
synchronous processing.
Place OrderError
Response on page
1412[]
errors
60.0Small, 60.0ID of the order created after a successful
request.
StringorderId
60.0Small, 60.0Request ID of the process to query
asynchronous status of the place order API.
StringrequestId
60.0Small, 60.0Asynchronous status URL of the request, if
available.
StringstatusURL
60.0Small, 60.0Indicates whether the synchronous part of
the processing is successful (true) or not
(false).
Booleansuccess
Place Quote Error Response
Output representation of the error responses of a place quote request.
JSON Example
{
"errorCode": "INVALID_API_INPUT",
"message": "Include record type and method in the request and try again.",
"referenceId": "refQuoteItem2"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Error code representing the type of error
encountered in the create place quote
request.
StringerrorCode
60.0Small, 60.0Message stating the reason for the error, if
any.
Stringmessage
60.0Small, 60.0Reference ID associated with the specific
error instance for tracking and reference
purposes.
StringreferenceId
Place Quote
Output representation of the request to create or update a quote.
1413
Response BodiesTransaction Management

===== PAGE 1428 =====

JSON Example
This example shows a sample response of the place quote request.
{
"quoteId": "0Q0xx0000004E2mCAE",
"requestIdentifier": "95Txx0000004Cx2",
"responseError": [],
"statusURL": "/services/data/v60.0/sobjects/RevenueAsyncOperation/95Txx0000004Cx2EAE",
"success": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the quote created after a successful
request.
StringquoteId
60.0Big, 60.0Unique request identifier that can be used
to poll the async request.
Stringrequest
Identifier
60.0Small, 60.0List of errors encountered during the
synchronous processing.
Place Quote Error
Response []
responseError
60.0Big, 60.0Asynchronous status URL to track the
operation, if available.
StringstatusURL
60.0Small, 60.0Indicates whether the synchronous part of
the processing is successful (true) or not
(false).
Booleansuccess
Sales Transaction Async Error
Output representation of the details of errors encountered during the async processing of the Place Sales Transaction API request.
JSON example
{
"errors": [
{
"errorCode": "FIELD_CUSTOM_VALIDATION_EXCEPTION",
"message": "Quantity cannot exceed 10",
"referenceId": "refQuoteLineItem2"
}
],
"jobStatus": "Completed",
"retryablePayload": {
"pricingPref": "System",
"configurationPref": {
"configurationMethod": "System",
"configurationOptions": {
"validateProductCatalog": true,
"validateAmendRenewCancel": true,
"executeConfigurationRules": true,
1414
Response BodiesTransaction Management

===== PAGE 1429 =====

"addDefaultConfiguration": true
}
},
"graph": {
"graphId": "1",
"records": [
{
"referenceId": "refQuoteLineItem2",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "000xx0000004CNYCA2",
"PricebookEntryId": "01uxx0000009CL2",
"Product2Id": "01txx0000006uu2",
"Quantity": 15,
"UnitPrice": 100
}
},
{
"referenceId": "refQuoteLineItem3",
"record": {
"attributes": {
"type": "QuoteLineItem",
"method": "POST"
},
"QuoteId": "000xx0000004CNYCA2",
"PricebookEntryId": "01uxx0000009CL3",
"Product2Id": "01txx0000006uu3",
"Quantity": 20,
"UnitPrice": 100
}
},
{
"referenceId": "refQuoteLinePriceAdjustment1",
"record": {
"attributes": {
"type": "QuoteLinePriceAdjustment",
"method": "POST"
},
"QuoteLineItemId": "@{refQuoteLineItem3.id}",
"Name": "Some Promo",
"Amount": -25
}
}
]
}
},
"rolledBackReferenceIds": [
"refQuoteLineItem3",
"refQuoteLinePriceAdjustment1"
]
}
1415
Response BodiesTransaction Management

===== PAGE 1430 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Small, 66.0List of async errors from Place Sales
Transaction API. The details include a
Place Sales
Transaction Error[]
errors
reference ID for the failed subrequest, an
error code, and a detailed message.
66.0Small, 66.0Status of the async tracker ID. Error results
are returned after the job is in a
Completed  status.
StringjobStatus
66.0Small, 66.0Subset of the original Place Sales
Transaction API payload errors that can be
Sales Transaction
Input
retryablePayload
used for retry attempts. Reference IDs that
are saved are replaced by their
corresponding record IDs.This property is
included in the response only when the
includeRetryablePayload query
parameter is set to true.
66.0Small, 66.0List of rolled-back reference IDs for
subrequests due to failure of a subrequest
in the same transaction.
String[]rolledBack
ReferenceIds
Preview Approval
Output representation of the details of a preview approval request.
JSON example
{
"approvalChainItems": [
{
"approvalChainName": "HR",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I9gtYAC",
"approvalChainName": "hr"
},
"approvalConditionName": "HR Stage 2 Step 1",
"assignedTo": "005DU000000I9gtYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step1_of_Stage1"
1416
Response BodiesTransaction Management

===== PAGE 1431 =====

}
]
},
{
"approvalChainName": "MARKETING",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I6yzYAC",
"approvalChainName": "marketing"
},
"approvalConditionName": "MARKETING Stage 1 Step 1",
"assignedTo": "005DU000000I6yzYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step2_of_Stage1"
}
]
},
{
"approvalChainName": "LEGAL",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I6yzYAC",
"approvalChainName": "legal"
},
"approvalConditionName": "Legal Stage 1 Step 1",
"assignedTo": "005DU000000I6yzYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step1_of_Stage2"
},
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I9gUYAS",
"approvalChainName": "legal"
1417
Response BodiesTransaction Management

===== PAGE 1432 =====

},
"approvalConditionName": "Legal Stage 2 Step 1",
"assignedTo": "005DU000000I9gUYAS",
"assigneeType": "User",
"level": 2,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [
"0jLDU0000001pIr2AI"
],
"status": "Not Submitted",
"stepApiName": "Step2_of_Stage2"
}
]
},
{
"approvalChainName": "SALES",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "00GDU000000MPZg2AO",
"approvalChainName": "sales"
},
"approvalConditionName": "Sales Stage 1 Step 1",
"assignedTo": "00GDU000000MPZg2AO",
"assigneeType": "Group",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step3_of_Stage1"
}
]
}
],
"flowOrchestrationDefinitionVersionId": "0jEDU0000001nZm",
"status": "Success"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0Details of the approval items for a specific
group.
Preview Approval
Chain Item[]
approvalChain
Items
65.0Small, 65.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
1418
Response BodiesTransaction Management

===== PAGE 1433 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0Details of the error encountered during the
processing of the API request.
Preview Approval
Error[]
error
65.0Small, 65.0ID of the flow orchestration definition
version.
StringflowOrchestration
DefinitionVersion
Id
65.0Small, 65.0Status of the API request.Stringstatus
Preview Approval Chain Item
Output representation of the details of an approval chain item for a specific group.
JSON example
{
"approvalChainItems": [
{
"approvalChainName": "HR",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I9gtYAC",
"approvalChainName": "hr"
},
"approvalConditionName": "HR Stage 2 Step 1",
"assignedTo": "005DU000000I9gtYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step1_of_Stage1"
}
]
},
{
"approvalChainName": "MARKETING",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I6yzYAC",
"approvalChainName": "marketing"
},
1419
Response BodiesTransaction Management

===== PAGE 1434 =====

"approvalConditionName": "MARKETING Stage 1 Step 1",
"assignedTo": "005DU000000I6yzYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step2_of_Stage1"
}
]
},
{
"approvalChainName": "LEGAL",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I6yzYAC",
"approvalChainName": "legal"
},
"approvalConditionName": "Legal Stage 1 Step 1",
"assignedTo": "005DU000000I6yzYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step1_of_Stage2"
},
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I9gUYAS",
"approvalChainName": "legal"
},
"approvalConditionName": "Legal Stage 2 Step 1",
"assignedTo": "005DU000000I9gUYAS",
"assigneeType": "User",
"level": 2,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [
"0jLDU0000001pIr2AI"
],
"status": "Not Submitted",
"stepApiName": "Step2_of_Stage2"
}
]
1420
Response BodiesTransaction Management

===== PAGE 1435 =====

},
{
"approvalChainName": "SALES",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "00GDU000000MPZg2AO",
"approvalChainName": "sales"
},
"approvalConditionName": "Sales Stage 1 Step 1",
"assignedTo": "00GDU000000MPZg2AO",
"assigneeType": "Group",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step3_of_Stage1"
}
]
}
],
"flowOrchestrationDefinitionVersionId": "0jEDU0000001nZm",
"status": "Success"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0Name of the approval chain for a specific
group.
StringapprovalChain
Name
65.0Small, 65.0Details of the approval items.Preview Approval
Item[]
approvalItems
Preview Approval Error
Output representation of the error details associated with the Preview Approval API.
JSON example
This example shows a sample error scenario.
{
"approvalChainItems": [],
"error": {
"correlationId": "0Q0DU0000005HZC0A2",
"errorCode": "[xmlrpc=-1, statusCode=INVALID_API_INPUT, exceptionCode=null,
scope=PublicApi, http=400]",
"errorMessage": "Looks like the flow associated with this approval workflow for the
current record isn't active. Activate the flow and try again.",
1421
Response BodiesTransaction Management

===== PAGE 1436 =====

"source": "PreviewApprovalDataProcessingException"
},
"status": "Failure"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
65.0Small, 65.0Code for the resultant error.StringerrorCode
65.0Small, 65.0Error message for the resultant error.StringerrorMessage
65.0Small, 65.0Details about the source of the error.Stringsource
Preview Approval Item
Output representation of the details of a specific approval item with an approval chain.
JSON example
{
"approvalChainItems": [
{
"approvalChainName": "HR",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I9gtYAC",
"approvalChainName": "hr"
},
"approvalConditionName": "HR Stage 2 Step 1",
"assignedTo": "005DU000000I9gtYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step1_of_Stage1"
}
]
},
{
"approvalChainName": "MARKETING",
"approvalItems": [
1422
Response BodiesTransaction Management

===== PAGE 1437 =====

{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I6yzYAC",
"approvalChainName": "marketing"
},
"approvalConditionName": "MARKETING Stage 1 Step 1",
"assignedTo": "005DU000000I6yzYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step2_of_Stage1"
}
]
},
{
"approvalChainName": "LEGAL",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I6yzYAC",
"approvalChainName": "legal"
},
"approvalConditionName": "Legal Stage 1 Step 1",
"assignedTo": "005DU000000I6yzYAC",
"assigneeType": "User",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step1_of_Stage2"
},
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "005DU000000I9gUYAS",
"approvalChainName": "legal"
},
"approvalConditionName": "Legal Stage 2 Step 1",
"assignedTo": "005DU000000I9gUYAS",
"assigneeType": "User",
"level": 2,
"objectApiName": "Quote",
1423
Response BodiesTransaction Management

===== PAGE 1438 =====

"objectId": "0Q0DU0000005HZC0A2",
"parents": [
"0jLDU0000001pIr2AI"
],
"status": "Not Submitted",
"stepApiName": "Step2_of_Stage2"
}
]
},
{
"approvalChainName": "SALES",
"approvalItems": [
{
"additionalFields": {
"isAutoReviewed": false,
"isEligibleForSmartApproval": true,
"smartApprovalBasisWI": "",
"reviewedBy": "00GDU000000MPZg2AO",
"approvalChainName": "sales"
},
"approvalConditionName": "Sales Stage 1 Step 1",
"assignedTo": "00GDU000000MPZg2AO",
"assigneeType": "Group",
"level": 1,
"objectApiName": "Quote",
"objectId": "0Q0DU0000005HZC0A2",
"parents": [],
"status": "Not Submitted",
"stepApiName": "Step3_of_Stage1"
}
]
}
],
"flowOrchestrationDefinitionVersionId": "0jEDU0000001nZm",
"status": "Success"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0Details of any additional fields in the
approval workflow.
Map<String, String>additional
Fields
65.0Small, 65.0Details of the configured conditions in the
approval workflow.
Stringapproval
ConditionName
65.0Small, 65.0Name of the assignee that the approval
request is assigned to.
StringassignedTo
65.0Small, 65.0Type of assignee.StringassigneeType
65.0Small, 65.0Hierarchy level of the approval item.Integerlevel
65.0Small, 65.0API name of the object to preview the
approval for.
StringobjectApiName
1424
Response BodiesTransaction Management

===== PAGE 1439 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0ID of the object to preview the approval for.StringobjectId
65.0Small, 65.0Details of the parent step.String[]parents
65.0Small, 65.0Status of the approval request.Stringstatus
65.0Small, 65.0API name of the step.StringstepApiName
Promotion Coupon
Output representation of the details of a coupon that's eligible for the recommended promotion.
JSON example
{
"coupon": {
"couponCode": "COUPON_002",
"endDateTime": null,
"startDateTime": "2025-10-08T19:00:00.000Z",
"status": "Active"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Unique code of the coupon.StringcouponCode
66.0Big, 66.0End date and time of the coupon.StringendDateTime
66.0Big, 66.0Start date and time of the coupon.StringstartDateTime
66.0Big, 66.0Status of the coupon.Stringstatus
Promotion Coupon Availability
Output representation of the details of the coupon that's eligible for the promotion. Additionally, this representation specifies the reason
for any coupon ineligibility.
JSON example
{
"couponDetails": {
"coupon": {
"couponCode": "COUPON_002",
"endDateTime": null,
"startDateTime": "2025-10-08T19:00:00.000Z",
"status": "Active"
},
"couponAvailabilityMessage": null
1425
Response BodiesTransaction Management

===== PAGE 1440 =====

}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Coupon that's eligible for the customers'
cart.
Promotion Coupon[]coupon
66.0Big, 66.0Specifies the reason for coupon ineligibility
for the promotion. Valid values are:
StringcouponAvailability
Message
• MultipleActiveCoupons
• NoActiveCoupons
• SingleActiveCouponLimitReached
Promotion Details Response
Output representation of the eligible promotion and its details. This representation includes details of any coupons, eligibility rules, and
terms and conditions.
JSON example
{
"eligiblePromotions": [
{
"additionalPromotionFields": {},
"couponDetails": {
"coupon": {
"couponCode": "COUPON_002",
"endDateTime": null,
"startDateTime": "2025-10-08T19:00:00.000Z",
"status": "Active"
},
"couponAvailabilityMessage": null
},
"currencyIsoCode": "USD",
"description": "15% on Accessories",
"displayName": "Comms Manual Promotion 15% on Accessories",
"endDateTime": null,
"isAutomatic": false,
"priorityNumber": null,
"promotionCode": null,
"promotionEligibleRules": [
{
"ruleName": "CommsAutoPromotionRule",
"rulePriority": 1,
"ruleRewards": [
{
"rewardDetails": {
"discountLevel": "Line",
"discountType": "PercentageOff",
1426
Response BodiesTransaction Management

===== PAGE 1441 =====

"discountValue": "10.0",
"discountAppliedAt": "LineItem",
"discountCategory": "Accessories"
},
"rewardType": "ProvideDiscount"
}
]
}
],
"promotionId": "0c8DX00000001UeYAI",
"promotionLimits": [],
"startDateTime": "2025-07-01T17:02:00.000Z",
"termsAndCondition": "&lt;p&gt;test&lt;/p&gt;"
},
{
"additionalPromotionFields": {},
"couponDetails": {
"coupon": {
"couponCode": "COUPON_001",
"endDateTime": null,
"startDateTime": null,
"status": "Active"
},
"couponAvailabilityMessage": null
},
"currencyIsoCode": "USD",
"description": "Promo_Printer_Child",
"displayName": "Promo_Printer_Child",
"endDateTime": null,
"isAutomatic": false,
"priorityNumber": null,
"promotionCode": null,
"promotionEligibleRules": [
{
"ruleName": "Rule001",
"rulePriority": 1,
"ruleRewards": [
{
"rewardDetails": {
"discountLevel": "Line",
"discountProduct": "Printer Paper",
"discountType": "AmountOff",
"discountValue": "2.0",
"discountAppliedAt": "LineItem"
},
"rewardType": "ProvideDiscount"
}
]
}
],
"promotionId": "0c8DX00000001h5YAA",
"promotionLimits": [],
"startDateTime": "2025-11-03T12:44:00.000Z",
"termsAndCondition": "&lt;p&gt;Promo_Printer_Child&lt;/p&gt;"
1427
Response BodiesTransaction Management

===== PAGE 1442 =====

}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Values of the additional promotion fields
that are mapped in the context definition.
Map<String,
Object>
additional
PromotionFields
66.0Big, 66.0Specifies the details of the coupon eligible
for the promotion or specifies the reason
Promotion Coupon
Availability[]
couponDetails
why there isn’t an eligible coupon for the
promotion.
66.0Big, 66.0Three-letter ISO 4217 code of the monetary
currency associated with the promotion.
StringcurrencyIso
Code
66.0Big, 66.0Description of the promotion.Stringdescription
66.0Big, 66.0Display name of the eligible promotion.StringdisplayName
66.0Big, 60.0End date and time of the promotion in the
ISO 8601 date format.
StringendDateTime
66.0Big, 66.0Indicates whether the promotion is
automatically applied for eligible carts
(true) or not (false).
BooleanisAutomatic
66.0Big, 66.0Priority number of the eligible promotion
for promotion ordering.
IntegerpriorityNumber
66.0Big, 66.0Code of the eligible promotion.StringpromotionCode
66.0Big, 66.0List of promotion rules that are eligible for
the customer's cart.
Promotion Rules
List[]
promotionEligible
Rules
66.0Big, 66.0ID of the eligible promotion.StringpromotionId
66.0Big, 66.0List of the promotion's cart level and cart
item level limits.
Promotion Limit[]promotion
Limits
66.0Big, 66.0Start date and time of the promotion in the
ISO 8601 date format.
StringstartDateTime
66.0Big, 66.0Terms and conditions of the promotion.StringtermsAnd
Condition
Promotion Limit
Output representation of the details of the promotion limit of an eligible promotion.
1428
Response BodiesTransaction Management

===== PAGE 1443 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Current attainment of the promotion's limit
value.
DoublelimitCurrent
Attainment
66.0Big, 66.0Value beyond which the promotion can't
be applied to customer carts.
DoublelimitTarget
66.0Big, 66.0Limit type for the promotion. Valid values
are:
StringlimitType
• CartItemCount—Specifes the limit
type that represents the maximum
number of cart items the promotion can
applied for.
• OrderCount—Specifies the limit
type that represents the maximum
number of carts the promotion can
applied for.
Promotion Reward Details
Output representation of the details of the rewards of an eligible promotion rule.
JSON example
{
"ruleRewards": [
{
"rewardDetails": {
"discountLevel": "Line",
"discountProduct": "Printer Paper",
"discountType": "AmountOff",
"discountValue": "2.0",
"discountAppliedAt": "LineItem"
},
"rewardType": "ProvideDiscount"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Details of the reward offered by the
promotion rule.
Map<String,
Object>
rewardDetails
66.0Big, 66.0Reward type of the promotion. Valid values
are:
StringrewardType
• AssignBadge
1429
Response BodiesTransaction Management

===== PAGE 1444 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
• AssignGame
• CreditFixedPoints
• CreditMultiplierPoints
• GiveFreeProduct
• IssueVoucher
• ProvideDiscount
Promotion Rules List
Output representation of the details of the rules of an eligible promotion.
JSON example
{
"promotionEligibleRules": [
{
"ruleName": "Rule001",
"rulePriority": 1,
"ruleRewards": [
{
"rewardDetails": {
"discountLevel": "Line",
"discountProduct": "Printer Paper",
"discountType": "AmountOff",
"discountValue": "2.0",
"discountAppliedAt": "LineItem"
},
"rewardType": "ProvideDiscount"
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Big, 66.0Rule name in the promotion which is
eligible for rewards.
StringruleName
66.0Big, 66.0Rule priority in the promotion which is
eligible for rewards.
IntegerrulePriority
66.0Big, 66.0Rewards associated with the eligible rule.Promotion Reward
Details[]
ruleRewards
1430
Response BodiesTransaction Management

===== PAGE 1445 =====

Ramp Deal Service Error Response
Output representation of the details of errors encountered during the processing of the API request.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Error code from the API request. For
example, INVALID_INPUT_ERROR.
StringerrorCode
62.0Small, 62.0Error message from the API request.Stringmessage
Ramp Deal Service
Output representation of the details of a created, updated, or deleted ramp deal.
JSON Example
This example shows the sample response for the create, update, or view ramp deal requests.
{
"correlationId": "0QLDU0000002t0Z4AQ",
"errors": [],
"salesTransactionContext": {
"SalesTransaction": [
{
"LegalEntity": null,
"Account": null,
"HeaderDistributionType": null,
"BillingCity": null,
"AccountBusinessType": null,
"HeaderDiscountType": null,
"businessObjectType": "Quote",
"QuoteAccount": null,
"EmployeeCount": null,
"SalesTransactionName": "WarrantyPriceRampAR",
"StartDate": null,
"HeaderDiscountValue": null,
"SalesTransactionType": null,
"Pricebook": "01sDU000000JGf4YAG",
"Opportunity": null,
"ShippingCountry": null,
"ShippingCity": null,
"BillingPostalCode": null,
"id": "0Q0DU0000002f3d0AA",
"BillToContact": null,
"CalculationStatus": "CompletedWithTax",
"Status": "Draft",
"LastPricedDate": null,
"Subtotal": 108.47145205479453,
"OriginalActionType": null,
"TotalAmount": 99.98,
"CurrencyIsoCode": null,
"ShippingStreet": null,
"SalesTransactionItem": [
1431
Response BodiesTransaction Management

===== PAGE 1446 =====

{
"LegalEntity": null,
"ProductName": "Warranty",
"businessObjectType": "QuoteLineItem",
"Product": "01tDU000000EsWSYA0",
"ItemIsPrimarySegment": true,
"ListPrice": 49.99,
"ValidationResult": null,
"StartDate": "2024-08-23T00:00:00.000Z",
"ContractVolumePasId": null,
"BillingTreatment": null,
"PeriodBoundaryStartMonth": null,
"SalesTransactionSourceAsset": null,
"id": "0QLDU0000002t0Z4AQ",
"PartnerDiscountPercent": null,
"PriceWaterFall": "0QLDU0000002t0Z4AQ:548201414593252",
"ItemProductRecipient": null,
"BillingFrequency": "Annual",
"ProductCode": "W001",
"DerivedPricingAttribute": null,
"TaxTreatment": "1ttDU0000001oGKYAY",
"Subtotal": 8.491452054794523,
"ItemRampIdentifier": "RDI5b5ce52b2db4484",
"ItemSegmentName": "Trial",
"PricebookEntry": "01uDU000000f4LSYAY",
"DiscountAmount": null,
"PricingTermCount": 0.0849315068493151,
"NetUnitPrice": 0,
"ItemEffectiveGrantDate": null,
"ProductCategory": null,
"SalesTransactionAction": null,
"SalesTransactionActionType": null,
"SalesTransactionItemGroup": null,
"PeriodBoundaryDay": null,
"LineItemDistributionType": null,
"ProrationPolicy": "0muDU00000029ryYAA",
"ContractDiscountType": null,
"TransactionType": null,
"ParentReference": null,
"Discount": 100,
"ProductSellingModel": "0jPDU00000029zb2AA",
"PricingTermUnit": "Annual",
"PricingSource": null,
"StockKeepingUnit": null,
"PartnerUnitPrice": null,
"ItemTotalAdjustmentAmount": -8.491452054794523,
"SalesTransactionItemSource": "0QLDU0000002t0Z4AQ",
"ContractAttributePasId": null,
"SubscriptionTerm": 1,
"SellingModelType": "TermDefined",
"EndQuantity": 2,
"NetTotalPrice": 0,
"TotalLineAmount": 8.491452054794523,
"ItemSegmentType": "FreeTrial",
1432
Response BodiesTransaction Management

===== PAGE 1447 =====

"ProductBasedOn": null,
"Deleted": null,
"BillingReference": null,
"ArePartialPeriodsAllowed": true,
"ItemRecordedPrice": null,
"CustomProductName": "Warranty",
"ItemSegmentIdentifier": "SEG4380006a1c2b416",
"SalesTransactionItemParent": "0Q0DU0000002f3d0AA",
"Quantity": 2,
"PeriodBoundary": "Anniversary",
"ContractDiscountValue": null,
"LineItemDiscountValue": null,
"ContractId": null,
"EndDate": "2024-09-22T00:00:00.000Z",
"ItemGroupSummarySubtotal": null,
"IsContracted": null,
"UnitPrice": 49.99,
"StartQuantity": 0,
"ContractPrice": null,
"TotalPrice": 0,
"ItemPath": null,
"LineItemDiscountType": null
},
{
"LegalEntity": null,
"ProductName": "Warranty",
"businessObjectType": "QuoteLineItem",
"Product": "01tDU000000EsWSYA0",
"ItemIsPrimarySegment": false,
"ListPrice": 49.99,
"ValidationResult": null,
"StartDate": "2024-09-23T00:00:00.000Z",
"ContractVolumePasId": null,
"BillingTreatment": null,
"PeriodBoundaryStartMonth": null,
"SalesTransactionSourceAsset": null,
"id": "0QLDU0000003CZ94AM",
"PartnerDiscountPercent": null,
"PriceWaterFall": "0QLDU0000003CZ94AM:548201414593252",
"ItemProductRecipient": null,
"BillingFrequency": "Annual",
"ProductCode": "W001",
"DerivedPricingAttribute": null,
"TaxTreatment": "1ttDU0000001oGKYAY",
"Subtotal": 99.98,
"ItemRampIdentifier": "RDI5b5ce52b2db4484",
"ItemSegmentName": "Year-1",
"PricebookEntry": "01uDU000000f4LSYAY",
"DiscountAmount": null,
"PricingTermCount": 1,
"NetUnitPrice": 49.99,
"ItemEffectiveGrantDate": null,
"ProductCategory": null,
"SalesTransactionAction": null,
1433
Response BodiesTransaction Management

===== PAGE 1448 =====

"SalesTransactionActionType": null,
"SalesTransactionItemGroup": null,
"PeriodBoundaryDay": null,
"LineItemDistributionType": null,
"ProrationPolicy": "0muDU00000029ryYAA",
"ContractDiscountType": null,
"TransactionType": null,
"ParentReference": null,
"Discount": null,
"ProductSellingModel": "0jPDU00000029zb2AA",
"PricingTermUnit": "Annual",
"PricingSource": null,
"StockKeepingUnit": null,
"PartnerUnitPrice": null,
"ItemTotalAdjustmentAmount": 0,
"SalesTransactionItemSource": "0QLDU0000003CZ94AM",
"ContractAttributePasId": null,
"SubscriptionTerm": 1,
"SellingModelType": "TermDefined",
"EndQuantity": 2,
"NetTotalPrice": 99.98,
"TotalLineAmount": 99.98,
"ItemSegmentType": "Yearly",
"ProductBasedOn": null,
"Deleted": null,
"BillingReference": null,
"ArePartialPeriodsAllowed": true,
"ItemRecordedPrice": null,
"CustomProductName": "Warranty",
"ItemSegmentIdentifier": "SEG73ad7378e1ed4c5",
"SalesTransactionItemParent": "0Q0DU0000002f3d0AA",
"Quantity": 2,
"PeriodBoundary": "Anniversary",
"ContractDiscountValue": null,
"LineItemDiscountValue": null,
"ContractId": null,
"EndDate": "2025-08-22T00:00:00.000Z",
"ItemGroupSummarySubtotal": null,
"IsContracted": null,
"UnitPrice": 49.99,
"StartQuantity": 0,
"ContractPrice": null,
"TotalPrice": 99.98,
"ItemPath": null,
"LineItemDiscountType": null
}
],
"AppUsageAssignment": [
{
"businessObjectType": "AppUsageAssignment",
"ParentReference": null,
"Record": "0Q0DU0000002f3d0AA",
"id": "0j8DU0000002VKiYAM",
"AppUsageType": "RevenueLifecycleManagement"
1434
Response BodiesTransaction Management

===== PAGE 1449 =====

}
],
"BillingCountry": null,
"BillingStreet": null,
"ShippingPostalCode": null,
"SalesTransactionSource": "0Q0DU0000002f3d0AA",
"PrimaryIndustry": null,
"ShippingState": null,
"HeaderDistributionLogic": null,
"Contract": null,
"BillingState": null,
"AnnualRevenue": null,
"EffectiveDate": null
}
]
},
"success": true,
"transactionContextId":
"d3fd83b007418ce4980340313b40fd45665b194973486ebac3674c2b8002336f"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Resource ID to correlate the API request with
the response.
StringcorrelationId
62.0Small, 62.0List of errors encountered during the
processing of the API request.
Ramp Deal Service
Error Response[]
errors
62.0Small, 62.0Context object for the sales transaction with
updated segment details.
Map<String,
Object>
sales
Transaction
Context
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
62.0Small, 62.0ID of the sales transaction context record
instance.
Stringtransaction
ContextId
Read Sales Transaction
Output representation of the request to read a sales transaction.
JSON example
{
"response": {
"records": {
"Quote": [
{
"data": {
"Id": "0Q05g000000AJK954",
"Name": "Sample Quote",
1435
Response BodiesTransaction Management

===== PAGE 1450 =====

"Status": "Draft",
"TotalPrice": 1500
}
}
],
"QuoteLineItem": [
{
"data": {
"Id": "0QL5g000000DEF456",
"Product2Id": "01t5g000000GUE752",
"Quantity": 2,
"UnitPrice": 750,
"TotalPrice": 1500
}
}
]
}
},
"isSuccess": true,
"errorResponse": []
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0List of errors encountered during the
processing of the API request.
Place Sales
Transaction Error
Response[]
errors
65.0Small, 65.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccess
65.0Small, 65.0Contains a map of keys and associated
values. The keys are record type names, such
Read Sales
Transaction
Records[]
response
as a Quote or QuoteLineItem, and values
are lists of records of that type.
Read Sales Transaction Records
Output representation of the details of a map of keys and associated values. The keys are record type names, such as a Quote or
QuoteLineItem, and values are lists of records of that type.
JSON example
{
"response": {
"records": {
"Quote": [
{
"data": {
"Id": "0Q05g000000AJK954",
"Name": "Sample Quote",
"Status": "Draft",
1436
Response BodiesTransaction Management

===== PAGE 1451 =====

"TotalPrice": 1500
}
}
],
"QuoteLineItem": [
{
"data": {
"Id": "0QL5g000000DEF456",
"Product2Id": "01t5g000000GUE752",
"Quantity": 2,
"UnitPrice": 750,
"TotalPrice": 1500
}
}
]
}
},
"isSuccess": true,
"errorResponse": []
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0Map of record type names to the list of
records.
Map<String, Sales
Transaction
Record>>
records
Renewal
Output representation of the details of a renewal record.
JSON example
{
"renewalRecordId": "0Q0xx0000004NsSCAU",
"errors": [
{
"errorCode": "REQUIRED_FIELD_MISSING",
"errorMessage": "Specify a value for quantityChange, and try again."
}
],
"requestId": "16Pxx0000004NIy",
"success": true
}
Properties
Available
Version
Filter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Error responses if the creation of a renewal
record fails.
ARC Base Error on
page 1405[]
errors
1437
Response BodiesTransaction Management

===== PAGE 1452 =====

Available
Version
Filter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0ID of the renewal record that’s created for
the Quote or Order record.
Stringrenewal
RecordId
62.0Small, 62.0Request ID that’s used to track the async
request.
StringrequestId
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
Sales Transaction
Output representation of the request to create a sales transaction.
JSON example
{
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708",
"isBuiltInTransaction": true
},
"errorResponse": {
"errorCode": "INVALID_API_INPUT",
"message": "Include record type and method in the request and try again.",
"referenceId": "refQuoteItem2"
},
"isSuccess": true,
"salesTransactionId": "0Q0xx0000004CNYCA2",
"statusUrl": null,
"trackerId": null
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Details of the context that’s created for the
sales transaction.
Sales Transaction
Context
contextDetails
63.0Small, 63.0Details of the error if the operation fails.Sales Transaction
Error Response[]
errorResponse
63.0Small, 63.0Indicates if the operation is successful
(true) or not (false).
BooleanisSuccess
63.0Small, 63.0ID of the sales transaction, such as a quote
or an order.
StringsalesTransactionId
63.0Small, 63.0URL to check the status of the operation.StringstatusUrl
63.0Small, 63.0Unique identifier assigned to a specific
operation or request that's used for tracking
and referencing the operation.
StringtrackerId
1438
Response BodiesTransaction Management

===== PAGE 1453 =====

The Calculation Status field for a quote or an order shows an intermediate status as Saving  during the creation of a sales transaction.
If the pricing calculation fails, then the Calculation Status field shows the Pricing Calculation Failed  status. See Quote
standard object for a list of applicable calculation status values.
Sales Transaction Context
Output representation of the context details that are associated with a sales transaction.
JSON example
{
"contextDetails": {
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708",
"isBuiltInTransaction": true
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0ID of the context that’s created for a session
of the sales transaction.
StringcontextId
63.0Small, 63.0Indicates whether a new context ID is
created for the sales transaction (true) or
not (false).
If the contextId property isn’t specified,
the Place Sales Transaction API generates it.
BooleanisBuiltIn
Transaction
Sales Transaction Error Response
Output representation of the error details associated with the API request.
JSON example
{
"errorResponse": {
"errorCode": "INVALID_API_INPUT",
"message": "Include record type and method in the request and try again.",
"referenceId": "refQuoteItem2"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Code for the resultant error.StringerrorCode
63.0Small, 63.0Error message for the resultant error.Stringmessage
63.0Small, 63.0Unique ID that’s associated with the specific
error for tracking and reference purposes.
StringreferenceId
1439
Response BodiesTransaction Management

===== PAGE 1454 =====

Sales Transaction Record
Generic output representation for any sales transaction record type.
JSON example
{
"response": {
"records": {
"Quote": [
{
"data": {
"Id": "0Q05g000000AJK954",
"Name": "Sample Quote",
"Status": "Draft",
"TotalPrice": 1500
}
}
],
"QuoteLineItem": [
{
"data": {
"Id": "0QL5g000000DEF456",
"Product2Id": "01t5g000000GUE752",
"Quantity": 2,
"UnitPrice": 750,
"TotalPrice": 1500
}
}
]
}
},
"isSuccess": true,
"errorResponse": []
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
65.0Small, 65.0Represents the data map for any sales
transaction record.
Map<String,
Object>
data
Supplemental Transaction Error Response
Output representation of the error details associated with the Place Supplemental Transaction API.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
64.0Small, 64.0Code for the resultant error.StringerrorCode
64.0Small, 64.0Message stating the reason for error, if any.Stringmessage
1440
Response BodiesTransaction Management

===== PAGE 1455 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
64.0Small, 64.0Unique ID that’s associated with the specific
error for tracking and reference purposes.
StringreferenceId
Supplemental Transaction
Output representation of the details of the created supplemental order.
JSON example
{
"requestId": "16PRM0000004DBq",
"statusURL": "/services/data/vXX.X/sobjects/AsyncOperationTracker/16PRM0000004DBq",
"orderId": "801S70000001VKgIAM",
"success": true,
"errors": []
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
64.0Small, 64.0List of errors encountered during
synchronous processing.
Supplemental
Transaction Error
Response[]
errors
64.0Small, 64.0Request ID of the process that can be used
to query the async status.
StringrequestId
64.0Small, 64.0URL to check the status of the async
operation, if available.
StringstatusURL
64.0Small, 64.0Indicates whether the synchronous part of
the processing is successful (true) or not
(false).
Booleansuccess
64.0Small, 64.0ID of the created supplemental transaction.Stringsupplemental
TransactionId
Transaction Management Apex Reference
Use built-in Apex classes and interfaces grouped by namespace.
CommerceOrders Namespace
The CommerceOrders  namespace provides classes and methods to place orders with integrated pricing, configuration, and
validation.
ConnectApi Namespace
The ConnectApi  namespace (also called Connect in Apex) provides an Apex class to specify details for asset transfer request
from one account to another.
1441
Transaction Management Apex ReferenceTransaction Management

===== PAGE 1456 =====

CommerceTax Namespace
Manage the communication between Salesforce and an external tax engine.
PlaceQuote Namespace
The PlaceQuote namespace provides classes and methods to create or update quotes with pricing preferences and configuration
options.
RevSalesTrxn Namespace
Create a sales transaction, such as a quote or an order, with integrated pricing and configuration. Additionally, update an order or a
quote, and insert and delete order or quote line items to calculate the estimated tax.
CommerceOrders Namespace
The CommerceOrders namespace provides classes and methods to place orders with integrated pricing, configuration, and validation.
Note:  This namespace has been deprecated as of API version 63.0. In API version 63.0 and later, use the new RevSalesTrxn
namespace.
The CommerceOrders  namespace includes these classes.
CatalogRatesPreferenceEnum Enum
Specifies the rate card entries defined in the catalog that must be fetched for order items, with usage-based selling during the order
creation process.
ConfigurationInputEnum Enum
Specifies the configuration input for the request to place an order.
ConfigurationOptionsInput Class
Contains methods and properties to set the configuration options for the input to the product configurator.
GraphRequest Class
Contains constructors and properties to set the graph ID and a list of records to be ingested. The list of records is specified in a
key-value map format that contains the field values of an order.
PlaceOrderExecutor Class
Contains methods to place an order with details of the graph request, pricing preferences, and configuration options.
PlaceOrderResult Class
Contains properties to hold the response to the place order request.
PricingPreferenceEnum Enum
Specifies the pricing preference during the create order process.
RecordResource Class
Contains constructors and properties to create a record object from field values of an order.
RecordWithReferenceRequest Class
Contains constructors and properties to associate a record object with a reference identifier.
CatalogRatesPreferenceEnum Enum
Specifies the rate card entries defined in the catalog that must be fetched for order items, with usage-based selling during the order
creation process.
1442
CommerceOrders NamespaceTransaction Management

===== PAGE 1457 =====

Usage
This enum is available when the Usage-Based Selling feature is enabled.
Enum Values
The commerceorders.CatalogRatesPreferenceEnum  enum includes these values.
DescriptionValue
Retrieves the rate card entries defined in the catalog for order items during the order
creation process.
Fetch
Skips the retrieval of rate card entries for order items during the order creation
process. The default value is Skip.
Skip
ConfigurationInputEnum Enum
Specifies the configuration input for the request to place an order.
Usage
Use these enum values for the configurationInputEnum  property in the PlaceOrderExecutor Class
Enum Values
The commerceorders.ConfigurationInputEnum  enum has these values.
DescriptionValue
Run the configuration and proceed with order ingestion upon encountering any
configuration errors.
RunAndAllowErrors
Run the configuration and block order ingestion upon encountering any
configuration errors.
RunAndBlockErrors
Skip the configuration execution.Skip
ConfigurationOptionsInput Class
Contains methods and properties to set the configuration options for the input to the product configurator.
Namespace
CommerceOrders
Usage
This class holds the required details of the product configuration input. Set the class properties to enable default configuration, execution
of configuration rules, and validation of the product catalog. Use these class properties as an input to the PlaceOrderExecutor Class
method.
1443
CommerceOrders NamespaceTransaction Management

===== PAGE 1458 =====

Example
CommerceOrders.ConfigurationOptionsInput configurationInput = new
CommerceOrders.ConfigurationOptionsInput();
configurationInput.validateProductCatalog = true;
configurationInput.validateAmendRenewCancel = true;
configurationInput.executeConfigurationRules = true;
configurationInput.addDefaultConfiguration = true;
CommerceOrders.GraphRequest graph = new CommerceOrders.GraphRequest('testGraph',
recordNodes);
CommerceOrders.PlaceOrderResult result = CommerceOrders.PlaceOrderExecutor.execute(graph,
pricingPreference, configurationPreference, configurationInput);
ConfigurationOptionsInput Properties
Set the ConfigurationOptionsInput class properties to add default configuration, execute configuration rules, and validate
the product catalog.
ConfigurationOptionsInput Methods
Learn more about the methods available with the ConfigurationOptionsInput  class.
ConfigurationOptionsInput Properties
Set the ConfigurationOptionsInput  class properties to add default configuration, execute configuration rules, and validate
the product catalog.
The ConfigurationOptionsInput  class includes these properties.
addDefaultConfiguration
Sets the default product configuration, such as bundle and product attributes, for an order request.
executeConfigurationRules
Sets the requirement for an order to adhere to the configuration rules.
validateAmendRenewCancel
Sets the requirement to run validations related to amend, renew, or cancel processes.
validateProductCatalog
Sets the requirement to validate an order against the product catalog.
addDefaultConfiguration
Sets the default product configuration, such as bundle and product attributes, for an order request.
Signature
public Boolean addDefaultConfiguration {get; set;}
Property Value
Type: Boolean
Indicates whether to automatically add default configuration to the order (true) or not (false).
1444
CommerceOrders NamespaceTransaction Management

===== PAGE 1459 =====

executeConfigurationRules
Sets the requirement for an order to adhere to the configuration rules.
Signature
public Boolean executeConfigurationRules {get; set;}
Property Value
Type: Boolean
Indicates whether the order must adhere to configuration rules during processing (true) or bypass them (false).
validateAmendRenewCancel
Sets the requirement to run validations related to amend, renew, or cancel processes.
Signature
public Boolean validateAmendRenewCancel {get; set;}
Property Value
Type: Boolean
Indicates whether to run validations related to amend, renew, or cancel processes (true) or not (false).
validateProductCatalog
Sets the requirement to validate an order against the product catalog.
Signature
public Boolean validateProductCatalog {get; set;}
Property Value
Type: Boolean
Indicates whether the order must be validated against the product catalog (true) or not (false).
ConfigurationOptionsInput Methods
Learn more about the methods available with the ConfigurationOptionsInput  class.
The ConfigurationOptionsInput  class includes these methods.
equals(obj)
Determines the equality of external objects in a list. This method is dynamic and is based on the equals()  method in Java.
hashCode()
Determines the uniqueness of the external object records in a list.
1445
CommerceOrders NamespaceTransaction Management

===== PAGE 1460 =====

toString()
Converts a value to a string.
equals(obj)
Determines the equality of external objects in a list. This method is dynamic and is based on the equals()  method in Java.
Signature
public Boolean equals(Object obj)
Parameters
obj
Type: Object
Reference object that’s used to compare with the class object.
Return Value
Type: Boolean
Indicates if the class object is same as the reference object (true) or not (false).
hashCode()
Determines the uniqueness of the external object records in a list.
Signature
public Integer hashCode()
Return Value
Type: Integer
Integer hash code that represents the value of the object. Equal objects as per the equals()  method must return the same hash
code.
toString()
Converts a value to a string.
Signature
public String toString()
Return Value
Type: String
1446
CommerceOrders NamespaceTransaction Management

===== PAGE 1461 =====

GraphRequest Class
Contains constructors and properties to set the graph ID and a list of records to be ingested. The list of records is specified in a key-value
map format that contains the field values of an order.
Namespace
CommerceOrders
Example
Create the list of records to be ingested by using these steps.
• Create the list of records by constructing the Map<String, Object>  map of field values of an order.
List<CommerceOrders.RecordWithReferenceRequest> recordNodes = new
List<CommerceOrders.RecordWithReferenceRequest>();
// Prepare for the Order
Map<String,Object> orderFieldValues = new Map<String,Object>();
orderFieldValues.put('Pricebook2Id', '01sDU0000000lEIYAY');
orderFieldValues.put('AccountId', '001DU000001nIPKYA2');
orderFieldValues.put('EffectiveDate', '2024-01-01');
• To create a record object from the field values, create an instance of the RecordResource class.
CommerceOrders.RecordResource orderRecord = new
CommerceOrders.RecordResource(Order.getSobjectType(), 'POST');
orderRecord.fieldValues = orderFieldValues;
• To associate the Record object with a reference identifier, create an instance of the RecordWithReferenceRequest class.
CommerceOrders.RecordWithReferenceRequest orderRecordNode = new
CommerceOrders.RecordWithReferenceRequest('refOrder', orderRecord);
recordNodes.add(orderRecordNode);
// Prepare for the App Usage Assignment
Map<String,Object> auaFieldValues = new Map<String,Object>();
auaFieldValues.put('AppUsageType', 'RevenueLifecycleManagement');
auaFieldValues.put('RecordId', '@{refOrder.id}');
CommerceOrders.RecordResource auaRecord = new
CommerceOrders.RecordResource(AppUsageAssignment.getSobjectType(), 'POST');
auaRecord.fieldValues = auaFieldValues;
CommerceOrders.RecordWithReferenceRequest auaRecordNode = new
CommerceOrders.RecordWithReferenceRequest('refAppTag', auaRecord);
recordNodes.add(auaRecordNode);
// Prepare for the Order Item
Map<String,Object> oiFieldValues = new Map<String,Object>();
oiFieldValues.put('OrderId', '@{refOrder.id}');
oiFieldValues.put('PricebookEntryId', '01uDU000000YPkIYAW');
1447
CommerceOrders NamespaceTransaction Management

===== PAGE 1462 =====

oiFieldValues.put('Product2Id', '01tDU000000ESCSYA4');
oiFieldValues.put('Quantity', 2);
oiFieldValues.put('UnitPrice', 800);
CommerceOrders.RecordResource oiRecord = new
CommerceOrders.RecordResource(OrderItem.getSobjectType(), 'POST');
oiRecord.fieldValues = oiFieldValues;
CommerceOrders.RecordWithReferenceRequest oiRecordNode = new
CommerceOrders.RecordWithReferenceRequest('refOrderItem', oiRecord);
recordNodes.add(oiRecordNode);
• Invoke the Place Order Apex API.
Note:  The CatalogRatesPreferenceEnum  enum is available when the Usage-Based Selling feature is enabled.
// Invoke the Place Order Apex API
CommerceOrders.PricingPreferenceEnum pricingPreference =
CommerceOrders.PricingPreferenceEnum.System;
CommerceOrders.CatalogRatesPreferenceEnum catalogRatesPreference =
CommerceOrders.CatalogRatesPreferenceEnum.Fetch;
CommerceOrders.ConfigurationInputEnum configurationPreference =
CommerceOrders.ConfigurationInputEnum.RunAndAllowErrors;
CommerceOrders.ConfigurationOptionsInput configurationInput = new
CommerceOrders.ConfigurationOptionsInput();
configurationInput.validateProductCatalog = true;
configurationInput.validateAmendRenewCancel = true;
configurationInput.executeConfigurationRules = true;
configurationInput.addDefaultConfiguration = true;
• To contain all record objects, create an instance of the GraphRequest  class.
CommerceOrders.GraphRequest graph = new CommerceOrders.GraphRequest('testGraph',
recordNodes);
CommerceOrders.PlaceOrderResultresult = CommerceOrders.PlaceOrderExecutor.execute(graph,
pricingPreference, catalogRatesPreference, configurationPreference, configurationInput);
// Process any error, if exists
if (!result.success) {
List<ConnectApi.PlaceOrderErrorResponse> errors = result.responseError;
for (ConnectApi.PlaceOrderErrorResponse error : errors) {
System.debug(error.errorCode + ': ' + error.message);
}
}
GraphRequest Constructors
Learn more about the available constructors with the GraphRequest  class.
GraphRequest Properties
Learn more about the available properties with the GraphRequest  class.
1448
CommerceOrders NamespaceTransaction Management

===== PAGE 1463 =====

GraphRequest Constructors
Learn more about the available constructors with the GraphRequest  class.
The GraphRequest  class includes these constructors.
GraphRequest(graphId, records)
Creates an instance of the GraphRequest  class to assign the graph ID and a list of records to be ingested.
GraphRequest(graphId, records)
Creates an instance of the GraphRequest  class to assign the graph ID and a list of records to be ingested.
Signature
public GraphRequest(String graphId, List<commerceorders.RecordWithReferenceRequest>
records)
Parameters
graphId
Type: String
ID of the graph.
records
Type: List<commerceorders.RecordWithReferenceRequest>
List of records to be ingested.
GraphRequest Properties
Learn more about the available properties with the GraphRequest  class.
The GraphRequest  class includes these properties.
graphId
Set the graphId  property to assign the ID value of the graph.
graphId
Set the graphId  property to assign the ID value of the graph.
Signature
public String graphId {get; set;}
Property Value
Type: String
1449
CommerceOrders NamespaceTransaction Management

===== PAGE 1464 =====

PlaceOrderExecutor Class
Contains methods to place an order with details of the graph request, pricing preferences, and configuration options.
Namespace
CommerceOrders
Example
CommerceOrders.PlaceOrderResult resp =
CommerceOrders.PlaceOrderExecutor.execute(graph,internalEnum,cEnum,cInput,catalogRatesPreference);
PlaceOrderExecutor Methods
Learn more about the methods available with the PlaceOrderExecutor  class.
PlaceOrderExecutor Example Implementation
Place orders with integrated pricing, configuration, and validation, and manage them throughout their entire lifecycle. To place an
order from Apex, refer to the example implementation of the PlaceOrderExecutor class.
PlaceOrderExecutor Methods
Learn more about the methods available with the PlaceOrderExecutor  class.
The PlaceOrderExecutor  class includes these methods.
execute(graphRequest, pricingPreferenceEnum, configurationInputEnum, configurationOptionsInput)
Use the method in the PlaceOrderExecutor  class to execute the Place Order Apex API request by assigning the properties
for graph request, pricing reference, and configuration options.
execute(graphRequest, pricingPreferenceEnum, catalogRatesPreference, configurationInputEnum, configurationOptionsInput)
Use the method in the PlaceOrderExecutor  class to execute the Place Order Apex API request by assigning the properties
for graph request, pricing reference, and configuration options. This method also includes the property to define fetching of rate
card entries.
execute(graphRequest)
Use the method in the PlaceOrderExecutor  class to execute the Place Order Apex API request by assigning the properties
for graph request.
execute(graphRequest, pricingPreferenceEnum, configurationInputEnum,
configurationOptionsInput)
Use the method in the PlaceOrderExecutor  class to execute the Place Order Apex API request by assigning the properties for
graph request, pricing reference, and configuration options.
Signature
public static commerceorders.PlaceOrderResult execute(commerceorders.GraphRequest
graphRequest, commerceorders.PricingPreferenceEnum pricingPreferenceEnum,
commerceorders.ConfigurationInputEnum configurationInputEnum,
commerceorders.ConfigurationOptionsInput configurationOptionsInput)
1450
CommerceOrders NamespaceTransaction Management

===== PAGE 1465 =====

Parameters
graphRequest
Type: commerceorders.GraphRequest
The sObject graph values of the order payload to be ingested.
pricingPreferenceEnum
Type: commerceorders.PricingPreferenceEnum
Pricing preference during the order process.
configurationInputEnum
Type: commerceorders.ConfigurationInputEnum
Configuration input for the place order process.
configurationOptionsInput
Type: commerceorders.ConfigurationOptionsInput on page 1443
Configuration options during the ingestion process.
Return Value
Type: commerceorders.PlaceOrderResult
execute(graphRequest, pricingPreferenceEnum, catalogRatesPreference,
configurationInputEnum, configurationOptionsInput)
Use the method in the PlaceOrderExecutor  class to execute the Place Order Apex API request by assigning the properties for
graph request, pricing reference, and configuration options. This method also includes the property to define fetching of rate card entries.
Signature
public static commerceorders.PlaceOrderResult execute(commerceorders.GraphRequest
graphRequest, commerceorders.PricingPreferenceEnum pricingPreferenceEnum,
commerceorders.CatalogRatesPreferenceEnum catalogRatesPreferenceEnum,
commerceorders.ConfigurationInputEnum configurationInputEnum,
commerceorders.ConfigurationOptionsInput configurationOptionsInput)
Parameters
graphRequest
Type: commerceorders.GraphRequest
The sObject graph values of the order payload to be ingested.
pricingPreferenceEnum
Type: commerceorders.PricingPreferenceEnum
Pricing preference during the order process.
catalogRatesPreference
Type: commerceorders.CatalogRatesPreferenceEnum
The rate card entries defined in the catalog that must be fetched for order items, with usage-based pricing during the order creation
process. The CatalogRatesPreferenceEnum  enum is available when the Usage-Based Selling feature is enabled.
1451
CommerceOrders NamespaceTransaction Management

===== PAGE 1466 =====

configurationInputEnum
Type: commerceorders.ConfigurationInputEnum
Configuration input for the place order process.
configurationOptionsInput
Type: commerceorders.ConfigurationOptionsInput on page 1443
Configuration options during the ingestion process.
Return Value
Type: commerceorders.PlaceOrderResult
execute(graphRequest)
Use the method in the PlaceOrderExecutor  class to execute the Place Order Apex API request by assigning the properties for
graph request.
Signature
public static commerceorders.PlaceOrderResult execute(commerceorders.GraphRequest
graphRequest)
Parameters
graphRequest
Type: commerceorders.GraphRequest
The sObject graph values of the order payload to be ingested.
Return Value
Type: commerceorders.PlaceOrderResult
PlaceOrderExecutor Example Implementation
Place orders with integrated pricing, configuration, and validation, and manage them throughout their entire lifecycle. To place an order
from Apex, refer to the example implementation of the PlaceOrderExecutor class.
Namespace
commerceorders
Usage
Customize this example to suit your requirements. Create the list of records to be ingested by using these steps. Replace the respective
IDs with the values that are present in your org. For example, replace the value of ${Pricebook2Id}  field with the price book ID
that’s present in the org.
1452
CommerceOrders NamespaceTransaction Management

===== PAGE 1467 =====

Example:
• Create the list of records by constructing the Map<String, Object>  map of field values of an order.
List<CommerceOrders.RecordWithReferenceRequest> recordNodes = new
List<CommerceOrders.RecordWithReferenceRequest>();
// Prepare for the Order
Map<String,Object> orderFieldValues = new Map<String,Object>();
orderFieldValues.put('Pricebook2Id', '01sDU0000000lEIYAY');
orderFieldValues.put('AccountId', '001DU000001nIPKYA2');
orderFieldValues.put('EffectiveDate', '2024-01-01');
• To create a record object from the field values, create an instance of the RecordResource class.
CommerceOrders.RecordResource orderRecord = new
CommerceOrders.RecordResource(Order.getSobjectType(), 'POST');
orderRecord.fieldValues = orderFieldValues;
• To associate the Record object with a reference identifier, create an instance of the RecordWithReferenceRequest
class.
CommerceOrders.RecordWithReferenceRequest orderRecordNode = new
CommerceOrders.RecordWithReferenceRequest('refOrder', orderRecord);
recordNodes.add(orderRecordNode);
// Prepare for the App Usage Assignment
Map<String,Object> auaFieldValues = new Map<String,Object>();
auaFieldValues.put('AppUsageType', 'RevenueLifecycleManagement');
auaFieldValues.put('RecordId', '@{refOrder.id}');
CommerceOrders.RecordResource auaRecord = new
CommerceOrders.RecordResource(AppUsageAssignment.getSobjectType(), 'POST');
auaRecord.fieldValues = auaFieldValues;
CommerceOrders.RecordWithReferenceRequest auaRecordNode = new
CommerceOrders.RecordWithReferenceRequest('refAppTag', auaRecord);
recordNodes.add(auaRecordNode);
// Prepare for the Order Item
Map<String,Object> oiFieldValues = new Map<String,Object>();
oiFieldValues.put('OrderId', '@{refOrder.id}');
oiFieldValues.put('PricebookEntryId', '01uDU000000YPkIYAW');
oiFieldValues.put('Product2Id', '01tDU000000ESCSYA4');
oiFieldValues.put('Quantity', 2);
oiFieldValues.put('UnitPrice', 800);
CommerceOrders.RecordResource oiRecord = new
CommerceOrders.RecordResource(OrderItem.getSobjectType(), 'POST');
oiRecord.fieldValues = oiFieldValues;
CommerceOrders.RecordWithReferenceRequest oiRecordNode = new
1453
CommerceOrders NamespaceTransaction Management

===== PAGE 1468 =====

CommerceOrders.RecordWithReferenceRequest('refOrderItem', oiRecord);
recordNodes.add(oiRecordNode);
• Invoke the Place Order Apex API.
Note:  The CatalogRatesPreferenceEnum enum is available when the Usage-Based Selling feature is enabled.
// Invoke the Place Order Apex API
CommerceOrders.PricingPreferenceEnum pricingPreference =
CommerceOrders.PricingPreferenceEnum.System;
CommerceOrders.CatalogRatesPreferenceEnum catalogRatesPreference =
CommerceOrders.CatalogRatesPreferenceEnum.Fetch;
CommerceOrders.ConfigurationInputEnum configurationPreference =
CommerceOrders.ConfigurationInputEnum.RunAndAllowErrors;
CommerceOrders.ConfigurationOptionsInput configurationInput = new
CommerceOrders.ConfigurationOptionsInput();
configurationInput.validateProductCatalog = true;
configurationInput.validateAmendRenewCancel = true;
configurationInput.executeConfigurationRules = true;
configurationInput.addDefaultConfiguration = true;
• To contain all record objects, create an instance of the GraphRequest class.
CommerceOrders.GraphRequest graph = new CommerceOrders.GraphRequest('testGraph',
recordNodes);
CommerceOrders.PlaceOrderResult result =
CommerceOrders.PlaceOrderExecutor.execute(graph, pricingPreference,
catalogRatesPreference, configurationPreference, configurationInput);
// Process any error, if exists
if (!result.success) {
List<ConnectApi.PlaceOrderErrorResponse> errors = result.responseError;
for (ConnectApi.PlaceOrderErrorResponse error : errors) {
System.debug(error.errorCode + ': ' + error.message);
}
}
PlaceOrderResult Class
Contains properties to hold the response to the place order request.
Namespace
CommerceOrders
1454
CommerceOrders NamespaceTransaction Management

===== PAGE 1469 =====

Example
CommerceOrders.PlaceOrderResult resp =
CommerceOrders.PlaceOrderExecutor.execute(graph,internalEnum,cEnum,cInput,catalogRatesPreference);
PlaceOrderResult Properties
Learn more about the available properties with the PlaceOrderResult  class.
PlaceOrderResult Properties
Learn more about the available properties with the PlaceOrderResult  class.
The PlaceOrderResult  class includes these properties.
orderId
Get the ID of the order that’s created after a successful request.
requestIdentifier
Get the request ID of the process to query the asynchronous status of the Place Order Apex API.
responseError
Get the list of errors encountered during the synchronous processing of the API request.
statusURL
Get the asynchronous status URL of the request, if available.
success
Get the request status of the synchronous part of the processing.
orderId
Get the ID of the order that’s created after a successful request.
Signature
public String orderId {get; set;}
Property Value
Type: String
requestIdentifier
Get the request ID of the process to query the asynchronous status of the Place Order Apex API.
Signature
public String requestIdentifier {get; set;}
Property Value
Type: String
1455
CommerceOrders NamespaceTransaction Management

===== PAGE 1470 =====

responseError
Get the list of errors encountered during the synchronous processing of the API request.
Signature
public List<commerceorders.PlaceOrderErrorResponse> responseError {get; set;}
Property Value
Type: List<ConnectApi.PlaceOrderErrorResponse>
statusURL
Get the asynchronous status URL of the request, if available.
Signature
public String statusURL {get; set;}
Property Value
Type: String
success
Get the request status of the synchronous part of the processing.
Signature
public Boolean success {get; set;}
Property Value
Type: Boolean
Indicates whether the synchronous part of the processing is successful (true) or not (false).
PricingPreferenceEnum Enum
Specifies the pricing preference during the create order process.
Usage
Used by the PlaceOrderExecutor class.
Enum Values
The commerceorders.PricingPreferenceEnum  enum includes these values.
1456
CommerceOrders NamespaceTransaction Management

===== PAGE 1471 =====

DescriptionValue
Enforce pricing during the order ingestion process.Force
Skip pricing during the order ingestion process.Skip
Determine whether a pricing calculation is required.System
RecordResource Class
Contains constructors and properties to create a record object from field values of an order.
Namespace
CommerceOrders
Example
CommerceOrders.RecordResource orderRecord = new
CommerceOrders.RecordResource(Order.getSobjectType(), 'POST');
orderRecord.fieldValues = orderFieldValues;
RecordResource Constructors
Learn more about the available constructors with the RecordResource  class.
RecordResource Properties
Learn more about the available properties with the RecordResource  class.
RecordResource Constructors
Learn more about the available constructors with the RecordResource  class.
The RecordResource  class includes these constructors.
RecordResource(type, method, id)
Creates an instance of the RecordResource  class to assign values to the fields of an order item by using the sObject type, API
method, and order ID properties.
RecordResource(type, method)
Creates an instance of the RecordResource  class to assign the values to the fields of an order item by using the sObject type
and API method properties.
RecordResource(type, method, id)
Creates an instance of the RecordResource  class to assign values to the fields of an order item by using the sObject type, API
method, and order ID properties.
Signature
public RecordResource(Schema.SObjectType type, String method, Id id)
1457
CommerceOrders NamespaceTransaction Management

===== PAGE 1472 =====

Parameters
type
Type: Schema.SObjectType
Object that’s returned from the field describe result using the getReferenceTo() method or from the sObject describe result
using the getSObjectType() method.
method
Type: String
Method for the API request, such as POST or PATCH.
id
Type: Id
ID of the order.
RecordResource(type, method)
Creates an instance of the RecordResource  class to assign the values to the fields of an order item by using the sObject type and
API method properties.
Signature
public RecordResource(Schema.SObjectType type, String method)
Parameters
type
Type: Schema.SObjectType
Object that’s returned from the field describe result using the getReferenceTo() method or from the sObject describe result
using the getSObjectType() method.
method
Type: String
Method for the API request, such as POST or PATCH.
RecordResource Properties
Learn more about the available properties with the RecordResource  class.
The RecordResource  class includes these properties.
fieldValues
Set the fieldValues  property to assign values to the fields to update the order record.
id
Set the id  property to assign the ID of the order record.
method
Set the method  property to specify the API request method, such as POST or PATCH.
1458
CommerceOrders NamespaceTransaction Management

===== PAGE 1473 =====

type
Set the type  property to assign the object type that’s returned from the field describe result using
the getReferenceTo() method or from the sObject describe result using the getSObjectType() method.
fieldValues
Set the fieldValues  property to assign values to the fields to update the order record.
Signature
public Map<String,ANY> fieldValues {get; set;}
Property Value
Type: List<Map<String,ANY>>
id
Set the id  property to assign the ID of the order record.
Signature
public String id {get; set;}
Property Value
Type: String
method
Set the method  property to specify the API request method, such as POST or PATCH.
Signature
public String method {get; set;}
Property Value
Type: String
type
Set the type  property to assign the object type that’s returned from the field describe result using the getReferenceTo() method
or from the sObject describe result using the getSObjectType() method.
Signature
public Schema.SObjectType type {get; set;}
1459
CommerceOrders NamespaceTransaction Management

===== PAGE 1474 =====

Property Value
Type: Schema.SObjectType
RecordWithReferenceRequest Class
Contains constructors and properties to associate a record object with a reference identifier.
Namespace
CommerceOrders
Example
CommerceOrders.RecordWithReferenceRequest orderRecordNode = new
CommerceOrders.RecordWithReferenceRequest('refOrder', orderRecord);
RecordWithReferenceRequest Constructors
Learn more about the available constructors with the RecordWithReferenceRequest  class.
RecordWithReferenceRequest Properties
Learn more about the available properties with the RecordWithReferenceRequest  class.
RecordWithReferenceRequest Constructors
Learn more about the available constructors with the RecordWithReferenceRequest  class.
The RecordWithReferenceRequest  class includes these constructors.
RecordWithReferenceRequest(referenceId, record)
Creates an instance of the RecordWithReferenceRequest  class to associate a record object with a reference identifier by
using the referenceId  and record  object properties.
RecordWithReferenceRequest(referenceId, record)
Creates an instance of the RecordWithReferenceRequest  class to associate a record object with a reference identifier by using
the referenceId  and record  object properties.
Signature
public RecordWithReferenceRequest(String referenceId, commerceorders.RecordResource
record)
Parameters
referenceId
Type: String
Reference ID that maps to the subrequest response and can be used to reference the response in subsequent subrequests. You can
reference the referenceId  in either the body or URL of a subrequest. Use this syntax to include a reference:
@{referenceId.FieldName}. See referenceId property of a composite subrequest.
1460
CommerceOrders NamespaceTransaction Management

===== PAGE 1475 =====

record
Type: commerceorders.RecordResource
Record object that’s defined using the RecordResource class.
RecordWithReferenceRequest Properties
Learn more about the available properties with the RecordWithReferenceRequest  class.
The RecordWithReferenceRequest  class includes these properties.
record
Set the record  property to specify the record object that’s defined by using the RecordResource  class.
referenceId
Set the referenceId  property to specify the reference ID that maps to the subrequest response. This reference ID can be used
to reference the response in subsequent subrequests.
record
Set the record  property to specify the record object that’s defined by using the RecordResource  class.
Signature
public commerceorders.RecordResource record {get; set;}
Property Value
Type: commerceorders.RecordResource
referenceId
Set the referenceId  property to specify the reference ID that maps to the subrequest response. This reference ID can be used to
reference the response in subsequent subrequests.
Signature
public String referenceId {get; set;}
Property Value
Type: String
ConnectApi Namespace
The ConnectApi  namespace (also called Connect in Apex) provides an Apex class to specify details for asset transfer request from
one account to another.
These classes are available in the ConnectApi namespace.
1461
ConnectApi NamespaceTransaction Management

===== PAGE 1476 =====

ConnectApi Input Classes
Transaction Management includes this Apex input class.
ConnectApi Input Classes
Transaction Management includes this Apex input class.
ConnectApi.TransferRecordInputRepresentation
Input representation of the details of the assets to be transferred.
ConnectApi.TransferRecordInputRepresentation
Input representation of the details of the assets to be transferred.
This Apex class is used by the transferRecords apex-defined input variable. See Initiate Transfer Action on page 1647.
Available VersionRequired or
Optional
DescriptionTypeProperty
65.0RequiredID of the asset to transfer.StringassetId
65.0RequiredTransfer quantity for the request.DoubletransferQuantity
CommerceTax Namespace
Manage the communication between Salesforce and an external tax engine.
The CommerceTax  namespace includes these classes.
AbstractTransactionResponse Class
Abstract class that contains methods for setting tax fields based on the external tax provider's response. Response classes that extend
AbstractTransactionResponse  inherit these methods.
AddressesResponse Class
Sets the tax address fields based on a response from the external tax engine. Contains setter methods for the Ship From, Ship To,
and Sold To addresses.
AddressResponse Class
Contains a location code sent from the external tax engine.
AmountDetailsResponse Class
Sets tax amount fields based on a response from the external tax engine.
CalculateTaxRequest Class
Represents a request to an external tax engine to calculate tax. Extends the TaxTransactionRequest class and is the top-level request
class.
CalculateTaxResponse Class
Sets the values of the tax transaction following a response from the external tax engine. Extends the AbstractTransactionResponse
class and is the top-level response class.
1462
CommerceTax NamespaceTransaction Management

===== PAGE 1477 =====

CalculateTaxType Enum
Shows whether a tax calculation request is for estimated or actual tax.
CustomTaxAttributesResponse Class
Sets additional data or custom attributes in the tax response.
ErrorResponse Class
Use to respond with an error after receiving errors from the PaymentGatewayAdapter methods of the CommercePayments namespace,
such as request-forbidden responses, custom validation errors, or expired API tokens.
HeaderTaxAddressesRequest Class
Captures the address values that are applicable for the quote or order transaction.
ImpositionResponse Class
Stores details of tax impositions from the external tax engine.
JurisdictionResponse Class
Stores details from the external tax engine about the tax jurisdiction used in the tax calculation process. A tax jurisdiction represents
a government entity that collects tax.
LineItemResponse Class
Response class that stores details of a list of one or more line items on which the tax engine has calculated tax.
LineTaxAddressesRequest Class
Stores details of the addresses applied per line item in a tax calculation request.
RequestType Enum
Shows the type of tax request made to the tax engine.
ResultCode Enum
Code that represents the results of a tax request made to the tax engine.
RuleDetailsResponse Class
Contains details about the tax rules used for tax calculation.
TaxAddressesRequest Class
Contains methods to get and set tax address values.
TaxAddressRequest Class
Contains address details used for tax calculation.
TaxApiException Class
Contains details about any exceptions during the tax calculation process. Extends the ApexBaseException class.
TaxCustomerDetailsRequest Class
Contains customer details used in tax calculation.
TaxDetailsResponse Class
Stores details of the tax values that an external tax engine calculates in response to a tax calculation request.
TaxEngineAdapter Interface
Retrieves information from the tax engine and evaluates the information to define tax details.
TaxEngineContext Class
Wrapper class that stores details about the type of a tax calculation request.
TaxLineItemRequest Class
Contains line item details of a tax request.
1463
CommerceTax NamespaceTransaction Management

===== PAGE 1478 =====

TaxSellerDetailsRequest Class
Contains tax code details used in the tax calculation request.
TaxTransactionRequest Class
Abstract class for storing customer details used in tax calculation and estimation requests.
TaxTransactionStatus Enum
Shows whether the tax transaction has been committed or uncommitted.
TaxTransactionType Enum
Shows whether the tax transaction is for a credit or debit transaction.
AbstractTransactionResponse Class
Abstract class that contains methods for setting tax fields based on the external tax provider's response. Response classes that extend
AbstractTransactionResponse  inherit these methods.
Namespace
CommerceTax
AbstractTransactionResponse Methods
Learn more about the methods for AbstractTransactionResponse class.
AbstractTransactionResponse Methods
Learn more about the methods for AbstractTransactionResponse class.
The AbstractTransactionResponse  class includes these methods.
setAddresses(addresses)
Uses an instance of AddressesResponse  to set the values of tax address fields.
setAmountDetails(amountDetails)
Uses an instance of AmountDetailsResponse  to set tax amount fields such as exemption amount and tax amount.
setCurrencyIsoCode(currencyIsoCode)
Sets the currencyIsoCode field.
setCustomTaxAttributes(customTaxAttributes)
Uses an instance of CustomTaxAttributesResponse  class to include additional attributes in the tax response at the header
level.
setDescription(dscptn)
Sets the Description field.
setDocumentCode(documentCode)
Sets the DocumentCode field. Document codes are often used to reference tax documents that the external tax engine uses in the
tax calculation process. Document code acts as a unique link to chain-related transactions, such as amendment or refunds.
setEffectiveDate(effectiveDate)
Sets the EffectiveDate field. Effective Date fields are optional fields that store the date that a transaction takes effect. We provide
these fields only for recordkeeping purposes – for example, if you must report an effective date to an external general ledger system.
Salesforce doesn't use them to calculate any tax or payment values.
1464
CommerceTax NamespaceTransaction Management

===== PAGE 1479 =====

setLineItems(lineItems)
Uses an instance of the LineItemResponse  class to set a list of line items. Each line item represents an item sent to an external
tax engine for tax calculation.
setReferenceDocumentCode(referenceDocumentCode)
Sets the ReferenceDocumentCode field. Use this field to store the code of an additional document used in the tax calculation process.
For example, use this field in case of a refund for a previously taxed purchase.
setReferenceEntityId(referenceEntityId)
Sets the ID of a reference entity. In Commerce Tax, a reference entity represents a record related to the items sent to the external
tax engine for tax calculation. For example, if you sent order items for tax calculation, you could define the parent order as the
reference entity.
setTaxTransactionId(taxTrxnId)
Sets the TaxTransactionId field using the ID of a tax transaction record. In Commerce Tax, a tax transaction record stores information
about a specific tax calculation process.
setTransactionDate(transactionDate)
Sets the TransactionDate field.
setAddresses(addresses)
Uses an instance of AddressesResponse  to set the values of tax address fields.
Signature
global void setAddresses(commercetax.AddressesResponse addresses)
Parameters
addresses
Type: AddressesResponse
Class that contains methods to set the Ship To, Ship From, and Sold To address information.
Return Value
Type: void
setAmountDetails(amountDetails)
Uses an instance of AmountDetailsResponse  to set tax amount fields such as exemption amount and tax amount.
Signature
global void setAmountDetails(commercetax.AmountDetailsResponse amountDetails)
Parameters
amountDetails
Type: AmountDetailsResponse
Class that contains methods to set the tax exemption amount, tax amount, total amount, and total amount with tax.
1465
CommerceTax NamespaceTransaction Management

===== PAGE 1480 =====

Return Value
Type: void
setCurrencyIsoCode(currencyIsoCode)
Sets the currencyIsoCode field.
Signature
global void setCurrencyIsoCode(String currencyIsoCode)
Parameters
currencyIsoCode
Type: String
Three-letter ISO 4217 currency code associated with a tax object.
Return Value
Type: void
setCustomTaxAttributes(customTaxAttributes)
Uses an instance of CustomTaxAttributesResponse  class to include additional attributes in the tax response at the header
level.
Signature
global void setCustomTaxAttributes(commercetax.CustomTaxAttributesResponse
customTaxAttributes)
Parameters
customTaxAttributes
Type: CustomTaxAttributesResponse
Additional data or custom attributes to include in the tax response.
Return Value
Type: void
setDescription(dscptn)
Sets the Description field.
Signature
global void setDescription(String dscptn)
1466
CommerceTax NamespaceTransaction Management

===== PAGE 1481 =====

Parameters
dscptn
Type: String
Optional field for providing additional information about a record.
Return Value
Type: void
setDocumentCode(documentCode)
Sets the DocumentCode field. Document codes are often used to reference tax documents that the external tax engine uses in the tax
calculation process. Document code acts as a unique link to chain-related transactions, such as amendment or refunds.
Signature
global void setDocumentCode(String documentCode)
Parameters
documentCode
Type: String
Code for a tax document used in the tax calculation process.
Return Value
Type: void
setEffectiveDate(effectiveDate)
Sets the EffectiveDate field. Effective Date fields are optional fields that store the date that a transaction takes effect. We provide these
fields only for recordkeeping purposes – for example, if you must report an effective date to an external general ledger system. Salesforce
doesn't use them to calculate any tax or payment values.
Signature
global void setEffectiveDate(Datetime effectiveDate)
Parameters
effectiveDate
Type: Datetime
Optional field that stores the date that a transaction takes effect.
Return Value
Type: void
1467
CommerceTax NamespaceTransaction Management

===== PAGE 1482 =====

setLineItems(lineItems)
Uses an instance of the LineItemResponse  class to set a list of line items. Each line item represents an item sent to an external
tax engine for tax calculation.
Signature
global void setLineItems(List<commercetax.LineItemResponse> lineItems)
Parameters
lineItems
Type: List<LineItemResponse>
A list of line items sent to an external tax engine for tax calculation.
Return Value
Type: void
setReferenceDocumentCode(referenceDocumentCode)
Sets the ReferenceDocumentCode field. Use this field to store the code of an additional document used in the tax calculation process.
For example, use this field in case of a refund for a previously taxed purchase.
Signature
global void setReferenceDocumentCode(String referenceDocumentCode)
Parameters
referenceDocumentCode
Type: String
The code for a document used in the tax calculation process.
Return Value
Type: void
setReferenceEntityId(referenceEntityId)
Sets the ID of a reference entity. In Commerce Tax, a reference entity represents a record related to the items sent to the external tax
engine for tax calculation. For example, if you sent order items for tax calculation, you could define the parent order as the reference
entity.
Signature
global void setReferenceEntityId(String referenceEntityId)
1468
CommerceTax NamespaceTransaction Management

===== PAGE 1483 =====

Parameters
referenceEntityId
Type: String
ID of a record related to the items sent for tax calculation.
Return Value
Type: void
setTaxTransactionId(taxTrxnId)
Sets the TaxTransactionId field using the ID of a tax transaction record. In Commerce Tax, a tax transaction record stores information
about a specific tax calculation process.
Signature
global void setTaxTransactionId(String taxTrxnId)
Parameters
taxTrxnId
Type: String
The ID of a tax transaction record in Commerce Tax.
Return Value
Type: void
setTransactionDate(transactionDate)
Sets the TransactionDate field.
Signature
global void setTransactionDate(Datetime transactionDate)
Parameters
transactionDate
Type: Datetime
Date that a tax transaction occurred.
Return Value
Type: void
1469
CommerceTax NamespaceTransaction Management

===== PAGE 1484 =====

AddressesResponse Class
Sets the tax address fields based on a response from the external tax engine. Contains setter methods for the Ship From, Ship To, and
Sold To addresses.
Namespace
CommerceTax
Usage
Because AddressesResponse contains multiple addresses, we recommend using multiple instances of AddressResponse
to set unique values for each address.
Example
This code sample represents a portion of the code used in a mock tax adapter. In this example, you create three AddressResponse
classes, set their location codes, and pass them to the Ship To, Ship From, and Sold To  setter methods in
AddressesResponse. In an actual implementation, your AddressResponse  classes already have a location code based on
the response from the external tax engine.
commercetax.AddressesResponse addressesRes = new commercetax.AddressesResponse();
//AddressResponse containing ShipTo information
commercetax.AddressResponse shipToAddress = new commercetax.AddressResponse();
shipToAddress.setLocationCode('1234567');
//AddressResponse containing ShipFrom information
commercetax.AddressResponse shipFromAddress = new commercetax.AddressResponse();
shipFromAddress.setLocationCode('84720385');
//AddressResponse containing Sold To information
commercetax.AddressResponse soldToAddress = new commercetax.AddressResponse();
soldToAddress.setLocationCode('92381749');
//set values of addressesRes
addressesRes.setShipFrom(shipFromAddress);
addressesRes.setShipTo(shipToAddress);
addressesRes.setSoldTo(soldToAddress);
AddressesResponse Methods
Learn more about the methods for AddressesResponse class.
AddressesResponse Methods
Learn more about the methods for AddressesResponse class.
The AddressesResponse  class includes these methods.
1470
CommerceTax NamespaceTransaction Management

===== PAGE 1485 =====

setShipFrom(shipFrom)
Sets the value of a ShipFrom address field.
setShipTo(shipTo)
Sets the value of a ShipTo address field.
setSoldTo(soldTo)
Sets the value of a SoldTo address field.
setShipFrom(shipFrom)
Sets the value of a ShipFrom address field.
Signature
global void setShipFrom(commercetax.AddressResponse shipFrom)
Parameters
shipFrom
Type: AddressResponse
A single address. Use this generic address parameter to store any type of address, such as Ship From, Ship To, and Sold To details.
Users set the specific address in an AddressResponse  instance and then pass that instance to the AddressesResponse’s
setShipTo(), setShipFrom(), and setSoldTo()  methods as needed.
Return Value
Type: void
setShipTo(shipTo)
Sets the value of a ShipTo address field.
Signature
global void setShipTo(commercetax.AddressResponse shipTo)
Parameters
shipTo
Type: AddressResponse
Stores a single address. This is a generic address parameter and can be used to store any type of address, such as Ship From, Ship
To, and Sold To details. Users set the specific address in an AddressResponse  instance and then pass that instance to the
AddressesResponse’s setShipTo(), setShipFrom(), and setSoldTo()  methods as needed.
Return Value
Type: void
1471
CommerceTax NamespaceTransaction Management

===== PAGE 1486 =====

setSoldTo(soldTo)
Sets the value of a SoldTo address field.
Signature
global void setSoldTo(commercetax.AddressResponse soldTo)
Parameters
soldTo
Type: AddressResponse
Stores a single address. This is a generic address parameter and can be used to store any type of address, such as Ship From, Ship
To, Sold To details. Users set the specific address in an AddressResponse instance and then pass that instance to the
AddressesResponse’s setShipTo(), setShipFrom(), and setSoldTo()  methods as needed.
Return Value
Type: void
AddressResponse Class
Contains a location code sent from the external tax engine.
Namespace
CommerceTax
Usage
Use the AddressResponse  class to set unique values for each address.
commercetax.AddressesResponse addressesRes = new commercetax.AddressesResponse();
//AddressResponse containing ShipTo information
commercetax.AddressResponse shipToAddress = new commercetax.AddressResponse();
shipToAddress.setLocationCode('1234567');
//AddressResponse containing ShipFrom information
commercetax.AddressResponse shipFromAddress = new commercetax.AddressResponse();
shipFromAddress.setLocationCode('84720385');
//AddressResponse containing Sold To information
commercetax.AddressResponse soldToAddress = new commercetax.AddressResponse();
soldToAddress.setLocationCode('92381749');
//set values of addressesRes
addressesRes.setShipFrom(shipFromAddress);
addressesRes.setShipTo(shipToAddress);
addressesRes.setSoldTo(soldToAddress);
1472
CommerceTax NamespaceTransaction Management

===== PAGE 1487 =====

AddressResponse Methods
Learn more about the available methods with the AddressResponse  class.
AddressResponse Methods
Learn more about the available methods with the AddressResponse  class.
The AddressResponse  class includes these methods.
setLocationCode(locationCode)
Sets the value of a LocationCode field.
setLocationCode(locationCode)
Sets the value of a LocationCode field.
Signature
global void setLocationCode(String locationCode)
Parameters
locationCode
Type: String
A code that contains address information. This value can be passed to a method that sets the value of an address field.
Return Value
Type: void
AmountDetailsResponse Class
Sets tax amount fields based on a response from the external tax engine.
Namespace
CommerceTax
Example
In this example, an instance of AmountDetailsResponse class in a mock adapter calculates several tax amount fields. The
totalTax  and totalAmount  parameters were defined in an instance of LineItemResponse class. The adapter then assigns
the instance to lineItemResponse.
commercetax.AmountDetailsResponse amountResponse = new commercetax.AmountDetailsResponse();
amountResponse.setTotalAmountWithTax(totalTax+totalAmount);
amountResponse.setExemptAmount(0);
amountResponse.setTotalAmount(totalAmount);
amountResponse.setTaxAmount(totalTax);
lineItemResponse.setAmountDetails(amountResponse);
1473
CommerceTax NamespaceTransaction Management

===== PAGE 1488 =====

AmountDetailsResponse Methods
Learn more about the methods available from the AmountDetailsResponse  class.
AmountDetailsResponse Methods
Learn more about the methods available from the AmountDetailsResponse  class.
The following are methods for AmountDetailsResponse.
setExemptAmount(exemptAmount)
Sets the value of the ExemptAmount field.
setTaxAmount(taxAmount)
Sets the value of the TaxAmount field.
setTotalAmount(totalAmount)
Sets the value of the TotalAmount field.
setTotalAmountWithTax(totalAmtWithTax)
Sets the value of the TotalAmountWithTax field.
setExemptAmount(exemptAmount)
Sets the value of the ExemptAmount field.
Signature
global void setExemptAmount(Double exemptAmount)
Parameters
exemptAmount
Type: Double
The amount of a line item's total amount that's exempt from tax calculation.
Return Value
Type: void
setTaxAmount(taxAmount)
Sets the value of the TaxAmount field.
Signature
global void setTaxAmount(Double taxAmount)
Parameters
taxAmount
Type: Double
1474
CommerceTax NamespaceTransaction Management

===== PAGE 1489 =====

The calculated amount of tax for a line item.
Return Value
Type: void
setTotalAmount(totalAmount)
Sets the value of the TotalAmount field.
Signature
global void setTotalAmount(Double totalAmount)
Parameters
totalAmount
Type: Double
The total amount of a line item, excluding tax.
Return Value
Type: void
setTotalAmountWithTax(totalAmtWithTax)
Sets the value of the TotalAmountWithTax field.
Signature
global void setTotalAmountWithTax(Double totalAmtWithTax)
Parameters
totalAmtWithTax
Type: Double
The total amount of a line item combined with the calculated tax for that line item.
Return Value
Type: void
CalculateTaxRequest Class
Represents a request to an external tax engine to calculate tax. Extends the TaxTransactionRequest class and is the top-level request
class.
Namespace
CommerceTax
1475
CommerceTax NamespaceTransaction Management

===== PAGE 1490 =====

Usage
Keep these considerations in mind when you use this class.
• If the shouldVoidTax  property value is set to true, then the operation returns a response with documentCode property
value updated to referenceDocumentCode  property value that was originally sent in the request payload. The response also
includes the taxTransactionType  property value as Void. This indicates that the document specified in the
referenceDocumentCode  property value is voided.
• If document is locked or you can't void the tax transaction for any reason, then you can use the Tax Calculation request to perform
another transaction such as a Credit Tax request. In this scenario, the response includes the documentCode  property value that
was sent in the request payload.
• If the document that's mentioned in the referenceDocumentCode  property value isn't available in the tax engine, then an
error response occurs with ResultCode on page 1510 value as ReferenceDocumentCodeMissing.
Example
See TaxEngineAdapter Example Implementation for more details on how to access information from the CalculateTaxRequest
class.
CalculateTaxRequest Constructors
Learn more about the constructors that are available with the CalculateTaxRequest  class. This constructor is intended for
test usage and throws an exception if used outside of the Apex test context.
CalculateTaxRequest Properties
Learn more about the available properties with the CalculateTaxRequest  class.
CalculateTaxRequest Methods
Learn more about the available methods with the CalculateTaxRequest  class.
CalculateTaxRequest Constructors
Learn more about the constructors that are available with the CalculateTaxRequest  class. This constructor is intended for test
usage and throws an exception if used outside of the Apex test context.
The CalculateTaxRequest  class includes these constructors.
CalculateTaxRequest(taxType)
This constructor is intended for test usage only and throws an exception if used outside of the Apex test context.
CalculateTaxRequest(taxType)
This constructor is intended for test usage only and throws an exception if used outside of the Apex test context.
Signature
global CalculateTaxRequest(commercetax.CalculateTaxType taxType)
Parameters
taxType
Type: CalculateTaxType
1476
CommerceTax NamespaceTransaction Management

===== PAGE 1491 =====

Indicates whether the tax calculation is for estimated tax or actual tax.
CalculateTaxRequest Properties
Learn more about the available properties with the CalculateTaxRequest  class.
The CalculateTaxRequest  class includes these properties.
isCommit
Indicates whether the tax calculation has to be committed or reported to government authorities.
isHeaderTaxRequested
Indicates whether header tax is enabled in the tax engine (true) or not (false).
shouldVoidTax
Indicates whether to void the tax transaction associated with a document that's mentioned in the referenceDocumentCode
property value with taxType  property value set to Actual  and isCommit  property value set to true.
taxTransactionType
Shows whether the tax transaction is for a credit or debit transaction.
taxType
Shows whether the tax calculation is for estimated or actual tax wherein only actual tax can be submitted.
isCommit
Indicates whether the tax calculation has to be committed or reported to government authorities.
Signature
global Boolean isCommit {get; set;}
Property Value
Type: Boolean
isHeaderTaxRequested
Indicates whether header tax is enabled in the tax engine (true) or not (false).
Signature
global Boolean isHeaderTaxRequested {get; set;}
Property Value
Type: Boolean
shouldVoidTax
Indicates whether to void the tax transaction associated with a document that's mentioned in the referenceDocumentCode
property value with taxType  property value set to Actual  and isCommit  property value set to true.
1477
CommerceTax NamespaceTransaction Management

===== PAGE 1492 =====

Signature
global commercetax.CalculateTaxType shouldVoidTax {get; set;}
Property Value
Type: Boolean
taxTransactionType
Shows whether the tax transaction is for a credit or debit transaction.
Signature
global commercetax.TaxTransactionType taxTransactionType {get; set;}
Property Value
Type: TaxTransactionType
taxType
Shows whether the tax calculation is for estimated or actual tax wherein only actual tax can be submitted.
Signature
global commercetax.CalculateTaxType taxType {get; set;}
Property Value
Type: CalculateTaxType
CalculateTaxRequest Methods
Learn more about the available methods with the CalculateTaxRequest  class.
The CalculateTaxRequest  class includes these methods.
equals(obj)
Maintains the integrity of lists of type CalculateTaxRequest  by determining the equality of external objects in a list. This
method is dynamic and is based on the equals() method in Java.
hashCode()
Maintains the integrity of lists of type CalculateTaxRequest by determining the uniqueness of the external object records
in a list.
toString()
Converts a value to a string.
1478
CommerceTax NamespaceTransaction Management

===== PAGE 1493 =====

equals(obj)
Maintains the integrity of lists of type CalculateTaxRequest  by determining the equality of external objects in a list. This method
is dynamic and is based on the equals() method in Java.
Signature
global Boolean equals(Object obj)
Parameters
obj
Type: Object
External object whose key is to be validated.
Return Value
Type: Boolean
hashCode()
Maintains the integrity of lists of type CalculateTaxRequest by determining the uniqueness of the external object records in a
list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a value to a string.
Signature
global String toString()
Return Value
Type: String
CalculateTaxResponse Class
Sets the values of the tax transaction following a response from the external tax engine. Extends the AbstractTransactionResponse class
and is the top-level response class.
1479
CommerceTax NamespaceTransaction Management

===== PAGE 1494 =====

Namespace
CommerceTax
Example
if(requestType == commercetax.RequestType.CalculateTax){
commercetax.calculatetaxtype type = request.taxtype;
String docCode='';
if(request.DocumentCode == 'simulateEmptyDocumentCode')
docCode = '';
else if(request.DocumentCode != null)
docCode =request.DocumentCode;
else if(request.ReferenceEntityId != null) docCode = request.ReferenceEntityId;
else docCode = String.valueOf(getRandomInteger(0,2147483647));
commercetax.CalculateTaxResponse response = new
commercetax.CalculateTaxResponse();
if(request.isCommit == true) {
response.setStatus(commercetax.TaxTransactionStatus.Committed);
} else {
response.setStatus(commercetax.TaxTransactionStatus.Uncommitted);
}
response.setDocumentCode(docCode);
response.setReferenceDocumentCode(request.referenceDocumentCode);
response.setTaxType(type);
response.setStatusDescription('statusDescription');
if(request.sellerDetails.code == 'testSellerCode') {
response.setDescription('SellerCode fetched from TaxEngine entity');
}
else {
response.setDescription('description');
}
response.setEffectiveDate(system.now());
if(request.transactionDate == null) {
response.setTransactionDate(system.now());
} else {
response.setTransactionDate(request.transactionDate);
}
if(request.taxTransactionType == null) {
response.setTaxTransactionType(commercetax.TaxTransactionType.Debit);
} else {
response.setTaxTransactionType(request.taxTransactionType);
}
if(request.currencyIsoCode == null || request.currencyIsoCode == '') {
response.setCurrencyIsoCode('USD');
} else {
response.setCurrencyIsoCode(request.currencyIsoCode);
}
response.setReferenceEntityId(request.ReferenceEntityId);
}
1480
CommerceTax NamespaceTransaction Management

===== PAGE 1495 =====

CalculateTaxResponse Methods
Learn more about the available methods with the CalculateTaxResponse  class.
CalculateTaxResponse Methods
Learn more about the available methods with the CalculateTaxResponse  class.
The CalculateTaxResponse  class includes these methods.
setAddresses(addresses)
Sets the value of the Addresses field using the addresses contained in an instance of the AddressesResponse class.
setAmountDetails(amountDetails)
Sets the value of the AmountDetails field using an instance of AmountDetailsResponse.
setCurrencyIsoCode(currencyIsoCode)
Sets the value of the CurrencyIsoCode field of the CalculateTaxResponse  object.
setDescription(dscptn)
Sets the value of the Description field of the CalculateTaxResponse  object.
setDocumentCode(documentCode)
Sets the value of the DocumentCode field of the CalculateTaxResponse  object.
setEffectiveDate(effectiveDate)
Sets the value of the EffectiveDate field of the CalculateTaxResponse  object.
setLineItems(lineItems)
Sets the value of the LineItems field of the CalculateTaxResponse  object.
setReferenceDocumentCode(referenceDocumentCode)
Sets the value of the ReferenceDocumentCode field of the CalculateTaxResponse  object.
setReferenceEntityId(referenceEntityId)
Sets the value of the ReferenceEntityId field of the CalculateTaxResponse  object.
setStatus(status)
Sets the value of the Status field of the CalculateTaxResponse  object.
setStatusDescription(statusDescription)
Sets the value of the StatusDescription field of the CalculateTaxResponse  object.
setTaxTransactionId(taxTrxnId)
Sets the value of the TaxTransactionId field of the CalculateTaxResponse  object.
setTaxTransactionType(taxTransactionType)
Sets the value of the TaxTransactionType field of the CalculateTaxResponse  object.
setTaxType(taxType)
Sets the value of the TaxType field of the CalculateTaxResponse  object.
setTransactionDate(transactionDate)
Sets the value of the TransactionDate field of the CalculateTaxResponse  object.
setAddresses(addresses)
Sets the value of the Addresses field using the addresses contained in an instance of the AddressesResponse class.
1481
CommerceTax NamespaceTransaction Management

===== PAGE 1496 =====

Signature
global void setAddresses(commercetax.AddressesResponse addresses)
Parameters
addresses
Type: AddressesResponse
Contains Ship To, Ship From, and Sold To addresses.
Return Value
Type: void
setAmountDetails(amountDetails)
Sets the value of the AmountDetails field using an instance of AmountDetailsResponse.
Signature
global void setAmountDetails(commercetax.AmountDetailsResponse amountDetails)
Parameters
amountDetails
Type: AmountDetailsResponse
The tax amount details for a line item on which tax was calculated.
Return Value
Type: void
setCurrencyIsoCode(currencyIsoCode)
Sets the value of the CurrencyIsoCode field of the CalculateTaxResponse  object.
Signature
global void setCurrencyIsoCode(String currencyIsoCode)
Parameters
currencyIsoCode
Type: String
Three-letter ISO 4217 currency code associated with a tax object.
Return Value
Type: void
1482
CommerceTax NamespaceTransaction Management

===== PAGE 1497 =====

setDescription(dscptn)
Sets the value of the Description field of the CalculateTaxResponse  object.
Signature
global void setDescription(String dscptn)
Parameters
dscptn
Type: String
Optional description for providing more information about the calculate tax response.
Return Value
Type: void
setDocumentCode(documentCode)
Sets the value of the DocumentCode field of the CalculateTaxResponse  object.
Signature
global void setDocumentCode(String documentCode)
Parameters
documentCode
Type: String
Code for a tax document that’s created by the tax engine for the calculation process.
Return Value
Type: void
setEffectiveDate(effectiveDate)
Sets the value of the EffectiveDate field of the CalculateTaxResponse  object.
Signature
global void setEffectiveDate(Datetime effectiveDate)
Parameters
effectiveDate
Type: Datetime
1483
CommerceTax NamespaceTransaction Management

===== PAGE 1498 =====

The date a tax calculation action takes effect. This parameter is optional and is provided only for recordkeeping purpose. Additionally,
this parameter is used to determine the tax rates or rules and overrides the transaction date. For example, if the tax calculation
request is placed on January 3 and the transaction date is January 1, you can set the effective date as January 1.
Return Value
Type: void
setLineItems(lineItems)
Sets the value of the LineItems field of the CalculateTaxResponse  object.
Signature
global void setLineItems(List<commercetax.LineItemResponse> lineItems)
Parameters
lineItems
Type: List<LineItemResponse>
Response object that the tax adapter populates from the response of the external tax engine.
Return Value
Type: void
setReferenceDocumentCode(referenceDocumentCode)
Sets the value of the ReferenceDocumentCode field of the CalculateTaxResponse  object.
Signature
global void setReferenceDocumentCode(String referenceDocumentCode)
Parameters
referenceDocumentCode
Type: String
Code for a reference document used in the tax calculation process.
Return Value
Type: void
setReferenceEntityId(referenceEntityId)
Sets the value of the ReferenceEntityId field of the CalculateTaxResponse  object.
1484
CommerceTax NamespaceTransaction Management

===== PAGE 1499 =====

Signature
global void setReferenceEntityId(String referenceEntityId)
Parameters
referenceEntityId
Type: String
ID of an entity related to the line items submitted for tax calculation. For example, if order items were sent for tax calculation, you
could use the ID of their parent order.
Return Value
Type: void
setStatus(status)
Sets the value of the Status field of the CalculateTaxResponse  object.
Signature
global void setStatus(commercetax.TaxTransactionStatus status)
Parameters
status
Type: TaxTransactionStatus
Indicates whether a tax transaction has been committed.
Return Value
Type: void
setStatusDescription(statusDescription)
Sets the value of the StatusDescription field of the CalculateTaxResponse  object.
Signature
global void setStatusDescription(String statusDescription)
Parameters
statusDescription
Type: String
Optional value for providing more information about a tax transaction's status.
Return Value
Type: void
1485
CommerceTax NamespaceTransaction Management

===== PAGE 1500 =====

setTaxTransactionId(taxTrxnId)
Sets the value of the TaxTransactionId field of the CalculateTaxResponse  object.
Signature
public void setTaxTransactionId(String taxTrxnId)
Parameters
taxTrxnId
Type: String
The ID of the Salesforce tax transaction entity that stores information about the tax calculation transaction.
Return Value
Type: void
setTaxTransactionType(taxTransactionType)
Sets the value of the TaxTransactionType field of the CalculateTaxResponse  object.
Signature
global void setTaxTransactionType(commercetax.TaxTransactionType taxTransactionType)
Parameters
taxTransactionType
Type: TaxTransactionType
Whether the tax transaction was for a credit, debit, or voided transaction.
Return Value
Type: void
setTaxType(taxType)
Sets the value of the TaxType field of the CalculateTaxResponse  object.
Signature
global void setTaxType(commercetax.CalculateTaxType taxType)
Parameters
taxType
Type: CalculateTaxType
Indicates whether a tax calculation request is for estimated or actual tax.
1486
CommerceTax NamespaceTransaction Management

===== PAGE 1501 =====

Return Value
Type: void
setTransactionDate(transactionDate)
Sets the value of the TransactionDate field of the CalculateTaxResponse  object.
Signature
global void setTransactionDate(Datetime transactionDate)
Parameters
transactionDate
Type: Datetime
The date that the tax transaction occurred.
Return Value
Type: void
CalculateTaxType Enum
Shows whether a tax calculation request is for estimated or actual tax.
Usage
Used by the CalculateTaxRequest and CalculateTaxResponse class methods.
Enum Values
The commercetax.CalculateTaxType  enum includes these values.
DescriptionValue
Specifies that the tax calculation service should calculate the finalized (actual) tax
for the requested line items.
Actual
Specifies that the tax calculation service should estimate the tax for the requested
line items.
Estimated
CustomTaxAttributesResponse Class
Sets additional data or custom attributes in the tax response.
Namespace
CommerceTax
1487
CommerceTax NamespaceTransaction Management

===== PAGE 1502 =====

CustomTaxAttributesResponse Constructors
Learn more about the available constructors with the CustomTaxAttributesResponse  class.
CustomTaxAttributesResponse Methods
Learn more about the available methods with the CustomTaxAttributesResponse  class.
CustomTaxAttributesResponse Constructors
Learn more about the available constructors with the CustomTaxAttributesResponse  class.
The CustomTaxAttributesResponse  class includes these constructors.
CustomTaxAttributesResponse()
Constructor to set additional data or custom attributes in the tax response.
CustomTaxAttributesResponse()
Constructor to set additional data or custom attributes in the tax response.
Signature
global CustomTaxAttributesResponse()
CustomTaxAttributesResponse Methods
Learn more about the available methods with the CustomTaxAttributesResponse  class.
The CustomTaxAttributesResponse  class includes these methods.
setData(data)
Sets additional data or custom attributes in the tax response.
setData(data)
Sets additional data or custom attributes in the tax response.
Signature
global void setData(Map<String, Object> data)
Parameters
data
Type: Map<String, Object>
Additional data or custom attributes to be included in the tax response.
Return Value
Type: void
1488
CommerceTax NamespaceTransaction Management

===== PAGE 1503 =====

ErrorResponse Class
Use to respond with an error after receiving errors from the PaymentGatewayAdapter methods of the CommercePayments namespace,
such as request-forbidden responses, custom validation errors, or expired API tokens.
Namespace
CommerceTax
Example
This example snippet of a mock tax adapter shows a hypothetical scenario to demo an error response. The adapter receives request
information from TaxEngineContext and stores it in an instance of CalculateTaxRequest. If the request's documentCode
property is null or indicates an error, the adapter returns an error response with information about the error.
global virtual class MockAdapter implements commercetax.TaxEngineAdapter {
global commercetax.TaxEngineResponse processRequest(commercetax.TaxEngineContext
taxEngineContext) {
commercetax.RequestType requestType = taxEngineContext.getRequestType();
commercetax.CalculateTaxRequest request =
(commercetax.CalculateTaxRequest)taxEngineContext.getRequest();
if(request.documentCode == null) {
return new commercetax.ErrorResponse(commercetax.resultcode.TaxEngineError,
'404', 'documentCode is mandatory');
}
if(request.documentCode == 'TaxEngineError') {
return new commercetax.ErrorResponse(commercetax.resultcode.TaxEngineError,
'504', 'documentCode - not supported');
}
if(request.documentCode == 'simulateValidationFailureInAdapter') {
return new commercetax.ErrorResponse(commercetax.resultcode.TaxEngineError,
'400', 'validations for documentCode failed in adapter');
}
if(request.documentCode == 'simulateMalformedErrorInAdapter') {
return new
commercetax.ErrorResponse(commercetax.resultcode.TaxEngineError, null, 'malformed adapter
error response');
}
if(request.documentCode == 'simulateTaxEngineProcessFailure') {
return new commercetax.ErrorResponse(commercetax.resultcode.TaxEngineError,
'500', 'Tax Engine couldnt process your request');
}
ErrorResponse Constructors
Learn more about the available constructors with the ErrorResponse  class.
1489
CommerceTax NamespaceTransaction Management

===== PAGE 1504 =====

ErrorResponse Constructors
Learn more about the available constructors with the ErrorResponse  class.
The ErrorResponse  class includes these constructors.
ErrorResponse(resultCode, errorCode, errorMessage)
Constructor to initialize an ErrorResponse  object from the result code, error code, and error message sent from the tax engine.
ErrorResponse(resultCode, errorCode, errorMessage)
Constructor to initialize an ErrorResponse  object from the result code, error code, and error message sent from the tax engine.
Signature
global ErrorResponse(commercetax.ResultCode resultCode, String errorCode, String
errorMessage)
Parameters
resultCode
Type: ResultCode
Code for the type of result sent by the tax engine.
errorCode
Type: String
Code for the type of error sent by the tax engine.
Codes must match the HTTP status codes to be returned to the user. Here are a few examples:
• If the status code is for a bad request, set errorCode  to 400.
• If the status code is for a forbidden request, set errorCode  to 403.
• If errorCode  isn't a valid HTTP status code, a 500 internal server error is returned.
errorMessage
Type: String
The error message sent by the tax engine.
HeaderTaxAddressesRequest Class
Captures the address values that are applicable for the quote or order transaction.
Namespace
CommerceTax
HeaderTaxAddressesRequest Constructors
Learn more about the constructors available with the HeaderTaxAddressesRequest  class.
HeaderTaxAddressesRequest Properties
Learn more about the available properties with the HeaderTaxAddressesRequest  class.
1490
CommerceTax NamespaceTransaction Management

===== PAGE 1505 =====

HeaderTaxAddressesRequest Methods
Learn more about the available methods with the HeaderTaxAddressesRequest  class.
HeaderTaxAddressesRequest Constructors
Learn more about the constructors available with the HeaderTaxAddressesRequest  class.
The HeaderTaxAddressesRequest  class includes these constructors.
HeaderTaxAddressesRequest(shipFrom, shipTo, soldTo, billTo, taxEngineAddress)
Constructor for initializing the required addresses of the tax addresses request such as the ship from, ship to, sold to, and bill to
addresses. This constructor is intended for test usage and throws an exception if used outside of the Apex test context.
HeaderTaxAddressesRequest(shipFrom, shipTo, soldTo, billTo, taxEngineAddress)
Constructor for initializing the required addresses of the tax addresses request such as the ship from, ship to, sold to, and bill to addresses.
This constructor is intended for test usage and throws an exception if used outside of the Apex test context.
Signature
global HeaderTaxAddressesRequest(commercetax.TaxAddressRequest shipFrom,
commercetax.TaxAddressRequest shipTo, commercetax.TaxAddressRequest soldTo,
commercetax.TaxAddressRequest billTo, commercetax.TaxAddressRequest taxEngineAddress)
Parameters
shipFrom
Type: TaxAddressRequest
Address where a line item was shipped from.
shipTo
Type: TaxAddressRequest
Address where a line item was shipped to.
soldTo
Type: TaxAddressRequest
Address of the line item's buyer.
billTo
Type: TaxAddressRequest
Person or group who was billed for the line item.
taxEngineAddress
Type: TaxAddressRequest
Address that the tax engine uses to calculate tax.
HeaderTaxAddressesRequest Properties
Learn more about the available properties with the HeaderTaxAddressesRequest  class.
The HeaderTaxAddressesRequest  class includes these properties.
1491
CommerceTax NamespaceTransaction Management

===== PAGE 1506 =====

billTo
Specifies the billTo address for a line item on which tax was calculated.
shipFrom
Specifies the shipFrom address for a line item on which tax was calculated.
shipTo
Specifies the shipTo address for a line item on which tax was calculated.
soldTo
Specifies the soldTo address for a line item on which tax was calculated.
taxEngineAddress
Address used by the tax engine when calculating tax for a line item.
billTo
Specifies the billTo address for a line item on which tax was calculated.
Signature
global commercetax.TaxAddressRequest billTo {get; set;}
Property Value
Type: TaxAddressRequest
shipFrom
Specifies the shipFrom address for a line item on which tax was calculated.
Signature
global commercetax.TaxAddressRequest shipFrom {get; set;}
Property Value
Type: TaxAddressRequest
shipTo
Specifies the shipTo address for a line item on which tax was calculated.
Signature
global commercetax.TaxAddressRequest shipTo {get; set;}
Property Value
Type: TaxAddressRequest
1492
CommerceTax NamespaceTransaction Management

===== PAGE 1507 =====

soldTo
Specifies the soldTo address for a line item on which tax was calculated.
Signature
global commercetax.TaxAddressRequest soldTo {get; set;}
Property Value
Type: TaxAddressRequest
taxEngineAddress
Address used by the tax engine when calculating tax for a line item.
Signature
global commercetax.TaxAddressRequest taxEngineAddress {get; set;}
Property Value
Type: TaxAddressRequest
HeaderTaxAddressesRequest Methods
Learn more about the available methods with the HeaderTaxAddressesRequest  class.
The HeaderTaxAddressesRequest  class includes these methods.
equals(obj)
Maintains the integrity of lists of type HeaderTaxAddressesRequest  by determining the equality of external objects in a
list. This method is dynamic and is based on the equals() method in Java.
hashCode()
Maintains the integrity of lists of type TaxAddressesRequest  by determining the uniqueness of the external objects in a list.
toString()
Converts a value to a string.
equals(obj)
Maintains the integrity of lists of type HeaderTaxAddressesRequest  by determining the equality of external objects in a list.
This method is dynamic and is based on the equals() method in Java.
Signature
global Boolean equals(Object obj)
1493
CommerceTax NamespaceTransaction Management

===== PAGE 1508 =====

Parameters
obj
Type: Object
External object whose key is to be validated.
Return Value
Type: Boolean
hashCode()
Maintains the integrity of lists of type TaxAddressesRequest  by determining the uniqueness of the external objects in a list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a value to a string.
Signature
global String toString()
Return Value
Type: String
ImpositionResponse Class
Stores details of tax impositions from the external tax engine.
Namespace
CommerceTax
Example
In this mock adapter example, the adapter sets the TaxDetailsResponse.setImposition()  method parameter to null if
the request's document code indicates that the tax calculation didn't require any exceptions. Otherwise, it creates an instance of
ImpositionResponse  and sets its SubType and Type values, and then assigns it to TaxDetailsResponse.
if(request.DocumentCode == 'SetsNullForResponseWithoutException'){
taxDetailsResponse.setImposition(null);
}else{
1494
CommerceTax NamespaceTransaction Management

===== PAGE 1509 =====

commercetax.ImpositionResponse imposition = new
commercetax.ImpositionResponse();
imposition.setSubType('subtype');
imposition.setType('type');
taxDetailsResponse.setImposition(imposition);
}
ImpositionResponse Methods
Learn more about the available methods with the ImpositionResponse  class.
ImpositionResponse Methods
Learn more about the available methods with the ImpositionResponse  class.
The ImpositionResponse  class includes these methods.
setId(id)
Sets the ID field of the ImpositionResponse  class.
setName(name)
Sets the Name field of the ImpositionResponse  class.
setSubType(subType)
Sets the SubType field of the ImpositionResponse  class.
setType(type)
Sets the Type field of the ImpositionResponse  class.
setId(id)
Sets the ID field of the ImpositionResponse  class.
Signature
global void setId(String id)
Parameters
id
Type: String
User-defined ID value used for referencing the tax imposition.
Return Value
Type: void
setName(name)
Sets the Name field of the ImpositionResponse  class.
1495
CommerceTax NamespaceTransaction Management

===== PAGE 1510 =====

Signature
global void setName(String name)
Parameters
name
Type: String
Optional user-defined name for the tax imposition response.
Return Value
Type: void
setSubType(subType)
Sets the SubType field of the ImpositionResponse  class.
Signature
global void setSubType(String subType)
Parameters
subType
Type: String
Many tax calculation organizations use types and subtypes to categorize their tax imposition procedures. If the tax engine you use
follows this process, set the subtype with this parameter.
Return Value
Type: void
setType(type)
Sets the Type field of the ImpositionResponse  class.
Signature
public void setType(String type)
Parameters
type
Type: String
Many tax calculation organizations use types and subtypes to categorize their tax imposition procedures. If the tax engine you use
follows this process, set the type with this parameter.
1496
CommerceTax NamespaceTransaction Management

===== PAGE 1511 =====

Return Value
Type: void
JurisdictionResponse Class
Stores details from the external tax engine about the tax jurisdiction used in the tax calculation process. A tax jurisdiction represents a
government entity that collects tax.
Namespace
CommerceTax
Example
In this mock adapter example, the adapter sets the TaxDetailsResponse.setJurisdiction()  method parameter to null
if the request's document code indicates that the tax calculation didn't require any exceptions. Otherwise, it creates an instance of
JurisdictionResponse  and sets its address values. Because this code represents a mock adapter, the example defines the
address parameters directly. In a standard implementation, the jurisdiction's setters receive values passed from the eternal tax engine.
if(request.DocumentCode == 'SetsNullForResponseWithoutException'){
taxDetailsResponse.setJurisdiction(null);
}else{
commercetax.JurisdictionResponse jurisdiction = new
commercetax.JurisdictionResponse();
jurisdiction.setCountry('country');
jurisdiction.setRegion('region');
jurisdiction.setName('name');
jurisdiction.setStateAssignedNumber('stateAssignedNo');
jurisdiction.setId('id');
jurisdiction.setLevel('level');
taxDetailsResponse.setJurisdiction(jurisdiction);
}
JurisdictionResponse Methods
Learn more about the available methods with the JurisdictionResponse  class.
JurisdictionResponse Methods
Learn more about the available methods with the JurisdictionResponse  class.
The JurisdictionResponse  class includes these methods.
setCountry(country)
Sets the Country field of the JurisdictionResponse  class.
setId(id)
Sets the ID field of the JurisdictionResponse  class.
setLevel(level)
Sets the Level field of the JurisdictionResponse  class.
1497
CommerceTax NamespaceTransaction Management

===== PAGE 1512 =====

setName(name)
Sets the Name field of the JurisdictionResponse  class.
setRegion(region)
Sets the Region value of the JurisdictionResponse  class.
setStateAssignedNumber(stateAssignedNo)
Sets the StateAssignedNumber field of the JurisdictionResponse  class.
setCountry(country)
Sets the Country field of the JurisdictionResponse  class.
Signature
global void setCountry(String country)
Parameters
country
Type: String
The country of the tax jurisdiction entity's address.
Return Value
Type: void
setId(id)
Sets the ID field of the JurisdictionResponse  class.
Signature
global void setId(String id)
Parameters
id
Type: String
User-defined Id value used to reference the jurisdiction response.
Return Value
Type: void
setLevel(level)
Sets the Level field of the JurisdictionResponse  class.
1498
CommerceTax NamespaceTransaction Management

===== PAGE 1513 =====

Signature
global void setLevel(String level)
Parameters
level
Type: String
Level value used in the jurisdiction entity's address.
Return Value
Type: void
setName(name)
Sets the Name field of the JurisdictionResponse  class.
Signature
global void setName(String name)
Parameters
name
Type: String
Optional user-defined name field for referencing the jurisdiction response.
Return Value
Type: void
setRegion(region)
Sets the Region value of the JurisdictionResponse  class.
Signature
global void setRegion(String region)
Parameters
region
Type: String
Region value used in the tax jurisdiction entity's address.
Return Value
Type: void
1499
CommerceTax NamespaceTransaction Management

===== PAGE 1514 =====

setStateAssignedNumber(stateAssignedNo)
Sets the StateAssignedNumber field of the JurisdictionResponse  class.
Signature
global void setStateAssignedNumber(String stateAssignedNo)
Parameters
stateAssignedNo
Type: String
State assigned number value of the tax jurisdiction entity's address.
Return Value
Type: void
LineItemResponse Class
Response class that stores details of a list of one or more line items on which the tax engine has calculated tax.
Namespace
CommerceTax
Example
This example uses a LineItemResponse  list to store information about each line item that was processed as part of the request.
For simplicity, the sample code uses a static value of 1 for the tax rate. However, most integrations typically have a more complex process
for determining a tax rate. Most integrations also build a TaxDetailsResponse  list to store the actual tax value information that
they assign to each line item in the LineItemResponse  list.
Double totalTax = 0.0;
Double totalAmount = 0.0;
List<commercetax.LineItemResponse> lineItemResponses = new
List<commercetax.LineItemResponse>();
for(Commercetax.TaxLineItemRequest lineItem : request.lineItems){
commercetax.AddressesResponse addressesRes = new
commercetax.AddressesResponse();
if(request.DocumentCode == 'SetsNullForResponseWithoutException'){
addressesRes.setShipFrom(null);
addressesRes.setShipTO(null);
addressesRes.setSoldTo(null);
}else{
commercetax.AddressResponse addRes = new commercetax.AddressResponse();
addRes.setLocationCode('locationCode');
addressesRes.setShipFrom(addRes);
addressesRes.setShipTO(addRes);
addressesRes.setSoldTo(addRes);
}
1500
CommerceTax NamespaceTransaction Management

===== PAGE 1515 =====

commercetax.LineItemResponse lineItemResponse = new
commercetax.LineItemResponse();
Double totalLineTax = 0;
List<commercetax.TaxDetailsResponse> taxDetailsResponses = new
List<commercetax.TaxDetailsResponse>();
for(integer i =0;i<1;i++){
Integer rate = 1;
Double taxableAmount = lineItem.amount;
commercetax.TaxDetailsResponse taxDetailsResponse = new
commercetax.TaxDetailsResponse();
taxDetailsResponse.setRate(Double.valueOf(rate));
taxDetailsResponse.setTaxableAmount(taxableAmount);
Double tax = taxableAmount*rate;
totalLineTax+=tax;
taxDetailsResponse.setTax(taxableAmount*rate);
taxDetailsResponse.setExemptAmount(0);
taxDetailsResponse.setExemptReason('exemptReason');
taxDetailsResponse.setTaxRegionId('taxRegionId');
taxDetailsResponse.setTaxId(String.valueOf(getRandomInteger(0,2323233)));
taxDetailsResponse.setSerCode('serCode');
taxDetailsResponse.setTaxAuthorityTypeId('taxAuthorityTypeId');
if(request.DocumentCode == 'SetsNullForResponseWithoutException'){
taxDetailsResponse.setImposition(null);
}else{
commercetax.ImpositionResponse imposition = new
commercetax.ImpositionResponse();
imposition.setSubType('subtype');
imposition.setType('type');
taxDetailsResponse.setImposition(imposition);
}
if(request.DocumentCode == 'SetsNullForResponseWithoutException'){
taxDetailsResponse.setJurisdiction(null);
}else{
commercetax.JurisdictionResponse jurisdiction = new
commercetax.JurisdictionResponse();
jurisdiction.setCountry('country');
jurisdiction.setRegion('region');
jurisdiction.setName('name');
jurisdiction.setStateAssignedNumber('stateAssignedNo');
jurisdiction.setId('id');
jurisdiction.setLevel('level');
taxDetailsResponse.setJurisdiction(jurisdiction);
}
taxDetailsResponses.add(taxDetailsResponse);
}
lineItemResponse.setTaxes(taxDetailsResponses);
totalTax +=totalLineTax;
totalAmount+=lineItem.amount;
1501
CommerceTax NamespaceTransaction Management

===== PAGE 1516 =====

LineItemResponse Methods
Learn more about the available methods with the LineItemResponse  class.
LineItemResponse Methods
Learn more about the available methods with the LineItemResponse  class.
The LineItemResponse  class includes these methods.
setAddresses(addresses)
Sets the Addresses field on the LineItemResponse  using an instance of AddressesResponse  class.
setAmountDetails(amountDetails)
Sets the Amount Details field on the LineItemResponse  using an instance of AmountDetails.
setCustomTaxAttributes(customTaxAttributes)
Uses an instance of CustomTaxAttributesResponse  class to include additional attributes in the tax response at line item
level.
setEffectiveDate(effectiveDate)
Sets the EffectiveDate field on the LineItemResponse  class. Effective Date fields are optional fields that store the date that a
transaction takes effect. We provide these fields only for recordkeeping purposes – for example, if you must report an effective date
to an external general ledger system. Salesforce doesn't use them to calculate any tax or payment values.
setIsTaxable(isTaxable)
Sets the IsTaxable field on the LineItemResponse  class.
setLineNumber(lineNumber)
Sets the LineNumber field on the LineItemResponse  class.
setProductCode(productCode)
Sets the ProductCode field on the LineItemResponse  class.
setQuantity(quantity)
Sets the Quantity field on the LineItemResponse  class.
setTaxCode(taxCode)
Sets the TaxCode field on the LineItemResponse.
setTaxes(taxes)
Sets the Taxes field on a LineItemResponse.
setAddresses(addresses)
Sets the Addresses field on the LineItemResponse  using an instance of AddressesResponse  class.
Signature
global void setAddresses(commercetax.AddressesResponse addresses)
Parameters
addresses
Type: AddressesResponse
1502
CommerceTax NamespaceTransaction Management

===== PAGE 1517 =====

Class that contains methods to set the Ship To, Ship From, and Sold To address information.
Return Value
Type: void
setAmountDetails(amountDetails)
Sets the Amount Details field on the LineItemResponse  using an instance of AmountDetails.
Signature
global void setAmountDetails(commercetax.AmountDetailsResponse amountDetails)
Parameters
amountDetails
Type: AmountDetailsResponse
Class that contains methods to set the tax amount, total amount with tax, total amount, and exempt amount.
Return Value
Type: void
setCustomTaxAttributes(customTaxAttributes)
Uses an instance of CustomTaxAttributesResponse  class to include additional attributes in the tax response at line item level.
Signature
global void setCustomTaxAttributes(commercetax.CustomTaxAttributesResponse
customTaxAttributes)
Parameters
customTaxAttributes
Type: CustomTaxAttributesResponse
Additional data or custom attributes to include in the tax response.
Return Value
Type: void
setEffectiveDate(effectiveDate)
Sets the EffectiveDate field on the LineItemResponse  class. Effective Date fields are optional fields that store the date that a
transaction takes effect. We provide these fields only for recordkeeping purposes – for example, if you must report an effective date to
an external general ledger system. Salesforce doesn't use them to calculate any tax or payment values.
1503
CommerceTax NamespaceTransaction Management

===== PAGE 1518 =====

Signature
global void setEffectiveDate(Datetime effectiveDate)
Parameters
effectiveDate
Type: Datetime
Optional field that stores the date that a transaction takes effect.
Return Value
Type: void
setIsTaxable(isTaxable)
Sets the IsTaxable field on the LineItemResponse  class.
Signature
global void setIsTaxable(Boolean isTaxable)
Parameters
isTaxable
Type: Boolean
Whether line items were taxed as part of the tax calculation request.
Return Value
Type: void
setLineNumber(lineNumber)
Sets the LineNumber field on the LineItemResponse  class.
Signature
global void setLineNumber(String lineNumber)
Parameters
lineNumber
Type: String
User-defined number used to identify a line item.
Return Value
Type: void
1504
CommerceTax NamespaceTransaction Management

===== PAGE 1519 =====

setProductCode(productCode)
Sets the ProductCode field on the LineItemResponse  class.
Signature
global void setProductCode(String productCode)
Parameters
productCode
Type: String
Code for the product that a line item represents.
Return Value
Type: void
setQuantity(quantity)
Sets the Quantity field on the LineItemResponse  class.
Signature
global void setQuantity(Double quantity)
Parameters
quantity
Type: Double
Quantity of a line item.
Return Value
Type: void
setTaxCode(taxCode)
Sets the TaxCode field on the LineItemResponse.
Signature
global void setTaxCode(String taxCode)
Parameters
taxCode
Type: String
Federal code that an individual or business uses to pay their taxes to a federal or state government. The tax engine uses this code
during the tax calculation process.
1505
CommerceTax NamespaceTransaction Management

===== PAGE 1520 =====

Return Value
Type: void
setTaxes(taxes)
Sets the Taxes field on a LineItemResponse.
Signature
global void setTaxes(List<commercetax.TaxDetailsResponse> taxes)
Parameters
taxes
Type: List<TaxDetailsResponse>
Tax values applied to a line item in the LineItemResponse list. This information is stored in a list of TaxDetailsResponses,
which contains values such as tax, taxable amount, and tax rate.
Return Value
Type: void
LineTaxAddressesRequest Class
Stores details of the addresses applied per line item in a tax calculation request.
Namespace
CommerceTax
LineTaxAddressesRequest Constructors
Learn more about the constructors available with the LineTaxAddressesRequest  class.
LineTaxAddressesRequest Properties
Learn more about the available properties with the LineTaxAddressesRequest  class.
LineTaxAddressesRequest Methods
Learn more about the available methods with the LineTaxAddressesRequest  class.
LineTaxAddressesRequest Constructors
Learn more about the constructors available with the LineTaxAddressesRequest  class.
The LineTaxAddressesRequest  class includes these constructors.
LineTaxAddressesRequest(shipFrom, shipTo, soldTo, billTo, taxEngineAddress)
Constructor for initializing the required addresses for a line item of the tax addresses request such as the ship to, ship from, and bill
to addresses. This constructor is intended for test usage and throws an exception if used outside of the Apex test context.
1506
CommerceTax NamespaceTransaction Management

===== PAGE 1521 =====

LineTaxAddressesRequest(shipFrom, shipTo, soldTo, billTo, taxEngineAddress)
Constructor for initializing the required addresses for a line item of the tax addresses request such as the ship to, ship from, and bill to
addresses. This constructor is intended for test usage and throws an exception if used outside of the Apex test context.
Signature
global LineTaxAddressesRequest(commercetax.TaxAddressRequest shipFrom,
commercetax.TaxAddressRequest shipTo, commercetax.TaxAddressRequest soldTo,
commercetax.TaxAddressRequest billTo, commercetax.TaxAddressRequest taxEngineAddress)
Parameters
shipFrom
TaxAddressRequest
Address where a line item was shipped from.
shipTo
TaxAddressRequest
Address where a line item is shipped to.
soldTo
TaxAddressRequest
Address of the line item's buyer.
billTo
TaxAddressRequest
Person or group who was billed for the line item.
taxEngineAddress
TaxAddressRequest
Address that the tax engine uses to calculate tax.
LineTaxAddressesRequest Properties
Learn more about the available properties with the LineTaxAddressesRequest  class.
The LineTaxAddressesRequest  class includes these properties.
billTo
The Bill To address for a line item.
shipFrom
The Ship From address for a line item.
shipTo
The Ship To address for a line item.
soldTo
The Sold To address for a line item.
1507
CommerceTax NamespaceTransaction Management

===== PAGE 1522 =====

billTo
The Bill To address for a line item.
Signature
global commercetax.TaxAddressRequest billTo {get; set;}
Property Value
Type: TaxAddressRequest
shipFrom
The Ship From address for a line item.
Signature
global commercetax.TaxAddressRequest shipFrom {get; set;}
Property Value
Type: TaxAddressRequest
shipTo
The Ship To address for a line item.
Signature
global commercetax.TaxAddressRequest shipTo {get; set;}
Property Value
Type: TaxAddressRequest
soldTo
The Sold To address for a line item.
Signature
global commercetax.TaxAddressRequest soldTo {get; set;}
Property Value
Type: TaxAddressRequest
LineTaxAddressesRequest Methods
Learn more about the available methods with the LineTaxAddressesRequest  class.
1508
CommerceTax NamespaceTransaction Management

===== PAGE 1523 =====

The LineTaxAddressesRequest  class includes these methods.
equals(obj)
Maintains the integrity of lists of type LineTaxAddressesRequest  by determining the equality of external objects in a list.
This method is dynamic and is based on the equals() method in Java.
hashCode()
Maintains the integrity of lists of type LineTaxAddressesRequest  by determining the uniquness of the external object
records in a list.
toString()
Converts a value to a string.
equals(obj)
Maintains the integrity of lists of type LineTaxAddressesRequest  by determining the equality of external objects in a list. This
method is dynamic and is based on the equals() method in Java.
Signature
global Boolean equals(Object obj)
Parameters
obj
Type: Object
External object whose key is to be validated.
Return Value
Type: Boolean
hashCode()
Maintains the integrity of lists of type LineTaxAddressesRequest  by determining the uniquness of the external object records
in a list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a value to a string.
1509
CommerceTax NamespaceTransaction Management

===== PAGE 1524 =====

Signature
global String toString()
Return Value
Type: String
RequestType Enum
Shows the type of tax request made to the tax engine.
Usage
Used by the TaxEngineContext class method.
Enum Values
The commercetax.RequestType  enum includes these values.
DescriptionValue
Represents a request to calculate tax on a list of taxable line items.CalculateTax
ResultCode Enum
Code that represents the results of a tax request made to the tax engine.
Usage
Used by the ErrorResponse class method.
Enum Values
The commercetax.ResultCode  enum includes these values.
DescriptionValue
Represents an error that occurred during the tax request process.TaxEngineError
Specifies if the document mentioned as a referenceDocumentCode  value
isn't available in the tax engine.
ReferenceDocumentCodeMissing
RuleDetailsResponse Class
Contains details about the tax rules used for tax calculation.
Namespace
CommerceTax
1510
CommerceTax NamespaceTransaction Management

===== PAGE 1525 =====

RuleDetailsResponse Methods
Learn more about the available methods with the RuleDetailsResponse  class.
RuleDetailsResponse Methods
Learn more about the available methods with the RuleDetailsResponse  class.
The RuleDetailsResponse  includes these methods.
RuleDetailsResponse()
Contains information about the tax rules used when calculating tax for line items.
setNonTaxableRuleId(nonTaxableRuleId)
Sets the NonTaxableRuleId field of the RuleDetailsResponse.
setNonTaxableType(nonTaxableType)
Sets the NonTaxableType field of the RuleDetailsResponse.
setRateRuleId(rateRuleId)
Sets the RateRuleId field of the RuleDetailsResponse.
setRateSourceId(rateSourceId)
Sets the RateSourceId field on the RuleDetailsResponse.
RuleDetailsResponse()
Contains information about the tax rules used when calculating tax for line items.
Signature
global void RuleDetailsResponse()
Return Value
Type: void
setNonTaxableRuleId(nonTaxableRuleId)
Sets the NonTaxableRuleId field of the RuleDetailsResponse.
Signature
global void setNonTaxableRuleId(String nonTaxableRuleId)
Parameters
nonTaxableRuleId
Type: String
ID of the tax rule applied to non-taxable line items.
1511
CommerceTax NamespaceTransaction Management

===== PAGE 1526 =====

Return Value
Type: void
setNonTaxableType(nonTaxableType)
Sets the NonTaxableType field of the RuleDetailsResponse.
Signature
global void setNonTaxableType(String nonTaxableType)
Parameters
nonTaxableType
Type: String
Reason (from several possible types) that a line item is non-taxable.
Return Value
Type: void
setRateRuleId(rateRuleId)
Sets the RateRuleId field of the RuleDetailsResponse.
Signature
global void setRateRuleId(String rateRuleId)
Parameters
rateRuleId
Type: String
ID of the tax rule used to determine a tax rate.
Return Value
Type: void
setRateSourceId(rateSourceId)
Sets the RateSourceId field on the RuleDetailsResponse.
Signature
global void setRateSourceId(String rateSourceId)
1512
CommerceTax NamespaceTransaction Management

===== PAGE 1527 =====

Parameters
rateSourceId
Type: String
ID of the source object used for calculating tax rate.
Return Value
Type: void
TaxAddressesRequest Class
Contains methods to get and set tax address values.
Namespace
CommerceTax
TaxAddressesRequest Constructors
Learn more about the available constructors with the TaxAddressesRequest  class.
TaxAddressesRequest Properties
Learn more about the available properties with the TaxAddressesRequest  class.
TaxAddressesRequest Methods
Learn more about the available methods with the TaxAddressesRequest  class.
TaxAddressesRequest Constructors
Learn more about the available constructors with the TaxAddressesRequest  class.
The TaxAddressesRequest  class includes these constructors.
TaxAddressesRequest(shipFrom, shipTo, soldTo, billTo, taxEngineAddress)
Constructor for defining addresses for the tax addresses request. This constructor is intended for test usage and throws an exception
if used outside of the Apex test context.
TaxAddressesRequest(shipFrom, shipTo, soldTo, billTo, taxEngineAddress)
Constructor for defining addresses for the tax addresses request. This constructor is intended for test usage and throws an exception if
used outside of the Apex test context.
Signature
global TaxAddressesRequest(commercetax.TaxAddressRequest shipFrom,
commercetax.TaxAddressRequest shipTo, commercetax.TaxAddressRequest soldTo,
commercetax.TaxAddressRequest billTo, commercetax.TaxAddressRequest taxEngineAddress)
1513
CommerceTax NamespaceTransaction Management

===== PAGE 1528 =====

Parameters
shipFrom
TaxAddressRequest
The address where a line item was shipped from.
shipTo
TaxAddressRequest
The address where a line item is shipped to.
soldTo
TaxAddressRequest
The address of the line item's buyer.
billTo
TaxAddressRequest
The person or group who was billed for the line item.
taxEngineAddress
TaxAddressRequest
The address that the tax engine uses to calculate tax.
TaxAddressesRequest Properties
Learn more about the available properties with the TaxAddressesRequest  class.
The TaxAddressesRequest  class includes these properties.
billTo
The Bill To address for a line item.
shipFrom
The Ship From address for a line item.
shipTo
The Ship To address for a line item.
soldTo
The Sold To address for a line item.
taxEngineAddress
The Tax Engine Address for a line item.
billTo
The Bill To address for a line item.
Signature
global commercetax.TaxAddressRequest billTo {get; set;}
1514
CommerceTax NamespaceTransaction Management

===== PAGE 1529 =====

Property Value
TaxAddressRequest
shipFrom
The Ship From address for a line item.
Signature
global commercetax.TaxAddressRequest shipFrom {get; set;}
Property Value
TaxAddressRequest
shipTo
The Ship To address for a line item.
Signature
public commercetax.TaxAddressRequest shipTo {get; set;}
Property Value
TaxAddressRequest
soldTo
The Sold To address for a line item.
Signature
global commercetax.TaxAddressRequest soldTo {get; set;}
Property Value
TaxAddressRequest
taxEngineAddress
The Tax Engine Address for a line item.
Signature
global commercetax.TaxAddressRequest taxEngineAddress {get; set;}
Property Value
TaxAddressRequest
1515
CommerceTax NamespaceTransaction Management

===== PAGE 1530 =====

TaxAddressesRequest Methods
Learn more about the available methods with the TaxAddressesRequest  class.
The TaxAddressesRequest  class includes these methods.
equals(obj)
Maintains the integrity of lists of type TaxAddressesRequest  by determining the equality of external objects in a list. This
method is dynamic and is based on the equals() method in Java.
hashCode()
Maintains the integrity of lists of type TaxAddressesRequest  by determining the uniqueness of the external object records
in a list.
toString()
Converts a value to a string.
equals(obj)
Maintains the integrity of lists of type TaxAddressesRequest  by determining the equality of external objects in a list. This method
is dynamic and is based on the equals() method in Java.
Signature
global Boolean equals(Object obj)
Parameters
obj
Type: Object
External object whose key is to be validated.
Return Value
Type: Boolean
hashCode()
Maintains the integrity of lists of type TaxAddressesRequest  by determining the uniqueness of the external object records in a
list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a value to a string.
1516
CommerceTax NamespaceTransaction Management

===== PAGE 1531 =====

Signature
global String toString()
Return Value
Type: String
TaxAddressRequest Class
Contains address details used for tax calculation.
Namespace
CommerceTax
TaxAddressRequest Constructors
Learn more about the available constructors with the TaxAddressRequest  class.
TaxAddressRequest Properties
Learn more about the available properties with the TaxAddressRequest  class.
TaxAddressRequest Methods
Learn more about the available methods with the TaxAddressRequest  class.
TaxAddressRequest Constructors
Learn more about the available constructors with the TaxAddressRequest  class.
The TaxAddressRequest  class includes these constructors.
TaxAddressRequest(city, country, latitude, longitude, postalCode, state, street, locationCode)
Initializes the TaxAddressRequest object using address details. This constructor is intended for test usage and throws an
exception if used outside of the Apex test context.
TaxAddressRequest(city, country, latitude, longitude, postalCode, state, street,
locationCode)
Initializes the TaxAddressRequest object using address details. This constructor is intended for test usage and throws an exception
if used outside of the Apex test context.
Signature
global TaxAddressRequest(String city, String country, Double latitude, Double longitude,
String postalCode, String state, String street, String locationCode)
Parameters
city
Type: String
City used in an address, which is required for tax calculation.
1517
CommerceTax NamespaceTransaction Management

===== PAGE 1532 =====

country
Type: String
Country used in an address, which is required for tax calculation.
latitude
Type: Double
Latitude used in an address, which is required for tax calculation.
longitude
Type: Double
Longitude used in an address, which is required for tax calculation.
postalCode
Type: String
Postal code used in an address, which is required for tax calculation.
state
Type: String
State used in an address, which is required for tax calculation.
street
Type: String
Street used in an address, which is required for tax calculation.
locationCode
Type: String
Location code used in an address, which is required for tax calculation.
TaxAddressRequest Properties
Learn more about the available properties with the TaxAddressRequest  class.
The TaxAddressRequest  class includes these properties.
city
City used in an address, which is required for tax calculation.
country
Country used in an address, which is required for tax calculation.
countryCode
Country code used in an address, which is required for tax calculation.
latitude
Latitude used in an address, which is required for tax calculation.
locationCode
Location code used in an address, which is required for tax calculation.
longitude
Longitude used in an address, which is required for tax calculation.
postalCode
Postal code used in an address, which is required for tax calculation.
1518
CommerceTax NamespaceTransaction Management

===== PAGE 1533 =====

state
State used in an address, which is required for tax calculation.
stateCode
State code used in an address, which is required for tax calculation.
street
Street used in an address, which is required for tax calculation.
city
City used in an address, which is required for tax calculation.
Signature
global String city {get; set;}
Property Value
Type: String
country
Country used in an address, which is required for tax calculation.
Signature
global String country {get; set;}
Property Value
Type: String
countryCode
Country code used in an address, which is required for tax calculation.
Signature
global String countryCode {get; set;}
Property Value
Type: String
latitude
Latitude used in an address, which is required for tax calculation.
Signature
global Double latitude {get; set;}
1519
CommerceTax NamespaceTransaction Management

===== PAGE 1534 =====

Property Value
Type: Double
locationCode
Location code used in an address, which is required for tax calculation.
Signature
global String locationCode {get; set;}
Property Value
Type: String
longitude
Longitude used in an address, which is required for tax calculation.
Signature
global Double longitude {get; set;}
Property Value
Type: Double
postalCode
Postal code used in an address, which is required for tax calculation.
Signature
global String postalCode {get; set;}
Property Value
Type: String
state
State used in an address, which is required for tax calculation.
Signature
global String state {get; set;}
Property Value
Type: String
1520
CommerceTax NamespaceTransaction Management

===== PAGE 1535 =====

stateCode
State code used in an address, which is required for tax calculation.
Signature
global String stateCode {get; set;}
Property Value
Type: String
street
Street used in an address, which is required for tax calculation.
Signature
global String street {get; set;}
Property Value
Type: String
TaxAddressRequest Methods
Learn more about the available methods with the TaxAddressRequest  class.
The TaxAddressRequest  class includes these methods.
equals(obj)
Maintains the integrity of lists of type TaxAddressRequest by determining the equality of external objects in a list. This method is
dynamic and based on the equals()  method in Java.
hashCode()
Maintains the integrity of lists of type TaxAddressRequest  by determining the uniqueness of the external object in a list.
toString()
Converts a date to a string.
equals(obj)
Maintains the integrity of lists of type TaxAddressRequest by determining the equality of external objects in a list. This method is dynamic
and based on the equals()  method in Java.
Signature
global Boolean equals(Object obj)
1521
CommerceTax NamespaceTransaction Management

===== PAGE 1536 =====

Parameters
obj
Type: Object
External object whose key is to be validated.
Return Value
Type: Boolean
hashCode()
Maintains the integrity of lists of type TaxAddressRequest  by determining the uniqueness of the external object in a list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a date to a string.
Signature
global String toString()
Return Value
Type: String
TaxApiException Class
Contains details about any exceptions during the tax calculation process. Extends the ApexBaseException class.
Namespace
CommerceTax
TaxApiException Constructors
Learn more about the available constructors with the TaxApiException  class.
TaxApiException Constructors
Learn more about the available constructors with the TaxApiException  class.
The TaxApiException  class includes these constructors.
1522
CommerceTax NamespaceTransaction Management

===== PAGE 1537 =====

TaxApiException(var1, var2)
Initializes the TaxApiException class using an Exception  and a string to provide more details about the exception. This
constructor is intended for test usage and throws an exception if used outside of the Apex test context.
TaxApiException(var1)
Initializes the TaxApiException class using an Exception. This constructor is intended for test usage and throws an
exception if used outside of the Apex test context.
TaxApiException()
Initializes the TaxApiException class without any initialized parameters. This constructor is intended for test usage and throws
an exception if used outside of the Apex test context.
TaxApiException(var1, var2)
Initializes the TaxApiException class using an Exception  and a string to provide more details about the exception. This
constructor is intended for test usage and throws an exception if used outside of the Apex test context.
Signature
global TaxApiException(String var1, Exception var2)
Parameters
var1
Type: String
Text that provides more information about the returned exception.
var2
Type: Exception
An exception denotes an error that disrupts the normal flow of code execution. You can use Apex built-in exceptions or create
custom exceptions. All exceptions have common methods.
TaxApiException(var1)
Initializes the TaxApiException class using an Exception. This constructor is intended for test usage and throws an exception
if used outside of the Apex test context.
Signature
global TaxApiException(Exception var1)
Parameters
var1
Type: Exception
An exception denotes an error that disrupts the normal flow of code execution. You can use Apex built-in exceptions or create
custom exceptions. All exceptions have common methods.
1523
CommerceTax NamespaceTransaction Management

===== PAGE 1538 =====

TaxApiException()
Initializes the TaxApiException class without any initialized parameters. This constructor is intended for test usage and throws an
exception if used outside of the Apex test context.
Signature
global TaxApiException()
TaxCustomerDetailsRequest Class
Contains customer details used in tax calculation.
Namespace
CommerceTax
TaxCustomerDetailsRequest Constructors
Learn more about the available constructors with the TaxCustomerDetailsRequest  class.
TaxCustomerDetailsRequest Properties
Learn more about the available properties with the TaxCustomerDetailsRequest  class.
TaxCustomerDetailsRequest Methods
Learn more about the available methods with the TaxCustomerDetailsRequest  class.
TaxCustomerDetailsRequest Constructors
Learn more about the available constructors with the TaxCustomerDetailsRequest  class.
The TaxCustomerDetailsRequest  class includes these constructors.
TaxCustomerDetailsRequest(accountId, code, exemptionNo, exemptionReason)
Initializes the TaxCustomerDetailsRequest  object. This constructor is intended for test usage and throws an exception if
used outside of the Apex test context.
TaxCustomerDetailsRequest(accountId, code, exemptionNo, exemptionReason)
Initializes the TaxCustomerDetailsRequest  object. This constructor is intended for test usage and throws an exception if used
outside of the Apex test context.
Signature
global TaxCustomerDetailsRequest(String accountId, String code, String exemptionNo,
String exemptionReason)
Parameters
accountId
Type: String
The customer account ID for the line items sent for tax calculation.
1524
CommerceTax NamespaceTransaction Management

===== PAGE 1539 =====

code
Type: String
The tax code used during tax calculation.
exemptionNo
Type: String
The exemption number applied to any tax exempt line items.
exemptionReason
Type: String
The reason that certain line items are tax exempt.
TaxCustomerDetailsRequest Properties
Learn more about the available properties with the TaxCustomerDetailsRequest  class.
The TaxCustomerDetailsRequest  class includes these properties.
accountId
Customer account that contains the line items sent for tax calculation.
code
Tax code used during tax calculation.
exemptionNo
Number used to qualify a line item for tax exemption.
exemptionReason
Reason why a line item qualifies for tax exemption.
taxCertificateId
ID of a tax certificate used for tax calculation.
accountId
Customer account that contains the line items sent for tax calculation.
Signature
global String accountId {get; set;}
Property Value
Type: String
code
Tax code used during tax calculation.
Signature
global String code {get; set;}
1525
CommerceTax NamespaceTransaction Management

===== PAGE 1540 =====

Property Value
Type: String
exemptionNo
Number used to qualify a line item for tax exemption.
Signature
global String exemptionNo {get; set;}
Property Value
Type: String
exemptionReason
Reason why a line item qualifies for tax exemption.
Signature
global String exemptionReason {get; set;}
Property Value
Type: String
taxCertificateId
ID of a tax certificate used for tax calculation.
Signature
global String taxCertificateId {get; set;}
Property Value
Type: String
TaxCustomerDetailsRequest Methods
Learn more about the available methods with the TaxCustomerDetailsRequest  class.
The TaxCustomerDetailsRequest  class includes these methods.
equals(obj)
Maintains the integrity of lists of type TaxCustomerDetailsRequest  by determining the equality of external objects in a
list. This method is dynamic and based on the equals() method in Java.
1526
CommerceTax NamespaceTransaction Management

===== PAGE 1541 =====

hashCode()
Maintains the integrity of lists of type TaxCustomerDetailsRequest  by determining the uniqueness of the external objects
in a list.
toString()
Converts a value to a string.
equals(obj)
Maintains the integrity of lists of type TaxCustomerDetailsRequest  by determining the equality of external objects in a list.
This method is dynamic and based on the equals() method in Java.
Signature
global Boolean equals(Object obj)
Parameters
obj
Type: Object
External object whose key is to be validated.
Return Value
Type: Boolean
hashCode()
Maintains the integrity of lists of type TaxCustomerDetailsRequest  by determining the uniqueness of the external objects in
a list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a value to a string.
Signature
global String toString()
Return Value
Type: String
1527
CommerceTax NamespaceTransaction Management

===== PAGE 1542 =====

TaxDetailsResponse Class
Stores details of the tax values that an external tax engine calculates in response to a tax calculation request.
Namespace
CommerceTax
Usage
If your tax calculation request contains multiple line items, we recommend building your adapter using a list of TaxDetailsResponse
instances. Each instance represents the tax details calculated for a given line item.
Example
List<commercetax.TaxDetailsResponse> taxDetailsResponses = new
List<commercetax.TaxDetailsResponse>();
for(integer i =0;i<1;i++){
Integer rate = 1;
Double taxableAmount = lineItem.amount;
commercetax.TaxDetailsResponse taxDetailsResponse = new
commercetax.TaxDetailsResponse();
taxDetailsResponse.setRate(Double.valueOf(rate));
taxDetailsResponse.setTaxableAmount(taxableAmount);
Double tax = taxableAmount*rate;
totalLineTax+=tax;
taxDetailsResponse.setTax(taxableAmount*rate);
taxDetailsResponse.setExemptAmount(0);
taxDetailsResponse.setExemptReason('exemptReason');
taxDetailsResponse.setTaxRegionId('taxRegionId');
taxDetailsResponse.setTaxId(String.valueOf(getRandomInteger(0,2323233)));
taxDetailsResponse.setSerCode('serCode');
taxDetailsResponse.setTaxAuthorityTypeId('taxAuthorityTypeId');
if(request.DocumentCode == 'SetsNullForResponseWithoutException'){
taxDetailsResponse.setImposition(null);
}else{
commercetax.ImpositionResponse imposition = new
commercetax.ImpositionResponse();
imposition.setSubType('subtype');
imposition.setType('type');
taxDetailsResponse.setImposition(imposition);
}
if(request.DocumentCode == 'SetsNullForResponseWithoutException'){
taxDetailsResponse.setJurisdiction(null);
}else{
commercetax.JurisdictionResponse jurisdiction = new
commercetax.JurisdictionResponse();
jurisdiction.setCountry('country');
jurisdiction.setRegion('region');
jurisdiction.setName('name');
jurisdiction.setStateAssignedNumber('stateAssignedNo');
1528
CommerceTax NamespaceTransaction Management

===== PAGE 1543 =====

jurisdiction.setId('id');
jurisdiction.setLevel('level');
taxDetailsResponse.setJurisdiction(jurisdiction);
}
taxDetailsResponses.add(taxDetailsResponse);
}
lineItemResponse.setTaxes(taxDetailsResponses);
totalTax +=totalLineTax;
totalAmount+=lineItem.amount;
TaxDetailsResponse Methods
Learn more about the available methods with the TaxDetailsResponse  class.
TaxDetailsResponse Methods
Learn more about the available methods with the TaxDetailsResponse  class.
The TaxDetailsResponse  class includes these methods.
setCustomTaxAttributes(customTaxAttributes)
Uses an instance of CustomTaxAttributesResponse  class to include additional attributes in the tax response at the tax
line item level.
setExemptAmount(exemptAmount)
Sets the ExemptAmount field of the TaxDetailsResponse  class.
setExemptReason(reason)
Sets the ExemptReason field of the TaxDetailsResponse  class.
setImposition(imposition)
Sets the Imposition field of the TaxDetailsResponse  class using an instance of the ImpositionResponse  class.
setJurisdiction(jurisdiction)
Sets the Jurisdiction field of the TaxDetailsResponse  using an instance of the JurisdictionResponse  class.
setRate(rate)
Sets the Rate field of the TaxDetailsResponse  class.
setSerCode(serCode)
Sets the Service Code field of the TaxDetailsResponse  class.
setTax(tax)
Sets the Tax field of the TaxDetailsResponse  class.
setTaxAuthorityTypeId(taxAuthorityTypeId)
Sets the TaxAuthorityTypeId field of the TaxDetailsResponse  class.
setTaxId(taxId)
Sets the TaxId field of the TaxDetailsResponse  class.
setTaxRegionId(taxRegionId)
Sets the TaxRegionId field on the TaxDetailsResponse  class.
1529
CommerceTax NamespaceTransaction Management

===== PAGE 1544 =====

setTaxRuleDetails(taxRuleDetails)
Sets the TaxRuleDetails field of the TaxDetailsResponse  class.
setTaxableAmount(taxableAmount)
Sets the TaxableAmount field of the TaxDetailsResponse class.
setCustomTaxAttributes(customTaxAttributes)
Uses an instance of CustomTaxAttributesResponse  class to include additional attributes in the tax response at the tax line
item level.
Signature
global void setCustomTaxAttributes(commercetax.CustomTaxAttributesResponse
customTaxAttributes)
Parameters
customTaxAttributes
Type: CustomTaxAttributesResponse
Additional data or custom attributes to include in the tax response.
Return Value
Type: void
setExemptAmount(exemptAmount)
Sets the ExemptAmount field of the TaxDetailsResponse  class.
Signature
global void setExemptAmount(Double exemptAmount)
Parameters
exemptAmount
Type: Double
Amount of tax on a line item that is exempt from tax calculation.
Return Value
Type: void
setExemptReason(reason)
Sets the ExemptReason field of the TaxDetailsResponse  class.
Signature
global void setExemptReason(String reason)
1530
CommerceTax NamespaceTransaction Management

===== PAGE 1545 =====

Parameters
reason
Type: String
Optional user-defined information on why a tax exemption applies to a line item.
Return Value
Type: void
setImposition(imposition)
Sets the Imposition field of the TaxDetailsResponse  class using an instance of the ImpositionResponse  class.
Signature
global void setImposition(commercetax.ImpositionResponse imposition)
Parameters
imposition
Type: ImpositionResponse
Contains information about why tax was imposed on a line item.
Return Value
Type: void
setJurisdiction(jurisdiction)
Sets the Jurisdiction field of the TaxDetailsResponse  using an instance of the JurisdictionResponse  class.
Signature
global void setJurisdiction(commercetax.JurisdictionResponse jurisdiction)
Parameters
jurisdiction
Type: JurisdictionResponse
Contains address information about the tax jurisdiction used in the tax calculation process.
Return Value
Type: void
setRate(rate)
Sets the Rate field of the TaxDetailsResponse  class.
1531
CommerceTax NamespaceTransaction Management

===== PAGE 1546 =====

Signature
global void setRate(Double rate)
Parameters
rate
Type: Double
Tax used during tax calculation. This value is often a decimal amount, such as 0.1 or 0.06, based on the applied tax percentage.
Return Value
Type: void
setSerCode(serCode)
Sets the Service Code field of the TaxDetailsResponse  class.
Signature
global void setSerCode(String serCode)
Parameters
serCode
Type: String
Service code used in tax calculation.
Return Value
Type: void
setTax(tax)
Sets the Tax field of the TaxDetailsResponse  class.
Signature
global void setTax(Double tax)
Parameters
tax
Type: Double
Amount of tax for a line item.
Return Value
Type: void
1532
CommerceTax NamespaceTransaction Management

===== PAGE 1547 =====

setTaxAuthorityTypeId(taxAuthorityTypeId)
Sets the TaxAuthorityTypeId field of the TaxDetailsResponse  class.
Signature
global void setTaxAuthorityTypeId(String taxAuthorityTypeId)
Parameters
taxAuthorityTypeId
Type: String
ID of the organization that oversees tax collection.
Return Value
Type: void
setTaxId(taxId)
Sets the TaxId field of the TaxDetailsResponse  class.
Signature
global void setTaxId(String taxId)
Parameters
taxId
Type: String
ID value used to determine the tax for an individual or business.
Return Value
Type: void
setTaxRegionId(taxRegionId)
Sets the TaxRegionId field on the TaxDetailsResponse  class.
Signature
global void setTaxRegionId(String taxRegionId)
Parameters
taxRegionId
Type: String
ID of the tax region used in tax calculation. A tax region represents a geographical area where tax is applied.
1533
CommerceTax NamespaceTransaction Management

===== PAGE 1548 =====

Return Value
Type: void
setTaxRuleDetails(taxRuleDetails)
Sets the TaxRuleDetails field of the TaxDetailsResponse  class.
Signature
global void setTaxRuleDetails(commercetax.RuleDetailsResponse taxRuleDetails)
Parameters
taxRuleDetails
Type: RuleDetailsResponse
Information about the Salesforce tax rules used during tax calculation.
Return Value
Type: void
setTaxableAmount(taxableAmount)
Sets the TaxableAmount field of the TaxDetailsResponse class.
Signature
global void setTaxableAmount(Double taxableAmount)
Parameters
taxableAmount
Type: Double
Amount that can be taxed on a line item.
Return Value
Type: void
TaxEngineAdapter Interface
Retrieves information from the tax engine and evaluates the information to define tax details.
Namespace
CommerceTax
TaxEngineAdapter Methods
Learn more about the available methods with the TaxEngineAdapter  class.
1534
CommerceTax NamespaceTransaction Management

===== PAGE 1549 =====

TaxEngineAdapter Example Implementation
Refer to the example implementation of the TaxEngineAdapter interface to accept information from a tax engine and evaluate
the information to define tax details.
Tax Mappings for Quotes and Orders
You can extend and customize the tax interface for quotes and orders by using custom metadata types and tax mappings. These
customizations help you with unique business requirements such as the inclusion of specific data for accurate calculations and
audits.
TaxEngineAdapter Methods
Learn more about the available methods with the TaxEngineAdapter  class.
The TaxEngineAdapter  class includes these methods.
processRequest(requestType)
The processRequest  method takes an instance of TaxEngineContext  class and returns a response with the calculated
tax details through the TaxDetailsResponse  class or an error response through the ErrorResponse  class.
processRequest(requestType)
The processRequest  method takes an instance of TaxEngineContext  class and returns a response with the calculated tax
details through the TaxDetailsResponse  class or an error response through the ErrorResponse  class.
Signature
global commercetax.TaxEngineResponse processRequest(commercetax.TaxEngineContext var1)
Parameters
var1
Type: TaxEngineContext
Wrapper class that stores information about the type of a tax calculation request.
Return Value
Type: TaxEngineResponse
Generic interface representing a response from a tax engine.
TaxEngineAdapter Example Implementation
Refer to the example implementation of the TaxEngineAdapter  interface to accept information from a tax engine and evaluate
the information to define tax details.
Namespace
commercetax
1535
CommerceTax NamespaceTransaction Management

===== PAGE 1550 =====

Usage
The TaxEngineAdapter  interface accepts information from the tax engine through the TaxEngineContext  class. The
interface evaluates the information to define tax in the response with details, such as tax amount and addresses. The response is used
to update and create entities in the Salesforce org.
Use these steps to build a sample tax adapter implementation. Each tax adapter implementation varies based on your implementation
requirements. Customize this example to suit your business requirements.
Example:
• The custom adapter class implements the TaxEngineAdapter  interface. The processRequest  method takes an
instance of TaxEngineContext  class and returns a response with the calculated tax details through the
TaxDetailsResponse  class or an error response through the ErrorResponse  class.
global virtual class AvalaraAdapter implements commercetax.TaxEngineAdapter {
global commercetax.TaxEngineResponse processRequest(commercetax.TaxEngineContext
taxEngineContext) {
commercetax.RequestType requestType = taxEngineContext.getRequestType();
if(requestType == commercetax.RequestType.CalculateTax){
return CalculateTaxService.getTax(taxEngineContext);
}
else
return null;
}
}
• This example shows the CalculateTaxService class.
global class CalculateTaxService {
// ============================================================================
// CONSTANT
// ============================================================================
private static final String AVALARA_ENDPOINT_URL_SANDBOX =
'https://sandbox-rest.avatax.com/api/v2';
// Avalara Endpoint URL Production
private static final String AVALARA_ENDPOINT_URL_PRODUCTION =
'https://rest.avatax.com/api/v2';
private static final String TEST_REQUEST_BODY = '{ "id": -1, "code": "00000131",
"companyId": -1, "date": "2017-02-03T00:00:00", "taxDate": "2017-02-03T00:00:00",
"status": "Temporary", "type": "SalesOrder", "reconciled": false, "totalAmount":
4000, "totalExempt": 0, "totalTax": 290, "totalTaxable": 4000,
"totalTaxCalculated": 290, "adjustmentReason": "NotAdjusted", "locked": false,
"version": 1, "modifiedDate": "2017-02-03T12:18:18.7347388Z", "modifiedUserId":
53894, "lines": [ { "id": -1, "transactionId": -1, "lineNumber":
"80241000000jNDCAA2", "discountAmount": 0, "exemptAmount": 0,
"exemptCertId": 0, "isItemTaxable": true, "lineAmount": 1000,
"reportingDate": "2017-02-03T00:00:00", "tax": 72.5, "taxableAmount":
1000, "taxCalculated": 72.5, "taxCode": "P0000000", "taxDate":
"2017-02-03T00:00:00", "taxIncluded": false, "details": [ {
"id": -1, "transactionLineId": -1, "transactionId": -1,
"country": "US", "region": "CA", "exemptAmount": 0,
"jurisCode": "06", "jurisName": "CALIFORNIA", "stateAssignedNo":
1536
CommerceTax NamespaceTransaction Management

===== PAGE 1551 =====

"", "jurisType": "STA", "nonTaxableAmount": 0, "rate":
0.06, "tax": 60, "taxableAmount": 1000, "taxType":
"Sales", "taxName": "CA STATE TAX", "taxAuthorityTypeId": 45,
"taxCalculated": 60, "rateType": "General" }, {
"id": -1, "transactionLineId": -1, "transactionId": -1,
"country": "US", "region": "CA", "exemptAmount": 0,
"jurisCode": "075", "jurisName": "SAN FRANCISCO",
"stateAssignedNo": "", "jurisType": "CTY", "nonTaxableAmount": 0,
"rate": 0.0025, "tax": 2.5, "taxableAmount": 1000,
"taxType": "Sales", "taxName": "CA COUNTY TAX",
"taxAuthorityTypeId": 45, "taxCalculated": 2.5, "rateType":
"General" }, { "id": -1, "transactionLineId": -1,
"transactionId": -1, "country": "US", "region": "CA",
"exemptAmount": 0, "jurisCode": "EMTV0", "jurisName": "SAN
FRANCISCO CO LOCAL TAX SL", "stateAssignedNo": "38", "jurisType":
"STJ", "nonTaxableAmount": 0, "rate": 0.01, "tax": 10,
"taxableAmount": 1000, "taxType": "Sales", "taxName":
"CA SPECIAL TAX", "taxAuthorityTypeId": 45, "taxCalculated": 10,
"rateType": "General" } ] } ]}';
private static String getTestResponseString(){
List<String> jsonResponse = new List<String> {
'"id": 0',
'"code": "testDocCode1231245984"',
'"companyId": 468039',
'"date": "2020-07-15"',
'"paymentDate": "2020-07-15"',
'"status": "Temporary"',
'"type": "SalesOrder"',
'"customerVendorCode": "testDocCode1234"',
'"customerCode": "testDocCode1234"',
'"reconciled": false',
'"totalAmount": 232',
'"totalExempt": 0',
'"totalDiscount": 0',
'"totalTax": 23.43',
'"totalTaxable": 232',
'"totalTaxCalculated": 23.43',
'"adjustmentReason": "NotAdjusted"',
'"locked": false',
'"version": 1',
'"exchangeRateEffectiveDate": "2020-07-15"',
'"exchangeRate": 1',
'"modifiedDate": "2020-08-13T11:19:20.4836636Z"',
'"modifiedUserId": 53894',
'"taxDate": "2020-07-15T00:00:00"',
'"lines": [{"id": 0,"transactionId":
0,"lineNumber": "1","discountAmount": 0,"exemptAmount": 0,"exemptCertId":
0,"isItemTaxable": true,"itemCode": "","lineAmount": 232,"quantity":
1,"reportingDate": "2020-07-15","tax": 23.43,"taxableAmount": 232,"taxCalculated":
23.43,"taxCode": "P0000000","taxCodeId": 8087,"taxDate":
"2020-07-15","taxOverrideType": "None","taxOverrideAmount": 0,"taxIncluded":
1537
CommerceTax NamespaceTransaction Management

===== PAGE 1552 =====

false,"details": [{"id": 0,"transactionLineId": 0,"transactionId": 0,"country":
"US","region": "WA","exemptAmount": 0,"jurisCode": "53","jurisName":
"WASHINGTON","stateAssignedNo": "","jurisType": "STA","jurisdictionType":
"State","nonTaxableAmount": 0,"rate": 0.065,"tax": 15.08,"taxableAmount":
232,"taxType": "Sales","taxSubTypeId": "S","taxName": "WA STATE
TAX","taxAuthorityTypeId": 45,"taxCalculated": 15.08,"rateType":
"General","rateTypeCode": "G","unitOfBasis": "PerCurrencyUnit","isNonPassThru":
false,"isFee": false},{"id": 0,"transactionLineId": 0,"transactionId": 0,"country":
"US","region": "WA","exemptAmount": 0,"jurisCode": "033","jurisName":
"KING","stateAssignedNo": "1700","jurisType": "CTY","jurisdictionType":
"County","nonTaxableAmount": 0,"rate": 0,"tax": 0,"taxableAmount": 232,"taxType":
"Sales","taxSubTypeId": "S","taxName": "WA COUNTY TAX","taxAuthorityTypeId":
45,"taxCalculated": 0,"rateType": "General","rateTypeCode": "G","unitOfBasis":
"PerCurrencyUnit","isNonPassThru": false,"isFee": false}],"nonPassthroughDetails":
[],"hsCode": "","costInsuranceFreight": 0,"vatCode": "","vatNumberTypeId": 0}]',
'"addresses": [{"id": 0,"transactionId":
0,"boundaryLevel": "Address","line1": "255 S. King Street","line2": "","line3":
"","city": "Seattle","region": "WA","postalCode": "98104","country":
"US","taxRegionId": 2109700,"latitude": "47.59821","longitude": "-122.33108"}]',
'"summary": [{"country": "US","region":
"WA","jurisType": "State","jurisCode": "53","jurisName":
"WASHINGTON","taxAuthorityType": 45,"stateAssignedNo": "","taxType":
"Sales","taxSubType": "S","taxName": "WA STATE TAX","rateType": "General","taxable":
232,"rate": 0.065,"tax": 15.08,"taxCalculated": 15.08,"nonTaxable": 0,"exemption":
0},{"country": "US","region": "WA","jurisType": "County","jurisCode":
"033","jurisName": "KING","taxAuthorityType":45,"stateAssignedNo": "1700","taxType":
"Sales","taxSubType":"S","taxName": "WA COUNTY TAX","rateType": "General","taxable":
232,"rate": 0,"tax": 0,"taxCalculated": 0,"nonTaxable": 0,"exemption": 0}]'
};
return '{' + String.join(jsonResponse, ',') + '}';
}
public static commercetax.TaxEngineResponse getTax(commercetax.TaxEngineContext
taxEngineContext)
{
commercetax.CalculateTaxRequest request =
(commercetax.CalculateTaxRequest)taxEngineContext.getRequest();
commercetax.calculatetaxtype requestType = request.taxtype;
string referenceEntity = request.ReferenceEntityId;
try{
List<commercetax.TaxLineItemRequest> listOfLines = request.lineItems;
if(!listOfLines.isEmpty()){
HttpService sendHttpRequest = new HttpService();
sendHttpRequest.addHeader('Content-type', 'application/json');
String requestBody =
AvalaraJSONBuilder.getInstance().frameJsonForGetTaxOrderItem(request);
sendHttpRequest.post('/transactions/create',requestBody);
//system.debug('Request '+requestBody);
String responseString = '';
if(Test.isRunningTest()){
responseString = getTestResponseString();
} else{
responseString = sendHttpRequest.getResponse().getBody();
}
1538
CommerceTax NamespaceTransaction Management

===== PAGE 1553 =====

//system.debug(sendHttpRequest.getResponse());
//system.debug('response'+responseString);
//responseString = TEST_REQUEST_BODY;
system.debug('Heap size used ' +Limits.getHeapSize());
if(!responseString.contains('error'))
{
commercetax.CalculateTaxResponse response = new
commercetax.CalculateTaxResponse();
JsonSuccessParser jsonSuccessParserClass =
JsonSuccessParser.parse(responseString);
response.setTaxTransactionType(request.taxTransactionType);
response.setDocumentCode(jsonSuccessParserClass.code);
response.setReferenceDocumentCode(jsonSuccessParserClass.referenceCode);
if(jsonSuccessParserClass.status == 'Temporary') {
response.setStatus(commercetax.TaxTransactionStatus.Uncommitted);
}
if(jsonSuccessParserClass.status == 'Committed') {
response.setStatus(commercetax.TaxTransactionStatus.Committed);
}
response.setTaxType(requestType);
commercetax.AmountDetailsResponse headerAmountResponse = new
commercetax.AmountDetailsResponse();
headerAmountResponse.setTotalAmountWithTax(jsonSuccessParserClass.totalAmount +
jsonSuccessParserClass.totaltax);
headerAmountResponse.setExemptAmount(jsonSuccessParserClass.totalExempt);
headerAmountResponse.setTotalAmount(jsonSuccessParserClass.totalAmount);
headerAmountResponse.setTaxAmount(jsonSuccessParserClass.totalTax);
response.setAmountDetails(headerAmountResponse);
response.setStatusDescription(jsonSuccessParserClass.adjustmentReason);
response.setEffectiveDate(date.valueof(jsonSuccessParserClass.taxDate));
response.setTransactionDate(date.valueof(jsonSuccessParserClass.transactionDate));
response.setReferenceEntityId(referenceEntity);
response.setTaxTransactionId(jsonSuccessParserClass.id);
response.setCurrencyIsoCode(request.currencyIsoCode);
List<commercetax.LineItemResponse> lineItemResponses = new
List<commercetax.LineItemResponse>();
for(JsonSuccessParser.Lines linesToProcess:
jsonSuccessParserClass.lines)
{
commercetax.LineItemResponse lineItemResponse = new
commercetax.LineItemResponse();
Double rateCalculated = 0.0;
List<commercetax.TaxDetailsResponse> taxDetailsResponses =
1539
CommerceTax NamespaceTransaction Management

===== PAGE 1554 =====

new List<commercetax.TaxDetailsResponse>();
for(JsonSuccessParser.details linesDetails :
linesToProcess.details)
{
commercetax.TaxDetailsResponse taxDetailsResponse = new
commercetax.TaxDetailsResponse();
if(linesDetails.exemptAmount != 0){
taxDetailsResponse.setExemptAmount(linesDetails.exemptAmount);
taxDetailsResponse.setExemptReason('Some reason we
dont know');
}
commercetax.ImpositionResponse imposition = new
commercetax.ImpositionResponse();
imposition.setSubType(linesDetails.taxName);
imposition.setType(linesDetails.ratetype);
imposition.setSubType(linesDetails.taxName);
taxDetailsResponse.setImposition(imposition);
commercetax.JurisdictionResponse jurisdiction = new
commercetax.JurisdictionResponse();
jurisdiction.setCountry(linesDetails.country);
jurisdiction.setRegion(linesDetails.region);
jurisdiction.setName(linesDetails.jurisName);
jurisdiction.setStateAssignedNumber(linesDetails.stateAssignedNo);
jurisdiction.setId(linesDetails.jurisCode);
jurisdiction.setLevel(linesDetails.jurisType);
taxDetailsResponse.setJurisdiction(jurisdiction);
rateCalculated += linesDetails.rate;
taxDetailsResponse.setRate(rateCalculated);
taxDetailsResponse.setTax(linesDetails.taxCalculated);
taxDetailsResponse.setTaxableAmount(linesDetails.taxableAmount);
taxDetailsResponse.setTaxAuthorityTypeId(String.valueOf(linesDetails.taxAuthorityTypeId));
taxDetailsResponse.setTaxId(linesDetails.id);
taxDetailsResponse.setTaxRegionId(linesDetails.region);
taxDetailsResponses.add(taxDetailsResponse);
}
lineItemResponse.setTaxes(taxDetailsResponses);
lineItemResponse.setEffectiveDate(date.valueof(linesToProcess.taxDate));
lineItemResponse.setIsTaxable(true);
commercetax.AmountDetailsResponse amountResponse =
new commercetax.AmountDetailsResponse();
amountResponse.setTaxAmount(linesToProcess.taxCalculated);
amountResponse.setTotalAmount(linesToProcess.lineAmount);
1540
CommerceTax NamespaceTransaction Management

===== PAGE 1555 =====

amountResponse.setTotalAmountWithTax(linesToProcess.lineAmount+linesToProcess.taxCalculated);
amountResponse.setExemptAmount(linesToProcess.exemptAmount);
lineItemResponse.setAmountDetails(amountResponse);
lineItemResponse.setIsTaxable(linesToProcess.isItemTaxable);
lineItemResponse.setProductCode(linesToProcess.itemCode);
lineItemResponse.setTaxCode(linesToProcess.taxCode);
lineItemResponse.setLineNumber(linesToProcess.lineNumber);
lineItemResponse.setQuantity(linesToProcess.quantity);
lineItemResponses.add(lineItemResponse);
}
response.setLineItems(lineItemResponses);
return response;
}
else
{
JsonErrorParser jsonErrorParserClass =
JsonErrorParser.parse(responseString);
String message = null;
if(String.isNotBlank(jsonErrorParserClass.error.message))
{
message=jsonErrorParserClass.error.message;
}else{
String errorMessage = '';
for(JsonErrorParser.cls_details messageString :
jsonErrorParserClass.error.details)
{
if(String.isNotBlank(messageString.message) )
{
errorMessage = messageString.message;
}
}
message = errorMessage;
}
return new
commercetax.ErrorResponse(commercetax.resultcode.TaxEngineError, '501', message);
}
}else return null;
}
catch (Exception e)
{
throw e;
}
}
}
1541
CommerceTax NamespaceTransaction Management

===== PAGE 1556 =====

• In the HttpService  class, replace the test  value in the endpoint variable with the name of the
TaxTypedNamedCredential record. This class contains the credentials that are required to access your Avalara account
through Salesforce.
public with sharing class HttpService
{
// Attribute to implement singleton pattern for Order Product Service class
private static HttpService httpServiceInstance;
// VARIABLES
private HttpResponse httpResponse;
private Map<String,String> mapOfHeaderParameter = new Map<String,String>();
private enum Method {GET, POST}
/**
* @name getInstance
* @description get an Instance of Service class
* @params NA
* @return Http Service Class Instance
*/
public static HttpService getInstance()
{
if (NULL == httpServiceInstance)
{
httpServiceInstance = new HttpService();
}
return httpServiceInstance;
}
/**
* @name get
* @description Get Method to get a HTTP request
*/
public void get(String endPoint)
{
send(newRequest(Method.GET, endPoint));
}
/**
* @name post
* @description Post Method to Post a HTTP request
*/
public void post(String path, String requestBody)
{
String endPoint = 'callout:commerce.tax.TaxTypedNamedCredential:test'+path;
send(newRequest(Method.POST, endPoint, requestBody));
}
/**
* @name addHeader
* @description addHeader Methods to add all the defualt Header's required fo
rthe request
1542
CommerceTax NamespaceTransaction Management

===== PAGE 1557 =====

*/
public void addHeader(String name, String value)
{
mapOfHeaderParameter.put(name, value);
}
/**
* @name setHeader
* @description setHeader Methods to set setHeader for the request
*/
private void setHeader(HttpRequest request)
{
for(String headerValue : mapOfHeaderParameter.keySet())
{
request.setHeader(headerValue, mapOfHeaderParameter.get(headerValue));
}
}
/**
* @name newRequest
* @description newRequest Methods to make a new request
*/
private HttpRequest newRequest(Method method, String endPoint)
{
return newRequest(method, endPoint, NULL);
}
/**
* @name newRequest
* @description newRequest Methods to make a new request
*/
private HttpRequest newRequest(Method method, String endPoint, String requestBody)
{
HttpRequest request = new HttpRequest();
request.setMethod(Method.name());
setHeader(request);
request.setEndpoint(endPoint);
if (String.isNotBlank(requestBody))
{
request.setBody(requestBody);
}
request.setTimeout(120000);
return request;
}
/**
* @name send
* @description send Methods to send a request
*/
private void send(HttpRequest request)
{
try
{
Http http = new Http();
1543
CommerceTax NamespaceTransaction Management

===== PAGE 1558 =====

httpResponse = http.send(request);
}
catch(System.CalloutException e)
{
system.debug('callout exception happened' + e.getMessage());
}
catch(Exception e)
{
system.debug('callout did not happen' + e.getMessage());
}
}
/**
* @name getResponse
* @description getResponse Method to get the Response
*/
public HttpResponse getResponse()
{
return httpResponse;
}
/**
* @name getResponseToString
* @description getResponse Method to get the Responses
*/
public String getResponseToString()
{
return getResponse().toString();
}
}
• Parse the JsonSuccessParser  response object by using the AvalaraJSONBuilder class to build the response
for your adapter.
This example shows the JsonSuccessParser class.
global with sharing class JsonSuccessParser
{
public static void consumeObject(JSONParser parser)
{
Integer depth = 0;
do {
JSONToken curr = parser.getCurrentToken();
if (curr == JSONToken.START_OBJECT ||
curr == JSONToken.START_ARRAY) {
depth++;
} else if (curr == JSONToken.END_OBJECT ||
curr == JSONToken.END_ARRAY) {
depth--;
}
} while (depth > 0 && parser.nextToken() != null);
}
public class Addresses {
public String id {get;set;}
1544
CommerceTax NamespaceTransaction Management

===== PAGE 1559 =====

public String transactionId {get;set;}
public String boundaryLevel {get;set;}
public String line1 {get;set;}
public String city {get;set;}
public String region {get;set;}
public String postalCode {get;set;}
public String country {get;set;}
public Integer taxRegionId {get;set;}
public Addresses(JSONParser parser) {
while (parser.nextToken() != JSONToken.END_OBJECT) {
if (parser.getCurrentToken() == JSONToken.FIELD_NAME) {
String text = parser.getText();
if (parser.nextToken() != JSONToken.VALUE_NULL) {
if (text == 'id') {
id = parser.getText();
} else if (text == 'transactionId') {
transactionId = parser.getText();
} else if (text == 'boundaryLevel') {
boundaryLevel = parser.getText();
} else if (text == 'line1') {
line1 = parser.getText();
} else if (text == 'city') {
city = parser.getText();
} else if (text == 'region') {
region = parser.getText();
} else if (text == 'postalCode') {
postalCode = parser.getText();
} else if (text == 'country') {
country = parser.getText();
} else if (text == 'taxRegionId') {
taxRegionId = parser.getIntegerValue();
} else {
consumeObject(parser);
}
}
}
}
}
}
public class Details {
public String id {get;set;}
public String transactionLineId {get;set;}
public String transactionId {get;set;}
public String country {get;set;}
public String region {get;set;}
public Integer exemptAmount {get;set;}
public String jurisCode {get;set;}
public String jurisName {get;set;}
public String stateAssignedNo {get;set;}
public String jurisType {get;set;}
public Integer nonTaxableAmount {get;set;}
public Double rate {get;set;}
1545
CommerceTax NamespaceTransaction Management

===== PAGE 1560 =====

public Double tax {get;set;}
public Integer taxableAmount {get;set;}
public String taxType {get;set;}
public String taxName {get;set;}
public Integer taxAuthorityTypeId {get;set;}
public Double taxCalculated {get;set;}
public String rateType {get;set;}
public Details(JSONParser parser) {
while (parser.nextToken() != JSONToken.END_OBJECT) {
if (parser.getCurrentToken() == JSONToken.FIELD_NAME) {
String text = parser.getText();
if (parser.nextToken() != JSONToken.VALUE_NULL) {
if (text == 'id') {
id = parser.getText();
} else if (text == 'transactionLineId') {
transactionLineId = parser.getText();
} else if (text == 'transactionId') {
transactionId = parser.getText();
} else if (text == 'country') {
country = parser.getText();
} else if (text == 'region') {
region = parser.getText();
} else if (text == 'exemptAmount') {
exemptAmount = parser.getIntegerValue();
} else if (text == 'jurisCode') {
jurisCode = parser.getText();
} else if (text == 'jurisName') {
jurisName = parser.getText();
} else if (text == 'stateAssignedNo') {
stateAssignedNo = parser.getText();
} else if (text == 'jurisType') {
jurisType = parser.getText();
} else if (text == 'nonTaxableAmount') {
nonTaxableAmount = parser.getIntegerValue();
} else if (text == 'rate') {
rate = parser.getDoubleValue();
} else if (text == 'tax') {
tax = parser.getDoubleValue();
} else if (text == 'taxableAmount') {
taxableAmount = parser.getIntegerValue();
} else if (text == 'taxType') {
taxType = parser.getText();
} else if (text == 'taxName') {
taxName = parser.getText();
} else if (text == 'taxAuthorityTypeId') {
taxAuthorityTypeId = parser.getIntegerValue();
} else if (text == 'taxCalculated') {
taxCalculated = parser.getDoubleValue();
} else if (text == 'rateType') {
rateType = parser.getText();
} else {
consumeObject(parser);
}
1546
CommerceTax NamespaceTransaction Management

===== PAGE 1561 =====

}
}
}
}
}
public class Messages {
public String summary {get;set;}
public String details {get;set;}
public String refersTo {get;set;}
public String severity {get;set;}
public String source {get;set;}
public Messages(JSONParser parser) {
while (parser.nextToken() != JSONToken.END_OBJECT) {
if (parser.getCurrentToken() == JSONToken.FIELD_NAME) {
String text = parser.getText();
if (parser.nextToken() != JSONToken.VALUE_NULL) {
if (text == 'summary') {
summary = parser.getText();
} else if (text == 'details') {
details = parser.getText();
} else if (text == 'refersTo') {
refersTo = parser.getText();
} else if (text == 'severity') {
severity = parser.getText();
} else if (text == 'source') {
source = parser.getText();
} else {
consumeObject(parser);
}
}
}
}
}
}
public String id {get;set;}
public String code {get;set;}
public String referenceCode {get;set;}
public Integer companyId {get;set;}
public String taxDate {get;set;}
public String transactionDate {get;set;}
public String status {get;set;}
public String type_Z {get;set;} // in json: type
public Boolean reconciled {get;set;}
public Integer totalAmount {get;set;}
public Integer totalExempt {get;set;}
public Double totalTax {get;set;}
public Integer totalTaxable {get;set;}
public Double totalTaxCalculated {get;set;}
public String adjustmentReason {get;set;}
public Boolean locked {get;set;}
public Integer version {get;set;}
1547
CommerceTax NamespaceTransaction Management

===== PAGE 1562 =====

public String modifiedDate {get;set;}
public Integer modifiedUserId {get;set;}
public List<Lines> lines {get;set;}
public List<Addresses> addresses {get;set;}
public List<Summary> summary {get;set;}
public List<Messages> messages {get;set;}
public JsonSuccessParser(JSONParser parser) {
while (parser.nextToken() != JSONToken.END_OBJECT) {
if (parser.getCurrentToken() == JSONToken.FIELD_NAME) {
String text = parser.getText();
if (parser.nextToken() != JSONToken.VALUE_NULL) {
if (text == 'id') {
id = parser.getText();
} else if (text == 'code') {
code = parser.getText();
} else if (text == 'referenceCode'){
referenceCode = parser.getText();
} else if (text == 'companyId') {
companyId = parser.getIntegerValue();
} else if (text == 'taxDate') {
taxDate = parser.getText();
} else if (text == 'date') {
transactionDate = parser.getText();
} else if (text == 'status') {
status = parser.getText();
} else if (text == 'type') {
type_Z = parser.getText();
} else if (text == 'reconciled') {
reconciled = parser.getBooleanValue();
} else if (text == 'totalAmount') {
totalAmount = parser.getIntegerValue();
} else if (text == 'totalExempt') {
totalExempt = parser.getIntegerValue();
} else if (text == 'totalTax') {
totalTax = parser.getDoubleValue();
} else if (text == 'totalTaxable') {
totalTaxable = parser.getIntegerValue();
} else if (text == 'totalTaxCalculated') {
totalTaxCalculated = parser.getDoubleValue();
} else if (text == 'adjustmentReason') {
adjustmentReason = parser.getText();
} else if (text == 'locked') {
locked = parser.getBooleanValue();
} else if (text == 'version') {
version = parser.getIntegerValue();
} else if (text == 'modifiedDate') {
modifiedDate = parser.getText();
} else if (text == 'modifiedUserId') {
modifiedUserId = parser.getIntegerValue();
} else if (text == 'lines') {
lines = new List<Lines>();
while (parser.nextToken() != JSONToken.END_ARRAY) {
lines.add(new Lines(parser));
1548
CommerceTax NamespaceTransaction Management

===== PAGE 1563 =====

}
} else if (text == 'addresses') {
addresses = new List<Addresses>();
while (parser.nextToken() != JSONToken.END_ARRAY) {
addresses.add(new Addresses(parser));
}
} else if (text == 'summary') {
summary = new List<Summary>();
while (parser.nextToken() != JSONToken.END_ARRAY) {
summary.add(new Summary(parser));
}
} else if (text == 'messages') {
messages = new List<Messages>();
while (parser.nextToken() != JSONToken.END_ARRAY) {
messages.add(new Messages(parser));
}
} else {
consumeObject(parser);
}
}
}
}
}
public class Summary {
public String country {get;set;}
public String region {get;set;}
public String jurisType {get;set;}
public String jurisCode {get;set;}
public String jurisName {get;set;}
public Integer taxAuthorityType {get;set;}
public String stateAssignedNo {get;set;}
public String taxType {get;set;}
public String taxName {get;set;}
public String taxGroup {get;set;}
public String rateType {get;set;}
public Integer taxable {get;set;}
public Double rate {get;set;}
public Double tax {get;set;}
public Double taxCalculated {get;set;}
public Integer nonTaxable {get;set;}
public Integer exemption {get;set;}
public Summary(JSONParser parser) {
while (parser.nextToken() != JSONToken.END_OBJECT) {
if (parser.getCurrentToken() == JSONToken.FIELD_NAME) {
String text = parser.getText();
if (parser.nextToken() != JSONToken.VALUE_NULL) {
if (text == 'country') {
country = parser.getText();
} else if (text == 'region') {
region = parser.getText();
} else if (text == 'jurisType') {
jurisType = parser.getText();
1549
CommerceTax NamespaceTransaction Management

===== PAGE 1564 =====

} else if (text == 'jurisCode') {
jurisCode = parser.getText();
} else if (text == 'jurisName') {
jurisName = parser.getText();
} else if (text == 'taxAuthorityType') {
taxAuthorityType = parser.getIntegerValue();
} else if (text == 'stateAssignedNo') {
stateAssignedNo = parser.getText();
} else if (text == 'taxType') {
taxType = parser.getText();
} else if (text == 'taxName') {
taxName = parser.getText();
} else if (text == 'taxGroup') {
taxGroup = parser.getText();
} else if (text == 'rateType') {
rateType = parser.getText();
} else if (text == 'taxable') {
taxable = parser.getIntegerValue();
} else if (text == 'rate') {
rate = parser.getDoubleValue();
} else if (text == 'tax') {
tax = parser.getDoubleValue();
} else if (text == 'taxCalculated') {
taxCalculated = parser.getDoubleValue();
} else if (text == 'nonTaxable') {
nonTaxable = parser.getIntegerValue();
} else if (text == 'exemption') {
exemption = parser.getIntegerValue();
} else {
consumeObject(parser);
}
}
}
}
}
}
public class Lines {
public String id {get;set;}
public String transactionId {get;set;}
public String lineNumber {get;set;}
public Integer discountAmount {get;set;}
public Integer exemptAmount {get;set;}
public Integer exemptCertId {get;set;}
public Boolean isItemTaxable {get;set;}
public Integer lineAmount {get;set;}
public Double quantity {get;set;}
public String reportingDate {get;set;}
public Double tax {get;set;}
public Integer taxableAmount {get;set;}
public Double taxCalculated {get;set;}
public String taxCode {get;set;}
public String taxDate {get;set;}
public Boolean taxIncluded {get;set;}
1550
CommerceTax NamespaceTransaction Management

===== PAGE 1565 =====

public List<Details> details {get;set;}
public String itemCode {get;set;}
public Lines(JSONParser parser) {
while (parser.nextToken() != JSONToken.END_OBJECT) {
if (parser.getCurrentToken() == JSONToken.FIELD_NAME) {
String text = parser.getText();
if (parser.nextToken() != JSONToken.VALUE_NULL) {
if (text == 'id') {
id = parser.getText();
} else if (text == 'transactionId') {
transactionId = parser.getText();
}else if (text == 'itemCode') {
itemCode = parser.getText();
}else if (text == 'lineNumber') {
lineNumber = parser.getText();
} else if (text == 'discountAmount') {
discountAmount = parser.getIntegerValue();
} else if (text == 'exemptAmount') {
exemptAmount = parser.getIntegerValue();
} else if (text == 'exemptCertId') {
exemptCertId = parser.getIntegerValue();
} else if (text == 'isItemTaxable') {
isItemTaxable = parser.getBooleanValue();
} else if (text == 'lineAmount') {
lineAmount = parser.getIntegerValue();
} else if (text == 'quantity') {
quantity = parser.getDoubleValue();
} else if (text == 'reportingDate') {
reportingDate = parser.getText();
} else if (text == 'tax') {
tax = parser.getDoubleValue();
} else if (text == 'taxableAmount') {
taxableAmount = parser.getIntegerValue();
} else if (text == 'taxCalculated') {
taxCalculated = parser.getDoubleValue();
} else if (text == 'taxCode') {
taxCode = parser.getText();
} else if (text == 'taxDate') {
taxDate = parser.getText();
} else if (text == 'taxIncluded') {
taxIncluded = parser.getBooleanValue();
} else if (text == 'details') {
details = new List<Details>();
while (parser.nextToken() != JSONToken.END_ARRAY) {
details.add(new Details(parser));
}
} else {
consumeObject(parser);
}
}
}
}
}
}
1551
CommerceTax NamespaceTransaction Management

===== PAGE 1566 =====

public static JsonSuccessParser parse(String json)
{
return new JsonSuccessParser(System.JSON.createParser(json));
}
}
Prepare your JSON request to call the Avalara endpoint by using the AvalaraJSONBuilder  class.
public with sharing class AvalaraJSONBuilder
{
private static AvalaraJSONBuilder avalaraJSONBuilderInstance;
public static AvalaraJSONBuilder getInstance()
{
if (NULL == avalaraJSONBuilderInstance)
{
avalaraJSONBuilderInstance = new AvalaraJSONBuilder();
}
return avalaraJSONBuilderInstance;
}
public String frameJsonForGetTaxOrderItem(commercetax.CalculateTaxRequest
calculateTaxRequest)
{
try
{
Id accountid = null;
if(calculateTaxRequest.CustomerDetails.AccountId != null &&
calculateTaxRequest.CustomerDetails.AccountId != '')
accountid = Id.valueof(calculateTaxRequest.CustomerDetails.AccountId);
JSONGenerator jsonGeneratorInstance = JSON.createGenerator(true);
jsonGeneratorInstance.writeStartObject();
String type = null;
if(calculateTaxRequest.taxtype == commercetax.CalculateTaxType.Actual)
type ='SalesInvoice';
else type = 'SalesOrder';
jsonGeneratorInstance.writeStringField('type', type);
if(calculateTaxRequest.SellerDetails != null)
jsonGeneratorInstance.writeStringField('companyCode',
calculateTaxRequest.SellerDetails.code);
else
jsonGeneratorInstance.writeStringField('companyCode', 'billing2');
if(calculateTaxRequest.isCommit != null) {
jsonGeneratorInstance.writeBooleanField('commit',
calculateTaxRequest.isCommit);
}
if(calculateTaxRequest.documentcode != null){
jsonGeneratorInstance.writeStringField('code',
calculateTaxRequest.documentcode);
}else if(calculateTaxRequest.referenceEntityId != null) {
jsonGeneratorInstance.writeStringField('code',
calculateTaxRequest.referenceEntityId);
1552
CommerceTax NamespaceTransaction Management

===== PAGE 1567 =====

}
if(calculateTaxRequest.CustomerDetails.code == null && accountid !=null)
{
Account acc = [select id, name from account where id=:accountid];
jsonGeneratorInstance.writeStringField('customerCode', acc.name);
} else {
jsonGeneratorInstance.writeStringField('customerCode',
calculateTaxRequest.CustomerDetails.code);
}
if(calculateTaxRequest.EffectiveDate == null)
jsonGeneratorInstance.writeDateField('date', system.today());
else
jsonGeneratorInstance.writeDateTimeField('date',
calculateTaxRequest.EffectiveDate);
jsonGeneratorInstance.writeFieldName('lines');
jsonGeneratorInstance.writeStartArray();
for(integer i=0;i<1;i++){
for(Commercetax.TaxLineItemRequest lineItem :
calculateTaxRequest.LineItems)
{
jsonGeneratorInstance.writeStartObject();
if(lineItem.linenumber != null){
jsonGeneratorInstance.writeStringField('number',
lineItem.linenumber);
}
jsonGeneratorInstance.writeNumberField('quantity',
lineItem.Quantity);
jsonGeneratorInstance.writeNumberField('amount',
(lineItem.Amount));
jsonGeneratorInstance.writeStringField('taxCode',lineItem.taxCode);
jsonGeneratorInstance.writeFieldName('addresses');
jsonGeneratorInstance.writeStartObject();
jsonGeneratorInstance.writeFieldName('ShipFrom');
jsonGeneratorInstance.writeStartObject();
jsonGeneratorInstance.writeStringField('line1',
lineItem.addresses.shipfrom.street);
jsonGeneratorInstance.writeStringField('line2',
lineItem.addresses.shipfrom.street);
jsonGeneratorInstance.writeStringField('city',
lineItem.addresses.shipfrom.city);
jsonGeneratorInstance.writeStringField('region',
lineItem.addresses.shipfrom.state);
jsonGeneratorInstance.writeStringField('country',
lineItem.addresses.shipfrom.country);
jsonGeneratorInstance.writeStringField('postalCode',lineItem.addresses.shipfrom.postalcode);
jsonGeneratorInstance.writeEndObject();
jsonGeneratorInstance.writeFieldName('ShipTo');
jsonGeneratorInstance.writeStartObject();
1553
CommerceTax NamespaceTransaction Management

===== PAGE 1568 =====

jsonGeneratorInstance.writeStringField('line1',
lineItem.addresses.shipto.street);
jsonGeneratorInstance.writeStringField('line2',
lineItem.addresses.shipto.street);
jsonGeneratorInstance.writeStringField('city',
lineItem.addresses.shipto.city);
jsonGeneratorInstance.writeStringField('region',
lineItem.addresses.shipto.state);
jsonGeneratorInstance.writeStringField('country',
lineItem.addresses.shipto.country);
jsonGeneratorInstance.writeStringField('postalCode',lineItem.addresses.shipto.postalcode);
jsonGeneratorInstance.writeEndObject();
jsonGeneratorInstance.writeFieldName('pointOfOrderOrigin');
jsonGeneratorInstance.writeStartObject();
jsonGeneratorInstance.writeStringField('line1',
lineItem.addresses.soldto.street);
jsonGeneratorInstance.writeStringField('line2',
lineItem.addresses.soldto.street);
jsonGeneratorInstance.writeStringField('city',
lineItem.addresses.soldto.city);
jsonGeneratorInstance.writeStringField('region',
lineItem.addresses.soldto.state);
jsonGeneratorInstance.writeStringField('country',
lineItem.addresses.soldto.country);
jsonGeneratorInstance.writeStringField('postalCode',lineItem.addresses.soldto.postalcode);
jsonGeneratorInstance.writeEndObject();
if(lineItem.effectiveDate != null)
{
jsonGeneratorInstance.writeFieldName('taxOverride');
jsonGeneratorInstance.writeStartObject();
jsonGeneratorInstance.writeDateTimeField('taxDate',
lineItem.effectiveDate);
jsonGeneratorInstance.writeEndObject();
}
jsonGeneratorInstance.writeEndObject();
jsonGeneratorInstance.writeEndObject();
}
}
jsonGeneratorInstance.writeEndArray();
jsonGeneratorInstance.writeEndObject();
return jsonGeneratorInstance.getAsString();
}
catch (Exception e)
{
throw e;
}
1554
CommerceTax NamespaceTransaction Management

===== PAGE 1569 =====

}
}
• Use the JsonErrorParser  class to extract the error details, if any.
global with sharing class JsonErrorParser
{
public cls_error error;
public class cls_error
{
public String code;
public String message;
public String target;
public cls_details[] details;
}
public class cls_details
{
public String code;
public String message;
public String description;
public String faultCode;
public String helpLink;
public String severity;
}
public static JsonErrorParser parse(String json)
{
return (JsonErrorParser) System.JSON.deserialize(json,JsonErrorParser.class);
}
}
Tax Mappings for Quotes and Orders
You can extend and customize the tax interface for quotes and orders by using custom metadata types and tax mappings. These
customizations help you with unique business requirements such as the inclusion of specific data for accurate calculations and audits.
Tax callout extensions are supported for the Quote, QuoteLineItem, Order, and OrderItem objects to include additional fields to tax
requests. You must manually write back tax response extensions to the objects. See custom metadata types to specify all your tax
mapping definitions.
Request Mappings for Header Attributes
This table defines the request mappings between the header attributes of a tax callout and fields of applicable quote and order objects.
Order MappingQuote MappingHeader Attributes
If multi-currency is enabled, then this value
is Order.CurrencyISOCode.
Otherwise, this value is NULL.
If multi-currency is enabled, then this value
is Quote.CurrencyISOCode.
Otherwise, this value is NULL.
currencyIsoCode
FalseFalseisCommit
1555
CommerceTax NamespaceTransaction Management

===== PAGE 1570 =====

Order MappingQuote MappingHeader Attributes
Order.IDQuote.IDreferenceEntityId
TaxTreatment.TaxEngine.IDTaxTreatment.TaxEngine.IDtaxEngineId
System DateCurrent System DatetransactionDate
NULLsellerDetails
TaxEngine.SellerCodecode
customerDetails
Order.AccountIdQuote.AccountIdaccountId
NULLNULLcode
NULLNULLexemptionNo
NULLNULLexemptionReason
EstimatedEstimatedtaxType
NULLNULLtaxTransactionType
NULLNULLeffectiveDate
addresses
NULLNULLbillTo
NULLNULLshipTo
NULLNULLshipFrom
NULLNULLsoldTo
TaxEngine.AddressTaxEngine.AddresstaxEngineAddress
NULLNULLreferenceDocumentCode
NULLNULLdescription
Order.ID-TaxEngineIdQuote.ID-TaxEngineIddocumentCode
FALSEFALSEshouldVoid
Refer to the next line attributes section.Refer to the next line attributes section.lineItems
Request Mappings for Line Attributes
This table defines the request mappings between the line attributes of a tax callout and fields of applicable quote line items and order
products.
Order Product MappingQuote Line Item MappingLine Attributes
TaxTreatment.TaxCodeTaxTreatment.TaxCodetaxCode
TaxTreatment.ProductCodeTaxTreatment.ProductCodeproductCode
1556
CommerceTax NamespaceTransaction Management

===== PAGE 1571 =====

Order Product MappingQuote Line Item MappingLine Attributes
OrderItem.Product2.IdQuoteLineItem.Product2.IdproductId
OrderItem.TotalPriceQuoteLineItem.TotalPriceamount
Current System DateCurrent System DateeffectiveDate
OrderItem.IdQuoteLineItem.IdlineNumber
NULLNULLdescription
OrderItem.QuantityQuoteLineItem.Quantityquantity
addresses
Order.BillingAddressQuote.BillingAddress. If Quote.BillingAddress
is null, then this value is
Quote.Account.BillingAddress.
billTo
Order.ShippingAddressQuote.ShippingAddress. If
Quote.ShippingAddress is null, then this
value is Quote.Account.ShippingAddress.
shipTo
NULLNULLshipFrom
NULLNULLsoldTo
OrderItem.Product2.ProductCodeQuoteLineItem.Product2.ProductCodeproductsku
NULLNULLreferenceDocumentCode
Response Mappings for Header Attributes
This table defines the response mappings between the header attributes of a tax callout and fields of applicable objects. Most response
data is used for tax calculation and isn’t persisted on quote or order records.
Order MappingQuote MappingHeader Attributes
Order.CurrencyISOCodeQuote.CurrencyISOCodecurrencyIsoCode
Not returned.Not returned.isCommit
Order.IDQuote.IDreferenceEntityId
TaxTreatment.TaxEngine.IDTaxTreatment.TaxEngine.IDtaxEngineId
System DateSystem DatetransactionDate
Not returned.Not returned.sellerDetails
Not returned.Not returned.code
Not returned.Not returned.customerDetails
Not returned.Not returned.accountId
Not returned.Not returned.code
1557
CommerceTax NamespaceTransaction Management

===== PAGE 1572 =====

Order MappingQuote MappingHeader Attributes
Not returned.Not returned.exemptionNo
Not returned.Not returned.exemptionReason
EstimatedEstimatedtaxType
Not returned.Not returned.taxTransactionType
System DateSystem DateeffectiveDate
addresses
Not returned.Not returned.billTo
locationCode -> locationCodelocationCode -> locationCodeshipTo
Not returned.Not returned.shipFrom
Not returned.Not returned.soldTo
Not returned.Not returned.taxEngineAddress
Not returned.Not returned.referenceDocumentCode
Not returned.Not returned.description
Order.ID-TaxEngineIdQuote.ID-TaxEngineIddocumentCode
UncommittedUncommittedstatus
Not returned.Not returned.taxEngineLogs
Not returned.Not returned.resultCode
System DateSystem DatetransactionDate
amountDetails
Actual exemptAmount from response.Actual exemptAmount from response.exemptAmount
Actual taxAmount from response.Actual taxAmount from response.taxAmount
Order.SubtotalQuote.SubtotaltotalAmount
TaxAmount + TotalAmountTaxAmount + TotalAmounttotalAmountWithTax
Refer to the next line attributes section.Refer to the next line attributes section.lineItems
Response Mappings for Line Attributes
This table defines the response mappings between the line attributes of a tax callout and fields of applicable objects.
Order Product MappingQuote Line Item MappingLine Attributes
TaxTreatment.TaxCodeTaxTreatment.TaxCodetaxCode
TaxTreatment.ProductCodeTaxTreatment.ProductCodeproductCode
1558
CommerceTax NamespaceTransaction Management

===== PAGE 1573 =====

Order Product MappingQuote Line Item MappingLine Attributes
Not returned.Not returned.productId
amountDetails
Actual exemptAmount from responseActual exemptAmount from responseexemptAmount
Actual taxAmount from responseActual taxAmount from responsetaxAmount
OrderItem.SubtotalQuoteLineItem.SubtotaltotalAmount
TaxAmount + TotalAmountTaxAmount + TotalAmounttotalAmountWithTax
System DateSystem DateeffectiveDate
OrderItem.IdQuoteLineItem.IdlineNumber
Not returned.Not returned.description
Not returned.Not returned.quantity
addresses
Not persisted.Not persisted.billTo
locationCode -> locationCodelocationCode -> locationCodeshipTo
Not returned.Not returned.shipFrom
Not returned.Not returned.soldTo
Not returned.Not returned.productsku
Not returned.Not returned.referenceDocumentCode
Refer to the next tax attributes section.Refer to the next tax attributes section.taxes
Response Mappings for Tax Attributes
This table defines the response mappings between the tax attributes of a tax callout and fields of applicable objects.
Order MappingQuote MappingTax Attributes
Not returned.Not returned.exemptAmount
Not returned.Not returned.exemptReason
imposition
Not returned.Not returned.type
Not returned.Not returned.Name
jurisdiction
Not returned.Not returned.country
Not returned.Not returned.id
1559
CommerceTax NamespaceTransaction Management

===== PAGE 1574 =====

Order MappingQuote MappingTax Attributes
Not returned.Not returned.level
Not returned.Not returned.name
Not returned.Not returned.region
Not returned.Not returned.stateAssignedNo
OrderItemTaxItem.RateQuoteItemTaxItem.Raterate
OrderItemTaxItem.amountQuoteItemTaxItem.amounttax
Not returned.Not returned.taxId
Not returned.Not returned.taxableAmount
TaxEngineContext Class
Wrapper class that stores details about the type of a tax calculation request.
Namespace
CommerceTax
Example
At the beginning of a tax adapter, use TaxEngineContext class to pass the value of a request type to an instance of RequestType.
global virtual class MockAdapter implements commercetax.TaxEngineAdapter {
global commercetax.TaxEngineResponse processRequest(commercetax.TaxEngineContext
taxEngineContext) {
commercetax.RequestType requestType = taxEngineContext.getRequestType();
commercetax.CalculateTaxRequest request =
(commercetax.CalculateTaxRequest)taxEngineContext.getRequest();
Build the rest of your adapter based on the type of request that you got from TaxEngineContext  class.
if(requestType == commercetax.RequestType.CalculateTax){
commercetax.calculatetaxtype type = request.taxtype;
String docCode='';
if(request.DocumentCode == 'simulateEmptyDocumentCode')
docCode = '';
else if(request.DocumentCode != null)
docCode =request.DocumentCode;
else if(request.ReferenceEntityId != null) docCode = request.ReferenceEntityId;
else docCode = String.valueOf(getRandomInteger(0,2147483647));
commercetax.CalculateTaxResponse response = new
commercetax.CalculateTaxResponse();
if(request.isCommit == true) {
response.setStatus(commercetax.TaxTransactionStatus.Committed);
} else {
1560
CommerceTax NamespaceTransaction Management

===== PAGE 1575 =====

response.setStatus(commercetax.TaxTransactionStatus.Uncommitted);
}
}
TaxEngineContext Constructors
Learn more about the available constructors with the TaxEngineContext  class.
TaxEngineContext Methods
Learn more about the available methods with the TaxEngineContext  class.
TaxEngineContext Constructors
Learn more about the available constructors with the TaxEngineContext  class.
The TaxEngineContext  class includes these constructors.
TaxEngineContext(request, requestType, namedUri)
Initializes the TaxEngineContext object. This constructor is intended for test usage and throws an exception if used outside
of the Apex test context.
TaxEngineContext(request, requestType, namedUri)
Initializes the TaxEngineContext object. This constructor is intended for test usage and throws an exception if used outside of
the Apex test context.
Signature
TaxEngineContext(commercetax.TaxEngineRequest request, commercetax.RequestType
requestType, String namedUri)
Parameters
request
Type: TaxEngineRequest
Information about the request.
requestType
Type: RequestType
Whether the tax request is to calculate or estimate tax.
namedUri
Type: String
URI that was called as part of the tax calculation request.
TaxEngineContext Methods
Learn more about the available methods with the TaxEngineContext  class.
The TaxEngineContext  class includes these methods.
1561
CommerceTax NamespaceTransaction Management

===== PAGE 1576 =====

getNamedUri()
Retrieves the value of the NamedUri field of the TaxEngineContext  class.
getRequest()
Gets the value of the TaxEngineContext's Request field.
getRequestType()
Gets the value of the RequestType field of the TaxEngineContext  class.
getNamedUri()
Retrieves the value of the NamedUri field of the TaxEngineContext  class.
Signature
global String getNamedUri()
Return Value
Type: String
getRequest()
Gets the value of the TaxEngineContext's Request field.
Signature
global commercetax.TaxEngineRequest getRequest()
Return Value
Type: TaxEngineRequest
An implemented instance of an external tax engine's interface for processing requests. We've provided the TaxEngineRequest
interface for you to test within mock adapters with classes that implement it, such as CalculateTaxRequest. However, don’t use it outside
of a testing context.
getRequestType()
Gets the value of the RequestType field of the TaxEngineContext  class.
Signature
global commercetax.RequestType getRequestType()
Return Value
Type: RequestType
Indicates whether the calculation request was for actual or calculated tax.
1562
CommerceTax NamespaceTransaction Management

===== PAGE 1577 =====

TaxLineItemRequest Class
Contains line item details of a tax request.
Namespace
CommerceTax
TaxLineItemRequest Constructors
Learn more about the constructors available with the TaxLineItemRequest  class.
TaxLineItemRequest Properties
Learn more about the available properties with the TaxLineItemRequest  class.
TaxLineItemRequest Methods
Learn more about the available methods with the TaxLineItemRequest  class.
TaxLineItemRequest Constructors
Learn more about the constructors available with the TaxLineItemRequest  class.
The TaxLineItemRequest  class includes these constructors.
TaxLineItemRequest(addresses, amount, description, productCode, quantity, lineNumber, taxCode, effectiveDate)
Initializes the request for the tax line item. This constructor is intended for test usage and throws an exception if used outside of the
Apex test context.
TaxLineItemRequest(addresses,amount, description, productCode, quantity, lineNumber,
taxCode, effectiveDate)
Initializes the request for the tax line item. This constructor is intended for test usage and throws an exception if used outside of the
Apex test context.
Signature
global TaxLineItemRequest(commercetax.LineTaxAddressesRequestaddresses, Double amount,
String description, String productCode, Double quantity, String lineNumber, String
taxCode, Datetime effectiveDate)
commercetax.TaxLineItemRequest, newinstance, [commercetax.LineTaxAddressesRequest, Double,
String, String, Double, String, String, Datetime], commercetax.TaxLineItemRequest
Parameters
addresses
Type: LineTaxAddressesRequest
Information about the addresses applied to each line item in a tax calculation request.
amount
Type: Double
Total amount (in a given currency) represented by a line item sent for tax calculation.
1563
CommerceTax NamespaceTransaction Management

===== PAGE 1578 =====

description
Type: String
User-defined description for a tax line item.
productCode
Type: String
Catalog code for the product represented by the tax line item.
quantity
Type: Double
Number of units of a given product that the tax line item represents.
lineNumber
Type: String
Unique number used to identify a tax line item.
taxCode
Type: String
Code used to identify how tax is calculated for a tax line item.
effectiveDate
Type: Datetime
This is a user-defined date used for reporting only. For negative invoice lines, this parameter represents the invoice date from the
original invoice. In other cases, it represents the date when the tax transaction takes effect on the line item. The previous tax transaction
type is always Debit  for negative invoice lines.
TaxLineItemRequest Properties
Learn more about the available properties with the TaxLineItemRequest  class.
The TaxLineItemRequest  class includes these properties.
addresses
Contains the list of addresses of a line item.
amount
Total amount (in a given currency) represented by a line item sent for tax calculation.
customTaxAttributes
Customised tax contract to include additional attributes at the line item level.
description
User-defined description for a tax line item.
effectiveDate
The date that a tax transaction takes effect on a line item. This is a user-defined date used for reporting only.
lineNumber
Unique number used to identify a tax line item.
productCode
Catalog code for the product represented by the tax line item.
1564
CommerceTax NamespaceTransaction Management

===== PAGE 1579 =====

productSKU
Unique identifier of a product that can be used to identify products that are exempted from tax.
quantity
Number of units of a given product that the tax line item represents.
referenceDocumentCode
Identifier that combines the original invoice ID, previous tax transaction type, and tax engine ID, used in tax calculations for negative
invoice lines.
taxCode
Code used to identify how tax is calculated for a tax line item.
addresses
Contains the list of addresses of a line item.
Signature
public commercetax.LineTaxAddressesRequest addresses {get; set;}
Property Value
Type: commercetax.LineTaxAddressesRequest
amount
Total amount (in a given currency) represented by a line item sent for tax calculation.
Signature
global Double amount {get; set;}
Property Value
Type: Double
customTaxAttributes
Customised tax contract to include additional attributes at the line item level.
Signature
global commercetax.TaxLineItemRequest customTaxAttributes {get; set;}
Property Value
Type: Map<String, Object>
description
User-defined description for a tax line item.
1565
CommerceTax NamespaceTransaction Management

===== PAGE 1580 =====

Signature
global String description {get; set;}
Property Value
Type: String
effectiveDate
The date that a tax transaction takes effect on a line item. This is a user-defined date used for reporting only.
Signature
global Datetime effectiveDate {get; set;}
Property Value
Type: Datetime
lineNumber
Unique number used to identify a tax line item.
Signature
global String lineNumber {get; set;}
Property Value
Type: String
productCode
Catalog code for the product represented by the tax line item.
Signature
global String productCode {get; set;}
Property Value
Type: String
productSKU
Unique identifier of a product that can be used to identify products that are exempted from tax.
Signature
global String productSKU {get; set;}
1566
CommerceTax NamespaceTransaction Management

===== PAGE 1581 =====

Property Value
Type: String
quantity
Number of units of a given product that the tax line item represents.
Signature
global Double quantity {get; set;}
Property Value
Type: Double
referenceDocumentCode
Identifier that combines the original invoice ID, previous tax transaction type, and tax engine ID, used in tax calculations for negative
invoice lines.
For example, a referenceDocumentCode parameter value 3ttxx00000004Bh_Debit-4wAxx0000000001EAA  indicates
3ttxx00000004Bh  is the original invoice ID and 4wAxx0000000001EAA  is the tax engine ID. The previous tax transaction
type is always Debit  for negative invoice lines.
Signature
global String referenceDocumentCode {get; set;}
Property Value
Type: String
taxCode
Code used to identify how tax is calculated for a tax line item.
Signature
global String taxCode {get; set;}
Property Value
Type: String
TaxLineItemRequest Methods
Learn more about the available methods with the TaxLineItemRequest  class.
The TaxLineItemRequest  class includes these methods.
1567
CommerceTax NamespaceTransaction Management

===== PAGE 1582 =====

equals(obj)
Maintains the integrity of lists of type TaxLineItemRequest  by determining the equality of external objects in a list. This
method is dynamic and is based on the equals()  method in Java.
hashCode()
Maintains the integrity of lists of type TaxLineItemRequest  by determining the uniqueness of the external object records in
a list.
toString()
Converts a value to a string.
equals(obj)
Maintains the integrity of lists of type TaxLineItemRequest  by determining the equality of external objects in a list. This method
is dynamic and is based on the equals()  method in Java.
Signature
global Boolean equals(Object obj)
Parameters
obj
Type: Object
External object whose key is to be validated.
Return Value
Type: Boolean
hashCode()
Maintains the integrity of lists of type TaxLineItemRequest  by determining the uniqueness of the external object records in a
list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a value to a string.
Signature
global String toString()
1568
CommerceTax NamespaceTransaction Management

===== PAGE 1583 =====

Return Value
Type: String
TaxSellerDetailsRequest Class
Contains tax code details used in the tax calculation request.
Namespace
CommerceTax
TaxSellerDetailsRequest Constructors
Learn more about the available constructors with the TaxSellerDetailsRequest  class.
TaxSellerDetailsRequest Properties
Learn more about the available properties with the TaxSellerDetailsRequest  class.
TaxSellerDetailsRequest Methods
Learn more about the available methods with the TaxSellerDetailsRequest  class.
TaxSellerDetailsRequest Constructors
Learn more about the available constructors with the TaxSellerDetailsRequest  class.
The TaxSellerDetailsRequest  class includes these constructors.
TaxSellerDetailsRequest(code)
Initializes the request for the tax seller details. This constructor is intended for test usage and throws an exception if used outside of
the Apex test context
TaxSellerDetailsRequest(code)
Initializes the request for the tax seller details. This constructor is intended for test usage and throws an exception if used outside of the
Apex test context
Signature
global TaxSellerDetailsRequest(String code)
Parameters
code
Type: String
Tax code used for tax calculation.
TaxSellerDetailsRequest Properties
Learn more about the available properties with the TaxSellerDetailsRequest  class.
The TaxSellerDetailsRequest  class includes these properties.
1569
CommerceTax NamespaceTransaction Management

===== PAGE 1584 =====

code
Tax code used for tax calculation.
code
Tax code used for tax calculation.
Signature
global String code {get; set;}
Property Value
Type: String
TaxSellerDetailsRequest Methods
Learn more about the available methods with the TaxSellerDetailsRequest  class.
The TaxSellerDetailsRequest  class includes these methods.
equals(obj)
Maintains the integrity of lists of type TaxSellerDetailsRequest  by determining the equality of the external objects in a
list. This method is dynamic and based on the equals() method in Java.
hashCode()
Maintains the integrity of lists of type TaxSellerDetailsRequest  by determining the uniqueness of the external objects
in a list.
toString()
Converts a value to a string.
equals(obj)
Maintains the integrity of lists of type TaxSellerDetailsRequest  by determining the equality of the external objects in a list.
This method is dynamic and based on the equals() method in Java.
Signature
global Boolean equals(Object obj)
Parameters
obj
Type: Object
External object whose key is to be validated.
Return Value
Type: Boolean
1570
CommerceTax NamespaceTransaction Management

===== PAGE 1585 =====

hashCode()
Maintains the integrity of lists of type TaxSellerDetailsRequest  by determining the uniqueness of the external objects in a
list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a value to a string.
Signature
global String toString()
Return Value
Type: String
TaxTransactionRequest Class
Abstract class for storing customer details used in tax calculation and estimation requests.
Namespace
CommerceTax
Usage
Specify the CommerceTax  namespace when creating an instance of this class. The constructor of this class takes no arguments. For
example, let's say you create an instance of CalculateTaxRequest  class, which extends the TaxTransactionRequest
class.
TaxTransactionRequest Constructors
Learn more about the available constructors with the TaxTransactionRequest  class.
TaxTransactionRequest Properties
Learn more about the available properties with the TaxTransactionRequest  class.
TaxTransactionRequest Methods
TaxTransactionRequest Constructors
Learn more about the available constructors with the TaxTransactionRequest  class.
The TaxTransactionRequest  class includes these constructors.
1571
CommerceTax NamespaceTransaction Management

===== PAGE 1586 =====

TaxTransactionRequest(addresses, currencyIsoCode, customerDetails, description, documentCode, referenceDocumentCode,
transactionDate, effectiveDate, lineItems, referenceEntityId, sellerDetails, customTaxAttributes)
Initializes the request for the tax transaction. This constructor is intended for test usage and throws an exception if used outside of
the Apex test context.
TaxTransactionRequest(addresses, currencyIsoCode, customerDetails, description,
documentCode, referenceDocumentCode, transactionDate, effectiveDate, lineItems,
referenceEntityId, sellerDetails, customTaxAttributes)
Initializes the request for the tax transaction. This constructor is intended for test usage and throws an exception if used outside of the
Apex test context.
Signature
global TaxTransactionRequest(commercetax.HeaderTaxAddressesRequest addresses, String
currencyIsoCode, commercetax.TaxCustomerDetailsRequest customerDetails, String
description, String documentCode, String referenceDocumentCode,Datetime transactionDate,
Datetime effectiveDate, List<commercetax.TaxLineItemRequest> lineItems, String
referenceEntityId, commercetax.TaxSellerDetailsRequest sellerDetails,Map<String,Object>
customTaxAttributes)
Parameters
addresses
Type: HeaderTaxAddressesRequest
Tax addresses, such as Ship To and Bill From.
currencyIsoCode
Type: String
Three-letter ISO 4217 currency code associated with the TaxTransactionRequest.
customerDetails
Type: TaxCustomerDetailsRequest
Customer information used in tax calculation.
description
Type: String
Optional user-defined description for providing more information about the tax transaction request.
documentCode
Type: String
Code for documents that are used to provide more information in the tax calculation process.
referenceDocumentCode
Type: String
Identifier that combines the original invoice ID, previous tax transaction type, and tax engine ID, used in tax calculations for negative
invoice lines. For example, a referenceDocumentCode parameter value 3ttxx00000004Bh_Debit-4wAxx0000000001EAA
indicates 3ttxx00000004Bh  is the original invoice ID and 4wAxx0000000001EAA  is the tax engine ID.
transactionDate
Type: Datetime
1572
CommerceTax NamespaceTransaction Management

===== PAGE 1587 =====

The date that the tax transaction occurred.
effectiveDate
Type: Datetime
The date that the tax transaction takes effect. User-defined and used only for reporting purposes.
lineItems
Type: List<TaxLineItemRequest>
A list of line items on which tax is calculated.
referenceEntityId
Type: String
ID of an object related to the line items sent for tax calculation.
sellerDetails
Type: TaxSellerDetailsRequest
Contains tax code information used in a tax calculation request.
customTaxAttributes
Type: Map<String, Object>
Customised tax contract to include additional attributes at the header level.
TaxTransactionRequest Properties
Learn more about the available properties with the TaxTransactionRequest  class.
The TaxTransactionRequest  class includes these properties.
addresses
A list of addresses (such as Ship To and Sold To) used as part of the tax transaction.
currencyIsoCode
Three-letter ISO 4217 currency code associated with the TaxTransactionRequest.
customerDetails
Customer information used in tax calculation.
customTaxAttributes
Customised tax contract to include additional attributes at the header level.
description
Optional user-defined description for providing more information about the tax transaction request.
documentCode
Code for documents used to provide more information in the tax calculation process.
effectiveDate
The date that the tax transaction takes effect. User-defined and used only for reporting purposes.
lineItems
A list of line items on which tax will be calculated.
referenceDocumentCode
Identifier that combines the original invoice ID, previous tax transaction type, and tax engine ID, used in tax calculations for negative
invoice lines.
1573
CommerceTax NamespaceTransaction Management

===== PAGE 1588 =====

referenceEntityId
ID of an object related to the line items sent for tax calculation.
sellerDetails
Contains tax code information used in a tax calculation request.
transactionDate
The date that the tax transaction occurred.
addresses
A list of addresses (such as Ship To and Sold To) used as part of the tax transaction.
Signature
global commercetax.HeaderTaxAddressesRequest addresses {get; set;}
Property Value
Type: HeaderTaxAddressesRequest
currencyIsoCode
Three-letter ISO 4217 currency code associated with the TaxTransactionRequest.
Signature
global String currencyIsoCode {get; set;}
Property Value
Type: String
customerDetails
Customer information used in tax calculation.
Signature
global CommerceTax.TaxCustomerDetailsRequest customerDetails {get; set;}
Property Value
Type: TaxCustomerDetailsRequest
customTaxAttributes
Customised tax contract to include additional attributes at the header level.
Signature
global commercetax.TaxTransactionRequest customTaxAttributes {get; set;}
1574
CommerceTax NamespaceTransaction Management

===== PAGE 1589 =====

Property Value
Type: Map<String, Object>
description
Optional user-defined description for providing more information about the tax transaction request.
Signature
global String description {get; set;}
Property Value
Type: String
documentCode
Code for documents used to provide more information in the tax calculation process.
Signature
global String documentCode {get; set;}
Property Value
Type: String
effectiveDate
The date that the tax transaction takes effect. User-defined and used only for reporting purposes.
Signature
global Datetime effectiveDate {get; set;}
Property Value
Type: Datetime
lineItems
A list of line items on which tax will be calculated.
Signature
global List<CommerceTax.TaxLineItemRequest> lineItems {get; set;}
Property Value
Type: List<TaxLineItemRequest>
1575
CommerceTax NamespaceTransaction Management

===== PAGE 1590 =====

referenceDocumentCode
Identifier that combines the original invoice ID, previous tax transaction type, and tax engine ID, used in tax calculations for negative
invoice lines.
For example, a referenceDocumentCode parameter value 3ttxx00000004Bh_Debit-4wAxx0000000001EAA  indicates
3ttxx00000004Bh  is the original invoice ID and 4wAxx0000000001EAA  is the tax engine ID.
Signature
global String referenceDocumentCode {get; set;}
Property Value
Type: String
referenceEntityId
ID of an object related to the line items sent for tax calculation.
Signature
global String referenceEntityId {get; set;}
Property Value
Type: String
sellerDetails
Contains tax code information used in a tax calculation request.
Signature
global commercetax.TaxSellerDetailsRequest sellerDetails {get; set;}
Property Value
Type: TaxSellerDetailsRequest
transactionDate
The date that the tax transaction occurred.
Signature
global Datetime transactionDate {get; set;}
Property Value
Type: Datetime
1576
CommerceTax NamespaceTransaction Management

===== PAGE 1591 =====

TaxTransactionRequest Methods
The following are methods for TaxTransactionRequest.
equals(obj)
Maintains the integrity of lists of type TaxTransactionRequest  by determining the equality of external objects in a list. This
method is dynamic and based on the equals()  method in Java.
hashCode()
Maintains the integrity of lists of type TaxTransactionRequest by determining the uniqueness of the external object records
in a list.
toString()
Converts a value to a string.
equals(obj)
Maintains the integrity of lists of type TaxTransactionRequest  by determining the equality of external objects in a list. This
method is dynamic and based on the equals()  method in Java.
Signature
global Boolean equals(Object obj)
Parameters
obj
Type: Object
Return Value
Type: Boolean
hashCode()
Maintains the integrity of lists of type TaxTransactionRequest  by determining the uniqueness of the external object records
in a list.
Signature
global Integer hashCode()
Return Value
Type: Integer
toString()
Converts a value to a string.
1577
CommerceTax NamespaceTransaction Management

===== PAGE 1592 =====

Signature
global String toString()
Return Value
Type: String
TaxTransactionStatus Enum
Shows whether the tax transaction has been committed or uncommitted.
Usage
Used by the CalculateTaxResponse class method.
Enum Values
The commercetax.TaxTransactionStatus  enum includes these values.
DescriptionValue
Tax has been calculated and committed.Committed
Tax has been calculated but hasn't been committed.Uncommitted
TaxTransactionType Enum
Shows whether the tax transaction is for a credit or debit transaction.
Usage
Used by the CalculateTaxResponse and CalculateTaxRequest class methods.
Enum Values
The commercetax.TaxTransactionType  enum includes these values.
DescriptionValue
Represents a credit transaction.Credit
Represents a debit transaction.Debit
Specifies that the tax engine has voided the document that's mentioned in the
referenceDocumentCode  property value.
Void
PlaceQuote Namespace
The PlaceQuote  namespace provides classes and methods to create or update quotes with pricing preferences and configuration
options.
1578
PlaceQuote NamespaceTransaction Management

===== PAGE 1593 =====

Note:  This namespace has been deprecated as of API version 63.0. In API version 63.0 and later, use the new RevSalesTrxn
namespace.
The PlaceQuote  namespace includes these classes.
CatalogRatesPreferenceEnum Enum
Specifies the rate card entries defined in the catalog that must be fetched for quote line items, with usage-based selling during the
quote creation process.
ConfigurationInputEnum Enum
Specifies the configuration input for the request to place a quote.
ConfigurationOptionsInput Class
Contains methods and properties to set the configuration options for the input to the product configurator.
GraphRequest Class
Contains constructors and properties to set the graph ID and a list of records to be ingested. The list of records is specified in a
key-value map format that contains the field values of an order.
PlaceQuoteException Class
Contains methods to hold the exception details for the place quote request.
PlaceQuoteResponse Class
Contains properties to hold the response to the place quote request.
PlaceQuoteRLMApexProcessor Class
Contains methods to place a quote with details of the graph request, pricing preferences, and configuration options.
PricingPreferenceEnum Enum
Specifies the pricing preference during the create quote process.
RecordResource Class
Contains constructors and properties to create a record object from the field values of a quote.
RecordWithReferenceRequest Class
Contains constructors and properties to associate a record object with a reference identifier.
CatalogRatesPreferenceEnum Enum
Specifies the rate card entries defined in the catalog that must be fetched for quote line items, with usage-based selling during the quote
creation process.
Usage
This enum is available when the Usage-Based Selling feature is enabled.
Enum Values
The placequote.CatalogRatesPreferenceEnum  enum includes these values.
DescriptionValue
Retrieves the rate card entries defined in the catalog for quote line items during the
quote creation process.
Fetch
1579
PlaceQuote NamespaceTransaction Management

===== PAGE 1594 =====

DescriptionValue
Skips the retrieval of rate card entries for quote line items during the quote creation
process. The default value is Skip.
Skip
ConfigurationInputEnum Enum
Specifies the configuration input for the request to place a quote.
Usage
Use these enum values for the configurationInputEnum property in the PlaceQuoteRLMApexProcessor class.
Enum Values
The placequote.ConfigurationInputEnum  enum has these values.
DescriptionValue
Run the configuration and proceed with order ingestion upon encountering any
configuration errors.
RunAndAllowErrors
Run the configuration and block order ingestion upon encountering any
configuration errors.
RunAndBlockErrors
Skip the configuration execution.Skip
ConfigurationOptionsInput Class
Contains methods and properties to set the configuration options for the input to the product configurator.
Namespace
PlaceQuote
Usage
This class holds the required details of the product configuration input. Set the class properties to enable default configuration, execution
of configuration rules, and validation of the product catalog. Use these class properties as an input to
the PlaceQuoteRLMApexProcessor class method.
Example
PlaceQuote.GraphRequest graph = new PlaceQuote.GraphRequest('test',listOfRecords);
PlaceQuote.PricingPreferenceEnum pricingPreference =
PlaceQuote.PricingPreferenceEnum.System;
PlaceQuote.ConfigurationInputEnum configurationPreference =
PlaceQuote.ConfigurationInputEnum.RunAndAllowErrors;
PlaceQuote.ConfigurationOptionsInputcInput = new PlaceQuote.ConfigurationOptionsInput();
1580
PlaceQuote NamespaceTransaction Management

===== PAGE 1595 =====

cInput.addDefaultConfiguration = true;
cInput.executeConfigurationRules = true;
cInput.validateAmendRenewCancel = true;
cInput.validateProductCatalog = true;
//Place Quote Call
PlaceQuote.PlaceQuoteResponse resp =
PlaceQuote.PlaceQuoteRLMApexProcessor.execute(pricingPreference,graph,configurationPreference,cInput);
ConfigurationOptionsInput Properties
Set the ConfigurationOptionsInput class properties to add default configuration, execute configuration rules, and validate
the product catalog.
ConfigurationOptionsInput Methods
Learn more about the methods available with the ConfigurationOptionsInput class.
ConfigurationOptionsInput Properties
Set the ConfigurationOptionsInput class properties to add default configuration, execute configuration rules, and validate
the product catalog.
The ConfigurationOptionsInput  class includes these properties.
addDefaultConfiguration
Sets the default product configuration, such as bundle and product attributes, for a quote request.
executeConfigurationRules
Sets the requirement for a quote to adhere to the configuration rules.
validateAmendRenewCancel
Sets the requirement to run validations related to amend, renew, or cancel processes.
validateProductCatalog
Sets the requirement to validate a quote against the product catalog.
addDefaultConfiguration
Sets the default product configuration, such as bundle and product attributes, for a quote request.
Signature
public Boolean addDefaultConfiguration {get; set;}
Property Value
Type: Boolean
Indicates whether to automatically add default configuration to the order (true) or not (false).
executeConfigurationRules
Sets the requirement for a quote to adhere to the configuration rules.
1581
PlaceQuote NamespaceTransaction Management

===== PAGE 1596 =====

Signature
public Boolean executeConfigurationRules {get; set;}
Property Value
Type: Boolean
Indicates whether the order must adhere to configuration rules during processing (true) or bypass them (false).
validateAmendRenewCancel
Sets the requirement to run validations related to amend, renew, or cancel processes.
Signature
public Boolean validateAmendRenewCancel {get; set;}
Property Value
Type: Boolean
Indicates whether to run validations related to amend, renew, or cancel processes (true) or not (false).
validateProductCatalog
Sets the requirement to validate a quote against the product catalog.
Signature
public Boolean validateProductCatalog {get; set;}
Property Value
Type: Boolean
Indicates whether the quote must be validated against the product catalog (true) or not (false).
ConfigurationOptionsInput Methods
Learn more about the methods available with the ConfigurationOptionsInput class.
The ConfigurationOptionsInput  class includes these methods.
equals(obj)
Determines the equality of external objects in a list. This method is dynamic and is based on the equals() method in Java.
hashCode()
Determines the uniqueness of the external object records in a list.
toString()
Converts a value to a string.
1582
PlaceQuote NamespaceTransaction Management

===== PAGE 1597 =====

equals(obj)
Determines the equality of external objects in a list. This method is dynamic and is based on the equals() method in Java.
Signature
public Boolean equals(Object obj)
Parameters
obj
Type: Object
Reference object that’s used to compare with the class object.
Return Value
Type: Boolean
Indicates if the class object is same as the reference object (true) or not (false).
hashCode()
Determines the uniqueness of the external object records in a list.
Signature
public Integer hashCode()
Return Value
Type: Integer
Integer hash code that represents the value of the object. Equal objects as per the equals() method must return the same hash
code.
toString()
Converts a value to a string.
Signature
public String toString()
Return Value
Type: String
GraphRequest Class
Contains constructors and properties to set the graph ID and a list of records to be ingested. The list of records is specified in a key-value
map format that contains the field values of an order.
1583
PlaceQuote NamespaceTransaction Management

===== PAGE 1598 =====

Namespace
PlaceQuote
Example
Invoke the Place Quote Apex API by using these steps.
• Set up a quote and quote line item. To associate the Record object with a reference identifier, create an instance of the
RecordWithReferenceRequest  class.
//Quote Setup
PlaceQuote.RecordResource quoteRecord = new
PlaceQuote.RecordResource(Quote.getSobjectType(),'POST');
Map<String,Object> quoteFieldValues = new Map<String,Object>();
quoteFieldValues.put('Name','q-ap12');
quoteFieldValues.put('OpportunityId','006xx000001aBFcAAM');
quoteFieldValues.put('Pricebook2Id','01sxx0000005pvRAAQ');
quoteRecord.fieldValues = quoteFieldValues;
//Quote Line Item Setup
PlaceQuote.RecordResource quoteLineItemRecord1 = new
PlaceQuote.RecordResource(QuoteLineItem.getSobjectType(),'POST');
Map<String,Object> quoteLineItemFieldValues = new Map<String,Object>();
quoteLineItemFieldValues.put('Product2Id','01txx0000006ibwAAA');
quoteLineItemFieldValues.put('PricebookEntryId','01uxx0000008zPqAAI');
quoteLineItemFieldValues.put('Quantity','2.0');
quoteLineItemFieldValues.put('UnitPrice','5.0');
quoteLineItemFieldValues.put('StartDate','2023-03-15');
quoteLineItemFieldValues.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord1.fieldValues = quoteLineItemFieldValues;
PlaceQuote.RecordWithReferenceRequest quoteItemRecords = new
PlaceQuote.RecordWithReferenceRequest('refQuote',quoteRecord);
PlaceQuote.RecordWithReferenceRequest quoteLineItemRecords1 = new
PlaceQuote.RecordWithReferenceRequest('refQuoteItem1',quoteLineItemRecord1);
• To create a quote line relationship, create an instance of the RecordResource class.
PlaceQuote.RecordResource quoteLineRelationship1 = new
PlaceQuote.RecordResource(QuoteLineRelationship.getSobjectType(),'POST');
Map<String,Object> quoteLineRelationshipValues = new Map<String,Object>();
quoteLineRelationshipValues.put('ProductRelationshipTypeId','0yoxx00000000JNAAY');
quoteLineRelationshipValues.put('MainQuoteLineId','@{refQuoteItem2.id}');
quoteLineRelationshipValues.put('AssociatedQuoteLineId','@{refQuoteItem1.id}');
quoteLineRelationshipValues.put('AssociatedQuoteLinePricing','IncludedInBundlePrice');
quoteLineRelationship1.fieldValues = quoteLineRelationshipValues;
• Create the list of records to be ingested.
PlaceQuote.RecordWithReferenceRequest quoteLineRelationship = new
PlaceQuote.RecordWithReferenceRequest('QuoteLineRelationship',quoteLineRelationship1);
List<PlaceQuote.RecordWithReferenceRequest> listOfRecords = new
1584
PlaceQuote NamespaceTransaction Management

===== PAGE 1599 =====

List<PlaceQuote.RecordWithReferenceRequest>();
listOfRecords.add(quoteItemRecords);
listOfRecords.add(quoteLineItemRecords1);
listOfRecords.add(quoteLineItemRecords2);
listOfRecords.add(quoteLineRelationship);
• To contain all record objects, create an instance of the GraphRequest  class.
Note:  The CatalogRatesPreferenceEnum  enum is available when the Usage-Based Selling feature is enabled.
PlaceQuote.GraphRequest graph = new PlaceQuote.GraphRequest('test',listOfRecords);
PlaceQuote.ConfigurationOptionsInput cInput = new
PlaceQuote.ConfigurationOptionsInput();
PlaceQuote.CatalogRatesPreferenceEnum catalogRatesPreference =
PlaceQuote.CatalogRatesPreferenceEnum.Fetch;
....PlaceQuote.ConfigurationInputEnum configurationPreference =
PlaceQuote.ConfigurationInputEnum.RunAndAllowErrors;
PlaceQuote.PricingPreferenceEnum pricingPreference =
PlaceQuote.PricingPreferenceEnum.System;
//System.debug(graph);
//Place Quote Call
PlaceQuote.PlaceQuoteResponse resp =
PlaceQuote.PlaceQuoteRLMApexProcessor.execute(pricingPreference,catalogRatesPreference,
graph, configurationPreference, cInput);
System.debug(resp);
GraphRequest Constructors
Learn more about the available constructors with the GraphRequest  class.
GraphRequest Properties
GraphRequest Constructors
Learn more about the available constructors with the GraphRequest  class.
The GraphRequest  class includes these constructors.
GraphRequest(graphId, records)
Creates an instance of the GraphRequest  class to assign the graph ID and a list of records to be ingested.
GraphRequest(graphId, records)
Creates an instance of the GraphRequest  class to assign the graph ID and a list of records to be ingested.
Signature
public GraphRequest(String graphId, List<placequote.RecordWithReferenceRequest>records)
1585
PlaceQuote NamespaceTransaction Management

===== PAGE 1600 =====

Parameters
graphId
Type: String
ID of the graph.
records
Type: List<placequote.RecordWithReferenceRequest on page 1596>
List of records to be ingested.
GraphRequest Properties
The following are properties for GraphRequest.
graphId
Set the graphId  property to assign the ID value of the graph.
graphId
Set the graphId  property to assign the ID value of the graph.
Signature
public String graphId {get; set;}
Property Value
Type: String
PlaceQuoteException Class
Contains methods to hold the exception details for the place quote request.
Namespace
PlaceQuote
PlaceQuoteException Methods
Learn more about the methods available with the PlaceQuoteException class.
PlaceQuoteException Methods
Learn more about the methods available with the PlaceQuoteException class.
The PlaceQuoteException  class includes these methods.
getErrorCode()
Gets the error code that’s associated to the place quote request.
1586
PlaceQuote NamespaceTransaction Management

===== PAGE 1601 =====

getErrorCode()
Gets the error code that’s associated to the place quote request.
Signature
public String getErrorCode()
Return Value
Type: String
PlaceQuoteResponse Class
Contains properties to hold the response to the place quote request.
Namespace
PlaceQuote
Example
PlaceQuote.PlaceQuoteResponse resp =
PlaceQuote.PlaceQuoteExecutor.execute(internalEnum,graph);
PlaceQuoteResponse Properties
Learn more about the available properties with the PlaceQuoteResponse class.
PlaceQuoteResponse Properties
Learn more about the available properties with the PlaceQuoteResponse class.
The PlaceQuoteResponse  class includes these properties.
quoteId
Get the ID of the quote that’s created after a successful request.
requestIdentifier
Get the request ID of the process to query the asynchronous status of the Place Quote Apex API.
responseError
Get the list of errors encountered during the synchronous processing of the API request.
statusURL
Get the asynchronous status URL of the request, if available.
success
Get the request status of the synchronous part of the processing.
quoteId
Get the ID of the quote that’s created after a successful request.
1587
PlaceQuote NamespaceTransaction Management

===== PAGE 1602 =====

Signature
public String quoteId {get; set;}
Property Value
Type: String
requestIdentifier
Get the request ID of the process to query the asynchronous status of the Place Quote Apex API.
Signature
public String requestIdentifier {get; set;}
Property Value
Type: String
responseError
Get the list of errors encountered during the synchronous processing of the API request.
Signature
public List<ConnectApi.PlaceQuoteErrorResponse> responseError {get; set;}
Property Value
Type: List<ConnectApi.PlaceQuoteErrorResponse>
statusURL
Get the asynchronous status URL of the request, if available.
Signature
public String statusURL {get; set;}
Property Value
Type: String
success
Get the request status of the synchronous part of the processing.
Signature
public Boolean success {get; set;}
1588
PlaceQuote NamespaceTransaction Management

===== PAGE 1603 =====

Property Value
Type: Boolean
Indicates whether the synchronous part of the processing is successful (true) or not (false).
PlaceQuoteRLMApexProcessor Class
Contains methods to place a quote with details of the graph request, pricing preferences, and configuration options.
Namespace
PlaceQuote
PlaceQuoteRLMApexProcessor Methods
Learn more about the methods available with the PlaceQuoteRLMApexProcessor class.
PlaceQuoteRLMApexProcessor Example Implementation
To place a quote from Apex, refer to the example implementation of the PlaceQuoteRLMApexProcessor  class.
PlaceQuoteRLMApexProcessor Methods
Learn more about the methods available with the PlaceQuoteRLMApexProcessor class.
The PlaceQuoteRLMApexProcessor  class includes these methods.
execute(pricingPreferenceEnum, graphRequest, configurationInputEnum, configurationOptionsInput)
Use the method in the PlaceQuoteExecutor class to execute the Place Quote Apex API request by assigning the properties
for graph request, pricing references, and configuration options.
execute(pricingPreferenceEnum, catalogRatesPreference, graphRequest, configurationInputEnum, configurationOptionsInput)
Use the method in the PlaceQuoteExecutor class to execute the Place Quote Apex API request by assigning the properties
for graph request, pricing references, and configuration options. This method also includes the property to define fetching of rate
card entries.
execute(pricingPreferenceEnum, graphRequest, configurationInputEnum,
configurationOptionsInput)
Use the method in the PlaceQuoteExecutor class to execute the Place Quote Apex API request by assigning the properties for
graph request, pricing references, and configuration options.
Signature
public static placequote.PlaceQuoteResponse execute(placequote.PricingPreferenceEnum
pricingPreferenceEnum, placequote.GraphRequest graphRequest,
placequote.ConfigurationInputEnum configurationInputEnum,
placequote.ConfigurationOptionsInput configurationOptionsInput)
1589
PlaceQuote NamespaceTransaction Management

===== PAGE 1604 =====

Parameters
pricingPreferenceEnum
Type: placequote.PricingPreferenceEnum
Pricing preference during the quote process.
graphRequest
Type: placequote.GraphRequest
The sObject graph values of the quote payload to be ingested.
configurationInputEnum
Type: placequote.ConfigurationInputEnum
Configuration input for the quote process.
configurationOptionsInput
Type: placequote.ConfigurationOptionsInput
Configuration options during the ingestion process.
Return Value
Type: placequote.PlaceQuoteResponse
execute(pricingPreferenceEnum, catalogRatesPreference, graphRequest,
configurationInputEnum, configurationOptionsInput)
Use the method in the PlaceQuoteExecutor class to execute the Place Quote Apex API request by assigning the properties for
graph request, pricing references, and configuration options. This method also includes the property to define fetching of rate card
entries.
Signature
public static placequote.PlaceQuoteResponse execute(placequote.PricingPreferenceEnum
pricingPreferenceEnum, placequote.CatalogRatesPreferenceEnum catalogRatesPreference,
placequote.GraphRequest graphRequest, placequote.ConfigurationInputEnum
configurationInputEnum, placequote.ConfigurationOptionsInput configurationOptionsInput)
Parameters
pricingPreferenceEnum
Type: placequote.PricingPreferenceEnum
Pricing preference during the quote process.
catalogRatesPreference
Type: placequote.CatalogRatesPreferenceEnum
The rate card entries defined in the catalog that must be fetched for quote line items, with usage-based pricing during the quote
creation process. The CatalogRatesPreferenceEnum  enum is available when the Usage-Based Selling feature is enabled.
graphRequest
Type: placequote.GraphRequest
The sObject graph values of the quote payload to be ingested.
1590
PlaceQuote NamespaceTransaction Management

===== PAGE 1605 =====

configurationInputEnum
Type: placequote.ConfigurationInputEnum
Configuration input for the quote process.
configurationOptionsInput
Type: placequote.ConfigurationOptionsInput
Configuration options during the ingestion process.
Return Value
Type: placequote.PlaceQuoteResponse
PlaceQuoteRLMApexProcessor Example Implementation
To place a quote from Apex, refer to the example implementation of the PlaceQuoteRLMApexProcessor  class.
Namespace
PlaceQuote
Usage
Customize this example to suit your requirements. Create the list of records to be ingested by using these steps. Replace the respective
IDs with the values that are present in your org. For example, replace the value of ${Pricebook2Id}  field with the price book ID
that’s present in the org.
Example:
• Set up a quote and quote line item. To associate the Record object with a reference identifier, create an instance of the
RecordWithReferenceRequest class.
//Quote Setup
PlaceQuote.RecordResource quoteRecord = new
PlaceQuote.RecordResource(Quote.getSobjectType(),'POST');
Map<String,Object> quoteFieldValues = new Map<String,Object>();
quoteFieldValues.put('Name','q-ap12');
quoteFieldValues.put('OpportunityId','006xx000001aBFcAAM');
quoteFieldValues.put('Pricebook2Id','01sxx0000005pvRAAQ');
quoteRecord.fieldValues = quoteFieldValues;
//Quote Line Item Setup
PlaceQuote.RecordResource quoteLineItemRecord1 = new
PlaceQuote.RecordResource(QuoteLineItem.getSobjectType(),'POST');
Map<String,Object> quoteLineItemFieldValues = new Map<String,Object>();
quoteLineItemFieldValues.put('Product2Id','01txx0000006ibwAAA');
quoteLineItemFieldValues.put('PricebookEntryId','01uxx0000008zPqAAI');
quoteLineItemFieldValues.put('Quantity','2.0');
quoteLineItemFieldValues.put('UnitPrice','5.0');
quoteLineItemFieldValues.put('StartDate','2023-03-15');
quoteLineItemFieldValues.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord1.fieldValues = quoteLineItemFieldValues;
PlaceQuote.RecordWithReferenceRequest quoteItemRecords = new
1591
PlaceQuote NamespaceTransaction Management

===== PAGE 1606 =====

PlaceQuote.RecordWithReferenceRequest('refQuote',quoteRecord);
PlaceQuote.RecordWithReferenceRequest quoteLineItemRecords1 = new
PlaceQuote.RecordWithReferenceRequest('refQuoteItem1',quoteLineItemRecord1);
• To create a quote line relationship, create an instance of the RecordResource class.
PlaceQuote.RecordResource quoteLineRelationship1 = new
PlaceQuote.RecordResource(QuoteLineRelationship.getSobjectType(),'POST');
Map<String,Object> quoteLineRelationshipValues = new Map<String,Object>();
quoteLineRelationshipValues.put('ProductRelationshipTypeId','0yoxx00000000JNAAY');
quoteLineRelationshipValues.put('MainQuoteLineId','@{refQuoteItem2.id}');
quoteLineRelationshipValues.put('AssociatedQuoteLineId','@{refQuoteItem1.id}');
quoteLineRelationshipValues.put('AssociatedQuoteLinePricing','IncludedInBundlePrice');
quoteLineRelationship1.fieldValues = quoteLineRelationshipValues;
• Create the list of records to be ingested.
PlaceQuote.RecordWithReferenceRequest quoteLineRelationship = new
PlaceQuote.RecordWithReferenceRequest('QuoteLineRelationship',quoteLineRelationship1);
List<PlaceQuote.RecordWithReferenceRequest> listOfRecords = new
List<PlaceQuote.RecordWithReferenceRequest>();
listOfRecords.add(quoteItemRecords);
listOfRecords.add(quoteLineItemRecords1);
listOfRecords.add(quoteLineItemRecords2);
listOfRecords.add(quoteLineRelationship);
• To contain all record objects, create an instance of the GraphRequest  class.
Note:  The CatalogRatesPreferenceEnum enum is available when the Usage-Based Selling feature is enabled.
PlaceQuote.GraphRequestgraph = new PlaceQuote.GraphRequest('test',listOfRecords);
PlaceQuote.ConfigurationOptionsInput cInput = new
PlaceQuote.ConfigurationOptionsInput();
PlaceQuote.CatalogRatesPreferenceEnum catalogRatesPreference =
PlaceQuote.CatalogRatesPreferenceEnum.Fetch;
....PlaceQuote.ConfigurationInputEnum configurationPreference =
PlaceQuote.ConfigurationInputEnum.RunAndAllowErrors;
PlaceQuote.PricingPreferenceEnum pricingPreference =
PlaceQuote.PricingPreferenceEnum.System;
//System.debug(graph);
//Place Quote Call
PlaceQuote.PlaceQuoteResponse resp =
PlaceQuote.PlaceQuoteRLMApexProcessor.execute(pricingPreference,
catalogRatesPreference, graph, configurationPreference, cInput);
System.debug(resp);
1592
PlaceQuote NamespaceTransaction Management

===== PAGE 1607 =====

PricingPreferenceEnum Enum
Specifies the pricing preference during the create quote process.
Usage
Used by the PlaceQuoteRLMApexProcessor class.
Enum Values
The placequote.PricingPreferenceEnum  enum class includes these values.
DescriptionValue
Enforce pricing during the quote ingestion process.Force
Skip pricing during the quote ingestion process.Skip
Determine whether a pricing calculation is required.System
RecordResource Class
Contains constructors and properties to create a record object from the field values of a quote.
Namespace
PlaceQuote
Example
PlaceQuote.RecordResource quoteLineRelationship1 = new
PlaceQuote.RecordResource(QuoteLineRelationship.getSobjectType(),'POST');
See PlaceQuoteRLMApexProcessor to refer to an example implementation.
RecordResource Constructors
Learn more about the available constructors with the RecordResource class.
RecordResource Properties
Learn more about the available properties with the RecordResource class.
RecordResource Constructors
Learn more about the available constructors with the RecordResource class.
The RecordResource  class includes these constructors.
RecordResource(type, method, id)
Creates an instance of the RecordResource class to assign values to the fields of a quote item by using the sObject type, API
method, and quote ID properties.
1593
PlaceQuote NamespaceTransaction Management

===== PAGE 1608 =====

RecordResource(type, method)
Creates an instance of the RecordResource class to assign the values to the fields of a quote item by using the sObject type
and API method properties.
RecordResource(type, method, id)
Creates an instance of the RecordResource class to assign values to the fields of a quote item by using the sObject type, API method,
and quote ID properties.
Signature
public RecordResource(Schema.SObjectType type, String method, Id id)
Parameters
type
Type: Schema.SObjectType
Object that’s returned from the field describe result using the getReferenceTo() method or from the sObject describe result
using the getSObjectType() method.
method
Type: String
Method for the API request, such as POST or PATCH.
id
Type: Id
ID of the quote.
RecordResource(type, method)
Creates an instance of the RecordResource class to assign the values to the fields of a quote item by using the sObject type and
API method properties.
Signature
public RecordResource(Schema.SObjectType type, String method)
Parameters
type
Type: Schema.SObjectType
Object that’s returned from the field describe result using the getReferenceTo() method or from the sObject describe result
using the getSObjectType() method.
method
Type: String
Method for the API request, such as POST or PATCH.
1594
PlaceQuote NamespaceTransaction Management

===== PAGE 1609 =====

RecordResource Properties
Learn more about the available properties with the RecordResource class.
The RecordResource  class includes these properties.
fieldValues
Set the fieldValues property to assign values to the fields to update the quote record.
id
Set the id property to assign the ID of the quote record.
method
Set the method property to specify the API request method, such as POST or PATCH.
type
Set the type property to assign the object type that’s returned from the field describe result by using
the getReferenceTo() method or from the sObject describe result by using the getSObjectType() method.
fieldValues
Set the fieldValues property to assign values to the fields to update the quote record.
Signature
public Map<String,ANY> fieldValues {get; set;}
Property Value
Type: List <Map<String,ANY>>
id
Set the id property to assign the ID of the quote record.
Signature
public String id {get; set;}
Property Value
Type: String
method
Set the method property to specify the API request method, such as POST or PATCH.
Signature
public String method {get; set;}
1595
PlaceQuote NamespaceTransaction Management

===== PAGE 1610 =====

Property Value
Type: String
type
Set the type property to assign the object type that’s returned from the field describe result by using the getReferenceTo() method
or from the sObject describe result by using the getSObjectType() method.
Signature
public Schema.SObjectType type {get; set;}
Property Value
Type: Schema.SObjectType
RecordWithReferenceRequest Class
Contains constructors and properties to associate a record object with a reference identifier.
Namespace
PlaceQuote
Example
PlaceQuote.RecordWithReferenceRequest quoteLineRelationship = new
PlaceQuote.RecordWithReferenceRequest('QuoteLineRelationship',quoteLineRelationship1);
See PlaceQuoteRLMApexProcessor to refer to an example implementation.
RecordWithReferenceRequest Constructors
Learn more about the available constructors with the RecordWithReferenceRequest class.
RecordWithReferenceRequest Properties
Learn more about the available properties with the RecordWithReferenceRequest class.
RecordWithReferenceRequest Constructors
Learn more about the available constructors with the RecordWithReferenceRequest class.
The RecordWithReferenceRequest  class includes these constructors.
RecordWithReferenceRequest(referenceId, record)
Creates an instance of the RecordWithReferenceRequest class to associate a record object with a reference identifier by
using the referenceId and record object properties.
1596
PlaceQuote NamespaceTransaction Management

===== PAGE 1611 =====

RecordWithReferenceRequest(referenceId, record)
Creates an instance of the RecordWithReferenceRequest class to associate a record object with a reference identifier by using
the referenceId and record object properties.
Signature
public RecordWithReferenceRequest(String referenceId, placequote.RecordResource record)
Parameters
referenceId
Type: String
Reference ID that maps to the subrequest response and can be used to reference the response in subsequent subrequests. You can
reference the referenceId in either the body or URL of a subrequest. Use this syntax to include a reference: @{referenceId.FieldName}.
See referenceId property of a composite subrequest.
record
Type: placequote.RecordResource
Record object that’s defined using the RecordResource class.
RecordWithReferenceRequest Properties
Learn more about the available properties with the RecordWithReferenceRequest class.
The RecordWithReferenceRequest  class includes these properties.
record
Set the record property to specify the record object that’s defined by using the RecordResource class.
referenceId
Set the referenceId property to specify the reference ID that maps to the subrequest response. This reference ID can be used
to reference the response in subsequent subrequests.
record
Set the record property to specify the record object that’s defined by using the RecordResource class.
Signature
public placequote.RecordResource record {get; set;}
Property Value
Type: placequote.RecordResource
referenceId
Set the referenceId property to specify the reference ID that maps to the subrequest response. This reference ID can be used to
reference the response in subsequent subrequests.
1597
PlaceQuote NamespaceTransaction Management

===== PAGE 1612 =====

Signature
public String referenceId {get; set;}
Property Value
Type: String
RevSalesTrxn Namespace
Create a sales transaction, such as a quote or an order, with integrated pricing and configuration. Additionally, update an order or a
quote, and insert and delete order or quote line items to calculate the estimated tax.
The RevSalesTrxn  namespace includes these classes.
CatalogRatesPreferenceEnum Enum
Specifies the rate card entries defined in the catalog that must be fetched for quote line items, with usage-based selling during the
place sales transaction process.
ConfigurationExecutionEnum Enum
Specifies the configuration method for the place sales transaction request.
ConfigurationOptionsInput Class
Contains methods and properties to set the configuration options for the input to the product configurator.
GraphRequest Class
Contains constructors and properties to set the graph ID and a list of records to be ingested. The list of records is specified in a
key-value map format that contains field values.
GroupRampActionEnum Enum
Specifies the action that you want to perform on group ramp segments. Additionally, you can also convert a non-ramped group
into a ramped group.
PersistPreferenceEnum Enum
Specifies whether to persist pricing changes for each sales transaction record. Available in API version 65.0 and later.
PlaceSalesTransactionException Class
Contains methods to hold the exception details for the place sales transaction request.
PlaceSalesTransactionExecutor Class
Contains methods to place a sales transaction with details of the graph request, pricing preferences, and configuration options.
PlaceSalesTransactionResponse Class
Contains properties to hold the response to the place sales transaction request.
PricingPreferenceEnum Enum
Specifies the pricing preference during the creation of a sales transaction.
RecordResource Class
Contains constructors and properties to create a record object from the field values of a sales transaction.
RecordWithReferenceRequest Class
Contains constructors and properties to associate a record object with a reference identifier.
TaxPreferenceEnum Enum
Specifies whether to execute or skip the tax calculation step for each sales transaction record. Available in API version 65.0 and later.
1598
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1613 =====

CatalogRatesPreferenceEnum Enum
Specifies the rate card entries defined in the catalog that must be fetched for quote line items, with usage-based selling during the place
sales transaction process.
Usage
This enum is available when Usage Selling is enabled.
Enum Values
The RevSalesTrxn.CatalogRatesPreferenceEnum  enum includes these values.
DescriptionValue
Retrieves the rate card entries defined in the catalog for quote line items during the
quote creation process.
Fetch
Skips the retrieval of rate card entries for quote line items during the quote creation
process. The default value is Skip.
Skip
ConfigurationExecutionEnum Enum
Specifies the configuration method for the place sales transaction request.
Usage
Use these enum values for the configurationExecutionEnum property in the PlaceSalesTransactionExecutor class.
Enum Values
The RevSalesTrxn.ConfigurationExecutionEnum  enum has these values.
DescriptionValue
Specifies to enforce the predefined configuration process during the sales transaction
process.
Force
Specifies to skip the configuration process during the quote creation process. The
default value is Skip.
Skip
Specifies the system to determine whether the configuration process is required.System
ConfigurationOptionsInput Class
Contains methods and properties to set the configuration options for the input to the product configurator.
Namespace
RevSalesTrxn
1599
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1614 =====

Usage
This class holds the required details of the product configuration input. Set the class properties to enable default configuration, execution
of configuration rules, and validation of the product catalog. Use these class properties as an input to
the PlaceSalesTransactionExecutor class method.
Example
RevSalesTrxn.GraphRequest graph = new RevSalesTrxn.GraphRequest('test',
listOfRecords);
RevSalesTrxn.PricingPreferenceEnum pricingPrefEnum =
RevSalesTrxn.PricingPreferenceEnum.SYSTEM;
RevSalesTrxn.ConfigurationExecutionEnum configurationExecutionEnum =
RevSalesTrxn.ConfigurationExecutionEnum.SYSTEM;
RevSalesTrxn.ConfigurationOptionsInput cInput = new
RevSalesTrxn.ConfigurationOptionsInput();
cInput.addDefaultConfiguration = true;
cInput.executeConfigurationRules = true;
cInput.validateAmendRenewCancel = true;
cInput.validateProductCatalog = true;
//Place Sales Transaction API Call
RevSalesTrxn.PlaceSalesTransactionResponse resp =
PlaceQuote.PlaceSalesTransactionExecutor.execute(graph,pricingPrefEnum,configurationExecutionEnum,cInput,null);
ConfigurationOptionsInput Properties
Set the ConfigurationOptionsInput class properties to add default configuration, execute configuration rules, and validate the product
catalog.
ConfigurationOptionsInput Methods
Learn more about the methods available with the ConfigurationOptionsInput class.
ConfigurationOptionsInput Properties
Set the ConfigurationOptionsInput class properties to add default configuration, execute configuration rules, and validate the product
catalog.
The ConfigurationOptionsInput  class includes these properties.
addDefaultConfiguration
Sets the default product configuration, such as bundle and product attributes, for a quote request.
executeConfigurationRules
Sets the requirement for a quote to adhere to the configuration rules.
validateAmendRenewCancel
Sets the requirement to run validations related to amend, renew, or cancel processes.
validateProductCatalog
Sets the requirement to validate a quote against the product catalog.
addDefaultConfiguration
Sets the default product configuration, such as bundle and product attributes, for a quote request.
1600
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1615 =====

Signature
public Boolean addDefaultConfiguration {get; set;}
Property Value
Type: Boolean
Indicates whether to automatically add default configuration to the order (true) or not (false).
executeConfigurationRules
Sets the requirement for a quote to adhere to the configuration rules.
Signature
public Boolean executeConfigurationRules {get; set;}
Property Value
Type: Boolean
Indicates whether the order must adhere to configuration rules during processing (true) or bypass them (false).
validateAmendRenewCancel
Sets the requirement to run validations related to amend, renew, or cancel processes.
Signature
public Boolean validateAmendRenewCancel {get; set;}
Property Value
Type: Boolean
Indicates whether to run validations related to amend, renew, or cancel processes (true) or not (false).
validateProductCatalog
Sets the requirement to validate a quote against the product catalog.
Signature
public Boolean validateProductCatalog {get; set;}
Property Value
Type: Boolean
Indicates whether the quote must be validated against the product catalog (true) or not (false).
1601
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1616 =====

ConfigurationOptionsInput Methods
Learn more about the methods available with the ConfigurationOptionsInput class.
The ConfigurationOptionsInput  class includes these methods.
equals(obj)
Determines the equality of external objects in a list. This method is dynamic and is based on the equals() method in Java.
hashCode()
Determines the uniqueness of the external object records in a list.
toString()
Converts a value to a string.
equals(obj)
Determines the equality of external objects in a list. This method is dynamic and is based on the equals() method in Java.
Signature
public Boolean equals(Object obj)
Parameters
obj
Type: Object
Reference object that’s used to compare with the class object.
Return Value
Type: Boolean
Indicates if the class object is same as the reference object (true) or not (false).
hashCode()
Determines the uniqueness of the external object records in a list.
Signature
public Integer hashCode()
Return Value
Type: Integer
Integer hash code that represents the value of the object. Equal objects as per the equals() method must return the same hash
code.
toString()
Converts a value to a string.
1602
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1617 =====

Signature
public String toString()
Return Value
Type: String
GraphRequest Class
Contains constructors and properties to set the graph ID and a list of records to be ingested. The list of records is specified in a key-value
map format that contains field values.
Namespace
RevSalesTrxn
GraphRequest Constructors
Learn more about the available constructors with the GraphRequest class.
GraphRequest Properties
Learn more about the available properties with the GraphRequest class.
GraphRequest Constructors
Learn more about the available constructors with the GraphRequest class.
The GraphRequest  class includes these constructors.
GraphRequest(graphId, records)
Creates an instance of the GraphRequest class to assign the graph ID and a list of records to be ingested.
GraphRequest(graphId, records)
Creates an instance of the GraphRequest class to assign the graph ID and a list of records to be ingested.
Signature
public GraphRequest(String graphId, List<RevSalesTrxn.RecordWithReferenceRequest>
records)
Parameters
graphId
Type: String
ID of the graph.
records
Type: List<revsalestrxn.RecordWithReferenceRequest on page 1623>
List of records to be ingested.
1603
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1618 =====

GraphRequest Properties
Learn more about the available properties with the GraphRequest class.
The GraphRequest  class includes these properties.
graphId
Set the graphId  property to assign the ID value of the graph.
graphId
Set the graphId  property to assign the ID value of the graph.
Signature
public String graphId {get; set;}
Property Value
Type: String
GroupRampActionEnum Enum
Specifies the action that you want to perform on group ramp segments. Additionally, you can also convert a non-ramped group into a
ramped group.
Enum Values
The RevSalesTrxn.GroupRampActionEnum  enum includes these values.
DescriptionValue
Specifies to add rampable products to group ramp segments.AddProducts
Specifies to delete ramped products.DeleteProducts
Specifies to convert a non-ramped group into a group ramp segment, or edit group
ramp segment attributes such as name and description, except the start and end
dates.
EditGroup
Specifies to edit details of the group ramp segments, including start and end dates.EditRampSchedule
Specifies to delete the first or last segment in a group ramp schedule.DeleteSegment
Specifies to convert the first or last group ramp segment into a non-ramped group.ConvertToNonRampedGroup
To add or delete ramped line items from multiple group ramp segments, pass all the applicable values in the graph  request. To refer
to Connect API examples that specify actions to create ramp deals for groups, see Group Ramp Action Input on page 1388.
PersistPreferenceEnum Enum
Specifies whether to persist pricing changes for each sales transaction record. Available in API version 65.0 and later.
1604
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1619 =====

Enum Values
The RevSalesTrxn.PersistPreferenceEnum  enum includes this value.
DescriptionValue
Skips the persistence of pricing changes for each sales transaction record. To persist
pricing changes, specify null  as the value in the method signature. If this value
isn't specified, then request to persist pricing changes is performed by default.
Skip
PlaceSalesTransactionException Class
Contains methods to hold the exception details for the place sales transaction request.
Namespace
RevSalesTrxn
PlaceSalesTransactionException Methods
Learn more about the methods available with the PlaceSalesTransactionException class.
PlaceSalesTransactionException Methods
Learn more about the methods available with the PlaceSalesTransactionException class.
The PlaceSalesTransactionException  class includes these methods.
getErrorCode()
Gets the error code that’s associated to the place sales transaction request.
getErrorCode()
Gets the error code that’s associated to the place sales transaction request.
Signature
public String getErrorCode()
Return Value
Type: String
PlaceSalesTransactionExecutor Class
Contains methods to place a sales transaction with details of the graph request, pricing preferences, and configuration options.
Namespace
RevSalesTrxn
1605
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1620 =====

PlaceSalesTransactionExecutor Methods
Learn more about the methods available with the PlaceSalesTransactionExecutor  class.
PlaceSalesTransactionExecutor Example Implementation
To place a sales transaction from Apex, refer to the example implementation of the PlaceSalesTransactionExecutor
class.
PlaceSalesTransactionExecutor Methods
Learn more about the methods available with the PlaceSalesTransactionExecutor  class.
The PlaceSalesTransactionExecutor  class includes these methods.
execute(graphRequest, pricingPreferenceEnum, configurationExecutionEnum, configuratorOptions, contextId)
Use the method in the PlaceSalesTransactionExecutor class to execute the Place Sales Transaction Apex API request
by assigning the properties for graph request, pricing references, and configurator options.
execute(graphRequest, pricingPreferenceEnum, configurationExecutionEnum, configuratorOptions, contextId,
catalogRatesPreferenceEnum)
Use the method in the PlaceSalesTransactionExecutor class to execute the Place Sales Transaction Apex API request
by assigning the properties for graph request, pricing references, configurator options, and catalog rates.
execute(graphRequest, pricingPreferenceEnum, configurationExecutionEnum, configuratorOptions, contextId,
catalogRatesPreferenceEnum, taxPreferenceEnum, persistPreferenceEnum)
Use the method in the PlaceSalesTransactionExecutor class to execute the Place Sales Transaction Apex API request
by assigning the properties for graph request, pricing and tax preferences, configurator options, and catalog rates.
execute(graphRequest, pricingPreferenceEnum, configurationExecutionEnum,
configuratorOptions, contextId)
Use the method in the PlaceSalesTransactionExecutor class to execute the Place Sales Transaction Apex API request by
assigning the properties for graph request, pricing references, and configurator options.
Signature
public static revsalestrxn.PlaceSalesTransactionResponse
execute(revsalestrxn.GraphRequest graphRequest, revsalestrxn.PricingPreferenceEnum
pricingPreferenceEnum, revsalestrxn.ConfigurationExecutionEnum
configurationExecutionEnum, revsalestrxn.ConfiguratorOptions configuratorOptions,
revsalestrxn.ContextId contextId)
Parameters
graphRequest
Type: revsalestrxn.GraphRequest
The sObject graph values of the order payload to be ingested.
pricingPreferenceEnum
Type: revsalestrxn.PricingPreferenceEnum
Pricing preference during the sales transaction process.
1606
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1621 =====

configurationExecutionEnum
Type: revsalestrxn.ConfigurationExecutionEnum
Configuration method for the sales transaction request.
configuratorOptions
Type: revsalestrxn.ConfigurationOptionsInput
Configuration options during the creation of the sales transaction.
contextId
Type: String
Context ID to assign to the sales transaction.
Return Value
Type: revsalestrxn.PlaceSalesTransactionResponse
execute(graphRequest, pricingPreferenceEnum, configurationExecutionEnum,
configuratorOptions, contextId, catalogRatesPreferenceEnum)
Use the method in the PlaceSalesTransactionExecutor class to execute the Place Sales Transaction Apex API request by
assigning the properties for graph request, pricing references, configurator options, and catalog rates.
Signature
Usage Selling must be enabled to use this signature.
public static revsalestrxn.PlaceSalesTransactionResponse
execute(revsalestrxn.GraphRequest graphRequest, revsalestrxn.PricingPreferenceEnum
pricingPreferenceEnum, revsalestrxn.ConfigurationExecutionEnum
configurationExecutionEnum, revsalestrxn.ConfiguratorOptions configuratorOptions,
revsalestrxn.ContextId contextId, revsalestrxn.CatalogRatesPreferenceEnum
catalogRatesPreferenceEnum)
Parameters
graphRequest
Type: revsalestrxn.GraphRequest
The sObject graph values of the order payload to be ingested.
pricingPreferenceEnum
Type: revsalestrxn.PricingPreferenceEnum
Pricing preference during the sales transaction process.
configurationExecutionEnum
Type: revsalestrxn.ConfigurationExecutionEnum
Configuration method for the sales transaction request.
configuratorOptions
Type: revsalestrxn.ConfigurationOptionsInput
Configuration options during the creation of the sales transaction.
1607
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1622 =====

contextId
Type: String
Context ID to assign to the sales transaction.
catalogRatesPreferenceEnum
Type: revsalestrxn.CatalogRatesPreferenceEnum
Rate card entries defined in the catalog that must be fetched for quote line items, with usage-based selling during the place sales
transaction process.
Return Value
Type: revsalestrxn.PlaceSalesTransactionResponse
execute(graphRequest, pricingPreferenceEnum, configurationExecutionEnum,
configuratorOptions, contextId, catalogRatesPreferenceEnum, taxPreferenceEnum,
persistPreferenceEnum)
Use the method in the PlaceSalesTransactionExecutor class to execute the Place Sales Transaction Apex API request by
assigning the properties for graph request, pricing and tax preferences, configurator options, and catalog rates.
Signature
Usage Selling must be enabled to use this signature.
public static revsalestrxn.PlaceSalesTransactionResponse
execute(revsalestrxn.GraphRequest graphRequest, revsalestrxn.PricingPreferenceEnum
pricingPreferenceEnum, revsalestrxn.ConfigurationExecutionEnum
configurationExecutionEnum, revsalestrxn.ConfiguratorOptions configuratorOptions,
revsalestrxn.ContextId contextId, revsalestrxn.CatalogRatesPreferenceEnum
catalogRatesPreferenceEnum, revsalestrxn.TaxPreferenceEnum taxPreferenceEnum,
revsalestrxn.PersistPreferenceEnum persistPreferenceEnum)
Parameters
graphRequest
Type: revsalestrxn.GraphRequest
The sObject graph values of the order payload to be ingested.
pricingPreferenceEnum
Type: revsalestrxn.PricingPreferenceEnum
Pricing preference during the sales transaction process.
configurationExecutionEnum
Type: revsalestrxn.ConfigurationExecutionEnum
Configuration method for the sales transaction request.
configuratorOptions
Type: revsalestrxn.ConfigurationOptionsInput
Configuration options during the creation of the sales transaction.
1608
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1623 =====

contextId
Type: String
Context ID to assign to the sales transaction.
catalogRatesPreferenceEnum
Type: revsalestrxn.CatalogRatesPreferenceEnum
Rate card entries defined in the catalog that must be fetched for quote line items, with usage-based selling during the place sales
transaction process.
taxPreferenceEnum
Type: revsalestrxn.taxPreferenceEnum
Tax preference during the sales transaction process. Available in API version 65.0 and later.
persistPreferenceEnum
Type: revsalestrxn.persistPreferenceEnum
Persist preference during the sales transaction process. Available in API version 65.0 and later.
Return Value
Type: revsalestrxn.PlaceSalesTransactionResponse
PlaceSalesTransactionExecutor Example Implementation
To place a sales transaction from Apex, refer to the example implementation of the PlaceSalesTransactionExecutor  class.
Namespace
RevSalesTrxn
Usage
Customize this example to suit your requirements. Create the list of records to be ingested by using these steps. Replace the respective
IDs with the values that are present in your org. For example, replace the value of ${Pricebook2Id}  field with the price book ID
that’s present in the org.
Example: This example shows a sample request to create a sales transaction, update a quote with a quote line item, delete a
quote line item, or skip or persist pricing changes. It includes these steps.
• Set up a quote and quote line item.
• To create a quote line relationship, create an instance of the RecordResource  class. To create an object with its fields,
specify the object that you want to create by using POST method. Create a map of the fields and its values by using put(key,
value) operation. Assign this field map to the record object.
• To update an object's specific fields, specify the object you want to update by using the PATCH method along with the ID of
the object. Create a map of the fields and its values by using put(key, value) operation. Only certain fields on an object can be
updated. Add the fields that you want to update to the map. Assign this field map to the record object.
• To associate the Record object with a reference identifier, create an instance of the RecordWithReferenceRequest
class.
1609
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1624 =====

• To contain all record objects, create an instance of the GraphRequest  class.
public class PlaceSalesTransactionTest {
public static void callPSTAPI_Post() {
RevSalesTrxn.PricingPreferenceEnum pricingPrefEnum =
RevSalesTrxn.PricingPreferenceEnum.SYSTEM;
RevSalesTrxn.ConfigurationExecutionEnum configurationExecutionEnum =
RevSalesTrxn.ConfigurationExecutionEnum.SYSTEM;
//Quote setup
RevSalesTrxn.RecordResource quoteRecord = new
RevSalesTrxn.RecordResource(Quote.getSobjectType(),'POST');
Map<String,Object> quoteFieldValues = new Map<String,Object>();
quoteFieldValues.put('Name','q-ap12');
quoteFieldValues.put('OpportunityId','006xx000001a3e8AAA');
quoteFieldValues.put('Pricebook2Id','01sDU000000JRX8YAO');
quoteRecord.fieldValues = quoteFieldValues;
//Quote line item setup
//1st quote line item
RevSalesTrxn.RecordResource quoteLineItemRecord1 = new
RevSalesTrxn.RecordResource(QuoteLineItem.getSobjectType(),'POST');
Map<String,Object> quoteLineItemFieldValues = new Map<String,Object>();
quoteLineItemFieldValues.put('Product2Id','01txx0000006i7JAAQ');
quoteLineItemFieldValues.put('PricebookEntryId','01uxx0000008yc6AAA');
quoteLineItemFieldValues.put('Quantity','2.0');
quoteLineItemFieldValues.put('UnitPrice','1000');
quoteLineItemFieldValues.put('StartDate','2025-03-15');
quoteLineItemFieldValues.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord1.fieldValues = quoteLineItemFieldValues;
RevSalesTrxn.RecordWithReferenceRequest quoteItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuote',quoteRecord);
RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords1 = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem1',quoteLineItemRecord1);
//2nd quote line item
RevSalesTrxn.RecordResource quoteLineItemRecord2 = new
RevSalesTrxn.RecordResource(QuoteLineItem.getSobjectType(),'POST');
Map<String,Object> quoteLineItemFieldValues2 = new Map<String,Object>();
quoteLineItemFieldValues2.put('Product2Id','01txx0000006i7RAAQ');
quoteLineItemFieldValues2.put('PricebookEntryId','01uxx0000008ybvAAA');
quoteLineItemFieldValues2.put('Quantity','2.0');
quoteLineItemFieldValues2.put('UnitPrice','7.0');
quoteLineItemFieldValues2.put('StartDate','2025-03-15');
quoteLineItemFieldValues2.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord2.fieldValues = quoteLineItemFieldValues2;
RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords2 = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem2',quoteLineItemRecord2);
List<RevSalesTrxn.RecordWithReferenceRequest> listOfRecords = new
List<RevSalesTrxn.RecordWithReferenceRequest>();
listOfRecords.add(quoteItemRecords);
listOfRecords.add(quoteLineItemRecords1);
listOfRecords.add(quoteLineItemRecords2);
1610
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1625 =====

RevSalesTrxn.GraphRequest graph = new
RevSalesTrxn.GraphRequest('test',listOfRecords);
System.debug(graph);
//Place sales transaction API call - There are different executor signatures
detailed in the documentation
RevSalesTrxn.PlaceSalesTransactionResponse resp =
RevSalesTrxn.PlaceSalesTransactionExecutor.execute(graph, pricingPrefEnum,
configurationExecutionEnum, new RevSalesTrxn.ConfigurationOptionsInput(), null, null,
null, null);
//If you do not have Usage Based Selling Feature, you can use the signatures
without catalog rates enum
//RevSalesTrxn.PlaceSalesTransactionResponse resp =
RevSalesTrxn.PlaceSalesTransactionExecutor.execute(graph, pricingPrefEnum,
configurationExecutionEnum, new RevSalesTrxn.ConfigurationOptionsInput(), null);
System.debug(resp);
}
public static void callPSTAPI_Post_Skip_Tax_Skip_Persist() {
RevSalesTrxn.PricingPreferenceEnum pricingPrefEnum =
RevSalesTrxn.PricingPreferenceEnum.SYSTEM;
RevSalesTrxn.ConfigurationExecutionEnum configurationExecutionEnum =
RevSalesTrxn.ConfigurationExecutionEnum.SYSTEM;
RevSalesTrxn.TaxPreferenceEnumtaxPrefEnum = RevSalesTrxn.TaxPreferenceEnum.SKIP;
RevSalesTrxn.PersistPreferenceEnum persistPrefEnum =
RevSalesTrxn.PersistPreferenceEnum.SKIP;
//Quote setup
RevSalesTrxn.RecordResource quoteRecord = new
RevSalesTrxn.RecordResource(Quote.getSobjectType(),'POST');
Map<String,Object> quoteFieldValues = new Map<String,Object>();
quoteFieldValues.put('Name','q-ap12');
quoteFieldValues.put('OpportunityId','006xx000001a3e8AAA');
quoteFieldValues.put('Pricebook2Id','01sDU000000JRX8YAO');
quoteRecord.fieldValues = quoteFieldValues;
//Quote line item setup
//1st quote line item
RevSalesTrxn.RecordResource quoteLineItemRecord1 = new
RevSalesTrxn.RecordResource(QuoteLineItem.getSobjectType(),'POST');
Map<String,Object> quoteLineItemFieldValues = new Map<String,Object>();
quoteLineItemFieldValues.put('Product2Id','01txx0000006i7JAAQ');
quoteLineItemFieldValues.put('PricebookEntryId','01uxx0000008yc6AAA');
quoteLineItemFieldValues.put('Quantity','2.0');
quoteLineItemFieldValues.put('UnitPrice','1000');
quoteLineItemFieldValues.put('StartDate','2025-03-15');
quoteLineItemFieldValues.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord1.fieldValues = quoteLineItemFieldValues;
RevSalesTrxn.RecordWithReferenceRequest quoteItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuote',quoteRecord);
1611
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1626 =====

RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords1 = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem1',quoteLineItemRecord1);
//2nd quote line item
RevSalesTrxn.RecordResource quoteLineItemRecord2 = new
RevSalesTrxn.RecordResource(QuoteLineItem.getSobjectType(),'POST');
Map<String,Object> quoteLineItemFieldValues2 = new Map<String,Object>();
quoteLineItemFieldValues2.put('Product2Id','01txx0000006i7RAAQ');
quoteLineItemFieldValues2.put('PricebookEntryId','01uxx0000008ybvAAA');
quoteLineItemFieldValues2.put('Quantity','2.0');
quoteLineItemFieldValues2.put('UnitPrice','7.0');
quoteLineItemFieldValues2.put('StartDate','2025-03-15');
quoteLineItemFieldValues2.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord2.fieldValues = quoteLineItemFieldValues2;
RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords2 = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem2',quoteLineItemRecord2);
List<RevSalesTrxn.RecordWithReferenceRequest> listOfRecords = new
List<RevSalesTrxn.RecordWithReferenceRequest>();
listOfRecords.add(quoteItemRecords);
listOfRecords.add(quoteLineItemRecords1);
listOfRecords.add(quoteLineItemRecords2);
RevSalesTrxn.GraphRequest graph = new
RevSalesTrxn.GraphRequest('test',listOfRecords);
System.debug(graph);
//Place sales transaction API call
RevSalesTrxn.PlaceSalesTransactionResponse resp =
RevSalesTrxn.PlaceSalesTransactionExecutor.execute(graph, pricingPrefEnum,
configurationExecutionEnum, new RevSalesTrxn.ConfigurationOptionsInput(), null, null,
taxPrefEnum, persistPrefEnum);
System.debug(resp);
}
public static void callPSTAPI_Patch() {
// Apex test to update a quote with a quote line item
RevSalesTrxn.PricingPreferenceEnum pricingPrefEnum =
RevSalesTrxn.PricingPreferenceEnum.SYSTEM;
RevSalesTrxn.ConfigurationExecutionEnum configurationExecutionEnum =
RevSalesTrxn.ConfigurationExecutionEnum.SYSTEM;
//Quote setup
RevSalesTrxn.RecordResource quoteRecord = new
RevSalesTrxn.RecordResource(Quote.getSobjectType(),'PATCH','0Q0xx0000004CYsCAM');
RevSalesTrxn.RecordWithReferenceRequest quoteItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuote',quoteRecord);
//Quote line item setup
//New quote line item
RevSalesTrxn.RecordResource quoteLineItemRecord = new
RevSalesTrxn.RecordResource(QuoteLineItem.getSobjectType(),'POST');
1612
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1627 =====

Map<String,Object> quoteLineItemFieldValues = new Map<String,Object>();
quoteLineItemFieldValues.put('Product2Id','01txx0000006i7KAAQ');
quoteLineItemFieldValues.put('PricebookEntryId','01uxx0000008ycFAAQ');
quoteLineItemFieldValues.put('Quantity','2.0');
quoteLineItemFieldValues.put('UnitPrice','7.0');
quoteLineItemFieldValues.put('StartDate','2025-03-15');
quoteLineItemFieldValues.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord.fieldValues = quoteLineItemFieldValues;
RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem',quoteLineItemRecord);
List<RevSalesTrxn.RecordWithReferenceRequest> listOfRecords = new
List<RevSalesTrxn.RecordWithReferenceRequest>();
listOfRecords.add(quoteItemRecords);
listOfRecords.add(quoteLineItemRecords);
RevSalesTrxn.GraphRequest graph = new RevSalesTrxn.GraphRequest('test',
listOfRecords);
//Place sales transaction API call
RevSalesTrxn.PlaceSalesTransactionResponse resp =
RevSalesTrxn.PlaceSalesTransactionExecutor.execute(graph, pricingPrefEnum,
configurationExecutionEnum, new RevSalesTrxn.ConfigurationOptionsInput(), null, null,
null, null);
System.debug(resp);
}
public static void callPSTAPI_Patch_Skip_Config_Skip_Pricing() {
// Apex test to update a quote with a quote line item
RevSalesTrxn.PricingPreferenceEnum pricingPrefEnum =
RevSalesTrxn.PricingPreferenceEnum.SKIP;
RevSalesTrxn.ConfigurationExecutionEnum configurationExecutionEnum =
RevSalesTrxn.ConfigurationExecutionEnum.SKIP;
//Quote setup
RevSalesTrxn.RecordResource quoteRecord = new
RevSalesTrxn.RecordResource(Quote.getSobjectType(),'PATCH','0Q0xx0000004CYsCAM');
RevSalesTrxn.RecordWithReferenceRequest quoteItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuote',quoteRecord);
//Quote line item setup
//New quote line item
RevSalesTrxn.RecordResource quoteLineItemRecord = new
RevSalesTrxn.RecordResource(QuoteLineItem.getSobjectType(),'POST');
Map<String,Object> quoteLineItemFieldValues = new Map<String,Object>();
quoteLineItemFieldValues.put('Product2Id','01txx0000006i7KAAQ');
quoteLineItemFieldValues.put('PricebookEntryId','01uxx0000008ycFAAQ');
quoteLineItemFieldValues.put('Quantity','2.0');
quoteLineItemFieldValues.put('UnitPrice','7.0');
quoteLineItemFieldValues.put('StartDate','2025-03-15');
quoteLineItemFieldValues.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord.fieldValues = quoteLineItemFieldValues;
RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem',quoteLineItemRecord);
List<RevSalesTrxn.RecordWithReferenceRequest> listOfRecords = new
1613
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1628 =====

List<RevSalesTrxn.RecordWithReferenceRequest>();
listOfRecords.add(quoteItemRecords);
listOfRecords.add(quoteLineItemRecords);
RevSalesTrxn.GraphRequest graph = new RevSalesTrxn.GraphRequest('test',
listOfRecords);
//Place sales transaction API call
RevSalesTrxn.PlaceSalesTransactionResponse resp =
RevSalesTrxn.PlaceSalesTransactionExecutor.execute(graph, pricingPrefEnum,
configurationExecutionEnum, new RevSalesTrxn.ConfigurationOptionsInput(), null, null,
null, null);
System.debug(resp);
}
public static void callPSTAPI_Patch_With_ContextId() {
// Apex test to update a quote with a quote line item
RevSalesTrxn.PricingPreferenceEnum pricingPrefEnum =
RevSalesTrxn.PricingPreferenceEnum.SYSTEM;
RevSalesTrxn.ConfigurationExecutionEnum configurationExecutionEnum =
RevSalesTrxn.ConfigurationExecutionEnum.SYSTEM;
//Quote setup
String contextId = 'MY_CONTEXT_ID';
RevSalesTrxn.RecordResource quoteRecord = new
RevSalesTrxn.RecordResource(Quote.getSobjectType(),'PATCH','0Q0xx0000004CYsCAM');
RevSalesTrxn.RecordWithReferenceRequest quoteItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuote',quoteRecord);
//Quote line item setup
//New quote line item
RevSalesTrxn.RecordResource quoteLineItemRecord = new
RevSalesTrxn.RecordResource(QuoteLineItem.getSobjectType(),'POST');
Map<String,Object> quoteLineItemFieldValues = new Map<String,Object>();
quoteLineItemFieldValues.put('Product2Id','01txx0000006i7KAAQ');
quoteLineItemFieldValues.put('PricebookEntryId','01uxx0000008ycFAAQ');
quoteLineItemFieldValues.put('Quantity','2.0');
quoteLineItemFieldValues.put('UnitPrice','7.0');
quoteLineItemFieldValues.put('StartDate','2025-03-15');
quoteLineItemFieldValues.put('QuoteId','@{refQuote.id}');
quoteLineItemRecord.fieldValues = quoteLineItemFieldValues;
RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem',quoteLineItemRecord);
List<RevSalesTrxn.RecordWithReferenceRequest> listOfRecords = new
List<RevSalesTrxn.RecordWithReferenceRequest>();
listOfRecords.add(quoteItemRecords);
listOfRecords.add(quoteLineItemRecords);
RevSalesTrxn.GraphRequest graph = new RevSalesTrxn.GraphRequest('test',
listOfRecords);
//Place sales transaction API call
RevSalesTrxn.PlaceSalesTransactionResponse resp =
RevSalesTrxn.PlaceSalesTransactionExecutor.execute(graph, pricingPrefEnum,
configurationExecutionEnum, new RevSalesTrxn.ConfigurationOptionsInput(), contextId,
1614
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1629 =====

null, null, null);
System.debug(resp);
}
public static void callPSTAPI_Delete() {
// Apex test to update a quote with a quote line item
RevSalesTrxn.PricingPreferenceEnum pricingPrefEnum =
RevSalesTrxn.PricingPreferenceEnum.SYSTEM;
RevSalesTrxn.ConfigurationExecutionEnum configurationExecutionEnum =
RevSalesTrxn.ConfigurationExecutionEnum.SYSTEM;
//Quote setup
RevSalesTrxn.RecordResource quoteRecord = new
RevSalesTrxn.RecordResource(Quote.getSobjectType(),'PATCH','0Q0xx0000004CYsCAM');
RevSalesTrxn.RecordWithReferenceRequest quoteItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuote',quoteRecord);
//Quote line item setup
//Delete a quote line item
RevSalesTrxn.RecordResource quoteLineItemRecord = new
RevSalesTrxn.RecordResource(QuoteLineItem.getSobjectType(),'DELETE','0QLxx0000004CYsCAM');
RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem',quoteLineItemRecord);
List<RevSalesTrxn.RecordWithReferenceRequest> listOfRecords = new
List<RevSalesTrxn.RecordWithReferenceRequest>();
listOfRecords.add(quoteItemRecords);
listOfRecords.add(quoteLineItemRecords);
RevSalesTrxn.GraphRequest graph = new
RevSalesTrxn.GraphRequest('test',listOfRecords);
//Place sales transaction API call
RevSalesTrxn.PlaceSalesTransactionResponse resp =
RevSalesTrxn.PlaceSalesTransactionExecutor.execute(graph, pricingPrefEnum,
configurationExecutionEnum, new RevSalesTrxn.ConfigurationOptionsInput(), null,null,
null, null);
System.debug(resp);
}
}
PlaceSalesTransactionResponse Class
Contains properties to hold the response to the place sales transaction request.
Namespace
RevSalesTrxn
1615
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1630 =====

Example
RevSalesTrxn.PlaceSalesTransactionResponse resp =
RevSalesTrxn.PlaceSalesTransactionExecutor.execute(graph, pricingPrefEnum,
configurationExecutionEnum, new RevSalesTrxn.ConfigurationOptionsInput(), null);
PlaceSalesTransactionResponse Properties
Learn more about the available properties with the PlaceSalesTransactionResponse class.
PlaceSalesTransactionResponse Properties
Learn more about the available properties with the PlaceSalesTransactionResponse class.
The PlaceSalesTransactionResponse  class includes these properties.
contextDetails
Get the details of the context that’s created for the sales transaction.
errorResponse
Get the list of errors encountered during the synchronous processing of the API request.
isSuccess
Get the request status of the synchronous part of the processing.
salesTransactionId
Get the ID of the sales transaction, such as a quote or an order.
statusUrl
Get the asynchronous status URL of the request, if available.
trackerId
Get the unique identifier assigned to a specific operation or request that's used for tracking and referencing the operation.
contextDetails
Get the details of the context that’s created for the sales transaction.
Signature
public ConnectApi.ContextDetails contextDetails {get; set;}
Property Value
Type: ConnectApi.ContextDetails
errorResponse
Get the list of errors encountered during the synchronous processing of the API request.
Signature
public List<ConnectApi.PlaceSalesTransactionErrorResponse> errorResponse {get; set;}
1616
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1631 =====

Property Value
Type: List<ConnectApi.PlaceSalesTransactionErrorResponse>
isSuccess
Get the request status of the synchronous part of the processing.
Signature
public Boolean isSuccess {get; set;}
Property Value
Type: Boolean
Indicates whether the synchronous part of the processing is successful (true) or not (false).
salesTransactionId
Get the ID of the sales transaction, such as a quote or an order.
Signature
public String salesTransactionId {get; set;}
Property Value
Type: String
statusUrl
Get the asynchronous status URL of the request, if available.
Signature
public String statusUrl {get; set;}
Property Value
Type: String
trackerId
Get the unique identifier assigned to a specific operation or request that's used for tracking and referencing the operation.
Signature
public String trackerId {get; set;}
1617
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1632 =====

Property Value
Type: String
PricingPreferenceEnum Enum
Specifies the pricing preference during the creation of a sales transaction.
Usage
Used by the PlaceSalesTransactionExecutor class.
Enum Values
The RevSalesTrxn.PricingPreferenceEnum  enum includes these values.
DescriptionValue
Specifies to enforce pricing during the creation of sales transactions.Force
Specifies to skip pricing during the creation of sales transactions.Skip
Specifies the system to determine whether a pricing calculation is required. The
default value is System.
System
RecordResource Class
Contains constructors and properties to create a record object from the field values of a sales transaction.
Namespace
RevSalesTrxn
Example
RevSalesTrxn.RecordResource quoteRecord = new
RevSalesTrxn.RecordResource(Quote.getSobjectType(),'POST');
RecordResource Constructors
Learn more about the available constructors with the RecordResource class.
RecordResource Properties
Learn more about the available properties with the RecordResource class.
RecordResource Constructors
Learn more about the available constructors with the RecordResource class.
The RecordResource  class has these constructors.
1618
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1633 =====

RecordResource(type, method, groupAction, criteria)
Creates an instance of the RecordResource class to assign values to the fields of a sales transaction by using the sObject type, API
method, and sales transaction ID properties. Additionally, you can group order or quote line items based on a criteria by using the
groupAction and criteria properties.
RecordResource(type, method, id)
Creates an instance of the RecordResource class to assign values to the fields of a sales transaction by using the sObject type, API
method, and sales transaction ID properties.
RecordResource(type, method)
Creates an instance of the RecordResource class to assign the values to the fields of a sales transaction by using the sObject type
and API method properties.
RecordResource(type, method, groupAction, criteria)
Creates an instance of the RecordResource class to assign values to the fields of a sales transaction by using the sObject type, API method,
and sales transaction ID properties. Additionally, you can group order or quote line items based on a criteria by using the groupAction
and criteria properties.
Signature
public RecordResource(Schema.SObjectType type, String method, String groupAction,
Map<String,ANY> criteria)
Parameters
type
Type: Schema.SObjectType
Object that’s returned from the field describe result using the getReferenceTo() method or from the sObject describe result
using the getSObjectType() method.
method
Type: String
Method for the API request, such as POST, PATCH, or DELETE.
groupAction
Type: String
Action to group order or quote line items. Valid values are:
• GroupBy
• Group
• Ungroup
• GroupAll
• DeleteGroup
criteria
Type: Map<String,ANY>
Criteria to group order or quote line items. For example, group order or quote line items based on a monthly billing frequency.
1619
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1634 =====

RecordResource(type, method, id)
Creates an instance of the RecordResource class to assign values to the fields of a sales transaction by using the sObject type, API method,
and sales transaction ID properties.
Signature
public RecordResource(Schema.SObjectType type, String method, Id id)
Parameters
type
Type: Schema.SObjectType
Object that’s returned from the field describe result using the getReferenceTo() method or from the sObject describe result
using the getSObjectType() method.
method
Type: String
Method for the API request, such as POST, PATCH, or DELETE.
id
Type: Id
ID of the sales transaction, such as a quote or an order.
RecordResource(type, method)
Creates an instance of the RecordResource class to assign the values to the fields of a sales transaction by using the sObject type and
API method properties.
Signature
public RecordResource(Schema.SObjectType type, String method)
Parameters
type
Type: Schema.SObjectType
Object that’s returned from the field describe result using the getReferenceTo() method or from the sObject describe result
using the getSObjectType()method.
method
Type: String
Method for the API request, such as POST, PATCH, or DELETE.
RecordResource Properties
Learn more about the available properties with the RecordResource class.
The RecordResource  class includes these properties.
1620
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1635 =====

criteria
Set the criteria property to group order or quote line items. For example, group order or quote line items based on a monthly billing
frequency.
fieldValues
Set the fieldValues property to assign values to the fields to update the sales transaction.
groupAction
Set the groupAction property to group order or quote line items.
id
Set the id property to assign the ID of the sales transaction record.
method
Set the method property to specify the API request method, such as POST, PATCH, or DELETE.
type
Set the type property to assign the object type that’s returned from the field describe result by using the getReferenceTo() method
or from the sObject describe result by using the getSObjectType() method.
criteria
Set the criteria property to group order or quote line items. For example, group order or quote line items based on a monthly billing
frequency.
Signature
public Map<String,ANY> criteria {get; set;}
Property Value
Type: Map<String,ANY>
fieldValues
Set the fieldValues property to assign values to the fields to update the sales transaction.
Signature
public Map<String,ANY> fieldValues {get; set;}
Property Value
Type: ListMap<String,ANY>
groupAction
Set the groupAction property to group order or quote line items.
You can group order or quote line items based on location, work types, or departments, if groups are enabled for your org. Groups
provide a visualization of the products to view large quotes.
1621
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1636 =====

Signature
public String groupAction {get; set;}
Property Value
Type: String
Valid values are:
• GroupBy
• Group
• Ungroup
• GroupAll
• DeleteGroup
id
Set the id property to assign the ID of the sales transaction record.
Signature
public String id {get; set;}
Property Value
Type: String
method
Set the method property to specify the API request method, such as POST, PATCH, or DELETE.
Signature
public String method {get; set;}
Property Value
Type: String
type
Set the type property to assign the object type that’s returned from the field describe result by using the getReferenceTo() method or
from the sObject describe result by using the getSObjectType() method.
Signature
public Schema.SObjectType type {get; set;}
Property Value
Type: Schema.SObjectType
1622
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1637 =====

RecordWithReferenceRequest Class
Contains constructors and properties to associate a record object with a reference identifier.
Namespace
RevSalesTrxn
Example
RevSalesTrxn.RecordWithReferenceRequest quoteLineItemRecords = new
RevSalesTrxn.RecordWithReferenceRequest('refQuoteItem',quoteLineItemRecord);
RecordWithReferenceRequest Constructors
Learn more about the available constructors with the RecordWithReferenceRequest class.
RecordWithReferenceRequest Properties
Learn more about the available properties with the RecordWithReferenceRequest class.
RecordWithReferenceRequest Constructors
Learn more about the available constructors with the RecordWithReferenceRequest class.
The RecordWithReferenceRequest  class includes these constructors.
RecordWithReferenceRequest(referenceId, record)
Creates an instance of the RecordWithReferenceRequest class to associate a record object with a reference identifier by using the
referenceId and record object properties.
RecordWithReferenceRequest(referenceId, record)
Creates an instance of the RecordWithReferenceRequest class to associate a record object with a reference identifier by using the
referenceId and record object properties.
Signature
public RecordWithReferenceRequest(String referenceId, RevSalesTrxn.RecordResource
record)
Parameters
referenceId
Type: String
Reference ID that maps to the subrequest response and can be used to reference the response in subsequent subrequests. You can
reference the referenceId in either the body or URL of a subrequest. Use this syntax to include a reference: @{referenceId.FieldName}.
See referenceId property of a composite subrequest.
record
Type: RevSalesTrxn.RecordResource
Record object that’s defined using the RecordResource class.
1623
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1638 =====

RecordWithReferenceRequest Properties
Learn more about the available properties with the RecordWithReferenceRequest class.
The RecordWithReferenceRequest  class has these properties.
record
Set the record property to specify the record object that’s defined by using the RecordResource class.
referenceId
Set the referenceId property to specify the reference ID that maps to the subrequest response. This reference ID can be used to
reference the response in subsequent subrequests.
record
Set the record property to specify the record object that’s defined by using the RecordResource class.
Signature
public RevSalesTrxn.RecordResource record {get; set;}
Property Value
Type: RevSalesTrxn.RecordResource
referenceId
Set the referenceId property to specify the reference ID that maps to the subrequest response. This reference ID can be used to reference
the response in subsequent subrequests.
Signature
public String referenceId {get; set;}
Property Value
Type: String
TaxPreferenceEnum Enum
Specifies whether to execute or skip the tax calculation step for each sales transaction record. Available in API version 65.0 and later.
Enum Values
The RevSalesTrxn.TaxPreferenceEnum  enum includes this value.
DescriptionValue
Specifies to skip tax calculation request for each sales transaction record. If this value
isn't specified, then tax calculation request is performed by default.
Skip
1624
RevSalesTrxn NamespaceTransaction Management

===== PAGE 1639 =====

Transaction Management Standard Invocable Actions
Learn more about the standard invocable actions available with Transaction Management.
Create Contract Action
Create a contract from a specific quote record.
Create or Update Asset From Order Action
Create an asset for each order item in the specified order. New assets are created for a new order. Modify existing assets for change
order requests, such as a renewal or a cancellation.
Create or Update Asset From Order Item Action
Create assets from individual order items within an order. Track assets after the individual line items of an order reach a certain stage
in their lifecycle, such as submitted, fulfilled, or provisioned. If the order item is part of a renewal, an amendment, or a cancellation,
existing assets are changed.
Create Order From Quote Action
Create an order from a quote record.
Create Orders From Quote Action
Create multiple orders from a single quote instead of a single order, ensuring easier order management and fulfillment operations.
Get Renewable Assets Summary Action
Retrieve details about renewable assets in a given order. You can use this information to create renewal opportunities.
Initiate Amendment Action
Initiate and execute the amendment of an asset.
Initiate Cancellation Action
Initiate and execute the cancellation of an asset.
Initiate Renewal Action
Initiate and execute the renewal of an asset.
Initiate Rollback on Last Action
Initiate the reversal of the last action on an asset to rectify any transactional errors or to meet changing business requirements.
Initiate Transfer Action
Transfer an asset or multiple assets from one account to another.
SEE ALSO:
Actions Developer Guide: Overview
REST API Developer Guide: Invocable Actions Standard
Create Contract Action
Create a contract from a specific quote record.
This action is available in API version 60.0 and later.
Special Access Rules
The Create Contract action is available in Developer, Enterprise, and Unlimited Editions of Revenue Cloud.
1625
Transaction Management Standard Invocable ActionsTransaction Management

===== PAGE 1640 =====

Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/createContract
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
contractPriceOption
Description
Optional.
Determines how the contract price is set for quote line items based on the selected value.
Valid values are:
• CONTRACT_HEADER_ONLY—Creates a contract with only the header information,
without using net prices or discounts.
• NET_UNIT_PRICE_ONLY—Creates a contract specifically for quote line items with a
net unit price, saving all net unit prices of the quote as contract prices.
• DISCOUNT_ONLY—Creates contract prices specifically for quote line items with discounts,
saving all discounts of the quote as contract prices.
The default value is CONTRACT_HEADER_ONLY.
Type
string
sourceId
Description
Required.
ID of the quote or order that you want to create a contract from.
Outputs
DetailsOutput
Type
string
contractId
1626
Create Contract ActionTransaction Management

===== PAGE 1641 =====

DetailsOutput
Description
ID of the contract created for the specified order or quote.
Example
POST
This sample request is for the Create Contract action.
{
"inputs": [
{
"sourceId": "0Q0RO0000003LyU",
"contractPriceOption": "NET_UNIT_PRICE_ONLY"
}
]
}
This sample response is for the Create Contract action.
[
{
"actionName": "createContract",
"errors": null,
"isSuccess": true,
"outputValues": {
"contractId": "800XXX123456789"
}
}
]
SEE ALSO:
Salesforce Help: Use a Custom Flow to Create Contracts
Create or Update Asset From Order Action
Create an asset for each order item in the specified order. New assets are created for a new order. Modify existing assets for change order
requests, such as a renewal or a cancellation.
When the custom product name for an order line item has a value, the asset name is set to custom product name.
This action is available in API version 60.0 and later.
Special Access Rules
You need the Assetize Order permission set to use this invocable action.
1627
Create or Update Asset From Order ActionTransaction Management

===== PAGE 1642 =====

Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/createOrUpdateAssetFromOrder
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
orderId
Description
Required.
ID of the order.
Outputs
DetailsOutput
Type
string
requestId
Description
ID of the request to create an asset.
Example
POST
This sample request is for the Create or Update Asset From Order action.
{
"inputs": [
{
"orderId": "801DE000000oJfAYAU"
}
]
}
1628
Create or Update Asset From Order ActionTransaction Management

===== PAGE 1643 =====

This sample response is for the Create or Update Asset From Order action.
[
{
"actionName": "createOrUpdateAssetFromOrder",
"errors": null,
"isSuccess": true,
"outputValues": {
"requestId": "3b89392d-6987-40d9-9190-d18fdb5cb849"
}
}
]
Create or Update Asset From Order Item Action
Create assets from individual order items within an order. Track assets after the individual line items of an order reach a certain stage in
their lifecycle, such as submitted, fulfilled, or provisioned. If the order item is part of a renewal, an amendment, or a cancellation, existing
assets are changed.
This action is available in API version 60.0 and later.
Special Access Rules
You need the Assetize Order permission set to use this invocable action.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/createOrUpdateAssetFromOrderItem
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
orderId
Description
Required.
ID of the order.
1629
Create or Update Asset From Order Item ActionTransaction Management

===== PAGE 1644 =====

Outputs
DetailsOutput
Type
string
requestId
Description
ID of the request to create an asset.
Example
POST
This sample request is for the Create or Update Asset From Order Item action.
{
"inputs": [
{
"orderItemIds": ["802SG000002HixxYAC"]
}
]
}
This sample response is for the Create or Update Asset From Order Item action.
{
"actionName": "createOrUpdateAssetFromOrderItem",
"errors": null,
"isSuccess": true,
"outputValues": {
"requestId": "b2a2b4b9-845b-4078-980a-759308389604"
},
"version": 1
}
Create Order From Quote Action
Create an order from a quote record.
This action is available in API version 60.0 and later.
Special Access Rules
The Create Order From Quote action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/createOrderFromQuote
1630
Create Order From Quote ActionTransaction Management

===== PAGE 1645 =====

Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearer token
Inputs
DetailsInput
Type
datetime
quoteRecordId
Description
Required.
ID of the quote record.
Outputs
DetailsOutput
Type
string
requestId
Description
ID of the request.
Example
POST
This sample request is for the Create Order From Quote action.
{
"inputs": [
{
"quoteRecordId": "0Q0D200000000DhKAI"
}
]
}
This sample response is for the Create Order From Quote action.
[
{
"actionName": "createOrderFromQuote",
"errors": null,
1631
Create Order From Quote ActionTransaction Management

===== PAGE 1646 =====

"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"orderNumber": "00000122",
"orderId": "801oB000000DCrNQAW"
},
"sortOrder": -1,
"version": 1
}
]
Create Orders From Quote Action
Create multiple orders from a single quote instead of a single order, ensuring easier order management and fulfillment operations.
You can split a quote to create orders in these ways.
• You can create an order by selecting a subset of quote line items.
• You can split a quote into multiple orders based on quote line group.
• You can split a quote into multiple orders based on a quote line item field, such as Product2.
See Considerations for Creating Multiple Orders from a Quote. This action is available in API version 65.0 and later.
Special Access Rules
Ensure the Advanced Order Creation From Quote toggle from Revenue Settings from Setup is enabled to access this action.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/createOrdersFromQuote
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
orderCreationMethod
Description
If specified, represents the method used to create orders. Valid values are:
1632
Create Orders From Quote ActionTransaction Management

===== PAGE 1647 =====

DetailsInput
• CreateSingleOrder—Creates a single order from a quote. This method creates the
order header and order line items synchronously.
• CreateOrderByGroup—Create multiple orders based on a quote line group.
• CreateOrderByField—Create multiple orders based on a specified quote line item
field.
If you're creating multiple orders from a quote, the order header records are created synchronously
and order line items are created asynchronously. If unspecified, the default value is
CreateSingleOrder.
Type
Apex-defined
orderCreationParameters
Description
An Apex ConnectApi.OrderCreationParametersInputRepresentation
record that contains the additional parameters required by the specified order creation method.
Type
id
quoteId
Description
Required.
The ID of the source quote tied to the orders created.
Type
id
quoteLineItemIds
Description
List of quote line item IDs to create the orders from. If specified, the orders are created for the
list of provided quote line items. If unspecified, orders are created for all quote line items.
Outputs
DetailsOutput
Type
id
orderIds
Description
List of the created order IDs.
Type
string
requestId
Description
The request ID used to query the async status.
1633
Create Orders From Quote ActionTransaction Management

===== PAGE 1648 =====

DetailsOutput
Type
string
statusUrl
Description
The status URL that's used to track the async status.
Examples
Create a partial order from a quote
This example shows a sample request to create a partial order from a quote.
{
"inputs": [
{
"quoteId": "0Q0DU0000005tJc0AI",
"quoteLineItemIds": [
"0QLDU000000ay2G4AQ",
"0QLDU000000ay2n4AA"
],
"orderCreationMethod": "CreateSingleOrder"
}
]
}
This example shows a sample successful response.
{
"actionName": "createOrdersFromQuote",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"requestId": null,
"statusUrl": null,
"orderIds": [
"801DU000000EYySYAW"
]
},
"sortOrder": -1,
"version": 1
}
Create orders from a quote based on a quote line group
This example shows a sample request to create orders from a quote based on a quote line group.
{
"inputs": [
{
"quoteId": "0Q0DU0000005tJk0AI",
"orderCreationMethod": "CreateOrderByGroup"
1634
Create Orders From Quote ActionTransaction Management

===== PAGE 1649 =====

}
]
}
This example shows a sample successful response.
{
"actionName": "createOrdersFromQuote",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"requestId": "16PRM0000004DBq",
"orderIds": [
"801S70000001VKgIAM"
],
"success": true,
"errors": [],
"statusURL": "/services/data/v66.0/sobjects/AsyncOperationTracker/16PRM0000004DBq"
},
"sortOrder": -1,
"version": 1
}
Create orders from a quote based on a quote line item field
This example shows a sample request to create orders from a quote based on a quote line item field
{
"inputs": [
{
"quoteId": "0Q0DU0000005tJW0AY",
"orderCreationMethod": "CreateOrderByField",
"orderCreationParameters": {
"splitFieldName": "Product2Id"
}
}
]
}
This example shows a sample successful response.
{
"actionName": "createOrdersFromQuote",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"requestId": "16PRM0000004DBq",
"orderIds": [
"801S70000001VKgIAM",
"801S70000001WKgIBN"
],
"success": true,
1635
Create Orders From Quote ActionTransaction Management

===== PAGE 1650 =====

"errors": [],
"statusURL": "/services/data/v66.0/sobjects/AsyncOperationTracker/16PRM0000004DBq"
},
"sortOrder": -1,
"version": 1
}
Get Renewable Assets Summary Action
Retrieve details about renewable assets in a given order. You can use this information to create renewal opportunities.
This action gets pricing data from the OrderEntitiesMapping context mapping within the SalesTransactionContext context definition.
Before you use this action, edit the context mapping to map the objects and fields used in your pricing procedure to the nodes and
attributes in the context definition.
Note:  We recommend adding the same fields and mappings for the Quote and Order objects, and for the Quote Line Item and
Order Product objects.
This action is available in API version 64.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getRenewableAssetsSummary
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
id
orderId
Description
Required.
ID of the order related to the assets to check for renewal opportunities.
1636
Get Renewable Assets Summary ActionTransaction Management

===== PAGE 1651 =====

Outputs
DetailsOutput
Type
Apex-defined
renewableAssetsSummary
Description
Summary of the assets associated with the order, including details about renewal opportunities
such as renewal pricing information.
Example
POST
Here's a sample request for the Get Renewable Assets Summary action.
{
"inputs": [
{
"orderId": "801xx000003GZ39AAG"
}
]
}
Here's a sample response for the Get Renewable Assets Summary action.
[
{
"actionName": "getRenewableAssetsSummary",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"renewableAssetsSummary": [
{
"startDate": "2025-07-22",
"rootAssetOpportunity": null,
"renewalPriceDetails": [
{
"quantity": 1,
"netUnitPrice": 0
}
],
"productId": "01txx0000006i3DAAQ",
"priceBookId": "01sxx0000005ptpAAA",
"priceBookEntryId": "01uxx0000008yXCAAY",
"orderItem": "802xx000001nb1LAAQ",
"opportunityProductId": null,
"lastAssetActionSubtype": null,
"lastAssetAction": "Initial Sale",
"endDate": "2025-08-21",
1637
Get Renewable Assets Summary ActionTransaction Management

===== PAGE 1652 =====

"assetId": "02ixx0000004HKwAAM",
"account": "001xx000003GZ1XAAW"
}
]
},
"sortOrder": -1,
"version": 1
}
]
Initiate Amendment Action
Initiate and execute the amendment of an asset.
Specify IDs of the assets that you want to add to amend by specifying a start date and any changes to quantity. You can also specify the
type of amendment record that you want to create such as a quote or an order.
This action is available in API version 60.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/initiateAmendment
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
amendAssetIds
Description
Required.
The IDs of the assets that you want to amend.
Type
string
amendContractId
Description
The ID of the contract record to be synced with the amendment.
1638
Initiate Amendment ActionTransaction Management

===== PAGE 1653 =====

DetailsInput
Type
datetime
amendStartDate
Description
Required.
Effective start date of the amendment.
Type
string
amendOpportunityId
Description
The ID of the Opportunity record to be synced with the amendment quote.
Type
string
amendOutputType
Description
Required.
Type of amendment record to create such as a quote or an order.
Type
double
quantityChange
Description
Required.
Quantity to add to or reduce from the asset's existing quantity.
Type
boolean
skipPricing
Description
Indicates whether the pricing procedure must be skipped (true) or performed (false).
Available in API version 64.0 and later.
Outputs
DetailsOutput
Type
string
amendRecordId
Description
The ID of the amendment record that’s created.
1639
Initiate Amendment ActionTransaction Management

===== PAGE 1654 =====

DetailsOutput
Type
string
requestIdentifier
Description
Request ID that’s used to track the async request.
Example
POST
This sample request is for the Initiate Amendment action.
{
"inputs": [
{
"amendAssetIds": ["02iI8000000HPzXIAW"],
"amendStartDate": "2023-10-21T00:00:00.000Z",
"quantityChange": 5,
"amendOutputType": "Quote",
"amendContractId": "800DU0000000lZlYAI",
"amendOpportunityId": "006DU0000025AanYAE",
"skipPricing": false
}
]
}
This sample response is for the Initiate Amendment action.
[
{
"actionName": "initiateAmendment",
"errors": null,
"isSuccess": true,
"outputValues": {
"record_id": "0Q0xx0000004NsSCAU",
"requestIdentifier": "16Pxx0000004NIy"
},
"version": 1
}
]
Initiate Cancellation Action
Initiate and execute the cancellation of an asset.
Specify the IDs of the assets that you want to add to cancel by specifying a start date. You can also specify the type of cancellation record
that you want to create, such as a quote or an order.
This action is available in API version 60.0 and later.
1640
Initiate Cancellation ActionTransaction Management

===== PAGE 1655 =====

Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/initiateCancellation
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
cancelAssetIds
Description
Required.
The IDs of the assets that you want to cancel.
All assets in a request must belong to the same price book.
Type
string
cancelContractId
Description
The ID of the contract record to sync with the cancellation.
Type
string
cancelOpportunityId
Description
The ID of the Opportunity record to sync with the cancellation quote.
Type
string
cancelOutputType
Description
Required.
Type of cancellation record to create such as a quote or an order.
Type
datetime
cancelStartDate
Description
Required.
1641
Initiate Cancellation ActionTransaction Management

===== PAGE 1656 =====

DetailsInput
Effective date of the cancellation.
Type
boolean
skipPricing
Description
Indicates whether the pricing procedure must be skipped (true) or performed (false).
Available in API version 64.0 and later.
Outputs
DetailsOutput
Type
string
cancelRecordId
Description
The ID of the cancellation record that’s created.
Type
string
requestIdentifier
Description
Request ID that’s used to track the async request.
Example
POST
This sample request is for the Initiate Cancellation action.
{
"inputs": [
{
"cancelAssetIds": [
"02iI8000000Lc5fIAC"
],
"cancelStartDate": "2023-11-09T00:00:00",
"cancelOutputType": "Quote",
"cancelContractId": "800DU0000000lZlYAI",
"cancelOpportunityId": "006DU0000025AanYAE",
"skipPricing": false
}
]
}
1642
Initiate Cancellation ActionTransaction Management

===== PAGE 1657 =====

This sample response is for the Initiate Cancellation action.
[
{
"actionName": "initiateCancellation",
"errors": null,
"isSuccess": true,
"outputValues": {
"record_id": "0Q0xx0000004P32CAE",
"requestIdentifier": "16Pxx0000004OTY"
},
"version": 1
}
]
Initiate Renewal Action
Initiate and execute the renewal of an asset.
Specify IDs of the assets that you want to add to renew by specifying a start date. You can also specify the type of renewal record that
you want to create such as a quote or an order.
This action is available in API version 60.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/initiateRenewal
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
renewAssetIds
Description
Required.
The IDs of the assets that you want to renew.
Type
string
renewContractId
1643
Initiate Renewal ActionTransaction Management

===== PAGE 1658 =====

DetailsInput
Description
The ID of the contract record to be synced with the renewal.
Type
datetime
renewEndDate
Description
Effective end date of the renewal. Available in API version 62.0 and later.
Type
string
renewOpportunityId
Description
The ID of the Opportunity record to be synced with the renewal quote.
Type
string
renewOutputType
Description
Required.
Type of renewal record to create such as a quote or an order.
Type
datetime
renewStartDate
Description
Optional
Effective start date of the renewal. Required for early asset renewals and renewing expired assets,
using today’s date or a future date. Available in API version 62.0 and later.
Type
boolean
skipPricing
Description
Indicates whether the pricing procedure must be skipped (true) or performed (false).
Available in API version 64.0 and later.
Outputs
DetailsOutput
Type
string
renewRecordId
1644
Initiate Renewal ActionTransaction Management

===== PAGE 1659 =====

DetailsOutput
Description
The ID of the amendment record that’s created.
Type
string
requestIdentifier
Description
Request ID that’s used to track the async request.
Example
POST
This sample request is for the Initiate Renewal action.
{
"inputs": [
{
"renewAssetIds": ["02ixx0000004LMwAAM"],
"renewOutputType": "Quote",
"renewContractId": "800DU0000000lZlYAI",
"renewOpportunityId": "006DU0000025AanYAE",
"renewStartDate": "2023-10-21T00:00:00.000Z",
"renewEndDate": "2024-10-21T00:00:00.000Z",
"skipPricing": false
}
]
}
This sample response is for the Initiate Renewal action.
[
{
"actionName": "initiateRenewal",
"errors": null,
"isSuccess": true,
"outputValues": {
"record_id": "0Q0xx0000004P32CAE",
"requestIdentifier": "16Pxx0000004OTY"
},
"version": 1
}
]
Initiate Rollback on Last Action
Initiate the reversal of the last action on an asset to rectify any transactional errors or to meet changing business requirements.
Use this action to revert the last amendment or renewal on a particular asset, restoring the asset to its previous state. This action creates
a quote or an order based on the specified output type. Use the created reversal quote to verify the reversal and convert the quote into
an order.
1645
Initiate Rollback on Last ActionTransaction Management

===== PAGE 1660 =====

Keep these considerations in mind when you use this action.
• You can roll back only future dated transactions.
• Rollback action isn't supported for legacy assets.
• The rollback operation is supported for amendment and renewal only.
This action is available in API version 65.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/initiateRollBackLastAction
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
assetIds
Description
Required.
List of asset IDs to include in the last action rollback.
Type
string
outputType
Description
Required.
The type of record to create for reversal. Valid values are:
• Quote—Creates a reversal quote.
• Order—Creates a reversal order.
1646
Initiate Rollback on Last ActionTransaction Management

===== PAGE 1661 =====

Outputs
DetailsOutput
Type
id
recordId
Description
The ID of the created quote or order.
Example
POST
This example shows a sample request that initiates the rollback action on an asset and converts it into a quote.
{
"inputs": [
{
"assetIds": [
"02iDU0000006UisYAE"
],
"outputType": "Quote"
}
]
}
This example shows a sample successful response.
{
"actionName": "initiateRollBackLastAction",
"errors": null,
"isSuccess": true,
"outputValues": {
"recordId": "0Q0xx0000004NsSCAU"
},
"version": 1
}
Initiate Transfer Action
Transfer an asset or multiple assets from one account to another.
Keep these considerations in mind when you use this invocable action.
• This action generates 2 quotes or 2 orders.
• One transaction is considered the source, which is used to calculate the reduction amount of the transfer. The other transaction is
the target, which is used to calculate the new amount on the target account.
• The quantity on the source is negative, which reduces the existing asset's quantity. The quantity on the target is positive, which
creates a new asset on the target account.
1647
Initiate Transfer ActionTransaction Management

===== PAGE 1662 =====

• You can change the quantity on the source or the target, but the quantities must be equal and opposite. For example, the source
quote line can have a quantity value as -5, and the target quote line can have a quantity value 5. If you change the source value
to -10, you must update the target value to 10. You must update quotes or orders manually.
• The transfer is complete after the orders are assetized.
This action is available in API version 65.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/initiateTransfer
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
outputRecordType
Description
Required.
Specifies either a quote or order record type that’s being transferred.
Type
boolean
shouldSkipPricing
Description
Indicates whether to skip pricing at the time of asset transfer (true) or not (false).
Type
string
targetAccountId
Description
Required.
The ID of the target account where the asset is transferred.
Type
string
targetContractId
Description
The ID of the target contract that’s associated with the asset that’s being transferred.
1648
Initiate Transfer ActionTransaction Management

===== PAGE 1663 =====

DetailsInput
Type
datetime
transferDate
Description
Required.
The date of the asset transfer.
Type
Apex-defined
transferRecords
Description
Required.
A collection of Apex connectapi__TransferRecordInputRepresentation
records that contain details about the assets to be transferred. See
ConnectApi.TransferRecordInputRepresentation.
Outputs
DetailsOutput
Type
id
assetTransferSourceId
Description
The ID of the quote or order that’s related to the source account used to start the transfer.
Type
id
assetTransferTargetId
Description
The ID of the quote or order that’s related to the target account used to start the transfer.
Type
id
requestIdentifier
Description
The request ID can be used to track the async request.
1649
Initiate Transfer ActionTransaction Management

===== PAGE 1664 =====

Example
POST
Here's a sample input to call this invocable action.
{
"inputs": [
{
"transferRecords": [
{
"assetId": "02ixx0000004HZbAAM",
"transferQuantity": 1
}
],
"transferDate": "2025-10-21T00:00:00.000Z",
"targetAccountId": "001xx000003GbeXAAS",
"targetContractId": "800DU0000000lZlYAI",
"outputRecordType": "Quote"
}
]
}
Here's a sample input to call this invocable action from Apex code.
ConnectApi.TransferRecordInputRepresentation transferRecord = new
ConnectApi.TransferRecordInputRepresentation();
transferRecord.assetId = '02ixx0000004HHjAAM';
transferRecord.transferQuantity = 1;
List<ConnectApi.TransferRecordInputRepresentation> transferRecords = new
List<ConnectApi.TransferRecordInputRepresentation>();
transferRecords.add(transferRecord);
Invocable.Action action = Invocable.Action.createStandardAction('initiateTransfer');
action.setInvocationParameter('transferRecords', transferRecords);
action.setInvocationParameter('targetAccountId', '001xx000003GYiHAAW');
action.setInvocationParameter('transferDate', '2025-03-01T00:00:00.000Z');
action.setInvocationParameter('outputRecordType', 'Quote');
List<Invocable.Action.Result> results = action.invoke();
System.assertEquals(true, results[0].isSuccess());
Assert.isNotNull(results[0].getOutputParameters().get('assetTransferSourceId'));
Here's a sample response when you call this action.
[
{
"actionName": "initiateTransfer",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"assetTransferSourceId": "0Q0DU0000006SYF0A2",
"assetTransferTargetId": "0Q0DU0000006SYE0A2"
},
"sortOrder": -1,
1650
Initiate Transfer ActionTransaction Management

===== PAGE 1665 =====

"version": 1
}
]
Transaction Management Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
Flow for Transaction Management
The flow for Transaction Management represents the metadata associated with a flow. With Flow, you can create an application
that takes users through a series of pages to query and update the records in the database. You can also run logic and provide
branching capability based on user input to build dynamic applications.
SEE ALSO:
Metadata API Developer Guide: Understanding Metadata API
Flow for Transaction Management
The flow for Transaction Management represents the metadata associated with a flow. With Flow, you can create an application that
takes users through a series of pages to query and update the records in the database. You can also run logic and provide branching
capability based on user input to build dynamic applications.
FlowActionCall
Transaction Management exposes additional actionType values for the FlowActionCall metadata type.
DescriptionField TypeField Name
Required.InvocableActionType
(enumeration of
type string)
actionType
The action type. Additional valid values for Transaction Management
are:
• createContract— Create a contract from a specific quote
record.
• createOrderFromQuote— Create an order from a quote
record.
• createServiceDocument—Create service documents from
work orders, work order line items, or service appointments.
• getRenewableAssetsSummary— Retrieve details about
renewable assets in a given order. You can use this information to
create renewal opportunities. Added in API version 64.0 and later.
• createOrUpdateAssetFromOrder— Create an asset for
each order item in the specified order. New assets are created for a
new order. Modify existing assets for change order requests, such
as a renewal or a cancellation.
1651
Transaction Management Metadata API TypesTransaction Management

===== PAGE 1666 =====

DescriptionField TypeField Name
• createOrUpdateAssetFromOrderItem— Create assets
from individual order items within an order. Track assets after the
individual line items of an order reach a certain stage in their lifecycle,
such as submitted, fulfilled, or provisioned. If the order item is part
of a renewal, an amendment, or a cancellation, existing assets are
changed.
• initiateAmendment— Initiate and execute the amendment
of an asset.
• initiateRenewal— Initiate and execute the renewal of an
asset.
• initiateCancellation— Initiate and execute the
cancellation of an asset.
• initiateRollBackLastAction— Initiate the reversal of
the last action on an asset to rectify any transactional errors or to
meet changing business requirements.
• createOrdersFromQuote— Create multiple orders from a
single quote instead of a single order, ensuring easier order
management and fulfillment operations.
• initiateTransfer— Transfer an asset or multiple assets from
one account to another.
/
1652
Flow for Transaction ManagementTransaction Management

===== PAGE 1667 =====

