# independent-thinker

Make the agent judge before it acts: what you actually want, whether it's worth doing, and what "done" means.

[中文说明](README.zh-CN.md)

The files use the standard Agent Skills layout: `SKILL.md` plus `modes/`. Any agent that reads that layout can load them. Nothing here is tied to one vendor.

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
git clone --depth 1 https://github.com/HbS66-pro/independent-thinker.git independent-thinker-src
rm -rf ~/.dsh/skills/independent-thinker
cp -r independent-thinker-src/en ~/.dsh/skills/independent-thinker
```

中文:

```bash
git clone --depth 1 https://github.com/HbS66-pro/independent-thinker.git independent-thinker-src
rm -rf ~/.dsh/skills/independent-thinker
cp -r independent-thinker-src/zh ~/.dsh/skills/independent-thinker
```

Three things in there are load-bearing. The folder name has to match the skill name, so this is not a plain clone into the skills folder. The remove step exists because copying onto a folder that already exists nests the new copy inside the old one, and the old files keep loading. The source clone is disposable; delete `independent-thinker-src` when you are done.

The paths assume `~/.dsh/skills/`; any other agent has its own skills folder, so swap the path. On Windows that is `%USERPROFILE%\.dsh\skills\`, and the last two commands become `Remove-Item -Recurse -Force` and `Copy-Item -Recurse`.

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

No text was copied from anywhere. The three-mode structure, the output templates and the tag format are this project's own. What is not: the habit of sorting constraints into hard and soft, tagging claims by evidence level, and writing exit conditions as something checkable. Those show up across public thinking skills — [cc-thinking-skills](https://github.com/tjboudreaux/cc-thinking-skills), [growth](https://github.com/zhu1090093659/growth), [thinking-partner](https://github.com/mattnowdev/thinking-partner) — and are mostly decision practice anyway.

The names have their own history: pre-mortem is Gary Klein's prospective hindsight, reversibility and opportunity cost are decision theory, first principles goes back to Aristotle, XY problem is community shorthand.

## License

MIT
