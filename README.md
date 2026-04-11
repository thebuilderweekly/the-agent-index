# The Agent Index

**Infrastructure for AI agents. Tools an agent reaches for mid-workflow to do its job.**

Maintained as the source of truth for [The Builder Weekly’s](https://thebuilderweekly.com) Agent Index page. Contributions welcome — see [CONTRIBUTING.md](./CONTRIBUTING.md).

## The bar

A tool earns a place in this list if an agent can use it end to end through a fully programmatic path. No human-only steps with no API or CLI equivalent. No KYC, no carrier compliance reviews, no manual dashboard configuration.

The distinction that matters most: complication is fine, human-gated steps are not. Some tools pass on a single API key (**Tier 1**). Others are fully programmatic but need credentials for additional services to complete setup — sending email from a custom domain, for example, requires DNS provider credentials alongside the email API key. Both shapes pass (**Tier 2** for multi-credential).

LLM inference APIs (Anthropic, OpenAI, Gemini, Groq, Together) get a dedicated exception and stay in the list regardless of account-creation friction. They are the substrate of agent operation; listing everything else while pretending the models did not exist would be dishonest.

The full inclusion criterion, the Tier 1 / Tier 2 framework, and the list of deliberate exclusions are in [STANDARDS.md](./STANDARDS.md).

## Categories

- [LLM Inference](#llm-inference) (5)
- [Memory](#memory) (3)
- [Browser Automation](#browser-automation) (3)
- [Code Execution](#code-execution) (4)
- [Communication](#communication) (2)
- [Credentials and Tool Management](#credentials-and-tool-management) (3)
- [MCP Ecosystem](#mcp-ecosystem) (3)
- [Scheduling and Orchestration](#scheduling-and-orchestration) (3)
- [Vector Stores](#vector-stores) (5)
- [Voice and Speech](#voice-and-speech) (5)
- [Web Search and Retrieval](#web-search-and-retrieval) (4)

**40 entries across 11 categories.**

---

## LLM Inference

### Anthropic API

Claude models (Sonnet, Opus, Haiku) via REST API with native tool-use, extended thinking, and MCP support.

> The default model for most agent workflows in 2026. Strong tool-use, reliable structured output, and a context window that holds up through 200k tokens instead of degrading past 50k. First-class MCP integration makes Claude the easiest frontier model to wire into agentic systems, and the hardest to regret when an agent needs to pick a tool and commit.

**Integration:** REST API · **Homepage:** [Anthropic API](https://anthropic.com) · **Docs:** [https://docs.anthropic.com](https://docs.anthropic.com)

### Google Gemini API

Gemini 3 Pro and Flash models with native multimodal input, 2M token context, and image generation.

> The model to reach for when the job involves images, video, audio, or very long documents. Gemini 3 Pro Image is the cleanest 4K editorial illustration model currently shipping, and the 2M context window is a genuine unlock for agents reasoning over a whole codebase or a year of transcripts at once. Multimodal-first by design, which shows the moment a task stops being text-only.

**Integration:** REST API · **Homepage:** [Google Gemini API](https://ai.google.dev) · **Docs:** [https://ai.google.dev/gemini-api/docs](https://ai.google.dev/gemini-api/docs)

### Groq

Ultra-low-latency inference for open models (Llama, Mixtral, Qwen) on custom LPU silicon.

> When you need token latency measured in milliseconds, not hundreds of milliseconds, Groq is it. Agents that drive voice interfaces, real-time UIs, or tight inner loops reach for Groq because the speed unlocks interaction patterns that don't work on slower infra. Model selection is narrower than the frontier providers; that trade-off is the point.

**Integration:** REST API · **Homepage:** [Groq](https://groq.com) · **Docs:** [https://console.groq.com/docs](https://console.groq.com/docs)

### OpenAI API

GPT-4 class models, embeddings, image generation, and the Responses API via REST.

> Still the default for a lot of production agents. Embeddings are cheap and reliable, the Responses API finally gives agents a clean way to manage state across turns, and the function-calling shape is the one every other provider copied. Not always the best model for reasoning, but always the most compatible.

**Integration:** REST API · **Homepage:** [OpenAI API](https://openai.com/api) · **Docs:** [https://platform.openai.com/docs](https://platform.openai.com/docs)

### Together AI

Hosted inference for hundreds of open models plus dedicated endpoints and fine-tuning.

> The default when you want to run a specific open model in production without standing up your own GPU fleet. Model catalog is deep, the pricing is predictable, and fine-tuning is available for cases where a prompt isn't enough. Agents call it exactly like they call OpenAI, which keeps the integration layer simple.

**Integration:** REST API · **Homepage:** [Together AI](https://together.ai) · **Docs:** [https://docs.together.ai](https://docs.together.ai)

---

## Memory

### Letta

Stateful agent platform with persistent memory, context management, and a REST API for agent servers.

> The team that shipped MemGPT turned it into a platform. Letta lets you spin up a stateful agent as a REST endpoint, and the agent keeps its memory across turns without you having to thread state manually. Useful when the thing you are building is an agent, not a pipeline that calls a model.

**Integration:** REST API · **Homepage:** [Letta](https://letta.com) · **Docs:** [https://docs.letta.com](https://docs.letta.com) · **GitHub:** [https://github.com/letta-ai/letta](https://github.com/letta-ai/letta) · **Open source**

### Mem0

Persistent memory layer for AI agents with user-scoped storage, semantic recall, and fact extraction.

> Persistent memory primitives for agents, with semantic recall and user-scoped storage. Agents get a place to write what they learned about a user or session and retrieve it by meaning rather than keyword. The managed version is fast enough that memory reads don't visibly slow an agent loop, and the open-source core makes self-hosting a real option for teams that need it.

**Integration:** REST API · **Homepage:** [Mem0](https://mem0.ai) · **Docs:** [https://docs.mem0.ai](https://docs.mem0.ai) · **GitHub:** [https://github.com/mem0ai/mem0](https://github.com/mem0ai/mem0) · **Open source**

### Zep

Long-term memory for AI agents built on a temporal knowledge graph (Graphiti).

> Where Mem0 treats memory as facts in a database, Zep treats it as a graph of entities and relationships over time. Agents that need to reason about how things changed, not just what is currently true, reach for Zep. The Graphiti engine under the hood is a real piece of engineering.

**Integration:** Python Library · **Homepage:** [Zep](https://getzep.com) · **Docs:** [https://help.getzep.com](https://help.getzep.com) · **GitHub:** [https://github.com/getzep/zep](https://github.com/getzep/zep) · **Open source**

---

## Browser Automation

### Browserbase

Managed headless browser infrastructure for AI agents with session recording, live view, and stealth.

> Agents need browsers the same way humans need browsers, and running Chromium yourself at scale is miserable. Browserbase takes over the infrastructure entirely and gives you a session handle, a live view for debugging, and stealth mode that actually works against bot detection. When an agent needs to use a website nobody built an API for, start here.

**Integration:** SDK · **Homepage:** [Browserbase](https://browserbase.com) · **Docs:** [https://docs.browserbase.com](https://docs.browserbase.com)

### Stagehand

High-level browser automation library that lets agents describe actions in natural language.

> Stagehand is what happens when you stop writing Playwright selectors and let the agent describe the action instead. You call act('click the login button'), and Stagehand figures out which element that is. From Browserbase but open source, and the model cost is low enough that the ergonomics pay for themselves.

**Integration:** TypeScript Library · **Homepage:** [Stagehand](https://stagehand.dev) · **Docs:** [https://docs.stagehand.dev](https://docs.stagehand.dev) · **GitHub:** [https://github.com/browserbase/stagehand](https://github.com/browserbase/stagehand) · **Open source**

### Steel Browser

Open-source browser API for AI agents with session persistence, proxies, and CAPTCHA handling.

> The open-source answer to Browserbase. Run it yourself, wire it into your agent, get session persistence and CAPTCHA solving without paying per-session. If you need browser automation in a private network or at a price point that will not scale linearly with usage, Steel is the move.

**Integration:** REST API · **Homepage:** [Steel Browser](https://steel.dev) · **Docs:** [https://docs.steel.dev](https://docs.steel.dev) · **GitHub:** [https://github.com/steel-dev/steel-browser](https://github.com/steel-dev/steel-browser) · **Open source**

---

## Code Execution

### Daytona

Open-source development environments on demand for AI agents to read, edit, and execute codebases.

> Where E2B is for running code, Daytona is for giving an agent a full development environment. Fresh workspace, cloned repo, language servers ready, sandboxed from the host. When the agent is a coding agent and the task is multi-file changes against a real codebase, Daytona is the substrate.

**Integration:** CLI · **Homepage:** [Daytona](https://daytona.io) · **Docs:** [https://www.daytona.io/docs](https://www.daytona.io/docs) · **GitHub:** [https://github.com/daytonaio/daytona](https://github.com/daytonaio/daytona) · **Open source**

### E2B

Secure cloud sandboxes for AI agents to run code, render files, and execute long-running processes.

> The first code sandbox that felt like it was designed for agents, not humans. Agents spin up a sandbox, run untrusted code, render outputs, and tear it down without touching your infra. E2B is the reason code-interpreter style loops are practical in production; the alternative was running a container yourself.

**Integration:** SDK · **Homepage:** [E2B](https://e2b.dev) · **Docs:** [https://e2b.dev/docs](https://e2b.dev/docs) · **GitHub:** [https://github.com/e2b-dev/e2b](https://github.com/e2b-dev/e2b) · **Open source**

### Modal

Serverless cloud platform for running Python functions, GPU jobs, and containers on demand.

> Modal turned serverless Python into something you can actually build agents on top of. Agents can call a Modal function the same way they call any other API, and the function runs on a container with GPUs attached if it needs them. Cold starts are fast enough to hide, and the pricing matches what the function actually did.

**Integration:** Python Library · **Homepage:** [Modal](https://modal.com) · **Docs:** [https://modal.com/docs](https://modal.com/docs)

### Riza

Secure code interpreter API for LLM-generated code with fast-start sandboxes and memory isolation.

> The focused answer to one narrow question: how do I let the model run the code it just wrote without it escaping and burning down my infra? Riza is a sandbox, not a development environment, and that narrowness is the point. Sub-second starts, strict isolation, a tight API surface you can wire into a tool call in five minutes.

**Integration:** REST API · **Homepage:** [Riza](https://riza.io) · **Docs:** [https://docs.riza.io](https://docs.riza.io)

---

## Communication

### Resend

Developer-first transactional email API with React Email integration and high deliverability.

> The transactional email API that feels designed for agents to call rather than humans to configure. Clean SDK, sensible deliverability defaults, React Email templates that produce designer-quality output. Sending a custom-domain email requires DNS records for SPF, DKIM, and DMARC, but the entire flow is programmatic: POST to /domains to create the domain and receive the records, apply them through a DNS provider's API, then POST to /domains/{id}/verify to trigger async validation. Tier 2 passage on the programmatic-path test: needs DNS credentials alongside the Resend API key, but there is no human-gated step.

**Integration:** REST API · **Homepage:** [Resend](https://resend.com) · **Docs:** [https://resend.com/docs](https://resend.com/docs)

### SendGrid

Email delivery infrastructure for transactional and marketing mail at high volume.

> For when the volume is high and the deliverability numbers matter. The incumbent holds the category because shipping a million emails a day without landing in spam is a genuinely hard problem, and SendGrid has solved it for longer than almost any competitor. Sending from a custom domain requires authenticated domain setup, but every step has a REST endpoint: create the domain, retrieve DNS records, push them through a DNS provider's API, then call the validate-authenticated-domain endpoint. Tier 2 passage on the programmatic-path test: needs DNS credentials alongside the SendGrid API key, but there is no human-gated step.

**Integration:** REST API · **Homepage:** [SendGrid](https://sendgrid.com) · **Docs:** [https://docs.sendgrid.com](https://docs.sendgrid.com)

---

## Credentials and Tool Management

### Arcade AI

Authenticated tool-calling platform for agents with permissioned actions and per-user credential storage.

> Arcade's bet is that tool-calling is not complete until the auth story is. Agents get a tool catalog, but every call goes through Arcade's auth layer, which means the model never sees a raw credential and the user can revoke scopes without redeploying the agent. Useful when the agent is operating on behalf of humans with real permissions.

**Integration:** SDK · **Homepage:** [Arcade AI](https://arcade.dev) · **Docs:** [https://docs.arcade.dev](https://docs.arcade.dev)

### Composio

Tool and credential management platform for AI agents with 250+ pre-built integrations and OAuth handling.

> Agents that need to act on behalf of a user hit OAuth the moment they try to do anything useful. Composio solves the tool-and-credential problem with a pre-built catalog of integrations that handles auth, refresh, and scope management. The agent calls a named tool; Composio makes sure the right user's token is in place.

**Integration:** SDK · **Homepage:** [Composio](https://composio.dev) · **Docs:** [https://docs.composio.dev](https://docs.composio.dev) · **GitHub:** [https://github.com/ComposioHQ/composio](https://github.com/ComposioHQ/composio) · **Open source**

### Metorial

Managed MCP and tool-use platform for AI agents with credential vaulting and usage analytics.

> The MCP-native answer in this category. Metorial hosts your MCP servers, vaults the credentials they need, and hands the agent a single connection instead of a sprawl. For teams standardizing on MCP as the tool-calling substrate, this is the control plane.

**Integration:** MCP Server · **Homepage:** [Metorial](https://metorial.com)

---

## MCP Ecosystem

### Context7

MCP server that feeds agents up-to-date library documentation and code examples from the source.

> Coding agents keep hallucinating APIs that do not exist because their training data froze before the library's last breaking change. Context7 is the fix: an MCP server that pulls the current docs at call time, so when an agent asks 'how do I use this library', the answer matches reality. Simple idea; outsized impact on agent code quality.

**Integration:** MCP Server · **Homepage:** [Context7](https://context7.com) · **Docs:** [https://context7.com/docs](https://context7.com/docs) · **GitHub:** [https://github.com/upstash/context7](https://github.com/upstash/context7) · **Open source**

### Model Context Protocol

Open standard for connecting AI agents to tools and data sources, with a reference server collection.

> The protocol under a lot of the rest of this list. MCP defined the shape of how an agent discovers and calls a tool, and the reference servers repo is where the official integrations live (Postgres, GitHub, Slack, Filesystem, and dozens more). When a tool says 'MCP-compatible', it is promising the shape these servers define.

**Integration:** MCP Server · **Homepage:** [Model Context Protocol](https://modelcontextprotocol.io) · **Docs:** [https://modelcontextprotocol.io/docs](https://modelcontextprotocol.io/docs) · **GitHub:** [https://github.com/modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) · **Open source**

### Smithery

MCP server registry and hosting with one-click install for Claude, Cursor, and other MCP clients.

> The registry layer on top of the MCP ecosystem. Smithery catalogs every known MCP server, handles discovery, and offers hosted execution so you do not have to run the server yourself. For agents picking tools at runtime, Smithery is the closest thing the MCP world has to an App Store.

**Integration:** MCP Server · **Homepage:** [Smithery](https://smithery.ai) · **Docs:** [https://smithery.ai/docs](https://smithery.ai/docs)

---

## Scheduling and Orchestration

### CueAPI

Scheduling and execution accountability API for AI agents with verified outcomes and retries.

> Cron fires jobs. Cue knows whether they succeeded. The distinction matters the moment an agent schedules work: delivery confirmation is not the same as outcome verification. CueAPI sits underneath agents that have to do something later and confirm it got done, with native retries and exponential backoff on failure. Open source under Apache 2.0 for teams that want to self-host.

**Integration:** REST API · **Homepage:** [CueAPI](https://cueapi.ai) · **Docs:** [https://docs.cueapi.ai](https://docs.cueapi.ai) · **GitHub:** [https://github.com/cueapi/cueapi-core](https://github.com/cueapi/cueapi-core) · **Open source**

### Inngest

Durable execution platform for background jobs, AI workflows, and long-running agent steps.

> Durable execution for agent workflows that cannot fit inside a single request. Inngest checkpoints every step, so when the agent crashes halfway through a multi-step job, it resumes at the last good state instead of starting over. Useful when the agent's job is measured in minutes, not seconds.

**Integration:** SDK · **Homepage:** [Inngest](https://inngest.com) · **Docs:** [https://www.inngest.com/docs](https://www.inngest.com/docs) · **GitHub:** [https://github.com/inngest/inngest](https://github.com/inngest/inngest) · **Open source**

### Trigger.dev

Background job platform with built-in AI task support, concurrency controls, and wait-until-event primitives.

> Trigger.dev is the other shape of durable execution, leaning harder into AI-specific primitives. The wait-for-event model lets agents pause on a real-world condition (an email arrives, a webhook fires, a human approves) without holding a process open. Concurrency controls are first-class, which matters once your agent starts calling rate-limited APIs.

**Integration:** SDK · **Homepage:** [Trigger.dev](https://trigger.dev) · **Docs:** [https://trigger.dev/docs](https://trigger.dev/docs) · **GitHub:** [https://github.com/triggerdotdev/trigger.dev](https://github.com/triggerdotdev/trigger.dev) · **Open source**

---

## Vector Stores

### Chroma

Embedded and hosted vector database with a simple Python-first API, popular for RAG prototyping.

> The shortest path from zero to a working RAG loop. Chroma starts as an embedded Python library, and you can graduate to their hosted service without changing your code when the prototype turns into a product. Not every agent needs this path, but the ones that do save a week of plumbing.

**Integration:** Python Library · **Homepage:** [Chroma](https://trychroma.com) · **Docs:** [https://docs.trychroma.com](https://docs.trychroma.com) · **GitHub:** [https://github.com/chroma-core/chroma](https://github.com/chroma-core/chroma) · **Open source**

### Pinecone

Fully managed vector database with serverless indexes, hybrid search, and metadata filtering.

> The managed option most teams start with when they need vector search and do not want to operate a database. Serverless indexes removed the biggest operational pain, and hybrid search means you can mix semantic recall with keyword and metadata filters without running two systems. Not the cheapest at scale; almost always the fastest to ship.

**Integration:** REST API · **Homepage:** [Pinecone](https://pinecone.io) · **Docs:** [https://docs.pinecone.io](https://docs.pinecone.io)

### Qdrant

Rust-based vector search engine with strong filtering, sparse vector support, and a managed cloud.

> Fast, honest, and easy to run yourself. Qdrant is written in Rust, which is not the reason to pick it, but the result is that self-hosting is a single binary. Filtered search is a first-class citizen, which matters when your agent needs to scope a query to a specific user, tenant, or time window.

**Integration:** REST API · **Homepage:** [Qdrant](https://qdrant.tech) · **Docs:** [https://qdrant.tech/documentation](https://qdrant.tech/documentation) · **GitHub:** [https://github.com/qdrant/qdrant](https://github.com/qdrant/qdrant) · **Open source**

### Turbopuffer

Object-storage-native vector database designed to store billions of vectors cheaply on S3.

> The pricing model alone is worth the category. Turbopuffer keeps the index on object storage and hydrates shards on demand, which means you can store billions of vectors for a tenth of what a hot-memory database costs. Agents that need massive long-tail recall over old data without paying for it every second reach for this.

**Integration:** REST API · **Homepage:** [Turbopuffer](https://turbopuffer.com) · **Docs:** [https://turbopuffer.com/docs](https://turbopuffer.com/docs)

### Weaviate

Open-source vector database with native hybrid search, multi-tenancy, and generative modules.

> Open source that is actually operable. Weaviate ships with multi-tenancy built in, which matters the moment you have more than one customer sharing infrastructure. The generative modules mean you can push more of the RAG pipeline into the database; your agent just asks for the answer instead of fetching chunks and composing them.

**Integration:** REST API · **Homepage:** [Weaviate](https://weaviate.io) · **Docs:** [https://weaviate.io/developers/weaviate](https://weaviate.io/developers/weaviate) · **GitHub:** [https://github.com/weaviate/weaviate](https://github.com/weaviate/weaviate) · **Open source**

---

## Voice and Speech

### AssemblyAI

Speech intelligence API with transcription, speaker diarization, sentiment, and topic extraction.

> When the job is not just transcription but understanding what is in the audio. AssemblyAI ships diarization, sentiment, and topic extraction as first-class outputs, so an agent can skip the post-processing step and act directly on structured audio metadata. Useful for meeting recap bots, call analysis, and anything that needs to know who said what.

**Integration:** REST API · **Homepage:** [AssemblyAI](https://assemblyai.com) · **Docs:** [https://www.assemblyai.com/docs](https://www.assemblyai.com/docs)

### Cartesia

State-space-model TTS with sub-100ms first-token latency and streaming voice synthesis.

> Sub-100ms first-token TTS, which is the latency floor for synthesis that feels like conversation instead of announcement. Sonic's voices are not quite as rich as ElevenLabs at the top end, but real-time agent interaction needs low latency more than it needs studio polish. When the alternative is waiting 600ms for the reply to start, Cartesia is the answer.

**Integration:** REST API · **Homepage:** [Cartesia](https://cartesia.ai) · **Docs:** [https://docs.cartesia.ai](https://docs.cartesia.ai)

### Deepgram

Speech-to-text and text-to-speech APIs tuned for low latency and real-time agent pipelines.

> The STT pipeline that can actually keep up with a live agent loop. Deepgram Nova is accurate enough for real transcripts, fast enough for streaming, and the pricing is sensible at volume. Agents wiring voice interfaces reach for Deepgram because the round-trip budget is already tight and they cannot afford to spend it on a slow ASR.

**Integration:** REST API · **Homepage:** [Deepgram](https://deepgram.com) · **Docs:** [https://developers.deepgram.com](https://developers.deepgram.com)

### ElevenLabs

High-fidelity voice synthesis with voice cloning, streaming TTS, and a conversational agent API.

> The voice synthesis most humans cannot tell from a human. When an agent has to say something and the stakes are real (outbound call, read a report aloud, narrate a product experience), ElevenLabs is the default. The conversational API is the cleanest path to a voice agent that does not sound like a voice agent.

**Integration:** REST API · **Homepage:** [ElevenLabs](https://elevenlabs.io) · **Docs:** [https://elevenlabs.io/docs](https://elevenlabs.io/docs)

### TalkAPI

Mobile voice recording with a public REST API designed for AI agents to consume.

> Mobile voice recording with a REST API designed for agents to consume as input. Humans record on a phone; agents read the audio, the transcript, and structured metadata through a clean endpoint. The category is narrow because most voice recorders either have no API or export only raw audio files; TalkAPI is the counter-example built specifically for the agent-as-consumer case.

**Integration:** REST API · **Homepage:** [TalkAPI](https://talkapi.com)

---

## Web Search and Retrieval

### Crawlbeam

AI crawler visibility and repair layer for client-side rendered websites.

> Client-side-rendered sites are invisible to most AI crawlers, which means agents searching the web cannot find content that lives behind React or Vue. Crawlbeam diagnoses which crawlers actually see the page, quantifies the gap, and ships a repair layer. Narrow category and tight scope; only matters when a site renders with JavaScript, but when it does, nothing else built on top reaches agents until this works.

**Integration:** REST API · **Homepage:** [Crawlbeam](https://crawlbeam.com)

### Exa

Neural web search API designed for LLMs, with semantic matching, live-crawled content, and similarity queries.

> Exa indexed the web the way an agent wants to search it. Instead of matching keywords, it matches meaning, and the content it returns is the actual page text, not a search-result snippet. For a research agent pulling primary sources, Exa is the search layer that makes the rest of the pipeline work.

**Integration:** REST API · **Homepage:** [Exa](https://exa.ai) · **Docs:** [https://docs.exa.ai](https://docs.exa.ai)

### Firecrawl

Scrape any website into clean markdown or structured data with a single API call, including JS-rendered pages.

> The 'turn a URL into readable markdown' service that agents actually use. Firecrawl handles JavaScript rendering, rate limiting, and format conversion in one call. When the agent needs the content of a specific page and not a search result summary, this is the tool. Open source core; managed tier for when the crawl gets serious.

**Integration:** REST API · **Homepage:** [Firecrawl](https://firecrawl.dev) · **Docs:** [https://docs.firecrawl.dev](https://docs.firecrawl.dev) · **GitHub:** [https://github.com/mendableai/firecrawl](https://github.com/mendableai/firecrawl) · **Open source**

### Tavily

Search API built specifically for AI agents with grounded answers, source citations, and news search.

> Tavily is the search API that picks up the phone. Cleanest developer experience in the category, a free tier generous enough to build on, and the responses are shaped for agent consumption from the first byte. When a newer agent framework says 'add web search', the default is almost always Tavily.

**Integration:** REST API · **Homepage:** [Tavily](https://tavily.com) · **Docs:** [https://docs.tavily.com](https://docs.tavily.com)

---

## Contributing

Read [STANDARDS.md](./STANDARDS.md) for the inclusion criterion, then [CONTRIBUTING.md](./CONTRIBUTING.md) for the PR process. New entries are reviewed manually; the bar is sharp but the review is fast.

## License

The list itself (this README and STANDARDS.md) is published under CC BY 4.0. The tools listed carry their own licenses — see each entry’s homepage.
