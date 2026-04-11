# How We Choose Tools

The Agent Index is small on purpose. Here is what gets in, what we keep out, and why.

## The bar

A tool belongs in the Agent Index if the entire setup and operation of that tool has a fully programmatic path. An agent with the right credentials must be able to complete the full lifecycle (sign up, configure, integrate, use) without anyone clicking anything in a dashboard, uploading identity documents, waiting for carrier compliance review, or completing a manual verification flow.

The question is not whether an agent *could* call the tool once a human finished setup. The question is whether the human is necessary. If the setup is gated by regulation or domain reality that forces a person into the loop, the tool fails the bar. If the setup is just more complicated (DNS records, multi-service credential plumbing), the tool still passes, because complication is not the same as human-gated.

That distinction matters enough that we make it explicit in two tiers.

## Tier 1 and Tier 2

**Tier 1.** API-key-only. An agent signs up, gets an API key, and is immediately productive. No other services required. Most of the Index lives here.

**Tier 2.** Fully programmatic but requires credentials for additional services to complete setup. The canonical example is sending email from a custom domain: Resend and SendGrid both let an agent create a domain, retrieve the DNS records, and trigger verification through their REST APIs. Pushing those DNS records into place requires a separate credential for a DNS provider like Cloudflare or Route 53. Both sides are API-driven; neither side needs a human. A Tier 2 tool passes the bar because an agent with both credentials can complete the full path without human intervention. Tier 2 entries carry a note in their editorial line acknowledging the extra credential requirement so the setup cost is visible upfront.

## The LLM inference exception

LLM inference APIs (Anthropic, OpenAI, Gemini, Groq, Together AI, and their peers) are the substrate of agent operation. They stay in the Index regardless of any friction on the account-creation side, because without a model call there is no agent to reason about in the first place. Some of these providers require a credit card or a phone number on signup that an agent running in a fresh environment may not have. That friction is real. It does not disqualify them. The Index would be dishonest if it listed vector databases and code sandboxes but pretended the models did not exist.

## What's in

Infrastructure an agent calls during its work, organized into these categories:

- **LLM Inference.** The models themselves. Anthropic, OpenAI, Gemini, Groq, Together AI. Under the inference exception above.
- **Memory.** Persistent state for agents across sessions. Mem0, Zep, Letta.
- **Vector Stores.** Semantic retrieval for RAG. Pinecone, Weaviate, Qdrant, Chroma, Turbopuffer.
- **Voice and Speech.** Turning audio into text and text into voice. Deepgram, AssemblyAI, ElevenLabs, Cartesia, TalkAPI.
- **Browser Automation.** Giving agents a real browser. Browserbase, Stagehand, Steel Browser. Bright Data was considered and cut — see below.
- **Code Execution.** Sandboxes for agent-written code. E2B, Modal, Daytona, Riza.
- **Web Search and Retrieval.** Search APIs designed for agents. Exa, Tavily, Firecrawl, Crawlbeam.
- **Scheduling and Orchestration.** Durable execution and outcome verification for agent work. CueAPI, Inngest, Trigger.dev.
- **Communication.** Outbound email from agents to humans. Resend and SendGrid. Both are Tier 2; see their editorial notes for the DNS dependency.
- **Credentials and Tool Management.** Handling OAuth and tool catalogs for agents. Composio, Arcade AI, Metorial.
- **MCP Ecosystem.** The Model Context Protocol and the servers built on top of it. Reference servers, Smithery, Context7.

## What we cut and why

The sharper bar cut five tools that a looser criterion would let through. Each failure mode is a class, not an accident — the underlying domain has regulatory or operational reality that forces a human into the loop with no API equivalent.

### Payment processing

Stripe, Lithic, and Bridge were all cut. Stripe's own docs are explicit: account activation can require a scan of a valid government-issued ID and a proof-of-address document, with human review attached. Lithic, a card-issuing platform regulated under banking law, requires KYC and KYB verification to move any production card. Bridge, the stablecoin payments rail, onboards through a sales conversation — there is no self-serve signup for money-transmitter access. None of the three has a programmatic path to production credentials. The category was removed from the filter bar entirely because zero tools in it passed.

### SMS and telephony

Twilio was cut. The A2P 10DLC campaign-registration process for sending US SMS requires carrier vetting that takes 10 to 15 days and involves human review of business documentation. Twilio offers the registration via API, but the carrier review at the end is not an API problem. The Communication category was kept because Resend and SendGrid solve a different shape of the same problem (email, not SMS) and their setup flows are fully programmatic.

### Compliance-gated web scraping

Bright Data was cut. Their own compliance documentation is unambiguous: full access to the residential proxy network requires live video identity verification, a personal review by an experienced compliance officer, and a valid form of government-issued identification such as a driver's license or passport. Approval takes up to 48 hours. That is the exact failure mode the bar exists to catch. The other three browser-automation entries (Browserbase, Stagehand, Steel Browser) remain.

## What's deliberately out (the categorical exclusions)

Independent of the programmatic-path test, some categories of tool are off-criterion by definition because the tool's user is not an agent:

- **Agent frameworks.** LangChain, LangGraph, LlamaIndex, CrewAI, AutoGen, DSPy, Haystack, Semantic Kernel. Scaffolding for building agents, not tools agents call. An agent does not wake up and reach for LangChain.
- **Observability and evals.** Langfuse, LangSmith, Helicone, Braintrust, Arize Phoenix, Weights & Biases, AgentOps. For humans watching agents, not for agents to call. Essential for operators; off-criterion for the Index.
- **Agent products humans use.** Cursor, Claude Code, Replit Agent, v0, Lovable, Bolt, Devin, ChatGPT. These are agents that humans use, not tools agents use.
- **Human-primary SaaS.** Notion, Airtable, Slack, Linear, Figma, GitHub, Google Workspace. Humans are the consumers. Agents might poke at these through an API, but the tool was not designed for the agent to be the user.
- **AI content creation tools.** Jasper, Copy.ai, Midjourney, Runway, Synthesia, Pika, Suno. These produce content for humans to consume. An agent that renders its own work does not reach for a marketing content tool.
- **Generic developer tools.** Git, GitHub Actions, Docker, Kubernetes, Terraform. Infrastructure for humans building software. An agent uses these the same way a human does, which is to say, off-criterion.
- **Datasets, benchmarks, papers, courses.** Reading material, not callable infrastructure.

## How we maintain the list

v1 is hand-curated. Every entry has a verification date and was confirmed to be alive and still meeting the criterion when added. A future phase will add a discovery pipeline that surfaces candidates for human review. The human review step is the point and will not go away.

We do not rank within categories. If two tools in the same category are both in the Index, they are both in because they both passed the bar. We might write about why one fits a specific use case better than the other; the Index itself is just the list.

## How to suggest a tool

Open a PR against [README.md](./README.md) that adds your tool in the appropriate category. Read [CONTRIBUTING.md](./CONTRIBUTING.md) first for the review process and the format to follow. If we cannot write an editorial note about why the tool passes the criterion, it does not make the Index.
