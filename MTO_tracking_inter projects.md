# Cross-Project Material Optimization Workflow

## Step 1 — Maintain Versioned MTOs
For each project:
- Store every MTO version (Initial, Revised, Final)
- Track:
  - Material ID
  - Size / Dimensions
  - Grade
  - Quantity
  - Version timestamp

---

## Step 2 — Maintain Aggregate Project MTO State
For each project, compute:
- Current Required Quantity (latest MTO)
- Ordered Quantity (from PRs)
- Available Quantity (after usage)

Derived:
- Surplus = Ordered - Required
- Shortage = Required - Ordered

---

## Step 3 — Trigger on MTO Revision
When a new MTO version is released:

1. Compare with previous version
2. Identify:
   - Increased materials → Shortage
   - Decreased materials → Surplus

---

## Step 4 — Update Global Material Pools

### Surplus Pool
- All excess materials across projects
- Indexed by:
  - Material ID
  - Size
  - Grade

### Demand Pool
- All shortages across projects
- Indexed similarly

---

## Step 5 — Cross-Project Matching Engine

For each item in Demand Pool:

1. Find matching items in Surplus Pool:
   - Exact match (Material ID)
   - Compatible match (Size tolerance, same grade)

2. Rank matches based on:
   - Closest size match
   - Project priority
   - Timeline alignment

---

## Step 6 — Generate Reallocation Suggestions

For each match:
- Suggest:
  - Source Project (Surplus)
  - Target Project (Demand)
  - Quantity to transfer

Example:
"Use 8 tons of Material X from Project A to fulfill Project B requirement"

---

## Step 7 — Decision Layer

- User reviews suggestion
- Approves / Rejects / Modifies

---

## Step 8 — Execute & Update State

If approved:
- Deduct from Source Project surplus
- Reduce Target Project shortage
- Update both project MTO states

---

## Step 9 — Audit & Logging

Log:
- Source → Target transfer
- Timestamp
- Decision maker
- Quantity moved
- Estimated cost saved

---

## Step 10 — Continuous Learning (Optional AI Layer)

- Track:
  - Accepted vs rejected matches
- Improve:
  - Matching accuracy
  - Suggestion ranking


  flowchart TD

A[MTO Revision Triggered] --> B[Compare with Previous MTO]

B --> C{Material Change Type}

C -->|Excess Material| D[Add to Surplus Pool]
C -->|Material Shortage| E[Add to Demand Pool]

D --> F[Global Surplus Pool<br/>All Projects]
E --> G[Global Demand Pool<br/>All Projects]

F --> H[Matching Engine]
G --> H[Matching Engine]

H --> I{Match Found?}

I -->|Yes| J[Generate Reallocation Suggestion<br/>Project A → Project B]
I -->|No| K[Proceed with New Procurement]

J --> L[User Decision Layer]

L -->|Approve| M[Transfer Material]
L -->|Reject| K

M --> N[Update Project States<br/>Surplus ↓ Demand ↓]

N --> O[Log Transaction<br/>Cost Saved + Audit Trail]

K --> O
