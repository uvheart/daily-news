# 从 ChatGPT 到 Agent Cloud：2023—2026 AI 演进与 Agentic RL、Sandbox、Agent Platform 的崛起

## 引言

如果从 2023 年 GPT-4 发布算起，到 2026 年，AI 行业已经经历了非常明显的范式迁移。

2023 年，行业核心问题还是：

> 大模型能不能理解复杂指令、生成高质量内容，并通过 API 接入业务？

到了 2024 年，问题开始变成：

> 模型能不能看懂图片、视频、屏幕，调用工具，并在真实环境里行动？

2025 年进一步演化为：

> 模型能不能作为 Agent，持续执行多步任务，而不只是完成一次问答？

而到 2026 年，越来越多系统开始回答更底层的问题：

> Agent 应该运行在哪里？如何获得计算环境？如何管理生命周期、工具、权限、状态、轨迹、训练与评测？

这意味着，AI 正在从单纯的 **Model-centric**，逐渐转向 **System-centric**。

如果把这几年压缩成一条技术路线，大致可以写成：

```text
2023
LLM
“我可以回答问题”
        ↓

2024
Multimodal + Tool-using Model
“我可以感知世界并使用工具”
        ↓

2025
Agent
“我可以自主完成复杂任务”
        ↓

2026
Agent Runtime / Agent Platform
“我拥有自己的计算环境，可以长期执行任务”
        ↓

下一阶段
Learning Agent
“我通过与环境交互不断学习和增强”
```

而最后这一步，正是今天快速发展的 **Agentic RL**。

---

# 一、2023：LLM 时代真正开始

ChatGPT 在 2022 年底发布，但真正推动整个产业进入大模型时代的，是 2023 年 GPT-4 的发布。

2023 年 3 月，OpenAI 发布 GPT-4。相比此前模型，它在复杂推理、指令遵循、多领域任务上的能力大幅提高。

官方介绍：

- [GPT-4 Research](https://openai.com/index/gpt-4-research/)

这个时期的系统架构依然非常简单：

```text
User
 ↓
LLM
 ↓
Answer
```

大模型的核心价值还是：

- 问答
- 写作
- 总结
- 编程辅助
- 文档理解
- 自然语言交互

因此 2023 年上半年，本质仍然是一个 **LLM as an API** 的世界。

## 1. Function Calling：Agent 架构的第一个真正起点

2023 年很快出现了一个极其重要的变化：**模型开始调用工具。**

OpenAI 先推出 ChatGPT Plugins，随后在 2023 年 6 月推出 Function Calling。

官方资料：

- [Function calling and other API updates](https://openai.com/index/function-calling-and-other-api-updates/)

在此之前，模型只能：

```text
Prompt
 ↓
LLM
 ↓
Text
```

Function Calling 之后，系统开始变成：

```text
Prompt
 ↓
LLM
 ↓
Choose Tool
 ↓
API / Search / Database / Code
 ↓
Observation
 ↓
LLM
 ↓
Answer
```

这是后来所有 Agent 系统最核心的基本循环。

它意味着：

> 模型不再需要自己直接完成任务，而是可以负责决策，再把动作交给外部系统。

今天我们谈的 Tool Use、MCP、Coding Agent、Browser Agent、Agent SDK，本质上都是从这套思想继续演进出来的。

## 2. RAG 成为 2023 年最重要的应用范式之一

2023 年另一个热门方向是 RAG。

因为当时大家面临一个明显问题：

> 模型知道的内容有限，而且知识无法实时更新。

于是出现了典型架构：

```text
User Query
 ↓
Embedding
 ↓
Vector Database
 ↓
Retrieve Documents
 ↓
LLM
 ↓
Answer
```

这一时期 AI Infra 的大量注意力集中在：

- Vector Database
- Embedding
- RAG Pipeline
- Prompt Engineering
- Model Serving

从今天回头看，这可以称为 **LLM Application 1.0**。

核心仍然是“如何把信息更好地喂给模型”。

## 3. 长上下文开始成为关键能力

2023 年 11 月，OpenAI 在 DevDay 发布 GPT-4 Turbo，并将上下文窗口提升到 128K。

官方资料：

- [New models and developer products announced at DevDay](https://openai.com/index/new-models-and-developer-products-announced-at-devday/)

这让模型第一次能更现实地处理：

- 大量文档
- 更大的代码库
- 长对话
- 企业知识
- 复杂上下文

AI 系统开始从单轮问答，向“具有工作上下文的助手”发展。

---

# 二、2024：Multimodal、Tool Use 与 Agent 基础设施开始成型

如果说 2023 是 LLM 元年，那么 2024 更像是一个非常典型的过渡年。

这一年最重要的变化，不再只是“模型参数更多”，而是：

> 模型开始拥有越来越丰富的感知和行动能力。

## 1. 长上下文进一步突破

Google 在 2024 年发布 Gemini 1.5 Pro，大幅推动长上下文能力。

官方介绍：

- [Gemini 1.5: Unlocking multimodal understanding across millions of tokens](https://blog.google/innovation-and-ai/products/google-gemini-next-generation-model-february-2024/)

Gemini 1.5 将长上下文提升到百万 token 级别，使模型能够处理：

- 视频
- 巨型文档
- 大型代码库
- 长时间音频
- 多模态内容

于是行业的问题开始发生变化。

以前是：

> 信息怎么塞进去？

后来逐渐变成：

> 模型已经看到了这么多信息，下一步能不能自己做事？

## 2. 多模态成为基础能力

2024 年，大模型逐渐从语言模型演化成通用感知模型。

输入不再局限于 Text，而是开始覆盖：

```text
Text
Image
Audio
Video
Code
Screen
```

这一步非常关键，因为 Agent 想进入真实世界，首先必须理解环境。

这直接为后来的 Browser Agent、Computer Use、GUI Agent、Coding Agent、Robotics Agent 提供了基础。

## 3. Computer Use：Agent 开始真正进入环境

2024 年 10 月，Anthropic 发布 Claude Computer Use。

官方资料：

- [Introducing computer use, a new Claude 3.5 Sonnet, and Claude 3.5 Haiku](https://www.anthropic.com/news/3-5-models-and-computer-use)

Computer Use 让模型能够：

- 看截图
- 移动鼠标
- 点击
- 输入文字
- 使用桌面软件

于是系统循环第一次变得非常接近强化学习：

```text
Screen / State
 ↓
Model
 ↓
Action
 ↓
Environment Changes
 ↓
New Screen
 ↓
Model
```

这和 RL 中经典结构非常相似：

```text
State
 ↓
Policy
 ↓
Action
 ↓
Environment
 ↓
Next State
```

因此从技术上说，**Computer Use 天然就是 Agentic RL 的重要前置条件。**

## 4. MCP：Agent 与工具生态开始标准化

2024 年 11 月，Anthropic 开源 Model Context Protocol，也就是 MCP。

官方资料：

- [Introducing the Model Context Protocol](https://www.anthropic.com/news/model-context-protocol)

MCP 试图解决一个很现实的问题：如果每一个模型都要分别适配 GitHub、Slack、Database、Browser、Internal API，系统很快会出现严重的 N×M 集成问题。

过去可能是：

```text
Claude → GitHub Adapter
Claude → Slack Adapter
Claude → Database Adapter

GPT → GitHub Adapter
GPT → Slack Adapter
GPT → Database Adapter
```

而 MCP 试图变成：

```text
Agent
 ↓
MCP
 ↓
GitHub / Slack / DB / Browser / Internal Tools
```

MCP 的真正意义不仅是一个协议，它是在尝试建立：

> **Agent 与外部世界之间的标准接口层。**

到这里，Agent 的基础组件已经逐渐清晰：

```text
Model
+
Context
+
Tool Calling
+
MCP
+
Computer Use
```

但当时仍然有一个巨大问题：

> 模型是否足够可靠，可以连续执行几十步甚至几百步任务？

这个问题在 2025 年开始被大规模解决。

---

# 三、2025：AI 真正进入 Agentic Era

2025 年是过去几年 AI 发展中非常重要的一年。

这一年，两条此前相对独立的技术路线开始明显汇合：

```text
Reasoning Model
+
Agent Infrastructure
```

一边是强化学习推动模型推理能力快速提高，另一边是工具、环境、Agent Runtime 开始成熟，最终产生了今天所谓的 **Agentic AI**。

---

# 四、2025 第一条主线：Reasoning + Reinforcement Learning

2025 年初，DeepSeek-R1 成为一个重要标志。

官方资料：

- [DeepSeek-R1 Release](https://api-docs.deepseek.com/news/news250120)

R1 强化了一个行业共识：

> 大模型能力提升，不再只能依靠更大规模预训练。

新的路线开始变成：

```text
Pretraining
 ↓
SFT
 ↓
RL / RLVR
 ↓
Inference-time Reasoning
```

## 1. RLVR 爆发

RLVR，即 Reinforcement Learning with Verifiable Rewards。

这类任务有一个巨大优势：reward 很容易自动验证。

例如数学：

```text
Model Answer == Ground Truth
```

Coding：

```text
Unit Tests Pass
```

SQL：

```text
Query Result Correct
```

因此 RL 系统可以自动产生大量高质量训练反馈。

这一阶段出现了大量算法和工程体系：

- GRPO
- PPO variants
- DAPO
- RLOO
- RLHF / RLVR Infra

但更关键的变化并不是某一个算法本身，而是：

> RL 开始从单轮文本任务向 Agent 多轮环境任务迁移。

---

# 五、verl、AReaL：RL Framework 开始向 Agentic RL Infra 演化

## 1. verl

verl 已经开始把 Agentic RL 作为重要方向支持。

资料：

- [verl GitHub](https://github.com/volcengine/verl)
- [verl Agentic RL Documentation](https://verl.readthedocs.io/en/latest/start/agentic_rl.html)

Agentic RL 和普通 RL 最大区别是：

普通模式：

```text
Prompt
 ↓
Model
 ↓
Answer
 ↓
Reward
```

Agentic RL：

```text
Task
 ↓
Agent
 ↓
Action
 ↓
Environment
 ↓
Observation
 ↓
Agent
 ↓
Action
 ↓
...
 ↓
Reward
```

这意味着 rollout 系统必须处理：

- Multi-turn
- Tool Calling
- Environment State
- Long Trajectory
- Async Execution
- Timeout
- Failure Recovery

于是 RL Framework 开始越来越像分布式系统。

## 2. AReaL

AReaL 更进一步推动了异步 RL。

论文：

- [AReaL: A Large-Scale Asynchronous Reinforcement Learning System](https://arxiv.org/abs/2505.24298)

项目：

- [AReaL GitHub](https://github.com/areal-project/AReaL)

传统同步 RL：

```text
Generate Batch
 ↓
Wait All Samples
 ↓
Train
 ↓
Generate Next Batch
```

问题是 Agent rollout 时长差异非常大：有的任务 2 秒，有的 30 秒，有的甚至 60 秒超时。

同步系统会出现大量资源空闲，因此 AReaL 推动：

```text
Rollout Workers
      ↓
Trajectories
      ↓
Async Trainer
```

也就是 **generation 和 training 解耦**。

这类架构后来逐渐发展成：

```text
Training Service
Inference Service
Agent Service
Weight Update Service
```

从这里开始可以明显看到：

> RL Framework 正在逐渐变成一个分布式 Agent Training Platform。

---

# 六、2025 第二条主线：Coding Agent 找到最清晰的 PMF

2025 年，Coding 成为 Agent 最成熟的应用场景之一。

原因并不神秘。Coding 天然就是一个非常完美的 Agent environment。

## State

```text
Repository
Files
Git
Compiler
Tests
Runtime
```

## Action

```text
Read
Edit
Shell
Search
Run Tests
Git Diff
```

## Reward

```text
Build Success
Tests Pass
Issue Resolved
```

因此 Coding Agent 同时满足：

- 工具使用
- 长上下文
- 多步规划
- 可验证奖励
- Sandbox
- RL

所以 2025 年迅速出现大量成熟 Coding Agent 产品：

- Claude Code
- OpenAI Codex
- Cursor Agent
- Devin
- Jules

Anthropic 的 Claude Sonnet 系列也越来越明确地强化 Coding、Agents、Computer Use、Long-running tasks。

官方：

- [Claude Sonnet 4.5](https://www.anthropic.com/news/claude-sonnet-4-5)

Coding Agent 的意义不仅仅是“程序员工具”，它实际上是：

> **Agentic AI 第一个真正成熟的大规模实验场。**

---

# 七、2025 第三条主线：Agent Platform 开始成型

2025 年 3 月，OpenAI 发布一系列 Agent 构建基础设施。

官方：

- [New tools for building agents](https://openai.com/index/new-tools-for-building-agents/)

包括：

- Responses API
- Agents SDK
- Web Search
- File Search
- Computer Use
- Tracing

架构已经开始变成：

```text
                 Tools
                  │
        ┌─────────┼──────────┐
        ↓         ↓          ↓
    Web Search  Files    Computer
        │
        └────── Agent Harness
                   │
                  Model
```

这意味着 Agent 不再只是：

```text
LLM + LangChain Workflow
```

而是在逐渐成为一套真正的平台能力。

Agent Platform 开始具备：

- Tool Management
- Tracing
- State
- Execution
- Memory
- Computer
- File System
- Background Tasks

---

# 八、2026：Agent 从软件实体变成计算实体

2026 年一个非常明显的趋势是：

> Agent 开始拥有自己的“Computer”。

OpenAI 在 2026 年介绍了如何给 Responses API 配备计算环境。

官方：

- [From model to agent: Equipping the Responses API with a computer environment](https://openai.com/index/equip-responses-api-computer-environment/)

其中开始直接提供：

- Shell
- Filesystem
- Container Workspace
- Network Control
- SQLite
- Skills
- Context Compaction

于是系统架构变成：

```text
LLM
 ↓
Agent Harness
 ↓
Computer Environment
 ├── Shell
 ├── Filesystem
 ├── Processes
 ├── Network
 └── State
```

这已经不是传统意义上的聊天机器人。

Agent 开始越来越像：

> 一个拥有 CPU、内存、文件系统和工具的数字 Worker。

---

# 九、Google Managed Agents：Agent-as-a-Service 进一步明确

Google 也开始往同一个方向发展。

2026 年 Gemini Managed Agents 将 Agent 与隔离 Linux 环境进一步整合。

资料：

- [Managed Agents in the Gemini API](https://blog.google/innovation-and-ai/technology/developers-tools/managed-agents-gemini-api/)

其思路大致是：

```text
Agent
+
Reasoning
+
Tools
+
Code Execution
+
Ephemeral Linux Sandbox
```

后续能力还继续加入：

- Background Tasks
- Remote MCP
- Function Calling
- Credential Refresh

相关资料：

- [Expanding Managed Agents in the Gemini API](https://blog.google/innovation-and-ai/technology/developers-tools/expanding-managed-agents-gemini-api/)

这说明云厂商正在把 AI 服务从：

```text
Model-as-a-Service
```

继续推向：

```text
Agent-as-a-Service
```

甚至：

```text
Computer-as-a-Service for Agents
```

---

# 十、2026：为什么 Sandbox 从配角变成核心基础设施

早期 Agent 主要调用的是受控 API。

例如：

```text
Agent
 ↓
Function Call
 ↓
REST API
```

这种模式风险相对可控。

但今天 Coding Agent 和 General Agent 往往需要：

```text
Agent
 ↓
Shell
 ↓
Git Clone
 ↓
pip install
 ↓
Run Code
 ↓
Browser
 ↓
Network
 ↓
Filesystem
```

这时候，Sandbox 就不再只是一个安全附件。

## 一个真正的 Agent Sandbox 至少需要解决：

```text
Lifecycle
Isolation
CPU / Memory
Filesystem
Network
Secrets
Image
Snapshot
Persistence
Timeout
Quota
Scheduling
Warm Pool
Observability
GPU
```

这已经完全进入云原生和基础设施领域。

---

# 十一、E2B 与 Daytona：Give Every Agent a Computer

E2B 是 Sandbox / Agent Compute 领域的重要代表。

相关资料：

- [E2B Blog](https://e2b.dev/blog)
- [E2B Series A](https://changelog.e2b.dev/blog/series-a)

它的方向非常明确：

> 为 Agent 提供 Cloud Computer。

其 Sandbox 能力逐渐扩展到：

- Linux
- Browser
- Kubernetes
- Private Networking
- Secret Management
- Observability

Daytona 的表达甚至更加直接：

> Give every agent a computer.

项目：

- [Daytona](https://www.daytona.io/)

这一方向背后的架构非常清晰：

```text
LLM Provider
 ↓
Agent Platform
 ↓
Sandbox Runtime
 ↓
Compute Infra
```

---

# 十二、Sandbox + MCP 开始融合

随着 Agent 工具越来越多，Sandbox 和 MCP 也开始融合。

E2B 与 Docker 曾推动 MCP 与 Sandbox 的组合。

资料：

- [Docker & E2B: MCP support in E2B Sandbox](https://e2b.dev/blog/docker-e2b-partner-to-introduce-mcp-support-in-e2b-sandbox)

以前可能是：

```text
Agent
 ↓
MCP
 ↓
Tool
```

未来更常见的形态可能变成：

```text
Agent
 ↓
Sandbox
 ├── MCP
 ├── Shell
 ├── Browser
 ├── Code
 └── Filesystem
```

也就是说：

> Sandbox 开始成为 Agent 的统一 Execution Boundary。

---

# 十三、为什么 Agentic RL 与 Sandbox 必然合流

Agentic RL 最关键的特点是：

> 模型必须和环境发生连续交互。

经典 RL 结构：

```text
State
 ↓
Action
 ↓
Environment
 ↓
Observation
 ↓
Reward
```

而 Agentic RL 中：

```text
Agent
 ↓
Tool
 ↓
Environment
 ↓
Observation
 ↓
Agent
 ↓
Next Action
```

环境必须具备：

```text
reset()
step()
observe()
reward()
```

以 Coding Agent 为例：

```text
Create Sandbox
 ↓
Clone Repo
 ↓
Model Edits Code
 ↓
Run Tests
 ↓
Observe Result
 ↓
Edit Again
 ↓
Run Tests
 ↓
Reward
 ↓
Destroy Sandbox
```

这里 Sandbox 本质上就是：

> **Environment Implementation**

因此 Sandbox 的角色发生了根本变化。

2023 年：

> Sandbox 是为了不让模型破坏宿主机。

2026 年：

> Sandbox 是 Agent 所处的“世界”。

这是非常重要的认知转变。

---

# 十四、Agentic RL 的核心挑战已经不只是算法

很多人谈 RL 时会首先关注：

- PPO
- GRPO
- DAPO
- RLOO

但到了 Agentic RL，这些只是一部分。

真正复杂的系统问题包括：

```text
Environment
Rollout
Sandbox
Trajectory
Tool
Scheduler
Inference
Training
Reward
Evaluation
Observability
```

尤其 Multi-turn Agent。

## 为什么 Async Rollout 变得越来越重要？

普通 Reasoning：

```text
Request
 ↓
Model
 ↓
Output
```

耗时虽然不同，但差距往往有限。

Agent 完全不同，例如：

```text
Agent A → Search → 2 秒
Agent B → Compile → 15 秒
Agent C → Sandbox → 40 秒
Agent D → Browser → Timeout 60 秒
```

如果 rollout 是同步的，资源利用率会非常差。

所以 Agentic RL 很自然会走向：

```text
Async Rollout
```

verl 的 Agentic RL 文档已经强调 server-based rollout：

- [verl Agentic RL](https://verl.readthedocs.io/en/latest/start/agentic_rl.html)

AReaL 则更进一步追求 Fully Asynchronous：

- [AReaL Paper](https://arxiv.org/abs/2505.24298)

这本质上已经是：

> 一个经典的 Distributed Systems 问题。

---

# 十五、Environment-as-a-Service 会成为重要基础设施

随着 Sandbox 和 Agentic RL 越来越融合，一层新的基础设施正在出现：

> **Environment as a Service**

它的 API 可能类似：

```python
env = create_env(
    image="ubuntu",
    cpu=8,
    memory="16G"
)

obs = env.reset(task)

while not done:
    action = agent(obs)
    obs = env.step(action)

env.destroy()
```

底层可能使用：

```text
Scheduler
 ↓
Kubernetes
 ↓
Container / Kata / Firecracker / VM
```

当规模进一步扩大：

```text
Environment Pool
 ↓
Thousands of Sandboxes
 ↓
Agent Rollouts
 ↓
Trajectories
 ↓
Reward
 ↓
RL Training
```

这时候 Env 平台不再只是执行服务。

它同时服务于：

- Training
- Evaluation
- Benchmark
- Production Agent
- Data Generation

---

# 十六、2026：Agent Harness 与 Compute 开始解耦

另一个非常重要的趋势是：

> Agent 的“智能逻辑”和“执行计算”逐渐分离。

OpenAI 在 Agents SDK 演进中越来越强调这种架构。

相关资料：

- [The next evolution of the Agents SDK](https://openai.com/index/the-next-evolution-of-the-agents-sdk/)

可以简单理解为：

Agent Harness 管：

```text
Planning
Context
Tool Loop
Memory
Agent Behavior
```

Sandbox / Compute 管：

```text
Processes
Filesystem
Network
Isolation
CPU
Memory
Runtime
```

这其实非常像 Kubernetes：

```text
Control Plane
 ↓
Container Runtime
```

未来 Agent 系统可能变成：

```text
Agent Control Plane
 ↓
Agent Runtime / Sandbox
```

---

# 十七、Agent 不再是一个实例，而会成为大规模 Worker

Coding Agent 已经展示出明显趋势：一个用户可能同时启动多个 Agent。

```text
             Agent A
           /
User → Supervisor → Agent B
           \
             Agent C
```

或者：

```text
Task Queue
 ↓
Agent Scheduler
 ↓
┌──────────┬──────────┬──────────┐
Agent 1    Agent 2    Agent 3
 ↓          ↓          ↓
Sandbox    Sandbox    Sandbox
```

OpenAI Codex 也越来越强调：

- Parallel Agents
- Background Tasks
- Cloud Environments
- Long-running Work

官方：

- [OpenAI Codex](https://openai.com/codex/)

这个结构越来越像 Kubernetes Job。

因此未来 Agent Runtime 很可能需要和今天的容器编排系统一样处理：

- Scheduling
- Retry
- Isolation
- Resource Quota
- Job State
- Logs
- Artifacts
- Multi-tenancy

---

# 十八、Agent Platform 最终可能长什么样

未来 Agent Platform 可能逐渐收敛成类似下面的架构：

```text
                  Agent Platform
                        │
         ┌──────────────┼──────────────┐
         ↓              ↓              ↓
    Orchestrator      Memory        Tracing
         │
         ↓
      Harness
         │
   ┌─────┼────────┐
   ↓     ↓        ↓
  MCP   Shell   Browser
   │
   ↓
Sandbox Runtime
   │
 ┌─┴─────────────────────────┐
 ↓           ↓        ↓      ↓
K8s    Firecracker   VM   Container
 ↓
Compute
```

然后再往上连接：

```text
Evaluation
Trajectory
Reward
Dataset
RL Training
```

最终形成：

```text
             Agent Platform
                   │
        ┌──────────┴──────────┐
        ↓                     ↓
 Production Agent        RL Training
        │                     │
        └──── Environment ────┘
```

---

# 十九、训练和生产可能共用同一套 Environment

这会是未来非常重要的一步。

过去 Training Infra 和 Production Agent Infra 往往完全分离。

但 Agentic RL 时代，它们可能逐渐合并。

因为 Training 和 Production Agent 都需要：

- Tool
- Browser
- Sandbox
- File System
- API
- Environment State

因此未来可以变成：

```text
               Environment Platform
                     │
        ┌────────────┴────────────┐
        ↓                         ↓
     RL Rollout             Production Agent
```

AReaL 等系统已经在推动这种统一 Training / Deployment 的理念。

项目：

- [AReaL Agentic RL Tutorial](https://github.com/areal-project/AReaL/blob/main/docs/en/tutorial/agentic_rl.md)

---

# 二十、AI 行业正在从 Model-Centric 走向 System-Centric

如果把整个趋势重新总结一次，可以看到非常明显的层级增长。

## 2023

```text
Model
```

模型能力几乎等于产品能力。

## 2024

```text
Model
+
RAG
+
Tools
+
Multimodal
```

## 2025

```text
Model
+
Reasoning
+
Agent Harness
+
Tools
+
MCP
```

## 2026

```text
Model
+
Agent
+
Runtime
+
Sandbox
+
Memory
+
Tools
+
MCP
+
Tracing
+
Evaluation
+
RL
+
Compute
```

模型仍然非常重要，但决定一个 Agent 产品能不能真正落地的，已经不只是模型。

越来越多价值开始进入：

> **System Engineering。**

---

# 二十一、2025—2026 Agentic RL 的三个阶段

## 2025 上半年：Reasoning RL

核心：

```text
Prompt
 ↓
Model
 ↓
Reasoning
 ↓
Answer
 ↓
Verifier
```

重点集中在：

- Math
- Coding
- GRPO
- RLVR
- Reasoning

DeepSeek-R1 是典型代表。

## 2025 下半年：Agentic RL

任务开始变成：

```text
Agent
 ↓
Multi-turn Interaction
 ↓
Tool
 ↓
Environment
 ↓
Trajectory
```

关注点开始变成：

- Multi-turn RL
- Tool Use RL
- Search RL
- Coding RL
- Long-horizon task
- Agent Environment

例如：

- [verl-agent](https://github.com/langfengq/verl-agent)

## 2026：Agent Learning Platform

当前的方向已经开始不满足于 RL Framework，而是逐渐向 Agent Training Platform 演进。

包含：

```text
Agent Framework
+
Environment
+
Sandbox
+
Rollout
+
Trajectory
+
Tooling
+
Evaluation
+
Observability
+
Training
```

未来这一层可以称为：

> **Agent Learning Infrastructure**

---

# 二十二、未来真正值得关注的三个 Infra 方向

## 方向一：Agent Sandbox / Agent Compute

核心关键词：

```text
Firecracker
Kata Containers
Kubernetes
Container
VM
Snapshot
Warm Pool
Isolation
Network
Secrets
Filesystem
GPU
```

它解决的是：

> Agent 到底运行在哪里？

## 方向二：Agent Runtime / Agent Platform

核心关键词：

```text
Agent Lifecycle
Task Scheduling
Multi-Agent
MCP
Tool Registry
Memory
Workflow
Observability
Tracing
Background Agent
```

可以简单理解成：

> **Agent 的 Kubernetes。**

## 方向三：Agentic RL Environment Platform

关键词：

```text
Environment-as-a-Service
Rollout
Trajectory
Reward
Verifier
Async Sampling
Dataset
Replay
Evaluation
Training
```

它负责解决：

> Agent 如何在大规模环境中训练、探索和评测。

---

# 二十三、这三个方向最终可能合并成 Agent Cloud

长期来看，三条路线极有可能收敛。

最终架构可能是：

```text
                   Agent Cloud
                       │
   ┌───────────┬───────┼───────────┐
   ↓           ↓       ↓           ↓
 Agent       Sandbox   Tools      Memory
 Runtime       │       │           │
               ↓       ↓           ↓
          Environment / Computer
                   │
                   ↓
                Rollout
                   ↓
              Trajectory
                   ↓
                  RL
```

现在一些看似完全不同的公司和项目：

- OpenAI
- Anthropic
- Google
- E2B
- Daytona
- verl
- AReaL

其实正在从不同方向向同一套基础设施收敛。

云厂商从 Agent Runtime 往下做 Sandbox；RL Framework 从 Trainer 往上做 Agent Service；Sandbox 公司从 Secure Execution 往上做 Agent Compute。

最终的交汇点，就是：

> **Agent Cloud / Agent Learning Infrastructure**

---

# 二十四、一个值得长期记住的判断

过去三年的 AI Infra 大致经历了：

```text
2023
Model Infra

2024
Inference + RAG + Multimodal Infra

2025
Agent Infra

2026
Agent Runtime + Sandbox + Agentic RL Infra
```

因此未来几年，一个很可能持续扩大的领域是：

> **Agent Runtime + Sandbox + Environment + Agentic RL**

但真正有价值的方向，不只是“做一个 Sandbox”。

而是把：

```text
Compute
+
Isolation
+
Environment
+
Tool
+
Agent Lifecycle
+
Trajectory
+
Evaluation
+
RL Rollout
```

连成一个统一平台。

从这个角度看，AI 行业正在走一条非常类似云计算历史的路线：

```text
Physical Machine
 ↓
Virtual Machine
 ↓
Container
 ↓
Kubernetes
 ↓
Cloud Native
```

而 Agent 世界可能会走成：

```text
LLM
 ↓
Tool Calling
 ↓
Agent
 ↓
Agent Runtime
 ↓
Sandbox
 ↓
Agent Platform
 ↓
Agent Cloud
```

如果说过去十年 Kubernetes 解决的是：

> **如何管理应用。**

那么未来的 Agent Platform 很可能要解决：

> **如何管理数字智能体。**

而 Agentic RL 则解决更进一步的问题：

> **如何让这些数字智能体通过真实环境中的持续交互，不断变得更强。**

这很可能就是 2026 年之后 AI Infra 最值得持续追踪的一条主线。
