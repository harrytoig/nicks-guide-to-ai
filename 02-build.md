# Build

*Nine real projects, sorted so each one teaches something the next depends on.*

This is the most important chapter. Theory is table stakes. Podcasts are background radiation. **Projects are the thing.**

If you do nothing else in this guide, do this ladder. By rung 7 you can hold a coherent technical conversation with anyone hiring for an AIOM, Forward Deployed Engineer, Applied AI Engineer, Customer Engineer, or AI PM role.

---

## The Rule

Ship every project publicly. GitHub repo, 90-second Loom, LinkedIn post. The artifacts ARE your portfolio. A resume with "interested in AI" is worth nothing. A GitHub profile with nine shipped AI projects is worth a job.

---

## The Ladder

### 1. Automate one annoying task with Claude Code
**Difficulty 1. 2-4 hours.**

Pick one friction point you actually hate: inbox triage, meal planning from fridge photos, weekly calendar summary, workout logging, expense categorization. Install Claude Code, describe the task in plain English, iterate until it works.

**Teaches:** how agents behave, why context matters, prompts as specifications. This is the easiest entry point and also a preview of how you'll spend your days as an AIOM.

### 2. Build a chatbot with the Claude API
**Difficulty 1. One weekend.**

Single-file Python script that hits the Claude API with a system prompt (a persona: your future-self therapist, an investing buddy, a writing coach). Use the [Anthropic quickstart](https://docs.claude.com/en/docs/get-started).

**Teaches:** API calls, tokens, system vs. user messages. Removes the abstraction so you see what's actually happening behind every agent builder.

### 3. RAG over your own notes
**Difficulty 2. One weekend.**

Start easy: drag your journal, Notion export, or Obsidian vault into Claude Projects and chat with it. Then rebuild from scratch with LlamaIndex or the [Anthropic RAG cookbook](https://platform.claude.com/cookbook/capabilities-retrieval-augmented-generation-guide).

**Teaches:** embeddings, chunking, and the truth that retrieval quality is the whole ballgame. You need to be able to explain RAG to a non-technical stakeholder in 90 seconds. Build one, and you can.

### 4. Build a tool-use agent
**Difficulty 2. One week.**

Claude with the tool_use API. A bot that reads your calendar, checks the weather, and texts you a day plan. Or a finance agent that reads Plaid transactions and yells at you about your grocery bill.

**Teaches:** function calling, agent loops, and (most importantly) why agents fail. Ambiguous tools, bad state handling, retry strategies, and when to have the agent ask a human. This is the meat of the AIOM job.

### 5. Install MCP servers and write a custom one
**Difficulty 2. A few hours.**

Install two or three MCP servers in Claude Desktop: Gmail, Google Calendar, Plaid, GitHub. Then write a tiny custom MCP server using [Anthropic's Python template](https://modelcontextprotocol.io/quickstart/server). Fifty lines. Point Claude at something weird in your life (your Oura data, your Spotify history, whatever).

**Teaches:** what MCP actually is and why it's the direction the industry is going. Every serious AI tool is gaining MCP support in 2026. Understanding this primitive is table stakes now and will be a floor in six months.

### 6. Build an agent on a no-code platform
**Difficulty 1. 2-4 hours.**

Glean Agent Builder if you're at a Glean customer. Otherwise: [Dify](https://dify.ai/), [Flowise](https://flowiseai.com/), [LangFlow](https://langflow.org/), or n8n's AI nodes. Build a three-step agent with retrieval, an LLM step, and a tool call.

**Teaches:** what "building an agent" looks like when the platform abstracts the API. This is exactly what AIOMs do with customers all day. If you can ship one thing on a no-code platform, you can walk into any AIOM interview.

### 7. Write a simple eval for one of your agents
**Difficulty 3. Half a day.**

Pick an agent you already built. Write 10-20 test cases with expected outputs. Run them. Score pass/fail. Then change one thing in the prompt and score again.

**Teaches:** you cannot ship what you cannot measure. This is the skill that separates hobbyists from people who get hired. Glean's AIOM technical interview explicitly probes this. See Anthropic's [evaluation framework guide](https://docs.claude.com/en/docs/test-and-evaluate/define-success) for patterns.

### 8. Deploy a public chatbot with the Vercel AI SDK
**Difficulty 2. One weekend.**

Clone [vercel/chatbot](https://github.com/vercel/chatbot), customize, deploy to a public URL. Get 10 friends to use it. Watch the logs. Notice what breaks.

**Teaches:** streaming, React hooks, and (crucially) shipping to real users. The gap most tutorials skip. Your first "users" experience is worth more than any tutorial.

### 9. Make Claude Code your daily driver
**Difficulty 3. Ongoing.**

Custom slash commands. Rules files. Skills. MCPs for your own tools. Replace five manual workflows with Claude-Code-driven ones. Commit your setup to a repo.

**Teaches:** all of it. This is the project AIOM interviewers actually want to see. When you've internalized the primitives by living in them for 30 days, it shows. See [Claude Code](./03-claude-code.md) for the setup.

---

## Optional Depth (for the curious, not AIOM-core)

- **Karpathy's makemore + nanoGPT** (Difficulty 4, 1-2 weeks). Watch [Zero to Hero](https://karpathy.ai/zero-to-hero.html). Code along. Train a character-level model on your own writing. Non-negotiable if you're going for a research-adjacent role. Credibility-bank if you want engineers to take you seriously in AIOM interviews.
- **Fine-tune a small model** (Difficulty 3, one week). Export 500 of your emails. Fine-tune Gemma 3 or Phi-3 with [Hugging Face TRL](https://huggingface.co/blog/dvgodoy/fine-tuning-llm-hugging-face). Runs on Colab free tier. Teaches data quality beats model size.
- **Voice app: Whisper + Claude + ElevenLabs** (Difficulty 3, one week). Record, transcribe, reason, speak. A voice journal. Teaches multi-model pipelines.

---

## Ideas If You Want More

- Home-finance agent that categorizes Plaid transactions and flags weird spending.
- "What did I do this week" agent that summarizes your git commits, calendar, and journal.
- Personal health tracker that ingests Oura data, lab results, and meal photos.
- Slack bot that reads your team's channels and drafts a weekly digest.
- GitHub-reading agent that writes a proper README for any repo you point it at.
- Agent that watches your Gong / Granola transcripts and drafts follow-up emails.

If the idea excites you and there's a small unknown in the middle, it's the right project.

---

## One Rule Before You Start

Pick the smallest version you can actually finish this week. **Shipped and ugly beats unshipped and beautiful.** You learn 10x more from one deployed project than from three half-built ones. Set a 72-hour timer and go.

---

## After You Ship

1. Push to GitHub with a README that explains what it does, why, and what broke.
2. Record a 90-second Loom demo.
3. Post on LinkedIn: what you built, what you were trying to learn, what surprised you.
4. Tweet it. Ethan Mollick, Simon Willison, and Alex Albert actually reply to people shipping good work. So does most of AI Twitter. Ship and they'll find you.

You are not trying to build the next ChatGPT. You are trying to prove to yourself and to future employers that you can ship. Both goals are served by getting one ugly thing out the door this week.
