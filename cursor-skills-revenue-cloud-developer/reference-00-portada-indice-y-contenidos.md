---
source: Revenue Cloud Developer Guide PDF v66.0 (Spring '26), Salesforce — texto extraído
language: en (original de la guía)
---

# Portada, copyright e índice (Contents)

> Contenido íntegro extraído del PDF *Revenue Cloud Developer Guide* (versión 66.0). La extracción automática puede introducir saltos de línea o espaciado irregulares respecto al PDF impreso; los nombres de API, objetos y metadatos deben tomarse como en el original.

---

TOTAL_PAGES=2788



===== PAGE 1 =====

Revenue Cloud Developer
Guide
Version 66.0, Spring ’26
Last updated: March 20, 2026

===== PAGE 2 =====

© Copyright 2000–2026 Salesforce, Inc. All rights reserved. Salesforce is a registered trademark of Salesforce, Inc., as are other
names and marks. Other marks appearing herein may be trademarks of their respective owners.

===== PAGE 3 =====

CONTENTS
Chapter 1: Get Started with Revenue Cloud Developer Resources . . . . . . . . . . . . . . . . . 1
Chapter 2: Revenue Management Settings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4
Chapter 3: Revenue Cloud Deployment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 9
Deployment Workflows and Sequence . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 10
Deployment Considerations . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 11
Global Unique ID Setup . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 11
Create a GUID Field . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
GUID Design and Usage . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 12
Managing Component States . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 13
Post-Deployment Steps . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 14
Deployment Scenarios . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 15
Object Deployment Reference . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 19
Product Catalog Management Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 19
Salesforce Pricing Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 23
Product Configurator Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 25
Transaction Management Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 26
Dynamic Revenue Orchestrator Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 26
Usage Management Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 27
Billing Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 29
Salesforce Contracts Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 30
Metadata Deployment Reference . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 30
Product Catalog Management Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 31
Salesforce Pricing Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 34
Product Configurator Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 36
Transaction Management Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 37
Dynamic Revenue Orchestrator Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 38
Usage Management Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 40
Billing Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 42
Industries Common Component Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 44
Salesforce Contracts Metadata . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 44
Additional Deployment Information . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 45
Product Catalog Management Additional Information . . . . . . . . . . . . . . . . . . . . . . . . 45
Salesforce Pricing Additional Information . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 47
Product Configurator Additional Information . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 49
Dynamic Revenue Orchestrator Additional Information . . . . . . . . . . . . . . . . . . . . . . . . 50
Usage Management Additional Information . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 53
Billing Additional Information . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 55
Business Rules Engine and Decision Tables Additional Information . . . . . . . . . . . . . . . . 56

===== PAGE 4 =====

Context Service Additional Information . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 57
Data Processing Engine Additional Information . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 58
Salesforce Contracts Additional Information . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 58
Chapter 4: Product Catalog Management . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 64
Product Catalog Management . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 65
Product Catalog Management Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . 65
Product Catalog Management Fields on Standard Objects . . . . . . . . . . . . . . . . . . . . . 114
Product Catalog Management Business APIs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 123
Product Catalog Management Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . 263
Product Catalog Management Tooling API Objects . . . . . . . . . . . . . . . . . . . . . . . . . . 268
Product Discovery . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 275
Product Discovery Business APIs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 275
Product Discovery Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 366
Product Discovery Apex Reference . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 433
Product Discovery Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 577
Chapter 5: Salesforce Pricing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 582
Salesforce Pricing Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 583
AttributeAdjustmentCondition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 585
AttributeBasedAdjRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 588
AttributeBasedAdjustment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 590
AttributeDefinition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 595
BundleBasedAdjustment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 599
CostBook . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 605
ContractItemPrice . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 607
CostBookEntry . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 610
PriceAdjustmentSchedule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 613
PriceAdjustmentTier . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 617
PriceBook2 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 621
PriceBookEntry . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 624
PriceBookEntryDerivedPrice . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 628
PriceRevisionPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 633
PricingAdjBatchJob . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 635
PricingAdjBatchJobLog . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 640
PricingAPIExecution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 642
PricingProcedureResolution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 645
PricingProcessExecution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 648
ProductPriceHistoryLog . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 651
ProductPriceRange . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 653
ProductSellingModel . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 655
ProductSellingModelDataTranslation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 658
ProductSellingModelOption . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 659
ProcedurePlanCriterion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 662
Contents

===== PAGE 5 =====

ProrationPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 664
Salesforce Pricing Fields on Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 666
IndexRate . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 666
Salesforce Pricing Business APIs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 667
Resources . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 669
Request Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 698
Response Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 723
Salesforce Pricing Apex Reference . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 762
RevSignaling Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 762
Salesforce Pricing Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 768
Run Salesforce Headless Pricing Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 769
Run Salesforce Pricing Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 775
Salesforce Pricing Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 778
Flow for Salesforce Pricing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 778
IndustriesPricingSettings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 779
PricingActionParameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 781
PricingRecipe . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 784
ProcedureOutputResolution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 789
Salesforce Pricing Tooling API Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 791
PricingActionParameters . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 792
PricingProcedureOutputMap . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 795
PricingRecipe . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 798
PricingRecipeTableMapping . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 801
ProcedureOutputResolution . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 803
ProcedurePlanCriterion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 806
ProcedurePlanDefinition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 808
ProcedurePlanDefinitionVersion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 810
ProcedurePlanOption . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 813
ProcedurePlanSection . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 817
ProcedurePlanVariable . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 819
Chapter 6: Rate Management . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 822
Rate Management Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 823
BindingObjectCustomExt . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 824
BindingObjectRateAdjustment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 825
BindingObjectRateCardEntry . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 827
PriceBookRateCard . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 832
RateAdjustmentByAttribute . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 834
RateAdjustmentByTier . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 839
RateCard . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 843
RateCardEntry . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 845
RatingFrequencyPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 851
RatingRequest . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 853
RatingRequestBatchJob . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 856
Contents

===== PAGE 6 =====

Rate Management Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 858
IndustriesRatingSettings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 858
Flow for Rate Management . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 860
Rate Management Business APIs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 860
Resources . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 860
Response Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 862
Rate Management Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 866
Invoke Rating Service Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 866
Chapter 7: Product Configurator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 870
Product Configurator Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 871
ExpressionSetConstraintObj . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 871
ProductConfigurationFlow . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 873
ProductConfigFlowAssignment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 874
ProductConfigurationRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 876
Product Configurator Business APIs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 879
Resources . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 881
Request Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 896
Response Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 912
Product Configurator Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 983
Run Config Rules Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 983
Product Configurator Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 986
Flow for Product Configurator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 987
ProductConfiguratorSettings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 987
Constraint Modeling Language . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 988
Modeling a Generator Set . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 990
Core Concepts . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 990
Core Concept Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1042
Annotation Examples . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1048
Constraint Modeling Language (CML) Best Practices . . . . . . . . . . . . . . . . . . . . . . . . 1093
Business-Centric Constraint Modeling Language (CML) Guidelines . . . . . . . . . . . . . . . 1101
Debugging Constraint Modeling Language (CML) . . . . . . . . . . . . . . . . . . . . . . . . . . 1104
Model Structure . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1107
Chapter 8: Transaction Management . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1114
Transaction Management Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1115
Asset . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1117
AssetAction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1134
AssetActionSource . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1142
AssetActionSrcPriceAdjustment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1150
AssetContractRelationship . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1152
AssetDowntimePeriod . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1155
AssetOwnerSharingRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1156
AssetRateAdjustment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1158
Contents

===== PAGE 7 =====

AssetRateCardEntry . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1160
AssetRelationship . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1164
AssetShare . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1169
AssetStatePeriod . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1171
AssetStatePeriodAttribute . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1176
AssetTag . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1178
AssetTokenEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1180
AssetWarranty . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1180
BindingObjUsageRsrcPlcy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1183
ContractItemPrice . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1187
ContractItemPriceAdjTier . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1191
ContractItemPriceHistory . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1193
OrderDeliveryMethod . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1196
OrderItemAttribute . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1199
OrderItemDetail . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1201
OrderItemRateAdjustment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1204
OrderItemRateCardEntry . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1206
OrderItemUsageRsrcGrant . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1209
OrderItemUsageRsrcPlcy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1212
SalesTransactionType . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1215
QuoteAction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1216
QuoteLineDetail . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1219
QuoteLineGroup . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1222
QuoteLineItemAttribute . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1227
QuotLineItmUseRsrcGrant . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1229
QuotLineItmUsageRsrcPlcy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1233
QuoteLineRateAdjustment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1237
QuoteLineRateCardEntry . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1238
Transaction Management Fields on Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . 1241
Transaction Management Fields on Object State Definition . . . . . . . . . . . . . . . . . . . . 1242
Transaction Management Fields on Object State Transition . . . . . . . . . . . . . . . . . . . 1242
Transaction Management Fields on Object State Value . . . . . . . . . . . . . . . . . . . . . . 1243
Transaction Management Fields on Order . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1243
Transaction Management Fields on Order Item . . . . . . . . . . . . . . . . . . . . . . . . . . . 1248
Transaction Management Fields on Order Item Group . . . . . . . . . . . . . . . . . . . . . . . 1254
Transaction Management Fields on Order Action . . . . . . . . . . . . . . . . . . . . . . . . . . 1258
Transaction Management Fields on Order Item Relationship . . . . . . . . . . . . . . . . . . . 1258
Transaction Management Fields on Quote . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1259
Transaction Management Fields on Quote Line Group . . . . . . . . . . . . . . . . . . . . . . . 1262
Transaction Management Fields on Quote Line Item . . . . . . . . . . . . . . . . . . . . . . . . 1266
Transaction Management Fields on Quote Document . . . . . . . . . . . . . . . . . . . . . . . 1270
Transaction Management Tooling API Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1271
TransactionProcessingType . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1271
Transaction Management Platform Event . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1275
Contents

===== PAGE 8 =====

CreateAssetOrderEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1276
PlaceOrderCompletedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1281
QuoteSaveEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1283
QuoteToOrderCompletedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1285
Transaction Management Business APIs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1288
Resources . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1290
Request Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1342
Response Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1403
Transaction Management Apex Reference . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1441
CommerceOrders Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1442
ConnectApi Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1461
CommerceTax Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1462
PlaceQuote Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1578
RevSalesTrxn Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1598
Transaction Management Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . . . . 1625
Create Contract Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1625
Create or Update Asset From Order Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1627
Create or Update Asset From Order Item Action . . . . . . . . . . . . . . . . . . . . . . . . . . . 1629
Create Order From Quote Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1630
Create Orders From Quote Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1632
Get Renewable Assets Summary Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1636
Initiate Amendment Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1638
Initiate Cancellation Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1640
Initiate Renewal Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1643
Initiate Rollback on Last Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1645
Initiate Transfer Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1647
Transaction Management Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1651
Flow for Transaction Management . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1651
Chapter 9: Advanced Approvals . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1653
Advanced Approvals Fields on Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1654
ApprovalSubmission . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1654
Advanced Approvals Fields on Approval Work Item . . . . . . . . . . . . . . . . . . . . . . . . . 1658
Advanced Approvals Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1660
Cancel Approval Submission Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1660
Get Previous Related Record Details Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1662
Override Approval Work Item Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1663
Reassign Approval Work Item Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1665
Recall Approval Submission Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1667
Review Approval Work Item Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1668
Advanced Approvals Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1670
Flow for Advanced Approvals . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1671
Chapter 10: Dynamic Revenue Orchestrator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1673
Contents

===== PAGE 9 =====

Dynamic Revenue Orchestrator Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1674
AssetFulfillmentDecomp . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1675
FulfillmentAsset . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1678
FulfillmentAssetAttribute . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1681
FulfillmentAssetRelationship . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1683
FulfillmentFalloutRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1685
FulfillmentLineAttribute . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1688
FulfillmentLineRel . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1690
FulfillmentLineSourceRel . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1693
FulfillmentPlan . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1696
FulfillmentStep . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1699
FulfillmentStepDefinition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1709
FulfillmentStepDefinitionGroup . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1717
FulfillmentStepDependency . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1719
FulfillmentStepDependencyDef . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1720
FulfillmentStepJeopardyRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1723
FulfillmentStepSource . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1726
FulfillmentTaskAssignmentRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1727
FulfillmentWorkspace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1731
FulfillmentWorkspaceItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1732
ProductDecompEnrichmentRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1734
ProdtDecompEnrchVarMap . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1738
ProductFulfillmentDecompRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1740
ProductFulfillmentScenario . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1744
SalesTrxnDeleteEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1747
SalesTransactionFulfillReq . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1748
ValTfrm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1752
ValTfrmGrp . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1755
Dynamic Revenue Orchestrator Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . 1758
Decompose Sales Transaction Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1758
Freeze Sales Transaction Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1762
Get Point Of No Return Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1765
Orchestrate Sales Transaction Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1767
Orchestrate Transaction Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1771
Submit Order Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1773
Submit Sales Transaction Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1788
Unfreeze Sales Transaction Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1791
Dynamic Revenue Orchestrator Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1794
Flow for Dynamic Revenue Orchestrator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1794
DynamicFulfillmentOrchestratorSettings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1795
Dynamic Revenue Orchestrator Tooling API Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1797
CustomFulfillmentScopeCnfg . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1797
OrchestrationPlanCtxMapping . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1800
Callouts in Dynamic Revenue Orchestrator . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1803
Contents

===== PAGE 10 =====

Configure Callout Settings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1805
Standard Fulfillment Provider . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1805
Apex Type Provider . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1812
External Services Defined Provider . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1817
Asynchronous Interaction Pattern . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1817
Input and Output Transformation Processors . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1819
Dynamic Revenue Orchestrator Platform Events . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1820
FulfillmentSourceChangeEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1820
SalesTrxnDecompositionEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1821
Chapter 11: Usage Management . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1824
Usage Management Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1825
ProductUsageGrant . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1826
ProductUsageResource . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1833
ProductUsageResourcePolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1837
TransactionUsageEntitlement . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1839
UnitOfMeasure . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1849
UnitOfMeasureClass . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1851
UsageBillingPeriodItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1854
UsageCmtAssetRelatedObj . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1859
UsageCommitmentPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1861
UsageEntitlementAccount . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1863
UsageEntitlementBucket . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1866
UsageEntitlementEntry . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1871
UsageGrantRenewalPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1875
UsageGrantRolloverPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1877
UsageOveragePolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1879
UsagePrdGrantBindingPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1881
UsageRatableSummary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1882
UsageRatableSumCmtAssetRt . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1889
UsageResource . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1892
UsageResourcePolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1896
UsageResourceBillingPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1898
UsageSummary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1900
Usage Management Fields on Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1906
Usage Management Fields on Product2 . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1906
Usage Management Fields on TransactionJournal . . . . . . . . . . . . . . . . . . . . . . . . . 1907
Usage Management Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1908
Invoke Summary Creation Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1908
Process Consumption Overages Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1910
Refresh Usage Entitlement Bucket Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1911
Retrigger Entitlement Creation Process Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1912
Usage Management Business APIs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1914
Resources . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1915
Contents

===== PAGE 11 =====

Request Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1921
Response Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1922
Usage Management Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1972
Flow for Usage Management . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1972
IndustriesUsageSettings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1973
Chapter 12: Billing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1975
Billing Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1976
AccountingPeriod . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1980
BillingArrangement . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1984
BillingArrangementLine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1986
BillingBatchScheduler . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1988
BillingBatchFilterCriteria . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1994
BillingMilestonePlan . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 1999
BillingMilestonePlanItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2001
BillingPeriodItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2006
BillingPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2011
BillingSchedule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2014
BillingScheduleGroup . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2024
BillingTreatment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2035
BillingTreatmentItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2038
BsgRelationship . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2043
CreditMemo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2046
CreditMemoAddressGroup . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2055
CreditMemoInvApplication . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2057
CreditMemoLine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2061
CreditMemoLineInvoiceLine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2069
CreditMemoLineTax . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2074
DebitMemo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2081
DebitMemoAddress . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2088
DebitMemoLine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2090
DebitMemoLineTax . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2096
GeneralLedgerAccount . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2100
GeneralLedgerAcctAsgntRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2103
GeneralLdgrAcctPrdSummary . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2107
GeneralLedgerJrnlEntryRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2110
InvBatchDraftToPostedRun . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2111
Invoice . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2115
InvoiceAddressGroup . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2129
InvoiceBatchRun . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2130
InvoiceBatchRunCriteria . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2138
InvoiceBatchRunRecovery . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2141
InvoiceDocument . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2143
InvoiceLine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2146
Contents

===== PAGE 12 =====

InvoiceLineRelationship . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2158
InvoiceLineTax . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2162
LegalEntity . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2170
LegalEntyAccountingPeriod . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2172
PaymentBatchRun . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2176
PaymentLineInvoiceLine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2180
PaymentRetryRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2185
PaymentRetryRuleSet . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2188
PaymentSchedule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2191
PaymentSchedulePolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2196
PaymentScheduleTreatment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2199
PaymentScheduleTreatmentDtl . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2201
PymtSchdDistributionMethod . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2205
PaymentScheduleItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2207
PaymentTerm . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2214
PaymentTermItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2215
RevenueTransactionErrorLog . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2218
SeqPolicySelectionCondition . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2222
SequenceGapReconciliation . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2224
SequencePolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2226
TaxEngine . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2231
TaxEngineInteractionLog . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2234
TaxEngineProvider . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2239
TaxPolicy . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2241
TaxTreatment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2243
Tax Treatment Item . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2246
Billing Fields on Standard Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2249
Billing Fields on AccountBillingAccount . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2250
Billing Fields on BillingAccount . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2250
Billing Fields on CollectionPlan . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2256
Billing Fields on CollectionPlanItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2257
Billing Fields on ExpressionSet . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2257
Billing Fields on Dispute . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2258
Billing Fields on DisputeItem . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2261
Billing Fields on Payment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2262
Billing Fields on PaymentLineInvoice . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2264
Billing Fields on Refund . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2265
Billing Fields on RefundLinePayment . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2268
Billing Fields on TaxRate . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2269
Billing Fields on TransactionJournal . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2272
Salesforce Payments Objects in Billing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2277
Billing Platform Events . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2277
BillingScheduleCreatedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2278
CreditInvoiceProcessedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2282
Contents

===== PAGE 13 =====

CreditMemoProcessedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2286
InvoiceProcessedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2288
NegInvcLineProcessedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2294
SequenceAssignedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2297
VoidInvoiceProcessedEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2299
Billing Standard Invocable Actions . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2302
Apply Credit Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2304
Apply Payments and Credits by Rules Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2306
Create Billing Schedules From Billing Transaction Action . . . . . . . . . . . . . . . . . . . . . 2308
Create Standalone Billing Schedules Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2310
Extend Invoice Due Date Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2312
Generate Account Statement . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2314
Generate Invoice Documents Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2318
Issue Credit Memo Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2320
Post Draft Credit Memo Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2322
Post Draft Invoice Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2323
Post Draft Invoice Batch Run Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2325
Recover Billing Schedules Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2326
Suspend Billing Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2328
Update Bill To Contact Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2330
Unapply Credit Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2332
Unapply Payment Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2334
Void Posted Credit Memo Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2336
Write Off Invoices Action . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2338
Billing Business APIs . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2340
Billing Business API Limits . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2345
Resources . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2347
Request Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2424
Response Bodies . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2583
Billing Apex Reference . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2630
ConnectApi Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2632
InvoiceWriteOff Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2672
IssueCreditMemo Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2681
RulesAppln Namespace . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2689
TaxEngineAdapter Interface . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2697
Billing Metadata API Types . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2713
BillingSettings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2713
Flow for Billing . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2720
PaymentsSharingSettings . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2721
Chapter 13: Revenue Cloud Associated Objects . . . . . . . . . . . . . . . . . . . . . . . . . . . 2724
StandardObjectNameChangeEvent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2725
StandardObjectNameFeed . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2727
StandardObjectNameHistory . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2734
Contents

===== PAGE 14 =====

StandardObjectNameOwnerSharingRule . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2736
StandardObjectNameShare . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2738
Event . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2739
Task . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2760
Contents

===== PAGE 15 =====

