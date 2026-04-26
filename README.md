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

**档位与上下文、模型能力要匹配，才能发挥最好效果：** 更高档位需要更大的有效上下文与更强的指令遵循、推理能力；**档位越高，规则与示范越全，通常消耗的 token 也越高。**

在多数严肃分析场景下，**推荐优先使用 Level 4 或 Levelmax**（二者在完整度与示范深度上更利于圆桌输出）。

| 目标 | 建议档位 |
|------|----------|
| 要省 token / 快答 | **Level 1** |
| 要稳定四人格、又不必超长上下文 | **Level 2** 或 **Level 3** |
| 要成长股等复杂案例、又不想上 max | **Level 4** |
| 要最全示范与「分歧百科」级规则 | **Levelmax**；建议 **只把 max 当作单一真源**，其余档位由自动化生成或手工裁剪得到 |

若使用 **本地自部署模型**，请根据实际上下文长度与能力选择合适档位；档位与模型不匹配时，效果会明显下降。

---

## 一般使用方法

1. **先挂载圆桌规则（Skill）**  
   在对话中 **@ 引用** 本仓库中你选定档位的 `roundtable-advisor-level*.md`（或按 Project Rules 已挂载），并说明意图，例如：「吸收这个 skill，一会我问你问题。」

2. **再结合你提供的材料做深度分析**  
   在已引用/已吸收圆桌规则的前提下，**@ 引用** 相关文件或你整理好的要点，例如：  
   「根据引用材料深度分析 [公司名]，分析它现在发生了什么、过去发生了什么，以及它的未来与投资建议。根据你的理解与网络信息，分析该公司的财务指标是否在同行业突出，竞争优势是明显还是落后。」

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
