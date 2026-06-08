# Data Desensitization Skill

一个面向 AI 协作场景的通用数据脱敏 skill。

它不是只做“手机号打码”，也不是只服务“客户报告外发”。这个 skill 面向更广的数据脱敏工作：Excel、CSV、PPT、Word、HTML、Markdown、SQL 查询结果，以及你直接贴给 AI 的文本、表格片段和分析内容。

核心原则只有一条最重要：

**只要是敏感标识或真实数字，就不能原样保留。**

## 这个 skill 解决什么问题

很多团队在做“脱敏”时，只想到姓名和手机号，但真正容易泄漏业务信息的往往还有：

- 品牌名、门店名、策略名、内部渠道名
- 用户 ID、会员 ID、订单号
- 人数、金额、GMV、ROI、客单价、订单量、转化率
- 图表标签、tooltip、页脚、附录、隐藏 sheet、embedded JSON

这个 skill 的价值在于：

- 把 **文件型脱敏** 作为第一优先级
- 兼容 **内容型脱敏**
- 支持 **轻度脱敏 / 重度脱敏**
- 明确规定 **所有数字都不能原样保留**
- 强调 **结构保留、真实值隐藏、避免反推**

## 适用场景

### 文件型优先

- Excel / CSV 脱敏
- PPT 脱敏
- Word 报告脱敏
- HTML / Markdown 页面脱敏

### 内容型兼容

- SQL 查询结果脱敏
- 一段复盘文字脱敏
- 一张表格片段脱敏
- 图表结论和业务洞察脱敏

## 轻度脱敏 vs 重度脱敏

### 轻度脱敏

适合：

- 发给当前客户继续讨论
- 外部沟通但仍然需要较强可读性

特点：

- 用户字段掩码或稳定匿名
- 经营字段做泛化替换
- 所有数字做扰动
- 保留趋势、排序、结构和叙事逻辑

### 重度脱敏

适合：

- Excel 明细外发
- 案例分享
- 培训材料
- 跨客户复用
- 公开或半公开材料

特点：

- 用户字段完全泛化
- 经营字段抽象到类目层
- 所有数字不保留精确值
- 用区间、量级、等级、指数或描述性表达替代

## 仓库结构

```text
data-desensitization-skill-repo/
├── README.md
├── data-desensitization/
│   ├── SKILL.md
│   └── references/
│       ├── checklist.md
│       ├── field-catalog.md
│       ├── output-guidelines.md
│       └── rule-matrix.md
└── examples/
    ├── data-desensitization-skill-design.html
    └── data-desensitization-examples.html
```

## 安装到 Codex

把 `data-desensitization/` 复制到本地 skill 目录即可：

```bash
cp -R data-desensitization ~/.codex/skills/
```

## 你可以怎么对 AI 说

```text
帮我对这个 Excel 做脱敏，按重度脱敏处理。用户字段全部匿名，所有数字都不能保留原值。
```

```text
把这份 PPT 做轻度脱敏，发给当前客户继续讨论，保留趋势和结构，但真实数字全部扰动。
```

```text
把这段 SQL 查询结果脱敏，去掉可识别字段，并把所有数字改成不可反推的表达。
```

```text
把这个项目复盘改成案例分享版，按重度脱敏，只保留方法论和启发，不保留真实经营值。
```

## 示例页面

- `examples/data-desensitization-skill-design.html`
  解释为什么“数据脱敏”不只是打码，而是包含用户字段处理、经营字段泛化、数字扰动和对外表达重写。

- `examples/data-desensitization-examples.html`
  提供脱敏前后示例，可切换轻度脱敏和重度脱敏。

## 适合谁

- 数据分析师
- CRM / CDP / MA 顾问
- 零售 / 餐饮 / 商超 / 快消分析团队
- 咨询项目复盘团队
- 任何需要把真实业务数据转成可安全分享材料的人

## 当前版本说明

这是一个可安装、可复用、文件型优先的通用数据脱敏 skill v1。

它已经适合直接使用；如果后续继续沉淀，可以再补：

- 行业化字段清单
- 更稳定的数字扰动规则
- Excel / PPT / HTML 的高风险位置样例
- 面向神策、零售、餐饮场景的默认表达模板
