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
