---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 6 — Rate Management

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 6 Rate Management
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions of Revenue Cloud
where Rate Management is
enabled
Quote and price products based on predefined rates for future use
of the product or service.
SEE ALSO:
Salesforce Help: Rate Management Permission Set Licenses
In this chapter ...
• Rate Management
Standard Objects
• Rate Management
Metadata API Types
• Rate Management
Business APIs
• Rate Management
Standard Invocable
Actions
822

===== PAGE 837 =====

Rate Management Standard Objects
The Rate Management data model provides objects and fields to manage rates and discounts for a product's resource consumption.
BindingObjectCustomExt
Represents the external or custom target object that's bound to the entitlements granted with the sellable product. This object is
available in API version 64.0 and later.
BindingObjectRateAdjustment
Represents the rate adjustments of the usage resource associated with the binding object that's used to charge over consumption.
This object is available in API version 64.0 and later.
BindingObjectRateCardEntry
Represents the rate card entry details of the usage resource associated with the binding object that's used to charge over consumption.
This object is available in API version 64.0 and later.
PriceBookRateCard
Represents a junction between price book and rate card objects. This object is available in API version 62.0 and later.
RateAdjustmentByAttribute
Represents the adjustments that determine the rate of a resource based on its rate-impacting attributes. These attributes are linked
to the usage product record. Rates are then influenced by conditions specified in the Attribute Based Adjustment Condition object.
Finally, the charge rate is determined by using the Attribute Based Adjustment Rule object. This object is available in API version
62.0 and later.
RateAdjustmentByTier
Represents the adjustments for the rate of a resource that’s determined based on the specified tiers. This object stores information
about the type of adjustment used, the value of the adjustment type, and any applicable boundaries. This object is available in API
version 62.0 and later.
RateCard
Represents the rules used to rate the consumption of a group of resources within a product. Usage of a resource is billed at a specified
rate if the user consumes more than their allowance for a time period. This object is available in API version 62.0 and later.
RateCardEntry
Represents a rule that determines the charge rate for using a product's resource. Each entry is linked to one rate card exclusively,
and its activation or deactivation can be controlled by assigning effective dates. This object is available in API version 62.0 and later.
RatingFrequencyPolicy
Represents the policy that defines the frequency at which rating is triggered for the ratable summary records. This object is available
in API version 62.0 and later.
RatingRequest
Represents the common run-time parameters, such as context definition and rating procedure for a set of records in the rateable
summary table. This object is available in API version 62.0 and later.
RatingRequestBatchJob
Represents a junction between the rating request and batch job objects. This object is available in API version 62.0 and later.
SEE ALSO:
Object Reference for the Salesforce Platform: Overview of Salesforce Objects and Fields
SOAP API Developer Guide: Introduction to SOAP API
823
Rate Management Standard ObjectsRate Management

===== PAGE 838 =====

BindingObjectCustomExt
Represents the external or custom target object that's bound to the entitlements granted with the sellable product. This object is available
in API version 64.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
• This object is available in Revenue Cloud when Rate Management is enabled.
• Users with any Rate Management permission set (Admin, Manager, Designtime, Runtime) can view records. Only Admins can create,
edit, and delete records.
Fields
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
The name of the binding custom object record.
Type
reference
OwnerId
824
BindingObjectCustomExtRate Management

===== PAGE 839 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the product usage grant.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
BindingObjectRateAdjustment
Represents the rate adjustments of the usage resource associated with the binding object that's used to charge over consumption. This
object is available in API version 64.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(), search()
Special Access Rules
• This object is available in Revenue Cloud when Rate Management is enabled.
• Users with any Rate Management permission set (Admin, Manager, Designtime, Runtime) can view records.
Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Filter, Group, Restricted picklist, Sort
Description
The type of rate adjustment related to the associated rate card entry.
Valid values are:
• Amount
• Override
• Percentage
825
BindingObjectRateAdjustmentRate Management

===== PAGE 840 =====

DetailsField
Type
double
AdjustmentValue
Properties
Filter, Sort
Description
The value of the rate adjustment based on the adjustment type.
Type
reference
BindingObjectRateCardEntryId
Properties
Filter, Group, Sort
Description
The binding object rate card entry associated with the binding object rate adjustment.
This field is a relationship field.
Relationship Name
BindingObjectRateCardEntry
Relationship Type
Master-detail
Refers To
BindingObjectRateCardEntry (the master object)
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
double
LowerBound
Properties
Filter, Sort
826
BindingObjectRateAdjustmentRate Management

===== PAGE 841 =====

DetailsField
Description
The minimum quantity of the rate adjustment value that can be applied to the binding object
rate adjustment record. This must be a positive number that's less than or equal to the upper
bound of the tier.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The autogenerated identifier for the binding object rate adjustment record.
Type
double
UpperBound
Properties
Filter, Nillable, Sort
Description
The maximum quantity of the rate adjustment value that can be applied to the binding
object rate adjustment record. This must be a positive number. Set this value one digit higher
than the quantity you want the tier to include.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
BindingObjectRateAdjustmentFeed
Feed tracking is available for the object.
BindingObjectRateAdjustmentHistory
History is available for tracked fields of the object.
BindingObjectRateAdjustmentShare
Sharing is available for the object.
BindingObjectRateCardEntry
Represents the rate card entry details of the usage resource associated with the binding object that's used to charge over consumption.
This object is available in API version 64.0 and later.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(), search()
827
BindingObjectRateCardEntryRate Management

===== PAGE 842 =====

Special Access Rules
• This object is available in Revenue Cloud when Rate Management is enabled.
• Users with any Rate Management permission set (Admin, Manager, Designtime, Runtime) can view records.
Fields
DetailsField
Type
reference
BindingObjectId
Properties
Filter, Group, Sort
Description
The object associated with the entitlements that are granted with the sellable product.
This field is a polymorphic relationship field.
Relationship Name
BindingObject
Refers To
Account, BindingObjectCustomExt, Contract
Type
double
BindingObjectRateOrder
Properties
Filter, Nillable, Sort
Description
The order that determines the applicable binding object rate when multiple rates are defined
for an Anchor target within an effective period. Available in API version 65.0 and later.
Type
string
BindingObjectUsageResourceKey
Properties
Filter, Group, idLookup, Nillable, Sort
Description
Specifies the autogenerated composite key combining the BindingObjectId and
UsageResourceId fields. The format used is BindingObjectId_UsageResourceId
and must be within 18 characters. The key is generated on saving the
BindingObjectRateCardEntry record. For
example,001xx000003Gc4FAAS_1BRxx0000004C95GAE. Available in API version
66.0 and later.
Type
dateTime
EffectiveFrom
828
BindingObjectRateCardEntryRate Management

===== PAGE 843 =====

DetailsField
Properties
Filter, Sort
Description
The date and time when the associated rate card entry comes into effect.
Type
dateTime
EffectiveTo
Properties
Filter, Nillable, Sort
Description
The date and time until which the associated rate card entry remains effective.
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
The autogenerated identifier for the binding object rate card entry record. For example,
BORCE-00004  or BORCE-4567.
Type
double
NegotiatedRate
Properties
Filter, Nillable, Sort
Description
The rate negotiated for the associated binding object.
829
BindingObjectRateCardEntryRate Management

===== PAGE 844 =====

DetailsField
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the user who created the record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
RateCardEntryId
Properties
Filter, Group, Sort
Description
The rate card entry associated with the binding object.
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
The rate card associated to the binding object.
This field is a relationship field.
Relationship Name
RateCard
Refers To
RateCard
Type
picklist
RateCardType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
830
BindingObjectRateCardEntryRate Management

===== PAGE 845 =====

DetailsField
Description
The type of the rate card associated with the binding object rate card entry.
Valid values are:
• Attribute
• Base
• Tier
Type
reference
RateUnitOfMeasureId
Properties
Filter, Group, Nillable, Sort
Description
The standard unit of measure associated with the rate defined for the binding object.
This field is a relationship field.
Relationship Name
RateUnitOfMeasure
Refers To
UnitOfMeasure
Type
reference
SourceAssetId
Properties
Filter, Group, Nillable, Sort
Description
The asset that's used to create the binding object rate card entry.
This field is a relationship field.
Relationship Name
SourceAsset
Refers To
Asset
Type
reference
UsageResourceId
Properties
Filter, Group, Nillable, Sort
Description
The usage resource associated with the binding object rate card entry.
This field is a relationship field.
Relationship Name
UsageResource
831
BindingObjectRateCardEntryRate Management

===== PAGE 846 =====

DetailsField
Refers To
UsageResource
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
BindingObjectRateAdjustmentFeed
Feed tracking is available for the object.
BindingObjectRateAdjustmentHistory
History is available for tracked fields of the object.
BindingObjectRateAdjustmentShare
Sharing is available for the object.
PriceBookRateCard
Represents a junction between price book and rate card objects. This object is available in API version 62.0 and later.
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
Timestamp for when the current user last referred to this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
832
PriceBookRateCardRate Management

===== PAGE 847 =====

DetailsField
Description
Timestamp for when the current user last viewed a record related to this record.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Auto-generated identifier for the price book rate card record.
Type
reference
PriceBookId
Properties
Create, Filter, Group, Sort
Description
Price book ID that's associated with the rate cards IDs. For Quote, Order, and Contracts, the
price book IDs identify the associated rate cards.
This field is a relationship field.
Relationship Name
PriceBook
Relationship Type
Master-detail
Refers To
Pricebook2 (the master object)
Type
reference
RateCardId
Properties
Create, Filter, Group, Sort
Description
Rate card ID that's associated with the price book.
This field is a relationship field.
Relationship Name
RateCard
Relationship Type
Master-detail
Refers To
RateCard (the detail object)
Type
picklist
RateCardType
833
PriceBookRateCardRate Management

===== PAGE 848 =====

DetailsField
Properties
Filter, Group, Restricted picklist, Sort
Description
Type of rate card associated with the price book.
Valid values are:
• Attribute
• Base
• Tier
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
PriceBookRateCardFeed
Feed tracking is available for the object.
PriceBookRateCardHistory
History is available for tracked fields of the object.
RateAdjustmentByAttribute
Represents the adjustments that determine the rate of a resource based on its rate-impacting attributes. These attributes are linked to
the usage product record. Rates are then influenced by conditions specified in the Attribute Based Adjustment Condition object. Finally,
the charge rate is determined by using the Attribute Based Adjustment Rule object. This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Type of rate adjustment.
834
RateAdjustmentByAttributeRate Management

===== PAGE 849 =====

DetailsField
Valid values are:
• Amount
• Override
• Percentage
Type
double
AdjustmentValue
Properties
Create, Filter, Sort, Update
Description
Value of the rate adjustment based on the selected adjustment type.
Type
reference
AttributeBasedAdjRuleId
Properties
Create, Filter, Group, Sort, Update
Description
ID of the attribute based adjustment rule associated with this rate adjustment by attribute
record.
This field is a relationship field.
Relationship Name
AttributeBasedAdjRule
Refers To
AttributeBasedAdjRule
Type
dateTime
EffectiveFrom
Properties
Filter, Sort
Description
Date and time when the associated rate card entry comes into effect.
Type
dateTime
EffectiveTo
Properties
Filter, Nillable, Sort
Description
Date and time until when the associated rate card entry remains effective.
Type
dateTime
LastReferencedDate
835
RateAdjustmentByAttributeRate Management

===== PAGE 850 =====

DetailsField
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
Auto-generated identifier for the rate adjustment by attribute record.
Type
reference
ProductId
Properties
Filter, Group, Nillable, Sort
Description
ID of the product whose resource is being used as the associated rate card entry.
This field is a relationship field.
Relationship Name
Product
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Filter, Group, Nillable, Sort
Description
ID of the product selling model for the associated rate card entry.
This field is a relationship field.
Relationship Name
ProductSellingModel
836
RateAdjustmentByAttributeRate Management

===== PAGE 851 =====

DetailsField
Refers To
ProductSellingModel
Type
reference
RateCardEntryId
Properties
Create, Filter, Group, Sort
Description
ID of the rate card entry associated with this rate adjustment by attribute record.
This field is a relationship field.
Relationship Name
RateCardEntry
Relationship Type
Master-detail
Refers To
RateCardEntry (the master object)
Type
picklist
RateCardEntryStatus
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Status of the rate card entry associated with this rate adjustment by attribute.
Valid values are:
• Active
• Draft
• Inactive
The default value is Draft. Available in API version 63.0 and later.
Type
reference
RateCardId
Properties
Filter, Group, Sort
Description
ID of the rate card of the associated rate card entry.
This field is a relationship field.
Relationship Name
RateCard
Refers To
RateCard
837
RateAdjustmentByAttributeRate Management

===== PAGE 852 =====

DetailsField
Type
reference
RateUnitOfMeasureId
Properties
Filter, Group, Sort
Description
ID of the standard unit of measure record of the associated rate card entry.
This field is a relationship field.
Relationship Name
RateUnitOfMeasure
Refers To
UnitOfMeasure
Type
string
RateUnitOfMeasureName
Properties
Filter, Group, Sort
Description
Name of the standard unit of measure record of the associated rate card entry.
Type
reference
UsageResourceId
Properties
Filter, Group, Sort
Description
ID of the resource selected for the associated rate card entry.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
RateAdjustmentByAttributeFeed
Feed tracking is available for the object.
RateAdjustmentByAttributeHistory
History is available for tracked fields of the object.
838
RateAdjustmentByAttributeRate Management

===== PAGE 853 =====

RateAdjustmentByTier
Represents the adjustments for the rate of a resource that’s determined based on the specified tiers. This object stores information about
the type of adjustment used, the value of the adjustment type, and any applicable boundaries. This object is available in API version 62.0
and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
AdjustmentType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Type of rate adjustment.
Valid values are:
• Amount
• Override
• Percentage
Type
double
AdjustmentValue
Properties
Create, Filter, Sort, Update
Description
Value of the rate adjustment based on the selected adjustment type.
Type
dateTime
EffectiveFrom
Properties
Filter, Sort
Description
Date and time when the associated rate card entry comes into effect.
Type
dateTime
EffectiveTo
839
RateAdjustmentByTierRate Management

===== PAGE 854 =====

DetailsField
Properties
Filter, Nillable, Sort
Description
Date and time until when the associated rate card entry remains effective.
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
double
LowerBound
Properties
Create, Filter, Sort, Update
Description
Minimum quantity of the rate adjustment value that can be applied to the record. This value
must be a positive integer and must be less than the upper bound of the tier.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Auto-generated identifier for the rate adjustment by tier record.
Type
reference
ProductId
Properties
Filter, Group, Nillable, Sort
Description
ID of the product whose resource is being used as the associated rate card entry.
This field is a relationship field.
840
RateAdjustmentByTierRate Management

===== PAGE 855 =====

DetailsField
Relationship Name
Product
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Filter, Group, Nillable, Sort
Description
ID of the product selling model for the associated rate card entry record.
This field is a relationship field.
Relationship Name
ProductSellingModel
Refers To
ProductSellingModel
Type
reference
RateCardEntryId
Properties
Create, Filter, Group, Sort
Description
ID of the rate card entry associated with this rate adjustment by tier record.
This field is a relationship field.
Relationship Name
RateCardEntry
Relationship Type
Master-detail
Refers To
RateCardEntry (the master object)
Type
picklist
RateCardEntryStatus
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Status of the rate card entry associated with this rate adjustment by tier.
Valid values are:
• Active
• Draft
841
RateAdjustmentByTierRate Management

===== PAGE 856 =====

DetailsField
• Inactive
The default value is Draft. Available in API version 63.0 and later.
Type
reference
RateCardId
Properties
Filter, Group, Sort
Description
ID of the rate card of the associated rate card entry.
This field is a relationship field.
Relationship Name
RateCard
Refers To
RateCard
Type
reference
RateUnitOfMeasureId
Properties
Filter, Group, Sort
Description
ID of the standard unit of measure record of the associated rate card entry.
This field is a relationship field.
Relationship Name
RateUnitOfMeasure
Refers To
UnitOfMeasure
Type
string
RateUnitOfMeasureName
Properties
Filter, Group, Sort
Description
Name of the standard unit of measure record of the associated rate card entry.
Type
double
UpperBound
Properties
Create, Filter, Nillable, Sort, Update
Description
Maximum quantity of the rate adjustment value that can be applied to the record. This value
must be a positive double and must be greater than the lower bound of the tier.
842
RateAdjustmentByTierRate Management

===== PAGE 857 =====

DetailsField
Type
reference
UsageResourceId
Properties
Filter, Group, Sort
Description
ID of the resource selected for the associated rate card entry.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
RateAdjustmentByTierFeed
Feed tracking is available for the object.
RateAdjustmentByTierHistory
History is available for tracked fields of the object.
RateCard
Represents the rules used to rate the consumption of a group of resources within a product. Usage of a resource is billed at a specified
rate if the user consumes more than their allowance for a time period. This object is available in API version 62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Description about the rate card.
843
RateCardRate Management

===== PAGE 858 =====

DetailsField
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
Date and time when the rate card becomes effective.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
Date and time until when the rate card remains effective.
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
Name of the rate card.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
ID of the user who created the record.
844
RateCardRate Management

===== PAGE 859 =====

DetailsField
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
picklist
Type
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Type of rate card.
Valid values are:
• Attribute
• Base
• Tier
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
RateCardFeed
Feed tracking is available for the object.
RateCardHistory
History is available for tracked fields of the object.
RateCardShare
Sharing is available for the object.
RateCardEntry
Represents a rule that determines the charge rate for using a product's resource. Each entry is linked to one rate card exclusively, and its
activation or deactivation can be controlled by assigning effective dates. This object is available in API version 62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
845
RateCardEntryRate Management

===== PAGE 860 =====

Fields
DetailsField
Type
reference
DefaultUnitOfMeasureClassId
Properties
Filter, Group, Nillable, Sort
Description
ID of the default unit of measure classification record associated with this rate card entry.
This field is a relationship field.
Relationship Name
DefaultUnitOfMeasureClass
Refers To
UnitOfMeasureClass
Type
reference
DefaultUnitOfMeasureId
Properties
Filter, Group, Nillable, Sort
Description
ID of the default unit of measure record associated with this rate card entry.
This field is a relationship field.
Relationship Name
DefaultUnitOfMeasure
Refers To
UnitOfMeasure
Type
dateTime
EffectiveFrom
Properties
Create, Filter, Sort, Update
Description
Date and time when the rate card entry comes into effect.
Type
dateTime
EffectiveTo
Properties
Create, Filter, Nillable, Sort, Update
Description
Date and time until when the rate card entry remains effective.
846
RateCardEntryRate Management

===== PAGE 861 =====

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
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Auto-generated identifier for the rate card entry record.
Type
reference
ProductId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
ID of the product whose resource is being used as a rate card entry.
This field is a relationship field.
Relationship Name
Product
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
ID of the product selling model associated with this rate card entry.
This field is a relationship field.
847
RateCardEntryRate Management

===== PAGE 862 =====

DetailsField
Relationship Name
ProductSellingModel
Refers To
ProductSellingModel
Type
double
Rate
Properties
Create, Filter, Nillable, Sort, Update
Description
Value of the rate card entry.
Type
reference
RateCardId
Properties
Create, Filter, Group, Sort
Description
ID of the rate card associated with this rate card entry.
This field is a relationship field.
Relationship Name
RateCard
Relationship Type
Master-detail
Refers To
RateCard (the master object)
Type
picklist
RateCardType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Type of rate card associated with this rate card entry.
Valid values are:
• Attribute
• Base
• Tier
Available in API version 63.0 and later.
Type
picklist
RateNegotiation
848
RateCardEntryRate Management

===== PAGE 863 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Type of rate negotiation applicable to the rate card entry.
Valid values are:
• Negotiable
• NonNegotiable
The default value is Negotiable. Available in API version 63.0 and later.
Type
reference
RateUnitOfMeasureClassId
Properties
Filter, Group, Sort
Description
ID of the unit of measure classification record associated with this rate card entry.
This field is a relationship field.
Relationship Name
RateUnitOfMeasureClass
Refers To
UnitOfMeasureClass
Type
reference
RateUnitOfMeasureId
Properties
Create, Filter, Group, Sort, Update
Description
ID of the standard unit of measure record associated with this rate card entry.
This field is a relationship field.
Relationship Name
RateUnitOfMeasure
Refers To
UnitOfMeasure
Type
string
RateUnitOfMeasureName
Properties
Filter, Group, Sort
Description
Name of the standard unit of measure record of the associated rate card entry.
849
RateCardEntryRate Management

===== PAGE 864 =====

DetailsField
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Status of the rate card entry.
• Active
• Draft
• Inactive
The default value is Draft. Available in API version 63.0 and later.
Type
reference
UsageProductId
Properties
Filter, Group, Nillable, Sort
Description
ID of the product associated with the resource for which the rate is specified.
This field is a relationship field.
Relationship Name
UsageProduct
Refers To
Product2
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
ID of the resource associated with this rate card entry.
This field is a relationship field.
Relationship Name
UsageResource
Refers To
UsageResource
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
850
RateCardEntryRate Management

===== PAGE 865 =====

RateCardEntryFeed
Feed tracking is available for the object.
RateCardEntryHistory
History is available for tracked fields of the object.
RatingFrequencyPolicy
Represents the policy that defines the frequency at which rating is triggered for the ratable summary records. This object is available in
API version 62.0 and later.
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
Auto-generated identifier for the rating frequency policy record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
851
RatingFrequencyPolicyRate Management

===== PAGE 866 =====

DetailsField
Description
ID of the user who created the record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
ProductId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
ID of the product for which the rating policy is defined.
This field is a relationship field. This field is deprecated and will be retired in a future version.
Relationship Name
Product
Refers To
Product2
Type
int
RatingDelayDuration
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Duration of delay—in hours—post the billing period after which the rating is to be triggered.
Type
picklist
RatingDelayDurationUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the unit for the specified rating delay duration. Available in API version 65.0 and
later.
Valid values are:
• Days
• Hours
Type
picklist
RatingPeriod
852
RatingFrequencyPolicyRate Management

===== PAGE 867 =====

DetailsField
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Period for which the usage of a product and usage resource combination are to be rated.
Valid values are:
• Daily
• Monthly
Type
reference
UsageResourceId
Properties
Create, Filter, Group, Sort, Update
Description
ID of the usage resource for which the rating policy is defined.
This field is a relationship field. This field is deprecated and will be retired in a future version.
Relationship Name
UsageResource
Refers To
UsageResource
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
RatingFrequencyPolicyFeed
Feed tracking is available for the object.
RatingFrequencyPolicyHistory
History is available for tracked fields of the object.
RatingFrequencyPolicyShare
Sharing is available for the object.
RatingRequest
Represents the common run-time parameters, such as context definition and rating procedure for a set of records in the rateable summary
table. This object is available in API version 62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
853
RatingRequestRate Management

===== PAGE 868 =====

Fields
DetailsField
Type
string
ContextDefinition
Properties
Create, Filter, Group, Sort, Update
Description
Context definition that's used for context instance creation, which encapsulates all aggregated
records that are stamped for the rating request.
Type
string
ContextMapping
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Context mapping that's used for context instance creation, which encapsulates all aggregated
records that are stamped for the rating request. If no ID is provided, default context mapping
is used.
Type
boolean
DoesExcludeWaterfall
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the waterfall isn't generated for the rating request (true) or is generated
(false). The default value is false. Available in API version 64.0 and later.
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
854
RatingRequestRate Management

===== PAGE 869 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
Auto-generated identifier for the rating request record.
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
string
RatingProcedureName
Properties
Create, Filter, Group, Sort, Update
Description
Procedure name that's used to rate the aggregated records that are stamped for rating
request.
Type
picklist
Status
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Status of the rating request.
Valid values are:
• Failed
• Pending
• RatingComplete
• RatingInProgress
• ReadyForRating
855
RatingRequestRate Management

===== PAGE 870 =====

Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
RatingRequestFeed
Feed tracking is available for the object.
RatingRequestHistory
History is available for tracked fields of the object.
RatingRequestShare
Sharing is available for the object.
RatingRequestBatchJob
Represents a junction between the rating request and batch job objects. This object is available in API version 62.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
BatchJobId
Properties
Create, Filter, Group, Sort, Update
Description
ID of the batch job that triggered the rating request on the aggregated records.
This field is a relationship field.
Relationship Name
BatchJob
Refers To
BatchJob
Type
picklist
ErrorCode
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Error code that defines the batch job failure.
856
RatingRequestBatchJobRate Management

===== PAGE 871 =====

DetailsField
Valid values are:
• BadRequest
• InternalError
Type
string
ErrorMessage
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Error message that describes the cause of the batch job failure.
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
Name of the rating request batch job record.
Type
reference
RatingRequestId
Properties
Create, Filter, Group, Sort
Description
ID of the rating request record associated with the batch job.
This field is a relationship field.
Relationship Name
RatingRequest
857
RatingRequestBatchJobRate Management

===== PAGE 872 =====

DetailsField
Relationship Type
Master-detail
Refers To
RatingRequest (the master object)
Associated Objects
This object has these associated objects. If the API version isn’t specified, they’re available in the same API versions as this object. Otherwise,
they’re available in the specified API version and later.
RatingRequestBatchJobFeed
Feed tracking is available for the object.
RatingRequestBatchJobHistory
History is available for tracked fields of the object.
Rate Management Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
IndustriesRatingSettings
Represents the settings for Rate Management.
Flow for Rate Management
Represents the metadata associated with a flow. With Flow, you can create an application that takes users through a series of pages
to query and update the records in the database. You can also run logic and provide branching capability based on user input to
build dynamic applications.
IndustriesRatingSettings
Represents the settings for Rate Management.
Parent Type and Manifest Access
This type extends the Metadata metadata type and inherits its fullName field.
In the package manifest, all the settings metadata types for the org are accessed using the “Settings” name. See Settings for more details.
File Suffix and Directory Location
The IndustriesRatingSettings values are stored in the IndustriesRating.settings file in the settings folder.
The .settings  files are different from other named components, because there’s only one settings file for each settings component.
Version
IndustriesRatingSettings components are available in API version 62.0 and later.
858
Rate Management Metadata API TypesRate Management

===== PAGE 873 =====

Special Access Rules
This metadata type is available with Rate Management.
Fields
DescriptionField Name
Field Type
boolean
enableRating
Description
Indicates whether to enable Rate Management (true) or not (false). The default
value is false.
Field Type
boolean
enableRatingWaterfall
Description
Indicates whether to enable Rating Waterfall (true) or not (false). The default
value is false. Rating Waterfall provides insights into the rating data, which you can
synchronize with your rating lookup tables.
Field Type
boolean
enableRatingWaterfallPersistence
Description
Indicates whether to enable Rating Waterfall Persistence (true) or not (false). The
default value is false. Rating Waterfall Persistence stores rating data, which you can
use to enhance the internal processes and increase efficiency.
Declarative Metadata Sample Definition
The following is an example of an IndustriesRatingSettings component.
<IndustriesRatingSettings xmlns="http://soap.sforce.com/2006/04/metadata">
<enableRating>true</enableRating>
<enableRatingWaterfall>true</enableRatingWaterfall>
<enableRatingWaterfallPersistence>true</enableRatingWaterfallPersistence>
</IndustriesRatingSettings>
The following is an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>IndustriesRating</members>
<name>Settings</name>
</types>
<version>66.0</version>
</Package>
859
IndustriesRatingSettingsRate Management

===== PAGE 874 =====

Wildcard Support in the Manifest File
The wildcard character *  (asterisk) in the package.xml manifest file doesn’t apply to metadata types for feature settings. The wildcard
applies only when retrieving all settings, not for an individual setting. For details, see Settings. For information about using the manifest
file, see Deploying and Retrieving Metadata with the Zip File.
Flow for Rate Management
Represents the metadata associated with a flow. With Flow, you can create an application that takes users through a series of pages to
query and update the records in the database. You can also run logic and provide branching capability based on user input to build
dynamic applications.
FlowActionCall
Rate Management exposes additional actionType values for the FlowActionCall metadata type.
DescriptionField TypeField Name
Required.InvocableActionType
(enumeration of
type string)
actionType
The action type. Additional valid values for Rate Management include:
• invokeRatingService— Invoke the rating service to rate the
usage records.
Rate Management Business APIs
Use the Rate Management Business APIs to get rate plan and persisted rating waterfall details.
Resources
Learn more about the available Rate Management API resources.
Response Bodies
Learn more about the available response bodies of Rate Management APIs.
SEE ALSO:
Connect REST API Developer Guide: Introduction
Resources
Learn more about the available Rate Management API resources.
Rate Plan (GET)
Get a rate plan for a specified set of context input. Use this API to retrieve rate cards, rate card entries, and related adjustments based
on the filter criteria for the context input.
860
Flow for Rate ManagementRate Management

===== PAGE 875 =====

Rating Waterfall (GET)
Get the persisted rating waterfall that stores the process logs. Rating waterfall provides insights into the internal rating process.
Rate Plan (GET)
Get a rate plan for a specified set of context input. Use this API to retrieve rate cards, rate card entries, and related adjustments based on
the filter criteria for the context input.
Keep these considerations in mind when you use this API.
• This API request supports one pricebook and one sellable product.
• The ID of the product is required to invoke this API.
• Invoke this API even if a hydrated context is available to fetch the rate card, rate card entry, and adjustment details.
Special Access Rules
The org must have the Rate Management: Run Time User permission set to use this API. Additionally, the org must also have a default
usage rating discovery procedure defined in the Revenue Settings from Setup.
Resource
/connect/core-rating/rate-plan
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-rating/rate-plan
?contextId=858a3ad3e5a0e5c319652a6ab92f6fdb2b4fa8be72b390506d014596c6da62c9&procedure
ApiName=SampleProcedure
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
62.0RequiredID of the context to specify as an input to
the procedure.
StringcontextId
62.0RequiredAPI name of the procedure to be executed.Stringprocedure
ApiName
Response body for GET
Rate Plan Response
Rating Waterfall (GET)
Get the persisted rating waterfall that stores the process logs. Rating waterfall provides insights into the internal rating process.
Resource
/connect/core-pricing/waterfall/lineItemId/executionId
861
ResourcesRate Management

===== PAGE 876 =====

Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/core-pricing/waterfall/Gold/2yHdNNEFOZr9jAe4gHS7?tagsToFilter=UnitPrice&usageType=Rating
Available version
62.0
HTTP methods
GET
Query parameters
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalComma-separated tags to filter.StringtagsToFilter
62.0OptionalUsage type of the waterfall log record.
Valid values are:
StringusageType
• Rating
• Pricing—Specifies that the record
type is Pricing. If this value is
specified, the API creates a log of
pricing waterfall. See Pricing Waterfall.
The default value is Pricing.
Response body for GET
Line Item Waterfall Response
Response Bodies
Learn more about the available response bodies of Rate Management APIs.
Adjustment Details
Output representation of a rate adjustment request.
Line Item Waterfall Response
Output representation of the line item waterfall response.
Rate Plan Response
Output representation of the details of a rate plan.
Rating Error Response
Output representation of the error details related to the API request.
Rating Waterfall Response
Output representation of a rating waterfall request.
862
Response BodiesRate Management

===== PAGE 877 =====

Adjustment Details
Output representation of a rate adjustment request.
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
60.0Small, 60.0Details of the rate element.Map<String,
Object>[]
adjustments
60.0Small, 60.0Description of the rate element.Stringdescription
60.0Small, 60.0Type of the rate element.StringelementType
60.0Small, 60.0Name of the rate element.Stringname
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
"usageType":"Rating",
"output": {
"quantity": "10",
"netUnitPrice": "10",
"subtotal": "100"
},
"waterfall": []
}
863
Response BodiesRate Management

===== PAGE 878 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Context definition version ID of the rating
procedure.
Stringcontext
Definition
VersionId
62.0Small, 62.0Context mapping ID of the record.Stringcontext
MappingId
62.0Small, 62.0Currency code. For example, USD or INR.StringcurrencyCode
62.0Small, 62.0Details of any errors.Rating Error
Response
error
62.0Small, 62.0End timestamp of procedure execution.StringexecutionEnd
Timestamp
62.0Small, 62.0Execution ID of a particular execution of a
rating procedure.
StringexecutionId
62.0Small, 62.0Start timestamp of procedure execution.Stringexecution
Start
Timestamp
62.0Small, 62.0Line item ID for which the price is being
calculated.
StringlineItemId
62.0Small, 62.0Output of the rating procedure.Map<String,
Object>
output
62.0Small, 62.0Indicates whether the API request is
successful (true) or not (false).
Booleansuccess
62.0Small, 62.0Usage type of the waterfall log record.StringusageType
62.0Small, 62.0Details of the rating waterfall.Rating Waterfall
Response[]
waterfall
Rate Plan Response
Output representation of the details of a rate plan.
JSON example
{
"success": true,
"executionId" : "a521d592-71c3-4db3-8048-r64504df1605",
"error": {}
}
864
Response BodiesRate Management

===== PAGE 879 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Error response for the API request, if any.Rating Error
Response[]
error
62.0Small, 62.0ID of the procedure execution record.StringexecutionId
62.0Small, 62.0Indicates whether the request is successful
(true) or not (false)
Booleansuccess
Rating Error Response
Output representation of the error details related to the API request.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Code indicating the type of error.StringerrorCode
62.0Small, 62.0Message stating the reason for error, if any.Stringmessage
Rating Waterfall Response
Output representation of a rating waterfall request.
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
865
Response BodiesRate Management

===== PAGE 880 =====

],
"name": "List Price"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Mappings of field to tag names.Map<String, String>fieldTo
TagName
Mapping
62.0Small, 62.0Parameters of rating element input.Map<String,
Object>
input
Parameters
62.0Small, 62.0Parameters of rating element output.Map<String,
Object>
output
Parameters
62.0Small, 62.0Details of the rate adjustment of a rating
element.
Adjustment Detailspricing
Element
62.0Small, 62.0Sequence of rating element execution.Integersequence
Rate Management Standard Invocable Actions
Learn more about the standard invocable actions available with Rate Management.
Invoke Rating Service Action
Invoke the rating service to rate the usage records.
SEE ALSO:
Actions Developer Guide: Overview
REST API Developer Guide: Invocable Actions Standard
Metadata API Developer Guide: Understanding Metadata API
Invoke Rating Service Action
Invoke the rating service to rate the usage records.
The Invoke Rating Service action acts as a connector between batch management and the rating service. This action is available in API
version 62.0 and later.
Special Access Rules
The Invoke Rating Service action is available in Enterprise, Unlimited, and Developer Editions where Rate Management is enabled.
866
Rate Management Standard Invocable ActionsRate Management

===== PAGE 881 =====

Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/invokeRatingService
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
attributeRateCardID
Description
ID of the rate card that’s used to define adjustments based on the attributes that impact the rate.
Type
string
baseRateCardID
Description
ID of the rate card that includes the base rate for the resource to be rated, based on its
consumption.
Type
string
contextDefinitionId
Description
Required.
ID of the context definition that’s used to create the context instance.
Type
string
contextMappingID
Description
ID of the context mapping that maps a standard object, context definition object, or any other
input data source to the node that’s defined in the context definition.
Type
boolean
isSkipWaterfall
Description
Indicates whether to skip the generation of price waterfall data (true) or not (false).
867
Invoke Rating Service ActionRate Management

===== PAGE 882 =====

DetailsInput
Type
string
procedureName
Description
Name of the rating procedure that’s used to calculate the rates.
Type
reference
recordID
Description
Required.
ID of the usage ratable summary record to be rated.
Type
string
tierRateCardID
Description
ID of the rate card that’s used to define adjustments for different tiers of a resource.
Outputs
None
Example
POST
This example shows a sample request for the Invoke Rating Service action.
{
"inputs": [
{
"recordIDs": "56jSB000002Bn12CXC",
"contextMappingId": "11jSB000002Bn13YAC",
"contextDefinitionId": "11OSB0000000WSv2AM",
"procedureName": "Invoke Rate",
"isSkipWaterfall": false,
"baseRateCardID": "11jSB000002Bn13YAC",
"tierRateCardID": "fgjjSB0sdf987dsf",
"attributeRateCardID": "asdfgh563034lk"
}
]
}
This example shows a sample response for the Invoke Rating Service action.
[
{
"actionName": "invokeRatingService",
"errors": null,
868
Invoke Rating Service ActionRate Management

===== PAGE 883 =====

"isSuccess": true,
"outputValues": {}
}
]
869
Invoke Rating Service ActionRate Management

===== PAGE 884 =====

