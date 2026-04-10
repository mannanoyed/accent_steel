# PRESENTATION OUTLINE
## Drawing Revision Intelligence System - Client Meeting

---

## MEETING FLOW (45-60 minutes)

### Opening (5 min)
**Goal:** Set context and energy

**Your opening:**
"During our discovery, we learned about a real problem: drawing revisions don't reach your shop floor in time, material gets scrapped, and you can't prove it was the client's change. We've designed a system to solve this. It's not a separate tool you have to log into. It lives in the tools you already use—email and Slack. Everything is automated. Everything is logged.

We want to walk you through exactly how it works, show you the benefits, and discuss next steps."

**Time:** 2 min on problem, 3 min on this overview

---

### Part 1: The Problem (5 min)

**Show the workflow:**

"Here's what happens today:

1. Client emails a revision → sits in inbox
2. Email is forwarded slowly → nobody's in a rush
3. Engineering eventually learns about it → delays
4. Production still cutting the OLD spec → material gets wasted
5. By the time shop floor knows, it's too late

Timeline: Revision issued → 4-12 hours later → production is still on old spec

Cost: You lose material. AND you lose the ability to charge the client."

**Pause for reaction.** Let them nod.

**Then:** "How often does this happen? What's your gut estimate for material waste from revisions?"

*Listen to their answer. They might say "we're not sure" or give a rough number. Either way, say:*

"That's what we want to measure and eliminate."

---

### Part 2: The Solution Flow (10 min)

**Use the visual flow diagram from the guide.**

Walk through step-by-step:

**Step 1-2: Detection**
"The moment a revision email arrives, our system watches for it. Looks for the signatures—attachments, keywords, version changes. Catches it instantly."

**Step 3-5: Processing**
"It reads the email chain, understands what changed and why, finds which components and work orders are affected, and classifies it: Is this the client changing their mind (EVO) or did we make an error (IVO)?"

**Step 6: Alerting**
"Within 30 seconds, a Slack alert goes to your production supervisor. Clear, actionable. What changed. Which jobs affected. Recommendation: hold or proceed."

Show the Slack alert template.

**Step 7: Decision**
"Your production supervisor clicks [CONFIRM HOLD] or [PROCEED] directly from Slack. Decision is logged automatically. Timestamp, who, why."

**Step 8: Recording**
"Complete audit trail is created. 6 months from now, if there's a dispute: you have proof of when you learned about the change, what you decided, and why. That's your evidence for cost recovery."

---

### Part 3: What Gets Stored (5 min)

**Say:** "Let me show you what the system captures for every single revision."

**Walk through the data structure table:**

"For every revision, we store:

- What changed (in plain English, thanks to AI)
- When we detected it (exact timestamp)
- Who caused it (client email = their change, internal = our error)
- Which jobs are affected
- The full email chain (linked for audit)
- What production decided (hold? proceed? why?)
- Any material scrapped or rework done

All of this is searchable, queryable, and auditable. It's the foundation for cost recovery claims and for understanding where your quality issues are."

---

### Part 4: The Integration (3 min)

"The system connects to three things you already have:

1. **Email:** Monitors your project inbox
2. **Stromis:** Gets BOM data, component definitions, work order status
3. **Slack:** Posts alerts, captures decisions

We're not asking you to learn a new tool. We're automating the connections you already have."

---

### Part 5: Timeline & Investment (5 min)

**Show the timeline table:**

"Phase 1 (Weeks 1-4): $25K
- We build the core system: detection, AI summarization, Slack alerts, decision logging
- You've got a live system catching every revision in real-time

Phase 2 (Weeks 5-6): $10K
- We go back 6 months, clean up historical revisions, classify them
- You get a baseline report: how many revisions? How much scrap? How much cost recovery potential?

Phase 3 (Weeks 7+): $8K (optional)
- Dashboards and reporting
- See patterns: which clients revise most? Which teams make the most errors?

Total: $35K for Phases 1-2. System is live and valuable after Phase 1. Phase 2 adds the historical insights."

---

### Part 6: ROI (3 min)

**Say:** "This is the math we're looking at.

Conservative estimate:

- **Scrap reduction:** 30-50% of revision-related waste prevented
- **Cost recovery:** 60-80% of client-caused losses recovered (that you're currently absorbing)
- **First-year ROI:** $100K+ (depends on your material costs and revision frequency)
- **Payback period:** 4-6 weeks

After that, the system runs for free. Every revision detected. Every decision logged. Year 2 and beyond: 100% value with zero incremental cost."

*Then ask:* "Does that ROI feel realistic to you, or do you think the revision rate is higher or lower than our assumptions?"

---

### Part 7: What We Need From You (3 min)

"To start Phase 1 next week, we need:

1. **Email access:** Read-only access to your project revision inbox (or API, or forwarding setup)
2. **Stromis access:** BOM data, component definitions, work order mapping
3. **Slack workspace:** Ability to create an alerts channel and post messages
4. **Sample data:** 10-15 recent revision emails so we can test detection
5. **Metadata:** List of active projects, naming conventions, typical lead times

We'll work with your IT team. Read-only, zero modifications to your source systems. Everything stays on-premises."

---

### Part 8: Next Steps (3 min)

"Here's what happens now:

**Today/Tomorrow:**
- You review this proposal with your team (production, engineering, IT, finance)
- We answer any technical questions

**By end of week:**
- You confirm: yes, let's move forward
- We schedule a technical kickoff with your IT team

**Week of April 22:**
- Phase 1 begins
- Weeks 1-4: system goes live
- Week 4: you have a live system detecting revisions

**Week of May 6:**
- Phase 2: historical analysis
- You get the baseline report

**By May 20:**
- You have a complete picture: past, present, and ongoing revision tracking"

---

### Q&A (10-15 min)

**Prep answers for common questions:**

---

## COMMON QUESTIONS & ANSWERS

### Q: "This seems complex. How do you know the AI summarization will be accurate?"

**A:** "Good question. The AI isn't doing geometry analysis. It's reading English text from the email chain and extracting: what specifically changed, why, and who approved it. That's much simpler and very accurate.

We'll test this on 10-15 of your recent revision emails before Phase 1 goes live. You'll see examples. If the summaries are off, we tweak the system. But in practice, this is a solved problem—email summarization is well-understood AI.

And here's the important part: every summary links back to the original email. If there's ever a dispute, the human can always click through and read the original."

---

### Q: "What if a revision email gets classified wrong (EVO vs. IVO)?"

**A:** "We use a simple rule: if it comes from a client email, it's EVO. If it comes from internal Stromis, it's IVO. That catches 90% correctly.

For the grey area—where a client-requested change is actually fixing our engineering error—we flag those and ask a human. But the important part is we *flag* them. You see them. You make the call.

Once you've classified a few, we learn your patterns and get smarter. But we never want to secretly misclassify something. Transparency is the goal."

---

### Q: "How long does it take from revision detection to shop floor alert?"

**A:** "About 30 seconds. The system sees the email, processes it, matches it to work orders, and posts the Slack alert. That's almost instant compared to the current 4-12 hours."

---

### Q: "What if there's a false positive? Email gets tagged as a revision but it's not?"

**A:** "We test extensively to minimize false positives. But if one happens, the production supervisor gets a Slack alert, glances at it, and ignores it (no action needed). Zero harm.

We also log false positives so we can learn and tune the detection rules. It gets better over time."

---

### Q: "Can the system auto-halt production without human input?"

**A:** "Not in Phase 1. The system alerts, a human decides. This is intentional—we want human judgment in the loop for something this critical.

In Phase 2 or 3, if you want us to auto-hold certain work orders, we can do that. But it's a separate conversation about risk tolerance."

---

### Q: "What about confidentiality? Storing all these emails and revisions?"

**A:** "Everything stays on-premises. No data leaves your environment. We're storing metadata (what changed, when, who), not the actual drawings. And you control access: who can see revision records? You decide.

We'll audit-log everything so you know exactly who accessed what, when."

---

### Q: "Can we integrate this with our finance system for automatic cost recovery filing?"

**A:** "In Phase 2/3, yes. We can flag cost-recoverable revisions and even auto-generate invoice line items. But in Phase 1, we focus on detection and logging. By Phase 2, you'll have the data foundation to do that integration cleanly."

---

### Q: "What happens if Stromis goes down or email goes down?"

**A:** "If email monitoring is down, we miss detection during that window. When it comes back up, we catch up (we can backfill recent emails).

If Stromis is down, we can still detect revisions and alert production, but we won't have work order detail. We'd post an alert saying 'couldn't match to WOs, need manual input.'

In practice, these systems are very reliable, so downtime is rare. But we build graceful degradation into the system."

---

### Q: "Who owns this system? Will we be vendor-locked?"

**A:** "We build it as your system. The code is yours. The data is yours. You're not locked in. If you ever want to stop working with us, the system keeps running—you just need someone to maintain it.

We're not trying to lock you in. We're trying to solve a real problem and build a good relationship."

---

### Q: "Can this help us understand our engineering quality?"

**A:** "Absolutely. After 2-3 months, you'll have data showing: which teams make the most errors? What kinds of errors? Are they repeating?

This is valuable for training, process improvement, and maybe even performance reviews. But we'll present it matter-of-factly as data, not as judgment."

---

### Q: "What if we want to pause this and restart later?"

**A:** "No problem. If Phase 1 is live and working, you can pause anytime. The system keeps running. When you want to restart Phase 2 or 3, all your data is there."

---

## CLOSING

**After Q&A, summarize:**

"Here's what we're proposing:

A system that:
- Detects revisions in real-time (not 4-12 hours later)
- Tells your production supervisor exactly what to do
- Logs everything for cost recovery and quality improvement
- Lives in your existing tools (email, Slack, Stromis)
- Pays for itself in 4-6 weeks

It's not magic. It's good engineering: integration + automation + logging.

Next step: Review this with your team. Confirm access. Schedule the tech kickoff. Week of April 22, Phase 1 begins.

Questions?"

---

## WHAT TO BRING TO THE MEETING

- Printed copies of the solution document (1 per person)
- Laptop with the visual guide open
- This presentation outline (notes for you)
- Whiteboard/markers (in case you need to sketch)
- Confidence (you know what you're talking about)

---

## TONE THROUGHOUT

- **Honest:** This solves a real problem. We're not overselling.
- **Clear:** Explain the flow simply. Use examples. Reference their workflow.
- **Confident:** You've thought this through. You know what you're doing.
- **Collaborative:** "We'll work with your IT team." "You decide when to auto-halt." Not a black box.
- **Humble:** "If we get the AI summarization wrong, we fix it." Not defensive.

---

## IF THEY SAY "YES, LET'S DO THIS"

**Immediate next steps:**

1. Schedule IT kickoff for next week (30 min)
   - Email integration
   - Stromis access
   - Slack workspace setup

2. Gather sample data:
   - 10-15 recent revision emails
   - Project metadata (active projects, naming conventions)
   - Typical lead times

3. Set team expectations:
   - Phase 1 goes live in 4 weeks
   - Slack alerts start immediately
   - Decision logging is manual (they click buttons)
   - No disruption to current process, only additions

4. Define roles:
   - Who's the internal champion (your point of contact)?
   - Who decides IVO vs. EVO in grey areas?
   - Who sets access controls (who can see revision records)?

---

## IF THEY SAY "WE NEED TO THINK ABOUT IT"

**Graceful response:**

"Of course. Take a week. Review it with your team. Send us questions anytime. The math doesn't change—the ROI is there. Whenever you're ready, we can move forward."

(Then follow up in 5 days with a check-in call.)

---

## IF THEY SAY "THIS IS TOO EXPENSIVE"

**Reframe:**

"$35K is the investment. The return is $100K+ in year one from scrap prevention and cost recovery.

But we can also scope down Phase 1 if you want—detection + alerts + basic logging is $20K. Then add the historical analysis later when budget allows.

Or we can discuss which phases matter most to you and build a custom package."

(Don't discount. Reframe the value instead.)

---

**End of Presentation Outline**

Use this to prepare your delivery. Practice the flow. Anticipate questions. Know your answers.

You've got this.
