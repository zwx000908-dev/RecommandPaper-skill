# 示例共同文献卡

以下为真实文献的有限证据示例，核验日期 2026-11-10。为突出阶段差异，三个示例使用相同方向“小样本分子性质预测”。课题描述与研究资源是教学情境，不代表用户真实课题。论文卡是各示例的组成部分，通过编号引用；这是小型示例文献集，不是完整综述或最新追踪结果。

## P1：MoleculeNet: a benchmark for molecular machine learning

- 作者：Zhenqin Wu、Bharath Ramsundar、Evan N. Feinberg、Joseph Gomes、Caleb Geniesse、Aneesh S. Pappu、Karl Leswing、Vijay Pande。年份/来源：2018，Chemical Science。类型：基准研究；正式发表。
- [出版社](https://doi.org/10.1039/C7SC02664A)；[预印本与版本](https://arxiv.org/abs/1703.00564)。已核验最早公开：2017-03-02；预印本 v3：2018-10-26。正式版具体在线日期本示例未核验。
- 证据范围：摘要及书目信息。核心问题：分子学习缺少可比评测。方法：汇集数据、指标与多种表征/模型基线。作者报告：学习表征有优势，但小数据和不平衡任务存在困难。
- 作者解释：数据与物理表征影响方法选择；本示例未审核具体实验表格。
- Skill 推断/关联：帮助把“小样本性能”转为可比较问题，不能据此证明任一模型在用户数据上更好。行动：精读评测协议与目标数据集，确认适用条件。版本：预印本与正式版属于同一工作；未比较内容变化。

## P2：Analyzing Learned Molecular Representations for Property Prediction

- 作者：Kevin Yang、Kyle Swanson、Wengong Jin、Connor Coley、Philipp Eiden、Hua Gao、Angel Guzman-Perez、Timothy Hopper、Brian Kelley、Miriam Mathea、Andrew Palmer、Volker Settels、Tommi Jaakkola、Klavs Jensen、Regina Barzilay。年份/来源：2019，Journal of Chemical Information and Modeling。类型：方法与评测；正式发表。
- [出版社](https://doi.org/10.1021/acs.jcim.9b00237)；[预印本](https://arxiv.org/abs/1904.01561)。最早核验公开：2019-04-02；预印本 v5：2019-11-20；正式版 online 日期本示例未核验。
- 证据范围：摘要与书目信息。问题：学习表征与固定表征在分子预测中的表现如何比较。方法：图模型及公开/工业数据评测。作者报告模型在所测任务中与固定表征等方法相当或更优。
- 作者解释：这支持其方法的工业应用潜力；不能推出所有数据条件下普遍优越。
- Skill 关联：构成“使用图学习提升分子预测”设想的关键前人工作。行动：比较用户的任务、切分和基线，不能把更换模型名称当贡献。
- 版本注意：[相关勘误](https://doi.org/10.1021/acs.jcim.9b01076) 的存在已由出版社检索结果核对，但正文访问失败，具体更改和影响未知；精读前应补查。预印本与正式论文合并展示，勘误独立关联。

## P3：Graph Networks as a Universal Machine Learning Framework for Molecules and Crystals

- 作者：Chi Chen、Weike Ye、Yunxing Zuo、Chen Zheng、Shyue Ping Ong。年份/来源：2019 期刊 DOI 关联，Chemistry of Materials；[所读预印本](https://arxiv.org/abs/1812.05055)、[关联期刊入口](https://doi.org/10.1021/acs.chemmater.9b01294)。类型：方法研究。所读为预印本，该版本未经同行评审；关联正式版存在，正文未在示例中比较。
- 已核验最早公开：2018-12-12；v2：2019-02-28。证据范围：摘要与版本元数据。
- 问题：分子/晶体预测中的状态信息与数据限制。方法：MEGNet 图网络、全局状态输入、元素嵌入迁移。作者报告跨性质迁移能改善部分小数据晶体性质预测。
- 作者解释：元素嵌入包含周期性化学趋势。Skill 推断：迁移思路可能用于小样本分子任务，但晶体元素嵌入与分子活性不是同一任务；这一迁移尚未被本示例验证。
- 关联与行动：探索阶段比较迁移路线；研究中保留弱相关观察，先判断标签/表征兼容性，再考虑实验。未核对版本间实质变化。

## P4：Unraveling Key Elements Underlying Molecular Property Prediction: A Systematic Study

- 作者：Jianyuan Deng、Zhibo Yang、Hehe Wang、Iwao Ojima、Dimitris Samaras、Fusheng Wang。年份/来源：2022，arXiv。[论文与版本](https://arxiv.org/abs/2209.13492)。类型：系统比较研究。所读 v4 为预印本，该版本未经同行评审；本示例未确认正式版对应关系。
- 最早核验公开：2022-09-26；v4：2023-09-02。证据范围：v4 摘要及版本历史。
- 问题：何种因素影响分子预测比较。方法：多种表征/模型在分子数据集与不同规模条件下比较。作者报告学习表征在不少任务中优势有限，并指出数据规模与活性悬崖的影响。
- 作者解释：数据规模是学习表征发挥优势的重要因素。Skill 推断：对“图模型在小样本下一定优于固定指纹”的强假设构成限制线索，尚不是对用户数据的直接反证。
- 行动：精读可比子集与切分协议，保留强指纹基线并检查学习曲线。版本：只确认发生过更新，未比对 v3/v4 正文，不能断言新增了何种证据。
