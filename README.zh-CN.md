# independent-thinker（独立思考）

让 AI 在动手前先判断：你到底要什么、这事值不值得做、怎么算做完。

[English](README.md)

文件是标准 Agent Skills 结构（`SKILL.md` + `modes/`）。凡是读这个结构的 agent 都能装，不绑哪一家。

## 三个模式

| 模式 | 什么时候用 | 输出 |
|---|---|---|
| 对齐（默认） | 需求含糊，或者想听一句「值不值得做」 | 一句判断 + 四行：要什么 / 不做什么 / 怎么算完 / 我替你定的假设 |
| 决策辅助 | 已经倾向一个方案，想让人验一验 | 三把尺 → 带严重度和证据级的倒推式挑错 → 看价值 → 旁人一句 → 三选一结论 |
| 第一性原理 | 绕来绕去说不清本质 | 结果倒推 → 约束分硬软 → 逐层剖 → 最脆弱一层 → 关键变量 |

## 和同类项目有什么不同

多数「思考 skill」做的是模型库：把几十个心智模型各写成一个技能，用之前你得先知道该用哪个。这个只做三件事——判断该不该做、挑错挑到点子上、拆到本质。

三条硬约束：

1. 判断必须落地：做 / 不做 / 换个做法做，不许「看情况」
2. 每条问题标两样：严重度（翻车 / 返工 / 难看）和证据级（实测 > 文档 > 推理 > 推测），推测不许装成事实
3. 有退出条件，够了就停

## 安装

两种语言各一份，技能名相同，装一个就行。

中文：

```bash
git clone --depth 1 https://github.com/HbS66-pro/independent-thinker.git independent-thinker-src
rm -rf ~/.dsh/skills/independent-thinker
cp -r independent-thinker-src/zh ~/.dsh/skills/independent-thinker
```

English:

```bash
git clone --depth 1 https://github.com/HbS66-pro/independent-thinker.git independent-thinker-src
rm -rf ~/.dsh/skills/independent-thinker
cp -r independent-thinker-src/en ~/.dsh/skills/independent-thinker
```

三条命令都不能省。目录名要和技能名一致，所以不能直接 clone 进技能目录。先删是因为往已经存在的目录上拷，新的会被套进旧目录里，加载的还是旧文件。源码那份用完可以删掉。

路径按 `~/.dsh/skills/` 写；换别的 agent 就换成它自己的技能目录。Windows 上是 `%USERPROFILE%\.dsh\skills\`，后两条换成 `Remove-Item -Recurse -Force` 和 `Copy-Item -Recurse`。

## 用法

说人话就行：

- 「你先想想这事值不值得做」→ 对齐
- 「唱反调，挑挑毛病」→ 决策辅助
- 「拆到底，本质是什么」→ 第一性原理

不说触发词也行，需求含糊时走默认的对齐模式。纯执行指令（复制、改格式、查数）不触发。

## 输出长什么样

问「这个 skill 该不该开源」，决策辅助的压缩版：

```
[翻车·3] 没有 LICENSE → 默认保留所有权利，别人不能合法用 → 先加 MIT
[返工·2] 没有示例输出 → 装完不知道「结构感」长什么样 → 贴一段真实输出
[难看·2] 名字太泛，搜 thinking 搜不到 → 仓库名统一叫 independent-thinker

成立前提：真有人愿意在开工前先判断。在「团队要统一判断口径」这个条件下，价值是让争论从措辞回到结构。

旁人看：它卖的不是思考，是把判断钉在固定位置上的仪式。真有用的话，你会发现自己开会时先问「这事可逆吗」。失败成本就是一次 push。

下限：最坏三天白干，能退。
结论：可逆、无致命项 → 做，先补 LICENSE 和示例。
```

方括号前半是严重度（翻车 / 返工 / 难看），后半是证据级（1 实测、2 文档、3 推理、4 推测）。一条问题压成一行，是硬要求。

## 结构

```
en/    英文版：SKILL.md、modes/decide.md、modes/first-principles.md
zh/    中文版，结构相同
```

对齐模式内联在 `SKILL.md` 里，因为它是默认路径、每次都用；另外两个是冷路径，拆出去省上下文。两份是互译，不是两个分支；改规则两边都要改。

## 参考与致谢

没抄任何文本。三模式结构、输出模板、标签格式是这个项目自己的。借的只有几个习惯：约束分硬软、结论标证据级、退出条件写成能被检验的一句话。这类做法在 [cc-thinking-skills](https://github.com/tjboudreaux/cc-thinking-skills)、[growth](https://github.com/zhu1090093659/growth)、[thinking-partner](https://github.com/mattnowdev/thinking-partner) 这些公开项目里都能看到，说到底也是决策里的常识。

几个名词另有出处：pre-mortem 来自 Gary Klein 的 prospective hindsight；可逆性和机会成本是决策理论；第一性原理追到亚里士多德；XY Problem 是社区说法。

## License

MIT
