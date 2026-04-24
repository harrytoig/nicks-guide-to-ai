# Fundamentals

*How LLMs work, what to learn first, and what to skip.*

You do not need to understand attention math to be dangerous at this job. You do need a working mental model of what a language model is, what it can and can't do, and how the primitives (prompts, context, tools, agents) fit together. That's what this chapter buys you.

---

## Core (watch these, ~5-6 hours)

These are the ones I'd watch first and the ones I re-watch.

1. **Andrej Karpathy, [Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g)** (1 hr). The single best "what is an LLM" video ever made. Non-technical but substantive. Start here.
2. **Andrej Karpathy, [Software Is Changing (Again)](https://www.youtube.com/watch?v=LCEmiRjPEtQ)** (40 min). The Software 1.0 → 2.0 → 3.0 framing. Essential mental model for where this is going.
3. **Andrej Karpathy, "Deep Dive into LLMs like ChatGPT"** (3.5 hr, Feb 2025). The full stack: pretraining, fine-tuning, RLHF, why hallucinations happen. Find it on [his YouTube channel](https://www.youtube.com/@AndrejKarpathy).
4. **Boris Cherny on Lenny's Podcast** (~90 min). Head of Claude Code on product philosophy. Watch this before you try to use Claude Code seriously. Also find his [Latent Space appearance](https://www.latent.space/p/claude-code) for the technical version.

---

## Do (hands-on training, ~5 hours)

Watching isn't enough. These are the tutorials you actually run.

1. **[Anthropic's Prompt Engineering Interactive Tutorial](https://github.com/anthropics/courses)** (free, 9 chapters of Jupyter notebooks, ~4 hr). The best free prompt engineering course that exists. Do every exercise. This is the single highest ROI thing on this page.
2. **[Code w/ Claude: Prompting 101](https://www.youtube.com/watch?v=ysPbXH0LpIE)** (Anthropic applied team, 45 min). Real production prompting patterns, not toy examples.
3. **Read the Claude docs.** Start with [Agents and Tool Use](https://docs.claude.com/en/docs/build-with-claude/tool-use/overview) and [Model Context Protocol](https://docs.claude.com/en/docs/agents-and-tools/mcp). Skim them now, come back when you're stuck.

---

## Optional Depth (for when the itch strikes)

Not required for the AIOM path. Worth it if you're curious.

- **Karpathy, [Let's build GPT from scratch](https://www.youtube.com/watch?v=kCc8FmEb1nY)** (2 hr). Codes GPT live. The highlight of his Zero to Hero series.
- **Karpathy, [Neural Networks: Zero to Hero](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ)** (7 videos, ~15 hr). Builds neural nets from scratch: micrograd → makemore → nanoGPT. If you want internals, this is the best playlist ever made.
- **3Blue1Brown, [But what is a GPT?](https://www.youtube.com/watch?v=wjZofJX0v4M)** and [Attention in transformers](https://www.youtube.com/watch?v=eMlx5fFNoYc) (~50 min together). Animated visual explainers of what's happening inside a transformer. The best "I'm not a math person but I want intuition" resource. Only pick these up if the architecture is nagging at you.
- **[Simon Willison's talks](https://simonwillison.net/tags/my-talks/)**. Running commentary on LLMs as a working tool. Watch his latest.

---

## Skip

Be ruthless about what you skip. The field moves fast enough that wrong-era resources cost you more than they teach.

- **LangChain courses.** AIOMs work on agent platforms (Glean, Dify, n8n, direct API). LangChain is a framework more than a mental model, and you won't use it day-to-day.
- **fast.ai Practical Deep Learning.** Great course, wrong audience. It's for people who want to be ML researchers or engineers, not AIOMs.
- **Hugging Face LLM Course.** Fine-tuning and deployment aren't AIOM-core. Come back here if you end up at an AI-native lab.
- **Lex Fridman AI episodes, mostly.** Occasional gems (Karpathy, Dario, Hassabis) but five-hour interviews are inefficient when Karpathy has a 1-hour explainer.
- **Anything from pre-2023 on practical LLMs.** The field has moved twice since. Theory (attention, transformers, training dynamics) ages well. Practical takes expire in 18 months.

---

## The Four-Week Path

- **Week 1.** Karpathy's Intro to LLMs + Software Is Changing + Anthropic's Prompt Engineering Tutorial (first 3 chapters). ~6 hrs.
- **Week 2.** Finish Anthropic Prompt Engineering + Code w/ Claude: Prompting 101 + read Claude Agents/Tool Use docs. ~5 hrs.
- **Week 3.** Karpathy's Deep Dive into LLMs like ChatGPT + Boris Cherny on Lenny's. ~5 hrs.
- **Week 4.** Start building. See [Build](./02-build.md). By now you know enough to be dangerous. The rest is reps.

You do not need to finish every video before you start building. In fact, you learn faster by building halfway through. The "do" section matters more than the "watch" section.
