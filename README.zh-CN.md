# independent-thinker（独立思考）

让 AI 在动手前先判断：你到底要什么、这事值不值得做、怎么算做完。

[English](README.md)

给 DeepSeek Harness 做的。文件是标准 Agent Skills 结构（`SKILL.md` + `modes/`），其他读这个结构的 agent 也能直接装。

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
git clone --depth 1 https://github.com/HbS66-pro/independent-thinker.git /tmp/it
cp -r /tmp/it/zh ~/.dsh/skills/independent-thinker
```

English:

```bash
git clone --depth 1 https://github.com/HbS66-pro/independent-thinker.git /tmp/it
cp -r /tmp/it/en ~/.dsh/skills/independent-thinker
```

目录名要和技能名一致，所以多一步拷贝，不能直接 clone 进去。Windows 上技能目录是 `%USERPROFILE%\.dsh\skills\`，把 `zh` 或 `en` 文件夹拷进去、改名成 `independent-thinker` 就行。

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

方法层面受这几个 MIT 项目启发，没有复制任何文本：

- [cc-thinking-skills](https://github.com/tjboudreaux/cc-thinking-skills)：约束分类、证据分级
- [growth](https://github.com/zhu1090093659/growth)：退出条件按「用户能说出什么」来定义
- [thinking-partner](https://github.com/mattnowdev/thinking-partner)：大目录放 `references/` 的分层做法

方法本身的出处：pre-mortem 源自 Gary Klein 的 prospective hindsight；可逆性、机会成本是决策理论常识；第一性原理可追到亚里士多德；XY Problem 是社区俗语。

## License

MIT
