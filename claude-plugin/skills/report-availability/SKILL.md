---
name: report-availability
description: Report whether a pharmacy has a medication in stock on IdkRx. Use when the person says a pharmacy has, is out of, or is low on a medication, asks to report or update a pharmacy's stock, or mentions a shortage they saw at a specific store.
---

Reporting goes through the IdkRx connector's `report_availability` tool, and nothing is saved until the person confirms it.

If `report_availability` is not among your tools, the connector is not connected yet. With the IdkRx plugin installed, ask the person to connect IdkRx on the plugin's Connectors tab; otherwise follow the `connect-idkrx` skill. Then continue here.

1. Split what the person said into separate fields: the medication name on its own, the strength, the form, the pharmacy or chain name, and the place (city, state, ZIP, a street or a store number). Leave out anything they did not say. Never invent a city, a strength or a form to fill a field. Always also send their words verbatim as `utterance`.
2. Call `report_availability` with those fields. It writes nothing on this call.
3. If it answers with a form naming one pharmacy and one medication, let the person choose the status (available, limited or unavailable) and submit it there. If you submit on their behalf, repeat back what will be filed and send `confirm: true` only after they agree.
4. If it answers with choices, show them and ask which one is right. Call again with the `resolutionToken` and the `choiceId` they picked. Never pick for them.
5. Reply with what was filed, in one sentence.

This tool never returns what a pharmacy currently has. If the person asks what is in stock somewhere, say that IdkRx's site shows it and do not call the tool.
