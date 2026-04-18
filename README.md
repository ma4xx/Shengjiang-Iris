# Shengjiang Iris Skills

一套面向 **软件出海 / AI 产品冷启动 / 开源增长** 的通用 agent skills。

只要你的 agent 支持 skills 目录加载或等价的 skill 机制，这套仓库就可以使用。

明确适用：

- Claude Code
- OpenClaw
- Codex
- 其他支持 skills 的 agent 框架

这套仓库包含两层能力：

1. **`shengjiang-iris-perspective`**
   - 这是“生姜 Iris 的判断层”
   - 负责决定：现在最该先做什么、什么是伪问题、什么动作会放大误解、什么时候该修定位、什么时候才适合放大渠道

2. **`gingiris-*`**
   - 这是“执行层”
   - 负责把判断落成具体方案，例如定位文案、7 天冷启动计划、用户访谈提纲、SEO / GEO 结构、社区方案、规模化增长计划、本地化方案

一句话理解：

- **`shengjiang-iris-perspective` = 生姜 Iris 的脑子**
- **`gingiris-*` = 生姜 Iris 这套方法怎么把事情做出来**

---

## 适合谁

这套 skills 适合：

- 做软件出海、AI 产品、开源产品的人
- 正在 0→1 冷启动阶段的人
- 已经有初步产品，想判断下一步该先修定位、找用户、做 SEO、建社区，还是开始放大的人
- 想用更“像生姜 Iris”的方式做判断，而不是套通用增长模板的人

不太适合：

- 强线下分销业务
- 重监管或超复杂 enterprise sales 场景
- 已经很成熟的大规模品牌投放团队

---

## 仓库结构

```text
skills/
  shengjiang-iris-perspective/
    SKILL.md
    agents/openai.yaml
    references/research/
  gingiris-growth/
  gingiris-growth-positioning/
  gingiris-growth-cold-start/
  gingiris-growth-user-research/
  gingiris-growth-seo-geo/
  gingiris-growth-community/
  gingiris-growth-scale-growth/
  gingiris-growth-localization/
```

---

## 每个 skill 是做什么的

### 1. `shengjiang-iris-perspective`

用途：

- 用“生姜 Iris 的视角”看问题
- 判断优先级
- 给取舍
- 识别伪增长动作

适合问：

- 这个产品现在最大的问题是什么？
- 我该先修定位，还是先做渠道？
- 现在适合投流吗？
- 这件事如果按生姜 Iris 的方式判断，会怎么做？

### 2. `gingiris-growth`

用途：

- 路由器
- 当你还不确定该用哪个模块时，先用它判断

### 3. `gingiris-growth-positioning`

用途：

- 一句话介绍
- 官网首屏
- 竞品参照系
- 差异化表达

### 4. `gingiris-growth-cold-start`

用途：

- 前 10 个用户
- 7 天冷启动计划
- 最小闭环
- DM / 私信 / 社媒触达

### 5. `gingiris-growth-user-research`

用途：

- 用户访谈提纲
- beta 用户筛选
- 录屏观察
- 反馈归类与决策信号提炼

### 6. `gingiris-growth-seo-geo`

用途：

- SEO
- GEO
- 博客结构
- FAQ / Schema / llms.txt / 内链
- 长尾内容和 AI 可引用内容建设

### 7. `gingiris-growth-community`

用途：

- 社区运营
- ambassador
- 伙伴体系
- Discord / Slack / 自传播机制

### 8. `gingiris-growth-scale-growth`

用途：

- PMF 之后的规模化增长
- 广告、KOL、投放、预算、漏斗
- 判断是否真的已经到了“该放大”的阶段

### 9. `gingiris-growth-localization`

用途：

- 目标市场判断
- 本地化优先级
- 支付 / 合规 / workflow / 渠道差异

---

## 安装方法

### 方式一：手动复制到你的 agent skills 目录

把本仓库里的 `skills/` 目录复制到你的 agent skills 目录下。

常见目录示例：

```bash
mkdir -p ~/.codex/skills
cp -R skills/* ~/.codex/skills/
```

如果你用的是其他支持 skills 的 agent，只需要把 `skills/*` 复制到该 agent 对应的 skills 目录即可。

例如：

- Claude Code：放到你的 Claude Code skills 目录
- OpenClaw：放到 OpenClaw 读取 skills 的目录
- 其他 agent：放到该 agent 约定的 skills 路径

复制完成后，新的 skill 目录大致会长这样：

```text
~/.codex/skills/
  shengjiang-iris-perspective/
  gingiris-growth/
  gingiris-growth-positioning/
  gingiris-growth-cold-start/
  ...
```

### 方式二：只安装部分模块

如果你只想装判断层和路由器，至少保留：

- `shengjiang-iris-perspective`
- `gingiris-growth`

如果你想要完整可用，建议把整个 `skills/` 目录一起复制过去。

---

## 怎么使用

下面的调用示例使用 `$skill-name` 的写法。

如果你的 agent 不使用这个触发格式，也可以直接用自然语言指定 skill 名称或按该 agent 的 skill 调用方式来用。

## 用法 1：先借“生姜 Iris 的脑子”判断

直接调用：

```text
$shengjiang-iris-perspective
```

示例：

```text
用 $shengjiang-iris-perspective 看看，我这个产品现在最大的问题是什么。
```

```text
用 $shengjiang-iris-perspective 判断一下，我现在该先修定位、找前 10 个用户，还是做 SEO。
```

适合场景：

- 你还没想清楚问题到底出在哪
- 你不确定现在该先做哪一步
- 你想先听“像生姜 Iris 一样”的判断，而不是立刻套模板

---

## 用法 2：直接交给执行模块做产物

如果你已经知道自己要做什么，直接点对应模块。

示例：

```text
用 $gingiris-growth-positioning 重写这个产品的一句话介绍、Hero 标题和竞品参照系。
```

```text
用 $gingiris-growth-cold-start 给这个产品做 7 天冷启动 plan，重点放在前 10 个高质量用户和最小传播闭环。
```

```text
用 $gingiris-growth-user-research 帮我设计一套早期用户访谈提纲，重点验证价值主张和付费信号。
```

```text
用 $gingiris-growth-seo-geo 给我规划这个产品的 SEO / GEO 内容结构、页面结构和 FAQ。
```

---

## 用法 3：让它先判断，再执行

这是最推荐的用法。

示例：

```text
先用 $shengjiang-iris-perspective 判断这个产品现在最该先做什么，再调用合适的 $gingiris-* 模块给我出具体方案。
```

这会更接近真实的生姜 Iris 工作方式：

- 不是一上来就做方案
- 而是先判断：问题究竟在定位、用户、闭环、渠道还是放大时机

---

## 推荐提问方式

### 如果你还很模糊

```text
用 $gingiris-growth 帮我判断，这个产品现在最该先做什么，为什么。
```

### 如果你要定位

```text
用 $gingiris-growth-positioning 帮我把这个产品讲成全球用户能听懂的一句话，并给出竞品参照系。
```

### 如果你要冷启动

```text
用 $gingiris-growth-cold-start 给我做一个 7 天冷启动方案，目标是前 10 个高质量用户，不要泛流量。
```

### 如果你要用户访谈

```text
用 $gingiris-growth-user-research 设计访谈提纲，重点看用户是否真的听懂了价值主张，以及什么情况下愿意付费。
```

### 如果你要判断能不能放大

```text
先用 $shengjiang-iris-perspective 判断这个产品现在是不是已经适合放大，再用 $gingiris-growth-scale-growth 给我出投放和渠道计划。
```

---

## 这套 skill 的核心原则

这套仓库不是“通用增长建议合集”，它有非常明确的判断偏好：

- 先讲清楚价值主张，再谈增长
- 先找前 10 个高质量用户，不先追大盘流量
- 先跑付费或传播闭环，再决定要不要投流
- 运营不是发帖，而是用户路径设计
- pivot 可以，但不能乱跳
- 开源、内容、社区只是杠杆，必须接成承接和转化

如果你喜欢更直接一点的理解：

**这套东西的本质是：少做自嗨动作，多做能拿到真实用户证据的动作。**

---

## 关于 `shengjiang-iris-perspective`

这个人物 skill 不是在模仿说话口气，而是在提炼：

- 她怎么判断优先级
- 她怎么看冷启动
- 她怎么区分“热闹”和“验证”
- 她会在哪一步踩刹车

研究材料放在：

```text
skills/shengjiang-iris-perspective/references/research/
```

里面包含：

- 公开播客与访谈证据
- 表达 DNA
- 决策记录
- 时间线
- 外部视角和交叉验证

---

## 适合怎么贡献

如果你要继续迭代这套仓库，建议优先做下面几类改进：

1. 增加更多生姜 Iris 的公开材料引用
2. 用真实产品题目做压测
3. 继续修正各个 `gingiris-*` 模块的默认判断顺序
4. 把“判断层”和“执行层”分得更干净

---

## 当前状态

本仓库已经包含：

- 新蒸馏的人物 skill：`shengjiang-iris-perspective`
- 接入该判断层后的整套 `gingiris-*`

也就是说，现在已经不是“多了一个新 skill”，而是：

**旧的 `gingiris` 模块已经开始用新的生姜 Iris 判断方式来工作。**
