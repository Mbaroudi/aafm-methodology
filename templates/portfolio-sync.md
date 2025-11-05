# Portfolio Sync Template

**Time**: 15 minutes
**Frequency**: Daily (after individual team morning syncs)
**Participants**: Product Owners from all teams + Product Line Manager
**Level**: Product Line (3-5 teams)

---

## Purpose

Coordinate across multiple AAFM teams to:
- Share daily outcomes
- Identify cross-team dependencies
- Coordinate releases and integrations
- Escalate blockers
- Ensure strategic alignment

---

## Pre-Sync Preparation

**Each Product Owner prepares** (2 minutes):
- [ ] Yesterday's outcome and status
- [ ] Today's committed outcome
- [ ] Dependencies on other teams
- [ ] Blockers requiring escalation
- [ ] Requests for other teams

**AI System prepares**:
- [ ] Cross-team dependency map
- [ ] Integration risks identified
- [ ] Deployment schedule
- [ ] Aggregated metrics

---

## Meeting Structure

### Part 1: Quick Round-Robin (10 min)

**Each Product Owner reports** (2 min per team):

```
Team: [Team Name]
Product Owner: [Name]

YESTERDAY:
Outcome: [Brief description]
Status: [✅ Deployed / ⚠️ Deployed with issues / ❌ Not completed]
Impact: [Business value delivered]

TODAY:
Outcome: [Brief description]
Dependencies: [None / List teams we depend on]
Risk: [Low / Medium / High]

NEEDS:
□ [Request to other team, if any]
□ [Decision needed, if any]
□ [Resource needed, if any]

OFFERS:
□ [Can help other team with...]
□ [Available capacity for...]
```

**Example**:
```
Team: User Services
Product Owner: Jessica

YESTERDAY:
✅ Profile picture upload - Deployed to production
   Impact: 2,341 users uploaded photos in first 12 hours

TODAY:
Outcome: Profile picture cropping feature
Dependencies: None
Risk: Low

NEEDS:
□ Design review from UX team (Tom) for crop UI

OFFERS:
□ Can share image processing library with other teams
```

---

### Part 2: Dependency Resolution (3 min)

**AI System highlights** critical dependencies:

```
CROSS-TEAM DEPENDENCIES DETECTED:

🔗 Team A → Team B
   Dependency: [What Team A needs]
   Status: [Ready / In Progress / Blocked]
   Impact if delayed: [Consequence]
   Resolution: [Coordination plan]

🔗 Team C → Team D
   Dependency: [What Team C needs]
   Status: [Ready / In Progress / Blocked]
   Impact if delayed: [Consequence]
   Resolution: [Coordination plan]

INTEGRATION POINTS TODAY:
📍 [Service A] + [Service B] integration
   Time: [When integration will happen]
   Owners: [Team A lead] + [Team B lead]
   Testing: [Integration test plan]
```

**Product Line Manager facilitates**:
- Confirm coordination plans
- Adjust priorities if needed
- Escalate blockers
- Ensure teams align on timing

---

### Part 3: Priorities & Risks (2 min)

**Product Line Manager shares**:

```
STRATEGIC PRIORITIES (This Week):
1. [Priority 1] - Teams involved: [list]
2. [Priority 2] - Teams involved: [list]
3. [Priority 3] - Teams involved: [list]

RISKS & ALERTS:
⚠️ [Risk description]
   Teams affected: [list]
   Mitigation: [plan]

UPCOMING EVENTS:
📅 [Event] - [Date]
   Impact: [What teams need to know]
```

---

## Decision-Making Framework

**Team-Level Decisions** (No escalation needed):
- Implementation details
- Technical choices within team scope
- Daily work prioritization

**Product Line Decisions** (Escalate to this meeting):
- Cross-team priorities
- Shared resource allocation
- Integration timing
- Dependency conflicts
- Architectural decisions affecting multiple teams

**Escalation to Leadership** (Beyond this meeting):
- Strategic direction changes
- Major resource constraints
- Cross-product-line dependencies
- Organizational blockers

---

## Metrics Dashboard (Reviewed Weekly)

```
┌─────────────────────────────────────────────────────────┐
│ Product Line Dashboard                                  │
├─────────────────────────────────────────────────────────┤
│                                                         │
│ 📊 Aggregate Velocity (Last 7 Days)                     │
│   Total deployments: [X] across [Y] teams              │
│   Average lead time: [X] hours                          │
│   On-time delivery: [X]%                                │
│                                                         │
│ 🔗 Dependency Health                                     │
│   Dependencies resolved on time: [X]%                   │
│   Average dependency resolution: [X] hours              │
│   Blocked dependencies: [X]                             │
│                                                         │
│ ✅ Quality Metrics                                       │
│   Average test coverage: [X]%                           │
│   Production incidents: [X] this week                   │
│   Defect escape rate: [X]%                              │
│                                                         │
│ 🤖 AI Effectiveness                                      │
│   AI code contribution: [X]% avg across teams           │
│   Time saved per team: [X] hours/day                    │
│                                                         │
│ 🎯 Business Value                                        │
│   Features delivered: [X] this week                     │
│   Customer satisfaction: [X]/10                         │
└─────────────────────────────────────────────────────────┘
```

---

## Example: Complete Portfolio Sync

```
Portfolio Sync - November 6, 2025, 09:45

Attendees:
- Jessica (User Services PO)
- Mike (Payment Services PO)
- Lisa (Product Catalog PO)
- Tom (Admin Tools PO)
- Rachel (Product Line Manager)

Part 1: Round-Robin (10 min)

TEAM 1: User Services (Jessica)
YESTERDAY: ✅ Profile picture upload - Deployed, 2,341 uploads
TODAY: Profile picture cropping
DEPENDENCIES: None
NEEDS: Design review from UX (Tom)
OFFERS: Image processing library to share

TEAM 2: Payment Services (Mike)
YESTERDAY: ✅ Stripe integration - Deployed, processing payments
TODAY: PayPal payment option
DEPENDENCIES: None
NEEDS: QA support for payment testing (shared resource)
OFFERS: Payment abstraction layer for other teams

TEAM 3: Product Catalog (Lisa)
YESTERDAY: ⚠️ Bulk product import - Deployed with perf issue
TODAY: Fix performance issue in bulk import
DEPENDENCIES: Platform team to add database index
NEEDS: Database admin help (escalated)
OFFERS: Can help test User Services profile features

TEAM 4: Admin Tools (Tom)
YESTERDAY: ✅ User audit log - Deployed
TODAY: Admin dashboard performance optimization
DEPENDENCIES: User Services API should remain stable
NEEDS: None
OFFERS: UX design review for User Services

Part 2: Dependency Resolution (3 min)

AI System flagged:
🔗 Product Catalog → Platform Team
   Dependency: Database index for product import
   Status: Platform team can do this morning
   Resolution: Platform team commits to 11:00 completion

✅ No other blocking dependencies

📍 Integration Point:
   User Services + Admin Tools
   Time: 14:00 today
   Testing: Integration tests already exist

Part 3: Priorities & Risks (2 min)

Rachel (Product Line Manager):
"Strategic priorities this week:
1. Payment diversification (Stripe + PayPal) - on track
2. Product import performance - addressing today
3. User engagement features - progressing well

⚠️ Risk: Shared QA resource at 90% capacity
   Mitigation: Mike and Lisa coordinate testing schedule

📅 Production freeze next Monday for infrastructure upgrade
   All teams: deploy by Friday if releasing this week"

DECISIONS:
✅ Platform team prioritizes database index (11:00)
✅ QA testing schedule: Mike (morning), Lisa (afternoon)
✅ All teams aim to deploy by Friday due to Monday freeze

Next sync: Tomorrow 09:45
```

---

## Tips for Effective Portfolio Syncs

### For Product Owners:

✅ **Be concise**: 2 minutes max per team
✅ **Focus on dependencies**: Other teams care about blockers, not details
✅ **Surface issues early**: Don't hide problems
✅ **Offer help proactively**: Share resources and knowledge
✅ **Come prepared**: Know your asks before the meeting

### For Product Line Managers:

✅ **Keep energy high**: Fast-paced, focused meeting
✅ **Facilitate, don't solve**: Connect teams, let them coordinate
✅ **Protect team autonomy**: Only escalate true conflicts
✅ **Use AI insights**: Let AI detect dependencies humans might miss
✅ **Make decisions quickly**: Don't defer unnecessarily

### For Everyone:

✅ **Start on time**: Respect everyone's schedule
✅ **Stay standing** (if in person): Keeps meetings short
✅ **Use visuals**: Shared dashboard, dependency map
✅ **Follow up async**: Complex coordination happens outside this meeting
✅ **Celebrate wins**: Quick acknowledgment of achievements

---

## Anti-Patterns to Avoid

❌ Deep technical discussions (take offline)
❌ Revisiting decisions (commit and move on)
❌ Blaming other teams (collaborative mindset)
❌ Running long (>15 min means poor time management)
❌ No dependencies mentioned (unrealistic, look harder)
❌ Hiding problems (transparency is critical)
❌ No one taking notes (AI Scribe should document)

---

## Advanced: Virtual Portfolio Sync

For distributed or large product lines, consider:

### Async-First Approach

**Daily Update** (async, posted by 09:00):
```markdown
## Team: [Name]

### Yesterday
- **Outcome**: [Description]
- **Status**: ✅/⚠️/❌
- **Metric**: [Key outcome metric]

### Today
- **Outcome**: [Description]
- **Dependencies**: [List or "None"]
- **Risk**: [High/Medium/Low]

### Needs/Offers
- [Specific requests or offers]

### Questions for Other Teams
- [Any questions]
```

**Sync Meeting** (15 min, only for active coordination):
- Only discuss dependencies and blockers
- Skip teams with no dependencies
- Use saved time for deeper coordination

---

## Scaling Beyond Product Line

### Business Unit Level (10-20 teams)

**Weekly Portfolio Sync** instead of daily:
- 30 minutes
- Product Line Managers report
- Focus on strategic alignment
- Cross-product-line dependencies

**AI Dependency Monitoring**:
- Automated dependency detection
- Daily reports (no meeting required)
- Alerts for critical blockers
- Suggested coordination plans

---

## Checklist

**Before Sync**:
- [ ] Each PO prepared 2-min update
- [ ] AI dependency analysis complete
- [ ] Previous action items reviewed
- [ ] Agenda shared

**During Sync**:
- [ ] All teams report (no skipping)
- [ ] Dependencies identified and resolved
- [ ] Decisions documented
- [ ] Next steps clear

**After Sync**:
- [ ] AI Scribe shares summary
- [ ] Dependency coordination happens
- [ ] Blockers escalated if needed
- [ ] Dashboard updated

---

## Success Metrics

Track portfolio sync effectiveness:

```
Coordination Quality:
├─ Dependencies resolved on time: [Target: >90%]
├─ Blocker resolution time: [Target: <4 hours]
├─ Integration success rate: [Target: >95%]
└─ Cross-team incidents: [Target: <1 per week]

Meeting Efficiency:
├─ Duration: [Target: <15 min]
├─ Attendance: [Target: 100%]
├─ Action item completion: [Target: >85%]
└─ Participant satisfaction: [Target: >8/10]

Business Outcomes:
├─ Product line velocity: [Trend]
├─ Cross-team delivery: [Successes]
├─ Time to market: [Improvements]
└─ Strategic goal progress: [On track?]
```

---

**Remember**: Portfolio syncs enable team autonomy while ensuring alignment. They're coordination, not command-and-control.
