# Roundtable Advisor · 圆桌投资顾问

**English:** A **Cursor AI Rules** pack that simulates a four-investor roundtable—Benjamin Graham, Philip Fisher, Charlie Munger, and Warren Buffett—for structured, multi-perspective equity and business analysis.

**中文：** 面向 **Cursor** 的规则与技能集合：在一次提问中，按固定顺序输出四位投资大师各自的框架、风格与可追溯原则编号，并支持多行业叠加与不同「深度档位」。

> **版本：** V1.1  
> **重要：** 本仓库为研究与学习辅助工具，**不构成投资建议**。输出仅供参考，投资决策请咨询持牌专业人士并自行承担风险。

---

## 亮点

| 能力 | 说明 |
|------|------|
| **四视角圆桌** | 格雷厄姆 → 费雪 → 芒格 → 巴菲特；分歧与共识分区；原则编号（如 `[G-2]`、`[B-3]`）可追溯 |
| **行业特化** | 8 份 `profession/` 叠加规则：银行、地产/REIT/基建、周期大宗、重资本制造、SaaS/平台、创新药、强监管、项目制订单等 |
| **多档位主规则** | `level1`～`level4` 与 `levelmax`：上下文体量、规则完整度与 token 消耗不同，可按场景选用 |
| **可选 PDF 工作流** | 内置 Skill：将 PDF 年报转为 Markdown 再分析（见下文） |

---

## 仓库结构

```
├── roundtable-advisor-level1.md   … level1（最省 token）
├── roundtable-advisor-level2.md
├── roundtable-advisor-level3.md
├── roundtable-advisor-level4.md   … 推荐复杂成长股场景
├── roundtable-advisor-levelmax.md … 最全示范与分歧百科；可作单一真源
├── profession/                    … 行业特化（与主档同级路由叠加）
│   ├── roundtable-advisor-banks.md
│   ├── roundtable-advisor-real-estate-reit-infra.md
│   ├── roundtable-advisor-cyclical-commodities.md
│   ├── roundtable-advisor-heavy-capex-manufacturing.md
│   ├── roundtable-advisor-saas-subscription-platforms.md
│   ├── roundtable-advisor-biotech-pharma-rnd.md
│   ├── roundtable-advisor-regulated-policy-exposed.md
│   └── roundtable-advisor-project-contract-backlog.md
├── .cursor/skills/pdf-annual-report-to-md/  … 可选：PDF→MD 再阅读
└── README.txt                     … 档位与使用提示（精简版）
```

---

## 快速开始（Cursor）

1. **克隆或下载**本仓库到本地。
2. 在 Cursor 中打开项目，将希望使用的 **`roundtable-advisor-level*.md`** 加入 **Project Rules**（或按你习惯的 Rules 挂载方式引用）。
3. 触发分析时建议使用明确意图，例如：**「圆桌分析：……」**，避免日常闲聊中偶发触发（规则内已说明边界）。
4. **行业特化**：分析前由模型按 `profession/` 中各文件的激活条件判定；命中则叠加对应全文逻辑，可与主档并存。

主文件与特化文件均在 YAML 头中包含 `description`，便于 Cursor 检索与按需应用。

---

## 如何选择 Level

| 场景 | 建议档位 |
|------|----------|
| 省 token、要快 | **Level 1** |
| 稳定四人格、篇幅不必很长 | **Level 2** 或 **3** |
| 成长股等较复杂案例、又不想上 max | **Level 4** |
| 最全规则、语录与分歧示范 | **Levelmax**（建议作为「单一真源」，其余可由自动化或手工裁剪生成） |

自托管本地模型时，请使 **模型能力与上下文** 与所选 level 匹配，否则效果可能下降。

---

## 引用年报 / PDF

- 模型对 **纯 PDF** 的直接阅读可能不稳定；若使用本仓库自带的 **`pdf-annual-report-to-md`** Skill，可先转为 Markdown 再分析。
- 依赖与命令见：`.cursor/skills/pdf-annual-report-to-md/SKILL.md`。  
- 扫描版 PDF 需 OCR；文本层缺失时转换结果可能不可用。

**你本地一次性依赖**

在仓库根目录执行：

```bash
pip install -r .cursor/skills/pdf-annual-report-to-md/requirements.txt
```

之后引用 PDF 年报时，由 Agent 按 skill 调脚本即可；

---

## 致谢与说明

- 行业特化等内容可能引用公开著作与框架（如各 `profession/` 文件内标注），用于表达投资讨论中的术语一致性，**不代表**任何机构或作者背书本仓库。
- 历史迭代与评价样例见 `历史版本/`、`评价/`（可选读）。

---

## 许可证

若未另行提供 `LICENSE` 文件，默认保留所有权利；发布前请自行添加你需要的开源或许可条款。

---

## Star 历史

若本仓库对你有帮助，欢迎 Star 与分享。问题与改进建议请通过 Issues 讨论（如已启用）。
