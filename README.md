# independent-thinker

Make the agent judge before it acts: what you actually want, whether it's worth doing, and what "done" means.

[中文说明](README.zh-CN.md)

Built for DeepSeek Harness. The files use the standard Agent Skills layout (`SKILL.md` plus `modes/`), so any agent that reads that layout can load them too.

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

Pick one language build. Both declare the same skill name, so install one, not both.

English:

```bash
git clone --depth 1 https://github.com/HbS66-pro/independent-thinker.git /tmp/it
cp -r /tmp/it/en ~/.dsh/skills/independent-thinker
```

中文:

```bash
git clone --depth 1 https://github.com/HbS66-pro/independent-thinker.git /tmp/it
cp -r /tmp/it/zh ~/.dsh/skills/independent-thinker
```

The folder name has to match the skill name, which is why there is a copy step instead of a plain clone. On Windows the skills folder is `%USERPROFILE%\.dsh\skills\`: copy the `en` or `zh` folder there and name it `independent-thinker`.

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
en/    English build: SKILL.md, modes/decide.md, modes/first-principles.md
zh/    Chinese build, same structure
```

Align sits inline in `SKILL.md` because it's the default path and runs every time. The other two are cold paths, kept in separate files to keep the entry small. The two builds are translations of each other, not forks; if you change a rule, change it in both.

## Credits

Methods borrowed from a few MIT-licensed projects. No text was copied.

- [cc-thinking-skills](https://github.com/tjboudreaux/cc-thinking-skills): constraint classes, evidence levels
- [growth](https://github.com/zhu1090093659/growth): exit conditions defined by what the user can say afterwards
- [thinking-partner](https://github.com/mattnowdev/thinking-partner): splitting a large catalog into `references/`

On the methods themselves: pre-mortem comes from Gary Klein's prospective hindsight. Reversibility and opportunity cost are standard decision theory. First-principles thinking goes back to Aristotle. The XY problem is community shorthand for asking about the wrong thing.

## License

MIT
