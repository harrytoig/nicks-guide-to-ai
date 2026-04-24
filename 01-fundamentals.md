# Fundamentals

*How LLMs actually work, in three tiers.*

A handful of hours with the right people will take you from "this is magic" to "okay, I see how this works."

This chapter is three tiers. **Do Tier 1 your first week.** Tier 2 over the next month if you want real intuition. Tier 3 is for when you're ready to build things that matter.

---

## Tier 1: Start Here (~4 hours)

Five pieces. Watch them in order. This is the minimum viable education.

1. **[Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g)**. Andrej Karpathy, 1 hour. The single best "what is an LLM" video ever made. Non-technical but substantive. Start here.
2. **[But what is a GPT? Visual intro to Transformers](https://www.youtube.com/watch?v=wjZofJX0v4M)**. 3Blue1Brown, ~27 min. Animated visualization of what's happening inside GPT. Zero code.
3. **[Attention in transformers, visually explained](https://www.youtube.com/watch?v=eMlx5fFNoYc)**. 3Blue1Brown, ~26 min. The clearest explanation of attention that exists. Watch right after #2.
4. **[Software Is Changing (Again)](https://www.youtube.com/watch?v=LCEmiRjPEtQ)**. Karpathy at YC AI Startup School, ~40 min. The "Software 1.0 → 2.0 → 3.0" framing. Essential mental model.
5. **[Dario Amodei on Lex Fridman](https://www.youtube.com/watch?v=ugvHCXCOmm4)**. ~5 hrs, skim. Anthropic's CEO on scaling, safety, and timelines. The Chris Olah interpretability segment is the highlight.

After Tier 1 you should be able to explain to a normal human: what a token is, the difference between pretraining and fine-tuning, and why "attention" matters. If you can't, rewatch #1.

---

## Tier 2: Go Deeper (~15-20 hours)

This is where you build actual intuition for how these things work.

- **"Deep Dive into LLMs like ChatGPT"**. Karpathy, 3.5 hours (Feb 2025). The full stack: pretraining, fine-tuning, RLHF, why hallucinations happen. Search his [YouTube channel](https://www.youtube.com/@AndrejKarpathy). Watch in one sitting with coffee.
- **[Neural Networks: Zero to Hero](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ)**. Karpathy, 7 videos, ~15 hours. Build neural nets from scratch: micrograd → makemore → nanoGPT. If I had to pick one playlist for the next decade, this is it.
- **[Let's build GPT, from scratch, in code, spelled out](https://www.youtube.com/watch?v=kCc8FmEb1nY)**. Karpathy, ~2 hours. If you only watch one Zero to Hero video, this is the one.
- **Karpathy x Dwarkesh Patel (Oct 2025)**. ~2.5 hours. "AGI is a decade away." The most honest conversation about AI capability limits right now. Find it on the [Dwarkesh Podcast](https://www.dwarkesh.com/podcast).
- **3Blue1Brown's Deep Learning Playlist (Chapters 1-4)**. ~2 hours. Watch before Zero to Hero if the math feels shaky.

---

## Tier 3: If You Want to Build

Hands-on. Do the exercises, don't just watch.

- **[Anthropic's Prompt Engineering Interactive Tutorial](https://github.com/anthropics/courses)**. Free. 9 chapters of Jupyter notebooks. Best free prompt engineering course that exists. Do every exercise.
- **[ChatGPT Prompt Engineering for Developers](https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/)**. Andrew Ng and Isa Fulford, ~1.5 hours, free. Minimal Python needed.
- **[LangChain for LLM Application Development](https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/)**. Harrison Chase + Ng, ~1 hour. Chains, memory, agents, RAG basics.
- **[Building Systems with the ChatGPT API](https://www.deeplearning.ai/short-courses/building-systems-with-chatgpt/)**. Ng and Fulford, ~1 hour. Multi-step LLM pipelines with moderation and evals.
- **[Practical Deep Learning for Coders](https://course.fast.ai/)**. Jeremy Howard, fast.ai. ~30 hours. Build-first pedagogy: you train a real model in lesson one and learn the theory after.
- **[Hugging Face LLM Course](https://huggingface.co/learn/llm-course)**. Free. Transformers, tokenizers, fine-tuning, deployment. The practitioner standard.
- **[Code w/ Claude: Prompting 101](https://www.youtube.com/watch?v=ysPbXH0LpIE)**. Anthropic applied-AI team, ~45 min. Real production prompting patterns.
- **Boris Cherny on Lenny's Podcast**. Head of Claude Code on what happens after coding is solved. Search "Boris Cherny Lenny's." Also find his Latent Space appearance.
- **[Simon Willison's "Things we learned about LLMs" talks](https://simonwillison.net/tags/my-talks/)**. The best running commentary on LLMs as a working tool.

---

## Suggested Path

- **Weekend 1:** Tier 1 in one sitting. 4 hours and a coffee.
- **Weeks 2-6:** Zero to Hero + Anthropic's Prompt Engineering tutorial in parallel. Two to three hours per weekend.
- **Month 3+:** fast.ai or Hugging Face, depending on whether you want to be a builder or a researcher.

---

## Skip for Now

- **Two Minute Papers**: good energy, thin substance.
- **Yannic Kilcher**: brilliant but assumes you read papers.
- **99% of "10x your productivity with AI" YouTube videos**: vibes, not information.
- **Anything from pre-2023 on practical LLMs**: the field has moved twice since.

---

## One Meta-Note

Theory (attention, transformers, training dynamics) ages well. Practical takes (which model is best, which tool to use) expire in 18 months. Calibrate your trust in a video by its release date. If you're watching something from 2022 about what Claude can do, you're reading yesterday's newspaper.
