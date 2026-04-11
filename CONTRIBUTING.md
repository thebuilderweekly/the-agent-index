# Contributing to The Agent Index

Thanks for thinking about contributing. The bar for inclusion is sharp but the contribution process is loose. Here is how it works.

## How to suggest a tool

1. **Read [STANDARDS.md](./STANDARDS.md)** to understand the inclusion criterion. The most common reason a suggestion gets rejected is that the tool requires a human-only setup step (KYC, business verification, carrier review, identity document upload) somewhere in its lifecycle.

2. **Open a pull request** that adds your tool to the appropriate category in [README.md](./README.md). Use the same format as existing entries: an H3 heading with the tool name, a one-sentence factual description, a blockquoted editorial note, and a metadata line with integration method + homepage + docs + github + open-source status where applicable.

3. **In the PR description, briefly answer three questions:**
   - What specific job does an agent reach for this tool to do?
   - Can an agent set this up and use it through a fully programmatic path? If there are setup steps, name them.
   - Is this Tier 1 (API-key only) or Tier 2 (multi-credential programmatic path — e.g. needs DNS provider credentials alongside the tool's own key)?

4. **A maintainer will review your PR.** Reviews are manual. There is no automated CI gate in v1 — no linter, no schema validator, no link checker. The review is a human reading the entry and deciding whether it matches the voice and passes the bar.

## What gets rejected

- **Agent frameworks** (LangChain, LangGraph, LlamaIndex, CrewAI, AutoGen, DSPy). These are scaffolding for building agents, not tools agents call.
- **Observability tools** (Langfuse, LangSmith, Helicone, Braintrust, Arize Phoenix). For humans watching agents, not for agents to call.
- **Agent products humans use** (Cursor, Claude Code, Replit Agent, Devin, Lovable). These are agents themselves, not tools agents call.
- **Human-primary SaaS with API access** (Notion, Slack, Linear, Figma, GitHub, Google Workspace). Humans are the primary users; agents are at most secondary writers.
- **AI content creation tools** (Jasper, Copy.ai, Midjourney, Runway, Synthesia). These produce content for humans to consume.
- **Tools with human-gated setup**: KYC, business verification, carrier compliance review, identity document uploads, sales-contact onboarding, manual approval dashboards. If the tool's own docs describe a step that a person has to do and there is no API or CLI equivalent, the tool fails the bar.
- **Tools behind a waitlist** where approval is discretionary. If anyone can sign up today and get a key immediately, the tool is eligible. If there is a waitlist or "request access" form that a human evaluates, it is not.

## What we welcome

- **Small tools you built or use** that meet the criterion. Star count, brand recognition, and revenue do not matter. The tool either passes the bar or it does not.
- **Corrections to existing entries**: the editorial note is wrong, the integration method has changed, the tool has shipped a material update, the tool has shut down, the homepage URL redirects somewhere surprising.
- **New categories** if you have at least three tools that fit the category and those tools do not fit an existing bucket. Fewer than three means the category folds into another one or does not get created yet.

## Editorial voice

The editorial notes in this README are written in the voice of The Builder Weekly. Short sentences. Direct claims. No scaffolding phrases like "leading", "powerful", "cutting-edge", "game-changing", or "revolutionary". No em dashes. The note describes what the tool is for and why an agent reaches for it, not what the vendor says about themselves.

Look at the existing entries for the rhythm. A good note is 2-4 sentences, makes one concrete claim, and would be edited down if it ran longer.

## Questions

Open a [GitHub issue](https://github.com/thebuilderweekly/the-agent-index/issues) or read [STANDARDS.md](./STANDARDS.md) for the full criterion.
