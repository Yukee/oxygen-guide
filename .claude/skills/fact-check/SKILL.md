---
name: fact-check
description: Use when the user asks to fact-check a guide section, verify claims, or says /fact-check. Takes a markdown filename as argument.
---

# Fact-Check a Guide Section

Launch fact-checking agent(s) to verify all factual claims in a markdown guide file using web search.

## Input

The argument is a markdown filename (e.g., `06-aborting-protocol.md`). Resolve it from the project root.

## Fact-Check Steps

### 1. Read the file

Read the input markdown file to understand its structure, length, and identify all factual claims that need verification.

### 2. Launch fact-checker agent(s)

Use the Task tool to launch fact-checker agent(s) in the background:

**For short files (under ~150 lines):**
- Launch a single fact-checker agent

**For long files (150+ lines):**
- Split the file into 2-3 subsection ranges
- Launch separate fact-checker agents for each range (all in parallel, in a single message)
- Tell each agent which sections/line ranges to focus on

**Agent configuration:**
- **Subagent type:** `general-purpose`
- **Prompt template:**

```
Read the fact-checker agent instructions from /Users/mace/clusterheaches/oxygen-guide/.claude/agents/fact-checker.md and follow them exactly.

The file to review is: /Users/mace/clusterheaches/oxygen-guide/INPUT_FILE.md

[For split files: Focus on lines X-Y, which covers sections: SECTION_NAMES]

Read the file, then perform your fact-checking review as instructed. Use web search to verify every factual claim. Return your complete fact-checking report.
```

### 3. Wait for agent(s) and collect results

Use the Read tool to check background agent output files. Wait for all fact-checker agents to complete before proceeding.

### 4. Synthesize the fact-check report

After all agents have returned their reviews, produce a unified report with these sections:

#### Report format

```markdown
## Fact-Check Report: [filename]

### Critical Errors (must fix immediately)
- [Claims that are WRONG or UNSUPPORTED and could cause harm]
- [Missing critical safety information]

### High Priority Issues
- [Claims that are PARTIALLY SUPPORTED or need qualification]
- [Important claims that lack sufficient nuance]

### Medium Priority Issues
- [Claims that are supported but could be stated more precisely]
- [Minor factual issues that don't affect safety]

### Low Priority Notes
- [Minor wording suggestions for clarity]
- [Additional context that could strengthen claims]

### Verification Summary Table

| Claim | Status | Priority | Source(s) | Suggested Action |
|-------|--------|----------|-----------|------------------|
| [Claim text] | SUPPORTED / PARTIALLY SUPPORTED / UNSUPPORTED / WRONG | HIGH / MEDIUM / LOW | [URLs] | [Action] |
| ... | ... | ... | ... | ... |

### Full Fact-Checker Report(s)
<details>
<summary>Fact-Checker Report [1]</summary>
[Full report]
</details>

[Additional fact-checker reports if file was split]
```

### 5. Suggest corrections

After the report, propose specific corrections for any claims that need fixing. For each correction:
- Quote the original claim
- State the issue (wrong, unsupported, partially supported, needs qualification)
- Provide the suggested replacement text
- Include supporting source(s)

Ask the user which corrections they'd like to apply.

## Notes

- The fact-checker agent should use web search extensively to verify claims
- This is a medical harm-reduction guide — accuracy and precision are critical
- For very long files (300+ lines), consider splitting into 3-4 parallel agents by major section
- If sources conflict, note the disagreement and present both perspectives
- Flag any claims that can't be verified due to lack of available research
