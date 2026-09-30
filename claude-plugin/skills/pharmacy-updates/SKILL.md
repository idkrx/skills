---
name: pharmacy-updates
description: Post a pharmacy's own verified medication availability or its public notice on IdkRx. Use when someone who works at a pharmacy on an IdkRx rep plan asks to mark a medication available, limited or out of stock, or to post, change or clear the notice on their pharmacy's page.
---

These actions are for pharmacy staff whose IdkRx account has an active rep plan and permission to post. What they write is public on the pharmacy's IdkRx page the moment it is confirmed, so every write is previewed first.

If the IdkRx connector is not connected, ask the person to connect it on the IdkRx plugin's Connectors tab, or follow the `connect-idkrx` skill when the plugin is not installed. If `rep_set_psa` is missing from your tools, the account has no active rep plan with permission to post: say so, rather than trying another tool.

To post a verified status, use `report_availability`, the same tool as a community report:

1. Split what the person said into fields, as the `report-availability` skill describes: the medication on its own, the strength, the form, and the pharmacy if they named one. Pharmacy staff with one pharmacy need not name it; the tool fills in their own. Always send their words verbatim as `utterance`.
2. Send `channel: "verified"` when the person clearly speaks for the pharmacy ("we're out of amoxicillin"). When it is unclear, leave `channel` out: the tool offers the choice between a verified status and a community report, and the person picks.
3. Statuses are words: `available`, `limited` or `unavailable`. A verified status may also carry `durationDays` (how long it stays up, default 7) and a short public `note`. It carries no price or restock date; those belong to community reports.
4. The first call returns a form naming the pharmacy and medication and writes nothing. Show it. A medication the pharmacy does not track yet is tracked when the status is posted, and the form says so.
5. Call again with the same arguments and `confirm: true` only after the person approves. A verified status replaces the one already up for the same medication, form and strength.

To change the public notice with `rep_set_psa`:

1. Send only the fields they asked to change: the notice text (up to 280 characters), operating status, staffing, prescription turnaround, or when the notice clears. Send `psa: null` to clear the notice.
2. The first call shows the current and the new notice side by side and writes nothing. Show both.
3. Call again with `confirm: true` only after the person approves.

If the person works at more than one pharmacy, `rep_set_psa` lists them by name; ask which, then call again with `pharmacy` set to the choiceId or the name it listed. Never choose for them.
