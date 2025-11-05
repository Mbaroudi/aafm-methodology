# AAFM Metrics Framework

Measuring Success in AI-Augmented Flow Methodology

---

## Overview

AAFM requires new metrics alongside traditional agile metrics to capture AI effectiveness, flow efficiency, and business value delivery.

**Measurement Philosophy**:
- Outcomes over outputs
- Flow over velocity
- Value over volume
- Learning over conformance

---

## Metric Categories

```
┌─────────────────────────────────────────────────────────┐
│ AAFM Metrics Hierarchy                                  │
├─────────────────────────────────────────────────────────┤
│                                                         │
│ 1. FLOW METRICS (How fast do we deliver?)              │
│    ├─ Daily deployment count                           │
│    ├─ Lead time                                        │
│    ├─ Cycle time                                       │
│    └─ Work in progress (WIP)                           │
│                                                         │
│ 2. QUALITY METRICS (How good is our work?)             │
│    ├─ Test coverage                                    │
│    ├─ Defect escape rate                               │
│    ├─ Production incidents                             │
│    └─ Security vulnerabilities                         │
│                                                         │
│ 3. AI EFFECTIVENESS (How well do we leverage AI?)      │
│    ├─ AI contribution percentage                       │
│    ├─ Human intervention rate                          │
│    ├─ AI suggestion acceptance                         │
│    └─ Time saved through automation                    │
│                                                         │
│ 4. BUSINESS VALUE (What impact do we have?)            │
│    ├─ Features delivered                               │
│    ├─ Customer satisfaction                            │
│    ├─ Revenue impact                                   │
│    └─ Time to market                                   │
│                                                         │
│ 5. TEAM HEALTH (How sustainable is this?)              │
│    ├─ Team satisfaction                                │
│    ├─ Burnout indicators                               │
│    ├─ Engagement levels                                │
│    └─ Learning and growth                              │
└─────────────────────────────────────────────────────────┘
```

---

## 1. Flow Metrics

### Daily Deployment Count

**Definition**: Number of production deployments per day (per team)

**Target**: 1.0+ (one deployment per team per day)

**Calculation**:
```
Daily Deployments = Total Deployments / Working Days
```

**Why it matters**: Validates daily delivery cadence

**Dashboard visualization**:
```
Daily Deployments (Last 30 Days)
│     1.2
│ ■ ■ ■ ■
│ ■ ■ ■ ■ ■
│ ■ ■ ■ ■ ■ ■ ■ ■ 0.8
│ ■ ■ ■ ■ ■ ■ ■ ■ ■ ■ ■
└─────────────────────────
  Week 1  2  3  4

Trend: ↑ +12% vs. previous month
```

**Red flags**:
- 🚩 <0.5 deployments/day: Not achieving daily cadence
- 🚩 High variance: Inconsistent delivery
- 🚩 Decreasing trend: Process degradation

---

### Lead Time

**Definition**: Time from idea conception to production deployment

**Target**: <24 hours (for work items in "ready" backlog)

**Calculation**:
```
Lead Time = Production Deployment Time - Idea Created Time
```

**Breakdown**:
```
Lead Time Components:
├─ Backlog time (idea → ready)
├─ Development time (ready → code complete)
├─ Testing time (code complete → all tests pass)
├─ Review time (waiting for approvals)
└─ Deployment time (approved → production)
```

**Why it matters**: Measures responsiveness to customer needs

**Example tracking**:
```
Work Item: WI-2025-142

Timestamps:
Nov 1, 09:00  - Idea created
Nov 3, 14:00  - Moved to "ready"
Nov 4, 09:00  - Development started
Nov 4, 16:30  - Code complete
Nov 4, 17:00  - Demo accepted
Nov 4, 17:30  - Deployed to production

Lead Time: 80.5 hours (idea → production)
Cycle Time: 7.5 hours (start → done)
```

---

### Cycle Time

**Definition**: Time from work start to completion (ready → done)

**Target**: <8 hours

**Calculation**:
```
Cycle Time = Work Complete Time - Work Start Time
```

**Why it matters**: Measures execution efficiency

**Distribution analysis**:
```
Cycle Time Distribution (Last 100 Work Items)

Count
  40│         ███
  30│      ███████
  20│   ██████████
  10│████████████████
   0└────────────────────
     <6h 6-8h 8-10h >10h

Avg: 7.2h
P50: 7.0h
P95: 9.5h
```

---

### Work in Progress (WIP)

**Definition**: Number of work items started but not completed

**Target**: 1 per team (strict WIP limit in AAFM)

**Why it matters**: Ensures focus, prevents context switching

**Dashboard**:
```
WIP Status (Real-time)

Team A: █ (1 item in progress) ✅
Team B: ██ (2 items in progress) ⚠️
Team C: █ (1 item in progress) ✅
Team D: ███ (3 items in progress) 🚨

Organization WIP: 7
Teams violating WIP limit: 2
```

**Red flags**:
- 🚩 WIP > 1 per team: Violating flow principle
- 🚩 Items aging >24h: Not completing daily

---

## 2. Quality Metrics

### Test Coverage

**Definition**: Percentage of code covered by automated tests

**Target**: ≥90% for new code

**Calculation**:
```
Test Coverage = (Lines Covered by Tests / Total Lines) × 100
```

**Breakdown**:
```
Coverage by Type:
├─ Unit tests: 95%
├─ Integration tests: 87%
├─ E2E tests: 78%
└─ Overall: 91%
```

**Trend tracking**:
```
Test Coverage Trend (6 Months)

  95%│           ●───●
  90%│     ●───●
  85%│ ●───●
  80%│
     └──────────────────
      M1  M2  M3  M4  M5  M6

Target: ≥90%
Current: 91% ✅
```

---

### Defect Escape Rate

**Definition**: Percentage of defects found in production vs. total defects

**Target**: <2%

**Calculation**:
```
Defect Escape Rate = (Production Defects / Total Defects) × 100

Where Total Defects = Dev Defects + Test Defects + Production Defects
```

**Why it matters**: Validates quality of AI-generated code and testing

**Example**:
```
Last Month Defects:
├─ Found in development: 45
├─ Found in testing: 12
├─ Found in production: 2
└─ Total: 59

Defect Escape Rate: 2/59 = 3.4% ⚠️ (Above target)
```

---

### Production Incidents

**Definition**: Number and severity of production issues

**Target**: <2 per week (for mature teams)

**Severity classification**:
```
SEV-1 (Critical): Service down, data loss
SEV-2 (High): Major feature broken, performance degraded
SEV-3 (Medium): Minor feature issue, workaround available
SEV-4 (Low): Cosmetic issue, no user impact
```

**Tracking**:
```
Production Incidents (Last Quarter)

Month 1: SEV-1: 0, SEV-2: 1, SEV-3: 3, SEV-4: 5
Month 2: SEV-1: 0, SEV-2: 0, SEV-3: 2, SEV-4: 4
Month 3: SEV-1: 0, SEV-2: 1, SEV-3: 1, SEV-4: 3

Trend: ↓ Decreasing ✅
MTTR: 45 minutes average
```

---

### Security Vulnerabilities

**Definition**: Number of security issues by severity

**Target**: 0 critical/high in production

**Tracking**:
```
Security Scan Results (Daily)

Critical:  0 ✅
High:      0 ✅
Medium:    2 ⚠️
Low:       5 ℹ️

AI Auto-Fixed: 12 this week
Human Review Required: 2
```

---

## 3. AI Effectiveness Metrics

### AI Contribution Percentage

**Definition**: Percentage of work (code, tests, docs) generated by AI

**Target**: >60% for code, >80% for tests

**Calculation**:
```
AI Code % = (Lines Generated by AI / Total Lines) × 100
AI Test % = (Tests Generated by AI / Total Tests) × 100
AI Docs % = (Docs Generated by AI / Total Docs) × 100
```

**Dashboard**:
```
AI Contribution (This Week)

Code:          ████████████░░░░░░░░ 68%
Tests:         ████████████████░░░░ 87%
Documentation: ██████████████████░░ 94%

Overall AI Contribution: 76%
Trend vs. last week: ↑ +4%
```

---

### Human Intervention Rate

**Definition**: How often humans need to fix/modify AI output

**Target**: <20%

**Calculation**:
```
Intervention Rate = (AI Outputs Modified by Humans / Total AI Outputs) × 100
```

**Breakdown by agent**:
```
Agent Performance:

Code Generation:    18% intervention ✅
Test Generation:    12% intervention ✅
Requirement Analyst: 8% intervention ✅
DevOps Agent:       25% intervention ⚠️
QA Validation:      15% intervention ✅

Target: <20%
```

**Why it matters**: Lower intervention = higher AI effectiveness

---

### AI Suggestion Acceptance Rate

**Definition**: Percentage of AI suggestions accepted by humans

**Target**: >85%

**Calculation**:
```
Acceptance Rate = (Accepted Suggestions / Total Suggestions) × 100
```

**Trend**:
```
AI Acceptance Rate (Last 90 Days)

  95%│               ●
  90%│          ●──●
  85%│     ●───●
  80%│ ●───●
     └────────────────────
      Week 1-12

Current: 91% ✅
Improving: +8% over 90 days
```

---

### Time Saved Through Automation

**Definition**: Hours saved per day through AI assistance

**Target**: >3 hours per team per day

**Calculation**:
```
Time Saved = Σ(Task Duration Without AI - Task Duration With AI)
```

**Example breakdown**:
```
Daily Time Savings (Per Team):

Code generation:     2.1 hours
Test generation:     1.8 hours
Documentation:       0.9 hours
Code review support: 0.6 hours
Bug analysis:        0.4 hours
────────────────────────────
Total:               5.8 hours/day ✅

Monthly value: 5.8h × 20 days = 116 hours
Annual value: ~1,400 hours per team
```

**ROI calculation**:
```
AI Cost:        $2,000/month
Time Saved:     116 hours/month
Avg Dev Cost:   $80/hour
Value Created:  116h × $80 = $9,280/month

ROI: (9,280 - 2,000) / 2,000 = 364% ✅
```

---

## 4. Business Value Metrics

### Features Delivered

**Definition**: Number of production-ready features deployed

**Target**: Varies by team, track trend

**Tracking**:
```
Features Delivered (Monthly)

Month 1: 18 features
Month 2: 22 features
Month 3: 25 features

Quarterly Total: 65 features
Avg per week: 5.4 features
Trend: ↑ +39% vs. previous quarter
```

---

### Customer Satisfaction (CSAT)

**Definition**: Customer satisfaction with delivered features

**Target**: >8/10

**Measurement**:
```
Post-deployment survey:
"How satisfied are you with [feature]?"

1 (Very Dissatisfied) ───────────── 10 (Very Satisfied)

Last 20 Features:
Average CSAT: 8.7/10 ✅
Distribution:
  10: ████████ (8)
   9: ██████ (6)
   8: ████ (4)
   7: █ (1)
   6: █ (1)
```

---

### Revenue Impact

**Definition**: Measurable revenue impact from features

**Target**: Varies by organization

**Tracking**:
```
Feature: Premium Profile Pictures
Deployed: Nov 5
Rollout: 100% by Nov 10

Metrics:
├─ Premium upgrades: +237 (first week)
├─ Revenue: +$4,740 (first week)
├─ Projected annual: $246,480
└─ ROI vs. development cost: 82x

Feature: Faster Checkout Flow
Deployed: Nov 8
Impact:
├─ Conversion rate: +2.3%
├─ Additional revenue: $12,400/week
└─ Payback period: 3 days
```

---

### Time to Market

**Definition**: Time from idea to customer availability

**Target**: <7 days (idea → 100% rollout)

**Example timeline**:
```
Feature: Image Cropping

Nov 1:  Idea validated (user research)
Nov 3:  Work item created and ready
Nov 4:  Development (1 day)
Nov 4:  Deployed with flag OFF (0% users)
Nov 5:  Internal testing (5% users)
Nov 6:  Gradual rollout (10% → 50%)
Nov 7:  Full rollout (100%)

Time to Market: 6 days ✅

Compare to traditional:
  Sprint planning:    Week 1
  Development:        Week 2-3
  Testing:            Week 4
  Deployment:         Week 5
  Rollout:            Week 6

  Traditional time to market: 6 weeks
  AAFM time to market: 6 days
  Improvement: 90% faster
```

---

## 5. Team Health Metrics

### Team Satisfaction

**Definition**: Team member satisfaction with AAFM process

**Target**: >8/10

**Survey questions** (weekly pulse):
```
1. How satisfied are you with the daily cycle process? (1-10)
2. Do you feel the workload is sustainable? (Yes/No/Sometimes)
3. Are AI agents helping or hindering? (Helping/Neutral/Hindering)
4. Would you recommend AAFM to other teams? (Yes/No)
5. What's your energy level this week? (1-10)
```

**Dashboard**:
```
Team Satisfaction (This Month)

Satisfaction:    8.9/10 ✅
Sustainability:  92% "Yes" ✅
AI Perception:   88% "Helping" ✅
Would Recommend: 94% "Yes" ✅
Energy Level:    7.8/10 ✅

Trend: → Stable
```

---

### Burnout Indicators

**Definition**: Signs of team stress or overwork

**Monitor**:
```
Red Flags:
🚩 Consistent overtime (>2 hours/day)
🚩 Weekend work (uninvited)
🚩 Vacation days not taken
🚩 Sick days increasing
🚩 Declining code quality
🚩 Increasing irritability in retrospectives

Current Status:
✅ Average hours: 40.2/week
✅ Weekend work: 0 hours (last month)
✅ Vacation utilization: 85%
✅ Sick days: Normal range
✅ Code quality: Stable
✅ Retrospective tone: Positive

Burnout Risk: LOW ✅
```

---

### Learning and Growth

**Definition**: Team skill development and career growth

**Track**:
```
Learning Metrics:

New Skills Acquired (This Quarter):
├─ AI prompt engineering: 5/5 team members
├─ Advanced testing patterns: 4/5
├─ Feature flag strategies: 5/5
└─ Performance optimization: 3/5

Certifications/Training:
├─ AI/ML courses completed: 3
├─ Architecture training: 2
└─ Leadership development: 1

Internal Knowledge Sharing:
├─ Brown bag sessions: 6 this quarter
├─ Blog posts written: 4
└─ Conference talks: 1
```

---

## Metric Dashboards

### Team-Level Dashboard (Daily)

```
┌─────────────────────────────────────────────────────────┐
│ Team A - Daily Dashboard                                │
│ Date: November 5, 2025                                  │
├─────────────────────────────────────────────────────────┤
│                                                         │
│ TODAY'S CYCLE STATUS                                    │
│ ├─ Outcome: Profile picture cropping                   │
│ ├─ Progress: [████████░░] 75%                          │
│ ├─ On track: ✅ Yes                                     │
│ └─ Demo: 17:00 (in 2 hours)                            │
│                                                         │
│ FLOW (7-day rolling)                                    │
│ ├─ Deployments/day: 1.2                                │
│ ├─ Avg cycle time: 7.2h                                │
│ ├─ WIP: 1 ✅                                            │
│ └─ On-time delivery: 94%                               │
│                                                         │
│ QUALITY (current cycle)                                 │
│ ├─ Test coverage: 94% ✅                                │
│ ├─ Security scan: 🟢 Pass                              │
│ ├─ Performance: 🟢 Pass                                │
│ └─ Accessibility: 🟢 Pass                              │
│                                                         │
│ AI EFFECTIVENESS (this week)                            │
│ ├─ Code contribution: 68%                              │
│ ├─ Test generation: 87%                                │
│ ├─ Intervention rate: 18%                              │
│ └─ Time saved: 5.2h/day                                │
│                                                         │
│ TEAM HEALTH                                             │
│ ├─ Satisfaction: 8.9/10                                │
│ ├─ Energy level: 8.1/10                                │
│ └─ Burnout risk: LOW ✅                                 │
└─────────────────────────────────────────────────────────┘
```

---

### Product Line Dashboard (Weekly)

```
┌─────────────────────────────────────────────────────────┐
│ Product Line - Weekly Dashboard                         │
│ Week of: November 4-8, 2025                             │
├─────────────────────────────────────────────────────────┤
│                                                         │
│ AGGREGATE VELOCITY (5 teams)                            │
│ ├─ Total deployments: 28                               │
│ ├─ Avg deployments/team: 5.6                           │
│ ├─ Features delivered: 22                              │
│ └─ Trend: ↑ +8% vs. last week                          │
│                                                         │
│ DEPENDENCY HEALTH                                       │
│ ├─ Dependencies resolved: 18/20 (90%)                  │
│ ├─ Avg resolution time: 4.2h                           │
│ ├─ Blocking dependencies: 0 ✅                          │
│ └─ Integration success: 96%                            │
│                                                         │
│ QUALITY (aggregate)                                     │
│ ├─ Avg test coverage: 91%                              │
│ ├─ Production incidents: 1 (SEV-3)                     │
│ ├─ Defect escape rate: 1.8%                            │
│ └─ Security: 0 critical/high                           │
│                                                         │
│ AI ROI                                                  │
│ ├─ Total time saved: 130h this week                    │
│ ├─ Value created: $10,400                              │
│ ├─ AI costs: $2,500                                    │
│ └─ ROI: 316% ✅                                         │
│                                                         │
│ BUSINESS VALUE                                          │
│ ├─ Customer satisfaction: 8.7/10                       │
│ ├─ Revenue impact: +$18,200                            │
│ └─ Time to market: -87% vs. baseline                   │
└─────────────────────────────────────────────────────────┘
```

---

## Metric Collection

### Automated Collection

```yaml
# metrics-config.yaml

collectors:
  - name: deployment_tracker
    source: ci_cd_pipeline
    metrics:
      - deployment_count
      - deployment_success_rate
      - deployment_duration

  - name: code_metrics
    source: git
    metrics:
      - commits_per_day
      - lines_added
      - lines_deleted
      - ai_generated_percentage

  - name: quality_metrics
    source: test_framework
    metrics:
      - test_coverage
      - test_pass_rate
      - test_execution_time

  - name: ai_metrics
    source: ai_orchestrator
    metrics:
      - ai_contribution_percentage
      - intervention_rate
      - suggestion_acceptance_rate
      - time_saved

  - name: incident_tracker
    source: monitoring
    metrics:
      - incident_count
      - severity_distribution
      - mttr
      - mtbf

reporting:
  frequency: realtime
  aggregation: [daily, weekly, monthly, quarterly]
  dashboards:
    - team_daily
    - product_line_weekly
    - executive_monthly
```

---

## Next Steps

- Review [Getting Started Guide](../guides/getting-started.md) to begin implementation
- Set up automated metric collection
- Create dashboards for your team
- Establish baseline metrics
- Track improvements over time

---

**Remember**: Metrics are for learning and improvement, not punishment. Focus on trends, not absolutes.
