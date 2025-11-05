# Getting Started with AAFM

A practical guide to launching your first AAFM team

---

## Overview

This guide walks you through setting up your first AAFM team, from initial assessment through your first successful 24-hour cycle.

**Timeline**: 4-8 weeks from decision to first daily deployment

---

## Phase 1: Assessment & Preparation (Week 1-2)

### Step 1: Assess Technical Readiness

Use the [Technical Prerequisites](../docs/06-technical-prerequisites.md) checklist:

```
Critical Prerequisites (MUST HAVE):
□ Version control (Git)
□ Automated CI/CD pipeline
□ Automated testing (unit + integration)
□ Infrastructure as Code
□ Deployment automation

Recommended (SHOULD HAVE):
□ Modular architecture
□ Feature flag system
□ Comprehensive observability
□ Automated security scanning
□ Performance monitoring
```

**Decision Point**:
- ✅ All critical items complete → Proceed to Phase 2
- ⚠️ Missing 1-2 critical items → Complete them before proceeding (2-4 weeks)
- ❌ Missing 3+ critical items → Not ready, build foundations first (2-3 months)

---

### Step 2: Select Pilot Team

**Ideal pilot team characteristics**:

✅ **Technical maturity**: Strong CI/CD, good test coverage
✅ **Team composition**: 3-5 people (not too large)
✅ **Motivation**: Enthusiastic about trying new methodology
✅ **Autonomy**: Can make decisions without excessive approval
✅ **Business support**: Stakeholder willing to attend daily demos
✅ **Low risk**: Non-critical path (safe to experiment)

**Red flags for pilot teams**:
❌ Brand new team (no established patterns)
❌ Actively firefighting production issues
❌ Rigid compliance requirements
❌ Distributed across many time zones
❌ Skeptical or resistant team members

---

### Step 3: Secure Resources

**Required roles**:

```
Core Team:
├─ Product Owner (1)
│  Time commitment: 50% (2-3 hours/day for ceremonies)
├─ Developers (2-4)
│  Time commitment: 100%
├─ AI Orchestrator (1)
│  Time commitment: 100%
│  Can be a developer who takes on this role
└─ QA/DevOps (1, can be shared)
   Time commitment: 25-50%

Supporting Roles:
├─ Executive Sponsor
│  Removes organizational blockers
├─ AAFM Coach (optional but recommended)
│  Guides methodology adoption
└─ Stakeholder
   Time commitment: 30 min/day for demos
```

**AI infrastructure**:
```
□ AI model access (OpenAI, Anthropic, or equivalent)
□ Budget for AI API costs (~$500-2000/month initially)
□ AI agent framework setup (if using custom agents)
□ Prompt library and versioning system
```

---

### Step 4: Training & Orientation

**Week 1: Methodology Training** (8 hours total)

```
Day 1 (2 hours):
- AAFM overview and principles
- Why daily delivery?
- Core vs. traditional agile

Day 2 (2 hours):
- 24-hour cycle framework deep dive
- Morning sync, execution, demo, retrospective
- Role responsibilities

Day 3 (2 hours):
- AI agents roles and capabilities
- Human-AI collaboration patterns
- AI orchestration basics

Day 4 (2 hours):
- Technical setup and tools
- Feature flags, validation gates
- Practice run (mock cycle)
```

**Recommended resources**:
- [ ] Read [Core Methodology](../docs/01-core-methodology.md)
- [ ] Read [Daily Cycle Framework](../docs/02-daily-cycle.md)
- [ ] Watch AAFM demo videos (if available)
- [ ] Visit high-performing AAFM team (if possible)

---

## Phase 2: Technical Setup (Week 2-3)

### Step 5: Infrastructure Configuration

**CI/CD Pipeline Optimization**:

```bash
# Target: Pipeline completes in <15 minutes

Current pipeline time: [X] minutes

Optimizations to implement:
□ Cache dependencies
□ Parallelize test execution
□ Use incremental builds
□ Implement smart test selection
□ Optimize Docker layer caching

Test: Run pipeline 5 times, measure average time
Goal: Achieve <15 min average
```

**Feature Flag Setup**:

```javascript
// Example: LaunchDarkly, Unleash, or similar

// 1. Install feature flag SDK
npm install launchdarkly-node-server-sdk

// 2. Initialize
const client = LaunchDarkly.init(SDK_KEY);

// 3. Create default feature flags
await client.createFeatureFlag({
  key: 'aafm.pilot.enabled',
  name: 'AAFM Pilot Features',
  variations: [true, false],
  targeting: {
    enabled: true,
    rules: [
      {
        variation: 0, // true
        clauses: [{ attribute: 'team', op: 'in', values: ['pilot'] }]
      }
    ]
  }
});

// 4. Test feature flag
console.log('Feature enabled:', await client.variation('aafm.pilot.enabled', user));
```

**Observability Setup**:

```yaml
# Logging (Structured logs)
logging:
  format: json
  level: info
  fields:
    - timestamp
    - level
    - message
    - service
    - correlation_id

# Metrics (Prometheus)
metrics:
  enabled: true
  endpoint: /metrics
  collectors:
    - http_requests_total
    - http_request_duration_seconds
    - application_errors_total

# Tracing (OpenTelemetry)
tracing:
  enabled: true
  exporter: jaeger
  sampling_rate: 0.1
```

---

### Step 6: AI Agent Setup

**Choose AI Provider**:

```
Option A: Cloud AI APIs (Recommended for starting)
├─ Pros: Easy setup, no infrastructure, latest models
├─ Cons: Ongoing costs, rate limits, data privacy concerns
└─ Examples: OpenAI GPT-4, Anthropic Claude, Google PaLM

Option B: Self-Hosted Open Source
├─ Pros: Full control, no usage limits, data stays local
├─ Cons: Requires GPU infrastructure, ongoing maintenance
└─ Examples: LLaMA 2, Mistral, CodeLlama

Recommendation: Start with Option A, consider Option B later
```

**Configure AI Agents**:

```python
# Example AI agent configuration
# agents/config.yaml

agents:
  - name: code_generation
    model: gpt-4
    temperature: 0.2
    max_tokens: 2000
    prompt_template: prompts/code-generation.txt
    tools:
      - file_read
      - file_write
      - code_analysis

  - name: test_generation
    model: gpt-4
    temperature: 0.3
    max_tokens: 3000
    prompt_template: prompts/test-generation.txt
    tools:
      - code_read
      - test_framework_access

  - name: requirement_analysis
    model: gpt-4
    temperature: 0.5
    max_tokens: 1500
    prompt_template: prompts/requirement-analysis.txt

# Load and initialize
from ai_orchestrator import AgentManager

manager = AgentManager.from_config('agents/config.yaml')
await manager.initialize()
```

**Test AI Agents**:

```python
# Test each agent with sample tasks

async def test_agents():
    # Test Code Generation Agent
    code = await manager.get_agent('code_generation').generate(
        prompt="Create a function to upload a file to S3"
    )
    assert 'S3' in code
    assert 'upload' in code

    # Test Test Generation Agent
    tests = await manager.get_agent('test_generation').generate(
        prompt="Generate tests for the S3 upload function",
        context=code
    )
    assert 'test' in tests.lower()
    assert 's3' in tests.lower()

    print("✅ All agents working")

# Run tests
await test_agents()
```

---

### Step 7: Backlog Preparation

**Prepare 10 "Ready" Work Items**:

Each work item must meet these criteria:

```
✅ Can be completed in < 8 hours with AI assistance
✅ Independently deployable (no dependencies)
✅ Clear business value articulated
✅ Specific, measurable success criteria
✅ Technical design reviewed
✅ No blocking dependencies

Use the [Work Item Template](../templates/work-item.md)
```

**Example ready backlog**:

```
Priority 1: Add "forgot password" flow
├─ Estimated effort: 6 hours
├─ Value: 15% of support tickets are password resets
├─ Dependencies: None
└─ Status: ✅ Ready

Priority 2: Implement user search in admin panel
├─ Estimated effort: 7 hours
├─ Value: Admins manually scroll through lists today
├─ Dependencies: None
└─ Status: ✅ Ready

Priority 3: Add profile picture upload
├─ Estimated effort: 8 hours
├─ Value: 78% of users requested this
├─ Dependencies: None
└─ Status: ✅ Ready

[Continue for 7 more items...]
```

**Backlog refinement session**:
- Product Owner presents candidates
- AI Requirement Analyst reviews each
- Team estimates with AI assistance
- Refine until 10 items are "Ready"

---

## Phase 3: Dry Run (Week 3)

### Step 8: Mock 24-Hour Cycle

**Run a practice cycle with NO production deployment**:

```
Day 1: Practice Cycle

09:00-09:30: Mock Morning Sync
├─ Select a simple, low-risk work item
├─ Assign AI agents
├─ Commit to success criteria
└─ Practice the format

09:30-16:00: Execution Phase
├─ Developers pair with AI agents
├─ Continuous validation in background
├─ Practice using feature flags
└─ Deploy to staging only (not production)

17:00-17:30: Mock Demo
├─ Present to team (not stakeholders)
├─ Practice demo format
├─ Get comfortable with flow
└─ Identify improvements

Day 2 Morning: Mock Retrospective
├─ Review metrics
├─ Discuss what went well/poorly
├─ Identify adjustments for real cycle
└─ Commit to process improvements
```

**Debrief after mock cycle**:

```
Questions to answer:
□ Did we complete the work item?
□ Was the morning sync effective?
□ Did AI agents work as expected?
□ Was the CI/CD pipeline fast enough?
□ Did we have the right metrics?
□ Is the team comfortable with the format?
□ What would we change for the real cycle?

If most answers are positive → Proceed to Phase 4
If significant issues → Fix them and run another dry run
```

---

## Phase 4: First Live Cycle (Week 4)

### Step 9: First Production Deployment

**Your first real 24-hour cycle!**

**Pre-Cycle Preparation**:
```
Day Before:
□ Stakeholder confirmed for demo (17:00)
□ Work item selected and ready
□ AI agents tested and ready
□ Monitoring dashboards configured
□ Team energized and prepared
□ Executive sponsor aware (for support if needed)
```

**Day 1: The Cycle**:

```
09:00-09:30: Morning Sync
- Use [Morning Sync Template](../templates/morning-sync.md)
- Keep energy high, confidence strong
- Select achievable (not ambitious) work item
- Clear success criteria

09:30-16:00: Execution
- Focus on delivering value
- Use AI agents actively
- Communicate frequently
- Celebrate small wins
- Address blockers immediately

17:00-17:30: Demo
- Use [Daily Demo Template](../templates/daily-demo.md)
- Show working software in staging
- Be transparent about any limitations
- Get stakeholder feedback
- Celebrate the achievement!

Post-Demo:
- If accepted: Deploy to production (feature flag OFF)
- Set up monitoring
- Plan gradual rollout

Day 2 Morning: Retrospective
- Use [Retrospective Template](../templates/daily-retrospective.md)
- Review metrics
- Celebrate success
- Identify 2-3 improvements
- Commit to next cycle
```

**What success looks like**:

```
✅ Work item completed and accepted
✅ Deployed to production (even if flag OFF)
✅ No major incidents
✅ Team felt good about the process
✅ Stakeholder satisfied
✅ Metrics captured
✅ Improvements identified for next cycle

It's okay if:
⚠️ Took slightly longer than 8 hours (you'll improve)
⚠️ AI agents needed more human intervention than expected
⚠️ Some rough edges in the process
⚠️ Not everything was perfect

Red flags (address immediately):
🚨 Work item not completed
🚨 Quality issues or security problems
🚨 Team stressed or burned out
🚨 Stakeholder unhappy with approach
🚨 Technical foundation lacking
```

---

## Phase 5: Establish Rhythm (Week 4-8)

### Step 10: Daily Cycles for 4 Weeks

**Week 1: Find Your Rhythm**
```
Goals:
□ Complete 5 consecutive daily cycles
□ Establish ceremony cadence
□ Build team confidence
□ Optimize AI agent usage

Metrics to track:
- Cycle completion rate
- Lead time
- AI effectiveness
- Quality metrics
- Team satisfaction
```

**Week 2: Improve Efficiency**
```
Goals:
□ Reduce cycle time
□ Improve AI autonomy
□ Streamline ceremonies
□ Optimize pipeline

Focus areas:
- Identify and remove bottlenecks
- Improve AI prompts and training
- Refine work item sizing
- Enhance monitoring
```

**Week 3: Scale Quality**
```
Goals:
□ Increase test coverage
□ Improve security posture
□ Enhance observability
□ Reduce defect rate

Quality improvements:
- Comprehensive validation gates
- Better AI test generation
- Proactive monitoring
- Faster incident response
```

**Week 4: Demonstrate Value**
```
Goals:
□ Show business impact
□ Celebrate achievements
□ Share learnings
□ Plan expansion

Success showcase:
- 20 features delivered in 4 weeks
- Metrics show improvement
- Stakeholder satisfaction high
- Team wants to continue
```

---

## Common Challenges & Solutions

### Challenge 1: "We Can't Finish in 8 Hours"

**Symptoms**:
- Consistently taking 10-12 hours
- Work items too large
- Frequent scope creep

**Solutions**:
- ✅ Break down work items smaller
- ✅ Improve AI agent effectiveness
- ✅ Simplify technical architecture
- ✅ Cut scope more aggressively
- ✅ Optimize CI/CD pipeline

---

### Challenge 2: "AI Agents Aren't Helping"

**Symptoms**:
- High human intervention rate
- Low AI suggestion acceptance
- More work to review AI output than doing it manually

**Solutions**:
- ✅ Improve prompt engineering
- ✅ Provide better context to AI
- ✅ Fine-tune models with your codebase
- ✅ Start with simpler AI tasks
- ✅ Train team on effective AI collaboration

---

### Challenge 3: "Stakeholders Won't Attend Daily Demos"

**Symptoms**:
- Low demo attendance
- Feedback delayed
- Acceptance decisions postponed

**Solutions**:
- ✅ Make demos engaging and valuable
- ✅ Respect stakeholder time (keep to 30 min)
- ✅ Allow rotating attendance
- ✅ Record demos for async review
- ✅ Show real business impact

---

### Challenge 4: "Quality Is Suffering"

**Symptoms**:
- Increased defect rate
- Security vulnerabilities
- Technical debt accumulating

**Solutions**:
- ✅ Strengthen Definition of Done
- ✅ Improve validation gates
- ✅ Don't skip retrospective actions
- ✅ Allocate time for refactoring
- ✅ Slow down if necessary (daily delivery ≠ rushed delivery)

---

## Success Criteria

After 4 weeks, you should achieve:

```
✅ Velocity
   - 15-20 deployments (3-4 per week)
   - Average cycle time <10 hours
   - 80%+ work items completed on first attempt

✅ Quality
   - Test coverage >85%
   - Zero critical/high security vulnerabilities
   - <2% defect escape rate
   - No major production incidents

✅ AI Effectiveness
   - AI code contribution >50%
   - AI test generation >70%
   - Human intervention rate <30%
   - Time saved >3 hours/day

✅ Team Health
   - Team satisfaction >7/10
   - No signs of burnout
   - High engagement in ceremonies
   - Enthusiasm for continuation

✅ Stakeholder Satisfaction
   - Stakeholder NPS >8
   - Regular demo attendance
   - Positive feedback on velocity
   - Requesting feature expansion
```

---

## Next Steps After Pilot

**If successful** (meeting most success criteria):

1. **Continue for another month**
   - Solidify practices
   - Build more confidence
   - Accumulate more data

2. **Share learnings**
   - Present to other teams
   - Document case study
   - Identify best practices

3. **Plan expansion**
   - Select next pilot team
   - Scale infrastructure
   - Train additional AI Orchestrators
   - Build shared services

4. **Formalize AAFM adoption**
   - Executive endorsement
   - Budget allocation
   - Organizational rollout plan
   - Center of Excellence

**If struggling** (not meeting criteria):

1. **Diagnose root causes**
   - Technical limitations?
   - Team readiness?
   - Organizational constraints?
   - Methodology fit?

2. **Address gaps**
   - Strengthen prerequisites
   - Additional training
   - Process adjustments
   - Resource additions

3. **Consider alternatives**
   - Extend cycle to 48 hours
   - Hybrid approach with sprints
   - Focus on specific practices
   - Delay full adoption

---

## Resources

- [Core Methodology](../docs/01-core-methodology.md)
- [Daily Cycle Framework](../docs/02-daily-cycle.md)
- [AI Agents Guide](../docs/03-ai-agents.md)
- [Technical Prerequisites](../docs/06-technical-prerequisites.md)
- [Templates](../templates/)
- [Metrics Framework](../metrics/framework.md)

---

## Getting Help

**Common Support Needs**:
- AI agent configuration issues
- CI/CD optimization
- Methodology questions
- Team coaching
- Stakeholder management

**Resources**:
- AAFM community forums
- Methodology coaches
- AI Center of Excellence
- Peer teams (if available)

---

**Remember**: The first cycle is the hardest. It gets easier and more valuable with each iteration. Focus on learning, not perfection!
