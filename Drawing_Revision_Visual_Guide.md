# DRAWING REVISION INTELLIGENCE SYSTEM
## Visual Reference Guide

---

## SYSTEM FLOW DIAGRAM

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     REVISION DETECTION & RESPONSE                        │
└─────────────────────────────────────────────────────────────────────────┘

STEP 1: DETECTION
═══════════════════════════════════════════════════════════════════════════
    
    Client sends revision email
              │
              ▼
    ┌──────────────────────────────┐
    │   EMAIL MONITORING SYSTEM    │
    │  (Watches project inbox)     │
    │                              │
    │  Detects:                    │
    │  • New attachments           │
    │  • Keywords: "revised",      │
    │    "updated", "REV:"         │
    │  • Version changes           │
    └──────────────────────────────┘
              │
              ▼ (Match found)
         [REVISION DETECTED]


STEP 2-5: PROCESSING
═══════════════════════════════════════════════════════════════════════════

    ┌─────────────────┐       ┌──────────────────┐       ┌──────────────────┐
    │  EMAIL READER   │──────▶│  AI SUMMARIZER   │──────▶│  BOM MATCHER     │
    │  (NLP Engine)   │       │  (Extract key    │       │  (Find affected  │
    │                 │       │   changes)       │       │   components &   │
    │  Reads:         │       │                  │       │   work orders)   │
    │  • Full email   │       │  Creates:        │       │                  │
    │    chain        │       │  • What changed  │       │  Links to:       │
    │  • Attachments  │       │  • Why           │       │  • Stromis BOM   │
    │  • Context      │       │  • Approved by   │       │  • Work orders   │
    │                 │       │  • When          │       │  • Project IDs   │
    └─────────────────┘       └──────────────────┘       └──────────────────┘
              │                        │                         │
              └────────────────────────┴─────────────────────────┘
                                       │
                                       ▼
                        ┌──────────────────────────────┐
                        │  CLASSIFICATION ENGINE       │
                        │                              │
                        │  Determines:                 │
                        │  • EVO (Client change)?      │
                        │  • IVO (Our error)?          │
                        │  • Grey area?                │
                        │    (Flag for human review)   │
                        └──────────────────────────────┘
                                       │
                                       ▼
                        ┌──────────────────────────────┐
                        │  REVISION RECORD CREATED     │
                        │                              │
                        │  Stores:                     │
                        │  • What changed              │
                        │  • When detected             │
                        │  • Classification (EVO/IVO)  │
                        │  • Affected work orders      │
                        │  • Email chain link          │
                        │  • AI summary                │
                        └──────────────────────────────┘


STEP 6: ALERTING
═══════════════════════════════════════════════════════════════════════════

    Revision record created
              │
              ▼
    ┌─────────────────────────────────────────────┐
    │     SLACK ALERT POSTED                      │
    │  (to #revisions-alerts channel)             │
    │                                             │
    │  🚨 REVISION ALERT — Project X / Comp Y    │
    │                                             │
    │  What changed: ...                          │
    │  Affected WOs: WO-5234, WO-5235             │
    │  Classification: EVO (Client change)        │
    │  Recommendation: HOLD production            │
    │                                             │
    │  [CONFIRM HOLD] [PROCEED] [REQUEST INFO]   │
    └─────────────────────────────────────────────┘
              │
              ▼
    Sent to:
    • Production Supervisor
    • Engineering Lead
    • Project Manager


STEP 7: DECISION CAPTURE
═══════════════════════════════════════════════════════════════════════════

    Production supervisor sees alert in Slack
              │
              ├─ Clicks [CONFIRM HOLD]
              │              │
              │              ▼
              │         System logs:
              │         • Decision: HOLD
              │         • Who: John Smith
              │         • When: 2024-04-15 14:33:00 UTC
              │         • Reasoning: Awaiting IFF
              │
              ├─ Clicks [PROCEED ANYWAY]
              │              │
              │              ▼
              │         System logs:
              │         • Decision: PROCEED
              │         • Who: John Smith
              │         • When: timestamp
              │         • Reasoning: [text field]
              │         • Risk ack: checkbox
              │
              └─ Clicks [REQUEST MORE INFO]
                         │
                         ▼
                    System opens Slack thread
                    Team discusses in thread
                    Decision logged once made


STEP 8: RECORDING
═══════════════════════════════════════════════════════════════════════════

    All information stored in database:
    
    ┌───────────────────────────────────────────────┐
    │          COMPLETE AUDIT TRAIL                 │
    │                                               │
    │  Project X / Plate Connection A               │
    │  ─────────────────────────────                │
    │  What: Thickness 10mm → 12mm                  │
    │  Why: Client structural analysis              │
    │  Detected: 2024-04-15 14:32:15 UTC            │
    │  Source: Client email (EVO)                   │
    │  Affected WOs: WO-5234, WO-5235, WO-5236      │
    │  Production decision: HOLD                    │
    │  Decided by: John Smith                       │
    │  Decided at: 2024-04-15 14:33:00 UTC          │
    │  Email chain: [link]                          │
    │  Status: On hold, awaiting IFF release        │
    │  Cost impact: TBD (will be measured)          │
    │                                               │
    │  ⬆ This entire record is searchable,          │
    │    queryable, and auditable for months/years  │
    │    to come                                    │
    └───────────────────────────────────────────────┘

```

---

## INTEGRATION ARCHITECTURE

```
┌──────────────────────────────────────────────────────────────────────────┐
│                        YOUR ACCENT STEEL ECOSYSTEM                        │
└──────────────────────────────────────────────────────────────────────────┘

                            DRAWING REVISION
                          INTELLIGENCE SYSTEM
                                  │
                    ┌─────────────┼─────────────┐
                    │             │             │
                    ▼             ▼             ▼
            
        ┌──────────────┐   ┌──────────────┐   ┌──────────────┐
        │    EMAIL     │   │   STROMIS    │   │     SLACK    │
        │              │   │              │   │              │
        │  Monitors    │   │  BOM data    │   │  Alerts      │
        │  project     │   │  Work orders │   │  Decisions   │
        │  inbox       │   │  Components  │   │  Threads     │
        │  Extracts    │   │  Project IDs │   │              │
        │  revisions   │   │              │   │              │
        │              │   │              │   │              │
        └──────────────┘   └──────────────┘   └──────────────┘
                    │             │             │
                    └─────────────┴─────────────┘
                            │
                            ▼
                    ┌───────────────────┐
                    │  PROCESSING CORE  │
                    │                   │
                    │  • Detect         │
                    │  • Extract        │
                    │  • Summarize      │
                    │  • Classify       │
                    │  • Link           │
                    └───────────────────┘
                            │
                            ▼
                    ┌───────────────────┐
                    │  DATABASE LAYER   │
                    │                   │
                    │  Stores:          │
                    │  • Revision recs  │
                    │  • Decisions      │
                    │  • Audit trail    │
                    │  • History        │
                    └───────────────────┘
                            │
                            ▼
            ┌───────────────────────────────┐
            │      DASHBOARDS (Phase 3)    │
            │                               │
            │  • Revision analytics        │
            │  • Cost impact               │
            │  • Client patterns           │
            │  • Quality trends            │
            └───────────────────────────────┘

```

---

## WHAT DATA GETS STORED

```
EVERY REVISION RECORD CONTAINS:
═══════════════════════════════════════════════════════════════════════════

┌─ IDENTIFICATION ─────────────────────────────────────────┐
│  • Project ID                                             │
│  • Component name                                         │
│  • Revision ID (auto-generated)                           │
└──────────────────────────────────────────────────────────┘

┌─ WHAT CHANGED ───────────────────────────────────────────┐
│  • AI-generated summary (e.g., "Plate thickness         │
│    changed from 10mm to 12mm")                           │
│  • Why it changed (extracted from email context)         │
│  • Technical details (specs, dimensions, etc.)           │
└──────────────────────────────────────────────────────────┘

┌─ TIMING & SOURCE ────────────────────────────────────────┐
│  • When detected (timestamp: YYYY-MM-DD HH:MM:SS UTC)   │
│  • Who initiated (client name, email, or internal eng)   │
│  • Classification: EVO (client) or IVO (internal)        │
│  • Confidence level (if grey area)                       │
└──────────────────────────────────────────────────────────┘

┌─ IMPACT ─────────────────────────────────────────────────┐
│  • Affected work orders (WO-5234, WO-5235, etc.)        │
│  • Affected stages (Stage 2 design? Stage 5 fab?)        │
│  • Severity (high/medium/low impact)                     │
│  • Components impacted (count, names)                    │
└──────────────────────────────────────────────────────────┘

┌─ COMMUNICATION ──────────────────────────────────────────┐
│  • Original email chain (full text, links)              │
│  • Client approvals (who approved? when?)               │
│  • Any follow-up discussions                            │
│  • Attachment links (drawing files, etc.)               │
└──────────────────────────────────────────────────────────┘

┌─ PRODUCTION RESPONSE ────────────────────────────────────┐
│  • Decision: HOLD / PROCEED / RESCHEDULE                │
│  • Decided by: [Name, Role, Timestamp]                  │
│  • Reasoning: [Free text explanation]                   │
│  • Action taken: [What production did]                  │
│  • Risk acknowledgment: [Y/N]                           │
└──────────────────────────────────────────────────────────┘

┌─ OUTCOMES & TRACKING ────────────────────────────────────┐
│  • Material scrapped: [Y/N, quantity if known]           │
│  • Rework required: [Y/N, hours if tracked]             │
│  • Cost impact: [$ amount, if later measured]           │
│  • Cost type: IVO-absorbed / EVO-recoverable            │
│  • Cost status: Filed / Pending / Paid                  │
│  • Final outcome: Resolved / On hold / TBD              │
└──────────────────────────────────────────────────────────┘

```

---

## SLACK ALERT TEMPLATE

```
🚨 REVISION ALERT — Project X / Plate Connection A

What changed:
Plate thickness 10mm → 12mm (structural load analysis)

Source:
Client (acme@client.com)

Client approval:
Yes, approved 2024-04-15

Affected work orders:
  • WO-5234 (started fabrication)
  • WO-5235 (material in queue)
  • WO-5236 (not yet started)

Status:
Awaiting IFF release

Recommendation:
HOLD production on these work orders

Email summary:
Client submitted revised drawing with thicker plates due to structural 
analysis update. Approved by their engineering team. Awaiting your IFF 
release before fabrication continues.

Full email thread:
[Click to view all 5 emails in this discussion]

──────────────────────────────────────────────────────────────────

[CONFIRM HOLD]     [PROCEED ANYWAY]     [REQUEST MORE INFO]

──────────────────────────────────────────────────────────────────

Logged by system at: 2024-04-15 14:32:15 UTC
Record: rev-20240415-001

```

---

## DASHBOARD EXAMPLE (MONTH 3 REPORT)

```
DRAWING REVISION INTELLIGENCE — APRIL 2026 SUMMARY
═══════════════════════════════════════════════════════════════════════════

KEY METRICS
─────────────────────────────────────────────────────────────────────────

  Total Revisions Detected:           47
  
  Classification:
    └─ Client-caused (EVO):           31 revisions (66%)
    └─ Internal errors (IVO):         16 revisions (34%)
    └─ Grey area (pending manual):     0 revisions (0%)

  Material Impact:
    └─ Scrap prevented:               2.3 tons
    └─ Rework hours avoided:          156 hours
    └─ Estimated cost avoidance:      $47,500 USD

  Cost Recovery:
    └─ Client-caused losses:          $42,000 claimed
    └─ Recovery status:               $28,000 paid, $14,000 pending

  Production Response:
    └─ Avg time: Detection → Hold:    3 minutes
    └─ Holds confirmed:               28 cases
    └─ Proceeds approved:             15 cases
    └─ Info requests:                  4 cases


CLIENT BREAKDOWN
─────────────────────────────────────────────────────────────────────────

  Highest revision rate:
    └─ Client A:                      12 revisions
        (Recommendation: Review specs process, adjust lead times)

  Lowest revision rate:
    └─ Client B:                      1 revision
        (Stable design process)

  Average per client:                 5.2 revisions


ENGINEERING INSIGHTS
─────────────────────────────────────────────────────────────────────────

  Internal errors (16 IVOs) by team:
    └─ Engineering Team 1:             8 errors (50%)
    └─ Engineering Team 2:             5 errors (31%)
    └─ Engineering Team 3:             3 errors (19%)

  Most common error types:
    └─ Dimension mismatch:             6 cases
    └─ Material spec oversight:        5 cases
    └─ Connection detail missed:       3 cases
    └─ Other:                          2 cases

  Recommendation: Additional QA on dimension checks


SAVINGS SUMMARY
─────────────────────────────────────────────────────────────────────────

  System cost (3 months):              $35,000
  Scrap prevented:                     $47,500
  Cost recovery filed:                 $42,000
  
  Net ROI (3 months):                  +$54,500
  Payback achieved:                    Week 6 ✅

```

---

## INTEGRATION CHECKLIST

Before Phase 1 starts, confirm you have:

```
REQUIRED ACCESS
═══════════════════════════════════════════════════════════════════════════

□ Email Integration
  □ Read access to project revision inbox
  □ Ability to set up email forwarding or API access
  □ IT permission to monitor incoming revisions

□ Stromis Integration
  □ Database read-only access
  □ BOM structure & component definitions
  □ Work order status & project ID mapping
  □ Contact: Stromis admin

□ Slack Integration
  □ Workspace admin approval
  □ Ability to create #revisions-alerts channel
  □ Ability to post messages from system
  □ Ability to add reaction buttons

□ Sample Data
  □ 10-15 recent revision emails
  □ Project metadata (active projects, naming conventions)
  □ Typical lead times & deadlines
  □ Material spec requirements


SECURITY & COMPLIANCE
═══════════════════════════════════════════════════════════════════════════

□ All data remains on-premises (no cloud storage)
□ Read-only access only (no modifications to source systems)
□ Audit logging enabled (all system actions logged)
□ Data retention policy defined (how long to keep records?)
□ Access controls defined (who can view revision records?)

```

---

## QUESTIONS TO ASK YOUR TEAM BEFORE KICKOFF

```
1. Who should receive revision alerts?
   ( ) Production supervisor only
   ( ) Production + Engineering + Project manager
   ( ) Custom list: ________________

2. How should "halt production" work?
   ( ) System posts alert only (manual halt)
   ( ) System auto-halts work orders in ERP
   ( ) System posts alert + blocks material picks
   ( ) Other: ________________

3. What constitutes a "grey area" revision?
   ( ) Client-reported issue that's actually our design error
   ( ) Changes made without explicit approval
   ( ) Others: ________________

4. Who decides IVO vs. EVO when unclear?
   ( ) Engineering lead
   ( ) Project manager
   ( ) Finance/Admin
   ( ) Rotation / escalation: ________________

5. How should cost recovery be handled?
   ( ) System auto-generates invoice line items
   ( ) System flags for manual review
   ( ) Monthly lump sum claim
   ( ) Other: ________________

6. What historical data needs cleanup?
   ( ) Last 3 months only
   ( ) Last 6 months
   ( ) Last 12 months
   ( ) All historical data we have

7. Who should have access to revision records?
   ( ) Production/Engineering only
   ( ) + Finance
   ( ) + Management
   ( ) Everyone

```

---

**End of Visual Reference Guide**

This document is a companion to the main solution document. Use it to:
- Explain the flow visually in presentations
- Reference specific data structures
- Walk through example scenarios
- Show integration points
- Prepare teams for system go-live

