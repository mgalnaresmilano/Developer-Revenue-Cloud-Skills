---
name: revenue-cloud-developer
description: >-
  Guía completa de desarrollo Revenue Cloud (RLM): texto íntegro por capítulos
  del PDF Revenue Cloud Developer Guide v66 (PCM, Pricing, Configurator/CML,
  Transaction Management, Rate, DRO, Usage, Billing, despliegue,
  RevenueManagementSettings, APIs, Apex, invocables, modelo de datos y límites).
  Usar cuando el usuario trabaja en Revenue Cloud, configuración avanzada,
  integraciones, metadata, restricciones de API o despliegue entre orgs; o cuando
  cite la guía oficial de desarrolladores o Help Revenue Lifecycle Management.
---

# Revenue Cloud — guía de desarrollo (contenido exhaustivo)

## Fuentes

- **PDF técnico (contenido principal):** *Revenue Cloud Developer Guide* **v66.0 (Spring ’26)** — el texto completo (~2788 páginas) está en los archivos `reference-ch*.md` y `reference-00-*.md` (extracción automática del PDF).
- **Help (producto):** [Revenue Lifecycle Management](https://help.salesforce.com/s/articleView?id=ind.revenue_lifecycle_management.htm&type=5) — marco de producto; el cuerpo del artículo se carga en el navegador. Ver [reference-help-revenue-lifecycle-management.md](reference-help-revenue-lifecycle-management.md).

## Índice y guía de navegación

El **índice maestro**, el mapeo tema → archivo y las convenciones de búsqueda están en:

**[reference-guia-pdf-revenue-cloud.md](reference-guia-pdf-revenue-cloud.md)**

Allí se listan los **14 archivos** de referencia con el texto completo del PDF por capítulo (portada + capítulos 1–13).

### Resumen rápido: qué archivo abrir

| Necesidad | Archivo(s) |
|-----------|------------|
| Visión general de componentes y capacidades API | [reference-ch01-get-started-revenue-cloud-developer.md](reference-ch01-get-started-revenue-cloud-developer.md) |
| Flags org-wide `RevenueManagementSettings` | [reference-ch02-revenue-management-settings.md](reference-ch02-revenue-management-settings.md) |
| Despliegue, GUID, orden de objetos, tablas Setup/metadata | [reference-ch03-revenue-cloud-deployment.md](reference-ch03-revenue-cloud-deployment.md) |
| Catálogo, atributos, clasificaciones, Product Discovery | [reference-ch04-product-catalog-management.md](reference-ch04-product-catalog-management.md) |
| Precios, procedure plan, recetas, APIs de pricing, Apex pricing | [reference-ch05-salesforce-pricing.md](reference-ch05-salesforce-pricing.md) |
| Tarjetas de tarifa y rating | [reference-ch06-rate-management.md](reference-ch06-rate-management.md) |
| Reglas de configuración y **CML** | [reference-ch07-product-configurator.md](reference-ch07-product-configurator.md) |
| Quote/Order/Contract/Asset, eventos, APIs TM, Apex | [reference-ch08-transaction-management.md](reference-ch08-transaction-management.md) |
| Aprobaciones avanzadas | [reference-ch09-advanced-approvals.md](reference-ch09-advanced-approvals.md) |
| Orquestación de cumplimiento / DRO / callouts | [reference-ch10-dynamic-revenue-orchestrator.md](reference-ch10-dynamic-revenue-orchestrator.md) |
| Consumo y políticas de uso | [reference-ch11-usage-management.md](reference-ch11-usage-management.md) |
| Facturación, impuestos, límites de API de billing, Apex | [reference-ch12-billing.md](reference-ch12-billing.md) |
| Objetos asociados (histórico, feeds, Event/Task…) | [reference-ch13-revenue-cloud-associated-objects.md](reference-ch13-revenue-cloud-associated-objects.md) |
| Índice del PDF (Contents) | [reference-00-portada-indice-y-contenidos.md](reference-00-portada-indice-y-contenidos.md) |

## Mapa mental por área (resumen)

| Área | Contenido en la guía |
|------|----------------------|
| **PCM + Product Discovery** | Objetos, fields, Business/Metadata/Tooling APIs, búsqueda e índice |
| **Salesforce Pricing** | Objetos de ajuste y listas, APIs, invocables, Apex `RevSignaling`, recetas |
| **Product Configurator** | Reglas, flows, APIs, **Constraint Modeling Language** |
| **Transaction Management** | Ciclo de vida transaccional, eventos, muchas APIs y Apex |
| **Rate Management** | Rate cards, rating service |
| **DRO** | Fulfillment, descomposición, invocables, integraciones externas |
| **Usage Management** | Derechos, resúmenes, políticas |
| **Billing** | Facturas, pagos, notas, límites de API documentados |

## Instrucciones para el agente

1. **Priorizar los archivos `reference-chNN-*.md`** para cualquier detalle de desarrollo, configuración, modelo de datos o restricciones: contienen el texto de la guía oficial, no un resumen.
2. Usar **[reference-guia-pdf-revenue-cloud.md](reference-guia-pdf-revenue-cloud.md)** para orientarse y elegir el capítulo correcto antes de leer archivos muy grandes (sobre todo los capítulos 4, 5, 7, 8 y 12).
3. Respetar **nombres de API y metadata** exactamente como aparecen en el extracto (la extracción puede tener saltos de línea feos pero los identificadores deben ser fieles al PDF).
4. Para **preguntas de producto** (mensajes comerciales, habilitación de alto nivel), complementar con Help; para **implementación**, ceñirse al PDF/capítulos técnicos.
5. Si falta una versión más nueva del PDF en el futuro, regenerar los `reference-ch*.md` desde el PDF actualizado (ver sección “Regenerar” en el índice maestro).

## Referencias cruzadas

- Índice maestro y búsqueda por tema: [reference-guia-pdf-revenue-cloud.md](reference-guia-pdf-revenue-cloud.md)
- Help RLM y notas de extracción: [reference-help-revenue-lifecycle-management.md](reference-help-revenue-lifecycle-management.md)
- Help URL: https://help.salesforce.com/s/articleView?id=ind.revenue_lifecycle_management.htm&type=5
