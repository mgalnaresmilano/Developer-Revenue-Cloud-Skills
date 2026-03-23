---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 4 — Product Catalog Management

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 4 Product Catalog Management
Create and manage a product catalog with components, such as attributes, product classifications,
simple and bundled products, and rules.
In this chapter ...
• Product Catalog
Management
• Product Discovery
64

===== PAGE 79 =====

Product Catalog Management
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions of Revenue Cloud
Manage an entire product portfolio with components such as attributes, product classifications,
simple and bundled products, and rules.
Product Catalog Management Standard Objects
The Product Catalog Management data model provides objects and fields to manage products,
rules, and catalogs.
Product Catalog Management Fields on Standard Objects
Product Catalog Management adds standard and custom fields to some standard Salesforce
objects. These fields are available only in orgs where Product Catalog Management is enabled.
This object is available in API version 60.0 and later.
Product Catalog Management Business APIs
Use primitive APIs of Product Catalog Management that serve catalog definitions to users or applications.
Product Catalog Management Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
Product Catalog Management Tooling API Objects
Tooling API exposes metadata used in developer tooling that you can access through REST or SOAP. Tooling API’s SOQL capabilities
for many metadata types allow you to retrieve smaller pieces of metadata.
SEE ALSO:
Salesforce Help: Product Catalog Management Permission Set Licenses
Salesforce Help: User Permissions for Product Catalog Management
Product Catalog Management Standard Objects
The Product Catalog Management data model provides objects and fields to manage products, rules, and catalogs.
AttributeCategory
Represents a logical grouping of attributes that can be reused while defining products. Attribute Categories are used for searching
and managing product attributes. For example, the "Mobile Handset Properties" category has color, storage and make model, and
size attributes. This object is available in API version 60.0 and later.
AttributeCategoryAttribute
Represents a relationship between an attribute category and the attribute definition. This object is available in API version 60.0 and
later.
AttrPicklistExcludedValue
Represents the excluded picklist values for a product classification attribute or a product attribute definition. This object is available
in API version 61.0 and later.
ProductAttributeDefinition
Represents the relationship between a product and its attributes. This object is available in API version 60.0 and later.
ProductCategoryDisqual
Represents disqualification rules for product categories. The rules determine when the product category doesn’t qualify to be
displayed to users. This object is available in API version 60.0 and later.
65
Product Catalog ManagementProduct Catalog Management

===== PAGE 80 =====

ProductCategoryQualification
Represents qualification rules for product categories. The rules determine when the product category qualifies to be displayed to
users. This object is available in API version 60.0 and later.
ProductClassification
Represents a template that holds a collection of dynamic attributes. Product classification is used to quickly define and create multiple
products that are similar yet different. This object is available in API version 60.0 and later.
ProductClassificationAttr
Represents the relationship between a product classification and its attributes. This is the default configuration for products based
on the product classification. This object is available in API version 60.0 and later.
ProductComponentGrpOverride
Represents override information for a Product Component Group. The cardinality of the product component group can be overridden
in the context of a product bundle. This object is available in API version 60.0 and later.
ProductDisqualification
Represents disqualification rules for products. The rules determine when the product doesn’t qualify to be displayed to users. The
rules are based on user context. This object is available in API version 60.0 and later.
ProductQualification
Represents qualification rules for products. The rules determine when the product qualifies to be displayed to users. The rules are
based on user context. This object is available in API version 60.0 and later.
ProductRampSegment
Represents the ramp period within a ramp deal where terms, volumes, and other commitments change over time. This object is
available in API version 62.0 and later.
ProductRelComponentOverride
Represents the cardinality overrides for product components in a bundle. This object is available in API version 60.0 and later.
ProductSpecificationRecType
Represents the relationship between industry-specific product specifications and the product record type. This object is available in
API version 60.0 and later.
ProductSpecificationType
Represents the type of product specification provided by the user to make the product terminology unique to an industry. A product
specification type is associated with a product specification record type. This object is available in API version 60.0 and later.
SEE ALSO:
Object Reference for the Salesforce Platform: Overview of Salesforce Objects and Fields
SOAP API Developer Guide: Introduction to SOAP API
AttributeCategory
Represents a logical grouping of attributes that can be reused while defining products. Attribute Categories are used for searching and
managing product attributes. For example, the "Mobile Handset Properties" category has color, storage and make model, and size
attributes. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
66
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 81 =====

Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
string
Code
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
The unique code for the attribute category. The maximum size is 80 alphanumeric characters.
The code can include the following special characters: @ ! - < > * ? + = % # ( ) / \ & ‘ £ € $ ”.
Type
textarea
Description
Properties
Create, Nillable, Update
Description
The description of the attribute category that's used only during design time.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the attribute category was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the attribute category was last viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The unique name of the attribute category. The maximum length is 80 characters (of any
type).
67
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 82 =====

DetailsField
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner of the attribute category.
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
AttributeCategoryFeed on page 2727
Feed tracking is available for the object.
AttributeCategoryHistory on page 2734
History is available for tracked fields of the object.
AttributeCategoryShare on page 2738
Sharing is available for the object.
AttributeCategoryAttribute
Represents a relationship between an attribute category and the attribute definition. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
68
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 83 =====

Fields
DetailsField
Type
reference
AttributeCategoryId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the attribute category that the attribute is associated with. The ID is unique within
the organization.
This field is a relationship field.
Relationship Name
AttributeCategory
Relationship Type
Lookup
Refers To
AttributeCategory
Type
reference
AttributeDefinitionId
Properties
Create, Filter, Group, Sort, Update
Description
The ID of the attribute definition associated with the attribute category. The ID is unique
within the organization.
This field is a relationship field.
Relationship Name
AttributeDefinition
Relationship Type
Lookup
Refers To
AttributeDefinition
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the attribute category attribute was last referenced.
Type
dateTime
LastViewedDate
69
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 84 =====

DetailsField
Properties
Filter, Nillable, Sort
Description
The date the attribute category attribute was last viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
A unique name for the attribute. The maximum length is 80 characters (of any type).
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner of the attribute category attribute.
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
AttributeCategoryAttributeFeed on page 2727
Feed tracking is available for the object.
AttributeCategoryAttributeHistory on page 2734
History is available for tracked fields of the object.
AttributeCategoryAttributeShare on page 2738
Sharing is available for the object.
AttrPicklistExcludedValue
Represents the excluded picklist values for a product classification attribute or a product attribute definition. This object is available in
API version 61.0 and later.
70
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 85 =====

Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
reference
AttributeId
Properties
Create, Filter, Group, Sort
Description
The ID of the product classification attribute or the product attribute definition of the picklist
data type.
This field is a polymorphic relationship field.
Relationship Name
Attribute
Relationship Type
Lookup
Refers To
ProductAttributeDefinition, ProductClassificationAttr
Type
reference
AttributePicklistValueId
Properties
Create, Filter, Group, Sort
Description
The ID of the attribute picklist value that’s excluded in the product classification attribute or
product attribute definition.
This field is a relationship field.
Relationship Name
AttributePicklistValue
Relationship Type
Lookup
Refers To
AttributePicklistValue
71
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 86 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the excluded attribute picklist value was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the excluded attribute picklist value was last viewed.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the excluded attribute picklist value.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner of the excluded attribute picklist value.
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
AttrPicklistExcludedValueFeed on page 2727
Feed tracking is available for the object.
72
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 87 =====

AttrPicklistExcludedValueHistory on page 2734
History is available for tracked fields of the object.
AttrPicklistExcludedValueShare on page 2738
Sharing is available for the object.
ProductAttributeDefinition
Represents the relationship between a product and its attributes. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
reference
AttributeCategoryId
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID of the attribute category assigned to the parent object.
This field is a relationship field.
Relationship Name
AttributeCategory
Relationship Type
Lookup
Refers To
AttributeCategory
Type
reference
AttributeDefinitionId
Properties
Create, Filter, Group, Sort
Description
The ID of the attribute associated with the product.
This field is a relationship field.
73
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 88 =====

DetailsField
Relationship Name
AttributeDefinition
Relationship Type
Lookup
Refers To
AttributeDefinition
Type
string
AttributeNameOverride
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The name to display for the attribute when shown for this object. This display name overrides
the name on the attribute. For example, the attribute "Color" is overridden to display as
"Laptop Color." The maximum size is 255 alphanumeric characters. The name can include
these special characters: @ ! - < > * ? + = % # ( ) / \ & ‘ £ € $ ”.
Type
string
DefaultValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The default value for the product attribute. The attribute value can be changed. This default
overrides the default value set for a picklist for the attribute.
Type
textarea
Description
Properties
Create, Nillable, Update
Description
A description of the attribute definition. The maximum size is 32,000 alphanumeric characters.
The description can include these special characters: @ ! - < > * ? + = % # ( ) / \ & ‘ £ € $ ”.
Type
picklist
DisplayType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type to display data for the selected data type.
Possible values are:
• CheckBox—Checkbox
74
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 89 =====

DetailsField
• ComboBox—Combobox
• Date
• Datetime—Date Time
• Number
• RadioButton—Radio Button
• Slider—Available in API version 61.0 and later
• Text
• Toggle
Type
textarea
HelpText
Properties
Create, Nillable, Update
Description
The help text to display when end users are configuring this attribute. This field overrides
the help text defined for the attribute itself.
Type
boolean
IsHidden
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates if this product attribute is hidden from end users in the run time (true) or not
(false).
The default value is false.
Type
boolean
IsPriceImpacting
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this attribute dictates the price of a product (true) or not (false).
The default value is false.
Type
boolean
IsReadOnly
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the attribute is read-only for users in the run time (true) or not (false).
The default value is false.
75
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 90 =====

DetailsField
Type
boolean
IsRequired
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this attribute requires a value when assigned to a parent object (true)
or not (false).
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product attribute was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product attribute was last viewed.
Type
int
MaximumCharacterCount
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The maximum number of characters that can be entered for an attribute value.
Type
string
MaximumValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The maximum value that can be entered as an attribute value.
Type
int
MinimumCharacterCount
Properties
Create, Filter, Group, Nillable, Sort, Update
76
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 91 =====

DetailsField
Description
The minimum number of characters that can be entered for an attribute value.
Type
string
MinimumValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The minimum value that can be entered as an attribute value.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the product attribute.
Type
reference
OverriddenProductAttributeDefinitionId
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID associated with the overridden product attribute definition.
This field is a relationship field.
Relationship Name
OverriddenProductAttributeDefinition
Relationship Type
Lookup
Refers To
ProductAttributeDefinition
Type
reference
OverrideContextId
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID associated with the root product record in a bundle.
This field is a polymorphic relationship field.
Relationship Name
OverrideContext
77
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 92 =====

DetailsField
Relationship Type
Lookup
Refers To
Product2
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner of the product attribute definition.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
reference
Product2Id
Properties
Create, Filter, Group, Sort
Description
The product ID associated with the product attribute definition.
This field is a relationship field.
Relationship Name
Product2
Relationship Type
Lookup
Refers To
Product2
Type
reference
ProductClassificationAttributeId
Properties
Create, Filter, Group, Sort
Description
The ID of the attribute assigned to the product classification.
This field is a relationship field.
78
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 93 =====

DetailsField
Relationship Name
ProductClassificationAttribute
Relationship Type
Lookup
Refers To
ProductClassificationAttr
Type
int
Sequence
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The display sequence of the attribute when configuring the product during run time.
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The lifecycle state of the product attribute definition.
Valid values are:
• Active
• Draft
• Inactive
The default value is Draft.
Type
string
StepValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The increment or decrement by which a slider's value changes as the user adjusts the product
attribute value. Available in API version 61.0 and later.
Type
textarea
ValueDescription
Properties
Create, Nillable, Update
Description
The description of the value assigned to this attribute. This field takes on the value description
from the attribute definition.
79
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 94 =====

Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductAttributeDefinitionFeed on page 2727
Feed tracking is available for the object.
ProductAttributeDefinitionHistory on page 2734
History is available for tracked fields of the object.
ProductAttributeDefinitionShare on page 2738
Sharing is available for the object.
ProductCategoryDisqual
Represents disqualification rules for product categories. The rules determine when the product category doesn’t qualify to be displayed
to users. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
reference
CategoryId
Properties
Create, Filter, Group, Sort, Update
Description
The product category associated with the product disqualification record.
This field is a relationship field.
Relationship Name
Category
Relationship Type
Lookup
Refers To
ProductCategory
Type
date
EffectiveFromDate
80
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 95 =====

DetailsField
Properties
Create, Filter, Group, Sort, Update
Description
The date from which the disqualification rule for the product category comes into effect.
Type
date
EffectiveToDate
Properties
Create, Filter, Group, Sort, Update
Description
The date to which the disqualification rule for the product category ceases to be in effect.
Type
boolean
IsDisqualified
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the product category is disqualified (true) or not (false) based on the
disqualification rules.
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product category disqualification record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product category disqualification record was last viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the product category disqualification record.
81
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 96 =====

DetailsField
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the product category disqualification record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
string
Reason
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The reason to disqualify the product category.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductCategoryDisqualFeed on page 2727
Feed tracking is available for the object.
ProductCategoryDisqualHistory on page 2734
History is available for tracked fields of the object.
ProductCategoryDisqualShare on page 2738
Sharing is available for the object.
ProductCategoryQualification
Represents qualification rules for product categories. The rules determine when the product category qualifies to be displayed to users.
This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
82
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 97 =====

Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
reference
CategoryId
Properties
Create, Filter, Group, Sort, Update
Description
The product category associated with the category qualification record.
This field is a relationship field.
Relationship Name
Category
Relationship Type
Lookup
Refers To
ProductCategory
Type
date
EffectiveFromDate
Properties
Create, Filter, Group, Sort, Update
Description
The date from which the qualification rule for the product category comes into effect.
Type
date
EffectiveToDate
Properties
Create, Filter, Group, Sort, Update
Description
The date to which the qualification rule for the product category ceases to be in effect.
Type
boolean
IsQualified
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the product category is qualified (true) or not (false) based on the
qualification rules.
The default value is false.
83
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 98 =====

DetailsField
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product category qualification record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product category qualification record was last viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the product category qualification record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the product category qualification record.
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
ProductCategoryQualificationFeed on page 2727
Feed tracking is available for the object.
84
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 99 =====

ProductCategoryQualificationHistory on page 2734
History is available for tracked fields of the object.
ProductCategoryQualificationShare on page 2738
Sharing is available for the object.
ProductClassification
Represents a template that holds a collection of dynamic attributes. Product classification is used to quickly define and create multiple
products that are similar yet different. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
string
Code
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
A unique code for the product classification. The maximum size is 80 alphanumeric characters.
The code can include the following special characters: @ ! - < > * ? + = % # ( ) / \ & ‘ £ € $ ”.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product classification record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product classification record was last viewed.
85
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 100 =====

DetailsField
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the product classification. The maximum length is 80 characters (of any type).
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner of the product classification.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The lifecycle status of the product classification.
Possible values are:
• Active
• Draft
• Inactive
The default value is Draft.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductClassificationFeed on page 2727
Feed tracking is available for the object.
86
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 101 =====

ProductClassificationHistory on page 2734
History is available for tracked fields of the object.
Sharing rules are available for the object.
ProductClassificationShare on page 2738
Sharing is available for the object.
ProductClassificationAttr
Represents the relationship between a product classification and its attributes. This is the default configuration for products based on
the product classification. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
reference
AttributeCategoryId
Properties
Create, Filter, Group, Nillable, Sort
Description
The ID of the attribute category assigned to the parent object.
This field is a relationship field.
Relationship Name
AttributeCategory
Relationship Type
Lookup
Refers To
AttributeCategory
Type
reference
AttributeDefinitionId
Properties
Create, Filter, Group, Sort
Description
The ID of the attribute assigned to the parent object.
87
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 102 =====

DetailsField
This field is a relationship field.
Relationship Name
AttributeDefinition
Relationship Type
Lookup
Refers To
AttributeDefinition
Type
string
AttributeNameOverride
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The overridden attribute name to display for the attribute when shown for this object. For
example, "Color" overridden to "Laptop Color."
Type
string
DefaultValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The default value of the attribute for a product based on the product classification. This value
can be changed.
Type
textarea
Description
Properties
Create, Nillable, Update
Description
The description of this product classification attribute definition.
Type
picklist
DisplayType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type to display data for the selected data type.
Valid values are:
• CheckBox—Checkbox
• ComboBox—Combobox
• Date
88
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 103 =====

DetailsField
• Datetime—Date Time
• Number
• RadioButton—Radio Button
• Slider—Available in API version 61.0 and later
• Text
• Toggle
Type
textarea
ExcludedPicklistValues
Properties
Create, Nillable, Update
Description
The picklist values excluded from the attribute picklist. This field ensures that the product
classification attribute only has valid values.
Type
textarea
HelpText
Properties
Create, Nillable, Update
Description
The help text to display when end users are configuring this attribute. This field overrides
the help text defined for the attribute itself.
Type
boolean
IsHidden
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates if this product attribute is hidden from end users in the run time (true) or not
(false).
The default value is false.
Type
boolean
IsPriceImpacting
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this attribute dictates the price of a product (true) or not (false).
The default value is false.
89
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 104 =====

DetailsField
Type
boolean
IsReadOnly
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the attribute is read-only for users in the run time (true) or not (false).
The default value is false.
Type
boolean
IsRequired
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this attribute requires a value when assigned to a parent object (true)
or not (false).
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product classification attribute was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product classification attribute was last viewed.
Type
int
MaximumCharacterCount
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The maximum number of characters that can be entered for an attribute value.
Type
string
MaximumValue
90
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 105 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The maximum value that can be entered as an attribute value.
Type
int
MinimumCharacterCount
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The minimum number of characters that can be entered for an attribute value.
Type
string
MinimumValue
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The minimum value that can be entered as an attribute value.
Type
string
Name
Properties
Create, Filter, Group, idLookup, Sort, Update
Description
The name of the product classification attribute.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the product classification attribute owner.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
91
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 106 =====

DetailsField
Type
reference
ProductClassificationId
Properties
Create, Filter, Group, Sort
Description
The ID of the product classification that the attribute is associated with. This field is unique
within your organization.
This field is a relationship field.
Relationship Name
ProductClassification
Relationship Type
Lookup
Refers To
ProductClassification
Type
int
Sequence
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The display sequence of the attribute when configuring the product during run time.
Type
picklist
Status
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The lifecycle status of the product classification attribute.
Valid values are:
• Active
• Draft
• Inactive
The default value is Draft.
Type
string
StepValue
Properties
Create, Filter, Group, Nillable, Sort, Update
92
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 107 =====

DetailsField
Description
The increment or decrement by which a slider's value changes as the user adjusts the product
classification attribute value. Available in API version 61.0 and later.
Type
textarea
ValueDescription
Properties
Create, Nillable, Update
Description
The description of the value assigned to this attribute. This field takes on the value description
from the attribute definition.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductClassificationAttrFeed on page 2727
Feed tracking is available for the object.
ProductClassificationAttrHistory on page 2734
History is available for tracked fields of the object.
Sharing rules are available for the object.
ProductClassificationAttrShare on page 2738
Sharing is available for the object.
ProductComponentGrpOverride
Represents override information for a Product Component Group. The cardinality of the product component group can be overridden
in the context of a product bundle. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
93
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 108 =====

Fields
DetailsField
Type
boolean
IsExcluded
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the product component group is excluded from the product bundle in
the runtime. Excluding a group automatically excludes all child components of the group.
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product component override record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product component override record was last viewed.
Type
int
MaxBundleComponents
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The maximum number of components that can be added to a group.
Type
int
MinBundleComponents
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The minimum number of components that must be added to a group.
Type
string
Name
94
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 109 =====

DetailsField
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the overridden product component group.
Type
reference
OverrideContextId
Properties
Create, Filter, Group, Sort
Description
The root bundle product in whose context the group cardinality is overridden.
This field is a polymorphic relationship field.
Relationship Name
OverrideContext
Relationship Type
Lookup
Refers To
Product2
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner of the product component group override record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
reference
ProductComponentGroupId
Properties
Create, Filter, Group, Sort
Description
The ID of the product component group record.
This field is a relationship field.
95
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 110 =====

DetailsField
Relationship Name
ProductComponentGroup
Relationship Type
Lookup
Refers To
ProductComponentGroup
ProductDisqualification
Represents disqualification rules for products. The rules determine when the product doesn’t qualify to be displayed to users. The rules
are based on user context. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
date
EffectiveFromDate
Properties
Create, Filter, Group, Sort, Update
Description
The date from which the disqualification rule for the product comes into effect.
Type
date
EffectiveToDate
Properties
Create, Filter, Group, Sort, Update
Description
The date to which the disqualification rule for the product ceases to be in effect.
Type
boolean
IsDisqualified
96
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 111 =====

DetailsField
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the product is disqualified based on the disqualification rules (true) or
not (false).
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product disqualification record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product disqualification record was last viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the product disqualification record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner of the product disqualification record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
97
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 112 =====

DetailsField
Type
reference
ParentProductId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the immediate parent product in the product bundle hierarchy.
This field is a relationship field.
Relationship Name
ParentProduct
Relationship Type
Lookup
Refers To
Product2
Type
reference
ProductId
Properties
Create, Filter, Group, Sort, Update
Description
The product for which the disqualification rule is defined.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Type
textarea
Reason
Properties
Create, Nillable, Update
Description
The reason to disqualify the product.
Type
reference
RootProductId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the root product in the product bundle hierarchy.
98
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 113 =====

DetailsField
This field is a relationship field.
Relationship Name
RootProduct
Relationship Type
Lookup
Refers To
Product2
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductDisqualificationFeed on page 2727
Feed tracking is available for the object.
ProductDisqualificationHistory on page 2734
History is available for tracked fields of the object.
ProductDisqualificationShare on page 2738
Sharing is available for the object.
ProductQualification
Represents qualification rules for products. The rules determine when the product qualifies to be displayed to users. The rules are based
on user context. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
date
EffectiveFromDate
Properties
Create, Filter, Group, Sort, Update
Description
The date from which the qualification rule for the product comes into effect.
99
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 114 =====

DetailsField
Type
date
EffectiveToDate
Properties
Create, Filter, Group, Sort, Update
Description
The date to which the qualification rule for the product ceases to be in effect.
Type
boolean
IsQualified
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the product is qualified based on the qualification rules (true) or not
(false). For a product to qualify, this field should be true.
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product qualification record was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product qualification record was last viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the product qualification record.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
100
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 115 =====

DetailsField
Description
The owner of the product qualification record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
reference
ParentProductId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the immediate parent product in the product bundle hierarchy.
This field is a relationship field.
Relationship Name
ParentProduct
Relationship Type
Lookup
Refers To
Product2
Type
reference
ProductId
Properties
Create, Filter, Group, Sort, Update
Description
The product for which the qualification rule is defined.
This field is a relationship field.
Relationship Name
Product
Relationship Type
Lookup
Refers To
Product2
Type
reference
RootProductId
101
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 116 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the root product in the product bundle hierarchy.
This field is a relationship field.
Relationship Name
RootProduct
Relationship Type
Lookup
Refers To
Product2
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductQualificationFeed on page 2727
Feed tracking is available for the object.
ProductQualificationHistory on page 2734
History is available for tracked fields of the object.
ProductQualificationShare on page 2738
Sharing is available for the object.
ProductRampSegment
Represents the ramp period within a ramp deal where terms, volumes, and other commitments change over time. This object is available
in API version 62.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
picklist
DurationType
102
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 117 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The unit of time within which users can try the product for free.
Valid values are:
• Days
• Months
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product ramp segment was last referenced.
Type
dateTime
LastViewedDate
Properties
Filter, Nillable, Sort
Description
The date the product ramp segment was last viewed.
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the product ramp segment.
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The ID of the owner of the product ramp segment.
This field is a polymorphic relationship field.
Relationship Name
Owner
Refers To
Group, User
103
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 118 =====

DetailsField
Type
reference
ProductId
Properties
Create, Filter, Group, Sort
Description
The ID of the product associated with the product ramp segment.
This field is a relationship field.
Relationship Name
Product
Refers To
Product2
Type
reference
ProductSellingModelId
Properties
Create, Filter, Group, Sort
Description
The ID of the product selling model associated with the product ramp segment.
This field is a relationship field.
Relationship Name
ProductSellingModel
Refers To
ProductSellingModel
Type
picklist
SegmentType
Properties
Create, Defaulted on create, Filter, Group, Restricted picklist, Sort, Update
Description
The time duration within the ramp deal where specific terms, volumes, and commitments
are applied to the subscription product.
Valid values are:
• Custom
• FreeTrial
• Yearly
The default value is Yearly.
Type
int
TrialDuration
104
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 119 =====

DetailsField
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The duration within which users can try the product for free.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductRampSegmentFeed on page 2727
Feed tracking is available for the object.
ProductRampSegmentHistory on page 2734
History is available for tracked fields of the object.
ProductRampSegmentShare on page 2738
Sharing is available for the object.
ProductRelComponentOverride
Represents the cardinality overrides for product components in a bundle. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeLayout(), describeSObjects(), getDeleted(), getUpdated(), query(),
retrieve(), search(), undelete(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
boolean
DoesBundlePriceIncludeChild
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the bundle price includes the associated child component's price (true)
or not (false).
The default value is false.
105
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 120 =====

DetailsField
Type
boolean
IsComponentRequired
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the component is a required component in the product bundle.
The default value is false.
Type
boolean
IsDefaultComponent
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether this component is included in the product component group by default.
The default value is false.
Type
boolean
IsExcluded
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the bundle excludes the component (true) or not (false).
The default value is false.
Type
boolean
IsQuantityEditable
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the product component quantity can be edited (true) or not (false).
The default value is false.
Type
dateTime
LastReferencedDate
Properties
Filter, Nillable, Sort
Description
The date the product related component override record was last referenced.
Type
dateTime
LastViewedDate
106
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 121 =====

DetailsField
Properties
Filter, Nillable, Sort
Description
The date the product related component override record was last viewed.
Type
double
MaxQuantity
Properties
Create, Filter, Nillable, Sort, Update
Description
The maximum quantity for the product component in the product bundle.
Type
double
MinQuantity
Properties
Create, Filter, Nillable, Sort, Update
Description
The minimum quantity for the product component in the product bundle
Type
string
Name
Properties
Autonumber, Defaulted on create, Filter, idLookup, Sort
Description
The name of the product related component override. The maximum length is 255 characters
(of any type).
Type
reference
OverrideContextId
Properties
Create, Filter, Group, Sort
Description
The ID associated with the root product in a bundle.
This field is a polymorphic relationship field.
Relationship Name
OverrideContext
Relationship Type
Lookup
Refers To
Product2
107
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 122 =====

DetailsField
Type
reference
OwnerId
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
The owner ID of the product related component override record.
This field is a polymorphic relationship field.
Relationship Name
Owner
Relationship Type
Lookup
Refers To
Group, User
Type
reference
ProductRelatedComponentId
Properties
Create, Filter, Group, Sort
Description
The ID associated with the product related component record.
This field is a relationship field.
Relationship Name
ProductRelatedComponent
Relationship Type
Lookup
Refers To
ProductRelatedComponent
Type
double
Quantity
Properties
Create, Filter, Nillable, Sort, Update
Description
The default number of child product related components.
Type
picklist
QuantityScaleMethod
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
108
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 123 =====

DetailsField
Description
The scaling method that determines how the child product quantity changes as the quantity
of the parent product changes in the runtime cart.
Possible values are:
• Constant
• Proportional
The default value is Proportional.
Associated Objects
This object has the following associated objects. If the API version isn’t specified, they’re available in the same API versions as this object.
Otherwise, they’re available in the specified API version and later.
ProductRelComponentOverrideFeed on page 2727
Feed tracking is available for the object.
ProductRelComponentOverrideHistory on page 2734
History is available for tracked fields of the object.
ProductRelComponentOverrideShare on page 2738
Sharing is available for the object.
ProductSpecificationRecType
Represents the relationship between industry-specific product specifications and the product record type. This object is available in API
version 60.0 and later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The unique name of the ProductSpecificationRecType object in the API. The name:
109
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 124 =====

DetailsField
• must be 40 characters or fewer.
• can contain only underscores and alphanumeric characters.
• must begin with a letter.
• can contain only underscores and alphanumeric characters.
• can’t include spaces
• can’t end with an underscore
• can’t contain 2 consecutive underscores
Type
boolean
IsCommercial
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the product is sold commercially (true) or not (false)
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The combined language and locale ISO code, which controls the language of the Product
Specification Record Type.
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
110
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 125 =====

DetailsField
• zh_CN—Chinese (Simplified)
• zh_TW—Chinese (Traditional)
Type
string
MasterLabel
Properties
Create, Filter, Group, Sort, Update
Description
Label for this Product Specification Record Type value. This display value is the internal label
that doesn't get translated.
Type
string
NamespacePrefix
Properties
Filter, Group, Nillable, Sort
Description
The namespace prefix that is associated with this object. Each Developer Edition org that
creates a managed package has a unique namespace prefix. Limit: 15 characters. You can
refer to a component in a managed package by using the
namespacePrefix_componentName
The namespace prefix can have one of the following values.
• In Developer Edition orgs, NamespacePrefix  is set to the namespace prefix of the
org for all objects that support it, unless an object is in an installed managed package.
In that case, the object has the namespace prefix of the installed managed package. This
field’s value is the namespace prefix of the Developer Edition org of the package
developer.
• In orgs that aren’t Developer Edition orgs, NamespacePrefix  is set only for objects
that are part of an installed managed package. All other objects have no namespace
prefix.
Type
picklist
ProductSpecificationType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
The product specification type that's associated with the record type.
Type
reference
RecordTypeId
Properties
Create, Filter, Group, Sort, Update
111
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 126 =====

DetailsField
Description
The ID of the record type that's associated with the product specification type.
This field is a relationship field.
Relationship Name
RecordType
Relationship Type
Lookup
Refers To
RecordType
ProductSpecificationType
Represents the type of product specification provided by the user to make the product terminology unique to an industry. A product
specification type is associated with a product specification record type. This object is available in API version 60.0 and later.
Supported Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Special Access Rules
Product Catalog Management must be enabled to access this object.
Fields
DetailsField
Type
textarea
Description
Properties
Create, Nillable, Update
Description
The description of the Product Specification Type.
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The unique name of the Product Specification Type object in the API. The name:
• must be 40 characters or fewer.
• can contain only underscores and alphanumeric characters.
112
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 127 =====

DetailsField
• must begin with a letter.
• can contain only underscores and alphanumeric characters.
• can’t include spaces
• can’t end with an underscore
• can’t contain 2 consecutive underscores
In managed packages, this field prevents naming conflicts on package installations. With
this field, a developer can change the object’s name in a managed package and the changes
are reflected in a subscriber’s organization.
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The combined language and locale ISO code, which controls the language of the Product
Specification Type.
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
113
Product Catalog Management Standard ObjectsProduct Catalog Management

===== PAGE 128 =====

DetailsField
Description
Label for this Product Specification Type value. This display value is the internal label that
doesn't get translated.
Type
string
NamespacePrefix
Properties
Filter, Group, Nillable, Sort
Description
The namespace prefix that is associated with this object. Each Developer Edition org that
creates a managed package has a unique namespace prefix. Limit: 15 characters. You can
refer to a component in a managed package by using the
namespacePrefix_componentName
The namespace prefix can have one of the following values.
• In Developer Edition orgs, NamespacePrefix  is set to the namespace prefix of the
org for all objects that support it, unless an object is in an installed managed package.
In that case, the object has the namespace prefix of the installed managed package. This
field’s value is the namespace prefix of the Developer Edition org of the package
developer.
• In orgs that aren’t Developer Edition orgs, NamespacePrefix  is set only for objects
that are part of an installed managed package. All other objects have no namespace
prefix.
Product Catalog Management Fields on Standard Objects
Product Catalog Management adds standard and custom fields to some standard Salesforce objects. These fields are available only in
orgs where Product Catalog Management is enabled. This object is available in API version 60.0 and later.
Product Catalog Management Fields on Attribute Definition
Standard and custom fields extend the standard Attribute Definition object for use in Product Catalog Management.
Product Catalog Management Fields on Product2
Standard and custom fields extend the standard Product2 object for use in Product Catalog Management to represent information
about products.
Product Catalog Management Fields on Product Catalog
Standard and custom fields extend the standard Product Catalog object for use in Product Catalog Management. This object is
available in API version 60.0 and later.
Product Catalog Management Fields on Product Category
Standard and custom fields extend the standard Product Category object for use in Product Catalog Management.
Product Catalog Management Fields on Product Component Group
Standard and custom fields extend the standard Product Component Group object for use in Product Catalog Management.
114
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 129 =====

Product Catalog Management Fields on Product Related Component
Standard and custom fields extend the standard Product Related Component object for use in Product Catalog Management.
Product Catalog Management Fields on Product Relationship Type
Standard and custom fields extend the standard Product Relationship Type object for use in Product Catalog Management.
Product Catalog Management Fields on Product Selling Model Option
Standard and custom fields extend the standard Product Selling Model Option object for use in Product Catalog Management. This
object is available in API version 60.0 and later.
Product Catalog Management Fields on Attribute Definition
Standard and custom fields extend the standard Attribute Definition object for use in Product Catalog Management.
Fields
DetailsField
Type
picklist
DataType
Properties
Create, Filter, Group, Restricted picklist, Sort
Description
The data type of the attribute definition.
Valid values are:
• Checkbox
• Currency—Available in API version 61.0 and later
• Date
• Datetime
• Number
• Percent—Available in API version 61.0 and later
• Picklist
• Text
SEE ALSO:
Attribute Definition
Product Catalog Management Fields on Product2
Standard and custom fields extend the standard Product2 object for use in Product Catalog Management to represent information about
products.
115
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 130 =====

Fields
DetailsField
Type
reference
Based On
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The ID of the product classification from which this product inherits.
This field is a relationship field.
Relationship Name
BasedOn
Relationship Type
Lookup
Refers To
ProductClassification
Type
textarea
Help Text
Properties
Create, Nillable, Update
Description
The help text that appears at runtime for the product. The maximum size is 32,000
alphanumeric characters. The help text can include these special characters: @ ! - < > * ? +
= % # ( ) / \ & ‘ £ € $ ”.
Type
dateTime
Availability Date
Properties
Create, Filter, Nillable, Sort, Update
Description
The date when the product is available.
Type
boolean
CanRamp
Properties
Defaulted on create, Filter, Group, Sort
Description
Indicates whether the product’s terms, volumes, and other commitments can be ramped
(true) at run time or not (false)
The default value is false.
116
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 131 =====

DetailsField
Type
dateTime
Discontinued Date
Properties
Create, Filter, Nillable, Sort, Update
Description
The date when the product is discontinued.
Type
dateTime
End Of Life Date
Properties
Create, Filter, Nillable, Sort, Update
Description
The date and time after which a product isn’t supported, ordered, or maintained.
Type
string
Specification Type
Properties
Filter, Group, Nillable, Sort
Description
The type of product specification that’s being created.
Type
picklist
DecompositionScope
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The number of fulfillment order line items that must be generated. Available in API version
61.0 and later.
Valid values are:
• Account
• Bundle
• Order
• OrderLineItem
Type
picklist
FulfillmentQtyCalcMethod
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Determines whether the quantity of fulfillment order line items must always be one or must
be aggregated from the source line items. Available in API version 61.0 and later.
117
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 132 =====

DetailsField
Valid values are:
• Aggregate
• AlwaysOne
Type
picklist
UsageModelType
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The type of usage model for a product or service. Anchor is the main subscription product
or service. Pack is the add-on product or service that grants additional usage resources for
consumption. Available in API version 62.0 and later.
Valid values are:
• Anchor
• Pack
SEE ALSO:
Product2
Product Catalog Management Fields on Product Catalog
Standard and custom fields extend the standard Product Catalog object for use in Product Catalog Management. This object is available
in API version 60.0 and later.
Fields
DetailsField
Type
string
Code
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
A unique ID associated with the catalog. The maximum size is 80 alphanumeric characters.
Type
textarea
Description
Properties
Create, Nillable, Update
118
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 133 =====

DetailsField
Description
The description of the catalog that's used during design time. The maximum size is 255
alphanumeric characters.
Type
dateTime
EffectiveEndDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date after which the product catalog is unavailable to end users.
Type
dateTime
EffectiveStartDate
Properties
Create, Filter, Nillable, Sort, Update
Description
The date on which the product catalog is available to end users.
Type
picklist
CatalogType
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
The category of an entry in the catalog.
Possible values are:
• Sales
• ServiceProcess—Service Process
The default value is Sales.
SEE ALSO:
Product Catalog
Product Catalog Management Fields on Product Category
Standard and custom fields extend the standard Product Category object for use in Product Catalog Management.
119
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 134 =====

Fields
DetailsField
Type
string
Code
Properties
Create, Filter, Group, idLookup, Nillable, Sort, Update
Description
A unique ID associated with the catalog. The maximum size is 80 alphanumeric characters.
Type
boolean
IsNavigational
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the category or subcategory is shown in the menu as a navigational
breadcrumb (true) or not (false). Available in API version 62.0 and later.
The default value is false.
SEE ALSO:
Product Category
Product Catalog Management Fields on Product Component Group
Standard and custom fields extend the standard Product Component Group object for use in Product Catalog Management.
Fields
DetailsField
Type
reference
ParentGroupId
Properties
Create, Filter, Group, Nillable, Sort, Update
Description
The parent product component group in a nested group hierarchy for the same parent
product. Available in API version 62.0 and later.
This field is a relationship field.
Relationship Name
ParentGroup
120
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 135 =====

DetailsField
Refers To
ProductComponentGroup
SEE ALSO:
Product Component Group
Product Catalog Management Fields on Product Related Component
Standard and custom fields extend the standard Product Related Component object for use in Product Catalog Management.
Fields
DetailsField
Type
reference
ChildProductClassificationId
Properties
Create, Filter, Group, Nillable, Sort
Description
The child product classification that's associated with a product.
This field is a relationship field.
Relationship Name
ChildProductClassification
Refers To
ProductClassification
Type
picklist
QuoteVisibility
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Specifies the product-related component to display as a quote line item in the Transaction
Line Editor and the quote document. The default value is Always.
Possible values are:
• Always
• Transaction Line Editor Only
• Quote Document Only
121
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 136 =====

DetailsField
• Never
SEE ALSO:
Product Related Component
Product Catalog Management Fields on Product Relationship Type
Standard and custom fields extend the standard Product Relationship Type object for use in Product Catalog Management.
Fields
DetailsField
Type
picklist
AssociatedProductRoleCat
Properties
Create, Filter, Group, Nillable, Restricted picklist, Sort
Description
The role that the associated component plays in the relationship.
Valid values are:
• BundleComponent— The associated product is part of a bundle.
• ClassificationComponent— The associated component is a product
classification. Available in API version 61.0 and later
SEE ALSO:
Product Relationship Type
Product Catalog Management Fields on Product Selling Model Option
Standard and custom fields extend the standard Product Selling Model Option object for use in Product Catalog Management. This
object is available in API version 60.0 and later.
Fields
DetailsField
Type
boolean
IsDefault
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
122
Product Catalog Management Fields on Standard ObjectsProduct Catalog Management

===== PAGE 137 =====

DetailsField
Description
Indicates the default product selling model for a product. Setting a product selling model
as default is optional. A product can only have one default product selling model.
The default value is false.
SEE ALSO:
Product Selling Model Option
Product Catalog Management Business APIs
Use primitive APIs of Product Catalog Management that serve catalog definitions to users or applications.
This table lists the available Product Catalog Management resources.
DescriptionResource
Retrieve, search, filter, or sort
catalog records.
/connect/pcm/catalogs (POST)
Retrieve details of catalog
records based on a catalog ID.
/connect/pcm/catalogs/catalogId (GET)
Retrieve the root-level
categories of a catalog based on
/connect/pcm/catalogs/catalogId/categories (GET)
a catalog ID, or subcategories
based on a parent category. You
can also search, filter, or sort the
categories.
Retrieve details of individual
category records based on a
category ID.
/connect/pcm/categories/categoryId (GET)
Retrieve products. You can also
search, filter, or sort the
products.
/connect/pcm/products (POST)
Retrieve details of individual
product records or a bundle
based on a product ID.
/connect/pcm/products/productId (GET)
Retrieve details for multiple
products.
/connect/pcm/products/bulk (POST)
Retrieve the saved index
configurations. Additionally, you
/connect/pcm/index/configurations  (GET, PUT)
can persist the index
configuration.
123
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 138 =====

DescriptionResource
Retrieve related
ProductRampSegment or
/connect/pcm/relatedRecords/entityName (POST)
ProductUsageGrant records for
Product2 object.
Retrieve the created snapshots
and snapshot indexes.
/connect/pcm/index/snapshots (GET)
Create indexes for a snapshot.
Indexes improve search results
/connect/pcm/index/deploy (POST)
and make it easier to find
products at run time through
search terms.
Fetch and update settings
related to indexing and search.
/connect/pcm/index/setting (GET, PATCH)
Get the count and details of the
errors that occurred during the
indexing process.
/connect/pcm/index/error (GET)
Copy related records of an
object along with the main
product record.
/connect/pcm/deep-clone (POST)
Get details about the unit of
measure for a specific set of
records.
/connect/pcm/unit-of-measure/info (GET)
Round off and scale decimal
data for a specific set of fields.
/connect/pcm/unit-of-measure/rounded-data (POST)
Resources
Learn more about the available Product Catalog Management API resources.
Request Bodies
Learn more about the available Product Catalog Management API request bodies.
Response Bodies
Learn more about the available Product Catalog Management API response bodies.
SEE ALSO:
Connect REST API Developer Guide: Introduction
Resources
Learn more about the available Product Catalog Management API resources.
124
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 139 =====

Bulk Product Details (POST)
Retrieve details for multiple products.
Catalog List (POST)
Retrieve, search, filter, or sort catalog records.
Catalog By ID (GET)
Retrieve details of catalog records based on a catalog ID.
Categories List (GET)
Retrieve the root-level categories of a catalog based on a catalog ID, or subcategories based on a parent category. You can also
search, filter, or sort the categories.
Category By ID (GET)
Retrieve details of individual category records based on a category ID.
Deep Clone (POST)
Copy related records of an object along with the main product record.
Index Configuration Collection (GET, PUT)
Retrieve the saved index configurations. Additionally, you can persist the index configuration.
Index Setting (GET, PATCH)
Fetch and update settings related to indexing and search.
Product Classification Details (POST)
Retrieve the details for a list of product classification records.
Product Details (GET)
Retrieve details of individual product records or a bundle based on a product ID.
Product Related Records List (POST)
Retrieve related ProductRampSegment or ProductUsageGrant records for Product2 object.
Products List (POST)
Retrieve products. You can also search, filter, or sort the products.
Snapshot Collection (GET)
Retrieve the created snapshots and snapshot indexes.
Snapshot Deployment (POST)
Create indexes for a snapshot. Indexes improve search results and make it easier to find products at run time through search terms.
Snapshot Index Error (GET)
Get the count and details of the errors that occurred during the indexing process.
Unit of Measure Info (GET)
Get details about the unit of measure for a specific set of records.
Unit of Measure Rounded Data (POST)
Round off and scale decimal data for a specific set of fields.
Bulk Product Details (POST)
Retrieve details for multiple products.
Resource
/connect/pcm/products/bulk
125
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 140 =====

Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/products/bulk
Available version
61.0
HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "cbfabffb-093f-45b3-8c2d-88b4acbd4867",
"productIds": [
"01tT1000000F0afIAC",
"01tT1000000F0afIAC"
],
"uptoLevel": 1,
"language": "french",
"additionalFields": {
"Product2": {
"fields": [
"code__c"
]
},
"ProductAttributeDefinition": {
"fields": [
"scope"
]
}
}
}
This example shows a sample request to fetch data from Enterprise Product Catalog.
{
"productIds": [
"01tLT000009vGXfYAM"
],
"catalogSystems": [
"epc"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalMap of object and list of additional
standard or custom fields to be included
in the response.
Map<String,
Additional Fields
Input>
additional
Fields
126
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 141 =====

Available
Version
Required or
Optional
DescriptionTypeName
The supported objects are:
• Product2
• ProductAttributeDefinition—If the
fields defined for the
ProductAttributeDefinition object
aren’t available for the
ProductClassificationAttr object, then
the API request fails.
66.0OptionalName of the catalog system. Valid values
are:
String[]catalogSystems
• epc—Enterprise Product Catalog
• pcm—Product Catalog Management
Although this property accepts a list, you
can pass only one value. If you don’t
specify a value, the default behavior is to
fetch data from the pcm  catalog.
61.0OptionalUnique token to track and associate
related events or transactions across
Stringcorrelation
Id
different components of the application.
If unspecified, a Universally Unique
Identifier (UUID) is generated.
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
61.0RequiredList of product IDs that details must be
returned for.
String[]productIds
If any product ID is blank, invalid, or not
found, then the request is processed with
valid and available product IDs.
61.0OptionalHierarchy level to follow to return the
product details. For a bundle, this
IntegeruptoLevel
property determines the number of levels
of child components to be returned. You
can specify up to a hierarchy level of 1.
If unspecified, the default level is the full
bundle hierarchy.
127
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 142 =====

Response body for POST
Products Output
Catalog List (POST)
Retrieve, search, filter, or sort catalog records.
Resource
/connect/pcm/catalogs
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/catalogs
Available version
60.0
Requires Chatter
No
HTTP methods
POST
Note:  The POST method is used to retrieve the catalog records instead of the GET method as a request payload is sent to
filter the records.
Request body for POST
JSON example
This example shows how to retrieve catalogs that contain apple  in the catalog name.
{
"pageSize": 100,
"offset": 0,
"language": "french",
"filter": {
"criteria": [
{
"property": "name",
"operator": "contains",
"value": "apple"
}
]
}
}
This example shows how to retrieve catalogs with ServiceProcess  as the catalog type.
{
"pageSize": 100,
"offset": 0,
"sort": {
"orders": [
{
"property": "name",
"direction": "desc"
}
128
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 143 =====

]
},
"filter": {
"criteria": [
{
"property": "catalogType",
"operator": "eq",
"value": "ServiceProcess"
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
60.0OptionalUnique token to track and associate
related events or transactions across
Stringcorrelation
Id
different components of the application.
If unspecified, a Universally Unique
Identifier (UUID) is generated.
60.0OptionalCriteria to filter the records. Filters are
applicable to the fields of the
Filterfilter
ProductCatalog object. The supported
operators are:
• eq
• in
• contains
The supported properties are name and
catalogType.
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
60.0OptionalNumber of records to skip. The default
value is 0.
Integeroffset
60.0OptionalNumber of records per page. Valid values
are from 1 through 100. If unspecified,
defaults to 100.
IntegerpageSize
60.0OptionalSort order of the catalog records. The
supported operators are:
Sortsort
• asc
129
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 144 =====

Available
Version
Required or
Optional
DescriptionTypeName
• desc
Response body for POST
Catalogs Output
Catalog By ID (GET)
Retrieve details of catalog records based on a catalog ID.
Resource
/connect/pcm/catalogs/catalogId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/catalogs/0ZST100000000kUOAQ
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/catalogs/0ZST100000000kUOAQ?language=spanish
Available version
60.0
Requires Chatter
No
HTTP methods
GET
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
60.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
60.0OptionalFor internal use only.String[]fields
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
Response body for GET
Catalogs Output
130
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 145 =====

Categories List (GET)
Retrieve the root-level categories of a catalog based on a catalog ID, or subcategories based on a parent category. You can also search,
filter, or sort the categories.
Resource
/connect/pcm/catalogs/catalogId/categories
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/catalogs/0ZST100000000kUOAQ/categories
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/catalogs/0ZST100000000kUOAQ/categories?language=spanish
Available version
60.0
Requires Chatter
No
HTTP methods
GET
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
60.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
60.0OptionalNumber of levels in the category hierarchy
to return. The default value is 1.
Integerdepth
60.0OptionalFor internal use only.String[]fields
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
60.0OptionalID of the category to fetch the associated
hierarchy of subcategories. If unspecified,
then the root-level categories are returned.
Stringparent
CategoryId
Response body for GET
Categories Output
131
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 146 =====

Category By ID (GET)
Retrieve details of individual category records based on a category ID.
Resource
/connect/pcm/categories/categoryId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/categories/0ZGT100000000qqOAA
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/categories/0ZGT100000000qqOAA?language=spanish
Available version
60.0
Requires Chatter
No
HTTP methods
GET
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
60.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
60.0OptionalFor internal use only.String[]fields
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
Response body for GET
Categories Output
Deep Clone (POST)
Copy related records of an object along with the main product record.
Resource
/connect/pcm/deep-clone
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/deep-clone
132
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 147 =====

Available version
63.0
HTTP methods
POST
Request body for POST
JSON example
{
"mainRecordId": "01tSG0000028kcSYAQ",
"mainObjectApiName": "Product2",
"mainRecordFieldValues": {
"Name": "New Cloud Storage"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredAPI name of the object. The supported
object is Product2.
StringmainObject
ApiName
63.0OptionalMapping of the API name of the field to
its value. The values passed through this
Map<String,
String>
mainRecord
FieldValues
map are set for the created record. You
can pass the Name field only through this
map.
63.0RequiredID of the record.StringmainRecordId
Response body for POST
Deep Clone Response
Index Configuration Collection (GET, PUT)
Retrieve the saved index configurations. Additionally, you can persist the index configuration.
Resource
/connect/pcm/index/configurations
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/index/configurations
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/index/configurations?includeMetadata=false&fieldTypes=Standard,Custom
Available version
62.0
HTTP methods
GET, PUT
133
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 148 =====

Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
62.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
62.0OptionalFilters and returns only the persisted index
configurations, based on the index
String[]fieldTypes
configuration type specified in the query
parameters.
The supported types of filters are:
• STANDARD
• CUSTOM
• ProductDynamicAttribute
• ProductAttributeDefinitionStandard
• ProductAttributeDefinitionCustom
62.0OptionalIndicates whether to include metadata
(true) or not (false).
Booleaninclude
Metadata
Response body for GET
Index Configuration Collection
Request body for PUT
JSON example
{
"correlationId": "8545b5aa-f3e6-429a-8f21-9cc4ce50b1d7",
"indexConfigurations": [
{
"attributeDefinitionId": "0tjT1000000002bIAA",
"name": "Color",
"type": "ProductDynamicAttribute",
"isSearchable": true
},
{
"attributeFieldId": "00Nxx000001FwnABII",
"name": "Message__c",
"type": "Custom",
"isSearchable": true
},
{
"name": "Code",
"type": "Standard",
134
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 149 =====

"isSearchable": true
},
{
"facetDisplayRank": 1,
"isFacetable": false,
"isSearchable": true,
"name": "Family",
"type": "Standard"
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalUnique token to track and associate
related events or transactions across
StringcorrelationId
different components of the application.
If unspecified, a Universally Unique
Identifier (UUID) is generated.
62.0RequiredList of index configurations.Index Configuration
Input[]
index
Configurations
Response body for PUT
Index Configurations Update
Index Setting (GET, PATCH)
Fetch and update settings related to indexing and search.
Resource
/connect/pcm/index/setting
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/index/setting
Available version
63.0
HTTP methods
GET, PATCH
Response body for GET
Index Setting Results
Request body for PATCH
JSON example
{
"setting" : {
135
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 150 =====

"supportedLanguages" : ["en_US","ja","es","nl_NL"],
"defaultLanguage" : "en_US",
"productsGrouping": "GROUPING_VARIATION"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredObject containing the setting-related
details.
Setting Input[]setting
Request parameters for PATCH
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0RequiredID of the setting to update the details for.StringsettingId
Response body for PATCH
Index Setting Update
Product Classification Details (POST)
Retrieve the details for a list of product classification records.
This API fetches metadata, attributes, and attribute categories associated with product classifications across supported catalog systems.
Resource
/revenue/product-catalog-management/product-classifications/details
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/revenue/product-catalog-management/product-classifications/details
Available version
66.0
HTTP methods
POST
Request body for POST
JSON example
{
"productClassificationIds": [
"01txx0000006iFMAAY",
"01txx0000006iGxAAY"
],
"catalogSystems": [
"epc"
136
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 151 =====

]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalName of the catalog system. Valid value
is:
String[]catalogSystems
• epc—Enterprise Product Catalog
66.0RequiredList of product classification IDs for which
you want to retrieve product details. In
String[]product
ClassificationIds
the epc  catalog system, these values
are the Product2  record IDs.
Response body for POST
Product Classification Details Collection on page 204
Product Details (GET)
Retrieve details of individual product records or a bundle based on a product ID.
Resource
/connect/pcm/products/productId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/products/01tT1000000F0afIAC
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/products/01tT1000000F0afIAC?language=spanish
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/products/01tT1000000F0afIAC/catalogSystems=epc
Available version
60.0
Requires Chatter
No
HTTP methods
GET
Note:  You must invoke this API request by using GET method only. If the request is invoked by using POST method, the
request is considered as a Products List API request.
137
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 152 =====

Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
66.0OptionalName of the catalog system. Valid values
are:
String[]catalogSystems
• epc—Enterprise Product Catalog
• pcm—Product Catalog Management
Although this parameter accepts a list, you
can pass only one value. If you don’t
specify a value, the default behavior is to
fetch data from the pcm  catalog.
60.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
60.0OptionalFor internal use only.String[]fields
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
Response body for GET
Products
Product Related Records List (POST)
Retrieve related ProductRampSegment or ProductUsageGrant records for Product2 object.
Resource
/connect/pcm/relatedRecords/entityName
The supported entity or object is Product2.
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/relatedRecords/product2
Available version
62.0
HTTP methods
POST
Note:  POST methods typically create an item, but for this resource POST is used to retrieve information.
138
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 153 =====

Request body for POST
JSON example
{
"recordIds": [
"01txx0000006i44AAA",
"01txx0000006i5gAAA"
],
"relatedObjectNodes": [
{
"relatedObjectAPIName": "ProductRampSegment",
"pageSize": 20,
"offSet": 0
},
{
"relatedObjectAPIName": "ProductUsageGrant",
"pageSize": 10,
"offSet": 0,
"filter": {
"criteria": [
{
"property": "status",
"operator": "eq",
"value": "active"
},
{
"property": "effectivestartdate",
"operator": "lte",
"value": "2024-06-25"
},
{
"criteriaType": "CustomWhereCondition",
"value": "(effectiveenddate = null OR effectiveenddate >= 2024-06-25)"
}
]
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
62.0OptionalUnique token to track and associate
related events or transactions across
Stringcorrelation
Id
different components of the application.
If unspecified, a Universally Unique
Identifier (UUID) is generated.
62.0RequiredList of record IDs to return the
relatedObjects records for. The maximum
number of record IDs supported is 20.
String[]recordIds
139
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 154 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredList of nodes for the related objects. The
maximum number of related object
nodes supported is two.
Related Object
Node Input[]
related
ObjectNodes
Response body for POST
Related Records List
Products List (POST)
Retrieve products. You can also search, filter, or sort the products.
Resource
/connect/pcm/products
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/products?productClassificationId=11BT10000004C9SMAU
Available version
60.0
Requires Chatter
No
HTTP methods
POST
Note:  POST methods typically create an item, but for this resource POST is used to retrieve information.
Request body for POST
JSON example
This example is a search request for products that contain Bundle Product  in the product name.
{
"catalogIds": [
"0ZST10000004D03OAE"
],
"language": "spanish",
"filter": {
"criteria": [
{
"property": "name",
"operator": "contains",
"value": "Bundle Product"
}
]
},
"relatedObjectFilters": [
{
"objectName": "ProductSpecificationRecType",
"criteria": [
140
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 155 =====

{
"property": "IsCommercial",
"operator": "eq",
"value": false
}
],
"additionalFields": {
"Product2": {
"fields": [
"code__c"
]
}
}
}
]
}
This example is a search request for products that contain the specified search term in the product name and are part of a catalog.
{
"catalogIds": [
"0ZSDU0000002Og54AE"
],
"searchTerm": "Slack"
}
Query parameters
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalID of the product classification template
that contains a collection of dynamic
Stringproduct
Classification
Id attributes and can be reused to create
multiple products. Products that are
based on a product classification inherit
all the attributes of the product
classification.
Specify either the product classification
ID, list of category IDs, or list of catalog
IDs to retrieve products.
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalMap of the object and the list of standard
and custom fields to be queried along
with the standard response.
Map<String,
Additional Fields
Input>
additional
Fields
The supported object is Product2.
141
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 156 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalList of comma-separated catalog IDs. The
API returns the list of product records that
List<String>catalogIds
are associated with the specified catalog
IDs.
Specify either the product classification
ID, list of category IDs, or list of catalog
IDs to retrieve products.
60.0OptionalList of comma-separated category IDs.
The API returns the list of product records
List<String>categoryIds
that are associated with the specified
category IDs. If unspecified, then returns
all products that are added to at least one
category.
Specify either the product classification
ID, list of category IDs, or list of catalog
IDs to retrieve products.
60.0OptionalUnique token to track and associate
related events or transactions across
Stringcorrelation
Id
different components of the application.
If unspecified, a Universally Unique
Identifier (UUID) is generated.
60.0OptionalCriteria to filter the records. Filters are
applicable to the fields of Product2
object. The supported operators are:
Criteria Inputfilter
• eq
• in
• contains—This value isn’t
applicable if the Use Indexed Data
For Product Listing and Search
toggle from the Product Discovery
Settings page from Setup is enabled.
• gt—Specifies a greater than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• lt—Specifies a less than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
142
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 157 =====

Available
Version
Required or
Optional
DescriptionTypeName
• gte—Specifies a greater than or
equal to criteria. Available from API
version 63.0 and later for Number,
Date, and Datetime data types only.
• lte—Specifies a less than or equal
to criteria. Available from API version
63.0 and later for Number, Date, and
Datetime data types only.
If multiple criteria are specified, then the
criteria are combined by using the and
operator.
The supported properties are name,
description, and isActive. If
the Use Indexed Data For Product
Listing and Search toggle from the
Product Discovery Settings page from
Setup is enabled, then the supported
property is name  only.
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
60.0OptionalNumber of records to skip. The default
value is 0.
Integeroffset
60.0OptionalSpecifies the number of records per page.
Valid values are from 1 through 200. If the
value is unspecified, it defaults to 100.
IntegerpageSize
60.0OptionalCriteria for the related objects to filter the
records. The supported operator is eq.
Related Object
Filter[]
related
Object
Filters The supported object is
ProductSpecificationRecType.
The supported values are true  and
false. The supported property is
IsCommercial.
62.0OptionalString used to get products with the
product name containing the search
StringsearchTerm
term. See Search Considerations When
Using Indexed Data.
60.0OptionalSort order for the products.Sortsort
143
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 158 =====

Available
Version
Required or
Optional
DescriptionTypeName
If the Use Indexed Data For Product
Listing and Search toggle from the
Product Discovery Settings page from
Setup is enabled, then you can sort
products by using name only.
Response body for POST
Products Output
Snapshot Collection (GET)
Retrieve the created snapshots and snapshot indexes.
Resource
/connect/pcm/index/snapshots
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/index/snapshots
Available version
62.0
HTTP methods
GET
Query Parameter for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0OptionalNumber of index logs to include in the
response. Specify a number from 0
through 100. The default value is 25.
IntegernumberOf
IndexLogs
Response body for GET
Snapshot Collection
Snapshot Deployment (POST)
Create indexes for a snapshot. Indexes improve search results and make it easier to find products at run time through search terms.
Resource
/connect/pcm/index/deploy
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/index/deploy
144
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 159 =====

Available version
62.0
HTTP methods
POST
Request body for POST
JSON example
This example shows a sample request to build a new snapshot with immediate activation.
{
"snapshot": {
"activationType": "IMMEDIATE"
},
"buildType": "FULL"
}
This example shows a sample request to rebuild a snapshot in the active  status.
{
"snapshot": {
"activationType": "IMMEDIATE",
"id": "1Avxx0000005DFe1AM"
},
"buildType": "FULL"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredBuild type of the snapshot index. Valid
value is:
StringbuildType
• FULL—Specifies a full index build.
• INCREMENTAL—Specifies an
incremental index build. Available
from API version 63.0 and later.
62.0RequiredSnapshot to deploy.Run-time Catalog
Snapshot Input[]
snapshot
Response body for POST
Snapshot Deployment
Snapshot Index Error (GET)
Get the count and details of the errors that occurred during the indexing process.
Resource
/connect/pcm/index/error
145
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 160 =====

Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/index/error
Available version
63.0
HTTP methods
GET
Request parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0RequiredID of the index.StringindexId
63.0RequiredID of the snapshot index.Stringsnapshot
IndexId
Response body for GET
Snapshot Index Error
Unit of Measure Info (GET)
Get details about the unit of measure for a specific set of records.
Resource
/connect/pcm/unit-of-measure/info
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/unit-of-measure/info
Available version
63.0
HTTP methods
GET
Query parameters for GET
Available
Version
Required or
Optional
DescriptionTypeParameter
Name
63.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
63.0OptionalIDs of the unit of measure records.Stringids
146
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 161 =====

Response body for GET
Bulk Unit Of Measure Info
Unit of Measure Rounded Data (POST)
Round off and scale decimal data for a specific set of fields.
Resource
/connect/pcm/unit-of-measure/rounded-data
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/pcm/unit-of-measure/rounded-data
Available version
63.0
HTTP methods
POST
Request body for POST
JSON example
{
"dataRowInputs": [
{
"key": "PRC1",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"unitOfMeasureId": "0hExx0000000001EAA"
},
{
"fieldApiName": "MinQuantity",
"originalValue": "987462848934739347.32232590183756545",
"unitOfMeasureId": "0hExx000000001dEAA"
}
]
},
{
"key": "PRC2",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"unitOfMeasureId": "uomId1"
},
{
"fieldApiName": "MinQuantity",
"originalValue": 987.4628,
"unitOfMeasureId": "Kgs Id"
}
]
},
147
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 162 =====

{
"key": "PRC3",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 0.437584,
"unitOfMeasureId": "uomId2"
},
{
"fieldApiName": "MinQuantity",
"originalValue": 7364.58923,
"unitOfMeasureId": "uomId2"
}
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
63.0OptionalUnique token to track and associate
related events or transactions across
Stringcorrelation
Id
different components of the application.
If unspecified, a Universally Unique
Identifier (UUID) is generated.
63.0RequiredList of row inputs for rounding the data.Data Row Input[]dataRow
Inputs
Response body for POST
Data Rounding
Request Bodies
Learn more about the available Product Catalog Management API request bodies.
Additional Fields Input
Input representation of the additional standard or custom fields to be included in the response.
Bulk Product Details Input
Input representation of the request to retrieve the details of multiple products.
Catalog Input
Input representation of the request to retrieve catalog records.
Criteria Input
Input representation of the filter criteria item request.
Data Rounding Input
Input representation of the details of the data rounding input.
148
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 163 =====

Data Row Input
Input representation of the details of the input for a data rounding request.
Deep Clone Input
Input representation of the details of the object and associated record to be cloned.
Field Data Input
Input representation of the details of the field data input.
Filter Input
Input representation of the filter request.
Include Object Input
Input representation of the object to include in the response.
Index Configuration Collection Input
Input representation of the collection of index configurations.
Index Configuration Input
Input representation of the request to persist the index configuration.
Index Setting Input
Input representation of the index setting.
Options Input
Reserved for internal use.
Order Input
Input representation of the sort order item request.
Product Classification Details Input
Input representation of the request to fetch details of product classification records, including their attributes and attribute categories.
Product Input
Input representation of a product in the catalog.
Related Object Filters Input
Input representation of the request to filter related objects.
Related Object Node Input
Input representation of the details of a related object node.
Related Records Input
Input representation of the request to retrieve related ProductRampSegment or ProductUsageGrant records for Product2 object.
Run-time Catalog Snapshot Input
Input representation of the details of a run-time catalog snapshot for deployment.
Setting Input
Input representation of the details of the index setting.
Snapshot Deployment Input
Input representation of the request to deploy a run-time catalog snapshot.
Sort Input
Input representation of the sort request.
149
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 164 =====

Additional Fields Input
Input representation of the additional standard or custom fields to be included in the response.
JSON example
"additionalFields": {
"Product2": {
"fields": [
"code__c"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0RequiredList of additional standard or custom fields
to be included in the response.
String[]fields
Bulk Product Details Input
Input representation of the request to retrieve the details of multiple products.
JSON example
{
"correlationId": "cbfabffb-093f-45b3-8c2d-88b4acbd4867",
"productIds": [
"01tT1000000F0afIAC",
"01tT1000000F0afIAC"
],
"uptoLevel": 1,
"language": "french",
"additionalFields": {
"Product2": {
"fields": [
"code__c"
]
},
"ProductAttributeDefinition": {
"fields": [
"scope"
]
}
}
}
This example shows a sample request to fetch data from Enterprise Product Catalog.
{
"productIds": [
"01tLT000009vGXfYAM"
],
150
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 165 =====

"catalogSystems": [
"epc"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalMap of object and list of additional
standard or custom fields to be included
in the response.
Map<String,
Additional Fields
Input>
additional
Fields
The supported objects are:
• Product2
• ProductAttributeDefinition—If the
fields defined for the
ProductAttributeDefinition object
aren’t available for the
ProductClassificationAttr object, then
the API request fails.
66.0OptionalName of the catalog system. Valid values
are:
String[]catalogSystems
• epc—Enterprise Product Catalog
• pcm—Product Catalog Management
Although this property accepts a list, you
can pass only one value. If you don’t
specify a value, the default behavior is to
fetch data from the pcm  catalog.
61.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
61.0RequiredList of product IDs that details must be
returned for.
String[]productIds
If any product ID is blank, invalid, or not
found, then the request is processed with
valid and available product IDs.
151
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 166 =====

Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalHierarchy level to follow to return the
product details. For a bundle, this property
IntegeruptoLevel
determines the number of levels of child
components to be returned. You can
specify up to a hierarchy level of 1.
If unspecified, the default level is the full
bundle hierarchy.
Catalog Input
Input representation of the request to retrieve catalog records.
JSON example
This example shows how to retrieve catalogs that contain apple  in the catalog name.
{
"pageSize": 100,
"offset": 0,
"language": "french",
"filter": {
"criteria": [
{
"property": "name",
"operator": "contains",
"value": "apple"
}
]
}
}
This example shows how to retrieve catalogs with ServiceProcess  as the catalog type.
{
"pageSize": 100,
"offset": 0,
"sort": {
"orders": [
{
"property": "name",
"direction": "desc"
}
]
},
"filter": {
"criteria": [
{
"property": "catalogType",
"operator": "eq",
"value": "ServiceProcess"
}
152
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 167 =====

]
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
60.0OptionalCriteria to filter the records. Filters are
applicable to the fields of the
Filterfilter
ProductCatalog object. The supported
operators are:
• eq
• in
• contains
The supported properties are name and
catalogType.
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
60.0OptionalNumber of records to skip. The default
value is 0.
Integeroffset
60.0OptionalNumber of records per page. Valid values
are from 1 through 100. If unspecified,
defaults to 100.
IntegerpageSize
60.0OptionalSort order of the catalog records. The
supported operators are:
Sortsort
• asc
• desc
Criteria Input
Input representation of the filter criteria item request.
153
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 168 =====

JSON example
"criteria":
[{
"attributeType": "ProductStandard",
"property": "name",
"operator": "eq",
"value": "iPhone"
},
{
"criteriaType": "CustomWhereCondition",
"value": "(effectiveenddate = null OR effectiveenddate >= 2024-06-25)"
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalSearch attribute type of the facet for a
faceted search. Valid values are:
StringattributeType
• ProductStandard
• ProductCustom
• ProductDynamicAttribute
• ProductAttributeStandard
• ProductAttributeCustom
This property is applicable if the Use
Indexed Data For Product Listing and
Search toggle from the Product Discovery
Settings page from Setup is enabled.
60.0RequiredType of criteria for the filter. Valid value is:StringcriteriaType
• CustomWhereCondition
60.0RequiredOperator used for the filter criteria. The
supported operators are:
Stringoperator
• eq
• in
• contains—This value isn’t
applicable if the Use Indexed Data
For Product Listing and Search
toggle from the Product Discovery
Settings page from Setup is enabled.
• gt—Specifies a greater than criteria.
Available from API version 63.0 and
154
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 169 =====

Available
Version
Required or
Optional
DescriptionTypeName
later for Number, Date, and Datetime
data types only.
• lt—Specifies a less than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• gte—Specifies a greater than or
equal to criteria. Available from API
version 63.0 and later for Number,
Date, and Datetime data types only.
• lte—Specifies a less than or equal
to criteria. Available from API version
63.0 and later for Number, Date, and
Datetime data types only.
60.0RequiredProperty name to use in the filter, which
must be the same as the object field.
Stringproperty
60.0RequiredValue for the filter criteria.Objectvalue
Data Rounding Input
Input representation of the details of the data rounding input.
JSON example
{
"dataRowInputs": [
{
"key": "PRC1",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"unitOfMeasureId": "0hExx0000000001EAA"
},
{
"fieldApiName": "MinQuantity",
"originalValue": "987462848934739347.32232590183756545",
"unitOfMeasureId": "0hExx000000001dEAA"
}
]
},
{
"key": "PRC2",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
155
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 170 =====

"unitOfMeasureId": "uomId1"
},
{
"fieldApiName": "MinQuantity",
"originalValue": 987.4628,
"unitOfMeasureId": "Kgs Id"
}
]
},
{
"key": "PRC3",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 0.437584,
"unitOfMeasureId": "uomId2"
},
{
"fieldApiName": "MinQuantity",
"originalValue": 7364.58923,
"unitOfMeasureId": "uomId2"
}
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
63.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
63.0RequiredList of row inputs for rounding the data.Data Row Input[]dataRowInputs
Data Row Input
Input representation of the details of the input for a data rounding request.
JSON example
JSON example
{
"dataRowInputs": [
{
"key": "PRC1",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
156
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 171 =====

"originalValue": 1234.5678,
"unitOfMeasureId": "0hExx0000000001EAA"
},
{
"fieldApiName": "MinQuantity",
"originalValue": "987462848934739347.32232590183756545",
"unitOfMeasureId": "0hExx000000001dEAA"
}
]
},
{
"key": "PRC2",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"unitOfMeasureId": "uomId1"
},
{
"fieldApiName": "MinQuantity",
"originalValue": 987.4628,
"unitOfMeasureId": "Kgs Id"
}
]
},
{
"key": "PRC3",
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 0.437584,
"unitOfMeasureId": "uomId2"
},
{
"fieldApiName": "MinQuantity",
"originalValue": 7364.58923,
"unitOfMeasureId": "uomId2"
}
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
63.0RequiredList of field-level data inputs.Field Data Input[]fieldData
Inputs
63.0RequiredKey that identifies a unique data row.Stringkey
157
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 172 =====

Deep Clone Input
Input representation of the details of the object and associated record to be cloned.
JSON example
{
"mainRecordId": "01tSG0000028kcSYAQ",
"mainObjectApiName": "Product2",
"mainRecordFieldValues": {
"Name": "New Cloud Storage"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredAPI name of the object. The supported
object is Product2.
StringmainObject
ApiName
63.0OptionalMapping of the API name of the field to its
value. The values passed through this map
Map<String,
String>
mainRecord
FieldValues
are set for the created record. You can pass
the Name field only through this map.
63.0RequiredID of the record.StringmainRecordId
Field Data Input
Input representation of the details of the field data input.
JSON example
"fieldDataInputs": [
{
"fieldApiName": "MaxQuantity",
"originalValue": 0.437584,
"unitOfMeasureId": "uomId2"
},
{
"fieldApiName": "MinQuantity",
"originalValue": 7364.58923,
"unitOfMeasureId": "uomId2"
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredUnique API name of the field.StringfieldApiName
63.0RequiredOriginal value of the fields.StringoriginalValue
158
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 173 =====

Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredID of the unit of measure record that’s
associated to the field.
StringunitOf
MeasureId
Filter Input
Input representation of the filter request.
JSON example
"filter":
{
"criteria": [ {
"property": "name",
"operator": "eq",
"value": "iPhone"
},
{
"criteriaType": "CustomWhereCondition",
"value": "(effectiveenddate = null OR effectiveenddate >= 2024-06-25)"
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0Required if the
filter  property
is specified.
Details of the filter criteria.Criteria[]criteria
Include Object Input
Input representation of the object to include in the response.
JSON example
"includeObjects":
[{
"objectName": "ProductCategory"
}]
159
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 174 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0Required if the
options
property is specified.
Name of the object to include in the
response. The supported object is
ProductCategory.
StringobjectName
Index Configuration Collection Input
Input representation of the collection of index configurations.
JSON example
{
"correlationId": "8545b5aa-f3e6-429a-8f21-9cc4ce50b1d7",
"indexConfigurations": [
{
"attributeDefinitionId": "0tjT1000000002bIAA",
"name": "Color",
"type": "ProductDynamicAttribute",
"isSearchable": true
},
{
"attributeFieldId": "00Nxx000001FwnABII",
"name": "Message__c",
"type": "Custom",
"isSearchable": true
},
{
"name": "Code",
"type": "Standard",
"isSearchable": true
},
{
"facetDisplayRank": 1,
"isFacetable": false,
"isSearchable": true,
"name": "Family",
"type": "Standard"
}
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
160
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 175 =====

Available
Version
Required or
Optional
DescriptionTypeName
unspecified, a Universally Unique Identifier
(UUID) is generated.
62.0RequiredList of index configurations.Index Configuration
Input[]
index
Configurations
Index Configuration Input
Input representation of the request to persist the index configuration.
JSON example
"indexConfigurations": [
{
"attributeDefinitionId": "0tjT1000000002bIAA",
"name": "Color",
"type": "ProductDynamicAttribute",
"isSearchable": true
},
{
"attributeFieldId": "00Nxx000001FwnABII",
"name": "Message__c",
"type": "Custom",
"isSearchable": true
},
{
"name": "Code",
"type": "Standard",
"isSearchable": true
},
{
"facetDisplayRank": 1,
"isFacetable": false,
"isSearchable": true,
"name": "Family",
"type": "Standard"
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0Required if the
attribute
ID of the attribute definition.Stringattribute
DefinitionId
FieldIdproperty
isn’t specified.
62.0Required if the
attribute
ID of the attribute field.Stringattribute
FieldId
161
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 176 =====

Available
Version
Required or
Optional
DescriptionTypeName
DefinitionIdproperty
isn’t specified.
63.0OptionalSort order for displaying the facets at run
time.
Integerfacet
DisplayRank
63.0OptionalIndicates whether the field is facetable
(true) or not (false).
BooleanisFacetable
62.0OptionalIndicates whether the index-configured
field is searchable (true) or not (false).
BooleanisSearchable
62.0RequiredName of the index-configured field.Stringname
62.0RequiredType of the index-configured field.Stringtype
Index Setting Input
Input representation of the index setting.
JSON example
{
"setting" : {
"supportedLanguages" : ["en_US","ja","es","nl_NL"],
"defaultLanguage" : "en_US",
"productsGrouping": "GROUPING_VARIATION"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredObject containing the setting-related
details.
Setting Input[]setting
Options Input
Reserved for internal use.
Order Input
Input representation of the sort order item request.
JSON example
"sort":{
"orders":
[{
162
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 177 =====

"property": "name",
"direction": "asc"
}]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0RequiredDirection to sort the list items, such as in
ascending order or descending order.
Stringdirection
60.0RequiredProperty to use for the sorting of the list
items.
Stringproperty
Product Classification Details Input
Input representation of the request to fetch details of product classification records, including their attributes and attribute categories.
JSON example
{
"productClassificationIds": [
"01txx0000006iFMAAY",
"01txx0000006iGxAAY"
],
"catalogSystems": [
"epc"
]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalName of the catalog system. Valid value is:String[]catalogSystems
• epc—Enterprise Product Catalog
66.0RequiredList of product classification IDs for which
you want to retrieve product details. In the
String[]product
ClassificationIds
epc  catalog system, these values are the
Product2  record IDs.
Product Input
Input representation of a product in the catalog.
163
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 178 =====

JSON example
This example is a search request for products that contain Bundle Product  in the product name.
{
"catalogIds": [
"0ZST10000004D03OAE"
],
"language": "spanish",
"filter": {
"criteria": [
{
"property": "name",
"operator": "contains",
"value": "Bundle Product"
}
]
},
"relatedObjectFilters": [
{
"objectName": "ProductSpecificationRecType",
"criteria": [
{
"property": "IsCommercial",
"operator": "eq",
"value": false
}
],
"additionalFields": {
"Product2": {
"fields": [
"code__c"
]
}
}
}
]
}
This example is a search request for products that contain the specified search term in the product name and are part of a catalog.
{
"catalogIds": [
"0ZSDU0000002Og54AE"
],
"searchTerm": "Slack"
}
Query parameters
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalID of the product classification template
that contains a collection of dynamic
Stringproduct
Classification
Id attributes and can be reused to create
164
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 179 =====

Available
Version
Required or
Optional
DescriptionTypeName
multiple products. Products that are based
on a product classification inherit all the
attributes of the product classification.
Specify either the product classification ID,
list of category IDs, or list of catalog IDs to
retrieve products.
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalMap of the object and the list of standard
and custom fields to be queried along with
the standard response.
Map<String,
Additional Fields
Input>
additional
Fields
The supported object is Product2.
60.0OptionalList of comma-separated catalog IDs. The
API returns the list of product records that
List<String>catalogIds
are associated with the specified catalog
IDs.
Specify either the product classification ID,
list of category IDs, or list of catalog IDs to
retrieve products.
60.0OptionalList of comma-separated category IDs. The
API returns the list of product records that
List<String>categoryIds
are associated with the specified category
IDs. If unspecified, then returns all
products that are added to at least one
category.
Specify either the product classification ID,
list of category IDs, or list of catalog IDs to
retrieve products.
60.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
165
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 180 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalCriteria to filter the records. Filters are
applicable to the fields of Product2 object.
The supported operators are:
Criteria Inputfilter
• eq
• in
• contains—This value isn’t
applicable if the Use Indexed Data
For Product Listing and Search
toggle from the Product Discovery
Settings page from Setup is enabled.
• gt—Specifies a greater than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• lt—Specifies a less than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• gte—Specifies a greater than or
equal to criteria. Available from API
version 63.0 and later for Number,
Date, and Datetime data types only.
• lte—Specifies a less than or equal
to criteria. Available from API version
63.0 and later for Number, Date, and
Datetime data types only.
If multiple criteria are specified, then the
criteria are combined by using the and
operator.
The supported properties are name,
description, and isActive. If the
Use Indexed Data For Product Listing
and Search toggle from the Product
Discovery Settings page from Setup is
enabled, then the supported property is
name  only.
64.0OptionalCustom language that you can specify to
get translated data for the fields of an
Stringlanguage
object that's enabled for translation. See
Translate Product and Product Category
Data.
166
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 181 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalNumber of records to skip. The default
value is 0.
Integeroffset
60.0OptionalSpecifies the number of records per page.
Valid values are from 1 through 200. If the
value is unspecified, it defaults to 100.
IntegerpageSize
60.0OptionalCriteria for the related objects to filter the
records. The supported operator is eq. The
Related Object
Filter[]
relatedObject
Filters
supported object is
ProductSpecificationRecType.
The supported values are true  and
false. The supported property is
IsCommercial.
62.0OptionalString used to get products with the
product name containing the search term.
StringsearchTerm
See Search Considerations When Using
Indexed Data.
60.0OptionalSort order for the products.Sortsort
If the Use Indexed Data For Product
Listing and Search toggle from the
Product Discovery Settings page from
Setup is enabled, then you can sort
products by using name only.
Related Object Filters Input
Input representation of the request to filter related objects.
JSON example
"relatedObjectFilters":
[{
"criteria": [
{
"property": "IsCommercial",
"operator": "eq",
"value": true
}
],
"objectName": "ProductSpecificationRecType"
}]
167
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 182 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0Required if the
relatedObjectFilters
property is specified.
Criteria to filter the related objects.Criteria[]criteria
60.0Required if the
relatedObjectFilters
property is specified.
API name of the object that’s related to the
main object.
StringobjectName
Related Object Node Input
Input representation of the details of a related object node.
JSON example
"relatedObjectNodes": [
{
"relatedObjectAPIName": "ProductRampSegment",
"pageSize": 20,
"offSet": 0
},
{
"relatedObjectAPIName": "ProductUsageGrant",
"pageSize": 10,
"offSet": 0,
"filter": {
"criteria": [
{
"property": "status",
"operator": "eq",
"value": "active"
},
{
"property": "effectivestartdate",
"operator": "lte",
"value": "2024-06-25"
},
{
"criteriaType": "CustomWhereCondition",
"value": "(effectiveenddate = null OR effectiveenddate >= 2024-06-25)"
}
]
}
}
]
168
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 183 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalCriteria to filter records. The supported
properties are:
Criteria[]filter
• StartDate
• EndDate
• Status
The supported operators are:
• eq
• gte
• lte
The supported related object is
ProductUsageGrant.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and operator.
62.0OptionalNumber of records to skip. The default
value is 0.
IntegeroffSet
62.0OptionalNumber of records per page. Valid values
are from 1 through 100. If unspecified, the
default value is 100.
IntegerpageSize
62.0RequiredAPI name of the related object to return
the records for. The supported related
StringrelatedObject
APIName
objects are ProductRampSegment and
ProductUsageGrant.
Related Records Input
Input representation of the request to retrieve related ProductRampSegment or ProductUsageGrant records for Product2 object.
JSON example
{
"recordIds": [
"01txx0000006i44AAA",
"01txx0000006i5gAAA"
],
"relatedObjectNodes": [
{
"relatedObjectAPIName": "ProductRampSegment",
"pageSize": 20,
"offSet": 0
},
169
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 184 =====

{
"relatedObjectAPIName": "ProductUsageGrant",
"pageSize": 10,
"offSet": 0,
"filter": {
"criteria": [
{
"property": "status",
"operator": "eq",
"value": "active"
},
{
"property": "effectivestartdate",
"operator": "lte",
"value": "2024-06-25"
},
{
"criteriaType": "CustomWhereCondition",
"value": "(effectiveenddate = null OR effectiveenddate >= 2024-06-25)"
}
]
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
62.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
62.0RequiredList of record IDs to return the
relatedObjects records for. The maximum
number of record IDs supported is 20.
String[]recordIds
62.0RequiredList of nodes for the related objects. The
maximum number of related object nodes
supported is two.
Related Object
Node Input[]
related
ObjectNodes
Run-time Catalog Snapshot Input
Input representation of the details of a run-time catalog snapshot for deployment.
JSON example
"snapshot": {
"activationType": "IMMEDIATE",
"activationDate": "2024-05-06T05:12:59.000Z",
170
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 185 =====

"id": "1Avxx0000005DFe1AM"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalActivation date of the snapshot.StringactivationDate
62.0RequiredActivation type of the snapshot. Valid value
is:
StringactivationType
• IMMEDIATE—Snapshot is activated
immediately after a successful build.
62.0RequiredID of the snapshot.Stringid
Setting Input
Input representation of the details of the index setting.
JSON example
"setting" : {
"supportedLanguages" : ["en_US","ja","es","nl_NL"],
"defaultLanguage" : "en_US"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0RequiredDefault language for the API.Stringdefault
Language
63.0RequiredList of supported language locales for
indexing.
String[]supported
Languages
Snapshot Deployment Input
Input representation of the request to deploy a run-time catalog snapshot.
JSON example
This example shows a sample request to build a new snapshot with immediate activation.
{
"snapshot": {
"activationType": "IMMEDIATE"
},
"buildType": "FULL"
}
171
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 186 =====

This example shows a sample request to rebuild a snapshot in the active  status.
{
"snapshot": {
"activationType": "IMMEDIATE",
"id": "1Avxx0000005DFe1AM"
},
"buildType": "FULL"
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0RequiredBuild type of the snapshot index. Valid
value is:
StringbuildType
• FULL—Specifies a full index build.
• INCREMENTAL—Specifies an
incremental index build. Available
from API version 63.0 and later.
62.0RequiredSnapshot to deploy.Run-time Catalog
Snapshot Input[]
snapshot
Sort Input
Input representation of the sort request.
JSON example
"sort":
{
"orders":
[{
"property": "name",
"direction": "asc"
}]
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0Required if the
sort  property is
specified.
Details of the sort order.Order[]orders
Response Bodies
Learn more about the available Product Catalog Management API response bodies.
172
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 187 =====

Attribute Category
Output representation of the attribute category.
Attribute Definition
Output representation of the attribute definition.
Attribute Picklist
Output representation of the attribute picklist.
Attribute Picklist Value
Output representation of the attribute picklist value.
Bulk Unit Of Measure Info
Output representation of the details of the unit of measure records along with error details.
Data Rounding
Output representation of the data rounding response.
Data Row
Output representation of the details of a data row.
Catalog Output
Output representation of the catalog definition.
Catalogs Output
Output representation of the retrieved catalog result.
Categories Output
Output representation of the retrieved categories result.
Category Output
Output representation of the category definition.
Deep Clone Error
Output representation of the error details related to the deep clone request.
Deep Clone Record Response
Output representation of the details of the cloned related records.
Deep Clone Response
Output representation of the details of the cloned record.
Error Output
Output representation of the error details.
Facet Value
Output representation of the facet values found in the search result.
Field Data
Output representation of the field data.
Fields Info
Output representation of the metadata fields in an object.
Index Configuration Collection
Output representation of the collection of index configuration details.
Index Configuration Field
Output representation of the details of the index-configured field.
173
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 188 =====

Index Configurations Update
Output representation of the updated index configuration.
Index Error
Output representation of the error details related to an index.
Index Setting
Output representation of the retrieved index settings.
Index Setting Update
Output representation of the details of the updated index setting.
Invalid Related Object Node
Output representation of the invalid related object node with details of errors.
Metadata
Output representation of the metadata details for objects.
Object Info
Output representation of the object details along with its fields.
Product Catalog Management Error
Output representation that contains error details, including error codes and messages.
Product Classification
Output representation of the product classification details.
Product Classification Details
Output representation that contains the details of a single product classification, including its attributes and categories.
Product Classification Details Collection
Output representation that contains a collection of product classification details along with any processing errors.
Product Component Group
Output representation of the product component group.
Product
Output representation of the product definition.
Product Related Component
Output representation of the product-related component.
Product Selling Model
Output representation of the definition of the product selling model.
Product Selling Model Option
Output representation of the definition of the product selling model option.
Product Specification Type
Output representation of the product specification type.
Products
Output representation of the list of retrieved products.
Related Object Records
Output representation of the related records for a specified record ID and related object API name.
Related Records
Output representation of the list of relatedObject records for a specified record ID.
174
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 189 =====

Related Records List
Output representation of the list of related records.
Search Facet
Output representation of the details of the faceted search.
Setting
Output representation of the setting that’s used in indexing.
Setting Metadata
Output representation of the metadata associated with a setting.
Snapshot
Output representation of the list of active snapshots.
Snapshot Collection
Output representation of the retrieved snapshot collection.
Snapshot Deployment
Output representation of the snapshot deployment.
Snapshot Index
Output representation of the snapshot index of a run-time catalog.
Snapshot Index Error
Output representation of the error details related to a snapshot index.
Snapshot Index Info
Output representation of the details of a snapshot index.
Snapshot Index Log
Output representation of a snapshot index log.
Status
Output representation of the status of the request.
Unit of Measure Error
Output representation of the details of errors encountered during the processing of the Unit of Measure API request.
Unit of Measure Info
Output representation of the details of a unit of measure record.
Unit of Measure Status
Output representation of the status of the Unit of Measure API request.
Attribute Category
Output representation of the attribute category.
JSON example
"attributeCategory": [
{
"attributes": [
{
"additionalFields": {
"scope": "Order"
},
175
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 190 =====

"attributeNameOverride": "AD Text",
"code": "AD02",
"dataType": "Text",
"defaultValue": "AD Text DV",
"description": "AD Text Desc",
"displayType": "Text",
"helpText": "AD Text DHT",
"id": "0tjT1000000002bIAA",
"isHidden": false,
"isPriceImpacting": true,
"isReadOnly": true,
"isRequired": true,
"label": "AD Text Label",
"maximumCharacterCount": "20",
"maximumValue": "100",
"minimumCharacterCount": "1",
"minimumValue": "50",
"name": "AD Text",
"sequence": 1,
"status": "Active",
"valueDescription": "AD Text VD"
}
],
"code": "AC001",
"id": "0v3T1000000000BIAQ",
"name": "build and make"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0List of categorized attributes associated with
the product.
Attribute Definition[]attributes
60.0Small, 60.0Code of the attribute category.Stringcode
60.0Small, 60.0ID associated with the attribute category.Stringid
60.0Small, 60.0Name of the attribute category. If data
translation is set up and specified in the org,
the translated description is available.
Stringname
Attribute Definition
Output representation of the attribute definition.
JSON example
"attributes": [
{
"additionalFields": {
"scope": "Order"
},
176
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 191 =====

"attributeNameOverride": "AD Text",
"code": "AD02",
"dataType": "Text",
"defaultValue": "AD Text DV",
"description": "AD Text Desc",
"displayType": "Text",
"helpText": "AD Text DHT",
"id": "0tjT1000000002bIAA",
"isHidden": false,
"isPriceImpacting": true,
"isReadOnly": true,
"isRequired": true,
"label": "AD Text Label",
"maximumCharacterCount": 20,
"maximumValue": "100",
"minimumCharacterCount": 1,
"minimumValue": "50",
"name": "AD Text",
"sequence": 1,
"status": "Active",
"valueDescription": "AD Text VD"
}
],
"code": "AC001",
"id": "0v3T1000000000BIAQ",
"name": "build and make"
}]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
61.0Small, 61.0Key-value pair of additional standard or
custom fields to include in the response.
Map<String,
Additional Fields
Input>
additional
Fields
60.0Small, 60.0Name to display for the attribute, which
overrides the name on the attribute. For
StringattributeName
Override
example, the Color attribute is overridden
to display as Laptop Color.
60.0Small, 60.0Unique code of the attribute definition.Stringcode
60.0Small, 60.0Data type of the attribute definition value.StringdataType
60.0Small, 60.0Default value of the attribute.StringdefaultValue
60.0Small, 60.0Description of the attribute.Stringdescription
60.0Small, 60.0Display types of the attribute. Valid values
are:
StringdisplayType
• Radio Button
• Checkbox
• Toggle
177
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 192 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
• Input Date
• DateTime
• Currency Symbol
• Currency Code
• Currency Name
• Percentage
• Text
• Combobox
• Radio Button
• MultiSelect
• MultiSelectCheckboxes
60.0Small, 60.0Help text that appears at run time for the
attribute. If data translation is set up and
StringhelpText
specified in the org, the translated
description is available.
60.0Small, 60.0ID of the attribute definition.Stringid
60.0Small, 60.0Reserved for future use.Booleanis
Configurable
60.0Small, 60.0Indicates whether to hide the attribute from
the users in the order capture interface
(true) or not (false).
BooleanisHidden
60.0Small, 60.0Indicates whether the attribute impacts the
product price (true) or not (false).
BooleanisPrice
Impacting
60.0Small, 60.0Indicates whether the product attribute is
read-only for the end users in the order
capture page (true) or not (false).
BooleanisReadOnly
60.0Small, 60.0Indicates whether a value for the attribute
is required for the assigned parent object
(true) or not (false).
BooleanisRequired
60.0Small, 60.0Reserved for future use.BooleanisValue
Cloneable
60.0Small, 60.0Label of the attribute. If data translation is
set up and specified in the org, the
translated description is available.
Stringlabel
60.0Small, 60.0Maximum number of alphanumeric
characters that can be entered for attributes
of type number and text in run time.
Integermaximum
Character
Count
178
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 193 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Maximum value that can be entered for
attributes of type number, currency, and
percent in run time.
StringmaximumValue
60.0Small, 60.0Minimum number of alphanumeric
characters that can be entered for attributes
Integerminimum
Character
Count of type number and text in run time. The
minimum character count must be less than
or equal to the maximum character count.
60.0Small, 60.0Minimum value that can be entered for
attributes of type number, currency, and
StringminimumValue
percent in run time. The minimum value
must be less than or equal to the maximum
value.
60.0Small, 60.0Name of the attribute.Stringname
60.0Small, 60.0ID of the attribute picklist that provides the
valid values for the attribute.
Attribute Picklistpicklist
60.0Small, 60.0Order in which the attribute values appear
in the attribute definition when the product
is configured at run time.
Integersequence
60.0Small, 60.0Lifecycle state of the attribute picklist. Valid
values are:
Stringstatus
• Active
• Draft
• Inactive
60.0Small, 60.0Reserved for future use.StringstepValue
60.0Small, 60.0Reserved for future use.StringvalueDecoder
60.0Small, 60.0Description of the value assigned to the
attribute.
Stringvalue
Description
Attribute Picklist
Output representation of the attribute picklist.
JSON example
"picklist": {
"dataType": "Text",
"description": "Fabric Module options",
"id": "0v51Q000000TNDkQAO",
"name": "Fabric Module options",
"values": [
179
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 194 =====

{
"abbreviation": "IFM1"
"code": "PV0051",
"displayValue": "25G Intelligent Fabric Module with 8x 25G SFP28 ports",
"id": "0v61Q0000008OMYQA2",
"name": "25G Intelligent Fabric Module with 8x 25G SFP28 ports",
"sequence": "1",
"value": "25G Intelligent Fabric Module with 8x 25G SFP28 ports",
"status" : "Active"
},
{
"abbreviation": "IFM2"
"code": "PV0052",
"displayValue": "100G Intelligent Fabric Module with 8x 100G QSFP28 ports",
"id": "0v61Q0000008OMZQA2",
"name": "100G Intelligent Fabric Module with 8x 100G QSFP28 ports",
"sequence": "2",
"value": "100G Intelligent Fabric Module with 8x 100G QSFP28 ports",
"status" : "Active"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Data type of the values in the picklist. Valid
values are:
StringdataType
• Boolean
• Date
• Datetime
• Number
• Text
• Currency
• Percent
60.0Small, 60.0Description of the picklist, such as the
picklist purpose or the associated product.
Stringdescription
60.0Small, 60.0ID associated with the attribute picklist
record.
Stringid
60.0Small, 60.0Name of the picklist value.Stringname
60.0Small, 60.0List of values associated with the picklist.Attribute Picklist
Value[]
values
Attribute Picklist Value
Output representation of the attribute picklist value.
180
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 195 =====

JSON example
"values": [
{
"abbreviation": "IFM1"
"code": "PV0051",
"displayValue": "25G Intelligent Fabric Module with 8x 25G SFP28 ports",
"id": "0v61Q0000008OMYQA2",
"name": "25G Intelligent Fabric Module with 8x 25G SFP28 ports",
"sequence": "1",
"value": "25G Intelligent Fabric Module with 8x 25G SFP28 ports",
"status" : "Active"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Name of the picklist value that appears at
run time.
Stringabbreviation
60.0Small, 60.0Unique code of the picklist value within the
picklist.
Stringcode
60.0Small, 60.0Picklist value that appears at run time in the
order capture page. If data translation is set
StringdisplayValue
up and specified in the org, the translated
description is available.
60.0Small, 60.0ID associated with the attribute picklist
value.
Stringid
60.0Small, 60.0Name of the picklist value.Stringname
60.0Small, 60.0Order in which the picklist value appears in
the picklist.
Stringsequence
62.0Small, 62.0Status of the attribute picklist value.Stringstatus
60.0Small, 60.0Value of the picklist item. Value must be
unique within the picklist.
Stringvalue
Bulk Unit Of Measure Info
Output representation of the details of the unit of measure records along with error details.
JSON example
{
"correlationId": "928ea35f-8a2f-4932-9f7e-ec6cdbcabdbe",
"errorCodeToErrorMap": {
"UNIT_OF_MEASURE_INFO_INVALID_UOM_IDS": {
"errorCode": "UOM_INFO_API_003",
"messageDetail": "Invalid uomId is passed. Please specify a valid uomId.",
"messageTitle": "Invalid uomId is passed.",
181
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 196 =====

"recordIds": [
"sample"
],
"source": "Unit_Of_Measure_Info_Api"
}
},
"status": {
"errors": [],
"httpStatusCode": "200",
"message": " Successfully fetched UnitOfMeasure Info. "
},
"uomIdToUnitOfMeasureInfo": {
"0hEU200000003M5MAI": {
"id": "0hEU200000003M5MAI",
"name": "Pounds",
"roundingMethod": "Nearest",
"scale": 1,
"unitCode": "Pounds"
},
"0hEU200000003KTMAY": {
"id": "0hEU200000003KTMAY",
"name": "Grams",
"roundingMethod": "Down",
"scale": 5,
"unitCode": "Grams"
}
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
63.0Small, 63.0Error codes mapped to their details.Map<String, Unit Of
Measure Error>
errorCode
ToErrorMap
63.0Small, 63.0Status of the API request.Unit Of Measure
Status[]
status
63.0Small, 63.0Unit of measure record IDs mapped to their
details.
Map<String, Unit Of
Measure Info>
uomIdToUnit
OfMeasureInfo
Data Rounding
Output representation of the data rounding response.
182
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 197 =====

JSON example
{
"keyToUomDataRowOutput": {
"PRC1": {
"key": "PRC1",
"fieldApiNameToFieldDataOutput": {
"MaxQuantity": {
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"isRoundingApplicable": true,
"roundedValue": 1234.56,
"unitOfMeasureId": "uomId1",
"errorCodeToErrorMap" : []
},
"MinQuantity": {
"fieldApiName": "MinQuantity",
"originalValue": 643.1,
"isRoundingApplicable": true,
"roundedValue": 643.1,
"unitOfMeasureId": "uomId1"
}
},
"errorCodeToErrorMap" : []
},
"PRC2": {
"key": "PRC2",
"fieldApiNameToFieldDataOutput": {
"MaxQuantity": {
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"isRoundingApplicable": true,
"roundedValue": 1234.56,
"unitOfMeasureId": "uomId1"
},
"MinQuantity": {
"fieldApiName": "MinQuantity",
"originalValue": 987.4628,
"isRoundingApplicable": true,
"errorCodeToErrorMap": {
"message": "arithrmetic operation"
},
"unitOfMeasureId": "uomId1"
}
},
"errorCodeToErrorMap": []
},
"PRC3": {
"key": "PRC3",
"fieldApiNameToFieldDataOutput": {
"MaxQuantity": {
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"isRoundingApplicable": false,
183
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 198 =====

"unitOfMeasureId": "uomId2"
},
"MinQuantity": {
"fieldApiName": "MinQuantity",
"originalValue": 987.4628,
"isRoundingApplicable": false,
"unitOfMeasureId": "uomId2"
}
},
"errorCodeToErrorMap": []
}
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
63.0Small, 63.0Error codes mapped to their details.Map<String, Unit Of
Measure Error>
errorCode
ToErrorMap
63.0Small, 63.0Data row key mapped to the associated data
row.
Map<String, Data
Row>
keyToData
RowOutput
63.0Small, 63.0Status of the API request.Unit Of Measure
Status[]
status
Data Row
Output representation of the details of a data row.
JSON example
{
"keyToUomDataRowOutput": {
"PRC1": {
"key": "PRC1",
"fieldApiNameToFieldDataOutput": {
"MaxQuantity": {
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"isRoundingApplicable": true,
"roundedValue": 1234.56,
"unitOfMeasureId": "uomId1",
"errorCodeToErrorMap" : []
},
"MinQuantity": {
"fieldApiName": "MinQuantity",
"originalValue": 643.1,
184
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 199 =====

"isRoundingApplicable": true,
"roundedValue": 643.1,
"unitOfMeasureId": "uomId1"
}
},
"errorCodeToErrorMap" : []
},
"PRC2": {
"key": "PRC2",
"fieldApiNameToFieldDataOutput": {
"MaxQuantity": {
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"isRoundingApplicable": true,
"roundedValue": 1234.56,
"unitOfMeasureId": "uomId1"
},
"MinQuantity": {
"fieldApiName": "MinQuantity",
"originalValue": 987.4628,
"isRoundingApplicable": true,
"errorCodeToErrorMap": {
"message": "arithrmetic operation"
},
"unitOfMeasureId": "uomId1"
}
},
"errorCodeToErrorMap": []
},
"PRC3": {
"key": "PRC3",
"fieldApiNameToFieldDataOutput": {
"MaxQuantity": {
"fieldApiName": "MaxQuantity",
"originalValue": 1234.5678,
"isRoundingApplicable": false,
"unitOfMeasureId": "uomId2"
},
"MinQuantity": {
"fieldApiName": "MinQuantity",
"originalValue": 987.4628,
"isRoundingApplicable": false,
"unitOfMeasureId": "uomId2"
}
},
"errorCodeToErrorMap": []
}
}
}
185
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 200 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Map of error codes to their details.Map<String, Unit Of
Measure Error>
errorCode
ToErrorMap
63.0Small, 63.0Map of field API name to associated field
data.
Map<String, Field
Data>
fieldApi
NameToField
DataOutput
63.0Small, 63.0Unique key of the data row.Stringkey
Catalog Output
Output representation of the catalog definition.
JSON example
catalogs": [
{
"catalogType": "Sales",
"code": "CAT009",
"description": "SmartBytes B2B Catalog",
"effectiveEndDate": "31-07-2023",
"effectiveStartDate": "24-07-2023",
"id": "0ZS1Q000000XbZAWA0",
"name": "SmartBytes B2B Catalog",
"numberOfCategories": 8
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0The category of an entry in the catalog,
which is customizable. For example, catalog
StringcatalogType
types, such as sellable products, services,
parts, technical services, or technical
resources.
60.0Small, 60.0Unique ID associated with the catalog.Stringcode
60.0Small, 60.0Description of the catalog. If data translation
is set up and specified in the org, the
translated description is available.
Stringdescription
60.0Small, 60.0Date and time from when the catalog isn't
available to the end users.
Stringeffective
EndDate
60.0Small, 60.0Date and time from when the catalog is
available to the end users.
Stringeffective
StartDate
60.0Small, 60.0ID of the catalog.Stringid
186
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 201 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Name of the catalog. If data translation is
set up and specified in the org, the
translated description is available.
Stringname
60.0Small, 60.0Number of categories in the catalog.IntegernumberOf
Categories
Catalogs Output
Output representation of the retrieved catalog result.
JSON example
{
"catalogs": [
{
"catalogType": "Sales",
"code": "CAT009",
"id": "0ZS1Q000000XbZAWA0",
"name": "SmartBytes B2B Catalog",
"numberOfCategories": 8
}
],
"correlationId": "0b7b6a30-895c-407a-91b3-e67482d339a3",
"count": 1,
"status": {
"code": "200",
"errors": [],
"message": "Successfully fetched the catalog records."
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0List of the catalogs.Catalog Output[]catalogs
60.0Small, 60.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
60.0Small, 60.0Total number of the catalog records
retrieved after the query execution, wherein
Integercount
the pageSize  property determines the
number of records returned in every page.
60.0Small, 60.0Status of the request.Statusstatus
187
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 202 =====

Categories Output
Output representation of the retrieved categories result.
JSON example
{
"categories": [
{
"catalogId": "0ZS1Q000000XbZAWA0",
"code": "B2B Category",
"description": "Products Category",
"hasSubCategories": true,
"id": "0ZG1Q000000XbVGWA0",
"name": "Unified Computing",
"numberOfProducts": 2,
"parentCategoryId": "0ZGT100000000qlOAA",
"sortOrder": 2,
"subCategories": [],
"isNavigational: false
}
],
"correlationId": "30230973-0a09-405e-b148-f085bb6dd66e",
"status": {
"code": "200",
"errors": [],
"message": "Successfully fetched the category records."
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0List of the retrieved categories.Category Output[]categories
60.0Small, 60.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
60.0Small, 60.0Status of the request.Statusstatus
Category Output
Output representation of the category definition.
JSON example
"categories": [
{
"catalogId": "0ZS1Q000000XbZAWA0",
"code": "B2B Category",
"description": "Products Category",
"hasSubCategories": true,
188
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 203 =====

"id": "0ZG1Q000000XbVGWA0",
"name": "Unified Computing",
"numberOfProducts": 2,
"parentCategoryId": "0ZGT100000000qlOAA",
"sortOrder": 2,
"subCategories": [],
"isNavigational: false
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the catalog that the category is
associated with.
StringcatalogId
60.0Small, 60.0Unique code of the product category.Stringcode
60.0Small, 60.0Description of the category. If data
translation is set up and specified in the org,
the translated description is available.
Stringdescription
60.0Small, 60.0Indicates whether the subcategories are
available (true) or not (false).
BooleanhasSub
Categories
60.0Small, 60.0ID of the category.Stringid
62.0Small, 62.0Indicates whether the category node is
navigational (true) or not (false).
BooleanisNavigational
60.0Small, 60.0Name of the category. If data translation is
set up and specified in the org, the
translated name is available.
Stringname
60.0Small, 60.0Number of products associated with the
category.
IntegernumberOf
Products
60.0Small, 60.0ID of the parent category.Stringparent
CategoryId
60.0Small, 60.0Display order of the product category
relative to the siblings with the same parent
category.
IntegersortOrder
60.0Small, 60.0List of subcategories, if available. This
property is returned with the Categories List
(GET) API response.
Category Output[]subCategories
Deep Clone Error
Output representation of the error details related to the deep clone request.
189
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 204 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Code of the error message related to the
deep clone request.
StringerrorCode
63.0Small, 63.0Details of the error message related to the
deep clone request.
StringerrorMessage
Deep Clone Record Response
Output representation of the details of the cloned related records.
JSON example
"createdRecordList": [
{
"createdRecordId": "01tSG0000030Yb3YAE",
"entityApiName": "Product2",
"entityLabel": "Product"
},
{
"createdRecordId": "0iOSG0000002rMn2AI",
"entityApiName": "ProductSellingModelOption",
"entityLabel": "Product Selling Model Option"
},
{
"createdRecordId": "0v7SG0000001ktdYAA",
"entityApiName": "ProductAttributeDefinition",
"entityLabel": "Product Attribute Definition"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0ID of the created related record.Stringcreated
RecordId
63.0Small, 63.0API name of the created object.StringentityApiName
63.0Small, 63.0Label of the created object.StringentityLabel
Deep Clone Response
Output representation of the details of the cloned record.
JSON example
{
"createdRecordList": [
{
"createdRecordId": "01tSG0000030Yb3YAE",
"entityApiName": "Product2",
190
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 205 =====

"entityLabel": "Product"
},
{
"createdRecordId": "0iOSG0000002rMn2AI",
"entityApiName": "ProductSellingModelOption",
"entityLabel": "Product Selling Model Option"
},
{
"createdRecordId": "0v7SG0000001ktdYAA",
"entityApiName": "ProductAttributeDefinition",
"entityLabel": "Product Attribute Definition"
}
],
"createdRootRecordId": "01tSG0000030Yb3YAE",
"errorList": [],
"isSuccessful": true
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of cloned related records of the main
record.
Deep Clone Record
Response[]
created
RecordList
63.0Small, 63.0ID of the created root record.StringcreatedRoot
RecordId
63.0Small, 63.0Details of errors, if any.Deep Clone Error[]errorList
63.0Small, 63.0Error message if the API request fails.StringerrorMessage
63.0Small, 63.0Indicates whether the API request is
successful (true) or not (false).
BooleanisSuccessful
Error Output
Output representation of the error details.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Code of the error message.StringerrorCode
60.0Small, 60.0Details of the error message.StringmessageDetail
60.0Small, 60.0Title of the error message.StringmessageTitle
61.0Small, 61.0ID of the product node.StringnodeProductId
60.0Small, 60.0ID of the record.StringrecordId
60.0Small, 60.0Name of the record.StringrecordName
62.0Small, 62.0List of related object nodes with errors.Invalid Related
Object Node[]
related
ObjectNodes
191
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 206 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Name of the API that’s the source of the
error.
Stringsource
Facet Value
Output representation of the facet values found in the search result.
JSON example
"values": [
{
"displayName": "Simple",
"nameOrId": "Simple",
"productCount": 9
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Display name of the facet value.StringdisplayName
63.0Small, 63.0Facet value name or ID. Reserved for internal
use.
StringnameOrId
63.0Small, 63.0Number of products in the search result that
match the facet value.
productCount
Field Data
Output representation of the field data.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Error codes mapped to their details.Map<String, Unit Of
Measure Error>
errorCode
ToErrorMap
63.0Small, 63.0Unique API Name of the field.StringfieldApiName
63.0Small, 63.0Indicates whether data rounding is
applicable to the decimal (true) or not
(false).
BooleanisRounding
Applicable
63.0Small, 63.0Original value of the field.StringoriginalValue
63.0Small, 63.0Rounded field value that corresponds to the
original value, if data rounding is applicable.
StringroundedValue
192
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 207 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0ID of the unit of measure record that’s
associated to the field.
StringunitOf
MeasureId
Fields Info
Output representation of the metadata fields in an object.
JSON example
"fields": [
{
"dataType": "text",
"isFacetableConfigurable": true,
"isSearchableConfigurable": false,
"label": "Product Name",
"name": "Name",
"type": "Standard"
},
{
"dataType": "multilinetext",
"isFacetableConfigurable": false,
"isSearchableConfigurable": true,
"label": "Product Description",
"name": "Description",
"type": "Standard"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0ID of the custom field.StringcustomFieldId
62.0Small, 62.0Type of data.StringdataType
62.0Small, 62.0Reserved for internal use.Booleanis
Configurable
Small, 63.0Small, 63.0Indicates whether the field is facetable
(true) or not (false).
BooleanisFacetable
Configurable
Small, 63.0Small, 63.0Indicates whether the field is searchable
(true) or not (false).
BooleanisSearchable
Configurable
62.0Small, 62.0Label of the object field.Stringlabel
62.0Small, 62.0Name of the object field.Stringname
62.0Small, 62.0Type of the object field.Stringtype
193
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 208 =====

Index Configuration Collection
Output representation of the collection of index configuration details.
JSON example
{
"correlationId": "ad960cb6-392d-4d11-bac3-3824baedf67e",
"errors": [],
"indexConfigurations": [
{
"isSearchable": true,
"name": "Name",
"type": "Standard"
}
],
"metadata": {
"objectInfos": [
{
"fields": [
{
"dataType": "text",
"isFacetableConfigurable": true,
"isSearchableConfigurable": false,
"label": "Product Name",
"name": "Name",
"type": "Standard"
},
{
"dataType": "multilinetext",
"isFacetableConfigurable": false,
"isSearchableConfigurable": true,
"label": "Product Description",
"name": "Description",
"type": "Standard"
}
],
"name": "Product2"
},
{
"fields": [
{
"dataType": "stringplusclob",
"label": "Description",
"name": "Description",
"type": "ProductAttributeDefinitionStandard"
},
{
"dataType": "text",
"label": "Name",
"name": "Name",
"type": "ProductAttributeDefinitionStandard"
},
],
"name": "ProductAttributeDefinition"
}
194
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 209 =====

]
},
"statusCode": "200"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
62.0Small, 62.0List of errors, if any.Error Output[]errors
62.0Small, 62.0Details of the index-configured fields.Index Configuration
Field[]
index
Configurations
62.0Small, 62.0Details of the metadata for objects.Metadata[]metadata
62.0Small, 62.0Code that indicates the status of the request.StringstatusCode
Index Configuration Field
Output representation of the details of the index-configured field.
JSON example
"indexConfigurations": [
{
"attributeDefinitionId": "0tjT1000000002bIAA",
"name": "Color",
"type": "ProductDynamicAttribute",
"isSearchable": true
},
{
"attributeFieldId": "00Nxx000001FwnABII",
"name": "Message__c",
"type": "Custom",
"isSearchable": true
},
{
"name": "Code",
"type": "Standard",
"isSearchable": true
},
{
"facetDisplayRank": 1,
"isFacetable": false,
"isSearchable": true,
"name": "Family",
"type": "Standard"
195
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 210 =====

}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0ID of the attribute definition.Stringattribute
DefinitionId
62.0Small, 62.0ID of the attribute field.Stringattribute
FieldId
63.0Small, 63.0Sort order for displaying the facets at run
time.
IntegerfacetDisplay
Rank
63.0Small, 63.0Indicates whether the field is facetable
(true) or not (false).
BooleanisFacetable
62.0Small, 62.0Indicates whether the index-configured field
is searchable (true) or not (false).
BooleanisSearchable
62.0Small, 62.0Name of the index-configured field.Stringname
62.0Small, 62.0Type of the index-configured field.Stringtype
Index Configurations Update
Output representation of the updated index configuration.
JSON example
{
"correlationId": "8545b5aa-f3e6-429a-8f21-9cc4ce50b1d7",
"errors": [],
"indexConfigurations": [
{
"attributeDefinitionId": "0tjT1000000002bIAA",
"name": "Color",
"type": "ProductDynamicAttribute",
"isSearchable": true
},
{
"attributeFieldId": "00Nxx000001FwnABII",
"name": "Message__c",
"type": "Custom",
"isSearchable": true
},
{
"name": "Code",
"type": "Standard",
"isSearchable": true
},
{
"facetDisplayRank": 1,
"isFacetable": false,
196
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 211 =====

"isSearchable": true,
"name": "Family",
"type": "Standard"
}
],
"statusCode": "200"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
62.0Small, 62.0List of errors, if any.Error Output[]errors
62.0Small, 62.0Details of the index-configured fields.Index Configuration
Field[]
index
Configurations
62.0Small, 62.0Code that indicates the status of the request.StringstatusCode
Index Error
Output representation of the error details related to an index.
JSON example
"indexErrorDetails": {
"errorFileId": "069xx0000004C92AAE",
"indexCreatedDate": "2024-10-03T05:24:18.000Z",
"indexErrorsCount": 1,
"indexLastUpdatedDate": "2024-10-03T05:27:00.000Z",
"itemLevelErrorsCount": 1
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0ID of the exported error file that contains
the index errors.
StringerrorFileId
63.0Small, 63.0Date on which the index was created.StringindexCreated
Date
63.0Small, 63.0Number of index-level errors.Integerindex
ErrorsCount
63.0Small, 63.0Date on which the index was last updated.StringindexLast
UpdatedDate
197
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 212 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Number of item-level errors.IntegeritemLevel
ErrorsCount
Index Setting
Output representation of the retrieved index settings.
JSON example
{
"errors": [],
"metadata": {
"activeLanguages": ["en_US","ja","es","nl_NL"]
},
"setting": {
"defaultLanguage": "en_US",
"id": "1JySG0000000GUb0AM",
"supportedLanguages": ["en_US","ja","es","nl_NL"]
},
"statusCode": "200"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of errors, if any.Error Output[]errors
63.0Small, 63.0Metadata associated with the setting.Setting Metadata[]metadata
63.0Small, 63.0Setting that’s used in indexing and
maintained for an org.
Setting[]setting
63.0Small, 63.0Code that indicates the status of the request.StringstatusCode
Index Setting Update
Output representation of the details of the updated index setting.
JSON example
{
"setting" : {
"supportedLanguages" : ["en_US","ja","es","nl_NL"],
"id": "1JySG0000000GUb0AM",
"defaultLanguage" : "en_US"
},
"errors" : [],
"statusCode" : "200"
}
198
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 213 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of errors, if any.Error Output[]errors
63.0Small, 63.0Setting that’s used in indexing and
maintained for an org.
Setting[]setting
63.0Small, 63.0Code that indicates the status of the API
request.
StringstatusCode
Invalid Related Object Node
Output representation of the invalid related object node with details of errors.
JSON example
To add
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0List of error messages.String[]errorMessages
62.0Small, 62.0API name of the related object.StringrelatedObject
APIName
Metadata
Output representation of the metadata details for objects.
JSON example
"metadata": {
"objectInfos": [
{
"fields": [
{
"dataType": "text",
"isFacetableConfigurable": true,
"isSearchableConfigurable": false,
"label": "Product Name",
"name": "Name",
"type": "Standard"
},
{
"dataType": "multilinetext",
"isFacetableConfigurable": false,
"isSearchableConfigurable": true,
"label": "Product Description",
"name": "Description",
"type": "Standard"
}
],
199
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 214 =====

"name": "Product2"
},
{
"fields": [
{
"dataType": "stringplusclob",
"label": "Description",
"name": "Description",
"type": "ProductAttributeDefinitionStandard"
},
{
"dataType": "text",
"label": "Name",
"name": "Name",
"type": "ProductAttributeDefinitionStandard"
},
],
"name": "ProductAttributeDefinition"
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Metadata details for objects.Object Info[]objectInfos
Object Info
Output representation of the object details along with its fields.
JSON example
"objectInfos": [
{
"fields": [
{
"dataType": "text",
"isFacetableConfigurable": true,
"isSearchableConfigurable": false,
"label": "Product Name",
"name": "Name",
"type": "Standard"
},
{
"dataType": "multilinetext",
"isFacetableConfigurable": false,
"isSearchableConfigurable": true,
"label": "Product Description",
"name": "Description",
"type": "Standard"
}
],
"name": "Product2"
200
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 215 =====

},
{
"fields": [
{
"dataType": "stringplusclob",
"label": "Description",
"name": "Description",
"type": "ProductAttributeDefinitionStandard"
},
{
"dataType": "text",
"label": "Name",
"name": "Name",
"type": "ProductAttributeDefinitionStandard"
},
],
"name": "ProductAttributeDefinition"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Fields of the object.Fields Info[]fields
62.0Small, 62.0Name of the object.Stringname
Product Catalog Management Error
Output representation that contains error details, including error codes and messages.
JSON example
{
"errorCode": "INSUFFICIENT_ACCESS",
"message": "Insufficient access rights on cross-reference ID"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Small, 66.0Error code that identifies the type of error.StringerrorCode
66.0Small, 66.0Message that explains the reason for the
error.
Stringmessage
Product Classification
Output representation of the product classification details.
JSON example
{
"productClassification": {
201
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 216 =====

"id": "11BT10000004C9SMAU",
"name": "class",
"code": "code",
"parentProductClassificationId": "11BDU0000004JXq2AM",
"status": "Active"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
61.0Small, 61.0Code of the product classification record.Stringcode
60.0Small, 60.0ID of the product classification record.Stringid
61.0Small, 61.0Name of the product classification record.
If data translation is set up and specified in
Stringname
the org, the translated description is
available.
65.0Small, 65.0ID of the parent product classification.StringparentProduct
Classification
Id
61.0Small, 61.0Status of the product classification record.Stringstatus
Product Classification Details
Output representation that contains the details of a single product classification, including its attributes and categories.
JSON example
{
"id": "dummyId",
"name": "Dummy Product Classification",
"code": "DUMMY_CODE",
"attributeCategories": [{
"attributes": [
{
"attributeNameOverride": "Dummy_Attribute__c",
"code": "ATTR_CODE_1",
"dataType": "String",
"defaultValue": "default",
"description": "A dummy attribute for demonstration.",
"developerName": "Dummy_Attribute",
"displayType": "Text",
"helpText": "Help text for dummy attribute",
"id": "attrId1",
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": false,
"isValueCloneable": true,
202
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 217 =====

"label": "Dummy Attribute Label",
"maximumCharacterCount": 100,
"maximumValue": "100",
"minimumCharacterCount": 1,
"minimumValue": "1",
"name": "Dummy Attribute",
"sequence": 1,
"status": "Active",
"stepValue": "1"
}
],
"code": "GENERAL",
"id": "catId1",
"name": "General"
}],
"attributes": [{
"attributeNameOverride": "Dummy_Attribute__c",
"code": "ATTR_CODE_1",
"dataType": "String",
"defaultValue": "default",
"description": "A dummy attribute for demonstration.",
"developerName": "Dummy_Attribute",
"displayType": "Text",
"helpText": "Help text for dummy attribute",
"id": "attrId1",
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": false,
"isValueCloneable": true,
"label": "Dummy Attribute Label",
"maximumCharacterCount": 100,
"maximumValue": "100",
"minimumCharacterCount": 1,
"minimumValue": "1",
"name": "Dummy Attribute",
"sequence": 1,
"status": "Active",
"stepValue": "1"
}]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Small, 66.0List of attribute categories applicable to the
product classification.
Product
Classification
Attribute Category[]
attributeCategories
66.0Small, 66.0List of uncategorized attributes applicable
to the product classification.
Product
Classification
Attribute Definition[]
attributes
203
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 218 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Small, 66.0Code of the product classification.Stringcode
66.0Small, 66.0ID of the product classification.Stringid
66.0Small, 66.0Name of the product classification.Stringname
Product Classification Details Collection
Output representation that contains a collection of product classification details along with any processing errors.
JSON example
{
"success": false,
"errors": [
{
"errorCode": "INSUFFICIENT_ACCESS",
"message": "Insufficient access rights on cross-reference ID"
}
],
"productClassifications": [
{
"id": "dummyId",
"name": "Dummy Product Classification",
"code": "DUMMY_CODE",
"attributeCategories": [
{
"attributes": [
{
"attributeNameOverride": "Dummy_Attribute__c",
"code": "ATTR_CODE_1",
"dataType": "String",
"defaultValue": "default",
"description": "A dummy attribute for demonstration.",
"developerName": "Dummy_Attribute",
"displayType": "Text",
"helpText": "Help text for dummy attribute",
"id": "attrId1",
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": false,
"isValueCloneable": true,
"label": "Dummy Attribute Label",
"maximumCharacterCount": 100,
"maximumValue": "100",
"minimumCharacterCount": 1,
"minimumValue": "1",
"name": "Dummy Attribute",
"sequence": 1,
"status": "Active",
204
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 219 =====

"stepValue": "1"
}
],
"code": "GENERAL",
"id": "catId1",
"name": "General"
}
],
"attributes": [
{
"attributeNameOverride": "Dummy_Attribute__c",
"code": "ATTR_CODE_1",
"dataType": "String",
"defaultValue": "default",
"description": "A dummy attribute for demonstration.",
"developerName": "Dummy_Attribute",
"displayType": "Text",
"helpText": "Help text for dummy attribute",
"id": "attrId1",
"isConfigurable": true,
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": false,
"isValueCloneable": true,
"label": "Dummy Attribute Label",
"maximumCharacterCount": 100,
"maximumValue": "100",
"minimumCharacterCount": 1,
"minimumValue": "1",
"name": "Dummy Attribute",
"sequence": 1,
"status": "Active",
"stepValue": "1"
}
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
66.0Small, 66.0List of errors encountered during the
processing of the API request.
Product Catalog
Management Error[]
errors
66.0Small, 66.0List of product classification detail records
that match the requested product
classification IDs.
Product
Classification Details
on page 202[]
productClassifications
66.0Small, 66.0Indicates whether the API request is
successful (true) or has failed (false).
Booleansuccess
205
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 220 =====

Product Component Group
Output representation of the product component group.
JSON example
"productComponentGroups":[
{
"childGroups":[
{
"childGroups":[],
" components":[
{
"additionalFields":{},
"attributeCategory":[],
"attributes":[],
"catalogs":[],
"categories":[],
"childProducts":[],
"id":"01txx0000006i2aAAA",
"isActive":true,
"isAssetizable":true,
"isSoldOnlyWithOtherProds":true,
"name":"GenWatt Diesel 1000kW",
"nodeType":"simpleProduct",
"productCode":"GC1060",
"productComponentGroups":[],
"productRelatedComponent":
{
"childProductId":"01txx0000006i2aAAA",
"doesBundlePriceIncludeChild":true,
"id":"0dSxx00000001P7EAI",
"isComponentRequired":false,
"isDefaultComponent":true,
"isExcluded":false,
"isQuantityEditable":false,
"parentProductId":"01txx0000006iC8AAI",
"productRelationshipTypeId":"0yoxx000000001dAAA",
"quantity":1,
"quantityScaleMethod":"Proportional"
},
"productSellingModelOptions":[]
},
{
"additionalFields":{},
"attributeCategory":[],
"attributes":[],
"catalogs":[],
"categories":[],
"childProducts":[],
"id":"01txx0000006i2TAAQ",
"isActive":true,
"isAssetizable":true,
"isSoldOnlyWithOtherProds":true,
"name":"GenWatt Diesel 10kW",
"nodeType":"simpleProduct",
206
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 221 =====

"productCode":"GC1020",
"productComponentGroups":[],
"productRelatedComponent":{
"childProductId":"01txx0000006i2TAAQ",
"doesBundlePriceIncludeChild":true,
"id":"0dSxx00000001P8EAI",
"isComponentRequired":false,
"isDefaultComponent":true,
"isExcluded":false,
"isQuantityEditable":false,
"parentProductId":"01txx0000006iC8AAI",
"productRelationshipTypeId":"0yoxx000000001dAAA",
"quantity":1,"quantityScaleMethod":"Proportional"
},
"productSellingModelOptions":[]
},
{
"additionalFields":{},
"attributeCategory":[],
"attributes":[],
"catalogs":[],
"categories":[],
"childProducts":[],
"id":"01txx0000006i2SAAQ",
"isActive":true,
"isAssetizable":true,
"isSoldOnlyWithOtherProds":true,
"name":"GenWatt Diesel 200kW",
"nodeType":"simpleProduct",
"productCode":"GC1040",
"productComponentGroups":[],
"productRelatedComponent":
{
"childProductId":"01txx0000006i2SAAQ",
"doesBundlePriceIncludeChild":true,
"id":"0dSxx00000001P9EAI",
"isComponentRequired":false,
"isDefaultComponent":true,
"isExcluded":false,
"isQuantityEditable":false,
"parentProductId":"01txx0000006iC8AAI",
"productRelationshipTypeId":"0yoxx000000001dAAA",
"quantity":1,
"quantityScaleMethod":"Proportional"
},
"productSellingModelOptions":[]
}
],
"id":"0y7xx000000015lAAA",
"isExcluded":false,
"name":"G1.1",
"parentGroupId":"0y7xx0000000149AAA",
"parentProductId":"01txx0000006iC8AAI"
}
207
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 222 =====

],
"components":[],
"id":"0y7xx0000000149AAA",
"isExcluded":false,
"name":"G1",
"parentProductId":"01txx0000006iC8AAI"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Unique code of the product component
group, which is used only during design
time.
Stringcode
60.0Small, 60.0List of the product details.Product[]components
62.0Small, 62.0List of child product components groups.Product Component
Group[]
childGroups
60.0Small, 60.0Description of the product component
group.
Stringdescription
60.0Small, 60.0ID of the record.Stringid
60.0Small, 60.0Indicates whether the product component
group is excluded from the product bundle
BooleanisExcluded
for selection in the run time (true) or not
(false).
60.0Small, 60.0Maximum number of product components
that can be added to a group.
IntegermaxBundle
Components
60.0Small, 60.0Minimum number of product components
that can be added to a group.
IntegerminBundle
Components
60.0Small, 60.0Name of the record. If data translation is set
up and specified in the org, the translated
description is available.
Stringname
60.0Small, 60.0ID associated with the parent product
record.
StringparentProduct
Id
62.0Small, 62.0ID of the parent group record.StringparentGroupId
60.0Small, 60.0Order in which the groups are listed in the
bundle.
Integersequence
Product
Output representation of the product definition.
208
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 223 =====

JSON example
This example shows a sample of the Product List (POST) API response.
{
"products": [
{
"additionalFields": {
"code__c": "SWX445"
},
"attributeCategory": [
{
"attributes": [
{
"additionalFields": {
"scope": "Order"
},
"attributeNameOverride": "AD Text",
"code": "AD02",
"dataType": "Text",
"displayType": "Text",
"MinimumCharacterCount": "1",
"MaximumCharacterCount": "20",
"defaultValue": "AD Text DV",
"description": "AD Text Desc",
"helpText": "AD Text DHT",
"id": "0tjT1000000002bIAA",
"isHidden": false,
"isPriceImpacting": true,
"isReadOnly": true,
"isRequired": true,
"label": "AD Text Label",
"name": "AD Text",
"sequence": 1,
"status": "Active",
"valueDescription": "AD Text VD"
}
],
"code": "AC001",
"id": "0v3T1000000000BIAQ",
"name": "build and make"
}
],
"attributes": [
{
"additionalFields": {
"scope": "SWX445"
},
"attributeNameOverride": "AD Picklist",
"code": "AD001",
"dataType": "Picklist",
"defaultValue": "Red",
"description": "AD Picklist Description",
"helpText": "AD Picklist DHT",
"id": "0tjT1000000002WIAQ",
209
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 224 =====

"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "AD Picklist Label",
"name": "AD Picklist",
"picklist": {
"dataType": "Text",
"description": "APV Description",
"id": "0v5T10000000001IAA",
"name": "Color",
"values": [
{
"abbreviation": "Blue Abb",
"code": "APV03",
"displayValue": "Blue DV",
"id": "0v6T10000000006IAA",
"name": "Blue",
"sequence": "3",
"value": "Blue b",
"status": "Active"
},
{
"abbreviation": "Red Abb",
"code": "APV04",
"displayValue": "Red",
"id": "0v6T10000000001IAA",
"name": "Red",
"sequence": "4",
"value": "Red",
"status": "Active"
},
{
"abbreviation": "One Abb",
"code": "APV02",
"displayValue": "One DV",
"id": "0v6T1000000000uIAA",
"name": "One",
"sequence": "2",
"value": "One 1",
"status": "Active"
},
{
"abbreviation": "Red Abbreviation",
"code": "APV01",
"displayValue": "Red Display Value",
"id": "0v6T1000000001OIAQ",
"name": "Red",
"sequence": "1",
"value": "red12",
"status": "Active"
}
]
},
210
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 225 =====

"sequence": 1,
"status": "Active",
"valueDescription": "AD Picklist VD"
}
],
"categories": [],
"childProducts": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"configureDuringSale": "NotAllowed",
"id": "01tZ7000000AJkaIAG",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Earphones",
"nodeType": "bundleProduct",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tZ7000000AJkaIAG",
"doesBundlePriceIncludeChild": true,
"id": "0dSZ700000000cdMAA",
"isComponentRequired": false,
"isDefaultComponent": true,
"isExcluded": false,
"isQuantityEditable": false,
"parentProductId": "01tZ7000000AJXOIA4",
"productRelationshipTypeId": "0yoZ700000000kPIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": []
}
],
"description": "Keep your organization connected with seamless collaboration across
distributed teams. No matter where employees are located, organizations are seeking
stronger employee engagement and customer experiences to enable more productivity and
greater business agility. More effective collaboration helps organizations work smarter.",
"displayUrl":
"https://dispatch.m.io/wp-content/uploads/2023/01/History-of-Webex.png",
"id": "01t1Q000008CD2eQAG",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "SmartBytes Collaboration Suite",
"nodeType": "bundleProduct",
"productClassification": {
"id": "11B1Q0000008OMGUA2"
},
"productCode": "P0143",
"productComponentGroups": [
211
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 226 =====

{
"components": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"id": "01tZ7000000AJXTIA4",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Charger",
"nodeType": "bundleProduct",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tZ7000000AJXTIA4",
"doesBundlePriceIncludeChild": true,
"id": "0dSZ700000000YLMAY",
"isComponentRequired": false,
"isDefaultComponent": true,
"isExcluded": false,
"isQuantityEditable": false,
"parentProductId": "01tZ7000000AJXOIA4",
"productRelationshipTypeId": "0yoZ700000000kPIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": []
}
],
"id": "0y7Z700000000TtIAI",
"isExcluded": false,
"name": "Box",
"parentProductId": "01tZ7000000AJXOIA4"
}
],
"productSellingModelOptions": [
{
"id": "0iO1Q0000008OkeUAE",
"productId": "01t1Q000008CD2eQAG",
"productSellingModel": {
"id": "0jP1Q000000CaVFUA0",
"isDefault": true,
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
}
}
],
"productSpecificationType": {
"name": "None"
}
}
],
212
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 227 =====

"status": {
"code": "200",
"correlationId": "fd158d80-d73c-4a1f-a009-9225db804d70",
"errors": [],
"message": "Successfully fetched product records."
}
}
This example shows a sample of the Bulk Product Details (POST) API response.
{
"products": [
{
"additionalFields": {
"code__c": "SWX445"
},
"attributeCategory": [
{
"attributes": [
{
"additionalFields": {
"scope": "Order"
},
"attributeNameOverride": "AD Text",
"code": "AD02",
"dataType": "Text",
"displayType": "Text",
"MinimumCharacterCount": "1",
"MaximumCharacterCount": "20",
"defaultValue": "AD Text DV",
"description": "AD Text Desc",
"helpText": "AD Text DHT",
"id": "0tjT1000000002bIAA",
"isHidden": false,
"isPriceImpacting": true,
"isReadOnly": true,
"isRequired": true,
"label": "AD Text Label",
"name": "AD Text",
"sequence": 1,
"status": "Active",
"valueDescription": "AD Text VD"
}
],
"code": "AC001",
"id": "0v3T1000000000BIAQ",
"name": "build and make"
}
],
"attributes": [
{
"additionalFields": {
"scope": "SWX445"
},
"attributeNameOverride": "AD Picklist",
213
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 228 =====

"code": "AD001",
"dataType": "Picklist",
"defaultValue": "Red",
"description": "AD Picklist Description",
"helpText": "AD Picklist DHT",
"id": "0tjT1000000002WIAQ",
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "AD Picklist Label",
"name": "AD Picklist",
"picklist": {
"dataType": "Text",
"description": "APV Description",
"id": "0v5T10000000001IAA",
"name": "Color",
"values": [
{
"abbreviation": "Blue Abb",
"code": "APV03",
"displayValue": "Blue DV",
"id": "0v6T10000000006IAA",
"name": "Blue",
"sequence": "3",
"value": "Blue b",
"status": "Active"
},
{
"abbreviation": "Red Abb",
"code": "APV04",
"displayValue": "Red",
"id": "0v6T10000000001IAA",
"name": "Red",
"sequence": "4",
"value": "Red",
"status": "Active"
},
{
"abbreviation": "One Abb",
"code": "APV02",
"displayValue": "One DV",
"id": "0v6T1000000000uIAA",
"name": "One",
"sequence": "2",
"value": "One 1",
"status": "Active"
},
{
"abbreviation": "Red Abbreviation",
"code": "APV01",
"displayValue": "Red Display Value",
"id": "0v6T1000000001OIAQ",
"name": "Red",
214
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 229 =====

"sequence": "1",
"value": "red12",
"status": "Active"
}
]
},
"sequence": 1,
"status": "Active",
"valueDescription": "AD Picklist VD"
}
],
"categories": [],
"childProducts": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"configureDuringSale": "NotAllowed",
"id": "01tZ7000000AJkaIAG",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Earphones",
"nodeType": "bundleProduct",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tZ7000000AJkaIAG",
"doesBundlePriceIncludeChild": true,
"id": "0dSZ700000000cdMAA",
"isComponentRequired": false,
"isDefaultComponent": true,
"isExcluded": false,
"isQuantityEditable": false,
"parentProductId": "01tZ7000000AJXOIA4",
"productRelationshipTypeId": "0yoZ700000000kPIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": []
}
],
"description": "Keep your organization connected with seamless collaboration across
distributed teams. No matter where employees are located, organizations are seeking
stronger employee engagement and customer experiences to enable more productivity and
greater business agility. More effective collaboration helps organizations work smarter.",
"displayUrl":
"https://dispatch.m.io/wp-content/uploads/2023/01/History-of-Webex.png",
"id": "01t1Q000008CD2eQAG",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "SmartBytes Collaboration Suite",
215
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 230 =====

"nodeType": "bundleProduct",
"productClassification": {
"id": "11B1Q0000008OMGUA2",
"name" : "class",
"code" : "code",
"status" : "Active"
},
"productCode": "P0143",
"productComponentGroups": [
{
"components": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"id": "01tZ7000000AJXTIA4",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Charger",
"nodeType": "bundleProduct",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tZ7000000AJXTIA4",
"doesBundlePriceIncludeChild": true,
"id": "0dSZ700000000YLMAY",
"isComponentRequired": false,
"isDefaultComponent": true,
"isExcluded": false,
"isQuantityEditable": false,
"parentProductId": "01tZ7000000AJXOIA4",
"productRelationshipTypeId": "0yoZ700000000kPIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional"
},
"productSellingModelOptions": []
}
],
"id": "0y7Z700000000TtIAI",
"isExcluded": false,
"name": "Box",
"parentProductId": "01tZ7000000AJXOIA4"
}
],
"productSellingModelOptions": [
{
"id": "0iO1Q0000008OkeUAE",
"productId": "01t1Q000008CD2eQAG",
"productSellingModel": {
"id": "0jP1Q000000CaVFUA0",
"isDefault": true,
"name": "One Time",
"sellingModelType": "OneTime",
216
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 231 =====

"status": "Active"
}
}
],
"productSpecificationType": {
"name": "None"
}
}
],
"status": {
"code": "200",
"correlationId": "fd158d80-d73c-4a1f-a009-9225db804d70",
"errors": [],
"message": "Successfully fetched product records."
}
}
This example shows a sample of the Product By ID (GET) API response.
{
"products": [
{
"attributeCategory": [
{
"attributes": [
{
"attributeNameOverride": "AD Text",
"code": "AD02",
"dataType": "Text",
"displayType": "Text",
"MinimumCharacterCount": "1",
"MaximumCharacterCount": "20",
"defaultValue": "AD Text DV",
"description": "AD Text Desc",
"helpText": "AD Text DHT",
"id": "0tjT1000000002bIAA",
"isHidden": false,
"isPriceImpacting": true,
"isReadOnly": true,
"isRequired": true,
"label": "AD Text Label",
"name": "AD Text",
"sequence": 1,
"status": "Active",
"valueDescription": "AD Text VD"
}
],
"code": "AC001",
"id": "0v3T1000000000BIAQ",
"name": "build and make"
}
],
"attributes": [
{
"attributeNameOverride": "AD Picklist",
217
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 232 =====

"code": "AD001",
"dataType": "Picklist",
"defaultValue": "Red",
"description": "AD Picklist Description",
"helpText": "AD Picklist DHT",
"id": "0tjT1000000002WIAQ",
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "AD Picklist Label",
"name": "AD Picklist",
"picklist": {
"dataType": "Text",
"description": "APV Description",
"id": "0v5T10000000001IAA",
"name": "Color",
"values": [
{
"abbreviation": "Blue Abb",
"code": "APV03",
"displayValue": "Blue DV",
"id": "0v6T10000000006IAA",
"name": "Blue",
"sequence": "3",
"value": "Blue b",
"status": "Active"
},
{
"abbreviation": "Red Abb",
"code": "APV04",
"displayValue": "Red",
"id": "0v6T10000000001IAA",
"name": "Red",
"sequence": "4",
"value": "Red",
"status": "Active"
},
{
"abbreviation": "One Abb",
"code": "APV02",
"displayValue": "One DV",
"id": "0v6T1000000000uIAA",
"name": "One",
"sequence": "2",
"value": "One 1",
"status": "Active"
},
{
"abbreviation": "Red Abbreviation",
"code": "APV01",
"displayValue": "Red Display Value",
"id": "0v6T1000000001OIAQ",
"name": "Red",
218
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 233 =====

"sequence": "1",
"value": "red12",
"status": "Active"
}
]
},
"sequence": 1,
"status": "Active",
"valueDescription": "AD Picklist VD"
}
],
"availabilityDate": "2023-07-12T19:00:00.000Z",
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
"description": "Bundle Product Description",
"discontinuedDate": "2023-07-27T19:00:00.000Z",
"displayUrl": "www.google.com",
"endOfLifeDate": "2023-07-31T19:00:00.000Z",
"id": "01tT1000000F0afIAC",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": true,
"name": "Bundle Product",
"nodeType": "bundleProduct",
"productClassification": {
"id": "11BT10000004C9SMAU",
"name" : "class",
"code" : "code",
"status" : "Active"
},
"productCode": "P001",
"productComponentGroups": [
{
"code": "PCG002",
"components": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"nodeType": "productClass",
"productClassification": {
"id": "11BT10000004C9SMAU",
"name" : "class",
"code" : "code",
"status" : "Active"
},
"productComponentGroups": [],
"productRelatedComponent": {
"childSellingModelId": "0jPT10000004CAfMAM",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rlMAA",
"isComponentRequired": false,
219
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 234 =====

"isDefaultComponent": false,
"isQuantityEditable": true,
"maxQuantity": 5,
"minQuantity": 1,
"parentProductId": "01tT1000000F0afIAC",
"productClassificationId": "11BT10000004C9SMAU",
"productRelationshipTypeId": "0yoT10000004CBEIA2",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 2,
"isExcluded": false
},
"productSellingModelOptions": []
}
],
"description": "PCG002 desc",
"id": "0y7T10000004C9IIAU",
"maxBundleComponents": 5,
"minBundleComponents": 1,
"name": "PCG002",
"parentProductId": "01tT1000000F0afIAC",
"sequence": 2,
"isExcluded": false
},
{
"code": "PCG001",
"components": [
{
"attributeCategory": [],
"attributes": [
{
"attributeNameOverride": "AD Picklist",
"code": "AD001",
"dataType": "Picklist",
"defaultValue": "Red",
"description": "AD Picklist Description",
"helpText": "AD Picklist DHT",
"id": "0tjT1000000002WIAQ",
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "AD Picklist Label",
"name": "AD Picklist",
"picklist": {
"dataType": "Text",
"description": "APV Description",
"id": "0v5T10000000001IAA",
"name": "Color",
"values": [
{
"abbreviation": "Blue Abb",
"code": "APV03",
"displayValue": "Blue DV",
220
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 235 =====

"id": "0v6T10000000006IAA",
"name": "Blue",
"sequence": "3",
"value": "Blue b",
"status": "Active"
},
{
"abbreviation": "Red Abb",
"code": "APV04",
"displayValue": "Red",
"id": "0v6T10000000001IAA",
"name": "Red",
"sequence": "4",
"value": "Red",
"status": "Active"
},
{
"abbreviation": "One Abb",
"code": "APV02",
"displayValue": "One DV",
"id": "0v6T1000000000uIAA",
"name": "One",
"sequence": "2",
"value": "One 1",
"status": "Active"
},
{
"abbreviation": "Red Abbreviation",
"code": "APV01",
"displayValue": "Red Display Value",
"id": "0v6T1000000001OIAQ",
"name": "Red",
"sequence": "1",
"value": "red12",
"status": "Active"
}
]
},
"sequence": 1,
"status": "Active",
"valueDescription": "AD Picklist VD"
},
{
"attributeNameOverride": "AD Text",
"code": "AD02",
"dataType": "Text",
"displayType": "Text",
"MinimumCharacterCount": "1",
"MaximumCharacterCount": "20",
"defaultValue": "AD Text DV",
"description": "AD Text Desc",
"helpText": "AD Text DHT",
"id": "0tjT1000000002bIAA",
"isHidden": false,
221
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 236 =====

"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "AD Text Label",
"name": "AD Text",
"status": "Active",
"valueDescription": "AD Text VD"
}
],
"availabilityDate": "2023-07-17T19:00:00.000Z",
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
"description": "P003 desc",
"discontinuedDate": "2023-07-19T19:00:00.000Z",
"displayUrl": "www.google.com",
"endOfLifeDate": "2023-07-28T19:00:00.000Z",
"id": "01tT1000000F0YyIAK",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Child1 - Bundle with PCG",
"nodeType": "bundleProduct",
"productClassification": {
"id": "11BT10000004C9SMAU",
"name" : "class",
"code" : "code",
"status" : "Active"
},
"productCode": "P003",
"productComponentGroups": [
{
"code": "PCG2",
"components": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"id": "01tT1000000F0Z8IAK",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Super Child2 - Bundle with PCG",
"nodeType": "bundleProduct",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tT1000000F0Z8IAK",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rWMAQ",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01tT1000000F0YyIAK",
222
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 237 =====

"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 2,
"isExcluded": false
},
"productSellingModelOptions": [],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
},
{
"attributeCategory": [],
"attributes": [],
"availabilityDate": "2023-07-15T19:00:00.000Z",
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
"discontinuedDate": "2023-07-16T19:00:00.000Z",
"displayUrl": "Test",
"endOfLifeDate": "2023-07-17T19:00:00.000Z",
"id": "01tT1000000F0YzIAK",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "SuperChild1 - Bundle with PCG",
"nodeType": "bundleProduct",
"productCode": "Test",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tT1000000F0YzIAK",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rXMAQ",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01tT1000000F0YyIAK",
"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 1,
"isExcluded": false
},
"productSellingModelOptions": [],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
},
{
"attributeCategory": [],
"attributes": [],
"categories": [],
223
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 238 =====

"childProducts": [],
"configureDuringSale": "Allowed",
"id": "01tT1000000F0apIAC",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Bundle2",
"nodeType": "bundleProduct",
"productCode": "PC003",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tT1000000F0apIAC",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rqMAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01tT1000000F0YyIAK",
"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"isExcluded": false
},
"productSellingModelOptions": [],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
}
],
"description": "Group for components at level 2",
"id": "0y7T10000004C98IAE",
"maxBundleComponents": 5,
"minBundleComponents": 1,
"name": "PCG2",
"parentProductId": "01tT1000000F0YyIAK",
"isExcluded": false
}
],
"productRelatedComponent": {
"childProductId": "01tT1000000F0YyIAK",
"childSellingModelId": "0jPT10000004CAfMAM",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rgMAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": true,
"maxQuantity": 3,
"minQuantity": 1,
"parentProductId": "01tT1000000F0afIAC",
"parentSellingModelId": "0jPT10000004CAfMAM",
"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
224
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 239 =====

"sequence": 1,
"isExcluded": false
},
"productSellingModelOptions": [
{
"id": "0iOT10000004CMrMAM",
"productId": "01tT1000000F0YyIAK",
"isDefault": false,
"productSellingModel": {
"id": "0jPT10000004CAfMAM",
"name": "OneTimePSM",
"sellingModelType": "OneTime",
"status": "Active"
}
}
],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
}
],
"description": "PCG001 Description",
"id": "0y7T10000004C9DIAU",
"maxBundleComponents": 5,
"minBundleComponents": 1,
"name": "PCG001",
"parentProductId": "01tT1000000F0afIAC",
"sequence": 1,
"isExcluded": false
}
],
"productSellingModelOptions": [
{
"id": "0iOT10000004CMmMAM",
"productId": "01tT1000000F0afIAC",
"productSellingModel": {
"id": "0jPT10000004CAfMAM",
"name": "OneTimePSM",
"sellingModelType": "OneTime",
"status": "Active"
}
}
],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
},
{
"attributeCategory": [
{
"attributes": [
{
225
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 240 =====

"attributeNameOverride": "AD Text",
"code": "AD02",
"dataType": "Text",
"displayType": "Text",
"MinimumCharacterCount": "1",
"MaximumCharacterCount": "20",
"defaultValue": "AD Text DV",
"description": "AD Text Desc",
"helpText": "AD Text DHT",
"id": "0tjT1000000002bIAA",
"isHidden": false,
"isPriceImpacting": true,
"isReadOnly": true,
"isRequired": true,
"label": "AD Text Label",
"name": "AD Text",
"sequence": 1,
"status": "Active",
"valueDescription": "AD Text VD"
}
],
"code": "AC001",
"id": "0v3T1000000000BIAQ",
"name": "build and make"
}
],
"attributes": [
{
"attributeNameOverride": "AD Picklist",
"code": "AD001",
"dataType": "Picklist",
"defaultValue": "Red",
"description": "AD Picklist Description",
"helpText": "AD Picklist DHT",
"id": "0tjT1000000002WIAQ",
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "AD Picklist Label",
"name": "AD Picklist",
"picklist": {
"dataType": "Text",
"description": "APV Description",
"id": "0v5T10000000001IAA",
"name": "Color",
"values": [
{
"abbreviation": "Blue Abb",
"code": "APV03",
"displayValue": "Blue DV",
"id": "0v6T10000000006IAA",
"name": "Blue",
"sequence": "3",
226
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 241 =====

"value": "Blue b",
"status": "Active"
},
{
"abbreviation": "Red Abb",
"code": "APV04",
"displayValue": "Red",
"id": "0v6T10000000001IAA",
"name": "Red",
"sequence": "4",
"value": "Red",
"status": "Active"
},
{
"abbreviation": "One Abb",
"code": "APV02",
"displayValue": "One DV",
"id": "0v6T1000000000uIAA",
"name": "One",
"sequence": "2",
"value": "One 1",
"status": "Active"
},
{
"abbreviation": "Red Abbreviation",
"code": "APV01",
"displayValue": "Red Display Value",
"id": "0v6T1000000001OIAQ",
"name": "Red",
"sequence": "1",
"value": "red12",
"status": "Active"
}
]
},
"sequence": 1,
"status": "Active",
"valueDescription": "AD Picklist VD"
}
],
"availabilityDate": "2023-07-12T19:00:00.000Z",
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
"description": "Bundle Product Description",
"discontinuedDate": "2023-07-27T19:00:00.000Z",
"displayUrl": "www.google.com",
"endOfLifeDate": "2023-07-31T19:00:00.000Z",
"id": "01tT1000000F0afIAC",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": true,
"name": "Bundle Product",
"nodeType": "bundleProduct",
227
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 242 =====

"productClassification": {
"id": "11BT10000004C9SMAU",
"name" : "class",
"code" : "code",
"status" : "Active"
},
"productCode": "P001",
"productComponentGroups": [
{
"code": "PCG002",
"components": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"nodeType": "productClass",
"productClassification": {
"id": "11BT10000004C9SMAU",
"name" : "class",
"code" : "code",
"status" : "Active"
},
"productComponentGroups": [],
"productRelatedComponent": {
"childSellingModelId": "0jPT10000004CAfMAM",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rlMAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": true,
"maxQuantity": 5,
"minQuantity": 1,
"parentProductId": "01tT1000000F0afIAC",
"productClassificationId": "11BT10000004C9SMAU",
"productRelationshipTypeId": "0yoT10000004CBEIA2",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 2,
"isExcluded": false
},
"productSellingModelOptions": []
}
],
"description": "PCG002 desc",
"id": "0y7T10000004C9IIAU",
"maxBundleComponents": 5,
"minBundleComponents": 1,
"name": "PCG002",
"parentProductId": "01tT1000000F0afIAC",
"sequence": 2,
"isExcluded": false
},
{
228
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 243 =====

"code": "PCG001",
"components": [
{
"attributeCategory": [],
"attributes": [
{
"attributeNameOverride": "AD Picklist",
"code": "AD001",
"dataType": "Picklist",
"defaultValue": "Red",
"description": "AD Picklist Description",
"helpText": "AD Picklist DHT",
"id": "0tjT1000000002WIAQ",
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "AD Picklist Label",
"name": "AD Picklist",
"picklist": {
"dataType": "Text",
"description": "APV Description",
"id": "0v5T10000000001IAA",
"name": "Color",
"values": [
{
"abbreviation": "Blue Abb",
"code": "APV03",
"displayValue": "Blue DV",
"id": "0v6T10000000006IAA",
"name": "Blue",
"sequence": "3",
"value": "Blue b",
"status": "Active"
},
{
"abbreviation": "Red Abb",
"code": "APV04",
"displayValue": "Red",
"id": "0v6T10000000001IAA",
"name": "Red",
"sequence": "4",
"value": "Red",
"status": "Active"
},
{
"abbreviation": "One Abb",
"code": "APV02",
"displayValue": "One DV",
"id": "0v6T1000000000uIAA",
"name": "One",
"sequence": "2",
"value": "One 1",
"status": "Active"
229
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 244 =====

},
{
"abbreviation": "Red Abbreviation",
"code": "APV01",
"displayValue": "Red Display Value",
"id": "0v6T1000000001OIAQ",
"name": "Red",
"sequence": "1",
"value": "red12",
"status": "Active"
}
]
},
"sequence": 1,
"status": "Active",
"valueDescription": "AD Picklist VD"
},
{
"attributeNameOverride": "AD Text",
"code": "AD02",
"dataType": "Text",
"displayType": "Text",
"MinimumCharacterCount": "1",
"MaximumCharacterCount": "20",
"defaultValue": "AD Text DV",
"description": "AD Text Desc",
"helpText": "AD Text DHT",
"id": "0tjT1000000002bIAA",
"isHidden": false,
"isPriceImpacting": false,
"isReadOnly": false,
"isRequired": true,
"label": "AD Text Label",
"name": "AD Text",
"status": "Active",
"valueDescription": "AD Text VD"
}
],
"availabilityDate": "2023-07-17T19:00:00.000Z",
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
"description": "P003 desc",
"discontinuedDate": "2023-07-19T19:00:00.000Z",
"displayUrl": "www.google.com",
"endOfLifeDate": "2023-07-28T19:00:00.000Z",
"id": "01tT1000000F0YyIAK",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Child1 - Bundle with PCG",
"nodeType": "bundleProduct",
"productClassification": {
"id": "11BT10000004C9SMAU",
230
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 245 =====

"name" : "class",
"code" : "code",
"status" : "Active"
},
"productCode": "P003",
"productComponentGroups": [
{
"code": "PCG2",
"components": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"id": "01tT1000000F0Z8IAK",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Super Child2 - Bundle with PCG",
"nodeType": "bundleProduct",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tT1000000F0Z8IAK",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rWMAQ",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01tT1000000F0YyIAK",
"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 2,
"isExcluded": false
},
"productSellingModelOptions": [],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
},
{
"attributeCategory": [],
"attributes": [],
"availabilityDate": "2023-07-15T19:00:00.000Z",
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
"discontinuedDate": "2023-07-16T19:00:00.000Z",
"displayUrl": "Test",
"endOfLifeDate": "2023-07-17T19:00:00.000Z",
"id": "01tT1000000F0YzIAK",
"isActive": false,
"isAssetizable": true,
231
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 246 =====

"isSoldOnlyWithOtherProds": false,
"name": "SuperChild1 - Bundle with PCG",
"nodeType": "bundleProduct",
"productCode": "Test",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tT1000000F0YzIAK",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rXMAQ",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01tT1000000F0YyIAK",
"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 1,
"isExcluded": false
},
"productSellingModelOptions": [],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
},
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
"id": "01tT1000000F0apIAC",
"isActive": false,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Bundle2",
"nodeType": "bundleProduct",
"productCode": "PC003",
"productComponentGroups": [],
"productRelatedComponent": {
"childProductId": "01tT1000000F0apIAC",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rqMAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": false,
"parentProductId": "01tT1000000F0YyIAK",
"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"isExcluded": false
},
"productSellingModelOptions": [],
"productSpecificationType": {
232
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 247 =====

"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
}
],
"description": "Group for components at level 2",
"id": "0y7T10000004C98IAE",
"maxBundleComponents": 5,
"minBundleComponents": 1,
"name": "PCG2",
"parentProductId": "01tT1000000F0YyIAK",
"isExcluded": false
}
],
"productRelatedComponent": {
"childProductId": "01tT1000000F0YyIAK",
"childSellingModelId": "0jPT10000004CAfMAM",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rgMAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isQuantityEditable": true,
"maxQuantity": 3,
"minQuantity": 1,
"parentProductId": "01tT1000000F0afIAC",
"parentSellingModelId": "0jPT10000004CAfMAM",
"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"sequence": 1,
"isExcluded": false
},
"productSellingModelOptions": [
{
"id": "0iOT10000004CMrMAM",
"productId": "01tT1000000F0YyIAK",
"isDefault": false,
"productSellingModel": {
"id": "0jPT10000004CAfMAM",
"name": "OneTimePSM",
"sellingModelType": "OneTime",
"status": "Active"
}
}
],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
}
],
"description": "PCG001 Description",
"id": "0y7T10000004C9DIAU",
"maxBundleComponents": 5,
233
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 248 =====

"minBundleComponents": 1,
"name": "PCG001",
"parentProductId": "01tT1000000F0afIAC",
"sequence": 1,
"isExcluded": false
}
],
"productSellingModelOptions": [
{
"id": "0iOT10000004CMmMAM",
"productId": "01tT1000000F0afIAC",
"productSellingModel": {
"id": "0jPT10000004CAfMAM",
"name": "OneTimePSM",
"sellingModelType": "OneTime",
"status": "Active"
}
}
],
"productSpecificationType": {
"name": "NonCommercialSpecType",
"productSpecificationRecordType": null
}
}
],
"status": {
"code": "200",
"correlationId": "fd158d80-d73c-4a1f-a009-9225db804d70",
"errors": [],
"message": "Successfully fetched Product records."
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
61.0Small, 61.0Key-value pair of additional standard or
custom fields with their values.
Map<String,
Additional Fields
Input>
additional
Fields
60.0Small, 60.0List of categorized attributes related to the
product.
Attribute Category[]attribute
Category
60.0Small, 60.0List of uncategorized attributes related to
the product.
Attribute Definition[]attributes
60.0Small, 60.0Date when the part is used in the product
or is made available for sale.
Stringavailability
Date
61.0Small, 61.0List of the associated catalogs returned with
the Product List API (POST) response. The
Catalog[]catalogs
Product By ID API (GET) returns an empty
catalog list in the response.
234
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 249 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
Returns the name  and id  values only.
60.0Small, 60.0List of the associated categories returned
with the Product List API (POST) response.
Category[]categories
The Product By ID API (GET) returns an
empty category list in the response.
Returns the name  and id  values only.
60.0Small, 60.0Hierarchy of the child products.Product[]childProducts
60.0Small, 60.0Determines whether to allow or prevent
configuration when a bundle is sold.
Stringconfigure
DuringSale
60.0Small, 60.0Description of the product. If data
translation is set up and specified in the org,
the translated description is available.
Stringdescription
60.0Small, 60.0Date from when the part can’t be used in
the product or sold.
Stringdiscontinued
Date
60.0Small, 60.0Display image URL of the product.StringdisplayUrl
60.0Small, 60.0Date after which a product isn’t supported,
ordered, or maintained.
StringendOfLifeDate
60.0Small, 60.0ID of the product.Stringid
60.0Small, 60.0Indicates if the product is active (true) or
not (false).
BooleanisActive
60.0Small, 60.0Indicates if the product instance remains a
customer asset after it's purchased (true)
or not (false).
BooleanisAssetizable
60.0Small, 60.0Indicates whether the product can't be sold
separately (true) or not (false).
BooleanisSoldOnly
WithOther
Prods
60.0Small, 60.0Name of the product. If data translation is
set up and specified in the org, the
translated name is available.
Stringname
60.0Small, 60.0Type of the node, such as a product or
bundled product.
StringnodeType
60.0Small, 60.0Details of the product classification that the
product is based on.
Product
Classification
product
Classification
60.0Small, 60.0Universal product code that's used to track
the part that’s used in the product.
StringproductCode
235
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 250 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Logical grouping of the component
products in a bundle and the group
Product Component
Group[]
product
Component
Groups cardinality for ordering the product
components.
60.0Small, 60.0Details of the related components of a
product.
Product Related
Component
product
Related
Component
60.0Small, 60.0Details of the product selling model options.Product Selling
Model Option[]
product
SellingModel
Options
60.0Small, 60.0Details of the product specification type.Product Specification
Type
product
Specification
Type
60.0Small, 60.0Method to scale the quantity of the child
product in relation to the quantity of the
parent.
StringquantityScale
Method
Product Related Component
Output representation of the product-related component.
JSON example
"productRelatedComponent": {
"childProductId": "01tT1000000F0YyIAK",
"childSellingModelId": "0jPT10000004CAfMAM",
"doesBundlePriceIncludeChild": true,
"id": "0dST100000000rgMAA",
"isComponentRequired": false,
"isDefaultComponent": false,
"isExcluded": false,
"isQuantityEditable": true,
"maxQuantity": 3,
"minQuantity": 1,
"parentProductId": "01tT1000000F0afIAC",
"parentSellingModelId": "0jPT10000004CAfMAM",
"productClassificationId": "11BRO00000000222AA",
"productRelationshipTypeId": "0yoT1000000002WIAQ",
"quantity": 1,
"quantityScaleMethod": "Proportional",
"quoteVisibility": "Quote Document Only",
"sequence": 1
}
236
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 251 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Lookup to the child product in the bundle.StringchildProduct
Id
60.0Small, 60.0ID of the child product selling model record.StringchildSelling
ModelId
60.0Small, 60.0Indicates whether the price of the bundle
includes the child product (true) or not
(false).
BooleandoesBundle
PriceInclude
Child
60.0Small, 60.0ID of the record.Stringid
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
60.0Small, 60.0Indicates whether the component is
excluded in the bundle group (true) or
not (false).
BooleanisExcluded
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
60.0Small, 60.0Lookup to the parent product.StringparentProduct
Id
60.0Small, 60.0ID of the product selling model record.StringparentSelling
ModelId
60.0Small, 60.0ID of the product classification record.Stringproduct
Classification
Id
62.0Small, 62.0Reserved for future use.StringproductInstance
Reuse
60.0Small, 60.0ID of the product relationship type record.Stringproduct
Relationship
TypeId
60.0Small, 60.0Quantity of the child products.Doublequantity
237
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 252 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
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
Product Selling Model
Output representation of the definition of the product selling model.
JSON example
"productSellingModel":
{
"id": "0jPT10000004CAfMAM",
"name": "OneTimePSM",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
}
}]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the record.Stringid
60.0Small, 60.0Name of the record.Stringname
238
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 253 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Duration of the selling model.IntegerpricingTerm
60.0Small, 60.0Units of the pricing term.StringpricingTerm
Unit
60.0Small, 60.0Different models of selling the product. Valid
values are:
StringsellingModel
Type
• OneTime
• TermDefined
• Evergreen
60.0Small, 60.0Status of the selling model. For example,
whether the selling model is active and can
be used in transactions.
Stringstatus
Product Selling Model Option
Output representation of the definition of the product selling model option.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
JSON example
"productSellingModelOptions": [
{
"id": "0iOT10000004CMrMAM",
"isDefault": false,
"productId": "01tT1000000F0YyIAK",
"productSellingModel": {
"id": "0jPT10000004CAfMAM",
"name": "OneTimePSM",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
}
}]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the record.Stringid
60.0Small, 60.0Indicates whether this model option is the
default product selling model option
(true) or not (false).
BooleanisDefault
60.0Small, 60.0ID of the product.StringproductId
239
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 254 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Master-detail field to the product selling
model.
Product Selling
Model
product
SellingModel
Product Specification Type
Output representation of the product specification type.
JSON example
"productSpecificationType":
{
"name": "NonCommercialSpecType",
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Name of the product specification type.Stringname
Products
Output representation of the list of retrieved products.
JSON example
{
"correlationId": "9b6bc520-3c82-4d6c-a458-47590370681a",
"facets":[
{
"attributeType": "ProductStandard",
"displayName": "Product Type",
"displayRank": 1,
"displayType": "MultiSelect",
"nameOrId": "Type",
"values": [
{
"displayName": "Simple",
"nameOrId": "Simple",
"productCount": 9
}
]
},
{
"attributeType": "ProductStandard",
"displayName": "Active",
"displayRank": 2,
"displayType": "MultiSelect",
"nameOrId": "IsActive",
"values": [
{
240
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 255 =====

"displayName": "true",
"nameOrId": "true",
"productCount": 47
}
]
}
],
"count": 3,
"products": [
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"description": "Keep your organization connected with seamless collaboration across
distributed teams. No matter where employees are located, organizations are seeking
stronger employee engagement and customer experiences to enable more productivity and
greater business agility. More effective collaboration helps organizations work smarter.",
"displayUrl":
"https://dispatch.m.io/wp-content/uploads/2023/01/History-of-Webex.png",
"id": "01t1Q000008CD2eQAG",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "SmartBytes Collaboration Suite",
"nodeType": "bundleProduct",
"productClassification": {
"id": "11B1Q0000008OMGUA2"
},
"productCode": "P0143",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iO1Q0000008OkeUAE",
"productId": "01t1Q000008CD2eQAG",
"productSellingModel": {
"id": "0jP1Q000000CaVFUA0",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
}
}
],
"productSpecificationType": {
"name": "None"
}
},
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
241
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 256 =====

"displayUrl":
"https://www.cisco.com/c/dam/en/us/products/collateral/wireless/small-business-300-series-wireless-access-points/datasheet-c78-732143.doc/_jcr_content/renditions/datasheet-c78-732143_1.jpg",
"id": "01t1Q000008CD36QAG",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "SmartBytes Repeater",
"nodeType": "simpleProduct",
"productClassification": {
"id": "11B1Q0000008OMMUA2"
},
"productCode": "BS_R001",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iO1Q0000008OlsUAE",
"productId": "01t1Q000008CD36QAG",
"productSellingModel": {
"id": "0jP1Q000000CaVFUA0",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
}
}
],
"productSpecificationType": {
"name": "COM_Offer"
}
},
{
"attributeCategory": [],
"attributes": [],
"categories": [],
"childProducts": [],
"configureDuringSale": "Allowed",
"description": "A converged data center architecture that integrates computing,
networking and storage resources to increase efficiency and enable centralized management.
UCS products are designed and configured to work together effectively.",
"displayUrl":
"https://www.cisco.com/c/dam/en/us/products/collateral/servers-unified-computing/ucs-x-series-modular-system/sap-hana-scaleup-appliance-with-xseries-wp.docx/_jcr_content/renditions/sap-hana-scaleup-appliance-with-xseries-wp_3.png",
"id": "01t1Q000008CD2sQAG",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "SmartBytes Unified Computing System",
"nodeType": "bundleProduct",
"productCode": "P0157",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iO1Q0000008OkzUAE",
"productId": "01t1Q000008CD2sQAG",
242
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 257 =====

"productSellingModel": {
"id": "0jP1Q000000CaVFUA0",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
}
},
{
"id": "0iO1Q0000008OlWUAU",
"productId": "01t1Q000008CD2sQAG",
"productSellingModel": {
"id": "0jP1Q000000CaVHUA0",
"name": "Evergreen",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "Evergreen",
"status": "Active"
}
}
],
"productSpecificationType": {
"name": "None"
}
}
],
"status": {
"code": "200",
"errors": [],
"message": "Successfully fetched the product records."
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
60.0Small, 60.0Total count of the products matching the
request query.
Integercount
63.0Small, 63.0Details of the faceted search. This property
is applicable if the Use Indexed Data For
Search Facetfacets
Product Listing and Search toggle from
the Product Discovery Settings page from
Setup is enabled.
60.0Small, 60.0List of products matching the request query.Product[]products
60.0Small, 60.0Status of the request.Statusstatus
243
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 258 =====

Related Object Records
Output representation of the related records for a specified record ID and related object API name.
JSON example
"relatedObjectRecords": [
{
"count": 2,
"records": [
{
"SegmentType": "Yearly",
"DurationType": "Months",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx000000001dEAA",
"ProductId": "01txx0000006i44AAA",
"Id": "1FTxx0000004CDtGAM",
"Name": "PPRS-000000005"
},
{
"SegmentType": "FreeTrial",
"DurationType": "Days",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx000000001dEAA",
"ProductId": "01txx0000006i44AAA",
"Id": "1FTxx0000004CFUGA2",
"Name": "PPRS-000000006"
}
],
"relatedObjectAPIName": "ProductRampSegment"
},
{
"count": 2,
"records": [
{
"UsageMetricId": "1BRxx0000004CAeGAM",
"UsageMetricName": "Test Usage Metric 2",
"UsageDefinitionProductId": null,
"Label": "PUG-103",
"Quantity": 100,
"Id": "1BXxx0000004CCGGA2"
},
{
"UsageMetricId": "1BRxx0000004CCGGA2",
"UsageMetricName": "Test Usage Metric 3",
"UsageDefinitionProductId": "01txx0000006i2eAAA",
"Label": "PUG-105",
"Quantity": 500,
"Id": "1BXxx0000004CFUGA2"
}
],
"relatedObjectAPIName": "ProductUsageGrant"
}
]
244
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 259 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Total count of the related records that are
returned.
Integercount
62.0Small, 62.0List of related object records.Map<String,
Object>
records
62.0Small, 62.0API name of the related object to return the
records for.
StringrelatedObject
APIName
Related Records
Output representation of the list of relatedObject records for a specified record ID.
JSON example
"relatedRecords": [
{
"recordId": "01txx0000006i44AAA",
"relatedObjectRecords": [
{
"count": 2,
"records": [
{
"SegmentType": "Yearly",
"DurationType": "Months",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx000000001dEAA",
"ProductId": "01txx0000006i44AAA",
"Id": "1FTxx0000004CDtGAM",
"Name": "PPRS-000000005"
},
{
"SegmentType": "FreeTrial",
"DurationType": "Days",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx000000001dEAA",
"ProductId": "01txx0000006i44AAA",
"Id": "1FTxx0000004CFUGA2",
"Name": "PPRS-000000006"
}
],
"relatedObjectAPIName": "ProductRampSegment"
},
{
"count": 2,
"records": [
{
"UsageMetricId": "1BRxx0000004CAeGAM",
"UsageMetricName": "Test Usage Metric 2",
"UsageDefinitionProductId": null,
"Label": "PUG-103",
245
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 260 =====

"Quantity": 100,
"Id": "1BXxx0000004CCGGA2"
},
{
"UsageMetricId": "1BRxx0000004CCGGA2",
"UsageMetricName": "Test Usage Metric 3",
"UsageDefinitionProductId": "01txx0000006i2eAAA",
"Label": "PUG-105",
"Quantity": 500,
"Id": "1BXxx0000004CFUGA2"
}
],
"relatedObjectAPIName": "ProductUsageGrant"
}
]
},
{
"recordId": "01txx0000006i5gAAA",
"relatedObjectRecords": [
{
"count": 4,
"records": [
{
"SegmentType": "Yearly",
"DurationType": "Months",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx0000000001EAA",
"ProductId": "01txx0000006i5gAAA",
"Id": "1FTxx0000004C92GAE",
"Name": "PPRS-000000001"
},
{
"SegmentType": "Custom",
"DurationType": "Days",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx0000000001EAA",
"ProductId": "01txx0000006i5gAAA",
"Id": "1FTxx0000004CAeGAM",
"Name": "PPRS-000000002"
},
{
"SegmentType": "FreeTrial",
"DurationType": "Months",
"TrialDuration": 6,
"ProductSellingModelId": "0jPxx0000000001EAA",
"ProductId": "01txx0000006i5gAAA",
"Id": "1FTxx0000004CCGGA2",
"Name": "PPRS-000000003"
},
{
"SegmentType": "Custom",
"DurationType": null,
"TrialDuration": null,
"ProductSellingModelId": "0jPxx0000000001EAA",
246
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 261 =====

"ProductId": "01txx0000006i5gAAA",
"Id": "1FTxx0000004CDsGAM",
"Name": "PPRS-000000004"
}
],
"relatedObjectAPIName": "ProductRampSegment"
},
{
"count": 0,
"records": [],
"relatedObjectAPIName": "ProductUsageGrant"
}
]
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0ID of the record.StringrecordId
62.0Small, 62.0List of related object records.Related Object
Records[]
relatedObject
Records
Related Records List
Output representation of the list of related records.
JSON example
{
"correlationId": "f4d6b42a-d9b7-49c9-8fa8-1c7bb6fe99aa",
"relatedRecords": [
{
"recordId": "01txx0000006i44AAA",
"relatedObjectRecords": [
{
"count": 2,
"records": [
{
"SegmentType": "Yearly",
"DurationType": "Months",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx000000001dEAA",
"ProductId": "01txx0000006i44AAA",
"Id": "1FTxx0000004CDtGAM",
"Name": "PPRS-000000005"
},
{
"SegmentType": "FreeTrial",
"DurationType": "Days",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx000000001dEAA",
"ProductId": "01txx0000006i44AAA",
247
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 262 =====

"Id": "1FTxx0000004CFUGA2",
"Name": "PPRS-000000006"
}
],
"relatedObjectAPIName": "ProductRampSegment"
},
{
"count": 2,
"records": [
{
"UsageMetricId": "1BRxx0000004CAeGAM",
"UsageMetricName": "Test Usage Metric 2",
"UsageDefinitionProductId": null,
"Label": "PUG-103",
"Quantity": 100,
"Id": "1BXxx0000004CCGGA2"
},
{
"UsageMetricId": "1BRxx0000004CCGGA2",
"UsageMetricName": "Test Usage Metric 3",
"UsageDefinitionProductId": "01txx0000006i2eAAA",
"Label": "PUG-105",
"Quantity": 500,
"Id": "1BXxx0000004CFUGA2"
}
],
"relatedObjectAPIName": "ProductUsageGrant"
}
]
},
{
"recordId": "01txx0000006i5gAAA",
"relatedObjectRecords": [
{
"count": 4,
"records": [
{
"SegmentType": "Yearly",
"DurationType": "Months",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx0000000001EAA",
"ProductId": "01txx0000006i5gAAA",
"Id": "1FTxx0000004C92GAE",
"Name": "PPRS-000000001"
},
{
"SegmentType": "Custom",
"DurationType": "Days",
"TrialDuration": null,
"ProductSellingModelId": "0jPxx0000000001EAA",
"ProductId": "01txx0000006i5gAAA",
"Id": "1FTxx0000004CAeGAM",
"Name": "PPRS-000000002"
},
248
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 263 =====

{
"SegmentType": "FreeTrial",
"DurationType": "Months",
"TrialDuration": 6,
"ProductSellingModelId": "0jPxx0000000001EAA",
"ProductId": "01txx0000006i5gAAA",
"Id": "1FTxx0000004CCGGA2",
"Name": "PPRS-000000003"
},
{
"SegmentType": "Custom",
"DurationType": null,
"TrialDuration": null,
"ProductSellingModelId": "0jPxx0000000001EAA",
"ProductId": "01txx0000006i5gAAA",
"Id": "1FTxx0000004CDsGAM",
"Name": "PPRS-000000004"
}
],
"relatedObjectAPIName": "ProductRampSegment"
},
{
"count": 0,
"records": [],
"relatedObjectAPIName": "ProductUsageGrant"
}
]
}
],
"status": {
"code": "200",
"errors": [
],
"message": ""
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Unique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
62.0Small, 62.0List of related records.Related Records[]related
Records
62.0Small, 62.0Status of the API request.Status[]status
249
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 264 =====

Search Facet
Output representation of the details of the faceted search.
JSON example
"facets":[
{
"attributeType": "ProductStandard",
"displayName": "Product Type",
"displayRank": 1,
"displayType": "MultiSelect",
"nameOrId": "Type",
"values": [
{
"displayName": "Simple",
"nameOrId": "Simple",
"productCount": 9
}
]
},
{
"attributeType": "ProductStandard",
"displayName": "Active",
"displayRank": 2,
"displayType": "MultiSelect",
"nameOrId": "IsActive",
"values": [
{
"displayName": "true",
"nameOrId": "true",
"productCount": 47
}
]
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Search attribute type of the facet.StringattributeType
63.0Small, 63.0Display name of the facet.StringdisplayName
63.0Small, 63.0Display rank of the facet.IntegerdisplayRank
63.0Small, 63.0Display type of the face.StringdisplayType
63.0Small, 63.0Facet name or ID. Reserved for internal use.StringnameOrId
63.0Small, 63.0Values of the facet found in the search
result. Sorted by display name in
alphabetical order.
Facet Value[]values
250
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 265 =====

Setting
Output representation of the setting that’s used in indexing.
JSON example
"setting": {
"defaultLanguage": "en_US",
"id": "1JySG0000000GUb0AM",
"supportedLanguages": ["en_US","ja","es","nl_NL"]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Default language for the API.Stringdefault
Language
63.0Small, 63.0ID of the setting.Stringid
63.0Small, 63.0List of supported language locales for
indexing.
String[]supported
Languages
Setting Metadata
Output representation of the metadata associated with a setting.
JSON example
"metadata": {
"activeLanguages": [
"en_US"
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of active languages in an org.String[]active
Languages
Snapshot
Output representation of the list of active snapshots.
JSON example
"snapshots": [
{
"activationDate": "2024-11-06T06:58:02.000Z",
"activationStatus": "ACTIVE",
"activationType": "IMMEDIATE",
"id": "1Avxx0000004C92CAE",
251
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 266 =====

"snapshotIndexes": [
{
"createdDate": "2024-11-06T06:56:49.000Z",
"id": "1D6xx0000004C92CAE",
"indexBuildType": "FULL",
"indexInfos": [
{
"buildType": "FULL",
"id": "0axxx00000000T3AAI",
"isIncrementable": true,
"usageType": "LIVE"
}
],
"indexLogs": [
{
"catalogSnapshotTime": "2024-11-06T16:14:30.000Z",
"completionTime": "2024-11-06T16:16:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED",
"indexBuildType": "FULL",
"indexId": "0axxx00000000T3AAI",
"numberOfChanges": 7
},
{
"catalogSnapshotTime": "2024-11-06T15:03:32.000Z",
"completionTime": "2024-11-06T15:05:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED_WITH_ERRORS",
"indexBuildType": "INCREMENTAL",
"indexId": "0axxx00000000RRAAY",
"message": "Warning: Product errors found.",
"numberOfChanges": 3
},
{
"catalogSnapshotTime": "2024-11-06T12:35:34.000Z",
"completionTime": "2024-11-06T12:35:34.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED",
"indexBuildType": "INCREMENTAL",
"indexId": "0axxx00000000RRAAY",
"message": "There are no changes for the partial update.",
"numberOfChanges": 0
},
{
"catalogSnapshotTime": "2024-11-06T12:07:32.000Z",
"completionTime": "2024-11-06T12:09:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED_WITH_ERRORS",
"indexBuildType": "FULL",
"message": "Warning: Product errors found.",
"numberOfChanges": 1
}
],
"indexType": "PRODUCT",
252
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 267 =====

"lastBuildStatus": "IN_PROGRESS",
"venueId": "1D6xx0000004C92CAE"
}
]
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Activation date of the snapshot.Stringactivation
Date
62.0Small, 62.0Activation status of the snapshot. Valid
values are:
Stringactivation
Status
• NONE
• ACTIVE—Snapshot is in active status.
• EXPIRED—Snapshot is in expired
status.
62.0Small, 62.0Activation type of the snapshot. Valid values
are:
Stringactivation
Type
• IMMEDIATE—Snapshot is activated
immediately after a successful build.
61.0Small, 61.0ID of the snapshot.Stringid
62.0Small, 62.0List of indexes created in the snapshot.Snapshot Index[]snapshot
Indexes
Snapshot Collection
Output representation of the retrieved snapshot collection.
JSON example
{
"errors": [],
"snapshots": [
{
"activationDate": "2024-11-06T06:58:02.000Z",
"activationStatus": "ACTIVE",
"activationType": "IMMEDIATE",
"id": "1Avxx0000004C92CAE",
"snapshotIndexes": [
{
"createdDate": "2024-11-06T06:56:49.000Z",
"id": "1D6xx0000004C92CAE",
"indexBuildType": "FULL",
"indexInfos": [
{
253
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 268 =====

"buildType": "FULL",
"id": "0axxx00000000T3AAI",
"isIncrementable": true,
"usageType": "LIVE"
}
],
"indexLogs": [
{
"catalogSnapshotTime": "2024-11-06T16:14:30.000Z",
"completionTime": "2024-11-06T16:16:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED",
"indexBuildType": "FULL",
"indexId": "0axxx00000000T3AAI",
"numberOfChanges": 7
},
{
"catalogSnapshotTime": "2024-11-06T15:03:32.000Z",
"completionTime": "2024-11-06T15:05:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED_WITH_ERRORS",
"indexBuildType": "INCREMENTAL",
"indexId": "0axxx00000000RRAAY",
"message": "Warning: Product errors found.",
"numberOfChanges": 3
},
{
"catalogSnapshotTime": "2024-11-06T12:35:34.000Z",
"completionTime": "2024-11-06T12:35:34.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED",
"indexBuildType": "INCREMENTAL",
"indexId": "0axxx00000000RRAAY",
"message": "There are no changes for the partial update.",
"numberOfChanges": 0
},
{
"catalogSnapshotTime": "2024-11-06T12:07:32.000Z",
"completionTime": "2024-11-06T12:09:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED_WITH_ERRORS",
"indexBuildType": "FULL",
"message": "Warning: Product errors found.",
"numberOfChanges": 1
}
],
"indexType": "PRODUCT",
"lastBuildStatus": "IN_PROGRESS",
"venueId": "1D6xx0000004C92CAE"
}
]
}
],
254
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 269 =====

"statusCode": "200"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0List of errors, if any.Error Output[]errors
62.0Small, 62.0List of active snapshots.Snapshot[]snapshots
62.0Small, 62.0Code indicating the status of the request.StringstatusCode
Snapshot Deployment
Output representation of the snapshot deployment.
JSON example
This example shows a sample response to the request to build a new snapshot with immediate activation.
{
"errors": [],
"snapshot": {
"activationStatus": "NONE",
"activationType": "IMMEDIATE",
"id": "1Avxx0000004CFU",
"snapshotIndexes": [
{
"createdDate": "2024-07-24T21:10:48.000Z",
"id": "1D6xx0000004CFU",
"indexBuildType": "FULL",
"indexType": "PRODUCT",
"lastBuildStatus": "IN_PROGRESS"
}
]
},
"statusCode": "200"
}
This example shows a sample response of the request to rebuild a snapshot in the active  status.
{
"errors": [],
"snapshot": {
"activationStatus": "NONE",
"activationType": "IMMEDIATE",
"id": "1Avxx0000004CH6",
"snapshotIndexes": [
{
"createdDate": "2024-07-24T21:13:05.000Z",
"id": "1D6xx0000004CH6",
"indexBuildType": "FULL",
"indexType": "PRODUCT",
"lastBuildStatus": "IN_PROGRESS"
}
]
255
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 270 =====

},
"statusCode": "200"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0List of errors, if any.Error Output[]errors
62.0Small, 62.0Run-time catalog snapshot associated with
the created index.
Snapshot[]snapshot
62.0Small, 62.0Code indicating the status of the request.StringstatusCode
Snapshot Index
Output representation of the snapshot index of a run-time catalog.
JSON example
"snapshotIndexes": [
{
"createdDate": "2024-11-06T06:56:49.000Z",
"id": "1D6xx0000004C92CAE",
"indexBuildType": "FULL",
"indexInfos": [
{
"buildType": "FULL",
"id": "0axxx00000000T3AAI",
"isIncrementable": true,
"usageType": "LIVE"
}
],
"indexLogs": [
{
"catalogSnapshotTime": "2024-11-06T16:14:30.000Z",
"completionTime": "2024-11-06T16:16:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED",
"indexBuildType": "FULL",
"indexId": "0axxx00000000T3AAI",
"numberOfChanges": 7
},
{
"catalogSnapshotTime": "2024-11-06T15:03:32.000Z",
"completionTime": "2024-11-06T15:05:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED_WITH_ERRORS",
"indexBuildType": "INCREMENTAL",
"indexId": "0axxx00000000RRAAY",
"message": "Warning: Product errors found.",
"numberOfChanges": 3
},
{
256
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 271 =====

"catalogSnapshotTime": "2024-11-06T12:35:34.000Z",
"completionTime": "2024-11-06T12:35:34.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED",
"indexBuildType": "INCREMENTAL",
"indexId": "0axxx00000000RRAAY",
"message": "There are no changes for the partial update.",
"numberOfChanges": 0
},
{
"catalogSnapshotTime": "2024-11-06T12:07:32.000Z",
"completionTime": "2024-11-06T12:09:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED_WITH_ERRORS",
"indexBuildType": "FULL",
"message": "Warning: Product errors found.",
"numberOfChanges": 1
}
],
"indexType": "PRODUCT",
"lastBuildStatus": "IN_PROGRESS",
"venueId": "1D6xx0000004C92CAE"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Completed date of the snapshot index.StringcompletedDate
62.0Small, 62.0Created date of the snapshot index.StringcreatedDate
62.0Small, 62.0ID of the snapshot index.Stringid
62.0Small, 62.0Build type of the snapshot index. Valid value
is:
StringindexBuild
Type
• FULL—Specifies a full index build.
• INCREMENTAL—Specifies an
incremental index build. Available in API
version 63.0 and later.
63.0Small, 63.0Index information records associated with
the snapshot index.
Index InfoindexInfos
63.0Small, 63.0Index logs associated with the snapshot
index.
Index Logs[]indexLogs
62.0Small, 62.0Index type of the snapshot index. Valid value
is:
StringindexType
• PRODUCT—Snapshot index is of
product type.
257
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 272 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Last build status of the snapshot index. Valid
values are:
StringlastBuild
Status
• IN_PROGRESS—Snapshot index
build is in progress.
• FAILED—Snapshot index build failed.
• COMPLETED—Snapshot index build
completed successfully.
62.0Small, 62.0Number of indexed records.IntegernumberOf
Records
63.0Small, 63.0Venue ID of the snapshot index.StringvenueId
Snapshot Index Error
Output representation of the error details related to a snapshot index.
JSON example
{
"errors": [],
"indexErrorDetails": {
"errorFileId": "069xx0000004C92AAE",
"indexCreatedDate": "2024-10-03T05:24:18.000Z",
"indexErrorsCount": 1,
"indexLastUpdatedDate": "2024-10-03T05:27:00.000Z",
"itemLevelErrorsCount": 1
},
"statusCode": "200"
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0List of errors encountered during the
processing of the API request.
Error Output[]errors
63.0Small, 63.0Count and details of errors that occurred
during indexing.
Index Error[]indexError
Details
63.0Small, 63.0Code that indicates the status of the API
request.
StringstatusCode
Snapshot Index Info
Output representation of the details of a snapshot index.
258
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 273 =====

JSON example
"indexInfos": [
{
"buildType": "FULL",
"id": "0axxx00000000T3AAI",
"isIncrementable": true,
"usageType": "LIVE"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Build type of the index. Valid values are:StringbuildType
• FULL—Specifies a full index build.
• INCREMENTAL—Specifies an
incremental index build. Available in API
version 63.0 and later.
63.0Small, 63.0ID of the index information record.Stringid
63.0Small, 63.0Indicates whether a partial build is enabled
(true) or disabled (false).
BooleanisIncrementable
63.0Small, 63.0Usage type of the index. Valid values are:StringusageType
• LIVE—Index usage type is live.
• OUT_OF_USE—Index usage type is
out of use.
Snapshot Index Log
Output representation of a snapshot index log.
JSON example
"indexLogs": [
{
"catalogSnapshotTime": "2024-11-06T16:14:30.000Z",
"completionTime": "2024-11-06T16:16:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED",
"indexBuildType": "FULL",
"indexId": "0axxx00000000T3AAI",
"numberOfChanges": 7
},
{
"catalogSnapshotTime": "2024-11-06T15:03:32.000Z",
"completionTime": "2024-11-06T15:05:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED_WITH_ERRORS",
259
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 274 =====

"indexBuildType": "INCREMENTAL",
"indexId": "0axxx00000000RRAAY",
"message": "Warning: Product errors found.",
"numberOfChanges": 3
},
{
"catalogSnapshotTime": "2024-11-06T12:35:34.000Z",
"completionTime": "2024-11-06T12:35:34.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED",
"indexBuildType": "INCREMENTAL",
"indexId": "0axxx00000000RRAAY",
"message": "There are no changes for the partial update.",
"numberOfChanges": 0
},
{
"catalogSnapshotTime": "2024-11-06T12:07:32.000Z",
"completionTime": "2024-11-06T12:09:02.000Z",
"createdById": "005xx000001X7x7AAC",
"indexBuildStatus": "COMPLETED_WITH_ERRORS",
"indexBuildType": "FULL",
"message": "Warning: Product errors found.",
"numberOfChanges": 1
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Catalog snapshot time of the index.Stringcatalog
SnapshotTime
63.0Small, 63.0Completion time of the index.Stringcompletion
Time
63.0Small, 63.0ID of the user that initiated the index build.StringcreatedById
63.0Small, 63.0Status of the index build.StringindexBuild
Status
63.0Small, 63.0Type of the index build. Valid values are:StringindexBuild
Type
• FULL—Specifies a full index build.
• INCREMENTAL—Specifies an
incremental index build. Available in API
version 63.0 and later.
63.0Small, 63.0ID of the index.StringindexId
63.0Small, 63.0Message for the index status.Stringmessage
63.0Small, 63.0Number of new or changed products
included in the index.
IntegernumberOf
Changes
260
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 275 =====

Status
Output representation of the status of the request.
JSON example
"status": {
"code": "200",
"errors": [],
"message": "Successfully fetched the catalog records."
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Code of the error message.Stringcode
60.0Small, 60.0Details of the error.Error[]errors
60.0Small, 60.0Error message.Stringmessage
Unit of Measure Error
Output representation of the details of errors encountered during the processing of the Unit of Measure API request.
JSON example
"errorCodeToErrorMap": {
"UNIT_OF_MEASURE_INFO_INVALID_UOM_IDS": {
"errorCode": "UOM_INFO_API_003",
"messageDetail": "Invalid uomId is passed. Please specify a valid uomId.",
"messageTitle": "Invalid uomId is passed.",
"recordIds": [
"sample"
],
"source": "Unit_Of_Measure_Info_Api"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Localized error code.StringerrorCode
63.0Small, 63.0Localized details of the error message.StringmessageDetail
63.0Small, 63.0Localized title of the error message.StringmessageTitle
63.0Small, 63.0List of erroneous record IDs.String[]recordIds
63.0Small, 63.0Localized source of the error.Stringsource
Unit of Measure Info
Output representation of the details of a unit of measure record.
261
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 276 =====

JSON example
"uomIdToUnitOfMeasureInfo": {
"0hEU200000003M5MAI": {
"id": "0hEU200000003M5MAI",
"name": "Pounds",
"roundingMethod": "Nearest",
"scale": 1,
"unitCode": "Pounds"
},
"0hEU200000003KTMAY": {
"id": "0hEU200000003KTMAY",
"name": "Grams",
"roundingMethod": "Down",
"scale": 5,
"unitCode": "Grams"
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0ID of the unit of measure record.Stringid
63.0Small, 63.0Name of the unit of measure record.Stringname
63.0Small, 63.0Data rounding method of the unit of
measure record.
StringroundingMethod
63.0Small, 63.0Scale of the unit of measure record.Integerscale
63.0Small, 63.0Code of the unit of measure record.StringunitCode
Unit of Measure Status
Output representation of the status of the Unit of Measure API request.
JSON example
"status": {
"errors": [],
"httpStatusCode": "200",
"message": " Successfully fetched UnitOfMeasure Info. "
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Errors encountered during the processing
of the API request.
Unit Of Measure
Error[]
errors
63.0Small, 63.0HTTP status code of the API request.StringhttpStatus
Code
63.0Small, 63.0Localized response message.Stringmessage
262
Product Catalog Management Business APIsProduct Catalog Management

===== PAGE 277 =====

Product Catalog Management Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
ProductCatalogManagementSettings
Represents the settings for Product Catalog Management.
ProductSpecificationType
Represents the specification types in your org that define products with unique terminology specific to the industry.
ProductSpecificationRecType
Represents the association of a product specification type with record types defined on the Product object. The product specification
record type also determines if the product specification is sold commercially or not.
SEE ALSO:
Metadata API Developer Guide: Understanding Metadata API
ProductCatalogManagementSettings
Represents the settings for Product Catalog Management.
Parent Type and Manifest Access
This type extends the Metadata metadata type and inherits its fullName field.
In the package manifest, all the settings metadata types for the org are accessed using the “Settings” name. See Settings for more details.
File Suffix and Directory Location
ProductCatalogManagementSettings values are stored in the ProductCatalogManagementSettings.settings
file in the settings  folder. The .settings  files are different from other named components, because there is only one settings
file for each settings component.
Version
ProductCatalogManagementSettings components are available in API version 64.0 and later.
Special Access Rules
These settings are available when Product Catalog Management is enabled.
Fields
DescriptionField Name
Field Type
string
productDeepCloneContextDefOrgValue
Description
Name of the context definition that you want to use to deep clone the product.
263
Product Catalog Management Metadata API TypesProduct Catalog Management

===== PAGE 278 =====

DescriptionField Name
Field Type
string
productDeepCloneExpressionSetOrgValue
Description
Expression set that contains the rules that you want to apply to deep clone the product.
Declarative Metadata Sample Definition
The following is an example of a ProductCatalogManagementSettings component.
<ProductCatalogManagementSettings xmlns="http://soap.sforce.com/2006/04/metadata">
<productDeepCloneContextDefOrgValue>ProductDeepCloneContextDefinition</productDeepCloneContextDefOrgValue>
<productDeepCloneExpressionSetOrgValue>ProductDeepCloneExpressionSet</productDeepCloneExpressionSetOrgValue>
</ProductCatalogManagementSettings>
The following is an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>ProductCatalogManagement</members>
<name>Settings</name>
</types>
<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
The wildcard character *  (asterisk) in the package.xml manifest file doesn’t apply to metadata types for feature settings. The wildcard
applies only when retrieving all settings, not for an individual setting. For details, see Settings. For information about using the manifest
file, see Deploying and Retrieving Metadata with the Zip File.
ProductSpecificationType
Represents the specification types in your org that define products with unique terminology specific to the industry.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Parent Type
This type extends the Metadata metadata type and inherits its fullName  field.
File Suffix and Directory Location
ProductSpecificationType components have the suffix .productSpecificationType  and are stored in the
productSpecificationTypes  folder.
264
Product Catalog Management Metadata API TypesProduct Catalog Management

===== PAGE 279 =====

Version
ProductSpecificationType components are available in API version 60.0 and later.
Special Access Rules
Ensure Product Catalog Management is enabled to access this metadata type.
Fields
DescriptionField Name
Field Type
string
description
Description
Required.
Description of the product specification type.
Field Type
string
masterLabel
Description
Required.
A user-friendly name for the product specification record type, which is defined when
the metadata component is created.
Declarative Metadata Sample Definition
The following is an example of a ProductSpecificationType component.
<ProductSpecificationType xmlns="http://soap.sforce.com/2006/04/metadata">
<masterLabel>sample</masterLabel>
<description>Sample Description</description>
</ProductSpecificationType>
The following is an example package.xml  that references the previous definition.
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>*</members>
<name>ProductSpecificationType</name>
</types>
<version>66.0</version>
</Package>
265
Product Catalog Management Metadata API TypesProduct Catalog Management

===== PAGE 280 =====

Wildcard Support in the Manifest File
This metadata type supports the wildcard character * (asterisk) in the package.xml  manifest file. For information about using the
manifest file, see Deploying and Retrieving Metadata with the Zip File.
ProductSpecificationRecType
Represents the association of a product specification type with record types defined on the Product object. The product specification
record type also determines if the product specification is sold commercially or not.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Parent Type
This type extends the Metadata metadata type and inherits its fullName  field.
File Suffix and Directory Location
ProductSpecificationRecType components have the suffix .productSpecificationRecType  and are stored in the
productSpecificationRecTypes  folder.
Version
ProductSpecificationRecType components are available in API version 60.0 and later.
Special Access Rules
Ensure Product Catalog Management is enabled to access this metadata type.
Fields
DescriptionField Name
Field Type
boolean
isCommercial
Description
Required. Indicates whether the product is sold commercially (true) or not (false).
The default value is true.
Field Type
string
masterLabel
Description
Required.
A user-friendly name for the product specification record type, which is defined when
the metadata component is created.
266
Product Catalog Management Metadata API TypesProduct Catalog Management

===== PAGE 281 =====

DescriptionField Name
Field Type
string
productSpecificationType
Description
Required.
Product specification type that's associated with the record type. This field is unique
within your organization.
Field Type
string
recordType
Description
Required.
Custom record type of Product2 object.
Declarative Metadata Sample Definition
The following is an example of a ProductSpecificationRecType component.
<ProductSpecificationRecType xmlns="http://soap.sforce.com/2006/04/metadata">
<masterLabel>sample</masterLabel>
<recordType>Product2.Offer</recordType>
<productSpecificationType>Placeholder</productSpecificationType>
<isCommercial>true</isCommercial>
</ProductSpecificationRecType>
The following is an example package.xml  that references the previous definition.
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>*</members>
<name>ProductSpecificationRecType</name>
</types>
<types>
<members>*</members>
<name>ProductSpecificationType</name>
</types>
<types>
<members>Product2.Offer</members>
<name>RecordType</name>
</types>
<version>66.0</version>
</Package>
267
Product Catalog Management Metadata API TypesProduct Catalog Management

===== PAGE 282 =====

Wildcard Support in the Manifest File
This metadata type supports the wildcard character * (asterisk) in the package.xml  manifest file. For information about using the
manifest file, see Deploying and Retrieving Metadata with the Zip File.
Product Catalog Management Tooling API Objects
Tooling API exposes metadata used in developer tooling that you can access through REST or SOAP. Tooling API’s SOQL capabilities for
many metadata types allow you to retrieve smaller pieces of metadata.
ProductSpecificationType
Represents the specification types in your org that define products with unique terminology specific to the industry. This object is
available in API version 60.0 and later.
ProductSpecificationRecType
Represents the association of a product specification type with record types defined on the Product object. The product specification
record type also determines if the product specification is sold commercially or not. This object is available in API version 60.0 and
later.
SEE ALSO:
Tooling API Developer Guide: Introducing Tooling API
ProductSpecificationType
Represents the specification types in your org that define products with unique terminology specific to the industry. This object is
available in API version 60.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
Special Access Rules
Ensure Product Catalog Management is enabled to access this object.
Fields
DetailsField
Type
textarea
Description
268
Product Catalog Management Tooling API ObjectsProduct Catalog Management

===== PAGE 283 =====

DetailsField
Properties
Create, Nillable, Update
Description
Description of the product specification type.
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The unique name of the object in the API. This name can contain only underscores and
alphanumeric characters, and must be unique in your org. It must begin with a letter, not
include spaces, not end with an underscore, and not contain two consecutive underscores.
In managed packages, this field prevents naming conflicts on package installations. With
this field, a developer can change the object’s name in a managed package and the changes
are reflected in a subscriber’s organization. Label is Record Type Name.
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Language of the product specification type instance.
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
269
Product Catalog Management Tooling API ObjectsProduct Catalog Management

===== PAGE 284 =====

DetailsField
• zh_CN—Chinese (Simplified)
• zh_TW—Chinese (Traditional)
Type
picklist
ManageableState
Properties
Filter, Group, Nillable, Restricted picklist, Sort
Description
Type
ManageableState enumerated list
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
Label assigned to the ProductSpecificationType object.
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
270
Product Catalog Management Tooling API ObjectsProduct Catalog Management

===== PAGE 285 =====

DetailsField
• In Developer Edition organizations, the namespace prefix is set to the namespace prefix
of the organization for all objects that support it. There is an exception if an object is in
an installed managed package. In that case, the object has the namespace prefix of the
installed managed package. This field’s value is the namespace prefix of the Developer
Edition organization of the package developer.
• In organizations that are not Developer Edition organizations, NamespacePrefix
is only set for objects that are part of an installed managed package. There is no
namespace prefix for all other objects.
ProductSpecificationRecType
Represents the association of a product specification type with record types defined on the Product object. The product specification
record type also determines if the product specification is sold commercially or not. This object is available in API version 60.0 and later.
Important:  Where possible, we changed noninclusive terms to align with our company value of Equality. We maintained certain
terms to avoid any effect on customer implementations.
Supported SOAP API Calls
create(), delete(), describeSObjects(), query(), retrieve(), update(), upsert()
Supported REST API Methods
DELETE, GET, HEAD, PATCH, POST, Query
Special Access Rules
Ensure Product Catalog Management is enabled to access this object.
Fields
DetailsField
Type
string
DeveloperName
Properties
Create, Filter, Group, Sort, Update
Description
The unique name of the object in the API. This name can contain only underscores and
alphanumeric characters, and must be unique in your org. It must begin with a letter, not
include spaces, not end with an underscore, and not contain two consecutive underscores.
In managed packages, this field prevents naming conflicts on package installations. With
this field, a developer can change the object’s name in a managed package and the changes
are reflected in a subscriber’s organization. Label is Record Type Name.
271
Product Catalog Management Tooling API ObjectsProduct Catalog Management

===== PAGE 286 =====

DetailsField
Type
boolean
IsCommercial
Properties
Create, Defaulted on create, Filter, Group, Sort, Update
Description
Indicates whether the product is sold commercially (true) or not (false). The default
value is true.
Type
picklist
Language
Properties
Create, Defaulted on create, Filter, Group, Nillable, Restricted picklist, Sort, Update
Description
Language of the product specification record type instance.
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
picklist
ManageableState
Properties
Filter, Group, Nillable, Restricted picklist, Sort
272
Product Catalog Management Tooling API ObjectsProduct Catalog Management

===== PAGE 287 =====

DetailsField
Description
Type
ManageableState enumerated list
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
Label assigned to the ProductSpecificationRecType object.
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
273
Product Catalog Management Tooling API ObjectsProduct Catalog Management

===== PAGE 288 =====

DetailsField
Type
picklist
ProductSpecificationType
Properties
Create, Filter, Group, Restricted picklist, Sort, Update
Description
Required.
Product specification type that's associated with the record type. This field is unique within
your organization.
The picklist values that are available to you depend on your industry solution and permission
sets.
Type
sObject
RecordType
Properties
Nillable
Description
Custom record type of Product2 object.
Type
reference
RecordTypeId
Properties
Create, Filter, Group, Sort, Update
Description
Required. ID of the product record type associated with the product specification type. This
field is unique within your organization.
This field is a relationship field.
Relationship Name
RecordType
Relationship Type
Lookup
Refers To
RecordType
274
Product Catalog Management Tooling API ObjectsProduct Catalog Management

===== PAGE 289 =====

Product Discovery
EDITIONS
Available in: Lightning
Experience
Available in: Enterprise,
Unlimited, and Developer
Editions of Revenue Cloud
Product Discovery provides a hierarchical catalog browsing experience to identify suitable products
with text-based and faceted search.
Product Discovery Business APIs
Use the Product Discovery Business APIs, which are composite APIs, to search products or to
discover catalogs, products, and categories during the product browsing experience.
Product Discovery Standard Invocable Actions
Use the standard invocable actions available with Product Discovery to find and retrieve product,
category, and catalog details. Additionally, execute a qualification procedure, and search products
with guided selection.
Product Discovery Apex Reference
Use built-in Apex classes and interfaces grouped by namespace.
Product Discovery Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
SEE ALSO:
Salesforce Help: Configure Product Discovery Settings
Salesforce Help: Invoke Qualification Procedures During Product Discovery
Product Discovery Business APIs
Use the Product Discovery Business APIs, which are composite APIs, to search products or to discover catalogs, products, and categories
during the product browsing experience.
This table lists the available Product Discovery resources.
DescriptionResource
Get catalog details for a
specified catalog ID. This API is
/connect/cpq/catalogs/catalogId (POST)
a composite API for Product
Discovery.
Get a paginated list of catalogs.
This API is a composite API for
Product Discovery.
/connect/cpq/catalogs (POST)
Get a list of categories and
subcategories of a specified
/connect/cpq/categories (POST)
catalog. This API is a composite
API for Product Discovery.
Get details of a category for a
specified category ID. This API
/connect/cpq/categories/categoryId (POST)
is a composite API for Product
Discovery.
275
Product DiscoveryProduct Catalog Management

===== PAGE 290 =====

DescriptionResource
Run the qualification procedure
on a list of product IDs. This API
/connect/cpq/qualification (POST)
is a composite API for Product
Discovery.
Retrieves a list of products
based on a search query or
/connect/cpq/products/search (POST)
search term. This API is a
composite API for Product
Discovery.
Get product details, such as
attributes, hierarchy, or
/connect/cpq/products/productId (POST)
cardinality, for a specified
product ID. This API is a
composite API for Product
Discovery.
Get a list of products for a
specified catalog, category, or
/connect/cpq/products (POST)
subcategory. This API is a
composite API for Product
Discovery.
Retrieve details for multiple
products. This API is a
/connect/cpq/products/bulk (POST)
composite API for Product
Discovery.
Retrieve a list of products based
on the response identifier or
/connect/cpq/products/guided-selection (POST)
search terms of a guided
selection. Guided selection
captures user requirements to
show suitable products.
Resources
Learn more about the available Product Discovery API resources.
Request Bodies
Learn more about the available Product Discovery API request bodies.
Response Bodies
Learn more about the available Product Discovery API response bodies.
Resources
Learn more about the available Product Discovery API resources.
276
Product Discovery Business APIsProduct Catalog Management

===== PAGE 291 =====

Catalog Details (POST)
Get catalog details for a specified catalog ID. This API is a composite API for Product Discovery.
Catalog List (POST)
Get a paginated list of catalogs. This API is a composite API for Product Discovery.
Categories List (POST)
Get a list of categories and subcategories of a specified catalog. This API is a composite API for Product Discovery.
Category Details (POST)
Get details of a category for a specified category ID. This API is a composite API for Product Discovery.
Bulk Product Details (POST)
Retrieve details for multiple products. This API is a composite API for Product Discovery.
Global Search (POST)
Retrieves a list of products based on a search query or search term. This API is a composite API for Product Discovery.
Guided Selection (POST)
Retrieve a list of products based on the response identifier or search terms of a guided selection. Guided selection captures user
requirements to show suitable products.
Product Details (POST)
Get product details, such as attributes, hierarchy, or cardinality, for a specified product ID. This API is a composite API for Product
Discovery.
Products List (POST)
Get a list of products for a specified catalog, category, or subcategory. This API is a composite API for Product Discovery.
Qualification (POST)
Run the qualification procedure on a list of product IDs. This API is a composite API for Product Discovery.
Catalog Details (POST)
Get catalog details for a specified catalog ID. This API is a composite API for Product Discovery.
Resource
/connect/cpq/catalogs/catalogId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/catalogs/0ZSxx000000009hGAA
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
277
Product Discovery Business APIsProduct Catalog Management

===== PAGE 292 =====

}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
Stringcorrelation
Id
references to a particular transaction or
event chain.
60.0OptionalUser context details. For example,
account ID or contact ID.
User Context InputuserContext
Response body for POST
CPQ Base Details
Catalog List (POST)
Get a paginated list of catalogs. This API is a composite API for Product Discovery.
Resource
/connect/cpq/catalogs
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/catalogs
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"limit": 10,
"offset": 0,
"orderBy": [
"name:asc",
"id:desc"
],
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
278
Product Discovery Business APIsProduct Catalog Management

===== PAGE 293 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
Stringcorrelation
Id
references to a particular transaction or
event chain.
60.0OptionalNumber of items to include in the
response.
Integerlimit
60.0OptionalOffset size from which to get the catalog
count.
Integeroffset
60.0OptionalSort order for the catalogs.String[]orderBy
60.0OptionalUser context details. For example,
account ID or contact ID.
User Context InputuserContext
Response body for POST
CPQ Base List
Categories List (POST)
Get a list of categories and subcategories of a specified catalog. This API is a composite API for Product Discovery.
Resource
/connect/cpq/categories
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/categories
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx000000009hGAA",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
279
Product Discovery Business APIsProduct Catalog Management

===== PAGE 294 =====

This example shows a sample request to get a list of categories with eligible promotions.
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx000000009hGAA",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"usePromotions": true
}
Response body for POST
CPQ Base List
Category Details (POST)
Get details of a category for a specified category ID. This API is a composite API for Product Discovery.
Resource
/connect/cpq/categories/categoryId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/categories/0ZGxx000000001dGAA
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
This example shows a sample request to get category details with eligible promotions.
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"usePromotions": true
}
280
Product Discovery Business APIsProduct Catalog Management

===== PAGE 295 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data Inputadditional
ContextData
maximum number of supported nodes
is 10.
60.0OptionalID of the catalog. If the catalog ID is
specified, then the API returns the list of
StringcatalogId
offers from the catalog with the pricing
details related to the catalog.
60.0OptionalAPI name of the custom context
definition that’s sent for context creation.
Stringcontext
Definition
If this property isn’t specified, then the
default context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether
the mapping belongs to the specified
context definition to process the details
for hydration.
60.0OptionalList of category fields to retrieve in the
response.
String[]customFields
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
Stringcorrelation
Id
references to a particular transaction or
event chain.
60.0OptionalIndicates whether to enable qualification
rules for the categories (true) or not
(false). The default value is true.
The Qualification Procedure toggle
from the Product Discovery Settings page
Booleanenable
Qualification
from Setup overrides this property. For
example, if the Qualification Procedure
toggle is disabled, then setting the
enableQualification  property
to true  has no effect and the
qualificationContext property
in the API response isn’t returned.
60.0OptionalFilters records based on supported
criteria.
Filter Inputfilter
The supported property is name.
281
Product Discovery Business APIsProduct Catalog Management

===== PAGE 296 =====

Available
Version
Required or
Optional
DescriptionTypeName
The supported operators are:
• eq
• in
• contains
• gt—Specifies a greater than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• lt—Specifies a less than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• gte—Specifies a greater than or
equal to criteria. Available from API
version 63.0 and later for Number,
Date, and Datetime data types only.
• lte—Specifies a less than or equal
to criteria. Available from API version
63.0 and later for Number, Date, and
Datetime data types only.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and  operator.
60.0OptionalAPI name of the custom qualification
procedure that’s used for the qualification
Stringqualification
Procedure
process. If this property isn’t specified,
then the default qualification procedure
is executed.
60.0OptionalUser context details. For example,
account ID or contact ID.
User Context InputuserContext
66.0OptionalIndicates whether to fetch eligible
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for the requested
category and its products (true) or not
(false). If Promotion feature is enabled
in the org and this property isn't
specified, then the default value is true.
If the Promotion feature isn't enabled, the
default value is false.
282
Product Discovery Business APIsProduct Catalog Management

===== PAGE 297 =====

Response body for POST
CPQ Base Details
Bulk Product Details (POST)
Retrieve details for multiple products. This API is a composite API for Product Discovery.
Resource
/connect/cpq/products/bulk
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/products/bulk
Available version
61.0
HTTP methods
POST
Request body for POST
JSON example
{
"productData": [
{
"productId": "01txx0000006ivJAAQ",
"productSellingModelId": "0jPxx000000009hEAA"
},
{
"productId": "01txx0000006ivLAAQ",
"productSellingModelId": "0jPxx000000009iEAABB"
}
],
"correlationId": "de9a674c-1807-438c-ac78-2c96f4655325",
"priceBookId" : "01sxx0000005qxxAAA",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
This example shows a sample request with proration policy details requested through the additionalFields property.
{
"additionalFields": {
"ProductSellingModelOption": {
"additionalFields": {
"ProrationPolicy": {
"fields": [
"ArePartialPeriodsAllowed",
"ProrationPolicyType"
]
}
}
283
Product Discovery Business APIsProduct Catalog Management

===== PAGE 298 =====

}
},
"productData": [
{
"productId": "01txx0000006ivJAAQ",
"productSellingModelId": "0jPxx000000009hEAA"
},
{
"productId": "01txx0000006ivLAAQ",
"productSellingModelId": "0jPxx000000009iEAABB"
}
],
"correlationId": "de9a674c-1807-438c-ac78-2c96f4655325",
"priceBookId": "01sxx0000005qxxAAA",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalAdditional nodes to add to the custom
or default context definition. This data is
Context Data
Input[]
additional
ContextData
appended to the context input and sent
for hydration and qualification. The
maximum limit of supported nodes is 10.
61.0OptionalAdditional standard or custom fields of
the Product2 object to include in the
Map<String,
Additional Fields
Input>
additional
Fields
response. The field values are returned in
the response for each of the products.
In API version 66.0 and later, you can
request proration policy details in the
response for each product selling model
option through this property.
61.0OptionalName of the custom context definition
that’s sent for the context creation. If
Stringcontext
Definition
unspecified, the default context definition
is used.
61.0OptionalContext mapping details from the
context definition. If specified, the API
Stringcontext
Mapping
validates if the context mapping belongs
to the specified context definition and
considers the mapping for hydration.
284
Product Discovery Business APIsProduct Catalog Management

===== PAGE 299 =====

Available
Version
Required or
Optional
DescriptionTypeName
If unspecified, the default context
mapping of the context definition is used.
61.0OptionalUnique token to track and associate
related events or transactions across
Stringcorrelation
Id
different components of the application.
If unspecified, a Universally Unique
Identifier (UUID) is generated.
61.0OptionalCurrency code to consider for pricing and
filtering.
StringcurrencyCode
61.0OptionalIndicates whether to enable pricing for
the products (true) or not (false).
The default value is true.
The Pricing Procedure toggle from the
Product Discovery Settings page from
Booleanenable
Pricing
Setup overrides this property. For
example, if the Pricing Procedure toggle
is disabled, then setting the
enablePricing  property to true
has no effect and the prices  property
in the API response is returned empty.
61.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
The Qualification Procedure toggle
from the Product Discovery Settings page
Booleanenable
Qualification
from Setup overrides this property. For
example, if the Qualification Procedure
toggle is disabled, then setting the
enableQualification property
to true  has no effect and the
qualificationContext property
in the API response isn’t returned.
61.0OptionalID of the price book to fetch the prices
from.
StringpriceBookId
61.0OptionalName of the custom pricing procedure
to send for processing. If unspecified, the
default pricing procedure is executed.
Stringpricing
Procedure
61.0RequiredList of maps that contain product IDs and
product selling model IDs.
Product Data
Input[]
productData
285
Product Discovery Business APIsProduct Catalog Management

===== PAGE 300 =====

Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalName of the custom qualification
procedure to send for processing. If
Stringqualification
Procedure
unspecified, the default qualification
procedure is executed.
61.0OptionalUser context details. For example,
account ID or contact ID.
User Context
Input[]
userContext
Response body for POST
Bulk Product Details
Global Search (POST)
Retrieves a list of products based on a search query or search term. This API is a composite API for Product Discovery.
Resource
/connect/cpq/products/search
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/products/search
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
This example shows a sample request to search products by using a query.
{
"query": {
"textQuery": {
"searchPhrase": "firstproduct"
}
},
"catalogId": "0ZSxx0000000001GAA",
"categoryId": "0ZGT100000000qlOAA",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc",
"id:desc"
],
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
286
Product Discovery Business APIsProduct Catalog Management

===== PAGE 301 =====

},
"additionalFields": {
"Product2": {
"fields": [
"CustomField1__c",
"CustomField2__c",
"StandardField1"
]
}
}
}
This example shows a sample request to search products by using the searchTerm property.
{
"searchTerm": "Laptop",
"catalogId": "0ZSDU0000002Og64AE",
"categoryId": "0ZGDU0000002P0A4AU",
"correlationId": "d9d8f898-19f5-464a-ba2b-6a070783f6c4",
"limit": 10,
"cursor": "MTAwMDAwMDAwNw==",
"orderBy": [
"name:asc",
"id:desc"
],
"userContext": {
"accountId": "001DU000001o2V0YAI"
}
}
If a parent category ID is specified in the request body, then the API returns all products associated to all child categories.
This example shows a sample request to search products with eligible promotions. To fetch eligible promotions, specify a value
for the query  or searchTerm  property, and set the usePromotions  property to true.
{
"query": {
"textQuery": {
"searchPhrase": "laptop"
}
},
"catalogId": "0ZSxx0000000001GAA",
"categoryId": "0ZGT100000000qlOAA",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc",
"id:desc"
],
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"additionalFields": {
"Product2": {
287
Product Discovery Business APIsProduct Catalog Management

===== PAGE 302 =====

"fields": [
"CustomField1__c",
"CustomField2__c",
"StandardField1"
]
}
},
"usePromotions": true
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data
Input[]
additional
ContextData
maximum number of supported nodes
is 10.
61.0OptionalAdditional standard or custom fields of
the Product2 object to include in the
response.
Map<String,
Additional Fields
Input>
additional
Fields
If the requested fields are invalid or access
to fields isn’t available, then the API
throws an error.
60.0OptionalID of the catalog. If the catalog ID is
specified, then the API returns the list of
StringcatalogId
offers from the catalog with the pricing
details related to the catalog.
60.0OptionalID of the category. If the category ID isn’t
specified, then the API returns the
matching query offers from the catalog.
StringcategoryId
60.0OptionalAPI name of the custom context
definition that’s sent for context creation.
Stringcontext
Definition
If this property isn’t specified, then the
default context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether
the mapping belongs to the specified
context definition to process the details
for hydration.
60.0OptionalUnique identifier of the request.Stringcorrelation
Id
60.0OptionalCurrency code that’s considered for
pricing and filtering request.
StringcurrencyCode
288
Product Discovery Business APIsProduct Catalog Management

===== PAGE 303 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalUnique ID to represent the position of
each product in the dataset.
Stringcursor
60.0OptionalIndicates whether to enable pricing for
the products (true) or not (false).
The default value is true.
The Pricing Procedure toggle from the
Product Discovery Settings page from
Booleanenable
Pricing
Setup overrides this property. For
example, if the Pricing Procedure toggle
is disabled, then setting the
enablePricing  property to true
has no effect and the prices  property
in the API response is returned empty.
60.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
The Qualification Procedure toggle
from the Product Discovery Settings page
Booleanenable
Qualification
from Setup overrides this property. For
example, if the Qualification Procedure
toggle is disabled, then setting the
enableQualification property
to true  has no effect and the
qualificationContext property
in the API response isn’t returned.
60.0OptionalFilters records based on supported
criteria.
Filter Inputfilter
The supported property is name.
The supported operators are:
• eq
• in
• contains
• gt—Specifies a greater than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• lt—Specifies a less than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
289
Product Discovery Business APIsProduct Catalog Management

===== PAGE 304 =====

Available
Version
Required or
Optional
DescriptionTypeName
• gte—Specifies a greater than or
equal to criteria. Available from API
version 63.0 and later for Number,
Date, and Datetime data types only.
• lte—Specifies a less than or equal
to criteria. Available from API version
63.0 and later for Number, Date, and
Datetime data types only.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and  operator.
61.0OptionalIndicates whether to include catalog
details in the response (true) or not
(false).
Booleaninclude
CatalogDetails
60.0OptionalNumber of items to include in the
response. The default value is 10.
Integerlimit
60.0OptionalReserved for internal use.Integeroffset
60.0OptionalSort order of the results, which is either
ascending or descending order. The
String[]orderBy
default sort order is ascending order. The
default value is asc.
60.0OptionalID of the price book to get the prices
from. If this property isn’t specified, then
StringpriceBookId
prices from the standard price book are
fetched.
60.0OptionalAPI name of the custom pricing
procedure that’s used for the pricing
StringpricingProcedure
process. If this property isn’t specified,
then the default pricing procedure is
executed.
60.0OptionalID of the product classification.Stringproduct
ClassificationId
60.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
60.0RequiredQuery to search the products.Map<String,
Object>
query
290
Product Discovery Business APIsProduct Catalog Management

===== PAGE 305 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalFilter records based on supported criteria
for related objects.
Related Object
Filter Input[]
related
ObjectFilter
The supported object is
ProductSpecificationRecType.
The supported property is
IsCommerical.
The supported operator is eq.
The supported values are true  and
false.
62.0OptionalString used to get products with the
product name containing the search
StringsearchTerm
term. See Search Considerations When
Using Indexed Data.
66.0OptionalIndicates whether to retrieve eligible
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for each product in
the search results (true) or not
(false). If Promotion feature is enabled
in the org and this property isn't
specified, then the default value is true.
If the Promotion feature isn't enabled, the
default value is false.
60.0OptionalUser context details. For example,
account ID or contact ID.
User Context InputuserContext
Response body for POST
CPQ Base List
Guided Selection (POST)
Retrieve a list of products based on the response identifier or search terms of a guided selection. Guided selection captures user
requirements to show suitable products.
Resource
/connect/cpq/products/guided-selection
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/products/guided-selection
Available version
62.0
291
Product Discovery Business APIsProduct Catalog Management

===== PAGE 306 =====

HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "corrId",
"catalogId": "0ZSxx0000000001GAA",
"priceBookId": "pricebookId",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"userContext": {
"accountId": "accId"
},
"guidedSelectionResponseId": "ABCxx0000000001GAA",
"searchTerms": [
{
"term": "IPhone",
"tags": [
"deviceType",
"mobile"
]
},
{
"term": "4GB",
"tags": [
"RAM"
]
},
{
"term": "64GB",
"tags": [
"Storage"
]
}
],
"enableQualification": true,
"enablePricing": true,
"includeCatalogDetails": false
}
This example shows a sample request to fetch eligible promotions.
{
"correlationId": "corrId",
"catalogId": "0ZSxx0000000001GAA",
"priceBookId": "pricebookId",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"userContext": {
"accountId": "accId"
},
"guidedSelectionResponseId": "ABCxx0000000001GAA",
"searchTerms": [
292
Product Discovery Business APIsProduct Catalog Management

===== PAGE 307 =====

{
"term": "IPhone",
"tags": [
"deviceType",
"mobile"
]
},
{
"term": "4GB",
"tags": [
"RAM"
]
},
{
"term": "64GB",
"tags": [
"Storage"
]
}
],
"enableQualification": true,
"enablePricing": true,
"includeCatalogDetails": false,
"transactionContextId": "context123",
"transactionId": "trans456",
"usePromotions": true
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data
Input[]
additional
ContextData
maximum number of supported nodes
is 10.
62.0OptionalAdditional standard or custom fields of
the Product2 object to include in the
response.
Map<String,
Additional Fields
Input>
additional
Fields
If the requested fields are invalid or access
to fields isn’t available, then the API
throws an error.
62.0RequiredID of the catalog.StringcatalogId
62.0OptionalID of the category.StringcategoryId
62.0OptionalAPI name of the custom context
definition that’s sent for context creation.
Stringcontext
Definition
If this property isn’t specified, then the
default context definition is used.
293
Product Discovery Business APIsProduct Catalog Management

===== PAGE 308 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether
the mapping belongs to the specified
context definition to process the details
for hydration.
62.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
Stringcorrelation
Id
references to a particular transaction or
event chain.
62.0OptionalCurrency code that’s considered for
pricing and filtering request. If multiple
StringcurrencyCode
currencies are enabled for the org, then
the currencyCode  property is
required.
62.0OptionalUnique ID to represent the position of
each product in the dataset.
Stringcursor
62.0OptionalIndicates whether to enable pricing for
the products (true) or not (false).
The default value is true.
Booleanenable
Pricing
62.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
Booleanenable
Qualification
62.0OptionalFilters records based on supported
criteria.
Filter Inputfilter
The supported property is name.
The supported operators are:
• eq
• in
• contains—This value isn't
applicable if the Use Indexed Data
For Product Listing and Search
toggle from the Product Discovery
Settings page from Setup is enabled.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and  operator.
62.0Required if the
searchTerms
Response identifier of the guided
selection.
Stringguided
Selection
ResponseId
294
Product Discovery Business APIsProduct Catalog Management

===== PAGE 309 =====

Available
Version
Required or
Optional
DescriptionTypeName
property isn’t
specified.
62.0OptionalIndicates whether to include catalog
details in the response (true) or not
(false).
Booleaninclude
Catalog
Details
62.0OptionalNumber of items to include in the
response. The default value is 10.
Integerlimit
62.0OptionalSort order of the results, which is either
ascending (asc) or descending order
String[]orderBy
(desc). The default sort order is
ascending order. The default value is
asc.
If the Use Indexed Data For Product
Listing and Search toggle from the
Product Discovery Settings page from
Setup is enabled, then you can sort
products by using name only.
62.0RequiredID of the price book to get the prices
from. If this property isn’t specified, then
StringpriceBookId
prices from the standard price book are
fetched.
62.0OptionalAPI name of the custom pricing
procedure that’s used for the pricing
Stringpricing
Procedure
process. If this property isn’t specified,
then the default pricing procedure is
executed.
62.0OptionalID of the product classification.Stringproduct
Classification
Id
62.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
62.0Required if the
guided
Search terms of the guided selection.Guided Selection
Search Term Input[]
searchTerms
Selection
ResponseId
property isn’t
specified.
295
Product Discovery Business APIsProduct Catalog Management

===== PAGE 310 =====

Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalIndicates whether to fetch applicable
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for the guided
selection (true) or not (false). If
Promotion feature is enabled in the org
and this property isn't specified, then the
default value is true. If the Promotion
feature isn't enabled, the default value is
false.
62.0OptionalUser context details. For example,
account ID or contact ID.
User Context InputuserContext
If both the guidedSelectionResponseId  and searchTerms  properties are specified, then the searchTerms
property is considered in the input request.
Response body for POST
Guided Selection
Product Details (POST)
Get product details, such as attributes, hierarchy, or cardinality, for a specified product ID. This API is a composite API for Product Discovery.
Resource
/connect/cpq/products/productId
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/products/01txx0000006j08AAA
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx0000000001GAA",
"priceBookId": "01s26000002ZT71AAG",
"productSellingModelId": "0jP1Q000000CaVFUA0",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"enablePricing": true,
"enableQualification": true,
296
Product Discovery Business APIsProduct Catalog Management

===== PAGE 311 =====

"qualificationProcedure": "QualificationProcedure",
"pricingProcedure": "Preview",
"contextDefinition": "TestDefinition",
"contextMapping": "TestDefinitionNode",
"additionalFields": {
"ProductSellingModelOption": {
"additionalFields": {
"ProrationPolicy": {
"fields": [
"ArePartialPeriodsAllowed",
"ProrationPolicyType"
]
}
}
},
"Product2": {
"fields": [
"field1",
"field2"
]
},
"ProductAttributeDefinition": {
"fields": [
"field3",
"field4"
]
}
},
"additionalContextData": [
{
"nodeName": "Contract",
"nodeData": {
"id": "xxxxx231",
"name": "Contract1"
}
},
{
"nodeName": "Lead",
"nodeData": {
"id": "lllllll31",
"name": "Lead1"
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
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data
Input[]
additional
ContextData
297
Product Discovery Business APIsProduct Catalog Management

===== PAGE 312 =====

Available
Version
Required or
Optional
DescriptionTypeName
maximum number of supported nodes
is 10.
61.0OptionalAdditional standard or custom fields to
include in the response.
The supported objects are:
Map<String,
Additional Fields
Input>
additional
Fields
• Product2
• ProductAttributeDefinition—If the
fields defined for the
ProductAttributeDefinition object
aren’t available for the
ProductClassificationAttr object, then
the API request fails.
In API version 66.0 and later, you can
request proration policy details in the
response for each product selling model
option through this property.
60.0OptionalID of the catalog. If the catalog ID is
specified, then the API returns the list of
StringcatalogId
offers from the catalog with the pricing
details related to the catalog.
60.0OptionalAPI name of the custom context
definition that’s sent for context creation.
Stringcontext
Definition
If this property isn’t specified, then the
default context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether
the mapping belongs to the specified
context definition to process the details
for hydration.
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
Stringcorrelation
Id
references to a particular transaction or
event chain.
60.0OptionalCurrency code that’s considered for
pricing and filtering request. If multiple
StringcurrencyCode
currencies are enabled for the org, then
the currencyCode  property is
required.
298
Product Discovery Business APIsProduct Catalog Management

===== PAGE 313 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalIndicates whether to enable pricing for
the products (true) or not (false).
The default value is true.
The Pricing Procedure toggle from the
Product Discovery Settings page from
Booleanenable
Pricing
Setup overrides this property. For
example, if the Pricing Procedure toggle
is disabled, then setting the
enablePricing  property to true
has no effect and the prices  property
in the API response is returned empty.
60.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
The Qualification Procedure toggle
from the Product Discovery Settings page
Booleanenable
Qualification
from Setup overrides this property. For
example, if the Qualification Procedure
toggle is disabled, then setting the
enableQualification property
to true  has no effect and the
qualificationContext property
in the API response isn’t returned.
60.0RequiredID of the price book to fetch the prices
from. If this property isn’t specified, then
StringpriceBookId
the prices from the standard price book
are fetched.
60.0OptionalAPI name of the custom pricing
procedure that’s used for the pricing
Stringpricing
Procedure
process. If this property isn’t specified,
then the default pricing procedure is
executed.
60.0OptionalID of the product selling model.Stringproduct
SellingModel
Id
60.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
299
Product Discovery Business APIsProduct Catalog Management

===== PAGE 314 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalUser context details. For example,
account ID or contact ID.
User Context InputuserContext
Response body for POST
CPQ Base Details
Products List (POST)
Get a list of products for a specified catalog, category, or subcategory. This API is a composite API for Product Discovery.
Resource
/connect/cpq/products
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/products
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"correlationId": "eeaa1db2-f371-4227-a886-c77e2f66ce1d",
"limit": 60,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc"
],
"catalogId": "0ZSDU0000002Og74AE",
"categoryId": "0ZGDU0000002P0H4AU",
"priceBookId": "01sDU000000JVsVYAW",
"productClassificationId": "11BDU0000002TCC2A2",
"currencyCode": "USD",
"userContext": {
"accountId": "001DU000001o2UzYAI"
},
"includeCatalogDetails": true,
"enableQualification": true,
"enablePricing": true,
"qualificationProcedure": "ProductQualification",
"pricingProcedure": "pricingProcedure",
"contextDefinition": "BrowseContextDefinitionExt",
"contextMapping": "ProductDiscoveryMapping",
"filter": {
"criteria": [
{
300
Product Discovery Business APIsProduct Catalog Management

===== PAGE 315 =====

"property": "name",
"operator": "eq",
"value": "Laptop Pro Bundle"
}
]
},
"relatedObjectFilters": [
{
"objectName": "ProductSpecificationRecType",
"criteria": [
{
"property": "IsCommercial",
"operator": "eq",
"value": true
}
]
}
],
"additionalContextData": [
{
"nodeName": "Account",
"nodeData": {
"id": "001DU000001o2UzYAI",
"name": "Cloud Kicks"
}
}
],
"additionalFields": {
"Product2": {
"fields": [
"CanRamp",
"DecompositionScope",
"ProductCode"
]
}
}
}
If a parent category ID is specified in the request body, then the API returns all products associated to all child categories.
This example shows a sample request to retrieve a product list with promotions.
{
"correlationId": "eeaa1db2-f371-4227-a886-c77e2f66ce1d",
"limit": 60,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc"
],
"catalogId": "0ZSDU0000002Og74AE",
"categoryId": "0ZGDU0000002P0H4AU",
"priceBookId": "01sDU000000JVsVYAW",
"productClassificationId": "11BDU0000002TCC2A2",
"currencyCode": "USD",
"userContext": {
301
Product Discovery Business APIsProduct Catalog Management

===== PAGE 316 =====

"accountId": "001DU000001o2UzYAI"
},
"includeCatalogDetails": true,
"enableQualification": true,
"enablePricing": true,
"qualificationProcedure": "ProductQualification",
"pricingProcedure": "pricingProcedure",
"contextDefinition": "BrowseContextDefinitionExt",
"contextMapping": "ProductDiscoveryMapping",
"filter": {
"criteria": [
{
"property": "name",
"operator": "eq",
"value": "Laptop Pro Bundle"
}
]
},
"relatedObjectFilters": [
{
"objectName": "ProductSpecificationRecType",
"criteria": [
{
"property": "IsCommercial",
"operator": "eq",
"value": true
}
]
}
],
"additionalContextData": [
{
"nodeName": "Account",
"nodeData": {
"id": "001DU000001o2UzYAI",
"name": "Cloud Kicks"
}
}
],
"additionalFields": {
"Product2": {
"fields": [
"CanRamp",
"DecompositionScope",
"ProductCode"
]
}
},
"executeConfigurationRules": false,
"transactionContextId": "a1b2c3d4e5f6",
"transactionId": "trans789",
"usePromotions": true
}
302
Product Discovery Business APIsProduct Catalog Management

===== PAGE 317 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data
Input[]
additional
ContextData
maximum number of supported nodes
is 10.
61.0OptionalAdditional standard or custom fields of
the Product2 object to include in the
response.
Map<String,
Additional Fields
Input>
additional
Fields
If the requested fields are invalid or access
to fields isn’t available, then the API
throws an error.
60.0OptionalID of the catalog. If the catalog ID is
specified, then the API returns the list of
StringcatalogId
offers from the catalog with the pricing
details related to the catalog.
60.0OptionalID of the category. If the category ID isn’t
specified, then the API returns the list of
offers from the catalog.
StringcategoryId
60.0OptionalAPI name of the custom context
definition that’s sent for context creation.
Stringcontext
Definition
If this property isn’t specified, then the
default context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether
the mapping belongs to the specified
context definition to process the details
for hydration.
60.0OptionalUnique identifier of the request.Stringcorrelation
Id
60.0OptionalCurrency code that’s considered for
pricing and filtering request. If multiple
StringcurrencyCode
currencies are enabled for the org, then
the currencyCode  property is
required.
60.0OptionalUnique ID to represent the position of
each product in the dataset.
Stringcursor
303
Product Discovery Business APIsProduct Catalog Management

===== PAGE 318 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalIndicates whether to enable pricing for
the products (true) or not (false).
The default value is true.
The Pricing Procedure toggle from the
Product Discovery Settings page from
Booleanenable
Pricing
Setup overrides this property. For
example, if the Pricing Procedure toggle
is disabled, then setting the
enablePricing  property to true
has no effect and the prices  property
in the API response is returned empty.
60.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
The Qualification Procedure toggle
from the Product Discovery Settings page
Booleanenable
Qualification
from Setup overrides this property. For
example, if the Qualification Procedure
toggle is disabled, then setting the
enableQualification  property
to true  has no effect and the
qualificationContext property
in the API response isn’t returned.
60.0OptionalFilters records based on supported
criteria.
Filter Inputfilter
The supported property is name.
The supported operators are:
• eq
• in
• contains—This value isn't
applicable if the Use Indexed Data
For Product Listing and Search
toggle from the Product Discovery
Settings page from Setup is enabled.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and  operator.
61.0OptionalIndicates whether to include catalog
details in the response (true) or not
(false).
Booleaninclude
Catalog
Details
304
Product Discovery Business APIsProduct Catalog Management

===== PAGE 319 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalNumber of items to include in the
response. The default value is 10.
Integerlimit
60.0OptionalReserved for internal use.Integeroffset
60.0OptionalSort order of the results, which is either
ascending (asc) or descending order
String[]orderBy
(desc). The default sort order is
ascending order. The default value is
asc.
If the Use Indexed Data For Product
Listing and Search toggle from the
Product Discovery Settings page from
Setup is enabled, then you can sort
products by using name only.
60.0RequiredID of the price book to get the prices
from. If this property isn’t specified, then
StringpriceBookId
prices from the standard price book are
fetched.
60.0OptionalAPI name of the custom pricing
procedure that’s used for the pricing
Stringpricing
Procedure
process. If this property isn’t specified,
then the default pricing procedure is
executed.
60.0OptionalID of the product classification.Stringproduct
Classification
Id
60.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
60.0OptionalFilter records based on supported criteria
for related objects.
Related Object
Filter Input[]
related
Object
Filters
The supported object is
ProductSpecificationRecType.
The supported property is
IsCommerical.
The supported operator is eq.
The supported values are true  and
false.
305
Product Discovery Business APIsProduct Catalog Management

===== PAGE 320 =====

Available
Version
Required or
Optional
DescriptionTypeName
66.0OptionalIndicates whether to fetch applicable
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for each product in
the list (true) or not (false). If
Promotion feature is enabled in the org
and this property isn't specified, then the
default value is true. If the Promotion
feature isn't enabled, the default value is
false.
60.0OptionalUser context details. For example,
account ID or contact ID.
User Context InputuserContext
Response body for POST
CPQ Base List
Qualification (POST)
Run the qualification procedure on a list of product IDs. This API is a composite API for Product Discovery.
Resource
/connect/cpq/qualification
Resource example
https://yourInstance.salesforce.com/services/data/v66.0/connect/cpq/qualification
Available version
60.0
HTTP methods
POST
Request body for POST
JSON example
{
"productIds": [
"01txx0000006i7PAAQ",
"01txx0000006i7QAAQ",
"01txx0000006i7IAAQ"
],
"userContext": {
"accountId": "001xx000003GZHgAAO"
}
}
306
Product Discovery Business APIsProduct Catalog Management

===== PAGE 321 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data
Input[]
additional
ContextData
maximum number of supported nodes
is 10.
60.0OptionalID of the catalog.StringcatalogId
60.0OptionalID of the category.StringcategoryId
60.0OptionalAPI name of the custom context
definition that’s sent for context creation.
Stringcontext
Definition
If this property isn’t specified, the default
context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether
the mapping belongs to the specified
context definition to process the details
for hydration.
60.0OptionalUnique identifier of the request.Stringcorrelation
Id
60.0RequiredList of product IDs for qualification check.String[]productIds
60.0OptionalAPI name of the custom qualification
procedure that’s sent for processing. If
Stringqualification
Procedure
this property isn’t specified, the default
qualification procedure is executed.
60.0OptionalUser context details. For example,
account ID or contact ID.
User Context InputuserContext
Response body for POST
CPQ Base List
Request Bodies
Learn more about the available Product Discovery API request bodies.
Additional Fields Input
Input representation of the additional standard or custom fields to include in the response.
Bulk Product Details Input
Input representation of the request to retrieve details of multiple products.
307
Product Discovery Business APIsProduct Catalog Management

===== PAGE 322 =====

Catalog Details Input
Input representation of the request to get the catalog details.
Catalog List Input
Input representation of the request to get a list of catalogs.
Category Details Input
Input representation of the request to get category details.
Category List Input
Input representation of the request to get a list of categories.
Context Data Input
Input representation of the context data.
Guided Selection Input
Input representation of the guided selection details.
Guided Selection Search Term Input
Input representation of the search terms of a guided selection.
Filter Criteria Input
Input representation of the criteria to filter records based on supported properties.
Filter Input
Input representation of the request to filter records.
Product Details Input
Input representation of the request to get product details.
Product Data Input
Input representation of the product details such as the product ID and product selling model ID.
Product List Input
Input representation of the request to retrieve a list of products.
Products Search Input
Input representation of the request to search products.
QOC Qualification
Input representation of the qualification request.
Related Object Filter Input
Input representation of the request to filter records of a related object.
User Context Input
Input representation of the details with the user context.
Additional Fields Input
Input representation of the additional standard or custom fields to include in the response.
JSON example
"additionalFields" : {
"Product2" : {
"fields" : ["CustomField1__c","StandardField1"]
}
}
308
Product Discovery Business APIsProduct Catalog Management

===== PAGE 323 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalList of additional standard or custom fields
to include in the response.
String[]fields
Bulk Product Details Input
Input representation of the request to retrieve details of multiple products.
JSON example
{
"productData": [
{
"productId": "01txx0000006ivJAAQ",
"productSellingModelId": "0jPxx000000009hEAA"
},
{
"productId": "01txx0000006ivLAAQ",
"productSellingModelId": "0jPxx000000009iEAABB"
}
],
"correlationId": "de9a674c-1807-438c-ac78-2c96f4655325",
"priceBookId" : "01sxx0000005qxxAAA",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
This example shows a sample request with proration policy details requested through the additionalFields property.
{
"additionalFields": {
"ProductSellingModelOption": {
"additionalFields": {
"ProrationPolicy": {
"fields": [
"ArePartialPeriodsAllowed",
"ProrationPolicyType"
]
}
}
}
},
"productData": [
{
"productId": "01txx0000006ivJAAQ",
"productSellingModelId": "0jPxx000000009hEAA"
},
{
309
Product Discovery Business APIsProduct Catalog Management

===== PAGE 324 =====

"productId": "01txx0000006ivLAAQ",
"productSellingModelId": "0jPxx000000009iEAABB"
}
],
"correlationId": "de9a674c-1807-438c-ac78-2c96f4655325",
"priceBookId": "01sxx0000005qxxAAA",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalAdditional nodes to add to the custom or
default context definition. This data is
Context Data Input[]additional
ContextData
appended to the context input and sent
for hydration and qualification. The
maximum limit of supported nodes is 10.
61.0OptionalAdditional standard or custom fields of the
Product2 object to include in the response.
Map<String,
Additional Fields
Input>
additional
Fields
The field values are returned in the
response for each of the products.
In API version 66.0 and later, you can
request proration policy details in the
response for each product selling model
option through this property.
61.0OptionalName of the custom context definition
that’s sent for the context creation. If
Stringcontext
Definition
unspecified, the default context definition
is used.
61.0OptionalContext mapping details from the context
definition. If specified, the API validates if
Stringcontext
Mapping
the context mapping belongs to the
specified context definition and considers
the mapping for hydration.
If unspecified, the default context mapping
of the context definition is used.
61.0OptionalUnique token to track and associate related
events or transactions across different
StringcorrelationId
components of the application. If
unspecified, a Universally Unique Identifier
(UUID) is generated.
310
Product Discovery Business APIsProduct Catalog Management

===== PAGE 325 =====

Available
Version
Required or
Optional
DescriptionTypeName
61.0OptionalCurrency code to consider for pricing and
filtering.
StringcurrencyCode
61.0OptionalIndicates whether to enable pricing for the
products (true) or not (false). The
default value is true.
The Pricing Procedure toggle from the
Product Discovery Settings page from
BooleanenablePricing
Setup overrides this property. For example,
if the Pricing Procedure toggle is
disabled, then setting the
enablePricing  property to true
has no effect and the prices  property
in the API response is returned empty.
61.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
The Qualification Procedure toggle from
the Product Discovery Settings page from
Booleanenable
Qualification
Setup overrides this property. For example,
if the Qualification Procedure toggle is
disabled, then setting the
enableQualification property to
true  has no effect and the
qualificationContext  property
in the API response isn’t returned.
61.0OptionalID of the price book to fetch the prices
from.
StringpriceBookId
61.0OptionalName of the custom pricing procedure to
send for processing. If unspecified, the
default pricing procedure is executed.
Stringpricing
Procedure
61.0RequiredList of maps that contain product IDs and
product selling model IDs.
Product Data Input[]productData
61.0OptionalName of the custom qualification
procedure to send for processing. If
Stringqualification
Procedure
unspecified, the default qualification
procedure is executed.
61.0OptionalUser context details. For example, account
ID or contact ID.
User Context Input[]userContext
311
Product Discovery Business APIsProduct Catalog Management

===== PAGE 326 =====

Catalog Details Input
Input representation of the request to get the catalog details.
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
StringcorrelationId
references to a particular transaction or
event chain.
60.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
Catalog List Input
Input representation of the request to get a list of catalogs.
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"limit": 10,
"offset": 0,
"orderBy": [
"name:asc",
"id:desc"
],
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
StringcorrelationId
312
Product Discovery Business APIsProduct Catalog Management

===== PAGE 327 =====

Available
Version
Required or
Optional
DescriptionTypeName
references to a particular transaction or
event chain.
60.0OptionalNumber of items to include in the
response.
Integerlimit
60.0OptionalOffset size from which to get the catalog
count.
Integeroffset
60.0OptionalSort order for the catalogs.String[]orderBy
60.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
Category Details Input
Input representation of the request to get category details.
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
}
}
This example shows a sample request to get category details with eligible promotions.
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"usePromotions": true
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data Inputadditional
ContextData
maximum number of supported nodes is
10.
60.0OptionalID of the catalog. If the catalog ID is
specified, then the API returns the list of
StringcatalogId
313
Product Discovery Business APIsProduct Catalog Management

===== PAGE 328 =====

Available
Version
Required or
Optional
DescriptionTypeName
offers from the catalog with the pricing
details related to the catalog.
60.0OptionalAPI name of the custom context definition
that’s sent for context creation. If this
Stringcontext
Definition
property isn’t specified, then the default
context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether the
mapping belongs to the specified context
definition to process the details for
hydration.
60.0OptionalList of category fields to retrieve in the
response.
String[]customFields
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
StringcorrelationId
references to a particular transaction or
event chain.
60.0OptionalIndicates whether to enable qualification
rules for the categories (true) or not
(false). The default value is true.
The Qualification Procedure toggle from
the Product Discovery Settings page from
Booleanenable
Qualification
Setup overrides this property. For example,
if the Qualification Procedure toggle is
disabled, then setting the
enableQualification property to
true  has no effect and the
qualificationContext  property
in the API response isn’t returned.
60.0OptionalFilters records based on supported criteria.Filter Inputfilter
The supported property is name.
The supported operators are:
• eq
• in
• contains
• gt—Specifies a greater than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
314
Product Discovery Business APIsProduct Catalog Management

===== PAGE 329 =====

Available
Version
Required or
Optional
DescriptionTypeName
• lt—Specifies a less than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• gte—Specifies a greater than or
equal to criteria. Available from API
version 63.0 and later for Number,
Date, and Datetime data types only.
• lte—Specifies a less than or equal
to criteria. Available from API version
63.0 and later for Number, Date, and
Datetime data types only.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and  operator.
60.0OptionalAPI name of the custom qualification
procedure that’s used for the qualification
Stringqualification
Procedure
process. If this property isn’t specified, then
the default qualification procedure is
executed.
60.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
66.0OptionalIndicates whether to fetch eligible
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for the requested
category and its products (true) or not
(false). If Promotion feature is enabled
in the org and this property isn't specified,
then the default value is true. If the
Promotion feature isn't enabled, the
default value is false.
Category List Input
Input representation of the request to get a list of categories.
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx000000009hGAA",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
315
Product Discovery Business APIsProduct Catalog Management

===== PAGE 330 =====

}
}
This example shows a sample request to get a list of categories with eligible promotions.
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx000000009hGAA",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"usePromotions": true
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data Input[]additional
ContextData
maximum number of supported nodes is
10.
60.0RequiredID of the catalog.StringcatalogId
60.0OptionalAPI name of the custom context definition
that’s sent for context creation. If this
Stringcontext
Definition
property isn’t specified, then the default
context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether the
mapping belongs to the specified context
definition to process the details for
hydration.
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
StringcorrelationId
references to a particular transaction or
event chain.
60.0OptionalList of additional custom fields to include
in the response.
String[]customFields
61.0OptionalSpecifies the levels of subcategories to
retrieve beneath the parent category. This
Integerdepth
parameter only applies when
parentCategoryId  is provided.
60.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
BooleanenableQualification
316
Product Discovery Business APIsProduct Catalog Management

===== PAGE 331 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalFilters records based on supported criteria.
The supported property is
isQualified.
Filter Inputfilter
The supported operators are:
• eq
• in
• contains—This value isn't
applicable if the Use Indexed Data
For Product Listing and Search
toggle from the Product Discovery
Settings page from Setup is enabled.
61.0OptionalID of the parent category whose
subcategories you want to retrieve. If not
Stringparent
CategoryId
specified, only root-level categories from
the catalog are returned.
60.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
66.0OptionalIndicates whether to fetch eligible
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for the requested
category and its products (true) or not
(false). If Promotion feature is enabled
in the org and this property isn't specified,
then the default value is true. If the
Promotion feature isn't enabled, the
default value is false.
60.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
Context Data Input
Input representation of the context data.
JSON example
"additionalContextData":[
{
"nodeName": "Contract",
"nodeData": {
317
Product Discovery Business APIsProduct Catalog Management

===== PAGE 332 =====

"id": "xxxxx231",
"name": "Contract1"
}
},
{
"nodeName": "Lead",
"nodeData": {
"id": "lllllll31",
"name": "Lead1"
}
}]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalDetails of the node.Map<String,
Object>
nodeData
60.0OptionalName of the node.StringnodeName
Guided Selection Input
Input representation of the guided selection details.
JSON example
{
"correlationId": "corrId",
"catalogId": "0ZSxx0000000001GAA",
"priceBookId": "pricebookId",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"userContext": {
"accountId": "accId"
},
"guidedSelectionResponseId": "ABCxx0000000001GAA",
"searchTerms": [
{
"term": "IPhone",
"tags": [
"deviceType",
"mobile"
]
},
{
"term": "4GB",
"tags": [
"RAM"
]
},
318
Product Discovery Business APIsProduct Catalog Management

===== PAGE 333 =====

{
"term": "64GB",
"tags": [
"Storage"
]
}
],
"enableQualification": true,
"enablePricing": true,
"includeCatalogDetails": false
}
This example shows a sample request to fetch eligible promotions.
{
"correlationId": "corrId",
"catalogId": "0ZSxx0000000001GAA",
"priceBookId": "pricebookId",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"userContext": {
"accountId": "accId"
},
"guidedSelectionResponseId": "ABCxx0000000001GAA",
"searchTerms": [
{
"term": "IPhone",
"tags": [
"deviceType",
"mobile"
]
},
{
"term": "4GB",
"tags": [
"RAM"
]
},
{
"term": "64GB",
"tags": [
"Storage"
]
}
],
"enableQualification": true,
"enablePricing": true,
"includeCatalogDetails": false,
"transactionContextId": "context123",
"transactionId": "trans456",
"usePromotions": true
}
319
Product Discovery Business APIsProduct Catalog Management

===== PAGE 334 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data Input[]additional
ContextData
maximum number of supported nodes is
10.
62.0OptionalAdditional standard or custom fields of the
Product2 object to include in the response.
Map<String,
Additional Fields
Input>
additional
Fields
If the requested fields are invalid or access
to fields isn’t available, then the API throws
an error.
62.0RequiredID of the catalog.StringcatalogId
62.0OptionalID of the category.StringcategoryId
62.0OptionalAPI name of the custom context definition
that’s sent for context creation. If this
Stringcontext
Definition
property isn’t specified, then the default
context definition is used.
62.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether the
mapping belongs to the specified context
definition to process the details for
hydration.
62.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
StringcorrelationId
references to a particular transaction or
event chain.
62.0OptionalCurrency code that’s considered for pricing
and filtering request. If multiple currencies
StringcurrencyCode
are enabled for the org, then the
currencyCode  property is required.
62.0OptionalUnique ID to represent the position of each
product in the dataset.
Stringcursor
62.0OptionalIndicates whether to enable pricing for the
products (true) or not (false). The
default value is true.
BooleanenablePricing
62.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
Booleanenable
Qualification
320
Product Discovery Business APIsProduct Catalog Management

===== PAGE 335 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalFilters records based on supported criteria.Filter Inputfilter
The supported property is name.
The supported operators are:
• eq
• in
• contains—This value isn't
applicable if the Use Indexed Data
For Product Listing and Search
toggle from the Product Discovery
Settings page from Setup is enabled.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and  operator.
62.0Required if the
searchTerms
Response identifier of the guided selection.Stringguided
Selection
ResponseId property isn’t
specified.
62.0OptionalIndicates whether to include catalog
details in the response (true) or not
(false).
Booleaninclude
Catalog
Details
62.0OptionalNumber of items to include in the
response. The default value is 10.
Integerlimit
62.0OptionalSort order of the results, which is either
ascending (asc) or descending order
String[]orderBy
(desc). The default sort order is ascending
order. The default value is asc.
If the Use Indexed Data For Product
Listing and Search toggle from the
Product Discovery Settings page from
Setup is enabled, then you can sort
products by using name only.
62.0RequiredID of the price book to get the prices from.
If this property isn’t specified, then prices
from the standard price book are fetched.
StringpriceBookId
62.0OptionalAPI name of the custom pricing procedure
that’s used for the pricing process. If this
Stringpricing
Procedure
property isn’t specified, then the default
pricing procedure is executed.
321
Product Discovery Business APIsProduct Catalog Management

===== PAGE 336 =====

Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalID of the product classification.Stringproduct
Classification
Id
62.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
62.0Required if the
guided
Search terms of the guided selection.Guided Selection
Search Term Input[]
searchTerms
Selection
ResponseId
property isn’t
specified.
66.0OptionalIndicates whether to fetch applicable
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for the guided
selection (true) or not (false). If
Promotion feature is enabled in the org
and this property isn't specified, then the
default value is true. If the Promotion
feature isn't enabled, the default value is
false.
62.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
If both the guidedSelectionResponseId  and searchTerms  properties are specified, then the searchTerms
property is considered in the input request.
Guided Selection Search Term Input
Input representation of the search terms of a guided selection.
JSON example
"searchTerms": [
{
"term": "IPhone",
"tags": [
"deviceType",
"mobile"
]
},
{
"term": "4GB",
322
Product Discovery Business APIsProduct Catalog Management

===== PAGE 337 =====

"tags": [
"RAM"
]
},
{
"term": "64GB",
"tags": [
"Storage"
]
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
62.0OptionalSearch term tags for the guided
selection.
String[]tags
62.0RequiredSearch term for the guided
selection.
Stringterm
Filter Criteria Input
Input representation of the criteria to filter records based on supported properties.
JSON example
"criteria":
[{
"attributeType": "ProductStandard",
"property": "name",
"operator": "eq",
"value": "iPhone"
}]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
63.0OptionalSearch attribute type of the facet for a
faceted search. Valid values are:
StringattributeType
• ProductStandard
• ProductCustom
• ProductDynamicAttribute
• ProductAttributeStandard
• ProductAttributeCustom
60.0RequiredOperator used for the filter criteria.Stringoperator
323
Product Discovery Business APIsProduct Catalog Management

===== PAGE 338 =====

Available
Version
Required or
Optional
DescriptionTypeName
The supported operators are:
• eq
• in
• contains
• gt—Specifies a greater than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• lt—Specifies a less than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• gte—Specifies a greater than or
equal to criteria. Available from API
version 63.0 and later for Number,
Date, and Datetime data types only.
• lte—Specifies a less than or equal
to criteria. Available from API version
63.0 and later for Number, Date, and
Datetime data types only.
60.0RequiredProperty name to use in the filter, which
must be the same as the object field.
Stringproperty
The supported property is name.
60.0RequiredValue for the filter criteria.Objectvalue
Filter Input
Input representation of the request to filter records.
JSON example
"filter":
{"criteria":
[ {
"attributeType": "ProductStandard",
"property": "name",
"operator": "eq",
"value": "iPhone"
}]}
324
Product Discovery Business APIsProduct Catalog Management

===== PAGE 339 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalFilter criteria to filter the records.Filter Criteria Input[]criteria
Product Details Input
Input representation of the request to get product details.
JSON example
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx0000000001GAA",
"priceBookId": "01s26000002ZT71AAG",
"productSellingModelId": "0jP1Q000000CaVFUA0",
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"enablePricing": true,
"enableQualification": true,
"qualificationProcedure": "QualificationProcedure",
"pricingProcedure": "Preview",
"contextDefinition": "TestDefinition",
"contextMapping": "TestDefinitionNode",
"additionalFields": {
"ProductSellingModelOption": {
"additionalFields": {
"ProrationPolicy": {
"fields": [
"ArePartialPeriodsAllowed",
"ProrationPolicyType"
]
}
}
},
"Product2": {
"fields": [
"field1",
"field2"
]
},
"ProductAttributeDefinition": {
"fields": [
"field3",
"field4"
]
}
},
"additionalContextData": [
{
325
Product Discovery Business APIsProduct Catalog Management

===== PAGE 340 =====

"nodeName": "Contract",
"nodeData": {
"id": "xxxxx231",
"name": "Contract1"
}
},
{
"nodeName": "Lead",
"nodeData": {
"id": "lllllll31",
"name": "Lead1"
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
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data Input[]additional
ContextData
maximum number of supported nodes is
10.
61.0OptionalAdditional standard or custom fields to
include in the response.
The supported objects are:
Map<String,
Additional Fields
Input>
additional
Fields
• Product2
• ProductAttributeDefinition—If the
fields defined for the
ProductAttributeDefinition object
aren’t available for the
ProductClassificationAttr object, then
the API request fails.
In API version 66.0 and later, you can
request proration policy details in the
response for each product selling model
option through this property.
60.0OptionalID of the catalog. If the catalog ID is
specified, then the API returns the list of
StringcatalogId
offers from the catalog with the pricing
details related to the catalog.
60.0OptionalAPI name of the custom context definition
that’s sent for context creation. If this
Stringcontext
Definition
property isn’t specified, then the default
context definition is used.
326
Product Discovery Business APIsProduct Catalog Management

===== PAGE 341 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether the
mapping belongs to the specified context
definition to process the details for
hydration.
60.0OptionalUnique identifier value that’s attached to
the requests and messages, and accepts
StringcorrelationId
references to a particular transaction or
event chain.
60.0OptionalCurrency code that’s considered for pricing
and filtering request. If multiple currencies
StringcurrencyCode
are enabled for the org, then the
currencyCode  property is required.
60.0OptionalIndicates whether to enable pricing for the
products (true) or not (false). The
default value is true.
The Pricing Procedure toggle from the
Product Discovery Settings page from
BooleanenablePricing
Setup overrides this property. For example,
if the Pricing Procedure toggle is
disabled, then setting the
enablePricing  property to true
has no effect and the prices  property
in the API response is returned empty.
60.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
The Qualification Procedure toggle from
the Product Discovery Settings page from
Booleanenable
Qualification
Setup overrides this property. For example,
if the Qualification Procedure toggle is
disabled, then setting the
enableQualification property to
true  has no effect and the
qualificationContext  property
in the API response isn’t returned.
60.0RequiredID of the price book to fetch the prices
from. If this property isn’t specified, then
StringpriceBookId
the prices from the standard price book
are fetched.
327
Product Discovery Business APIsProduct Catalog Management

===== PAGE 342 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAPI name of the custom pricing procedure
that’s used for the pricing process. If this
Stringpricing
Procedure
property isn’t specified, then the default
pricing procedure is executed.
60.0OptionalID of the product selling model.Stringproduct
SellingModel
Id
60.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
60.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
Product Data Input
Input representation of the product details such as the product ID and product selling model ID.
JSON example
"productData": [
{
"productId": "01txx0000006ivJAAQ",
"productSellingModelId": "0jPxx000000009hEAA"
},
{
"productId": "01txx0000006ivLAAQ",
"productSellingModelId": "0jPxx000000009iEAABB"
}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
61.0RequiredID of the product.StringproductId
61.0OptionalID of the product selling model.Stringproduct
Selling
ModelId
Product List Input
Input representation of the request to retrieve a list of products.
328
Product Discovery Business APIsProduct Catalog Management

===== PAGE 343 =====

JSON example
{
"correlationId": "eeaa1db2-f371-4227-a886-c77e2f66ce1d",
"limit": 60,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc"
],
"catalogId": "0ZSDU0000002Og74AE",
"categoryId": "0ZGDU0000002P0H4AU",
"priceBookId": "01sDU000000JVsVYAW",
"productClassificationId": "11BDU0000002TCC2A2",
"currencyCode": "USD",
"userContext": {
"accountId": "001DU000001o2UzYAI"
},
"includeCatalogDetails": true,
"enableQualification": true,
"enablePricing": true,
"qualificationProcedure": "ProductQualification",
"pricingProcedure": "pricingProcedure",
"contextDefinition": "BrowseContextDefinitionExt",
"contextMapping": "ProductDiscoveryMapping",
"filter": {
"criteria": [
{
"property": "name",
"operator": "eq",
"value": "Laptop Pro Bundle"
}
]
},
"relatedObjectFilters": [
{
"objectName": "ProductSpecificationRecType",
"criteria": [
{
"property": "IsCommercial",
"operator": "eq",
"value": true
}
]
}
],
"additionalContextData": [
{
"nodeName": "Account",
"nodeData": {
"id": "001DU000001o2UzYAI",
"name": "Cloud Kicks"
}
}
],
329
Product Discovery Business APIsProduct Catalog Management

===== PAGE 344 =====

"additionalFields": {
"Product2": {
"fields": [
"CanRamp",
"DecompositionScope",
"ProductCode"
]
}
}
}
If a parent category ID is specified in the request body, then the API returns all products associated to all child categories.
This example shows a sample request to retrieve a product list with promotions.
{
"correlationId": "eeaa1db2-f371-4227-a886-c77e2f66ce1d",
"limit": 60,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc"
],
"catalogId": "0ZSDU0000002Og74AE",
"categoryId": "0ZGDU0000002P0H4AU",
"priceBookId": "01sDU000000JVsVYAW",
"productClassificationId": "11BDU0000002TCC2A2",
"currencyCode": "USD",
"userContext": {
"accountId": "001DU000001o2UzYAI"
},
"includeCatalogDetails": true,
"enableQualification": true,
"enablePricing": true,
"qualificationProcedure": "ProductQualification",
"pricingProcedure": "pricingProcedure",
"contextDefinition": "BrowseContextDefinitionExt",
"contextMapping": "ProductDiscoveryMapping",
"filter": {
"criteria": [
{
"property": "name",
"operator": "eq",
"value": "Laptop Pro Bundle"
}
]
},
"relatedObjectFilters": [
{
"objectName": "ProductSpecificationRecType",
"criteria": [
{
"property": "IsCommercial",
"operator": "eq",
"value": true
}
330
Product Discovery Business APIsProduct Catalog Management

===== PAGE 345 =====

]
}
],
"additionalContextData": [
{
"nodeName": "Account",
"nodeData": {
"id": "001DU000001o2UzYAI",
"name": "Cloud Kicks"
}
}
],
"additionalFields": {
"Product2": {
"fields": [
"CanRamp",
"DecompositionScope",
"ProductCode"
]
}
},
"executeConfigurationRules": false,
"transactionContextId": "a1b2c3d4e5f6",
"transactionId": "trans789",
"usePromotions": true
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data Input[]additional
ContextData
maximum number of supported nodes is
10.
61.0OptionalAdditional standard or custom fields of the
Product2 object to include in the response.
Map<String,
Additional Fields
Input>
additional
Fields
If the requested fields are invalid or access
to fields isn’t available, then the API throws
an error.
60.0OptionalID of the catalog. If the catalog ID is
specified, then the API returns the list of
StringcatalogId
offers from the catalog with the pricing
details related to the catalog.
60.0OptionalID of the category. If the category ID isn’t
specified, then the API returns the list of
offers from the catalog.
StringcategoryId
331
Product Discovery Business APIsProduct Catalog Management

===== PAGE 346 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAPI name of the custom context definition
that’s sent for context creation. If this
Stringcontext
Definition
property isn’t specified, then the default
context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether the
mapping belongs to the specified context
definition to process the details for
hydration.
60.0OptionalUnique identifier of the request.StringcorrelationId
60.0OptionalCurrency code that’s considered for pricing
and filtering request. If multiple currencies
StringcurrencyCode
are enabled for the org, then the
currencyCode  property is required.
60.0OptionalUnique ID to represent the position of each
product in the dataset.
Stringcursor
60.0OptionalIndicates whether to enable pricing for the
products (true) or not (false). The
default value is true.
The Pricing Procedure toggle from the
Product Discovery Settings page from
BooleanenablePricing
Setup overrides this property. For example,
if the Pricing Procedure toggle is
disabled, then setting the
enablePricing  property to true
has no effect and the prices  property
in the API response is returned empty.
60.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
The Qualification Procedure toggle from
the Product Discovery Settings page from
Booleanenable
Qualification
Setup overrides this property. For example,
if the Qualification Procedure toggle is
disabled, then setting the
enableQualification property to
true  has no effect and the
qualificationContext  property
in the API response isn’t returned.
60.0OptionalFilters records based on supported criteria.Filter Inputfilter
332
Product Discovery Business APIsProduct Catalog Management

===== PAGE 347 =====

Available
Version
Required or
Optional
DescriptionTypeName
The supported property is name.
The supported operators are:
• eq
• in
• contains—This value isn't
applicable if the Use Indexed Data
For Product Listing and Search
toggle from the Product Discovery
Settings page from Setup is enabled.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and  operator.
61.0OptionalIndicates whether to include catalog
details in the response (true) or not
(false).
Booleaninclude
Catalog
Details
60.0OptionalNumber of items to include in the
response. The default value is 10.
Integerlimit
60.0OptionalReserved for internal use.Integeroffset
60.0OptionalSort order of the results, which is either
ascending (asc) or descending order
String[]orderBy
(desc). The default sort order is ascending
order. The default value is asc.
If the Use Indexed Data For Product
Listing and Search toggle from the
Product Discovery Settings page from
Setup is enabled, then you can sort
products by using name only.
60.0RequiredID of the price book to get the prices from.
If this property isn’t specified, then prices
from the standard price book are fetched.
StringpriceBookId
60.0OptionalAPI name of the custom pricing procedure
that’s used for the pricing process. If this
Stringpricing
Procedure
property isn’t specified, then the default
pricing procedure is executed.
60.0OptionalID of the product classification.Stringproduct
Classification
Id
333
Product Discovery Business APIsProduct Catalog Management

===== PAGE 348 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
60.0OptionalFilter records based on supported criteria
for related objects.
Related Object Filter
Input[]
relatedObject
Filters
The supported object is
ProductSpecificationRecType.
The supported property is
IsCommerical.
The supported operator is eq.
The supported values are true  and
false.
66.0OptionalIndicates whether to fetch applicable
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for each product in
the list (true) or not (false). If
Promotion feature is enabled in the org
and this property isn't specified, then the
default value is true. If the Promotion
feature isn't enabled, the default value is
false.
60.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
Products Search Input
Input representation of the request to search products.
JSON example
This example shows a sample request to search products by using a query.
{
"query": {
"textQuery": {
"searchPhrase": "firstproduct"
}
},
"catalogId": "0ZSxx0000000001GAA",
"categoryId": "0ZGT100000000qlOAA",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
334
Product Discovery Business APIsProduct Catalog Management

===== PAGE 349 =====

"orderBy": [
"name:asc",
"id:desc"
],
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"additionalFields": {
"Product2": {
"fields": [
"CustomField1__c",
"CustomField2__c",
"StandardField1"
]
}
}
}
This example shows a sample request to search products by using the searchTerm property.
{
"searchTerm": "Laptop",
"catalogId": "0ZSDU0000002Og64AE",
"categoryId": "0ZGDU0000002P0A4AU",
"correlationId": "d9d8f898-19f5-464a-ba2b-6a070783f6c4",
"limit": 10,
"cursor": "MTAwMDAwMDAwNw==",
"orderBy": [
"name:asc",
"id:desc"
],
"userContext": {
"accountId": "001DU000001o2V0YAI"
}
}
If a parent category ID is specified in the request body, then the API returns all products associated to all child categories.
This example shows a sample request to search products with eligible promotions. To fetch eligible promotions, specify a value for
the query  or searchTerm  property, and set the usePromotions  property to true.
{
"query": {
"textQuery": {
"searchPhrase": "laptop"
}
},
"catalogId": "0ZSxx0000000001GAA",
"categoryId": "0ZGT100000000qlOAA",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc",
"id:desc"
335
Product Discovery Business APIsProduct Catalog Management

===== PAGE 350 =====

],
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI"
},
"additionalFields": {
"Product2": {
"fields": [
"CustomField1__c",
"CustomField2__c",
"StandardField1"
]
}
},
"usePromotions": true
}
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data Input[]additional
ContextData
maximum number of supported nodes is
10.
61.0OptionalAdditional standard or custom fields of the
Product2 object to include in the response.
Map<String,
Additional Fields
Input>
additional
Fields
If the requested fields are invalid or access
to fields isn’t available, then the API throws
an error.
60.0OptionalID of the catalog. If the catalog ID is
specified, then the API returns the list of
StringcatalogId
offers from the catalog with the pricing
details related to the catalog.
60.0OptionalID of the category. If the category ID isn’t
specified, then the API returns the
matching query offers from the catalog.
StringcategoryId
60.0OptionalAPI name of the custom context definition
that’s sent for context creation. If this
Stringcontext
Definition
property isn’t specified, then the default
context definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether the
mapping belongs to the specified context
definition to process the details for
hydration.
336
Product Discovery Business APIsProduct Catalog Management

===== PAGE 351 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalUnique identifier of the request.StringcorrelationId
60.0OptionalCurrency code that’s considered for pricing
and filtering request.
StringcurrencyCode
60.0OptionalUnique ID to represent the position of each
product in the dataset.
Stringcursor
60.0OptionalIndicates whether to enable pricing for the
products (true) or not (false). The
default value is true.
The Pricing Procedure toggle from the
Product Discovery Settings page from
BooleanenablePricing
Setup overrides this property. For example,
if the Pricing Procedure toggle is
disabled, then setting the
enablePricing  property to true
has no effect and the prices  property
in the API response is returned empty.
60.0OptionalIndicates whether to enable qualification
rules for the products (true) or not
(false). The default value is true.
The Qualification Procedure toggle from
the Product Discovery Settings page from
Booleanenable
Qualification
Setup overrides this property. For example,
if the Qualification Procedure toggle is
disabled, then setting the
enableQualification property to
true  has no effect and the
qualificationContext  property
in the API response isn’t returned.
60.0OptionalFilters records based on supported criteria.Filter Inputfilter
The supported property is name.
The supported operators are:
• eq
• in
• contains
• gt—Specifies a greater than criteria.
Available from API version 63.0 and
later for Number, Date, and Datetime
data types only.
• lt—Specifies a less than criteria.
Available from API version 63.0 and
337
Product Discovery Business APIsProduct Catalog Management

===== PAGE 352 =====

Available
Version
Required or
Optional
DescriptionTypeName
later for Number, Date, and Datetime
data types only.
• gte—Specifies a greater than or
equal to criteria. Available from API
version 63.0 and later for Number,
Date, and Datetime data types only.
• lte—Specifies a less than or equal
to criteria. Available from API version
63.0 and later for Number, Date, and
Datetime data types only.
If multiple criteria are specified, then the
resultant criteria are combined by using
the and  operator.
61.0OptionalIndicates whether to include catalog
details in the response (true) or not
(false).
Booleaninclude
CatalogDetails
60.0OptionalNumber of items to include in the
response. The default value is 10.
Integerlimit
60.0OptionalReserved for internal use.Integeroffset
60.0OptionalSort order of the results, which is either
ascending or descending order. The
String[]orderBy
default sort order is ascending order. The
default value is asc.
60.0OptionalID of the price book to get the prices from.
If this property isn’t specified, then prices
from the standard price book are fetched.
StringpriceBookId
60.0OptionalAPI name of the custom pricing procedure
that’s used for the pricing process. If this
StringpricingProcedure
property isn’t specified, then the default
pricing procedure is executed.
60.0OptionalID of the product classification.Stringproduct
ClassificationId
60.0OptionalAPI name of the custom qualification
procedure that’s used for the product
Stringqualification
Procedure
qualification process. If this property isn’t
specified, then the default qualification
procedure is executed.
60.0RequiredQuery to search the products.Map<String,
Object>
query
338
Product Discovery Business APIsProduct Catalog Management

===== PAGE 353 =====

Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalFilter records based on supported criteria
for related objects.
Related Object Filter
Input[]
related
ObjectFilter
The supported object is
ProductSpecificationRecType.
The supported property is
IsCommerical.
The supported operator is eq.
The supported values are true  and
false.
62.0OptionalString used to get products with the
product name containing the search term.
StringsearchTerm
See Search Considerations When Using
Indexed Data.
66.0OptionalIndicates whether to retrieve eligible
promotions from Global Promotion
BooleanusePromotions
Management (GPM) for each product in
the search results (true) or not (false).
If Promotion feature is enabled in the org
and this property isn't specified, then the
default value is true. If the Promotion
feature isn't enabled, the default value is
false.
60.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
QOC Qualification
Input representation of the qualification request.
JSON example
{
"productIds": [
"01txx0000006i7PAAQ",
"01txx0000006i7QAAQ",
"01txx0000006i7IAAQ"
],
"userContext": {
"accountId": "001xx000003GZHgAAO"
}
}
339
Product Discovery Business APIsProduct Catalog Management

===== PAGE 354 =====

Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0OptionalAdditional nodes that are added to the
custom or default context definition. The
Context Data Input[]additional
ContextData
maximum number of supported nodes is
10.
60.0OptionalID of the catalog.StringcatalogId
60.0OptionalID of the category.StringcategoryId
60.0OptionalAPI name of the custom context definition
that’s sent for context creation. If this
Stringcontext
Definition
property isn’t specified, the default context
definition is used.
60.0OptionalDefault context mapping of the context
definition. If a context mapping is
Stringcontext
Mapping
specified, then the API checks whether the
mapping belongs to the specified context
definition to process the details for
hydration.
60.0OptionalUnique identifier of the request.StringcorrelationId
60.0RequiredList of product IDs for qualification check.String[]productIds
60.0OptionalAPI name of the custom qualification
procedure that’s sent for processing. If this
Stringqualification
Procedure
property isn’t specified, the default
qualification procedure is executed.
60.0OptionalUser context details. For example, account
ID or contact ID.
User Context InputuserContext
Related Object Filter Input
Input representation of the request to filter records of a related object.
JSON example
"relatedObjectFilters":
[
{
"objectName": "ProductSpecificationRecType",
"criteria":
[{
"property": "IsCommercial",
"operator": "eq",
"value": true
}]
340
Product Discovery Business APIsProduct Catalog Management

===== PAGE 355 =====

}
]
Properties
Available
Version
Required or
Optional
DescriptionTypeName
60.0Required if the
relatedObjectFilters
property is specified.
Criteria to filter the related objects.Filter Criteria Input[]criteria
60.0Required if the
relatedObjectFilters
property is specified.
Name of the object that’s related to the
main object.
StringobjectName
User Context Input
Input representation of the details with the user context.
JSON example
"userContext": {
"accountId": "001xx0000000001AAA",
"contactId": "003xx00000000D7AAI",
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708"
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
Learn more about the available Product Discovery API response bodies.
API Status
Output representation of the API status.
Bulk Product Details
Output representation of the response that contains the details of multiple products.
CPQ Base Details
Output representation of the catalog, category, or product details based on the request.
341
Product Discovery Business APIsProduct Catalog Management

===== PAGE 356 =====

CPQ Base List
Output representation of the list of catalogs, categories, or products based on the request.
CPQ Message
Output representation of the API messages.
Facet Value
Output representation of the facet values found in the search result.
Guided Selection
Output representation of the details of a guided selection.
Guided Selection Search Term
Output representation of the search term details for a guided selection.
Search Products Facet
Output representation of the details of the faceted search.
User Context
Output representation of the user context details.
API Status
Output representation of the API status.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Status messages of the API execution.CPQ Message[]messages
60.0Small, 60.0Status code of the API execution.StringstatusCode
60.0Small, 60.0Display label for the API status.StringstatusMessage
Bulk Product Details
Output representation of the response that contains the details of multiple products.
JSON example
{
"apiStatus": {
"messages": [],
"statusCode": "FetchedDetailsSuccessfully"
},
"contextId": "c68c7c7e85f3ea5b0e7bcfefc0f2dba9bbd24bfe2f4240ca589af50e473e2242",
"correlationId": "de9a674c-1807-438c-ac78-2c96f4655325",
"result": [
{
"additionalFields": [],
"attributeCategories": [],
"attributes": [],
"catalogs": [],
"childProducts": [],
"id": "01txx0000006ivJAAQ",
"isActive": true,
342
Product Discovery Business APIsProduct Catalog Management

===== PAGE 357 =====

"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "iPhone12",
"nodeType": "simpleProduct",
"prices": [
{
"currencyIsoCode": "USD",
"isDefault": false,
"isSelected": true,
"price": 100,
"priceBookEntryId": "01uxx0000008zUkAAI",
"priceBookId": "01sxx0000005qxxAAA",
"pricingModel": {
"id": "0jPxx000000009hEAA",
"name": "OneTime",
"pricingModelType": "OneTime"
}
},
{
"currencyIsoCode": "USD",
"isDefault": true,
"isSelected": false,
"price": 15,
"priceBookEntryId": "01uxx0000008zUmAAI",
"priceBookId": "01sxx0000005qxxAAA",
"pricingModel": {
"frequency": "Months",
"id": "0jPxx000000009iEAA",
"name": "Monthly",
"occurrence": 1,
"pricingModelType": "TermDefined"
}
}
],
"productClassification": {},
"productCode": "iPhone12",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iOxx00000000EfEAI",
"productId": "01txx0000006ivJAAQ",
"productSellingModel": {
"id": "0jPxx000000009iEAA",
"name": "Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000009iEAA"
},
{
"id": "0iOxx00000000EgEAI",
"productId": "01txx0000006ivJAAQ",
343
Product Discovery Business APIsProduct Catalog Management

===== PAGE 358 =====

"productSellingModel": {
"id": "0jPxx000000009hEAA",
"name": "OneTime",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000009hEAA"
}
],
"productSpecificationType": {
"name": "ProdSpecRecType1",
"productSpecificationRecordType": {}
},
"qualificationContext": {
"isQualified": true
}
},
{
"additionalFields": [],
"attributeCategories": [],
"attributes": [],
"catalogs": [],
"childProducts": [],
"id": "01txx0000006ivLAAQ",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "iPhone13",
"nodeType": "simpleProduct",
"prices": [
{
"currencyIsoCode": "USD",
"isDefault": true,
"isSelected": false,
"price": 1520,
"priceBookEntryId": "01uxx0000008zUpAAI",
"priceBookId": "01sxx0000005qxxAAA",
"pricingModel": {
"id": "0jPxx000000009hEAA",
"name": "OneTime",
"pricingModelType": "OneTime"
}
},
{
"currencyIsoCode": "USD",
"isDefault": false,
"isSelected": false,
"price": 152,
"priceBookEntryId": "01uxx0000008zUqAAI",
"priceBookId": "01sxx0000005qxxAAA",
"pricingModel": {
"frequency": "Months",
"id": "0jPxx000000009iEAA",
"name": "Monthly",
344
Product Discovery Business APIsProduct Catalog Management

===== PAGE 359 =====

"occurrence": 1,
"pricingModelType": "TermDefined"
}
}
],
"productClassification": {},
"productCode": "iPhone13",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iOxx00000000EbEAI",
"productId": "01txx0000006ivLAAQ",
"productSellingModel": {
"id": "0jPxx000000009iEAA",
"name": "Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx000000009iEAA"
},
{
"id": "0iOxx00000000EeEAI",
"productId": "01txx0000006ivLAAQ",
"productSellingModel": {
"id": "0jPxx000000009hEAA",
"name": "OneTime",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPxx000000009hEAA"
}
],
"productSpecificationType": {
"name": "ProdSpecRecType1",
"productSpecificationRecordType": {}
},
"qualificationContext": {
"isQualified": true
}
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
61.0Small, 61.0Status of the API request.API Status[]apiStatus
61.0Small, 61.0ID of the context.StringcontextId
61.0Small, 61.0Unique identifier of the request.StringcorrelationId
61.0Small, 61.0Result that contains the details of products.Any response bodyresult
345
Product Discovery Business APIsProduct Catalog Management

===== PAGE 360 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
61.0Small, 61.0User context details. For example, account
ID or contact ID.
User Context[]userContext
CPQ Base Details
Output representation of the catalog, category, or product details based on the request.
JSON example
This example shows the sample catalog details.
{
"apiStatus": {
"messages": [
],
"statusCode": "FetchedDetailsSuccessfully"
},
"correlationId": "32595ed6-1922-41f7-9c2c-373c677a7d62",
"result": {
"catalogCode": "Mobiles",
"catalogType": "Sales",
"description": "Catalog for mobile phones",
"effectiveEndDate": "2028-04-01T19:00Z",
"effectiveStartDate": "2024-04-01T19:00Z",
"id": "0ZSxx0000000001GAA",
"name": "Mobiles",
"numberOfCategories": 3
}
}
This example shows the sample category details.
{
"apiStatus": {
"messages": [
],
"statusCode": "FetchedDetailsSuccessfully"
},
"correlationId": "f9fb90de-36aa-44a1-9961-a9ef5fc0cad8",
"result": {
"catalogId": "0ZSxx0000000001GAA",
"childCategories": [
],
"description": "Category for Samsung phones",
"id": "0ZGxx000000004rGAA",
"name": "Samsung",
"isNavigational": true,
"sortOrder": 2
346
Product Discovery Business APIsProduct Catalog Management

===== PAGE 361 =====

}
}
This example shows the sample product details.
{
"apiStatus": {
"messages": [
],
"statusCode": "FetchedDetailsSuccessfully"
},
"correlationId": "822a8941-7412-4883-bb80-e488f908471e",
"result": {
"additionalFields": {
"CustomField1__c": "TextValue",
"CustomField2__c": "10",
"StandardField1": "false"
},
"attributeCategories": [
],
"attributes": [
],
"catalogs": [
],
"childProducts": [
],
"id": "01txx0000006i2WAAQ",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "iPhone15",
"nodeType": "simpleProduct",
"prices": [
],
"productClassification": {
},
"productCode": "iPhone15",
"productComponentGroups": [
],
"productSellingModelOptions": [
{
"id": "0iOxx0000000003EAA",
"productId": "01txx0000006i2WAAQ",
"productSellingModel": {
"id": "0jPxx0000000001EAA",
"name": "OneTime",
"sellingModelType": "OneTime",
347
Product Discovery Business APIsProduct Catalog Management

===== PAGE 362 =====

"status": "Active"
},
"productSellingModelId": "0jPxx0000000001EAA"
},
{
"id": "0iOxx0000000004EAA",
"productId": "01txx0000006i2WAAQ",
"productSellingModel": {
"id": "0jPxx0000000002EAA",
"name": "Monthly",
"pricingTerm": 1,
"pricingTermUnit": "Months",
"sellingModelType": "TermDefined",
"status": "Active"
},
"productSellingModelId": "0jPxx0000000002EAA"
}
],
"productSpecificationType": {
"name": "ProdSpecRecType1",
"productSpecificationRecordType": {
}
}
}
}
This example shows a sample of category details with eligible promotions.
{
"apiStatus": {
"messages": [],
"statusCode": "FetchedDetailsSuccessfully"
},
"correlationId": "f9fb90de-36aa-44a1-9961-a9ef5fc0cad8",
"result": {
"catalogId": "0ZSxx0000000001GAA",
"childCategories": [],
"description": "Category for Samsung phones",
"id": "0ZGxx000000004rGAA",
"name": "Samsung",
"isNavigational": true,
"sortOrder": 2,
"eligiblePromotions": [
{
"id": "0ZPxx0000000001AAA",
"name": "Summer Sale 2025",
"displayName": "Summer Electronics Sale",
"description": "Get 20% off on all Samsung devices",
"priority": 100,
"startDateTime": "2025-06-01T00:00:00Z",
"endDateTime": "2025-08-31T23:59:59Z",
"isAutomatic": true,
"isCategoryPromo": true,
"isProductPromo": false,
348
Product Discovery Business APIsProduct Catalog Management

===== PAGE 363 =====

"couponCode": null,
"termsAndConditions": "Valid on all Samsung products. Cannot be combined with
other offers."
},
{
"id": "0ZPxx0000000002AAA",
"name": "Electronics Bundle Deal",
"displayName": "Bundle & Save",
"description": "Save 15% when you buy 2 or more items",
"priority": 90,
"startDateTime": "2025-05-15T00:00:00Z",
"endDateTime": "2025-12-31T23:59:59Z",
"isAutomatic": false,
"isCategoryPromo": false,
"isProductPromo": true,
"couponCode": "BUNDLE15",
"termsAndConditions": "Minimum 2 items required."
}
]
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Status of the API request.API StatusapiStatus
60.0Small, 60.0ID of the context.StringcontextId
60.0Small, 60.0Unique identifier of the request.StringcorrelationId
60.0Small, 60.0Result that contains the details of catalogs,
categories, or products as per the requested
resource.
Any response bodyresult
60.0Small, 60.0User context details. For example, account
ID or contact ID.
User ContextuserContext
CPQ Base List
Output representation of the list of catalogs, categories, or products based on the request.
JSON example
This example shows a sample catalog list.
{
"apiStatus": {
"messages": [
],
"statusCode": "FetchedDetailsSuccessfully"
},
"correlationId": "9f417514-9587-4063-9e48-18a2cf2477c0",
"limit": 10,
349
Product Discovery Business APIsProduct Catalog Management

===== PAGE 364 =====

"offSet": 0,
"query": {
},
"result": [
{
"catalogCode": "Mobiles",
"catalogType": "Sales",
"description": "Catalog for mobile phones",
"effectiveEndDate": "2028-04-01T19:00Z",
"effectiveStartDate": "2024-04-01T19:00Z",
"id": "0ZSxx0000000001GAA",
"name": "Mobiles",
"numberOfCategories": 3
}
],
"total": 1
}
This example shows a sample category list.
{
"apiStatus": {
"messages": [
],
"statusCode": "FetchedDetailsSuccessfully"
},
"correlationId": "3f2a8f45-e7d2-42ec-bc4c-b981d750e912",
"query": {
},
"result": [
{
"catalogId": "0ZSxx0000000001GAA",
"childCategories": [
],
"description": "Category for Apple phones and iPads",
"id": "0ZGxx0000000001GAA",
"name": "Apple",
"sortOrder": 1,
"isNavigational": true
},
{
"catalogId": "0ZSxx0000000001GAA",
"childCategories": [
],
"description": "Category for Samsung phones",
"id": "0ZGxx000000004rGAA",
"name": "Samsung",
"sortOrder": 2,
"isNavigational": true
},
350
Product Discovery Business APIsProduct Catalog Management

===== PAGE 365 =====

{
"catalogId": "0ZSxx0000000001GAA",
"childCategories": [
],
"description": "Category for Android phones",
"id": "0ZGxx000000006TGAQ",
"name": "Android",
"isNavigational": true
}
],
"total": 3
}
This example shows a sample product list.
{
"apiStatus": {
"messages": [],
"statusCode": "FetchedDetailsSuccessfully"
},
"contextId": "f36f8e73f1fc338cc4e93c61613cba07a6a0129941d97e5dd6e52a2885776ce4",
"correlationId": "eeaa1db2-f371-4227-a886-c77e2f66ce1d",
"cursor": "MTAwMDAwMDAwNg==",
"query": {},
"result": [
{
"additionalFields": {
"DecompositionScope": "OrderLineItem",
"ProductCode": "LPB001",
"CanRamp": false
},
"attributeCategories": [],
"catalogs": [
{
"customFields": {},
"id": "0ZSDU0000002Og74AE",
"name": "Service Catalog",
"numberOfCategories": 5
}
],
"categories": [
{
"catalogId": "0ZSDU0000002Og74AE",
"childCategories": [],
"customFields": {},
"hasSubCategories": false,
"id": "0ZGDU0000002P0H4AU",
"name": "Cloud Services",
"qualificationContext": {
"isQualified": true
}
}
],
"childProducts": [],
351
Product Discovery Business APIsProduct Catalog Management

===== PAGE 366 =====

"configureDuringSale": "Allowed",
"description": "The laptop pro bundle includes a Laptop, mouse, warranty for 2
years, premium support and printer bundle",
"displayUrl":
"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSCrGjPR1fvJqg4yP3RMyqjI0H9eL6tk1fvzw&amp;usqp=CAU",
"id": "01tDU000000ExkZYAS",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Laptop Pro Bundle",
"nodeType": "bundleProduct",
"prices": [],
"productClassification": {},
"productCode": "LPB001",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iODU0000002TBN2A2",
"productId": "01tDU000000ExkZYAS",
"productSellingModel": {
"id": "0jPDU0000002OTv2AM",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPDU0000002OTv2AM"
}
],
"productSpecificationType": {
"name": "Commercial",
"productSpecificationRecordType": {}
},
"productType": "Bundle",
"qualificationContext": {
"isQualified": true
}
}
]
}
This example shows a sample of the list of products retrieved based on the Laptop  search term.
{
"apiStatus": {
"messages": [],
"statusCode": "FetchedDetailsSuccessfully"
},
"correlationId": "d9d8f898-19f5-464a-ba2b-6a070783f6c4",
"cursor": "MTAwMDAwMDAwMw==",
"facets": [
{
"attributeType": "ProductStandard",
"displayName": "Product Type",
"displayRank": 2,
352
Product Discovery Business APIsProduct Catalog Management

===== PAGE 367 =====

"nameOrId": "Type",
"values": [
{
"displayName": "Bundle",
"nameOrId": "Bundle"
}
]
},
{
"attributeType": "ProductDynamicAttribute",
"displayName": "Display",
"displayRank": 3,
"nameOrId": "0tjDU0000003K5BYAU",
"values": [
{
"displayName": "1080p Built-in Display",
"nameOrId": "1080p Built-in Display"
},
{
"displayName": "2k Built-in Display",
"nameOrId": "2k Built-in Display"
},
{
"displayName": "4k Built-in Display",
"nameOrId": "4k Built-in Display"
}
]
}
],
"limit": 10,
"query": {},
"result": [
{
"additionalFields": {},
"attributeCategories": [],
"catalogs": [],
"categories": [
{
"catalogId": "0ZSDU0000002Og64AE",
"childCategories": [],
"customFields": {},
"hasSubCategories": false,
"id": "0ZGDU0000002P0A4AU",
"name": "Laptops",
"qualificationContext": {
"isQualified": true
}
}
],
"configureDuringSale": "Allowed",
"description": "Battery- or AC-powered personal computer (PC) smaller than a
briefcase",
"displayUrl":
"https://media.istockphoto.com/id/1023428598/photo/3d-illustration-laptop-isolated-on-white-background-laptop-with-empty-space-screen-laptop-at.jpg?s=612x612&amp;w=0&amp;k=20&amp;c=ssK6er5v1fGpSghGiqySwoD8tn5blC7xgefQJI2xU38=",
353
Product Discovery Business APIsProduct Catalog Management

===== PAGE 368 =====

"id": "01tDU000000ExkWYAS",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Laptop",
"nodeType": "simpleProduct",
"prices": [],
"productClassification": {
"id": "11BDU0000002TCD2A2"
},
"productCode": "LP001",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iODU0000002TBF2A2",
"productId": "01tDU000000ExkWYAS",
"productSellingModel": {
"id": "0jPDU0000002OTv2AM",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPDU0000002OTv2AM"
}
],
"productSpecificationType": {
"name": "Commercial",
"productSpecificationRecordType": {}
},
"qualificationContext": {
"isQualified": true
}
},
{
"additionalFields": {},
"attributeCategories": [],
"catalogs": [],
"categories": [
{
"catalogId": "0ZSDU0000002Og64AE",
"childCategories": [],
"customFields": {},
"hasSubCategories": false,
"id": "0ZGDU0000002P0A4AU",
"name": "Laptops",
"qualificationContext": {
"isQualified": true
}
}
],
"configureDuringSale": "Allowed",
"description": "The laptop basic bundle includes a Laptop, mouse, and warranty
for 1 year.",
354
Product Discovery Business APIsProduct Catalog Management

===== PAGE 369 =====

"displayUrl":
"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTbf49JG4zZogCmZMJuXU38qOkR9X36MN4bSw&amp;usqp=CAU",
"id": "01tDU000000ExkXYAS",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Laptop Basic Bundle",
"nodeType": "bundleProduct",
"prices": [],
"productClassification": {},
"productCode": "LB001",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iODU0000002TBD2A2",
"productId": "01tDU000000ExkXYAS",
"productSellingModel": {
"id": "0jPDU0000002OTv2AM",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPDU0000002OTv2AM"
}
],
"productSpecificationType": {
"name": "Commercial",
"productSpecificationRecordType": {}
},
"productType": "Bundle",
"qualificationContext": {
"isQualified": true
}
},
{
"additionalFields": {},
"attributeCategories": [],
"catalogs": [],
"categories": [
{
"catalogId": "0ZSDU0000002Og64AE",
"childCategories": [],
"customFields": {},
"hasSubCategories": false,
"id": "0ZGDU0000002P0A4AU",
"name": "Laptops",
"qualificationContext": {
"isQualified": true
}
}
],
"configureDuringSale": "Allowed",
"description": "The laptop pro bundle includes a Laptop, mouse, warranty for 2
355
Product Discovery Business APIsProduct Catalog Management

===== PAGE 370 =====

years, premium support and printer bundle",
"displayUrl":
"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSCrGjPR1fvJqg4yP3RMyqjI0H9eL6tk1fvzw&amp;usqp=CAU",
"id": "01tDU000000ExkZYAS",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Laptop Pro Bundle",
"nodeType": "bundleProduct",
"prices": [],
"productClassification": {},
"productCode": "LPB001",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iODU0000002TBN2A2",
"productId": "01tDU000000ExkZYAS",
"productSellingModel": {
"id": "0jPDU0000002OTv2AM",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPDU0000002OTv2AM"
}
],
"productSpecificationType": {
"name": "Commercial",
"productSpecificationRecordType": {}
},
"productType": "Bundle",
"qualificationContext": {
"isQualified": true
}
},
{
"additionalFields": {},
"attributeCategories": [],
"catalogs": [],
"categories": [
{
"catalogId": "0ZSDU0000002Og64AE",
"childCategories": [],
"customFields": {},
"hasSubCategories": false,
"id": "0ZGDU0000002P0A4AU",
"name": "Laptops",
"qualificationContext": {
"isQualified": true
}
}
],
"configureDuringSale": "Allowed",
356
Product Discovery Business APIsProduct Catalog Management

===== PAGE 371 =====

"description": "Laptop, Laptop Bag, Laptop stand, Mouse, Keyboard, USB-C
Hub,External Hard Drive, Noise Cancelling Headphones, office 365",
"displayUrl": "https://m.media-amazon.com/images/I/613Fno-NLYL._AC_SL1000_.jpg",
"id": "01tDU000000ExlAYAS",
"isActive": true,
"isAssetizable": true,
"isSoldOnlyWithOtherProds": false,
"name": "Laptop Productivity Bundle",
"nodeType": "bundleProduct",
"prices": [],
"productClassification": {},
"productCode": "LPB001",
"productComponentGroups": [],
"productSellingModelOptions": [
{
"id": "0iODU0000002TBq2AM",
"productId": "01tDU000000ExlAYAS",
"productSellingModel": {
"id": "0jPDU0000002OTv2AM",
"name": "One Time",
"sellingModelType": "OneTime",
"status": "Active"
},
"productSellingModelId": "0jPDU0000002OTv2AM"
}
],
"productSpecificationType": {
"name": "Commercial",
"productSpecificationRecordType": {}
},
"productType": "Bundle",
"qualificationContext": {
"isQualified": true
}
}
],
"total": 4
}
This example shows a sample of the results of a qualification procedure that’s executed on a list of product IDs.
{
"apiStatus": {
"messages": [
],
"statusCode": "FetchedDetailsSuccessfully"
},
"contextId": "e055bb18-d4e8-41c3-881e-0132b9561708",
"correlationId": "c280c1b0-fd3f-4eac-9b08-075bdf1cbefc",
"query": {
},
"result": [
{
357
Product Discovery Business APIsProduct Catalog Management

===== PAGE 372 =====

"productId": "01txx0000006i7PAAQ",
"qualificationContext": {
"isQualified": true
}
},
{
"productId": "01txx0000006i7QAAQ",
"qualificationContext": {
"isQualified": true
}
},
{
"productId": "01txx0000006i7IAAQ",
"qualificationContext": {
"isQualified": true
}
}
]
}
This example shows a list of products with eligible promotions.
{
"apiStatus": {
"messages": [],
"statusCode": "FetchedDetailsSuccessfully"
},
"correlationId": "f9fb90de-36aa-44a1-9961-a9ef5fc0cad8",
"result": {
"catalogId": "0ZSxx0000000001GAA",
"childCategories": [],
"description": "Category for Samsung phones",
"id": "0ZGxx000000004rGAA",
"name": "Samsung",
"isNavigational": true,
"sortOrder": 2,
"eligiblePromotions": [
{
"id": "0ZPxx0000000001AAA",
"name": "Summer_Sale_2025",
"displayName": "Summer Electronics Sale",
"description": "Get 20% off on all Samsung devices",
"priority": 100,
"startDateTime": "2025-06-01T00:00:00Z",
"endDateTime": "2025-08-31T23:59:59Z",
"isAutomatic": true,
"isCategoryPromo": true,
"isProductPromo": false,
"couponCode": null,
"termsAndConditions": "Valid on all Samsung products. Cannot be combined with
other offers."
},
{
"id": "0ZPxx0000000002AAA",
"name": "Electronics_Bundle",
358
Product Discovery Business APIsProduct Catalog Management

===== PAGE 373 =====

"displayName": "Bundle & Save",
"description": "Save 15% when you buy 2 or more items",
"priority": 90,
"startDateTime": "2025-05-15T00:00:00Z",
"endDateTime": "2025-12-31T23:59:59Z",
"isAutomatic": false,
"isCategoryPromo": false,
"isProductPromo": true,
"couponCode": "BUNDLE15",
"termsAndConditions": "Minimum 2 items required."
}
]
}
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Status of the API request.API StatusapiStatus
60.0Small, 60.0ID of the context.StringcontextId
60.0Small, 60.0Unique ID of the request.StringcorrelationId
60.0Small, 60.0Unique ID to represent the position of each
product in the dataset.
Stringcursor
63.0Small, 63.0Details of the faceted search.Search Products
Facet
facets
60.0Small, 60.0Number of items fetched in the response.Integerlimit
60.0Small, 60.0Offset size from which the item count is
fetched.
IntegeroffSet
60.0Small, 60.0Query that was used for the search request.Map<String,
Object>
query
60.0Small, 60.0Result that contains the list of catalogs,
categories, or products as per the requested
resource.
Any response bodyresult
60.0Small, 60.0Number of fetched records.Integertotal
60.0Small, 60.0User context details. For example, account
ID or contact ID.
User ContextuserContext
CPQ Message
Output representation of the API messages.
359
Product Discovery Business APIsProduct Catalog Management

===== PAGE 374 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0Code specifying the type of message. Valid
value is CartValidationError.
Stringcode
60.0Small, 60.0Required details other than the message
text.
Stringdetail
60.0Small, 60.0Text of the API message.Stringmessage
60.0Small, 60.0Severity of the API message. Valid values
are:
Stringseverity
• Error
• Info
• Warning
Facet Value
Output representation of the facet values found in the search result.
JSON example
"values": [
{
"displayName": "1080p Built-in Display",
"nameOrId": "1080p Built-in Display"
},
{
"displayName": "2k Built-in Display",
"nameOrId": "2k Built-in Display"
},
{
"displayName": "4k Built-in Display",
"nameOrId": "4k Built-in Display"
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Display name of the facet value.StringdisplayName
63.0Small, 63.0ID or the internal name of the facet value.StringnameOrId
Guided Selection
Output representation of the details of a guided selection.
360
Product Discovery Business APIsProduct Catalog Management

===== PAGE 375 =====

JSON example
{
"apiStatus": {
"messages": [],
"statusCode": "FETCHED_DETAILS_SUCCESSFULLY"
},
"correlationId": "corrId",
"cursor": "MTAwMDAwMDAwNg==",
"searchTerms": [
{
"term": "IPhone"
},
{
"term": "4GB"
},
{
"term": "64GB"
}
],
"result": [
{
"additionalFields": {
"CustomField1__c": "TextValue",
"CustomField2__c": "10",
"StandardField1": "false"
},
"description": "IPhone-13",
"id": "01txx0000006kYwAAI",
"name": "Sample product 1",
"prices": [
{
"price": 150,
"priceBookEntryId": "12Axx0000004DF7EAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"frequency": "Monthly",
"id": "12Bxx000000CiCDEA0",
"name": "IPhone-13",
"occurrence": 6,
"pricingModelType": "Recurring"
}
},
{
"price": 400,
"priceBookEntryId": "12Axx0000004DGjEAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"id": "12Bxx000000CiCCEA0",
"name": "IPhone-13",
"pricingModelType": "OneTime"
}
}
],
361
Product Discovery Business APIsProduct Catalog Management

===== PAGE 376 =====

"qualificationContext": {
"isQualified": true
}
}
]
}
This example shows a sample response with details of eligible promotions.
{
"apiStatus": {
"messages": [],
"statusCode": "FETCHED_DETAILS_SUCCESSFULLY"
},
"correlationId": "corrId",
"cursor": "MTAwMDAwMDAwNg==",
"searchTerms": [
{
"term": "IPhone",
"tags": [
"deviceType",
"mobile"
]
},
{
"term": "4GB",
"tags": [
"RAM"
]
},
{
"term": "64GB",
"tags": [
"Storage"
]
}
],
"result": [
{
"additionalFields": {
"CustomField1__c": "TextValue",
"CustomField2__c": "10",
"StandardField1": "false"
},
"description": "IPhone-13",
"id": "01txx0000006kYwAAI",
"name": "Sample product 1",
"prices": [
{
"price": 150,
"priceBookEntryId": "12Axx0000004DF7EAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"frequency": "Monthly",
"id": "12Bxx000000CiCDEA0",
362
Product Discovery Business APIsProduct Catalog Management

===== PAGE 377 =====

"name": "IPhone-13",
"occurrence": 6,
"pricingModelType": "Recurring"
}
},
{
"price": 400,
"priceBookEntryId": "12Axx0000004DGjEAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"id": "12Bxx000000CiCCEA0",
"name": "IPhone-13",
"pricingModelType": "OneTime"
}
}
],
"qualificationContext": {
"isQualified": true
},
"eligiblePromotions": [
{
"id": "0ZPxx0000000001AAA",
"name": "IPhone_Promotion_2025",
"displayName": "iPhone Special Offer",
"description": "Get 15% off on iPhone 13",
"priority": 100,
"startDateTime": "2025-03-01T00:00:00Z",
"endDateTime": "2025-03-31T23:59:59Z",
"isAutomatic": true,
"isCategoryPromo": false,
"isProductPromo": true,
"couponCode": null,
"termsAndConditions": "Valid on iPhone 13 models only."
},
{
"id": "0ZPxx0000000002AAA",
"name": "Memory_Upgrade_Deal",
"displayName": "Free Memory Upgrade",
"description": "Upgrade to 128GB for the price of 64GB",
"priority": 90,
"startDateTime": "2025-02-01T00:00:00Z",
"endDateTime": "2025-12-31T23:59:59Z",
"isAutomatic": false,
"isCategoryPromo": false,
"isProductPromo": true,
"couponCode": "MEMORY128",
"termsAndConditions": "Applies to select iPhone models."
}
]
}
]
}
363
Product Discovery Business APIsProduct Catalog Management

===== PAGE 378 =====

Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Status of the API request.API StatusapiStatus
62.0Small, 62.0Unique ID of the request.StringcorrelationId
62.0Small, 62.0Unique ID to represent the position of each
product in the dataset.
Stringcursor
62.0Small, 62.0Result that contains the list of products as
per the requested resource.
Any response bodyresult
62.0Small, 62.0Search terms for the guided selection.Guided Selection
Search Term[]
searchTerms
Guided Selection Search Term
Output representation of the search term details for a guided selection.
JSON example
{
"searchTerms": [
{
"term": "IPhone",
"tags": [
"deviceType",
"mobile"
]
},
{
"term": "4GB",
"tags": [
"RAM"
]
},
{
"term": "64GB",
"tags": [
"Storage"
]
}
]
}
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
62.0Small, 62.0Search term tags for the guided selection.String[]tags
62.0Small, 62.0Search term value for the guided selection.Stringterm
364
Product Discovery Business APIsProduct Catalog Management

===== PAGE 379 =====

Search Products Facet
Output representation of the details of the faceted search.
JSON example
"facets": [
{
"attributeType": "ProductStandard",
"displayName": "Product Type",
"displayRank": 2,
"nameOrId": "Type",
"values": [
{
"displayName": "Bundle",
"nameOrId": "Bundle"
}
]
},
{
"attributeType": "ProductDynamicAttribute",
"displayName": "Display",
"displayRank": 3,
"nameOrId": "0tjDU0000003K5BYAU",
"values": [
{
"displayName": "1080p Built-in Display",
"nameOrId": "1080p Built-in Display"
},
{
"displayName": "2k Built-in Display",
"nameOrId": "2k Built-in Display"
},
{
"displayName": "4k Built-in Display",
"nameOrId": "4k Built-in Display"
}
]
}
]
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
63.0Small, 63.0Search attribute type of the facet.StringattributeType
63.0Small, 63.0Display name of the facet.StringdisplayName
63.0Small, 63.0Display rank for the facet.IntegerdisplayRank
63.0Small, 63.0ID or the internal name of the facet.StringnameOrId
63.0Medium, 63.0Values of the facet found in the search
result. Sorted by display name in
alphabetical order.
Facet Value[]values
365
Product Discovery Business APIsProduct Catalog Management

===== PAGE 380 =====

User Context
Output representation of the user context details.
Available VersionFilter Group and
Version
DescriptionTypeProperty Name
60.0Small, 60.0ID of the context.StringcontextId
Product Discovery Standard Invocable Actions
Use the standard invocable actions available with Product Discovery to find and retrieve product, category, and catalog details. Additionally,
execute a qualification procedure, and search products with guided selection.
Find Products Action
Search for the products from a catalog, category, or subcategory by using the specified search term.
Execute Qualification Procedure Action
Execute a qualification procedure, which returns the qualification status for the specified products.
Get Catalogs Action
Get a list of catalog records.
Get Catalog Details Action
Get details of a catalog record.
Get Categories Action
Get the list of categories associated with a catalog record.
Get Category Details Action
Get details of a category record.
Get Multiple Product Details Action
Get product details for a list of products.
Get Products Action
Get products from the specified catalog, category, or subcategory, including product qualification and pricing details.
Get Product Details Action
Get details such as attributes, hierarchy, and cardinality for the specified product.
Search Product with Guided Selection Action
Use guided product selection to search for products.
Find Products Action
Search for the products from a catalog, category, or subcategory by using the specified search term.
This action is available in API version 62.0 and later.
Special Access Rules
The Find Products action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery is enabled.
366
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 381 =====

Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/findProducts
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearer token
Inputs
DetailsInput
Type
Apex-defined
additionalContextData
Description
An array of Apex runtime_industries_cpq.AdditionalContextData records
that contain the additional nodes that are used along with the context definition nodes for data
hydration.
The maximum number of supported nodes is 10.
Type
Apex-defined
additionalFields
Description
An Apex runtime_industries_cpq.AdditionalFields record that contains an
array of additional standard or custom fields to include in the response.
The supported objects are:
• Product2
• ProductAttributeDefinition—If the fields defined for the
ProductAttributeDefinition  object aren’t available for the
ProductClassificationAttr  object, then the API request fails.
Type
string
catalogId
Description
Catalog ID that’s used to find and retrieve the products.
Type
string
categoryId
367
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 382 =====

DetailsInput
Description
ID of the category or subcategory to get the products for.
Type
string
contextDefinition
Description
API name of the context definition used for context creation. If you don’t specify a value, the
context selected on the Product Discovery Settings page from Setup is used.
Type
string
contextMapping
Description
API name of the context mapping that’s used for data hydration. The value of this parameter is
used only if it belongs to the specified context definition.
Type
string
correlationId
Description
Currency code that’s used to calculate and show prices. Only the products with the currency
code matching the specified currency code are fetched.
Type
string
currencyCode
Description
Currency code that’s used to calculate and show prices.
Type
string
cursor
Description
A unique identifier that represents the position of the product from which the next set of results
are retrieved.
Type
boolean
enablePricing
Description
Indicates whether the pricing procedure must run (true) or not (false).
The default value is true. To use this parameter, you must enable the Pricing Procedure setting
from Setup.
368
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 383 =====

DetailsInput
Type
boolean
enableQualification
Description
Indicates whether the qualification procedure must run (true) or not (false).
The default value is true. To use this parameter, you must enable the Qualification Procedure
setting from Setup.
Type
Apex-defined
filter
Description
A collection of Apex runtime_industries_cpq.FilterInputRepresentation
records where each record contains a related object and the filter criteria that’s applied on the
object.
The filter  parameter supports only the name  property.
The supported operators are:
• eq
• in
• contains
If this parameter contains multiple criteria, all the criteria are applied.
Type
boolean
includeCatalogDetails
Description
Indicates whether catalog details must be included in the response (true) or not (false).
Type
integer
limit
Description
Maximum number of results to be returned in the response. Enter a value from 1 through 100.
The default value is 10.
Type
string
orderBy
Description
Comma-separated string of key-value pairs that specify how results are sorted. Each string must
contain a field name and its sort order. For example,
["name:asc",”custom_field:asc”].
369
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 384 =====

DetailsInput
Type
string
priceBookId
Description
ID of the pricebook from which you wan to retrieve the pricing details.
Type
string
productClassificationId
Description
ID of the product classification that’s used to filter products.
Type
string
pricingProcedure
Description
API name of the pricing procedure to calculate product prices. If you don’t specify a value, the
pricing procedure selected on the Product Discovery Settings page from Setup is used.
Type
string
qualificationProcedure
Description
API name of the qualification procedure to evaluate product eligibility. If you don’t specify a
value, the qualification procedure selected on the Product Discovery Settings page from Setup
is used.
Type
Apex-defined
relatedObjectFilters
Description
A collection of Apex
runtime_industries_cpq.RelatedObjectFilterInputRepresentation
records, where each record contains a related object and the filter criteria that’s applied on the
object.
Type
string
searchTerm
Description
Required.
Search term to find and retrieve products.
Type
Apex-defined
userContext
370
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 385 =====

DetailsInput
Description
An Apex ConnectApi.UserContextInputRepresentation record that contains
the user details to evaluate product eligibility and calculate prices.
Outputs
DetailsOutput
Type
Apex-defined
apiStatus
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains a status code and message.
Type
string
contextId
Description
ID of the context that’s created by using the specified context definition.
Type
string
correlationId
Description
ID to reference a series of related actions.
Type
string
cursor
Description
Unique identifier that represents the position of the next product in the dataset. It’s used as an
input to retrieve the next set of products.
Type
Apex-defined
facets
Description
Collection of Apex ProductFacetsRepresentation records that contain details of the facet that's
retrieved.
Type
Apex-defined
results
371
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 386 =====

DetailsOutput
Description
An Apex runtime_industries_cpq.SearchProductsRepresentation record
that contains the products that match the query.
Type
Apex-defined
userContext
Description
An Apex ConnectApi.UserContextRepresentation  record that includes the user
details.
Example
POST
This sample request is for the Find Products action.
{
"inputs": [
{
"searchTerm": "firstproduct",
"additionalContextData": [
{
"nodeName": "Contract",
"nodeData": {
"id": "xxxxx231",
"name": "Contract1"
}
},
{
"nodeName": "Lead",
"nodeData": {
"id": "lllllll31",
"name": "Lead1"
}
}
],
"additionalFields": {
"Product2": {
"fields": [
"CustomField1__c",
"StandardField1"
]
}
},
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx0000000001GAA",
"categoryId": "0ZGxx0000000004TAJ",
"currencyCode": "USD",
"priceBookId": "01sxx0000005puLAAQ",
372
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 387 =====

"productClassificationId": "11BRO00000000222AA",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc"
],
"userContext": {
"accountId": "001xx0000000001AAA"
},
"enableQualification": true,
"enablePricing": true,
"qualificationProcedure": "QualificationProcedure",
"pricingProcedure": "Preview",
"contextDefinition": "TestDefinition",
"contextMapping": "TestDefinitionNode",
"includeCatalogDetails": false,
"filter": {
"criteria": [
{
"property": "name",
"operator": "eq",
"value": "Catalog_Name_1"
}
]
},
"relatedObjectFilters": [
{
"objectName": "ProductSpecificationRecType",
"criteria": [
{
"property": "IsCommercial",
"operator": "eq",
"value": true
}
]
}
]
}
]
}
This is the sample response for the Find Products action.
{
"apiStatus": {
"messages": [],
"statusCode": "FETCHED_DETAILS_SUCCESSFULLY"
},
"contextId": "0U3RM00000000SR0AY",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"cursor": "MTAwMDAwMDAwNg==",
"result": [
{
"additionalFields": {
"CustomField1__c": "TextValue",
373
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 388 =====

"CustomField2__c": "10",
"StandardField1": "false"
},
"description": "IPhone-13",
"id": "01txx0000006kYwAAI",
"name": "Sample product 1",
"prices": [
{
"price": 150,
"priceBookEntryId": "12Axx0000004DF7EAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"frequency": "Monthly",
"id": "12Bxx000000CiCDEA0",
"name": "IPhone-13",
"occurrence": 6,
"pricingModelType": "Recurring"
}
},
{
"price": 400,
"priceBookEntryId": "12Axx0000004DGjEAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"id": "12Bxx000000CiCCEA0",
"name": "IPhone-13",
"pricingModelType": "OneTime"
}
}
],
"qualificationContext": {
"isQualified": true
}
},
{
"additionalFields": {
"CustomField1__c": "TextValue",
"CustomField2__c": "10",
"StandardField1": "false"
},
"description": "Sample product 2",
"name": "Sample product 2",
"id": "01txx0000006kYwAAI",
"prices": [],
"qualificationContext": {
"isQualified": false
}
},
{
"description": "Sample product 3",
"name": "Sample product 3",
"id": "01txx0000006kYwAAI",
"prices": [],
"qualificationContext": {
374
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 389 =====

"isQualified": true
}
}
],
"userContext": {
"accountId": "001xx0000000001AAA"
}
}
Usage of an Apex-Defined Data Type in a Flow
To use an Apex-defined input parameter in a flow, follow these guidelines.
Create an Apex Class
Create an Apex class defining the input and output parameters. In the flow, include the Apex-defined input parameters for which
you want to add the details. In this example, we’ve created a class named ProductServiceAction that takes an object’s API name and
record ID as input, and returns the additional context data.
public class ProductServiceAction {
// Define input parameters
public class FlowInput{
@InvocableVariable(required=false)
public String objectApiName;
@InvocableVariable(required=false)
public String recordId;
}
// Define output parameters
public class FlowOutput{
@invocableVariable
public runtime_industries_cpq.AdditionalContextData
additionalContextDataFinalOutput = new runtime_industries_cpq.AdditionalContextData();
}
// This method is invoked from a Flow
@InvocableMethod(label='Process Input' description='Creates the Array of
ContextDataInput for additional Context Data')
public static List<FlowOutput> processContextData(List<FlowInput> inputs){
String apiName;
String recId;
FlowOutput output = new FlowOutput();
// Capture input from the flow
for(FlowInput input: inputs){
apiName = input.objectApiName;
recId = input.recordId;
}
// Populate the ContextDataInput list to store additional context data
List<runtime_industries_cpq.ContextDataInput> listContextData = new
List<runtime_industries_cpq.ContextDataInput>();
runtime_industries_cpq.ContextDataInput cd1 = new
runtime_industries_cpq.ContextDataInput();
cd1.nodeName = apiName;
375
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 390 =====

cd1.nodeData = new Map<String, Object>();
cd1.nodeData.put('id',recId);
listContextData.add(cd1);
output.additionalContextDataFinalOutput.additionalContextData = listContextData;
List<FlowOutput> flowOutputs = new List<FlowOutput>();
flowOutputs.add(output);
List<runtime_industries_cpq.RelatedObjectFilter> relatedObjectFilterList = new
List<runtime_industries_cpq.RelatedObjectFilter>();
runtime_industries_cpq.RelatedObjectFilter relatedObjectFilter = new
runtime_industries_cpq.RelatedObjectFilter();
relatedObjectFilter.objectName = 'ProductSpecificationRecType';
List<runtime_industries_cpq.FilterCriteriaInputRepresentation> criteriaList =
new List<runtime_industries_cpq.FilterCriteriaInputRepresentation>();
runtime_industries_cpq.FilterCriteriaInputRepresentation criteria = new
runtime_industries_cpq.FilterCriteriaInputRepresentation();
criteria.property = 'IsCommercial';
criteria.operator = 'eq';
criteria.value = 'true';
criteriaList.add(criteria);
relatedObjectFilter.criteria = criteriaList;
relatedObjectFilterList.add(relatedObjectFilter);
output.relatedObjectFilter.relatedObjectFilter = relatedObjectFilterList;
output.userContext.accountId = '001DU000001nx9BYAQ';
return flowOutputs;
}
}
Create a Flow with the Necessary Variables and Components
Create a flow that enables users to add a search term to find products. Add the ProductService action that you’ve created above by
using Apex. When a flow is invoked from a record, the flow sends the record's objectApiName and recordId to the Apex class, which
then generates the flow output. The flow passes the objectApiName and recordId of the record that the flow is invoked from to the
Apex class to generate the flow output. See Example of How to Create a Flow for Product Discovery.
Configure the Action
Configure the action (for example, Find Products action) to add values for the Apex-defined input parameters. Use the output of the
created Apex class as the input of the Apex-defined parameter in the Find Products action, which users can use to find products.
Execute Qualification Procedure Action
Execute a qualification procedure, which returns the qualification status for the specified products.
This action is available in API version 64.0 and later.
376
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 391 =====

Special Access Rules
The Execute Qualification Procedure action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery is
enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/executeQualificationProcedure
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
Apex-defined
additionalContextData
Description
Collection of Apex AdditionalContextData records that contain additional context data for nodes
of the custom context definition, if applicable. You can add details for up to 10 nodes. See
AdditionalContextData.
Type
string
contextDefinitionName
Description
Name of the custom context definition that’s used to create context data for categories. If null,
the default context definition is used.
Type
string
contextMappingName
Description
Name of the context mapping. By default, the default context mapping associated with the
context definition is used.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
377
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 392 =====

DetailsInput
Type
string
productIds
Description
Required.
Collection of IDs of products that are to be checked for qualification.
Type
string
qualificationProcedureName
Description
Name of the custom qualification procedure that’s executed to determine the category list. If
null, the default qualification procedure is executed.
Type
Apex-defined
userContextInputRepresentation
Description
An Apex UserContextInputRepresentation record that contains user details, such as account ID,
geographical location, language preferences, and more.
Outputs
DetailsOutput
Type
Apex-defined
apiStatusOutputRepresentation
Description
An Apex ApiStatusOutputRepresentation record that contains the status of the request, including
the status code and message.
Type
string
contextId
Description
ID of the context that’s created by using the specified context definition.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
378
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 393 =====

DetailsOutput
Type
Apex-defined
qualificationResultRepresentations
Description
Collection of Apex QualificationResultRepresentation records that contain details about the
qualified product.
Example
POST
Here's a sample input to call this invocable action.
{
"inputs": [
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"additionalContextData": [
{
"nodeName": "Quote__c",
"nodeData": {
"id": "0Q0xx0000004CDsCAM",
"businessObjectType": "Quote"
}
}
],
"contextDefinitionName": "CategoryCD",
"contextMappingName": "ProductDiscoveryMapping",
"qualificationProcedureName": "CatQual02",
"userContextInputRepresentation": {
"accountId": "001xx000003GYiEAAW"
}
}
]
}
Here's a sample input to call this invocable action from Apex code.
Invocable.Action action =
Invocable.Action.createStandardAction('executeQualificationProcedure');
ConnectApi.UserContextInputRepresentation userContext = new
ConnectApi.UserContextInputRepresentation();
userContext.accountId = '001xx000003GYiEAAW';
runtime_industries_cpq.ContextDataInput data = new
runtime_industries_cpq.ContextDataInput();
String nodeNameVal = 'Quote__c';
Map<String,Object> nodeDataVal = new Map<String,Object>();
nodeDataVal.put('id',(Object)'0Q0xx0000004CDsCAM');
nodeDataVal.put('businessObjectType',(Object)'Quote');
data.nodeName = nodeNameVal;
379
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 394 =====

data.nodeData = nodeDataVal;
List<runtime_industries_cpq.ContextDataInput> contextData= new
List<runtime_industries_cpq.ContextDataInput>();
contextData.add(data);
runtime_industries_cpq.AdditionalContextData additionalContextDataOut = new
runtime_industries_cpq.AdditionalContextData();
additionalContextDataOut.additionalContextData = new
List<runtime_industries_cpq.ContextDataInput>();
additionalContextDataOut.additionalContextData.add(data);
List<String> productIds = new List<String>();
prodIds.add('01txx0000006i2ZAAQ');
prodIds.add('01txx0000006i35AAA');
action2.setInvocationParameter('productIds', productIds);
action.setInvocationParameter('correlationId', '9cbb9650-48c5-11ed-96d1-0afcf185843b');
action.setInvocationParameter('userContextInputRepresentation', userContext);
action.setInvocationParameter('qualificationProcedureName', 'CatQual02');
action.setInvocationParameter('contextDefinitionName', 'CategoryCD');
action.setInvocationParameter('contextMappingName', 'ProductDiscoveryMapping');
action.setInvocationParameter('additionalContextData', additionalContextDataOut);
List<Invocable.Action.Result> results = action.invoke();
System.debug('Execute Qualification Procedure Action + '+results);
Here's a sample response when you call this action.
[
{
"actionName": "executeQualificationProcedure",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"apiStatusOutputRepresentation": {
"statusMessage": null,
"statusCode": "FetchedDetailsSuccessfully",
"messages": []
},
"qualificationResultRepresentations": [
{
"qualificationContext": {
"reason": null,
"isQualified": true
},
"productId": "01tSG000007uDL8YAM"
},
{
"qualificationContext": {
"reason": "Product is not qualified because one or more field(s) do not
match the qualification criteria. Fields:- ProductId - 01tSG000007uDLBYA2
Max_Number_of_Employees - 50 Min_Number_of_Employees - 50 RootProductId - ",
"isQualified": false
},
"productId": "01tSG000007uDLBYA2"
380
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 395 =====

}
],
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"contextId": "0000000b28op21g00251747224654739cade16577eac4c8fb5d94a20d952fdab"
},
"sortOrder": -1,
"version": 1
}
]
Get Catalogs Action
Get a list of catalog records.
This action is available in API version 64.0 and later.
Special Access Rules
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getCatalogs
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
integer
recordLimit
Description
Number of catalog records to get. The minimum is 1, the maximum is 100, and the default is
100.
Type
integer
recordOffset
Description
Number of catalog records to skip in the request. The default is 0.
Type
string
correlationId
381
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 396 =====

DetailsInput
Description
Unique identifier for tracking requests and messages, allowing reference to a specific transaction
or event chain.
Type
string
orderBy
Description
Sort records in ascending or descending order.
Outputs
DetailsOutput
Type
Apex-defined
resultCatalogList
Description
List of filtered catalog records. See CatalogOutputRepresentation.
Type
Apex-defined
apiStatusOutputRepresentation
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains the status of the request, including the status code and message.
Type
integer
recordLimit
Description
Number of catalog records to show per page.
Type
integer
resultListCount
Description
Number of catalog records in the result.
Type
string
correlationId
Description
Unique identifier for tracking requests and messages, allowing reference to a specific transaction
or event chain.
382
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 397 =====

DetailsOutput
Type
integer
recordOffset
Description
Number of catalog records to skip in the request. The default is 0.
Example
POST
Here's a sample input to call this invocable action.
{
"inputs": [
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"recordLimit": 2,
"recordOffset": 0,
"orderBy": [
"Name:ASC"
]
}
]
}
Here's a sample input to call this invocable action from Apex code.
Invocable.Action action = Invocable.Action.createStandardAction('getCatalogs');
action.setInvocationParameter('correlationId', '9cbb9650-48c5-11ed-96d1-0afcf185843b');
action.setInvocationParameter('recordLimit', 1);
action.setInvocationParameter('recordOffset', 1);
String[] sortOrder = new String[]{'Name:ASC'};
action.setInvocationParameter('orderBy', sortOrder);
List<Invocable.Action.Result> results = action.invoke();
System.debug('Catalog List Action + '+results);
Here's a sample response when you call this action.
[
{
"actionName": "getCatalogs",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"resultListCount": 2,
"apiStatusOutputRepresentation": {
"statusMessage": null,
"statusCode": "FetchedDetailsSuccessfully",
383
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 398 =====

"messages": []
},
"resultCatalogList": [
{
"status": null,
"numberOfCategories": 2,
"name": "Hardware Catalog",
"id": "0ZSZ6000000CtXYOA0",
"effectiveStartDate": null,
"effectiveEndDate": null,
"description": "Hardware Catalog Desc",
"customFields": [],
"catalogType": "Sales",
"catalogCode": "HC"
}
],
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"recordOffset": 0,
"recordLimit": 1
},
"sortOrder": -1,
"version": 1
}
]
Get Catalog Details Action
Get details of a catalog record.
This action is available in API version 64.0 and later.
Special Access Rules
The Get Catalog Details action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery is enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getCatalogDetails
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
384
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 399 =====

Inputs
DetailsInput
Type
string
catalogId
Description
Required.
ID of the catalog record.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, enabling reference to a specific transaction
or event chain.
Outputs
DetailsOutput
Type
Apex-defined
apiStatusOutputRepresentation
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains the status of the request, including the status code and message.
Type
Apex-defined
catalogDetailsResult
Description
Details of the catalog record.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
385
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 400 =====

Example
POST
Here's a sample input to call this invocable action.
{
"inputs": [
{
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSZ6000000CtXYOA0"
}
]
}
Here's a sample input to call this invocable action from Apex code.
Invocable.Action action = Invocable.Action.createStandardAction('getCatalogDetails');
action.setInvocationParameter('correlationId', '9cbb9650-48c5-11ed-96d1-0afcf185843b');
action.setInvocationParameter('catalogId', '0ZSZ6000000CtXYOA0');
List<Invocable.Action.Result> results = action.invoke();
System.debug('Catalog Details Action + '+results);
Here's a sample response when you call this action.
[
{
"actionName": "getCatalogDetails",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"apiStatusOutputRepresentation": {
"statusMessage": null,
"statusCode": "FetchedDetailsSuccessfully",
"messages": []
},
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogDetailsResult": {
"status": null,
"numberOfCategories": 2,
"name": "Hardware Catalog",
"id": "0ZSZ6000000CtXYOA0",
"effectiveStartDate": null,
"effectiveEndDate": null,
"description": "Hardware Catalog Desc",
"customFields": null,
"catalogType": "Sales",
"catalogCode": "HC"
}
},
"sortOrder": -1,
"version": 1
386
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 401 =====

}
]
Get Categories Action
Get the list of categories associated with a catalog record.
This action is available in API version 64.0 and later.
Special Access Rules
The Get Categories action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery is enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getCategories
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
Apex-defined
additionalContextData
Description
Collection of Apex runtime_industries_cpq.AdditionalContextData records
that contain additional context data for nodes of the custom context definition, if applicable.
You can add details for up to 10 nodes.
Type
string
catalogId
Description
Required.
ID of the catalog record.
Type
integer
categoryNestLevel
Description
Level of nesting within the category hierarchy to include in the request.
387
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 402 =====

DetailsInput
Type
string
contextDefinitionName
Description
Name of the custom context definition that’s used to create context data for categories. If null,
the default context definition is used.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
Type
string
contextMappingName
Description
Name of the context mapping. By default, the default context mapping associated with the
context definition is used.
Type
boolean
enableQualificationProcedure
Description
Indicates whether qualification rules are applied to categories (true) or not (false).
Type
Apex-defined
filterInputRepresentation
Description
Collection of Apex runtime_industries_cpq.FilterInputRepresentation
records that contain the filter criteria applied to the category records.
Type
string
parentCategoryId
Description
ID of the parent category record.
Type
string
qualificationProcedureName
Description
Name of the custom qualification procedure that’s executed to determine the category list. If
null, the default qualification procedure is executed.
388
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 403 =====

DetailsInput
Type
Apex-defined
userContextInputRepresentation
Description
An Apex UserContextInputRepresentation record that contains user details, such as account ID,
geographical location, language preferences, and more.
Outputs
DetailsOutput
Type
Apex-defined
apiStatusOutputRepresentation
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains the status of the request, including the status code and message.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
Type
Apex-defined
resultCategoryList
Description
List of filtered category records. See CategoryOutputRepresentation.
Type
integer
resultListCount
Description
Number of category records in the result.
Example
POST
Here's a sample input to call this invocable action.
{
"inputs": [
{
"catalogId": "0ZSxx0000000002GAA",
389
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 404 =====

"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"additionalContextData": [
{
"nodeName": "Quote__c",
"nodeData": {
"id": "0Q0xx0000004CDsCAM",
"businessObjectType": "Quote"
}
}
],
"contextDefinitionName": "CategoryCD",
"contextMappingName": "ProductDiscoveryMapping",
"EnableQualificationProcedure": true,
"QualificationProcedureName": "CatQual02",
"userContextInputRepresentation": {
"accountId": "001xx000003GYiEAAW"
}
}
]
}
Here's a sample input to call this invocable action from Apex code.
Invocable.Action action = Invocable.Action.createStandardAction('getCategories');
ConnectApi.UserContextInputRepresentation userContext = new
ConnectApi.UserContextInputRepresentation();
userContext.accountId = '001xx000003GYiEAAW';
runtime_industries_cpq.ContextDataInput data = new
runtime_industries_cpq.ContextDataInput();
String nodeNameVal = 'Quote__c';
Map<String,Object> nodeDataVal = new Map<String,Object>();
nodeDataVal.put('id',(Object)'0Q0xx0000004CDsCAM');
nodeDataVal.put('businessObjectType',(Object)'Quote');
data.nodeName = nodeNameVal;
data.nodeData = nodeDataVal;
List<runtime_industries_cpq.ContextDataInput> contextData= new
List<runtime_industries_cpq.ContextDataInput>();
contextData.add(data);
runtime_industries_cpq.AdditionalContextData additionalContextDataOut = new
runtime_industries_cpq.AdditionalContextData();
additionalContextDataOut.additionalContextData = new
List<runtime_industries_cpq.ContextDataInput>();
additionalContextDataOut.additionalContextData.add(data);
action.setInvocationParameter('catalogId', '0ZSxx0000000002GAA');
action.setInvocationParameter('correlationId', '9cbb9650-48c5-11ed-96d1-0afcf185843b');
action.setInvocationParameter('userContextInputRepresentation', userContext);
action.setInvocationParameter('enableQualificationProcedure', True);
action.setInvocationParameter('qualificationProcedureName', 'CatQual02');
action.setInvocationParameter('contextDefinitionName', 'CategoryCD');
action.setInvocationParameter('contextMappingName', 'ProductDiscoveryMapping');
action.setInvocationParameter('additionalContextData', additionalContextDataOut);
390
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 405 =====

//action.setInvocationParameter('categoryDepth', 4);
//action.setInvocationParameter('parentCategoryId', '0ZGxx0000000001GAA');
List<Invocable.Action.Result> results = action.invoke();
System.debug('Search Action + '+results);
Here's a sample response when you call this action.
[
{
"actionName": "getCategories",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"resultCategoryList": [
{
"sortOrder": null,
"qualificationContext": {
"reason": "Category is not qualified because one or more field(s) do not
match the qualification criteria. Fields:- CategoryId - 0ZGxx0000000001GAA quotename -
null Max_Number_of_Employees - 1500 Min_Number_of_Employees - 1500",
"isQualified": false
},
"parentCategoryId": null,
"name": "Laptops",
"isNavigational": true,
"id": "0ZGxx0000000001GAA",
"hasSubCategories": true,
"description": null,
"childCategories": [],
"catalogId": "0ZSxx0000000002GAA"
},
{
"sortOrder": null,
"qualificationContext": {
"reason": null,
"isQualified": true
},
"parentCategoryId": null,
"name": "Desktops",
"isNavigational": true,
"id": "0ZGxx0000000002GAA",
"hasSubCategories": false,
"description": null,
"childCategories": [],
"catalogId": "0ZSxx0000000002GAA"
},
{
"sortOrder": null,
"qualificationContext": {
"reason": null,
"isQualified": true
},
391
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 406 =====

"parentCategoryId": null,
"name": "Accessories",
"isNavigational": true,
"id": "0ZGxx0000000003GAA",
"hasSubCategories": false,
"description": null,
"childCategories": [],
"catalogId": "0ZSxx0000000002GAA"
}
],
"resultListCount": 3,
"apiStatusOutputRepresentation": {
"statusMessage": null,
"statusCode": "FetchedDetailsSuccessfully",
"messages": []
},
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b"
},
"sortOrder": -1,
"version": 1
}
]
Get Category Details Action
Get details of a category record.
This action is available in API version 64.0 and later.
Special Access Rules
The Get Category Details action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery is enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getCategoryDetails
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
Apex-defined
additionalContextData
392
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 407 =====

DetailsInput
Description
Collection of Apex runtime_industries_cpq.AdditionalContextData records
that contain additional context data for nodes of the custom context definition, if applicable.
You can add details for up to 10 nodes.
Type
string
catalogId
Description
ID of the catalog record that’s used to search for products within a category.
Type
string
categoryId
Description
Required.
ID of the category or subcategory that’s used to search for products.
Type
string
contextDefinitionName
Description
Name of the custom context definition that’s used to create context data for categories. If null,
the default context definition is used.
Type
string
contextMappingName
Description
Name of the context mapping. By default, the default context mapping associated with the
context definition is used.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
Type
boolean
enableQualificationProcedure
Description
Indicates whether qualification rules are applied to categories (true) or not (false).
393
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 408 =====

DetailsInput
Type
Apex-defined
filterInputRepresentation
Description
Collection of Apex runtime_industries_cpq.FilterInputRepresentation
records that contain the filter criteria applied to the category records.
Type
string
qualificationProcedureName
Description
Name of the custom qualification procedure that’s executed to determine the category list. If
null, the default qualification procedure is executed.
Type
Apex-defined
userContextInputRepresentation
Description
An Apex UserContextInputRepresentation record that contains user details, such as account ID,
geographical location, language preferences, and more.
Outputs
DetailsOutput
Type
Apex-defined
apiStatusOutputRepresentation
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains the status of the request, including the status code and message.
Type
Apex-defined
categoryDetailsRepresentations
Description
Collection of Apex CategoryDetailsRepresentation records that contain details about the retrieved
category.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
394
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 409 =====

Example
POST
Here's a sample input to call this invocable action.
{
"inputs": [
{
"categoryId": "0ZGxx0000000001GAA",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"additionalContextData": [
{
"nodeName": "Quote__c",
"nodeData": {
"id": "0Q0xx0000004CDsCAM",
"businessObjectType": "Quote"
}
}
],
"contextDefinitionName": "CategoryCD",
"contextMappingName": "ProductDiscoveryMapping",
"EnableQualificationProcedure": true,
"QualificationProcedureName": "CatQual02",
"userContextInputRepresentation": {
"accountId": "001xx000003GYiEAAW"
}
}
]
}
Here's a sample input to call this invocable action from Apex code.
Invocable.Action action = Invocable.Action.createStandardAction('getCategoryDetails');
ConnectApi.UserContextInputRepresentation userContext = new
ConnectApi.UserContextInputRepresentation();
userContext.accountId = '001xx000003GYiEAAW';
runtime_industries_cpq.ContextDataInput data = new
runtime_industries_cpq.ContextDataInput();
String nodeNameVal = 'Quote__c';
Map<String,Object> nodeDataVal = new Map<String,Object>();
nodeDataVal.put('id',(Object)'0Q0xx0000004CDsCAM');
nodeDataVal.put('businessObjectType',(Object)'Quote');
data.nodeName = nodeNameVal;
data.nodeData = nodeDataVal;
List<runtime_industries_cpq.ContextDataInput> contextData= new
List<runtime_industries_cpq.ContextDataInput>();
contextData.add(data);
runtime_industries_cpq.AdditionalContextData additionalContextDataOut = new
runtime_industries_cpq.AdditionalContextData();
additionalContextDataOut.additionalContextData = new
List<runtime_industries_cpq.ContextDataInput>();
additionalContextDataOut.additionalContextData.add(data);
395
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 410 =====

action.setInvocationParameter('categoryId', '0ZGxx0000000001GAA');
action.setInvocationParameter('correlationId', '9cbb9650-48c5-11ed-96d1-0afcf185843b');
action.setInvocationParameter('userContext', userContext);
action.setInvocationParameter('enableQualification', True);
action.setInvocationParameter('qualificationProcedure', 'CatQual02');
action.setInvocationParameter('contextDefinition', 'CategoryCD');
action.setInvocationParameter('contextMapping', 'ProductDiscoveryMapping');
action.setInvocationParameter('additionalContextData', additionalContextDataOut);
List<Invocable.Action.Result> results = action.invoke();
System.debug('Search Action + '+results);
Here's a sample response when you call this action.
{
"root": [
{
"actionName": "getCategoryDetails",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"apiStatusOutputRepresentation": {
"statusMessage": null,
"statusCode": "FetchedDetailsSuccessfully",
"messages": []
},
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"categoryDetailsRepresentations": {
"sortOrder": null,
"qualificationContext": {
"reason": "Category is not qualified because one or more field(s) do not
match the qualification criteria. Fields:- CategoryId - 0ZGxx0000000001GAA quotename -
null Max_Number_of_Employees - 1500 Min_Number_of_Employees - 1500",
"isQualified": false
},
"parentCategoryId": null,
"name": "Laptops",
"isNavigational": true,
"id": "0ZGxx0000000001GAA",
"hasSubCategories": true,
"description": null,
"childCategories": [
{
"sortOrder": null,
"qualificationContext": {
"reason": null,
"isQualified": true
},
"parentCategoryId": "0ZGxx0000000001GAA",
"name": "level1",
"isNavigational": true,
"id": "0ZGxx000000004rGAA",
396
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 411 =====

"hasSubCategories": true,
"description": null,
"childCategories": [],
"catalogId": null
}
],
"catalogId": "0ZSxx0000000002GAA"
}
},
"sortOrder": -1,
"version": 1
}
]
}
Get Multiple Product Details Action
Get product details for a list of products.
This action is available in API version 64.0 and later.
Special Access Rules
The Get Multiple Product Details action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery is enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getMultipleProductDetails
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
Apex-defined
additionalContextData
Description
Collection of Apex runtime_industries_cpq.AdditionalContextData records
that contain additional context data for nodes of the custom context definition, if applicable.
You can add details for up to 10 nodes.
397
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 412 =====

DetailsInput
Type
Apex-defined
additionalFields
Description
An Apex AdditionalFields record that contains the additional fields that are passed for the Product2
object.
Type
string
catalogId
Description
ID of the catalog record.
Type
string
contextDefinitionName
Description
Name of the custom context definition that’s used to create context data for categories. If null,
the default context definition is used.
Type
string
contextMappingName
Description
Name of the context mapping. By default, the default context mapping associated with the
context definition is used.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
Type
string
currencyCode
Description
Currency code that’s used to calculate and show prices.
Type
boolean
enablePricing
Description
Indicates whether pricing procedure must run (true) or not (false). The default value is
true. To use this parameter, the Pricing Procedure setting must be enabled.
398
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 413 =====

DetailsInput
Type
boolean
enableQualificationProcedure
Description
Indicates whether the qualification procedure is applied to categories (true) or not (false).
Type
string
priceBookId
Description
ID of the pricebook that the pricing information is retrieved from.
Type
string
pricingProcedureName
Description
Name of the pricing procedure to calculate product prices. If you don’t enter a value, the pricing
procedure selected on the Product Discovery Settings page is used.
Type
Apex-defined
productDataInputs
Description
Required.
Collection of Apex BulkProductDetailsInputBody records that contain details about the products
that are to be retrieved.
Type
string
qualificationProcedureName
Description
Name of the custom qualification procedure that’s executed to determine the category list. If
null, the default qualification procedure is executed.
Type
Apex-defined
userContextInputRepresentation
Description
An Apex UserContextInputRepresentation record that contains user details, such as account ID,
geographical location, language preferences, and more.
399
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 414 =====

Outputs
DetailsOutput
Type
Apex-defined
apiStatusOutputRepresentation
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains the status of the request, including the status code and message.
Type
string
contextId
Description
ID of the context that’s created using the specified context definition.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
Type
Apex-defined
productDetailsOutputRepresentation
Description
Collection of Apex BulkProductDetailsRepresentation records that contain details of available
products.
Type
Apex-defined
userContext
Description
An Apex ConnectApi.UserContextRepresentation record containing user information.
Example
POST
Here's a sample input to call this invocable action.
{
"inputs": [
{
"productDataInputs": {
"productData": [
{
"productId": "01txx0000006i2rAAA",
400
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 415 =====

"productSellingModelId": "0jPxx0000000002EAA"
},
{
"productId": "01txx0000006i2oAAA",
"productSellingModelId": "0jPxx0000000002EAA"
}
]
},
"priceBookId": "01sxx0000005ptpAAA",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"enableQualification": true,
"enablePricing": true,
"catalogId": "0ZSxx0000000002GAA",
"userContext": {
"accountId": "001xx000003GYiFAAW"
},
"currencyCode": "USD"
}
]
}
Here's a sample input to call this invocable action from Apex code.
Invocable.Action action =
Invocable.Action.createStandardAction('getMultipleProductDetails');
List<runtime_industries_cpq.BulkProductDetailsInputBody> productDataList = new
List<runtime_industries_cpq.BulkProductDetailsInputBody>();
runtime_industries_cpq.BulkProductDetailsInputBody productData = new
runtime_industries_cpq.BulkProductDetailsInputBody();
productData.productId = '01tIY000000nCxhYAE';
productDataList.add(productData);
runtime_industries_cpq.BulkProductDetailsInputBodyList productList = new
runtime_industries_cpq.BulkProductDetailsInputBodyList();
productList.productData = productDataList;
action.setInvocationParameter('productDataInputs', productList);
List<Invocable.Action.Result> results = action.invoke();
System.debug('Result === ' + results);
Here's a sample response when you call this action.
[
{
"actionName": "getMultipleProductDetails",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"apiStatusOutputRepresentation": {
"statusMessage": null,
401
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 416 =====

"statusCode": "FetchedDetailsSuccessfully",
"messages": []
},
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"contextId": null,
"productDetailsOutputRepresentation": [
{
"unitOfMeasure": {
"unitCode": null,
"scale": null,
"roundingMethod": null,
"name": null,
"id": null
},
"status": null,
"qualificationContext": null,
"productType": null,
"productSpecificationType": null,
"productSellingModelOptions": [
{
"productSellingModelId": "0jPxx0000000002EAA",
"productSellingModel": {
"status": "Active",
"sellingModelType": "TermDefined",
"pricingTermUnit": "Annual",
"pricingTerm": 1,
"name": "Term Based - Yearly",
"id": "0jPxx0000000002EAA"
},
"productId": "01txx0000006i2oAAA",
"id": "0iOxx000000000JEAQ"
}
],
"productRelatedComponent": {
"unitOfMeasure": null,
"sequence": null,
"quoteVisibility": null,
"quantityScaleMethod": null,
"quantity": null,
"productRelationshipTypeId": null,
"productComponentGroupId": null,
"productClassificationId": null,
"parentSellingModelId": null,
"parentProductId": null,
"minQuantity": null,
"maxQuantity": null,
"isQuantityEditable": null,
"isExcluded": null,
"isDefaultComponent": null,
"isComponentRequired": null,
"id": null,
"doesBundlePriceIncludeChild": null,
"childSellingModelId": null,
"childProductId": null
402
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 417 =====

},
"productQuantity": {
"quantity": null,
"minQuantity": null,
"maxQuantity": null
},
"productPricingInformation": null,
"productInformation": null,
"productComponentGroups": [],
"productCode": "ASTCERT001",
"productClassification": {
"id": null
},
"prices": [
{
"pricingModel": {
"unitOfMeasure": null,
"pricingModelType": "TermDefined",
"occurrence": 1,
"name": "Term Based - Yearly",
"id": "0jPxx0000000002EAA",
"frequency": "Annual"
},
"priceBookId": "01sxx0000005ptpAAA",
"priceBookEntryId": "01uxx0000008yXaAAI",
"price": 2000,
"isSelected": true,
"isDerived": false,
"isDefault": true,
"effectiveTo": null,
"effectiveFrom": null,
"currencyIsoCode": "USD"
}
],
"nodeType": "simpleProduct",
"name": "AI Specialist Certification",
"isSoldOnlyWithOtherProds": false,
"isQuantityEditable": null,
"isDefaultComponent": null,
"isComponentRequired": null,
"isAssetizable": true,
"isActive": true,
"id": "01txx0000006i2oAAA",
"endOfLifeDate": null,
"displayUrl":
"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQsp4GoUP_nGiCXJ-wzYkPx-RlA_UCUX0zIDv3slxnJACqXaRd1vHJUZe6yQklUiXvEDgo&usqp=CAU",
"discontinuedDate": null,
"description": "The Certified Artificial Intelligence Expert certification is
typically designed for individuals who have an in-depth understanding of artificial
intelligence (AI) concepts, algorithms, and applications and want to validate their
expertise in the field.",
"configureDuringSale": "NotAllowed",
"childProducts": [],
403
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 418 =====

"catalogs": [],
"availabilityDate": null,
"attributes": [],
"attributeCategories": [],
"additionalFields": []
},
{
"unitOfMeasure": {
"unitCode": null,
"scale": null,
"roundingMethod": null,
"name": null,
"id": null
},
"status": null,
"qualificationContext": null,
"productType": null,
"productSpecificationType": null,
"productSellingModelOptions": [
{
"productSellingModelId": "0jPxx0000000002EAA",
"productSellingModel": {
"status": "Active",
"sellingModelType": "TermDefined",
"pricingTermUnit": "Annual",
"pricingTerm": 1,
"name": "Term Based - Yearly",
"id": "0jPxx0000000002EAA"
},
"productId": "01txx0000006i2rAAA",
"id": "0iOxx000000000QEAQ"
}
],
"productRelatedComponent": {
"unitOfMeasure": null,
"sequence": null,
"quoteVisibility": null,
"quantityScaleMethod": null,
"quantity": null,
"productRelationshipTypeId": null,
"productComponentGroupId": null,
"productClassificationId": null,
"parentSellingModelId": null,
"parentProductId": null,
"minQuantity": null,
"maxQuantity": null,
"isQuantityEditable": null,
"isExcluded": null,
"isDefaultComponent": null,
"isComponentRequired": null,
"id": null,
"doesBundlePriceIncludeChild": null,
"childSellingModelId": null,
"childProductId": null
404
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 419 =====

},
"productQuantity": {
"quantity": null,
"minQuantity": null,
"maxQuantity": null
},
"productPricingInformation": null,
"productInformation": null,
"productComponentGroups": [],
"productCode": "ACERT001",
"productClassification": {
"id": null
},
"prices": [
{
"pricingModel": {
"unitOfMeasure": null,
"pricingModelType": "TermDefined",
"occurrence": 1,
"name": "Term Based - Yearly",
"id": "0jPxx0000000002EAA",
"frequency": "Annual"
},
"priceBookId": "01sxx0000005ptpAAA",
"priceBookEntryId": "01uxx0000008yXdAAI",
"price": 2000,
"isSelected": true,
"isDerived": false,
"isDefault": true,
"effectiveTo": null,
"effectiveFrom": null,
"currencyIsoCode": "USD"
}
],
"nodeType": "simpleProduct",
"name": "Admin Certification",
"isSoldOnlyWithOtherProds": false,
"isQuantityEditable": null,
"isDefaultComponent": null,
"isComponentRequired": null,
"isAssetizable": true,
"isActive": true,
"id": "01txx0000006i2rAAA",
"endOfLifeDate": null,
"displayUrl": null,
"discontinuedDate": null,
"description": null,
"configureDuringSale": "Allowed",
"childProducts": [],
"catalogs": [],
"availabilityDate": null,
"attributes": [],
"attributeCategories": [],
"additionalFields": []
405
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 420 =====

}
]
},
"sortOrder": -1,
"version": 1
}
]
Get Products Action
Get products from the specified catalog, category, or subcategory, including product qualification and pricing details.
If a catalog, category, or subcategory isn’t specified, then this action retrieves all the products from all catalogs. This action is available
in API version 62.0 and later.
Special Access Rules
The Get Products action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery is enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getProducts
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearer token
Inputs
DetailsInput
Type
Apex-defined
additionalContextData
Description
An array of Apex runtime_industries_cpq.AdditionalContextData records
that contain the additional nodes that are used along with the context definition nodes for data
hydration.
The maximum number of supported nodes is 10.
Type
Apex-defined
additionalFields
406
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 421 =====

DetailsInput
Description
An Apex runtime_industries_cpq.AdditionalFields record that contains an
array of additional standard or custom fields to include in the response.
The supported objects are:
• Product2
• ProductAttributeDefinition—If the fields defined for the
ProductAttributeDefinition  object aren’t available for the
ProductClassificationAttr  object, then the API request fails.
Type
string
catalogId
Description
Catalog ID that’s used to find and retrieve the products.
Type
string
categoryId
Description
ID of the category or subcategory to get the products for.
Type
string
contextDefinition
Description
API name of the context definition that’s used for context creation.
If you don’t specify a value, the context selected on the Product Discovery Settings page from
Setup is used.
Type
string
contextMapping
Description
API name of the context mapping that’s used for data hydration.
The value of this parameter is used only if it belongs to the specified context definition.
Type
string
correlationId
Description
Unique ID that’s used to reference a series of related actions.
407
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 422 =====

DetailsInput
Type
string
currencyCode
Description
Currency code that’s used to calculate and show prices. Only the products with the currency
code matching the specified currency code are fetched.
Type
string
cursor
Description
Unique identifier that represents the position of the product from which the next set of results
are retrieved.
Type
boolean
enablePricing
Description
Indicates whether the pricing procedure must run (true) or not (false).
The default value is true. To use this parameter, you must enable the Pricing Procedure setting
from Setup.
Type
boolean
enableQualification
Description
Indicates whether the qualification procedure must run (true) or not (false).
The default value is true. To use this parameter, you must enable the Qualification Procedure
setting from Setup.
Type
Apex-defined
filter
Description
A collection of Apex runtime_industries_cpq.FilterInputRepresentation
records where each record contains a related object and the filter criteria that’s applied on the
object.
The filter  parameter supports only the name property.
The supported operators are:
• eq
• in
• contains
If this parameter contains multiple criteria, all the criteria are applied.
408
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 423 =====

DetailsInput
Type
boolean
includeCatalogDetails
Description
Indicates whether catalog details must be included in the response (true) or not (false).
Type
integer
limit
Description
Maximum number of results to be returned in the response. Specify a value from 1 through 100.
The default value is 10.
Type
string
orderBy
Description
Comma-separated string of key-value pairs that specify how the results are sorted. Each string
must contain a field name and its sort order. For example,
["name:asc",”custom_field:asc”].
Type
string
priceBookId
Description
ID of the pricebook that the pricing details are retrieved from.
Type
string
pricingProcedure
Description
API name of the pricing procedure to calculate product prices. If you don’t specify a value, the
pricing procedure selected on the Product Discovery Settings page from Setup is used.
Type
string
productClassificationId
Description
ID of the product classification that’s used to filter the products.
Type
string
qualificationProcedure
409
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 424 =====

DetailsInput
Description
API name of the qualification procedure to evaluate product eligibility. If you don’t specify a
value, the qualification procedure selected on the Product Discovery Settings page from Setup
is used.
Type
Apex-defined
relatedObjectFilters
Description
A collection of Apex
runtime_industries_cpq.RelatedObjectFilterInputRepresentation
records, where each record contains a related object and the filter criteria that’s applied on the
object.
Type
Apex-defined
userContext
Description
An Apex ConnectApi.UserContextInputRepresentation record that contains
the user details to evaluate product eligibility and calculate prices.
Outputs
DetailsOutput
Type
Apex-defined
apiStatus
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains a status code and message.
Type
string
contextId
Description
ID of the context that’s created by using the specified context definition.
Type
string
correlationId
Description
ID to reference a series of related actions.
410
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 425 =====

DetailsOutput
Type
string
cursor
Description
Unique identifier that represents the position of the product from which the next set of results
are retrieved.
Type
Apex-defined
results
Description
An Apex runtime_industries_cpq.ProductListRepresentation record that
contains the retrieved products.
Type
Apex-defined
userContext
Description
An Apex ConnectApi.UserContextRepresentation record that includes the user
details.
Example
POST
This sample request is for the Get Products action.
{
"inputs": [
{
"additionalContextData": [
{
"nodeName": "Contract",
"nodeData": {
"id": "xxxxx231",
"name": "Contract1"
}
},
{
"nodeName": "Lead",
"nodeData": {
"id": "lllllll31",
"name": "Lead1"
}
}
],
"additionalFields": {
"Product2": {
"fields": [
411
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 426 =====

"CustomField1__c",
"StandardField1"
]
}
},
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx0000000001GAA",
"categoryId": "0ZGxx0000000004TAJ",
"currencyCode": "USD",
"priceBookId": "01sxx0000005puLAAQ",
"productClassificationId": "11BRO00000000222AA",
"limit": 10,
"cursor": "MTAwMDAwMDAwNg==",
"orderBy": [
"name:asc"
],
"userContext": {
"accountId": "001xx0000000001AAA"
},
"enableQualification": true,
"enablePricing": true,
"qualificationProcedure": "QualificationProcedure",
"pricingProcedure": "Preview",
"contextDefinition": "TestDefinition",
"contextMapping": "TestDefinitionNode",
"filter": {
"criteria": [
{
"property": "name",
"operator": "eq",
"value": "Catalog_Name_1"
}
]
},
"relatedObjectFilters": [
{
"objectName": "ProductSpecificationRecType",
"criteria": [
{
"property": "IsCommercial",
"operator": "eq",
"value": true
}
]
}
]
}
]
}
This is the sample response for the Get Products action.
{
"apiStatus": {
"messages": [],
412
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 427 =====

"statusCode": "FETCHED_DETAILS_SUCCESSFULLY"
},
"contextId": "0U3RM00000000SR0AY",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"cursor": "MTAwMDAwMDAwNg==",
"result": [
{
"additionalFields": {
"CustomField1__c": "TextValue",
"CustomField2__c": "10",
"StandardField1": "false"
},
"description": "IPhone-13",
"id": "01txx0000006kYwAAI",
"name": "Sample product 1",
"prices": [
{
"price": 150,
"priceBookEntryId": "12Axx0000004DF7EAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"frequency": "Monthly",
"id": "12Bxx000000CiCDEA0",
"name": "IPhone-13",
"occurrence": 6,
"pricingModelType": "Recurring"
}
},
{
"price": 400,
"priceBookEntryId": "12Axx0000004DGjEAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"id": "12Bxx000000CiCCEA0",
"name": "IPhone-13",
"pricingModelType": "OneTime"
}
}
],
"qualificationContext": {
"isQualified": true
}
},
{
"additionalFields": {
"CustomField1__c": "TextValue",
"CustomField2__c": "10",
"StandardField1": "false"
},
"description": "Sample product 2",
"name": "Sample product 2",
"id": "01txx0000006kYwAAI",
"prices": [],
"qualificationContext": {
413
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 428 =====

"isQualified": false
}
},
{
"description": "Sample product 3",
"name": "Sample product 3",
"id": "01txx0000006kYwAAI",
"prices": [],
"qualificationContext": {
"isQualified": true
}
}
],
"userContext": {
"accountId": "001xx0000000001AAA"
}
}
Usage of an Apex-Defined Data Type in a Flow
To use an Apex-defined input parameter in a Flow, follow these guidelines.
Create an Apex class
Create an Apex class defining the input and output parameters. In the flow, include the Apex-defined input parameters for which
you want to add the details. In this example, we have created a class named ProductServiceAction that takes an object’s API name
and record ID as input, and returns the additional context data.
public class ProductServiceAction {
// Define input parameters
public class FlowInput{
@InvocableVariable(required=false)
public String objectApiName;
@InvocableVariable(required=false)
public String recordId;
}
// Define output parameters
public class FlowOutput{
@invocableVariable
public runtime_industries_cpq.AdditionalContextData
additionalContextDataFinalOutput = new runtime_industries_cpq.AdditionalContextData();
@invocableVariable
public runtime_industries_cpq.RelatedObjectFilterInputRepresentation
relatedObjectFilter= new runtime_industries_cpq.RelatedObjectFilterInputRepresentation();
@invocableVariable
public ConnectApi.UserContextInputRepresentation userContext = new
ConnectApi.UserContextInputRepresentation();
}
414
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 429 =====

// This method is invoked from a Flow
@InvocableMethod(label='Process Input' description='Creates the Array of
ContextDataInput for additional Context Data')
public static List<FlowOutput> processContextData(List<FlowInput> inputs){
String apiName;
String recId;
FlowOutput output = new FlowOutput();
// Capture input from the flow
for(FlowInput input: inputs){
apiName = input.objectApiName;
recId = input.recordId;
}
// Populate the ContextDataInput list to store additional context data
List<runtime_industries_cpq.ContextDataInput> listContextData = new
List<runtime_industries_cpq.ContextDataInput>();
runtime_industries_cpq.ContextDataInput cd1 = new
runtime_industries_cpq.ContextDataInput();
cd1.nodeName = apiName;
cd1.nodeData = new Map<String, Object>();
cd1.nodeData.put('id',recId);
listContextData.add(cd1);
output.additionalContextDataFinalOutput.additionalContextData = listContextData;
List<FlowOutput> flowOutputs = new List<FlowOutput>();
flowOutputs.add(output);
List<runtime_industries_cpq.RelatedObjectFilter> relatedObjectFilterList = new
List<runtime_industries_cpq.RelatedObjectFilter>();
runtime_industries_cpq.RelatedObjectFilter relatedObjectFilter = new
runtime_industries_cpq.RelatedObjectFilter();
relatedObjectFilter.objectName = 'ProductSpecificationRecType';
List<runtime_industries_cpq.FilterCriteriaInputRepresentation> criteriaList =
new List<runtime_industries_cpq.FilterCriteriaInputRepresentation>();
runtime_industries_cpq.FilterCriteriaInputRepresentation criteria = new
runtime_industries_cpq.FilterCriteriaInputRepresentation();
criteria.property = 'IsCommercial';
criteria.operator = 'eq';
criteria.value = 'true';
criteriaList.add(criteria);
relatedObjectFilter.criteria = criteriaList;
relatedObjectFilterList.add(relatedObjectFilter);
output.relatedObjectFilter.relatedObjectFilter = relatedObjectFilterList;
output.userContext.accountId = '001Hs00003r17HNIAY';
return flowOutputs;
}
415
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 430 =====

}
Create a Flow with the necessary variables and components
Create a flow that enables users to add a search term to find products. Add the ProductService action that you’ve created above by
using Apex. When a flow is invoked from a record, the flow sends the record's objectApiName and recordId to the Apex class, which
then generates the flow output. The flow passes the objectApiName and recordId of the record that the flow is invoked from to the
Apex class to generate the flow output. See Example of How to Create a Flow for Product Discovery.
Configure the action
Configure the action (for example, Get Products action) to add values for the Apex-defined input parameters. Use the output of the
created Apex class as the input of the Apex-defined parameter in the Get Products action, which users can use to get products.
Get Product Details Action
Get details such as attributes, hierarchy, and cardinality for the specified product.
This action is available in API version 62.0 and later.
Special Access Rules
The Get Product Details action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery is enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/getProductDetails
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearer token
Inputs
DetailsInput
Type
Apex-defined
additionalContextData
Description
An array of Apex runtime_industries_cpq.AdditionalContextData records
that contain the additional nodes that are used along with the context definition nodes for data
hydration.
The maximum number of supported nodes is 10.
416
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 431 =====

DetailsInput
Type
Apex-defined
additionalFields
Description
An Apex runtime_industries_cpq.AdditionalFields record that contains an
array of additional standard or custom fields to include in the response.
The supported objects are:
• Product2
• ProductAttributeDefinition—If the fields defined for the
ProductAttributeDefinition  object aren’t available for the
ProductClassificationAttr  object, then the API request fails.
Type
string
catalogId
Description
Catalog ID that’s used to find and retrieve the products.
Type
string
contextDefinition
Description
API name of the context definition for context creation.
If you don’t provide a value, the context selected on the Product Discovery Settings page from
Setup is used.
Type
string
contextMapping
Description
API name of the context mapping for data hydration. The value of this parameter is used only if
it belongs to the specified context definition.
Type
string
correlationId
Description
Currency code that’s used to calculate and show prices. Only the products with the currency
code matching the specified currency code are fetched.
Type
string
currencyCode
417
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 432 =====

DetailsInput
Description
Currency code that’s used to calculate and show prices.
Type
boolean
enablePricing
Description
Indicates whether the pricing procedure must run (true) or not (false).
The default value is true.
To use this parameter, you must enable the Pricing Procedure setting from Setup.
Type
boolean
enableQualification
Description
Indicates whether the qualification procedure must run (true) or not (false).
The default value is true.
To use this parameter, you must enable the Qualification Procedure setting from Setup.
Type
string
priceBookId
Description
ID of the pricebook from which you want to retrieve the pricing details.
Type
string
pricingProcedure
Description
API name of the pricing procedure to calculate product prices.
If you don’t specify a value, the pricing procedure selected on the Product Discovery Settings
page from Setup is used.
Type
string
productId
Description
Required.
ID of the product to get the details for.
Type
string
productSellingModelId
418
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 433 =====

DetailsInput
Description
ID of the product selling model.
Type
string
qualificationProcedure
Description
API name of the qualification procedure to evaluate product eligibility.
If you don’t specify a value, the qualification procedure selected on the Product Discovery Settings
page from Setup is used.
Type
Apex-defined
userContext
Description
An Apex ConnectApi.UserContextInputRepresentation record that contains
the user details to evaluate product eligibility and calculate prices.
Outputs
DetailsOutput
Type
Apex-defined
apiStatus
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains a status code and message.
Type
string
contextId
Description
ID of the context that’s created by using the specified context definition.
Type
string
correlationId
Description
ID to reference a series of related actions.
Type
Apex-defined
results
419
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 434 =====

DetailsOutput
Description
An Apex runtime_industries_cpq.ProductDetailsRepresentation record
that contains the product details.
Type
Apex-defined
userContext
Description
An Apex ConnectApi.UserContextRepresentation record that contains the user
details.
Example
POST
This sample request is for the Get Product Details action.
{
"inputs": [{
"additionalContextData": [
{
"nodeName": "Contract",
"nodeData": {
"id": "xxxxx231",
"name": "Contract1"
}
},
{
"nodeName": "Lead",
"nodeData": {
"id": "lllllll31",
"name": "Lead1"
}
}
],
"additionalFields": {
"Product2": {
"fields": [
"CustomField1__c",
"StandardField1"
]
}
},
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"catalogId": "0ZSxx0000000001GAA",
"currencyCode": "USD",
"priceBookId": "01sxx0000005puLAAQ",
"productId": "01txx0000006j08AAA",
"productSellingModelId": "0jPxx000000004rEAA",
"userContext": {
420
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 435 =====

"accountId": "001xx0000000001AAA"
},
"enableQualification": true,
"enablePricing": true,
"qualificationProcedure": "QualificationProcedure",
"pricingProcedure": "Preview",
"contextDefinition": "TestDefinition",
"contextMapping": "TestDefinitionNode"
}]
}
This is the sample response for the Get Product Details action.
{
"apiStatus": {
"messages": [],
"statusCode": "FETCHED_DETAILS_SUCCESSFULLY"
},
"contextId": "0U3RM00000000SR0AY",
"correlationId": "9cbb9650-48c5-11ed-96d1-0afcf185843b",
"result": [
{
"additionalFields": {
"CustomField1__c": "TextValue",
"CustomField2__c": "10",
"StandardField1": "false"
},
"description": "IPhone-13",
"id": "01txx0000006kYwAAI",
"name": "Sample product 1",
"prices": [
{
"price": 150,
"priceBookEntryId": "12Axx0000004DF7EAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"frequency": "Monthly",
"id": "12Bxx000000CiCDEA0",
"name": "IPhone-13",
"occurrence": 6,
"pricingModelType": "Recurring"
}
},
{
"price": 400,
"priceBookEntryId": "12Axx0000004DGjEAM",
"priceBookId": "01sxx0000005puLAAQ",
"pricingModel": {
"id": "12Bxx000000CiCCEA0",
"name": "IPhone-13",
"pricingModelType": "OneTime"
}
}
],
"qualificationContext": {
421
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 436 =====

"isQualified": true
}
},
{
"additionalFields": {
"CustomField1__c": "TextValue",
"CustomField2__c": "10",
"StandardField1": "false"
},
"description": "Sample product 2",
"name": "Sample product 2",
"id": "01txx0000006kYwAAI",
"prices": [],
"qualificationContext": {
"isQualified": false
}
},
{
"description": "Sample product 3",
"name": "Sample product 3",
"id": "01txx0000006kYwAAI",
"prices": [],
"qualificationContext": {
"isQualified": true
}
}
],
"userContext": {
"accountId": "001xx0000000001AAA"
}
}
Usage of an Apex-Defined Data Type in a Flow
To use an Apex-defined input parameter in a flow, follow these guidelines.
Create an Apex Class
Create an Apex class defining the input and output parameters. In the flow, include the Apex-defined input parameters for which
you want to add the details. In this example, we have created a class named ProductServiceAction that takes an object’s API name
and record ID as input, and returns the additional context data.
public class ProductServiceAction {
// Define input parameters
public class FlowInput{
@InvocableVariable(required=false)
public String objectApiName;
@InvocableVariable(required=false)
public String recordId;
}
// Define output parameters
public class FlowOutput{
@invocableVariable
422
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 437 =====

public runtime_industries_cpq.AdditionalContextData
additionalContextDataFinalOutput = new runtime_industries_cpq.AdditionalContextData();
}
// This method is invoked from a Flow
@InvocableMethod(label='Process Input' description='Creates the Array of
ContextDataInput for additional Context Data')
public static List<FlowOutput> processContextData(List<FlowInput> inputs){
String apiName;
String recId;
FlowOutput output = new FlowOutput();
// Capture input from the flow
for(FlowInput input: inputs){
apiName = input.objectApiName;
recId = input.recordId;
}
// Populate the ContextDataInput list to store additional context data
List<runtime_industries_cpq.ContextDataInput> listContextData = new
List<runtime_industries_cpq.ContextDataInput>();
runtime_industries_cpq.ContextDataInput cd1 = new
runtime_industries_cpq.ContextDataInput();
cd1.nodeName = apiName;
cd1.nodeData = new Map<String, Object>();
cd1.nodeData.put('id',recId);
listContextData.add(cd1);
output.additionalContextDataFinalOutput.additionalContextData = listContextData;
List<FlowOutput> flowOutputs = new List<FlowOutput>();
flowOutputs.add(output);
List<runtime_industries_cpq.RelatedObjectFilter> relatedObjectFilterList = new
List<runtime_industries_cpq.RelatedObjectFilter>();
runtime_industries_cpq.RelatedObjectFilter relatedObjectFilter = new
runtime_industries_cpq.RelatedObjectFilter();
relatedObjectFilter.objectName = 'ProductSpecificationRecType';
List<runtime_industries_cpq.FilterCriteriaInputRepresentation> criteriaList =
new List<runtime_industries_cpq.FilterCriteriaInputRepresentation>();
runtime_industries_cpq.FilterCriteriaInputRepresentation criteria = new
runtime_industries_cpq.FilterCriteriaInputRepresentation();
criteria.property = 'IsCommercial';
criteria.operator = 'eq';
criteria.value = 'true';
criteriaList.add(criteria);
relatedObjectFilter.criteria = criteriaList;
relatedObjectFilterList.add(relatedObjectFilter);
output.relatedObjectFilter.relatedObjectFilter = relatedObjectFilterList;
output.userContext.accountId = '001DU000001nx9BYAQ';
423
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 438 =====

return flowOutputs;
}
}
Create a Flow with the Necessary Variables and Components
Create a flow that enables users to add a search term to find products. Add the ProductService action that you’ve created above by
using Apex. When a flow is invoked from a record, the flow sends the record's objectApiName and recordId to the Apex class, which
then generates the flow output. The flow passes the objectApiName and recordId of the record that the flow is invoked from to the
Apex class to generate the flow output. See Example of How to Create a Flow for Product Discovery.
Configure the action
Configure the action (for example, Get Product Details action) to add values for the Apex-defined input parameters. Use the output
of the created Apex class as the input of the Apex-defined parameter in the Get Product Details action, which users can use to get
the product details.
Search Product with Guided Selection Action
Use guided product selection to search for products.
This action is available in API version 64.0 and later.
Special Access Rules
The Search Product with Guided Selection action is available in Enterprise, Unlimited, and Developer Editions where Product Discovery
is enabled.
Supported REST HTTP Methods
URI
/services/data/v66.0/actions/standard/searchPrdctWithGuidedSelection
Formats
JSON, XML
HTTP Methods
POST
Authentication
Authorization: Bearertoken
Inputs
DetailsInput
Type
Apex-defined
additionalContextData
424
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 439 =====

DetailsInput
Description
Collection of Apex runtime_industries_cpq.AdditionalContextData records
that contain the nodes used in addition to context definition nodes for data hydration. This
parameter can contain up to 10 nodes.
Type
Apex-defined
additionalFields
Description
An Apex runtime_industries_cpq.AdditionalFields record that contains the
collection of additional fields to be included in the response. This parameter supports only the
fields from the Product2 and ProductAttributeDefinition objects. The fields defined for the
ProductAttributeDefinition object must also be available on the ProductClassificationAttr object.
Type
string
catalogId
Description
ID of the catalog to find and retrieve products.
Type
string
categoryId
Description
ID of the category or subcategory to find and retrieve products.
Type
string
contextDefinition
Description
API name of the context definition that's used for context creation. If you don’t specify a value,
the context selected on the Product Discovery Settings page is used.
Type
string
contextMapping
Description
API name of the context mapping that's used for data hydration. The value of this parameter is
used only if it belongs to the specified context definition.
Type
string
correlationId
Description
Unique ID that’s used to reference a series of related actions.
425
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 440 =====

DetailsInput
Type
string
currencyCode
Description
Currency code that’s used to calculate and show prices. Only the products with the currency
code matching the entered currency code are fetched.
Type
boolean
enablePricing
Description
Indicates whether pricing procedure must run (true) or not (false). The default value is
true. To use this parameter, the Pricing Procedure setting must be enabled.
Type
boolean
enableQualification
Description
Indicates whether qualification procedure must run (true) or not (false). The default value
is true. To use this parameter, the Qualification Procedure setting must be enabled.
Type
Apex-defined
filterInputRepresentation
Description
An Apex runtime_industries_cpq.FilterInputRepresentation record that
contains the filter criteria. This parameter supports only the name  property and the eq, in, or
contains  operators. If it contains multiple criteria, all the criteria are applied.
Type
string
guidedSelectionResponseId
Description
Response identifier that stores user responses specified in the guided product selection window.
Type
boolean
includeCatalogDetails
Description
Indicates whether catalog details must be included in the response (true) or not (false).
Type
string
orderBy
Description
Comma-delimited string of key-value pairs that specify how results are sorted. Each string must
contain a field name and its sort order. For example, ["name:asc",”custom_field:asc”].
426
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 441 =====

DetailsInput
Type
string
priceBookId
Description
ID of the pricebook that the pricing information is retrieved from.
Type
string
pricingProcedure
Description
API name of the pricing procedure to calculate product prices. If you don’t specify a value, the
pricing procedure selected on the Product Discovery Settings page is used.
Type
string
productClassificationId
Description
ID of the product classification that's used to filter products.
Type
string
productCursor
Description
Unique identifier that represents the position of the product from which the next set of results
are retrieved.
Type
string
qualificationProcedure
Description
API name of the qualification procedure to evaluate product eligibility. If you don’t specify a
value, the qualification procedure selected on the Product Discovery Settings page is used.
Type
integer
recordLimit
Description
Maximum number of results to be returned in the response. Specify a value from 1 through 100.
Default value is 10.
Type
Apex-defined
relatedObjectFilters
Description
Collection of Apex
runtime_industries_cpq.RelatedObjectFilterInputRepresentation
records, each containing a related object and the filter criteria that’s applied on the object.
427
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 442 =====

DetailsInput
Type
Apex-defined
searchTerms
Description
Collection of terms that are used to search products. See GuidedSelectionSearchTerm.
Type
Apex-defined
userContext
Description
An Apex ConnectApi.UserContextInputRepresentation record containing user information to
evaluate product eligibility and calculate pricing.
Outputs
DetailsOutput
Type
Apex-defined
apiStatusOutputRepresentation
Description
An Apex runtime_industries_cpq.ApiStatusRepresentation record that
contains the status of the request, including the status code and message.
Type
string
contextId
Description
ID of the context that’s created by using the specified context definition.
Type
string
correlationId
Description
Unique identifier attached to requests and messages, allowing reference to a specific transaction
or event chain.
Type
string
productCursor
Description
Unique identifier that represents the position of the product from which the next set of results
are retrieved.
Type
Apex-defined
productListOutputRepresentations
428
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 443 =====

DetailsOutput
Description
Collection of Apex ProductListOutputRepresentation records that contain details about the
product shown by the Guided Product Selection.
Type
integer
recordOffset
Description
Number of catalog records to skip in the request. The default is 0.
Type
Apex-defined
searchTerms
Description
Collection of terms that are used to search products. See GuidedSelectionSearchTerm.
Type
Apex-defined
userContext
Description
An Apex ConnectApi.UserContextRepresentation record containing user information.
Example
POST
Here's a sample input to call this invocable action.
{
"inputs": [
{
"searchTerms": {
"searchTerms": [
{
"term": "Laptop"
}
]
},
"categoryId": "0ZGxx0000000001GAA",
"correlationId": "77f9dc6a-8ecc-44a3-8d89-4050179cc846",
"additionalContextData": [
{
"nodeName": "Quote__c",
"nodeData": {
"id": "0Q0xx0000004CDsCAM",
"businessObjectType": "Quote"
}
}
],
429
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 444 =====

"contextDefinition": "CategoryCD",
"contextMapping": "ProductDiscoveryMapping",
"enableQualification": true,
"qualificationProcedure": "CatQual02",
"userContext": {
"accountId": "001xx000003GYiEAAW"
}
}
]
}
Here's a sample input to call this invocable action from Apex code.
Invocable.Action action =
Invocable.Action.createStandardAction('searchPrdctWithGuidedSelection');
action.setInvocationParameter('correlationId', '77f9dc6a-8ecc-44a3-8d89-4050179cc846');
//action.setInvocationParameter('catalogId', '0ZSxx000000004sGAA');
action.setInvocationParameter('guidedSelectionResponseId', '0U3xx0000004CPACA2');
//action.setInvocationParameter('priceBookId', '01sxx0000005pyfAAA');
//action.setInvocationParameter('categoryId', '0ZGxx000000004rGAA');
action.setInvocationParameter('enableQualification', true);
action.setInvocationParameter('enablePricing', true);
//action.setInvocationParameter('contextDefinition', 'PDACDCtx');
//action.setInvocationParameter('contextMapping', 'ProductDiscoveryMapping');
//action.setInvocationParameter('qualificationProcedure', 'PDQualProceWithQuote');
//action.setInvocationParameter('pricingProcedure', 'IconpricingProcedure');
action.setInvocationParameter('includeCatalogDetails', true);
action.setInvocationParameter('currencyCode', 'USD');
List<String> orderByInputs = new List<String>();
orderByInputs.add('name:asc');
orderByInputs.add('id:desc');
action.setInvocationParameter('orderBy', orderByInputs);
List<runtime_industries_cpq.GuidedSelectionSearchTerm> searchTerms = new
List<runtime_industries_cpq.GuidedSelectionSearchTerm>();
runtime_industries_cpq.GuidedSelectionSearchTerm searchTerm = new
runtime_industries_cpq.GuidedSelectionSearchTerm();
searchTerm.term = 'Laptop Basic Bundle';
List<String> tags = new List<String>();
tags.add('Laptop');
tags.add('Desktop');
searchTerm.tags = tags;
searchTerms.add(searchTerm);
runtime_industries_cpq.GuidedSelectionSearchTermList searchTermList = new
runtime_industries_cpq.GuidedSelectionSearchTermList();
searchTermList.searchTerms = searchTerms;
action.setInvocationParameter('searchTerms', searchTermList);
List<Invocable.Action.Result> results = action.invoke();
System.debug('Guided Selection result = ' + results);
Here's a sample response when you call this action.
[
{
430
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 445 =====

"actionName": "searchPrdctWithGuidedSelection",
"errors": null,
"invocationId": null,
"isSuccess": true,
"outcome": null,
"outputValues": {
"productListOutputRepresentations": [
{
"unitOfMeasure": null,
"status": null,
"qualificationContext": {
"reason": null,
"isQualified": true
},
"productType": null,
"productSpecificationType": {
"productSpecificationRecordType": {
"isCommercial": null
},
"name": "Commercial"
},
"productSellingModelOptions": [
{
"productSellingModelId": "0jPLT0000000YWL2A2",
"productSellingModel": {
"status": "Active",
"sellingModelType": "OneTime",
"pricingTermUnit": null,
"pricingTerm": null,
"name": "One Time",
"id": "0jPLT0000000YWL2A2"
},
"productId": "01tLT000007DFAiYAO",
"id": "0iOLT0000000n4j2AA"
}
],
"productRelatedComponent": null,
"productQuantity": null,
"productPricingInformation": null,
"productInformation": null,
"productComponentGroups": [],
"productCode": "LBG001",
"productClassification": {
"id": null
},
"prices": [],
"nodeType": "simpleProduct",
"name": "Laptop Bag",
"isSoldOnlyWithOtherProds": false,
"isQuantityEditable": null,
"isDefaultComponent": null,
"isComponentRequired": null,
"isAssetizable": true,
"isActive": true,
431
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 446 =====

"id": "01tLT000007DFAiYAO",
"endOfLifeDate": null,
"displayUrl":
"https://gangslifestyle.com/cdn/shop/files/goldstorm-collegetravel-backpack-513.png?v=1706166408&width=1300",
"discontinuedDate": null,
"description": "Premium Laptop bag with separate compartments for laptop and
accessories.",
"configureDuringSale": "NotAllowed",
"childProducts": [],
"categories": [
{
"sortOrder": null,
"qualificationContext": {
"reason": null,
"isQualified": true
},
"parentCategoryId": null,
"name": "Accessories",
"isNavigational": null,
"id": "0ZGLT000000JBsd4AG",
"hasSubCategories": false,
"description": null,
"childCategories": null,
"catalogId": "0ZSLT000000DUoI4AW"
}
],
"catalogs": [],
"availabilityDate": null,
"attributeCategories": [],
"additionalFields": []
}
],
"searchTerms": [
{
"term": "Laptop Bag",
"tags": []
}
],
"apiStatusOutputRepresentation": {
"statusMessage": null,
"statusCode": "FetchedDetailsSuccessfully",
"messages": []
},
"correlationId": "77f9dc6a-8ecc-44a3-8d89-4050179cc846",
"contextId": null,
"recordOffset": 1
},
"sortOrder": -1,
"version": 1
}
]
432
Product Discovery Standard Invocable ActionsProduct Catalog Management

===== PAGE 447 =====

Product Discovery Apex Reference
Use built-in Apex classes and interfaces grouped by namespace.
runtime_industries_cpq Namespace
The runtime_industries_cpq namespace provides classes and methods to search products or to manage products, catalogs, and
categories.
runtime_industries_cpq Namespace
The runtime_industries_cpq namespace provides classes and methods to search products or to manage products, catalogs, and
categories.
The runtime_industries_cpq  namespace includes these classes.
Usage
You can access the runtime_industries_cpq  classes if your org has the Product Discovery feature.
AdditionalContextData Class
Contains properties to include a list of additional context data nodes. These nodes are used along with the context definition nodes
for data hydration.
AdditionalFields Class
Contains properties to include a map where the key is a string and the value is an instance of the AdditionalFieldsInput class.
AdditionalFieldsInput Class
Contains properties to include the additional standard or custom fields in the request.
ApiStatusRepresentation Class
Stores details of the API request such as execution messages, status code, and status message.
AttributeCategoryOutputRepresentation Class
Stores details of an attribute such as code, description, usage type, and so on.
AttributePickListOutputRepresentation Class
Stores details of an attribute picklist.
AttributePickListValueOutputRepresentation Class
Stores details of an attribute picklist value.
BulkProductDetailsInputBody Class
Contains the details of the request to retrieve product details by using product ID and product selling model ID.
BulkProductDetailsInputBodyList Class
Contains details of the request to retrieve a list of products.
BulkProductDetailsRepresentation Class
Get the details of multiple product definitions in a single request. This class is used for bulk product retrieval operations in Product
Discovery.
CatalogOutputRepresentation Class
Contains properties to store details of a catalog definition.
433
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 448 =====

ConfigRuleResult Class
Contains the results of configuration rule evaluation, including message rules, product recommendation rules, and visibility rules
that are applied during product configuration.
CategoryOutputRepresentation Class
Contains properties to store details of a category.
ContextDataInput Class
Get details of a context.
FacetValueRepresentation Class
Get details of the facet values that are found in the search result.
Filter Class
Contains the criteria property to store the details of a filter criteria, which is used to filter records.
FilterCriteriaInputRepresentation Class
Contains properties to store criteria details to filter records based on supported properties.
FilterInputRepresentation Class
Contains the filter property to filters records based on supported criteria.
GuidedSelectionRepresentation Class
Contains properties to represent a product in a guided selection flow. This class is used in Product Discovery to provide structured
product information during guided product selection processes.
GuidedSelectionSearchTerm Class
Represents a search term used in guided product selection. Contains the search term text and associated tags for filtering and
searching products in Product Discovery.
GuidedSelectionSearchTermList Class
Contains a list of search terms used in guided product selection. This class is used to pass multiple search terms for filtering and
searching products in Product Discovery.
MessageRule Class
Represents a message rule that is evaluated during product configuration. Message rules display informational, warning, or error
messages to users based on configuration conditions.
PricingModelOutputRepresentation Class
Contains details of a pricing model in a product configuration.
ProductAttributeOutputRepresentation Class
Contains details about the attribute in a product configuration.
ProductClassificationOutputRepresentation Class
Get details of the product classification in a product configuration.
ProductComponentGroupOutputRepresentation Class
Get details of the product component group in a product classification.
ProductComponentGroupRepresentation Class
Represents a product component group used in bulk product operations. This class is similar to
ProductComponentGroupOutputRepresentation but is used specifically for bulk product detail representations where components
are represented as BulkProductDetailsRepresentation objects.
ProductDetailsRepresentation Class
Get the details of a product definition.
434
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 449 =====

ProductListRepresentation Class
Get the list of retrieved products.
ProductOutputRepresentation Class
Get the details of a product definition.
ProductPricesOutputRepresentation Class
Get the price details of a product.
ProductQuantityOutputRepresentation Class
Represents the quantity constraints and current quantity for a product in the product discovery context.
ProductRecommendationRule Class
Represents a product recommendation rule that is evaluated during product configuration. Product recommendation rules suggest
additional products to users based on configuration conditions.
ProductRelatedComponentOutputRepresentation Class
Represents a related component product in a bundle or product relationship, including component configuration details such as
quantity constraints, required status, and relationship metadata.
ProductSellingModelOptionOutputRepresentation Class
Represents a selling model option available for a product, which defines how the product can be sold (such as subscription, one-time,
or usage-based).
ProductSellingModelOutputRepresentation Class
Represents a product selling model that defines how a product is sold, including the selling model type, pricing term, and status.
ProductSpecificationRecordTypeOutputRepresentation Class
Represents the record type information for a product specification, which defines the type of record used to store product specification
data.
ProductSpecificationTypeOutputRepresentation Class
Represents a product specification type that defines the structure and attributes available for configuring a product.
QocQualificationOutputRepresentation Class
Represents a quote, order, or contract qualification that determines whether a product can be sold based on specific business rules
and conditions.
QualificationContextOutputRepresentation Class
Represents the context information used for product qualification, including account, opportunity, and other relevant context data
for determining product eligibility.
RelatedObjectFilter Class
Represents a filter for related objects used in product search and discovery, allowing you to filter products based on related object
criteria.
RelatedObjectFilterInputRepresentation Class
Represents input criteria for filtering products based on related object information, such as account, opportunity, or contract data.
SearchProductsFacetRepresentation Class
Represents a search facet that provides filtering and categorization options for product search results, such as categories, attributes,
or other product characteristics.
SearchProductsRepresentation Class
Represents the results of a product search operation, including the list of products, search facets, pagination information, and total
count of matching products.
435
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 450 =====

UnitOfMeasureOutputRepresentation Class
Represents the unit of measure for a product. This class contains information about how product quantities are measured, including
the unit code, name, scale, and rounding method.
VisibilityRule Class
Represents a visibility rule that is evaluated during product configuration. Visibility rules control the visibility of products, attributes,
or other UI elements based on configuration conditions.
AdditionalContextData Class
Contains properties to include a list of additional context data nodes. These nodes are used along with the context definition nodes for
data hydration.
Namespace
runtime_industries_cpq on page 433
AdditionalContextData Properties
Set the AdditionalContextData class property to specify a list of additional nodes for data hydration.
AdditionalContextData Properties
Set the AdditionalContextData class property to specify a list of additional nodes for data hydration.
The AdditionalContextData  class includes this property.
additionalContextData
Include a list of additional nodes that are used along with the context definition nodes for data hydration. The maximum number
of supported nodes is 10.
additionalContextData
Include a list of additional nodes that are used along with the context definition nodes for data hydration. The maximum number of
supported nodes is 10.
Signature
public List<runtime_industries_cpq.ContextDataInput> additionalContextData {get; set;}
Property Value
Type: List<runtime_industries_cpq.ContextDataInput on page 469>
AdditionalFields Class
Contains properties to include a map where the key is a string and the value is an instance of the AdditionalFieldsInput class.
Namespace
runtime_industries_cpq on page 433
436
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 451 =====

AdditionalFields Properties
Set the AdditionalFields class property to include a map where the key is a string and the value is an instance of the
AdditionalFieldsInput class.
AdditionalFields Properties
Set the AdditionalFields class property to include a map where the key is a string and the value is an instance of the AdditionalFieldsInput
class.
The AdditionalFields  class includes this property.
additionalFields
Includes a map where the key is a string and the value is an instance of the AdditionalFieldsInput class.
additionalFields
Includes a map where the key is a string and the value is an instance of the AdditionalFieldsInput class.
Signature
public Map<String,runtime_industries_cpq.AdditionalFieldsInput> additionalFields {get;
set;}
Property Value
Type: Map<String,runtime_industries_cpq.AdditionalFieldsInput on page 437>
AdditionalFieldsInput Class
Contains properties to include the additional standard or custom fields in the request.
Namespace
runtime_industries_cpq on page 433
AdditionalFieldsInput Properties
Set the AdditionalFieldsInput class property to include the additional standard or custom fields in the response.
AdditionalFieldsInput Properties
Set the AdditionalFieldsInput class property to include the additional standard or custom fields in the response.
The AdditionalFieldsInput  class includes this property.
fields
Include the additional standard or custom fields in the response.
fields
Include the additional standard or custom fields in the response.
437
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 452 =====

Signature
public List<String> fields {get; set;}
Property Value
Type: List<String>
ApiStatusRepresentation Class
Stores details of the API request such as execution messages, status code, and status message.
Namespace
runtime_industries_cpq on page 433
ApiStatusRepresentation Properties
Contains properties to include the API response details.
ApiStatusRepresentation Properties
Contains properties to include the API response details.
The ApiStatusRepresentation  class includes these properties.
messages
Get the status messages of the API execution.
statusCode
Get the status code of the API execution.
statusMessage
Get the display label for the API status.
messages
Get the status messages of the API execution.
Signature
public List<ConnectApi.CpqMessageOutputRepresentation> messages {get; set;}
Property Value
Type: List<ConnectApi.CpqMessageOutputRepresentation>
statusCode
Get the status code of the API execution.
438
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 453 =====

Signature
public String statusCode {get; set;}
Property Value
Type: String
statusMessage
Get the display label for the API status.
Signature
public String statusMessage {get; set;}
Property Value
Type: String
AttributeCategoryOutputRepresentation Class
Stores details of an attribute such as code, description, usage type, and so on.
Namespace
runtime_industries_cpq on page 433
AttributeCategoryOutputRepresentation Properties
Contains properties to include details of an attribute.
AttributeCategoryOutputRepresentation Properties
Contains properties to include details of an attribute.
The AttributeCategoryOutputRepresentation  class includes these properties.
code
Get the code of the attribute category.
description
Get the description of the attribute category.
id
Get the ID of the attribute category.
name
Get the name of the attribute category.
records
Get the attributes of the attribute category.
439
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 454 =====

status
Get the status of the attribute category.
totalSize
Get the total size of the attribute category.
usageType
Get the usage type of the attribute category.
code
Get the code of the attribute category.
Signature
public String code {get; set;}
Property Value
Type: String
description
Get the description of the attribute category.
Signature
public String description {get; set;}
Property Value
Type: String
id
Get the ID of the attribute category.
Signature
public String id {get; set;}
Property Value
Type: String
name
Get the name of the attribute category.
Signature
public String name {get; set;}
440
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 455 =====

Property Value
Type: String
records
Get the attributes of the attribute category.
Signature
public List<runtime_industries_cpq.ProductAttributeOutputRepresentation> records {get;
set;}
Property Value
Type: List<runtime_industries_cpq.ProductAttributeOutputRepresentation on page 491>
status
Get the status of the attribute category.
Signature
public String status {get; set;}
Property Value
Type: String
totalSize
Get the total size of the attribute category.
Signature
public Integer totalSize {get; set;}
Property Value
Type: Integer
usageType
Get the usage type of the attribute category.
Signature
public String usageType {get; set;}
Property Value
Type: String
441
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 456 =====

AttributePickListOutputRepresentation Class
Stores details of an attribute picklist.
Namespace
runtime_industries_cpq on page 433
AttributePickListOutputRepresentation Properties
Contains properties to include details of an attribute picklist.
AttributePickListOutputRepresentation Properties
Contains properties to include details of an attribute picklist.
The AttributePickListOutputRepresentation  class includes these properties.
description
Get the description of the attribute picklist.
id
Get the ID of the attribute picklist.
name
Get the name of the attribute picklist.
status
Get the status of the attribute picklist.
values
Get the values of the attribute picklist.
dataType
Get the datatype value.
description
Get the description of the attribute picklist.
Signature
public String description {get; set;}
Property Value
Type: String
id
Get the ID of the attribute picklist.
442
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 457 =====

Signature
public String id {get; set;}
Property Value
Type: String
name
Get the name of the attribute picklist.
Signature
public String name {get; set;}
Property Value
Type: String
status
Get the status of the attribute picklist.
Signature
public String status {get; set;}
Property Value
Type: String
values
Get the values of the attribute picklist.
Signature
public List<runtime_industries_cpq.AttributePickListValueOutputRepresentation> values
{get; set;}
Property Value
Type: List<runtime_industries_cpq.AttributePickListValueOutputRepresentation on page 444>
dataType
Get the datatype value.
Signature
public String dataType {get; set;}
443
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 458 =====

Property Value
Type: String
AttributePickListValueOutputRepresentation Class
Stores details of an attribute picklist value.
Namespace
runtime_industries_cpq on page 433
AttributePickListValueOutputRepresentation Properties
Contains properties to include details of an attribute picklist value.
AttributePickListValueOutputRepresentation Properties
Contains properties to include details of an attribute picklist value.
The AttributePickListValueOutputRepresentation  class includes these properties.
code
Get the code of the attribute picklist value.
description
Get the description of attribute picklist value.
displayValue
Get the display value of the attribute value.
id
Get the ID of the attribute picklist value.
isBooleanValue
Indicates whether this attribute value is a boolean value (true) or not (false).
label
Get the label of the attribute picklist value.
name
Get the name of the attribute picklist value.
sequence
Get the sequence of the attribute picklist value.
status
Get the status of the attribute picklist value.
textValue
Get the text value of the attribute picklist value.
code
Get the code of the attribute picklist value.
444
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 459 =====

Signature
public String code {get; set;}
Property Value
Type: String
description
Get the description of attribute picklist value.
Signature
public String description {get; set;}
Property Value
Type: String
displayValue
Get the display value of the attribute value.
Signature
public String displayValue {get; set;}
Property Value
Type: String
id
Get the ID of the attribute picklist value.
Signature
public String id {get; set;}
Property Value
Type: String
isBooleanValue
Indicates whether this attribute value is a boolean value (true) or not (false).
Signature
public Boolean isBooleanValue {get; set;}
445
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 460 =====

Property Value
Type: Boolean
label
Get the label of the attribute picklist value.
Signature
public String label {get; set;}
Property Value
Type: String
name
Get the name of the attribute picklist value.
Signature
public String name {get; set;}
Property Value
Type: String
sequence
Get the sequence of the attribute picklist value.
Signature
public Integer sequence {get; set;}
Property Value
Type: Integer
status
Get the status of the attribute picklist value.
Signature
public String status {get; set;}
Property Value
Type: String
446
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 461 =====

textValue
Get the text value of the attribute picklist value.
Signature
public String textValue {get; set;}
Property Value
Type: String
BulkProductDetailsInputBody Class
Contains the details of the request to retrieve product details by using product ID and product selling model ID.
Namespace
runtime_industries_cpq on page 433
BulkProductDetailsInputBody Properties
Contains properties to retrieve details of products.
BulkProductDetailsInputBody Properties
Contains properties to retrieve details of products.
The BulkProductDetailsInputBody  class includes these properties.
productId
Set the ID of the product to return the details for.
productSellingModelId
Set the ID of the product selling model to return the details for.
productId
Set the ID of the product to return the details for.
Signature
public String productId {get; set;}
Property Value
Type: String
productSellingModelId
Set the ID of the product selling model to return the details for.
447
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 462 =====

Signature
public String productSellingModelId {get; set;}
Property Value
Type: String
BulkProductDetailsInputBodyList Class
Contains details of the request to retrieve a list of products.
Namespace
runtime_industries_cpq on page 433
BulkProductDetailsInputBodyList Properties
Contains properties to retrieve details of a list of products.
BulkProductDetailsInputBodyList Properties
Contains properties to retrieve details of a list of products.
The BulkProductDetailsInputBodyList  class includes these properties.
productData
Set the list of maps that contain product IDs and product selling model IDs.
productData
Set the list of maps that contain product IDs and product selling model IDs.
Signature
public List<runtime_industries_cpq.BulkProductDetailsInputBody>productData {get; set;}
Property Value
Type: List<runtime_industries_cpq.BulkProductDetailsInputBody on page 447>
BulkProductDetailsRepresentation Class
Get the details of multiple product definitions in a single request. This class is used for bulk product retrieval operations in Product
Discovery.
Namespace
runtime_industries_cpq on page 433
448
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 463 =====

BulkProductDetailsRepresentation Constructor
Learn more about the constructors that are available with the BulkProductDetailsRepresentation class.
BulkProductDetailsRepresentation Properties
Contains properties to include details of product definitions retrieved in bulk operations.
BulkProductDetailsRepresentation Constructor
Learn more about the constructors that are available with the BulkProductDetailsRepresentation class.
The BulkProductDetailsRepresentation  class includes these constructors.
BulkProductDetailsRepresentation(apexObj)
Constructor to create a BulkProductDetailsRepresentation instance from a ConnectApi CPQProductDetailsOutputRepresentation
object.
BulkProductDetailsRepresentation()
Default constructor to create an empty BulkProductDetailsRepresentation instance.
BulkProductDetailsRepresentation(apexObj)
Constructor to create a BulkProductDetailsRepresentation instance from a ConnectApi CPQProductDetailsOutputRepresentation object.
Signature
public BulkProductDetailsRepresentation(ConnectApi.CPQProductDetailsOutputRepresentation
apexObj)
Parameters
apexObj
Type: ConnectApi.CPQProductDetailsOutputRepresentation
The ConnectApi product details representation object to convert to BulkProductDetailsRepresentation.
BulkProductDetailsRepresentation()
Default constructor to create an empty BulkProductDetailsRepresentation instance.
Signature
public BulkProductDetailsRepresentation()
BulkProductDetailsRepresentation Properties
Contains properties to include details of product definitions retrieved in bulk operations.
The BulkProductDetailsRepresentation  class includes these properties.
additionalFields
Get the list of additionalfield.
449
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 464 =====

attributeCategories
Get the list of attributecategorie.
attributes
Get the list of attribute.
availabilityDate
Get the availability date.
catalogs
Get the list of catalog.
childProducts
Get the list of childproduct.
configureDuringSale
Get the configureduringsale value.
description
Get the description of the bulkproductdetails.
discontinuedDate
Get the discontinued date.
displayUrl
Get the displayurl value.
endOfLifeDate
Get the endoflife date.
isActive
Indicates whether the item is active.
isAssetizable
Indicates whether assetizable is true or false.
isComponentRequired
Indicates whether componentrequired is true or false.
id
Get the ID of the product.
isDefaultComponent
Indicates whether defaultcomponent is true or false.
isQuantityEditable
Indicates whether quantityeditable is true or false.
isSoldOnlyWithOtherProds
Indicates whether soldonlywithotherprods is true or false.
name
Get the name of the bulkproductdetails.
nodeType
Get the nodetype value.
prices
Get the list of price.
450
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 465 =====

productClassification
Get the productclassification value.
productCode
Get the productcode value.
productComponentGroups
Get the list of productcomponentgroup.
productInformation
Get the productinformation value.
productPricingInformation
Get the productpricinginformation value.
productQuantity
Get the productquantity value.
productRelatedComponent
Get the productrelatedcomponent value.
productSellingModelOptions
Get the list of productsellingmodeloption.
productSpecificationType
Get the productspecificationtype value.
productType
Get the producttype value.
qualificationContext
Get the qualificationcontext value.
status
Get the status of the bulkproductdetails.
unitOfMeasure
Get the unitofmeasure value.
additionalFields
Get the list of additionalfield.
Signature
public List<runtime_industries_cpq.AdditionalFieldsWrapper> additionalFields {get;
set;}
Property Value
Type: List<runtime_industries_cpq.AdditionalFieldsWrapper>
attributeCategories
Get the list of attributecategorie.
451
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 466 =====

Signature
public List<runtime_industries_cpq.AttributeCategoryOutputRepresentation>
attributeCategories {get; set;}
Property Value
Type: List<runtime_industries_cpq.AttributeCategoryOutputRepresentation on page 439>
attributes
Get the list of attribute.
Signature
public List<runtime_industries_cpq.ProductAttributeOutputRepresentation> attributes
{get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductAttributeOutputRepresentation on page 491>
availabilityDate
Get the availability date.
Signature
public Datetime availabilityDate {get; set;}
Property Value
Type: Datetime
catalogs
Get the list of catalog.
Signature
public List<runtime_industries_cpq.CatalogOutputRepresentation> catalogs {get; set;}
Property Value
Type: List<runtime_industries_cpq.CatalogOutputRepresentation on page 459>
childProducts
Get the list of childproduct.
452
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 467 =====

Signature
public List<runtime_industries_cpq.BulkProductDetailsRepresentation> childProducts
{get; set;}
Property Value
Type: List<runtime_industries_cpq.BulkProductDetailsRepresentation on page 448>
configureDuringSale
Get the configureduringsale value.
Signature
public String configureDuringSale {get; set;}
Property Value
Type: String
description
Get the description of the bulkproductdetails.
Signature
public String description {get; set;}
Property Value
Type: String
discontinuedDate
Get the discontinued date.
Signature
public Datetime discontinuedDate {get; set;}
Property Value
Type: Datetime
displayUrl
Get the displayurl value.
Signature
public String displayUrl {get; set;}
453
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 468 =====

Property Value
Type: String
endOfLifeDate
Get the endoflife date.
Signature
public Datetime endOfLifeDate {get; set;}
Property Value
Type: Datetime
isActive
Indicates whether the item is active.
Signature
public Boolean isActive {get; set;}
Property Value
Type: Boolean
isAssetizable
Indicates whether assetizable is true or false.
Signature
public Boolean isAssetizable {get; set;}
Property Value
Type: Boolean
isComponentRequired
Indicates whether componentrequired is true or false.
Signature
public Boolean isComponentRequired {get; set;}
Property Value
Type: Boolean
454
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 469 =====

id
Get the ID of the product.
Signature
public String id {get; set;}
Property Value
Type: String
isDefaultComponent
Indicates whether defaultcomponent is true or false.
Signature
public Boolean isDefaultComponent {get; set;}
Property Value
Type: Boolean
isQuantityEditable
Indicates whether quantityeditable is true or false.
Signature
public Boolean isQuantityEditable {get; set;}
Property Value
Type: Boolean
isSoldOnlyWithOtherProds
Indicates whether soldonlywithotherprods is true or false.
Signature
public Boolean isSoldOnlyWithOtherProds {get; set;}
Property Value
Type: Boolean
name
Get the name of the bulkproductdetails.
455
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 470 =====

Signature
public String name {get; set;}
Property Value
Type: String
nodeType
Get the nodetype value.
Signature
public String nodeType {get; set;}
Property Value
Type: String
prices
Get the list of price.
Signature
public List<runtime_industries_cpq.ProductPricesOutputRepresentation> prices {get;
set;}
Property Value
Type: List<runtime_industries_cpq.ProductPricesOutputRepresentation on page 537>
productClassification
Get the productclassification value.
Signature
public runtime_industries_cpq.ProductClassificationOutputRepresentation
productClassification {get; set;}
Property Value
Type: runtime_industries_cpq.ProductClassificationOutputRepresentation on page 499
productCode
Get the productcode value.
456
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 471 =====

Signature
public String productCode {get; set;}
Property Value
Type: String
productComponentGroups
Get the list of productcomponentgroup.
Signature
public List<runtime_industries_cpq.ProductComponentGroupRepresentation>
productComponentGroups {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductComponentGroupRepresentation on page 503>
productInformation
Get the productinformation value.
Signature
public String productInformation {get; set;}
Property Value
Type: String
productPricingInformation
Get the productpricinginformation value.
Signature
public String productPricingInformation {get; set;}
Property Value
Type: String
productQuantity
Get the productquantity value.
457
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 472 =====

Signature
public runtime_industries_cpq.ProductQuantityOutputRepresentationproductQuantity {get;
set;}
Property Value
Type: runtime_industries_cpq.ProductQuantityOutputRepresentation on page 540
productRelatedComponent
Get the productrelatedcomponent value.
Signature
public runtime_industries_cpq.ProductRelatedComponentOutputRepresentation
productRelatedComponent {get; set;}
Property Value
Type: runtime_industries_cpq.ProductRelatedComponentOutputRepresentation on page 544
productSellingModelOptions
Get the list of productsellingmodeloption.
Signature
public List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation>
productSellingModelOptions {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation on page 550>
productSpecificationType
Get the productspecificationtype value.
Signature
public runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation
productSpecificationType {get; set;}
Property Value
Type: runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation on page 555
productType
Get the producttype value.
458
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 473 =====

Signature
public String productType {get; set;}
Property Value
Type: String
qualificationContext
Get the qualificationcontext value.
Signature
public runtime_industries_cpq.QualificationContextOutputRepresentation
qualificationContext {get; set;}
Property Value
Type: runtime_industries_cpq.QualificationContextOutputRepresentation on page 557
status
Get the status of the bulkproductdetails.
Signature
public String status {get; set;}
Property Value
Type: String
unitOfMeasure
Get the unitofmeasure value.
Signature
public runtime_industries_cpq.UnitOfMeasureOutputRepresentation unitOfMeasure {get;
set;}
Property Value
Type: runtime_industries_cpq.UnitOfMeasureOutputRepresentation on page 571
CatalogOutputRepresentation Class
Contains properties to store details of a catalog definition.
459
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 474 =====

Namespace
runtime_industries_cpq on page 433
CatalogOutputRepresentation Properties
Contains properties to include details of a catalog definition.
CatalogOutputRepresentation Properties
Contains properties to include details of a catalog definition.
The CatalogOutputRepresentation  class includes these properties.
catalogCode
Get the unique ID associated with the catalog.
catalogType
Get the category of an entry in the catalog, which is customizable. For example, catalog types, such as sellable products, services,
parts, technical services, or technical resources.
customFields
Get details of the custom fields associated with a catalog.
description
Get the description of the catalog.
effectiveEndDate
Get the date and time from when the catalog isn't available to the end users.
effectiveStartDate
Get the date and time from when the catalog is available to the end users.
id
Get the ID of the catalog.
name
Get the name of the catalog.
numberOfCategories
Get the number of categories in the catalog.
status
Get the status of the catalog.
catalogCode
Get the unique ID associated with the catalog.
Signature
public String catalogCode {get; set;}
Property Value
Type: String
460
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 475 =====

catalogType
Get the category of an entry in the catalog, which is customizable. For example, catalog types, such as sellable products, services, parts,
technical services, or technical resources.
Signature
public String catalogType {get; set;}
Property Value
Type: String
customFields
Get details of the custom fields associated with a catalog.
Signature
public List<runtime_industries_cpq.AdditionalFieldsWrapper> customFields {get; set;}
Property Value
Type: List<runtime_industries_cpq.AdditionalFieldsWrapper>
description
Get the description of the catalog.
Signature
public String description {get; set;}
Property Value
Type: String
effectiveEndDate
Get the date and time from when the catalog isn't available to the end users.
Signature
public String effectiveEndDate {get; set;}
Property Value
Type: String
effectiveStartDate
Get the date and time from when the catalog is available to the end users.
461
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 476 =====

Signature
public String effectiveStartDate {get; set;}
Property Value
Type: String
id
Get the ID of the catalog.
Signature
public String id {get; set;}
Property Value
Type: String
name
Get the name of the catalog.
Signature
public String name {get; set;}
Property Value
Type: String
numberOfCategories
Get the number of categories in the catalog.
Signature
public Integer numberOfCategories {get; set;}
Property Value
Type: Integer
status
Get the status of the catalog.
Signature
public String status {get; set;}
462
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 477 =====

Property Value
Type: String
ConfigRuleResult Class
Contains the results of configuration rule evaluation, including message rules, product recommendation rules, and visibility rules that
are applied during product configuration.
Namespace
runtime_industries_cpq on page 433
ConfigRuleResult Constructor
Learn more about the constructor that's available with the ConfigRuleResult class.
ConfigRuleResult Properties
Contains properties to store configuration rule evaluation results.
ConfigRuleResult Constructor
Learn more about the constructor that's available with the ConfigRuleResult class.
The ConfigRuleResult  class includes this constructor.
ConfigRuleResult(transactionContextId, messageRules, productRecommendationRules, visibilityRules, errors)
Constructor to create a ConfigRuleResult instance with configuration rule evaluation results.
ConfigRuleResult(transactionContextId, messageRules, productRecommendationRules,
visibilityRules, errors)
Constructor to create a ConfigRuleResult instance with configuration rule evaluation results.
Signature
public ConfigRuleResult(String transactionContextId,
List<runtime_industries_cpq.MessageRule> messageRules,
List<runtime_industries_cpq.ProductRecommendationRule> productRecommendationRules,
List<runtime_industries_cpq.VisibilityRule> visibilityRules, List<String> errors)
Parameters
transactionContextId
Type: String
The ID of the transaction context for this configuration rule evaluation.
messageRules
Type: List<runtime_industries_cpq.MessageRule>
List of message rules that were evaluated during configuration.
463
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 478 =====

productRecommendationRules
Type: List<runtime_industries_cpq.ProductRecommendationRule>
List of product recommendation rules that were evaluated during configuration.
visibilityRules
Type: List<runtime_industries_cpq.VisibilityRule>
List of visibility rules that were evaluated during configuration.
errors
Type: List<String>
List of error messages from the configuration rule evaluation, if any.
ConfigRuleResult Properties
Contains properties to store configuration rule evaluation results.
The ConfigRuleResult  class includes these properties.
errors
Get the list of error messages.
messageRules
Get the list of messagerule.
productRecommendationRules
Get the list of productrecommendationrule.
transactionContextId
Get the ID of the transactioncontext.
visibilityRules
Get the list of visibilityrule.
errors
Get the list of error messages.
Signature
public List<String> errors {get; set;}
Property Value
Type: List<String>
messageRules
Get the list of messagerule.
Signature
public List<runtime_industries_cpq.MessageRule> messageRules {get; set;}
464
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 479 =====

Property Value
Type: List<runtime_industries_cpq.MessageRule on page 487>
productRecommendationRules
Get the list of productrecommendationrule.
Signature
public List<runtime_industries_cpq.ProductRecommendationRule>productRecommendationRules
{get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductRecommendationRule on page 541>
transactionContextId
Get the ID of the transactioncontext.
Signature
public String transactionContextId {get; set;}
Property Value
Type: String
visibilityRules
Get the list of visibilityrule.
Signature
public List<runtime_industries_cpq.VisibilityRule> visibilityRules {get; set;}
Property Value
Type: List<runtime_industries_cpq.VisibilityRule on page 573>
CategoryOutputRepresentation Class
Contains properties to store details of a category.
Namespace
runtime_industries_cpq on page 433
CategoryOutputRepresentation Properties
Learn more about the properties available with the CategoryOutputRepresentation class.
465
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 480 =====

CategoryOutputRepresentation Properties
Learn more about the properties available with the CategoryOutputRepresentation class.
The CategoryOutputRepresentation  class includes these properties.
catalogId
Get the ID of the catalog that the category is associated with.
description
Get the description of a catalog.
hasSubCategories
Indicates whether the subcategories are available (true) or not (false).
id
Get the ID of the category.
isNavigational
Indicates whether the category node is navigational (true) or not (false).
name
Get the name of the category. If data translation is set up and specified in the org, the translated name is available.
parentCategoryId
Get the ID of the parent category.
qualificationContext
Get the context details of a user, which are used for qualification rules.
sortOrder
Get the display order of the product category relative to the siblings with the same parent category.
childCategories
Get the list of childcategorie.
catalogId
Get the ID of the catalog that the category is associated with.
Signature
public String catalogId {get; set;}
Property Value
Type: String
description
Get the description of a catalog.
Signature
public String description {get; set;}
466
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 481 =====

Property Value
Type: String
hasSubCategories
Indicates whether the subcategories are available (true) or not (false).
Signature
public Boolean hasSubCategories {get; set;}
Property Value
Type: Boolean
id
Get the ID of the category.
Signature
public String id {get; set;}
Property Value
Type: String
isNavigational
Indicates whether the category node is navigational (true) or not (false).
Signature
public Boolean isNavigational {get; set;}
Property Value
Type: Boolean
name
Get the name of the category. If data translation is set up and specified in the org, the translated name is available.
Signature
public String name {get; set;}
Property Value
Type: String
467
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 482 =====

parentCategoryId
Get the ID of the parent category.
Signature
public String parentCategoryId {get; set;}
Property Value
Type: String
qualificationContext
Get the context details of a user, which are used for qualification rules.
Signature
public runtime_industries_cpq.QualificationContextOutputRepresentation
qualificationContext {get; set;}
Property Value
Type: runtime_industries_cpq.QualificationContextOutputRepresentation on page 557
sortOrder
Get the display order of the product category relative to the siblings with the same parent category.
Signature
public Integer sortOrder {get; set;}
Property Value
Type: Integer
childCategories
Get the list of childcategorie.
Signature
public List<runtime_industries_cpq.CategoryOutputRepresentation> childCategories {get;
set;}
Property Value
Type: List<runtime_industries_cpq.CategoryOutputRepresentation on page 465>
468
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 483 =====

ContextDataInput Class
Get details of a context.
Namespace
runtime_industries_cpq on page 433
ContextDataInput Properties
Learn more about the properties available with the ContextDataInput class.
ContextDataInput Properties
Learn more about the properties available with the ContextDataInput class.
The ContextDataInput  class includes these properties.
nodeData
Get details of the node.
nodeName
Get the name of the node.
nodeData
Get details of the node.
Signature
public Map<String,ANY> nodeData {get; set;}
Property Value
Type: Map<String,ANY>
nodeName
Get the name of the node.
Signature
public String nodeName {get; set;}
Property Value
Type: String
FacetValueRepresentation Class
Get details of the facet values that are found in the search result.
469
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 484 =====

Namespace
runtime_industries_cpq on page 433
FacetValueRepresentation Properties
Learn more about the properties available with the FacetValueRepresentation class.
FacetValueRepresentation Properties
Learn more about the properties available with the FacetValueRepresentation class.
The FacetValueRepresentation  class includes these properties.
displayName
Get the display name of the facet value.
nameOrId
Get the name or ID of the facet. Reserved for internal use.
displayName
Get the display name of the facet value.
Signature
public String displayName {get; set;}
Property Value
Type: String
nameOrId
Get the name or ID of the facet. Reserved for internal use.
Signature
public String nameOrId {get; set;}
Property Value
Type: String
Filter Class
Contains the criteria property to store the details of a filter criteria, which is used to filter records.
Namespace
runtime_industries_cpq on page 433
470
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 485 =====

Filter Properties
Learn more about the properties available with the Filter class.
Filter Properties
Learn more about the properties available with the Filter class.
The Filter  class includes these properties.
criteria
Get the filter criteria to filter the records.
criteria
Get the filter criteria to filter the records.
Signature
public List<runtime_industries_cpq.FilterCriteriaInputRepresentation> criteria {get;
set;}
Property Value
Type: List<runtime_industries_cpq.FilterCriteriaInputRepresentation on page 471>
FilterCriteriaInputRepresentation Class
Contains properties to store criteria details to filter records based on supported properties.
Namespace
runtime_industries_cpq on page 433
FilterCriteriaInputRepresentation Properties
Learn more about the properties available with the FilterCriteriaInputRepresentation class.
FilterCriteriaInputRepresentation Properties
Learn more about the properties available with the FilterCriteriaInputRepresentation class.
The FilterCriteriaInputRepresentation  class includes these properties.
attributeType
Get details of the search attribute type of the facet for a faceted search.
operator
Get the operator that's used for the filter criteria.
property
Get the property name to use in the filter, which must be the same as the object field. The supported property is name.
471
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 486 =====

value
Get the value for the filter criteria.
attributeType
Get details of the search attribute type of the facet for a faceted search.
Signature
public String attributeType {get; set;}
Property Value
Type: String
Usage
Valid values are:
• ProductStandard
• ProductCustom
• ProductDynamicAttribute
• ProductAttributeStandard
• ProductAttributeCustom
operator
Get the operator that's used for the filter criteria.
Signature
public String operator {get; set;}
Property Value
Type: String
Usage
The supported operators are:
• eq
• in
• contains
• gt—Specifies a greater than criteria. Available from API version 63.0 and later for Number, Date, and Datetime data types only.
• lt—Specifies a less than criteria. Available from API version 63.0 and later for Number, Date, and Datetime data types only.
• gte—Specifies a greater than or equal to criteria. Available from API version 63.0 and later for Number, Date, and Datetime data
types only.
472
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 487 =====

• lte—Specifies a less than or equal to criteria. Available from API version 63.0 and later for Number, Date, and Datetime data types
only.
property
Get the property name to use in the filter, which must be the same as the object field. The supported property is name.
Signature
public String property {get; set;}
Property Value
Type: String
value
Get the value for the filter criteria.
Signature
public String value {get; set;}
Property Value
Type: String
FilterInputRepresentation Class
Contains the filter property to filters records based on supported criteria.
Namespace
runtime_industries_cpq on page 433
FilterInputRepresentation Properties
Learn more about the available properties with the FilterInputRepresentation class.
FilterInputRepresentation Properties
Learn more about the available properties with the FilterInputRepresentation class.
The FilterInputRepresentation  class includes these properties.
filter
Filters records based on supported criteria. The supported property is name.
filter
Filters records based on supported criteria. The supported property is name.
473
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 488 =====

Signature
public runtime_industries_cpq.Filter filter {get; set;}
Property Value
Type: runtime_industries_cpq.Filter on page 470
Usage
The supported operators are:
• eq
• in
• contains—This value isn't applicable if the Use Indexed Data For Product Listing and Search toggle from the Product
Discovery Settings page from Setup is enabled.
If multiple criteria are specified, then the resultant criteria are combined by using the and  operator.
GuidedSelectionRepresentation Class
Contains properties to represent a product in a guided selection flow. This class is used in Product Discovery to provide structured product
information during guided product selection processes.
Namespace
runtime_industries_cpq on page 433
GuidedSelectionRepresentation Properties
Contains properties to include details of a product in a guided selection flow.
GuidedSelectionRepresentation Properties
Contains properties to include details of a product in a guided selection flow.
The GuidedSelectionRepresentation  class includes these properties.
additionalFields
Get the list of additionalfield.
attributeCategories
Get the list of attributecategorie.
availabilityDate
Get the availability date.
catalogs
Get the list of catalog.
categories
Get the list of categorie.
childProducts
Get the list of childproduct.
474
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 489 =====

configureDuringSale
Get the configureduringsale value.
description
Get the description of the guidedselection.
discontinuedDate
Get the discontinued date.
displayUrl
Get the displayurl value.
endOfLifeDate
Get the endoflife date.
id
Get the ID of the guidedselection.
isActive
Indicates whether the item is active.
isAssetizable
Indicates whether assetizable is true or false.
isComponentRequired
Indicates whether componentrequired is true or false.
isDefaultComponent
Indicates whether defaultcomponent is true or false.
isQuantityEditable
Indicates whether quantityeditable is true or false.
isSoldOnlyWithOtherProds
Indicates whether soldonlywithotherprods is true or false.
name
Get the name of the guidedselection.
nodeType
Get the nodetype value.
prices
Get the list of price.
productClassification
Get the productclassification value.
productCode
Get the productcode value.
productComponentGroups
Get the list of productcomponentgroup.
productInformation
Get the productinformation value.
productPricingInformation
Get the productpricinginformation value.
475
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 490 =====

productQuantity
Get the productquantity value.
productRelatedComponent
Get the productrelatedcomponent value.
productSellingModelOptions
Get the list of productsellingmodeloption.
productSpecificationType
Get the productspecificationtype value.
productType
Get the producttype value.
qualificationContext
Get the qualificationcontext value.
status
Get the status of the guidedselection.
unitOfMeasure
Get the unitofmeasure value.
additionalFields
Get the list of additionalfield.
Signature
public List<runtime_industries_cpq.AdditionalFieldsWrapper> additionalFields {get;
set;}
Property Value
Type: List<runtime_industries_cpq.AdditionalFieldsWrapper>
attributeCategories
Get the list of attributecategorie.
Signature
public List<runtime_industries_cpq.AttributeCategoryOutputRepresentation>
attributeCategories {get; set;}
Property Value
Type: List<runtime_industries_cpq.AttributeCategoryOutputRepresentation on page 439>
availabilityDate
Get the availability date.
476
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 491 =====

Signature
public Datetime availabilityDate {get; set;}
Property Value
Type: Datetime
catalogs
Get the list of catalog.
Signature
public List<runtime_industries_cpq.CatalogOutputRepresentation> catalogs {get; set;}
Property Value
Type: List<runtime_industries_cpq.CatalogOutputRepresentation on page 459>
categories
Get the list of categorie.
Signature
public List<runtime_industries_cpq.CategoryOutputRepresentation>categories {get; set;}
Property Value
Type: List<runtime_industries_cpq.CategoryOutputRepresentation on page 465>
childProducts
Get the list of childproduct.
Signature
public List<runtime_industries_cpq.ProductListRepresentation>childProducts {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductListRepresentation on page 518>
configureDuringSale
Get the configureduringsale value.
Signature
public String configureDuringSale {get; set;}
477
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 492 =====

Property Value
Type: String
description
Get the description of the guidedselection.
Signature
public String description {get; set;}
Property Value
Type: String
discontinuedDate
Get the discontinued date.
Signature
public Datetime discontinuedDate {get; set;}
Property Value
Type: Datetime
displayUrl
Get the displayurl value.
Signature
public String displayUrl {get; set;}
Property Value
Type: String
endOfLifeDate
Get the endoflife date.
Signature
public Datetime endOfLifeDate {get; set;}
Property Value
Type: Datetime
478
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 493 =====

id
Get the ID of the guidedselection.
Signature
public String id {get; set;}
Property Value
Type: String
isActive
Indicates whether the item is active.
Signature
public Boolean isActive {get; set;}
Property Value
Type: Boolean
isAssetizable
Indicates whether assetizable is true or false.
Signature
public Boolean isAssetizable {get; set;}
Property Value
Type: Boolean
isComponentRequired
Indicates whether componentrequired is true or false.
Signature
public Boolean isComponentRequired {get; set;}
Property Value
Type: Boolean
isDefaultComponent
Indicates whether defaultcomponent is true or false.
479
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 494 =====

Signature
public Boolean isDefaultComponent {get; set;}
Property Value
Type: Boolean
isQuantityEditable
Indicates whether quantityeditable is true or false.
Signature
public Boolean isQuantityEditable {get; set;}
Property Value
Type: Boolean
isSoldOnlyWithOtherProds
Indicates whether soldonlywithotherprods is true or false.
Signature
public Boolean isSoldOnlyWithOtherProds {get; set;}
Property Value
Type: Boolean
name
Get the name of the guidedselection.
Signature
public String name {get; set;}
Property Value
Type: String
nodeType
Get the nodetype value.
Signature
public String nodeType {get; set;}
480
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 495 =====

Property Value
Type: String
prices
Get the list of price.
Signature
public List<runtime_industries_cpq.ProductPricesOutputRepresentation> prices {get;
set;}
Property Value
Type: List<runtime_industries_cpq.ProductPricesOutputRepresentation on page 537>
productClassification
Get the productclassification value.
Signature
public runtime_industries_cpq.ProductClassificationOutputRepresentation
productClassification {get; set;}
Property Value
Type: runtime_industries_cpq.ProductClassificationOutputRepresentation on page 499
productCode
Get the productcode value.
Signature
public String productCode {get; set;}
Property Value
Type: String
productComponentGroups
Get the list of productcomponentgroup.
Signature
public List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation>
productComponentGroups {get; set;}
481
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 496 =====

Property Value
Type: List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation on page 500>
productInformation
Get the productinformation value.
Signature
public String productInformation {get; set;}
Property Value
Type: String
productPricingInformation
Get the productpricinginformation value.
Signature
public String productPricingInformation {get; set;}
Property Value
Type: String
productQuantity
Get the productquantity value.
Signature
public runtime_industries_cpq.ProductQuantityOutputRepresentationproductQuantity {get;
set;}
Property Value
Type: runtime_industries_cpq.ProductQuantityOutputRepresentation on page 540
productRelatedComponent
Get the productrelatedcomponent value.
Signature
public ConnectApi.CPQProductRelatedComponentOutputRepresentationproductRelatedComponent
{get; set;}
482
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 497 =====

Property Value
Type: ConnectApi.CPQProductRelatedComponentOutputRepresentation
productSellingModelOptions
Get the list of productsellingmodeloption.
Signature
public List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation>
productSellingModelOptions {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation on page 550>
productSpecificationType
Get the productspecificationtype value.
Signature
public runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation
productSpecificationType {get; set;}
Property Value
Type: runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation on page 555
productType
Get the producttype value.
Signature
public String productType {get; set;}
Property Value
Type: String
qualificationContext
Get the qualificationcontext value.
Signature
public runtime_industries_cpq.QualificationContextOutputRepresentation
qualificationContext {get; set;}
483
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 498 =====

Property Value
Type: runtime_industries_cpq.QualificationContextOutputRepresentation on page 557
status
Get the status of the guidedselection.
Signature
public String status {get; set;}
Property Value
Type: String
unitOfMeasure
Get the unitofmeasure value.
Signature
public runtime_industries_cpq.UnitOfMeasureOutputRepresentation unitOfMeasure {get;
set;}
Property Value
Type: runtime_industries_cpq.UnitOfMeasureOutputRepresentation on page 571
GuidedSelectionSearchTerm Class
Represents a search term used in guided product selection. Contains the search term text and associated tags for filtering and searching
products in Product Discovery.
Namespace
runtime_industries_cpq on page 433
GuidedSelectionSearchTerm Constructor
Learn more about the constructors that are available with the GuidedSelectionSearchTerm class.
GuidedSelectionSearchTerm Properties
Contains properties to include search term details for guided product selection.
GuidedSelectionSearchTerm Constructor
Learn more about the constructors that are available with the GuidedSelectionSearchTerm class.
The GuidedSelectionSearchTerm  class includes these constructors.
484
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 499 =====

GuidedSelectionSearchTerm(apexObj)
Constructor to create a GuidedSelectionSearchTerm instance from a ConnectApi CPQGuidedSelectionSearchTermOutputRepresentation
object.
GuidedSelectionSearchTerm()
Default constructor to create an empty GuidedSelectionSearchTerm instance.
GuidedSelectionSearchTerm(apexObj)
Constructor to create a GuidedSelectionSearchTerm instance from a ConnectApi CPQGuidedSelectionSearchTermOutputRepresentation
object.
Signature
public
GuidedSelectionSearchTerm(ConnectApi.CPQGuidedSelectionSearchTermOutputRepresentation
apexObj)
Parameters
apexObj
Type: ConnectApi.CPQGuidedSelectionSearchTermOutputRepresentation
The ConnectApi guided selection search term representation object to convert to GuidedSelectionSearchTerm.
GuidedSelectionSearchTerm()
Default constructor to create an empty GuidedSelectionSearchTerm instance.
Signature
public GuidedSelectionSearchTerm()
GuidedSelectionSearchTerm Properties
Contains properties to include search term details for guided product selection.
The GuidedSelectionSearchTerm  class includes these properties.
tags
Get the list of tags.
term
Get the term value.
tags
Get the list of tags.
Signature
public List<String> tags {get; set;}
485
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 500 =====

Property Value
Type: List<String>
term
Get the term value.
Signature
public String term {get; set;}
Property Value
Type: String
GuidedSelectionSearchTermList Class
Contains a list of search terms used in guided product selection. This class is used to pass multiple search terms for filtering and searching
products in Product Discovery.
Namespace
runtime_industries_cpq on page 433
GuidedSelectionSearchTermList Constructor
Learn more about the constructor that's available with the GuidedSelectionSearchTermList class.
GuidedSelectionSearchTermList Properties
Contains properties to include a list of search terms for guided product selection.
GuidedSelectionSearchTermList Constructor
Learn more about the constructor that's available with the GuidedSelectionSearchTermList class.
The GuidedSelectionSearchTermList  class includes this constructor.
GuidedSelectionSearchTermList()
Default constructor to create an empty GuidedSelectionSearchTermList instance.
GuidedSelectionSearchTermList()
Default constructor to create an empty GuidedSelectionSearchTermList instance.
Signature
public GuidedSelectionSearchTermList()
GuidedSelectionSearchTermList Properties
Contains properties to include a list of search terms for guided product selection.
486
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 501 =====

The GuidedSelectionSearchTermList  class includes these properties.
searchTerms
Get the list of searchterm.
searchTerms
Get the list of searchterm.
Signature
public List<runtime_industries_cpq.GuidedSelectionSearchTerm> searchTerms {get; set;}
Property Value
Type: List<runtime_industries_cpq.GuidedSelectionSearchTerm on page 484>
MessageRule Class
Represents a message rule that is evaluated during product configuration. Message rules display informational, warning, or error messages
to users based on configuration conditions.
Namespace
runtime_industries_cpq on page 433
MessageRule Constructor
Learn more about the constructor that's available with the MessageRule class.
MessageRule Properties
Contains properties to store message rule details from configuration rule evaluation.
MessageRule Constructor
Learn more about the constructor that's available with the MessageRule class.
The MessageRule  class includes this constructor.
MessageRule(stiId, severity, messages)
Constructor to create a MessageRule instance with the specified STI ID, severity, and messages.
MessageRule(stiId, severity, messages)
Constructor to create a MessageRule instance with the specified STI ID, severity, and messages.
Signature
public MessageRule(String stiId, String severity, List<String> messages)
487
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 502 =====

Parameters
stiId
Type: String
The ID of the Sales Transaction Item (STI) associated with this message rule.
severity
Type: String
The severity level of the message (for example, Error, Warning, or Info).
messages
Type: List<String>
List of message strings to display to the user.
MessageRule Properties
Contains properties to store message rule details from configuration rule evaluation.
The MessageRule  class includes these properties.
messages
Get the list of messages.
severity
Get the severity value.
stiId
Get the ID of the sti.
messages
Get the list of messages.
Signature
public List<String> messages {get; set;}
Property Value
Type: List<String>
severity
Get the severity value.
Signature
public String severity {get; set;}
Property Value
Type: String
488
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 503 =====

stiId
Get the ID of the sti.
Signature
public String stiId {get; set;}
Property Value
Type: String
PricingModelOutputRepresentation Class
Contains details of a pricing model in a product configuration.
Namespace
runtime_industries_cpq on page 433
PricingModelOutputRepresentation Properties
Learn more about the properties available with the PricingModelOutputRepresentation class.
PricingModelOutputRepresentation Properties
Learn more about the properties available with the PricingModelOutputRepresentation class.
The PricingModelOutputRepresentation  class includes these properties.
frequency
Contains frequency details of the pricing model.
id
Contains the ID of the pricing model.
name
Contains the name of the pricing model.
occurrence
Contains details about the occurrence of the pricing model.
pricingModelType
Contains the type of the pricing model.
unitOfMeasure
Contains details about the unit of measure for the pricing model.
frequency
Contains frequency details of the pricing model.
489
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 504 =====

Signature
public String frequency {get; set;}
Property Value
Type: String
id
Contains the ID of the pricing model.
Signature
public String id {get; set;}
Property Value
Type: String
name
Contains the name of the pricing model.
Signature
public String name {get; set;}
Property Value
Type: String
occurrence
Contains details about the occurrence of the pricing model.
Signature
public Integer occurrence {get; set;}
Property Value
Type: Integer
pricingModelType
Contains the type of the pricing model.
Signature
public String pricingModelType {get; set;}
490
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 505 =====

Property Value
Type: String
unitOfMeasure
Contains details about the unit of measure for the pricing model.
Signature
public String unitOfMeasure {get; set;}
Property Value
Type: String
ProductAttributeOutputRepresentation Class
Contains details about the attribute in a product configuration.
Namespace
runtime_industries_cpq on page 433
ProductAttributeOutputRepresentation Properties
Learn more about the properties available with the ProductAttributeOutputRepresentation class.
ProductAttributeOutputRepresentation Properties
Learn more about the properties available with the ProductAttributeOutputRepresentation class.
The ProductAttributeOutputRepresentation  class includes these properties.
additionalFields
Get the key-value pairs of additional standard or custom fields and their values for the product attribute.
attributeCategoryId
Get the ID of the attribute category.
attributeNameOverride
Get the name override value of the attribute.
attributePickList
Get the picklist values of the attribute.
code
Get the code of the attribute.
dataType
Get the data type of the attribute.
defaultHelpText
Get the default help text value of the attribute.
491
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 506 =====

defaultValue
Get the default value of the attribute.
description
Get the description of the attribute.
developerName
Get the developer name of the product attribute.
displayTypeOverride
Get the override value of the display type of the attribute.
hidden
Indicates whether the attribute is hidden (true) or not (false).
id
Get the ID of the attribute.
isCloneable
Indicates whether the attribute is cloneable (true) or not (false).
isConfigurable
Indicates whether the attribute is configurable (true) or not (false).
isEncrypted
Indicates whether the attribute is encrypted (true) or not (false).
isPriceImpacting
Indicates whether this is a price impacting attribute (true) or not (false).
isReadOnly
Indicates whether the attribute is read-only (true) or not (false).
isRequired
Indicates whether the attribute is required (true) or not (false).
label
Get the label of the attribute.
maximumValue
Get the maximum value for the product attribute.
minimumValue
Get the minimum value for the product attribute.
name
Get the name of the attribute.
sequence
Get the sequence values of the attribute.
status
Get the status of the attribute.
stepValue
Get the step value for the attribute.
unitOfMeasure
Get details about the unit of measure associated with an attribute.
492
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 507 =====

userValue
Get the user value of the attribute.
valueDescription
Get the value description of the attribute.
additionalFields
Get the key-value pairs of additional standard or custom fields and their values for the product attribute.
Signature
public List<runtime_industries_cpq.AdditionalFieldsWrapper> additionalFields {get;
set;}
Property Value
Type: List<runtime_industries_cpq.AdditionalFieldsWrapper>
attributeCategoryId
Get the ID of the attribute category.
Signature
public String attributeCategoryId {get; set;}
Property Value
Type: String
attributeNameOverride
Get the name override value of the attribute.
Signature
public String attributeNameOverride {get; set;}
Property Value
Type: String
attributePickList
Get the picklist values of the attribute.
Signature
public runtime_industries_cpq.AttributePickListOutputRepresentation attributePickList
{get; set;}
493
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 508 =====

Property Value
Type: runtime_industries_cpq.AttributePickListOutputRepresentation on page 442
code
Get the code of the attribute.
Signature
public String code {get; set;}
Property Value
Type: String
dataType
Get the data type of the attribute.
Signature
public String dataType {get; set;}
Property Value
Type: String
defaultHelpText
Get the default help text value of the attribute.
Signature
public String defaultHelpText {get; set;}
Property Value
Type: String
defaultValue
Get the default value of the attribute.
Signature
public String defaultValue {get; set;}
Property Value
Type: String
494
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 509 =====

description
Get the description of the attribute.
Signature
public String description {get; set;}
Property Value
Type: String
developerName
Get the developer name of the product attribute.
Signature
public String developerName {get; set;}
Property Value
Type: String
displayTypeOverride
Get the override value of the display type of the attribute.
Signature
public String displayTypeOverride {get; set;}
Property Value
Type: String
hidden
Indicates whether the attribute is hidden (true) or not (false).
Signature
public Boolean hidden {get; set;}
Property Value
Type: Boolean
id
Get the ID of the attribute.
495
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 510 =====

Signature
public String id {get; set;}
Property Value
Type: String
isCloneable
Indicates whether the attribute is cloneable (true) or not (false).
Signature
public Boolean isCloneable {get; set;}
Property Value
Type: Boolean
isConfigurable
Indicates whether the attribute is configurable (true) or not (false).
Signature
public Boolean isConfigurable {get; set;}
Property Value
Type: Boolean
isEncrypted
Indicates whether the attribute is encrypted (true) or not (false).
Signature
public Boolean isEncrypted {get; set;}
Property Value
Type: Boolean
isPriceImpacting
Indicates whether this is a price impacting attribute (true) or not (false).
Signature
public Boolean isPriceImpacting {get; set;}
496
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 511 =====

Property Value
Type: Boolean
isReadOnly
Indicates whether the attribute is read-only (true) or not (false).
Signature
public Boolean isReadOnly {get; set;}
Property Value
Type: Boolean
isRequired
Indicates whether the attribute is required (true) or not (false).
Signature
public Boolean isRequired {get; set;}
Property Value
Type: Boolean
label
Get the label of the attribute.
Signature
public String label {get; set;}
Property Value
Type: String
maximumValue
Get the maximum value for the product attribute.
Signature
public String maximumValue {get; set;}
Property Value
Type: String
497
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 512 =====

minimumValue
Get the minimum value for the product attribute.
Signature
public String minimumValue {get; set;}
Property Value
Type: String
name
Get the name of the attribute.
Signature
public String name {get; set;}
Property Value
Type: String
sequence
Get the sequence values of the attribute.
Signature
public Integer sequence {get; set;}
Property Value
Type: Integer
status
Get the status of the attribute.
Signature
public String status {get; set;}
Property Value
Type: String
stepValue
Get the step value for the attribute.
498
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 513 =====

Signature
public String stepValue {get; set;}
Property Value
Type: String
unitOfMeasure
Get details about the unit of measure associated with an attribute.
Signature
public ConnectApi.UnitOfMeasureOutputRepresentation unitOfMeasure {get; set;}
Property Value
Type: ConnectApi.UnitOfMeasureOutputRepresentation
userValue
Get the user value of the attribute.
Signature
public String userValue {get; set;}
Property Value
Type: String
valueDescription
Get the value description of the attribute.
Signature
public String valueDescription {get; set;}
Property Value
Type: String
ProductClassificationOutputRepresentation Class
Get details of the product classification in a product configuration.
Namespace
runtime_industries_cpq on page 433
499
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 514 =====

ProductClassificationOutputRepresentation Properties
Learn more about the properties available with the ProductClassificationOutputRepresentation class.
ProductClassificationOutputRepresentation Properties
Learn more about the properties available with the ProductClassificationOutputRepresentation class.
The ProductClassificationOutputRepresentation  class includes these properties.
id
Get the ID of the product classification.
id
Get the ID of the product classification.
Signature
public String id {get; set;}
Property Value
Type: String
ProductComponentGroupOutputRepresentation Class
Get details of the product component group in a product classification.
Namespace
runtime_industries_cpq on page 433
ProductComponentGroupOutputRepresentation Properties
Learn more about the properties available with the ProductComponentGroupOutputRepresentation class.
ProductComponentGroupOutputRepresentation Properties
Learn more about the properties available with the ProductComponentGroupOutputRepresentation class.
The ProductComponentGroupOutputRepresentation  class includes these properties.
childGroups
Get the child groups associated with a product component group.
classifications
Get the list of classifications for the product component group.
code
Get the code of the product component group.
500
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 515 =====

components
Get the details of components within the product component group.
description
Get the description of the product component group.
id
Get the ID of the product component group.
name
Get the name of the product component group.
parentGroupId
Get the ID of the parent group.
parentProductId
Get the parent Product2 ID of the product component group.
sequence
Get the sequence of the product component group.
childGroups
Get the child groups associated with a product component group.
Signature
public List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation>childGroups
{get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation on page 500>
classifications
Get the list of classifications for the product component group.
Signature
public List<runtime_industries_cpq.ProductClassificationOutputRepresentation>
classifications {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductClassificationOutputRepresentation on page 499>
code
Get the code of the product component group.
Signature
public String code {get; set;}
501
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 516 =====

Property Value
Type: String
components
Get the details of components within the product component group.
Signature
public List<runtime_industries_cpq.ProductDetailsRepresentation>components {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductDetailsRepresentation on page 507>
description
Get the description of the product component group.
Signature
public String description {get; set;}
Property Value
Type: String
id
Get the ID of the product component group.
Signature
public String id {get; set;}
Property Value
Type: String
name
Get the name of the product component group.
Signature
public String name {get; set;}
Property Value
Type: String
502
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 517 =====

parentGroupId
Get the ID of the parent group.
Signature
public String parentGroupId {get; set;}
Property Value
Type: String
parentProductId
Get the parent Product2 ID of the product component group.
Signature
public String parentProductId {get; set;}
Property Value
Type: String
sequence
Get the sequence of the product component group.
Signature
public Integer sequence {get; set;}
Property Value
Type: Integer
ProductComponentGroupRepresentation Class
Represents a product component group used in bulk product operations. This class is similar to
ProductComponentGroupOutputRepresentation but is used specifically for bulk product detail representations where components are
represented as BulkProductDetailsRepresentation objects.
Namespace
runtime_industries_cpq on page 433
ProductComponentGroupRepresentation Constructor
Learn more about the constructor that's available with the ProductComponentGroupRepresentation class.
ProductComponentGroupRepresentation Properties
Contains properties to include details of a product component group used in bulk operations.
503
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 518 =====

ProductComponentGroupRepresentation Constructor
Learn more about the constructor that's available with the ProductComponentGroupRepresentation class.
The ProductComponentGroupRepresentation  class includes this constructor.
ProductComponentGroupRepresentation(apexObj)
Constructor to create a ProductComponentGroupRepresentation instance from a ConnectApi
CPQProductComponentGroupOutputRepresentation object.
ProductComponentGroupRepresentation(apexObj)
Constructor to create a ProductComponentGroupRepresentation instance from a ConnectApi
CPQProductComponentGroupOutputRepresentation object.
Signature
public
ProductComponentGroupRepresentation(ConnectApi.CPQProductComponentGroupOutputRepresentation
apexObj)
Parameters
apexObj
Type: ConnectApi.CPQProductComponentGroupOutputRepresentation
The ConnectApi product component group representation object to convert to ProductComponentGroupRepresentation.
ProductComponentGroupRepresentation Properties
Contains properties to include details of a product component group used in bulk operations.
The ProductComponentGroupRepresentation  class includes these properties.
childGroups
Get the list of childgroup.
classifications
Get the list of product classifications.
code
Get the code of the productcomponentgroup.
components
Get the list of component.
description
Get the description of the productcomponentgroup.
id
Get the ID of the productcomponentgroup.
name
Get the name of the productcomponentgroup.
504
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 519 =====

parentGroupId
Get the ID of the parentgroup.
parentProductId
Get the ID of the parentproduct.
sequence
Get the sequence value.
childGroups
Get the list of childgroup.
Signature
public List<runtime_industries_cpq.ProductComponentGroupRepresentation> childGroups
{get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductComponentGroupRepresentation on page 503>
classifications
Get the list of product classifications.
Signature
public List<runtime_industries_cpq.ProductClassificationOutputRepresentation>
classifications {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductClassificationOutputRepresentation on page 499>
code
Get the code of the productcomponentgroup.
Signature
public String code {get; set;}
Property Value
Type: String
components
Get the list of component.
505
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 520 =====

Signature
public List<runtime_industries_cpq.BulkProductDetailsRepresentation> components {get;
set;}
Property Value
Type: List<runtime_industries_cpq.BulkProductDetailsRepresentation on page 448>
description
Get the description of the productcomponentgroup.
Signature
public String description {get; set;}
Property Value
Type: String
id
Get the ID of the productcomponentgroup.
Signature
public String id {get; set;}
Property Value
Type: String
name
Get the name of the productcomponentgroup.
Signature
public String name {get; set;}
Property Value
Type: String
parentGroupId
Get the ID of the parentgroup.
Signature
public String parentGroupId {get; set;}
506
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 521 =====

Property Value
Type: String
parentProductId
Get the ID of the parentproduct.
Signature
public String parentProductId {get; set;}
Property Value
Type: String
sequence
Get the sequence value.
Signature
public Integer sequence {get; set;}
Property Value
Type: Integer
ProductDetailsRepresentation Class
Get the details of a product definition.
Namespace
runtime_industries_cpq on page 433
ProductDetailsRepresentation Constructor
Learn more about the constructor that's available with the ProductDetailsRepresentation class.
ProductDetailsRepresentation Properties
Learn more about the properties available with the ProductDetailsRepresentation class.
ProductDetailsRepresentation Constructor
Learn more about the constructor that's available with the ProductDetailsRepresentation class.
The ProductDetailsRepresentation  class includes this constructor.
ProductDetailsRepresentation()
Constructor to get the product details for a product definition.
507
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 522 =====

ProductDetailsRepresentation()
Constructor to get the product details for a product definition.
Signature
public ProductDetailsRepresentation()
ProductDetailsRepresentation Properties
Learn more about the properties available with the ProductDetailsRepresentation class.
The ProductDetailsRepresentation  includes these properties.
additionalFields
Get the key-value pair of additional standard or custom fields with their values.
attributeCategories
Get the list of categorized attributes related to the product.
attributes
Get the list of uncategorized attributes related to the product.
availabilityDate
Get the date when the part is used in the product or is made available for sale.
catalogs
Get the list of the associated catalogs returned with the Product List API (POST) response. The Product By ID API (GET) returns an
empty catalog list in the response. Returns the name and id values only.
childProducts
Get the hierarchy of the child products.
configureDuringSale
Determines whether to allow or prevent configuration when a bundle is sold.
description
Get the description of the product.
discontinuedDate
Get the date from when the part can’t be used in the product or sold.
displayUrl
Get the display image URL of the product.
endOfLifeDate
Get the date after which a product isn’t supported, ordered, or maintained.
id
Get the ID of the product.
isActive
Indicates whether the product is active (true) or not (false).
isAssetizable
Indicates whether the product instance remains a customer asset after it's purchased (true) or not (false).
508
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 523 =====

isComponentRequired
Indicates whether the product component is required (true) or not (false).
isDefaultComponent
Indicates whether the product component is the default component (true) or not (false).
isQuantityEditable
Indicates whether the product quantity is editable (true) or not (false).
isSoldOnlyWithOtherProds
Indicates whether the product can't be sold separately (true) or not (false).
name
Get the name of the product.
nodeType
Get the type of the node, such as a product or bundled product.
prices
Get the price details associated with the products.
productClassification
Get the details of the product classification that the product is based on.
productCode
Get the universal product code that's used to track the part that’s used in the product.
productComponentGroups
Get the logical grouping of the component products in a bundle and the group cardinality for ordering the product components.
productInformation
Get the details of a product.
productPricingInformation
Get the pricing details of a product.
productQuantity
Get the quantity of a product.
productRelatedComponent
Get the details of the related components of a product.
productSellingModelOptions
Get the details of the product selling model options.
productSpecificationType
Get the details of the product specification type.
productType
Get the product type.
qualificationContext
Get the context details of a user, which are used for qualification rules.
status
Get or set the status of the product, such as Active or Inactive.
unitOfMeasure
Get details about the unit of measure for a specific set of records.
509
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 524 =====

additionalFields
Get the key-value pair of additional standard or custom fields with their values.
Signature
public List<runtime_industries_cpq.AdditionalFieldsWrapper> additionalFields {get;
set;}
Property Value
Type: List<runtime_industries_cpq.AdditionalFieldsWrapper>
attributeCategories
Get the list of categorized attributes related to the product.
Signature
public List<runtime_industries_cpq.AttributeCategoryOutputRepresentation>
attributeCategories {get; set;}
Property Value
Type: List<runtime_industries_cpq.AttributeCategoryOutputRepresentation on page 439>
attributes
Get the list of uncategorized attributes related to the product.
Signature
public List<runtime_industries_cpq.ProductAttributeOutputRepresentation> attributes
{get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductAttributeOutputRepresentation on page 491>
availabilityDate
Get the date when the part is used in the product or is made available for sale.
Signature
public Datetime availabilityDate {get; set;}
Property Value
Type: Datetime
510
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 525 =====

catalogs
Get the list of the associated catalogs returned with the Product List API (POST) response. The Product By ID API (GET) returns an empty
catalog list in the response. Returns the name and id values only.
Signature
public List<runtime_industries_cpq.CatalogOutputRepresentation> catalogs {get; set;}
Property Value
Type: List<runtime_industries_cpq.CatalogOutputRepresentation on page 459>
childProducts
Get the hierarchy of the child products.
Signature
public List<runtime_industries_cpq.ProductDetailsRepresentation> childProducts {get;
set;}
Property Value
Type: List<runtime_industries_cpq.ProductDetailsRepresentation on page 507>
configureDuringSale
Determines whether to allow or prevent configuration when a bundle is sold.
Signature
public String configureDuringSale {get; set;}
Property Value
Type: String
description
Get the description of the product.
If data translation is set up and specified in the org, the translated description is available.
Signature
public String description {get; set;}
Property Value
Type: String
511
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 526 =====

discontinuedDate
Get the date from when the part can’t be used in the product or sold.
Signature
public Datetime discontinuedDate {get; set;}
Property Value
Type: Datetime
displayUrl
Get the display image URL of the product.
Signature
public String displayUrl {get; set;}
Property Value
Type: String
endOfLifeDate
Get the date after which a product isn’t supported, ordered, or maintained.
Signature
public Datetime endOfLifeDate {get; set;}
Property Value
Type: Datetime
id
Get the ID of the product.
Signature
public String id {get; set;}
Property Value
Type: String
isActive
Indicates whether the product is active (true) or not (false).
512
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 527 =====

Signature
public Boolean isActive {get; set;}
Property Value
Type: Boolean
isAssetizable
Indicates whether the product instance remains a customer asset after it's purchased (true) or not (false).
Signature
public Boolean isAssetizable {get; set;}
Property Value
Type: Boolean
isComponentRequired
Indicates whether the product component is required (true) or not (false).
Signature
public Boolean isComponentRequired {get; set;}
Property Value
Type: Boolean
isDefaultComponent
Indicates whether the product component is the default component (true) or not (false).
Signature
public Boolean isDefaultComponent {get; set;}
Property Value
Type: Boolean
isQuantityEditable
Indicates whether the product quantity is editable (true) or not (false).
Signature
public Boolean isQuantityEditable {get; set;}
513
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 528 =====

Property Value
Type: Boolean
isSoldOnlyWithOtherProds
Indicates whether the product can't be sold separately (true) or not (false).
Signature
public Boolean isSoldOnlyWithOtherProds {get; set;}
Property Value
Type: Boolean
name
Get the name of the product.
If data translation is set up and specified in the org, the translated name is available.
Signature
public String name {get; set;}
Property Value
Type: String
nodeType
Get the type of the node, such as a product or bundled product.
Signature
public String nodeType {get; set;}
Property Value
Type: String
prices
Get the price details associated with the products.
Signature
public List<runtime_industries_cpq.ProductPricesOutputRepresentation> prices {get;
set;}
514
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 529 =====

Property Value
Type: List<runtime_industries_cpq.ProductPricesOutputRepresentation on page 537>
productClassification
Get the details of the product classification that the product is based on.
Signature
public runtime_industries_cpq.ProductClassificationOutputRepresentation
productClassification {get; set;}
Property Value
Type: runtime_industries_cpq.ProductClassificationOutputRepresentation on page 499
productCode
Get the universal product code that's used to track the part that’s used in the product.
Signature
public String productCode {get; set;}
Property Value
Type: String
productComponentGroups
Get the logical grouping of the component products in a bundle and the group cardinality for ordering the product components.
Signature
public List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation>
productComponentGroups {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation on page 500>
productInformation
Get the details of a product.
Signature
public String productInformation {get; set;}
515
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 530 =====

Property Value
Type: String
productPricingInformation
Get the pricing details of a product.
Signature
public String productPricingInformation {get; set;}
Property Value
Type: String
productQuantity
Get the quantity of a product.
Signature
public runtime_industries_cpq.ProductQuantityOutputRepresentationproductQuantity {get;
set;}
Property Value
Type: runtime_industries_cpq.ProductQuantityOutputRepresentation on page 540
productRelatedComponent
Get the details of the related components of a product.
Signature
public ConnectApi.CPQProductRelatedComponentOutputRepresentationproductRelatedComponent
{get; set;}
Property Value
Type: ConnectApi.CPQProductRelatedComponentOutputRepresentation
productSellingModelOptions
Get the details of the product selling model options.
Signature
public List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation>
productSellingModelOptions {get; set;}
516
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 531 =====

Property Value
Type: List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation on page 550>
productSpecificationType
Get the details of the product specification type.
Signature
public runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation
productSpecificationType {get; set;}
Property Value
Type: runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation on page 555
productType
Get the product type.
Signature
public String productType {get; set;}
Property Value
Type: String
qualificationContext
Get the context details of a user, which are used for qualification rules.
Signature
public runtime_industries_cpq.QualificationContextOutputRepresentation
qualificationContext {get; set;}
Property Value
Type: runtime_industries_cpq.QualificationContextOutputRepresentation on page 557
status
Get or set the status of the product, such as Active or Inactive.
Signature
public String status {get; set;}
517
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 532 =====

Property Value
Type: String
unitOfMeasure
Get details about the unit of measure for a specific set of records.
Signature
public ConnectApi.UnitOfMeasureOutputRepresentation unitOfMeasure {get; set;}
Property Value
Type: ConnectApi.UnitOfMeasureOutputRepresentation
ProductListRepresentation Class
Get the list of retrieved products.
Namespace
runtime_industries_cpq on page 433
ProductListRepresentation Properties
Learn more about the properties available with the ProductListRepresentation class.
ProductListRepresentation Properties
Learn more about the properties available with the ProductListRepresentation class.
The following are properties for ProductListRepresentation.
additionalFields
Get the key-value pair of additional standard or custom fields with their values.
attributeCategories
Get the list of categorized attributes related to the product.
availabilityDate
Get the date when the part is used in the product or is made available for sale.
catalogs
Get the list of associated catalogs. Returns the name and id values only.
categories
Get the list of associated categories. Returns the name and id values only.
childProducts
Get the hierarchy of the child products.
configureDuringSale
Determines whether to allow or prevent configuration when a bundle is sold.
518
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 533 =====

description
Get the description of the product. If data translation is set up and specified in the org, the translated description is available.
discontinuedDate
Get the date from when the part can’t be used in the product or sold.
displayUrl
Get the display image URL of the product.
endOfLifeDate
Get the date after which a product isn’t supported, ordered, or maintained.
id
Get the ID of the product.
isActive
Indicates whether the product is active (true) or not (false).
isAssetizable
Indicates whether the product instance remains a customer asset after it's purchased (true) or not (false).
isComponentRequired
Indicates whether the product component is required (true) or not (false).
isDefaultComponent
Indicates whether the product component is the default component (true) or not (false).
isQuantityEditable
Indicates whether the product quantity is editable (true) or not (false).
isSoldOnlyWithOtherProds
Indicates whether the product can't be sold separately (true) or not (false).
name
Get the name of the product. If data translation is set up and specified in the org, the translated name is available.
nodeType
Get the type of the node, such as a product or bundled product.
prices
Get the price details associated with the products.
productClassification
Get the details of the product classification that the product is based on.
productCode
Get the universal product code that's used to track the part that’s used in the product.
productComponentGroups
Get the logical grouping of the component products in a bundle and group cardinality for ordering the product components.
productInformation
Get the details of a product.
productPricingInformation
Get the pricing details of a product.
productQuantity
Get the quantity of a product.
519
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 534 =====

productRelatedComponent
Get the details of the related components of a product.
productSellingModelOptions
Get the details of the product selling model options.
productSpecificationType
Get the details of the product specification type.
productType
Get the product type.
qualificationContext
Get the context details of a user, which are used for qualification rules.
status
Get or set the status of the product, such as Active or Inactive.
unitOfMeasure
Get details about the unit of measure for a specific set of records.
additionalFields
Get the key-value pair of additional standard or custom fields with their values.
Signature
public List<runtime_industries_cpq.AdditionalFieldsWrapper> additionalFields {get;
set;}
Property Value
Type: List<runtime_industries_cpq.AdditionalFieldsWrapper>
attributeCategories
Get the list of categorized attributes related to the product.
Signature
public List<runtime_industries_cpq.AttributeCategoryOutputRepresentation>
attributeCategories {get; set;}
Property Value
Type: List<runtime_industries_cpq.AttributeCategoryOutputRepresentation on page 439>
availabilityDate
Get the date when the part is used in the product or is made available for sale.
Signature
public Datetime availabilityDate {get; set;}
520
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 535 =====

Property Value
Type: Datetime
catalogs
Get the list of associated catalogs. Returns the name and id values only.
Signature
public List<runtime_industries_cpq.CatalogOutputRepresentation> catalogs {get; set;}
Property Value
Type: List<runtime_industries_cpq.CatalogOutputRepresentation on page 459>
categories
Get the list of associated categories. Returns the name and id values only.
Signature
public List<runtime_industries_cpq.CategoryOutputRepresentation>categories {get; set;}
Property Value
Type: List<runtime_industries_cpq.CategoryOutputRepresentation on page 465>
childProducts
Get the hierarchy of the child products.
Signature
public List<runtime_industries_cpq.ProductListRepresentation>childProducts {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductListRepresentation on page 518>
configureDuringSale
Determines whether to allow or prevent configuration when a bundle is sold.
Signature
public String configureDuringSale {get; set;}
Property Value
Type: String
521
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 536 =====

description
Get the description of the product. If data translation is set up and specified in the org, the translated description is available.
Signature
public String description {get; set;}
Property Value
Type: String
discontinuedDate
Get the date from when the part can’t be used in the product or sold.
Signature
public Datetime discontinuedDate {get; set;}
Property Value
Type: Datetime
displayUrl
Get the display image URL of the product.
Signature
public String displayUrl {get; set;}
Property Value
Type: String
endOfLifeDate
Get the date after which a product isn’t supported, ordered, or maintained.
Signature
public Datetime endOfLifeDate {get; set;}
Property Value
Type: Datetime
id
Get the ID of the product.
522
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 537 =====

Signature
public String id {get; set;}
Property Value
Type: String
isActive
Indicates whether the product is active (true) or not (false).
Signature
public Boolean isActive {get; set;}
Property Value
Type: Boolean
isAssetizable
Indicates whether the product instance remains a customer asset after it's purchased (true) or not (false).
Signature
public Boolean isAssetizable {get; set;}
Property Value
Type: Boolean
isComponentRequired
Indicates whether the product component is required (true) or not (false).
Signature
public Boolean isComponentRequired {get; set;}
Property Value
Type: Boolean
isDefaultComponent
Indicates whether the product component is the default component (true) or not (false).
Signature
public Boolean isDefaultComponent {get; set;}
523
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 538 =====

Property Value
Type: Boolean
isQuantityEditable
Indicates whether the product quantity is editable (true) or not (false).
Signature
public Boolean isQuantityEditable {get; set;}
Property Value
Type: Boolean
isSoldOnlyWithOtherProds
Indicates whether the product can't be sold separately (true) or not (false).
Signature
public Boolean isSoldOnlyWithOtherProds {get; set;}
Property Value
Type: Boolean
name
Get the name of the product. If data translation is set up and specified in the org, the translated name is available.
Signature
public String name {get; set;}
Property Value
Type: String
nodeType
Get the type of the node, such as a product or bundled product.
Signature
public String nodeType {get; set;}
Property Value
Type: String
524
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 539 =====

prices
Get the price details associated with the products.
Signature
public List<runtime_industries_cpq.ProductPricesOutputRepresentation> prices {get;
set;}
Property Value
Type: List<runtime_industries_cpq.ProductPricesOutputRepresentation on page 537>
productClassification
Get the details of the product classification that the product is based on.
Signature
public runtime_industries_cpq.ProductClassificationOutputRepresentation
productClassification {get; set;}
Property Value
Type: runtime_industries_cpq.ProductClassificationOutputRepresentation on page 499
productCode
Get the universal product code that's used to track the part that’s used in the product.
Signature
public String productCode {get; set;}
Property Value
Type: String
productComponentGroups
Get the logical grouping of the component products in a bundle and group cardinality for ordering the product components.
Signature
public List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation>
productComponentGroups {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation on page 500>
525
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 540 =====

productInformation
Get the details of a product.
Signature
public String productInformation {get; set;}
Property Value
Type: String
productPricingInformation
Get the pricing details of a product.
Signature
public String productPricingInformation {get; set;}
Property Value
Type: String
productQuantity
Get the quantity of a product.
Signature
public runtime_industries_cpq.ProductQuantityOutputRepresentationproductQuantity {get;
set;}
Property Value
Type: runtime_industries_cpq.ProductQuantityOutputRepresentation on page 540
productRelatedComponent
Get the details of the related components of a product.
Signature
public ConnectApi.CPQProductRelatedComponentOutputRepresentationproductRelatedComponent
{get; set;}
Property Value
Type: ConnectApi.CPQProductRelatedComponentOutputRepresentation
526
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 541 =====

productSellingModelOptions
Get the details of the product selling model options.
Signature
public List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation>
productSellingModelOptions {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation on page 550>
productSpecificationType
Get the details of the product specification type.
Signature
public runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation
productSpecificationType {get; set;}
Property Value
Type: runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation on page 555
productType
Get the product type.
Signature
public String productType {get; set;}
Property Value
Type: String
qualificationContext
Get the context details of a user, which are used for qualification rules.
Signature
public runtime_industries_cpq.QualificationContextOutputRepresentation
qualificationContext {get; set;}
Property Value
Type: runtime_industries_cpq.QualificationContextOutputRepresentation on page 557
527
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 542 =====

status
Get or set the status of the product, such as Active or Inactive.
Signature
public String status {get; set;}
Property Value
Type: String
unitOfMeasure
Get details about the unit of measure for a specific set of records.
Signature
public ConnectApi.UnitOfMeasureOutputRepresentation unitOfMeasure {get; set;}
Property Value
Type: ConnectApi.UnitOfMeasureOutputRepresentation
ProductOutputRepresentation Class
Get the details of a product definition.
Namespace
runtime_industries_cpq on page 433
ProductOutputRepresentation Properties
Learn more about the properties available with the ProductOutputRepresentation class.
ProductOutputRepresentation Properties
Learn more about the properties available with the ProductOutputRepresentation class.
The ProductOutputRepresentation  class includes these properties.
additionalFields
Get the key-value pair of additional standard or custom fields with their values.
attributeCategories
Get the list of categorized attributes related to the product.
availabilityDate
Get the date when the part is used in the product or is made available for sale.
catalogs
Get the list of associated catalogs. Returns the name and id values only.
528
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 543 =====

configureDuringSale
Determines whether to allow or prevent configuration when a bundle is sold.
description
Get the description of the product. If data translation is set up and specified in the org, the translated description is available.
discontinuedDate
Get the date from when the part can’t be used in the product or sold.
displayUrl
Get the display image URL of the product.
endOfLifeDate
Get the date after which a product isn’t supported, ordered, or maintained.
id
Get the ID of the product.
isActive
Indicates whether the product is active (true) or not (false).
isAssetizable
Indicates whether the product instance remains a customer asset after it's purchased (true) or not (false).
isComponentRequired
Indicates whether the product component is required (true) or not (false).
isDefaultComponent
Indicates whether the product component is the default component (true) or not (false).
isQuantityEditable
Indicates whether the product quantity is editable (true) or not (false).
isSoldOnlyWithOtherProds
Indicates whether the product can't be sold separately (true) or not (false).
name
Get the name of the product. If data translation is set up and specified in the org, the translated name is available.
nodeType
Get the type of the node, such as a product or bundled product.
productClassification
Get the details of the product classification that the product is based on.
productCode
Get the universal product code that's used to track the part that’s used in the product.
productComponentGroups
Get the logical grouping of the component products in a bundle and group cardinality for ordering the product components.
productInformation
Get the details of a product.
productPricingInformation
Get the pricing details of a product.
productQuantity
Get the quantity of a product.
529
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 544 =====

productRelatedComponent
Get the details of the related components of a product.
productSellingModelOptions
Get the details of the product selling model options.
productSpecificationType
Get the details of the product specification type.
productType
Get the product type.
qualificationContext
Get the context details of a user, which are used for qualification rules.
status
Get or set the status of the product, such as Active or Inactive.
additionalFields
Get the key-value pair of additional standard or custom fields with their values.
Signature
public List<runtime_industries_cpq.AdditionalFieldsWrapper> additionalFields {get;
set;}
Property Value
Type: List<runtime_industries_cpq.AdditionalFieldsWrapper>
attributeCategories
Get the list of categorized attributes related to the product.
Signature
public List<runtime_industries_cpq.AttributeCategoryOutputRepresentation>
attributeCategories {get; set;}
Property Value
Type: List<runtime_industries_cpq.AttributeCategoryOutputRepresentation on page 439>
availabilityDate
Get the date when the part is used in the product or is made available for sale.
Signature
public Datetime availabilityDate {get; set;}
530
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 545 =====

Property Value
Type: Datetime
catalogs
Get the list of associated catalogs. Returns the name and id values only.
Signature
public List<runtime_industries_cpq.CatalogOutputRepresentation> catalogs {get; set;}
Property Value
Type: List<runtime_industries_cpq.CatalogOutputRepresentation on page 459>
configureDuringSale
Determines whether to allow or prevent configuration when a bundle is sold.
Signature
public String configureDuringSale {get; set;}
Property Value
Type: String
description
Get the description of the product. If data translation is set up and specified in the org, the translated description is available.
Signature
public String description {get; set;}
Property Value
Type: String
discontinuedDate
Get the date from when the part can’t be used in the product or sold.
Signature
public Datetime discontinuedDate {get; set;}
Property Value
Type: Datetime
531
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 546 =====

displayUrl
Get the display image URL of the product.
Signature
public String displayUrl {get; set;}
Property Value
Type: String
endOfLifeDate
Get the date after which a product isn’t supported, ordered, or maintained.
Signature
public Datetime endOfLifeDate {get; set;}
Property Value
Type: Datetime
id
Get the ID of the product.
Signature
public String id {get; set;}
Property Value
Type: String
isActive
Indicates whether the product is active (true) or not (false).
Signature
public Boolean isActive {get; set;}
Property Value
Type: Boolean
isAssetizable
Indicates whether the product instance remains a customer asset after it's purchased (true) or not (false).
532
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 547 =====

Signature
public Boolean isAssetizable {get; set;}
Property Value
Type: Boolean
isComponentRequired
Indicates whether the product component is required (true) or not (false).
Signature
public Boolean isComponentRequired {get; set;}
Property Value
Type: Boolean
isDefaultComponent
Indicates whether the product component is the default component (true) or not (false).
Signature
public Boolean isDefaultComponent {get; set;}
Property Value
Type: Boolean
isQuantityEditable
Indicates whether the product quantity is editable (true) or not (false).
Signature
public Boolean isQuantityEditable {get; set;}
Property Value
Type: Boolean
isSoldOnlyWithOtherProds
Indicates whether the product can't be sold separately (true) or not (false).
Signature
public Boolean isSoldOnlyWithOtherProds {get; set;}
533
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 548 =====

Property Value
Type: Boolean
name
Get the name of the product. If data translation is set up and specified in the org, the translated name is available.
Signature
public String name {get; set;}
Property Value
Type: String
nodeType
Get the type of the node, such as a product or bundled product.
Signature
public String nodeType {get; set;}
Property Value
Type: String
productClassification
Get the details of the product classification that the product is based on.
Signature
public runtime_industries_cpq.ProductClassificationOutputRepresentation
productClassification {get; set;}
Property Value
Type: runtime_industries_cpq.ProductClassificationOutputRepresentation on page 499
productCode
Get the universal product code that's used to track the part that’s used in the product.
Signature
public String productCode {get; set;}
Property Value
Type: String
534
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 549 =====

productComponentGroups
Get the logical grouping of the component products in a bundle and group cardinality for ordering the product components.
Signature
public List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation>
productComponentGroups {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation on page 500>
productInformation
Get the details of a product.
Signature
public String productInformation {get; set;}
Property Value
Type: String
productPricingInformation
Get the pricing details of a product.
Signature
public String productPricingInformation {get; set;}
Property Value
Type: String
productQuantity
Get the quantity of a product.
Signature
public runtime_industries_cpq.ProductQuantityOutputRepresentationproductQuantity {get;
set;}
Property Value
Type: runtime_industries_cpq.ProductQuantityOutputRepresentation on page 540
535
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 550 =====

productRelatedComponent
Get the details of the related components of a product.
Signature
public ConnectApi.CPQProductRelatedComponentOutputRepresentationproductRelatedComponent
{get; set;}
Property Value
Type: ConnectApi.CPQProductRelatedComponentOutputRepresentation
productSellingModelOptions
Get the details of the product selling model options.
Signature
public List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation>
productSellingModelOptions {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation on page 550>
productSpecificationType
Get the details of the product specification type.
Signature
public runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation
productSpecificationType {get; set;}
Property Value
Type: runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation on page 555
productType
Get the product type.
Signature
public String productType {get; set;}
Property Value
Type: String
536
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 551 =====

qualificationContext
Get the context details of a user, which are used for qualification rules.
Signature
public runtime_industries_cpq.QualificationContextOutputRepresentation
qualificationContext {get; set;}
Property Value
Type: runtime_industries_cpq.QualificationContextOutputRepresentation on page 557
status
Get or set the status of the product, such as Active or Inactive.
Signature
public String status {get; set;}
Property Value
Type: String
ProductPricesOutputRepresentation Class
Get the price details of a product.
Namespace
runtime_industries_cpq on page 433
ProductPricesOutputRepresentation Properties
Learn more about the properties available with the ProductPricesOutputRepresentation class.
ProductPricesOutputRepresentation Properties
Learn more about the properties available with the ProductPricesOutputRepresentation class.
The following are properties for ProductPricesOutputRepresentation.
currencyIsoCode
Get or set the ISO currency code for the price.
effectiveFrom
Get or set the date and time when this price becomes effective.
effectiveTo
Get or set the date and time when this price expires.
537
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 552 =====

isDefault
Indicates whether this is the default price for the product.
isDerived
Indicates whether this price is derived from another price.
isSelected
Indicates whether this price is currently selected.
price
Get or set the price value for the product.
priceBookEntryId
Get or set the ID of the price book entry.
priceBookId
Get or set the ID of the price book containing this price.
pricingModel
Get or set the pricing model associated with this price.
currencyIsoCode
Get or set the ISO currency code for the price.
Signature
public String currencyIsoCode {get; set;}
Property Value
Type: String
effectiveFrom
Get or set the date and time when this price becomes effective.
Signature
public String effectiveFrom {get; set;}
Property Value
Type: String
effectiveTo
Get or set the date and time when this price expires.
Signature
public String effectiveTo {get; set;}
538
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 553 =====

Property Value
Type: String
isDefault
Indicates whether this is the default price for the product.
Signature
public Boolean isDefault {get; set;}
Property Value
Type: Boolean
isDerived
Indicates whether this price is derived from another price.
Signature
public Boolean isDerived {get; set;}
Property Value
Type: Boolean
isSelected
Indicates whether this price is currently selected.
Signature
public Boolean isSelected {get; set;}
Property Value
Type: Boolean
price
Get or set the price value for the product.
Signature
public Double price {get; set;}
Property Value
Type: Double
539
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 554 =====

priceBookEntryId
Get or set the ID of the price book entry.
Signature
public String priceBookEntryId {get; set;}
Property Value
Type: String
priceBookId
Get or set the ID of the price book containing this price.
Signature
public String priceBookId {get; set;}
Property Value
Type: String
pricingModel
Get or set the pricing model associated with this price.
Signature
public runtime_industries_cpq.PricingModelOutputRepresentationpricingModel {get; set;}
Property Value
Type: runtime_industries_cpq.PricingModelOutputRepresentation
ProductQuantityOutputRepresentation Class
Represents the quantity constraints and current quantity for a product in the product discovery context.
Namespace
runtime_industries_cpq on page 433
ProductQuantityOutputRepresentation Properties
ProductQuantityOutputRepresentation Properties
The following are properties for ProductQuantityOutputRepresentation.
540
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 555 =====

maxQuantity
Get or set the maximum quantity allowed for the product.
minQuantity
Get or set the minimum quantity allowed for the product.
quantity
Get or set the current quantity of the product.
maxQuantity
Get or set the maximum quantity allowed for the product.
Signature
public Double maxQuantity {get; set;}
Property Value
Type: Double
minQuantity
Get or set the minimum quantity allowed for the product.
Signature
public Double minQuantity {get; set;}
Property Value
Type: Double
quantity
Get or set the current quantity of the product.
Signature
public Double quantity {get; set;}
Property Value
Type: Double
ProductRecommendationRule Class
Represents a product recommendation rule that is evaluated during product configuration. Product recommendation rules suggest
additional products to users based on configuration conditions.
541
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 556 =====

Namespace
runtime_industries_cpq on page 433
ProductRecommendationRule Constructor
Learn more about the constructor that's available with the ProductRecommendationRule class.
ProductRecommendationRule Properties
Contains properties to store product recommendation rule details from configuration rule evaluation.
ProductRecommendationRule Constructor
Learn more about the constructor that's available with the ProductRecommendationRule class.
The ProductRecommendationRule  class includes this constructor.
ProductRecommendationRule(referenceId, productIds, message, recordType, target, scope)
Constructor to create a ProductRecommendationRule instance with the specified recommendation details.
ProductRecommendationRule(referenceId, productIds, message, recordType, target,
scope)
Constructor to create a ProductRecommendationRule instance with the specified recommendation details.
Signature
public ProductRecommendationRule(String referenceId, List<String> productIds, String
message, String recordType, String target, String scope)
Parameters
referenceId
Type: String
The reference ID of the product recommendation rule.
productIds
Type: List<String>
List of product IDs that are recommended.
message
Type: String
The message to display with the product recommendation.
recordType
Type: String
The record type associated with the recommendation.
target
Type: String
The target of the recommendation rule.
542
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 557 =====

scope
Type: String
The scope of the recommendation rule.
ProductRecommendationRule Properties
Contains properties to store product recommendation rule details from configuration rule evaluation.
The ProductRecommendationRule  class includes these properties.
message
Get the message value.
productIds
Get the list of productid.
recordType
Get the recordtype value.
referenceId
Get the ID of the reference.
scope
Get the scope value.
target
Get the target value.
message
Get the message value.
Signature
public String message {get; set;}
Property Value
Type: String
productIds
Get the list of productid.
Signature
public List<String> productIds {get; set;}
Property Value
Type: List<String>
543
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 558 =====

recordType
Get the recordtype value.
Signature
public String recordType {get; set;}
Property Value
Type: String
referenceId
Get the ID of the reference.
Signature
public String referenceId {get; set;}
Property Value
Type: String
scope
Get the scope value.
Signature
public String scope {get; set;}
Property Value
Type: String
target
Get the target value.
Signature
public String target {get; set;}
Property Value
Type: String
ProductRelatedComponentOutputRepresentation Class
Represents a related component product in a bundle or product relationship, including component configuration details such as quantity
constraints, required status, and relationship metadata.
544
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 559 =====

Namespace
runtime_industries_cpq on page 433
ProductRelatedComponentOutputRepresentation Properties
ProductRelatedComponentOutputRepresentation Properties
The following are properties for ProductRelatedComponentOutputRepresentation.
childProductId
Get or set the identifier of the child product in the relationship.
childSellingModelId
Get or set the identifier of the child product's selling model in the relationship.
doesBundlePriceIncludeChild
Get or set whether the bundle price includes the price of this child component.
id
Get or set the unique identifier of the product related component relationship.
isComponentRequired
Get or set whether this component is required in the bundle or product relationship.
isDefaultComponent
Get or set whether this component is selected by default in the bundle or product relationship.
isQuantityEditable
Get or set whether the quantity of this component can be edited.
maxQuantity
Get or set the maximum quantity allowed for this component.
minQuantity
Get or set the minimum quantity required for this component.
parentProductId
Get or set the identifier of the parent product in the relationship.
parentSellingModelId
Get or set the identifier of the parent product's selling model in the relationship.
productClassificationId
Get or set the identifier of the product classification for this component.
productComponentGroupId
Get or set the identifier of the product component group that this component belongs to.
productRelationshipTypeId
Get or set the identifier of the product relationship type that defines this relationship.
quantity
Get or set the current quantity of this component.
quantityScaleMethod
Get or set the method used to scale the quantity of this component, such as "PerUnit" or "PerBundle".
545
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 560 =====

sequence
Get or set the display sequence order of this component within the bundle or product relationship.
unitOfMeasure
Get or set the unit of measure for the quantity of this component.
isExcluded
Indicates whether excluded is true or false.
quoteVisibility
Get the quotevisibility value.
childProductId
Get or set the identifier of the child product in the relationship.
Signature
public String childProductId {get; set;}
Property Value
Type: String
childSellingModelId
Get or set the identifier of the child product's selling model in the relationship.
Signature
public String childSellingModelId {get; set;}
Property Value
Type: String
doesBundlePriceIncludeChild
Get or set whether the bundle price includes the price of this child component.
Signature
public Boolean doesBundlePriceIncludeChild {get; set;}
Property Value
Type: Boolean
id
Get or set the unique identifier of the product related component relationship.
546
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 561 =====

Signature
public String id {get; set;}
Property Value
Type: String
isComponentRequired
Get or set whether this component is required in the bundle or product relationship.
Signature
public Boolean isComponentRequired {get; set;}
Property Value
Type: Boolean
isDefaultComponent
Get or set whether this component is selected by default in the bundle or product relationship.
Signature
public Boolean isDefaultComponent {get; set;}
Property Value
Type: Boolean
isQuantityEditable
Get or set whether the quantity of this component can be edited.
Signature
public Boolean isQuantityEditable {get; set;}
Property Value
Type: Boolean
maxQuantity
Get or set the maximum quantity allowed for this component.
Signature
public Double maxQuantity {get; set;}
547
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 562 =====

Property Value
Type: Double
minQuantity
Get or set the minimum quantity required for this component.
Signature
public Double minQuantity {get; set;}
Property Value
Type: Double
parentProductId
Get or set the identifier of the parent product in the relationship.
Signature
public String parentProductId {get; set;}
Property Value
Type: String
parentSellingModelId
Get or set the identifier of the parent product's selling model in the relationship.
Signature
public String parentSellingModelId {get; set;}
Property Value
Type: String
productClassificationId
Get or set the identifier of the product classification for this component.
Signature
public String productClassificationId {get; set;}
Property Value
Type: String
548
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 563 =====

productComponentGroupId
Get or set the identifier of the product component group that this component belongs to.
Signature
public String productComponentGroupId {get; set;}
Property Value
Type: String
productRelationshipTypeId
Get or set the identifier of the product relationship type that defines this relationship.
Signature
public String productRelationshipTypeId {get; set;}
Property Value
Type: String
quantity
Get or set the current quantity of this component.
Signature
public Double quantity {get; set;}
Property Value
Type: Double
quantityScaleMethod
Get or set the method used to scale the quantity of this component, such as "PerUnit" or "PerBundle".
Signature
public String quantityScaleMethod {get; set;}
Property Value
Type: String
sequence
Get or set the display sequence order of this component within the bundle or product relationship.
549
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 564 =====

Signature
public Integer sequence {get; set;}
Property Value
Type: Integer
unitOfMeasure
Get or set the unit of measure for the quantity of this component.
Signature
public ConnectApi.UnitOfMeasureOutputRepresentation unitOfMeasure {get; set;}
Property Value
Type: ConnectApi.UnitOfMeasureOutputRepresentation
isExcluded
Indicates whether excluded is true or false.
Signature
public Boolean isExcluded {get; set;}
Property Value
Type: Boolean
quoteVisibility
Get the quotevisibility value.
Signature
public String quoteVisibility {get; set;}
Property Value
Type: String
ProductSellingModelOptionOutputRepresentation Class
Represents a selling model option available for a product, which defines how the product can be sold (such as subscription, one-time,
or usage-based).
Namespace
runtime_industries_cpq on page 433
550
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 565 =====

ProductSellingModelOptionOutputRepresentation Properties
Learn more about the properties available with the ProductSellingModelOptionOutputRepresentation class.
ProductSellingModelOptionOutputRepresentation Properties
Learn more about the properties available with the ProductSellingModelOptionOutputRepresentation class.
The ProductSellingModelOptionOutputRepresentation  class includes these properties.
id
Get or set the unique identifier of the product selling model option.
productId
Get or set the identifier of the product that this selling model option applies to.
productSellingModel
Get or set the product selling model details for this option.
productSellingModelId
Get or set the identifier of the product selling model for this option.
id
Get or set the unique identifier of the product selling model option.
Signature
public String id {get; set;}
Property Value
Type: String
productId
Get or set the identifier of the product that this selling model option applies to.
Signature
public String productId {get; set;}
Property Value
Type: String
productSellingModel
Get or set the product selling model details for this option.
551
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 566 =====

Signature
public runtime_industries_cpq.ProductSellingModelOutputRepresentationproductSellingModel
{get; set;}
Property Value
Type: runtime_industries_cpq.ProductSellingModelOutputRepresentation
productSellingModelId
Get or set the identifier of the product selling model for this option.
Signature
public String productSellingModelId {get; set;}
Property Value
Type: String
ProductSellingModelOutputRepresentation Class
Represents a product selling model that defines how a product is sold, including the selling model type, pricing term, and status.
Namespace
runtime_industries_cpq on page 433
ProductSellingModelOutputRepresentation Properties
Learn more about the properties available with the ProductSellingModelOutputRepresentation class.
ProductSellingModelOutputRepresentation Properties
Learn more about the properties available with the ProductSellingModelOutputRepresentation class.
The ProductSellingModelOutputRepresentation  class includes these properties.
id
Get or set the unique identifier of the product selling model.
name
Get or set the name of the product selling model.
pricingTerm
Get or set the pricing term value, which represents the duration or quantity for the pricing term unit.
pricingTermUnit
Get or set the unit for the pricing term, such as "Month", "Year", or "Day".
sellingModelType
Get or set the type of selling model, such as "Subscription", "OneTime", or "Usage".
552
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 567 =====

status
Get or set the status of the product selling model, such as "Active" or "Inactive".
id
Get or set the unique identifier of the product selling model.
Signature
public String id {get; set;}
Property Value
Type: String
name
Get or set the name of the product selling model.
Signature
public String name {get; set;}
Property Value
Type: String
pricingTerm
Get or set the pricing term value, which represents the duration or quantity for the pricing term unit.
Signature
public Integer pricingTerm {get; set;}
Property Value
Type: Integer
pricingTermUnit
Get or set the unit for the pricing term, such as "Month", "Year", or "Day".
Signature
public String pricingTermUnit {get; set;}
Property Value
Type: String
553
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 568 =====

sellingModelType
Get or set the type of selling model, such as "Subscription", "OneTime", or "Usage".
Signature
public String sellingModelType {get; set;}
Property Value
Type: String
status
Get or set the status of the product selling model, such as "Active" or "Inactive".
Signature
public String status {get; set;}
Property Value
Type: String
ProductSpecificationRecordTypeOutputRepresentation Class
Represents the record type information for a product specification, which defines the type of record used to store product specification
data.
Namespace
runtime_industries_cpq on page 433
ProductSpecificationRecordTypeOutputRepresentation Properties
Learn more about the properties available with the ProductSpecificationRecordTypeOutputRepresentation class.
ProductSpecificationRecordTypeOutputRepresentation Properties
Learn more about the properties available with the ProductSpecificationRecordTypeOutputRepresentation class.
The ProductSpecificationRecordTypeOutputRepresentation class includes these properties.
isCommercial
Get or set whether this product specification record type is commercial.
isCommercial
Get or set whether this product specification record type is commercial.
554
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 569 =====

Signature
public Boolean isCommercial {get; set;}
Property Value
Type: Boolean
ProductSpecificationTypeOutputRepresentation Class
Represents a product specification type that defines the structure and attributes available for configuring a product.
Namespace
runtime_industries_cpq on page 433
ProductSpecificationTypeOutputRepresentation Properties
Learn more about the properties available with the ProductSpecificationTypeOutputRepresentation class.
ProductSpecificationTypeOutputRepresentation Properties
Learn more about the properties available with the ProductSpecificationTypeOutputRepresentation class.
The ProductSpecificationTypeOutputRepresentation  class includes these properties.
name
Get or set the name of the product specification type.
productSpecificationRecordType
Get or set the product specification record type associated with this specification type.
name
Get or set the name of the product specification type.
Signature
public String name {get; set;}
Property Value
Type: String
productSpecificationRecordType
Get or set the product specification record type associated with this specification type.
Signature
public runtime_industries_cpq.ProductSpecificationRecordTypeOutputRepresentation
productSpecificationRecordType {get; set;}
555
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 570 =====

Property Value
Type: runtime_industries_cpq.ProductSpecificationRecordTypeOutputRepresentation
QocQualificationOutputRepresentation Class
Represents a quote, order, or contract qualification that determines whether a product can be sold based on specific business rules and
conditions.
Namespace
runtime_industries_cpq on page 433
QocQualificationOutputRepresentation Constructors
QocQualificationOutputRepresentation Properties
Learn more about the properties available with the QocQualificationOutputRepresentation class.
QocQualificationOutputRepresentation Constructors
The following are constructors for QocQualificationOutputRepresentation.
QocQualificationOutputRepresentation()
Constructs an empty QocQualificationOutputRepresentation instance.
QocQualificationOutputRepresentation()
Constructs an empty QocQualificationOutputRepresentation instance.
Signature
public QocQualificationOutputRepresentation()
QocQualificationOutputRepresentation Properties
Learn more about the properties available with the QocQualificationOutputRepresentation class.
The QocQualificationOutputRepresentation  class includes these properties.
productId
Get or set the identifier of the product being qualified.
qualificationContext
Get or set the qualification context that contains the qualification result and reason.
productId
Get or set the identifier of the product being qualified.
556
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 571 =====

Signature
public String productId {get; set;}
Property Value
Type: String
qualificationContext
Get or set the qualification context that contains the qualification result and reason.
Signature
public runtime_industries_cpq.QualificationContextOutputRepresentation
qualificationContext {get; set;}
Property Value
Type: runtime_industries_cpq.QualificationContextOutputRepresentation
QualificationContextOutputRepresentation Class
Represents the context information used for product qualification, including account, opportunity, and other relevant context data for
determining product eligibility.
Namespace
runtime_industries_cpq on page 433
QualificationContextOutputRepresentation Properties
Learn more about the properties available with the QualificationContextOutputRepresentation class.
QualificationContextOutputRepresentation Properties
Learn more about the properties available with the QualificationContextOutputRepresentation class.
The QualificationContextOutputRepresentation  class includes these properties.
isQualified
Get or set whether the product is qualified based on the qualification rules.
reason
Get or set the reason for the qualification result, explaining why the product is qualified or not qualified.
isQualified
Get or set whether the product is qualified based on the qualification rules.
557
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 572 =====

Signature
public Boolean isQualified {get; set;}
Property Value
Type: Boolean
reason
Get or set the reason for the qualification result, explaining why the product is qualified or not qualified.
Signature
public String reason {get; set;}
Property Value
Type: String
RelatedObjectFilter Class
Represents a filter for related objects used in product search and discovery, allowing you to filter products based on related object criteria.
Namespace
runtime_industries_cpq on page 433
RelatedObjectFilter Properties
Learn more about the properties available with the RelatedObjectFilter class.
RelatedObjectFilter Properties
Learn more about the properties available with the RelatedObjectFilter class.
The RelatedObjectFilter  class includes these properties.
criteria
Get or set the list of filter criteria to apply to the related object.
objectName
Get or set the name of the related object to filter by, such as "Account" or "Opportunity".
criteria
Get or set the list of filter criteria to apply to the related object.
Signature
public List<runtime_industries_cpq.FilterCriteriaInputRepresentation> criteria {get;
set;}
558
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 573 =====

Property Value
Type: List<runtime_industries_cpq.FilterCriteriaInputRepresentation>
objectName
Get or set the name of the related object to filter by, such as "Account" or "Opportunity".
Signature
public String objectName {get; set;}
Property Value
Type: String
RelatedObjectFilterInputRepresentation Class
Represents input criteria for filtering products based on related object information, such as account, opportunity, or contract data.
Namespace
runtime_industries_cpq on page 433
RelatedObjectFilterInputRepresentation Properties
Learn more about the properties available with the RelatedObjectFilterInputRepresentation
RelatedObjectFilterInputRepresentation Properties
Learn more about the properties available with the RelatedObjectFilterInputRepresentation
The RelatedObjectFilterInputRepresentation  class includes these properties.
relatedObjectFilter
Get or set the list of related object filters to apply when searching for products.
relatedObjectFilter
Get or set the list of related object filters to apply when searching for products.
Signature
public List<runtime_industries_cpq.RelatedObjectFilter> relatedObjectFilter {get; set;}
Property Value
Type: List<runtime_industries_cpq.RelatedObjectFilter>
559
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 574 =====

SearchProductsFacetRepresentation Class
Represents a search facet that provides filtering and categorization options for product search results, such as categories, attributes, or
other product characteristics.
Namespace
runtime_industries_cpq on page 433
SearchProductsFacetRepresentation Properties
Learn more about the properties available with the SearchProductsFacetRepresentation class.
SearchProductsFacetRepresentation Properties
Learn more about the properties available with the SearchProductsFacetRepresentation class.
The SearchProductsFacetRepresentation  class includes these properties.
attributeType
Get or set the type of attribute this facet represents, such as "Picklist" or "Text".
displayName
Get or set the display name of the search facet.
displayRank
Get or set the display rank that determines the order in which this facet appears in search results.
nameOrId
Get or set the name or identifier of the attribute or category that this facet represents.
values
Get or set the list of facet values available for filtering, each representing a distinct option within this facet.
attributeType
Get or set the type of attribute this facet represents, such as "Picklist" or "Text".
Signature
public String attributeType {get; set;}
Property Value
Type: String
displayName
Get or set the display name of the search facet.
Signature
public String displayName {get; set;}
560
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 575 =====

Property Value
Type: String
displayRank
Get or set the display rank that determines the order in which this facet appears in search results.
Signature
public Integer displayRank {get; set;}
Property Value
Type: Integer
nameOrId
Get or set the name or identifier of the attribute or category that this facet represents.
Signature
public String nameOrId {get; set;}
Property Value
Type: String
values
Get or set the list of facet values available for filtering, each representing a distinct option within this facet.
Signature
public List<runtime_industries_cpq.FacetValueRepresentation> values {get; set;}
Property Value
Type: List<runtime_industries_cpq.FacetValueRepresentation>
SearchProductsRepresentation Class
Represents the results of a product search operation, including the list of products, search facets, pagination information, and total count
of matching products.
Namespace
runtime_industries_cpq on page 433
SearchProductsRepresentation Properties
Learn more about the properties available with the SearchProductsRepresentation class.
561
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 576 =====

SearchProductsRepresentation Properties
Learn more about the properties available with the SearchProductsRepresentation class.
The SearchProductsRepresentation  class includes these properties.
additionalFields
Get or set additional custom fields for the product in the search results.
attributeCategories
Get or set the list of attribute categories that contain product attributes for configuration.
availabilityDate
Get or set the date when the product becomes available for sale.
catalogs
Get or set the list of catalogs that this product belongs to.
configureDuringSale
Get or set whether the product can be configured during the sales process.
description
Get or set the description of the product in the search results. If data translation is set up and specified in the org, the translated
description is available.
discontinuedDate
Get or set the date when the product was discontinued.
displayUrl
Get or set the URL to display additional information about the product.
endOfLifeDate
Get or set the end of life date for the product.
id
Get or set the ID of the product in the search results.
isActive
Get or set whether the product is active (true) or not (false) in the search results.
isAssetizable
Get or set whether the product can be converted to an asset after sale.
isComponentRequired
Get or set whether this component is required in a bundle or product relationship.
isDefaultComponent
Get or set whether this component is selected by default in a bundle or product relationship.
isQuantityEditable
Get or set whether the quantity of this product can be edited.
isSoldOnlyWithOtherProds
Get or set whether this product can only be sold with other products.
name
Get or set the name of the product in the search results. If data translation is set up and specified in the org, the translated name is
available.
562
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 577 =====

nodeType
Get or set the node type of the product, such as "Product" or "Bundle".
prices
Get or set the list of prices available for this product.
productClassification
Get or set the product classification information for this product.
productCode
Get or set the universal product code that's used to track the part that's used in the product.
productComponentGroups
Get or set the list of product component groups that organize related components.
productInformation
Get or set additional product information details.
productPricingInformation
Get or set the pricing information for this product, including price lists and pricing models.
productQuantity
Get or set the quantity constraints and current quantity for this product.
productRelatedComponent
Get or set the related component information for this product in bundle or product relationships.
productSellingModelOptions
Get or set the list of selling model options available for this product.
productSpecificationType
Get or set the product specification type that defines the structure and attributes for configuring this product.
productType
Get or set the type of product, such as "Product", "Service", or "Bundle".
qualificationContext
Get or set the qualification context that contains the qualification result and reason for this product.
status
Get or set the status of the product, such as "Active" or "Inactive".
unitOfMeasure
Get or set the unit of measure for the quantity of this product.
additionalFields
Get or set additional custom fields for the product in the search results.
Signature
public List<runtime_industries_cpq.AdditionalFieldsWrapper> additionalFields {get;
set;}
Property Value
Type: List<runtime_industries_cpq.AdditionalFieldsWrapper>
563
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 578 =====

attributeCategories
Get or set the list of attribute categories that contain product attributes for configuration.
Signature
public List<runtime_industries_cpq.AttributeCategoryOutputRepresentation>
attributeCategories {get; set;}
Property Value
Type: List<runtime_industries_cpq.AttributeCategoryOutputRepresentation>
availabilityDate
Get or set the date when the product becomes available for sale.
Signature
public Datetime availabilityDate {get; set;}
Property Value
Type: Datetime
catalogs
Get or set the list of catalogs that this product belongs to.
Signature
public List<runtime_industries_cpq.CatalogOutputRepresentation> catalogs {get; set;}
Property Value
Type: List<runtime_industries_cpq.CatalogOutputRepresentation>
configureDuringSale
Get or set whether the product can be configured during the sales process.
Signature
public String configureDuringSale {get; set;}
Property Value
Type: String
564
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 579 =====

description
Get or set the description of the product in the search results. If data translation is set up and specified in the org, the translated description
is available.
Signature
public String description {get; set;}
Property Value
Type: String
discontinuedDate
Get or set the date when the product was discontinued.
Signature
public Datetime discontinuedDate {get; set;}
Property Value
Type: Datetime
displayUrl
Get or set the URL to display additional information about the product.
Signature
public String displayUrl {get; set;}
Property Value
Type: String
endOfLifeDate
Get or set the end of life date for the product.
Signature
public Datetime endOfLifeDate {get; set;}
Property Value
Type: Datetime
id
Get or set the ID of the product in the search results.
565
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 580 =====

Signature
public String id {get; set;}
Property Value
Type: String
isActive
Get or set whether the product is active (true) or not (false) in the search results.
Signature
public Boolean isActive {get; set;}
Property Value
Type: Boolean
isAssetizable
Get or set whether the product can be converted to an asset after sale.
Signature
public Boolean isAssetizable {get; set;}
Property Value
Type: Boolean
isComponentRequired
Get or set whether this component is required in a bundle or product relationship.
Signature
public Boolean isComponentRequired {get; set;}
Property Value
Type: Boolean
isDefaultComponent
Get or set whether this component is selected by default in a bundle or product relationship.
Signature
public Boolean isDefaultComponent {get; set;}
566
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 581 =====

Property Value
Type: Boolean
isQuantityEditable
Get or set whether the quantity of this product can be edited.
Signature
public Boolean isQuantityEditable {get; set;}
Property Value
Type: Boolean
isSoldOnlyWithOtherProds
Get or set whether this product can only be sold with other products.
Signature
public Boolean isSoldOnlyWithOtherProds {get; set;}
Property Value
Type: Boolean
name
Get or set the name of the product in the search results. If data translation is set up and specified in the org, the translated name is
available.
Signature
public String name {get; set;}
Property Value
Type: String
nodeType
Get or set the node type of the product, such as "Product" or "Bundle".
Signature
public String nodeType {get; set;}
Property Value
Type: String
567
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 582 =====

prices
Get or set the list of prices available for this product.
Signature
public List<runtime_industries_cpq.ProductPricesOutputRepresentation> prices {get;
set;}
Property Value
Type: List<runtime_industries_cpq.ProductPricesOutputRepresentation>
productClassification
Get or set the product classification information for this product.
Signature
public runtime_industries_cpq.ProductClassificationOutputRepresentation
productClassification {get; set;}
Property Value
Type: runtime_industries_cpq.ProductClassificationOutputRepresentation
productCode
Get or set the universal product code that's used to track the part that's used in the product.
Signature
public String productCode {get; set;}
Property Value
Type: String
productComponentGroups
Get or set the list of product component groups that organize related components.
Signature
public List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation>
productComponentGroups {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductComponentGroupOutputRepresentation>
568
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 583 =====

productInformation
Get or set additional product information details.
Signature
public String productInformation {get; set;}
Property Value
Type: String
productPricingInformation
Get or set the pricing information for this product, including price lists and pricing models.
Signature
public String productPricingInformation {get; set;}
Property Value
Type: String
productQuantity
Get or set the quantity constraints and current quantity for this product.
Signature
public runtime_industries_cpq.ProductQuantityOutputRepresentationproductQuantity {get;
set;}
Property Value
Type: runtime_industries_cpq.ProductQuantityOutputRepresentation
productRelatedComponent
Get or set the related component information for this product in bundle or product relationships.
Signature
public ConnectApi.CPQProductRelatedComponentOutputRepresentationproductRelatedComponent
{get; set;}
Property Value
Type: ConnectApi.CPQProductRelatedComponentOutputRepresentation
569
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 584 =====

productSellingModelOptions
Get or set the list of selling model options available for this product.
Signature
public List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation>
productSellingModelOptions {get; set;}
Property Value
Type: List<runtime_industries_cpq.ProductSellingModelOptionOutputRepresentation>
productSpecificationType
Get or set the product specification type that defines the structure and attributes for configuring this product.
Signature
public runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation
productSpecificationType {get; set;}
Property Value
Type: runtime_industries_cpq.ProductSpecificationTypeOutputRepresentation
productType
Get or set the type of product, such as "Product", "Service", or "Bundle".
Signature
public String productType {get; set;}
Property Value
Type: String
qualificationContext
Get or set the qualification context that contains the qualification result and reason for this product.
Signature
public runtime_industries_cpq.QualificationContextOutputRepresentation
qualificationContext {get; set;}
Property Value
Type: runtime_industries_cpq.QualificationContextOutputRepresentation
570
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 585 =====

status
Get or set the status of the product, such as "Active" or "Inactive".
Signature
public String status {get; set;}
Property Value
Type: String
unitOfMeasure
Get or set the unit of measure for the quantity of this product.
Signature
public ConnectApi.UnitOfMeasureOutputRepresentation unitOfMeasure {get; set;}
Property Value
Type: ConnectApi.UnitOfMeasureOutputRepresentation
UnitOfMeasureOutputRepresentation Class
Represents the unit of measure for a product. This class contains information about how product quantities are measured, including the
unit code, name, scale, and rounding method.
Namespace
runtime_industries_cpq on page 433
UnitOfMeasureOutputRepresentation Constructor
Learn more about the constructor that's available with the UnitOfMeasureOutputRepresentation class.
UnitOfMeasureOutputRepresentation Properties
Contains properties to include unit of measure details for products.
UnitOfMeasureOutputRepresentation Constructor
Learn more about the constructor that's available with the UnitOfMeasureOutputRepresentation class.
The UnitOfMeasureOutputRepresentation  class includes this constructor.
UnitOfMeasureOutputRepresentation(apexObj)
Constructor to create a UnitOfMeasureOutputRepresentation instance from a ConnectApi UnitOfMeasureOutputRepresentation
object.
571
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 586 =====

UnitOfMeasureOutputRepresentation(apexObj)
Constructor to create a UnitOfMeasureOutputRepresentation instance from a ConnectApi UnitOfMeasureOutputRepresentation object.
Signature
public UnitOfMeasureOutputRepresentation(ConnectApi.UnitOfMeasureOutputRepresentation
apexObj)
Parameters
apexObj
Type: ConnectApi.UnitOfMeasureOutputRepresentation
The ConnectApi unit of measure representation object to convert to UnitOfMeasureOutputRepresentation.
UnitOfMeasureOutputRepresentation Properties
Contains properties to include unit of measure details for products.
The UnitOfMeasureOutputRepresentation  class includes these properties.
id
Get the ID of the unitofmeasure.
name
Get the name of the unitofmeasure.
roundingMethod
Get the roundingmethod value.
scale
Get the scale value.
unitCode
Get the unitcode value.
id
Get the ID of the unitofmeasure.
Signature
public String id {get; set;}
Property Value
Type: String
name
Get the name of the unitofmeasure.
572
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 587 =====

Signature
public String name {get; set;}
Property Value
Type: String
roundingMethod
Get the roundingmethod value.
Signature
public String roundingMethod {get; set;}
Property Value
Type: String
scale
Get the scale value.
Signature
public Integer scale {get; set;}
Property Value
Type: Integer
unitCode
Get the unitcode value.
Signature
public String unitCode {get; set;}
Property Value
Type: String
VisibilityRule Class
Represents a visibility rule that is evaluated during product configuration. Visibility rules control the visibility of products, attributes, or
other UI elements based on configuration conditions.
Namespace
runtime_industries_cpq on page 433
573
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 588 =====

VisibilityRule Constructor
Learn more about the constructor that's available with the VisibilityRule class.
VisibilityRule Properties
Contains properties to store visibility rule details from configuration rule evaluation.
VisibilityRule Constructor
Learn more about the constructor that's available with the VisibilityRule class.
The VisibilityRule  class includes this constructor.
VisibilityRule(stiId, prcId, attributeId, attributePicklistValueId, target, scope, type, productIds, message)
Constructor to create a VisibilityRule instance with the specified visibility rule details.
VisibilityRule(stiId, prcId, attributeId, attributePicklistValueId, target, scope,
type, productIds, message)
Constructor to create a VisibilityRule instance with the specified visibility rule details.
Signature
public VisibilityRule(String stiId, String prcId, String attributeId, String
attributePicklistValueId, String target, String scope, String type, List<String>
productIds, String message)
Parameters
stiId
Type: String
The ID of the Sales Transaction Item (STI) associated with this visibility rule.
prcId
Type: String
The ID of the Product Relationship Configuration (PRC) associated with this visibility rule.
attributeId
Type: String
The ID of the attribute associated with this visibility rule.
attributePicklistValueId
Type: String
The ID of the attribute picklist value associated with this visibility rule.
target
Type: String
The target of the visibility rule (for example, product, attribute, or component).
scope
Type: String
The scope of the visibility rule.
574
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 589 =====

type
Type: String
The type of visibility rule (for example, Show or Hide).
productIds
Type: List<String>
List of product IDs affected by this visibility rule.
message
Type: String
The message to display when the visibility rule is applied.
VisibilityRule Properties
Contains properties to store visibility rule details from configuration rule evaluation.
The VisibilityRule  class includes these properties.
attributeId
Get the ID of the attribute.
attributePicklistValueId
Get the ID of the attributepicklistvalue.
message
Get the message value.
prcId
Get the ID of the prc.
productId
Get the ID of the product.
scope
Get the scope value.
stiId
Get the ID of the sti.
target
Get the target value.
type
Get the type value.
attributeId
Get the ID of the attribute.
Signature
public String attributeId {get; set;}
575
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 590 =====

Property Value
Type: String
attributePicklistValueId
Get the ID of the attributepicklistvalue.
Signature
public String attributePicklistValueId {get; set;}
Property Value
Type: String
message
Get the message value.
Signature
public String message {get; set;}
Property Value
Type: String
prcId
Get the ID of the prc.
Signature
public String prcId {get; set;}
Property Value
Type: String
productId
Get the ID of the product.
Signature
public List<String> productId {get; set;}
Property Value
Type: List<String>
576
Product Discovery Apex ReferenceProduct Catalog Management

===== PAGE 591 =====

scope
Get the scope value.
Signature
public String scope {get; set;}
Property Value
Type: String
stiId
Get the ID of the sti.
Signature
public String stiId {get; set;}
Property Value
Type: String
target
Get the target value.
Signature
public String target {get; set;}
Property Value
Type: String
type
Get the type value.
Signature
public String type {get; set;}
Property Value
Type: String
Product Discovery Metadata API Types
Metadata API enables you to access some types and feature settings that you can customize in the user interface.
577
Product Discovery Metadata API TypesProduct Catalog Management

===== PAGE 592 =====

Flow for Product Discovery
Represents the metadata associated with a flow. With Flow, you can create an application that takes users through a series of pages
to query and update the records in the database. You can also run logic and provide branching capability based on user input to
build dynamic applications.
ProductDiscoverySettings
Represents the settings for Product Discovery.
Flow for Product Discovery
Represents the metadata associated with a flow. With Flow, you can create an application that takes users through a series of pages to
query and update the records in the database. You can also run logic and provide branching capability based on user input to build
dynamic applications.
FlowActionCall
Product Discovery exposes additional actionType values for the FlowActionCall metadata type.
DescriptionField TypeField Name
Required.InvocableActionType
(enumeration of
type string)
actionType
The action type. Additional valid values for Product Discovery are:
• findProducts— Search for the products from a catalog,
category, or subcategory by using the specified search term.
• GetProducts— Get products from the specified catalog,
category, or subcategory, including product qualification and pricing
details.
• GetProductDetails— Get details such as attributes, hierarchy,
and cardinality for the specified product.
• executeQualificationProcedure— Execute a
qualification procedure, which returns the qualification status for
the specified products.
• getCatalogDetails— Get details of a catalog record.
• getCatalogs— Get a list of catalog records.
• getCategories— Get the list of categories associated with a
catalog record.
• getCategoryDetails— Get details of a category record.
• getMultipleProductDetails— Get product details for a
list of products.
• searchPrdctWithGuidedSelection— Use guided product
selection to search for products.
ProductDiscoverySettings
Represents the settings for Product Discovery.
578
Product Discovery Metadata API TypesProduct Catalog Management

===== PAGE 593 =====

Parent Type and Manifest Access
This type extends the Metadata metadata type and inherits its fullName field.
In the package manifest, all the settings metadata types for the org are accessed using the “Settings” name. See Settings for more details.
File Suffix and Directory Location
ProductDiscoverySettings values are stored in the ProductDiscoverySettings.settings file in the settings
folder. The .settings  files are different from other named components, because there is only one settings file for each settings
component.
Version
ProductDiscoverySettings components are available in API version 62.0 and later.
Fields
DescriptionField Name
Field Type
boolean
enableGuidedSelling
Description
Indicates whether guided product selection is enabled (true) or not (false). Using
guided product selection, you can manage dynamic forms that assess user requirements
and show relevant products. The default value is false. Available in API version 63.0
and later.
Field Type
string
discoverProductsFlowNameOrgValue
Description
Name of the custom flow for browsing and adding products. If this field isn’t specified,
the Discover Products flow is used for browsing and adding products. Available in API
version 63.0 and later.
Field Type
string
prodDiscBrowseContextDefOrgValue
Description
Context definition that gets updated based on the user-selected options and provides
summary data.
Field Type
string
prodDiscDefaultCatalogOrgValue
Description
Default catalog that determines the products to be displayed on the product list page.
Available in API version 64.0 and later.
579
Product Discovery Metadata API TypesProduct Catalog Management

===== PAGE 594 =====

DescriptionField Name
Field Type
string
prodDiscPricingEnabledOrgValue
Description
Indicates whether pricing is enabled (true) or not (false). The default value is
false.
Field Type
string
prodDiscProcedureOrgValue
Description
Pricing procedure that calculates the list price.
Field Type
string
prodDiscQualEnabledOrgValue
Description
Indicates whether product qualification is enabled (true) or not (false). The default
value is false.
Field Type
string
prodDiscQualificationOrgValue
Description
Qualification procedure that determines product eligibility.
Declarative Metadata Sample Definition
The following is an example of a ProductDiscoverySettings component.
<ProductDiscoverySettings xmlns="http://soap.sforce.com/2006/04/metadata">
<enableGuidedSelling>true</enableGuidedSelling>
<discoverProductsFlowNameOrgValue>revenue_products__DiscoverProducts</discoverProductsFlowNameOrgValue>
<prodDiscPricingEnabledOrgValue>true</prodDiscPricingEnabledOrgValue>
<prodDiscQualEnabledOrgValue>true</prodDiscQualEnabledOrgValue>
<prodDiscProcedureOrgValue>PricingProcedure</prodDiscProcedureOrgValue>
<prodDiscQualificationOrgValue>QualificationProcedure</prodDiscQualificationOrgValue>
<prodDiscBrowseContextDefOrgValue>BrowseContextDefinition</prodDiscBrowseContextDefOrgValue>
</ProductDiscoverySettings>
The following is an example package.xml  that references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>ProductDiscovery</members>
<name>Settings</name>
580
Product Discovery Metadata API TypesProduct Catalog Management

===== PAGE 595 =====

</types>
<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
The wildcard character *  (asterisk) in the package.xml manifest file doesn’t apply to metadata types for feature settings. The wildcard
applies only when retrieving all settings, not for an individual setting. For details, see Settings. For information about using the manifest
file, see Deploying and Retrieving Metadata with the Zip File.
581
Product Discovery Metadata API TypesProduct Catalog Management

===== PAGE 596 =====

