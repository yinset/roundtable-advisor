# Roundtable Advisor · 圆桌投资顾问

**English:** A **Cursor AI Rules** pack that simulates a four-investor roundtable—Benjamin Graham, Philip Fisher, Charlie Munger, and Warren Buffett—for structured, multi-perspective equity and business analysis.

**中文：** 面向 **Cursor** 的规则与技能集合：在一次提问中，按固定顺序输出四位投资大师各自的框架、风格与可追溯原则编号，并支持多行业叠加与行业特化路由。

> **版本：** V1.1  
> **重要：** 本仓库为研究与学习辅助工具，**不构成投资建议**。输出仅供参考，投资决策请咨询持牌专业人士并自行承担风险。

---

## 亮点


| 能力         | 说明                                                                     |
| ---------- | ---------------------------------------------------------------------- |
| **四视角圆桌**  | 格雷厄姆 → 费雪 → 芒格 → 巴菲特；分歧与共识分区；原则编号（如 `[G-2]`、`[B-3]`）可追溯                |
| **行业特化**   | 8 份 `profession/` 叠加规则：银行、地产/REIT/基建、周期大宗、重资本制造、SaaS/平台、创新药、强监管、项目制订单等 |
| **主 Skill** | 根目录 `roundtable-advisor-skill.md` 为默认完整规则；`mini_version/` 仅作极端省 token 场景备用，**非特殊情况不建议使用**（见下文「仓库结构」说明）          |


---

## 仓库结构

> **关于 `mini_version/`：** 该目录为极简档位（L1～L4 mini），仅在上下文极度紧张、必须再压缩规则体积时使用。**一般情况下请直接使用根目录的 `roundtable-advisor-skill.md`**，不必叠加或改用 mini 版本，以免损失圆桌完整度与可追溯性。

> **关于年报与 Token：** 为最大化节省输入侧 token，建议先将公司**年度报告（PDF 等）转换为 Markdown**（可用 OCR、文档转换或专用工具），再投喂大模型。相对直接贴原始 PDF/大段复制，**通常可节约约 50%～80% 的 token 用量**（视版面、图表与冗余多少而定），且便于模型检索段落。且非常友好一些读取pdf效果不好的模型。

```
roundtable-advisorV1.2/
├── roundtable-advisor-skill.md    … 主 Skill（圆桌完整规则与原则库；默认使用本文件）
├── 提示词.txt                     … 一键分析用提示词模板（与 Skill、年报配合）
├── profession/                    … 行业特化（与主 Skill 按【行业特化路由】叠加）
│   ├── roundtable-advisor-banks.md
│   ├── roundtable-advisor-real-estate-reit-infra.md
│   ├── roundtable-advisor-cyclical-commodities.md
│   ├── roundtable-advisor-heavy-capex-manufacturing.md
│   ├── roundtable-advisor-saas-subscription-platforms.md
│   ├── roundtable-advisor-biotech-pharma-rnd.md
│   ├── roundtable-advisor-regulated-policy-exposed.md
│   └── roundtable-advisor-project-contract-backlog.md
├── mini_version/                  … 极简档位（非特殊情况不建议使用）
│   ├── roundtable-advisor-L1mini.md
│   ├── roundtable-advisor-L2mini.md
│   ├── roundtable-advisor-L3mini.md
│   └── roundtable-advisor-L4mini.md
├── 更新日志.txt
└── README.md
```

---

## 快速开始（Cursor）

1. **克隆或下载**本仓库到本地。
2. 在 Cursor 中打开项目。将 **`roundtable-advisor-skill.md`** 加入 **Project Rules**，或在与模型对话时用 **`@` 引用**该文件（与 `profession/` 中文件的用法一致，见 Skill 内说明）。
3. 触发分析时建议使用明确意图，例如：**「圆桌分析：……」**，避免日常闲聊中偶发触发（规则内已说明边界）。
4. **行业特化**：分析前由模型按 `profession/` 中各文件的激活条件判定；命中则叠加对应全文逻辑，可与主 Skill 并存。

主 Skill 与特化文件均在 YAML 头或文首包含 `description`，便于 Cursor 检索与按需应用。

---

## 推荐用法（最少输入）

以下文件一并引用即可运行一轮完整分析，**无需再写长提示或补充其他输入**（模型可按 Skill 与提示词自行组织输出）：

| 引用内容 | 说明 |
| -------- | ---- |
| **`roundtable-advisor-skill.md`** | 圆桌规则、原则编号、输出结构 |
| **`提示词.txt`** | 分析目标与输出要求（公司现状/历史/未来、同业对比、竞争优势等） |
| **相关公司年度报告 `.md`（建议 1～3 篇）** | 自行准备的 Markdown 年报；篇数按上下文与成本取舍 |

**可选补充：** 在对话中附上**当前股价**（或交易代码 + 时点），便于结合估值与市场信息讨论；不提供则仍可按年报与公开信息做基本面圆桌分析。

---

## 档位与 `mini_version`（可选）

本仓库以 **`roundtable-advisor-skill.md` 为单一主档**，不再在根目录拆分 level1～levelmax 多文件。

若设备或模型的**有效上下文极小**，可选用 `mini_version/` 中与需求接近的 `L*mini` 文件以压缩规则体积。**默认仍建议优先保证主 Skill**，仅在确有必要时使用 mini，并理解其可能删减示范与细则。

若使用 **本地自部署模型**，请根据实际上下文长度与指令遵循能力选择；规则体积与材料过长不匹配时，效果会明显下降。

---

## 一般使用方法（分步说明）

1. **挂载圆桌 Skill**  
   在对话中 **`@` 引用** `roundtable-advisor-skill.md`（或已通过 Project Rules 挂载），并说明意图，例如：「吸收这个 skill，按圆桌规则分析下面材料。」

2. **引用提示词与年报**  
   **`@` 引用** `提示词.txt`，以及你准备好的 **1～3 篇** 公司年度报告 **Markdown** 文件（文件名可自定，例如 `某某公司2024年度报告.md`）。

3. **可选**  
   补充当前股价、货币币种或分析截止日期，便于讨论估值与市场因素。

---

## 致谢与说明

- 行业特化等内容可能引用公开著作与框架（如各 `profession/` 文件内标注），用于表达投资讨论中的术语一致性，**不代表**任何机构或作者背书本仓库。

---

## 许可证

若未另行提供 `LICENSE` 文件，默认保留所有权利；发布前请自行添加你需要的开源或许可条款。

---

## Star 历史

若本仓库对你有帮助，欢迎 Star 与分享。问题与改进建议请通过 Issues 讨论（如已启用）。
