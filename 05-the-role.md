# The Role

*What AIOMs actually do, and what skills you need to get there.*

You are not going to become an AI researcher at Anthropic without a PhD. Fine. The most valuable roles in AI right now are not research roles. They are the people who stand between a research lab and a paying customer: **Forward Deployed Engineers**, **Applied AI Engineers**, **Customer Engineers**, **AI Outcomes Managers**. They build prototypes against real customer data, run enablement, turn ambiguous pain into shippable agents, and feed what they learn back into the product.

These roles are aggressively gettable if you come from a non-technical background. And they're the ones that actually teach you the craft.

This chapter is what the job looks like.

---

## The North Star: AI Native

Glean's internal framework for AI fluency has three tiers. The hiring bar for AIOM is the top one.

- **AI Literate.** Uses ChatGPT competently. Writes decent prompts. Below the floor.
- **AI Proficient.** Has built agents. Uses Claude Code. Has workflows that measurably change their output.
- **AI Native.** Builds habitually. Architects workflows from scratch. Iterates prompts as craft. Debugs failure modes. Can't imagine working without these tools.

AI Native is not a credential. It is what you are after you have shipped enough things. You get there by building, not by reading about it.

---

## A Typical AIOM Week

A real week. Not polished. Representative.

- **Monday.** Build a campaign-brief-generator agent for a customer's marketing team that pulls from Snowflake. 90 minutes of use-case discovery, 90 of prompt iteration, 60 of testing.
- **Tuesday.** Roll out an agent champion program at a 3,000-person enterprise. Train 15 department leads to run their own workshops. Write a best-practices doc.
- **Wednesday.** Internal: help another AIOM unblock their customer. Post 500 words in #aiom-team on a technical pattern. Interview a candidate.
- **Thursday.** Executive briefing at a Fortune 500. Present the customer's agent portfolio, usage numbers, and 90-day plan. Schedule the next six weeks of work.
- **Friday.** Ship a new Claude Code skill to automate part of your own job. Run a 160-person webinar on prompt engineering. Log everything to your trackers.

You are a hybrid consultant / prompt engineer / product thinker. Scored on **adoption** (is the customer actually using it?) and **power agents** (are the agents still used weekly, months later?). Both metrics reward learn-by-doing. Neither rewards talk.

---

## The Skills That Matter

### Technical must-haves

- **Prompting as craft.** The structure that works: *Role → Task → Context → Reasoning → Output → Stop Condition*. Iteration, not one-shot.
- **Agent design.** Retrieval, grounding, guardrails, tool calling, multi-step flows.
- **RAG fundamentals.** You should be able to explain retrieval-augmented generation to a non-technical Sales Director in 90 seconds.
- **LLM fundamentals.** Context windows (a Glean agent gets 128K per run), reasoning vs. fast mode, evals, why models hallucinate.
- **MCP, Custom Actions, APIs.** Why you'd use one over the other. Webhooks, REST, OAuth basics.
- **JSON literacy.** Reading and editing configs.
- **Reading code.** You don't need to write Python from scratch. You do need to read it without flinching.

### Non-technical must-haves

- **Customer discovery.** Turn ambiguous pain into a shippable agent spec.
- **Change management at enterprise scale.** Champion frameworks, departmental rollouts.
- **Writing.** Briefings, runbooks, how-to guides customers actually use.
- **Enablement delivery.** Training 50-200 people without putting them to sleep.
- **Executive presence.**

### Personality filters

Hungry, curious, consultative. Candidates who "have something to show" because they built it for themselves, not for the interview. Low ego, high agency. Resilience with ambiguity. Candidates who drop off when asked to "build or present something" are self-selecting below the bar.

---

## How You Get There

The whole guide is the answer. A summary:

1. **Build in public.** Every project gets a GitHub repo, a 90-second Loom, and a LinkedIn post. Your visible work becomes the resume.
2. **Your cold outreach is a working demo.** Ship something on the target company's API. Record a 90-second walkthrough. Send it with one specific question. Reply rate is roughly 10x generic outreach.
3. **Pick a vertical and go deep.** Domain expertise plus AI fluency is rarer than either alone.
4. **Write.** A Substack with five posts of "here is what I built and what I learned" outperforms any polished resume.
5. **Skip the bootcamps.** The only thing Reforge or Refonte buys you that you can't get free is a cohort, which you can replicate with one Discord server.
6. **Treat the job search itself as a project.** Build an agent that finds roles, drafts tailored cover letters, and tracks applications. Show it to your interviewers.

---

## The Single Piece of Meta-Advice

The gap between "has shipped one real AI project" and "has shipped zero" is wider than any other credential in the industry right now. Closing that gap is a weekend of work. Go.
