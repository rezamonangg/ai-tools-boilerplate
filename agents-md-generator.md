# Prompt: Generate AGENTS.md for This Repository

Analyze this codebase and generate a complete AGENTS.md file following this structure:

---

## SECTION 1: OVERVIEW (Repository-Specific)

Analyze the repository and provide:

**Project Name:** [Actual project name]

**Purpose:** [One sentence: what business problem does this solve?]

**Type:** [e.g., Microservice, REST API, Web App, CLI Tool, Library, Mobile App]

**Tech Stack:** [List key technologies: language version, frameworks, databases, message queues, cloud services]

**Domain:** [Business domain: e.g., E-commerce, Finance, Healthcare, Messaging, etc.]

---

## SECTION 2: BUSINESS USE CASES & CRITICAL BUSINESS RULES (Repository-Specific)

### Core Business Use Cases

Identify and list the 5-7 main business use cases this system handles:
- What problems does it solve?
- Who are the users?
- What are the key workflows?

For each use case:
- Name and brief description
- Why it's important
- Key requirements or constraints

### CRITICAL BUSINESS RULES

> These rules MUST NEVER be violated. Verify before making any changes.

Identify 5-10 critical business rules that must always be enforced:

For each rule, provide:
1. **Rule name and description**
2. **Why it exists** (business or legal reason)
3. **Where it's enforced** (which layer/component)
4. **Violation impact** (what breaks if violated)

Examples of critical rules:
- Data validation requirements (PII protection, compliance)
- Business workflow constraints (approval processes, authorization)
- Rate limiting or quota enforcement
- Financial transaction rules
- Legal/regulatory compliance (GDPR, PCI-DSS, etc.)

---

## SECTION 3: STRUCTURE (Repository-Specific)

### Directory Organization

Provide the actual directory tree showing:
- Main source code directories
- Where different types of code live (API, business logic, data access, etc.)
- Configuration locations
- Test locations
- Any important subdirectories

Format:
```
[actual directory structure]
```

### Naming Conventions

Document the actual naming conventions used in this codebase:
- **Packages/Modules:** [convention]
- **Files:** [convention]
- **Classes/Types:** [convention]
- **Interfaces:** [convention]
- **Functions/Methods:** [convention]
- **Variables:** [convention]
- **Constants:** [convention]
- **Test files:** [convention]

Note any language-specific or framework-specific patterns.

---

## SECTION 4: ARCHITECTURE (Generic with Repository Examples)

Use this generic template, but include repository-specific examples:

### Architecture Style

Identify the architectural pattern(s) used:
- [e.g., Layered, Hexagonal, Event-Driven, Microservices, MVC, Clean Architecture]
- Explain why this architecture was chosen for this project
- Note if multiple patterns are combined

### Key Architectural Patterns

Identify 2-4 important patterns used in this codebase:

For each pattern:
- **Pattern name**
- **Where it's used** (with actual file/directory examples from this repo)
- **Why it's used** (benefit it provides)
- **Example location** (specific file path)

### Technology Choices

For each major technology, explain:
- **What it is**
- **Why it was chosen** (what problem it solves)
- **How it's used in this project**
- Any important gotchas or constraints

---

## SECTION 5: HOW TO GET THINGS DONE (Fully Generic - Copy As-Is)

### 5.1 Finding Codes

#### Token Budget Guidelines

| Task Complexity | Target Token Budget | When Exceeded |
|----------------|---------------------|---------------|
| Simple (bug fix, deletion) | 5-20k tokens | Re-evaluate search approach |
| Medium (new feature, single component) | 20-50k tokens | Break into smaller tasks |
| Complex (multi-component refactoring) | 50-100k tokens | Use planning tools first |

#### Choose the Right Search Tool

| What You're Looking For | Tool to Use | Why |
|------------------------|-------------|-----|
| Exact string, method, or class name | Serena MCP or grep | Precise, few results |
| Code structure, inheritance, references | Serena MCP | AST-aware, understands relationships |
| Semantic/conceptual ("how do we...") | Vector DB (limit 5-10) | Finds related code by meaning |
| Configuration values | grep/ripgrep | Fast text search |

#### Search Workflow

**Phase 1: Targeted Search (Don't Load Files Yet)**

```
For exact matches:
- Tool: Serena MCP or grep
- Query: Exact string, class name, or method name
- Scope: Specific directory when possible
- Output: File paths + line numbers only

For conceptual understanding:
- Tool: Vector DB with limit=5-10
- Query: Conceptual question
- Output: Relevant code sections
```

**Phase 2: Review Results**
- Check number of results (should be <20 for exact searches)
- Verify relevance before loading full content
- If too many results, narrow scope or refine query

**Phase 3: Load Minimal Context**

```
✅ DO:
- Load only specific methods or functions (10-30 lines)
- Show snippets with immediate context
- Ask for confirmation before loading more

❌ DON'T:
- Load entire files when you need one method
- Load test files unless debugging tests
- Use vector DB for exact string searches
```

---

### 5.2 Adding / Deleting / Editing Codes

#### General Principles

**Before Any Change:**
1. Understand the current implementation
2. Find similar existing code to follow patterns
3. Identify all affected areas (callers, tests, configs)
4. Plan the change before executing
5. Make minimal, focused changes

**Token Efficiency:**
- Show proposed changes before implementing
- Make surgical edits, not full file rewrites
- Load only what's necessary

---

#### EDITING Existing Code

**Step 1: Locate and Understand**
1. Search for exact location using Serena MCP or grep
2. Load ONLY the specific method/component (not entire file)
3. Understand current behavior and why it exists
4. Check for related tests

**Step 2: Plan the Edit**

Before modifying, answer:
- What exactly needs to change?
- Why is this change needed?
- What's the impact on callers?
- What tests need updating?
- Does this affect any business rules?

**Step 3: Show Proposed Changes**

Don't immediately rewrite. Instead:
1. Describe the change in plain English
2. Show before/after comparison or diff
3. Explain impact on behavior
4. Highlight any risks
5. Ask for confirmation

**Step 4: Execute Changes**

```
✅ Best practices:
- Modify only the specific lines needed
- Preserve existing code style and formatting
- Keep consistent with surrounding code
- Update related tests
- Add/update comments if logic is complex

❌ Avoid:
- Rewriting entire files unnecessarily
- Changing unrelated code
- Mixing refactoring with bug fixes
- Introducing new patterns inconsistently
```

---

#### ADDING New Code

**Step 1: Understand Context**

Before writing new code:
1. Find similar existing implementations
2. Review 1-2 examples of similar code
3. Identify patterns and conventions to follow
4. Note required dependencies and imports

**Step 2: Plan the Addition**

Answer these questions:
1. Where does this code belong? (which directory/file)
2. What naming convention applies?
3. What interfaces/base classes to extend?
4. What dependencies are needed?
5. What configurations are required?
6. What tests are needed?
7. Does this follow existing patterns?

**Step 3: Generate Code Incrementally**

```
For complex additions:
1. Define interface/contract first → Get confirmation
2. Implement core logic → Get confirmation
3. Add error handling and logging → Get confirmation
4. Write tests → Done

For simple additions:
- Generate complete code with explanatory comments
- Follow existing patterns exactly
- Include necessary imports and dependencies
```

**Step 4: Integration Check**

After adding code, verify:
- Follows project naming conventions
- Matches existing code style
- Has appropriate error handling
- Includes necessary logging
- Has corresponding tests
- Updates configuration if needed

---

#### DELETING Code

**Step 1: Find All References (CRITICAL)**

Never delete code without understanding its usage.

Use Serena MCP to find:
1. Where is it called? (direct usages)
2. Where is it extended/implemented? (inheritance)
3. Where is it imported? (dependencies)
4. What tests reference it?
5. What configs reference it?

**Step 2: Impact Analysis**

For each reference found, determine:
1. Will it break if we delete? (compilation error)
2. Will it cause runtime errors? (missing dependency)
3. Are there alternative implementations?
4. What tests will fail?
5. What configurations become obsolete?
6. Are there database migrations needed?

**Step 3: Plan Deletion Strategy**

```
Simple deletion (no external dependencies):
1. Remove the code
2. Remove related tests
3. Remove unused imports
4. Clean up configuration

Complex deletion (has dependencies):
1. List all files that need changes
2. Determine order of removal
3. Identify refactoring needed
4. Plan rollback strategy
```

**Step 4: Execute Deletion**

Recommended order:
1. Remove or update tests first
2. Remove or refactor code that depends on target
3. Remove the target code itself
4. Remove unused imports and configurations
5. Verify compilation and existing tests pass

**Step 5: Verification Checklist**

After deletion, confirm:
- [ ] Code compiles without errors
- [ ] No unused imports remain
- [ ] All tests pass (or are properly updated/removed)
- [ ] No orphaned configuration entries
- [ ] No TODO/FIXME comments referencing deleted code
- [ ] Documentation updated if needed

---

### 5.3 Common Tasks - How To

Identify 3-5 common development tasks for this repository and provide step-by-step instructions:

**Task 1: [Common task name - e.g., "Adding a new API endpoint"]**
1. [Step-by-step instructions]
2. [Where files go]
3. [What to update]
4. [Testing requirements]

**Task 2: [Common task name - e.g., "Integrating an external service"]**
1. [Step-by-step instructions]
2. [Where files go]
3. [What to update]
4. [Testing requirements]

**Task 3: [Common task name - e.g., "Modifying configuration"]**
1. [Step-by-step instructions]
2. [What to check]
3. [How to test]
4. [Deployment considerations]

[Add more tasks as relevant to this repository]

---

## SECTION 6: MCP TOOLS (Fully Generic - Copy As-Is)

### 6.1 Serena MCP

**Purpose:** Code-aware search and navigation using Abstract Syntax Tree (AST) analysis.

**When to Use:**
- Finding exact class, method, or variable names
- Locating all references to a code element
- Understanding inheritance and implementation relationships
- Navigating code structure

**When NOT to Use:**
- Semantic searches ("find similar error handling")
- Conceptual queries ("how do we handle authentication?")
- Text-based searches in comments or documentation

**Usage Examples:**

```
✅ GOOD USES:

"Use Serena to find method [methodName]"
"Use Serena to find all calls to [methodName]"
"Use Serena to find classes implementing [InterfaceName]"
"Use Serena to find all references to [ClassName]"

❌ BAD USES:

"Use Serena to find code similar to retry logic"
→ Use Vector DB instead

"Use Serena to understand how errors are handled"
→ Use Vector DB or ask conceptual question
```

**Best Practices:**
- Be specific with names (exact class/method names)
- Scope to specific directories when possible
- Use for structural code navigation
- Prefer Serena over Vector DB for exact matches

---

### 6.2 Sequential Thinking MCP

**Purpose:** Break down complex problems into logical steps before implementation.

**When to Use:**
- Complex multi-step tasks requiring careful planning
- Debugging intricate issues with multiple potential causes
- Architectural decisions that affect multiple components
- High-risk changes to critical business logic
- Tasks where you need to "think through" consequences

**When NOT to Use:**
- Simple, straightforward tasks
- Well-understood repetitive tasks
- When immediate action is clear

**Usage Pattern:**

```
Before implementing [complex task], use Sequential Thinking to:

1. Understand the current state
   - What exists now?
   - Why was it designed this way?
   - What are the constraints?

2. Identify the goal
   - What needs to change?
   - What's the desired end state?
   - What are the success criteria?

3. Break down the problem
   - What are the logical steps?
   - What are the dependencies?
   - What could go wrong?

4. Consider implications
   - What are the side effects?
   - What else might be affected?
   - What are the risks?

5. Plan the implementation
   - What's the safest order?
   - What can be tested incrementally?
   - What's the rollback plan?

6. Then proceed with implementation
```

**Best Practices:**
- Use for high-impact or complex changes
- Document the thinking process
- Validate assumptions before proceeding
- Use for any change affecting critical business rules

---

### 6.3 Git MCP

**Purpose:** Interact with git history, branches, and commits to understand code evolution.

**When to Use:**
- Understanding why code was written a certain way
- Finding when a bug was introduced
- Reviewing recent changes in an area
- Understanding code ownership and history
- Investigating regressions

**Common Operations:**

```
View Recent Changes:
"Use Git to show recent commits affecting [file/directory]"

Find When Bug Introduced:
"Use Git to find commits that modified [method/class] in the last month"

Understand Design Decision:
"Use Git to show the commit that introduced [feature/pattern]"

Review Author Context:
"Use Git to show who last modified [critical section]"

Compare Branches:
"Use Git to show differences between branches"
```

**Best Practices:**
- Check git history before modifying unfamiliar code
- Read commit messages for context
- Use git blame to find who to ask about code intent
- Review related commits when fixing bugs

---

## SECTION 7: DO's (Fully Generic - Copy As-Is)

### Code Quality

**Follow Language/Framework Best Practices**
- Use idiomatic patterns for the language
- Follow framework conventions and lifecycle
- Use appropriate data structures and algorithms
- Write clean, readable code

**Use Structured Logging**
- Include relevant context (IDs, operation names)
- Use appropriate log levels (DEBUG, INFO, WARN, ERROR)
- Log significant business events
- Make logs searchable and actionable

**Handle Errors Gracefully**
- Catch and handle exceptions appropriately
- Log errors with full context
- Return user-friendly error messages
- Never expose internal errors to end users

**Protect Sensitive Data**
- Never log passwords, tokens, or API keys
- Mask PII (emails, phone numbers, addresses)
- Be cautious with business-sensitive data
- Follow data protection regulations

**Pass Context Through Operations**
- Include request/trace IDs in all operations
- Preserve context through async operations
- Enable distributed tracing for debugging
- Make operations traceable end-to-end

**Write Tests**
- Write unit tests for business logic
- Write integration tests for critical paths
- Mock external dependencies appropriately
- Use test utilities suited to the framework

**Follow Existing Patterns**
- Match existing code style and formatting
- Use established naming conventions
- Follow existing error handling patterns
- Replicate existing logging approaches

**Keep Code Modular**
- Separate concerns appropriately
- Keep functions/methods focused and single-purpose
- Use dependency injection
- Make code testable and maintainable

**Document Complex Logic**
- Add comments for non-obvious code
- Document business rules and edge cases
- Keep documentation close to code
- Update docs when code changes

---

## SECTION 8: DON'Ts (Fully Generic - Copy As-Is)

### Critical Mistakes to Avoid

**Don't Mix Business Logic with Framework Code**
- Keep business logic separate from HTTP/UI concerns
- Don't put validation in presentation layer only
- Business rules should be framework-agnostic
- Keep core logic testable without framework

**Don't Hardcode Configuration**
- Use configuration files or environment variables
- Don't embed credentials in code
- Make configuration environment-specific
- Use configuration management tools

**Don't Log Sensitive Information**
- Never log passwords or authentication tokens
- Don't log full credit card numbers or PII
- Don't log sensitive business data
- Use masking utilities when necessary

**Don't Make Changes Without Understanding Impact**
- Always find all references before deleting code
- Understand dependencies before modifying
- Don't assume tests cover all cases
- Search for configuration dependencies

**Don't Mix Concerns in Changes**
- Don't refactor while fixing bugs
- Don't add features while deleting code
- Keep changes focused on single purpose
- Make one logical change per commit

**Don't Make Assumptions**
- Don't assume build tools or processes
- Don't assume deployment methods
- Ask about environment if unsure
- Don't add dependencies without confirmation

**Don't Skip Impact Analysis**
- Always check what calls modified code
- Verify tests still pass
- Check for configuration dependencies
- Consider downstream effects

**Don't Ignore Existing Conventions**
- Match existing file naming
- Follow established directory structure
- Use consistent formatting
- Replicate existing patterns

**Don't Block Critical Operations**
- Be aware of performance implications
- Don't introduce blocking operations in async code
- Consider scalability impact
- Test with realistic load

**Don't Skip Security Considerations**
- Validate all inputs
- Follow principle of least privilege
- Don't trust user input
- Consider security in design

---

## TOKEN EFFICIENCY QUICK REFERENCE (Fully Generic - Copy As-Is)

**Tool Selection:**
- Exact names → Serena MCP or grep
- Code structure → Serena MCP
- Semantic search → Vector DB (limit 5-10)

**Loading Strategy:**
- Load only relevant files/methods
- Show snippets before full context
- Ask before loading more
- Scope searches to specific directories

**Task Budgets:**
- Simple: 5-20k tokens
- Medium: 20-50k tokens
- Complex: 50-100k tokens

**Common Mistakes:**
- Using Vector DB for exact searches (causes 50+ results)
- Loading entire files when needing one method
- Not scoping searches to relevant directories
- Making changes without finding all references first

---

## GENERATION INSTRUCTIONS

**For Sections 1-3 (Repository-Specific):**
- Analyze the actual codebase thoroughly
- Provide real file paths, directory structures, and examples
- Identify actual business rules from the code
- Be specific and accurate

**For Sections 4-8 (Generic with Examples):**
- Section 4: Use generic template but include repository-specific examples
- Sections 5-8: Copy the generic content exactly as provided
- Ensure consistency in formatting and structure

**Output Format:**
- Generate the complete AGENTS.md file
- Use clear markdown formatting
- Include all sections in order
- Make it ready to commit to the repository
