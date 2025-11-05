# Daily Demo Template

**Time**: 30 minutes
**Frequency**: Daily (end of execution day)
**Participants**: Team + Stakeholders + Product Owner

---

## Pre-Demo Checklist

**30 Minutes Before Demo**:
- [ ] Feature deployed to staging environment
- [ ] Smoke tests passed
- [ ] Demo script prepared
- [ ] Stakeholders confirmed attendance
- [ ] Screen sharing tested
- [ ] Fallback plan ready (if demo environment issues)

---

## Demo Structure

### Part 1: Outcome Recap (3 min)

**Product Owner reminds attendees of morning commitment**

```
Today's Committed Outcome:
[Brief description of what was committed this morning]

Success Criteria Review:
✅ [Criterion 1] - We committed to achieve this
✅ [Criterion 2] - We committed to achieve this
✅ [Criterion 3] - We committed to achieve this

Business Context:
[Why this matters, who benefits, expected impact]
```

---

### Part 2: Live Demonstration (15 min)

**Developer demonstrates working software**

**Demo Script Template**:

```
"Today we implemented [outcome description]."

[Screen share - Staging environment]

Step 1: [User action]
├─ What user does: [Description]
├─ What system does: [Response]
└─ Result: [Outcome]

Step 2: [User action]
├─ What user does: [Description]
├─ What system does: [Response]
└─ Result: [Outcome]

[Continue for main flow...]

Edge Cases We Handled:
✅ [Edge case 1] → [How we handle it]
✅ [Edge case 2] → [How we handle it]
✅ [Edge case 3] → [How we handle it]

Quality Metrics:
✅ Test coverage: ___%
✅ Performance: [metric] (target: [target])
✅ Security: [scan results]
✅ Accessibility: [compliance level]

AI Contributions:
🤖 AI-generated code: ___%
🤖 AI-generated tests: ___%
🤖 Time saved: ___ hours
```

**Demonstration Best Practices**:
- Use real staging environment (not localhost)
- Show actual user workflows (not technical details)
- Demonstrate happy path first, then edge cases
- Keep technical jargon minimal
- Have backup plan if environment issues

---

### Part 3: Q&A and Feedback (10 min)

**Stakeholder Questions**:

```
Q: [Stakeholder question]
A: [Team response]
   [Demo additional aspect if needed]

Q: [Stakeholder question]
A: [Team response]
   [Demo additional aspect if needed]

Feedback Captured:
💡 [Suggestion 1] - Priority: [High/Medium/Low]
💡 [Suggestion 2] - Priority: [High/Medium/Low]
💡 [Suggestion 3] - Priority: [High/Medium/Low]

Follow-up Items:
📋 [Item to add to backlog]
📋 [Item to add to backlog]
```

**AI Scribe captures all feedback in real-time**

---

### Part 4: Acceptance Decision (2 min)

**Product Owner makes acceptance decision**

```
Decision: [✅ Accept / ⚠️ Accept with Caveats / ❌ Reject]

Rationale:
[Explanation of decision]

✅ ACCEPT:
   Next Steps:
   1. Deploy to production with feature flag OFF
   2. Monitor baseline metrics
   3. Plan rollout for [date/time]
   4. Success metrics to track: [list]

⚠️ ACCEPT WITH CAVEATS:
   Accepted because: [Core value delivered]
   Caveats:
   - [Minor issue 1] → Follow-up item created
   - [Minor issue 2] → Follow-up item created
   Next Steps: [Same as Accept, plus follow-up scheduling]

❌ REJECT:
   Gaps identified:
   - [What's missing]
   - [What doesn't meet criteria]
   Next Steps:
   1. Rework plan for tomorrow
   2. Retrospective discusses root cause
   3. Re-demo when ready
```

---

## Demo Templates by Feature Type

### Template A: New User Feature

```
Demo Script Example:

"Today we implemented profile picture cropping."

[Show user profile page]

"Users can now select a custom crop area for their profile picture."

Step 1: User clicks "Upload Photo"
├─ System shows file picker
└─ User selects image file

Step 2: Crop interface appears
├─ User sees their image with crop overlay
├─ User can drag to reposition
├─ User can select aspect ratio (square, 16:9, 4:3)
└─ Preview shows final result

Step 3: User clicks "Save"
├─ System crops image server-side
├─ Upload progress shown
└─ Profile updates with cropped image

Edge Cases:
✅ Small images → Warning shown, crop still works
✅ Extreme aspect ratios → Sensible defaults applied
✅ Slow connection → Progress indicator shown

Quality:
✅ Works on Chrome, Firefox, Safari, Edge
✅ Mobile-responsive (tested on iOS and Android)
✅ Accessibility: Keyboard navigation, screen reader support
```

---

### Template B: API / Backend Feature

```
Demo Script Example:

"Today we implemented bulk user data export API."

[Show API documentation]

"The new /api/users/export endpoint allows admins to export user data."

Step 1: Admin authenticates
[Show Postman/Insomnia request]
POST /api/auth/login
✅ Returns JWT token

Step 2: Admin requests export
POST /api/users/export
{
  "filters": { "role": "customer", "created_after": "2025-01-01" },
  "format": "csv"
}
✅ Returns job ID

Step 3: System processes export
GET /api/users/export/:jobId
✅ Shows progress: "processing" → "completed"

Step 4: Admin downloads file
GET /api/users/export/:jobId/download
✅ Returns CSV file with 1,247 users

Edge Cases:
✅ Large exports (>10k users) → Streamed response
✅ Invalid filters → Clear error messages
✅ Expired job ID → 404 with helpful message

Quality:
✅ Performance: 10k users exported in <30 seconds
✅ Security: Role-based access control enforced
✅ Privacy: PII redacted in logs
```

---

### Template C: Performance Improvement

```
Demo Script Example:

"Today we optimized the dashboard loading performance."

[Show dashboard in staging]

Before Optimization:
├─ Load time: 4.2 seconds
├─ Database queries: 247 (N+1 problem)
└─ User feedback: "Too slow"

After Optimization:
├─ Load time: 0.8 seconds (81% improvement)
├─ Database queries: 12 (optimized with joins)
└─ Perceived performance: Much faster

What We Did:
✅ Added database index on user_id
✅ Implemented query result caching (Redis)
✅ Lazy-loaded non-critical widgets
✅ Optimized API response payloads

[Live demonstration of fast loading]

Metrics:
✅ 95th percentile: 1.2 seconds (was 5.1s)
✅ Server response time: 145ms (was 890ms)
✅ Cache hit rate: 78%
✅ No increase in server load
```

---

### Template D: Bug Fix

```
Demo Script Example:

"Today we fixed the payment confirmation email bug."

The Issue:
├─ Users not receiving confirmation emails after payment
├─ Affected ~3% of transactions (87 users last week)
└─ Root cause: Race condition in async processing

The Fix:
✅ Implemented message queue for reliable delivery
✅ Added retry logic with exponential backoff
✅ Improved error logging for debugging

Demonstration:
[Live: Complete a test payment]

Step 1: User completes checkout
Step 2: Payment processed successfully
Step 3: Email sent within 5 seconds ✅
Step 4: Email delivery confirmed in logs

Verification:
✅ Tested 50 transactions - 100% email delivery
✅ No duplicate emails
✅ Average delivery time: 2.3 seconds
✅ Monitoring added to alert on failures

Prevent Recurrence:
✅ Added integration test for email flow
✅ Monitoring dashboard for email delivery rate
✅ Alerting if delivery rate drops below 99%
```

---

## Post-Demo Actions

**Immediately After Demo**:

```
✅ ACCEPTED:
- [ ] Deploy to production (feature flag OFF)
- [ ] Document deployment time and version
- [ ] Set up monitoring for new feature
- [ ] Plan feature flag rollout schedule
- [ ] Update stakeholders on rollout plan

⚠️ ACCEPTED WITH CAVEATS:
- [ ] All actions from "Accepted" above
- [ ] Create follow-up items in backlog
- [ ] Prioritize follow-ups with Product Owner
- [ ] Schedule follow-up demo if needed

❌ REJECTED:
- [ ] Do NOT deploy to production
- [ ] Document gaps identified
- [ ] Plan rework for tomorrow's cycle
- [ ] Schedule retrospective discussion
- [ ] Inform stakeholders of revised timeline
```

**AI Scribe Actions**:
- [ ] Generate demo summary
- [ ] Document acceptance decision
- [ ] Create backlog items from feedback
- [ ] Update knowledge base
- [ ] Prepare metrics for retrospective

---

## Tips for Great Demos

### DO:
✅ Rehearse before the actual demo (15 min practice)
✅ Use production-like data (anonymized if needed)
✅ Show the feature from user's perspective
✅ Highlight AI contributions proudly
✅ Be transparent about limitations
✅ Invite questions and feedback
✅ Celebrate the team's work

### DON'T:
❌ Demo from localhost (use staging)
❌ Gloss over bugs or issues
❌ Get defensive about feedback
❌ Promise features not in today's scope
❌ Use technical jargon unnecessarily
❌ Skip edge cases
❌ Run long (>30 min)

---

## Demo Metrics to Track

```
Demo Effectiveness:
- Stakeholder attendance rate
- Acceptance rate (✅ / ⚠️ / ❌ ratio)
- Feedback items captured per demo
- Time from demo to production deployment
- Stakeholder satisfaction (survey)

Quality Indicators:
- Features accepted on first demo
- Features requiring rework
- Follow-up items generated
- Production defects after deployment
```

---

## Example: Complete Demo Session

```
Daily Demo - November 5, 2025, 5:00 PM

Attendees:
✅ Product Owner (Jessica)
✅ Lead Developer (Sarah)
✅ Frontend Developer (Marcus)
✅ UX Designer (Tom)
✅ Customer Success Rep (Maria)
✅ AI Orchestrator (Alex)

Part 1: Outcome Recap (3 min)
Jessica: "This morning we committed to implement profile picture
cropping with support for square, 16:9, and 4:3 aspect ratios."

Part 2: Live Demo (15 min)
Marcus: [Shares screen - staging.example.com]
"Let me show you the new crop feature..."
[Demonstrates full flow]
[Shows edge cases]
Quality metrics: 94% test coverage, <300ms processing time

Part 3: Q&A (10 min)
Tom: "Can users rotate images too?"
Sarah: "Not in this iteration, but great idea for backlog."

Maria: "Will this work on the mobile app?"
Marcus: "Yes, fully responsive. Let me show..."
[Demos on mobile emulator]

Part 4: Acceptance (2 min)
Jessica: "✅ ACCEPTED. This meets all our criteria. Great work!
Let's deploy to production with the feature flag off, and plan
gradual rollout starting tomorrow."

Next Steps:
- Deploy to production tonight
- Start rollout at 10% tomorrow morning
- Monitor crop success rate and processing time
- Full rollout by end of week if metrics good
```

---

**Remember**: Demos are celebrations of daily value delivery. Make them engaging, transparent, and collaborative!
