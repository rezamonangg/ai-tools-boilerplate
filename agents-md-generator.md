# Prompt: Generate AGENTS.md Using Vector DB + Code Search

## Context
This codebase is indexed in Qdrant vector database using Nomic embeddings for semantic search.

## Generation Strategy

**Use Vector DB (Qdrant) to understand and discover:**
- Business domain and use cases
- Architecture patterns and design decisions  
- Common workflows and conventions
- Critical business rules from code

**Use Serena MCP to verify and locate:**
- Exact file paths and structure
- Specific class/method names for examples
- Code organization details

---

## SECTION 1: OVERVIEW (Use Vector DB + Serena)

**Step 1: Use Vector DB to understand the project**

Query Qdrant with these semantic searches (limit 10 results each):
```
1. "What is the main purpose of this system?"
2. "What business problem does this solve?"
3. "What type of application is this?"
4. "What technologies and frameworks are used?"
5. "What domain or industry is this for?"
```

**Step 2: Use Serena to verify structure**

Use Serena MCP to:
- Confirm actual tech stack (check build files, dependencies)
- Verify project type (find main entry points)

**Generate:**

**Project Name:** [Actual project name from repository]

**Purpose:** [One sentence from vector DB results]

**Type:** [e.g., Microservice, REST API, Web App, CLI Tool - from vector DB + Serena verification]

**Tech Stack:** [List key technologies found via vector DB, verified with Serena checking build files]

**Domain:** [Business domain identified from vector DB]

---

## SECTION 2: BUSINESS USE CASES & CRITICAL BUSINESS RULES (Use Vector DB)

**Step 1: Discover use cases**

Query Qdrant:
```
1. "What are the main business use cases?"
2. "What problems do users solve with this system?"
3. "What are the key workflows?"
4. "What business operations are supported?"
```

Limit: 10 results per query

**Step 2: Identify critical business rules**

Query Qdrant:
```
1. "What are critical business rules and validations?"
2. "What compliance or regulatory requirements exist?"
3. "What must never be violated in the business logic?"
4. "What are the most important constraints?"
5. "What security or privacy rules are enforced?"
```

Limit: 10 results per query

**Generate:**

### Core Business Use Cases

List 5-7 main use cases discovered from vector search:
- Use case name and description
- Why it's important
- Key requirements

### CRITICAL BUSINESS RULES

> These rules MUST NEVER be violated.

List 5-10 critical rules found in code:

For each rule:
1. **Rule name and description**
2. **Why it exists** (found from comments/documentation)
3. **Where enforced** (use Serena to verify exact locations)
4. **Violation impact** (from vector search understanding)

---

## SECTION 3: STRUCTURE (Use Serena + Vector DB)

**Step 1: Get actual directory structure**

Use Serena MCP to:
- List main directories
- Show actual file organization
- Identify where different code types live

**Step 2: Understand organization patterns**

Query Qdrant:
```
"How is the code organized and why?"
"What are the layers and their purposes?"
"What naming conventions are used?"
```

Limit: 5 results

**Generate:**

### Directory Organization

Provide actual directory tree from Serena:
```
[actual directory structure from codebase]
```

Explain organization based on vector DB insights.

### Naming Conventions

Document actual conventions found:
- **Packages/Modules:** [from Serena scan]
- **Files:** [from Serena scan]
- **Classes/Types:** [from vector DB patterns]
- **Functions/Methods:** [from vector DB patterns]
- **Variables:** [from vector DB patterns]
- **Constants:** [from vector DB patterns]

---

## SECTION 4: ARCHITECTURE (Use Vector DB + Serena for Examples)

**Step 1: Understand architecture**

Query Qdrant:
```
1. "What architectural patterns are used?"
2. "How is the system structured?"
3. "What are the key design decisions?"
4. "How do components interact?"
5. "What integration patterns exist?"
```

Limit: 10 results per query

**Step 2: Find concrete examples**

Use Serena to locate specific files/classes mentioned in vector DB results.

**Generate:**

### Architecture Style

[Architectural pattern from vector DB - e.g., Layered, Event-Driven, etc.]

Explain why this architecture (from vector DB understanding).

### Key Architectural Patterns

Identify 2-4 patterns with examples:

For each pattern:
- **Pattern name** [from vector DB]
- **Where used** [verify with Serena MCP - actual file paths]
- **Why used** [from vector DB understanding]
- **Example location** [from Serena]

### Technology Choices

For major technologies:
- **What it is**
- **Why chosen** [from vector DB or git history]
- **How used** [from vector DB patterns]
- **Important constraints** [from vector DB]

---

## SECTION 5: HOW TO GET THINGS DONE (Generic + Repository Examples)

### 5.1 Finding Codes

**IMPORTANT: Tool Selection Strategy**

Document this clearly for daily usage:

```markdown
### Choose the Right Search Tool

| What You're Looking For | Tool to Use | Why |
|------------------------|-------------|-----|
| Exact string, method, class name | Serena MCP or grep | Precise, few results (3-10) |
| Code structure, references | Serena MCP | AST-aware, understands code |
| Semantic/conceptual questions | Vector DB (limit 5-10) | Finds related code by meaning |
| Configuration values | grep/ripgrep | Fast text search |

### When to Use Vector DB (Qdrant):

✅ **GOOD for learning and exploration:**
- "How do we handle authentication?"
- "Show examples of error handling patterns"
- "What are the common validation approaches?"
- "How does the approval workflow work?"
- "What integration patterns exist?"

**IMPORTANT: Always limit to 5-10 results**

❌ **BAD for exact searches (use Serena instead):**
- "Find class EmailService" → Use Serena
- "Find method sendEmail" → Use Serena
- "Find string 'email_tracker'" → Use grep
- "Find all calls to processPayment" → Use Serena

### Why This Matters:

**The 189k token problem:**
- Vector DB for exact search = 50 results = 189k tokens ❌
- Serena for exact search = 5 results = 10k tokens ✅

**Token Budget Guidelines:**

| Task Complexity | Target Tokens | Tool Choice |
|----------------|---------------|-------------|
| Simple (find + edit method) | 5-20k | Serena/grep only |
| Medium (understand pattern + implement) | 20-50k | Vector DB (limit 5) + Serena |
| Complex (learn system + refactor) | 50-100k | Vector DB (limit 10) + Serena |
```

### 5.2 Adding / Deleting / Editing Codes

[Copy generic content from previous universal prompt - Sections on EDITING, ADDING, DELETING]

**Enhancement: Add Vector DB use case**

```markdown
#### Using Vector DB to Understand Before Changing

**When adding similar functionality:**

Step 1: Find examples with Vector DB
Query: "How are [similar features] implemented?"
Limit: 5 results
Review: Understand the patterns

Step 2: Find exact locations with Serena
Use Serena to locate specific files mentioned in vector results

Step 3: Follow the pattern
Implement using discovered patterns
```

### 5.3 Common Tasks - How To

**Step 1: Discover common tasks**

Query Qdrant:
```
1. "What are common development tasks?"
2. "How to add new features?"
3. "How to integrate external services?"
4. "What do developers frequently modify?"
```

Limit: 10 results

**Step 2: Document with Serena verification**

For each task, provide:
- Step-by-step instructions (from vector DB)
- Actual file paths (from Serena)
- Code examples (from Serena)

**Generate 3-5 common tasks based on vector DB findings**

---

## SECTION 6: MCP TOOLS

### 6.1 Serena MCP

[Copy generic Serena content from previous prompt]

**Add this critical section:**

```markdown
### Serena vs Vector DB

**Use Serena when you know what you're looking for:**
- Exact class/method/variable names
- All references to a specific element
- Code structure and inheritance
- Finding definitions

**Use Vector DB when you're exploring:**
- Understanding concepts
- Finding similar patterns
- Learning how something works
- Discovering related code
```

### 6.2 Sequential Thinking MCP

[Copy generic Sequential Thinking content]

### 6.3 Git MCP

[Copy generic Git content]

### 6.4 Vector Database (Qdrant with Nomic Embeddings)

**NEW SECTION - Add this:**

```markdown
### 6.4 Vector Database (Qdrant)

**Purpose:** Semantic code search for understanding concepts, patterns, and relationships.

**When to Use:**
- Learning how the system works
- Finding examples of patterns
- Understanding design decisions
- Exploring related functionality
- Discovering what's possible

**When NOT to Use:**
- Finding exact class/method names (use Serena)
- Locating specific strings (use grep)
- Getting all references (use Serena)
- Finding file paths (use Serena)

**Usage Examples:**

✅ **GOOD USES (Semantic Understanding):**

"How does this system handle authentication?"
→ Limit: 5-10 results
→ Returns: Related authentication code patterns

"Show me examples of error handling"
→ Limit: 5 results
→ Returns: Various error handling approaches

"What are common validation patterns?"
→ Limit: 5 results
→ Returns: Different validation implementations

"How does the bulk email workflow work?"
→ Limit: 10 results
→ Returns: Related workflow components

❌ **BAD USES (Exact Search - causes token bloat):**

"Find EmailService class"
→ Returns: 50+ results with "Email" or "Service" ❌
→ Use Serena instead: exact match ✅

"Find email_tracker database operations"
→ Returns: 50+ results mentioning email or tracking ❌
→ Use Serena/grep instead: 5 exact matches ✅

**Critical Rules:**

1. **Always limit results to 5-10 maximum**
   - More results = more tokens
   - Quality over quantity

2. **Never use for exact searches**
   - Exact names → Serena
   - Exact strings → grep
   - This prevents the 189k token problem

3. **Use for learning, not locating**
   - Learning: "How does X work?" → Vector DB ✅
   - Locating: "Where is X defined?" → Serena ✅

4. **Refine if results are poor**
   - Too broad: "code" → Too specific: "error handling in payment service"
   - Adjust query to be more specific

**Best Practices:**

- Start broad, then narrow with Serena
- Use Vector DB for discovery phase
- Switch to Serena for implementation phase
- Combine both: Vector DB (understand) → Serena (locate)

**Example Workflow:**

```
Task: Add rate limiting to email sending

Step 1 - Understand (Vector DB):
Query: "How is rate limiting implemented?"
Limit: 5 results
Result: Understand existing patterns

Step 2 - Locate (Serena):
"Use Serena to find RateLimiter class"
Result: Exact file location

Step 3 - Implement:
Follow discovered pattern in exact location

Token usage: 15k (Vector DB: 10k, Serena: 5k) ✅
vs 189k if used Vector DB for exact search ❌
```
```

---

## SECTION 7: DO's (Fully Generic)

### Code Quality

**Follow Language/Framework Best Practices**
- Use idiomatic patterns for the language
- Follow framework conventions and lifecycle
- Use appropriate data structures and algorithms
- Write clean, readable code
- Follow SOLID principles where applicable

**Use Structured Logging**
- Include relevant context (IDs, operation names, user info)
- Use appropriate log levels (DEBUG, INFO, WARN, ERROR)
- Log significant events and state changes
- Make logs searchable and actionable
- Include timestamps and trace IDs

**Handle Errors Gracefully**
- Catch and handle exceptions appropriately
- Log errors with full context and stack traces
- Return user-friendly error messages
- Never expose internal errors or stack traces to end users
- Use error codes for categorization
- Implement retry logic for transient failures

**Protect Sensitive Data**
- Never log passwords, tokens, or API keys
- Mask PII (emails, phone numbers, addresses, credit cards)
- Encrypt sensitive data at rest and in transit
- Be cautious with business-sensitive data
- Follow data protection regulations (GDPR, CCPA, etc.)
- Use secure credential storage (vaults, environment variables)

**Pass Context Through Operations**
- Include request/trace IDs in all operations
- Preserve context through async operations
- Enable distributed tracing for debugging
- Make operations traceable end-to-end
- Propagate security context (user, permissions)

**Write Comprehensive Tests**
- Write unit tests for business logic (aim for 70%+ coverage)
- Write integration tests for critical paths
- Write end-to-end tests for key workflows
- Mock external dependencies appropriately
- Test edge cases and error scenarios
- Use test utilities suited to the framework
- Keep tests fast and deterministic

**Follow Existing Patterns**
- Match existing code style and formatting
- Use established naming conventions
- Follow existing error handling patterns
- Replicate existing logging approaches
- Respect architectural boundaries
- Don't introduce new patterns without discussion

**Keep Code Modular**
- Separate concerns appropriately (SRP - Single Responsibility Principle)
- Keep functions/methods focused and single-purpose
- Use dependency injection for flexibility
- Make code testable and maintainable
- Avoid tight coupling between modules
- Design for extensibility

**Document When Necessary**
- Add comments for non-obvious code
- Document business rules and edge cases
- Keep documentation close to code
- Update docs when code changes
- Use self-documenting code (clear names) over comments
- Document API contracts and interfaces

**Version Control Best Practices**
- Write clear, descriptive commit messages
- Make atomic commits (one logical change per commit)
- Keep commits focused and small
- Reference tickets/issues in commits
- Don't commit commented-out code
- Don't commit credentials or secrets

**Performance Awareness**
- Consider algorithmic complexity (Big O)
- Avoid N+1 queries in database operations
- Use appropriate caching strategies
- Be mindful of memory usage
- Profile before optimizing
- Don't premature optimize

**Security Consciousness**
- Validate all inputs (never trust user input)
- Use parameterized queries (prevent SQL injection)
- Implement proper authentication and authorization
- Follow principle of least privilege
- Keep dependencies up to date
- Use security scanners and linters

**Use Vector DB Wisely**
- Limit results to 5-10 maximum
- Use for understanding, not locating
- Switch to Serena for exact searches
- Be specific in semantic queries
- Refine queries if results are too broad

---

## SECTION 8: DON'Ts (Fully Generic)

### Critical Mistakes to Avoid

**Don't Mix Business Logic with Presentation/Framework Code**
- Keep business logic separate from HTTP/UI concerns
- Don't put validation in presentation layer only
- Business rules should be framework-agnostic
- Keep core logic testable without framework
- Don't leak domain concepts into infrastructure layer

**Don't Hardcode Configuration**
- Use configuration files or environment variables
- Don't embed credentials in code
- Make configuration environment-specific (dev/staging/prod)
- Use configuration management tools
- Don't hardcode URLs, ports, or timeouts
- Use feature flags for conditional behavior

**Don't Log Sensitive Information**
- Never log passwords or authentication tokens
- Don't log full credit card numbers or PII
- Don't log API keys or secrets
- Don't log sensitive business data
- Use masking utilities when necessary
- Be extra careful in production environments

**Don't Make Changes Without Understanding Impact**
- Always find all references before deleting code
- Understand dependencies before modifying
- Don't assume tests cover all cases
- Search for configuration dependencies
- Check database migrations and schema changes
- Review API contracts before changing interfaces

**Don't Mix Concerns in Changes**
- Don't refactor while fixing bugs
- Don't add features while deleting code
- Keep changes focused on single purpose
- Make one logical change per commit
- Don't fix unrelated issues in the same PR
- Separate formatting changes from logic changes

**Don't Make Assumptions**
- Don't assume build tools or processes
- Don't assume deployment methods
- Don't assume environment setup
- Ask about environment if unsure
- Don't add dependencies without confirmation
- Don't assume data exists or is in expected format

**Don't Skip Impact Analysis**
- Always check what calls modified code
- Verify tests still pass
- Check for configuration dependencies
- Consider downstream effects
- Think about backwards compatibility
- Consider rollback scenarios

**Don't Ignore Existing Conventions**
- Match existing file naming
- Follow established directory structure
- Use consistent formatting
- Replicate existing patterns
- Don't introduce personal style preferences
- Respect team decisions even if you disagree

**Don't Block Critical Operations**
- Be aware of performance implications
- Don't introduce blocking operations in async code
- Don't hold locks longer than necessary
- Consider scalability impact
- Test with realistic load
- Be mindful of thread pool exhaustion

**Don't Skip Security Considerations**
- Validate all inputs (sanitize and validate)
- Follow principle of least privilege
- Don't trust user input
- Consider security in design, not as afterthought
- Don't roll your own crypto
- Use established security libraries

**Don't Ignore Errors Silently**
- Don't catch exceptions and do nothing
- Don't return null instead of throwing exceptions
- Don't swallow errors without logging
- Handle or propagate, never ignore
- Log context when catching exceptions

**Don't Create God Objects/Classes**
- Keep classes focused and cohesive
- Don't let classes grow beyond 500 lines
- Don't let methods grow beyond 50 lines
- Split responsibilities when things get complex
- Follow Single Responsibility Principle

**Don't Copy-Paste Code**
- Don't duplicate logic across files
- Extract common functionality into utilities
- Create abstractions for repeated patterns
- DRY (Don't Repeat Yourself) principle
- If you copy-paste, you probably need a function

**Don't Commit Broken Code**
- Always compile/build before committing
- Run tests before pushing
- Don't commit with failing tests
- Don't commit with merge conflicts
- Use pre-commit hooks to catch issues

**Don't Misuse Vector Database**
- Don't use for exact name searches (causes 50+ results)
- Don't exceed 10 result limit (token bloat)
- Don't use when Serena is more appropriate
- Don't use for finding specific files/lines
- Remember: Vector DB for understanding, Serena for locating

**Don't Over-Engineer**
- Don't add abstraction layers prematurely
- Don't optimize before measuring
- Don't use design patterns unnecessarily
- YAGNI (You Aren't Gonna Need It)
- Start simple, refactor when needed

**Don't Ignore Technical Debt**
- Don't let "temporary" hacks become permanent
- Document known issues and TODOs
- Schedule time to pay down debt
- Don't let debt accumulate unchecked
- Refactor when you touch old code

**Don't Deploy Without Testing**
- Don't skip staging environments
- Don't deploy on Friday afternoons
- Don't deploy without rollback plan
- Test in production-like environment first
- Have monitoring and alerts ready

---

## TOKEN EFFICIENCY QUICK REFERENCE

**Tool Selection Decision Tree:**

```
Do you know the exact name/string?
├─ YES → Use Serena MCP or grep (5-20k tokens)
└─ NO → Need to understand/explore?
    ├─ YES → Use Vector DB, limit 5-10 (10-20k tokens)
    └─ NO → Ask clarifying question first

Are you getting too many results?
├─ Vector DB returning 50+ → Switch to Serena ✅
└─ Serena returning 50+ → Refine scope/query
```

**Common Mistakes:**

| Mistake | Token Cost | Fix |
|---------|-----------|-----|
| Vector DB for "find EmailService" | 189k ❌ | Serena: 5k ✅ |
| Loading entire files | 100k ❌ | Load methods only: 10k ✅ |
| No result limits on Vector DB | 200k ❌ | Limit to 5-10: 15k ✅ |
| Searching whole codebase | 150k ❌ | Scope to directory: 20k ✅ |

---

## GENERATION INSTRUCTIONS

**Execution Strategy:**

1. **For Sections 1-3:** Use Vector DB for semantic understanding, Serena for verification
2. **For Section 4:** Use Vector DB for patterns, Serena for examples
3. **For Section 5.3:** Use Vector DB to discover tasks, Serena to verify steps
4. **For Sections 5.1-5.2, 6-8:** Use the generic templates provided

**Quality Checks:**

- Are file paths actual and verified with Serena?
- Are business rules discovered from code, not assumed?
- Is the Vector DB vs Serena distinction clear?
- Are token efficiency guidelines prominent?

**Output Format:**

- Complete AGENTS.md ready to commit
- Clear markdown formatting
- All sections included
- Specific to this repository (sections 1-4)
- Generic best practices (sections 5-8)
