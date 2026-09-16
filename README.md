# Math Coach

An agent skill that turns math help into tutoring, not a vending machine for answers. It's a
plain instruction file, not tied to any one product — it works with Claude, Codex, Gemini, or
any coding/chat agent that can load a skill or a system prompt from a file.

## Installation

```bash
npx skills add sugarforever/math-coach
```

This works with Claude Code, Codex, Gemini CLI, and any other agent whose skill/plugin system
can pull in a `SKILL.md`-style instruction file — it's plain markdown, no product-specific
syntax.

## What it is

Most AI math help optimizes for getting to the final answer fast. Math Coach does the
opposite: it treats every problem as a doorway into the theorem, notation, or trick hiding
inside it, and won't let the agent walk through that doorway without naming what's on the
other side.

It was built by studying real tutoring sessions — watching how a student actually drives an AI
tutor toward genuine understanding: pushing back the moment an explanation leans on something
unexplained, asking "teach me the basics" the moment a solution goes over their head, then
"I'm actually good, show me the deeper version" once it clicks, and demanding harder practice
once they've proven they can handle it. Math Coach encodes that back-and-forth as default
behavior, so it happens without the student having to fight for it turn by turn.

## Features

- **Reads the student first.** Builds a running picture of level and background from how a
  problem is phrased and how the conversation goes, and keeps adjusting it — without ever
  blocking on an intake questionnaire before it starts helping.
- **Solves with the lightest tools that work.** Leads with the elementary path a problem
  actually requires instead of the most elegant or advanced one, and only introduces heavier
  machinery when it's genuinely necessary — introducing it by name, not silently.
- **Names everything it leans on.** Every theorem, rule, or piece of notation a solution uses
  gets a plain-language gloss the first time it appears, whether or not it's asked for.
- **Downshifts to concrete analogies on the first sign of confusion** — a road speed limit for
  a Lipschitz bound, a looping race track for modular arithmetic — instead of just repeating
  the same argument more slowly.
- **Bridges upward on request**, connecting a "give me the college-level version" ask to
  something the student already accepts as true, instead of dropping a wall of new notation.
- **Chases vocabulary and history tangents in full** — pronunciation, notation, who discovered
  what and why — because that curiosity *is* the learning, not a detour from it.
- **Draws the actual picture** for geometry, coordinate, function, and periodic/modular
  problems instead of describing points and regions in prose.
- **Calibrates practice to demonstrated skill.** If a practice problem was too easy, the next
  one mirrors the real structure of the original hard problem instead of nudging difficulty up
  one notch.
- **Always ends with a specific offer** — practice problems, a related idea to explore — never
  a bare answer or a generic "let me know if you have questions."

## Who it's for

Secondary school students (and anyone self-studying math) who want to actually understand
what they're solving — whether that's regular homework or exam prep for AMC, AIME, math
Olympiads, GCSE, A-level, IB, or the SAT. Also useful for parents or tutors who want to set up
an AI agent as a coaching partner for a student, rather than an answer key.

## How to use it

Just bring a math problem the way you normally would — paste it, describe it in your own
words, or ask about a concept directly. The skill activates automatically; you don't need to
invoke it by name.

Examples of what to say:

- *"Show me the solution"* (paste a problem) — you'll get a solution that also teaches you
  what makes it work.
- *"I don't understand this step"* — the explanation changes shape, it doesn't just repeat.
- *"Teach me the basics of X first"* — the agent backs up and builds the foundation before
  returning to the original problem.
- *"I'm actually good, give me the deeper explanation"* — the agent goes further, bridging from
  something you already know.
- *"Give me some practice"* / *"that was too easy"* — the agent generates problems calibrated
  to what you've just shown you can do.
- *"What should I learn next?"* — the agent evaluates the conversation so far and gives you a
  concrete plan with real resources, not a generic syllabus.

## License

MIT — see [LICENSE](LICENSE).
