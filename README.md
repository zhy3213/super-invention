# Self-Composing Personal Agent / Derived App 描述

> 一种能够为用户自我编排文字回复、快捷入口、交互界面、程序化工作流和派生应用的个人 AI agent。

## 一句话定义

Self-Composing Personal Agent 不是“更聪明的聊天机器人”，而是一个会根据用户意图、历史模式、任务复杂度、重复频率和程序化收益，持续为用户生成最合适交互形态与个人软件的 agent。

它的最终形态不是所有任务都回到聊天框，而是：

```text
自然语言请求
  → 识别任务模式
  → 选择交互形态
  → 生成 surface / shortcut / workflow
  → 稳定任务沉淀为 derived app
  → 用户之后直接使用个人软件，LLM 只在必要时介入
```

## 背景：聊天不是软件的终态

过去两年，AI agent 的主流形态仍然停留在“聊天机器人 + 工具调用”的范式里：

1. 用户用自然语言提出请求。
2. 模型理解意图。
3. 模型选择工具并执行任务。
4. 最后用文本返回结果。

这种形态证明了大模型可以成为新的软件入口，但也暴露出根本瓶颈：

- 聊天不是软件的终态。
- 文本不是高效交互的唯一形态。
- LLM 不应该成为所有控制流的默认执行路径。
- 很多任务天然需要表单、按钮、状态、历史、进度、对比、批处理和持久入口。

如果所有任务都被压扁进聊天框，系统就会被迫让 LLM 承担大量本应由软件界面承担的工作：维护状态、展示选项、解释上下文、解析用户选择、反复确认字段、手动触发脚本、在文本中模拟 UI。

这不是智能，这是交互层贫血。

## 新物种定义

Self-Composing Personal Agent 是一种新的个人计算层：agent 不只操作软件，而是持续塑造用户自己的交互环境和个人软件系统。

它将用户的自然语言请求、长期上下文、工具调用历史、个人偏好和任务重复模式，转换成五类产物：

1. **文字回复**  
   对低频、低结构化、低操作成本的简单任务，直接用对话完成。

2. **Intent Shortcut**  
   对高频、简单、结构稳定的任务，生成一键入口或快捷指令，避免每次重新输入和重新推理。

3. **交互界面 / Surface**  
   为当前任务生成临时或持久 UI，例如表单、列表、状态面板、确认页面、批处理入口。

4. **状态模型与操作路径**  
   把任务中的对象、字段、进度、决策、按钮、表单、选择器和批处理动作绑定到稳定 executor。

5. **派生应用 / Derived App**  
   把重复出现的工作流沉淀成可再次打开、可被通知唤起、可被自动化触发的小型个人应用。

## 核心原则

### 1. Chat is the fallback, not the product

聊天仍然重要，但它不是唯一产品形态。低频、开放、模糊的任务适合聊天；高频、结构化、可确定执行的任务应该逐渐从聊天迁移到 shortcut、surface、workflow 和 derived app。

### 2. Compile once, execute many times

普通 agent 的路径是：

```text
Prompt → LLM reasoning → tool call → response
```

Self-Composing Personal Agent 的路径是：

```text
Prompt → task pattern → generated surface → executable workflow → derived app
```

随着使用时间增长，越来越多任务会从“每次解释执行”变成“编译一次，多次执行”。

### 3. 稳定控制流交给程序，不交给 prompt

当任务可以确定性执行时，应该绕过 LLM 推理，直接调用程序化执行路径。LLM 只在任务仍然模糊、开放、需要判断、需要总结、需要生成时作为语义层介入。

### 4. Agent 生成软件，而不是永远亲自跑流程

稳定、高频、结构化的工作不应该每次都让 agent 重新理解、重新规划、重新选择工具。agent 应该把它沉淀成个人软件：有入口、有状态、有 UI、有 executor、有运行历史、有调度能力。

## 任务升级路径

一个任务从自然语言请求到 derived app 的典型升级路径：

```text
第一次：用户用自然语言描述任务。
第二次：agent 识别类似任务并调用已有工具。
第三次：如果任务简单但高频，系统生成 intent shortcut。
第四次：如果任务需要状态、比较、编辑或确认，系统生成专属界面。
第五次：如果任务结构稳定且持续重复，界面绑定程序化 executor。
第六次：任务沉淀为派生应用。
之后：用户直接使用 shortcut / surface / app，LLM 只在必要时介入。
```

## Derived App 是什么

Derived App 是由 Hermes 根据用户需求生成或维护的小型个人应用。它通常包括：

- 一个 WebUI surface：让用户通过页面、按钮、表单、列表和状态面板交互。
- 一个 deterministic executor：用脚本稳定执行工作流。
- 一个 manifest：声明 app 元数据、入口、权限、状态和 executor。
- 一个 input schema：定义输入字段和校验规则。
- 本地状态和运行历史：记录默认配置、最近运行结果、stdout/stderr、错误和完成状态。
- 可选的 Hermes API 调用：当脚本需要语义判断、总结或生成时，显式调用 Hermes API Server。
- 可选的 Hermes cron 调度：定时运行稳定脚本，而不是定时跑 prompt。

## 用户价值

Self-Composing Personal Agent 的价值不是“又一个 agent chat UI”，而是让个人软件从用户真实需求中自然长出来：

- 高频任务少重复输入。
- 结构化任务有合适界面。
- 稳定流程可审计、可复跑、可调度。
- 用户不必每次解释同一个需求。
- LLM 不再负责所有控制流，系统更稳定、更快、更可验证。
- 个人知识、偏好、历史 workflow 可以逐渐变成专属软件系统。

一句中文产品叙事：

> 它学习的不只是你的意图，而是你的生活和工作应该长出什么软件。

一句英文产品叙事：

> The agent learns not only what you mean, but what interface your life needs.

## 与普通 agent 的区别

| 维度 | 普通 Agent | Self-Composing Personal Agent |
| --- | --- | --- |
| 主入口 | 聊天框 | 聊天 + shortcut + surface + app |
| 任务执行 | 每次 prompt 推理 | 稳定任务编译为 executor |
| UI | 文本模拟 UI | 生成真实 WebUI surface |
| 高频任务 | 反复描述 | 沉淀入口和应用 |
| LLM 角色 | 默认控制所有流程 | 只在语义/判断/生成处显式介入 |
| 结果形态 | 文本回复 | 个人软件系统逐渐生长 |

## Hermes 为什么适合做这个底座

Hermes 已经具备 Self-Composing Personal Agent 的底层条件：

- API Server：可作为 OpenAI-compatible agent backend。
- 多入口：Discord、Telegram、CLI、API、webhook。
- 长期上下文：memory、user profile、session DB、session_search。
- 工具执行：terminal、file、browser、web、cron、messaging、MCP 等。
- 技能沉淀：skills 本质上是 workflow fossilization / 经验固化。
- 后台运行：cron jobs 和 webhook 触发。
- 多 agent 协作：delegation、profiles、kanban 等。

因此 Hermes 缺的不是 agent brain，而是把 tools / memory / sessions / cron 包装成可组合、可视化、可持久化的 personal software layer。

## 最简产品表达

> Hermes chat 负责理解你和生成软件；Hermes App Runtime 负责托管和运行这些软件；Hermes cron 负责按时触发稳定脚本；Hermes API Server 只在脚本需要语义能力时被显式调用。

最终目标：

```text
一个会持续长出你个人软件系统的 agent OS。
```
