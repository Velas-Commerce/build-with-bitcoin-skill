# Build with Bitcoin — Claude Skill

A Claude skill that helps founders, operators, and builders figure out where Bitcoin fits their project and what to build.

Describe your idea. Answer a few questions. Walk away with a personalised Bitcoin Project Brief.

Built by [Velas Commerce](https://velascommerce.com) · MIT License

---

## What it does

The skill guides you through a short discovery conversation (4–6 questions), identifies which of three Bitcoin building blocks fits your idea, and produces a brief covering:

- Which block fits your project and why
- 2–3 real-world examples of similar projects
- A recommended technology stack in plain language
- Key risks and considerations
- A clear next step

**The three blocks:**

| Block | What it means |
|---|---|
| **Use Bitcoin** | Add Bitcoin to an existing business — payments, rewards, or treasury. Minimal technical lift. |
| **Build on Bitcoin** | Build a new product using Bitcoin's infrastructure (Lightning, Taproot Assets, L402). Moderate–high complexity. |
| **Build with Bitcoin** | Bitcoin is the product — wallets, protocols, financial infrastructure, ecosystem tooling. |

---

## Install

### Option A — Claude Code (recommended for developers)

1. Clone or download this repo
2. Copy `SKILL.md` into your project's `.claude/skills/` directory:
   ```
   your-project/
     .claude/
       skills/
         SKILL.md
   ```
3. Open Claude Code in that project directory
4. Describe your idea — Claude will pick up the skill automatically

### Option B — Claude.ai Projects (no setup required)

1. Open [Claude.ai](https://claude.ai) and create a new Project
2. In the Project instructions, paste the full contents of `SKILL.md`
3. Start a new conversation in that Project and describe your idea

---

## Usage

Just describe what you're thinking about building. Claude will take it from there.

**Example prompts to get started:**
- "I run an e-commerce store and I want to accept Bitcoin payments"
- "I want to build a micropayment API for content creators"
- "I'm not sure what to build — I just know I want to use Bitcoin somehow"

---

## Project structure

```
build-with-bitcoin-skill/
  SKILL.md          — the skill (this is the product)
  README.md         — this file
  blocks/           — reference material per block (optional, for deeper context)
```

---

## Contributing

Pull requests welcome. If you find a Bitcoin project that should be in the examples, a tool that's missing from the stack recommendations, or a use case that isn't handled well — open an issue or send a PR.

---

## License

MIT — use it, fork it, share it.

---

*Built on the [Build with Bitcoin guide](https://velascommerce.com/build-with-bitcoin/) by Velas Commerce · San Juan, PR*
