# Claims Processing Platform

## General objective
Design and implement an enterprise-oriented claims management platform for insurance, where requests are processed asynchronously and reliably using API Management + Service Bus + Functions, ensuring traceability, error handling (DLQ), secret security, and observability.

## Specific objectives
 * APIM as the entry point (minimal policies and correlation).
 * App Service (.NET API) receives the claim and publishes a command to Service Bus.
 * Functions consume commands and update the claim status in Azure SQL.
 * DLQ enabled and demonstrated (“poison” message) + reprocessing runbook.
 * Observability with App Insights (latency, errors, dependencies) + minimal alerts.
 * Security: secrets outside the repository (Key Vault/Managed Identity in phase 2; documented MVP).

## Arquitectura (alto nivel)
- **Entrada**: Azure API Management (APIM)
- **API**: Azure App Service (`Claims.Api`)
- **Procesamiento async**: Azure Functions (`Claims.ProcessorFn`, `Claims.NotificationsFn`)
- **Mensajería**: Azure Service Bus (Queue + Topic + DLQ)
- **Datos**: Azure SQL Database
- **Seguridad**: Managed Identity + Key Vault
- **Observabilidad**: Application Insights + Log Analytics

Diagramas: ver `docs/c4/`.

## Requisitos no funcionales (NFR)
Ver `docs/nfr/` (seguridad, resiliencia, costo, observabilidad).

## ADRs (decisiones)
Ver `docs/adrs/` (Architecture Decision Records).

## Contratos
- Esquemas de eventos/mensajes: `docs/contracts/`

## Cómo correr local
> se Completara cuando exista docker-compose o configuración local mínima.

## Cómo desplegar en Azure (Bicep)
- Scripts y plantillas: `infra/bicep/`
- Requisitos: Azure CLI + permisos

## Observabilidad
- Dashboards, alertas y runbooks: `docs/runbooks/`

## Demo para entrevistas
- Guion, Q&A y casos: `docs/interview/`

## Licencia
MIT
