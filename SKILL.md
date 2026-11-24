---
name: paper-insight-template
description: "结构化、层次化的高密度红黑灰技术洞察 PPT 制作 skill，覆盖「Deck 宏观叙事规划 → Slide 页内逻辑与版式路由 → Component 原子组件装配」三层工作流，强调语言凝练、图文并茂、信息密度高。支持单页论文洞察模板与完整多页技术洞察/顶会综述/务虚会报告。"
---

# Paper Insight · 结构化技术洞察 PPT

将单篇论文或整套会议专题转化为**语言凝练、图文并茂、信息密度高**的红黑灰工程风格 PPT。采用「三层流水线 + 横切约束」架构，所有视觉样式均为厂商中性的红灰高对比工程体系。

## 三大核心质感原则（贯穿全流程）

1. **语言凝练**：删净铺垫、过渡词和套话，用「**3–8 字加粗引导词** + 精准因果/机制陈述（无末尾句号）」承载信息；平实通俗、禁用比喻与宣传词。
2. **图文并茂**：内容页每张主卡片必配至少 1 张高信息量视觉元素（原文架构/定量图、极简对比表或原生流程条），保持 **40%–55% 图表 + 45%–60% 文字**，图文互证不重复，每图配一行 `Fig. X  一句话中文结论` 图注。
3. **信息密度高**：善用 16:9 全画幅有效区（左右边距 `0.50 in`、`8.2–9.0 pt` 正文），一页完整承载 1 篇深度拆解或 2–3 篇横向对比；靠「判断句标题 → 顶部串联/KPI 条 → 细灰框多栏 → ①②③ 机制步骤 → 底部洞察启示条」建立秩序，拒绝大字号空洞海报风。

## 三层工作流（按顺序执行，按需加载参考文档）

### Layer 1 · Deck 级规划（宏观叙事与页间逻辑）
详见 `references/01-deck-planning.md`。

- 明确受众、1 句核心总命题与素材聚类。
- 选定叙事组织思路：总-分-总全景型 / 问题驱动递进型 / 横向选型对比型 / 单点深挖精读型。
- 输出整套大纲，**显式标注每页与上一页的逻辑关系**（总起、递进、并列、串联、收束），据此触发下一页的「承接条 / 拟串链路条」。

### Layer 2 · Slide 级规划（页内逻辑 → 版式路由与容量预算）
详见 `references/02-slide-layouts.md`。

- 每页先锁定 4 要素：`判断句主标题`、`页内逻辑类型`、`图文槽位`、`底部洞察启示`。
- 按「页内逻辑 → 8 类 16:9 标准页型」路由骨架（趋势词云、三层全景、章节红带、KPI+三栏、三栏因果流、双栏对比/串联、定义条+三栏正交、终页收束）。
- 规划期即落实图文面积比与字数预算；超限时按「删背景废话 → 压缩引导词 → 拆页」收敛，不把溢出留到渲染阶段。

### Layer 3 · Component 级装配（Design Tokens + 语义组件库）
详见 `references/03-component-library.md`。

- 遵循统一红灰 Design Tokens（`#FFFFFF` 白底、`#C00000` 主题红、`#1D1D1A` 炭黑正文、`#525252` 辅助灰、`#F2F2F2` 容器浅灰、`#D3D3D3` 细灰框，统一 `Microsoft YaHei` / `Microsoft YaHei UI`）。
- 按表达意图往槽位装配原子组件：页眉组、顶部论点/串联条、底部洞察启示条、栏内佐证微卡、KPI 指标卡、引导词 Bullet、`①②③` 机制步骤块、300 DPI 论文图卡、轻量原生流程条、极简高密度对比表、跨栏红箭头。

### 横切约束 · 凝练文案、事实溯源与视觉自检
详见 `references/04-copy-and-qc.md`。

- 核实原文正式论文标题、Session/页码与全部量化数字（必含指标 + 幅度 + 基线 + 条件），零编造。
- 术语按工程习惯保留英文（如 `kernel`、`tile`、`warp`、`NoC`、`GEMM`），严禁将 `kernel` 硬译为「核/内核/注意力核」。
- 交付前逐页导出 PNG 目视验收：零溢出、零重叠、留白均衡、图注去原英文并带中文结论、无残留句号 `。` 与黄色审稿高亮框。

---

## 本仓库目录与脚本工具

- `references/01-deck-planning.md`：Layer 1 叙事组织思路与页间逻辑规范
- `references/02-slide-layouts.md`：Layer 2 页内逻辑 → 8 类版式路由、安全区坐标与容量预算
- `references/03-component-library.md`：Layer 3 Design Tokens 与语义组件库选型表
- `references/04-copy-and-qc.md`：横切文案凝练约束、术语表、裁图规范与交付前自检清单
- `assets/reference.pptx`、`references/style-spec.json`、`references/paper-to-insight.md`、`references/dsh-validation.md`：单页论文模板资产与几何规格
- `examples/aiperf-report.json`：单页模板输入样例（仅内容稿）
- `scripts/build-report.py` / `scripts/build-report.mjs`：单页模板生成器（复制 `assets/reference.pptx` 并替换 8 处文本槽与 4 张配图、写备注）
- `scripts/crop-figure.py`：从论文 PDF 渲染页面并按 bbox 裁图（`--trim` 自动去白边）
- `scripts/fit-figures.py`：将单页模板中的 4 张配图按纵横比放大至栏内空白
- `scripts/merge-decks.py`：将多篇单页 deck 合并为多页 PPT（页码自动顺延）

## 单页论文模板快速流程（兼容既有脚本）

当只需要基于 `assets/reference.pptx` 快速产出单篇一页洞察（三栏：问题 / 方案 / 收益 + 顶部洞察启示 + 底部关键技术 + 备注证据）时，直接运行：

```bash
# 1) 裁图（--box 为 left,top,right,bottom 比例，--trim 去白边）
<python> scripts/crop-figure.py --paper paper.pdf --page 5 --box 0.49,0.09,1.0,0.372 --out figs/fig4.png --trim

# 2) 按 examples/aiperf-report.json 编写 report.json 并生成单页
<python> scripts/build-report.py --input report.json --output out/draft.pptx

# 3) 若配图偏小，等比放大至栏内剩余空间
<python> scripts/fit-figures.py --input out/draft.pptx --output out/draft-fit.pptx

# 4) 多篇合并
<python> scripts/merge-decks.py --output combined.pptx 01.pptx 02.pptx
```

单页模板注意事项：
- 复制整张原幻灯片再填充，不要删除原页后从母版新建（`assets/reference.pptx` 有效路径为 `slide1 → slideLayout5 → slideMaster3 → theme3`）。
- `report.json` 中 `figures` 的 4 个键（`context`/`method`/`evaluation`/`result`）必须显式给对象或 `null`；缺图直接删槽不复用样例图。
- 证据定位（PDF 页码、节号、图表号）写入演讲者备注，单页模板正文不标页码出处；完整几何与母版映射见 `references/style-spec.json`。
