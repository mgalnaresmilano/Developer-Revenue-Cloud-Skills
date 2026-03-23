---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 13 — Revenue Cloud Associated Objects

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 13 Revenue Cloud Associated Objects
This section provides a list of objects associated to standard objects of Revenue Cloud with their standard
fields.
In this chapter ...
• StandardObjectNameChangeEventSome fields may not be listed for some objects. To see the system fields for each object, see System
Fields in the Object Reference for Salesforce and Lightning Platform.• StandardObjectNameFeed
• StandardObjectNameHistoryTo verify the complete list of fields for an object, use a describe call from the API or inspect with an
appropriate tool. For example, inspect the WSDL or use a schema viewer.• StandardObjectNameOwnerSharingRule
• StandardObjectNameShare
• Event
• Task
2724

===== PAGE 2739 =====

StandardObjectNameChangeEvent
A ChangeEvent object is available for each object that supports Change Data Capture. You can subscribe to a stream of change events
using Change Data Capture to receive data tied to record changes in Salesforce. Changes include record creation, updates to an existing
record, deletion of a record, and undeletion of a record. A change event isn’t a Salesforce object—it doesn’t support CRUD operations
or queries. It’s included in the object reference so you can discover which Salesforce objects support change events.
Supported Calls
describeSObjects()
Special Access Rules
• All objects may not be available in your org. Some objects require specific feature settings and permissions to be enabled.
• For more special access rules, if any, see the documentation for the standard object. For example, for AccountChangeEvent, see the
special access rules for Account.
Change Event Support
Change events are available for all custom objects and a subset of standard objects. Change events that correspond to custom settings
are partially supported. They aren't supported in Apex triggers but are supported in other types of subscribers. For more information
about standard object support, see the Objects That Support Change Events section below.
Change Event Name
The name of a change event is based on the name of the corresponding object for which it captures the changes.
Standard Object Change Event Name
<Standard_Object_Name>ChangeEvent
Example: AccountChangeEvent
Custom Object Change Event Name
<Custom_Object_Name>__ChangeEvent
Example: MyCustomObject__ChangeEvent
Change Event Fields
The fields that a change event can include correspond to the fields on the associated parent Salesforce object, with a few exceptions.
For example, AccountChangeEvent fields correspond to the fields on Account.
The fields that a change event doesn’t include are:
• The IsDeleted  system field.
• The SystemModStamp  system field.
• Any field whose value isn’t on the record and is derived from another record or from a formula, except roll-up summary fields, which
are included. Examples are formula fields. Examples of fields with derived values include LastActivityDate  and PhotoUrl.
2725
StandardObjectNameChangeEventRevenue Cloud Associated Objects

===== PAGE 2740 =====

Each change event also contains header fields. The header fields are included inside the ChangeEventHeader  field. They contain
information about the event, such as whether the change was an update or delete and the name of the object, like Account.
In addition to the event payload, the event schema ID is included in the schema  field. Also included is the event-specific field,
replayId, which is used for retrieving past events.
Event Message Example
This example is an event message in JSON format for a new account record creation.
{
"schema": "IeRuaY6cbI_HsV8Rv1Mc5g",
"payload": {
"ChangeEventHeader": {
"entityName": "Account",
"recordIds": [
"<record_ID>"
],
"changeType": "CREATE",
"changeOrigin": "com/salesforce/api/soap/51.0;client=SfdcInternalAPI/",
"transactionKey": "0002343d-9d90-e395-ed20-cf416ba652ad",
"sequenceNumber": 1,
"commitTimestamp": 1612912679000,
"commitNumber": 10716283339728,
"commitUser": "<User_ID>"
},
"Name": "Acme",
"Description": "Everyone is talking about the cloud. But what does it mean?",
"OwnerId": "<Owner_ID>",
"CreatedDate": "2021-02-09T23:17:59Z",
"CreatedById": "<User_ID>",
"LastModifiedDate": "2021-02-09T23:17:59Z",
"LastModifiedById": "<User_ID>"
},
"event": {
"replayId": 6
}
}
API Version and Schema
When you subscribe to change events, the subscription uses the latest API version and the event messages received reflect the latest
field definitions. For more information, see API Version and Event Schema in the Change Data Capture Developer Guide.
Usage
For more information about Change Data Capture, see Change Data Capture Developer Guide.
2726
StandardObjectNameChangeEventRevenue Cloud Associated Objects

===== PAGE 2741 =====

StandardObjectNameFeed
StandardObjectNameFeed is the model for all feed objects associated with standard objects. These objects represent the posts
and feed-tracked changes of a standard object.
The object name is variable and uses StandardObjectNameFeed syntax. For example, AccountFeed represents the posts and
feed-tracked changes on an account record. We list the available associated feed objects at the end of this topic. For specific version
information, see the documentation for the standard object.
Supported Calls
delete(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
Special Access Rules
In the internal org, users can delete all feed items they created. This rule varies in Experience Cloud sites where threaded discussions
and delete-blocking are enabled. Site members can delete all feed items they created, provided the feed items don’t have content nested
under them—like a comment, answer, or reply. Where the feed item has nested content, only feed moderators and users with the
Modify All Data permission can delete threads.
To delete feed items they didn’t create, users must have one of these permissions:
• Modify All Data
• Modify All Records on the parent object, like Account for AccountFeed
• Moderate Chatter
Note:  Users with the Moderate Chatter permission can delete only the feed items and comments they can see.
Only users with this permission can delete items in unlisted groups.
For more special access rules, if any, see the documentation for the standard object. For example, for AccountFeed, see the special access
rules for Account.
Fields
DetailsField
Type
reference
BestCommentId
Properties
Filter, Group, Nillable, Sort
Description
The ID of the comment marked as best answer on a question post. This field is available in
API version 44.0 and later.
Type
textarea
Body
2727
StandardObjectNameFeedRevenue Cloud Associated Objects

===== PAGE 2742 =====

DetailsField
Properties
Nillable, Sort
Description
The body of the post. Required when Type  is TextPost. Optional when Type  is
ContentPost  or LinkPost.
Type
int
CommentCount
Properties
Filter, Group, Sort
Description
The number of comments associated with this feed item.
In a feed that supports pre-moderation, CommentCount  isn’t updated until a comment is
published. For example, say that you comment on a post that already has one published comment
and your comment triggers moderation. Now there are two comments on the post, but the
count says there's only one. In a moderated feed, comments aren’t counted until approved by
an admin or someone with Can Approve Feed Post and Comment or Modify All Data.
Feed moderation has implications on how you retrieve feed comments. In a moderated feed,
rather than retrieving comments by looping through CommentCount, go through pagination
until the end of comments is returned.
Type
reference
ConnectionId
Properties
Filter, Group, Nillable, Sort
Description
When a PartnerNetworkConnection modifies a record that is tracked, the CreatedBy
field contains the ID of the system administrator. The ConnectionId  contains the ID of
the PartnerNetworkConnection. Available if Salesforce to Salesforce is enabled for your
organization.
Type
base64
ContentData
Properties
Nillable
Description
Available in API version 36.0 and earlier only. Required if Type  is ContentPost. Encoded
file data in any format, and can’t be 0 bytes. Setting this field automatically sets Type  to
ContentPost.
Type
textarea
ContentDescription
2728
StandardObjectNameFeedRevenue Cloud Associated Objects

===== PAGE 2743 =====

DetailsField
Properties
Nillable, Sort
Description
Available in API version 36.0 and earlier only. The description of the file specified in
ContentData.
Type
string
ContentFileName
Properties
Group, Nillable, Sort
Description
Available in API version 36.0 and earlier only. This field is required if Type  is
ContentPost.The name of the file uploaded to the feed. Setting ContentFileName
automatically sets Type  to ContentPost.
Type
int
ContentSize
Properties
Group, Nillable, Sort
Description
Available in API version 36.0 and earlier only. The size of the file (in bytes) uploaded to the
feed. This field is read-only and is automatically determined during insert.
Type
string
ContentType
Properties
Group, Nillable, Sort
Description
Available in API version 36.0 and earlier only. The MIME type of the file uploaded to the feed.
This field is read-only and is automatically determined during insert.
Type
reference
FeedPostId
Properties
Filter, Group, Nillable, Sort
Description
This field was removed in API version 22.0, and is available in earlier versions for backward
compatibility only.
ID of the associated FeedPost. A FeedPost represents the following types of changes in a
feed item: changes to tracked fields, text posts, link posts, and content posts.
2729
StandardObjectNameFeedRevenue Cloud Associated Objects

===== PAGE 2744 =====

DetailsField
Type
reference
InsertedById
Properties
Group, Nillable, Sort
Description
ID of the user who added this item to the feed. For example, if an application migrates posts
and comments from another application into a feed, the InsertedBy  value is set to the
ID of the context user.
Type
boolean
isRichText
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the feed item Body contains rich text. If you post a rich text feed comment
using SOAP API, set IsRichText  to true  and escape HTML entities from the body.
Otherwise, the post is rendered as plain text.
Rich text supports the following HTML tags:
• <p>Though the <br>  tag isn’t supported, you can use <p>&nbsp;</p>  to create
lines.
• <a>
• <b>
• <code>
• <i>
• <u>
• <s>
• <ul>
• <ol>
• <li>
• <img>
The <img>  tag is accessible only through the API and must reference files in Salesforce
similar to this example: <img src="sfdc://069B0000000omjh"></img>
In API version 35.0 and later, the system replaces special characters in rich text with escaped
HTML. In API version 34.0 and prior, all rich text appears as a plain-text representation.
Type
int
LikeCount
Properties
Filter, Group, Sort
2730
StandardObjectNameFeedRevenue Cloud Associated Objects

===== PAGE 2745 =====

DetailsField
Description
The number of likes associated with this feed item.
Type
url
LinkUrl
Properties
Nillable, Sort
Description
The URL of a LinkPost.
Type
picklist
NetworkScope
Properties
Group, Nillable, Restricted picklist, Sort
Description
Specifies whether this feed item is available in the default Experience Cloud site, a specific
Experience Cloud site, or all sites. This field is available in API version 26.0 and later, if digital
experiences is enabled for your org.
NetworkScope  can have the following values:
• NetworkId—The ID of the Experience Cloud site in which the FeedItem is available.
If left empty, the feed item is only available in the default Experience Cloud site.
• AllNetworks—The feed item is available in all Experience Cloud sites.
Note the following exceptions for NetworkScope:
• Only feed items with a Group or User parent can set a NetworkId  or a null value for
NetworkScope.
• For feed items with a record parent, users can set NetworkScope  only to
AllNetworks.
• You can’t filter a feed item on the NetworkScope  field.
Type
reference
ParentId
Properties
Filter, Group, Sort
Description
ID of the record that is tracked in the feed. The detail page for the record displays the feed.
Type
reference
RelatedRecordId
Properties
Group, Nillable, Sort
2731
StandardObjectNameFeedRevenue Cloud Associated Objects

===== PAGE 2746 =====

DetailsField
Description
ID of the ContentVersion record associated with a ContentPost. This field is null for all
posts except ContentPost.
Type
string
Title
Properties
Group, Nillable, Sort
Description
The title of the feed item. When the Type  is LinkPost, the LinkUrl  is the URL and
this field is the link name.
Type
picklist
Type
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
The type of feed item:
• ActivityEvent—indirectly generated event when a user or the API adds a Task
associated with a feed-enabled parent record (excluding email tasks on cases). Also
occurs when a user or the API adds or updates a Task or Event associated with a case
record (excluding email and call logging).
For a recurring Task with CaseFeed disabled, one event is generated for the series only.
For a recurring Task with CaseFeed enabled, events are generated for the series and each
occurrence.
• AdvancedTextPost—created when a user posts a group announcement and, in
Lightning Experience as of API version 39.0 and later, when a user shares a post.
• AnnouncementPost—Not used.
• ApprovalPost—generated when a user submits an approval.
• BasicTemplateFeedItem—Not used.
• CanvasPost—a post made by a canvas app posted on a feed.
• CollaborationGroupCreated—generated when a user creates a public group.
• CollaborationGroupUnarchived—Not used.
• ContentPost—a post with an attached file.
• CreatedRecordEvent—generated when a user creates a record from the publisher.
• DashboardComponentAlert—generated when a dashboard metric or gauge
exceeds a user-defined threshold.
• DashboardComponentSnapshot—created when a user posts a dashboard
snapshot on a feed.
• LinkPost—a post with an attached URL.
• PollPost—a poll posted on a feed.
2732
StandardObjectNameFeedRevenue Cloud Associated Objects

===== PAGE 2747 =====

DetailsField
• ProfileSkillPost—generated when a skill is added to a user’s Chatter profile.
• QuestionPost—generated when a user posts a question.
• ReplyPost—generated when Chatter Answers posts a reply.
• RypplePost—generated when a user creates a Thanks badge in WDC.
• TextPost—a direct text entry on a feed.
• TrackedChange—a change or group of changes to a tracked field.
• UserStatus—automatically generated when a user adds a post. Deprecated.
The following values appear in the Type  picklist for all feed objects but apply only to
CaseFeed:
• CaseCommentPost—generated event when a user adds a case comment for a case
object
• EmailMessageEvent—generated event when an email related to a case object is
sent or received
• CallLogPost—generated event when a user logs a call for a case through the user
interface. CTI calls also generate this event.
• ChangeStatusPost—generated event when a user changes the status of a case
• AttachArticleEvent—generated event when a user attaches an article to a case
If you set Type  to ContentPost, also specify ContentData  and
ContentFileName.
Type
picklist
Visibility
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Specifies whether this feed item is available to all users or internal users only. This field is
available in API version 26.0 and later, if digitial experiences is enabled for your organization.
Visibility can have the following values:
• AllUsers—The feed item is available to all users who have permission to see the
feed item.
• InternalUsers—The feed item is available to internal users only.
Note the following exceptions for Visibility:
• For record posts, Visibility  is set to InternalUsers  for all internal users by
default.
• External users can set Visibility  only to AllUsers.
• On user and group posts, only internal users can set Visibility  to
InternalUsers.
2733
StandardObjectNameFeedRevenue Cloud Associated Objects

===== PAGE 2748 =====

Usage
A feed for an object is automatically created when a user enables feed tracking for the object. Use feeds to track changes to records. For
example, AccountFeed  tracks changes to an account record. Use feed objects to retrieve the content of feed fields, such as type of
feed or feed ID.
• NewsFeed  and UserProfileFeed  are available in API version 18.0 through API version 26.0. In API version 27.0 and later,
NewsFeed  and UserProfileFeed are no longer available in SOAP API. Use Connect REST API to access NewsFeed  and
UserProfileFeed.
Use the NewsFeed  object to query and retrieve lead feed items associated with a converted lead record.
• For NewsFeed  and UserProfileFeed, users who don’t have the View All Data permission have the following limitations
when querying records: Must specify a LIMIT  clause and the limit must be less than or equal to 1000. Can include a WHERE  clause
that references object fields, but can‘t include references to fields in related objects. For example, you can filter by CreatedDate
or ParentId, but not by Parent.Name. Can include an ORDER BY  clause that references object fields, but can’t include
references to fields in related objects. For example, ORDER BY CreatedDate  or ParentId, but not by Parent.Name.
To query for the most recent feed items, ORDER BY CreatedDate DESC, Id DESC.
Note the following SOQL restrictions. No SOQL limit if logged-in user has View All Data permission. If not, specify a LIMIT  clause
of 1,000 records or fewer. SOQL ORDER BY  on fields using relationships isn’t available. Use ORDER BY  on fields on the root
object in the SOQL query.
• The name Article Type__Feed is variable, where Article Type is the object name for the article type associated with the article.
For example, Offer__Feed represents a feed on an article of type Offer.
• Field Service must be enabled in your organization for ServiceAppointmentFeed, ServiceCrewFeed,
ServiceMemberFeed, ServiceResourceCapacityFeed, ServiceResourceFeed,
ServiceResourceSkillFeed, ServiceTerritoryFeed, ServiceTerritoryMemberFeed, and
SkillRequirementFeed.
• For WorkOrderFeed, Work Orders or Field Service must be enabled in your organization.
• On UserFeed, if you use the FeedComment object to comment on a user record, the user can delete the comment. For example,
if John Smith adds a comment to the feed on Sasha Jones’ user record, Sasha can delete the comment.
StandardObjectNameHistory
StandardObjectNameHistory is the model for all history objects associated with standard objects. These objects represent the
history of changes to the values in the fields of a standard object.
The object name is variable and uses StandardObjectNameHistory syntax. For example, AccountHistory represents the history of
changes to the values of an account record’s fields. We list the available associated history objects at the end of this topic. For specific
version information, see the documentation for the standard object.
Supported Calls
describeSObjects(), getDeleted(), getUpdated(), query(), retrieve()
You can also enable delete()  in API version 42.0 and later. See Enable delete of Field History and Field History Archive.
2734
StandardObjectNameHistoryRevenue Cloud Associated Objects

===== PAGE 2749 =====

Special Access Rules
For specific special access rules, if any, see the documentation for the standard object. For example, for AccountHistory, see the special
access rules for Account.
Fields
DetailsField Name
Type
reference
StandardObjectNameId
Properties
Filter, Group, Sort
Description
ID of the standard object.
Type
picklist
DataType
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Data type of the field that was changed.
Type
picklist
Field
Properties
Filter, Group, Restricted picklist, Sort
Description
Name of the field that was changed.
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
Old value of the field that was changed.
2735
StandardObjectNameHistoryRevenue Cloud Associated Objects

===== PAGE 2750 =====

StandardObjectNameOwnerSharingRule
StandardObjectNameOwnerSharingRule is the model for all owner sharing rule objects associated with standard objects. These
objects represent a rule for sharing a standard object with users other than the owner.
The object name is variable and uses StandardObjectNameOwnerSharingRule syntax. For example,
ChannelProgramOwnerSharingRule is a rule for sharing a channel program with users other than the channel program owner. The
available associated owner sharing rule objects are listed at the end of this topic. For specific version information, see the standard object
documentation.
Note:  To enable access to this object, contact Salesforce customer support. But we recommend that you use Metadata API to
programmatically update owner sharing rules instead because it triggers automatic sharing rule recalculation. The SharingRules
Metadata API type is enabled for all orgs.
Supported Calls
create(), delete(), describeSObjects(), getDeleted(), getUpdated(), query(), retrieve(), update(),
upsert()
Special Access Rules
For specific special access rules, if any, see the documentation for the standard object. For example, for ChannelProgramOwnerSharingRule,
see the special access rules for ChannelProgram.
Fields
DetailsField Name
Type
picklist
AccessLevel
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Determines the level of access users have to records. Values are:
• Read  (read only)
• Edit  (read/write)
Type
textarea
Description
Properties
Create, Filter, Nillable, Sort, Update
Description
Description of the sharing rule. Maximum length is 1,000 characters.
2736
StandardObjectNameOwnerSharingRuleRevenue Cloud Associated Objects

===== PAGE 2751 =====

DetailsField Name
Type
string
DeveloperName
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The unique name of the object in the API. This name can contain only underscores
and alphanumeric characters and must be unique in your org. It must begin with
a letter, not include spaces, not end with an underscore, and not contain two
consecutive underscores. In managed packages, this field prevents naming
conflicts on package installations. With this field, a developer can change the
object’s name in a managed package, and the changes are reflected in a
subscriber’s organization.
When creating large sets of data, always specify a unique DeveloperName
for each record. If no DeveloperName  is specified, performance can slow
while Salesforce generates one for each record.
Type
reference
GroupId
Properties
Create, Filter, Group, Sort
Description
ID of the source group. Records that are owned by users in the source group
trigger the rule to give access.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
Label of the sharing rule as it appears in the UI. Maximum length is 80 characters.
Type
reference
UserOrGroupId
Properties
Create, Filter, Group, Sort
Description
ID of the user or group that you're granting access to.
2737
StandardObjectNameOwnerSharingRuleRevenue Cloud Associated Objects

===== PAGE 2752 =====

StandardObjectNameShare
StandardObjectNameShare is the model for all share objects associated with standard objects. These objects represent a sharing
entry on the standard object.
The object name is variable and uses StandardObjectNameShare syntax. For example, AccountBrandShare is a sharing entry on
an account brand. For specific version information, see the standard object documentation.
You can only create, edit, and delete sharing entries for standard objects whose RowCause  field is set to Manual. Sharing entries
for standard objects with different RowCause  values are created as a result of your Salesforce org’s sharing configuration and are
read-only. For some sharing mechanisms, such as sharing sets, sharing entries aren’t stored at all.
Note:  While Salesforce currently maintains read-only sharing entries for multiple sharing mechanisms, it’s possible that we’ll stop
storing certain share records to improve performance. As a best practice, don’t create customizations that rely on the availability
of these sharing entries. Any changes to sharing behavior will be communicated before they occur.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Special Access Rules
For specific special access rules, if any, see the documentation for the standard object. For example, for AccountBrandShare, see the
special access rules for AccountBrand.
Fields
DetailsField Name
Type
picklist
AccessLevel
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The level of access allowed. Values are:
• All (owner)
• Edit (read/write)
• Read  (read only)
Type
reference
ParentId
Properties
Create, Filter, Group, Sort
Description
ID of the parent record.
2738
StandardObjectNameShareRevenue Cloud Associated Objects

===== PAGE 2753 =====

DetailsField Name
Type
picklist
RowCause
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Reason that the sharing entry exists.
Type
reference
UserOrGroupId
Properties
Create, Filter, Group, Sort
Description
ID of the user or group that has been given access to the object.
Event
Represents an event in the calendar. In the user interface, event and task records are collectively referred to as activities.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Note:
• An EventRelation object can’t be related to a child event, and child events don’t include the invitee related list.
• query(), delete(), and update() aren’t allowed with events related to more than one contact in API versions 25.0
and earlier.
• create()  and update()  aren’t available for read-only fields on Lightning Experience event series.
• upsert()  and undelete()  aren’t supported for syncing changes made to events through the API using the feature
Lightning Sync.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
DetailsField
Type
JunctionIdList
AcceptedEventInviteeIds
2739
EventRevenue Cloud Associated Objects

===== PAGE 2754 =====

DetailsField
Properties
Create, Update
Description
A string array of contact or lead IDs who accepted this event. This JunctionIdList  is
linked to the AcceptedEventRelation  child relationship.
Warning:  Adding a JunctionIdList  field name to the fieldsToNull
property deletes all related junction records. This action can’t be undone.
Type
reference
AccountId
Properties
Filter, Group, Nillable, Sort
Description
Represents the ID of the related account. The AccountId  is determined as follows.
If the value of WhatId  is any of the following objects, then Salesforce uses that object’s
AccountId.
• Account
• Opportunity
• Contract
• Custom object that’s a child of Account
If the value of the WhatId field is any other object, and the value of the WhoId  field is a
contact object, then Salesforce uses that contact’s AccountId. If your org uses Shared
Activities, Salesforce uses the AccountId  of the primary contact.
Otherwise, Salesforce sets the value of the AccountId  field to null.
This is a relationship field.
Relationship Name
Account
Relationship Type
Lookup
Refers To
Account
Type
date
ActivityDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Contains the event’s due date if the IsAllDayEvent  flag is set to true. This field is a
date field with a timestamp that’s always set to midnight in the Coordinated Universal Time
2740
EventRevenue Cloud Associated Objects

===== PAGE 2755 =====

DetailsField
(UTC) time zone. Don’t attempt to alter the timestamp to account for time zone differences.
Label is Due Date Only.
This field is required in API versions 12.0 and earlier if the IsAllDayEvent  flag is set to
true.
The value for this field and StartDateTime  must match, or one of them must be null.
Type
dateTime
ActivityDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
Contains the event’s due date if the IsAllDayEvent  flag is set to false. The time
portion of this field is always transferred in the Coordinated Universal Time (UTC) time zone.
Translate the time portion to or from a local time zone for the user or the application, as
appropriate. Label is Due Date Time.
This field is required in API versions 12.0 and earlier if the IsAllDayEvent  flag is set to
false.
The value for this field and StartDateTime  must match, or one of them must be null.
Type
string
ClientGuid
Properties
Filter, Group, Nillable, Sort
Description
The client globally unique identifier identifies the external API client used to create the event.
Label is Client GUID.
Type
picklist
CurrencyIsoCode
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Available only for orgs with the multicurrency feature enabled. Contains the ISO code for
any currency allowed by the organization.
Type
JunctionIdLIst
DeclinedEventInviteeIds
Properties
Create, Update
Description
A string array of contact, lead, or user IDs who declined this event. This JunctionIdList
is linked to the DeclinedEventRelation  child relationship.
2741
EventRevenue Cloud Associated Objects

===== PAGE 2756 =====

DetailsField
Warning:  Adding a JunctionIdList  field name to the fieldsToNull
property deletes all related junction records. This action can’t be undone.
Type
textarea
Description
Properties
Create, Nillable, Update
Description
Contains a text description of the event. Limit: 32,000 characters.
Type
picklist
Division
Properties
Defaulted on create, Filter, Group, Restricted picklist, Sort
Description
A logical segment of your organization's data. For example, if your company is organized
into different business units, you could create a division for each business unit, such as “North
America,” “Healthcare,” or “Consulting.” Available only if the organization has the Division
permission enabled.
Type
int
DurationInMinutes
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Contains the event length, in minutes. Even though this field represents a temporal value,
it’s an integer type—not a Date/Time type.
Required in API versions 12.0 and earlier if IsAllDayEvent  is false.
In API versions 13.0 and later, this field is optional, depending on the following:
• If IsAllDayEvent is true, you can supply a value for either DurationInMinutes
or EndDateTime. Supplying values in both fields is allowed if the values add up to
the same amount of time. If both fields are null, the duration defaults to one day.
• If IsAllDayEvent  is false, a value must be supplied for either
DurationInMinutes or EndDateTime. Supplying values in both fields is allowed
if the values add up to the same amount of time.
If the multiday event feature is enabled, then API versions 13.0 and later support values
greater than 1440 for the DurationInMinutes  field. API versions 12.0 and earlier can’t
access event objects whose DurationInMinutes  is greater than 1440. For more
information, see Multiday Events.
Depending on your API version, errors with the DurationInMinutes  and
EndDateTime  fields may appear in different places.
• Versions 38.0 and before—Errors always appear in the DurationInMinutes  field.
2742
EventRevenue Cloud Associated Objects

===== PAGE 2757 =====

DetailsField
• Versions 39.0 and later—If there’s no value for the DurationInMinutes field, errors
appear in the EndDateTime  field. Otherwise, they appear in the
DurationInMinutes  field.
Type
date
EndDate
Properties
Filter, Group, Nillable, Sort
Description
Read-only. Available in API versions 46.0 and later. This field supplies the date value that
appears in the EndDateTime field. This field is a date field with a timestamp that is always
set to midnight in the Coordinated Universal Time (UTC) time zone.
Type
dateTime
EndDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
Available in API versions 13.0 and later. The time portion of this field is always transferred in
the Coordinated Universal Time (UTC) time zone. Translate the time portion to or from a
local time zone for the user or the application, as appropriate.
This field is optional, depending on the following:
• If IsAllDayEvent is true, you can supply a value for either DurationInMinutes
or EndDateTime. Supplying values in both fields is allowed if the values add up to
the same amount of time. If both fields are null, the duration defaults to one day.
• If IsAllDayEvent  is false, a value must be supplied for either
DurationInMinutes or EndDateTime. Supplying values in both fields is allowed
if the values add up to the same amount of time.
Depending on your API version, errors with the DurationInMinutes  and
EndDateTime  fields may appear in different places.
• Versions 38.0 and before—Errors always appear in the DurationInMinutes  field.
• Versions 39.0 and later—If there’s no value for the DurationInMinutes field, errors
appear in the EndDateTime  field. Otherwise, they appear in the
DurationInMinutes  field.
Type
picklist
EventSubtype
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Provides standard subtypes to facilitate creating and searching for events. This field isn’t
updateable.
2743
EventRevenue Cloud Associated Objects

===== PAGE 2758 =====

DetailsField
Type
JunctionIdList
EventWhoIds
Properties
Create, Update
Description
A string array of contact or lead IDs used to create many-to-many relationships with a shared
event. EventWhoIds  is available when the shared activities setting is enabled. The first
contact or lead ID in the list becomes the primary WhoId  if you don’t specify a primary
WhoId. If you set the EventWhoIds  field to null, all entries in the list are deleted and
the value of WhoId  is added as the first entry.
Warning:  Adding a JunctionIdList  field name to the fieldsToNull
property deletes all related junction records. This action can’t be undone.
Type
picklist
GroupEventType
Properties
Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Read-only. Available in API versions 19.0 and later.
The possible values are:
• 0 (Non–group event)—An event with no invitees.
• 1  (Group event)—An event with invitees.
• 2 (Proposed event)—An event created when a user requests a meeting with a contact,
lead, or person account using the Salesforce user interface. When the user confirms the
meeting, the proposed event becomes a group event. You can’t create, edit, or delete
proposed events in the API. This value is no longer used in API version 41.0 and later.
• 3 (IsRecurrence2 Series Pattern)—An event representing an event series recurrence
pattern in Lightning Experience.
Type
boolean
IsAllDayEvent
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the ActivityDate field (true) or the ActivityDateTime  field
(false) is used to define the date or time of the event. Label is All-Day Event. See also
DurationInMinutes and EndDateTime.
Type
boolean
IsArchived
Properties
Defaulted on create, Filter, Group, Sort
2744
EventRevenue Cloud Associated Objects

===== PAGE 2759 =====

DetailsField
Description
Indicates whether the event has been archived.
Type
boolean
IsChild
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the event is a child of another event (true) or not (false).
For a child event, you can update IsReminderSet  and ReminderDateTime  only.
You can query and delete a child event. If the objects related to the child event are different
from those objects related to the parent event (this difference is possible if you use API
version 25.0 or earlier) and one of the objects related to the child event is deleted, the objects
related to the parent event are updated to ensure data integrity.
Type
boolean
IsClientManaged
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the event is managed by an external client. If the value of this field is false,
the event isn’t owned or managed by an external client, and Salesforce can be used to update
it. If the value is true, Salesforce can be used to change only noncritical fields on the event.
Label is Is Client Managed.
Type
boolean
IsGroupEvent
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the event is a group event—that is, whether it has invitees ( true) or not
(false).
Type
boolean
IsPrivate
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether users other than the creator of the event can (false) or can’t (true)
see the event details when viewing the event user’s calendar. However, users with the View
All Data or Modify All Data permission can see private events in reports and searches, or
when viewing other users’ calendars. Private events can’t be associated with opportunities,
accounts, cases, campaigns, contracts, leads, or contacts. Label is Private.
2745
EventRevenue Cloud Associated Objects

===== PAGE 2760 =====

DetailsField
Type
boolean
IsRecurrence
Properties
Create, Defaulted on create, Filter, Group, Sort
Description
Indicates whether a Salesforce Classic event is scheduled to repeat itself (true) or only
occurs one time (false). This field is read-only when updating records, but not when
creating them. If this field value is true, then RecurrenceEndDateOnly,
RecurrenceStartDateTime, RecurrenceType, and any recurrence fields
associated with the given recurrence type must be populated. Label is Create recurring
series of events.
Type
boolean
IsRecurrence2
Properties
Defaulted on create, Filter, Group, Sort
Description
Read-only. This field is available in API version 44.0 and later. Indicates whether a Lightning
Experience event is scheduled to repeat (true) or only occurs one time (false). If this
field value is true, then Recurrence2PatternText  and
Recurrence2PatternVersion  must be populated. Label is Repeat.
Type
boolean
IsRecurrence2Exception
Properties
Defaulted on create, Filter, Group, Sort
Description
Read-only. This field is available in API version 44.0 and later. Indicates whether an individual
event in a Lightning Experience event series has a recurrence pattern that’s different from
the rest of the series, making it an exception.
Type
boolean
IsRecurrence2Exclusion
Properties
Defaulted on create, Filter, Group, Sort
Description
Read-only. This field is available in API version 44.0 and later. Indicates when updates to a
Lightning Experience event series recurrence pattern have been made, but affect future
event occurrences only. For past event occurrences, IsRecurrence2Exclusion  is
set to true, excluding past occurrences from the series recurrence pattern.
Type
boolean
IsReminderSet
2746
EventRevenue Cloud Associated Objects

===== PAGE 2761 =====

DetailsField
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the activity is a reminder (true) or not (false).
Type
boolean
IsVisibleInSelfService
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether an event associated with an object can be viewed in the Customer Portal
(true) or not (false). If your org has enabled digital experiences, events marked
IsVisibleInSelfService  are visible to any external user in the Experience Cloud
site, as long as the user has access to the record the event was created on. This field is available
when
• Customer Portal or partner portal is enabled
OR
• Digital experiences is enabled and you have Customer Portal or partner portal licenses
Type
string
Location
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Contains the location of the event.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Contains the ID of the user or public calendar who owns the event. Label is Assigned to ID.
This is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Calendar, User
2747
EventRevenue Cloud Associated Objects

===== PAGE 2762 =====

DetailsField
Type
dateTime
Recurrence2PatternStartDate
Properties
Filter, Nillable, Sort
Description
Read-only. This field is available in API version 44.0 and later. Indicates the date and time
when the Lightning Experience event series begins. The time portion of this field is always
transferred in the Coordinated Universal Time (UTC) time zone. Translate the time portion
to or from a local time zone for the user or the application, as appropriate.
Type
textarea
Recurrence2PatternText
Properties
Create, Nillable
Description
The RRULE that describes the recurrence pattern for Lightning Experience event series.
Supports a subset of the RFC 5545 standard for internet calendaring and scheduling. See the
Event Series section in this topic for usage examples. This field has a maximum length of 512
characters.
This field is available in API version 44.0 and later, and has the Create  property in API
version 52.0 and later.
Type
string
Recurrence2PatternTimeZone
Properties
Filter, Group, Nillable, Sort
Description
This field is available in API version 44.0 and later. Indicates the time zone in which the
Lightning Experience event series was created or updated. This field uses standard Java
TimeZone IDs. For example, America/Los_Angeles.
Type
picklist
Recurrence2PatternVersion
Properties
Filter, Group, Nillable, Restricted picklist, Sort,
Description
Read-only. This field is available in API version 44.0 and later. Indicates the standard
specifications for Lightning Experience event series recurrence patterns. The only possible
value is 1  (RFC 5545 v4 RRULE)—RFC 5545 is a standard set of specifications for internet
calendaring and scheduling that IsRecurrence2  adheres to for series recurrence
patterns. RFC 5545 specifications for series recurrence patterns are called RRULES. For examples
of RRULE usage, see the Lightning Experience Event Series and Recurring Events section in
this topic.
2748
EventRevenue Cloud Associated Objects

===== PAGE 2763 =====

DetailsField
Type
reference
RecurrenceActivityId
Properties
Filter, Group, Nillable, Sort
Description
Read-only. Not required on create. Contains the ID of the main record of the Salesforce Classic
recurring event. Subsequent occurrences have the same value in this field.
Type
int
RecurrenceDayOfMonth
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Indicates the day of the month on which the event repeats.
Type
int
RecurrenceDayOfWeekMask
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Indicates the day or days of the week on which the Salesforce Classic recurring event repeats.
This field contains a bitmask. The values are as follows:
• Sunday = 1
• Monday = 2
• Tuesday = 4
• Wednesday = 8
• Thursday = 16
• Friday = 32
• Saturday = 64
Multiple days are represented as the sum of their numerical values. For example, Tuesday
and Thursday = 4 + 16 = 20.
Type
date
RecurrenceEndDateOnly
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Indicates the last date on which the event repeats. For multiday Salesforce Classic recurring
events, this date is the day on which the last occurrence starts. This field is a date field with
a timestamp that is always set to midnight in the Coordinated Universal Time (UTC) time
zone. Don’t attempt to alter the timestamp to account for time zone differences.
2749
EventRevenue Cloud Associated Objects

===== PAGE 2764 =====

DetailsField
Type
picklist
RecurrenceInstance
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Indicates the frequency of the Salesforce Classic event’s recurrence. For example, 2nd  or
3rd.
Type
int
RecurrenceInterval
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Indicates the interval between Salesforce Classic recurring events.
Type
picklist
RecurrenceMonthOfYear
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Indicates the month in which the Salesforce Classic recurring event repeats.
Type
dateTime
RecurrenceStartDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
Indicates the date and time when the Salesforce Classic recurring event begins. The value
must precede the RecurrenceEndDateOnly. The time portion of this field is always
transferred in the Coordinated Universal Time (UTC) time zone. Translate the time portion
to or from a local time zone for the user or the application, as appropriate.
Type
picklist
RecurrenceTimeZoneSidKey
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Indicates the time zone associated with a Salesforce Classic recurring event. For example,
“UTC-8:00” for Pacific Standard Time.
Type
picklist
RecurrenceType
2750
EventRevenue Cloud Associated Objects

===== PAGE 2765 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Indicates how often the Salesforce Classic event repeats. For example, daily, weekly, or every
nth month (where “nth” is defined in RecurrenceInstance).
Type
dateTime
ReminderDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
Represents the time when the reminder is scheduled to fire, if IsReminderSet  is set to
true. If IsReminderSet  is set to false, then the user may have deselected the
reminder checkbox in the Salesforce user interface, or the reminder has already fired at the
time indicated by the value.
Type
picklist
ShowAs
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Indicates how this event appears when another user views the calendar: Busy, Out of Office,
or Free. Label is Show Time As.
Type
dateTime
StartDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
Indicates the start date and time of the event. Available in versions 13.0 and later.
If the Event IsAllDayEvent  flag is set to true (indicating that it’s an all-day Event), then
the event start date information is contained in the StartDateTime  field. The time
portion of this field is always transferred in the Coordinated Universal Time (UTC) time zone.
Translate the time portion to or from a local time zone for the user or the application, as
appropriate.
If the Event IsAllDayEvent  flag is set to false (indicating that it isn’t an all-day event),
then the event start date information is contained in the StartDateTime  field. The time
portion is always transferred in the Coordinated Universal Time (UTC) time zone. You need
to translate the time portion to or from a local time zone for the user or the application, as
appropriate.
If this field has a value, then ActivityDate  and ActivityDateTime  must either
be null  or match the value of this field.
2751
EventRevenue Cloud Associated Objects

===== PAGE 2766 =====

DetailsField
Type
combobox
Subject
Properties
Create, Filter, Nillable, Sort, Update
Description
The subject line of the event, such as Call, Email, or Meeting. Limit: 255 characters.
Type
picklist
Type
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Indicates the event type, such as Call, Email, or Meeting.
Type
JunctionIdList
UndecidedEventInviteeIds
Properties
Create, Update
Description
A string array of contact, lead, or user IDs who are undecided about this event. This
JunctionIdList  is linked to the UndecidedEventRelation child relationship.
Warning:  Adding a JunctionIdList  field name to the fieldsToNull
property deletes all related junction records. This action can’t be undone.
Type
int
WhatCount
Properties
Filter, Group, Nillable, Sort
Description
Available if your organization has enabled Shared Activities. Represents the count of related
EventRelations pertaining to the WhatId. The count of the WhatId  must be 1  or less.
Type
reference
WhatId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The WhatId  represents nonhuman objects such as accounts, opportunities, campaigns,
cases, or custom objects. WhatIds are polymorphic. Polymorphic means a WhatId  is
equivalent to the ID of a related object. The label is Related To ID.
This is a polymorphic relationship field.
2752
EventRevenue Cloud Associated Objects

===== PAGE 2767 =====

DetailsField
Relationship Name
What
Relationship Type
Lookup
Refers To
Account, Accreditation, AssessmentIndicatorDefinition, AssessmentTask,
AssessmentTaskContentDocument, AssessmentTaskDefinition, AssessmentTaskOrder, Asset,
AssetRelationship, AssignedResource, Award, BoardCertification, BusinessLicense,
BusinessMilestone, BusinessProfile, Campaign, CareBarrier, CareBarrierDeterminant,
CareBarrierType, CareDeterminant, CareDeterminantType, CareDiagnosis,
CareInterventionType, CareMetricTarget, CareObservation, CareObservationComponent,
CarePgmProvHealthcareProvider, CarePreauth, CarePreauthItem, CareProgram,
CareProgramCampaign, CareProgramEligibilityRule, CareProgramEnrollee,
CareProgramEnrolleeProduct, CareProgramEnrollmentCard, CareProgramGoal,
CareProgramProduct, CareProgramProvider, CareProgramTeamMember,
CareProviderAdverseAction, CareProviderFacilitySpecialty, CareProviderSearchableField,
CareRegisteredDevice, CareRequest, CareRequestDrug, CareRequestExtension,
CareRequestItem, CareSpecialty, CareSpecialtyTaxonomy, CareTaxonomy, Case,
CommSubscriptionConsent, ContactEncounter, ContactEncounterParticipant, ContactRequest,
Contract, CoverageBenefit, CoverageBenefitItem, CreditMemo, DelegatedAccount,
DocumentChecklistItem, EnrollmentEligibilityCriteria, HealthcareFacility,
HealthcareFacilityNetwork, HealthcarePayerNetwork, HealthcarePractitionerFacility,
HealthcareProvider, HealthcareProviderNpi, HealthcareProviderSpecialty,
HealthcareProviderTaxonomy, IdentityDocument, Image, IndividualApplication, Invoice,
ListEmail, Location, MemberPlan, Opportunity, Order, OtherComponentTask, PartyConsent,
PersonLifeEvent, PlanBenefit, PlanBenefitItem, ProcessException, Product2, ProductItem,
ProductRequest, ProductRequestLineItem, ProductTransfer, PurchaserPlan,
ReceivedDocument, ResourceAbsence, ReturnOrder, ReturnOrderLineItem,
ServiceAppointment, ServiceResource, Shift, Shipment, ShipmentItem, Solution, Visit,
VisitedParty, VolunteerProject, WorkOrder, WorkOrderLineItem
Type
int
WhoCount
Properties
Filter, Group, Nillable, Sort
Description
Available to organizations that have Shared Activities enabled. Represents the count of
related EventRelations pertaining to the WhoId.
Type
reference
WhoId
Properties
Create, Filter, Group, Nillable, Sort, Update
2753
EventRevenue Cloud Associated Objects

===== PAGE 2768 =====

DetailsField
Description
The WhoId represents a human such as a lead or a contact. WhoIds are polymorphic.
Polymorphic means a WhoId is equivalent to a contact’s ID or a lead’s ID. The label is Name
ID.
If Shared Activities is enabled, the value of this field is the ID of the related lead or primary
contact. If you add, update, or remove the WhoId field, you might encounter problems with
triggers, workflows, and data validation rules that are associated with the record. The label
is Name ID.
If the JunctionIdList  field is used, all WhoIds are included in the relationship list.
Beginning in API version 37.0, if the contact or lead ID in the WhoId  field isn't in the
EventWhoIds  list, no error occurs and the ID is added to the EventWhoIds  as the
primary WhoId. If WhoId  is set to null, an arbitrary ID from the existing EventWhoIds
list is promoted to the primary position.
This is a polymorphic relationship field.
Relationship Name
Who
Relationship Type
Lookup
Refers To
Contact, Lead
Usage
Use Event to manage calendar appointments.
Queries on events are denied before they time out if they involve amounts of data that are deemed too large. In such cases, the exception
code OPERATION_TOO_LARGE  is returned. If you receive OPERATION_TOO_LARGE, refactor your query to return or scan a
smaller amount of data.
When querying for events with a specific due date, you must filter on both the ActivityDateTimeand  and ActivityDate
fields. For example to find all events with a due date of February 14, 2003, you need two filters:
• One filter with the ActivityDate  field equal to the Coordinated Universal Time (UTC) time zone on February 14, 2003.
• One filter with the ActivityDate  field greater than or equal to midnight on February 14, 2003 in the user’s local time zone AND
less than or equal to midnight on February 15, 2003 in the user’s local time zone.
Alternatively, in API version 13.0 and later, you can find events with a specific due date by filtering on StartDateTime. For example,
to find all events with a due date of February 14, 2003, filter with the StartDateTime  greater than or equal to midnight on February
14, 2003 in the user's local time zone AND less than or equal to midnight on February 15, 2003 in the user's local time zone.
The EventId field of an EventRelation object always points to the master record. An invitee on a group event can query the EventRelation
object to view the master record.
Multiday Events
• Multiday events are available in API version 13.0 and later. Also, in earlier versions SOQL queries don’t return multiday events.
2754
EventRevenue Cloud Associated Objects

===== PAGE 2769 =====

• Multiday events are enabled through the user interface from Setup by entering Activity Settings  in the Quick Find
box, then selecting Activity Settings.
• If the multiday event feature is enabled, then API versions 13.0 and later support values greater than 1440 for the
DurationInMinutes  field. API versions 12.0 and earlier can’t access event objects whose DurationInMinutes  is greater
than 1440.
• Multiday events can’t exceed 14 days.
Event Series and Recurring Events
In Lightning Experience, events with multiple occurrences are called event series, and are indicated when the IsRecurrence2  field
is set to true. In Salesforce Classic, events with multiple occurrences are called recurring events, and are indicated when the
IsRecurrence  field is set to true. Both fields can’t be set to true for the same event.
• Lightning Experience event series are available in API version 44.0 and later as read-only fields. Recurrence patterns, specified by the
Recurrence2PatternText field, are creatable in API version 52.0 and later. Salesforce Classic recurring events are available in API version
7.0 and later. In earlier versions, SOQL queries don’t return any Lightning Experience event series.
• After an event is created, you can’t change the values of IsRecurrence2  or IsRecurrence  from true  to false  or vice
versa.
• You can’t set fields associated with IsRecurrence2  for events where IsRecurrence  is set to true, or vice versa.
• For Lightning Experience event series where IsRecurrence2 is true, if you’d like to delete a single or all remaining events,
use the REST API call. For Salesforce Classic recurring events where IsRecurrence  is true, all past and future events in the
series are removed when you delete the recurring event series through the API. However, when you delete the recurring event series
through the user interface, only future occurrences are removed.
• For Lightning Experience event series in API version 58.0 and later, when you change a future event, events in the entire series also
change. When you change a past event, IsRecurrence2Exception is set to true and only that past event changes.
• When creating a Salesforce Classic recurring event series, the duration of the event must be 24 hours or less. When the Salesforce
Classic recurring event series is created, you can extend the length of individual occurrences beyond 24 hours if Multiday events are
enabled; see Multiday Events.
• For Salesforce Classic recurring events, RecurrenceStartDateTime, RecurrenceEndDateOnly, RecurrenceType,
and any properties associated with the given recurrence type (see the Recurrence Field Usage for Salesforce Classic Recurring Events
table) must be populated.
• When updating a Salesforce Classic recurring event series, it’s not possible to update the EventRelation  for the event series
object and the EventRelation for the series object occurrences at the same time.
• Lightning Experience event series have no series ID, so it’s not possible to locate other occurrences in the series. In Salesforce Classic
recurring events, you can use RecurrenceActivityId  to locate other occurrences.
• For both Lightning Experience event series and Salesforce Classic recurring events, when a series repeats every day, month, or year,
you can only schedule occurrences one time per day, month, or year. The week option lets you schedule occurrences multiple days
per week.
Limits for Lightning Experience event series and limits for Salesforce Classic recurring events also apply.
Lightning Experience Event Series and Recurring Events
Use the Recurrence2PatternText field to specify the recurrence pattern for Lightning Experience event series. These recurrence
patterns, called reference rules or RRULES, support a subset of the RFC 5545 standards. This table includes common RRULE examples.
RRULE ExampleRecurrence Pattern
RRULE:FREQ=DAILY;INTERVAL=1;COUNT=5Every day for five days
2755
EventRevenue Cloud Associated Objects

===== PAGE 2770 =====

RRULE ExampleRecurrence Pattern
RRULE:FREQ=WEEKLY;INTERVAL=1;BYDAY=MO,TU,WE,TH,FREvery Monday, Tuesday, Wednesday, Thursday, and Friday with no
end date
RRULE:FREQ=WEEKLY;INTERVAL=2;BYDAY=MO,FR;COUNT=10Every two weeks on Monday and Friday for 10 occurrences
RRULE:FREQ=MONTHLY;INTERVAL=1;BYMONTHDAY=1;UNTIL=20200101T100000ZMonthly on the first day of the month until January 1, 2020
RRULE:FREQ=YEARLY;INTERVAL=1;BYMONTH=7;BYMONTHDAY=4;COUNT=3Yearly on July 4th for three years (in this example, specify the date
using StartDateTime)
RRULE:FREQ=DAILY;UNTIL=20220101T000000ZDaily until January 1, 2022 with no end date
RRULE:FREQ=MONTHLY;BYSETPOS=3;BYDAY=FREvery third Friday of the month with no end date
The RRULE defined by Recurrence2PatternText supports a subset of the RFC 5545 standard for internet calendaring and
scheduling. Supported RRULE parts include FREQ, BYMONTH, BYMONTHDAY, BYDAY, WKST, BYSETPOS, INTERVAL, UNTIL, and COUNT.
When the event record is saved, the RRULE might be modified to follow the required format:
• The RRULE parts are placed in the following order: FREQ, BYMONTH, BYMONTHDAY, BYDAY, WKST, BYSETPOS, INTERVAL, UNTIL, and
COUNT.
• Any missing default values are inserted. For example, if the RRULE doesn't include INTERVAL, then INTERVAL=1  is added.
• The RRULE is prefaced with RRULE:  if that preface is missing.
Supported RFC 5545 ImplementationRRULE Part
Required. Indicates the type of recurrence rule. Allowed values are:FREQ
• DAILY—supported parts include FREQ, INTERVAL, UNTIL, and COUNT.
• WEEKLY—supported parts include INTERVAL, UNTIL, COUNT, BYDAY, and WKST. BYDAY is required, but
can't be preceded by a number.
For example, to indicate weekly on Tuesday and Thursday until September 1, 2023, use
RRULE:FREQ=WEEKLY;UNTIL=20230901T000000Z;BYDAY=TU,TH
• MONTHLY—supported patterns include:
– BYMONTHDAY
For example, to indicate monthly on the third day of the month use:
RRULE:FREQ=MONTHLY;BYMONTHDAY=3
– BYDAY and BYSETPOS
For example, to indicate the last weekday of the month, use
RRULE:FREQ=MONTHLY;BYDAY=MO,TU,WE,TH,FR;BYSETPOS=-1
– BYDAY, where the BYDAY values are specified with a numeric value
For example, to indicate monthly on the first Friday for 10 occurrences, use
RRULE:FREQ=MONTHLY;COUNT=10;BYDAY=1FR
• YEARLY—supported patterns include:
– BYMONTH, BYDAY, and BYSETPOS
2756
EventRevenue Cloud Associated Objects

===== PAGE 2771 =====

Supported RFC 5545 ImplementationRRULE Part
For example, to indicate every year on the second Friday of January, use
RRULE:FREQ=YEARLY;BYMONTH=1;BYDAY=FR;BYSETPOS=2
– BYMONTH and BYMONTHDAY
For example, to indicate every year on October 31, use
RRULE:FREQ=YEARLY;BYMONTH=10;BYMONTHDAY=31
For example, to create a maintenance pattern such as twice in May, and September on 7th and 15th;
and one time in June/July/August on the 1st, use two RRULEs: RRULE: FREQ=MONTHLY;
BYMONTH=5,9; BYMONTHDAY=7, 15 RRULE:FREQ=MONTHLY; BYMONTH=6,7,8;
BYMONTHDAY=1
The month. Valid values are 1  to 12.BYMONTH
The day of the month. Valid values are 1  to 31. If BYMONTHDAY is 31  and the month has fewer than 31
days, the event is created on the last day of the month.
BYMONTHDAY
A comma-separated list of days of the week. Valid values are SU, MO, TU, WE, TH, FR, SA. For RRULES with
yearly or monthly frequency, BYDAY must be one of:
BYDAY
• a single day
• weekend days
• weekdays
• every day of the week
Each BYDAY value can be preceded by an integer that indicates the nth occurrence of a specific day within
the monthly or yearly RRULE. Allowed values are -1, 1, 2, 3, and 4. You can't use different numbers in the
BYDAY values. For example, this RRULE isn’t supported:
RRULE:FREQ=MONTHLY;INTERVAL=2;COUNT=10;BYDAY=1SU,-1SU  If BYDAY values are
prefaced with a number, the RRULE can't include BYSETPOS.
Specifies the day on which the workweek starts. Valid values are MO, TU, WE, TH, FR, SA, and SU. Default
value is based on the user's locale.
WKST
A comma-separated list of values that correspond to the nth occurrence within the set of recurrence instances
specified by the rule. Valid values are -1, 1, 2, 3, or 4. Default value is 1.
For example, to indicate the last weekday of the month, use:
RRULE:FREQ=MONTHLY;BYDAY=MO,TU,WE,TH,FR;BYSETPOS=-1
BYSETPOS
The repetition interval. Valid values are:INTERVAL
• an integer between 1  and 999  if FREQ=DAILY
• an integer between 1  and 99  if FREQ=WEEKLY or FREQ=MONTHLY
• 1  if FREQ=YEARLY
Default value is 1.
2757
EventRevenue Cloud Associated Objects

===== PAGE 2772 =====

Supported RFC 5545 ImplementationRRULE Part
Specifies the datetime in UTC format when the recurrence rule stops. The supported format is
yyyyMMddTHHmmssZ, for example: 20210419T083000Z.
An RRULE can't contain both UNTIL and COUNT. A recurring event without either UNTIL or COUNT repeats
indefinitely.
UNTIL
The number of occurrences. Allowed values are 1 to 999.
An RRULE can't contain both UNTIL and COUNT. A recurring event without either UNTIL or COUNT repeats
indefinitely.
COUNT
Specifies a comma-separated list of values that specify weeks of the year. Valid values are:BYWEEKNO
• 1  to 53
• -53  to -1
For example, to indicate specific weeks in a year, use: RRULE: BYWEEKNO=20, -20.
This rule part can’t be used when the FREQ rule part is set to anything other than YEARLY. For example, 3
represents the third week of the year.
Note: Assuming a Monday week start, week 53 can only occur when Thursday is January 1 or if it’s a leap year
and Wednesday is January 1.
Specifies a comma-separated list of values that specify days of the year. Valid values are:BYYEARDAY
• 1  to 366
• -366  to -1
For example, to indicate specific days in a year, use: RRULE:BYYEARDAY=1,100,200; or,
RRULE:BYYEARDAY=1,-2.
Salesforce Classic Event Series and Recurring Events
This table describes the usage of recurrence fields for Salesforce Classic recurring events. Each recurrence type must have all of its
properties set. All unused properties must be set to null.
Example PatternPropertiesRecurrenceType Value
Every second dayRecurrenceIntervalRecursDaily
Every weekday - can’t be Saturday or SundayRecurrenceDayOfWeekMaskRecursEveryWeekday
Every second month, on the third day of the monthRecurrenceDayOfMonth
RecurrenceInterval
RecursMonthly
Every second month, on the last Friday of the monthRecurrenceInterval RecurrenceInstance
RecurrenceDayOfWeekMask
RecursMonthlyNth
Every three weeks on Wednesday and FridayRecurrenceInterval
RecurrenceDayOfWeekMask
RecursWeekly
Every March on the 26th day of the monthRecurrenceDayOfMonth
RecurrenceMonthOfYear
RecursYearly
2758
EventRevenue Cloud Associated Objects

===== PAGE 2773 =====

Example PatternPropertiesRecurrenceType Value
The first Saturday in every OctoberRecurrenceDayOfWeekMask
RecurrenceInstanceRecurrenceMonthOfYear
RecursYearlyNth
Attendees, Invitees, and Resources
The field GroupEventType  indicates that event participants are included on an event. You can add a resource to an event only
when the resource is available. The only attendance status that can be assigned to resources is Accepted. Events can’t be saved when
resources you’ve added aren’t available.
JunctionIdList
To create an event using JunctionIdList, IDs are pulled from the related contacts and both the event and the EventRelation
records are created in one API call. If the EventRelation fails, the event is rolled back because it’s all done in a single API call.
public void createEventNew(Contact[] contacts) {
String[] contactIds = new String[contacts.size()];
for (int i = 0; i < contacts.size(); i++) {
contactIds[i] = contacts[i].getID();
}
Event event = new Event();
event.setSubject("New Event");
event.setEventWhoIds(contactIds);
SaveResult[] results = null;
try {
results = connection.create(new Event[] {
task
});
} catch (ConnectionException ce) {
ce.printStackTrace();
}
}
Syncing Events with Lightning Sync
Attendee statuses (Accepted or Maybe, Declined, or No Response) sync from Microsoft® Exchange or Google to Salesforce, but not from
Salesforce to Exchange or Google. Be wary of creating API flows that update attendee status in Salesforce for users set up to sync both
ways. Eventually the original Exchange or Google status overrides the update made in Salesforce.
Shared Field-Level Security for Event and Task Objects
Metadata deployments for the Event object must include the field-level security for the Task object. Shared field-level security prevents
each object from changing the field-level security of the associated object.
Metadata deployments that include field-level security for only one of either the Event or Task objects can cause field-level security
changes to the other object that aren't reflected in the metadata.
• If field-level security is enabled for one object, then field-level security is enabled for both objects.
• If field-level security is disabled for one object, then it's disabled for both objects.
Note:  A missing entry in the metadata is treated as field-level security being disabled.
2759
EventRevenue Cloud Associated Objects

===== PAGE 2774 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
EventChangeEvent (API version 44.0)
Change events are available for the object.
EventFeed (API version 20.0)
Feed tracking is available for the object.
Task
Represents a business activity such as making a phone call or other to-do items. In the user interface, Task and Event records are collectively
referred to as activities.
Note:  Task fields related to calls are exclusive to Salesforce CRM Call Center. Also, query(), delete(), and update()
aren’t allowed with tasks related to more than one contact in API versions 23.0 and earlier.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Fields
Field TypeField
Type
reference
AccountId
Properties
Filter, Group, Nillable, Sort
Description
Represents the ID of the related Account. The AccountId  is determined as follows.
If the value of WhatId  is any of the following objects, then Salesforce uses that object’s
AccountId.
• Account
• Opportunity
• Contract
• Custom object that is a child of Account
If the value of the WhatIdfield is any other object, and the value of the WhoId  field is a
Contact object, then Salesforce uses that contact’s AccountId. (If your organization uses
Shared Activities, then Salesforce uses the AccountId  of the primary contact.)
Otherwise, Salesforce sets the value of the AccountId field to null.
For information on IDs, see ID Field Type.
2760
TaskRevenue Cloud Associated Objects

===== PAGE 2775 =====

Field TypeField
This is a relationship field.
Relationship Name
Account
Relationship Type
Lookup
Refers To
Account
Type
date
ActivityDate
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Represents the due date of the task. This field has a timestamp that is always set to midnight
in the Coordinated Universal Time (UTC) time zone. The timestamp is not relevant; do not
attempt to alter it to accommodate time zone differences. Label is Due Date.
This field can’t be set or updated for a recurring task (IsRecurrence  is true).
Type
string
CallDisposition
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Represents the result of a given call, for example, “we'll call back,” or “call unsuccessful.” Limit
is 255 characters.
Not subject to field-level security, available for any user in an organization with Salesforce
CRM Call Center.
Type
int
CallDurationInSeconds
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
Duration of the call in seconds.
Not subject to field-level security, available for any user in an organization with Salesforce
CRM Call Center.
Type
string
CallObject
Properties
Create, Filter, Group, Nillable, Sort, Update
2761
TaskRevenue Cloud Associated Objects

===== PAGE 2776 =====

Field TypeField
Description
Name of a call center. Limit is 255 characters.
Not subject to field-level security, available for any user in an organization with Salesforce
CRM Call Center.
Type
picklist
CallType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type of call being answered: Inbound, Internal, or Outbound.
Type
dateTime
CompletedDateTime
Properties
Filter, Nillable, Sort
Description
The date and time the task was saved with a Closed status.
• For insert, if the task is saved with a Closed status the field is set. If the task is saved with
an Open status the field is set to NULL.
• For update, if the task is saved with a new Closed status, the field is reset.
If the task is saved with a new non-closed status, the field is reset to NULL.
If the task is saved with the same closed status (that is, unchanged) there is no change
to the field.
The status is a dynamic enum. If the Closed mapping is changed it won’t cause an update
of existing tasks. Only new insert/update operations are affected.
Type
reference
ConnectionReceivedId
Properties
Filter, Group, Nillable, Sort
Description
ID of the PartnerNetworkConnection that shared this record with your organization. This
field is available if you enabled Salesforce to Salesforce.
Type
reference
ConnectionSentId
Properties
Filter, Group, Nillable, Sort
2762
TaskRevenue Cloud Associated Objects

===== PAGE 2777 =====

Field TypeField
Description
ID of the PartnerNetworkConnection that you shared this record with. This field is available
if you enabled Salesforce to Salesforce. This field is supported using API versions earlier than
15.0. In all other API versions, this field’s value is null. You can use the new
PartnerNetworkRecordConnection object to forward records to connections.
Type
textarea
Description
Properties
Create, Nillable, Update
Description
Contains a text description of the task.
Type
boolean
IsArchived
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the event has been archived. The default value of this field is false.
Type
boolean
IsClosed
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the task has been completed (true) or not (false). The default value
of this field is false. Is only set indirectly via the Status picklist. Label is Closed.
Type
boolean
IsHighPriority
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates a high-priority task. This field is derived from the Priority  field. The default
value of this field is false.
Type
boolean
IsRecurrence
Properties
Create, Defaulted on create, Filter, Group, Sort
2763
TaskRevenue Cloud Associated Objects

===== PAGE 2778 =====

Field TypeField
Description
Indicates whether the task is scheduled to repeat itself (true) or only occurs once (false).
The default value of this field is false. This field is read-only on update, but not on create.
If this field value is true, then RecurrenceStartDateOnly,
RecurrenceEndDateOnly, RecurrenceType, and any recurrence fields associated
with the given recurrence type must be populated. See Recurring Tasks.
Type
boolean
IsReminderSet
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether a popup reminder has been set for the task (true) or not (false). The
default value of this field is false.
Type
boolean
IsVisibleInSelfService
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether a task associated with an object can be viewed in the Customer Portal
(true) or not (false).
If your organization has digital experiences enabled, tasks marked
IsVisibleInSelfService are visible to any external user in the Experience Cloud
site, as long as the user has access to the record the task was created on.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
ID of the User or Group who owns the record. Label is Assigned To ID. This field accepts
Groups of type Queue only.
In the user interface, Group IDs correspond with the queue’s list view names. To create or
update tasks assigned to Group, use v48.0 or later.
This is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
2764
TaskRevenue Cloud Associated Objects

===== PAGE 2779 =====

Field TypeField
Type
picklist
Priority
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Required. Indicates the importance or urgency of a task, such as high or low. The default
value of this field is Normal.
Type
reference
RecurrenceActivityId
Properties
Filter, Group, Nillable, Sort
Description
Read-only. Not required on create. ID of the main record of the recurring task. Subsequent
occurrences have the same value in this field.
Type
int
RecurrenceDayOfMonth
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The day of the month in which the task repeats.
Type
int
RecurrenceDayOfWeekMask
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The day or days of the week on which the task repeats. This field contains a bitmask. The
values are as follows:
• Sunday = 1
• Monday = 2
• Tuesday = 4
• Wednesday = 8
• Thursday = 16
• Friday = 32
• Saturday = 64
Multiple days are represented as the sum of their numerical values. For example, Tuesday
and Thursday = 4 + 16 = 20.
2765
TaskRevenue Cloud Associated Objects

===== PAGE 2780 =====

Field TypeField
Type
date
RecurrenceEndDateOnly
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The last date on which the task repeats. This field has a timestamp that is always set to
midnight in the Coordinated Universal Time (UTC) time zone. The timestamp is not relevant;
do not attempt to alter it to accommodate time zone differences.
Type
picklist
RecurrenceInstance
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The frequency of the recurring task.
Possible values are:
• First—1st
• Fourth—4th
• Last—last
• Second—2nd
• Third—3rd
Type
int
RecurrenceInterval
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The interval between recurring tasks.
Type
picklist
RecurrenceMonthOfYear
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The month of the year in which the task repeats.
Type
picklist
RecurrenceRegeneratedType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
2766
TaskRevenue Cloud Associated Objects

===== PAGE 2781 =====

Field TypeField
Description
Represents what triggers a repeating task to repeat. Add this field to a page layout together
with the RecurrenceInterval  field, which determines the number of days between
the triggering date (due date or close date) and the due date of the next repeating task in
the series.
Label is Repeat This Task. This field has the following picklist values:
• None: The task doesn’t repeat.
• After due date: The next repeating task will be due the specified number of days after
the current task’s due date.
• After the task is closed: The next repeating task will be due the specified number of
days after the current task is closed.
• (Task closed): This task, now closed, was opened as part of a repeating series.
Note:  When tasks in a series are set to repeat after their due date, Salesforce doesn’t
create recurrences that would have been due in the past. Instead, Salesforce keeps
adding the interval until a repeated task has a due date in the future.
For example, suppose that someone sets a task to repeat three days after it’s due. But,
that person doesn’t complete the task (mark it Closed) until five days after it’s due.
Instead of creating a task that’s already overdue, Salesforce gives the new task a due
date of tomorrow. This due date is equivalent to 6 days after the due date; two intervals
of three days each.
If that person completes the repeating task (marks it Closed) before the due date, the
next task is still due three days after the due date.
Type
date
RecurrenceStartDateOnly
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The date when the recurring task begins. Must be a date and time before
RecurrenceEndDateOnly.
Type
picklist
RecurrenceTimeZoneSidKey
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The time zone associated with the recurring task. For example, “UTC-8:00” for Pacific Standard
Time.
Type
picklist
RecurrenceType
2767
TaskRevenue Cloud Associated Objects

===== PAGE 2782 =====

Field TypeField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Indicates how often the task repeats. For example, daily, weekly, or every nth month (where
“nth” is defined in RecurrenceInstance).
Type
dateTime
ReminderDateTime
Properties
Create, Filter, Nillable, Sort, Update
Description
Represents the time when the reminder is scheduled to fire, if IsReminderSet  is set to
true. If IsReminderSet  is set to false, then the user may have deselected the
reminder checkbox in the Salesforce user interface, or the reminder has already fired at the
time indicated by the value.
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Required. Indicates the status of the task. The default value of this field is Not Started.
Each predefined Status  field implies a value for the IsClosed  flag. To obtain picklist
values, query the TaskStatus object.
Possible values are:
• Completed
• Deferred
• In Progress
• Not Started
• Waiting on someone else
Note:  This field can’t be updated for recurring tasks (IsRecurrence  is true).
Type
combobox
Subject
Properties
Create, Filter, Nillable, Sort, Update
Description
The subject line of the task, such as “Call” or “Send Quote.” Limit: 255 characters.
Type
picklist
TaskSubtype
2768
TaskRevenue Cloud Associated Objects

===== PAGE 2783 =====

Field TypeField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
Provides standard subtypes to facilitate creating and searching for specific task subtypes.
This field isn’t updateable.
TaskSubtype  values:
• Task
• Email
• LinkedIn —Available in API version 56.0 and later.
• List Email
• Cadence
• Call
Note:  The Cadence  subtype is an internal value used by Sales Engagement, and
can’t be set manually.
Type
JunctionIdList
TaskWhoIds
Properties
Create, Update
Description
A string array of contact or lead IDs related to this task. This JunctionIdList  field is
linked to the TaskWhoRelations child relationship. TaskWhoIds is only available
when the shared activities setting is enabled. The first contact or lead ID in the list becomes
the primary WhoId  if you don’t specify a primary WhoId. If you set the EventWhoIds
field to null, all entries in the list are deleted and the value of WhoId  is added as the first
entry.
Warning:  Adding a JunctionIdList  field name to the fieldsToNull
property deletes all related junction records. This action can’t be undone.
Type
picklist
Type
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The type of task, such as Call or Meeting.
Type
int
WhatCount
Properties
Filter, Group, Nillable, Sort
2769
TaskRevenue Cloud Associated Objects

===== PAGE 2784 =====

Field TypeField
Description
Available to organizations that have Shared Activities enabled. Count of related TaskRelations
pertaining to WhatId. Count of the WhatId  must be 1  or less.
Type
reference
WhatId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The WhatId  represents nonhuman objects such as accounts, opportunities, campaigns,
cases, or custom objects. WhatIds are polymorphic. Polymorphic means a WhatId  is
equivalent to the ID of a related object. The label is Related To ID.
This is a polymorphic relationship field.
Relationship Name
What
Relationship Type
Lookup
Refers To
Account, Accreditation, AssessmentIndicatorDefinition, AssessmentTask,
AssessmentTaskContentDocument, AssessmentTaskDefinition, AssessmentTaskOrder, Asset,
AssetRelationship, AssignedResource, Award, BoardCertification, BusinessLicense,
BusinessMilestone, BusinessProfile, Campaign, CareBarrier, CareBarrierDeterminant,
CareBarrierType, CareDeterminant, CareDeterminantType, CareDiagnosis,
CareInterventionType, CareMetricTarget, CareObservation, CareObservationComponent,
CarePgmProvHealthcareProvider, CarePreauth, CarePreauthItem, CareProgram,
CareProgramCampaign, CareProgramEligibilityRule, CareProgramEnrollee,
CareProgramEnrolleeProduct, CareProgramEnrollmentCard, CareProgramGoal,
CareProgramProduct, CareProgramProvider, CareProgramTeamMember,
CareProviderAdverseAction, CareProviderFacilitySpecialty, CareProviderSearchableField,
CareRegisteredDevice, CareRequest, CareRequestDrug, CareRequestExtension,
CareRequestItem, CareSpecialty, CareSpecialtyTaxonomy, CareTaxonomy, Case,
CommSubscriptionConsent, ContactEncounter, ContactEncounterParticipant, ContactRequest,
Contract, CoverageBenefit, CoverageBenefitItem, CreditMemo, DelegatedAccount,
DocumentChecklistItem, EnrollmentEligibilityCriteria, HealthcareFacility,
HealthcareFacilityNetwork, HealthcarePayerNetwork, HealthcarePractitionerFacility,
HealthcareProvider, HealthcareProviderNpi, HealthcareProviderSpecialty,
HealthcareProviderTaxonomy, IdentityDocument, Image, IndividualApplication, Invoice,
ListEmail, Location, MemberPlan, Opportunity, Order, OtherComponentTask, PartyConsent,
PersonLifeEvent, PlanBenefit, PlanBenefitItem, ProcessException, Product2, ProductItem,
ProductRequest, ProductRequestLineItem, ProductTransfer, PurchaserPlan,
ReceivedDocument, ResourceAbsence, ReturnOrder, ReturnOrderLineItem,
ServiceAppointment, ServiceResource, Shift, Shipment, ShipmentItem, Solution, Visit,
VisitedParty, VolunteerProject, WorkOrder, WorkOrderLineItem
2770
TaskRevenue Cloud Associated Objects

===== PAGE 2785 =====

Field TypeField
Type
int
WhoCount
Properties
Filter, Group, Nillable, Sort
Description
Available to organizations that have Shared Activities enabled. Count of related TaskRelations
pertaining to WhoId.
Type
reference
WhoId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The WhoId represents a human such as a lead or a contact. WhoIds are polymorphic.
Polymorphic means a WhoId is equivalent to a contact’s ID or a lead’s ID. The label is Name
ID.
If Shared Activities is enabled, the value of this field is the ID of the related lead or primary
contact. If you add, update, or remove the WhoId field, you might encounter problems with
triggers, workflows, and data validation rules that are associated with the record. The label
is Name ID.
Beginning in API version 37.0, if the contact or lead ID in the WhoId  field is not in the
TaskWhoIds list, no error occurs and the ID is added to the TaskWhoIds as the primary
WhoId. If WhoId  is set to null, an arbitrary ID from the existing TaskWhoIds  list is
promoted to the primary position.
This is a polymorphic relationship field.
Relationship Name
Who
Relationship Type
Lookup
Refers To
Contact, Lead
Usage
Recurring Tasks
• Recurring tasks are available in API version 16.0 and later.
• After a task is created, it can’t be changed from recurring to nonrecurring or vice versa.
• When a user creates a series of recurring tasks, Salesforce creates a main record and subsequent occurrences. For the main record,
IsRecurrence  is set to true  and other fields that define the recurrence pattern are populated. The ID of the main record of
the recurring task is saved in the subsequent occurrences, in the RecurrenceActivityId  field.
2771
TaskRevenue Cloud Associated Objects

===== PAGE 2786 =====

• When you delete a recurring task series through the API, all open and closed task occurrences in the series are removed. However,
when you delete a recurring task series through the user interface, only open tasks occurrences (IsClosed  is false) in the
series are removed.
• If IsRecurrence  is true, then RecurrenceStartDateOnly, RecurrenceEndDateOnly, RecurrenceType,
and any properties associated with the given recurrence type (see the following table) must be populated.
• When you change the RecurrenceStartDateOnly  field or the recurrence pattern, all open tasks occurrences in the series
are deleted and new open task occurrences are created based on the new recurrence pattern. The following fields determine the
recurrence pattern: RecurrenceType, RecurrenceTimeZoneSidKey, RecurrenceInterval,
RecurrenceDayOfWeekMask, RecurrenceDayOfMonth, RecurrenceInstance, and
RecurrenceMonthOfYear.
• When you change the value of RecurrenceEndDateOnly  to an earlier date (for example, from January 20 to January 10), all
open task occurrences in the series with the ActivityDate  value greater than the new end date value are deleted. Other open
and closed task occurrences in the series are not affected.
• When you change the value of RecurrenceEndDateOnly  to a later date (for example, from January 10 to January 20), new
task occurrences are created up to the new end date. Existing open and closed tasks in the series are not affected.
This table describes the usage of recurrence fields for Salesforce Classic recurring events. Each recurrence type must have all of its
properties set. All unused properties must be set to null.
Example PatternPropertiesRecurrenceType Value
Every second dayRecurrenceIntervalRecursDaily
Every weekday - can’t be Saturday or SundayRecurrenceDayOfWeekMaskRecursEveryWeekday
Every second month, on the third day of the monthRecurrenceDayOfMonth
RecurrenceInterval
RecursMonthly
Every second month, on the last Friday of the monthRecurrenceInterval RecurrenceInstance
RecurrenceDayOfWeekMask
RecursMonthlyNth
Every three weeks on Wednesday and FridayRecurrenceInterval
RecurrenceDayOfWeekMask
RecursWeekly
Every March on the 26th day of the monthRecurrenceDayOfMonth
RecurrenceMonthOfYear
RecursYearly
The first Saturday in every OctoberRecurrenceDayOfWeekMask
RecurrenceInstanceRecurrenceMonthOfYear
RecursYearlyNth
JunctionIdList
The JunctionIdList  field is now implemented in the Event and Task objects. With a single API call, it’s easy to create
many-to-many relationships between the Event or Task object with contacts, leads, or users.
To create a Task with related Contacts without JunctionIdList, you first have to create the task, then use the returned task
ID to create the TaskRelation  records. If the TaskRelation  save call fails, error handling is your responsibility because the
task has already been committed to the database.
public void createTasksOld(Contact[] contacts) {
Task task = new Task();
task.setSubject("New Task");
SaveResult[] results = null;
2772
TaskRevenue Cloud Associated Objects

===== PAGE 2787 =====

try {
results = connection.create(new Task[] {
task
});
if (results[0].isSuccess()) {
TaskRelation[] relations = new TaskRelation[contacts.size()];
for (int i = 0; i < contacts.length; i++) {
relations[i] = new TaskRelation();
relations[i].setTaskId(results[0].getID());
relations[i].setRelationId(contacts[i].getID());
}
results = connection.create(relations);
}
} catch (ConnectionException ce) {
ce.printStackTrace();
}
}
To create a task using JuncionIdList, IDs are pulled from the related contacts and both the task and the TaskRelation
records are created in one API call. If the TaskRelation  fails, the task is rolled back because it’s all done in a single API call.
public void createTaskNew(Contact[] contacts) {
String[] contactIds = new String[contacts.size()];
for (int i = 0; i < contacts.size(); i++) {
contactIds[i] = contacts[i].getID();
}
Task task = new Task();
task.setSubject("New Task");
task.setTaskWhoIds(contactIds);
SaveResult[] results = null;
try {
results = connection.create(new Task[] {
task
});
} catch (ConnectionException ce) {
ce.printStackTrace();
}
}
Shared Field-Level Security for Event and Task Objects
Metadata deployments for the Task object should always include the field-level security for the Event object. Shared field-level security
prevents each object from changing the field-level security of the associated object.
Metadata deployments that include field-level security for only one of either the Event or Task objects can cause field-level security
changes to the other object that aren't reflected in the metadata.
• If field-level security is enabled for one object, then field-level security is enabled for both objects.
• If field-level security is disabled for one object, then it's disabled for both objects.
Note:  A missing entry in the metadata is treated as field-level security being disabled.
2773
TaskRevenue Cloud Associated Objects

===== PAGE 2788 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
TaskChangeEvent (API version 44.0)
Change events are available for the object.
TaskFeed (API version 20.0)
Feed tracking is available for the object.
2774
TaskRevenue Cloud Associated Objects