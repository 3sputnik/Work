# 华泰智研 official product model

Source inspected: `https://inst.htsc.com/skillhub?resource=1` on 2026-08-04.

## Product identity

- Official name: 华泰智研.
- Positioning: 你的专属机构AI工具箱，一键安装，专业随行.
- Audience: authorized licensed financial institutions, qualified institutional investors, and authorized professional research staff.
- Value propositions:
  - 兼容多家主流平台
  - 汇聚专业投研技能
  - 支持多种安装方式
  - 华泰研究所官方团队开发
  - 获取华泰智研海量数据

## Primary information architecture

- Keep `Skill` and `MCP` as mutually exclusive first-level resource tabs.
- Provide API Key management and usage instructions as supporting actions.
- Cards are the primary discovery unit for Skill resources.
- MCP content groups capabilities under a “华泰智研 MCP核心能力集” concept.

## Official Skill examples

Use these names and meanings when reproducing official content. Do not rewrite them into unrelated capabilities.

### 行业周度观点

Calls the latest core views and judgment logic from Huatai Securities Research Institute industry chief analysts. Use for industry outlooks, drivers, policy interpretation, value-chain analysis, allocation strategy, and key targets.

### 专业研报查询

Provides cross-industry research-report search and positioning, supporting market understanding, investment-opportunity discovery, current analytical approaches, and key targets.

### 公司估值模型

Presents detailed forecast-model results for covered companies, including revenue, net profit, EPS, growth rates, valuation, forecast revisions, and business-line contribution analysis.

### 市场每日复盘

Provides a daily market overview at industry and sector level, material macro news, and concise analysis for post-close review.

## Official MCP capability groups

The official page exposes these research-oriented capabilities:

- 量化大类资产配置
- A股多维量化择时
- A股风格因子择时与轮动
- A股量化行业轮动
- 基本面量化选股因子
- 公募基金评价、归因与筛选
- 美国宏观经济
- 美股权益研究
- 美债利率研判
- 跨资产隐含预期雷达
- 华泰研究框架
- 华泰首席观点
- A股资金面
- 港股资金面
- A股中观景气度
- A股情绪指数
- 港股情绪指数
- AI与基本面选股因子

## Content and interaction requirements

- Distinguish resource discovery from installation/configuration.
- Use concise card summaries; move detailed capability descriptions to detail or expanded views.
- Make API Key management visible but never display or prefill a real credential in mockups.
- Provide usage guidance near installation/configuration entry points.
- When search is present, search Skill and MCP names and descriptions; communicate the current resource scope.
- Preserve the existing official copy when the task requests reproduction or incremental modification.

## Risk and compliance requirements

The service transmits Huatai research reports and research data for use inside a customer-controlled AI environment. It does not itself provide Huatai-generated secondary AI analysis, summaries, predictions, investment advice, securities-consulting opinions, or trading instructions.

When a flow enables access or first use, account for these requirements:

- Show a clear risk disclosure and require explicit acknowledgment where applicable.
- State that outputs are for internal research reference and require independent verification.
- Warn about data timeliness, inconsistent historical views, incomplete context, and AI hallucination or interpretation risk.
- Limit use to authorized institutional users and compliant internal research purposes.
- Do not imply permission for redistribution, commercialization, public disclosure, scraping, reverse engineering, credential sharing, or data export.
- Treat API Keys as sensitive credentials; include secure-storage and abnormal-use considerations.
- Explain that third-party AI/model availability, accuracy, Token consumption, and related costs remain the customer’s responsibility.

Do not reproduce the entire legal disclosure inside ordinary cards. Use a dedicated disclosure surface, layered summary, or mandatory pre-use modal when the task requires the consent flow.
