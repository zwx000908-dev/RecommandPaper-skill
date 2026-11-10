# RecommandPaper-skill

根据研究问题、已有论文和实验线索检索文献，解释关联、比较证据，并记录值得跟进的新进展。

这是一个供 AI Agent 使用的科研文献推荐 Skill。给它一个问题、几篇论文或一段研究记录，就可以开始检索。搜索范围和阅读重点会随你提供的信息调整，一次请求也可以同时查背景、找方法、核对相反结果。

[查看 Skill](research-literature-discovery/SKILL.md) · [阅读示例](#推荐结果是什么样的) · [安装与使用](#使用方法)

## 思路灵感

读论文时，最有用的线索未必来自与课题名字最像的文章。研究对象不同的工作，可能提供一个可以借鉴的办法；一篇结论相反的论文，也可能帮助解释实验为什么没有达到预期。

RecommandPaper-skill 关注这些具体联系。它会结合你已经读过的材料、正在尝试的方法和遇到的困难，寻找下一批值得看的文献。推荐时说明相似之处，也说明条件差在哪里，让你判断这篇文章是否值得花时间。

## 功能介绍

可以从已有论文继续往下查。Skill 会利用参考文献、后续引用、相关团队和语义线索寻找关联工作；需要核对方法来源或已有结果时，关键旧论文也会保留。

可以围绕一个困难找办法。例如实验结果与预期不符、不同条件下结论不一致，或者某种分析手段不够用。检索会关注其他工作如何处理相似问题，并说明方法迁移到当前课题还需要哪些条件。

也可以关注新论文和已有工作的修改。直接相关的结果会优先提醒；联系较远但理由明确的文章会保留在观察列表。同一工作的预印本和正式发表版本合并记录，重要修订、勘误和撤稿另作提示。

需要反复使用时，可以为不同课题分别保存论文、研究问题、反馈和检索记录。补充实验结果或修改想法后，后续检索会据此调整。收藏与忽略用于改善推荐，可能影响判断的反证和竞争工作仍会保留。

## 推荐结果是什么样的

每篇推荐包含可核验的文献信息与链接、核心问题、主要方法、论文报告的发现，以及它与你的具体关联。还会建议下一步读哪里、比较什么，或为什么暂时留作观察。

内容相互关联时，会把几篇论文放在一起比较。只需要少量推荐时，就直接给出文献卡；不会每次都生成一套长报告。

推荐按用途标记为“优先提醒”“建议阅读”和“弱相关观察”，同时注明读到了全文还是只有摘要。论文结果、作者解释和进一步的推测会分开表述，预印本也会标明评审状态。

三份示例展示了不同请求下的写法：

- [从一个兴趣方向拓展阅读线索](research-literature-discovery/references/example-explore.md)
- [把研究设想与已有论文放在一起比较](research-literature-discovery/references/example-define.md)
- [围绕模型表现不稳定的问题查找证据和方法](research-literature-discovery/references/example-track.md)

示例以小样本分子性质预测为题，使用真实历史论文；你可以换成自己的问题。它们用于展示输出方式，不是当前最新文献报告。

## 使用方法

将仓库里的 `research-literature-discovery/` 整个文件夹放进所用 Agent 的 Skill 目录。以 Codex 为例，默认位置是 `~/.codex/skills/`；设置了 `CODEX_HOME` 时，使用其中的 `skills` 子目录。

安装后，直接说明你想查什么：

```text
使用 $research-literature-discovery。

下面是我的研究问题和最近读过的几篇论文。
帮我继续找相关工作，说明每篇与这个问题的联系。
重点看看有没有可借鉴的方法，以及与现有解释不一致的结果。
```

也可以给出具体困难：

```text
使用 $research-literature-discovery。

我的模型在随机划分的数据上表现不错，换一种划分方式后效果明显下降。
请找讨论这类现象的论文，比较它们的评估方法，并建议先读哪一部分。
```

已有课题记录时，可以继续追加材料：

```text
使用 $research-literature-discovery，继续上次保存的课题。

我补充了下面这些结果。请更新记录，查找相关的新论文，
也重新看看之前观察列表里有没有现在用得上的方法。
```

不用先填完整的表。有论文链接、笔记或问题描述就可以开始；只有缺少的信息会影响检索时，才需要补充。

### 运行条件

在线检索需要 Agent 能联网，并能访问所选信息源。保存课题和阅读记录需要持久文件目录。定期更新则需要另外接入可用的调度工具；未配置时按单次请求运行。

本仓库提供 Skill 指令、模板和示例，不附带 API 密钥、付费数据库权限或常驻后台服务。可用信息源和配置方式见 [工具与调度说明](research-literature-discovery/references/tools-and-scheduling.md)。

实际课题档案应保存在自己的数据目录。不要把未发表的设想、实验记录或访问凭证提交到这个公开仓库。

<details>
<summary>项目文件</summary>

| 文件 | 用途 |
|---|---|
| [SKILL.md](research-literature-discovery/SKILL.md) | Agent 执行检索与推荐的主指令 |
| [课题模板](research-literature-discovery/assets/project-template.json) | 保存问题、已有材料、反馈与检索设置 |
| [检索与推荐规则](research-literature-discovery/references/retrieval-rules.md) | 查询扩展、推荐分级和反馈处理 |
| [档案与版本规则](research-literature-discovery/references/state-and-versions.md) | 多课题记录、文献去重、版本变化及旧档案迁移 |
| [输出格式](research-literature-discovery/references/output-format.md) | 文献卡和推荐内容的基本要求 |
| [示例文献](research-literature-discovery/references/example-corpus.md) | 示例使用的真实来源与阅读依据 |
| [验收场景](research-literature-discovery/references/acceptance.md) | 检查遗漏、重复、证据不足和反馈等情况 |
| [验证记录](VALIDATION.md) | 已完成的检查与尚未验证的能力 |

没有检索到相近工作，只能说明本轮检索的结果，不能直接作为首创性依据。具体判断仍需结合原文与检索范围。

</details>

## 致谢

感谢玻尔平台的 **Token-Plan** 支持。

## 许可

本项目采用 [MIT License](LICENSE)。
