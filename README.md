# socratic-learning

Learning verification through the **Socratic Method** — powered by AI, driven by your own thinking.

## The Problem

I maintain a [digital garden](https://github.com/PinkR1ver/my-digital-garden) (a personal wiki built with Quartz + Obsidian) with 380+ notes covering LLMs, signal processing, mathematics, physics, and more. Many of these notes were expanded with AI assistance — which creates a trap:

> **Writing a note with AI help ≠ understanding the material.**

I found myself staring at beautifully structured notes and wondering: *"Do I actually know this, or did I just organize information well?"*

## The Solution

A global skill for Claude Code and Codex:

- `quiz`: turns the agent into a Socratic learning partner.

Instead of asking the AI to *explain* concepts to me, `/quiz` does the opposite: the AI primarily **asks questions**, and I must answer from my own understanding. It probes deeper with each exchange, following a 5-level depth progression:

```
Level 1: Basic Recall     — "Can you say it in your own words?"
Level 2: Relationships    — "How does X relate to Y?"
Level 3: Application      — "How would you use this in a new scenario?"
Level 4: Critical View    — "What are the limits? When does this fail?"
Level 5: Synthesis        — "What new thing can you create from these ideas?"
```

The AI stays in Socratic mode by default: it asks, tracks mastery across the core ideas, escalates misconceptions through focused prompts, and closes when understanding is demonstrated. If I explicitly leave Socratic mode, it can provide a concise correction before resuming.

## Usage

In Claude Code or Codex:

```
/quiz me on LoRA
test my understanding of scaling laws
check if I really know the Chinchilla paper
use the Socratic method on my antenna notes
```

The skill works with any source — local files, URLs, pasted text, or just a topic name. The agent proactively hunts down the material and begins questioning.

### Example Session

```
User: /quiz me on LoRA

AI: I've read your LoRA notes. Let's explore this together.
    To start — what problem does LoRA solve that full 
    fine-tuning creates? In your own words.

User: Full fine-tuning needs gradients and optimizer states
      for all 7B parameters — that's ~84GB VRAM. LoRA 
      freezes the base model and only trains tiny adapter 
      matrices.

AI: Good. Now — LoRA makes a key assumption about the 
    weight update ΔW. What is that assumption, and why 
    is it reasonable?

User: It assumes ΔW is low-rank... because the intrinsic 
      dimension of task adaptation is much smaller than 
      the full parameter space.

AI: Interesting — "intrinsic dimension." If a 7B model only 
    needs to change a few hundred degrees of freedom to 
    learn a new task... what does that imply about how 
    knowledge is stored in the pretrained weights?

... (continues probing deeper, never giving answers)
```

## Why Socratic Rather Than Flashcards?

| Flashcards / Quizzes | Socratic Method |
|---|---|
| Test memorization | Test understanding |
| Right/wrong answers | Depth of reasoning |
| Fixed question set | Adaptive follow-ups |
| You vs. the test | Dialogue with a mentor |
| Surface-level recall | Exposes hidden gaps |

The Socratic method reveals *unknown unknowns* — the gaps you didn't even know you had.

## Installation

Paste this into Claude Code or Codex — the agent will install the quiz skill:

```
Install this as a global skill for both Claude Code and Codex:
https://raw.githubusercontent.com/PinkR1ver/socratic-learning/main/skills/quiz/SKILL.md
```

The agent reads the skill file, creates the right directories, and sets it up. No manual commands needed.

## Project Structure

```
socratic-learning/
├── README.md
└── skills/
    └── quiz/
        └── SKILL.md          # The Socratic questioning skill
```

## Prerequisites

- [Claude Code](https://claude.ai/code) or [Codex](https://github.com/openai/codex)
- A knowledge base to quiz yourself on (works with any markdown notes, not just the author's digital garden)
- No API key needed — the skill runs entirely within your existing AI agent

## Philosophy

> "I know that I know nothing."
> — Socrates

The goal is not to feel smart. The goal is to find the edges of your understanding — and then push them outward.

This is a method, not a tool. The skill file is just the prompt that keeps the AI in character. The real work happens in your mind, one question at a time.
