# Work Item Template

**Use this template to define daily work items / micro-epics for AAFM**

---

## Work Item Header

```
ID: [WI-YYYY-NNN]
Title: [Concise, user-facing description]
Type: [Feature / Bug / Performance / Technical / Refactoring]
Status: [Backlog / Ready / In Progress / Demo / Done]
Priority: [Critical / High / Medium / Low]
Created: [Date]
Owner: [Product Owner name]
```

---

## Business Value

**Value Statement**:
```
As a [user type],
I want [capability],
So that [business benefit].
```

**Impact**:
- **Business Metric**: [What will improve and by how much?]
- **User Benefit**: [How does this help users?]
- **Strategic Alignment**: [How does this support company goals?]

**Size Estimate**:
```
Effort: [Can this be done in 8 hours with AI assistance? YES / NO]

If NO:
  - This item needs to be broken down into smaller micro-epics
  - Each micro-epic should be completable in one day
```

---

## Success Criteria (Definition of Done)

```
✅ [Specific, measurable, testable criterion 1]
✅ [Specific, measurable, testable criterion 2]
✅ [Specific, measurable, testable criterion 3]
✅ [Specific, measurable, testable criterion 4]
✅ [Specific, measurable, testable criterion 5]

Non-Functional Requirements:
✅ Test coverage ≥90%
✅ No security vulnerabilities (critical/high)
✅ Performance meets targets: [specify]
✅ Accessibility: WCAG 2.1 AA compliant
✅ Documentation complete
✅ Deployed to production (with feature flag)
```

**Anti-Pattern Examples**:
- ❌ "Code is written" (too vague)
- ❌ "Feature works" (not measurable)
- ❌ "Improve performance" (no target)
- ✅ "API response time <200ms for 95th percentile" (specific, measurable)

---

## Technical Specification

### User Flow

```
1. User [action]
   → System [response]
   → User sees [outcome]

2. User [action]
   → System [response]
   → User sees [outcome]

[Continue for main flow...]

Edge Cases:
⚠️ Edge case 1: [Description] → [Expected behavior]
⚠️ Edge case 2: [Description] → [Expected behavior]
⚠️ Edge case 3: [Description] → [Expected behavior]
```

---

### Technical Design

**Components Affected**:
```
□ Frontend: [Specific components]
□ Backend: [Specific services/APIs]
□ Database: [Schema changes if any]
□ Infrastructure: [New resources needed]
□ Third-party integrations: [External APIs]
```

**API Changes** (if applicable):
```
Endpoint: [Method] /api/path
Request:
{
  "param1": "type",
  "param2": "type"
}

Response:
{
  "result": "type",
  "data": {}
}

Authentication: [Required / Not required]
Rate limiting: [Limits]
```

**Database Changes** (if applicable):
```sql
-- Migration: [Description]

-- Example
ALTER TABLE users ADD COLUMN profile_picture_url VARCHAR(255);
CREATE INDEX idx_users_profile_picture ON users(profile_picture_url);
```

**Dependencies**:
```
Internal Dependencies:
□ [Service/component] - Status: [Ready / In Progress / Blocked]
□ [Service/component] - Status: [Ready / In Progress / Blocked]

External Dependencies:
□ [Third-party API] - Status: [Available / Needs setup]
□ [Infrastructure] - Status: [Available / Needs provisioning]
```

---

### AI Agent Assignment Recommendations

```
🤖 Requirement Analyst Agent (___% capacity)
Recommended tasks:
- Analyze edge cases
- Generate acceptance criteria details
- Create test scenarios

🤖 Code Generation Agent (___% capacity)
Recommended tasks:
- Implement [component name]
- Generate boilerplate code
- Apply design patterns

🤖 Test Engineer Agent (___% capacity)
Recommended tasks:
- Generate unit tests
- Create integration tests
- Develop E2E test scenarios

🤖 DevOps Agent (___% capacity)
Recommended tasks:
- Infrastructure updates
- CI/CD pipeline adjustments
- Deployment automation

🤖 QA Validation Agent (___% capacity)
Recommended tasks:
- Security scanning
- Performance testing
- Accessibility validation

🤖 Scribe Agent (___% capacity)
Recommended tasks:
- Documentation generation
- API docs updates
- ADR creation
```

---

## Testing Strategy

### Test Coverage Requirements

**Unit Tests**:
```
□ [Function/method] - [Test scenario]
□ [Function/method] - [Test scenario]
□ [Function/method] - [Test scenario]

Target: 90%+ coverage
```

**Integration Tests**:
```
□ [Service integration] - [Test scenario]
□ [API endpoint] - [Test scenario]
□ [Database operation] - [Test scenario]

Target: All critical paths covered
```

**E2E Tests**:
```
□ [User journey] - Happy path
□ [User journey] - Error handling
□ [User journey] - Edge cases

Target: Critical user flows covered
```

**Performance Tests**:
```
Load test scenarios:
- Concurrent users: [number]
- Requests per second: [number]
- Target response time: [<Xms]
- Target error rate: [<X%]
```

---

## Security Considerations

```
Security Checklist:
□ Input validation implemented
□ Output encoding applied
□ Authentication/authorization checked
□ SQL injection prevention (parameterized queries)
□ XSS prevention
□ CSRF protection (if applicable)
□ Sensitive data encrypted
□ API rate limiting configured
□ Security headers configured
□ OWASP Top 10 reviewed

Data Privacy:
□ PII handling compliant with regulations
□ Data retention policy followed
□ User consent obtained (if applicable)
□ Audit logging in place
```

---

## Deployment Strategy

### Feature Flag

```
Flag Name: [feature.name.description]
Default State: OFF
Rollout Plan:
  Day 1: Deploy to production (0% users, flag OFF)
  Day 2: Internal users only (5%)
  Day 3: Gradual rollout (10% → 25%)
  Day 4: Expanded rollout (50% → 75%)
  Day 5: Full rollout (100%) or rollback based on metrics

Rollback Criteria:
⚠️ Error rate >1%
⚠️ Performance degradation >50%
⚠️ Critical bug discovered
```

### Monitoring

```
Metrics to Monitor:
📊 [Metric 1] - Target: [value]
📊 [Metric 2] - Target: [value]
📊 [Metric 3] - Target: [value]

Alerts:
🚨 [Critical alert condition]
⚠️ [Warning alert condition]

Dashboard: [Link to monitoring dashboard]
```

---

## Acceptance Criteria Validation

**Before marking as "Ready for Dev"**:
- [ ] Business value clearly articulated
- [ ] Success criteria are specific and measurable
- [ ] Can be completed in < 8 hours with AI assistance
- [ ] No blocking dependencies
- [ ] Technical design reviewed by architect
- [ ] Security considerations addressed
- [ ] Testing strategy defined
- [ ] Feature flag configured
- [ ] Monitoring plan in place

---

## Example: Filled Work Item

```
ID: WI-2025-142
Title: Implement user profile picture cropping
Type: Feature
Status: Ready
Priority: High
Created: 2025-11-05
Owner: Jessica (Product Owner)

BUSINESS VALUE
As a user,
I want to crop my profile picture before uploading,
So that I can control how my image appears on the platform.

Impact:
- User satisfaction: 78% of users requested this feature
- Engagement: Expected +15% profile completion rate
- Competitive: Matches competitor features

Effort: YES (8 hours with AI assistance)

SUCCESS CRITERIA
✅ Users can select crop area with draggable UI
✅ Aspect ratios supported: square, 16:9, 4:3
✅ Cropping happens server-side
✅ Works on mobile and desktop browsers
✅ Processing time <300ms for images up to 10MB

✅ Test coverage ≥90%
✅ No security vulnerabilities
✅ Performance: <300ms processing
✅ Accessibility: WCAG 2.1 AA
✅ Feature flag: user.profile.crop

TECHNICAL SPECIFICATION

User Flow:
1. User clicks "Upload Photo"
   → File picker opens
   → User selects image

2. Crop interface displays
   → User sees image with crop overlay
   → User drags to select area
   → User chooses aspect ratio

3. User clicks "Save"
   → Server crops image
   → Profile updates
   → Success message shown

Components Affected:
□ Frontend: ProfilePictureUpload.tsx, CropInterface.tsx
□ Backend: /api/users/:id/profile-picture (update endpoint)
□ Database: No schema changes
□ Infrastructure: Image processing library (Sharp)

AI Agent Assignments:
🤖 Requirement Analyst (15%)
   - Edge case analysis
   - Acceptance criteria refinement

🤖 Code Generation (65%)
   - Crop UI component
   - Server-side crop logic
   - API endpoint updates

🤖 Test Engineer (55%)
   - Unit tests for crop calculations
   - E2E tests for crop flow
   - Performance tests

🤖 DevOps (10%)
   - Monitor processing time

🤖 QA Validation (30%)
   - Security review
   - Cross-browser testing

TESTING STRATEGY
Unit Tests:
□ Crop calculation logic
□ Aspect ratio validation
□ Image dimension handling

Integration Tests:
□ API endpoint with crop parameters
□ Image processing pipeline

E2E Tests:
□ Full crop and upload flow
□ Mobile responsiveness

SECURITY
□ Validate crop parameters (prevent manipulation)
□ Scan processed images for malware
□ Rate limit upload endpoint

DEPLOYMENT
Flag: user.profile.crop
Rollout: Day 1 (0%), Day 2 (10%), Day 3 (50%), Day 4 (100%)

Metrics:
📊 Crop success rate - Target: >95%
📊 Processing time - Target: <300ms
📊 User adoption - Target: 30% within 1 week
```

---

**Remember**: Well-defined work items are the foundation of successful daily delivery. Take time to define them properly before starting development.
