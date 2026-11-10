# RecommandPaper-skill

根据课题进展，帮你找文献、理清选题，再跟进值得注意的新工作。

## 思路灵感

做科研时，不同阶段读文献的目的其实不一样。

还没确定课题时，希望多看看别人怎么提问题、怎么解决问题，偶尔也需要跳出熟悉的领域。等到有了具体想法，就要认真查清楚：前人已经做到了哪一步？自己的设想与他们究竟有什么不同？课题开始以后，关注点又会变化——有没有人做了相近的工作，有没有新方法能解决眼前的困难，原来的假设是否还站得住。

这个 Skill 就是围绕这些需求设计的。它会先了解课题处在哪个阶段，再调整搜索范围、时间窗口和推荐理由。希望每次看完推荐，都能更清楚接下来该读什么、查什么，或者验证什么。

## 功能介绍

### 找课题时，多看几条可能的路

从感兴趣的方向出发，同时寻找代表性研究、综述、新问题和其他领域可借鉴的方法。推荐会按研究思路整理，说明已有基础、主要困难和可能的切入点，方便比较几个候选方向。

例如，对“小样本分子性质预测”感兴趣，可以分别看看模型比较、数据与评测、跨任务迁移这些问题。文献中的结果和由此想到的研究设想会分开写。

### 确定选题时，把前人工作查清楚

围绕具体课题和种子论文，回溯参考文献、追踪后续引用，查找相近问题、类似机制和不同领域的相关方法。关键旧论文也会保留。

这一阶段重点解释：哪些部分已经有人解决，当前设想的差异在哪里，哪些判断有文献支持，哪些还需要验证。支持设想的论文、限制条件和反面结果都会纳入比较。

### 课题进行中，留意会影响研究的新进展

优先关注预印本、期刊在线首发和已有论文的更新。即使关键词不同，只要在问题、机制、中间体或方法上有具体联系，也会进入候选。

推荐分成三类：

- **优先提醒**：与课题直接重叠、可能挑战核心假设，或能解决关键困难。
- **建议阅读**：有助于改进实验设计、分析方法或结果解释。
- **弱相关观察**：暂时用不上，但有明确的相似思路或迁移可能，留在列表里供后续查看。

每篇都会附上文献信息、原文链接、主要内容、与课题的关联和建议行动，并注明依据是全文还是摘要。预印本会标明评审状态；同一工作的预印本和正式版会合并，重要修订另作提示。

也可以同时维护多个课题。确定了新方向、改了假设或遇到实验瓶颈，直接告诉它即可更新档案。收藏和忽略会用于调整推荐，但不会因为连续忽略某类论文，就自动屏蔽可能影响课题的反证或竞争工作。

## 使用方法

将仓库中的 `research-literature-discovery/` 文件夹复制到你的 Skill 目录。以 Codex 为例，默认位置是 `~/.codex/skills/`；自定义了 `CODEX_HOME` 时，放在对应的 `skills` 子目录。

然后在对话中调用：

```text
使用 $research-literature-discovery。我正在寻找小样本分子预测的课题，
有化学基础、刚开始学机器学习。先帮我建立方向地图。
```

已经有具体课题时，可以把设想和几篇代表性文献一起提供：

```text
使用 $research-literature-discovery。我想用图神经网络改善小样本分子性质预测。
下面是我的设想和两篇种子论文。帮我查清已有工作，看看差异是否成立。
```

研究进行到一半，也可以从眼前的问题开始：

```text
使用 $research-literature-discovery。我的课题已开题，下面是研究假设和种子论文。
先做一次新进展检索，保留竞争工作、反证和弱相关的方法线索。
```

不用一开始就填完所有信息。已有的课题描述、阅读笔记和论文都可以作为起点；缺少会影响检索的关键信息时，再逐步补充。

实际检索需要所用 Agent 能联网，并能访问相应信息源；课题档案需要可保存文件的位置。定期追踪还需接入所在环境的定时任务功能，没有配置时就按单次请求执行。本仓库不附带 API 密钥或付费数据库权限。

课题档案、未发表的研究设想和反馈记录请保存在自己的数据目录中，不要上传到这个公开仓库。

想先看推荐长什么样，可以打开三份示例：[寻找课题](research-literature-discovery/references/example-explore.md)、[确定选题](research-literature-discovery/references/example-define.md)、[研究中期](research-literature-discovery/references/example-track.md)。它们使用同一方向的真实历史论文展示区别，不代表当前最新检索结果。

<details>
<summary>文件与规则</summary>

- [完整 Skill](research-literature-discovery/SKILL.md)
- [课题档案模板](research-literature-discovery/assets/project-template.json)
- [检索、推荐分级与反馈规则](research-literature-discovery/references/retrieval-rules.md)
- [去重、版本追踪与档案保存](research-literature-discovery/references/state-and-versions.md)
- [信息源和定时任务接入](research-literature-discovery/references/tools-and-scheduling.md)
- [推荐内容格式](research-literature-discovery/references/output-format.md)
- [示例文献及依据](research-literature-discovery/references/example-corpus.md)
- [验收场景](research-literature-discovery/references/acceptance.md)
- [已有验证及尚未验证的部分](VALIDATION.md)

推荐会区分原文结果、作者解释和进一步推测。“没有检索到”也不等于没有人做过，选题的新颖性仍需要结合检索范围和原文判断。

</details>

## 致谢

感谢玻尔平台的 **Token-Plan** 支持。
