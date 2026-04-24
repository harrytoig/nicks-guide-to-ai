# Heart of Gold

> *"The ship hung in the sky in much the same way that bricks don't."*
> - Douglas Adams

The Heart of Gold is the ship in Hitchhiker's that runs on the Infinite Improbability Drive. It goes places that by any reasonable measure shouldn't be reachable. That is what you are trying to build: something that shouldn't quite work but does.

This is the most important chapter in the guide. Theory is table stakes. Podcasts are background radiation. **Projects are the thing.**

---

## The Rule

Ship every project publicly. GitHub repo, 90-second Loom, LinkedIn post. The artifacts ARE your portfolio. A resume with "interested in AI" is worth nothing. A GitHub profile with ten shipped AI projects is worth a job.

---

## The Ladder

Ten rungs, zero-code to ambitious. Do at least five. If you do all ten, you are hireable.

### 1. Automate one annoying task with Claude Code
**Difficulty 1. 2-4 hours.**

Pick one friction point: inbox triage, meal planning from fridge photos, weekly calendar summary, logging your workouts. Install Claude Code, describe the task in plain English, iterate until it works.

**Teaches:** How agents actually behave. Why context matters. Prompts as specifications.

### 2. Chatbot with the Claude API
**Difficulty 1. One weekend.**

Single-file Python script that hits the Claude API with a persona (your dad's voice, a future-self therapist, an investing buddy). [Anthropic quickstart](https://docs.claude.com/en/docs/get-started).

**Teaches:** API calls, tokens, system vs. user messages.

### 3. Automate a real workflow in n8n or Make.com
**Difficulty 1. One weekend.**

Pattern: new Gmail arrives, Claude classifies it, auto-label plus draft reply. Deploy on n8n's free tier. [n8n AI tutorial](https://docs.n8n.io/advanced-ai/intro-tutorial/).

**Teaches:** Plumbing, webhooks, and why 80% of so-called "AI products" are really workflows.

### 4. RAG over your own notes
**Difficulty 2. One weekend.**

Start easy: drag your journal or Obsidian vault into Claude Projects, chat with it. Then rebuild from scratch with LlamaIndex or the [Anthropic RAG cookbook](https://platform.claude.com/cookbook/capabilities-retrieval-augmented-generation-guide).

**Teaches:** Embeddings, chunking, and why retrieval quality is the whole ballgame.

### 5. Tool-use agent that does something real
**Difficulty 2. One week.**

Claude with the tool-use API. A bot that reads your calendar, checks the weather, and texts you a day plan. Or a finance agent that reads Plaid transactions and yells at you about your grocery bill.

**Teaches:** Function calling, agent loops, and why agents fail (ambiguous tools, bad state handling).

### 6. Deploy a public chatbot with Vercel AI SDK
**Difficulty 2. One weekend.**

Clone [vercel/chatbot](https://github.com/vercel/chatbot), customize it, deploy to a public URL. Get 10 friends to use it.

**Teaches:** Streaming, React hooks, and (crucially) shipping to real users. The gap most tutorials skip.

### 7. Voice app with Whisper + Claude + ElevenLabs
**Difficulty 3. One week.**

Record, transcribe, reason, speak. Build a voice journal that responds to you.

**Teaches:** Multi-model pipelines, latency tradeoffs, and the UX problems of voice.

### 8. Karpathy's makemore and nanoGPT
**Difficulty 4. One to two weeks.**

Watch [Neural Networks: Zero to Hero](https://karpathy.ai/zero-to-hero.html). Code along, don't just watch. Train a character-level model on your own texts.

**Teaches:** What is actually inside the box. Non-negotiable if you want to credibly talk to engineers.

### 9. Fine-tune a small model in your voice
**Difficulty 3. One week.**

Export 500 of your emails or journal entries. Fine-tune a small model (Gemma 3 270M, Phi-3 Mini) with [Hugging Face's TRL](https://huggingface.co/blog/dvgodoy/fine-tuning-llm-hugging-face). Runs on Colab's free tier.

**Teaches:** Data quality beats model size. When fine-tuning beats prompting.

### 10. Make Claude Code your daily driver
**Difficulty 3. Ongoing.**

Custom slash commands. Hooks. MCPs for your own tools. Replace five manual workflows with agent workflows. This is the project AIOM and Forward Deployed Engineer interviewers actually want to see. You have internalized the primitives by living in them.

**Teaches:** All of it. See [Marvin's Brain](./03-marvins-brain.md) for my setup.

---

## Ideas If You Want More

- Home-finance agent that categorizes Plaid transactions and flags weird spending.
- "What did I do this week" agent that summarizes your git commits, calendar, and journal.
- Personal health tracker that ingests Oura data, lab results, and meal photos.
- Slack bot that reads your team's channels and drafts a weekly digest.
- GitHub-reading agent that writes a proper README for any repo you point it at.

If the idea excites you and there's a small unknown in the middle, it's the right project.

---

## One Rule Before You Start

Pick the smallest version you can actually finish this week. **Shipped and ugly beats unshipped and beautiful.** You will learn 10x more from one deployed project than from three half-built ones. Set a 72-hour timer and go.

---

## After You Ship

1. Push to GitHub with a README that explains what it does, why, and what broke.
2. Record a 90-second Loom demo.
3. Post on LinkedIn: what you built, what you were trying to learn, what surprised you.
4. Tweet it at Simon Willison or Ethan Mollick. They actually reply to people shipping good work.

You are not trying to build the next ChatGPT. You are trying to prove to yourself and to future employers that you can ship. Both goals are served by getting one ugly thing out the door this week.
