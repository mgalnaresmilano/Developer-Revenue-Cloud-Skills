---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 9 — Advanced Approvals

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 9 Advanced Approvals
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions of Revenue Cloud
where Advanced Approvals
is enabled
Advanced Approvals feature provides invocable actions to
streamline complex business processes. These actions automate
and manage intricate parallel or sequential approval chains with
detailed audit trails.
SEE ALSO:
Salesforce Help: Advanced Approvals
In this chapter ...
• Advanced Approvals
Fields on Standard
Objects
• Advanced Approvals
Standard Invocable
Actions
• Advanced Approvals
Metadata API Types
1653

===== PAGE 1668 =====

Advanced Approvals Fields on Standard Objects
Advanced Approvals adds standard and custom fields to some standard Salesforce objects. These fields are available only in Revenue
Cloud orgs where Advanced Approvals is enabled.
ApprovalSubmission
Represents the instance of an approval request that's submitted for a record of the related object. This object is available in API
version 62.0 and later.
Advanced Approvals Fields on Approval Work Item
Standard and custom fields extend the standard Approval Work Item object for use in Advanced Approvals.
ApprovalSubmission
Represents the instance of an approval request that's submitted for a record of the related object. This object is available in API version
62.0 and later.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
Special Access Rules
This object is available in Enterprise, Unlimited, and Developer Editions of Revenue Cloud.
Fields
DetailsField
Type
textarea
Comments
Properties
Nillable
Description
The comments about the request that's submitted for approval.
Type
boolean
DoesSendApprovalEmail
Properties
Defaulted on create, Filter, Group, Sort
Description
Required. Indicates whether approval request emails are sent to approvers and delegates
(true) or not (false).
The default value is false.
1654
Advanced Approvals Fields on Standard ObjectsAdvanced Approvals

===== PAGE 1669 =====

DetailsField
Type
reference
FlowOrchestrationInstanceId
Properties
Filter, Group, Nillable, Sort
Description
The ID of the flow orchestration instance record that's associated with the approval.
This field is a relationship field.
Relationship Name
FlowOrchestrationInstance
Refers To
FlowOrchestrationInstance
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The auto-generated name for the approval submission.
Type
reference
OwnerId
Properties
Filter, Group, Sort
Description
The ID of the user or the group that owns the approval submission record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
Type
reference
RelatedRecordId
Properties
Filter, Group, Nillable, Sort
Description
Required. The ID of the related record that's submitted for approval.
This field is a polymorphic relationship field.
Relationship Name
RelatedRecord
1655
ApprovalSubmissionAdvanced Approvals

===== PAGE 1670 =====

DetailsField
Refers To
Account, AdAvailabilityViewConfig, Address, AnalyticsUserAttrFuncTkn, ApprovalSubmission,
ApprovalSubmissionDetail, ApprovalWorkItem, Asset, AssetAction, AssetActionSource,
AssetContractRelationship, AssetRateAdjustment, AssetRateCardEntry, AssetRelationship,
AssetStatePeriod, AssociatedLocation, AsyncOperationTracker, AttrPicklistExcludedValue,
AttributeAdjustmentCondition, AttributeBasedAdjRule, AttributeBasedAdjustment,
AttributeCategory, AttributeCategoryAttribute, AttributeDefinition, AttributePicklist,
AttributePicklistValue, AuthorizationForm, AuthorizationFormConsent,
AuthorizationFormDataUse, AuthorizationFormText, BatchJob, BatchJobPart,
BatchJobPartFailedRecord, BundleBasedAdjustment, BusinessBrand, Case, CaseComment,
ChannelProgram, ChannelProgramLevel, ChannelProgramMember, CollaborationGroup,
CommSubscription, CommSubscriptionChannelType, CommSubscriptionConsent,
CommSubscriptionTiming, Contact, ContactPointAddress, ContactPointConsent,
ContactPointEmail, ContactPointPhone, ContactPointTypeConsent, ContactRequest,
ContextDefinitionSync, Contract, ContractItemPrice, ContractItemPriceAdjTier, CostBook,
CostBookEntry, Customer, DTRecordsetReplica, DataUseLegalBasis, DataUsePurpose,
DecisionTblFileImportData, DelegatedAccount, DocGenerationQueryResult,
DocTemplateSectionCondition, DocumentEnvelope, DocumentGenerationProcess,
DocumentRecipient, DocumentTemplate, DocumentTemplateContentDoc,
DocumentTemplateSection, DocumentTemplateToken, DuplicateRecordItem,
DuplicateRecordSet, EmailMessage, EngagementChannelType, ExpressionSetConstraintObj,
ExternalEventMapping, FlowOrchestrationInstance, FulfillmentOrder,
FulfillmentOrderItemAdjustment, FulfillmentOrderItemTax, FulfillmentOrderLineItem,
GeneratedDocument, GeneratedDocumentSection, Idea, Image, Individual,
IntegrationProviderDcsnRqmt, IntegrationProviderExecution, Lead, Location,
LocationTrustMeasure, ManagedContentVariant, ObjectStateDefinition, ObjectStateTransition,
ObjectStateValue, Obligation, Opportunity, OpportunityRelatedDeleteLog, Order, OrderAction,
OrderAdjustmentGroup, OrderDeliveryGroup, OrderDeliveryMethod, OrderItem,
OrderItemAdjustmentLineItem, OrderItemDetail, OrderItemRateAdjustment,
OrderItemRateCardEntry, OrderItemRecipient, OrderItemRelationship, OrderItemTaxLineItem,
OrgMetricScanResult, OrgMetricScanSummary, Organization, PartnerFundAllocation,
PartnerFundClaim, PartnerFundRequest, PartnerMarketingBudget, PartyConsent,
PriceBookEntryDerivedPrice, PriceBookRateCard, PricingAdjBatchJob, PricingAdjBatchJobLog,
PricingApiExecution, PricingProcessExecution, ProcessException, Product2,
ProductAttributeDefinition, ProductCatalog, ProductCategory, ProductCategoryDisqual,
ProductCategoryProduct, ProductCategoryQualification, ProductClassification,
ProductClassificationAttr, ProductComponentGroup, ProductComponentGrpOverride,
ProductConfigFlowAssignment, ProductConfigurationFlow, ProductConfigurationRule,
ProductDisqualification, ProductPriceHistoryLog, ProductPriceRange, ProductQualification,
ProductRampSegment, ProductRelComponentOverride, ProductUsageGrant, ProfileSkill,
ProfileSkillEndorsement, ProfileSkillUser, PromptAction, PromptError, QuickText,
QuickTextUsage, Quote, QuoteLineDetail, QuoteLineItem, QuoteLineItemRecipient,
QuoteLineRateAdjustment, QuoteLineRateCardEntry, RateAdjustmentByAttribute,
RateAdjustmentByTier, RateCard, RateCardEntry, RatingFrequencyPolicy, SalesTransactionType,
Seller, Shipment, ShipmentItem, Site, SocialPersona, SocialPost, Solution, StreamingChannel,
TableauHostMapping, Topic, UnitOfMeasure, UnitOfMeasureClass, UsageGrantRenewalPolicy,
UsageGrantRolloverPolicy, UsageResource, UsageResourceBillingPolicy, User,
1656
ApprovalSubmissionAdvanced Approvals

===== PAGE 1671 =====

DetailsField
UserEsignVendorIdentifier, UserLicense, UserLocalWebServerIdentity, UserProvisioningRequest,
WorkBadge, WorkBadgeDefinition, WorkOrder, WorkOrderLineItem, WorkThanks
Type
string
RelatedRecordObjectName
Properties
Filter, Group, Nillable, Sort
Description
Required. The type of record that was submitted for approval.
Type
picklist
Status
Properties
Filter, Group, Restricted picklist, Sort
Description
Required. The status of the approval.
Valid values are:
• Approved
• Canceled
• Errored
• InProgress
• Recalled
• Rejected
• Suspended
Type
reference
SubmittedById
Properties
Filter, Group, Nillable, Sort
Description
Required. The ID of the user who submitted the record for approval.
This field is a relationship field.
Relationship Name
SubmittedBy
Refers To
User
1657
ApprovalSubmissionAdvanced Approvals

===== PAGE 1672 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ApprovalSubmissionOwnerSharingRule on page 2736
Sharing rules are available for the object.
ApprovalSubmissionShare on page 2738
Sharing is available for the object.
Advanced Approvals Fields on Approval Work Item
Standard and custom fields extend the standard Approval Work Item object for use in Advanced Approvals.
Supported Calls
describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(), update()
Special Access Rules
This object is available in Enterprise, Performance, Unlimited, and Developer Editions for users with access to the Approval Submission
object.
Fields
DetailsField
Type
string
ApprovalChainName
Properties
Filter, Group, Nillable, Sort, Update
Description
The name of the related approval chain. This field is populated when there are multiple
approval chains that are run in parallel. This field is only available with Advanced Approvals
enabled.
Type
picklist
CurrencyIsoCode
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only for organizations with the multicurrency feature enabled. Contains the ISO
code for any currency allowed by the organization.
Valid values are:
• AED—UAE Dirham
• AUD—Australian Dollar
1658
Advanced Approvals Fields on Approval Work ItemAdvanced Approvals

===== PAGE 1673 =====

DetailsField
• BRL—Brazilian Real
• CAD—Canadian Dollar
• EUR—Euro
• GBP—British Pound
• INR—Indian Rupee
• JPY—Japanese Yen
• SEK—Swedish Krona
• USD—U.S. Dollar
The default value is USD.
Type
boolean
IsAutoReviewed
Properties
Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the approval work item is eligible for smart approval (true) or not (false).
The default value is false.
Type
boolean
IsEligibleForSmartApproval
Properties
Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the approval work item is eligible for smart approval (true) or not
(false).
The default value is false.
Type
reference
SmartApprovalBasisWorkItemId
Properties
Filter, Group, Nillable, Sort, Update
Description
The previous approval work item used as a reference for the auto-approval evaluation.
This field is a relationship field.
Relationship Name
SmartApprovalBasisWorkItem
Refers To
ApprovalWorkItem
1659
Advanced Approvals Fields on Approval Work ItemAdvanced Approvals

===== PAGE 1674 =====

Advanced Approvals Standard Invocable Actions
Learn more about the standard invocable actions available with Advanced Approvals.
Cancel Approval Submission Action
Cancels an approval submission and all child approval work items that haven't been completed. You can also add comments about
why the approval admin made the cancellation.
Get Previous Related Record Details Action
Get the related record details submitted for approval before the current approval submission. The details are required for approval
steps that use custom logic for auto-approvals.
Override Approval Work Item Action
Update an approval work item status with the approval admin decision and any comments that the approval admin added.
Reassign Approval Work Item Action
Reassign an approval work item that hasn't been completed. You can also add comments about why the approval admin reassigned
the approval work item.
Recall Approval Submission Action
Recall an approval submission that isn't completed. You can also add comments that the submitter or approval admin made the
recall.
Review Approval Work Item Action
Update an approval work item status with the assignee or reviewer's decision and any comments that the assignee or reviewer
added.
SEE ALSO:
Actions Developer Guide: Overview
REST API Developer Guide: Invocable Actions Standard
Cancel Approval Submission Action
Cancels an approval submission and all child approval work items that haven't been completed. You can also add comments about why
the approval admin made the cancellation.
This action also validates if a user has required permissions to cancel an approval submission. Keep these considerations in mind when
you use this invocable action.
• The user must have the Approval Admin user permission.
• The status of the approval submission must be in In progress  or Suspended status.
This action is available in API version 62.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/cancelApprovalSubmission
Formats
JSON, XML
1660
Advanced Approvals Standard Invocable ActionsAdvanced Approvals

===== PAGE 1675 =====

HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
string
approvalSubmissionId
Description
Required.
ID of the Approval Submission to be canceled.
Type
string
comments
Description
Comments entered by the approval admin about why they canceled the Approval Submission.
Outputs
None.
Example
POST
Here's a sample request for the Cancel Approval Submission action.
{
"inputs": [
{
"approvalSubmissionId": "9iPxx00000001lhEBA",
"comments": "Cancellation comments."
}
]
}
Here's a sample response for the Cancel Approval Submission action.
{
"actionName": "cancelApprovalSubmission",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
1661
Cancel Approval Submission ActionAdvanced Approvals

===== PAGE 1676 =====

"outputValues": null,
"sortOrder": -1,
"version": 1
}
Get Previous Related Record Details Action
Get the related record details submitted for approval before the current approval submission. The details are required for approval steps
that use custom logic for auto-approvals.
This Apex action is available in API version 66.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getPreviousRelaRecDetails
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
flowOrchestrationInstanceId
Description
Required.
The ID of the flow orchestration instance associated with the approval submission.
Type
string
stepApiNamesList
Description
Required.
The comma-delimited list of step API names to retrieve previous related record details for.
1662
Get Previous Related Record Details ActionAdvanced Approvals

===== PAGE 1677 =====

Outputs
DetailsOutput
Type
sObject
previousRelatedRecordDetails
Description
The collection of previous related record details for approval steps that use custom logic for
auto-approvals.
Usage
To use this Apex action in approval workflows, see Define Rules and Conditions for Auto-Approval Resubmissions.
Example
POST
Here's a sample request for the Get Previous Related Record Details action.
{
"flowOrchestrationInstanceId": "0jEDU0000001zeN",
"stepApiNameList": [
"ManagerApprovalStep",
"FinancialApprovalStep"
]
}
Override Approval Work Item Action
Update an approval work item status with the approval admin decision and any comments that the approval admin added.
This action also validates if a user has required permissions to override an approval work item and update its status. Keep these
considerations in mind when you use this invocable action.
• The user must have the Approval Admin user permission.
• This action enables approval admins to interject the approval decision for any assignee.
• The status of the approval work item must be in Assigned  status.
This action is available in API version 62.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/overrideApprovalWorkItem
Formats
JSON, XML
HTTP Methods
POST
1663
Override Approval Work Item ActionAdvanced Approvals

===== PAGE 1678 =====

Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
string
approvalDecision
Description
Required.
Action that the overriding approval admin made for the unreviewed approval work item. Valid
values are:
• approve
• reject
Type
string
approvalWorkItemId
Description
Required.
ID of the unreviewed approval work item to be reviewed by an approval admin.
Type
picklist
channelType
Description
Type of channel where the request to review the approval work item originated. Valid values
are:
• InvocableAction
• Slack
• ApprovalRecord
The default value is InvocableAction. Available in API version 65.0 and later.
Type
string
comments
Description
Comments entered by the approval admin about their decision to approve or reject an unreviewed
approval work item.
1664
Override Approval Work Item ActionAdvanced Approvals

===== PAGE 1679 =====

Outputs
None.
Example
POST
Here's a sample request for the Override Approval Work Item action.
{
"inputs": [
{
"approvalWorkItemId": "9jRxx00000001lhEAA",
"approvalDecision": "Reject",
"channelType": "InvocableAction",
"comments": "Needs to be reviewed."
}
]
}
Here's a sample response for the Override Approval Work Item action.
{
"actionName": "overrideApprovalWorkItem",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": null,
"sortOrder": -1,
"version": 1
}
Reassign Approval Work Item Action
Reassign an approval work item that hasn't been completed. You can also add comments about why the approval admin reassigned
the approval work item.
This action also validates if a user has required permissions to reassign an approval work item and update the assignee. Keep these
considerations in mind when you use this invocable action.
• The user must have the Approval Admin user permission.
• The status of the approval work item must be in Assigned  status.
This action is available in API version 62.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/reassignApprovalWorkItem
Formats
JSON, XML
1665
Reassign Approval Work Item ActionAdvanced Approvals

===== PAGE 1680 =====

HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
string
approvalWorkItemId
Description
Required.
ID of the approval work item to be reassigned.
Type
string
assigneeId
Description
Required.
ID of the user, group, or queue to reassign the approval work item to.
Type
string
comments
Description
Comments entered by the approval admin about why they reassigned the approval work item.
Outputs
None.
Example
POST
Here's a sample request for the Reassign Approval Work Item action.
{
"inputs": [
{
"approvalWorkItemId": "9jRDU00000015C22AI",
"assigneeId": "005DU000000I3zHYAS",
"comments": "Needs to be reviewed."
}
1666
Reassign Approval Work Item ActionAdvanced Approvals

===== PAGE 1681 =====

]
}
Here's a sample response for the Reassign Approval Work Item action.
{
"actionName": "reassignApprovalWorkItem",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": null,
"sortOrder": -1,
"version": 1
}
Recall Approval Submission Action
Recall an approval submission that isn't completed. You can also add comments that the submitter or approval admin made the recall.
This action also validates if a user has required permissions to recall an approval submission. Keep these considerations in mind when
you use this invocable action.
• The user must have the Approval Admin user permission.
• The user must also be a submitter of this approval submission.
• The status of the approval submission must be in In progress  or Suspended status.
This action is available in API version 62.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/recallApprovalSubmission
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
approvalSubmissionId
Description
Required.
1667
Recall Approval Submission ActionAdvanced Approvals

===== PAGE 1682 =====

DetailsInput
ID of the approval submission to be recalled.
Type
string
comments
Description
Comments entered by the approval admin or approval submitter about why they recalled the
approval submission.
Outputs
None.
Example
POST
Here's a sample request for the Recall Approval Submission action.
{
"inputs": [
{
"approvalSubmissionId": "9iPxx00000001lhEBA",
"comments": "Recall comments."
}
]
}
Here's a sample response for the Recall Approval Submission action.
{
"actionName": "recallApprovalSubmission",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": null,
"sortOrder": -1,
"version": 1
}
Review Approval Work Item Action
Update an approval work item status with the assignee or reviewer's decision and any comments that the assignee or reviewer added.
Keep these considerations in mind when you use this invocable action.
• The user must be an assignee of the approval work item or be a member of a group or queue if the approval work item is assigned
to the group or queue. Additionally, a user has access to Approval Submissions if they're a delegate of the assignee or has a role
higher than the assignee.
1668
Review Approval Work Item ActionAdvanced Approvals

===== PAGE 1683 =====

• The status of the approval work item must be in Assigned  status.
• The user can also use this action if inherited access to group or queue membership, nested group membership, roles hierarchy, or
delegates is available. See Public Group Considerations.
This action is available in API version 62.0 and later.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/reviewApprovalWorkItem
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
approvalDecision
Description
Required.
Action that the assigned approver made for the approval work item. Valid values are:
• approve
• reject
Type
string
approvalWorkItemId
Description
Required.
ID of the approval work item to be reviewed by the assigned approver.
Type
picklist
channelType
Description
Type of channel where the request to review the approval work item originated. Valid values
are:
• InvocableAction
• Slack
1669
Review Approval Work Item ActionAdvanced Approvals

===== PAGE 1684 =====

DetailsInput
• ApprovalRecord
The default value is InvocableAction. Available in API version 65.0 and later.
Type
string
comments
Description
Approval comments for the decision.
Outputs
None.
Example
POST
Here's a sample request for the Review Approval Work Item action.
{
"inputs": [
{
"approvalWorkItemId": "9jRxx00000001lhEAA",
"approvalDecision": "Approve",
"channelType": "InvocableAction",
"comments": "Looks good."
}
]
}
Here's a sample response for the Review Approval Work Item action.
{
"actionName": "reviewApprovalWorkItem",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": null,
"sortOrder": -1,
"version": 1
}
Advanced Approvals Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
1670
Advanced Approvals Metadata API TypesAdvanced Approvals

===== PAGE 1685 =====

Flow for Advanced Approvals
The flow for Advanced Approvals represents the metadata associated with a flow. With Flow, you can create an application that
takes users through a series of pages to query and update the records in the database. You can also run logic and provide branching
capability based on user input to build dynamic applications.
SEE ALSO:
Metadata API Developer Guide: Understanding Metadata API
Flow for Advanced Approvals
The flow for Advanced Approvals represents the metadata associated with a flow. With Flow, you can create an application that takes
users through a series of pages to query and update the records in the database. You can also run logic and provide branching capability
based on user input to build dynamic applications.
FlowActionCall
Advanced Approvals exposes additional actionType values for the FlowActionCall metadata type.
DescriptionField TypeField Name
Required.InvocableActionType
(enumeration of
type string)
actionType
The action type. Additional valid values for Advanced Approvals are:
• cancelApprovalSubmission— Cancels an approval
submission and all child approval work items that haven't been
completed. You can also add comments about why the approval
admin made the cancellation. Added in API version 62.0 and later.
• overrideApprovalWorkItem— Update an approval work
item status with the approval admin decision and any comments
that the approval admin added. Added in API version 62.0 and later.
• reassignApprovalWorkItem— Reassign an approval work
item that hasn't been completed. You can also add comments about
why the approval admin reassigned the approval work item. Added
in API version 62.0 and later.
• recallApprovalSubmission— Recall an approval
submission that isn't completed. You can also add comments that
the submitter or approval admin made the recall. Added in API
version 62.0 and later.
• reviewApprovalWorkItem— Update an approval work item
status with the assignee or reviewer's decision and any comments
that the assignee or reviewer added. Added in API version 62.0 and
later.
• getPreviousRelaRecDetails— Get the related record
details submitted for approval before the current approval
submission. The details are required for approval steps that use
custom logic for auto-approvals. Added in API version 66.0 and later.
1671
Flow for Advanced ApprovalsAdvanced Approvals

===== PAGE 1686 =====

/
1672
Flow for Advanced ApprovalsAdvanced Approvals

===== PAGE 1687 =====

