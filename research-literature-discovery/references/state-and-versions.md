# 持久状态与版本

复制 `assets/project-template.json` 至用户数据目录 `<project_id>/profile.json`。只填已知信息；未知保留 null/空数组。标识稳定、名称可变。provenance 区分 user、supplied_document、inferred，附时间和依据。修改前读取最新 revision，临时文件写入后原子替换；并发冲突重读合并，不覆盖新反馈。

每课题 UTF-8 文件：

- `papers.jsonl`：每行一个工作，含全部版本与课题关联。
- `runs.jsonl`：追加 run_id、profile_revision、起止时间/时区、实际查询、来源、日期字段/窗口、分页、真实计数、失败、停止原因和产物路径。
- `feedback.jsonl`：追加 work_id、version_id、课题、反馈类型、原因、时间、调整措施。
- `reports/<run_id>.md` 和 `observations/<run_id>.md`：报告与完整观察清单；可合为一个文件，但必须有可浏览载体。

跨对话从实际文件恢复，不能假定记忆完整；无法写文件就输出状态导出。

## 文献记录字段

工作：work_id、title、authors、year、source、paper_type、canonical_url、identifiers、first_public_date（精度/来源）、first_seen_at、versions、relations、project_assessments。

版本：version_id、url、status（preprint/accepted/published/corrected/retracted/unknown）、posted_at、updated_at、checked_at、evidence_level（full_text/abstract/metadata/snippet）、evidence_locator、reported_findings、author_interpretation、agent_inference、change_summary、change_verified、last_notified_at。

课题关联：project_id、profile_revision、matched_axes、specific_connection、conditions_match、evidence_role（support/limitation/contradiction/competitor/transferable/background，多选）、priority、verification_needed、recommended_action、disposition、reason。未知字段不靠推断补全。

## 去重

1. DOI 移除 doi:/解析器前缀及首尾空白，统一小写；保留原值。arXiv 工作 ID 与 vN 分开，其他平台用稳定 ID。
2. 同 DOI/平台工作 ID 合并重复。预印本与期刊 DOI 不同不等于两个工作。
3. 跨平台优先用明确版本关联，再核对作者、题名、数据和方法。模糊题名只能生成待核对对，不能自动合并。
4. 确认同一工作才共享 work_id，保留合并依据与全部标识；不确定用 possible_same_work。范围/数据不同的续作独立保存并关联。
5. 勘误、撤稿、评论与回复保留独立事件/工作，用 corrects/retracts/comments_on 关联，不能当重复吞掉。

## 时间、更新与水位

first_public_date 是已核验版本中最早公开日期，不能保证不存在更早版本。引用年份、工作首发、online first、卷期日期分开；索引/发现时间不作发表日期。

同工作默认不重复推荐。纯排版/卷期变化更新元数据；预印本转正式版可汇总标状态变更。数据、条件、方法、机制或结论变化及更正/撤稿触发核查；比较过两个版本才写具体变化。只知版本号变化则写“检测到更新，实质变化待核验”，不能宣称结论改变。

使用 `(project_id, work_id, version_id, notification_kind)` 防重复，失败只补未完成动作。fetched、processed、delivered 分开。各来源仅在本轮范围处理并持久化成功后推进水位；失败/分页截断保存未完成范围，下次从原水位补查。其他来源可独立推进。
