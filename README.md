# Roundtable Advisor · 圆桌投资顾问

**English:** A **Cursor Skill / Rules** pack that runs a four-investor roundtable—Benjamin Graham, Philip Fisher, Charlie Munger, and Warren Buffett—in a fixed order, with traceable principle tags (for example `[G-2]`, `[B-3]`), optional industry overlays, and four depth tiers.

**中文：** 面向 **Cursor** 的圆桌投资分析技能：一次提问中按 **格雷厄姆 → 费雪 → 芒格 → 巴菲特** 固定顺序输出四视角；原则编号可追溯；可按行业叠加 `profession/` 特化；按 **mini / lite / std / max** 四档控制体量与完整度。

> **版本脉络：** 见仓库根目录 `更新日志.txt`（当前技能档位体系为 **V1.3**：mini → lite → std → max）。  
> **重要：** 本仓库为研究与学习辅助工具，**不构成投资建议**。输出仅供参考；投资决策请咨询持牌专业人士并自行承担风险。

---

## 亮点

- **四视角圆桌**：四位全部作答；分歧与共识分区；`[G-x]` / `[F-x]` / `[M-x]` / `[B-x]` 原则编号可追溯。
- **行业特化**：`profession/` 下 8 份 `roundtable-advisor-*.md`，按主体行业/商业模式路由，可多项叠加（详见各主 skill 内的「行业特化路由」）。
- **四档主技能**：同一套圆桌逻辑，从省 token 到自包含 max，按场景选用；**max** 档结合 `origindata/` 做语录与原则溯源，token 占用明显高于 std。

---

## 仓库结构

```
roundtable-advisor-skill-L1mini.md   … 最省 token（mini）
roundtable-advisor-skill-L2lite.md   … 轻量完整度（lite）
roundtable-advisor-skill-L3std.md    … 标准完整 Skill（std）
roundtable-advisor-skill-L4max.md    … 自包含 max；依赖 origindata 溯源；profession 可选叠加

profession/                          … 行业特化（与主 skill 同级目录，由主文件路由叠加）
├── roundtable-advisor-banks.md
├── roundtable-advisor-real-estate-reit-infra.md
├── roundtable-advisor-cyclical-commodities.md
├── roundtable-advisor-heavy-capex-manufacturing.md
├── roundtable-advisor-saas-subscription-platforms.md
├── roundtable-advisor-biotech-pharma-rnd.md
├── roundtable-advisor-regulated-policy-exposed.md
└── roundtable-advisor-project-contract-backlog.md

origindata/                          … 各大师摘录/笔记类原始片段（max 档溯源用；扁平目录）
├── 格雷厄姆skill-1.txt
├── 费雪skill-*.txt、查理skill-*.txt、巴菲特skill-*.txt 等

更新日志.txt                         … 版本与档位变更说明
```

---

## 快速开始（Cursor）

1. **克隆或下载**本仓库到本地，在 Cursor 中打开。
2. 选定一档主技能：在对话里 **@ 引用** 对应的 `roundtable-advisor-skill-L*.md`，或按你的习惯将其加入 **Project Rules**。
3. 触发分析时建议使用明确意图，例如：**「圆桌分析：……」**；避免日常闲聊中偶发触发（各主文件内已约定激活边界）。
4. **行业特化**：由模型按主 skill 中的路由表判定；命中则须叠加对应 `profession/` 全文逻辑。
5. **使用 max 档**时：保证本仓库内 `origindata/` 可被读取，以便按 skill 约定做溯源；`profession/` 若不可得，按 `roundtable-advisor-skill-L4max.md` 内说明降级处理。

主 skill 与特化文件均带有可被 Cursor 检索的 **description**（部分文件 frontmatter 格式为 `description:` 或文档内 `## description`，以实际文件为准）。

---

## 如何选择档位（mini / lite / std / max）

更高档位通常需要更大的有效上下文与更强的指令遵循能力；**档位越高，规则与示范越全，token 消耗一般越高。**

| 目标 | 建议档位 |
|------|----------|
| 省 token、快速四视角 | **L1 mini** |
| 介于 mini 与 std 之间的平衡 | **L2 lite** |
| 常规严肃分析、完整 Skill | **L3 std** |
| 需要自包含执行 + `origindata` 溯源、最厚规则与示范 | **L4 max** |

若使用 **本地或上下文较小的模型**，请优先 **mini / lite**，避免截断导致圆桌结构不完整。

---

## 一般使用方法

1. **先挂载圆桌主 skill**  
   @ 引用选定档位的 `roundtable-advisor-skill-L*.md`，并说明意图（例如：先吸收 skill，再基于材料提问）。

2. **再结合材料做分析**  
   在已引用规则的前提下，@ 你的笔记、年报摘要、数据表等，并说明公司或标的与分析重点。

---

## 致谢与说明

- 行业与框架表述可能引用公开著作与通用投资术语，用于讨论一致性，**不代表**任何机构或人物背书本仓库。
- 历史迭代说明见 `更新日志.txt`。

---

## 许可证

若未另行提供 `LICENSE` 文件，默认保留所有权利；对外发布前请自行补充所需许可条款。
