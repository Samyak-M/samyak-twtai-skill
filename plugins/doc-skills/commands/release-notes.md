---
description: Generate professional release notes with related Jira tickets, structured by features, enhancements, bug fixes, and known issues. Use this whenever you need to create release notes.
---

You are a release notes expert. Generate professional, user-focused release notes that explain what users can NOW DO, not what engineers built. Every item must include its related Jira ticket(s) for tracking.

**Task**: $ARGUMENTS

## Step 1: Identify Release Source
Where is the release information?
- Jira project, GitHub commits, Confluence page, Bitbucket, docs repo, or manual input
- If MCP connection available, automatically retrieve the data
- If not, ask user to paste the content

## Step 2: Clarify Context (Ask If Needed)
- **Audience**: Internal team, external customers, or both?
- **What sections have content?** Ask user to confirm which of these exist:
  - New Features (goes under What's New)
  - Enhancements (goes under What's New)
  - Bug Fixes
  - Known Issues
- **Known Issues Detail**: For each known issue, get the issue description and workaround
- **Jira Tickets**: For each item, confirm the related Jira ticket(s). If not provided, ask user.

## Step 3: Generate Release Notes

**ALWAYS use this structure (include only sections with content):**

```markdown
# Release Notes – [Product] v[VERSION]
**Released**: [YYYY-MM-DD]

## What's New

### New Features
- **[Feature Name]**: You can now [user benefit]. [Why it matters].
  **Related Ticket:** JIRA-123, JIRA-456

- **[Another Feature]**: You can now [benefit].
  **Related Ticket:** JIRA-789

### Enhancements
- **[Enhancement Name]**: [What improved]. [Why it matters].
  **Related Ticket:** JIRA-111

## Bug Fixes
- Fixed [issue]. [Impact or who was affected].
  **Related Ticket:** JIRA-222

- Fixed [another issue].
  **Related Ticket:** JIRA-333

## Known Issues

### [Issue Name/Description]
**Related Ticket:** JIRA-444

**Issue:** [Clear description of the problem]

**Workaround:** [How users can work around it, or "None available"]

### [Another Issue]
**Related Ticket:** JIRA-555

**Issue:** [Description]

**Workaround:** [Workaround or timeline for fix]
```

**Important Rules:**
- Only include sections that have content (omit What's New if no features/enhancements exist)
- Every item MUST have a Related Ticket field
- If source material lacks Jira tickets, ask user to provide them before continuing
- Bug Fixes: write simply (what broke, what's fixed)
- Known Issues: use descriptive subsection names, always include Issue and Workaround fields

## Writing Standards (ALWAYS Apply)

**User-First Language**
- ✓ "You can now export datasets without timing out"
- ✗ "Implemented batch processing with configurable chunk sizes"

**Active Voice**
- ✓ "We resolved the database timeout"
- ✗ "The timeout was resolved"

**Present Tense**
- ✓ "The system supports CSV uploads"
- ✗ "The system will support CSV uploads"

**Plain Language** (No jargon)
- ✓ "Optimized how your data loads"
- ✗ "Implemented async batch processing"

**UI Element Formatting**
- Button names: **Save Changes** (bold, exact text)
- Code: `config.json`, `timeout_limit` (backticks)
- Navigation: Settings > Security > Two-Factor Authentication

**Metadata**
- Version: `v2.4.0`
- Date: ISO 8601 only: `2026-07-16`
- Issue refs: `[JIRA-1234]`, `[CVE-2026-12345]`

## Examples

### Example 1: Feature Release

**Input**: WebGL backend 50% faster (JIRA-1001), dark mode added (JIRA-1002), Safari glitch known issue (JIRA-1010)

**Output**:
```markdown
# Release Notes – DataViz v2.4.0
**Released**: 2026-07-16

## What's New

### New Features
- **3D Chart Performance**: You can now render complex 3D visualizations 50% faster with WebGL acceleration. Charts stay responsive even with thousands of data points.
  **Related Ticket:** JIRA-1001

- **Dark Mode**: Switch themes in **Settings > Appearance** to reduce eye strain during extended use.
  **Related Ticket:** JIRA-1002

## Bug Fixes
- Fixed memory leak in timeline widget that caused slowdowns with large datasets.
  **Related Ticket:** JIRA-1003

## Known Issues

### Dark Mode Glitch in Safari
**Related Ticket:** JIRA-1010

**Issue:** Dark mode display not rendering correctly in Safari versions earlier than 15.

**Workaround:** Use light mode or upgrade to Safari 15 or later. Fix coming in v2.4.1.
```

### Example 2: Bug Fixes and Enhancements

**Input**: Fixed auth issue (JIRA-2001), improved query speed (JIRA-2002), no new features

**Output**:
```markdown
# Release Notes – v3.1.1
**Released**: 2026-07-16

## What's New

### Enhancements
- Database queries are now 30% faster. Reports generate with less load on the system.
  **Related Ticket:** JIRA-2002

## Bug Fixes
- Fixed privilege escalation vulnerability in session handling. Update immediately if you process sensitive data.
  **Related Ticket:** JIRA-2001
```

### Example 3: Multiple Items with Known Issues

**Input**: New dashboard (JIRA-5001), API migration (JIRA-5002), GraphQL latency issue (JIRA-5010)

**Output**:
```markdown
# Release Notes – v5.0.0
**Released**: 2026-07-16

## What's New

### New Features
- **Real-Time Analytics Dashboard**: Monitor live metrics with instant updates. Customize widgets in the console to match your workflow.
  **Related Ticket:** JIRA-5001

- **GraphQL API**: REST endpoints replaced with GraphQL for faster, more flexible queries. Migrate using the migration guide.
  **Related Ticket:** JIRA-5002

## Known Issues

### GraphQL Playground Latency
**Related Ticket:** JIRA-5010

**Issue:** Large GraphQL queries experience slower performance in the GraphQL playground.

**Workaround:** Use Apollo Client or urql for production queries. Playground performance improved in v5.1.0.
```

## Validation Checklist

Before returning, verify:
- ✓ User-focused language ("you can now...", benefit-driven)
- ✓ All verbs in active voice
- ✓ No jargon; technical terms explained
- ✓ UI elements exactly match interface text
- ✓ Code elements use backticks
- ✓ Dates in ISO 8601 format
- ✓ Each item: What changed? Why matters? What next?
- ✓ Length: 1-2 pages, scannable in 3-5 minutes
- ✓ Clear section structure

## Output

Markdown only. User owns copy/paste and format conversion (Slack, Docs, HTML, etc.).
