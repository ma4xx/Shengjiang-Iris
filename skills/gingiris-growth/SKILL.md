---
name: gingiris-growth
description: |
  Iris / Gingiris 的软件出海主路由。用于把冷启动、价值主张、用户访谈、SEO/GEO、社区、规模化增长、本地化等问题路由到对应子 skill；先按 `shengjiang-iris-perspective` 的判断层决定优先级，再路由到对应模块。当用户提到“软件出海”“出海增长”“冷启动”“Iris/Gingiris 视角”或问题类型不明确但明显属于出海增长时使用。
---

# Gingiris Growth

## Router Rule

这个 skill 只做路由，不抢答细节。

- 路由前，先按 `shengjiang-iris-perspective` 的判断顺序看 4 件事：
  - 一句话价值主张是否全球可懂
  - 当前更缺前 10 个高质量用户，还是更缺放大渠道
  - 问题核心是在修闭环，还是在做放大
  - 用户是在问“怎么想”，还是已经进入某个具体模块
- 先判断问题属于哪个阶段：定位、冷启动、用户研究、SEO/GEO、社区、规模化增长、本地化
- 只选一个主 skill；不要把多个 playbook 混成一锅
- 如果问题同时跨两个阶段，选最紧急、最靠前的那个阶段
- 只有在阶段完全无法判断时，才补问一个直接问题

## Routing Table

| 用户信号 | 路由到 |
|---|---|
| 明显在问「Iris 会怎么看」「帮我判断先做什么」「应该先修哪里」 | `shengjiang-iris-perspective` |
| 价值主张、主页一句话、竞品对标、品牌定位、10 秒内讲清楚 | `gingiris-growth-positioning` |
| 第一批用户、冷启动、DM、早期 traction、注册到付费、7 天/14 天 launch plan | `gingiris-growth-cold-start` |
| 用户访谈、beta 用户、录屏、反馈整理、Power User、访谈问题 | `gingiris-growth-user-research` |
| SEO、GEO、博客、FAQ Schema、llms.txt、canonical、内链、落地页 | `gingiris-growth-seo-geo` |
| 社区、大使、渠道伙伴、Reseller、Service Partner、Discord/Slack | `gingiris-growth-community` |
| PMF 之后、投放、KOL、广告、内容包、漏斗、预算、放大渠道 | `gingiris-growth-scale-growth` |
| 市场选择、语言、本地化、支付、合规、地区差异、招聘本地人 | `gingiris-growth-localization` |

## Output Contract

路由后，按这个格式回应：

1. 选中的 skill
2. 为什么选它
3. 需要补充的唯一关键假设，如果有
4. 下一步的可执行步骤

优先把“为什么现在先做这一步”说清楚，别只报 skill 名。

## Guardrails

- 不要在 router 里写完整方案
- 不要假装已经做过调研
- 不要一次把所有子 skill 都激活
- 输出要偏执行，不偏解释
- 不要把还没讲清楚定位的问题，路由成放大问题
