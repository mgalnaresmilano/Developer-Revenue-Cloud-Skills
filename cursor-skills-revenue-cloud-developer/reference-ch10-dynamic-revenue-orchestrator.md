---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 10 — Dynamic Revenue Orchestrator

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 10 Dynamic Revenue Orchestrator
EDITIONS
Available in: Enterprise,
Unlimited, and Developer
Editions
Get visibility into a product’s fulfillment journey. Also, get a complete
view of the entire fulfillment design that includes processes such
as order decomposition, fulfillment plans, and jeopardy
management.
In this chapter ...
• Dynamic Revenue
Orchestrator
Standard Objects
• Dynamic Revenue
Orchestrator
Standard Invocable
Actions
• Dynamic Revenue
Orchestrator
Metadata API Types
• Dynamic Revenue
Orchestrator Tooling
API Objects
• Callouts in Dynamic
Revenue
Orchestrator
• Dynamic Revenue
Orchestrator Platform
Events
1673

===== PAGE 1688 =====

Dynamic Revenue Orchestrator Standard Objects
The Dynamic Revenue Orchestrator data model provides objects and fields to manage details of a product’s fulfillment.
AssetFulfillmentDecomp
Represents the relationship between an ordered asset and its corresponding fulfillment asset. This object is available in API version
62.0 and later.
FulfillmentAsset
Represents an instance of a technical product used to provide a customer asset. This object is available in API version 61.0 and later.
FulfillmentAssetAttribute
Represents an attribute of a fulfillment asset. This object is available in API version 61.0 and later.
FulfillmentAssetRelationship
Represents a relationship between two fulfillment assets. This object is available in API version 61.0 and later.
FulfillmentFalloutRule
Represents the fulfillment fallout handling rule. This object is available in API version 61.0 and later.
FulfillmentLineAttribute
Represents an attribute of a fulfillment order line. This object is available in API version 61.0 and later.
FulfillmentLineRel
Represents a relationship between two fulfillment order lines. This object is available in API version 61.0 and later.
FulfillmentLineSourceRel
Represents the relationship between a fulfillment order line and its decomposition source. This object is available in API version 61.0
and later.
FulfillmentPlan
Represents a set of steps to be created to fulfill the order. This object is available in API version 61.0 and later.
FulfillmentStep
Represents a task that's required to perform a certain action as part of order fulfillment. This task can be manual or automated. This
object is available in API version 61.0 and later.
FulfillmentStepDefinition
Represents a definition of a step that must be executed during fulfillment orchestration. This object is available in API version 61.0
and later.
FulfillmentStepDefinitionGroup
Represents a set of fulfillment step definitions. This object is available in API version 61.0 and later.
FulfillmentStepDependency
Represents a dependency between tasks by defining the order between a task and one that depends on it. This object is available
in API version 61.0 and later.
FulfillmentStepDependencyDef
Represents a dependency that must be created between two fulfillment step records. This object is available in API version 62.0 and
later.
FulfillmentStepJeopardyRule
Represents the duration and tolerance for the step in the fulfillment process to allow the overall tracking of rules and risks. This object
is available in API version 61.0 and later.
1674
Dynamic Revenue Orchestrator Standard ObjectsDynamic Revenue Orchestrator

===== PAGE 1689 =====

FulfillmentStepSource
Represents a link between a fulfillment step and the corresponding order lines. This object is available in API version 61.0 and later.
FulfillmentTaskAssignmentRule
Represents a set of actions that assign a task to a user or queue. This object is available in API version 63.0 and later.
FulfillmentWorkspace
Represents a visual designer for fulfillment plans that can have multiple step groups and their dependencies. This object is available
in API version 61.0 and later.
FulfillmentWorkspaceItem
Represents information about the attributes that are used in the definition for a fulfillment step group. This object is available in API
version 61.0 and later.
ProductDecompEnrichmentRule
Represents mappings between fields and attributes. Enrichment rules are part of a decomposition rule, and are used to propagate
data to fulfillment order lines. This object is available in API version 61.0 and later.
ProdtDecompEnrchVarMap
Represents the mapping of a field context tag or an attribute to a variable within an expression set. This object is available in API
version 64.0 and later.
ProductFulfillmentDecompRule
Represents a rule that determines how an order is broken into sub-orders with specific technical details that help in order fulfillment.
It can be applied to a commercial or a technical product. This object is available in API version 61.0 and later.
ProductFulfillmentScenario
Represents a link between a product and the corresponding group of fulfillment steps that's necessary to fulfill that product. This
object is available in API version 61.0 and later.
SalesTrxnDeleteEvent
Represents the platform event that triggers the deletion of sales transaction fulfillment request records when the corresponding
reference records are deleted. This object is available in API version 64.0 and later.
SalesTransactionFulfillReq
Represents the statuses of all the sub-orders that belong to the selected commercial or technical product. This object is available in
API version 62.0 and later.
ValTfrm
Represents mappings between fields and attributes. Enrichment rules are part of a decomposition rule, and are used to propagate
data to fulfillment order lines. This object is available in API version 61.0 and later.
ValTfrmGrp
Represents a rule that determines how an order is broken into sub-orders with specific technical details that help in order fulfillment.
The rule can be applied to a commercial or a technical product. This object is available in API version 61.0 and later.
SEE ALSO:
Object Reference for the Salesforce Platform: Overview of Salesforce Objects and Fields
SOAP API Developer Guide: Introduction to SOAP API
AssetFulfillmentDecomp
Represents the relationship between an ordered asset and its corresponding fulfillment asset. This object is available in API version 62.0
and later.
1675
AssetFulfillmentDecompDynamic Revenue Orchestrator

===== PAGE 1690 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
FulfillmentSourceAssetId
Properties
Create, Filter, Group, Sort, Update
Description
The identifier of the relationship between an asset and a fulfillment asset.
This field is a polymorphic relationship field.
Relationship Name
FulfillmentSourceAsset
Refers To
Asset, FulfillmentAsset
Type
reference
FulfillmentTargetAssetId
Properties
Create, Filter, Group, Sort, Update
Description
The identifier of the target asset that's being fulfilled.
This field is a relationship field.
Relationship Name
FulfillmentTargetAsset
Refers To
FulfillmentAsset
Type
boolean
IsUsedForFulfmtAssetActivation
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates if internal jobs are allowed to activate the related fulfillment asset. The default value
is true.
This field is available in API version 6.0 and later.
1676
AssetFulfillmentDecompDynamic Revenue Orchestrator

===== PAGE 1691 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the asset that's being fulfilled.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the user who created the request record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
picklist
RelationshipType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of relationship between an asset and a fulfillment asset.
Valid values are:
• SourceBundleRoot
• SourceLineItem
Type
string
SegmentIdentifier
Properties
Create, Group, Nillable, Sort,
Description
The ID of the ramp segment associated with the asset state period.
This field is available in API version 63.0 and later in orgs that have Revenue Cloud when the
Ramp Deals setting is enabled.
Type
picklist
Status
1677
AssetFulfillmentDecompDynamic Revenue Orchestrator

===== PAGE 1692 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The status of the fulfillment asset.
Valid values are:
• Active
• Inactive
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
AssetFulfillmentDecompHistory on page 2734
History is available for tracked fields of the object starting API version 65.0.
AssetFulfillmentDecompShare on page 2738
Sharing is available for the object.
FulfillmentAsset
Represents an instance of a technical product used to provide a customer asset. This object is available in API version 61.0 and later.
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
Description
The identifier of the account.
This field is a relationship field.
Relationship Name
Account
Relationship Type
Lookup
1678
FulfillmentAssetDynamic Revenue Orchestrator

===== PAGE 1693 =====

DetailsField
Refers To
Account
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
For internal use only.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
For internal use only.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the fulfillment asset.
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
Relationship Type
Lookup
Refers To
Group, User
Type
reference
ProductId
Properties
Create, Filter, Group, Sort, Update
1679
FulfillmentAssetDynamic Revenue Orchestrator

===== PAGE 1694 =====

DetailsField
Description
The identifier of the corresponding product.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Type
double
Quantity
Properties
Create, Filter, Nillable, Sort, Update
Description
For internal use only.
Type
string
ScopeIdentifierText
Properties
Create, Filter, Group, idLookup, Nillable, Sort
Description
The scope in which this fulfillment asset record is created. This field is available in API version
65.0 and later.
Type
picklist
Status
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The status of the fulfillment asset.
Valid values are:
• Active
• InActive
Type
reference
UnitOfMeasureId
Properties
Create, Filter, Group, Nillable, Sort
1680
FulfillmentAssetDynamic Revenue Orchestrator

===== PAGE 1695 =====

DetailsField
Description
The unit of measure for the asset quantity such as, unit, gallon, ton, or case. This field is
available in API version 63.0 and later.
This field is a relationship field.
Relationship Name
UnitOfMeasure
Refers To
UnitOfMeasure
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentAssetHistory on page 2734
History is available for tracked fields of the object starting API version 65.0.
FulfillmentAssetShare on page 2738
Sharing is available for the object.
FulfillmentAssetAttribute
Represents an attribute of a fulfillment asset. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), query(), update(), upsert()
Fields
DetailsField
Type
reference
AttributeDefinitionId
Properties
Create, Filter, Group, Sort, Update
Description
The attribute definition in the catalog.
This field is a relationship field.
Relationship Name
AttributeDefinition
1681
FulfillmentAssetAttributeDynamic Revenue Orchestrator

===== PAGE 1696 =====

DetailsField
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
The name of the attribute.
Type
reference
AttributePicklistValueId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
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
The value of the attribute.
Type
string
ExternalId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
1682
FulfillmentAssetAttributeDynamic Revenue Orchestrator

===== PAGE 1697 =====

DetailsField
Type
reference
FulfillmentAssetId
Properties
Create, Filter, Group, Sort
Description
The identifier of the fulfillment asset.
This field is a relationship field.
Relationship Name
FulfillmentAsset
Relationship Type
Master-detail
Refers To
FulfillmentAsset (the master object)
FulfillmentAssetRelationship
Represents a relationship between two fulfillment assets. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
AssociatedFulfillAssetRole
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The role of the associated fulfillment asset.
Valid values are:
• BundleComponent
• ClassificationComponent—Product Classification Component
1683
FulfillmentAssetRelationshipDynamic Revenue Orchestrator

===== PAGE 1698 =====

DetailsField
Type
reference
AssociatedFulfillmentAssetId
Properties
Create, Filter, Group, Sort, Update
Description
The name of the associated fulfillment asset.
This field is a relationship field.
Relationship Name
AssociatedFulfillmentAsset
Refers To
FulfillmentAsset
Type
reference
MainFulfillmentAssetId
Properties
Create, Filter, Group, Sort
Description
The name of the primary fulfillment asset.
This field is a relationship field.
Relationship Name
MainFulfillmentAsset
Relationship Type
Master-detail
Refers To
FulfillmentAsset (the master object)
Type
picklist
MainFulfillmentAssetRole
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The role of the primary fulfillment asset.
Valid value is Bundle Parent.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the fulfillment asset relationship.
1684
FulfillmentAssetRelationshipDynamic Revenue Orchestrator

===== PAGE 1699 =====

DetailsField
Type
reference
ProductRelationshipTypeId
Properties
Create, Filter, Group, Sort, Update
Description
The type of relationship between two assets.
This field is a relationship field.
Relationship Name
ProductRelationshipType
Refers To
ProductRelationshipType
FulfillmentFalloutRule
Represents the fulfillment fallout handling rule. This object is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
ErrorCode
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The failure error code of the fulfillment step that's associated with the rule.
Type
reference
FalloutQueueId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The fallout queue that's associated with the fallout task. This field is available in API version
62.0 and later.
This field is a relationship field.
1685
FulfillmentFalloutRuleDynamic Revenue Orchestrator

===== PAGE 1700 =====

DetailsField
Relationship Name
FalloutQueue
Refers To
Group
Type
string
FlowDefinitionName
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The name of the flow definition that's associated with the AutoTask  type of fulfillment
step.
Type
reference
IntegrationDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The integration definition that's associated with the Callout  type of fulfillment step.
This field is a relationship field.
Relationship Name
IntegrationDefinition
Relationship Type
Lookup
Refers To
IntegrationProviderDef
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record.
1686
FulfillmentFalloutRuleDynamic Revenue Orchestrator

===== PAGE 1701 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the flow definition that's associated with the AutoTask  type of fulfillment
step.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the user who created the fulfillment record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
int
RetriesAllowed
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The maximum number of times a retry policy is run before the fulfillment step is considered
failed.
Type
string
RetryIntervals
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The interval after which the selected retry policy is run when the fulfillment step fails. This
field is available in API version 62.0 and later.
Type
picklist
RetryPolicy
1687
FulfillmentFalloutRuleDynamic Revenue Orchestrator

===== PAGE 1702 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the retry policy used when the fulfillment step fails.
Valid value is:
• Immediate
• Monotonous
• Staggered
Type
picklist
StepType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the type of fulfillment step associated with the fallout rule.
Valid values are:
• AutoTask
• Callout
• ManualTask
• Milestone
• Pause
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentFalloutRuleHistory on page 2734
History is available for tracked fields of the object.
FulfillmentFalloutRuleShare on page 2738
Sharing is available for the object.
FulfillmentLineAttribute
Represents an attribute of a fulfillment order line. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), query(), update(), upsert()
1688
FulfillmentLineAttributeDynamic Revenue Orchestrator

===== PAGE 1703 =====

Fields
DetailsField
Type
reference
AttributeDefinitionId
Properties
Create, Filter, Group, Sort, Update
Description
A unique identifier for the attribute definition in the catalog.
This field is a relationship field.
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
The name of the attribute.
Type
reference
AttributePicklistValueId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
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
The value of the attribute.
1689
FulfillmentLineAttributeDynamic Revenue Orchestrator

===== PAGE 1704 =====

DetailsField
Type
string
ExternalId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID that uniquely identifies the relationship in an external data source.
Type
reference
FulfillmentOrderLineItemId
Properties
Create, Filter, Group, Sort
Description
A unique identifier for the fulfillment order line item.
This field is a relationship field.
Relationship Name
FulfillmentOrderLineItem
Relationship Type
Master-detail
Refers To
FulfillmentOrderLineItem (the master object)
FulfillmentLineRel
Represents a relationship between two fulfillment order lines. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
AssociatedFoItemInventory
Properties
Filter, Group, Restricted picklist, Sort
1690
FulfillmentLineRelDynamic Revenue Orchestrator

===== PAGE 1705 =====

DetailsField
Description
Inventory level for the associated fulfillment order item.
Valid values are:
• Included in Main Inventory
• Not Included in Main Inventory
This field is available in API version 63.0 and later.
Type
reference
AssociatedFulfillOrderItemId
Properties
Create, Filter, Group, Sort, Update
Description
The identifier of the associated fulfillment order line item.
This field is a relationship field.
Relationship Name
AssociatedFulfillOrderItem
Refers To
FulfillmentOrderLineItem
Type
picklist
AssociatedLineRole
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The role of the associated fulfillment order line item.
Valid values are:
• BundleComponent
• ClassificationComponent—Product Classification Component
Type
picklist
AssociatedQuanScaleMethod
Properties
Filter, Group, Restricted picklist, Sort
Description
Method used to scale the quantity of the associated order item summary relative to the main
fulfillment order item.
Valid values are:
• Constant
• Proportional
1691
FulfillmentLineRelDynamic Revenue Orchestrator

===== PAGE 1706 =====

DetailsField
The default value is Proportional.
This field is available in API version 63.0 and later.
Type
reference
FulfillmentOrderId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the parent fulfillment order.
This field is a relationship field.
Relationship Name
FulfillmentOrder
Refers To
FulfillmentOrder
Type
picklist
MainFulfillOrderItemRole
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The role of the primary fulfillment order line item.
Valid value is Bundle.
Type
reference
MainFulfillmentOrderItemId
Properties
Create, Filter, Group, Sort
Description
The ID of the associated fulfillment order line item.
This field is a relationship field.
Relationship Name
MainFulfillmentOrderItem
Relationship Type
Master-detail
Refers To
FulfillmentOrderLineItem (the master object)
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
1692
FulfillmentLineRelDynamic Revenue Orchestrator

===== PAGE 1707 =====

DetailsField
Description
The name of the fulfillment order line relationship.
Type
reference
ProductRelationshipTypeId
Properties
Create, Filter, Group, Sort, Update
Description
The type of relationship between two assets.
This field is a relationship field.
Relationship Name
ProductRelationshipType
Refers To
ProductRelationshipType
FulfillmentLineSourceRel
Represents the relationship between a fulfillment order line and its decomposition source. This object is available in API version 61.0
and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
Action
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Specifies the action to be performed on the asset fulfillment decomposition record. This field
is available in API version 66.0 and later.
Possible values are:
• Add
• Cancel
• NoChange—No Change
1693
FulfillmentLineSourceRelDynamic Revenue Orchestrator

===== PAGE 1708 =====

DetailsField
Type
reference
FulfilmentOrderLineId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the fulfillment order line.
This field is a relationship field.
Relationship Name
FulfilmentOrderLine
Refers To
FulfillmentOrderLineItem
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The relation between the two order line sources.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the user who created the relationship record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
string
SourceItemIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
The ID of the decomposition source that's related to the fulfilment order line. This field is
available in API version 64.0 and later.
Type
reference
SourceLineItemId
1694
FulfillmentLineSourceRelDynamic Revenue Orchestrator

===== PAGE 1709 =====

DetailsField
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the source line item.
This field is a polymorphic relationship field.
Relationship Name
SourceLineItem
Refers To
FulfillmentOrderLineItem, OrderItem
Type
picklist
SourceType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of source for the line item.
Valid values are:
• SourceBundleRoot
• SourceLineItem
Type
picklist
SupplementalAction
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
The supplemental action that's applied to the line item based on the run-time changes made
to the original fulfillment request. This field is available in API version 62.0 and later.
Valid values are:
• Add
• Amend
• Cancel
• NoChange
Type
string
UniqueIdentifier
Properties
Create, Filter, Group, Nillable, Sort
Description
For internal use only.
1695
FulfillmentLineSourceRelDynamic Revenue Orchestrator

===== PAGE 1710 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentLineSourceRelShare on page 2738
Sharing is available for the object.
FulfillmentPlan
Represents a set of steps to be created to fulfill the order. This object is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
ExecutionUserId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
Relationship Name
ExecutionUser
Refers To
User
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record.
1696
FulfillmentPlanDynamic Revenue Orchestrator

===== PAGE 1711 =====

DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the fulfillment plan.
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
picklist
Priority
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The priority of the fulfillment plan execution. This field is available in API version 63.0 and
later.
Valid values are:
• Default
• High
• Bulk
Type
string
SourceIdentifier
Properties
Create, Filter, Group, Nillable, Sort, Update, idLookup (Available in API version 64.0 and later)
Description
For internal use only.
Type
string
SourceType
1697
FulfillmentPlanDynamic Revenue Orchestrator

===== PAGE 1712 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort
Description
The type of source for the fulfillment plan. This field is available in API version 62.0 and later.
Type
picklist
State
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The status of the fulfillment plan.
Valid values are:
• Completed
• InProgress
• NotStarted
Type
picklist
UsageType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The business that uses Fulfillment Orchestration.
Valid values are:
• IntegrationOrchestrator
• OrderFulfillment
• StageManagement
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentPlanChangeEvent on page 2725
Change events are available for the object.
FulfillmentPlanHistory on page 2734
History is available for tracked fields of the object starting API version 65.0.
FulfillmentPlanShare on page 2738
Sharing is available for the object.
1698
FulfillmentPlanDynamic Revenue Orchestrator

===== PAGE 1713 =====

FulfillmentStep
Represents a task that's required to perform a certain action as part of order fulfillment. This task can be manual or automated. This object
is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
dateTime
ActualCompletionDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the fulfillment step state changed to Completed  or Skipped.
Type
dateTime
ActualStartDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the fulfillment step state changed to Ready.
Type
reference
AssignedToId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The user or queue associated with the fulfillment step.
This field is a polymorphic relationship field.
Relationship Name
AssignedTo
Relationship Type
Lookup
Refers To
Queue, User
Type
reference
CompensatedStepId
1699
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1714 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort
Description
The alternative step that's executed when a particular step in the fulfillment plan is amended
or canceled.
This field is a relationship field. This field is available in API version 62.0 and later.
Relationship Name
CompensatedStep
Refers To
FulfillmentStep
Type
int
DelayOf
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The value of the delay. This field is available in API version 63.0 and later.
Type
picklist
DelayUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The unit for the delay of the fulfillment step. This field is available in API version 63.0 and
later.
Valid values are:
• Days
• Hours
• Minutes
Type
picklist
ExecuteOn
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies when to execute the fulfillment step. This field is available in API version 63.0 and
later.
Valid values are:
• PreviousStepExecutionDate
• SourceLineStartDate
1700
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1715 =====

DetailsField
Type
reference
ExecuteOnRuleId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The name of the expression set. The fulfillment step is executed only when its corresponding
expression set returns the value true.
This field is a polymorphic relationship field.
Relationship Name
ExecuteOnRule
Relationship Type
Lookup
Refers To
ExpressionSet
Type
string
ExecutionMessage
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
Type
reference
FalloutQueueId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The fallout queue that's associated with the fallout task. This field is available in API version
62.0 and later.
This field is a relationship field.
Relationship Name
FalloutQueue
Refers To
Group
Type
string
FlowDefinitionName
Properties
Create, Filter, Group, Nillable, Sort, Update
1701
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1716 =====

DetailsField
Description
The name of the flow definition that's associated with the AutoTask  type of fulfillment
step. This field is available in API version 62.0 and later.
Type
reference
FlowInterviewId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The flow interview associated with the fulfillment step.
This field is a relationship field.
Relationship Name
FlowInterview
Relationship Type
Lookup
Refers To
FlowInterview
Type
picklist
ForcePlanFreezeDuringExecution
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether to freeze the plan while the step is in progress. If enabled, specifies how
to complete the step before resuming the plan. This field is available in API version 63.0 and
later.
Valid values are:
• Never
• YesButWaitForStepCompletion
The default value is Never.
Type
reference
FulfillmentPlanId
Properties
Create, Filter, Group, Sort, Update
Description
The fulfillment plan associated with the fulfillment step.
This field is a relationship field.
Relationship Name
FulfillmentPlan
1702
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1717 =====

DetailsField
Relationship Type
Lookup
Refers To
FulfillmentPlan
Type
reference
FulfillmentStepDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The fulfillment step definition associated with the fulfillment step.
This field is a relationship field.
Relationship Name
FulfillmentStepDefinition
Relationship Type
Lookup
Refers To
FulfillmentStepDefinition
Type
reference
IntegrationDefinitionNameId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
This field is a relationship field.
Relationship Name
IntegrationDefinitionName
Relationship Type
Lookup
Refers To
IntegrationProviderDef
Type
boolean
IsSkipBranch
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the remaining steps in the fulfillment step group are skipped from execution
when the Execute On Rule condition is set (true) or not (false). This field is available in
API version 62.0 and later.
1703
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1718 =====

DetailsField
The default value is false.
Type
string
JeopardyStatus
Properties
Filter, Group, Nillable, Sort
Description
The jeopardy status of the fulfillment step.
This field is a calculated field.
Type
int
JeopardyThreshold
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The number of days, hours, minutes, or seconds, counting back from the expected duration,
before a fulfillment step is in jeopardy.
Type
picklist
JeopardyThresholdUnit
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The time unit of the jeopardy threshold.
Valid values are:
• Days
• Hours
• Minutes
• Seconds
The default value is Minutes.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
1704
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1719 =====

DetailsField
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the fulfillment step.
Type
dateTime
NextEarliestRunTime
Properties
Create, Filter, Nillable, Sort, Update
Description
The next available time for the process execution. This field is available in API version 62.0
and later.
Type
string
OmniscriptName
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For inyternal use only.
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
Relationship Type
Lookup
Refers To
Group, User
1705
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1720 =====

DetailsField
Type
dateTime
PlannedCompletionDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time Dynamic Revenue Orchestrator estimates that the fulfillment step will
complete.
Type
dateTime
PlannedStartDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time when the Dynamic Revenue Orchestrator calculates the fulfillment step
state change to Ready.
Type
multipicklist
PointOfNoReturn
Properties
Create, Filter, Nillable
Description
The type of source change applied to the line item. This field is available in API version 62.0
and later.
Valid value is:
• Changes Denied
Type
dateTime
RequestedCompletionDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The planned completion date and time of the fulfillment step.
Type
dateTime
RequestedStartDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The planned start date and time of the fulfillment step.
1706
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1721 =====

DetailsField
Type
reference
ResumeOnRuleId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The rule set or expression set for the fulfillment step. The step is completed only when the
corresponding expression set returns the isExecuteStep  output as true.
This field is a polymorphic relationship field.
Relationship Name
ResumeOnRule
Relationship Type
Lookup
Refers To
ExpressionSet
Type
int
RetryAttempts
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The number of attempts allowed for retry as set up in the Fallout Qualification Rule table.
Type
reference
RunAsUserId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Overrides user context for an automated step. The default user context is AutomatedProc
user.
This field is a relationship field.
Relationship Name
RunAsUser
Relationship Type
Lookup
Refers To
User
Type
picklist
State
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
1707
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1722 =====

DetailsField
Description
The state of the fulfillment step. For example, In Progress  or Completed.
Valid values are:
• Completed
• Failed
• FatallyFailed
• InProgress
• Pending
• Ready
• Scheduled
• Skipped
Type
picklist
StepType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The fulfillment step type associated with the fulfillment step.
Valid values are:
• AutoTask
• Callout
• ManualTask
• Milestone
• Pause
• StagedAssetize—Available in API version 63.0 and later.
Type
picklist
TaskAllocationType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The method of assigning the manual step. This field is available in API version 63.0 and later.
Valid values are:
• ContextBased
• LeastLoaded
• RoundRobin
Type
reference
TaskId
1708
FulfillmentStepDynamic Revenue Orchestrator

===== PAGE 1723 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the task assigned to a user or queue. This field is available in API version 63.0 and
later.
This field is a relationship field.
Relationship Name
Task
Refers To
Task
Type
picklist
UsageType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The details about the business that uses Fulfillment Orchestration. Some examples of UsageBy
include Financial Services Cloud and CPQ.
Valid values are:
• Fulfillment
• InsuranceRuleAction
• IntegrationOrchestrator
• OrderFulfillment
• StageManagement
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentStepChangeEvent on page 2725
Change events are available for the object.
FulfillmentStepHistory on page 2734
History is available for tracked fields of the object.
FulfillmentStepShare on page 2738
Sharing is available for the object.
FulfillmentStepDefinition
Represents a definition of a step that must be executed during fulfillment orchestration. This object is available in API version 61.0 and
later.
1709
FulfillmentStepDefinitionDynamic Revenue Orchestrator

===== PAGE 1724 =====

Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
AmendGroupId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The fulfillment step group that's added to the fulfillment plan when the step is amended.
This field is available in API version 62.0 and later.
This field is a relationship field.
Relationship Name
AmendGroup
Refers To
FulfillmentStepDefinitionGroup
Type
reference
AssignedToId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The user or queue associated with the fulfillment step definition.
This field is a polymorphic relationship field.
Relationship Name
AssignedTo
Relationship Type
Lookup
Refers To
Queue, User
Type
reference
CancelledGroupId
Properties
Create, Filter, Group, Nillable, Sort, Update
1710
FulfillmentStepDefinitionDynamic Revenue Orchestrator

===== PAGE 1725 =====

DetailsField
Description
The fulfillment step group that's added to the fulfillment plan when the step is canceled.
This field is available in API version 62.0 and later.
This field is a relationship field.
Relationship Name
CancelledGroup
Refers To
FulfillmentStepDefinitionGroup
Type
string
CustomBaseExecutionDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The context tag containing a custom date that's used to calculate the execution time for a
future-dated step. This field is available in API version 65.0 and later.
Type
string
CustomFulfillmentScope
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The custom scope to use during order fulfillment. This field is available in API version 65.0
and later.
Type
int
DelayOf
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The value of the delay. This field is available in API version 63.0 and later.
Type
picklist
DelayUnit
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The unit for the delay of the fulfillment step. This field is available in API version 63.0 and
later.
Valid values are:
• Days
1711
FulfillmentStepDefinitionDynamic Revenue Orchestrator

===== PAGE 1726 =====

DetailsField
• Hours
• Minutes
Type
picklist
ExecuteOn
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies when to execute the fulfillment step. This field is available in API version 63.0 and
later.
Valid values are:
• PreviousStepsStartDate
• SourceLineStartDate
Type
textarea
ExecuteOnConditionData
Properties
Create, Nillable, Update
Description
The condition for executing the fulfillment step. The condition is defined as a rule or a set of
rules in JSON format. This field is available in API version 66.0 and later.
Type
reference
ExecuteOnRuleId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The expression set for the fulfillment step. The step is executed only when the corresponding
expression set is true.
This field is a polymorphic relationship field.
Relationship Name
ExecuteOnRule
Relationship Type
Lookup
Refers To
ExpressionSet
Type
string
FlowDefinitionName
Properties
Create, Filter, Group, Nillable, Sort, Update
1712
FulfillmentStepDefinitionDynamic Revenue Orchestrator

===== PAGE 1727 =====

DetailsField
Description
The name of the associated flow.
Type
picklist
ForcePlanFreezeDuringExecution
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether to freeze the plan while the step is in progress. If enabled, specifies how
to complete the step before resuming the plan. This field is available in API version 63.0 and
later.
Valid values are:
• Never
• YesButForcefullyCompleteStep
The default value is Never.
Type
reference
IntegrationDefinitionNameId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The name of the integration definition that’s used to set up communication with an external
endpoint.
This field is a relationship field.
Relationship Name
IntegrationDefinitionName
Relationship Type
Lookup
Refers To
IntegrationProviderDef
Type
boolean
IsSkipBranch
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the remaining steps in the fulfillment step group are skipped from execution
when the Execute On Rule condition is set. This field is available in API version 62.0 and later.
The default value is false.
1713
FulfillmentStepDefinitionDynamic Revenue Orchestrator

===== PAGE 1728 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the fulfillment step definition.
Type
string
OmniscriptName
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
Type
multipicklist
PointOfNoReturn
Properties
Create, Filter, Nillable, Update
Description
The type of source change applied to the line item. This field is available in API version 62.0
and later.
Valid value is:
• Changes Denied
Type
textarea
ResumeOnConditionData
1714
FulfillmentStepDefinitionDynamic Revenue Orchestrator

===== PAGE 1729 =====

DetailsField
Properties
Create, Nillable, Update
Description
The condition for resuming the paused fulfillment step. The condition is defined as a rule or
a set of rules in JSON format. This field is available in API version 66.0 and later.
Type
reference
ResumeOnRuleId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The expression set for the fulfillment step definition. The step is completed when the
expression set is true.
This field is a polymorphic relationship field.
Relationship Name
ResumeOnRule
Relationship Type
Lookup
Refers To
ExpressionSet
Type
reference
RunAsUserId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The user context to run a fulfillment step when the fulfillment operator wants to override
the default autoproc user.
This field is a relationship field.
Relationship Name
RunAsUser
Relationship Type
Lookup
Refers To
User
Type
picklist
Scope
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
1715
FulfillmentStepDefinitionDynamic Revenue Orchestrator

===== PAGE 1730 =====

DetailsField
Description
The scope of the fulfillment step definition. For example, Bundle  or Order.
Valid values are:
• Bundle
• CrossPlan
• LineItem
• Plan
The default value is Plan.
Type
reference
StepDefinitionGroupId
Properties
Create, Filter, Group, Sort, Update
Description
For internal use only.
This field is a relationship field.
Relationship Name
StepDefinitionGroup
Relationship Type
Master-detail
Refers To
FulfillmentStepDefinitionGroup (the master object)
Type
picklist
StepType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
For internal use only.
Valid values are:
• AutoTask
• Callout
• ManualTask
• Milestone
• Pause
• StagedAssetize
Type
picklist
TaskAllocationType
1716
FulfillmentStepDefinitionDynamic Revenue Orchestrator

===== PAGE 1731 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The method of assigning the manual step. This field is available in API version 62.0 and later.
Valid value is:
• RoundRobin
• LeastLoaded
• ContextBased
Type
picklist
UsageType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The business vertical that uses fulfillment orchestration. For example, Financial Services Cloud.
Valid values are:
• IntegrationOrchestrator
• OrderFulfillment
• StageManagement
FulfillmentStepDefinitionGroup
Represents a set of fulfillment step definitions. This object is available in API version 61.0 and later.
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
The most recent date when a user referenced this record.
1717
FulfillmentStepDefinitionGroupDynamic Revenue Orchestrator

===== PAGE 1732 =====

DetailsField
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the fulfillment step definition group.
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
picklist
UsageType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The business that uses Fulfillment Orchestration.
Possible values are:
• IntegrationOrchestrator
• OrderFulfillment
• StageManagement
• InsuranceRuleAction
1718
FulfillmentStepDefinitionGroupDynamic Revenue Orchestrator

===== PAGE 1733 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentStepDefinitionGroupHistory on page 2734
History is available for tracked fields of the object.
FulfillmentStepDefinitionGroupShare on page 2738
Sharing is available for the object.
FulfillmentStepDependency
Represents a dependency between tasks by defining the order between a task and one that depends on it. This object is available in API
version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
DependencyDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The name of the fulfillment step dependency definition.
This field is a relationship field.
Relationship Name
DependencyDefinition
Refers To
FulfillmentStepDependencyDef
Type
reference
DependentStepId
Properties
Create, Filter, Group, Sort
Description
The name of a fulfillment step that depends on this step.
This field is a relationship field.
1719
FulfillmentStepDependencyDynamic Revenue Orchestrator

===== PAGE 1734 =====

DetailsField
Relationship Name
DependentStep
Relationship Type
Master-detail
Refers To
FulfillmentStep
Type
reference
DependsOnStepId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The name of the fulfillment step that this step depends on. That is, the name of the step that
must be executed before this one can run.
This field is a relationship field.
Relationship Name
DependsOnStep
Refers To
FulfillmentStep
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
An automatically generated name for the fulfillment step dependency.
FulfillmentStepDependencyDef
Represents a dependency that must be created between two fulfillment step records. This object is available in API version 62.0 and
later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
1720
FulfillmentStepDependencyDefDynamic Revenue Orchestrator

===== PAGE 1735 =====

Fields
DetailsField
Type
picklist
DependencyScope
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The scope of the fulfillment step dependency definition. For example, Order or Order Item.
Valid values are:
• Bundle
• LineItem
• Plan
• CrossPlan
• Custom
The default value is Plan.
Type
reference
DependsOnStepDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The fulfillment step definition that must be executed before this step.
This field is a relationship field.
Relationship Name
DependsOnStepDefinition
Refers To
FulfillmentStepDefinition
Type
reference
FulfillmentStepDefinitionId
Properties
Create, Filter, Group, Sort
Description
The identifier of the fulfillment step definition.
This field is a relationship field.
Relationship Name
FulfillmentStepDefinition
Relationship Type
Master-detail
1721
FulfillmentStepDependencyDefDynamic Revenue Orchestrator

===== PAGE 1736 =====

DetailsField
Refers To
FulfillmentStepDefinition (the master object)
Type
boolean
IsCompensateInReverse
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the order to insert the compensated group steps is reversed when a
fulfillment step is canceled (true) or not (false).
The default value is false. This field is available in API version 63.0 and later.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the fulfillment step dependency definition.
Type
picklist
PropagateStateToDependentStep
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The state that’s propagated to the dependent fulfillment step when the source fulfillment
step is amended or canceled in the fulfillment plan.
Valid values are:
• Amended
• Both
• Canceled
• None
This field is available in API version 63.0 and later.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentStepDependencyDefChangeEvent on page 2725
Change events are available for the object.
1722
FulfillmentStepDependencyDefDynamic Revenue Orchestrator

===== PAGE 1737 =====

FulfillmentStepDependencyDefFeed on page 2727
Feed tracking is available for the object.
FulfillmentStepDependencyDefHistory on page 2734
History is available for tracked fields of the object.
FulfillmentStepDependencyDefOwnerSharingRule on page 2736
Sharing rules are available for the object.
FulfillmentStepDependencyDefShare on page 2738
Sharing is available for the object.
FulfillmentStepJeopardyRule
Represents the duration and tolerance for the step in the fulfillment process to allow the overall tracking of rules and risks. This object
is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
int
EstimatedDuration
Properties
Create, Filter, Group, Sort, Update
Description
The estimated time to complete the fulfillment step.
Type
picklist
EstimatedDurationUnit
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The unit of measurement that applies to the estimated time to complete the fulfillment step.
Valid values are:
• Days
• Hours
• Minutes
• Seconds
The default value is Minutes.
1723
FulfillmentStepJeopardyRuleDynamic Revenue Orchestrator

===== PAGE 1738 =====

DetailsField
Type
string
FlowDefinition
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The flow definition that's associated with the AutoTask  type of the fulfillment step.
Type
reference
IntegrationDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The integration definition that's associated with the Callout  type of the fulfillment step.
This field is a relationship field.
Relationship Name
IntegrationDefinition
Relationship Type
Lookup
Refers To
IntegrationProviderDef
Type
int
JeopardyThreshold
Properties
Create, Filter, Group, Sort, Update
Description
The value indicating the threshold after which the fulfillment step is in jeopardy.
Type
picklist
JeopardyThresholdUnit
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The unit of measurement that applies to the jeopardy threshold value.
Valid values are:
• Days
• Hours
• Minutes
• Seconds
The default value is Minutes.
1724
FulfillmentStepJeopardyRuleDynamic Revenue Orchestrator

===== PAGE 1739 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
For internal use only.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
For internal use only.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
For internal use only.
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
Relationship Type
Lookup
Refers To
Group, User
Type
picklist
StepType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of fulfillment step that's affected by the jeopardy rule.
1725
FulfillmentStepJeopardyRuleDynamic Revenue Orchestrator

===== PAGE 1740 =====

DetailsField
Valid values are:
• AutoTask
• Callout
• ManualTask
• Milestone
• Pause
FulfillmentStepSource
Represents a link between a fulfillment step and the corresponding order lines. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
An automatically generated name for the fulfillment step source.
Type
string
SourceIdentifier
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The identifier of the source order line item (order item or fulfillment order line).
Type
reference
SourceLineItemId
Properties
Create, Filter, Group, Nillable, Sort, Update
1726
FulfillmentStepSourceDynamic Revenue Orchestrator

===== PAGE 1741 =====

DetailsField
Description
For internal use only.
This field is a polymorphic relationship field.
Relationship Name
SourceLineItem
Refers To
FulfillmentOrderLineItem, OrderItem
Type
reference
StepId
Properties
Create, Filter, Group, Sort
Description
The identifier of the fulfillment step.
This field is a relationship field.
Relationship Name
Step
Relationship Type
Master-detail
Refers To
FulfillmentStep (the master object)
Type
string
VersionGroupIdentifier
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the version group that's assigned to the fulfillment step source item. This field is
available in API version 64.0 and later.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentStepSourceChangeEvent on page 2725
Change events are available for the object.
FulfillmentTaskAssignmentRule
Represents a set of actions that assign a task to a user or queue. This object is available in API version 63.0 and later.
1727
FulfillmentTaskAssignmentRuleDynamic Revenue Orchestrator

===== PAGE 1742 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
textarea
ConditionData
Properties
Create, Nillable, Update
Description
The condition for executing the fulfillment task assignment rule. The condition is defined as
a rule or a set of rules in JSON format. This field is available in API version 66.0 and later.
Type
reference
ConditionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Condition ID that's used to determine the task assignment.
This field is a polymorphic relationship field.
Relationship Name
Condition
Refers To
ExpressionSet
Type
reference
DestinationId
Properties
Create, Filter, Group, Sort, Update
Description
Destination ID of the task assignment such as, Queue or User.
This field is a polymorphic relationship field.
Relationship Name
Destination
Refers To
Group, User
Type
dateTime
LastReferencedDate
1728
FulfillmentTaskAssignmentRuleDynamic Revenue Orchestrator

===== PAGE 1743 =====

DetailsField
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the object that specifies the condition used to determine the task assignment.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the user who created the task assignment rule record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
int
Priority
Properties
Create, Filter, Group, Sort, Update
Description
The priority of the rule for execution.
Type
reference
SourceId
1729
FulfillmentTaskAssignmentRuleDynamic Revenue Orchestrator

===== PAGE 1744 =====

DetailsField
Properties
Create, Filter, Group, Sort, Update
Description
Source ID of the task assignment such as Queue.
This field is a relationship field.
Relationship Name
Source
Refers To
Group
Type
picklist
TaskAllocationType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The method of assigning the manual step.
Valid values are:
• ContextBased
• LeastLoaded
• RoundRobin
Type
picklist
UsageType
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Name of the usage type.
Possible values are:
• Fulfillment
• Generic
• InsuranceRuleAction—Insurance Rule Action
• IntegrationOrchestrator—Integration Orchestrator
• StageManagement—Stage Management
The default value is Fulfillment.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
1730
FulfillmentTaskAssignmentRuleDynamic Revenue Orchestrator

===== PAGE 1745 =====

FulfillmentTaskAssignmentRuleFeed
Feed tracking is available for the object.
FulfillmentTaskAssignmentRuleHistory
History is available for tracked fields of the object.
FulfillmentTaskAssignmentRuleShare
Sharing is available for the object.
FulfillmentWorkspace
Represents a visual designer for fulfillment plans that can have multiple step groups and their dependencies. This object is available in
API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
textarea
Description
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The description of the fulfillment workspace.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record.
Type
string
Name
1731
FulfillmentWorkspaceDynamic Revenue Orchestrator

===== PAGE 1746 =====

DetailsField
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the fulfillment workspace.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the user who owns this record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
FulfillmentWorkspaceHistory on page 2734
History is available for tracked fields of the object starting API version 65.0.
FulfillmentWorkspaceShare on page 2738
Sharing is available for the object.
FulfillmentWorkspaceItem
Represents information about the attributes that are used in the definition for a fulfillment step group. This object is available in API
version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
1732
FulfillmentWorkspaceItemDynamic Revenue Orchestrator

===== PAGE 1747 =====

Fields
DetailsField
Type
reference
FulfillmentStepDefinitionGroupId
Properties
Create, Filter, Group, Sort
Description
For internal use only.
This field is a relationship field.
Relationship Name
FulfillmentStepDefinitionGroup
Relationship Type
Master-detail
Refers To
FulfillmentStepDefinitionGroup (the detail object)
Type
reference
FulfillmentWorkspaceId
Properties
Create, Filter, Group, Sort
Description
The ID of the parent fulfillment workspace that's related to this record.
This field is a relationship field.
Relationship Name
FulfillmentWorkspace
Relationship Type
Master-detail
Refers To
FulfillmentWorkspace (the master object)
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the fulfillment workspace item.
Type
int
ShowOrder
Properties
Create, Filter, Group, Nillable, Sort, Update
1733
FulfillmentWorkspaceItemDynamic Revenue Orchestrator

===== PAGE 1748 =====

DetailsField
Description
The display sequence value of the fulfillment workspace item.
ProductDecompEnrichmentRule
Represents mappings between fields and attributes. Enrichment rules are part of a decomposition rule, and are used to propagate data
to fulfillment order lines. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
reference
CalculationDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
An expression set or a decision matrix that calculates the destination value.
This field is a polymorphic relationship field.
Relationship Name
CalculationDefinition
Refers To
DecisionMatrixDefinition, ExpressionSet
Type
picklist
CalculationMethod
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The type of enrichment rule.
Valid values are:
• Ad-verbatim—As Is
• Static-Lookup—List Lookup
1734
ProductDecompEnrichmentRuleDynamic Revenue Orchestrator

===== PAGE 1749 =====

DetailsField
• Expression-Set—Available in API version 64.0 and later
Type
reference
DecompositionRuleId
Properties
Create, Filter, Group, Sort
Description
The identifier of the decomposition rule.
This field is a relationship field.
Relationship Name
DecompositionRule
Relationship Type
Parent-child
Refers To
ProductFulfillmentDecompRule (the master object)
Type
string
DestinationApiName
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The API name of the destination field or attribute code of an attribute.
Type
reference
DestinationAttributeDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
This field is a relationship field.
Relationship Name
DestinationAttributeDefinition
Refers To
AttributeDefinition
Type
string
DestinationAttributeIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
1735
ProductDecompEnrichmentRuleDynamic Revenue Orchestrator

===== PAGE 1750 =====

DetailsField
Description
The destination entity attribute that is mapped from the source entity attribute. This field
can store a Salesforce AttributeDefinition ID or an external identifier. This field is available in
API version 65.0 and later.
Type
string
DestinationContextTag
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The name of the destination context definition.
Type
picklist
DestinationType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The destination type for mapping.
Valid values are:
• Attribute
• Field
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record
Type
reference
ListMappingGroupId
Properties
Create, Filter, Group, Nillable, Sort, Update
1736
ProductDecompEnrichmentRuleDynamic Revenue Orchestrator

===== PAGE 1751 =====

DetailsField
Description
For internal use only.
This field is a relationship field.
Relationship Name
ListMappingGroup
Refers To
ValTfrmGrp
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the decomposition rule.
Type
picklist
RuleEnforcement
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies whether the rule applies to all fulfillment requests or only to specific ones.
Valid values are:
• AllFulfillmentRequests
• InitialFulfillmentRequest
This field is available in API version 63.0 and later.
Type
string
SourceApiName
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The API name of the source field or attribute code of an attribute.
Type
reference
SourceAttributeDefinitionId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
For internal use only.
This field is a relationship field.
1737
ProductDecompEnrichmentRuleDynamic Revenue Orchestrator

===== PAGE 1752 =====

DetailsField
Relationship Name
SourceAttributeDefinition
Refers To
AttributeDefinition
Type
string
SourceAttributeIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
The source entity attribute that is mapped to the destination entity attribute. This field can
store a Salesforce AttributeDefinition ID or an external identifier. This field is available in API
version 65.0 and later.
Type
string
SourceContextTag
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The source type for the context definition.
Type
picklist
SourceType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The source type for mapping.
Valid values are:
• Attribute
• Field
ProdtDecompEnrchVarMap
Represents the mapping of a field context tag or an attribute to a variable within an expression set. This object is available in API version
64.0 and later.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(), search()
1738
ProdtDecompEnrchVarMapDynamic Revenue Orchestrator

===== PAGE 1753 =====

Fields
DetailsField
Type
reference
AttributeDefinitionId
Properties
Filter, Group, Nillable, Sort
Description
The attribute definition the expression set variable is mapped to when creating the enrichment
rule.
This field is a relationship field.
Relationship Name
AttributeDefinition
Refers To
AttributeDefinition
Type
string
ExpressionSetVarName
Properties
Filter, Group, Sort
Description
The name of the variable that's mapped to the expression set defined in the enrichment
rule.
Type
string
FieldContextTagName
Properties
Filter, Group, Nillable, Sort
Description
The name of the field context tag to which the expression set variable is mapped when
creating the enrichment rule.
Type
string
ProductAttributeIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
The product attribute from an internal or external catalog, used by DRO to copy data during
the enrichment process. This field is available in API version 65.0 and later.
Type
reference
ProductDecompEnrichmentRuleId
1739
ProdtDecompEnrchVarMapDynamic Revenue Orchestrator

===== PAGE 1754 =====

DetailsField
Properties
Filter, Group, Sort
Description
The rule that contains the mappings between the fields and attributes for the decomposing
product.
This field is a relationship field.
Relationship Name
ProductDecompEnrichmentRule
Relationship Type
Master-detail
Refers To
ProductDecompEnrichmentRule (the master object)
Type
picklist
VariableType
Properties
Defaulted on create, Filter, Group, Restricted picklist, Sort
Description
Specifies whether the expression set variable is an input or output variable.
Valid values are:
• Input
• Output
The default value is Input.
ProductFulfillmentDecompRule
Represents a rule that determines how an order is broken into sub-orders with specific technical details that help in order fulfillment. It
can be applied to a commercial or a technical product. This object is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
textarea
ConditionData
1740
ProductFulfillmentDecompRuleDynamic Revenue Orchestrator

===== PAGE 1755 =====

DetailsField
Properties
Create, Nillable, Update
Description
The condition for executing the product fulfillment decomposition. The condition is defined
as a rule or a set of rules in JSON format. This field is available in API version 66.0 and later.
Type
reference
DestinationProductId
Properties
Create, Filter, Group, Sort, Update
Description
The destination product for the decomposition rule.
This field is a relationship field.
Relationship Name
DestinationProduct
Relationship Type
Lookup
Refers To
Product2
Type
string
DestinationIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
The destination entity in the product fulfillment decomposition rule. This field can store a
Salesforce product ID or an external identifier. This field is available in API version 65.0 and
later.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
1741
ProductFulfillmentDecompRuleDynamic Revenue Orchestrator

===== PAGE 1756 =====

DetailsField
Description
The most recent date when a user viewed this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the decomposition rule.
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
Relationship Type
Lookup
Refers To
Group, User
Type
int
Priority
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The priority of the decomposition rule. Decomposition rules are executed in order of priority.
Type
reference
SourceProductClassificationId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The classification of the source product that's used for decomposition. This field is available
in API version 62.0 and later.
This field is a relationship field.
Relationship Name
SourceProductClassification
1742
ProductFulfillmentDecompRuleDynamic Revenue Orchestrator

===== PAGE 1757 =====

DetailsField
Refers To
ProductClassification
Type
string
SourceClassIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
The source classification entity in the product fulfillment decomposition rule. This field can
store a Salesforce product ID or an external identifier. This field is available in API version 65.0
and later.
Type
string
SourceIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
The source entity in the product fulfillment decomposition rule. This field can store a Salesforce
product ID or an external identifier. This field is available in API version 65.0 and later.
Type
reference
SourceProductId
Properties
Create, Filter, Group, Sort, Update
Description
Source product for the decomposition rule.
This field is a relationship field.
Relationship Name
SourceProduct
Relationship Type
Lookup
Refers To
Product2
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductFulfillmentDecompRuleShare on page 2738
Sharing is available for the object.
1743
ProductFulfillmentDecompRuleDynamic Revenue Orchestrator

===== PAGE 1758 =====

ProductFulfillmentScenario
Represents a link between a product and the corresponding group of fulfillment steps that's necessary to fulfill that product. This object
is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
multipicklist
Action
Properties
Create, Filter, Nillable, Update
Description
For internal use only.
Valid values are:
• Add
• Amend
• Cancel
• NoChange
• Renew
Type
textarea
ConditionData
Properties
Create, Nillable, Update
Description
The condition for executing the product fulfillment scenario. The condition is defined as a
rule or a set of rules in JSON format. This field is available in API version 66.0 and later.
Type
reference
FulfillmentStepDefnGroupId
Properties
Create, Filter, Group, Sort, Update
Description
The fulfillment step definition group associated with the product fulfillment scenario.
This field is a relationship field.
1744
ProductFulfillmentScenarioDynamic Revenue Orchestrator

===== PAGE 1759 =====

DetailsField
Relationship Name
FulfillmentStepDefnGroup
Relationship Type
Lookup
Refers To
FulfillmentStepDefinitionGroup
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
For internal use only.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
For internal use only.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the product fulfillment scenario.
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
Relationship Type
Lookup
Refers To
Group, User
1745
ProductFulfillmentScenarioDynamic Revenue Orchestrator

===== PAGE 1760 =====

DetailsField
Type
reference
ProductClassificationId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The product classification associated with the product fulfillment scenario.
This field is a relationship field.
Relationship Name
ProductClassification
Relationship Type
Lookup
Refers To
ProductClassification
Type
reference
ProductId
Properties
Create, Filter, Group, Sort, Update, Nillable (Available in API version 64.0 and later)
Description
The product associated with the product fulfillment scenario.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Type
string
SourceClassIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
The source classification entity in the product fulfillment scenario. This field can store a
Salesforce Product Class ID or an external identifier. This field is available in API version 65.0
and later.
Type
string
SourceIdentifier
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
1746
ProductFulfillmentScenarioDynamic Revenue Orchestrator

===== PAGE 1761 =====

DetailsField
Description
The source entity in the product fulfillment scenario. This field can store a Salesforce product
ID or an external identifier. This field is available in API version 65.0 and later.
Type
picklist
UsageType
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Name of the usage type. This field is available in API version 66.0 and later.
Possible values are:
• Fulfillment
• Generic
• InsuranceRuleAction—Insurance Rule Action
• IntegrationOrchestrator—Integration Orchestrator
• StageManagement—Stage Management
The default value is Fulfillment.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductFulfillmentScenarioShare on page 2738
Sharing is available for the object.
SalesTrxnDeleteEvent
Represents the platform event that triggers the deletion of sales transaction fulfillment request records when the corresponding reference
records are deleted. This object is available in API version 64.0 and later.
Supported Calls
create(), describeSObjects()
Fields
DetailsField
Type
string
ReferenceObjectIdentifier
1747
SalesTrxnDeleteEventDynamic Revenue Orchestrator

===== PAGE 1762 =====

DetailsField
Properties
Create, Nillable
Description
Object identifier for the sales transaction fulfillment request to be deleted.
SalesTransactionFulfillReq
Represents the statuses of all the sub-orders that belong to the selected commercial or technical product. This object is available in API
version 62.0 and later.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
Fields
DetailsField
Type
picklist
AssetizationStatus
Properties
Filter, Group, Restricted picklist, Sort
Description
Specifies the status of the assetization.
Valid values are:
• Completed
• Failed
• InProgress
• NotStarted
• Rejected
• NotApplicable- Available in API version 64.0 and later.
Type
picklist
DecompositionStatus
Properties
Filter, Group, Restricted picklist, Sort
Description
Specifies the status of the decomposition.
Valid values are:
• Completed
1748
SalesTransactionFulfillReqDynamic Revenue Orchestrator

===== PAGE 1763 =====

DetailsField
• Failed
• InProgress
• NotStarted
• Rejected
• NotApplicable- Available in API version 64.0 and later.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the sales transaction fulfillment request.
Type
string
OrchestrationGroupKey
Properties
Filter, Group, Nillable, Sort
Description
The identifier of the group of sales transactions that require synchronization before processing.
This field is available in API version 63.0 and later.
Type
reference
OwnerId
Properties
Filter, Group, Sort
Description
The ID of the user who created the request record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
picklist
PlanCompositionStatus
Properties
Filter, Group, Restricted picklist, Sort
Description
For internal use only.
Valid values are:
1749
SalesTransactionFulfillReqDynamic Revenue Orchestrator

===== PAGE 1764 =====

DetailsField
• Completed
• Failed
• InProgress
• NotStarted
• Rejected
• NotApplicable  - Available in API version 64.0 and later.
Type
picklist
PlanExecutionStatus
Properties
Filter, Group, Nillable, Sort
Description
Specifies the status of the plan execution.
Valid values are:
• InProgress
• Frozen
• Freezing
Type
reference
PlanId
Properties
Filter, Group, Nillable, Sort
Description
The identifier of the plan.
This field is a relationship field.
Relationship Name
Plan
Refers To
FulfillmentPlan
Type
reference
PreviousRequestId
Properties
Filter, Group, Nillable, Sort
Description
The identifier of the previous fulfillment request.
This field is a relationship field.
Relationship Name
PreviousRequest
1750
SalesTransactionFulfillReqDynamic Revenue Orchestrator

===== PAGE 1765 =====

DetailsField
Refers To
SalesTransactionFulfillReq
Type
reference
ReferenceObjectIdentifier
Properties
Filter, Group, idLookup, Nillable, Sort
Description
The ID of the sales transaction record. This field is available in API version 64.0 and later.
Type
picklist
SalesTransactionType
Properties
Filter, Group, Restricted picklist, Sort
Description
Specifies the type of sales transaction that's processed by the fulfillment request.
Valid values are:
• StandardOrder
• GenericAdapter—Available in API version 64.0 and later.
Type
picklist
Status
Properties
Filter, Group, Restricted picklist, Sort
Description
Specifies the overall status of the fulfillment.
Valid values are:
• Created
• Freezing
• Frozen
• Fulfilled
• Fulfilling
• Rejected
• Superseded
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
1751
SalesTransactionFulfillReqDynamic Revenue Orchestrator

===== PAGE 1766 =====

SalesTransactionFulfillReqShare on page 2738
Sharing is available for the object.
ValTfrm
Represents mappings between fields and attributes. Enrichment rules are part of a decomposition rule, and are used to propagate data
to fulfillment order lines. This object is available in API version 61.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Fields
DetailsField
Type
date
InputDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date of value entry.
Type
dateTime
InputDatetime
Properties
Create, Filter, Nillable, Sort, Update
Description
The time of value entry.
Type
double
InputNumber
Properties
Create, Filter, Nillable, Sort, Update
Description
The value of input number.
Type
reference
InputPicklistValueId
Properties
Create, Filter, Group, Nillable, Sort, Update
1752
ValTfrmDynamic Revenue Orchestrator

===== PAGE 1767 =====

DetailsField
Description
The identifier of the input list of values.
This field is a relationship field.
Relationship Name
InputPicklistValue
Refers To
AttributePicklistValue
Type
string
InputString
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The value of input text.
Type
boolean
IsInputBoolean
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates if a value was entered (true) or not (false).
The default value is false.
Type
boolean
IsOutputBoolean
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates if there was an output value (true) or not (false).
The default value is false.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the related transformation group.
Type
date
OutputDate
1753
ValTfrmDynamic Revenue Orchestrator

===== PAGE 1768 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date of matched output.
Type
dateTime
OutputDatetime
Properties
Create, Filter, Nillable, Sort, Update
Description
The time of matched output.
Type
double
OutputNumber
Properties
Create, Filter, Nillable, Sort, Update
Description
The value of output number.
Type
reference
OutputPicklistValueId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The identifier of the output list of values.
This field is a relationship field.
Relationship Name
OutputPicklistValue
Refers To
AttributePicklistValue
Type
string
OutputString
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The value of output text.
Type
reference
ValueTransformGroupId
1754
ValTfrmDynamic Revenue Orchestrator

===== PAGE 1769 =====

DetailsField
Properties
Create, Filter, Group, Sort
Description
The identifier of the related transformation group.
This field is a relationship field.
Relationship Name
ValueTransformGroup
Relationship Type
Master-detail
Refers To
ValTfrmGrp (the master object)
ValTfrmGrp
Represents a rule that determines how an order is broken into sub-orders with specific technical details that help in order fulfillment.
The rule can be applied to a commercial or a technical product. This object is available in API version 61.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
picklist
DestinationPrimitiveType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The data type of the output value.
Valid values are:
• Boolean
• Currency
• Date
• Datetime
• Number
• Percent—Picklist Value
• Picklist
1755
ValTfrmGrpDynamic Revenue Orchestrator

===== PAGE 1770 =====

DetailsField
• Text
Type
boolean
IsDestinationEnumerated
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the output is a list of values (true) or not (false).
The default value is false.
Type
boolean
IsSourceEnumerated
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the input is from a list of values (true) or not (false).
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user referenced this record.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The most recent date when a user viewed this record.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the list mapping.
Type
reference
OwnerId
1756
ValTfrmGrpDynamic Revenue Orchestrator

===== PAGE 1771 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the user who owns this record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
picklist
SourcePrimitiveType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The data type of the input value.
Valid values are:
• Boolean
• Currency
• Date
• Datetime
• Number
• Percent—Picklist Value
• Picklist
• Text
Type
picklist
UsageType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The data mapping feature that uses this value transformation group.
Valid value is DFOListMapping.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ValTfrmGrpShare on page 2738
Sharing is available for the object.
1757
ValTfrmGrpDynamic Revenue Orchestrator

===== PAGE 1772 =====

Dynamic Revenue Orchestrator Standard Invocable Actions
Use standard invocable actions to submit an order or a sales transaction to Dynamic Revenue Orchestrator (DRO) for fulfillment.
Decompose Sales Transaction Action
Decompose a sales transaction, such as a quote, order, or order summary.
Freeze Sales Transaction Action
Freeze a sales transaction to disable the modification of a line item.
Get Point Of No Return Action
Get details about the point of no return milestone for each line item in a sales transaction.
Orchestrate Sales Transaction Action
Initiate the orchestration process for a sales transaction. This action executes only the plan composition and orchestration phases,
without performing decomposition.
Orchestrate Transaction Action
Orchestrate a transaction for any domain-specific object, such as a collection plan for Revenue billing, that requires the composition
and execution of a fulfillment plan.
Submit Order Action
Submit an order to Dynamic Revenue Orchestrator (DRO) for fulfillment.
Submit Sales Transaction Action
Initiate the fulfillment process of any sales transaction, such as a quote, an order, or an order summary.
Unfreeze Sales Transaction Action
Unfreeze a sales transaction to enable the modification of a line item.
SEE ALSO:
Actions Developer Guide: Overview
REST API Developer Guide: Invocable Actions Standard
Decompose Sales Transaction Action
Decompose a sales transaction, such as a quote, order, or order summary.
Specify the ID of the sales transaction to decompose. The decomposition process includes these steps.
• Intake process
• Sales transaction decomposition
The intake process occurs synchronously or asynchronously, as specified with the intakeRequestType  input parameter. You can
also specify the decomposition priority using the fulfillmentPriority parameter.
This action executes only the decomposition process and stops before orchestration. You can execute custom logic in between the
decomposition and orchestration processes.
This action is available in API version 66.0 and later.
1758
Dynamic Revenue Orchestrator Standard Invocable ActionsDynamic Revenue Orchestrator

===== PAGE 1773 =====

Special Access Rules
The Decompose Sales Transaction action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud. See the required
permissions to access and call this invocable action.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/decomposeSalesTransaction
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
boolean
allowOverride
OfPointOfNoReturn
Description
Indicates whether to override the point of no return setting for the fulfillment step (true) or
not (false). The default value is false.
Type
string
fulfillmentAdapter
Description
Required.
Type of fulfillment adapter. Valid values are:
• StandardOrder
• GenericAdapter
Type
string
fulfillmentPriority
Description
Priority to fulfill the sales transaction. Valid values are:
• High
• Bulk
• Default
1759
Decompose Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1774 =====

DetailsInput
Type
string
hydratedContextId
Description
ID of the hydrated context.
Type
string
intakeRequestType
Description
Type of request to process the intake. Valid values are:
• Synchronous
• Asynchronous
Type
string
priorityLimitAction
Description
Type of action to perform when the priority limit is reached. Valid values are:
• Reject
• Downgrade
This parameter is applicable only when you specify the fulfillmentPriority parameter.
Type
id
salesTransactionId
Description
Required. ID of the sales transaction to submit.
Outputs
DetailsOutput
Type
string
errorCode
Description
Code that corresponds to the type of error encountered.
Type
string
requested
FulfillmentPriority
1760
Decompose Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1775 =====

DetailsOutput
Description
Priority to fulfill the sales transaction. Valid values are:
• High
• Bulk
• Default
Type
string
requestId
Description
Request ID of the invocation.
Type
string
resolved
FulfillmentPriority
Description
Resolved priority to fulfill the sales transaction. Valid values are:
• High
• Bulk
• Default
Type
string
submitStatus
Description
Submission status of the sales transaction for decomposition. Valid values are:
• Success
• Error
• Submitted
• Rejected
Type
string
usedContextId
Description
ID of the used context that updates the decomposition process.
1761
Decompose Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1776 =====

Example
POST
This sample request is for the Decompose Sales Transaction action.
{
"inputs": [
{
"fulfillmentAdapter": "StandardOrder",
"intakeRequestType": "Synchronous",
"salesTransactionId": "801xx000003GYexAAG"
}
]
}
This sample response is for the Decompose Sales Transaction action.
[
{
"actionName": "decomposeSalesTransaction",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"requestId": "ee3ded2e-fe43-401b-a54d-9124d48a0b72",
"requestedFulfillmentPriority": "Default",
"submitStatus": "SUCCESS",
"usedContextId": "0000000s21to18g0009176412796953180a8259def914e1abbd863dde076b71f",
"resolvedFulfillmentPriority": "Default"
},
"sortOrder": -1,
"version": 1
}
]
Freeze Sales Transaction Action
Freeze a sales transaction to disable the modification of a line item.
A line item can reach a milestone in the fulfillment process, which is known as a point of no return, where the line item can’t accept
modifications. Get details about the point of no return for each line item of a sales transaction.
This action is available in API version 64.0 and later.
Special Access Rules
The Freeze Sales Transaction action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud. See the required
permissions to access and call this invocable action.
1762
Freeze Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1777 =====

Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/freezeSalesTransaction
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
salesTransactionId
Description
Required. ID of the sales transaction that's submitted to the Dynamic Revenue Orchestrator.
Outputs
DetailsOutput
Type
string
errorCode
Description
Code indicating the type of error.
Type
id
orchestrationPlanId
Description
ID of the created orchestration plan.
Type
string
planState
Description
Status of the created orchestration plan. Valid values are:
• FAILURE
• NOTSTARTED
• PENDING
1763
Freeze Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1778 =====

DetailsOutput
• COMPLETED
• FROZEN
• INPROGRESS
Type
string
pointOfNoReturn
DetailForLineItems
List
Description
Collection of sales transaction line items, where each item includes a boolean value indicating
whether it has reached the point of no return.
Type
string
requestId
Description
ID of the request to get the point of no return details.
Type
string
salesTransactionId
Description
ID of the sales transaction that's submitted to the Dynamic Revenue Orchestrator.
Example
POST
This sample request is for the Freeze Sales Transaction action.
{
"inputs": [
{
"salesTransactionId": "801SG00000jQO1ZYAW"
}
]
}
This sample response is for the Freeze Sales Transaction action.
[
{
"actionName": "freezeSalesTransaction",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"salesTransactionId": "801SG00000jQO1ZYAW",
"orchestrationPlanId": "13VSG00000229Z72AI",
1764
Freeze Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1779 =====

"requestId": "452789a6-f2ab-4079-8aca-a11dbfef6a45",
"pointOfNoReturnDetailForLineItemsList": "802SG000007D0B4YAK\": {\namendAllowed:
false,\nanyChangesAllowed: true,\ncancelAllowed: false\n}, \n802SG000007D0B3YAK\":
{\namendAllowed: false,\nanyChangesAllowed: true,\ncancelAllowed: false\n}",
"planState": "Frozen"
},
"sortOrder": -1,
"version": 1
}
]
Get Point Of No Return Action
Get details about the point of no return milestone for each line item in a sales transaction.
A line item can reach a milestone in the fulfillment process, which is known as a point of no return, where the line item can’t accept
modifications. Get details about the point of no return for each line item of a sales transaction.
This action is available in API version 64.0 and later.
Special Access Rules
The Get Point Of No Return action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud. See the required
permissions to access and call this invocable action.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getPointOfNoReturn
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
salesTransactionId
Description
Required. ID of the sales transaction to get the point of no return details for.
1765
Get Point Of No Return ActionDynamic Revenue Orchestrator

===== PAGE 1780 =====

Outputs
DetailsOutput
Type
string
errorCode
Description
Code indicating the type of error.
Type
string
lineItemsPointOf
NoReturnInfo
Description
Line items with the point of no return details.
Type
id
planId
Description
ID of the composed fulfillment plan.
Type
string
planState
Description
State of the fulfillment plan.
Type
string
requestId
Description
Request ID of the invocation.
Type
string
salesTransactionId
Description
ID of the submitted sales transaction.
Example
POST
This sample request is for the Get Point Of No Return action.
{
"inputs": [
{
"salesTransactionId": "801SG00000jQO1ZYAW"
1766
Get Point Of No Return ActionDynamic Revenue Orchestrator

===== PAGE 1781 =====

}
]
}
This sample response is for the Get Point Of No Return action.
[
{
"actionName": "getPointOfNoReturn",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"planId": "13VSG00000229Z72AI",
"requestId": "35c9388b-d30d-4d68-aae5-c109c8bff7ef",
"lineItemsPointOfNoReturnInfo": "802SG000007D0B4YAK\": {\namendAllowed:
false,\nanyChangesAllowed: true,\ncancelAllowed: false\n}, \n802SG000007D0B3YAK\":
{\namendAllowed: false,\nanyChangesAllowed: true,\ncancelAllowed: false\n}",
"salesTransactionId": "801SG00000jQO1ZYAW",
"planState": "InProgress"
},
"sortOrder": -1,
"version": 1
}
]
Orchestrate Sales Transaction Action
Initiate the orchestration process for a sales transaction. This action executes only the plan composition and orchestration phases, without
performing decomposition.
Specify the ID of the sales transaction to orchestrate. The decomposition process includes these steps.
• Intake process
• Fulfillment orchestration
The intake process occurs synchronously or asynchronously, as specified with the intakeRequestType  input parameter. You can
also specify the orchestration priority using the fulfillmentPriority parameter.
Use this action when the sales transaction is decomposed either by a previous decomposition action or by custom logic before orchestrating
the fulfillment plan.
This action is available in API version 66.0 and later.
Special Access Rules
The Orchestrate Sales Transaction action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud. See the required
permissions to access and call this invocable action.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/orchestrateSalesTransaction
1767
Orchestrate Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1782 =====

Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
boolean
allowOverride
OfPointOfNoReturn
Description
Indicates whether to override the point-of-no-return setting for the fulfillment step (true) or
not (false). The default value is false.
Type
string
fulfillmentAdapter
Description
Required. Type of fulfillment adapter. Valid values are:
• StandardOrder
• GenericAdapter
Type
string
fulfillmentPriority
Description
Priority to fulfill the sales transaction. Valid values are:
• High
• Bulk
• Default
Type
string
hydratedContextId
Description
ID of the hydrated context.
Type
string
intakeRequestType
1768
Orchestrate Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1783 =====

DetailsInput
Description
Type of request to process the intake. Valid values are:
• Synchronous
• Asynchronous
Type
string
priorityLimitAction
Description
Type of action to perform when the priority limit is reached. Valid values are:
• Reject
• Downgrade
This parameter is applicable only when you specify the fulfillmentPriority parameter.
Type
id
salesTransactionId
Description
Required. ID of the sales transaction to submit.
Outputs
DetailsOutput
Type
string
errorCode
Description
Code indicating the type of error.
Type
id
fulfillmentPlanId
Description
ID of the composed fulfillment plan.
Type
string
requested
FulfillmentPriority
Description
Priority to fulfill the sales transaction. Valid values are:
• High
• Bulk
1769
Orchestrate Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1784 =====

DetailsOutput
• Default
Type
string
requestId
Description
Request ID of the invocation.
Type
string
resolved
FulfillmentPriority
Description
Resolved priority to fulfill the sales transaction. Valid values are:
• High
• Bulk
• Default
Type
string
submitStatus
Description
Submission status of the sales transaction for orchestration. Valid values are:
• SUCCESS
• ERROR
• SUBMITTED
• REJECTED
Type
string
usedContextId
Description
ID of the context that updates the orchestration process.
Example
POST
This sample request is for the Orchestrate Sales Transaction action.
{
"inputs": [
{
"fulfillmentAdapter": "StandardOrder",
"intakeRequestType": "Synchronous",
"salesTransactionId": "801xx000003GYgZAAW"
}
1770
Orchestrate Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1785 =====

]
}
This sample response is for the Orchestrate Sales Transaction action.
[
{
"actionName": "orchestrateSalesTransaction",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"usedContextId": "0000000s21to18g00091764134566956e2100424de0d4af8869669df515e24cb",
"requestId": "ac2a9d18-c702-43ee-bc08-1c03061b549c",
"fulfillmentPlanId": "13Vxx0000004CFUEA2",
"submitStatus": "SUCCESS",
"resolvedFulfillmentPriority": "Default",
"requestedFulfillmentPriority": "Default"
},
"sortOrder": -1,
"version": 1
}
]
Orchestrate Transaction Action
Orchestrate a transaction for any domain-specific object, such as a collection plan for Revenue billing, that requires the composition and
execution of a fulfillment plan.
Specify the ID of the transaction to orchestrate and the orchestration type. The orchestration process includes:
• Composition of the orchestration plan
• Execution of the fulfillment plan
This action is available in API version 66.0 and later.
Special Access Rules
The Orchestrate Transaction action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud. See the required
permissions to access and call this invocable action.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/orchestrateTransaction
Formats
JSON, XML
HTTP Methods
POST
1771
Orchestrate Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1786 =====

Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
string
transactionId
Description
Required. ID of the business object or domain object to be orchestrated, such as a Collection
Plan ID.
Type
string
orchestrationType
Description
Required. Type of orchestration that’s used to orchestrate the transaction. Valid values are:
• Generic
• Fulfillment
• Billing
Outputs
DetailsOutput
Type
string
requestId
Description
Request ID of the invocation.
Type
string
errorCode
Description
Code that corresponds to the type of encountered error.
Type
string
fulfillmentPlanId
Description
ID of the composed fulfillment plan.
1772
Orchestrate Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1787 =====

DetailsOutput
Type
string
submitStatus
Description
Submission status of the transaction that’s orchestrated. Valid values are:
• Success
• Error
Example
POST
This sample request is for the Orchestrate Transaction action.
{
"inputs": [
{
"transactionId": "801xx000003GYexAAG",
"orchestrationType": "Fulfillment"
}
]
}
This sample response is for the Orchestrate Transaction action.
[
{
"actionName": "orchestrateTransaction",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"requestId": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
"fulfillmentPlanId":
"0000000s21to18g0009176412796953180a8259def914e1abbd863dde076b71f",
"submitStatus": "SUCCESS"
},
"sortOrder": -1,
"version": 1
}
]
Submit Order Action
Submit an order to Dynamic Revenue Orchestrator (DRO) for fulfillment.
By using the Submit Order action, you can perform:
• Order decomposition
1773
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1788 =====

• Fulfillment orchestration that’s driven through message queues
• Dynamic plan composition that’s based on the incoming order
This action is available in API version 61.0 and later.
Special Access Rules
The Submit Order action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud. See the required permissions
to access and call this invocable action.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/submitOrder
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
ID of the order to submit to DRO.
Type
string
callType
Description
Optional.
Mode that the order intake must be processed in. Valid values are:
• Synchronous
• Asynchronous
The default value is Asynchronous.
Type
string
contextId
1774
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1789 =====

DetailsInput
Description
Optional.
ID of the hydrated context. See Context Service.
Outputs
DetailsOutput
Type
string
errorCode
Description
Error code for the failed request, if any.
Type
string
fulfillmentPlanId
Description
ID of the orchestrated fulfillment plan that’s generated. Returned only if the callType  value
is Synchronous.
Type
string
requestId
Description
Unique ID of the invocation request that helps identify a single request.
Type
string
submitStatus
Description
Submit status of the invocation request.
Valid values are:
• SUCCESS
• ERROR
• SUBMITTED
• REJECTED
Type
string
usedContextId
Description
Hydrated context ID that’s used in this request, which can be different from the contextId
input.
1775
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1790 =====

Example
POST
This example shows a sample request.
{
"inputs": [
{
"orderId": "801RM0000007yGaYAI",
"callType": "Synchronous"
}
]
}
This example shows a sample response when the call type is synchronous.
[
{
"actionName":"submitOrder"
"errors":NULL
"invocationId":NULL
"isSuccess":true
"outputValues":{
"requestId":"a161cfda-868c-41d2-b589-7c7d7ff2d4c1"
"submitStatus":"SUCCESS"
"usedContextId":"e275e930923106ee7e39cbfa232e38252bd4d63f4ea2dd956b7301e243554134"
"fulfillmentPlanId":"13VZM00000000062AA"
}
]
This example shows a sample response when the call type is asynchronous or isn’t specified.
[
{
"actionName": "submitOrder",
"errors": null,
"isSuccess": true,
"outputValues": {
"submitStatus": "SUBMITTED"
"requestId": "a161cfda-868c-41d2-b589-7c7d7ff2d4c1"
}
}
]
This example shows a sample response when a validation error occurs.
[
{
"actionName": "submitOrder",
"errors": [
{
"statusCode": "UNKNOWN_EXCEPTION",
"message": "Missing required input parameter: orderId",
"fields": []
}
],
1776
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1791 =====

"invocationId": null,
"isSuccess": false,
"outputValues": {
"requestId": "4c7d8ebb-6b0b-4852-a8a0-b67e0d36a73e",
"errorCode": "DRO_INTERNAL_ERROR"
},
}
]
Explainability Action Logs
To troubleshoot or debug errors, retrieve a list of explainability action logs. See Action Logs.
Get logs for order intake
This resource example includes sample query parameters to retrieve the action logs for an order intake.
https://yourInstance.salesforce.com/services/data/v66.0/connect/decision-explainer/action-logs?applicationSubType=DroSubmit&applicationType=7&processType=DroSubmit&primaryFilter=801xx000003GYzvAAG
This example shows the sample response. The actionLog property contains the action logs.
{
"actionLogs": [
{
"actionContextCode": "801NA000000XKPUYA4",
"actionLog": {
"OrderIntakeStatus": "",
"OrderIntakeStatusMessage": "",
"OrderId": "801NA000000XKPUYA4",
"SubmitMode": "Synchronous",
"UniqueRequestId": "d00c2aa7-56b0-411a-9b51-83d9fe2e4440",
"ContexId": "a0ca3c2296c82ad071a5efa83e8974793910f44ebddb21d37f007ce4889b65d7",
"DesActionSpecDevName": "DroSubmitAction",
"ContextDefinition": "SalesTransactionContext__stdctx"
},
"additionalFilter": "undef",
"applicationLogDate": "Thu Mar 28 12:36:26 GMT 2024",
"applicationSubtype": "DroSubmit",
"applicationType": "7",
"explainabilitySpecName": "DroSubmitAction",
"isChunked": false,
"name": "DroSubmitAction",
"primaryFilter": "801NA000000XKPUYA4",
"processType": "DroSubmit",
"secondaryFilter": "undef",
"uniqueIdentifier": "02c4bae9-d8b0-42f6-b031-e983d4247c76"
}
],
"queryMore": ""
}
1777
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1792 =====

Get logs for decomposition scope
This resource example includes sample query parameters to retrieve the decomposition-related action logs.
https://yourInstance.salesforce.com/services/data/v66.0/connect/decision-explainer/action-logs?applicationSubType=DroDcmp&applicationType=7&processType=DcmpScp&primaryFilter=801xx000003GYzvAAG
This example shows the sample response. The actionLog property contains the action logs.
{
"actionLogs": [
{
"actionContextCode": "801NA000000XKPeYAO",
"actionLog": {
"CandidateDecompositionRules": [
{
"decompRuleId": "13UNA0000004C932AE",
"SourceProductId": "01tNA0000007NP5YAM",
"AssociatedOlis": [
"802NA000002lWjOYAU"
],
"DestinationProductId": "01tNA0000007NOvYAM",
"DestinationProductScope": "Order",
"ConfiguredContextRuleId": "null"
},
{
"decompRuleId": "13UNA0000004ITY2A2",
"SourceProductId": "01tNA0000007NP5YAM",
"AssociatedOlis": [
"802NA000002lWjOYAU"
],
"DestinationProductId": "01tNA0000007NOqYAM",
"DestinationProductScope": "Order",
"ConfiguredContextRuleId": "null"
},
{
"decompRuleId": "13UNA0000004C942AE",
"SourceProductId": "01tNA0000007NPAYA2",
"AssociatedOlis": [
"802NA000002lWjKYAU"
],
"DestinationProductId": "01tNA0000007NOwYAM",
"DestinationProductScope": "Order",
"ConfiguredContextRuleId": "null"
},
{
"decompRuleId": "13UNA0000004ITd2AM",
"SourceProductId": "01tNA0000007NPAYA2",
"AssociatedOlis": [
"802NA000002lWjKYAU"
],
"DestinationProductId": "01tNA0000007NP0YAM",
"DestinationProductScope": "Order",
"ConfiguredContextRuleId": "null"
},
{
1778
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1793 =====

"decompRuleId": "13UNA0000004C952AE",
"SourceProductId": "01tNA0000007NPBYA2",
"AssociatedOlis": [
"802NA000002lWjLYAU"
],
"DestinationProductId": "01tNA0000007NOxYAM",
"DestinationProductScope": "Order",
"ConfiguredContextRuleId": "9QwNA0000000CTu0AM"
},
{
"decompRuleId": "13UNA0000004C982AE",
"SourceProductId": "01tNA0000007NPCYA2",
"AssociatedOlis": [
"802NA000002lWjNYAU"
],
"DestinationProductId": "01tNA0000007NOqYAM",
"DestinationProductScope": "Order",
"ConfiguredContextRuleId": "null"
},
{
"decompRuleId": "13UNA0000004C992AE",
"SourceProductId": "01tNA0000007NPCYA2",
"AssociatedOlis": [
"802NA000002lWjNYAU"
],
"DestinationProductId": "01tNA0000007NOrYAM",
"DestinationProductScope": "Order",
"ConfiguredContextRuleId": "9QwNA0000000CTt0AM"
}
],
"SelectedDecompositionRules": [
{
"OliId": "802NA000002lWjKYAU",
"DecompositionRuleIds": [
"13UNA0000004C942AE",
"13UNA0000004ITd2AM"
]
},
{
"OliId": "802NA000002lWjOYAU",
"DecompositionRuleIds": [
"13UNA0000004C932AE",
"13UNA0000004ITY2A2"
]
},
{
"OliId": "802NA000002lWjNYAU",
"DecompositionRuleIds": [
"13UNA0000004C982AE"
]
}
],
"OliScopeDetails": [
{
1779
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1794 =====

"OliId": "802NA000002lWjLYAU",
"ParentOliId": "802NA000002lWjOYAU",
"BundleRootOli": "802NA000002lWjOYAU"
},
{
"OliId": "802NA000002lWjMYAU",
"ParentOliId": "802NA000002lWjOYAU",
"BundleRootOli": "802NA000002lWjOYAU"
},
{
"OliId": "802NA000002lWjKYAU",
"ParentOliId": "802NA000002lWjOYAU",
"BundleRootOli": "802NA000002lWjOYAU"
},
{
"OliId": "802NA000002lWjNYAU",
"ParentOliId": "802NA000002lWjOYAU",
"BundleRootOli": "802NA000002lWjOYAU"
}
],
"FoliComputationDetails": [
{
"FoliId": "0a4NA000003HYbWYAW",
"ComputedAction": "AMEND",
"ComputedQuantity": "3.0"
},
{
"FoliId": "0a4NA000003HYbXYAW",
"ComputedAction": "AMEND",
"ComputedQuantity": "6.0"
},
{
"FoliId": "0a4NA000003HYbYYAW",
"ComputedAction": "AMEND",
"ComputedQuantity": "3.0"
},
{
"FoliId": "0a4NA000003HYbZYAW",
"ComputedAction": "AMEND",
"ComputedQuantity": "3.0"
}
],
"FlsrDetails": [
{
"FlsrId": "16ANA000005idR82AI",
"FlsrGuid": "WQoYClnAszG9axKxWxoe",
"SourceId": "802NA000002lWjOYAU",
"FoliId": "0a4NA000003HYbWYAW"
},
{
"FlsrId": "16ANA000005idR92AI",
"FlsrGuid": "80xWFpBK8sDmTFRV3Dn0",
"SourceId": "802NA000002lWjOYAU",
"FoliId": "0a4NA000003HYbXYAW"
1780
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1795 =====

},
{
"FlsrId": "16ANA000005idRA2AY",
"FlsrGuid": "nAql9VD3KiziZTFrfYXq",
"SourceId": "802NA000002lWjNYAU",
"FoliId": "0a4NA000003HYbXYAW"
},
{
"FlsrId": "16ANA000005idRB2AY",
"FlsrGuid": "wgCJT6NJ3ESolFXP5ajQ",
"SourceId": "802NA000002lWjKYAU",
"FoliId": "0a4NA000003HYbYYAW"
},
{
"FlsrId": "16ANA000005idRC2AY",
"FlsrGuid": "bvVhA34WvTBOYbG4q2Fj",
"SourceId": "802NA000002lWjKYAU",
"FoliId": "0a4NA000003HYbZYAW"
}
],
"OrderId": "801NA000000XKPeYAO",
"SubmitMode": "Synchronous",
"UniqueRequestId": "b9ac5971-0d71-45c6-a18e-f472976eaeae",
"ContextId": "1422049ffa3cc42d8c060b9a7732be360bd62a346652cda9ab6e5fd54cd03eca",
"DesActionSpecDevName": "DroDecompScopeAction",
"ContextDefinition": "SalesTransactionContext__stdctx"
},
"additionalFilter": "undef",
"applicationLogDate": "Fri Mar 29 10:02:26 GMT 2024",
"applicationSubtype": "DroDcmp",
"applicationType": "7",
"explainabilitySpecName": "DroDecompScopeAction",
"isChunked": false,
"name": "DroDecompScopeAction",
"primaryFilter": "801NA000000XKPeYAO",
"processType": "DcmpScp",
"secondaryFilter": "undef",
"uniqueIdentifier": "c1e11bc0-53e5-4f62-9ae8-1096e79a62b6"
}
],
"queryMore": ""
}
Get logs for decomposition enrichment
This resource example includes sample query parameters to retrieve the logs for decomposition enrichment tasks. For example,
conversion of order items to fulfillment order line items.
https://yourInstance.salesforce.com/services/data/v66.0/connect/decision-explainer/action-logs?applicationSubType=DroDcmp&applicationType=7&processType=DcmpEnrich&primaryFilter=801xx000003GYzvAAG&secondaryFilter=BxyDQUJ2B49CoKXiuvGI
The secondaryFilter  property is optional. If this property is specified, the API returns the enrichment rule details for a
decomposition rule. If this property is unspecified, the API returns all enrichment rule details for the order.
1781
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1796 =====

This example shows the sample response. The actionLog property contains the action logs.
{
"actionLogs": [
{
"actionContextCode": "801NA000000XKPUYA4",
"actionLog": {
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"EnrichmentRulesExecutionDetails": [
{
"EnrichmentRuleId": "13TNA00000000eG2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004CygYAE",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CyDYAU",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "SUCCESS"
},
{
"EnrichmentRuleId": "13TNA00000000eH2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004CylYAE",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CyIYAU",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "SUCCESS"
},
{
"EnrichmentRuleId": "13TNA00000000eI2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004CyqYAE",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CyhYAE",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "SUCCESS"
},
{
"EnrichmentRuleId": "13TNA00000000eJ2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004CzPYAU",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CymYAE",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "SUCCESS"
},
{
"EnrichmentRuleId": "13TNA00000000eK2AQ",
1782
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1797 =====

"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004CzUYAU",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CyrYAE",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "SUCCESS"
},
{
"EnrichmentRuleId": "13TNA00000000eL2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004CzZYAU",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CywYAE",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "SUCCESS"
},
{
"EnrichmentRuleId": "13TNA00000000eM2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004D0dYAE",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004Cz1YAE",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "ERROR_DATA_TYPE_MISMATCH"
},
{
"EnrichmentRuleId": "13TNA00000000eN2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004D0iYAE",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CzQYAU",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "ERROR_DATA_TYPE_MISMATCH"
},
{
"EnrichmentRuleId": "13TNA00000000eO2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004D18YAE",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CzVYAU",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "ERROR_DATA_TYPE_MISMATCH"
},
{
1783
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1798 =====

"EnrichmentRuleId": "13TNA00000000eP2AQ",
"DecompRuleId": "13UNA0000004C942AE",
"FlsrUid": "1FxfIhMq53OIpE9Hzs5w",
"SourceType": "Attribute",
"SourceAttributeId": "0tjNA0000004D1QYAU",
"TargetType": "Attribute",
"TargetAttributeId": "0tjNA0000004CzaYAE",
"CalculationMethod": "Ad-verbatim",
"ExecutionStatus": "ERROR_DATA_TYPE_MISMATCH"
}
],
"OrderId": "801NA000000XKPUYA4",
"SubmitMode": "Synchronous",
"UniqueRequestId": "d00c2aa7-56b0-411a-9b51-83d9fe2e4440",
"ContexId": "a0ca3c2296c82ad071a5efa83e8974793910f44ebddb21d37f007ce4889b65d7",
"DesActionSpecDevName": "DroDecompEnrichmentAction",
"ContextDefinition": "SalesTransactionContext__stdctx"
},
"additionalFilter": "undef",
"applicationLogDate": "Thu Mar 28 12:36:25 GMT 2024",
"applicationSubtype": "DroDcmp",
"applicationType": "7",
"explainabilitySpecName": "DroDecompEnrichmentAction",
"isChunked": false,
"name": "DroDecompEnrichmentAction",
"primaryFilter": "801NA000000XKPUYA4",
"processType": "DcmpEnrich",
"secondaryFilter": "1FxfIhMq53OIpE9Hzs5w",
"uniqueIdentifier": "0bd42942-12b2-4c2e-9f10-b77ee85fd20b"
}
],
"queryMore": ""
}
Get logs for plan composition
This resource example includes sample query parameters to retrieve the logs for plan composition.
https://yourInstance.salesforce.com/services/data/v66.0/connect/decision-explainer/action-logs?applicationSubType=DroPcmp&applicationType=7&processType=PcmpSteps&primaryFilter=801xx000003GYzvAAG
This example shows the sample response. The actionLog property contains the action logs.
{
"actionLogs": [
{
"actionContextCode": "801NA000000XKPeYAO",
"actionLog": {
"PlanCompositionStatus": "",
"PlanCompositionStatusMessage": "",
"CandidateProductFulfillmentScenarios": [
{
"ProductFulfillmentScenarioId": "1axNA0000004C93YAE",
"ProductId": "01tNA0000007NP5YAM",
"FulfillmentStepDefinitionGroupId": "13oNA0000004CARYA2",
1784
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1799 =====

"LineItemIds": [
"802NA000002lWjOYAU"
],
"ContextRulesetId": "9QwNA0000000CXq0AM"
}
],
"SelectedProductFulfillmentScenarios": [
null
],
"SelectedProductFulfillmentScenariosByOli": [
{
"OliId": "0a4NA000003HYbFYAW",
"ProductFulfillmentScenarios": [
null
]
},
{
"OliId": "0a4NA000003HYbXYAW",
"ProductFulfillmentScenarios": [
null
]
},
{
"OliId": "0a4NA000003HYbIYAW",
"ProductFulfillmentScenarios": [
null
]
},
{
"OliId": "802NA000002lWjOYAU",
"ProductFulfillmentScenarios": [
null
]
}
],
"PlanId": "13VNA000000OQ9W2AW",
"FulfillmentStepCreationStatus": "FulfillmentStepsCreated",
"FulfillmentStepDependencyCreationStatus": "FulfilmentStepDepCreated",
"OrderId": "801NA000000XKPeYAO",
"SubmitMode": "Synchronous",
"UniqueRequestId": "b9ac5971-0d71-45c6-a18e-f472976eaeae",
"ContextId": "1422049ffa3cc42d8c060b9a7732be360bd62a346652cda9ab6e5fd54cd03eca",
"DesActionSpecDevName": "DroPlanCompStepsAction",
"ContextDefinition": "SalesTransactionContext__stdctx"
},
"additionalFilter": "undef",
"applicationLogDate": "Fri Mar 29 10:02:27 GMT 2024",
"applicationSubtype": "DroPcmp",
"applicationType": "7",
"explainabilitySpecName": "DroPlanCompStepsAction",
"isChunked": false,
"name": "DroPlanCompStepsAction",
"primaryFilter": "801NA000000XKPeYAO",
1785
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1800 =====

"processType": "PcmpSteps",
"secondaryFilter": "undef",
"uniqueIdentifier": "bb532c9b-a88f-4add-8cd8-bd385359b1ad"
}
],
"queryMore": ""
}
Capture logs for an order
This resource example includes sample query parameters to retrieve the logs for an order.
https://yourInstance.salesforce.com/services/data/v66.0/connect/decision-explainer/action-logs?actionContextCode=801DU000000CqBJYA0&applicationType=7
This example shows the sample response. The actionLog  property contains the action logs.
{
"actionLogs": [
{
"actionContextCode": "801xx000003GZSxAAO",
"actionLog":
"{&quot;FlsrUid&quot;:&quot;qrh0Z3xv6buew1BW0wdn&quot;,&quot;DecompositionEnrichmentExecutionSequence&quot;:&quot;0&quot;,&quot;EnrichmentRulesExecutionDetails&quot;:[{&quot;EnrichmentRuleId&quot;:&quot;13Txx0000004CLwEAM&quot;,&quot;DecompRuleId&quot;:&quot;13Uxx0000004CCGEA2&quot;,&quot;FlsrUid&quot;:&quot;qrh0Z3xv6buew1BW0wdn&quot;,&quot;SourceType&quot;:&quot;Attribute&quot;,&quot;SourceAttributeId&quot;:&quot;0tjxx0000000001AAA&quot;,&quot;TargetType&quot;:&quot;Attribute&quot;,&quot;TargetAttributeId&quot;:&quot;0tjxx0000000085AAA&quot;,&quot;CalculationMethod&quot;:&quot;Ad-verbatim&quot;,&quot;ExecutionStatus&quot;:&quot;ERROR_SOURCE_DATA_FETCH&quot;},{&quot;EnrichmentRuleId&quot;:&quot;13Txx0000004CNYEA2&quot;,&quot;DecompRuleId&quot;:&quot;13Uxx0000004CCGEA2&quot;,&quot;FlsrUid&quot;:&quot;qrh0Z3xv6buew1BW0wdn&quot;,&quot;SourceType&quot;:&quot;Field&quot;,&quot;SourceFieldName&quot;:&quot;Product2Id&quot;,&quot;SourceContextTag&quot;:&quot;Product&quot;,&quot;TargetType&quot;:&quot;Attribute&quot;,&quot;TargetAttributeId&quot;:&quot;0tjxx000000006TAAQ&quot;,&quot;CalculationMethod&quot;:&quot;Ad-verbatim&quot;,&quot;ExecutionStatus&quot;:&quot;SUCCESS&quot;},{&quot;EnrichmentRuleId&quot;:&quot;13Txx0000004CPAEA2&quot;,&quot;DecompRuleId&quot;:&quot;13Uxx0000004CCGEA2&quot;,&quot;FlsrUid&quot;:&quot;qrh0Z3xv6buew1BW0wdn&quot;,&quot;SourceType&quot;:&quot;Field&quot;,&quot;SourceFieldName&quot;:&quot;IsAssetizable&quot;,&quot;SourceContextTag&quot;:&quot;IsAssetizable&quot;,&quot;TargetType&quot;:&quot;Attribute&quot;,&quot;TargetAttributeId&quot;:&quot;0tjxx000000004rAAA&quot;,&quot;CalculationMethod&quot;:&quot;Ad-verbatim&quot;,&quot;ExecutionStatus&quot;:&quot;SUCCESS&quot;},{&quot;EnrichmentRuleId&quot;:&quot;13Txx0000004CQmEAM&quot;,&quot;DecompRuleId&quot;:&quot;13Uxx0000004CCGEA2&quot;,&quot;FlsrUid&quot;:&quot;qrh0Z3xv6buew1BW0wdn&quot;,&quot;SourceType&quot;:&quot;Attribute&quot;,&quot;SourceAttributeId&quot;:&quot;0tjxx000000001dAAA&quot;,&quot;TargetType&quot;:&quot;Attribute&quot;,&quot;TargetAttributeId&quot;:&quot;0tjxx000000003FAAQ&quot;,&quot;CalculationMethod&quot;:&quot;Ad-verbatim&quot;,&quot;ExecutionStatus&quot;:&quot;ERROR_SOURCE_DATA_FETCH&quot;}],&quot;OrderId&quot;:&quot;801xx000003GZSxAAO&quot;,&quot;SubmitMode&quot;:&quot;Synchronous&quot;,&quot;UniqueRequestId&quot;:&quot;5dd3888e-e883-4770-b0ad-aa59e88450eb&quot;,&quot;ContextId&quot;:&quot;d9995de15eea0b3c1ed0a552813fe9cd02b73d0de80c0c15fd4e8ac6661508df&quot;,&quot;DesActionSpecDevName&quot;:&quot;DroDecompEnrichmentAction&quot;,&quot;ContextDefinition&quot;:&quot;SalesTransactionContext__stdctx&quot;}",
"additionalFilter": "undef",
"applicationLogDate": "Tue May 07 13:05:28 GMT 2024",
"applicationSubtype": "DroDcmp",
"applicationType": "7",
"explainabilitySpecName": "DroDecompEnrichmentAction",
"isChunked": false,
"name": "DroDecompEnrichmentAction",
"primaryFilter": "801xx000003GZSxAAO",
"processType": "DcmpEnrich",
"secondaryFilter": "qrh0Z3xv6buew1BW0wdn",
"uniqueIdentifier": "768f7d03-6770-4939-980f-a6f42ad07cde"
},
{
"actionContextCode": "801xx000003GZSxAAO",
"actionLog":
"{&quot;FlsrUid&quot;:&quot;hjow5L3YcntZsnNuEd5n&quot;,&quot;DecompositionEnrichmentExecutionSequence&quot;:&quot;0&quot;,&quot;EnrichmentRulesExecutionDetails&quot;:[{&quot;EnrichmentRuleId&quot;:&quot;13Txx0000004CH6EAM&quot;,&quot;DecompRuleId&quot;:&quot;13Uxx0000004CAeEAM&quot;,&quot;FlsrUid&quot;:&quot;hjow5L3YcntZsnNuEd5n&quot;,&quot;SourceType&quot;:&quot;Field&quot;,&quot;SourceFieldName&quot;:&quot;IsAssetizable&quot;,&quot;SourceContextTag&quot;:&quot;IsAssetizable&quot;,&quot;TargetType&quot;:&quot;Attribute&quot;,&quot;TargetAttributeId&quot;:&quot;0tjxx000000004rAAA&quot;,&quot;CalculationMethod&quot;:&quot;Ad-verbatim&quot;,&quot;ExecutionStatus&quot;:&quot;SUCCESS&quot;},{&quot;EnrichmentRuleId&quot;:&quot;13Txx0000004CKKEA2&quot;,&quot;DecompRuleId&quot;:&quot;13Uxx0000004CAeEAM&quot;,&quot;FlsrUid&quot;:&quot;hjow5L3YcntZsnNuEd5n&quot;,&quot;SourceType&quot;:&quot;Field&quot;,&quot;SourceFieldName&quot;:&quot;PricebookEntryId&quot;,&quot;SourceContextTag&quot;:&quot;ItemPricebookEntry&quot;,&quot;TargetType&quot;:&quot;Attribute&quot;,&quot;TargetAttributeId&quot;:&quot;0tjxx000000003FAAQ&quot;,&quot;CalculationMethod&quot;:&quot;Ad-verbatim&quot;,&quot;ExecutionStatus&quot;:&quot;SUCCESS&quot;}],&quot;OrderId&quot;:&quot;801xx000003GZSxAAO&quot;,&quot;SubmitMode&quot;:&quot;Synchronous&quot;,&quot;UniqueRequestId&quot;:&quot;5dd3888e-e883-4770-b0ad-aa59e88450eb&quot;,&quot;ContextId&quot;:&quot;d9995de15eea0b3c1ed0a552813fe9cd02b73d0de80c0c15fd4e8ac6661508df&quot;,&quot;DesActionSpecDevName&quot;:&quot;DroDecompEnrichmentAction&quot;,&quot;ContextDefinition&quot;:&quot;SalesTransactionContext__stdctx&quot;}",
"additionalFilter": "undef",
"applicationLogDate": "Tue May 07 13:05:28 GMT 2024",
"applicationSubtype": "DroDcmp",
"applicationType": "7",
"explainabilitySpecName": "DroDecompEnrichmentAction",
"isChunked": false,
"name": "DroDecompEnrichmentAction",
"primaryFilter": "801xx000003GZSxAAO",
"processType": "DcmpEnrich",
"secondaryFilter": "hjow5L3YcntZsnNuEd5n",
"uniqueIdentifier": "7ce652e3-81a0-4b2d-a072-88b012c83864"
},
{
"actionContextCode": "801xx000003GZSxAAO",
"actionLog":
"{&quot;CandidateDecompositionRules&quot;:[{&quot;decompRuleId&quot;:&quot;13Uxx0000004CCGEA2&quot;,&quot;SourceProductId&quot;:&quot;01txx0000006i5gAAA&quot;,&quot;AssociatedOlis&quot;:[&quot;802xx000001nbKhAAI&quot;],&quot;DestinationProductId&quot;:&quot;01txx0000006iAWAAY&quot;,&quot;DestinationProductScope&quot;:&quot;OrderLineItem&quot;,&quot;ConfiguredContextRuleId&quot;:&quot;null&quot;},{&quot;decompRuleId&quot;:&quot;13Uxx0000004CAeEAM&quot;,&quot;SourceProductId&quot;:&quot;01txx0000006i5gAAA&quot;,&quot;AssociatedOlis&quot;:[&quot;802xx000001nbKhAAI&quot;],&quot;DestinationProductId&quot;:&quot;01txx0000006i8uAAA&quot;,&quot;DestinationProductScope&quot;:&quot;OrderLineItem&quot;,&quot;ConfiguredContextRuleId&quot;:&quot;null&quot;}],&quot;SelectedDecompositionRules&quot;:[{&quot;OliId&quot;:&quot;802xx000001nbKhAAI&quot;,&quot;DecompositionRuleIds&quot;:[&quot;13Uxx0000004CCGEA2&quot;,&quot;13Uxx0000004CAeEAM&quot;]}],&quot;OliScopeDetails&quot;:[],&quot;FoliComputationDetails&quot;:[{&quot;FoliId&quot;:&quot;0a4xx00000000ODAAY&quot;,&quot;ComputedAction&quot;:&quot;ADD&quot;,&quot;ComputedQuantity&quot;:&quot;1.0&quot;},{&quot;FoliId&quot;:&quot;0a4xx00000000OEAAY&quot;,&quot;ComputedAction&quot;:&quot;ADD&quot;,&quot;ComputedQuantity&quot;:&quot;1.0&quot;}],&quot;FlsrDetails&quot;:[{&quot;FlsrId&quot;:&quot;16Axx0000004CXEEA2&quot;,&quot;FlsrGuid&quot;:&quot;qrh0Z3xv6buew1BW0wdn&quot;,&quot;SourceId&quot;:&quot;802xx000001nbKhAAI&quot;,&quot;FoliId&quot;:&quot;0a4xx00000000ODAAY&quot;},{&quot;FlsrId&quot;:&quot;16Axx0000004CXFEA2&quot;,&quot;FlsrGuid&quot;:&quot;hjow5L3YcntZsnNuEd5n&quot;,&quot;SourceId&quot;:&quot;802xx000001nbKhAAI&quot;,&quot;FoliId&quot;:&quot;0a4xx00000000OEAAY&quot;}],&quot;OrderId&quot;:&quot;801xx000003GZSxAAO&quot;,&quot;SubmitMode&quot;:&quot;Synchronous&quot;,&quot;UniqueRequestId&quot;:&quot;5dd3888e-e883-4770-b0ad-aa59e88450eb&quot;,&quot;ContextId&quot;:&quot;c132f6fca3628bf9608c0e61865b4cd0d9de1479f5171686abc040c69f0504d7&quot;,&quot;DesActionSpecDevName&quot;:&quot;DroDecompScopeAction&quot;,&quot;ContextDefinition&quot;:&quot;SalesTransactionContext__stdctx&quot;}",
1786
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1801 =====

"additionalFilter": "undef",
"applicationLogDate": "Tue May 07 13:05:32 GMT 2024",
"applicationSubtype": "DroDcmp",
"applicationType": "7",
"explainabilitySpecName": "DroDecompScopeAction",
"isChunked": false,
"name": "DroDecompScopeAction",
"primaryFilter": "801xx000003GZSxAAO",
"processType": "DcmpScp",
"secondaryFilter": "undef",
"uniqueIdentifier": "9f633a63-67d0-4f90-b4dc-c368defe8b44"
},
{
"actionContextCode": "801xx000003GZSxAAO",
"actionLog":
"{&quot;CandidateProductFulfillmentScenarios&quot;:[{&quot;ProductFulfillmentScenarioId&quot;:&quot;1axxx0000000001AAA&quot;,&quot;ProductId&quot;:&quot;01txx0000006i8uAAA&quot;,&quot;FulfillmentStepDefinitionGroupId&quot;:&quot;13oxx0000004CFUAA2&quot;,&quot;LineItemIds&quot;:[&quot;0a4xx00000000OEAAY&quot;]},{&quot;ProductFulfillmentScenarioId&quot;:&quot;1axxx0000000002AAA&quot;,&quot;ProductId&quot;:&quot;01txx0000006i8uAAA&quot;,&quot;FulfillmentStepDefinitionGroupId&quot;:&quot;13oxx0000004CH6AAM&quot;,&quot;LineItemIds&quot;:[&quot;0a4xx00000000OEAAY&quot;]}],&quot;SelectedProductFulfillmentScenarios&quot;:[&quot;1axxx0000000001AAA&quot;,&quot;1axxx0000000002AAA&quot;],&quot;SelectedProductFulfillmentScenariosByOli&quot;:[{&quot;OliId&quot;:&quot;802xx000001nbKhAAI&quot;,&quot;ProductFulfillmentScenarios&quot;:[]},{&quot;OliId&quot;:&quot;0a4xx00000000ODAAY&quot;,&quot;ProductFulfillmentScenarios&quot;:[]},{&quot;OliId&quot;:&quot;0a4xx00000000OEAAY&quot;,&quot;ProductFulfillmentScenarios&quot;:[&quot;1axxx0000000001AAA&quot;,&quot;1axxx0000000002AAA&quot;]}],&quot;PlanId&quot;:&quot;13Vxx0000004Ck8EAE&quot;,&quot;FulfillmentStepCreationStatus&quot;:&quot;FulfillmentStepsCreated&quot;,&quot;FulfillmentStepDependencyCreationStatus&quot;:&quot;FulfilmentStepDepCreated&quot;,&quot;OrderId&quot;:&quot;801xx000003GZSxAAO&quot;,&quot;SubmitMode&quot;:&quot;Synchronous&quot;,&quot;UniqueRequestId&quot;:&quot;5dd3888e-e883-4770-b0ad-aa59e88450eb&quot;,&quot;ContextId&quot;:&quot;c132f6fca3628bf9608c0e61865b4cd0d9de1479f5171686abc040c69f0504d7&quot;,&quot;DesActionSpecDevName&quot;:&quot;DroPlanCompStepsAction&quot;,&quot;ContextDefinition&quot;:&quot;SalesTransactionContext__stdctx&quot;}",
"additionalFilter": "undef",
"applicationLogDate": "Tue May 07 13:05:33 GMT 2024",
"applicationSubtype": "DroPcmp",
"applicationType": "7",
"explainabilitySpecName": "DroPlanCompStepsAction",
"isChunked": false,
"name": "DroPlanCompStepsAction",
"primaryFilter": "801xx000003GZSxAAO",
"processType": "PcmpSteps",
"secondaryFilter": "undef",
"uniqueIdentifier": "47a956a6-ae52-4e4a-843b-08b404beb52a"
},
{
"actionContextCode": "801xx000003GZSxAAO",
"actionLog":
"{&quot;OrderId&quot;:&quot;801xx000003GZSxAAO&quot;,&quot;SubmitMode&quot;:&quot;Synchronous&quot;,&quot;UniqueRequestId&quot;:&quot;5dd3888e-e883-4770-b0ad-aa59e88450eb&quot;,&quot;ContextId&quot;:&quot;c132f6fca3628bf9608c0e61865b4cd0d9de1479f5171686abc040c69f0504d7&quot;,&quot;DesActionSpecDevName&quot;:&quot;DroSubmitAction&quot;,&quot;ContextDefinition&quot;:&quot;SalesTransactionContext__stdctx&quot;}",
"additionalFilter": "undef",
"applicationLogDate": "Tue May 07 13:06:30 GMT 2024",
"applicationSubtype": "DroSubmit",
"applicationType": "7",
"explainabilitySpecName": "DroSubmitAction",
"isChunked": false,
"name": "DroSubmitAction",
"primaryFilter": "801xx000003GZSxAAO",
"processType": "DroSubmit",
"secondaryFilter": "undef",
"uniqueIdentifier": "278caec4-680c-4df8-a1b2-608e05e44baa"
}
],
"queryMore": ""
}
1787
Submit Order ActionDynamic Revenue Orchestrator

===== PAGE 1802 =====

Submit Sales Transaction Action
Initiate the fulfillment process of any sales transaction, such as a quote, an order, or an order summary.
Specify the ID of the sales transaction to be fulfilled. The fulfillment process includes these steps.
• Intake process
• Fulfillment orchestration
The intake process happens synchronously or asynchronously, which is specified by using the intakeRequestType input parameter.
You can also specify the priority for the execution of the fulfillment process, which is specified by using the fulfillmentPriority
parameter.
This action is available in API version 63.0 and later.
Special Access Rules
The Submit Sales Transaction action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud. See the required
permissions to access and call this invocable action.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/submitSalesTransaction
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
boolean
allowOverrideOfPointOfNoReturn
Description
Indicates whether to override the point of no return setting for the fulfillment step (true) or
not (false). The default value is false. Available in API version 64.0 and later.
Type
string
fulfillmentAdapter
Description
Type of fulfillment adapter. Valid values are:
• StandardOrder
• GenericAdapter—Available in API version 64.0 and later.
1788
Submit Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1803 =====

DetailsInput
Type
string
fulfillmentPriority
Description
Priority to fulfill the sales transaction. Valid values are:
• High
• Bulk
• Default
Type
string
hydratedContextId
Description
ID of the hydrated context.
Type
string
intakeRequestType
Description
Type of request to process the intake. Valid values are:
• Synchronous
• Asynchronous
Type
string
priorityLimitAction
Description
Type of action to perform when the priority limit is reached. Valid values are:
• Reject
• Downgrade
This parameter is applicable only when you specify the fulfillmentPriority parameter.
Type
id
salesTransactionId
Description
Required. ID of the sales transaction to submit.
1789
Submit Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1804 =====

Outputs
DetailsOutput
Type
string
errorCode
Description
Code indicating the type of error.
Type
id
fulfillmentPlanId
Description
ID of the composed fulfillment plan.
Type
string
requestedFulfillmentPriority
Description
Priority to fulfill the sales transaction. Valid values are:
• High
• Bulk
• Default
Type
string
requestId
Description
Request ID of the invocation.
Type
string
resolvedFulfillmentPriority
Description
Resolved priority to fulfill the sales transaction.
Type
string
submitStatus
Description
Submit status of the invocation.
Type
string
usedContextId
Description
ID of the used context that updates the decomposition process.
1790
Submit Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1805 =====

Example
POST
This sample request is for the Submit Sales Transaction action.
{
"inputs": [
{
"allowOverrideOfPointOfNoReturn": false,
"salesTransactionId": "801DV000000CbIPYA0",
"intakeRequestType": "Synchronous",
"fulfillmentAdapter": "StandardOrder",
"fulfillmentPriority": "Default",
"priorityLimitAction": "Reject"
}
]
}
This sample response is for the Submit Sales Transaction action.
[
{
"actionName": "submitSalesTransaction",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"submitStatus": "SUCCESS",
"resolvedFulfillmentPriority": "Default",
"requestedFulfillmentPriority": "Default",
"usedContextId": "0abc8db32b30d09c5051e4561f0b39d938a3bd8db4ccb13e04d41019e427211d",
"requestId": "927f72b7-85e0-4b5d-b92e-c265f41898f0",
"fulfillmentPlanId": "13VDV00000008M92AI"
},
"sortOrder": -1,
"version": 1
}
]
Unfreeze Sales Transaction Action
Unfreeze a sales transaction to enable the modification of a line item.
A line item can reach a milestone in the fulfillment process, which is known as a point of no return, where the line item can’t accept
modifications. Get details about the point of no return for each line item of a sales transaction.
This action is available in API version 64.0 and later.
Special Access Rules
The Unfreeze Sales Transaction action is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud. See the required
permissions to access and call this invocable action.
1791
Unfreeze Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1806 =====

Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/unfreezeSalesTransaction
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
salesTransactionId
Description
Required. ID of the sales transaction that's submitted to the Dynamic Revenue Orchestrator.
Outputs
DetailsOutput
Type
string
errorCode
Description
Code indicating the type of error.
Type
id
orchestrationPlanId
Description
ID of the created orchestration plan.
Type
string
planState
Description
Status of the created orchestration plan. Valid values are:
• FAILURE
• NOTSTARTED
• PENDING
1792
Unfreeze Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1807 =====

DetailsOutput
• COMPLETED
• FROZEN
• INPROGRESS
Type
string
requestId
Description
ID of the request to get the point of no return details.
Type
string
salesTransactionId
Description
ID of the sales transaction that's submitted to the Dynamic Revenue Orchestrator.
Example
POST
This sample request is for the Unfreeze Sales Transaction action.
{
"inputs": [
{
"salesTransactionId": "801SG00000jQO1ZYAW"
}
]
}
This sample response is for the Unfreeze Sales Transaction action.
[
{
"actionName": "unfreezeSalesTransaction",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"orchestrationPlanId": "13VSG00000229Z72AI",
"salesTransactionId": "801SG00000jQO1ZYAW",
"planState": "InProgress",
"requestId": "e9f2d961-b218-4911-8fee-8de31937850d"
},
"sortOrder": -1,
"version": 1
}
]
1793
Unfreeze Sales Transaction ActionDynamic Revenue Orchestrator

===== PAGE 1808 =====

Dynamic Revenue Orchestrator Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
Flow for Dynamic Revenue Orchestrator
Represents the metadata associated with a flow. With Flow, you can create an application that navigates users through a series of
screens to query and update records in the database. You can also execute logic and provide branching capability based on user
input to build dynamic applications.
DynamicFulfillmentOrchestratorSettings
Represents the settings for Dynamic Revenue Orchestrator.
SEE ALSO:
Metadata API Developer Guide: Understanding Metadata API
Flow for Dynamic Revenue Orchestrator
Represents the metadata associated with a flow. With Flow, you can create an application that navigates users through a series of screens
to query and update records in the database. You can also execute logic and provide branching capability based on user input to build
dynamic applications.
FlowActionCall
Dynamic Revenue Orchestrator exposes additional actionType values for the FlowActionCall Metadata type.
DescriptionField TypeField Name
Required.InvocableActionType
(enumeration of
type string)
actionType
The action type. Additional valid values only for Dynamic Revenue
Orchestrator include:
• decomposeSalesTransaction— Decompose a sales
transaction, such as a quote, order, or order summary.
• freezeSalesTransaction— Freeze a sales transaction to
disable the modification of a line item.
• getPointOfNoReturn— Get details about the point of no
return milestone for each line item in a sales transaction.
• orchestrateSalesTransaction— Initiate the orchestration
process for a sales transaction.
• orchestrateTransaction— Orchestrate a transaction for
any domain-specific object, such as a collection plan for Revenue
billing, that requires the composition and execution of a fulfillment
plan.
• submitOrder— Submit an order to Dynamic Revenue
Orchestrator (DRO) for fulfillment.
1794
Dynamic Revenue Orchestrator Metadata API TypesDynamic Revenue Orchestrator

===== PAGE 1809 =====

DescriptionField TypeField Name
• submitSalesTransaction— Initiate the fulfillment process
of any sales transaction, such as a quote, an order, or an order
summary.
• unfreezeSalesTransaction— Unfreeze a sales transaction
to enable the modification of a line item.
DynamicFulfillmentOrchestratorSettings
Represents the settings for Dynamic Revenue Orchestrator.
Parent Type and Manifest Access
This type extends the Metadata metadata type and inherits its fullName field.
In the package manifest, all the settings metadata types for the org are accessed using the “Settings” name. See Settings for more details.
File Suffix and Directory Location
DynamicFulfillmentOrchestratorSettings  values are stored in the
DynamicFulfillmentOrchestratorSettings.settings  file in the settings  folder. The .settings  files are
different from other named components, because there is only one settings file for each settings component.
Version
DynamicFulfillmentOrchestratorSettings components are available in API version 61.0 and later.
Fields
DescriptionField Name
Field Type
boolean
enableDFOFallout
Description
Indicates whether to enable fallout management to handle fallouts and retry policies
(true) or not (false). The default value is false. See Turn On Feature to Manage
Fallout.
Field Type
boolean
enableDFOJeopardy
Description
Indicates whether to enable management of Service Level Agreements (true) or not
(false). The default value is false. See Turn On Feature to Manage Service Level
Agreements.
1795
DynamicFulfillmentOrchestratorSettingsDynamic Revenue Orchestrator

===== PAGE 1810 =====

DescriptionField Name
Field Type
boolean
enableDFOPref
Description
Indicates whether to enable features of Dynamic Revenue Orchestrator (true) or not
(false). The default value is false. See Turn On Dynamic Revenue Orchestrator.
Field Type
boolean
enableDROFutureDatedTasks
Description
Indicates whether to enable the Future Dated Steps feature (true) or not (false).
The default value is false. See Enable Future Dated Steps. Available in API version
63.0 and later.
Field Type
boolean
enableDROInflightRequest
Description
Indicates whether to allow changes to fulfillment requests that are in progress (true)
or not (false). The default value is false. Available in API version 64.0 and later.
Field Type
boolean
enableDROTaskSource
Description
Indicates whether to link a Salesforce manual task to a fulfillment step source (true)
or not (false). The default value is false. See Enable the Linking of Task to Step
Source. Available in API version 63.0 and later.
Declarative Metadata Sample Definition
The following is an example of a DynamicFulfillmentOrchestratorSettings component.
<DynamicFulfillmentOrchestratorSettings xmlns="http://soap.sforce.com/2006/04/metadata">
<enableDFOPref>true</enableDFOPref>
<enableDFOFallout>true</enableDFOFallout>
<enableDFOJeopardy>true</enableDFOJeopardy>
<enableDROFutureDatedTasks>true</enableDROFutureDatedTasks>
<enableDROInflightRequest>true</enableDROInflightRequest>
<enableDROTaskSource>true</enableDROTaskSource>
</DynamicFulfillmentOrchestratorSettings>
The following is an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>DynamicFulfillmentOrchestrator</members>
<name>Settings</name>
1796
DynamicFulfillmentOrchestratorSettingsDynamic Revenue Orchestrator

===== PAGE 1811 =====

</types>
<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
The wildcard character *  (asterisk) in the package.xml manifest file doesn’t apply to metadata types for feature settings. The wildcard
applies only when retrieving all settings, not for an individual setting. For details, see Settings. For information about using the manifest
file, see Deploying and Retrieving Metadata with the Zip File.
Dynamic Revenue Orchestrator Tooling API Objects
Tooling API exposes metadata used in developer tooling that you can access through REST or SOAP. Tooling API’s SOQL capabilities for
many metadata types allow you to retrieve smaller pieces of metadata.
CustomFulfillmentScopeCnfg
Represents a user-defined scope to define and customize scope-specific validation and orchestration for flexible fulfillment. This
object is available in API version 64.0 and later.
OrchestrationPlanCtxMapping
Represents an orchestration plan context mapping entry in the org. This entry is used to connect the business data in an object to
the orchestration logic within Dynamic Revenue Orchestrator (DRO) by using the orchestration type. This object is available in API
version 66.0.0 and later.
SEE ALSO:
Tooling API Developer Guide: Introducing Tooling API
CustomFulfillmentScopeCnfg
Represents a user-defined scope to define and customize scope-specific validation and orchestration for flexible fulfillment. This object
is available in API version 64.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
1797
Dynamic Revenue Orchestrator Tooling API ObjectsDynamic Revenue Orchestrator

===== PAGE 1812 =====

Fields
DetailsField
Type
string
AssetContextTag
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Context tag that's used to derive custom scope value from assets. This field is available in
API version 65.0 and later.
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
Required.
Name of the custom fulfillment scope.
Type
boolean
DoesParticipatingAssetImpact
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Required.
Indicates whether the technical assets related to sales transactions impact the fulfillment
line item actions (true) or not (false). If set to true, Dynamic Revenue Orchestrator
reuses the existing technical assets with the same custom value.
The default value is false.
Type
picklist
FallbackScope
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Scope that's used when custom scope can't be determined.
Valid value is:
• LineItem
If an empty value is returned, then ID of the line item is used.
The default value is LineItem.
1798
CustomFulfillmentScopeCnfgDynamic Revenue Orchestrator

===== PAGE 1813 =====

DetailsField
Type
boolean
IsAssetized
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the fulfillment line items grouped by the custom scope are assetized
true  or not (false). If set to false, then the scope can't be associated with assetizable
products.
The default value is false.
Type
string
ItemContextTag
Properties
Create, Filter, Group, Sort, Update
Description
Required.
Context tag that's used to derive custom scope from item context nodes. The supported
value is of string type only.
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The language of the CustomFulfillmentScopeCnfg tooling API object.
Type
ManageableState enumerated list
ManageableState
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Indicates the manageable state of the specified component that is contained in a package:
• beta
• deleted
• deprecated
• deprecatedEditable
• installed
• installedEditable
• released
• unmanaged
1799
CustomFulfillmentScopeCnfgDynamic Revenue Orchestrator

===== PAGE 1814 =====

DetailsField
Type
string
MasterLabel
Properties
Create, Filter, Group, Sort, Update
Description
Label of the custom fulfillment scope.
Type
string
NamespacePrefix
Properties
Filter, Group, Nillable, Sort
Description
The namespace prefix associated with this object. Each Developer Edition organization that
creates a managed package has a unique namespace prefix. Limit: 15 characters. You can
refer to a component in a managed package by using the
namespacePrefix__componentName notation.
The namespace prefix can have one of the following values:
• In Developer Edition organizations, the namespace prefix is set to the namespace prefix
of the organization for all objects that support it. There is an exception if an object is in
an installed managed package. In that case, the object has the namespace prefix of the
installed managed package. This field’s value is the namespace prefix of the Developer
Edition organization of the package developer.
• In organizations that are not Developer Edition organizations, NamespacePrefix
is only set for objects that are part of an installed managed package. There is no
namespace prefix for all other objects.
OrchestrationPlanCtxMapping
Represents an orchestration plan context mapping entry in the org. This entry is used to connect the business data in an object to the
orchestration logic within Dynamic Revenue Orchestrator (DRO) by using the orchestration type. This object is available in API version
66.0.0 and later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
1800
OrchestrationPlanCtxMappingDynamic Revenue Orchestrator

===== PAGE 1815 =====

Special Access Rules
Fields
DetailsField
Type
reference
ContextDefinition
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Required. Name of the context definition to be used for the object.
Type
string
ContextItemNode
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Required. Name of the node that represents an item in the context definition.
Type
string
ContextMapping
Properties
Create, Filter, Group, Sort, Update
Description
Required. Name of the context definition mapping to apply. This mapping must be related
to the specified context definition.
Type
string
ContextRootNode
Properties
Create, Filter, Group, Sort, Update
Description
Required. Name of the node that represents the root in the context definition.
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
1801
OrchestrationPlanCtxMappingDynamic Revenue Orchestrator

===== PAGE 1816 =====

DetailsField
this field, a developer can change the object’s name in a managed package and the changes
are reflected in a subscriber’s organization. Label is Record Type Name.
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The language of the OrchestrationPlanCtxMapping tooling API object.
Valid values are:
Type
ManageableState enumerated list
ManageableState
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Indicates the manageable state of the specified component that is contained in a package:
• beta
• deleted
• deprecated
• deprecatedEditable
• installed
• installedEditable
• released
• unmanaged
Type
string
MasterLabel
Properties
Create, Filter, Group, Sort, Update
Description
Label for the orchestration plan context mapping.
Type
string
NamespacePrefix
Properties
Filter, Group, Nillable, Sort
Description
The namespace prefix associated with this object. Each Developer Edition organization that
creates a managed package has a unique namespace prefix. Limit: 15 characters. You can
1802
OrchestrationPlanCtxMappingDynamic Revenue Orchestrator

===== PAGE 1817 =====

DetailsField
refer to a component in a managed package by using the
namespacePrefix__componentName notation.
The namespace prefix can have one of the following values:
• In Developer Edition organizations, the namespace prefix is set to the namespace prefix
of the organization for all objects that support it. There is an exception if an object is in
an installed managed package. In that case, the object has the namespace prefix of the
installed managed package. This field’s value is the namespace prefix of the Developer
Edition organization of the package developer.
• In organizations that are not Developer Edition organizations, NamespacePrefix
is only set for objects that are part of an installed managed package. There is no
namespace prefix for all other objects.
Type
string
ObjectName
Properties
Create, Filter, Group, Sort, Update
Description
API name of the object for orchestration.
Type
picklist
OrchestrationType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
Name of the type of the orchestration plan.
Valid value is Generic.
Callouts in Dynamic Revenue Orchestrator
Use callout step types to make HTTP calls to an external system. Callout step types use the Data Consumption Framework and Process
Type Integration for interface management and communication with external systems.
Use callout step types to implement these features.
• Endpoint configuration
• Authentication parameters
• Default sync and async implementation
• Extensions or Apex Interfaces
• Error handling and fallout management
• Request and response logging
• Timeouts
Dynamic Revenue Orchestrator supports these types of callouts.
1803
Callouts in Dynamic Revenue OrchestratorDynamic Revenue Orchestrator

===== PAGE 1818 =====

DescriptionType
Use this callout provider to use a fixed payload structure to request
an order. You can also define Omnistudio Integration Procedures
for request transformation and response handling.
Standard Fulfillment Provider
Use this callout provider to implement custom integration scenarios
via the
Apex Type Provider
industriesintegrationfwk.ProcessIntegrationProvider
Apex interface.
Use this callout provider to implement custom integration scenarios
via external services through the OpenAPI specification. You can
External Services Defined Provider
also define Omnistudio Integration Procedures for request
transformation and response handling. To use this callout, the
Omnistudio Admin and Omnistudio Runtime permissions are
required.
Callouts support these integration patterns.
DescriptionType
The callout step is completed when the external system returns a
response.
Sync
The callout step is set to In Progress  when the external
system returns the acknowledgment response with 202 HTTP code.
Async
The system waits until the external system sends a callback
response to complete the callout step. See Asynchronous
Interaction Pattern on page 1817.
Configure Callout Settings
Before you set up a callout provider, configure the callout settings. The settings include the creation of a named credential and an
external credential, the creation of an integration definition, and the configuration of a fulfillment step definition.
Standard Fulfillment Provider
The Standard Fulfillment Provider or CalloutIntegrationProvider  is a provider for the order fulfillment usage type. A
Fulfillment Designer can configure this provider.
Apex Type Provider
Implement custom integration logic via Apex by using the Apex Type Provider. This provider requires an Apex Integration Developer
to implement a custom Apex adapter interface.
External Services Defined Provider
Generate interface contract and Apex types by using external services and Open API compatible schema.
Asynchronous Interaction Pattern
To specify an asynchronous request, you must add the callback URI to the integration definition for Standard Fulfillment Provider or
Apex Type Provider as an optional attribute.
1804
Callouts in Dynamic Revenue OrchestratorDynamic Revenue Orchestrator

===== PAGE 1819 =====

Input and Output Transformation Processors
Use input and output processors to process a standard fulfillment request before sending it to an external system.
SEE ALSO:
Salesforce Help: Data Consumption Framework
Configure Callout Settings
EDITIONS
Available in: Developer,
Enterprise, and Unlimited
Editions
USER PERMISSIONS
To create authenticated
callouts:
• External Credentials
Principal Access
Permission
Before you set up a callout provider, configure the callout settings. The settings include the creation
of a named credential and an external credential, the creation of an integration definition, and the
configuration of a fulfillment step definition.
Meet these prerequisites before you configure the callout settings.
• Configure named and external credentials to define access to an external system. Specify a
named credential as the callout endpoint and an external credential to configure the
authentication protocol.
See Create Named Credentials and External Credentials.
• Create integration definitions to connect Salesforce with an external system. Integration
definitions use APIs to perform operations in both Salesforce and the external system. You can
create Apex Defined, External Services Defined, or Standard integration definitions.
See Create an Integration Definition.
• Define a fulfillment step with Callout  as the step type. Additionally, set the integration
definition name and integration user.
See Callout Fulfillment Step.
Standard Fulfillment Provider
The Standard Fulfillment Provider or CalloutIntegrationProvider  is a provider for the order fulfillment usage type. A
Fulfillment Designer can configure this provider.
The Standard Fulfillment Provider includes these features.
• Predefined payload with sales transaction items and fulfillment items data, including attribute values
• Fixed integration parameters such as timeouts, credentials, encoding styles, and path. See Integration Definition for Standard
Fulfillment Provider on page 1810 for details about the integration parameters.
• Modified requests and responses via Omnistudio Integration Procedures
• Asynchronous interaction pattern. See Asynchronous Interaction Pattern on page 1817.
• Request and response logging
• Error handling and retry policies. See Fallout Design and Management.
• Request transformation and response handling via integration procedures
To configure the callout settings for Standard Fulfillment Provider, see Configuration Steps.
1805
Configure Callout SettingsDynamic Revenue Orchestrator

===== PAGE 1820 =====

Request Payload
This example shows a sample request payload structure with data for sales transaction items and fulfillment transaction items. This data
is derived using context definition mappings that are defined through settings. See Context Definitions in Order Orchestration.
{
"AccountId": "001xx000003GbsxAAC",
"OrderId": "801xx000003GbsyAAC",
"StepId": "802xx000001ndnyAAA",
"PlanSourceId": "802xx000001ndnyAAA",
"StepSourceId": "13Wxx0000004Cdh",
"CorrelationId": "callout:13Wxx0000004Cdh:",
"SalesTransactionItems": [
{
"ArePartialPeriodsAllowed": "false",
"ParentReference": "801xx000003GbsyAAC",
"IsAssetizable": "true",
"ProductName": "iPhone18",
"ProductCode": "iPhone18",
"SalesTransactionItemParent": "801xx000003GbsyAAC",
"Attributes": [
{
"AttributeKey": "0tjxx00000000ePAAQ",
"ParentReference": "802xx000001ndnxAAA",
"AttributeValue": "true",
"AttributeName": "IsDeliveryNotificationNeeded",
"AttributeDefinitionCode": "FDT5",
"SalesTransactionItemAttrParent": "802xx000001ndnxAAA"
},
{
"AttributeKey": "0tjxx00000000eNAAQ",
"ParentReference": "802xx000001ndnxAAA",
"AttributeValue": "10",
"AttributeName": "FDTCharge",
"AttributeDefinitionCode": "FDT3",
"SalesTransactionItemAttrParent": "802xx000001ndnxAAA"
}
],
"Product": "01txx0000006igoAAA",
"Quantity": "1.0",
"ListPrice": "1.0",
"ItemTotalAdjustmentAmount": "0.0",
"SalesTransactionItemSource": "802xx000001ndnxAAA",
"PricebookEntry": "01uxx0000008zT8AAI",
"StartDate": "2024-10-15T00:00:00.000Z",
"UnitPrice": "1.0",
"RoundedLineAmount": "1.0",
"EndQuantity": "1.0",
"TotalTaxAmount": "0.0",
"IsItemLocked": "false",
"TotalPrice": "1.0",
"ProductBasedOn": "11Bxx000002C9M2EAK",
"SalesTransactionActionType": "Add",
"SalesTransactionAction": "8OAxx0000004DGOGA2"
},
1806
Standard Fulfillment ProviderDynamic Revenue Orchestrator

===== PAGE 1821 =====

{
"ArePartialPeriodsAllowed": "false",
"ParentReference": "801xx000003GbsyAAC",
"IsAssetizable": "true",
"ProductName": "iPhone19",
"ProductCode": "iPhone19",
"SalesTransactionItemParent": "801xx000003GbsyAAC",
"Attributes": [
{
"AttributeKey": "0tjxx00000000eQAAQ",
"ParentReference": "802xx000001ndnyAAA",
"AttributeValue": "false",
"AttributeName": "IsDelivered",
"AttributeDefinitionCode": "FDT6",
"SalesTransactionItemAttrParent": "802xx000001ndnyAAA"
}
],
"Product": "01txx0000006igpAAA",
"Quantity": "1.0",
"ListPrice": "1.0",
"ItemTotalAdjustmentAmount": "0.0",
"SalesTransactionItemSource": "802xx000001ndnyAAA",
"PricebookEntry": "01uxx0000008zTAAAY",
"StartDate": "2024-10-20T00:00:00.000Z",
"UnitPrice": "1.0",
"RoundedLineAmount": "1.0",
"EndQuantity": "1.0",
"TotalTaxAmount": "0.0",
"IsItemLocked": "false",
"TotalPrice": "1.0",
"ProductBasedOn": "11Bxx000002C9M2EAK",
"SalesTransactionActionType": "Add",
"SalesTransactionAction": "8OAxx0000004DGOGA2",
"SalesTrxnItemDescription": "TrackingRef:TRK-HUBSWQT18-4238"
}
],
"FulfillmentTransactionItems": [
{
"ParentReference": "0a3xx00000000JOAAY",
"OriginalQuantity": "2.0",
"FulfillmentItemSource": "0a4xx00000000JOAAY",
"Attributes": [
{
"FulfillmentOrderLineId": "0a4xx00000000JOAAY",
"LineAttributeDefinitionCode": "FDT6",
"ParentReference": "0a4xx00000000JOAAY",
"LineAttributeName": "IsDelivered",
"LineAttributeValue": "false",
"LineAttributeKey": "0tjxx00000000eQAAQ"
},
{
"FulfillmentOrderLineId": "0a4xx00000000JOAAY",
"LineAttributeDefinitionCode": "FDT2",
"ParentReference": "0a4xx00000000JOAAY",
1807
Standard Fulfillment ProviderDynamic Revenue Orchestrator

===== PAGE 1822 =====

"LineAttributeName": "FDTColor",
"LineAttributeKey": "0tjxx00000000eMAAQ"
},
{
"FulfillmentOrderLineId": "0a4xx00000000JOAAY",
"LineAttributeDefinitionCode": "FDT1",
"ParentReference": "0a4xx00000000JOAAY",
"LineAttributeName": "FDTSize",
"LineAttributeKey": "0tjxx00000000eLAAQ"
}
],
"FulfillmentItemAction": "ADD",
"FulfillmentItemProductCode": "iPhone-Pack",
"FulfillmentOrderItemQuantity": "2.0",
"FulfillmentItemProductName": "iPhone-Pack",
"FulfillmentOrderId": "0a3xx00000000JOAAY",
"FulfillmentItemTypeCode": "Product",
"FulfillmentItemType": "Order Product",
"FulfillmentOrderNumber": "FO-0002",
"FulfillmentItemStartDate": "2024-10-20T00:00:00.000Z",
"FulfillmentItemProductId": "01txx0000006igqAAA"
},
{
"ParentReference": "0a3xx00000000JNAAY",
"OriginalQuantity": "2.0",
"FulfillmentItemSource": "0a4xx00000000JNAAY",
"Attributes": [
{
"FulfillmentOrderLineId": "0a4xx00000000JNAAY",
"LineAttributeDefinitionCode": "FDT2",
"ParentReference": "0a4xx00000000JNAAY",
"LineAttributeName": "FDTColor",
"LineAttributeKey": "0tjxx00000000eMAAQ"
},
{
"FulfillmentOrderLineId": "0a4xx00000000JNAAY",
"LineAttributeDefinitionCode": "FDT5",
"ParentReference": "0a4xx00000000JNAAY",
"LineAttributeName": "IsDeliveryNotificationNeeded",
"LineAttributeValue": "false",
"LineAttributeKey": "0tjxx00000000ePAAQ"
},
{
"FulfillmentOrderLineId": "0a4xx00000000JNAAY",
"LineAttributeDefinitionCode": "FDT3",
"ParentReference": "0a4xx00000000JNAAY",
"LineAttributeName": "FDTCharge",
"LineAttributeKey": "0tjxx00000000eNAAQ"
}
],
"FulfillmentItemAction": "ADD",
"FulfillmentItemProductCode": "iPhone-Tech",
"FulfillmentOrderItemQuantity": "2.0",
"FulfillmentItemProductName": "iPhone-Tech",
1808
Standard Fulfillment ProviderDynamic Revenue Orchestrator

===== PAGE 1823 =====

"FulfillmentOrderId": "0a3xx00000000JNAAY",
"FulfillmentItemTypeCode": "Product",
"FulfillmentItemType": "Order Product",
"FulfillmentOrderNumber": "FO-0001",
"FulfillmentItemStartDate": "2024-10-10T00:00:00.000Z",
"FulfillmentItemProductId": "01txx0000006igrAAA"
}
]
}
The step source ID of the fulfillment step, which is either a related order or fulfillment item, determines the payload composition with
these considerations.
• If the step source ID is an order item, then all order items of the order are included in the payload under the SalesTransactionItems
node.
• If the step source ID is a fulfillment item, then all fulfillment items of the fulfillment order are included in the payload under the
FulfillmentTransactionItems node.
• If a product attribute doesn't have a defined code, then the attribute is excluded from the payload.
Considerations
Keep these considerations in mind for the request payload.
• The maximum request payload size limit is 12 MB.
• The default timeout period is five seconds, and the maximum timeout period is 120 seconds.
• The encoding style for fulfillment order line items, sales transaction items, and attributes can be configured through the Integration
Definition for Standard Fulfillment Provider on page 1810.
Error Handling
To verify if the callout request was successful, check the status  value in the payload. If the status is undefined, then these HTTP codes
indicate a successful response.
• 200
• 201
• 202
• 203
• 204
• 205
• 206
• 302
• 304
If the request isn't successful, then the fulfillment step state is marked as Fatally Failed.
Integration Definition Configurations
You can configure these additional features for the integration definition.
1809
Standard Fulfillment ProviderDynamic Revenue Orchestrator

===== PAGE 1824 =====

• Select the Save the request and response as attachments to the record checkbox for the integration definition to save request
and response payloads as attachments to the Integration Provider Execution record. Content publish limits apply when saving
request and response payloads as attachments. Use Shield Platform Encryption for secure storage of sensitive information.
• Define Input and Output Processors for the Integration Definition for the pre-processing of the standard fulfillment request before
you send the request to an external system. See Omnistudio Integration Procedures.
See Create an Integration Definition.
Integration Definition for Standard Fulfillment Provider
Use supported attribute values of an integration definition for a Standard Fulfillment Provider to implement features as per your
requirement.
Integration Definition for Standard Fulfillment Provider
Use supported attribute values of an integration definition for a Standard Fulfillment Provider to implement features as per your
requirement.
The Standard Fulfillment Provider supports these attribute values.
1810
Standard Fulfillment ProviderDynamic Revenue Orchestrator

===== PAGE 1825 =====

DescriptionAttribute Name
API name of the associated named credentials.Named Credentials
Additional string that's added to the URL specified in the named
credential endpoint.
Path
Number of milliseconds to set as a timeout parameter for the HTTP
connection.
Timeout (ms)
Attribute used by a third party as the callback to process steps in
case of a async callout. Additionally, this attribute also indicates
these scenarios.
Callback URI
• The configured callout is an async callout.
• If callback URI is defined, then it's included as the
ResponseUri  parameter value in the default payload for
Standard Fulfillment Provider. For example, a ResponseUri
parameter value as
/services/apexrest/async/callout.
• The executor expects 202 response code from the remote
destination.
• The 202 response code keeps the Fulfillment Step state as
Running whereas 200 response code completes it.
Type_Subtype  or Id  of OmniProcess to process the input
payload.
Input Processor
Type_Subtype  or Id  of OmniProcess to process the output
payload.
Output Processor
Required.Item Encoding Style
Encoding style for fulfillment transaction items and sales transaction
items. Valid values are:
• Flat—Includes a list of fulfillment transaction items and sales
transaction items without any hierarchy details in the payload.
• Structure—Includes a list of all child line items if the step's
source line item has a hierarchy of line items associated with
it.
If item encoding style is configured as Structure  on a
fulfillment order line item or a sales transaction item, then the
payload contains the details of the line item that the fulfillment
order line item or sales transaction item is decomposed from.
If the fulfillment order line item or sales transaction item is
decomposed from the root of a bundle order line item or sales
transaction item, then the payload contains the entire order
line item or sales transaction item bundle structure.
The default value is Flat.
1811
Standard Fulfillment ProviderDynamic Revenue Orchestrator

===== PAGE 1826 =====

DescriptionAttribute Name
Required.Attribute Encoding Style
Generates the payload for attributes based on the specified
encoding style. Valid values are:
• Flat—Includes specific details in key-value pair format that
doesn't include granular details of attributes.
• Structure—This payload structure includes granular details
of attributes.
The default value is Structure.
If this checkbox is selected, the request payload includes empty
attribute values wherever applicable.
Send Empty Attributes
If this checkbox is selected, a default request payload is generated
to optimize processing performance. If this checkbox isn't selected,
a value for the input processor is required.
Send Payload
Apex Type Provider
Implement custom integration logic via Apex by using the Apex Type Provider. This provider requires an Apex Integration Developer to
implement a custom Apex adapter interface.
Use a custom Apex adapter to:
• Include and use integration parameters in adapter implementations such as timeouts, credentials, and path.
• Generate and transform requests and responses via Omnistudio Integration Procedures or Extract, Transform, Load (ETL) libraries.
• Enable asynchronous interaction pattern.
• Enable request and response logging by implementing a specific Apex interface.
• Handle errors, and integrate with fallout rules.
To configure the callout settings for Apex Type Provider, see Configuration Steps.
Integration Adapter Implementation
Implement the industriesintegrationfwk.ProcessIntegrationProvider  Apex interface. Use the
industriesintegrationfwk.ApexProviderAttr  class to define and access the attribute values in the integration
provider definition.
global with sharing class DROSampleOrderAdapter implements
industriesintegrationfwk.ProcessIntegrationProvider {
// Named credential attribute
private static final String MOCK_CALLOUT_NAMED_CREDENTIAL =
'callout:DROOrderInterfaceNamedCred';
private final static Integer TIMEOUT = 10000; // Request timeout in milliseconds, or
can be defined on Integration Definition as an Attribute
1812
Apex Type ProviderDynamic Revenue Orchestrator

===== PAGE 1827 =====

private static final industriesintegrationfwk.ApexProviderAttr NAMED_CRED_ATTR = new
industriesintegrationfwk.ApexProviderAttr('Named Credential',
'Named_Credential', 'DROOrderInterfaceNamedCred', true, 'String');
private static final industriesintegrationfwk.ApexProviderAttr ENDPOINT_ATTR = new
industriesintegrationfwk.ApexProviderAttr('Endpoint URI',
'Endpoint_URI', '/v1/orderitems/', true, 'String');
/**
* @param requestGuid Request Globally Unique Identifier (GUID) provided
by the client
* @param inputRecordId Input Record ID — value is taken from Fulfillment
Step > Fulfillment Step Source > Source Line Item
* @param payload Payload to be passed to the Provider Class (empty
in DRO)
* @param attributes Map of configuration attributes
* @return IntegrationCalloutResponse Response sent to the client
*/
global static industriesintegrationfwk.IntegrationCalloutResponseexecuteCallout(String
requestGuid, String inputRecordId, String payload, Map<String, Object> attributes) {
// create request
String msgBody = '{\"message\":\"Hello\",'
+ '\n\"requestGuid\":\"' + requestGuid + '\",\n'
+ '\n\"inputRecordId\":\"' + inputRecordId + '\",\n'
+ '\n\"payload\":\"' + payload + '\"}'
;
String endpointUri = (String) attributes.get('Endpoint_URI');
// Make a call
HttpResponse response = makeCallout(endpointUri, msgBody);
// process response and pass details to the DRO Callout Step processor by using
IntegrationCalloutResponse(isSuccess, ResponseCode, ErrorMessage)
industriesintegrationfwk.IntegrationCalloutResponse integrationCalloutResponse =
handleResponse(response);
return integrationCalloutResponse;
}
// define configurable attriobutes
global static List<industriesintegrationfwk.ApexProviderAttr> getProviderAttributes()
{
List<industriesintegrationfwk.ApexProviderAttr> defaults = new
List<industriesintegrationfwk.ApexProviderAttr>();
defaults.add(NAMED_CRED_ATTR);
defaults.add(ENDPOINT_ATTR);
// add any attributes such as endpoint, timeout, interface, and params
// ...
return defaults;
}
// Call Mock Service API.
private static HttpResponse makeCallout(String endpointUri, String msgBody) {
1813
Apex Type ProviderDynamic Revenue Orchestrator

===== PAGE 1828 =====

// Construct the request object
String endPoint = MOCK_CALLOUT_NAMED_CREDENTIAL + endpointUri;
HttpRequest request = new HttpRequest();
request.setMethod('POST');
request.setHeader('Content-Type', 'application/json');
request.setHeader('Accept', 'application/json');
request.setEndpoint(endPoint);
request.setTimeout(TIMEOUT);
request.setBody(msgBody);
// Send request
HttpResponse response = new Http().send(request);
return response;
}
}
Error Handling
This sample shows how to pass errors from response to orchestration via the IntegrationResponse interface in the Apex provider
implementation. See ProcessIntegrationProvider Interface.
public static industriesintegrationfwk.IntegrationCalloutResponsehandleResponse(HttpResponse
response) {
industriesintegrationfwk.IntegrationCalloutResponse integrationCalloutResponse;
Map<String, Object> responseGroup = getResponseGroupAfterCallout(response);
if(response.getStatusCode() == 200)
{
// SUCCESS
integrationCalloutResponse = new
industriesintegrationfwk.IntegrationCalloutResponse(true);
integrationCalloutResponse.setResponseCode(response.getStatusCode());
integrationCalloutResponse.setReturnValue(responseGroup);
} else {
//FAILURE - pass error to DRO Fallout Handling to apply Retry Policies
integrationCalloutResponse = new
industriesintegrationfwk.IntegrationCalloutResponse(false);
integrationCalloutResponse.setResponseCode(response.getStatusCode());
integrationCalloutResponse.setReturnValue(responseGroup);
integrationCalloutResponse.setErrorMessage('Unable to process request.');
}
return integrationCalloutResponse;
}
// Process Response payLoad
private static Map<String, Object> getResponseGroupAfterCallout(HttpResponse response)
{
Map<String, Object> responseGroup = new Map<String, Object>();
if (response.getStatusCode() == 200) {
1814
Apex Type ProviderDynamic Revenue Orchestrator

===== PAGE 1829 =====

responseGroup.put('isSuccess', true);
} else {
responseGroup.put('isSuccess', false);
}
responseGroup.put('response', getResponseMap(response.getBody()));
return responseGroup;
}
// Convert response string into Map
private static Map<String,Object> getResponseMap(String responseBody) {
try {
Map<String,Object> responseBodyMap = (Map<String,Object>)
JSON.deserializeUntyped(responseBody);
return responseBodyMap;
} catch (Exception e) {
Map<String, Object> responseMap = new Map<String,Object>();
responseMap.put('response', responseBody);
return responseMap;
}
}
The fulfillment step state changes to Fatally Failed, and the error message is saved in the Execution Message  field.
Apex Advanced Interface Implementation
To use advanced features such as logging, the Apex provider must implement the Apex Provider Advanced interface. You must use the
HttpBaseProvider client for HTTP requests.
1815
Apex Type ProviderDynamic Revenue Orchestrator

===== PAGE 1830 =====

This example shows a sample of the ProcessIntegrationProviderAdvanced  Apex interface implementation.
global with sharing class DFOApexVlocMockWithDelay
implements industriesintegrationfwk.ProcessIntegrationProviderAdvanced {
...
global static industriesintegrationfwk.IntegrationCalloutResponse executeCallout(String
requestGuid, String inputRecordId, String payload, Map<String, Object> attributes,
industriesintegrationfwk.HttpBaseProvider httpProvider) {
...
String endPoint = MOCK_CALLOUT_NAMED_CREDENTIAL + '/delay/5';
HttpRequest request = new HttpRequest();
request.setMethod('POST');
request.setHeader('Content-Type', 'application/json');
request.setHeader('Accept', 'application/json');
request.setEndpoint(endPoint);
request.setTimeout(TIMEOUT);
request.setBody(msgBody);
// Send request
//HttpResponse response = httpProvider.httpCallout(request);
HttpResponse response = new Http().send(request);
Integration Definition Configuration
Select the Save the request and response as attachments to the record checkbox for the integration definition to save request and
response payloads as attachments to the Integration Provider Execution record. Content publish limits apply when saving request and
response payloads as attachments. Use Shield Platform Encryption for secure storage of sensitive information.
See Create an Integration Definition.
Log Records
Integration Provider execution records are created on every request and associated with the fulfillment step. The referenced object
identifier is set to order item or fulfillment order line item ID. SeeIntegrationProviderExecution.
To view the Integration Provider execution records, configure the Fulfillment Step record page to include the Integration Provider
Executions related list by using Lightning App Builder. See Lightning App Builder.
1816
Apex Type ProviderDynamic Revenue Orchestrator

===== PAGE 1831 =====

External Services Defined Provider
Generate interface contract and Apex types by using external services and Open API compatible schema.
To configure the callout settings for External Services Defined Provider, see Configuration Steps.
As an integration specialist user or admin user, perform these steps.
• Set up an external service and actions.
• In the external service definition, include integration parameters such as error codes, credentials, and path.
External Service
Use external services for outbound integrations from Salesforce by using low-code, process-based integrations to enhance your Apex
integrations. See External Services.
Integration Definition Configurations
You can configure these additional features for the integration definition.
• Select the Save the request and response as attachments to the record checkbox for the integration definition to save request
and response payloads as attachments to the Integration Provider Execution record. Content publish limits apply when saving
request and response payloads as attachments. Use Shield Platform Encryption for secure storage of sensitive information.
• Define Input and Output Processors for the Integration Definition for the pre-processing of the standard fulfillment request before
you send the request to an external system. See Omnistudio Integration Procedures.
See Create an Integration Definition.
Step Definition
Set the created integration definition on the Step Definition record with Callout  as the step type.
Asynchronous Interaction Pattern
To specify an asynchronous request, you must add the callback URI to the integration definition for Standard Fulfillment Provider or
Apex Type Provider as an optional attribute.
Standard Fulfillment Provider
• Provide the callback URI in the integration definition to accept the callback.
• Use these steps to set up the async callout.
– • Use the ResponseUri  key to retrieve the Callback URI value from the payload.
• Use the StepId key to retrieve the Fulfillment Step value from the payload. If order item ID is returned instead of Fulfillment
Step ID, use CorrelationId  key to extract the value of the step ID. For example, callout:13Wxx0000004CAf:.
• Pass the StepId value to the callback URI endpoint. Return 202 response code to ensure the Fulfillment Step is in Running
state. Otherwise, the 200 response code completes the step.
Here's a sample payload.
{
"ResponseUri": "/services/apexrest/async/callout",
1817
External Services Defined ProviderDynamic Revenue Orchestrator

===== PAGE 1832 =====

"StepId": "802xx000001nb1MAAQ",
"CorrelationId": "callout:13Wxx0000004CAf:",
...//Other values
}
• Extract the step ID from the request. Find the Fulfillment Step ID in the org by using the extracted step ID and update the Fulfillment
Step state to Completed.
Apex Type Provider
• Provide the callback URI in the integration definition to accept the callback.
• Set up the async callout by using Apex Type Provider.
– Create an Apex class that implements the ProcessIntegrationProvider  interface.
Here's a sample that shows the addition of a callback URI to the provider attribute for Apex Type Provider.
global with sharing class DFOAsyncApexSample implements
industriesintegrationfwk.ProcessIntegrationProvider {
•
private static final industriesintegrationfwk.ApexProviderAttr NAMED_CRED_ATTR
=
new industriesintegrationfwk.ApexProviderAttr('Named Credential',
'Named_Credential', 'DFOCalloutMockCreds', true, 'String');
private static final industriesintegrationfwk.ApexProviderAttrCALLBACK_URL_ATTR
=
new industriesintegrationfwk.ApexProviderAttr('Callback URL',
'Callback_URL', 'DFOCallbackUrl', true, 'String');
global static List<industriesintegrationfwk.ApexProviderAttr>
getProviderAttributes() {
List<industriesintegrationfwk.ApexProviderAttr> defaults = new
List<industriesintegrationfwk.ApexProviderAttr>();
defaults.add(NAMED_CRED_ATTR);
defaults.add(CALLBACK_URL_ATTR);
return defaults;
}
• Specify the Fulfillment Step ID as the value of the requestGuid  parameter of the executeCallout  method. You
can also extract the Step ID from the CorrelationId  key value. For example, "callout:13Wxx0000004CAf:".
Here's a sample payload that assigns the provider attribute values.
public interface ProcessIntegrationProvider {
IntegrationCalloutResponse executeCallout(String requestGuid,
String inputRecordId, String payload, Map<String, Object> attributes);
List<ProviderAttr> getProviderAttributes();
}
– Set response code to 202 to indicate that the callout is asynchronously executed and in Processing  state.
1818
Asynchronous Interaction PatternDynamic Revenue Orchestrator

===== PAGE 1833 =====

Here's a sample payload that sets the response code.
global with sharing class DFOAsyncApexSample implements
industriesintegrationfwk.ProcessIntegrationProvider {
...
IntegrationCalloutResponse executeCallout(String requestGuid,
String inputRecordId, String payload, Map<String, Object> attributes){
// execute http request
...
// set accepted if no failures
IntegrationCalloutResponse acceptedResponse =
new IntegrationCalloutResponse(true);
acceptedResponse.setResponseCode(202);
return new IntegrationCalloutResponse();
}
}
– The callback URI is visible in the integration definition.
• Extract the step ID from the request. Find the Fulfillment Step ID in the org by using the extracted step ID and update the Fulfillment
Step state to Completed.
FulfillmentStep step = new FulfillmentStep(id = 'stepId', State = 'Completed');
upsert step;
Input and Output Transformation Processors
Use input and output processors to process a standard fulfillment request before sending it to an external system.
Prerequisites
• Omnistudio license is required.
• Omnistudio Admin permission set license is assigned to Integration Configuration User (Fulfillment Designer).
• The input and output procedure attributes of an integration definition, which are available from Setup, are assigned with the
Omnistudio Integration Procedure request and response. You can use Type_Subtype  or Id  of OmniProcess as the values for
attributes.
When a callout step is executed, these steps are followed.
• The defined integration procedures are identified for request and response handling from an integration definition.
1819
Input and Output Transformation ProcessorsDynamic Revenue Orchestrator

===== PAGE 1834 =====

• The input processor generates the request by using Fulfillment Step Source > SourceIdentifier  as the
InputRecordId  input parameter value. For example, the ID of an order item.
• The output processor handles the response by passing a map to the Integration Procedure service. The results from the Integration
Procedure are used to identify any errors and details are passed to Dynamic Revenue Orchestrator.
Dynamic Revenue Orchestrator Platform Events
Salesforce publishes standard platform events in response to an action that occurred in the org or to report errors.
FulfillmentSourceChangeEvent
Notifies updates to the sources orchestrated by Dynamic Revenue Orchestrator like order product or fulfillment order product. This
object is available in API version 66.0 and later.
SalesTrxnDecompositionEvent
Notifies when the decomposition process status changes. This object is available in API version 66.0 and later.
FulfillmentSourceChangeEvent
Notifies updates to the sources orchestrated by Dynamic Revenue Orchestrator like order product or fulfillment order product. This object
is available in API version 66.0 and later.
Supported Calls
describeSObjects()
Supported Subscribers
Supported?Subscriber
Apex Triggers
Flows
Processes
Pub/Sub API
Streaming API (CometD)
Streaming API Subscription Channel
/event/SalesTrxnDecompositionEvent
Special Access Rules
This object is available in orgs with Revenue Cloud.
1820
Dynamic Revenue Orchestrator Platform EventsDynamic Revenue Orchestrator

===== PAGE 1835 =====

Event Delivery Allocation Enforced
Yes
Fields
DetailsField
Type
string
EventUuid
Properties
Nillable
Description
A universally unique identifier (UUID) that identifies a platform event message.
Type
string
RecordIdentifier
Properties
Create, Nillable
Description
The identifier of the source record that has been updated.
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
SalesTrxnDecompositionEvent
Notifies when the decomposition process status changes. This object is available in API version 66.0 and later.
Supported Calls
describeSObjects()
1821
SalesTrxnDecompositionEventDynamic Revenue Orchestrator

===== PAGE 1836 =====

Supported Subscribers
Supported?Subscriber
Apex Triggers
Flows
Processes
Pub/Sub API
Streaming API (CometD)
Streaming API Subscription Channel
/event/SalesTrxnDecompositionEvent
Special Access Rules
This object is available in orgs with Revenue Cloud.
Event Delivery Allocation Enforced
Yes
Fields
DetailsField
Type
string
ErrorCode
Properties
Create, Nillable
Description
The error code returned for a decomposition process failure.
Type
string
EventUuid
Properties
Nillable
Description
A universally unique identifier (UUID) that identifies a platform event message.
Type
string
ReplayId
1822
SalesTrxnDecompositionEventDynamic Revenue Orchestrator

===== PAGE 1837 =====

DetailsField
Properties
Nillable
Description
Represents an ID value that is populated by the system and refers to the position of the event
in the event stream. Replay ID values aren’t guaranteed to be contiguous for consecutive
events. A subscriber can store a replay ID value and use it on resubscription to retrieve missed
events that are within the retention window.
Type
string
SalesTransactionIdentifier
Properties
Create, Nillable
Description
The sales transaction being decomposed.
Type
string
Status
Properties
Create, Nillable
Description
The status of the decomposition process.
1823
SalesTrxnDecompositionEventDynamic Revenue Orchestrator

===== PAGE 1838 =====

