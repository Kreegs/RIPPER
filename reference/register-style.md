# Risk Register HTML Template

This is the canonical HTML output format for RIPPER. All full risk register responses must follow this structure and styling exactly. The example below is populated with data from the MKR Motor Controller Development and SBR Migration project.

---

## Structure

1. **`<header>`** — dark background block containing project metadata table and priority tier summary badges
2. **Risk Summary table** — all risks in one view, sorted critical first, ID links to detail card
3. **Risk Detail cards** — one `<article>` per risk, grouped by tier with a section label, left border color-coded by priority
4. Resolved and accepted risks appear in a separate section below active risks (not shown in this example as none are resolved yet)

## CSS Classes

| Class | Tier | Border / Badge color |
|-------|------|----------------------|
| `.critical` | Score 15–25 | Red `#dc2626` / badge `#fee2e2` |
| `.high` | Score 8–14 | Orange `#ea580c` / badge `#ffedd5` |
| `.medium` | Score 4–7 | Amber `#ca8a04` / badge `#fef9c3` |
| `.low` | Score 1–3 | Green `#16a34a` / badge `#dcfce7` |

---

## Full Template (MKR Project — Example Output)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Risk Register — [Project Name]</title>
  <style>
    body { font-family: system-ui, -apple-system, sans-serif; max-width: 1100px; margin: 0 auto; padding: 2rem; color: #1a1a2e; background: #f8f9fa; }
    header { background: #1a1a2e; color: white; padding: 1.75rem 2rem; border-radius: 8px; margin-bottom: 2rem; }
    header h1 { margin: 0 0 1rem 0; font-size: 1.5rem; font-weight: 700; }
    .meta { border-collapse: collapse; color: #cbd5e1; font-size: 0.85rem; }
    .meta th { text-align: left; font-weight: 400; padding: 0.15rem 1.25rem 0.15rem 0; color: #94a3b8; }
    .meta td { font-weight: 500; color: #e2e8f0; }
    .summary { display: flex; gap: 0.75rem; margin-top: 1.25rem; flex-wrap: wrap; align-items: center; }
    .badge { display: inline-block; padding: 0.3rem 0.85rem; border-radius: 4px; font-size: 0.75rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.06em; }
    .critical { background: #fee2e2; color: #991b1b; }
    .high { background: #ffedd5; color: #9a3412; }
    .medium { background: #fef9c3; color: #854d0e; }
    .low { background: #dcfce7; color: #166534; }
    .total { font-size: 0.85rem; color: #94a3b8; margin-left: 0.5rem; }
    h2 { font-size: 1.1rem; color: #1a1a2e; border-bottom: 2px solid #e2e8f0; padding-bottom: 0.4rem; margin: 2rem 0 1rem; }
    table.register { width: 100%; border-collapse: collapse; font-size: 0.85rem; }
    table.register th { background: #1e293b; color: #e2e8f0; padding: 0.65rem 0.75rem; text-align: left; font-weight: 600; font-size: 0.8rem; text-transform: uppercase; letter-spacing: 0.04em; }
    table.register td { padding: 0.55rem 0.75rem; border-bottom: 1px solid #e2e8f0; vertical-align: middle; }
    table.register tr:hover td { background: #f1f5f9; }
    table.register a { color: #2563eb; text-decoration: none; font-weight: 700; font-size: 0.8rem; }
    .score-cell { font-weight: 700; font-size: 0.95rem; }
    .risk-card { background: white; border-radius: 6px; padding: 1.5rem 1.75rem; margin-bottom: 1.25rem; border-left: 5px solid #ccc; box-shadow: 0 1px 3px rgba(0,0,0,0.07); }
    .risk-card.critical { border-left-color: #dc2626; }
    .risk-card.high { border-left-color: #ea580c; }
    .risk-card.medium { border-left-color: #ca8a04; }
    .risk-card.low { border-left-color: #16a34a; }
    .card-header { display: flex; align-items: baseline; gap: 0.75rem; margin-bottom: 1.25rem; }
    .card-header h3 { margin: 0; font-size: 1rem; color: #1a1a2e; }
    dl { display: grid; grid-template-columns: 170px 1fr; gap: 0.6rem 1.25rem; margin: 0; }
    dt { font-weight: 600; color: #64748b; font-size: 0.8rem; text-transform: uppercase; letter-spacing: 0.04em; padding-top: 0.15rem; }
    dd { margin: 0; font-size: 0.875rem; color: #1a1a2e; line-height: 1.5; }
    .divider { border: none; border-top: 1px solid #e2e8f0; margin: 1.5rem 0; }
    .section-label { font-size: 0.7rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.08em; color: #94a3b8; margin: 2.5rem 0 0.5rem; }
  </style>
</head>
<body>

<header>
  <h1>Project Risk Register</h1>
  <table class="meta">
    <tr><th>Project</th><td>MKR Motor Controller Development and SBR Migration</td></tr>
    <tr><th>Analysis date</th><td>June 2026</td></tr>
    <tr><th>Input source</th><td>reference/Project-files/demo-project.md</td></tr>
  </table>
  <div class="summary">
    <span class="badge critical">Critical: 4</span>
    <span class="badge high">High: 9</span>
    <span class="badge medium">Medium: 2</span>
    <span class="badge low">Low: 0</span>
    <span class="total">15 risks identified</span>
  </div>
</header>

<h2>Risk Summary</h2>
<table class="register">
  <thead>
    <tr>
      <th>ID</th>
      <th>Risk Description</th>
      <th>Category</th>
      <th>Probability</th>
      <th>Impact</th>
      <th>Score</th>
      <th>Priority</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><a href="#R01">R01</a></td><td>8-month hard deadline with no float</td><td>Schedule</td><td>4</td><td>5</td><td class="score-cell">20</td><td><span class="badge critical">Critical</span></td><td>Open</td></tr>
    <tr><td><a href="#R02">R02</a></td><td>Engineering lead is sole designer with no dedicated capacity</td><td>Resource</td><td>4</td><td>5</td><td class="score-cell">20</td><td><span class="badge critical">Critical</span></td><td>Open</td></tr>
    <tr><td><a href="#R03">R03</a></td><td>Key components not yet ordered; long lead times likely</td><td>External</td><td>4</td><td>5</td><td class="score-cell">20</td><td><span class="badge critical">Critical</span></td><td>Open</td></tr>
    <tr><td><a href="#R04">R04</a></td><td>FCC certification timeline outside Alltrax control</td><td>External</td><td>4</td><td>4</td><td class="score-cell">16</td><td><span class="badge critical">Critical</span></td><td>Open</td></tr>
    <tr><td><a href="#R05">R05</a></td><td>Customer qualification timelines driven by customers, not Alltrax</td><td>External</td><td>3</td><td>4</td><td class="score-cell">12</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R06">R06</a></td><td>Contract penalty clauses active across all four customers</td><td>External</td><td>3</td><td>4</td><td class="score-cell">12</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R07">R07</a></td><td>New processor: first-time integration on new PCB</td><td>Technical</td><td>3</td><td>4</td><td class="score-cell">12</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R08">R08</a></td><td>Manufacturing capacity not formally reserved for MKR builds</td><td>Resource</td><td>4</td><td>3</td><td class="score-cell">12</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R09">R09</a></td><td>No contingency budget allocated</td><td>Budget</td><td>4</td><td>3</td><td class="score-cell">12</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R10">R10</a></td><td>FCC pre-certification failure requires retest and resubmission</td><td>Technical</td><td>3</td><td>3</td><td class="score-cell">9</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R11">R11</a></td><td>Pacific Electric Vehicles NEV/LSV regulatory dependency</td><td>External</td><td>3</td><td>3</td><td class="score-cell">9</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R12">R12</a></td><td>New power stage: first-time integration</td><td>Technical</td><td>3</td><td>3</td><td class="score-cell">9</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R13">R13</a></td><td>Form factor constraints are contractual; any deviation requires amendment</td><td>Scope</td><td>2</td><td>4</td><td class="score-cell">8</td><td><span class="badge high">High</span></td><td>Open</td></tr>
    <tr><td><a href="#R14">R14</a></td><td>Budget not formally established</td><td>Budget</td><td>3</td><td>2</td><td class="score-cell">6</td><td><span class="badge medium">Medium</span></td><td>Open</td></tr>
    <tr><td><a href="#R15">R15</a></td><td>Single-PCB dual-SKU: manufacturing differentiation at stuffing stage</td><td>Technical</td><td>2</td><td>3</td><td class="score-cell">6</td><td><span class="badge medium">Medium</span></td><td>Open</td></tr>
  </tbody>
</table>

<h2>Risk Details</h2>

<!-- CRITICAL RISKS -->
<p class="section-label">Critical</p>

<article id="R01" class="risk-card critical">
  <div class="card-header">
    <span class="badge critical">Critical — Score 20</span>
    <h3>R01 — 8-month hard deadline with no float</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>The 8-month project deadline is fixed by physical SBR component inventory. When inventory is exhausted, SBR production stops regardless of MKR readiness. This is a physical constraint, not a business preference. There is no float on this deadline.</dd>
    <dt>Category</dt>
    <dd>Schedule</dd>
    <dt>Probability</dt>
    <dd>4 (Likely) — The timeline contains multiple sequential external dependencies — FCC certification, four separate customer qualifications — each of which could individually cause a slip. Cascading delays are more likely than not over an 8-month window.</dd>
    <dt>Impact</dt>
    <dd>5 (Critical) — If MKR is not production-ready before SBR inventory is exhausted, Alltrax cannot fulfill orders for any of the four OEM customers simultaneously, triggering contract penalties and supply disruption across all active OEM relationships.</dd>
    <dt>Mitigation</dt>
    <dd>Build a full project schedule mapping all milestones against the Month 8 constraint. Identify the critical path. Target Month 7 as the internal completion gate for all production readiness activities, preserving a 4-week operational buffer.</dd>
    <dt>Contingency</dt>
    <dd>If a slip becomes likely, prioritize customers with shortest qualification lead times (Summit Industrial: 2–3 weeks) for earliest cutover. Assess whether temporary bridge supply or inventory reallocation can cover the highest-volume customers during a transition gap.</dd>
    <dt>Owner</dt>
    <dd>Director of Sales and Operations</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R02" class="risk-card critical">
  <div class="card-header">
    <span class="badge critical">Critical — Score 20</span>
    <h3>R02 — Engineering lead is sole designer with no dedicated capacity</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>The Director of Engineering is the sole hardware and firmware designer for this project. No dedicated project engineering resource exists. This individual simultaneously owns production support, warranty escalations, and two other active development projects.</dd>
    <dt>Category</dt>
    <dd>Resource</dd>
    <dt>Probability</dt>
    <dd>4 (Likely) — Four concurrent responsibilities over an 8-month timeline makes capacity conflicts highly probable. Any production support escalation or warranty issue will compete directly with MKR milestone work.</dd>
    <dt>Impact</dt>
    <dd>5 (Critical) — Hardware design, PCB layout, and firmware development cannot proceed without this individual. Delay at any engineering milestone — schematic, layout, bring-up, validation — cascades to every downstream milestone including FCC testing and customer samples.</dd>
    <dt>Mitigation</dt>
    <dd>Formally allocate a defined percentage of this individual's capacity to MKR and document it. Sequence competing project commitments to protect MKR milestones at Month 2 (hardware design) and Month 3.5 (firmware bring-up). Evaluate whether any engineering tasks — PCB layout review, test fixture design, documentation — can be offloaded to a contract resource.</dd>
    <dt>Contingency</dt>
    <dd>If engineering lead availability is disrupted, engage a contract hardware or firmware engineer immediately. Identify candidate firms before the project begins rather than searching under timeline pressure.</dd>
    <dt>Owner</dt>
    <dd>Owner (project sponsor)</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R03" class="risk-card critical">
  <div class="card-header">
    <span class="badge critical">Critical — Score 20</span>
    <h3>R03 — Key components not yet ordered; long lead times likely</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>The new processor and new power stage — the two components replacing the EOL SBR parts — have been identified but purchase orders have not been placed. Electronic component lead times frequently run 12–26+ weeks. PCB fabrication is targeted at Month 3, meaning components must arrive substantially before that milestone.</dd>
    <dt>Category</dt>
    <dd>External</dd>
    <dt>Probability</dt>
    <dd>4 (Likely) — Long lead times on electronic components are the industry norm. No order placed means no confirmed delivery date. The longer the delay in ordering, the higher the probability of a timeline impact.</dd>
    <dt>Impact</dt>
    <dd>5 (Critical) — Without the key components, prototype PCB assembly cannot begin. Every downstream milestone — firmware bring-up, internal validation, FCC testing, customer sample units — is blocked until components arrive.</dd>
    <dt>Mitigation</dt>
    <dd>Place purchase orders for the new processor and power stage immediately. Procure safety stock quantities covering prototype builds, first production run, and potential rework. Confirm lead times with suppliers before finalizing the project schedule. If lead times are unacceptable, evaluate alternate suppliers or alternate component selection now.</dd>
    <dt>Contingency</dt>
    <dd>If lead times exceed the available window, assess expedite options. Note that any component substitution at this stage has design implications — pin compatibility, thermal characteristics, and firmware driver support must all be re-evaluated before a substitute is committed.</dd>
    <dt>Owner</dt>
    <dd>Director of Engineering</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R04" class="risk-card critical">
  <div class="card-header">
    <span class="badge critical">Critical — Score 16</span>
    <h3>R04 — FCC certification timeline outside Alltrax control</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>FCC certification is required for the MKR-BT SKU before it can ship to production customers. Typical FCC grant timelines run 8–16 weeks from submission. The project targets submission at Month 4.5 and grant receipt at Month 6 — a 6-week window that is shorter than the minimum typical timeline. Customer A (GreenTech Mobility) and Customer B (Pacific Electric Vehicles) both require the MKR-BT SKU and cannot begin qualification until samples are received.</dd>
    <dt>Category</dt>
    <dd>External</dd>
    <dt>Probability</dt>
    <dd>4 (Likely) — The target grant window (6 weeks) is shorter than the stated minimum typical timeline (8 weeks). The schedule has no margin for a standard-length FCC review, and any pre-certification failure that delays submission compounds this further.</dd>
    <dt>Impact</dt>
    <dd>4 (Major) — FCC grant delay holds MKR-BT samples from Customer A (needs 6–8 weeks to qualify) and Customer B (needs 4–6 weeks). Both qualification windows must complete before Month 8. A delayed grant eliminates the qualification buffer for both customers simultaneously.</dd>
    <dt>Mitigation</dt>
    <dd>Engage an FCC test lab immediately — lab scheduling adds lead time on top of the review timeline. Review FCC requirements during the PCB layout phase, not after fabrication. Follow Bluetooth module manufacturer reference layout exactly. Design pre-certification testing to allow time for one correction cycle before submission.</dd>
    <dt>Contingency</dt>
    <dd>If grant is delayed beyond Month 6, assess whether Customer A and B can accept MKR (non-BT SKU) as interim supply to avoid disruption, with MKR-BT shipments to follow once certified. Begin this conversation by Month 5 — not after the delay is confirmed.</dd>
    <dt>Owner</dt>
    <dd>Director of Engineering / Director of Sales and Operations</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<hr class="divider">

<!-- HIGH RISKS -->
<p class="section-label">High</p>

<article id="R05" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 12</span>
    <h3>R05 — Customer qualification timelines driven by customers, not Alltrax</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>All four OEM customers must complete qualification before approving MKR for production. Qualification timelines are set by each customer's internal processes and engineering availability: Customer A needs 6–8 weeks, Customer B 4–6 weeks, Customer D 4–5 weeks. Each must complete before Month 8 cutover.</dd>
    <dt>Category</dt>
    <dd>External</dd>
    <dt>Probability</dt>
    <dd>3 (Possible) — Customers are motivated to qualify because they face supply disruption if they don't. However, their internal scheduling is outside Alltrax control and cannot be contracted or accelerated unilaterally.</dd>
    <dt>Impact</dt>
    <dd>4 (Major) — A customer that does not complete qualification before Month 8 cannot receive MKR. Alltrax cannot continue shipping SBR once inventory is exhausted. Either outcome activates contract penalty provisions.</dd>
    <dt>Mitigation</dt>
    <dd>Notify all four customers now and align sample delivery dates with their earliest qualification start windows. Customer C (Summit Industrial) has the shortest qualification requirement (2–3 weeks) and lowest risk — prioritize their sample delivery. Establish a qualification status checkpoint at Month 6 for all customers.</dd>
    <dt>Contingency</dt>
    <dd>If a customer is at risk of missing qualification by Month 7, escalate directly and assess whether a phased cutover or interim supply arrangement can prevent penalty activation.</dd>
    <dt>Owner</dt>
    <dd>Director of Sales and Operations</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R06" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 12</span>
    <h3>R06 — Contract penalty clauses active across all four customers</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>All four OEM customers have active supply agreements with continuity of supply clauses and penalty provisions. Notice periods vary: 90 days (Customer A, Customer D), 30-day consecutive interruption trigger (Customer B), 60 days (Customer C). Given the project started at Month 0, most notice windows are already inside or approaching their threshold.</dd>
    <dt>Category</dt>
    <dd>External</dd>
    <dt>Probability</dt>
    <dd>3 (Possible) — If customers are notified promptly and the project executes on schedule, penalties can be avoided for most customers. Customer B's 30-day consecutive interruption clause creates structural exposure that differs from the others — a brief gap triggers it regardless of notice.</dd>
    <dt>Impact</dt>
    <dd>4 (Major) — Triggered penalties represent direct financial liability and potential relationship damage with high-volume OEM customers collectively representing approximately 3,000 units annually.</dd>
    <dt>Mitigation</dt>
    <dd>Issue formal product change notifications to all four customers immediately. Document notification dates and confirm receipt. For Customer B, begin early conversation about whether bridge supply or modified delivery schedule can prevent the 30-day interruption clause from activating.</dd>
    <dt>Contingency</dt>
    <dd>If a penalty is triggered, review contract language for any EOL-driven transition defense. Engage legal counsel before any formal dispute arises.</dd>
    <dt>Owner</dt>
    <dd>Director of Sales and Operations</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R07" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 12</span>
    <h3>R07 — New processor: first-time integration on new PCB</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>The new processor replacing EOL component 1 has not been used by Alltrax before. It must be integrated into a new PCB design and supported by new or substantially revised firmware. Firmware bring-up is targeted for Month 3.5 — two weeks after PCB assembly completion.</dd>
    <dt>Category</dt>
    <dd>Technical</dd>
    <dt>Probability</dt>
    <dd>3 (Possible) — First-time processor integrations routinely surface unexpected behavior during bring-up. Two weeks between PCB assembly and firmware bring-up completion is a compressed window for a new component.</dd>
    <dt>Impact</dt>
    <dd>4 (Major) — Processor integration failure delays firmware bring-up and cascades to internal validation (Month 4), FCC testing (Month 4), and customer sample units (Month 5). Every downstream milestone is affected.</dd>
    <dt>Mitigation</dt>
    <dd>Review processor datasheet and reference designs thoroughly during hardware design. Plan bring-up incrementally: confirm basic boot and peripheral operation before implementing motor control functions. Allocate explicit debug time within the Month 3.5 milestone window.</dd>
    <dt>Contingency</dt>
    <dd>If bring-up reveals a fundamental integration issue, evaluate whether a pin-compatible fallback processor exists that requires minimal schematic change before committing to a full redesign cycle.</dd>
    <dt>Owner</dt>
    <dd>Director of Engineering</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R08" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 12</span>
    <h3>R08 — Manufacturing capacity not formally reserved for MKR builds</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>The production team is a shared resource scheduled alongside existing production orders. No capacity has been reserved for MKR prototype assembly (Month 3) or first production run (Month 7.5). Without formal reservation, MKR builds will compete with existing customer orders.</dd>
    <dt>Category</dt>
    <dd>Resource</dd>
    <dt>Probability</dt>
    <dd>4 (Likely) — Shared manufacturing resources without formal reservation consistently result in scheduling conflicts when existing order volume is present.</dd>
    <dt>Impact</dt>
    <dd>3 (Moderate) — Assembly delays compress the time available for bring-up and validation. A delayed first production run pushes the SBR cutover date, compressing the already-tight Month 8 window.</dd>
    <dt>Mitigation</dt>
    <dd>Formally reserve manufacturing capacity for MKR prototype builds and first production run immediately. Add MKR build windows to the production schedule with the same priority as committed customer orders. Assign a production point of contact to own MKR build coordination.</dd>
    <dt>Contingency</dt>
    <dd>If internal capacity cannot be secured in time for Month 3 prototype assembly, evaluate contract assembly for prototype quantities while internal capacity is arranged for the production run.</dd>
    <dt>Owner</dt>
    <dd>Director of Sales and Operations / Production team lead</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R09" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 12</span>
    <h3>R09 — No contingency budget allocated</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>The project budget has not been finalized and no contingency has been allocated. Known uncertain cost items include FCC testing ($8,000–$15,000 depending on scope and lab), component procurement for long-lead parts, expedite fees if orders are placed late, and rework costs if pre-certification fails or prototypes require redesign.</dd>
    <dt>Category</dt>
    <dd>Budget</dd>
    <dt>Probability</dt>
    <dd>4 (Likely) — Projects with unfinalized budgets and multiple uncertain cost elements almost always encounter cost surprises. FCC retesting, component expedite premiums, and prototype iterations are all probable on a first-time design.</dd>
    <dt>Impact</dt>
    <dd>3 (Moderate) — Cost overruns do not inherently stop the project, but requiring owner approval for every unbudgeted expenditure creates decision latency at exactly the moments when speed matters most — component expedites, emergency lab scheduling, prototype rework authorization.</dd>
    <dt>Mitigation</dt>
    <dd>Establish and approve a formal project budget within the first two weeks, including a minimum 15% contingency given the volume of uncertain cost elements. Pre-authorize a threshold for expedite decisions that does not require owner approval delay.</dd>
    <dt>Contingency</dt>
    <dd>If cost overruns exceed contingency, prioritize spending on timeline-critical items: component procurement and FCC testing. Defer discretionary items.</dd>
    <dt>Owner</dt>
    <dd>Owner (project sponsor)</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R10" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 9</span>
    <h3>R10 — FCC pre-certification failure requires retest</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>FCC pre-certification testing is scheduled at Month 4. Failure requires identifying the root cause, implementing a fix, and retesting before formal submission. This is a common outcome on first-time Bluetooth integrations, particularly where antenna placement or PCB filtering has not been independently reviewed.</dd>
    <dt>Category</dt>
    <dd>Technical</dd>
    <dt>Probability</dt>
    <dd>3 (Possible) — First-time Bluetooth integrations frequently require at least one round of antenna or filtering adjustment. The MKR-BT has not gone through this process before.</dd>
    <dt>Impact</dt>
    <dd>3 (Moderate) — A single pre-cert failure with a known, contained fix is recoverable within the timeline. Multiple failures or a fundamental layout issue could consume 4–6 weeks, pushing FCC submission beyond Month 4.5 and grant receipt beyond Month 6.</dd>
    <dt>Mitigation</dt>
    <dd>Engage an EMC consultant to review PCB layout before fabrication. Follow Bluetooth module manufacturer reference layout exactly. Schedule pre-certification testing to allow one correction cycle before the submission target.</dd>
    <dt>Contingency</dt>
    <dd>If pre-cert fails, immediately characterize the failure mode. Assess whether a targeted PCB patch (rework on existing boards) is feasible before committing to a full respun fabrication run.</dd>
    <dt>Owner</dt>
    <dd>Director of Engineering</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R11" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 9</span>
    <h3>R11 — Pacific Electric Vehicles NEV/LSV regulatory dependency</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>Customer B's NEV/LSV application may trigger additional regulatory review on their end during MKR qualification. FMVSS and NHTSA requirements applicable to NEV/LSV vehicles can require separate approval for powertrain component changes. This timeline is outside both Alltrax's and Customer B's direct control.</dd>
    <dt>Category</dt>
    <dd>External</dd>
    <dt>Probability</dt>
    <dd>3 (Possible) — Whether this applies depends on Customer B's specific compliance posture and any existing approvals they hold for the SBR. It has not been assessed yet.</dd>
    <dt>Impact</dt>
    <dd>3 (Moderate) — If triggered, Customer B's qualification timeline extends beyond their estimated 4–6 weeks. Combined with their 30-day consecutive interruption penalty clause, an extended qualification timeline creates compounding exposure.</dd>
    <dt>Mitigation</dt>
    <dd>Raise this question directly with Customer B in the first product change notification. Ask them to assess whether their NEV/LSV compliance posture requires any regulatory review for this component change. Document their response before Month 3.</dd>
    <dt>Contingency</dt>
    <dd>If Customer B confirms a regulatory review is required, immediately assess the timeline impact and determine whether interim supply arrangements or modified cutover sequencing can absorb the delay.</dd>
    <dt>Owner</dt>
    <dd>Director of Sales and Operations</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R12" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 9</span>
    <h3>R12 — New power stage: first-time integration</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>The new power stage replacing EOL component 2 has not been used by Alltrax before. Power stage selection and integration affects thermal management, motor drive performance, and PCB layout. Internal validation is targeted at Month 4.</dd>
    <dt>Category</dt>
    <dd>Technical</dd>
    <dt>Probability</dt>
    <dd>3 (Possible) — New power stage components at different performance parameters carry uncertainty in real-world thermal and electrical behavior that simulation alone does not fully resolve.</dd>
    <dt>Impact</dt>
    <dd>3 (Moderate) — Power stage issues discovered during internal validation require hardware revision. Downstream effects reach FCC testing and customer sample unit dates.</dd>
    <dt>Mitigation</dt>
    <dd>Run thermal and electrical simulation for the new power stage during the design phase. Build a test fixture to validate power stage behavior in isolation before full PCB assembly. Identify a fallback component early.</dd>
    <dt>Contingency</dt>
    <dd>If validation reveals a performance issue, evaluate whether firmware adjustments (current limits, switching frequency tuning) can resolve it before committing to a hardware revision.</dd>
    <dt>Owner</dt>
    <dd>Director of Engineering</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R13" class="risk-card high">
  <div class="card-header">
    <span class="badge high">High — Score 8</span>
    <h3>R13 — Form factor constraints are contractual; any deviation requires customer amendment</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>Mounting hole pattern, wire harness connector positions, and overall enclosure dimensions must match the SBR exactly for all four customers. These constraints are contractual with no exceptions permitted without written customer approval and a contract amendment — a process that could take weeks and may not be achievable within the project timeline.</dd>
    <dt>Category</dt>
    <dd>Scope</dd>
    <dt>Probability</dt>
    <dd>2 (Unlikely) — SBR dimensions are known. Starting the design from documented SBR measurements makes constraint violation unlikely if controlled properly in the design review process.</dd>
    <dt>Impact</dt>
    <dd>4 (Major) — Any form factor deviation triggers a contract amendment process with all affected customers simultaneously. A single unresolved amendment blocks cutover for that customer. If the deviation affects all four customers, the entire project cutover is at risk.</dd>
    <dt>Mitigation</dt>
    <dd>Document exact SBR mounting dimensions and connector positions as formal design constraints before hardware design begins. Include a form factor verification check in the internal validation milestone. Treat any deviation flag as a stop-work condition requiring immediate escalation.</dd>
    <dt>Contingency</dt>
    <dd>If a form factor deviation is discovered post-fabrication, assess whether a mechanical adapter solution is feasible before initiating customer amendment discussions. Amendment discussions should begin immediately in parallel regardless.</dd>
    <dt>Owner</dt>
    <dd>Director of Engineering</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<hr class="divider">

<!-- MEDIUM RISKS -->
<p class="section-label">Medium</p>

<article id="R14" class="risk-card medium">
  <div class="card-header">
    <span class="badge medium">Medium — Score 6</span>
    <h3>R14 — Budget not formally established</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>A formal project budget has not been finalized. Known cost categories exist but no confirmed figures are in place. Without a formal budget, procurement decisions and vendor commitments may be delayed pending owner approval.</dd>
    <dt>Category</dt>
    <dd>Budget</dd>
    <dt>Probability</dt>
    <dd>3 (Possible) — Budget approval is a standard process, but the absence of one at project start signals it has not been prioritized. Procurement decisions cannot wait indefinitely.</dd>
    <dt>Impact</dt>
    <dd>2 (Minor) — Budget establishment delay creates friction but rarely blocks early project stages on its own. Risk escalates if component orders or FCC lab booking are held waiting for approval. Related to and partially driving R09.</dd>
    <dt>Mitigation</dt>
    <dd>Establish and approve a formal project budget within the first two weeks. Prioritize cost categories that are blocking procurement (component orders, FCC lab booking).</dd>
    <dt>Contingency</dt>
    <dd>If formal budget approval is delayed, identify which expenditures can be authorized under existing operational budgets to keep component ordering and lab scheduling moving.</dd>
    <dt>Owner</dt>
    <dd>Owner (project sponsor)</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

<article id="R15" class="risk-card medium">
  <div class="card-header">
    <span class="badge medium">Medium — Score 6</span>
    <h3>R15 — Single-PCB dual-SKU: manufacturing differentiation at stuffing stage</h3>
  </div>
  <dl>
    <dt>Description</dt>
    <dd>The MKR-BT and MKR share a single PCB, differentiated only by whether the Bluetooth module is populated. Manufacturing must reliably control which SKU is produced at the stuffing stage. A mix-up would result in incorrect units shipped to customers with no visible external difference.</dd>
    <dt>Category</dt>
    <dd>Technical</dd>
    <dt>Probability</dt>
    <dd>2 (Unlikely) — Single-PCB multi-SKU is a standard manufacturing approach. The risk is process control, not design complexity.</dd>
    <dt>Impact</dt>
    <dd>3 (Moderate) — A production mix-up caught at customer incoming inspection triggers immediate escalation, potential return, and rework of an entire production run. A mix-up in the field is worse.</dd>
    <dt>Mitigation</dt>
    <dd>Define the SKU differentiation procedure as a formal manufacturing work instruction before the first prototype build. Include a functional test step that confirms Bluetooth module presence or absence before shipment. Label BOM differences clearly in the production package.</dd>
    <dt>Contingency</dt>
    <dd>If a mix-up is discovered post-shipment, initiate product return immediately and identify root cause in the manufacturing procedure before resuming production.</dd>
    <dt>Owner</dt>
    <dd>Production team lead</dd>
    <dt>Status</dt>
    <dd>Open</dd>
  </dl>
</article>

</body>
</html>
```
