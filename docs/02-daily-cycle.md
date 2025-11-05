# The 24-Hour Cycle Framework

## Overview

The AAFM 24-hour cycle is the heartbeat of the methodology. It consists of four distinct phases executed across two calendar days:

- **Day N, Hour 0-1**: Morning Sync (Planning)
- **Day N, Hour 1-7**: Parallel Execution (Delivery)
- **Day N, Hour 7-8**: Daily Demo (Validation)
- **Day N+1, Hour 0-1**: Retrospective (Learning)

## Visual Timeline

```
Day N (Execution Day)
═══════════════════════════════════════════════════════════════
│ 9:00 │ 9:30      │           │            │         │ 5:00 │ 5:30 │
│──────┤───────────┤───────────┤────────────┤─────────┤──────┤──────│
│ Sync │  Human-AI │   Build   │ Continuous │ Deploy  │ Demo │ Done │
│      │  Pairing  │   Test    │ Validation │         │      │      │
│      │           │  Parallel │  Pipeline  │         │      │      │
└──────┴───────────┴───────────┴────────────┴─────────┴──────┴──────┘

Day N+1 (Learning Day)
═══════════════════════════════════════════════════════════════
│ 9:00 │ 9:30      │
│──────┤───────────┤
│Retro │ Start     │
│      │ Next      │
│      │ Cycle     │
└──────┴───────────┘
```

## Phase 1: Morning Sync (30 minutes)

**Time**: Day N, 0900-0930
**Participants**: Full team + AI Orchestrator
**Location**: Team room or video call

### Objectives

1. Review yesterday's retrospective actions
2. Select the highest-priority outcome for today
3. Assign AI agents to work items
4. Establish daily success criteria
5. Identify risks and dependencies

### Structure (30 minutes)

#### Part 1: Retrospective Review (5 min)
- **AI Scribe presents**: Yesterday's improvement actions
- **Team confirms**: Actions implemented or blocked
- **Example**:
  ```
  Yesterday we committed to:
  ✅ Reduce pipeline time by caching dependencies
  ✅ Add AI-generated integration tests
  ⚠️  Blocked: Staging environment access for QA agent
  ```

#### Part 2: Outcome Selection (10 min)
- **Product Owner presents**: Top 3 candidates from validated backlog
- **Team discusses**: Complexity, risks, dependencies
- **Decision**: Select ONE outcome to commit to today

  **Outcome Format**:
  ```
  📋 Outcome: [Business-facing description]

  Success Criteria:
  ✅ [Measurable criterion 1]
  ✅ [Measurable criterion 2]
  ✅ [Measurable criterion 3]

  Business Value: [Impact statement]
  Feature Flag: [flag.name]
  ```

#### Part 3: AI Agent Assignment (10 min)
- **AI Orchestrator proposes**: Agent allocation for selected work
- **Team reviews**: Capacity, capability match, risks
- **Example**:
  ```
  Outcome: Implement user profile image upload

  AI Agent Assignments:
  🤖 Requirement Analyst Agent (10% capacity)
     - Analyze security requirements for file uploads
     - Generate acceptance criteria for edge cases

  🤖 Code Generation Agent (60% capacity)
     - Implement file upload API endpoint
     - Add image validation and resizing
     - Update user model and database schema

  🤖 Test Engineer Agent (50% capacity)
     - Generate unit tests for upload service
     - Create integration tests for API
     - Build E2E tests for UI flow

  🤖 DevOps Agent (20% capacity)
     - Configure S3 bucket for image storage
     - Update deployment pipeline
     - Add monitoring for upload failures

  🤖 QA Validation Agent (30% capacity)
     - Security scan for file upload vulnerabilities
     - Performance test for large image handling
     - Accessibility check for upload UI

  Human Developer Assignments:
  👤 Sarah (Lead Dev)
     - Pair with Code Gen Agent on API design
     - Review and refine generated code
     - Handle complex edge cases

  👤 Marcus (Frontend Dev)
     - Design upload UI/UX
     - Integrate with API
     - Pair with Test Agent on E2E tests
  ```

#### Part 4: Risk & Dependency Check (5 min)
- **Team identifies**:
  - Technical risks
  - External dependencies
  - Required decisions
  - Potential blockers

- **Mitigation plans**:
  ```
  Risk: Image storage may exceed S3 quota
  → Mitigation: DevOps Agent monitors usage, alerts at 80%

  Dependency: Need design approval for upload UI
  → Mitigation: Designer joins demo at 5pm for immediate feedback
  ```

### Morning Sync Outputs

1. ✅ One committed outcome for the day
2. ✅ AI agent assignments with capacity allocation
3. ✅ Human developer assignments
4. ✅ Success criteria defined
5. ✅ Risks identified and mitigated
6. ✅ Stakeholder expectations set (who attends demo)

### Anti-Patterns to Avoid

❌ Selecting multiple outcomes ("we can do both")
❌ Accepting vague success criteria ("make it better")
❌ Skipping risk assessment ("we'll figure it out")
❌ Overallocating AI agents (>100% capacity)
❌ No clear definition of done

## Phase 2: Parallel Execution (6.5 hours)

**Time**: Day N, 0930-1600
**Mode**: Asynchronous collaboration with continuous integration

The execution phase runs three parallel streams simultaneously:

### Stream 1: Human-AI Pairing

**Humans focus on**:
- High-level design decisions
- Complex problem-solving
- Code review and refinement
- Edge case handling
- Architecture guidance

**AI agents focus on**:
- Code generation from specifications
- Boilerplate and repetitive code
- Test generation
- Documentation generation
- Refactoring for quality

**Pairing Patterns**:

#### Pattern A: AI Generates, Human Reviews
```
1. Human writes specification/pseudocode
2. AI generates implementation
3. Human reviews, provides feedback
4. AI refines based on feedback
5. Human approves or iterates
```

#### Pattern B: Human Guides, AI Executes
```
1. Human describes desired outcome
2. AI proposes multiple approaches
3. Human selects approach
4. AI implements
5. Human validates
```

#### Pattern C: Collaborative Refinement
```
1. AI generates initial implementation
2. Human identifies improvements
3. AI and human iterate together
4. Converge on optimal solution
```

### Stream 2: Continuous Validation Pipeline

**Automated checks running continuously**:

```
Code Commit
    ↓
[AI Monitors]
    ↓
┌───────────────────┐
│ Linting & Format  │ ← AI auto-fixes
├───────────────────┤
│ Unit Tests        │ ← AI generates missing tests
├───────────────────┤
│ Integration Tests │ ← AI validates contracts
├───────────────────┤
│ Security Scan     │ ← AI fixes CVEs
├───────────────────┤
│ Performance Test  │ ← AI optimizes hot paths
├───────────────────┤
│ Quality Gates     │ ← AI refactors if needed
└───────────────────┘
    ↓
[All Green?]
    ↓
Auto-Deploy to Staging
```

**Traffic Light Validation** (detailed in [04-validation-gates.md](./04-validation-gates.md)):

🟢 **Green** (90%+ confidence): Auto-proceed
🟡 **Yellow** (70-90% confidence): Human review flagged
🔴 **Red** (<70% confidence): Blocked, requires intervention

### Stream 3: Build-Test-Deploy Pipeline

**Automated pipeline**:

```yaml
On: [push, pull_request]

Steps:
  1. Build
     - Compile/transpile code
     - Bundle assets
     - Generate artifacts
     - AI validates build output

  2. Test
     - Run test suites (unit, integration, E2E)
     - AI analyzes failures
     - AI suggests fixes for failing tests
     - Auto-retry with AI fixes

  3. Deploy to Staging
     - Feature flag: OFF by default
     - Smoke tests
     - AI monitors logs for errors
     - Health checks

  4. Notify Team
     - Success: Ready for demo
     - Failure: AI reports issues + suggested fixes
```

**AI DevOps Agent Responsibilities**:
- Monitor pipeline health
- Optimize build times
- Manage infrastructure as code
- Handle deployment rollbacks
- Alert on anomalies

### Execution Phase Best Practices

#### For Humans:
- ✅ Stay focused on one outcome
- ✅ Provide clear specifications to AI
- ✅ Review AI output promptly
- ✅ Trust but verify AI suggestions
- ✅ Escalate blockers immediately

#### For AI Orchestrators:
- ✅ Monitor agent capacity and performance
- ✅ Load-balance across agents
- ✅ Escalate when AI confidence is low
- ✅ Capture learnings for agent improvement
- ✅ Ensure agents have necessary context

#### For the Team:
- ✅ Use feature flags for safe deployment
- ✅ Keep main branch always deployable
- ✅ Write clear commit messages (for AI context)
- ✅ Document decisions in code comments
- ✅ Communicate continuously in team chat

## Phase 3: Daily Demo & Acceptance (30 minutes)

**Time**: Day N, 1700-1730
**Participants**: Team + Stakeholders + Product Owner
**Format**: Live demonstration of working software

### Objectives

1. Demonstrate the completed outcome
2. Validate business value delivered
3. Gather stakeholder feedback
4. Accept or reject the work
5. Identify follow-up items

### Structure (30 minutes)

#### Part 1: Outcome Recap (3 min)
- **Product Owner reminds**: What we committed to this morning
- **Show success criteria**: What we aimed to achieve

#### Part 2: Live Demo (15 min)
- **Developer demonstrates**: Working software in staging environment
- **Show**:
  - Happy path user flow
  - Key features implemented
  - Edge cases handled
  - Quality metrics (test coverage, performance)

- **Example Demo Script**:
  ```
  Today we implemented user profile image upload.

  [Screen share - Staging environment]

  1. User navigates to profile settings
  2. Clicks "Upload Photo"
  3. Selects image file (2MB JPG)
  4. Image is validated, resized, and uploaded
  5. Profile shows new image immediately
  6. Image is stored securely in S3

  Edge cases we handled:
  - Files too large (>10MB) → Error message
  - Invalid file types → Error message
  - Slow connections → Progress indicator

  Quality metrics:
  - Test coverage: 94%
  - API response time: <200ms
  - Security scan: No vulnerabilities
  - Accessibility: WCAG 2.1 AA compliant
  ```

#### Part 3: Q&A and Feedback (10 min)
- **Stakeholders ask questions**
- **Team demonstrates** additional aspects
- **Product Owner captures** feedback for backlog

#### Part 4: Acceptance Decision (2 min)
- **Product Owner decides**:
  - ✅ **Accept**: Deploy to production (with feature flag)
  - ⚠️ **Accept with caveats**: Deploy, but add follow-up items
  - ❌ **Reject**: Does not meet success criteria, rework needed

### Demo Best Practices

✅ **Do**:
- Demo in an environment identical to production
- Show real data (anonymized if necessary)
- Highlight AI contributions ("AI generated 85% of tests")
- Be transparent about limitations
- Capture feedback in real-time (AI Scribe helps)

❌ **Don't**:
- Demo from localhost
- Use mock data or stubs
- Gloss over unfinished aspects
- Get defensive about feedback
- Promise unvalidated future work

### After the Demo

**If Accepted**:
1. Deploy to production (feature flag OFF)
2. Monitor for issues
3. Plan feature flag rollout for Day N+1
4. Update documentation

**If Rejected**:
1. Understand gaps clearly
2. Plan rework for Day N+1
3. Adjust process to prevent recurrence
4. Retrospective discusses why success criteria weren't met

## Phase 4: Daily Retrospective (30 minutes)

**Time**: Day N+1, 0900-0930 (before next Morning Sync)
**Participants**: Full team + AI Orchestrator
**Format**: Data-driven, action-oriented

### Objectives

1. Analyze what happened yesterday
2. Identify improvements
3. Commit to 2-3 concrete actions for today
4. Continuously improve the process

### Structure (30 minutes)

#### Part 1: AI-Prepared Analytics (5 min)

**AI Scribe Agent presents**:

```
📊 Daily Metrics Report - [Date]

Outcome: User profile image upload
Status: ✅ Accepted

Velocity Metrics:
- Lead time: 8.5 hours (target: <8h)
- Deployment count: 1
- Cycle time: 7.8 hours
- Commits: 24
- PRs merged: 3

AI Effectiveness:
- AI-generated code: 72%
- AI-generated tests: 89%
- Human intervention rate: 18%
- AI suggestion acceptance: 91%

Quality Metrics:
- Test coverage: 94% (target: >90%)
- Defects found: 0
- Security vulnerabilities: 0
- Performance: All green

Bottlenecks Identified:
⚠️ Build pipeline took 45 min (3 retries due to flaky test)
⚠️ Code review wait time: 1.2 hours

Predictive Insights:
ℹ️ Similar work items averaged 6.5h - we're 2h over
ℹ️ DevOps Agent capacity at 90% - consider offloading
```

#### Part 2: Team Discussion (20 min)

**Framework: 4Ls (Liked, Learned, Lacked, Longed For)**

**Liked** (What went well?):
```
✅ AI generated comprehensive tests, saved ~2 hours
✅ Pairing session with Code Gen Agent was smooth
✅ Feature flag deployment was seamless
✅ Stakeholders loved the demo
```

**Learned** (What did we discover?):
```
💡 AI struggles with S3 permission configurations
💡 Image processing library has good AI documentation
💡 Daily demos keep stakeholders engaged
💡 Flaky tests cause pipeline delays
```

**Lacked** (What was missing?):
```
❌ Design spec wasn't detailed enough (AI had to guess)
❌ Test environment intermittently slow
❌ Code review bottleneck (only Sarah available)
```

**Longed For** (What do we wish we had?):
```
🌟 Faster feedback on AI-generated code
🌟 Better AI understanding of our architecture patterns
🌟 Automated design mockup generation
🌟 Real-time test coverage visualization
```

#### Part 3: Action Commitments (5 min)

**Team commits to 2-3 improvements**:

```
Today's Improvement Actions:

1. 🎯 Fix flaky test in upload service
   Owner: Marcus
   Why: Prevents pipeline delays
   Done when: Test passes 10 consecutive runs

2. 🎯 Create architecture guide for AI Code Agent
   Owner: Sarah
   Why: Reduce AI "guessing" on patterns
   Done when: AI uses consistent patterns

3. 🎯 Add second code reviewer to rotation
   Owner: Team
   Why: Eliminate review bottleneck
   Done when: <30min average review time
```

### Retrospective Anti-Patterns

❌ Blame culture ("Why did Marcus write that bug?")
❌ No actions committed ("Let's just be more careful")
❌ Vague actions ("Improve code quality")
❌ Ignoring data ("I feel like we're slow" vs. metrics)
❌ Too many actions (>3 is unrealistic for daily implementation)

## Cycle Metrics Dashboard

Teams should maintain a real-time dashboard showing:

```
┌─────────────────────────────────────────────────────────┐
│ AAFM Team Dashboard - Day 247/365                      │
├─────────────────────────────────────────────────────────┤
│                                                         │
│ 🎯 Current Cycle Status: Execution Phase (Hour 4/8)    │
│                                                         │
│ Today's Outcome:                                        │
│ Implement user profile image upload                    │
│ Progress: [████████░░] 75%                             │
│                                                         │
│ ⏱️  Velocity Metrics                                    │
│   • Daily deployments: 1.2 avg (7-day)                 │
│   • Lead time: 7.8h avg                                │
│   • Cycle time: 7.2h avg                               │
│   • On-time delivery: 94%                              │
│                                                         │
│ 🤖 AI Effectiveness                                     │
│   • Code contribution: 68%                             │
│   • Test generation: 87%                               │
│   • Intervention rate: 15%                             │
│   • Time saved: 4.2h/day                               │
│                                                         │
│ ✅ Quality Gates                                        │
│   • Build: 🟢 Green                                     │
│   • Tests: 🟢 Green (94% coverage)                     │
│   • Security: 🟢 Green                                  │
│   • Performance: 🟢 Green                               │
│                                                         │
│ 📈 Trend (Last 30 Days)                                │
│   • Deployments: ↑ +12%                                │
│   • Defects: ↓ -23%                                    │
│   • AI efficiency: ↑ +8%                               │
│   • Team satisfaction: ↑ 8.7/10                        │
└─────────────────────────────────────────────────────────┘
```

## Adapting the Cycle

### For Different Time Zones

**Distributed Teams**:
- Async demos (record + review)
- Morning Sync becomes "Daily Sync" (find overlap hours)
- AI Scribe generates comprehensive summaries

### For Different Work Patterns

**Part-Time Teams**:
- Extend cycle to 48 hours
- Maintain same principles
- AI agents work during off-hours

**24/7 Teams**:
- Multiple cycles per day possible
- Handoff protocols critical
- AI agents provide continuity

### For Emergencies

**Production Incidents**:
- Pause planned cycle
- All hands on incident
- AI agents assist in triage and root cause analysis
- Resume cycle after resolution

## Next Steps

- Review [AI Agent Roles](./03-ai-agents.md) for detailed agent capabilities
- Study [Validation Gates](./04-validation-gates.md) for quality assurance
- Explore [Templates](../templates/) for ready-to-use meeting formats

---

**Remember**: The 24-hour cycle is a rhythm, not a deadline. The goal is sustainable daily delivery, not heroics.
