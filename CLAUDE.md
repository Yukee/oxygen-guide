# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a markdown-based medical guide about high-flow oxygen therapy for cluster headache patients. The target audience is a 50-something with no experience with oxygen — including how to talk to specialists, get a prescription, choose equipment, and use it safely. Content must be comprehensive yet accessible to someone with little skill finding reliable information online.

## Workflow

Guide sections are written as markdown files in the project root. Key skills:

- `/review <file.md>` — launches three editorial agents in parallel (straight-to-facts editor, visual artist, median user) and synthesizes their findings
- `/fact-check <file.md>` — launches fact-checker agent(s) to verify all claims via web search
- `/generate-html <file.md>` — converts markdown to styled HTML with navigation, using the full inline CSS template defined in the skill
- `/generate-image <description> <filename>` — generates flat infographic illustrations via Gemini API (blue/teal palette, light cream background, medical educational style)

## Content Conventions

- Images go in `images/` directory, named `illustration-<descriptive-name>.jpg`
- Image references in markdown: `![Alt text](images/filename.jpg)` followed by `*Caption text*` on the next line
- Markdown files link to each other with `.md` extensions (converted to `.html` by the generate-html skill)
- Em dashes (—) are not used, as they are too LLM-coded

## Editorial Agents

Four specialized agents in `.claude/agents/` review content from different perspectives:

- **fact-checker** — verifies every factual claim via web search; rates as SUPPORTED/PARTIALLY SUPPORTED/UNSUPPORTED/WRONG
- **straight-to-facts** — finds redundancies, unnecessary details, and verbose passages; does NOT web search
- **visual-artist** — checks that illustrations match their surrounding text and alt text
- **median-user** — role-plays the target audience to find jargon, ambiguities, and missing information; does NOT web search

## Writing Guidelines

- This is a harm-reduction guide — accuracy is paramount
- Hand-holding is expected and necessary for the audience; don't cut explanations of unfamiliar concepts
- Keep medical claims precise and verifiable
- When in doubt about a factual claim, use `/fact-check` rather than guessing
