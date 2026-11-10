# RecommandPaper-skill

按课题研究阶段动态调整的科研文献发现与推荐 Skill。Skill 标识为 `research-literature-discovery`。

| 研究阶段 | 检索重点 | 交付 |
|---|---|---|
| 寻找课题 | 广泛主题、跨领域方法、代表作与新问题 | 方向地图与可验证的切入点 |
| 确定选题 | 关键前人工作、引用网络、支持与反证 | 选题边界矩阵 |
| 开题后/研究中期 | 新首发、预印本更新、竞争工作与方法线索 | 优先提醒、建议阅读、完整观察列表 |

## 安装与使用

将本仓库的 `research-literature-discovery/` 整个文件夹复制到你的 Skill 目录，例如 Codex 的 `~/.codex/skills/`（自定义 CODEX_HOME 时使用其 skills 子目录）。由支持 Skill 的 Agent 加载 [SKILL.md](research-literature-discovery/SKILL.md) 执行。

调用示例：

```text
使用 $research-literature-discovery。我正在寻找小样本分子预测的课题，
有化学基础、刚开始学机器学习。先帮我建立方向地图。
```

```text
使用 $research-literature-discovery。我的课题已开题，下面是研究假设和种子论文。
先做一次新进展检索，保留竞争工作、反证和弱相关的方法线索。
```

## 文件导航

- [完整工作流](research-literature-discovery/SKILL.md)
- [课题档案 JSON 模板](research-literature-discovery/assets/project-template.json)
- [检索、推荐分级与反馈](research-literature-discovery/references/retrieval-rules.md)
- [去重、版本追踪与持久状态](research-literature-discovery/references/state-and-versions.md)
- [工具、来源和定时执行依赖](research-literature-discovery/references/tools-and-scheduling.md)
- [统一输出格式](research-literature-discovery/references/output-format.md)
- 三阶段示例：[探索](research-literature-discovery/references/example-explore.md)、[选题](research-literature-discovery/references/example-define.md)、[追踪](research-literature-discovery/references/example-track.md)
- [示例真实文献卡及证据边界](research-literature-discovery/references/example-corpus.md)
- [行为验收场景](research-literature-discovery/references/acceptance.md)
- [本次验证范围](VALIDATION.md)

## 能力边界

这是由 Agent 执行的工作流，不是独立检索程序，不自带 API 密钥、付费数据库或后台服务。在线发现需可用检索/浏览工具；长期记录需持久存储；定时运行需另行配置真实调度能力。没有调度时单次执行，不声称持续监控。

示例使用真实可核验的历史论文，仅展示阶段差异，不是当前最新文献报告，也不声称已完成全面引文检索。推荐区分原文报告、作者解释和推断；未检索到不等于不存在或具有首创性。

用户的实际课题档案、假设、反馈和运行结果保存在仓库外的数据目录，不应随本公开仓库发布。
