# 👻 Replit Ghost-Buster — Support Ops Triage Console

**Built for the Replit Social Media Support Specialist application · by [Sefket Nouri](https://replit.com/@sefketnouri)**

A deployment health monitor and social ticket triage tool that demonstrates the full support workflow: inbound social complaint → endpoint diagnosis → structured engineering hand-off.

🔗 **Live demo:** [replit-ghost-buster on Replit](https://replit.com/@sefketnouri/replit-ghost-buster)

---

## What It Does

This tool simulates the exact workflow a Replit support specialist runs when a user reports a deployment issue on X, Reddit, LinkedIn, or the App Stores.

### Step 1 — Social Ticket Intake
Paste any inbound user complaint. The tool automatically:
- Detects the platform (𝕏 Twitter, Reddit, LinkedIn, Apple & Google Play)
- Classifies the issue type (503 / 500 / 404 / Billing / Performance / Secrets)
- Assigns a priority (P1 Critical → P3 Low)
- Extracts any Replit endpoint URL from the message
- Suggests the correct routing (Tier 1 response, Tier 2 triage, or direct Engineering escalation)

### Step 2 — Diagnose
Pings the reported endpoint every 30 seconds and streams live deployment logs. On failure, it surfaces the specific error code and suggests a concrete support action — e.g., *"Check `.replit` run command"* or *"Restart Nix environment"* — matching Replit's actual troubleshooting playbook.

### Step 3 — Generate Internal Brief
One click produces a structured Markdown engineering hand-off ticket containing:
- Severity level (SEV-1 / SEV-2 / SEV-3)
- The original social complaint with user handle and platform
- HTTP error detail and stack trace
- Environment variable audit (`REPLIT_DB_URL`, `TOKEN`, `NODE_ENV`, etc.)
- Resolution checklist
- Escalation path (Tier 1 → Tier 2 → Engineering)

---

## Why This Exists

Most support candidates submit writing samples. This demonstrates **systems thinking** — specifically, how I'd reduce ambiguity in engineering escalations and cut the back-and-forth that slows incident resolution.

The "Generate Internal Brief" feature directly maps to the JD requirement: *"Escalate and coordinate resolutions with internal teams."* The social intake panel maps to: *"Manage customer inquiries across X, LinkedIn, Reddit, and app stores."*

---

## Tech

Single-file static HTML/JS — no build step, no dependencies. Intentionally minimal so the logic is readable, not hidden behind a framework.

- JetBrains Mono font (matches Replit's own IDE aesthetic)
- Polling via `fetch` with `AbortSignal` timeout
- Regex-based URL and issue-type extraction from complaint text
- Markdown ticket generation with severity classification

---

## Platforms Covered

| Platform | Intake | Example Complaints |
|---|---|---|
| 𝕏 Twitter | ✅ | Deployment 503s, outages |
| Reddit | ✅ | Server errors, env config |
| LinkedIn | ✅ | Billing disputes |
| Apple & Google Play | ✅ | App store reviews |

---

## Running Locally

```bash
open index.html
```

No server required — open directly in any browser.

---

*Built by [Sefket Nouri](https://replit.com/@sefketnouri) as part of the Replit Social Media Support Specialist application.*
