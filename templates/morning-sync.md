# Morning Sync Template

**Time**: 30 minutes
**Frequency**: Daily
**Participants**: Full team + AI Orchestrator

---

## Meeting Agenda

### Part 1: Retrospective Review (5 min)

**AI Scribe presents yesterday's improvement actions**

```
Yesterday's Commitments:
□ [Action 1] - Status: ✅ Done / ⚠️ In Progress / ❌ Blocked
□ [Action 2] - Status: ✅ Done / ⚠️ In Progress / ❌ Blocked
□ [Action 3] - Status: ✅ Done / ⚠️ In Progress / ❌ Blocked

Blockers to discuss:
- [Describe blocker]
- [Root cause]
- [Proposed resolution]
```

**Team Discussion**:
- Celebrate completed actions
- Address blockers
- Adjust approach if needed

---

### Part 2: Outcome Selection (10 min)

**Product Owner presents top candidates**

```
Candidate 1: [Outcome Description]
├─ Business Value: [Impact statement]
├─ Complexity: [High / Medium / Low]
├─ Dependencies: [List or "None"]
└─ Risk: [Description or "Low risk"]

Candidate 2: [Outcome Description]
├─ Business Value: [Impact statement]
├─ Complexity: [High / Medium / Low]
├─ Dependencies: [List or "None"]
└─ Risk: [Description or "Low risk"]

Candidate 3: [Outcome Description]
├─ Business Value: [Impact statement]
├─ Complexity: [High / Medium / Low]
├─ Dependencies: [List or "None"]
└─ Risk: [Description or "Low risk"]
```

**Team Discussion**:
- Estimate effort with AI assistance
- Identify risks
- Discuss dependencies
- **Decision**: Select ONE outcome

**Today's Commitment**:

```
📋 Outcome: [Selected outcome description]

Success Criteria:
✅ [Measurable criterion 1]
✅ [Measurable criterion 2]
✅ [Measurable criterion 3]

Business Value: [Impact statement]
Feature Flag: [flag.name]
Demo Plan: [What will we show at 5pm?]
```

---

### Part 3: AI Agent Assignment (10 min)

**AI Orchestrator proposes agent allocation**

```
🤖 AI Agent Assignments:

Requirement Analyst Agent (___% capacity)
├─ Task: [Specific work]
└─ Output: [Expected deliverable]

Code Generation Agent (___% capacity)
├─ Task: [Specific work]
└─ Output: [Expected deliverable]

Test Engineer Agent (___% capacity)
├─ Task: [Specific work]
└─ Output: [Expected deliverable]

DevOps Agent (___% capacity)
├─ Task: [Specific work]
└─ Output: [Expected deliverable]

QA Validation Agent (___% capacity)
├─ Task: [Specific work]
└─ Output: [Expected deliverable]

Scribe Agent (___% capacity)
├─ Task: [Document decisions, maintain knowledge base]
└─ Output: [Meeting notes, ADRs]

Total Capacity Check: [Sum should be reasonable, agents can be <100%]
```

**Human Developer Assignments**:

```
👤 [Developer Name] (Lead)
├─ Pair with: [AI Agent name]
├─ Focus: [High-level design, review, complex logic]
└─ Responsibilities: [Specific tasks]

👤 [Developer Name]
├─ Pair with: [AI Agent name]
├─ Focus: [Integration, testing, validation]
└─ Responsibilities: [Specific tasks]

[Add more team members as needed]
```

---

### Part 4: Risk & Dependency Check (5 min)

**Identify risks and mitigation plans**

```
Technical Risks:
⚠️ Risk: [Description]
   Probability: [High / Medium / Low]
   Impact: [High / Medium / Low]
   Mitigation: [Specific action plan]

External Dependencies:
🔗 Dependency: [What we need from whom]
   Status: [Available / Needs coordination / Blocked]
   Owner: [Who will handle]
   Deadline: [When we need it]

Required Decisions:
❓ Decision Needed: [Description]
   Options: [List alternatives]
   Decision Maker: [Who decides]
   Deadline: [When]

Potential Blockers:
🚧 Blocker: [Description]
   Workaround: [Alternative approach]
   Escalation: [If blocked, who to notify]
```

---

## Meeting Outputs (Document and Share)

```
✅ Committed Outcome: [Brief description]
✅ Success Criteria: [3-5 measurable items]
✅ AI Agent Assignments: [Capacity allocated]
✅ Human Assignments: [Clear responsibilities]
✅ Risks Identified: [With mitigation plans]
✅ Demo Plan: [What stakeholders will see at 5pm]
✅ Definition of Done: [When are we "done"?]
```

---

## Tips for Success

### For Product Owners:
✅ Come prepared with pre-validated backlog items
✅ Have clear business value statements
✅ Be ready to answer edge case questions
✅ Prioritize ruthlessly (only ONE outcome per day)

### For AI Orchestrators:
✅ Review AI agent capacity before meeting
✅ Suggest agent assignments based on capability match
✅ Flag if agents are overloaded
✅ Provide confidence estimates for AI work

### For Developers:
✅ Ask clarifying questions early
✅ Surface technical risks immediately
✅ Commit realistically (don't over-promise)
✅ Identify pairing opportunities with AI

### For the Team:
✅ Start on time, end on time (30 min max)
✅ Stay focused (defer deep technical discussions)
✅ Make decisions, don't debate endlessly
✅ Leave with clear commitments

---

## Anti-Patterns to Avoid

❌ Selecting multiple outcomes ("we can do both")
❌ Vague success criteria ("make it better")
❌ Skipping risk assessment ("we'll figure it out")
❌ Overallocating AI agents (>100% total capacity)
❌ Unclear assignments ("someone will handle it")
❌ No demo plan ("we'll show whatever we finish")

---

## After the Meeting

**Immediately**:
- [ ] Post meeting notes to team channel
- [ ] Update project board with today's outcome
- [ ] Set feature flag to OFF (if new feature)
- [ ] Start execution phase (no delay!)

**AI Scribe Actions**:
- [ ] Generate meeting summary
- [ ] Create work tracking items
- [ ] Send reminders for demo attendance
- [ ] Prepare retrospective template for tomorrow

---

## Example: Filled Template

```
Morning Sync - November 5, 2025

Part 1: Retrospective Review
✅ Fixed flaky test in upload service (Marcus)
✅ Created architecture guide for Code Gen Agent (Sarah)
✅ Added Jessica to code review rotation (Team)

Part 2: Outcome Selection
SELECTED: Implement image cropping for profile pictures

Success Criteria:
✅ Users can select crop area before upload
✅ Image is cropped server-side to selected dimensions
✅ Aspect ratios: square, 16:9, 4:3 supported
✅ Works on mobile and desktop
✅ <300ms processing time

Business Value: 78% of user feedback requested this feature
Feature Flag: user.profile_picture.crop
Demo Plan: Show full upload + crop flow on staging

Part 3: AI Agent Assignments
🤖 Requirement Analyst (15%)
   - Analyze UX requirements for crop interface
   - Generate acceptance criteria for aspect ratios

🤖 Code Generation (65%)
   - Implement crop selection UI component
   - Add server-side cropping logic
   - Update API endpoint with crop parameters

🤖 Test Engineer (55%)
   - Generate tests for crop calculations
   - E2E tests for crop UI
   - Performance tests for crop processing

🤖 DevOps (10%)
   - No infrastructure changes needed
   - Monitor processing time

🤖 QA Validation (30%)
   - Security check for crop parameters
   - Cross-browser testing
   - Mobile responsiveness

👤 Sarah (Lead Dev)
   - Pair with Code Gen on UI component design
   - Review cropping algorithm
   - Handle edge cases (small images, extreme ratios)

👤 Marcus (Frontend)
   - Design crop interface UX
   - Integrate with existing upload flow
   - Mobile optimization

Part 4: Risks
⚠️ Risk: Complex UI interaction on mobile
   Mitigation: Start with desktop, mobile in next iteration if needed

🔗 Dependency: Design approval for crop interface
   Status: Designer will join demo at 5pm
```

---

**Remember**: The morning sync sets the tone for the day. Clear commitments = successful delivery.
