# Help: Revenue Lifecycle Management (referencia de producto)

## URL canónica (Salesforce Help)

- Versión con parámetros de la petición del usuario:  
  https://help.salesforce.com/s/articleView?id=ind.revenue_lifecycle_management.htm&type=5
- Variante con idioma explícito (según Salesforce):  
  https://help.salesforce.com/s/articleView?id=ind.revenue_lifecycle_management.htm&language=en_US&type=5

## Cómo usar este artículo junto al PDF de desarrollador

- El artículo **Revenue Lifecycle Management** en Help describe el **producto** (alcance funcional, habilitación en la org, relación con el recorrido de ingresos en Salesforce).
- El PDF **Revenue Cloud Developer Guide** (v66) es la **referencia técnica**: objetos, APIs, metadata, Apex, eventos, secuencias de despliegue.

Para desarrollo (Apex, metadata, integraciones, despliegues), priorizar el **PDF** y esta skill. Para preguntas de **qué es RLM**, **beneficios** o pasos de **alta nivel en la plataforma**, abrir el artículo Help en el navegador.

## Limitación de extracción automática

- Las páginas de `help.salesforce.com` suelen ser **aplicaciones de una sola página (SPA)**. Un fetch HTTP simple devuelve principalmente el shell HTML; el cuerpo del artículo se hidrata por JavaScript.
- Por tanto, **no** se debe asumir que un scraper sin navegador contiene el texto íntegro del artículo. Para citas textuales exactas, usar el navegador o herramientas de documentación Salesforce (p. ej. extracción con renderizado, según política de la organización).

## Alineación conceptual con Revenue Cloud (desde el PDF)

El PDF presenta Revenue Cloud como conjunto de componentes **API-first** para el ciclo **producto–efectivo**: catálogo y descubrimiento de productos, precios, configuración, transacciones (cotización/pedido/contrato/activo), orquestación de cumplimiento, consumo/tarifas y facturación. El artículo Help de **Revenue Lifecycle Management** encaja como capa de **visión de producto** sobre ese mismo ecosistema; validar siempre definiciones actualizadas en Help.
