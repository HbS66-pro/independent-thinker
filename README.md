# independent-thinker

Make the agent judge before it acts: what you actually want, whether it's worth doing, and what "done" means.

Install it into any tool that supports Agent Skills (Claude Code, Codex, Cursor, Gemini CLI). It doesn't do the work for you. It forces a judgment first, in a shape you can check: do it, don't do it, or do it another way.

## Three modes

| Mode | Use when | Output |
|---|---|---|
| Align (default) | The request is vague, or you want a verdict on whether it's worth doing | One-line verdict, then four lines: what you want / what is out of scope / done when / assumptions I made |
| Decision aid | You already lean toward something and want it tested | Three rulers, a pre-mortem tagged with severity and evidence, the case for it, one outsider note, a three-way verdict |
| First principles | The problem keeps going in circles | Work back from the result, sort constraints into hard and soft, find the layer that breaks first, name the key variable |

## Why another thinking skill

Most of them ship a library. A few dozen mental models, one skill each, and you need to know which one to reach for before any of them helps. This one does three things: judge whether to do it, find what is actually wrong with it, and take it apart down to the assumptions.

Three rules it doesn't break:

1. Every judgment lands on do / don't / do it differently. "It depends" isn't an answer.
2. Every problem carries two tags: severity (breaks / rework / ugly) and evidence (tested > documented > reasoned > guessed). A guess is labeled as a guess.
3. There is an exit condition. Once the shape is filled, it stops instead of generating more angles.

## Install

```bash
git clone https://github.com/HbS66-pro/independent-thinker.git ~/.claude/skills/independent-thinker
```

`SKILL.md` plus `modes/` is the standard layout. Other Agent Skills tools work the same way. No dependencies; it's plain markdown plus a YAML header.

The instructions inside are written in Chinese. The mechanics are language-independent; the wording is not.

## Usage

Plain language works:

- "Think about whether this is worth doing" → Align
- "Play devil's advocate" → Decision aid
- "Strip it to the first principles" → First principles

No trigger words needed. A vague request goes to Align by default. Plain execution ("copy this", "fix the format", "count these rows") doesn't trigger a mode.

## Sample output

A compressed decision-aid pass on "should this skill be open sourced":

```
[breaks·3] No LICENSE → default all rights reserved, nobody can legally use it → add MIT first
[rework·2] No sample output → people install it and still don't know what it looks like → paste a real one
[ugly·2] Generic name, doesn't surface for "thinking" → keep the repo name independent-thinker

Holds if people actually want to judge before acting. Within a team that argues in circles, the value is moving the argument from wording to structure.

Outsider: it sells a ritual more than thinking. If it works, you'll catch yourself asking "is this reversible" in meetings. Worst case is one wasted push.

Floor: three days lost, recoverable.
Verdict: reversible, nothing fatal → do it, but add LICENSE and the sample first.
```

Left of the dot is severity (breaks / rework / ugly), right of it is evidence (1 tested, 2 documented, 3 reasoned, 4 guessed). One line per problem is a hard rule.

## Layout

```
SKILL.md                    entry: triage, context, mode table, Align in full, self-checks, budget
modes/decide.md             decision aid
modes/first-principles.md   first principles
```

Align sits inline because it's the default path and runs every time. The other two are cold paths, kept in separate files to keep the entry small.

## Credits

Methods borrowed from a few MIT-licensed projects. No text was copied.

- [cc-thinking-skills](https://github.com/tjboudreaux/cc-thinking-skills): constraint classes, evidence levels
- [growth](https://github.com/zhu1090093659/growth): exit conditions defined by what the user can say afterwards
- [thinking-partner](https://github.com/mattnowdev/thinking-partner): splitting a large catalog into `references/`

On the methods themselves: pre-mortem comes from Gary Klein's prospective hindsight. Reversibility and opportunity cost are standard decision theory. First-principles thinking goes back to Aristotle. The XY problem is community shorthand for asking about the wrong thing.

## License

MIT
