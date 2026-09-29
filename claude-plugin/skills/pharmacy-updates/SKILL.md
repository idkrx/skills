---
name: pharmacy-updates
description: Post a pharmacy's own verified medication availability or its public notice on IdkRx. Use when someone who works at a pharmacy on an IdkRx rep plan asks to mark a medication available, limited or out of stock, or to post, change or clear the notice on their pharmacy's page.
---

These tools appear only for pharmacy staff whose IdkRx account has an active rep plan and permission to post. What they write is public on the pharmacy's IdkRx page the moment it is confirmed, so every write is previewed first.

If the IdkRx connector is not connected, ask the person to connect it on the IdkRx plugin's Connectors tab, or follow the `connect-idkrx` skill when the plugin is not installed. If it is connected but these tools are missing, the account has no active rep plan with permission to post: say so, rather than trying another tool.

To set a verified status with `rep_set_verified_status`:

1. Name the medication the way the person did, and the status: `av` (available), `li` (limited) or `un` (unavailable). Only medications the pharmacy already tracks can carry a status; if the tool offers choices, ask which one they mean.
2. The first call returns a preview and writes nothing. Show it.
3. Call again with the same arguments and `confirm: true` only after the person approves.

To change the public notice with `rep_set_psa`:

1. Send only the fields they asked to change: the notice text (up to 280 characters), operating status, staffing, prescription turnaround, or when the notice clears. Send `psa: null` to clear the notice.
2. The first call shows the current and the new notice side by side and writes nothing. Show both.
3. Call again with `confirm: true` only after the person approves.

If the person works at more than one pharmacy, the tool asks which one. Never choose for them.
