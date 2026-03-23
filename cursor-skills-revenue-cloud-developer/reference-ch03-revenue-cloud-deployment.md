---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 3 — Revenue Cloud Deployment

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 3 Revenue Cloud Deployment
This section provides a clear roadmap for accurately and efficiently deploying Revenue Cloud objects
and metadata between development, staging, sandbox, and production orgs.
In this chapter ...
• Deployment
Workflows and
Sequence
Developing and maintaining complex business applications on the Salesforce Platform requires a
structured approach to managing changes and deployments. This is especially true for Revenue Cloud,
which involves a complex data model and metadata components.• Deployment
Considerations The interconnected nature of Revenue Cloud's architecture requires a meticulous and well-defined
development operations (DevOps) process. Without it, organizations face significant risks, including data
corruption, deployment failures, and disruption to critical business processes.
• Global Unique ID
Setup
Who This Section Is For
This section is intended for advanced users who are familiar with Salesforce development, established
DevOps concepts, and Salesforce administration.
• Managing
Component States
• Post-Deployment
Steps
• Deployment
Scenarios
What’s Not Included
• Object Deployment
Reference
• Metadata
Deployment
Reference
• This section doesn't include information about data migration from external or legacy systems.
• There's no built-in, Revenue Cloud-specific deployment tool. Select the Salesforce or third-party
deployment tools appropriate for your use case.• Additional
Deployment
Information
• Every Salesforce implementation is unique. This guide doesn't address how to deploy your custom
objects, fields, Apex classes, metadata, Lightning Web Components (LWCs), and so on.
9

===== PAGE 24 =====

Deployment Workflows and Sequence
A typical dev ops cycle involves managing test orgs, sandboxes, and a production org. Your deployment workflow can be a simple
deployment of all setup and data from a development org to production. Or, it can be much more complex, involving multiple staging
and testing orgs before any changes are sent to production.
Here's a diagram illustrating several potential deployment plans.
Full vs. Incremental Deployment
Deployments take two primary forms: full and incremental.
A full deployment involves migrating the entire set of relevant metadata such as objects, fields, classes, triggers, and potentially a
significant volume of data from a source org. This ensures that the target org is a complete, synchronized replica of the source at that
point in time.
Full deployments are best suited for initial setup, major releases, or when deploying to a completely new, or non-synced environment,
such as the first deployment to a sandbox or staging org.
Incremental deployments are used for ongoing DevOps activities. They focus only on the specific metadata components and associated
data records that have been created, modified, or deleted since the last successful deployment.
This incremental approach is faster, reduces deployment risk by minimizing the scope of changes, and is essential for maintaining
business continuity in a live production environment. Critical to this process is a version control system to track and compare differences
between environments, ensuring only the necessary "delta" is packaged and deployed.
Planning for incremental deployments requires change tracking, dependency analysis, and careful sequencing of data and metadata
components to ensure that all prerequisites are met in the target environment.
Deployment Sequence and Dependencies
The deployment process must navigate intricate dependencies involving both metadata and the data records themselves. For instance,
before deploying the data records for an object, the necessary metadata must be in place first to ensure that the destination org is
structurally prepared to receive the data.
10
Deployment Workflows and SequenceRevenue Cloud Deployment

===== PAGE 25 =====

Also, there are dependencies based on the record relationships. For example, if you're deploying a custom object with a lookup to the
standard Account object, the Account records must be created first to satisfy the lookup relationship when the custom object's child
records are subsequently inserted. You must also account for parent-child or master-detail relationships, requiring the parent record to
be deployed before the child, to preserve referential integrity. Proper assessment and sequencing of these interdependent data and
metadata components is vital to avoid validation errors and data corruption.
Sometimes, there are loops in the inter-relationships. For example, an object A depends on object B being deployed earlier, and object
B depends on object A being deployed earlier. Let’s say object A goes first, then object B goes next. Because of circular dependencies,
one has to redeploy object A a second time to ensure all the references are properly populated.
Here are a few deployment dependency examples.
• The Product Specification Record Type must be deployed before you can insert any Product records.
• The Attribute Based Adjustment Rule must be deployed before you can insert any Attribute Based Adjustment records.
• Decision Tables (metadata records) must be deployed before deploying Pricing Recipes (metadata records).
Note:  For complete information on the required deployment sequence, see Object Deployment Sequence and Metadata
Deployment Reference.
Deployment Considerations
In any deployment scenario, you must understand all dependencies and prerequisites related to your planned changes.
Here's a list of things to consider and plan for.
Key considerations include:
• What’s the sequence followed for object deployment? What dependencies exist on related objects?
• Do your objects have Draft, Active, or Inactive states?
• Does activation occur through an API or by simply setting a boolean field (active flag)?
• Are there special fields to consider, such as text fields with embedded IDs, JSON, or fields populated via triggers?
• Are there fields or objects that represent unique or sequential data that must be preserved in the target org?
• How would you handle system settings between the orgs? For example, making sure that a feature toggle is turned off in the target
org so that automation doesn't start executing when you insert data from your source org.
• What's the impact of versioning on your deployment? For example, schema, app, or API versions.
Note: For detailed information about these deployment considerations, see Additional Deployment Information.
Global Unique ID Setup
The establishment of a Global Unique ID (GUID) column on all objects during day-one initialization is a recommended practice for
Salesforce DevOps.
Salesforce uses its own internal ID for records, but this ID isn't portable. The same record in a testing, sandbox, or production org has
different Salesforce IDs. This makes tracking a single piece of data across environments nearly impossible. By introducing your own
custom, externally set GUID, you have a single, immutable, and universally consistent identifier.
Note:  You can also choose your preferred method to maintain the mapping of records IDs across orgs.
Before performing any deployment work, establish your GUID across all database objects, and across all Salesforce orgs involved in your
deployment plan.
11
Deployment ConsiderationsRevenue Cloud Deployment

===== PAGE 26 =====

Note:  Add a GUID field to all objects used during your deployment. Since you can't add fields to metadata types (such as a Flow),
use the API name for each metadata type as the unique identifier.
Create a GUID Field
Add a GUID field to all objects used during your deployment to ensure unique identification of records across environments.
GUID Design and Usage
The format and values of the Global Unique ID (GUID) are up to you. Here's some guidance on what makes a good versus poor GUID
for deployment tracking.
Create a GUID Field
Add a GUID field to all objects used during your deployment to ensure unique identification of records across environments.
1. From Setup, in the Quick Find box, find and select Object Manager.
2. Select an object.
3. Click Fields & Relationships.
4. Click New.
5. Select Text for the data type.
6. Enter a field label and field name.
7. Enter a length.
We recommend 255 to avoid any errors related to ID length.
8. Select Unique and External ID.
Important:  Selecting these attributes ensures that every record gets a unique ID.
9. Click Next.
10. Select the appropriate profiles for field access, optionally add the field to page layouts, and then click Save.
11. Repeat this process for all Salesforce objects related to your deployment plan.
Note:  Alternatively, you can create GUID fields by using the Metadata API. For more information, see Understanding Metadata
API and the Custom Field metadata type.
GUID Design and Usage
The format and values of the Global Unique ID (GUID) are up to you. Here's some guidance on what makes a good versus poor GUID for
deployment tracking.
The format and values of the GUID itself are up to you. Here's some guidance on what makes a good versus poor GUID.
A good GUID design includes these characteristics.
• Immutable
• Unique globally
• Non-translatable
• A single key
• Generated programmatically, and not manually
12
Create a GUID FieldRevenue Cloud Deployment

===== PAGE 27 =====

Poor GUID design includes these characteristics.
• Record Name field (mutable)
• Combination of mutable attributes such as Name + Version + Sequence
• Concatenated keys
• Conditional keys (Pricebook + Product OR Pricebook + Product + ISO Code)
Populate a GUID
Once you have created the GUID field on all the Salesforce objects related to your deployment plan, you're ready to populate the field
with data.
Add the GUID column to your import spreadsheets or import file definitions. Populate the field with the GUID format you've chosen.
Now, you're ready to use the GUID in your deployment process.
Important:  You must populate the GUID field not only at the beginning of your deployment process, but you must also populate
it for any new records you generate along the way.
Usage of GUID in the Deployment Cycle
The GUID is the cornerstone of your deployment and data migration strategy. During the deployment process, leverage the GUID for
accurate upserts and data mapping. When migrating data records from one org to another, your deployment method must use the
GUID as the external ID field for lookup and matching. This practice ensures that updates are applied precisely to the correct record,
preventing data duplication or corruption.
In the event of a deployment failure or a post-deployment data issue, administrators can use the GUID to quickly and confidently locate
the problematic records in all orgs for precise auditing and troubleshooting.
Non-Extensible Objects
A few Revenue Cloud objects are protected, and therefore non-extensible. You can't add a GUID field to these objects. Instead, create
an external reference table to store your GUID. Use this reference table to track the non-extensible object throughout your deployment
process.
Managing Component States
Manage activation, versioning, and dependencies for components and objects as part of your deployment plan. A successful deployment
makes sure that the system executes the intended, final, and active logic, preventing failures caused by stale or inactive component
dependencies.
A component's state is its operational status, which includes the:
• Active, inactive, or draft state
• Component version
13
Managing Component StatesRevenue Cloud Deployment

===== PAGE 28 =====

• Dependencies on other components and objects
• Component-specific attributes like rank on expression sets
Components like decision tables, expression sets, and context definitions must be deployed taking their state into account. Also, some
objects use an Active checkbox to determine if their records must be used during run time operations or not.
You must also make sure that all related dependencies are moved correctly and in the proper sequence from the source org to the target
org.
State Management Scenarios
Component deployments usually fall into one of these categories:
Deploy a New Component
If the target org doesn’t contain the component that you want to migrate, deploy it along with its versions from the source org to
the target org.
Deploy Component Updates
When the target org already contains the component you want to migrate, then state and version management take effect. For
example, with expression sets, you must deactivate the version in the target org where you want to deploy changes. If you try to
deploy to an active version, the deployment fails.
Deploy Components with Dependencies
All related dependencies must be moved correctly and in the proper sequence from the source org to the target org. For example,
expression sets reference elements such as decision matrices, decision tables, subexpressions, context definitions, field and object
aliases, and explainability message templates. Migrate the dependent elements independently before you migrate the expression
set version.
Helpful Links
Refer to these links for examples and component-specific information:
• Considerations for Migrating Decision Tables
• Considerations for Migrating Expression Sets
• Migration of Expression Sets with Dependencies
• Migrate Context Definitions
Note:  Some Revenue Cloud components have unique activation requirements. For complete information about state management
for these components, see Additional Deployment Information.
Post-Deployment Steps
Most deployments require that you take some actions after the deployment to the target org is complete to ensure proper functionality
and data integrity.
Here are some examples of common post-deployment tasks.
• Refresh decision tables
• Sync pricing data
• Rebuild the product index
• Manually create elements that couldn’t be deployed through the API
• Create or activate user accounts for testing and validation
14
Post-Deployment StepsRevenue Cloud Deployment

===== PAGE 29 =====

Note:  For information about the post-deployment steps necessary for each Revenue Cloud feature, see Additional Deployment
Information.
Deployment Scenarios
Learn about specific deployment scenarios including new environment setup, refreshes, retiring records, deploying patches, and many
more.
Product Catalog Management
Table 1: Product Definition: Full Deployment Scenarios
Validation and DependenciesImpactScenario
In the target org: Align baseline metadata.Metadata: See Additional Deployment
Information.
Large Catalog Refresh
Introduce 200+ new SKUs for accessories
line
Validation: Run automated regression tests
on bundles and pricing. Validate sample
SKUs across categories.
Data: bulk product load, product classes,
selling models, price book entries, discount
schedules, association to categories,
catalogs
Table 2: Product Definition: Incremental Deployment Scenarios
Validation and DependenciesImpactScenario
In the target org, a price book and rate card
must exist, and billing rules are configured.
Metadata: product record type, updated
page layouts, product catalog management,
pricing, usage, and rating metadata
New Product Launch
Introduce a new product (simple) of type
one time, subscription, and usage with
standard pricing.
Validation: Create a test quote with
products, confirm price flows into quote or
order, validate subscription billing cycle,
validate rates.
Data: product records, product
classifications, attributes, attribute picklists,
price book entries, rate card entries,
subscription term details
In the target org, attributes and picklists
must be created or updated, child products
Metadata: none
Data: bundle definition, child products,
option groups, option attribute
configurations, bundle pricing
Bundle Creation
Launch a new product bundle that includes
core products, add-ons, and attribute
configurations with standard pricing.
must be created or updated, and a price
book must exist.
Validation: Configure a bundle in a quote,
test configuration options, and ensure
correct pricing roll up.
In the target org, attributes and picklists
must be created or updated first.
Metadata: none
Data: new attributes, new and updated
product class attribute assignments.
Update Product Classification Properties
Add new attributes and update existing
attribute properties to existing product
classification.
Validation: Generate a quote with updated
product, and validate that product attributes
appear correctly.
15
Deployment ScenariosRevenue Cloud Deployment

===== PAGE 30 =====

Validation and DependenciesImpactScenario
In the target org, attributes and picklists
must be created or updated first.
Metadata: none
Data: new class, class relationship, and class
attribute assignments
Update Product Classification Hierarchy
Add a new sub-classification, configure
attributes, and create a product by using
the sub-class.
Validation: Generate a quote with a new
product. Validate product attributes
correctly appear.
Active quotes with retired products must
be closed or replaced.
Metadata: none
Data: Set product status to Inactive. Remove
the product from active price books.
Product Retirement
Deactivate legacy products
Validation: Attempt to add a retired product
to the quote and confirm it's blocked. Make
sure that reporting reflects retirement.
In target org, make sure that baseline
metadata is created. Run full indexing in the
target org before you enable the feature.
Metadata: See Appendix C
Data: Index configuration (searchable,
filterable, languages)
Update Product Discovery Setup
Change qualification procedure, product
discovery flow, and turn on Indexed Product
feature. Validation: Validate the product discovery
setup changes and product indexing
process status. Verify by discovering
products with term-based and faceted
search.
Table 3: Catalog, Categories & Related Products: Full Deployment Scenarios
Validation and DependenciesImpactScenario
Products must exist before adding to the
catalog
Metadata: Catalog object configuration, and
Salesforce Configure, Price, Quote (CPQ)
page layouts
New Catalog Creation
Introduce a new catalog for a business line.
For example, Cloud Services. Validation: Validate that the catalog is visible
in quotes and orders. Confirm that all linked
products appear.
Data: Create catalog records and linked
products
In the target org, make sure that baseline
metadata is created.
Metadata: Update catalog metadata if new
categories are required.
Large Catalog Expansion
Add 500+ new SKUs across multiple
categories. Validation: Confirm that sample SKUs appear
in the correct categories. Perform a
regression test of the catalog navigation.
Data: Bulk product-category relationships,
and new catalog entries.
Table 4: Catalog, Categories & Related Products: Incremental Deployment Scenarios
Validation and DependenciesImpactScenario
Parent catalog must exist in the target org.Metadata: Update category hierarchy
metadata
Add New Category
16
Deployment ScenariosRevenue Cloud Deployment

===== PAGE 31 =====

Validation and DependenciesImpactScenario
Add the Security Services category under
the existing catalog.
Validation: Confirm that products appear
under the new category in the catalog
browser.
Data: Create category record, and link
products
Validation: Validate that moved products
appear only in the new category and that
the old category is clean.
Metadata: Update category hierarchy and
associations.
Data: Update category-to-product
mappings.
Category Reorganization
Move products from the Hardware category
to the Accessories category.
Validation: Validate that the products aren’t
visible in the category browser or guided
selling.
Metadata: Update product visibility settings.
Data: Update product-category
relationships.
Product Retirement from Category
Remove retired products from catalog and
related category.
Products must exist and be tagged for
promotion.
Metadata: Configure the category (and
time-based visibility if applicable).
Seasonal Category
Introduce a temporary Holiday Deals
category. Validation: Confirm that the category is
visible during the correct time period only.
Verify that the correct products are included.
Data: Establish product-category
relationships with seasonal tag.
Table 5: Qualification Rules: Full Deployment Scenarios
Validation and DependenciesImpactScenario
Perform target org metadata baseline
alignment and staging of decision tables for
verification.
Metadata: Qualification Rule framework and
Expression Set alignment
Data: Insert decision tables in bulk.
Large-Scale Decision Table Migration
Introduce 100+ new eligibility conditions,
such as new geographies and pricing
models. Validation: Regression test eligibility across
multiple conditions and customer profiles.
All child rules and data mappings must exist
in the target org.
Metadata: Create parent qualification rule,
and update multiple expression sets.
Composite Qualification Rule
Combine multiple decision tables and
expression sets into a new guided selling
path.
Validation: Test end-to-end guided selling
to confirm the composite flow works
correctly.
Data: Populate multiple decision tables with
new mappings.
Table 6: Qualification Rules: Incremental Deployment Scenarios
Validation and DependenciesImpactScenario
Product catalog and customer tiers must be
available in the target org.
Metadata: New qualification rule metadata,
and context definition setup
New Qualification Rule with Decision Table
Create a qualification rule to enforce
eligibility for product bundles based on
region and customer tier.
17
Deployment ScenariosRevenue Cloud Deployment

===== PAGE 32 =====

Validation and DependenciesImpactScenario
Validation: Create test quotes for each
region and tier. Confirm that only eligible
products appear.
Data: Populate decision table entries with
region and tier mappings
Make sure that new values are aligned with
the active product catalog.
Metadata: none
Data: Update and add rows in decision
tables.
Update Existing Decision Table Entries
Add new conditions to an existing
qualification rule such as adding a new
country to eligibility.
Validation: Confirm that the rule returns the
correct product eligibility for the new
condition.
Make sure that the dependent context
variable exists.
Metadata: Update expression set definition
Data: none
Modify Expression Set
Change logical criteria from OR to AND in
the qualification logic. For example, the Validation: Confirm both the positive and
negative test cases (eligible vs. non-eligible
customers).
customer must be an enterprise and have
a support contract.
Ensure that the Industry field exists and is
populated.
Metadata: Add field reference in context
definition
Context Definition Expansion
Add a new attribute to the context (for
example, Industry) for use in qualification
rules.
Validation: Test that qualification rules can
read Industry context during quote creation.
Data: None (until data is mapped into a
decision table)
Make sure that the rule isn’t referenced by
other bundles or flows.
Metadata: Update rule status to inactive,
and remove references from related
expression set.
Retirement of Qualification Rule
Deactivate old eligibility rule no longer
needed such as a legacy discount program. Validation: Confirm that the retired rule no
longer impacts guided selling or product
selection.
Data: Remove or disable related decision
table entries.
Salesforce Pricing
Table 7: Pricing: Incremental Deployment Scenarios
Validation and DependenciesImpactScenario
Make sure that no dependent contracts
reference the old pricing.
Metadata: None (if there are no new rules)
Data: Update price book entries and adjust
discount tiers.
Pricing Update
Update base license cost by +5% for existing
products. Validation: Generate a quote with the
updated product. Confirm that pricing
reflects the new value. Confirm no impact
to active contracts.
Approval workflow for discount must be
active
Metadata: New time-based pricing rule and
approval process update.
Promotional Discount
Introduce a three-month promotional
discount for enterprise customers.
18
Deployment ScenariosRevenue Cloud Deployment

===== PAGE 33 =====

Validation and DependenciesImpactScenario
Validation: Confirm that the discount applies
only during the promotion period and verify
that approvals trigger correctly.
Data: Create a discount schedule and promo
product entry.
Object Deployment Reference
Get to know the object deployment sequence and associated properties.
Product Catalog Management Objects
This table provides the deployment sequence, object types, API names, lookup fields, and data translation requirements for Product
Catalog Management objects in Revenue Cloud.
Salesforce Pricing Objects
This table provides the deployment sequence, object types, API names, lookup fields, and data translation requirements for Salesforce
Pricing objects in Revenue Cloud.
Product Configurator Objects
This table provides the object deployment sequence and properties for Product Configurator in Revenue Cloud, including object
types, API names, deployment sequences, and lookup fields.
Transaction Management Objects
This table provides the deployment sequence, object types, and API names for Transaction Management objects in Revenue Cloud.
Dynamic Revenue Orchestrator Objects
This table provides the deployment sequence, object types, API names, and lookup fields for Dynamic Revenue Orchestrator objects
in Revenue Cloud.
Usage Management Objects
This table provides the deployment sequence, object types, API names, and lookup fields for Usage Management objects in Revenue
Cloud.
Billing Objects
This table provides the deployment sequence, object types, API names, and lookup fields for Billing objects in Revenue Cloud.
Salesforce Contracts Objects
This table provides the deployment sequence, object types, API names, and lookup fields for Salesforce Contracts in Revenue Cloud.
Product Catalog Management Objects
This table provides the deployment sequence, object types, API names, lookup fields, and data translation requirements for Product
Catalog Management objects in Revenue Cloud.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Note:  Internal objects aren't accessible.
19
Object Deployment ReferenceRevenue Cloud Deployment

===== PAGE 34 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
User1ProductSpecificationTypeProduct Specification
Type
Metadata
Product Specification Type2ProductSpecification Record TypeProduct Specification
Record Type
Metadata
User, User Group, Unit of Measure3AttributePickistAttribute PicklistConfiguration
User, Attribute Picklist
(Master-Detail)
4
46
AttributePicklistValue
Translation table: AttributePicklist
ValueDataTranslation
Attribute Picklist Value
Translation table:
Attribute Picklist Value
Data Translation
Configuration
User, Unit of Measure5UnitOfMeasureClassUnit of Measure ClassConfiguration
User Group, Unit of Measure Class6UnitOfMeasureUnit of MeasureConfiguration
User, Attribute Picklist, Unit of
Measure
7
47
AttributeDefinition
Translation table:
AttributeDefinitionDataTranslation
Attribute Definition
Translation table:
Attribute Definition Data
Translation
Configuration
User Group8AttributeCategoryAttribute CategoryConfiguration
48Translation table:
AttributeCategoryDataTranslation
Translation table:
Attribute Category Data
Translation
User Group, Attribute Category,
Attribute Definition
9AttributeCategoryAttributeAttribute Category
Attribute
Configuration
User, User Group, Product
Classification
10
49
ProductClassification
Translation table:
ProductClassificationData
Translation
Product Classification
Translation table: Product
Classification Data
Translation
Configuration
Attribute Definition, Attribute
Category, Product Classification
11
50
ProductClassificationAttr
Translation table:
ProductClassificationAttrData
Translation
Product Classification
Attribute
Translation table: Product
Classification Attribute
Data Translation
Configuration
Attribute, Product Classification
Attribute, User, User Group, Unit of
Measure
User, Tax Treatment12TaxPolicyTax PolicyConfiguration
Product Classification, Billing
Policy, User, External Data Source,
Tax Policy, Unit of Measure
13
51
Product2
Translation table:
Product2DataTranslation
Product
Translation table:
Product2 Data Translation
Configuration
20
Product Catalog Management ObjectsRevenue Cloud Deployment

===== PAGE 35 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
Named Credential, Tax Engine
Provider
14TaxEngineTax EngineConfiguration
Legal Entity, Product, Tax Policy,
Tax Engine
15TaxTreatmentTax TreatmentConfiguration
Attribute Definition, Attribute
Category, User, Product Attribute
16ProductAttributeDefinitionProduct Attribute
Definition
Configuration
Definition, Product Classification
Attribute, Unit of Measure
Product Classification Attribute,
Product Attribute Definition
17AttrPicklistExcludedValueAttribute Picklist Excluded
Value
Configuration
(polymorphic), Attribute Picklist
Value
User, User Group18ProdtAttrScopeProduct Attribute ScopeConfiguration
Product Classification Attribute,
Product Attribute Definition
19ProdtAttrMappedScopeProduct Attribute
Mapped Scope
Configuration
(polymorphic), Product Attribute
Mapped Scope, Product Attribute
Scope
User20ProductSellingModelProduct Selling ModelConfiguration
User, Product Selling Model,
Proration Policy
21ProductSellingModelOptionProduct Selling Model
Option
Configuration
User, Product Selling Model,
Product
22ProductRampSegmentProduct Ramp SegmentConfiguration
User23ProductRelationshipTypeProduct Relationship
Type
Configuration
User, User Group, Product
Component Group
24ProductComponentGroupProduct Component
Group
Configuration
User, Product, Product
Classification, Product Selling
25ProductRelatedComponentProduct Related
Component
Configuration
Model, Product Component Group,
Product Relationship Type, Unit of
Measure
User, User Group, Product, Product
Component Group
26ProductComponentGrpOverrideProduct Related Group
Override
Configuration
UserGroup, Product, Product
Related Component, Unit of
Measure
27ProductRelComponentOverrideProduct Related
Component Override
Configuration
User, User Group28ProductCatalogCatalogConfiguration
21
Product Catalog Management ObjectsRevenue Cloud Deployment

===== PAGE 36 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
52Translation table:
ProductCatalogDataTranslation
Translation table: Product
Catalog Data Translation
User, Catalog (Master-Detail)29ProductCategoryCategoryConfiguration
53Translation table:
ProductCategoryDataTranslation
Translation table: Product
Category Data Translation
Product, Category (Master-Detail)30ProductCategoryProductProduct Category ProductConfiguration
User, User Group, Product31ProductQualificationProduct QualificationConfiguration
User, User Group, Product32ProductDisqualificationProduct DisqualificationConfiguration
User, User Group, Category33ProductCategoryQualificationProduct Category
Qualification
Configuration
User, User Group, Category34ProductCategoryDisqualProduct Category
Disqualification
Configuration
35RuntimeCatalogIndexSettingRuntime Catalog Index
Settings (Internal)
Configuration
36WebStoreSearchAttrSettingsWebStore Search Attr
Settings (Internal)
Configuration
Assessment Question Version,
Assessment Question, User, User
Group
37AssessmentQuestionAssessment QuestionConfiguration
Assessment Question
(Master-Detail)
38AssessmentQuestionVersionAssessment Question
Version
Configuration
Account, Contact, User, User
Group, Omni Process, Assessment
39AssessmentAssessmentConfiguration
Assessment Question Version,
Assessment (Master-Detail), User,
User Group
40AssessmentQuestionResponseAssessment Question
Response
Configuration
User, User Group41OmniProcessOmni ProcessConfiguration
Omni Process (Master-Detail),
Omni Process Element
42OmniProcessElementOmni Process ElementConfiguration
Assessment Question Version,
Omni Process, Omni Process
Element, User Group
43OmniProcessAsmtQuestionVerOmniProcess Assessment
Question Version
Configuration
User, User Group44AssessmentQuestionSetAssessment Question SetConfiguration
22
Product Catalog Management ObjectsRevenue Cloud Deployment

===== PAGE 37 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
Assessment Question Set, User,
User Group
45AssessmentQuestionAssignmentAssessment Question
Assignment
Configuration
SEE ALSO:
Revenue Cloud Developer Guide: Product Catalog Management Standard Objects
Explore the Revenue Cloud Data Model
Salesforce Pricing Objects
This table provides the deployment sequence, object types, API names, lookup fields, and data translation requirements for Salesforce
Pricing objects in Revenue Cloud.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Note:  Internal objects aren't accessible.
Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
1ProductSellingModelProduct Selling ModelConfiguration
Translation table: ProductSelling
ModelDataTranslation
Translation table: Product
Selling Model Data
Translation
ProductSellingModel
(Master-Detail), Product2 (Foreign
key), ProrationPolicy (Foreign key)
2ProductSellingModelOption
Translation table: ProductSelling
ModelOptionDataTranslation
Product Selling Model
Option
Translation table: Product
Selling Model Option
Data Translation
Configuration
Pricebook2 (Foreign Key)3Pricebook2Price BookConfiguration
4CostBookCost BookConfiguration
Pricebook2 (Foreign Key), Product2
(Foreign key), ProductSellingModel
(Foreign Key)
5PriceBookEntryPrice Book EntryConfiguration
CostBook (Master-Detail), Product
(Foreign Key)
6CostBookEntryCost Book EntryConfiguration
Pricebook2 (Foreign Key), Contract
(Foreign Key)
7PriceAdjustmentSchedulePrice Adjustment
Schedule
Configuration
23
Salesforce Pricing ObjectsRevenue Cloud Deployment

===== PAGE 38 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
PriceAdjustmentSchedule
(Master-Detail),
8Price Adjustment TierPrice Adjustment TierConfiguration
ProductSellingModel (Foreign Key),
Product2 (Foreign key)
Product2 (Foreign Key),
PricebookEntry (Foreign Key),
9PriceBookEntryDerivedPricePrice Book Entry Derived
Price
Configuration
Pricebook2 (Foreign Key),
ProductSellingModel (Foreign Key)
PriceAdjustmentSchedule
(Master-Detail), Product2 (Foreign
10BundleBasedAdjustmentBundle Based AdjustmentConfiguration
key), ProductSellingModel (Foreign
Key)
11AttributeBasedAdjRuleAttribute Based
Adjustment Rule
Configuration
AttributeBasedAdjRule
(Master-Detail), AttributeDefinition
12AttributeAdjustmentConditionAttribute Adjustment
Condition
Configuration
(Foreign Key), Product2 (Foreign
Key)
PriceAdjustmentSchedule
(Master-Detail),
13AttributeBasedAdjustmentAttribute Based
Adjustment
Configuration
ProductSellingModel (Foreign Key),
AttributeBasedAdjRule (Foreign
Key), Product2 (Foreign key)
30IndexRateIndex rate (extended
from Financial Services
Cloud)
Configuration
PricebookEntry (Foreign Key),
Pricebook (Foreign Key), Product
35PriceBookPriceGuidancePrice Book Price GuidanceMetadata
(Foreign Key), ProductSellingModel
(Foreign Key)
ExpressionSet (Foreign Key)40PricingProcedureResolutionPricing Procedure
Resolution
Metadata
PricingRecipeTableMapping
(Foreign Key), OutputFieldName
(Foreign Key)
40PricingProcedureOutputMapPricing Procedure Output
Map
Configuration
ExpressionSetDefinition (Foreign
Key)
50PricingRecipePricing RecipeMetadata
50ProrationPolicyProration PolicyConfiguration
Pricebook2 (Foreign Key)90ProductPriceRangeProduct Price RangeConfiguration
24
Salesforce Pricing ObjectsRevenue Cloud Deployment

===== PAGE 39 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
PriceRevisionPolicyPrice Revision PolicyConfiguration
PricingRecipe (Master-Detail),
LookupTable (Foreign Key)
PricingRecipeTableMappingPricing Recipe Table
Mapping (Internal)
Metadata
ProductPriceRange (Master-Detail)ProductPriceHistoryLogProduct Price History Log
(Internal)
Configuration
PricingAdjBatchJobPricing Adjustment Batch
Job (Internal)
Configuration
PricingAdjBatchJob (Master-Detail)PricingAdjBatchJobLogPricing Adjustment Batch
Job Log (Internal)
Configuration
ProcedurePlanDefinitionProcedure Plan Definition
(Internal)
Configuration
ProcedurePlanDefinition
(Master-Detail)
ProcedurePlanDefinitionVersionProcedure Plan Definition
Version (Internal)
Configuration
ProcedurePlanOption
(Master-Detail),
ProcedurePlanCriterionProcedure Plan Criterion
(Internal)
Configuration
DecisionTableParameter (Foreign
Key)
ProcedurePlanSection
(Master-Detail),
ProcedurePlanOptionProcedure Plan Option
(Internal)
Configuration
ExpressionSetDefinition (Foreign
Key), DecisionTable (Foreign Key),
DecisionTableParameter (Foreign
Key), DecisionTableParameter
(Foreign Key),
DecisionTableParameter (Foreign
Key), ApexClass (Foreign Key)
ProcedurePlanDefinitionVersion
(Master-Detail)
ProcedurePlanVariableProcedure Plan Variable
(Internal)
Configuration
ProcedurePlanDefinitionVersion
(Master-Detail)
ProcedurePlanSectionProcedure Plan Section
(Internal)
Configuration
SEE ALSO:
Revenue Cloud Developer Guide: Salesforce Pricing Standard Objects
Explore the Revenue Cloud Data Model
Product Configurator Objects
This table provides the object deployment sequence and properties for Product Configurator in Revenue Cloud, including object types,
API names, deployment sequences, and lookup fields.
25
Product Configurator ObjectsRevenue Cloud Deployment

===== PAGE 40 =====

Lookup Fields (Foreign
Keys)
Deployment
Sequence
Object APIObject NameObject Use
Type
User1ProductConfigurationRuleProduct Configuration RuleConfiguration
UserFlowIdentifier1ProductConfigurationFlowProduct Configuration FlowConfiguration
ExpressionSetId,
ReferenceObjectId
(Polymorphic)
1ExpressionSetConstraintObjExpressionSetConstraintObjConfiguration
User, ProductId,
ProductClassificationId,
ProductConfigurationFlow
2ProductConfigFlowAssignmentProduct Configuration Flow
Assignment
Configuration
Transaction Management Objects
This table provides the deployment sequence, object types, and API names for Transaction Management objects in Revenue Cloud.
Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
Order, Quote, Contract, Asset1AppUsageAssignmentApp Usage AssignmentMetadata
PricingProcedure1SalesTransactionTypeSales Transaction TypeMetadata
None1QuoteTemplateRichTextDataQuote Template Rich Text
Data
Metadata
None1TransactionProcessingTypeTransaction Processing
Type
Metadata
SEE ALSO:
Revenue Cloud Developer Guide: Transaction Management Standard Objects
Explore the Revenue Cloud Data Model
Dynamic Revenue Orchestrator Objects
This table provides the deployment sequence, object types, API names, and lookup fields for Dynamic Revenue Orchestrator objects in
Revenue Cloud.
Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
None1FulfillmentStepDefinitionGroupFulfillment Step
Definition Group
Configuration
Ruleset, ExpressionSet,
FulfillmentStepDefinitionGroup,
2FulfillmentStepDefinitionFulfillment Step
Definition
Configuration
IntegrationProviderDef, User,
Queue
26
Transaction Management ObjectsRevenue Cloud Deployment

===== PAGE 41 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
FulfillmentStepDefinition3FulfillmentStepDependencyDefFulfillment Step
Dependency Definition
Configuration
FulfillmentStepDefinitionGroup,
Ruleset, Product2,
4ProductFulfillmentScenarioProduct Fulfillment
Scenario
Configuration
ProductClassification,
FlowDefinition, StageDefinition,
FlowRecord, FlowOrchestration
None5FulfillmentWorkspaceFulfillment WorkspaceConfiguration
FulfillmentWorkspace,
FulfillmentStepDefinitionGroup
6FulfillmentWorkspaceItemFulfillment Workspace
Item
Configuration
IntegrationProviderDef, Group7FulfillmentFalloutRuleFulfillment Fallout RuleConfiguration
IntegrationProviderDef8FulfillmentStepJeopardyRuleFulfillment Step Jeopardy
Rule
Configuration
Ruleset, ExpressionSet, User, Queue9FulfillmentTaskAssignmentRuleFulfillment Task
Assignment Rule
Configuration
Ruleset, Product2,
ProductClassification
1ProductFulfillmentDecompRuleProduct Fulfillment
Decomposition Rule
Configuration
None2ValTfrmGrpValue Transformation
Group
Configuration
ValTfrmGrp, AttributePicklistValue3ValTfrmValue TransformationConfiguration
ProductFulfillmentDecompRule,
ExpressionSet, AttributeDefinition,
4ProductDecompEnrichmentRuleProduct Decomposition
Enrichment Rule
Configuration
ValTfrmGrp,
DecisionMatrixDefinition
ProductDecompEnrichmentRule,
AttributeDefinition
5ProdtDecompEnrchVarMapProduct Decomposition
Enrichment Variable
Mapping
Configuration
SEE ALSO:
Revenue Cloud Developer Guide: Dynamic Revenue Orchestrator Standard Objects
Explore the Revenue Cloud Data Model
Usage Management Objects
This table provides the deployment sequence, object types, API names, and lookup fields for Usage Management objects in Revenue
Cloud.
27
Usage Management ObjectsRevenue Cloud Deployment

===== PAGE 42 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
None1UsageResourceBillingPolicyUsage Aggregation PolicyConfiguration
None2UsageGrantRolloverPolicyUsage Grant Rollover
Policy
Configuration
None3UsageGrantRenewalPolicyUsage Grant Renewal
Policy
Configuration
None4UsageOveragePolicyUsage Overage PolicyConfiguration
None5UsageCommitmentPolicyUsage Commitment
Policy
Configuration
None6RateCardRate CardConfiguration
UnitOfMeasure,
UnitOfMeasureClass, Product2,
UsageResourceBillingPolicy
7UsageResourceUsage ResourceConfiguration
PriceBook2, RateCard8PriceBookRateCardPrice Book Rate CardConfiguration
Product2, UsageResource9RatingFrequencyPolicyRating Frequency PolicyConfiguration
Product2, UsageResource10ProductUsageResourceProduct Usage ResourceConfiguration
RateCard, UnitOfMeasure,
UnitOfMeasureClass,
11RateCardEntryRate Card EntryConfiguration
UsageResource, Product2,
ProductSellingModel
UsageResource,
UsageOveragePolicy,
12UsageResourcePolicyUsage Resource PolicyConfiguration
RatingFrequencyPolicy,
UsageResourceBillingPolicy,
UsageCommitmentPolicy
ProductUsageResource,
UnitOfMeasure,
13ProductUsageGrantProduct Usage GrantConfiguration
UnitOfMeasureClass,
UsageGrantRolloverPolicy,
UsageGrantRenewalPolicy,
Product2, ProductSellingModel
ProductUsageResource,
UsageOveragePolicy,
14ProductUsageResourcePolicyProduct Usage Resource
Policy
Configuration
RatingFrequencyPolicy,
UsageResourceBillingPolicy,
UsageCommitmentPolicy,
ProductSellingModel
RateCardEntry15RateAdjustmentByTierRate Adjustment By TierConfiguration
28
Usage Management ObjectsRevenue Cloud Deployment

===== PAGE 43 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
RateCardEntry,
AttributeBasedAdjRule
16RateAdjustmentByAttributeRate Adjustment By
Attribute
Configuration
SEE ALSO:
Revenue Cloud Developer Guide: Usage Management Standard Objects
Explore the Revenue Cloud Data Model
Billing Objects
This table provides the deployment sequence, object types, API names, and lookup fields for Billing objects in Revenue Cloud.
Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
None1ProfileProfileConfiguration
None2UserUserConfiguration
None3UserRoleUser RoleConfiguration
None4LegalEntityLegal EntityConfiguration
None5BillingPolicyBilling PolicyConfiguration
LegalEntity, BillingPolicy6BillingTreatmentBilling TreatmentConfiguration
BillingTreatment7BillingTreatmentItemBilling Treatment ItemConfiguration
ApexAdapter8TaxEngineProviderTax Engine ProviderConfiguration
NamedCredential,
TaxEngineProvider
9TaxEngineTax EngineConfiguration
None10TaxPolicyTax PolicyConfiguration
TaxEngine, TaxPolicy11TaxTreatmentTax TreatmentConfiguration
Product212TaxTreatmentItemTax Treatment ItemConfiguration
None13PaymentTermPayment TermConfiguration
PaymentTerm14PaymentTermItemPayment Term ItemConfiguration
None15AccountingPeriodAccounting PeriodConfiguration
LegalEntity, AccountingPeriod16LegalEntityAccountingPeriodLegal Entity Accounting
Period
Configuration
LegalEntity17GeneralLedgerAccountGeneral Ledger AccountConfiguration
LegalEntity, GeneralLedgerAccount18GeneralLedgerAcctAsgntRuleGeneral Ledger Account
Assignment Rules
Configuration
29
Billing ObjectsRevenue Cloud Deployment

===== PAGE 44 =====

Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
None19PaymentSchedulePolicyPayment Schedule PolicyConfiguration
PaymentSchedulePolicy20PaymentScheduleTreatmentPayment Schedule
Treatment
Configuration
PaymentScheduleTreatment,
PymtSchdDistributionMethod
21PaymentScheduleTreatmentDtlPayment Schedule
Treatment Detail
Configuration
None22PymtSchdDistributionMethodPayment Schedule
Distribution Method
Configuration
BillingTreatment23BillingMilestonePlanBilling Milestone PlanConfiguration
BillingMilestonePlan24BillingMilestonePlanItemBilling Milestone Plan
Item
Configuration
GeneralLedgerAccount,
GeneralLedgerAcctAsgntRule
25GeneralLedgerJrnlEntryRuleGeneral Ledger Journal
Entry Rule
Configuration
PaymentGateway26PaymentRetryRulePayment Retry RuleConfiguration
None27PaymentRetryRuleSetPayment Retry Rule SetConfiguration
None28BillingArrangementBilling ArrangementConfiguration
Account, BillingAccount29BillingArrangementLineBilling Arrangement LineConfiguration
SEE ALSO:
Revenue Cloud Developer Guide: Billing Standard Objects
Explore the Revenue Cloud Data Model
Salesforce Contracts Objects
This table provides the deployment sequence, object types, API names, and lookup fields for Salesforce Contracts in Revenue Cloud.
Lookup Fields (Foreign Keys)Deployment
Sequence
Object APIObject NameObject Use
Type
None1ClauseCatgConfigurationClause Category
Configuration
Metadata
ClauseCatgConfiguration2DocumentClauseSetDocument Clause SetConfiguration
DocumentClauseSet,
ContentDocument
3DocumentClauseDocument ClauseConfiguration
Metadata Deployment Reference
Get to know the metadata deployment sequence and associated details.
30
Salesforce Contracts ObjectsRevenue Cloud Deployment

===== PAGE 45 =====

Product Catalog Management Metadata
This table provides the metadata deployment reference for Product Catalog Management in Revenue Cloud, including setup paths
and configuration details.
Salesforce Pricing Metadata
This table provides the metadata deployment reference for Salesforce Pricing in Revenue Cloud, including setup paths and configuration
details.
Product Configurator Metadata
This table provides the metadata deployment reference for Product Configurator in Revenue Cloud, including setup paths and
configuration details.
Transaction Management Metadata
This table provides the metadata deployment reference for Transaction Management in Revenue Cloud, including setup paths and
configuration details.
Dynamic Revenue Orchestrator Metadata
This table provides the metadata deployment reference for Dynamic Revenue Orchestrator (DRO) in Revenue Cloud, including setup
paths and configuration details.
Usage Management Metadata
This table provides the metadata deployment reference for Usage Management in Revenue Cloud, including setup paths and
configuration details.
Billing Metadata
This table provides the metadata deployment reference for Billing in Revenue Cloud, including setup paths and configuration details.
Industries Common Component Metadata
This table provides the metadata deployment reference for Industries common components in Revenue Cloud, including setup
paths and configuration details.
Salesforce Contracts Metadata
This table provides the metadata deployment reference for Salesforce Contracts in Revenue Cloud, including setup paths and
configuration details.
Product Catalog Management Metadata
This table provides the metadata deployment reference for Product Catalog Management in Revenue Cloud, including setup paths and
configuration details.
DetailsSetup PathLabelType
Prerequisite: Omnistudio
Managed package must
be installed.
Setup > Apps > Packaging > Installed PackagesOmnistudio SettingsSetup
DisableSetup > Feature Settings > Omni interaction >
Omnistudio Settings
Managed Package RuntimeFlag
EnableSetup > Feature Settings > Omni interaction >
Omnistudio Settings
Define Custom Lightning Web
Components in Standard
Runtime
Flag
Prerequisite: Enable
guided product selection
Setup > Discovery FrameworkDiscovery FrameworkSetup
31
Product Catalog Management MetadataRevenue Cloud Deployment

===== PAGE 46 =====

DetailsSetup PathLabelType
through this path. Setup>
Product Discovery >
Product Discovery
Settings- > Guided
Product Selection
EnableSetup > Discovery Framework > General SettingsDiscovery FrameworkFlag
EnableSetup > Discovery Framework > General SettingsImport & ExportFlag
Enable. Also, refer to these
steps.
Setup > Discovery Framework > General SettingsSample TemplatesFlag
• In the Sample
Templates section,
click the Discovery
Framework Sample
Template page link.
The Discovery
Framework Sample
Templates page
appears.
• Click Deploy if not
already deployed.
Procedure Plan Setup > Procedure Plan DefinitionsProcedure Plan DefinitionSetup
Setup> Product Discovery > Product Discovery
Settings
Product Discovery SettingsSetup
Setup> Product Discovery > Product Discovery
Settings
Select Context DefinitionField
Setup> Product Discovery > Product Discovery
Settings
Select Pricing ProcedureField + Flag
Setup> Product Discovery > Product Discovery
Settings
Select Qualification ProcedureField + Flag
Setup> Product Discovery > Product Discovery
Settings
Select a Custom Flow for
Browsing and Adding Products
in Revenue Cloud
Field
Setup> Product Discovery > Product Discovery
Settings
Select Default CatalogField
Setup> Product Discovery > Product Discovery
Settings
Product Field SearchFlag
Setup> Product Discovery > Product Discovery
Settings
Use Indexed Data for Product
Listing and Search
Flag
32
Product Catalog Management MetadataRevenue Cloud Deployment

===== PAGE 47 =====

DetailsSetup PathLabelType
Setup> Product Discovery > Product Discovery
Settings
Dynamic Product FacetsFlag
Setup> Product Discovery > Product Discovery
Settings
Semantic SearchFlag
Setup> Product Discovery > Product Discovery
Settings
Guided Product SelectionFlag
Setup> Product Discovery > Product Discovery
Settings
Generate Product Descriptions
with Einstein AI
Flag
Setup> Product Discovery > Product Discovery
Settings
Product Catalog Management
Cache
Flag
Setup > Users > Permission SetsProduct Catalog Management
Customer Community User
Permission Sets
Setup > Users > Permission SetsProduct Catalog Management
Partner Community User
Permission Sets
Setup > Users > Permission SetsProduct Catalog Management
Cache
Permission Sets
Setup > Users > Permission SetsProduct Discovery AdminPermission Sets
Setup > Users > Permission SetsProduct Discovery UserPermission Sets
Setup > Users > Permission SetsProductImport APIPermission Sets
Setup > Users > Permission SetsDecimalQuantityDesigntimePermission Sets
Setup > Users > Permission SetsDecimalQuantityRuntimePermission Sets
Data Processing Engine
(DPE) is included. Data
Setup > Users > Permission SetsAdvanced CSV Data ImportPermission Sets
Cloud is licensed and
deployed separately.
Setup > Users > Permission SetsBasic CSV Data ImportPermission Sets
Setup > Users > Permission SetsContext Service AdminPermission Sets
Setup > Users > Permission SetsContext Service RuntimePermission Sets
Setup > Users > Permission SetsFulfillment DesignerPermission Sets
Setup > Users > Permission SetsOmnistudio AdminPermission Sets
Setup > Users > Permission SetsOmnistudio UserPermission Sets
Supports Flow version,
activation, and
deactivation
Setup > FlowDiscover ProductsFlow
33
Product Catalog Management MetadataRevenue Cloud Deployment

===== PAGE 48 =====

DetailsSetup PathLabelType
Supports Omniscript
version, activation, and
deactivation
All Apps > OmnistudioProductGuidedSelectionIntegrationOmniscript
Setup > Decision TableProductQualificationDTDecision Table
Definition
Setup > Decision TableProductDisqualificationQualificationDTDecision Table
Definition
Setup > Decision TableProductCategoryQualificationDTDecision Table
Definition
Setup > Decision TableProductCategory
DisqualificationQualificationDT
Decision Table
Definition
Salesforce Pricing Metadata
This table provides the metadata deployment reference for Salesforce Pricing in Revenue Cloud, including setup paths and configuration
details.
DetailsSetup PathLabelType
Enable. This is a
prerequisite to
Context Service > Context Service SettingsContext ServiceSetup
Salesforce Pricing
settings.
EnableSetup > Salesforce Pricing > Salesforce Pricing SettingsSalesforce Pricing SettingsSetup
Setup > Salesforce Pricing > Pricing RecipesPricing RecipesSetup
Setup > Salesforce Pricing > Salesforce Pricing SetupSalesforce Pricing SetupSetup
Setup > Salesforce Pricing > Salesforce Pricing SetupSelect a Pricing RecipeField
Setup > Salesforce Pricing > Salesforce Pricing SetupSelect a Pricing ProcedureField
Decision tables are
refreshed.
Setup > Salesforce Pricing > Salesforce Pricing SetupSync Pricing DataFlag
Setup > Salesforce Pricing > Salesforce Pricing SetupActivate Price Waterfall for API
Responses
Flag
Setup > Salesforce Pricing > Salesforce Pricing SetupTurn On Price Waterfall
Persistence
Flag
Includes two fields of
type flag. 1. Enable
Setup > Salesforce Pricing > Salesforce Pricing SetupPrice Tracking HistoryField
Maximum Price 2.
Enable Minimum Price
34
Salesforce Pricing MetadataRevenue Cloud Deployment

===== PAGE 49 =====

DetailsSetup PathLabelType
Includes two fields of
type field. 1. Evergreen
2. One Time
Setup > Salesforce Pricing > Salesforce Pricing SetupProration SettingsField
Setup > Salesforce Pricing > Salesforce Pricing SetupTurn On Price Logs CaptureFlag
Setup > Salesforce Pricing > Salesforce Pricing SetupTurn on Parallel ExecutionFlag
For Procedure Plan
definitions, if Apex is
Procedure Plan Setup > Procedure Plan DefinitionsProcedure Plan DefinitionSetup
selected, the Apex
class must be
migrated. Packaging
isn't supported in
Winter' 26. See
Customize Your
Procedure Plans With
Apex Hooks.
Setup > Users > Permission SetsSalesforce Pricing AdminPermission Sets
Setup > Users > Permission SetsSalesforce Pricing Design Time
User
Permission Sets
Setup > Users > Permission SetsSalesforce Pricing ManagerPermission Sets
Setup > Users > Permission SetsSalesforce Pricing Run Time
User
Permission Sets
Setup > Decision TableAsset Action Source EntriesDecision Table
Definition
Setup > Decision TableAsset Action Source Entries V2Decision Table
Definition
Setup > Decision TableAttribute Discount EntriesDecision Table
Definition
Setup > Decision TableBundle Based Adjustment
Entries
Decision Table
Definition
Setup > Decision TableContract Pricing Adjustment
Tiers
Decision Table
Definition
Setup > Decision TableContract Pricing EntriesDecision Table
Definition
Setup > Decision TableContract Pricing Volume TiersDecision Table
Definition
Setup > Decision TableContract Pricing Volume Tiers
V2
Decision Table
Definition
35
Salesforce Pricing MetadataRevenue Cloud Deployment

===== PAGE 50 =====

DetailsSetup PathLabelType
Setup > Decision TableDerived Pricing EntriesDecision Table
Definition
Setup > Decision TableIndex RateDecision Table
Definition
Setup > Decision TablePrice Book EntriesDecision Table
Definition
Setup > Decision TablePrice Book Entries V2Decision Table
Definition
Setup > Decision TablePricebook Rate Card EntriesDecision Table
Definition
Setup > Decision TableProduct Price Range EntriesDecision Table
Definition
Setup > Decision TableProduct Price Range Entries V2Decision Table
Definition
Setup > Decision TableTiered Adjustment EntriesDecision Table
Definition
Setup > Decision TableVolume Discount EntriesDecision Table
Definition
Product Configurator Metadata
This table provides the metadata deployment reference for Product Configurator in Revenue Cloud, including setup paths and configuration
details.
CommentsSetup PathLabelType
Enable (prerequisite to Product
Configurator).
Context Service > Context Service SettingsContext ServiceSetup
Setup > Feature Settings > Revenue Cloud >
Revenue Settings
Configure Products at RuntimeSetup
Standard Configurator
Prerequisite: Create a Rule Library
Setup > Feature Settings > Revenue Cloud >
Revenue Settings
Set Up Configuration Rules with
Business Rules Engine
Setup
Version (Set Up Configurator
With Business Rules Engine)
Setup > Feature Settings > Revenue Cloud >
Revenue Settings
Set Up Configuration Rules and
Constraints with Constraints
Engine
Setup
If both Business Rules Engine
and Constraint Builder are
Setup > Feature Settings > Revenue Cloud >
Revenue Settings
Transaction processing for
quotes and orders
Setup
enabled in the org,
36
Product Configurator MetadataRevenue Cloud Deployment

===== PAGE 51 =====

CommentsSetup PathLabelType
ConstraintBuilder is used.
Exception is Transaction
Processing Type on Quotes and
Orders override.
Setup > Feature Settings > Revenue Cloud >
Revenue Settings
Set Up Asset Context for Product
Configurator
Setup
Prerequisite for Constraint
Builder.
Setup > Object Manager > Quote Line ItemConstraintEngineNodeStatus
(Text Area (Long), length 5000)
Custom Field
Prerequisite for Constraint
Builder.
Setup > Object Manager > Order ProductConstraintEngineNodeStatus
(Text Area (Long), length 5000)
Custom Field
Prerequisite for Constraint
Builder.
Setup > Object Manager > Asset Action SourceConstraintEngineNodeStatus
(Text Area (Long), length 5000)
Custom Field
Map the three custom fields,
which are mentioned in the
Setup > Feature Settings > Context Definitions
> [Context]
ConstraintEngineNodeStatusContext
Mapping
previous rows, with the
ConstraintEngineNodeStatus tag.
Setup > Users > Permission SetsProduct ConfiguratorPermission Set
Prerequisite for Business Rules
Engine Configurator.
Setup > Users > Permission SetsProduct Configuration Rules
Designer
Permission Set
Prerequisite for Constraint
Builder.
Setup > Users > Permission SetsProduct Configuration
Constraints Designer
Permission Set
Supports Flow version, and
activation or deactivation. Other
Flows can be created.
Setup > FlowDefault Product Configurator
Flow
Flow
Transaction Management Metadata
This table provides the metadata deployment reference for Transaction Management in Revenue Cloud, including setup paths and
configuration details.
Setup PathLabel
App Usage Type
Transaction Processing Type
Setup > Revenue Cloud > Revenue SettingsRevenueManagement
Setup > Revenue Cloud > Revenue SettingsIncludeEstTaxInQuoteCPQ
Setup > Feature Settings > Sales > Quotes > Quote SettingsQuote
Setup > Feature Settings > Sales > Order SettingsOrder
37
Transaction Management MetadataRevenue Cloud Deployment

===== PAGE 52 =====

Setup PathLabel
Setup > Revenue Cloud > Revenue SettingsLargeQuotesandOrdersForRlm
User UI Preference
Dynamic Revenue Orchestrator Metadata
This table provides the metadata deployment reference for Dynamic Revenue Orchestrator (DRO) in Revenue Cloud, including setup
paths and configuration details.
DetailsSetup PathLabelType
Setup > Feature Settings > Dynamic Revenue OrchestratorDynamic Revenue OrchestratorSetup
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Dynamic Revenue Orchestrator Settings
Dynamic Revenue OrchestratorFlag
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Dynamic Revenue Orchestrator Settings
In-flight AmendmentsFlag
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Dynamic Revenue Orchestrator Settings
Future Dated StepsFlag
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Dynamic Revenue Orchestrator Settings
Link Task to Step SourceFlag
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Dynamic Revenue Orchestrator Settings
Fulfillment UserField
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context DefinitionField
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Sales
Transaction Header
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context field for Orchestration
Group Key (Optional)
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Sales
Transaction Item
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Sales
Transaction Item Relationship
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Sales
Transaction Item Attribute
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Fulfillment
Transaction
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Fulfillment
Transaction Item
Field
38
Dynamic Revenue Orchestrator MetadataRevenue Cloud Deployment

===== PAGE 53 =====

DetailsSetup PathLabelType
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Fulfillment
Transaction Item Relationship
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Fulfillment
Transaction Item Attribute
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Sales Transaction Context Definition)
Context Node for Fulfillment
Transaction Item Source
Relationship
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Fulfillment Asset Context Definition)
Context DefinitionField
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Fulfillment Asset Context Definition)
Context Node for Fulfillment
Asset
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Context Definition Settings (Fulfillment Asset Context Definition)
Context Node for Fulfillment
Asset Attribute
Field
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Fallout and SLA Settings
FalloutFlag
Setup > Feature Settings > Dynamic Revenue Orchestrator >
Fallout and SLA Settings
Service Level AgreementFlag
Setup > Users > Permission SetsDRO Admin UserPermission Sets
Setup > Users > Permission SetsSubmit Transactions and
Fulfillment User
Permission Sets
Setup > Users > Permission SetsFulfillment DesignerPermission Sets
Setup > Users > Permission SetsFulfillment Manager/OperatorPermission Sets
The value of
UsageType
Procedure Plan Setup > Procedure Plan DefinitionsProcedure Plan DefinitionSetup
field is Dfo. This
is used to define
an alternate
context mapping
for sales
transaction
context in an
order submission
flow. See Submit
Orders for
Decomposition
and Order
Fulfillment
Enables user to
submit and
Submit Transactions and
Orchestrate User
User
Permission
orchestrate
39
Dynamic Revenue Orchestrator MetadataRevenue Cloud Deployment

===== PAGE 54 =====

DetailsSetup PathLabelType
transactions for
any object by
using Dynamic
Revenue
Orchestrator.
SEE ALSO:
Revenue Cloud Developer Guide: DynamicFulfillmentOrchestratorSettings
Usage Management Metadata
This table provides the metadata deployment reference for Usage Management in Revenue Cloud, including setup paths and configuration
details.
DetailsSetup PathLabelType
EnableContext Service > Context Service SettingsContext ServiceSetup
Enable Rate
Management.
Setup > Usage Management > Usage Management
Settings
Rate ManagementSetup
Rating Waterfall ->
Enable / Disable based
Setup > Usage Management > Rate Management SetupRating SetupSetup
on preference. Rating
Waterfall Persistence
-> Enable / Disable
based on preference.
Setup > Users > Permission SetsRate Management: AdminPermission
Sets
Setup > Users > Permission SetsRate Management: Design Time
User
Permission
Sets
Setup > Users > Permission SetsRate Management: ManagerPermission
Sets
Setup > Users > Permission SetsRate Management Run Time
User
Permission
Sets
Setup > Decision TablesBinding Object Rate Adjustment
Resolution Entries
Decision Table
Definition
Setup > Decision TablesBinding Object Rate Card Entry
Resolution Entries
Decision Table
Definition
Setup > Decision TablesRate Card Entry Resolution
Entries 2
Decision Table
Definition
40
Usage Management MetadataRevenue Cloud Deployment

===== PAGE 55 =====

DetailsSetup PathLabelType
Setup > Decision TablesRate Adjustment by Attribute
Resolution Entries
Decision Table
Definition
Setup > Decision TablesRate Adjustment by Tier
Resolution Entries
Decision Table
Definition
Setup > Decision TablesPricebook Rate Card EntriesDecision Table
Definition
Setup > Decision TablesBinding Object Volume-based
Rate Adjustment
Decision Table
Definition
Setup > Decision TablesBinding Object RateDecision Table
Definition
Setup > Decision TablesBinding Object Tier-based Rate
Adjustment
Decision Table
Definition
Setup > Decision TablesBinding Object Rate Card EntryDecision Table
Definition
Setup > Decision TablesAsset Volume-based Rate
Adjustment
Decision Table
Definition
Setup > Decision TablesAsset RateDecision Table
Definition
Setup > Decision TablesAsset Rate Card EntryDecision Table
Definition
Setup > Decision TablesAsset Tier-based Rate
Adjustment
Decision Table
Definition
Setup > Decision TablesAttribute-based Rate Adjustment
by Rate Card Entry ID
Decision Table
Definition
Setup > Decision TablesVolume-based Rate Adjustment
by Rate Card Entry ID
Decision Table
Definition
Setup > Decision TablesTier-based Rate Adjustment by
Rate Card Entry ID
Decision Table
Definition
Setup > Decision TablesRate Adjustment by Attribute
Entries 2
Decision Table
Definition
Setup > Decision TablesRate Adjustment by Tier Entries
2
Decision Table
Definition
Setup > Decision TablesRate Adjustment by Volume
Entries 2
Decision Table
Definition
Setup > Decision TablesRate Card Entries 2Decision Table
Definition
Setup > FlowsCall Rating ServiceFlow
41
Usage Management MetadataRevenue Cloud Deployment

===== PAGE 56 =====

DetailsSetup PathLabelType
Setup > FlowsCall Entitlement Refresh ServiceFlow
Setup > FlowsCreate SummaryFlow
Setup > FlowsGenerate Liable SummaryFlow
Setup > FlowsGenerate Usage Rateable
Summary
Flow
Setup > FlowsGenerate Usage SummaryFlow
Setup > FlowsOrchestrate Usage ManagementFlow
Setup > Data Processing EngineCreate Liable Summary
Template
Data
Processing
Engine
Setup > Data Processing EngineCreate Usage Summary
Template
Data
Processing
Engine
Billing Metadata
This table provides the metadata deployment reference for Billing in Revenue Cloud, including setup paths and configuration details.
DetailsSetup PathLabelType
Context Service > Context Service SettingsContext ServiceSetup
Setup > Feature Settings > Analytics > Data PipelineData PipelineSetup
Setup > Users > Permission SetsBilling AdminPermission Set
Assignment
Setup > Feature Settings > Billing > Billing SettingsEnable BillingSetup
Document GenerationSetup
Setup > Feature Settings > Billing > Billing SettingsCreate Transaction Journals for
Transactions
Setup
Setup > Feature Settings > Billing > Billing SettingsApply Credits to Posted InvoicesSetup
Enable Foreign Exchange
Transaction Journal
Setup
Setup > Feature Settings > Billing > Billing SettingsApply Credits to Posted InvoicesSetup
Setup > Feature Settings > Billing > Billing SettingsConfigure Email Delivery
Settings
Setup
Setup > Feature Settings > Billing > Billing SettingsConfigure Gapless Sequential
Numbering for Billing
Setup
42
Billing MetadataRevenue Cloud Deployment

===== PAGE 57 =====

DetailsSetup PathLabelType
Setup > Feature Settings > Billing > Billing SettingsStore Transaction Amounts in
Corporate Currency
Setup
Setup > Feature Settings > Billing > Billing SettingsCreate Payment Schedules and
Payment Schedule Items
Setup
Setup > Feature Settings > Billing > Billing SettingsShare Payment AccountsSetup
Setup > Feature Settings > Billing > Billing SettingsConvert Negative Invoice Lines
to Credit Memo Lines
Setup
Setup > Feature Settings > Billing > Billing SettingsCredit and Payment Application
Level
Setup
Setup > Feature Settings > Billing > Billing SettingsSelect Default Credit Memo FlowSetup
Setup > Users > Permission SetsData Pipeline UserPermission
Sets
Setup > Users > Permission SetsBilling AdminPermission
Sets
Setup > Users > Permission SetsContext Service AdminPermission
Sets
For Analytics
Dashboard Enabling
Setup > Users > Permission SetsTableau Next AdminPermission
Sets
For Analytics
Dashboard Enabling
Setup > Users > Permission SetsData Cloud AdminPermission
Sets
Setup > Users > Permission SetsBillingAdvanced
PaymentAdministrator
Permission
Sets
Setup > Users > Permission SetsRevenueLifecycle
ManagementBilling
CustomerService
Permission
Sets
Setup > Users > Permission SetsBillingAdvancedPaymentOperationsPermission
Sets
Setup > Users > Permission SetsRevenueLifecycle
ManagementBillingCreditMemo
Operations
Permission
Sets
Default Invoice TemplateSetup
FX Gain/Loss Account LookupsSetup
Context DefinitionSetup
Context MappingSetup
Intra Context Custom MappingSetup
43
Billing MetadataRevenue Cloud Deployment

===== PAGE 58 =====

DetailsSetup PathLabelType
Default DPE Definition to Close
Legal Entity Accounting Periods
Setup
Default Invoice Preview
Template
Setup
Default Invoice Email TemplateSetup
Default Credit Memo FlowSetup
Industries Common Component Metadata
This table provides the metadata deployment reference for Industries common components in Revenue Cloud, including setup paths
and configuration details.
DetailsSetup PathLabelType
EnableContext Service > Context Service SettingsContext ServiceSetup
Data Pipeline UserSetup > Users > Permission SetsPermission SetsPermission Sets
Data Cloud AdminSetup > Users > Permission SetsPermission SetsPermission Sets
Read permission to the
user who is creating the
v{}/tooling/sobjects/BatchCalcJobDefinitiondatasources -> sourceNameData Processing
Engine (DPE)
Definition Data Processing Engine
(DPE) with the data
sources and fields.
Read permission to the
Analytics Integration User
v{}/tooling/sobjects/BatchCalcJobDefinitiondatasources -> sourceNameData Processing
Engine (DPE)
Definition with the data sources and
fields.
Create, update, or delete
permission on the
v{}/tooling/sobjects/BatchCalcJobDefinitionwritebacks ->
targetObjectName
Data Processing
Engine (DPE)
Definition targetObjectName object
based on the
operationType value
defined in the writebacks.
Delete this value if it
exists.
v{}/tooling/sobjects/BatchCalcJobDefinitionwritebacks -> writebackUserData Processing
Engine (DPE)
Definition
Salesforce Contracts Metadata
This table provides the metadata deployment reference for Salesforce Contracts in Revenue Cloud, including setup paths and configuration
details.
44
Industries Common Component MetadataRevenue Cloud Deployment

===== PAGE 59 =====

Setup PathLabelType
Setup > Document Generation > General SettingsDocument Templates ExportFlag
Context Service > Context Service Settings > Context DefinitionsContext ServiceSetup
Additional Deployment Information
Get to know additional deployment information for each Revenue Cloud feature domain, ensuring successful deployments and migrations.
Product Catalog Management Additional Information
Get to know additional deployment information for Product Catalog Management in Revenue Cloud, including active or inactive
states, object information, and migration considerations.
Salesforce Pricing Additional Information
Get to know additional deployment information for Salesforce Pricing in Revenue Cloud, including active or inactive states, object
information, and migration considerations.
Product Configurator Additional Information
Get to know additional deployment information for Product Configurator in Revenue Cloud, including active or inactive states, object
information, and migration considerations.
Dynamic Revenue Orchestrator Additional Information
Get to know additional deployment information for Dynamic Revenue Orchestrator (DRO) in Revenue Cloud, including active or
inactive states, object information, and migration considerations.
Usage Management Additional Information
Get to know additional deployment information for Usage Management in Revenue Cloud, including active or inactive states, object
information, and migration considerations.
Billing Additional Information
Get to know additional deployment information for Billing in Revenue Cloud, including active or inactive states, object information,
and migration considerations.
Business Rules Engine and Decision Tables Additional Information
Get to know additional Revenue Cloud deployment information for Industries common features such as Business Rules Engine,
Expression Sets, and Decision Tables.
Context Service Additional Information
Get to know additional deployment information for Context Service in Revenue Cloud.
Data Processing Engine Additional Information
Get to know additional deployment information for Data Processing Engine in Revenue Cloud.
Salesforce Contracts Additional Information
Get to know additional deployment information for Salesforce Contracts in Revenue Cloud, including active or inactive states, and
migration considerations.
Product Catalog Management Additional Information
Get to know additional deployment information for Product Catalog Management in Revenue Cloud, including active or inactive states,
object information, and migration considerations.
45
Additional Deployment InformationRevenue Cloud Deployment

===== PAGE 60 =====

Object-Specific Information
NotesObject APIObject Name
ProductQualificationProduct Qualification • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
ProductDisqualificationProduct Disqualification • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
ProductCategoryQualificationProduct Category Qualification • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
ProductCategoryDisqualProduct Category Disqualification • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
Other Information
• All product data (product, class, product attributes, attributes, picklist, catalog, categories, and so on) definitions must be active to
appear in the sales channels.
– These definitions need not be deactivated in the target to propagate updates as part of an org-to-org deployment. Exceptions
are qualification rules that use decision tables, expression sets, and context definitions. The definitions in the target org must be
deactivated to promote changes.
• Use the Full Index Rebuild to rebuild the entire search index, when enabling the feature for the first time, or changing the index
settings. Use the Partial Index Rebuild to update recent changes to products and categories assignment. For more information about
indexing products, see Manage Your Product Index.
– If indexing is enabled in source but not enabled in the target, then while deploying the indexing flag (enable indexed
product=true), the Full indexing must be run on the target org before the feature flag can be enabled.
• Migrating qualification rules records requires refreshing Qualification Rules Decision Table definitions (Product and Category
Qualification and Disqualification Decision Tables).
• Migrating price book Entries requires Decision Table refresh for Product Discovery to show list price.
46
Product Catalog Management Additional InformationRevenue Cloud Deployment

===== PAGE 61 =====

• Core to Near Core Sync Processes— Configure Product Catalog Management Cache in the new org to populate the product details
cache, essential for large-scale implementations.
• Cross-Module Synchronization—Synchronization of catalog date to Constraint Modeling Language (CML) to support constraint
rules.
• Incremental Changes and cohesive Sync (Recommended)—Depending on the deployment scenario, for example, new or changed
product, new or changed price, new price book, new or changed rules, and so on.
Salesforce Pricing Additional Information
Get to know additional deployment information for Salesforce Pricing in Revenue Cloud, including active or inactive states, object
information, and migration considerations.
Object-Specific Information
NotesObject APIObject Name
AttributeBasedAdjustmentAttribute Based Adjustment • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
PriceAdjustmentTierPrice Adjustment Tier • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
BundleBasedAdjustmentBundle Based Adjustment • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
ProductPriceRangeProduct Price Range • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
47
Salesforce Pricing Additional InformationRevenue Cloud Deployment

===== PAGE 62 =====

Other Information
• You need active context definitions for pricing recipes. A pricing recipe is marked as default in an org. A System Admin can access
the PricingRecipe object whereas a Pricing Admin can't access this object internally. You can’t create or update fields of a PricingRecipe
object.
• You must activate decision tables and pricing procedures.
• You need a refresh of the decision table for any new or modified records. For example, any modification in price book entries requires
a refresh of the Price Book Entries decision table.
• You must migrate the Apex class if Apex is selected for Procedure Plan definitions. See Customize Your Procedure Plans with Apex
Hooks.
• You can’t delete a standard price book. A price book can be deleted after all references are removed. Instead, set the price book to
Inactive status.
• If you delete a price adjustment schedule, all associated data is deleted without any warning or error messages. The adjustment
method and status of a price adjustment schedule aren’t considered for resolution. If you edit or delete an active price adjustment
schedule, an error is thrown.
• The EffectiveFrom and EffectiveTo field values of a price adjustment tier, attribute-based adjustment, and bundle-based adjustment
must be within the EffectiveFrom and EffectiveTo field values.
• Product and product selling model must be a part of the product selling model option before you create values in a price book entry.
• You can’t delete an inactive or active product selling model. You can delete a draft product selling model by deleting all references.
You can’t change status from Active or Inactive to Draft.
• You can’t edit a product price range after you've created it. Enable price tracking to edit a product price range.
• Salesforce Pricing doesn’t consider the Active status of a price book when fetching the values. Also, it doesn't consider the validity
date ranges of a price book.
• The pricing term and pricing term unit of a price adjustment tier aren’t considered for resolution.
• The IsActive field of a price book entry and price adjustment schedule aren’t considered for resolution.
Salesforce Pricing Migration Scenarios
Review these considerations to understand the Salesforce Pricing data migration process along with migration order and prerequisites.
Salesforce Pricing Migration Scenarios
Review these considerations to understand the Salesforce Pricing data migration process along with migration order and prerequisites.
Here are the possible migration scenarios.
• One sandbox org to another sandbox org
• Sandbox org to production org
To migrate pricing procedures, see Export and Import Procedure Plans.
To import and export pricing data, see Considerations for Importing and Exporting Pricing Data. Keep these considerations in mind for
first-time migration.
First-Time Migration
• You must migrate metadata in this specific sequence to ensure a successful deployment.
– You must migrate context definitions before any pricing procedures. If multiple pricing procedures are linked to various context
definitions, include all associated definitions in the migration.
48
Salesforce Pricing Additional InformationRevenue Cloud Deployment

===== PAGE 63 =====

– You must deploy all decision tables (DTs) before you migrate the pricing procedures that reference them.
– Pricing recipe migration also migrates the associated default pricing procedure.
• You must manually refresh decision tables after migration within the target environment to make sure that the data is updated and
active. If a decision table migration encounters missing metadata, such as a custom field or element, the deployment fails.
• You must manually update any pricing procedure constants that contain reference sandbox org IDs to the corresponding production
org IDs. This step is required before migration to avoid logic failures in the production environment.
• You must manually update the price adjustment schedule IDs in the pricing procedure constants of the production org before or
after migration.
Subsequent Production Migrations
• You must migrate context definitions before you migrate pricing procedures. If multiple pricing procedures are linked to various
context definitions, then you must migrate all associated metadata to ensure system integrity.
• You must migrate decision tables along with any relevant metadata changes. If a decision table migration fails, the system must roll
back to the previous snapshot, making sure that the existing decision tables are usable.
• You must migrate pricing procedures and expression set versions after the successful deployment of context definitions, decision
tables, and pricing recipes in a sequential order.
Product Configurator Additional Information
Get to know additional deployment information for Product Configurator in Revenue Cloud, including active or inactive states, object
information, and migration considerations.
Object-Specific Information
NotesObject APIObject Name
ProductConfigurationRule has a Binary Large
Object (BLOB) for the rule content.
ProductConfigurationRuleProduct Configuration Rule
ConfigurationRuleDefinition contains a JSON
with the rules details. The BLOB references
product IDs, which can't be migrated as is.
You must use the npm migration utility for
the migration.
ProductConfigurationRule has a status field.
ProductConfigurationFlow has a status field.
You don't require an API to set the status.
ProductConfigurationFlowProduct Configuration Flow
The ExpressionSet for Constraints has a
status field. The ReferenceObjectId lookup
ExpressionSetConstraintObjExpressionSetConstraintObj
field is polymorphic and references object
IDs.
49
Product Configurator Additional InformationRevenue Cloud Deployment

===== PAGE 64 =====

Other Information
• You can't update rules in active status.
• Product catalog management data must be migrated before the associations (ExpressionSetConstraintObj) are migrated and before
the Business Rules Engine rules (ProductConfigurationRule) are migrated. When updating an Expression Set (Constraint Model), the
target must be deactivated.
• Cross-Module Synchronization—Constraint Modeling Language (CML) and Business Rules Engine rules both reference product
catalog management data. This data must be migrated before the business rules or the constraint rules.
• These components have dependencies on Industries common features.
– Business Rules Product Configuration Rules—Business Rules Engine and Context Service
– Constraint Builder Product Configuration Rules—Expression Set and Context Service
– Product Configurator—Flow
In a future version of this guide, we plan to add information for moving Constraint Modeling Language (CML) code and related expression
sets.
Dynamic Revenue Orchestrator Additional Information
Get to know additional deployment information for Dynamic Revenue Orchestrator (DRO) in Revenue Cloud, including active or inactive
states, object information, and migration considerations.
Object-Specific Information
NotesObject APIObject Name
Rule set references are created in the target
org by using UPDATE operation on the JSON
ProductFulfillmentDecompRuleProduct Fulfillment Decomposition Rule
fields as listed in the Special Fields section.
Any rule set records and references aren’t
created on INSERT operation.
Rule set references are created in the target
org by using UPDATE operation on the JSON
FulfillmentStepDefinitionFulfillment Step Definition
fields as listed in the Special Fields section.
Any rule set records and references aren’t
created on INSERT operation.
Rule set references are created in the target
org by using UPDATE operation on the JSON
ProductFulfillmentScenarioProduct Fulfillment Scenario
fields as listed in the Special Fields section.
Any rule set records and references aren’t
created on INSERT operation.
After migration, refresh the related Decision
Tables.
FulfillmentFalloutRuleFulfillment Fallout Rule
Rule set references are created in the target
org by using UPDATE operation on the JSON
FulfillmentTaskAssignmentRuleFulfillment Task Assignment Rule
50
Dynamic Revenue Orchestrator Additional InformationRevenue Cloud Deployment

===== PAGE 65 =====

NotesObject APIObject Name
fields as listed in the Special Fields section.
Any rule set records and references aren’t
created on INSERT operation.
This setup object is always active after
creation. Here are some considerations.
OrchestrationPlanCtxMappingOrchestration Plan Context Mapping
• The object must have an active context
definition to create the mapping.
• The context definition must remain
active for the mapping to be valid.
• Context nodes or referenced mappings
must exist in the active context
definition version.
Special Fields
• These objects use a large text field to contain a JSON representation of Dynamic Revenue Orchestrator (DRO) condition data, backed
up by internal Business Rules Engine (BRE) RuleSet objects.
– FulfillmentStepDefinition
• ExecuteOnConditionData. This is related to ExecuteOnRule field (RuleSet reference).
• ResumeOnConditionData. This is related to ResumeOnRule field (RuleSet reference).
– ProductFulfillmentScenario
• ConditionData. This is related to ScenarioRule field (RuleSet reference).
– ProductFulfillmentDecompRule
• ConditionData. This is related to ExecuteOnRule field (RuleSet reference).
– FulfillmentTaskAssignmentRule
• ConditionData. This is related to Condition field (RuleSet reference).
Other Information
• Migration Prerequisites
– When DRO is enabled in a new org, the system provides an built-in library named as DRORuleLibrary. See Dynamic Fulfillment
Orchestrator Settings.
– Context rules library is Active with Usage Type=Dfo  and is linked with Sales Context Definition.
– The active rule library version must point to the context definition currently configured in the DRO Admin settings. If you change
the context definition in the settings, you must create a new rule library version that links to the new definition and activate it.
When creating a version, you must clone from the latest rule library version. If you clone from an older version instead of the
latest, any rule sets created in the latest version is lost in any other newly created version. This leads to evaluation errors where
rules evaluate to false  as the engine is unable to find the rule set in the active library.
When moving to a new version, you must first deactivate the older version and then activate the cloned version.
51
Dynamic Revenue Orchestrator Additional InformationRevenue Cloud Deployment

===== PAGE 66 =====

– Context definitions must have the necessary nodes, mappings, and context tags used in rule sets.
– DRO rules include Product Fulfillment Decomposition Rule, Fulfillment Step Definition, Product Fulfillment Scenario, and Fulfillment
Task Assignment Rule objects. To migrate DRO rules or scenarios, make sure the AttributeDefinition and AttributePicklistValue
records are referenced in condition data fields by attribute code and picklist value name in the org before migration. The code
value is defined in product management records.
– The SourceAttributeIdentifier and DestinationAttributeIdentifier fields of a ProductDecompEnrichmentRule record can include
attribute IDs from the source org, leading to invalid references in the target org. Refresh the identifier fields by saving the
ProductDecompEnrichmentRule records again. You can also set the identifier fields to null during migration to make sure that
they auto-populate correctly.
– Before you can migrate the Product Fulfillment Decomposition Rule, Fulfillment Step Definition, Product Fulfillment Scenario,
and Fulfillment Task Assignment Rule objects with their related child records, several other key records must exist in the target
Salesforce org. Migrating these records first is crucial to maintain data integrity and to make sure that the relationships are
correctly established in rules.
Here are the required records in the target org as per the required migration sequence.
• Products (Product2)—The top-level ProductFulfillmentDecompRule record is directly linked to a specific product via the
ProductId field. You can’t create the rule without associating it with an existing product record.
Make sure that the Product2 records in the source and target orgs can be uniquely identified. For example, use a custom
external ID field such as GlobalKey__c or any other ExternalId field, or use the standard ProductCode field.
• Attribute Definitions (AttributeDefinition)—The ProductDecompEnrichmentRule records, which are children of the
decomposition rule, use attribute definitions to specify which product attributes to use for enrichment or transformation.
These rules reference AttributeDefinition records in fields, such as SourceAttributeDefinitionId and TargetAttributeDefinitionId.
DRO Condition Data fields and rule sets use AttributeCode values in Condition Expressions.
Attribute Definitions must be migrated before the enrichment rules to make sure that the lookup relationships are resolved
successfully. Attribute Code values must be defined as these values are used in DRO Conditions as unique identifiers for
attribute-type expressions.
• Attribute Definition Picklist Values (AttributePicklistValue)—The ValTfrm (Value Transform) records, which are used for
mapping and transforming data, often rely on picklist values defined in the AttributePicklistValue object. These records define
the specific values used in the transformation logic. DRO Condition Data fields and rule sets use AttributeCode values in
Condition Expressions.
If your transformation rules involve picklist fields, you must migrate the corresponding AttributePicklistValue records first.
• DRO Rules and Scenario Migration
– Internal rule set tables may contain attribute ID values, which are the Salesforce IDs of the relevant AttributeDefinition records
of the Product or Product Classification.
– DRO stores rule set-related data in string representation with AttributeDefinition. During migration, the JSON representation of
a rule set uses Attribute Code as the natural key to resolve AttributeDefinition records and set as key in internal rule set tables.
As a prerequisite, make sure that attribute code values are populated and consistent in both the source and target orgs before
you migrate DRO rules.
– Rule sets also contain attribute picklist values in condition expressions. The AttributePicklistValue records of the associated
AttributeDefinition records must exist in target org before you migrate DRO rules.
– You can’t insert a new DRO rule record with condition data. You can only update the record. In such a scenario, migrate the rule
record with an empty condition field through an INSERT operation. Then, perform an UPDATE operation on the condition field
with the JSON value from the source org.
• After Migration:
52
Dynamic Revenue Orchestrator Additional InformationRevenue Cloud Deployment

===== PAGE 67 =====

Refresh the Decision Tables (DT) used by DRO Fallout Management—Migrating the Fulfillment Fallout Rules records requires a
refreshed Fallout Rules DT definition.
–
– Refresh DTs used by DRO Jeopardy Management—Migrating the Fulfillment Step Jeopardy Rule records requires a refreshed
Fulfillment Step Jeopardy Rule DT definition.
– Make sure to activate technical products in your target org as part of your deployment.
• These components have dependencies on Industries common features:
– Enrichment Rule—Expression Set
– Decomposition Rule with condition—Business Rules Engine Context Rule and Context Service
– Callout step—Integration Definition
– Autotask step—Flow
– Manual Task step—Queue
– Product Fulfillment Scenario with condition—Business Rules Engine Context Rule and Context Service
SEE ALSO:
Bulk API 2.0 and Bulk API Developer Guide: Introduction to Bulk API 2.0 and Bulk API
Usage Management Additional Information
Get to know additional deployment information for Usage Management in Revenue Cloud, including active or inactive states, object
information, and migration considerations.
Object-Specific Information
NotesObject APIObject Name
RateCardRate Card • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
PriceBookRateCardPrice Book Rate Card • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
Effective end date can be extended in Active
state.
ProductUsageResourceProduct Usage Resource
RateCardEntryRate Card Entry • Considerations for Migrating Decision
Tables
53
Usage Management Additional InformationRevenue Cloud Deployment

===== PAGE 68 =====

NotesObject APIObject Name
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
• No updates are allowed in Active or
Inactive state.
The Effective End Date can be extended in
Active state.
ProductUsageGrantProduct Usage Grant
RateAdjustmentByTierRate Adjustment By Tier • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
RateAdjustmentByAttributeRate Adjustment By Attribute • Considerations for Migrating Decision
Tables
• Considerations for Migrating Expression
Sets
• Migrate Context Definitions
The RelatedObjectId lookup field is
polymorphic.
UsageCmtAssetRelatedObjUsage Commitment Asset Related Object
Other Information
• For Selling (Revenue Cloud Advanced), perform these actions:
– Confirm that Rates, Grants, and Policies for usage products are set up correctly.
– Extend and sync the SalesTransaction context definition.
– Confirm that the pricing procedure is active and set up correctly in Revenue Settings.
– Refresh Decision Tables (DT) being referred in pricing procedures.
– Set up and activate the rating discovery procedure.
– Sync the RatingDiscovery context definition.
– Refresh all Decision Tables (DTs) being used in the rating discovery procedure.
• For Consumption (Revenue Cloud Billing), perform these actions:
– Clone and set up the Orchestration Flow.
– Configure the Data Processing Engine (DPE) jobs.
– Set up and activate the rating procedure.
– Sync the Rate Management context definition.
– Refresh all Decision Tables (DTs) being used in the rating procedure.
• These components have dependencies on Industries common Features:
54
Usage Management Additional InformationRevenue Cloud Deployment

===== PAGE 69 =====

Rating or Discovery Procedures: Expression Set–
– Rating, Discovery, or Selling Journey: Business Rules Engine and Context Service
– Rating or summary creation: Batch and Data Processing Engine
• After migration, selling and consumption-related object records such as UnitOfMeasureClass, UsageResource, RateCardEntry,
ProductUsageResource, ProductUsageGrant must be active before you use it.
For ProductUsageResource and ProductUsageGrant objects, review these considerations.
• You can delete records in Draft or Inactive states. You can’t delete a record in Active state.
• After you activate a record, you can extend end date only.
• The applicable status transitions are Draft, Active, and Inactive.
You can edit a RateCardEntry object in Draft status only. You can’t edit this object after you've activated it. The applicable status transitions
are:
• Draft, Active, and Inactive
• Inactive and Active
Billing Additional Information
Get to know additional deployment information for Billing in Revenue Cloud, including active or inactive states, object information, and
migration considerations.
Object-Specific Information
NotesObject APIObject Name
This object contains a polymorphic field for
address.
LegalEntityLegal Entity
Activate after Billing Treatment is activated.BillingPolicyBilling Policy
Activate after Billing Treatment Item is
activated.
BillingTreatmentBilling Treatment
Activate first when activating Billing Policy.BillingTreatmentItemBilling Treatment Item
Activate after Tax Treatment is activated.TaxPolicyTax Policy
Activate first when activating Tax Policy.TaxTreamentTax Treatment
Activate after Payment Term Item is
activated.
PaymentTermPayment Term
Activate first when activating Payment Term.PaymentTermItemPayment Term Item
Activate after Payment Schedule Treatment
is activated
PaymentSchedulePolicyPayment Schedule Policy
Activate first when activating Payment
Schedule Policy.
PaymentScheduleTreatmentPayment Schedule Treatment
If RetryIntervalType  field value is
specified, you must also specify values for
PaymentRetryRulePayment Retry Rule
55
Billing Additional InformationRevenue Cloud Deployment

===== PAGE 70 =====

NotesObject APIObject Name
IntervalUnit  and
IntervalValue fields.
You can’t delete or modify the active
org-default rule set after the feature is
PaymentRetryRuleSetPayment Retry Rule Set
enabled. The org can’t have multiple active
org-default rule sets.
You can’t delete a tax treatment item when
the parent tax treatment is active.
TaxTreatmentItemTax Treatment Item
Other Information
• Data pipeline must be enabled before enabling Billing.
• Order to Billing Schedule Flow must be copied from the template and activated.
Business Rules Engine and Decision Tables Additional Information
Get to know additional Revenue Cloud deployment information for Industries common features such as Business Rules Engine, Expression
Sets, and Decision Tables.
Object-Specific Information
NotesObject APIObject Name
Only call the setup object via Metadata API
to get child setup objects.
ExpressionSetDefinitionExpression Set Definition
Only call the setup object via Metadata API
to get child setup objects.
ExpressionSetDefinitionVersionExpression Set Definition Version
Not supported by Metadata API.RuleLibraryRule Library
Not supported by Metadata API.RuleLibraryVersionRule Library Version
Helpful Links
• Considerations for Migrating Expression Sets
• Migration of Expression Sets with Dependencies
Deployment Considerations
• Initial Deployment—Expression Sets Decision Tables can be deployed in any state during their first deployment to a target org.
• Subsequent Updates—To update an expression set that exists in the target org, migrate a new expression set version with the
updates. You must not update the existing active version.
56
Business Rules Engine and Decision Tables Additional
Information
Revenue Cloud Deployment

===== PAGE 71 =====

• When deploying an active decision table, it goes through activation again in the target org and may fail if the required custom object
isn’t present in the target org.
• Two expression set versions of the same parent expression set can't have the same rank, regardless of the Draft  or Active
states. In this case:
– Create an expression set version in the source org with the updates.
– Activate the new version in the source org.
– Then, migrate the new version or the entire expression set to the target org.
– The migrated expression set version is invoked in the target org as per the specified rank.
– Migration fails if the target org contains an expression set version with the specified rank.
• Activate and refresh of decision tables after deployment.
• Activate sub expressions after deployment.
• Dynamic rules are stored in platform objects, and not in setup objects. There's no platform support for deploying dynamic rules.
Dependencies
• Industries common features can have dependencies among themselves. For example, expression sets can have sub expressions and
reference decision tables or context definitions. Decision Tables can have a dependency on a custom object, and so on.
• For a deployment to be successful, all dependent components must be migrated correctly before the expression set version itself.
• You must migrate dependencies before the expression sets that reference them. If there are nested dependencies, you must migrate
the lowest-level components first. Here's a general deployment order.
– Standard and custom objects
– Context Definitions, Decision Tables, Decision Matrices, Object Aliases, and Explainability Message Templates
– Sub Expression Sets
– Parent Expression Set Version
Other Information
• Both Expression Set and Decision Matrix have versioned objects.
• Decision Tables don’t have versions.
Context Service Additional Information
Get to know additional deployment information for Context Service in Revenue Cloud.
Helpful Links
• Migrate Context Definitions
Deployment Considerations
• Context tags and individual sObject mappings must be unique for every definition.
• Deployment can lead to conflict if there are multiple tags with the same name, or if there are multiple mappings to the same sObject
and sObject fields.
57
Context Service Additional InformationRevenue Cloud Deployment

===== PAGE 72 =====

• Standard definitions are versioned and new changes must have a higher version than the version, which is available in the org.
• You can deploy updates that introduce new custom nodes, attributes, and their corresponding mappings to existing context
definitions.
• Deployments that modify (update or delete) existing custom mappings for context definitions in an activated or a deactivated state
are supported.
Unsupported Deployment Scenarios
• Deploying context definitions from the current release to an older release is not supported.
• Modifying custom nodes and attributes for context definitions that are in a deactivated state aren’t supported. To make changes,
replicate your desired modifications manually on the target context definition. You can also delete the context definition on the
target org and deploy again.
• Modifying standard nodes and attributes for context definitions that are in an activated state isn't supported. To make changes,
deactivate the definition on the target org first, make your desired modifications, and then activate the context definition again.
• You can’t activate or deactivate an active context definition as an action within a deployment package. Activation or deactivation
must be performed as a separate, manual step outside the deployment process.
• You can’t make a context mapping default or non-default as an action within a deployment. Changing the default status of context
mappings must be done as a separate, manual step.
Data Processing Engine Additional Information
Get to know additional deployment information for Data Processing Engine in Revenue Cloud.
Deployment Considerations
• Data Processing Engine objects have Draft  and Active  states.
• The objects must be created in Draft  state and activated later. The activation is done through API.
• Configuration can’t be changed after an object is updated to Active  state.
• Set the state of the object to Inactive  for any modifications, and then set the state to Active.
Other Information
• Data Processing Engine has dependencies on these components.
– CRM Analytics or Data Cloud
– Bulk API
• You can deploy Data Processing Engine definitions from one organization to another. Both organizations must be on the same
Salesforce release version.
Salesforce Contracts Additional Information
Get to know additional deployment information for Salesforce Contracts in Revenue Cloud, including active or inactive states, and
migration considerations.
Document clauses can be in different states, such as Draft, In Approval, Active, and Archived. Keep these considerations in mind regarding
the clause statuses.
58
Data Processing Engine Additional InformationRevenue Cloud Deployment

===== PAGE 73 =====

• A clause is created in Draft status.
• During the import process, the clause must be in Draft status. You can update the status after you complete the import process.
• An archived clause can’t be updated.
• An active clause can’t be updated, but it can change to Draft status only if it’s not used.
• An active clause must be moved to Draft status before you update it to Active status.
Clause Migration Considerations
Clause migration is a prerequisite for Microsoft 365 template migration. Review these considerations to understand how clause
structure, versions, and relationships must exist in the target org before migrating document templates.
Clause Validations and Migration Constraints
Validation rules, data model constraints, and known migration behaviors that affect clause records during migration. Review this
reference to understand sequencing, status handling, and dependency requirements that can impact migration success.
Clause Migration Considerations
Clause migration is a prerequisite for Microsoft 365 template migration. Review these considerations to understand how clause structure,
versions, and relationships must exist in the target org before migrating document templates.
Clause migration prepares the target org with all required clause data so that template migration can resolve clause references correctly.
Clause records don’t retain source org record IDs during migration. Instead, template migration resolves references based on clause
attributes and relationships that already exist in the target org.
Clause migration requires careful sequencing and coordination because clause records enforce strict validation rules around status,
hierarchy, and versioning.
Microsoft 365 template migration requires all clause records, clause categories, and related clause sets to exist in the target org.
During template migration, clause references resolve in the target org by matching this combination of attributes. Make sure that the
target org contains clauses with the exact attribute values referenced by the Microsoft 365 template.
• ClauseSetName
• ClauseName
• ClauseVersion
• ClauseLanguage
If a referenced clause is missing in the target org, template migration stops to prevent broken references. This alignment helps maintain
template integrity and reduces the need for manual corrections after migration.
Migrate clause-related objects separately by using a data migration tool, such as Data Loader.
Migrate the three document clause objects in the required order.
• Clause Category Configuration
• Document Clause Set
• Document Clause
Important: Avoid modifying clause data in the target org after migration to prevent mismatches between source and target.
Avoid modifying clause data in the source org after exporting clause data and before Microsoft 365 template migration to prevent
reference mismatches.
59
Salesforce Contracts Additional InformationRevenue Cloud Deployment

===== PAGE 74 =====

Clause Category Configuration
Clause Category Configuration is a setup object that you migrate by using metadata deployment tools, such as Package Manager, and
Salesforce CLI. Migrate all clause categories referenced by your clause sets.
Clause Set
Clause sets must be migrated before you can migrate clauses. This needs to be either created explicitly on the target org or migrated
from the source org by using data migration utilities. Resolve these clause category configuration references to IDs on the target org in
your export set before you migrate.
• CategoryReferenceId—Replace with the mapped ID obtained from clause category migration
• Category—This is a 15-character ID of the clause category. Update CategoryReferenceId by removing the last three characters.
For iterative migrations, use upsert operation to update existing clause sets and insert newly created clause sets since the previous
migration.
Clause
Migrate clause category configuration and clause sets before initiating clause migration. Resolve the clause set references
(DocumentClauseSet) to the IDs on the target in your export set before migrating.
Important: All clauses are inserted only in Draft status, regardless of their source status. Run a subsequent migration that includes
status mapping to update the clauses to the correct status. See Clause Status Mapping During Migration on page 61.
First-Time Migration
Use this approach when migrating clause data for the first time from the source org to the destination org for Microsoft 365 template
migration. Clauses enforce validation rules that affect insert and update operations during migration.
• Insert main clauses before alternate clauses.
• Clauses are inserted in Draft status. Run a subsequent migration to update the clause status. See Clause Status Mapping During
Migration on page 61 for details on how clause statuses are applied and updated.
Iterative Migration
Use iterative migration when clause data exists in the target org and you must migrate updates or newly created clauses from the source
org. Track the timestamp of the last successful export and migrate only records that were created or updated after that timestamp. This
approach avoids validation failures when attempting to update unchanged clauses, especially clauses in Archived status.
• Migrate clause records that were modified after the last export timestamp and created on or before the last export timestamp. This
step migrates only updated records and preserves the correct status for existing clauses before introducing new draft versions.
• Migrate main clause records that were created after the last export timestamp. Clauses are inserted in Draft status. Run a subsequent
migration to update the clause status. See Clause Status Mapping During Migration on page 61 for details on how clause statuses
are applied and updated.
• Migrate alternate clause records that were created after the last export timestamp. Clauses are inserted in Draft status. Run a
subsequent migration to update the status.
Clause Validations and Migration Constraints
Validation rules, data model constraints, and known migration behaviors that affect clause records during migration. Review this reference
to understand sequencing, status handling, and dependency requirements that can impact migration success.
60
Salesforce Contracts Additional InformationRevenue Cloud Deployment

===== PAGE 75 =====

Clause Migration Validations
These validations apply during insert, update, and delete operations on clause records. Operations fail when a validation is violated.
DescriptionValidationOperation
Allows only Draft clauses during initial insert
operations.
Draft-only creationInsert
Prevents inserting a clause when a Draft
version exists for the same clause.
Version conflict preventionInsert
Requires each clause to reference a valid
DocumentClauseSet that exists in the target
org.
Clause set requirementInsert
Main and alternate clause hierarchyInsert • Requires an existing main clause before
inserting alternate clauses and allows
only one main clause per clause group.
• Allows only one main clause per
language within a clause set, and allows
multiple alternate clauses for the same
language.
Prevents updating the DocumentClauseSet,
Language, IsAlternateClause, and Version
fields after clause creation.
Restricted fieldsUpdate
Allows changing an Active clause only to
Draft (without modifying other fields) or to
Archived.
Status transition rulesUpdate
Prevents updates to Archived clauses.Archived clause immutabilityUpdate
Requires clause content before changing
status to Active.
Content requirement for activationUpdate
Allows deletion of Draft and Archived
clauses only.
Status-based deletionDelete
Prevents deleting a main clause while
alternate clauses still exist.
Main clause protectionDelete
Clause Status Mapping During Migration
Clauses insert only in Draft status, regardless of their source status. Run a subsequent migration with status mapping to update the
clause statuses. For example, a clause in the source org has three versions: Version 1 is Archived, Version 2 is Active, and Version 3 is Draft.
When the clause is inserted, all three versions are created in Draft status in the target org. Perform a follow-up upsert migration with
status mapping to align each clause version with its source org status.
61
Salesforce Contracts Additional InformationRevenue Cloud Deployment

===== PAGE 76 =====

GuidanceSource Org Status (Pre-Migration)
Archived clauses insert as Draft. Run a subsequent migration with
status mapping to restore the Archived status. After a clause is
archived, you can’t change its status.
Archived
Active clauses insert as Draft. Run a subsequent migration with
status mapping to restore the Active status.
Active
Draft clauses insert as Draft, so no status change is required.Draft
You must not migrate In Approval clauses because their workflows
don’t migrate. However, if In Approval clauses are migrated, they’re
In Approval
inserted in Draft status, and the approval process must be
reinitiated from the UI.
Clause Migration Constraints
These constraints describe behavioral rules, sequencing requirements, and tooling limitations that affect clause migration, especially
during iterative and incremental migrations.
DescriptionConstraintCategory
Requires that you use supported data
migration tools, such as Data Loader,
No automated migrationTooling
because no automated clause migration
utility exists.
Requires OAuth-based authentication.
Enforcing OAuth, Proof Key for Code
Authentication requirements for Data
Loader
Tooling
Exchange (PKCE), or IP restrictions requires
completing additional connected app and
access configuration.
Prevents adding custom fields to Clause
Category Configuration because it’s a setup
object.
Clause category limitationsData Model
Creation of an external ID field in the target
org to store source org IDs for upsert
Manual ID creationData Model
operations on clause sets and clause
records.
Requires manually mapping clause category
IDs between source and target orgs.
Manual ID mappingData Model
Requires clause sets and clause category
configuration to exist in the target org
before importing clauses.
Clause set dependencyData Dependency
62
Salesforce Contracts Additional InformationRevenue Cloud Deployment

===== PAGE 77 =====

DescriptionConstraintCategory
Requires that you update existing clauses
before you insert newly created clauses.
Migration order dependencyIterative Migration
Also, insert main clauses before alternate
clauses.
Prevents template migration when
referenced clauses, versions, or languages
don’t exist in the target org.
Missing clause referencesTemplate Dependency
Can cause clause reference mismatches
during template migration when duplicate
clauses exist in the target org.
Duplicate clausesTemplate Dependency
Can cause template migration to fail when
Office Open XML updates fail during
document import.
Office Open XML failuresTemplate Dependency
63
Salesforce Contracts Additional InformationRevenue Cloud Deployment

===== PAGE 78 =====

