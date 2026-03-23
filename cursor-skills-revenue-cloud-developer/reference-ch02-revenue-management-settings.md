---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Capítulo 2 — RevenueManagementSettings

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

CHAPTER 2 RevenueManagementSettings
Represents the configuration settings to set up Revenue Cloud.
Parent Type and Manifest Access
This type extends the Metadata metadata type and inherits its fullName  field.
In the package manifest, all the settings metadata types for the org are accessed using the "Settings"
name. See Settings for more details.
File Suffix and Directory Location
RevenueManagementSettings values are stored in the revenuemanagement.settings
file in the settings  folder. The .settings  files are different from other named components,
because there's only one settings file for each settings component.
Version
RevenueManagementSettings is available in API version 60.0 and later.
Special Access Rules
This metadata settings type is available with Revenue Cloud.
Fields
DescriptionField Name
Field Type
boolean
enableAdvCreateOrdersFromQuote
Description
Indicates whether to enable users to choose a method
for generating multiple orders from a single quote
(true) or not (false). This setting updates the
functionality of the Create Order capability on quotes.
Available in API version 65.0 and later.
4

===== PAGE 19 =====

DescriptionField Name
Field Type
boolean
enableAdvancedDetailLinePricing
Description
Indicates whether to enable advanced pricing for quote
and order detail line items (true) or not (false).
The default value is false. Available in API version
65.0 and later.
Field Type
boolean
enableAsIsRenewals
Description
Indicates whether users can enable as-is renewals
capability for existing assets (true) or not (false).
The default value is false. Available in API version
64.0 and later.
Field Type
boolean
enableAutoAddDerivedAsset
Description
Indicates whether to automatically add assets with
derived pricing to a quote or an order when
contributing products are added to it (true) or not
(false). Available in API version 62.0 and later.
Field Type
boolean
enableCoreCPQ
Description
Indicates whether to enable read and write access to
Revenue Cloud features and objects (true) or not
(false). See Enable Revenue Cloud Features in Your
Scratch Org.
Field Type
boolean
enableDeltaPricing
Description
Indicates whether to reprice faster by processing only
the changes (delta) made to quotes and orders (true)
or not (false). The default value is false. Available
in API version 63.0 and later.
Field Type
boolean
enableGroupRamp
5
RevenueManagementSettings

===== PAGE 20 =====

DescriptionField Name
Description
Reserved for internal use.
Field Type
boolean
enableGroupRampPref
Description
Indicates whether to create ramp deals for multiple
products by creating group ramp segments (true)
or not (false). The default value is false. Configure
group ramp segments with specific start dates and
end dates, and different product quantities and prices.
Available in API version 65.0 and later.
Before you enable this setting, ensure the
groupsEnabled  and
enableTransactionCloning  fields are set to
true.
Field Type
boolean
enableRampDeal
Description
Indicates whether to create ramp deals for individual
line items by creating segments with specific start
dates, end dates, quantities, and prices (true) or not
(false). Available in API version 62.0 and later.
Field Type
boolean
enableRevUnifiedSetup
Description
Indicates whether to enable the usage of a procedure
plan for price calculation (true) or not (false).
Field Type
boolean
enableTransactionCloning
Description
Indicates whether to clone quotes or orders with their
line items and groups, or clone the individual line items
and groups of line items. Available in API version 64.0
and later.
Field Type
boolean
enableTransactionProcessor
6
RevenueManagementSettings

===== PAGE 21 =====

DescriptionField Name
Description
Indicates whether to enable transaction types for
quotes and orders (true) or not (false). Transaction
types optimize the way transactions are processed,
depending on their size, complexity, and the business
needs of the org. You can’t turn off transaction
processing after it’s turned on. Available in API version
63.0 and later.
To set a default transaction type, create transaction
types, and select the default. After you select a default
transaction type, you can’t be without a default.
Field Type
boolean
groupsEnabled
Description
Indicates whether users can group line items in quotes
and orders (true) or not (false). Available in API
version 62.0 and later.
Field Type
boolean
hidePriceRefreshNtfcn
Description
Indicates whether to hide the notification that appears
when quote or order prices aren’t updated (true) or
not (false). Hiding this notification may affect saving
quotes and creating orders because you could be using
outdated prices. The default value is false. Available
in API version 65.0 and later.
Field Type
boolean
relaxUniqueCipValidation
Description
Indicates whether to enable fully customizable
extensions to contract item prices by ignoring record
validations (true) or not (false). Available in API
version 64.0 and later.
Field Type
boolean
skipOrgSttPricing
Description
Indicates whether to skip the default pricing procedure
and any pricing procedure set for a sales transaction
with quote or order type (true) or not (false). To
7
RevenueManagementSettings

===== PAGE 22 =====

DescriptionField Name
enable this field, you must enable the
enableRevUnifiedSetup  field.
Declarative Metadata Sample Definition
Here's an example of a RevenueManagementSettings component.
<?xml version="1.0" encoding="UTF-8"?>
<RevenueManagementSettings
xmlns="http://soap.sforce.com/2006/04/metadata">
<enableCoreCPQ>true</enableCoreCPQ>
<enableDeltaPricing>true</enableDeltaPricing>
<enableTransactionProcessor>true</enableTransactionProcessor>
<enableAutoAddDerivedAsset>true</enableAutoAddDerivedAsset>
<enableRampDeal>true</enableRampDeal>
<enableRevUnifiedSetup>true</enableRevUnifiedSetup>
<groupsEnabled>true</groupsEnabled>
<enableTransactionCloning>true</enableTransactionCloning>
<relaxUniqueCipValidation>true</relaxUniqueCipValidation>
<skipOrgSttPricing>true</skipOrgSttPricing>
<enableAsIsRenewals>true</enableAsIsRenewals>
<enableAdvCreateOrdersFromQuote>true</enableAdvCreateOrdersFromQuote>
<enableAdvancedDetailLinePricing>true</enableAdvancedDetailLinePricing>
<enableGroupRampPref>true</enableGroupRampPref>
<hidePriceRefreshNtfcn>true</hidePriceRefreshNtfcn>
</RevenueManagementSettings>
This example package.xml  references the previous definition.
<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
<types>
<members>RevenueManagement</members>
<name>Settings</name>
</types>
<version>66.0</version>
</Package>
Wildcard Support in the Manifest File
The wildcard character *  (asterisk) in the package.xml  manifest file doesn’t apply to metadata
types for feature settings. The wildcard applies only when retrieving all settings, not for an individual
setting. For details, see Settings. For information about using the manifest file, see Deploying and
Retrieving Metadata with the Zip File.
8
RevenueManagementSettings

===== PAGE 23 =====

