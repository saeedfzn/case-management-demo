# Citizen case management: a Power Platform concept demo

**Live demo:** https://saeedfzn.github.io/case-management-demo/

A clickable concept of a case-management app for a fictional council repairs service ("Northbrook Council"). I built it for a Power Platform Developer application on a public-sector CRM transformation. It covers:

1. **A working case app (simulated).** Log a case with validation (UK postcode format, a simulated postcode lookup, email or phone, a damp-and-mould priority rule and a duplicate check). Work a queue with SLA timers (on track, at risk, breached, paused) and assign cases. The SLA targets and the damp-and-mould rule are illustrative local policy, not a statement of the law. Move a case through New, Triage, In progress, Awaiting citizen, Resolved and Closed, add notes, and read the full audit history.
2. **Security roles.** Switch between caseworker, team leader and read-only auditor. One rule function decides every permission, and each action re-checks it. The permission matrix on the page is generated from that same function.
3. **Automations (simulated).** An acknowledgement on create, SLA warnings and a breach escalation (advance the demo clock to trigger them), and a weekly summary, all with a run log.
4. **Legacy migration dry run.** A messy CSV export is mapped to the new model. The dry run handles duplicates, invalid postcodes, bad or missing dates, unknown codes and contact merging, and reports what is migrated, flagged and rejected. You can edit the CSV and run it again.
5. **Dataverse / Dynamics 365 design notes.** The table model, relationships, lifecycle mapping, business rules, security roles and team ownership, environments and ALM, UK GDPR notes and a REST integration sketch (OpenAPI 2.0, as custom connectors require).
6. **Agile and testing.** Sample user stories with Gherkin acceptance criteria. The test log's 17 unit tests run live in the browser against the page's own logic.

## What this is

It's plain HTML, CSS and JavaScript in one file (`index.html`), with no dependencies and no build step. All the data is synthetic and deterministic, and the demo clock is fixed at Tue 17 Nov 2026 09:00. NB postcodes are fictional.

The real build would be a Power Apps model-driven app on Dataverse (or Dynamics 365 Customer Service) with Power Automate. The Dataverse and D365 sections are **design**.

| Demo piece | Real build |
|---|---|
| Case form, queue, detail | Model-driven app: forms, views, timeline, business process flow |
| Case data | Dataverse: Case (incident), Contact, Account, Property (custom), notes and activities |
| Roles | Dataverse security roles, business units, owner teams, column-level security |
| SLA timers | Customer Service SLAs: SLA KPIs and SLA items with warning and failure times, pause and resume |
| Flow run log | Power Automate cloud flows |
| Migration dry run | Data migration tooling chosen with the architect, using the same mapping and rules |

## About me

I'm Faizaan Saeed, a Power Platform developer based in Swindon. On a 15-day contract I built a stock-control system for a satellite/RF manufacturer. It has a 14-screen Power Apps canvas app on 7 SharePoint lists, 6 Power Automate flows, Office Scripts reports and a dashboard. It also has role-based access, an append-only transaction ledger, 56 versioned releases, test scenarios, UAT and user, admin and technical guides. It was signed off.

[LinkedIn](https://www.linkedin.com/in/faizaan-saeed-ba96a426b) · [Portfolio](https://saeedfzn.github.io/)

Microsoft, Power Apps, Power Automate, Dataverse, Dynamics 365 and Microsoft Entra are trademarks of the Microsoft group of companies. This is an independent demo, not affiliated with or endorsed by Microsoft.
