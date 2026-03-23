# Índice maestro — Revenue Cloud Developer Guide (texto completo por capítulo)

Esta skill incluye el contenido de la guía **Revenue Cloud Developer Guide** (versión **66.0, Spring ’26**) **extraído íntegramente del PDF** (~2788 páginas), repartido en archivos `reference-ch*.md` para que el agente pueda abrir solo el capítulo relevante.

## Convenciones

- El texto está en **inglés** (idioma original de Salesforce).
- La extracción automática puede tener **saltos de línea** o espacios raros; los **nombres de API, objetos, campos y tipos de metadata** deben tomarse como en el original.
- Para **modelo de datos**: cada capítulo de objetos estándar documenta campos, relaciones, reglas y notas de uso.
- Para **restricciones y límites**: buscar en el capítulo correspondiente términos como *Special Access Rules*, *Validation*, *Considerations*, *Limits*, *Important*, *Note*.
- Para **configuración**: capítulo 3 (despliegue y rutas de Setup) + secciones *Metadata* / *Settings* dentro de cada área.

## Archivos de referencia (texto completo del PDF)

| Archivo | Contenido principal |
|---------|----------------------|
| [reference-00-portada-indice-y-contenidos.md](reference-00-portada-indice-y-contenidos.md) | Portada, copyright, **índice (Contents)** del PDF. |
| [reference-ch01-get-started-revenue-cloud-developer.md](reference-ch01-get-started-revenue-cloud-developer.md) | **Cap. 1** — Introducción a recursos de desarrollo por componente (PCM, Pricing, Configurator, TM, Usage, Rate, DRO, Billing). |
| [reference-ch02-revenue-management-settings.md](reference-ch02-revenue-management-settings.md) | **Cap. 2** — Tipo metadata `RevenueManagementSettings`: campos, versiones API, XML de ejemplo, manifiesto. |
| [reference-ch03-revenue-cloud-deployment.md](reference-ch03-revenue-cloud-deployment.md) | **Cap. 3** — Despliegue: flujos full/incremental, GUID, estados de componentes, escenarios, **orden de objetos** por área, **tablas de metadata** (rutas Setup, permisos, Decision Tables, prerequisitos Omnistudio/Discovery, etc.). |
| [reference-ch04-product-catalog-management.md](reference-ch04-product-catalog-management.md) | **Cap. 4** — PCM: objetos estándar y campos en objetos estándar, **Business APIs**, **Metadata API**, **Tooling API**, **Product Discovery** (APIs, invocables, Apex, metadata). |
| [reference-ch05-salesforce-pricing.md](reference-ch05-salesforce-pricing.md) | **Cap. 5** — Objetos de precios (listado del índice: ajustes, listas de precios, recetas, procedure plan…), APIs (resources, request/response bodies), **Apex RevSignaling**, invocables, **Tooling API**, metadata (`IndustriesPricingSettings`, `PricingRecipe`, etc.). |
| [reference-ch06-rate-management.md](reference-ch06-rate-management.md) | **Cap. 6** — Objetos de Rate Management, metadata, Business APIs, invocable **Invoke Rating Service**. |
| [reference-ch07-product-configurator.md](reference-ch07-product-configurator.md) | **Cap. 7** — Objetos del configurador, APIs, invocables, **Constraint Modeling Language (CML)** completo (conceptos, ejemplos, buenas prácticas, depuración). |
| [reference-ch08-transaction-management.md](reference-ch08-transaction-management.md) | **Cap. 8** — Activos, cotizaciones, pedidos, contratos, campos TM en objetos estándar, **Platform Events**, **Business APIs**, **Apex** (CommerceOrders, ConnectApi, PlaceQuote, RevSalesTrxn…), invocables (amendment, renewal, cancel, create order from quote…), metadata. |
| [reference-ch09-advanced-approvals.md](reference-ch09-advanced-approvals.md) | **Cap. 9** — ApprovalSubmission, campos en Approval Work Item, invocables, metadata/Flow. |
| [reference-ch10-dynamic-revenue-orchestrator.md](reference-ch10-dynamic-revenue-orchestrator.md) | **Cap. 10** — Objetos DRO, invocables, metadata, **callouts** (configuración, proveedores), **Platform Events**. |
| [reference-ch11-usage-management.md](reference-ch11-usage-management.md) | **Cap. 11** — Objetos de uso/consumo, campos en Product2 y TransactionJournal, invocables, APIs, metadata (`IndustriesUsageSettings`). |
| [reference-ch12-billing.md](reference-ch12-billing.md) | **Cap. 12** — Objetos de facturación e impuestos, campos en objetos estándar, eventos, invocables, **Billing Business API Limits**, **Apex** (ConnectApi, InvoiceWriteOff, IssueCreditMemo…), metadata (`BillingSettings`, etc.). |
| [reference-ch13-revenue-cloud-associated-objects.md](reference-ch13-revenue-cloud-associated-objects.md) | **Cap. 13** — Objetos asociados (histórico, feeds, sharing, Event, Task, etc.). |

## Cómo buscar por tema (sin leer 2788 páginas a mano)

1. **Desarrollo (APIs, Apex, invocables)**  
   - Usar el capítulo del área (4–12) y buscar subsecciones *Business APIs*, *Apex Reference*, *Invocable Actions*, *Connect API*.

2. **Configuración (Setup, permisos, flags, rutas)**  
   - **Cap. 3** — tablas *Metadata Deployment Reference* y *Additional Deployment Information* por producto.  
   - **Cap. 2** — `RevenueManagementSettings`.  
   - Cada capítulo de producto incluye metadata types y a veces *Flow for …*.

3. **Modelo de datos (objetos, campos, relaciones)**  
   - Secciones *Standard Objects* y *Fields on Standard Objects* en el capítulo correspondiente (p. ej. *Transaction Management Standard Objects*, *Billing Standard Objects*).

4. **Restricciones, reglas de acceso, consideraciones**  
   - Campos *Special Access Rules*, *General Considerations*, notas *Important* / *Note* en cada objeto o tipo de metadata.  
   - **Cap. 3** — dependencias de despliegue y escenarios de validación.  
   - **Cap. 12** — *Billing Business API Limits* y condiciones de uso de APIs.

5. **Product Discovery, Pricing Procedure, CML, DRO**  
   - Cap. 4 (Discovery), Cap. 5 (Pricing), Cap. 7 (CML), Cap. 10 (DRO).

## Tamaño aproximado de los archivos

Los capítulos 4, 5, 7, 8 y 12 son los más voluminosos (decenas de miles de líneas de texto extraído). El agente debe **abrir solo el archivo del capítulo** necesario para la pregunta concreta.

## Regenerar el extracto (mantenimiento)

Si Salesforce publica una nueva versión del PDF:

1. Sustituir el archivo PDF de origen.
2. Ejecutar extracción con `pypdf` (u otra herramienta) a un `.txt` monolítico.
3. Volver a partir por líneas de `CHAPTER N` como en el script de partición usado para generar estos `reference-ch*.md`.

## Help de producto (no sustituye al PDF técnico)

- [reference-help-revenue-lifecycle-management.md](reference-help-revenue-lifecycle-management.md) — artículo Help *Revenue Lifecycle Management* y limitaciones de extracción web.
