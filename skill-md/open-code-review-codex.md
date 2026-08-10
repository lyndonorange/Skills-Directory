---
name: open-code-review
display_name: open-code-review
platform: Codex
category: General and specialized workflows
---

# open-code-review - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `open-code-review` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

>

## How To Use It In Codex

In Codex, click the chat box, press /, choose open-code-review, then write the task. Fallback prompt: Use the open-code-review skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `open-code-review` |
| Canonical name | `open-code-review` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

>


## Original SKILL.md

---
name: open-code-review
description: >
  Automatically executes the installed `ocr` program from alibaba/open-code-review
  to review Git changes; never responds with instructions alone. Use when the user
  asks to review code, a pull request, staged or unstaged changes, a commit, or a
  branch comparison. Runs OCR-managed review when its LLM is available and falls
  back to OCR delegation so the program still performs deterministic file selection
  and rule resolution. Produces line-level findings and applies fixes only when asked.
license: Apache-2.0
metadata:
  author: alibaba
  homepage: https://github.com/alibaba/open-code-review
  version: "1.0.0"
---

# Open Code Review

A skill for invoking [open-code-review](https://github.com/alibaba/open-code-review) (`ocr`) — an open-source AI code review CLI that reads Git diffs and generates structured, line-level review comments.

## Mandatory execution contract

When this skill triggers, execute the real `ocr` CLI during the same task. Do not merely describe commands, provide a setup guide, or ask the user to run OCR manually unless execution is genuinely blocked.

1. Run `command -v ocr` and `ocr version`.
2. Resolve the target repository and review scope from the request.
3. Run `ocr llm test`.
4. If the LLM test succeeds, run the matching `ocr review --audience agent --concurrency 1 ...` command. Keep one worker unless the user explicitly approves higher parallelism after a live memory check.
5. If the LLM test fails, automatically use OCR delegation: run `ocr delegate preview ...`, run `ocr delegate rule` for every reviewable file or batch, then perform the reasoning as the host agent using OCR's selected files and rules.
6. Report which OCR mode ran and include its file-selection receipt. A review response without an `ocr` invocation is incomplete.

The prerequisite, preview, rule-resolution, and review commands are read-only. Run them without an extra confirmation. Never modify code unless the user explicitly requested fixes.

## Prerequisites check

Before starting a review, verify the environment:

```bash
# 1. Check the CLI is installed
which ocr || echo "NOT INSTALLED"

# 2. Verify LLM connectivity
ocr llm test
```

If `ocr` is not installed, install it first:

```bash
npm install -g @alibaba-group/open-code-review
```

If `ocr llm test` fails, the user must configure an LLM. Guide them with one of these options:

**Option A — Environment variables (highest priority, recommended for CI):**

```bash
export OCR_LLM_URL=https://api.anthropic.com/v1/messages
export OCR_LLM_TOKEN=<api-key>
export OCR_LLM_MODEL=claude-opus-4-6
export OCR_USE_ANTHROPIC=true
```

**Option B — Persistent config:**

```bash
ocr config set llm.url https://api.anthropic.com/v1/messages
ocr config set llm.auth_token <api-key>
ocr config set llm.model claude-opus-4-6
ocr config set llm.use_anthropic true
```

Never invent or hardcode API keys. If the user explicitly requires OCR-managed LLM execution, stop and request configuration. Otherwise, continue automatically with delegation mode so OCR still participates in the review.

## Workflow

### Step 1: Gather Business Context

Analyze the review target (commits, branch, or changes) to extract concise business context. Pass this context via `--background` to improve review quality.

### Step 2: Run Code Review

Run the OCR command with appropriate flags. **Always pass business context via `--background`** when available. Prefer OCR-managed mode when `ocr llm test` succeeds:

```bash
ocr review --audience agent --concurrency 1 --background "business context here" [user-args]
```

If `ocr llm test` fails, use the program's delegation pipeline automatically:

```bash
ocr delegate preview --background "business context here" [target-args]
ocr delegate rule <reviewable-file> [more-reviewable-files]
```

Use the preview's mode, refs, reviewable paths, exclusions, and resolved rule groups to retrieve the corresponding diffs and complete the review as the host agent. Do not substitute an unscaffolded generic review.

**Argument handling:**

- **Background context** (RECOMMENDED): use `--background "context"` or `-b "context"` to provide business context for better review quality
- **Default** (no user arguments): reviews staged, unstaged, and untracked changes (workspace mode)
- **Specific commit**: use `--commit` or `-c` to review a single commit against its parent
- **Branch comparison**: use `--from <ref>` and `--to <ref>` to review diff between two refs
- **Timeout**: default timeout is 10 minutes per file; adjust with `--timeout <minutes>`
- **Concurrency**: always pass `--concurrency 1` by default. Higher parallelism requires explicit user approval after checking live memory pressure, especially for local Ollama models.
- **Preview mode**: use `--preview` or `-p` to preview which files will be reviewed without running the LLM
- **Installation**: if `ocr` command is not found, install it by running `npm i -g @alibaba-group/open-code-review`

**Common invocation patterns:**

| User says | Command to run |
|-----------|---------------|
| "review my changes" / "review the working copy" | `ocr review --audience agent --concurrency 1 -b "context"` |
| "review this PR" / "review feature branch" | `ocr review --audience agent --concurrency 1 -b "context" --from main --to <branch>` |
| "review commit abc123" | `ocr review --audience agent --concurrency 1 -b "context" --commit abc123` |
| "what would be reviewed?" (dry-run) | `ocr review --preview` |

**Output mode:**

- Always use `--audience agent` to suppress progress UI and emit only the final summary

### Step 3: Classify and Report

For each comment from the review output, classify by priority and report all issues to the user:

- **High**: Obvious bugs, security issues, clear mistakes, or well-founded suggestions with precise fix proposals
- **Medium**: Reasonable concerns but context-dependent, style/performance suggestions, or fixes that require manual implementation
- **Low**: Likely false positives, lacking sufficient context, nitpicks, or meaningless suggestions

Report all comments grouped by priority level.

### Step 4: Fix

Before applying fixes, check whether the user requested automatic fixes:

- If the user explicitly requested "review and fix" or similar, proceed with automatic fixes
- If the user only requested "review" without fix intent, ask for permission before applying any changes

When fixing issues and suggestions:

- Focus on High and Medium priority items
- Apply fixes directly to the code when safe and well-defined
- For complex fixes requiring manual intervention, clearly describe what needs to be done
- Always verify fixes with the user before committing

## Output Format

Each comment contains:

- `path`: File path
- `content`: Review comment text
- `start_line` / `end_line`: Line range (both 0 means positioning failed)
- `suggestion_code`: Optional fix suggestion
- `existing_code`: Optional original code snippet
- `thinking`: Optional LLM reasoning process

After filtering comments by priority, present results using this template:

```markdown
## Code Review Results

**Files reviewed**: N
**Issues found**: X high priority / Y medium priority

### High Priority

- **`path/to/file.java:42`** — Brief description
  > Recommendation: How to fix

### Medium Priority

- **`path/to/file.ts:88`** — Brief description
  > Recommendation: How to fix (if applicable)
```

If the review found no issues after filtering, simply state: "Review complete — no issues found in N files."

**Priority classification:**

- **High**: Obvious bugs, security issues, clear mistakes, or well-founded suggestions with precise fix proposals
- **Medium**: Reasonable concerns but context-dependent, style/performance suggestions, or fixes that require manual implementation
- **Low**: Discarded silently (likely false positives, lacking context, nitpicks, or meaningless suggestions)

**Handling mispositioned comments:**

When `start_line` and `end_line` are both `0`, the comment failed to locate the exact position in the file. In such cases:

1. Read the comment content to understand the issue
2. Examine the target file mentioned in the comment
3. Identify the relevant code section based on the comment's context
4. Apply the fix or suggestion to the correct location

## Custom Review Rules

If the user wants project-specific rules, OCR resolves them in this priority order:

1. `--rule <path>` flag (highest)
2. `<repo>/.opencodereview/rule.json`
3. `~/.opencodereview/rule.json`
4. Built-in system defaults (lowest)

By default, the first matching user rule replaces the built-in system rule. Set `merge_system_rule: true` on a rule entry when the matched system rule and user rule should both be included.

Rule file format:

```json
{
  "rules": [
    {
      "path": "**/*.java",
      "rule": "All new methods must validate required parameters for null",
      "merge_system_rule": true
    },
    {
      "path": "**/*mapper*.xml",
      "rule": "Check SQL for injection risks and missing closing tags"
    }
  ]
}
```

To preview which rule applies to a file before reviewing:

```bash
ocr rules check src/main/java/com/example/Foo.java
```

## Gotchas

- **LLM availability selects the mode** — run `ocr llm test`; use `ocr review` when it passes and automatically fall back to `ocr delegate` when it fails.
- **Working directory matters** — `ocr review` operates on the Git repo at the current directory. Use `--repo /path/to/repo` to run from elsewhere.
- **Untracked files are reviewed in workspace mode** — running bare `ocr review` includes staged, unstaged, *and* untracked changes. Stage selectively if you want narrower scope.
- **Large diffs may hit token limits** — files with very large diffs may be truncated. The default `MAX_TOKENS` is 58888 per request.
- **Plan phase triggers at 50 lines** — diffs exceeding 50 changed lines run an extra risk-analysis phase before main review. This adds latency but improves quality.
- **Don't pass `--audience human`** — it streams progress UI that pollutes output. Always use `--audience agent`.
- **Comment language follows config** — set `language` config to `English` or `Chinese` (default: Chinese) to control review comment language.

## Validation

After the review completes, verify success by checking:

1. `ocr version` identified the executable.
2. OCR-managed review exited with code 0, or delegation preview and rule resolution both exited with code 0.
3. The reported file count matches OCR's reviewable-file receipt.
4. Comments were generated, or the result explicitly states that no actionable findings were found.
5. Warnings and exclusions are disclosed when they affect coverage.

If errors occurred, check the stderr warnings for details about which files failed and why.

## References

- Full docs: https://github.com/alibaba/open-code-review
- NPM package: https://www.npmjs.com/package/@alibaba-group/open-code-review
- Issue tracker: https://github.com/alibaba/open-code-review/issues
