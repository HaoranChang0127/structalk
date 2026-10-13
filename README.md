# StrucTalk｜有章

**让讨论有结构，让思路接得上。**

和 AI 讨论方案时，你需要的是一起想清楚，而不是收到一篇需要花十分钟阅读的报告。

StrucTalk 是一个面向多轮讨论的 Agent Skill：先列出议题目录，再逐项讨论；想法变了可以调整结构，旧结论依然有编号、有位置、有来路。

## 它怎么改变讨论

| 常见困扰 | StrucTalk 的约定 |
| --- | --- |
| 一问就收到一大段方案 | 每轮聚焦一个问题，结论先行 |
| 聊着聊着忘了整体方向 | 开始时给出简短议题表 |
| 改主意后旧结论找不到 | 固定编号，拆分和合并保留承接关系 |
| 看似达成共识，实际理解不同 | 关键分歧先用一句话复述澄清 |
| 文字难解释结构或变化 | 按需用表格、Mermaid 或可用的 Visualize 技能 |

## 一次讨论的样子

下面是示意，不是实测效果：

| 编号 | 问题 | 状态 | 结论／待解决点 |
| --- | --- | --- | --- |
| 01 | 我们真正想解决什么？ | 已确认 | 降低用户首次使用的理解成本 |
| 02 | 先改善哪个环节？ | 讨论中 | 比较引导页与操作提示 |
| 03 | 怎么验证有帮助？ | 待讨论 | 验证指标待定 |

**当前：02。** 我建议先改操作提示，因为它出现在用户真正卡住的时刻。引导页可能覆盖得更全，但用户未必记得住。你观察到的卡点主要发生在开始前，还是操作过程中？

如果随后发现 02 包含两个问题，可以保留 02，将子问题记为 02a、02b。切换讨论顺序也不必重新编号。

## 安装与使用

在带有 `skill-installer` 的 Codex 中发送：

```text
请使用 skill-installer，从 https://github.com/HaoranChang0127/structalk 安装 skills/structalk。
```

然后在新一轮对话中调用：

```text
请用 $structalk 和我讨论这个方案：先列讨论目录，再一次讨论一个问题。
```

手动安装时，将本仓库的 `skills/structalk` 文件夹复制到你的 Codex 技能目录，通常是 `~/.codex/skills/`，自定义环境则以实际 `CODEX_HOME` 为准。不要覆盖已有同名技能而不检查内容。

## 语言与边界

- 跟随用户使用中文或英文，不默认双语重复输出。
- 普通轮次中文约 150–250 字，英文约 100–160 词；这是阅读预算，必要信息不会为了字数被截断。
- 无需 API key、外部服务或额外写作技能即可进行文字讨论。
- 交互图需要宿主提供兼容的 Visualize 技能；仓库不包含该技能或其宿主运行时。不可用时使用文字、表格或 Mermaid。
- 适合设计、研究、学习和方案讨论。简单问答和直接执行任务不会被强行变成多轮讨论。
- 这是一组行为指引，不保证模型每次完全遵守，也不是自动跨聊天记忆。需要长期保存时，应将讨论记录写入获授权的文件。

## 致谢

简洁写作原则参考 [writing-clearly-and-concisely](https://github.com/obra/the-elements-of-style/tree/main/skills/writing-clearly-and-concisely)；分歧澄清参考 [brainstorming](https://github.com/obra/superpowers/tree/main/skills/brainstorming)。本项目对原则进行面向讨论场景的整合，不打包这些项目或 Visualize 的完整内容。

## English

**Give discussions structure. Keep ideas connected.**

StrucTalk is an instruction-based skill for focused design and research conversations. It starts with an editable agenda, keeps stable topic IDs, and discusses one issue per turn. Splits, merges and revised conclusions retain their history. Responses follow the user's language; optional visuals are used only when they reduce explanation effort.

Install `skills/structalk` with your skill installer, then invoke `$structalk`. Interactive visualization depends on a compatible host skill and is optional. The skill itself needs no API key or external service.
