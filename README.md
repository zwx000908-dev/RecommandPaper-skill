# RecommandPaper-skill

把课题和手头的论文交给 AI，帮你找到值得继续读的文献。

## 思路灵感

一篇论文值不值得读，往往取决于手里正在做什么。同样一篇文章，有时能引出一个新想法，有时只是补充背景，也可能让人重新考虑已经采用的实验方案。

RecommandPaper-skill 想把这层判断带进文献推荐。搜索之前，先了解你已经知道什么、正在尝试什么、还有哪个问题没想清楚；拿到结果以后，再解释这篇文章为什么与你有关。

推荐也应该留一点余地。有些工作研究的对象不同，却用了可以借鉴的办法；有些结果与预期相反，反而值得仔细读。只追着熟悉的关键词找，很容易错过这些线索。

## 功能介绍

**沿着手头的线索继续找。** 可以从一个模糊的想法开始，也可以给出几篇论文、一段研究计划或一次失败的实验记录。Skill 会据此选择检索范围，沿参考文献、后续引用、相关团队和方法继续查找。

**把相关之处讲清楚。** 每篇推荐都会说明它研究了什么、采用什么方法，以及与你的工作有什么联系。必要时将几篇文章放在一起比较，帮助分辨已有结果、适用条件和仍待验证的想法。推荐附有原文链接，并标明依据来自全文还是摘要。

**留意会改变判断的信息。** 相近工作的出现、已有结论的修订，或者一种可能解决当前困难的方法，都值得单独提醒。联系较远的文章会放进观察列表，写明可借鉴之处，方便以后回看。

**接着上一次的进展工作。** 不同课题可以分别保存档案。改了研究思路、补了实验结果或遇到新的困难，更新描述后就能调整检索。收藏和忽略会影响推荐，但反面结果和竞争工作不会因此被自动排除。同一篇论文的预印本与正式版会合并，重要修改另作提示。

## 使用方法

将 `research-literature-discovery/` 文件夹放进所用 Agent 的 Skill 目录。以 Codex 为例，默认位置是 `~/.codex/skills/`；设置了 `CODEX_HOME` 时，使用其中的 `skills` 子目录。

安装后，直接说明眼前的需求。例如：

```text
使用 $research-literature-discovery。

我对小样本分子性质预测感兴趣，懂一些化学，机器学习刚开始学。
请找几条不同的研究线索，说明各自需要什么基础，以及可以先读哪些文章。
```

也可以从已有材料开始：

```text
使用 $research-literature-discovery。

下面是我的研究设想和最近读过的三篇论文。
请继续查找相关工作，重点比较它们已经解决的问题和我的设想。
如果存在相反结论，也一起列出来。
```

遇到具体困难时，把条件说清楚通常更有帮助：

```text
使用 $research-literature-discovery。

我的模型在随机划分的数据上表现不错，换一种划分方式后效果明显下降。
请找讨论这类现象的论文，也看看其他领域有没有可借鉴的评估方法。
每篇说明与这个问题的联系，并建议先读哪一部分。
```

不必先填一张完整的表。研究笔记、论文链接和已有对话都可以作为起点，需要补充的信息会随检索逐步明确。

检索需要 Agent 能联网，并拥有相应信息源的访问权限。希望定期收到更新时，还需要接入所在环境的定时任务；没有配置就按单次请求运行。课题档案请保存在自己的数据目录，未发表的设想和实验记录不要上传到本公开仓库。

<details>
<summary>查看示例和详细说明</summary>

示例使用同一研究方向的真实历史论文，展示不同需求下的推荐方式；它们不是当前最新文献报告。

- 示例：[拓展研究线索](research-literature-discovery/references/example-explore.md) · [比较已有工作](research-literature-discovery/references/example-define.md) · [筛选值得关注的变化](research-literature-discovery/references/example-track.md)
- [完整 Skill](research-literature-discovery/SKILL.md)与[课题档案模板](research-literature-discovery/assets/project-template.json)
- [检索、推荐与反馈规则](research-literature-discovery/references/retrieval-rules.md)
- [去重和版本记录](research-literature-discovery/references/state-and-versions.md)
- [信息源与定时任务接入](research-literature-discovery/references/tools-and-scheduling.md)
- [推荐内容格式](research-literature-discovery/references/output-format.md)与[示例文献来源](research-literature-discovery/references/example-corpus.md)
- [验收场景](research-literature-discovery/references/acceptance.md)与[已有验证](VALIDATION.md)

Skill 会区分论文报告的结果、作者的解释和由此作出的推测。预印本会标注评审状态，未找到相近文献也不能直接作为首创性的依据。仓库不附带 API 密钥、付费数据库权限或常驻后台服务。

</details>

## 致谢

感谢玻尔平台的 **Token-Plan** 支持。
