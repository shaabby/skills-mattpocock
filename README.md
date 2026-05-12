<p>
  <a href="https://www.aihero.dev/s/skills-newsletter">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skills-repo-dark_2x.png">
      <source media="(prefers-color-scheme: light)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png">
      <img alt="Skills" src="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png" width="369">
    </picture>
  </a>
</p>

# 给真正工程师用的 Skills

[![skills.sh](https://skills.sh/b/mattpocock/skills)](https://skills.sh/mattpocock/skills)

我每天都在用的 agent skills，用来做真正的工程——不是 vibe coding。

开发真正的应用是件难事。GSD、BMAD 和 Spec-Kit 这类方法试图通过掌控流程来提供帮助。但这样做时，它们剥夺了你的控制权，并且让流程中产生的 bug 难以解决。

这些 skills 被设计得小巧、易于修改和组合。它们适用于任何模型。它们基于数十年的工程经验。随意修改它们。把它们变成你自己的。尽情享受。

如果你想跟进这些 skills 的更新，以及我创建的任何新 skill，可以加入我 newsletter 上的约 60,000 名开发者：

[订阅 Newsletter](https://www.aihero.dev/s/skills-newsletter)

## 快速开始（30 秒配置）

1. 运行 skills.sh 安装器：

```bash
npx skills@latest add mattpocock/skills
```

2. 选择你想要的 skills，以及你想将它们安装到哪些编码 agent 上。**确保你选择了 `/setup-matt-pocock-skills`**。

3. 在你的 agent 中运行 `/setup-matt-pocock-skills`。它会：
   - 询问你想使用哪个 issue 追踪器（GitHub、Linear 或本地文件）
   - 询问你在分类 issue 时使用什么标签（`/triage` 会用到标签）
   - 询问你想在哪里保存我们创建的文档

4. 搞定——你可以开始了。

## 这些 Skills 为什么存在

我构建这些 skills 是为了解决我在 Claude Code、Codex 和其他编码 agent 中看到的常见失败模式。

### #1：Agent 没按我的想法做

> "没有人确切知道自己想要什么"
>
> David Thomas & Andrew Hunt，《程序员修炼之道》

**问题**。软件开发中最常见的失败模式是认知偏差。你以为开发者知道你想要什么。然后你看到他们做出来的东西——才发现它根本没理解你。

这在 AI 时代也是一样的。你和 agent 之间存在沟通鸿沟。解决这个问题的方法是**追问式对话**——让 agent 向你提出关于你正在构建的东西的详细问题。

**解决方案**是使用：

- [`/grill-me`](./skills/productivity/grill-me/SKILL.md) — 非编码场景使用
- [`/grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md) — 与 [`/grill-me`](./skills/productivity/grill-me/SKILL.md) 相同，但增加了更多好东西（见下文）

这些是我最受欢迎的 skills。它们帮助你在开始之前与 agent 达成一致，并深入思考你正在做的变更。每次要做变更时都使用它们。

### #2：Agent 太啰嗦了

> 有了通用语言，开发者之间的对话和代码的表达都源于同一个领域模型。
>
> Eric Evans，《领域驱动设计》

**问题**：在项目开始时，开发者和他们为之构建软件的人（领域专家）通常说着不同的语言。

我在我的 agent 身上感受到了同样的张力。Agent 通常被丢进一个项目，被要求在摸索中理解术语。所以它们用 20 个词来表达 1 个词就能说清的事。

**解决方案**是共享语言。这是一份文档，帮助 agent 解读项目中使用的术语。

<details>
<summary>
示例
</summary>

这是我的 `course-video-manager` 仓库中的一个 [`CONTEXT.md`](https://github.com/mattpocock/course-video-manager/blob/076a5a7a182db0fe1e62971dd7a68bcadf010f1c/CONTEXT.md) 示例。哪一个更容易阅读？

- **之前**："当课程中某个章节里的课时被设为'真实'时（即在文件系统中被分配了一个位置），会出现一个问题"
- **之后**："物化级联有一个问题"

这种简洁会在一次次会话中持续产生回报。

</details>

这已内置于 [`/grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md) 中。它是一次追问式对话，但能帮助你与 AI 建立共享语言，并用 ADR 记录难以解释的决策。

很难用语言描述这有多强大。它可能是这个仓库中最酷的技巧。试试看吧。

> [!TIP]
> 共享语言除了减少啰嗦之外还有很多好处：
>
> - **变量、函数和文件的命名保持一致**，使用共享语言
> - 因此，**代码库对 agent 来说更容易导航**
> - Agent 也**花更少的 token 在思考上**，因为它可以使用更简洁的语言

### #3：代码跑不通

> "始终采取小而深思熟虑的步骤。反馈速度就是你的速度上限。永远不要接太大的任务。"
>
> David Thomas & Andrew Hunt，《程序员修炼之道》

**问题**：假设你和 agent 在要构建什么上达成了一致。那当 agent 仍然产出垃圾代码时怎么办？

是时候审视你的反馈循环了。如果对它产出的代码实际运行效果没有反馈，agent 就是在盲目飞行。

**解决方案**：你需要常规的反馈循环组合：静态类型、浏览器访问和自动化测试。

对于自动化测试，红-绿-重构循环至关重要。这是 agent 先写一个失败的测试，然后再修复测试的过程。这有助于给 agent 提供一致的反馈水平，从而产生好得多的代码。

我构建了一个 **[`/tdd`](./skills/engineering/tdd/SKILL.md) skill**，你可以插入任何项目。它鼓励红-绿-重构，并给 agent 提供大量关于什么是好测试和坏测试的指导。

对于调试，我还构建了一个 **[`/diagnose`](./skills/engineering/diagnose/SKILL.md)** skill，将最佳调试实践封装成一个简单的循环。

### #4：我们构建了一团烂泥

> "每天都投入于系统设计。"
>
> Kent Beck，《解析极限编程》

> "最好的模块是深的。它们允许通过简单的接口访问大量功能。"
>
> John Ousterhout，《软件设计的哲学》

**问题**：大多数用 agent 构建的应用都很复杂且难以修改。因为 agent 可以极大地加速编码，它们也加速了软件熵增。代码库以前所未有的速度变得更加复杂。

**解决方案**是一种全新的 AI 驱动开发方法：关心代码的设计。

这已内置于这些 skills 的每一层：

- [`/to-prd`](./skills/engineering/to-prd/SKILL.md) 在创建 PRD 之前会询问你正在修改哪些模块
- [`/zoom-out`](./skills/engineering/zoom-out/SKILL.md) 让 agent 在整个系统的上下文中解释代码

而至关重要的是，[`/improve-codebase-architecture`](./skills/engineering/improve-codebase-architecture/SKILL.md) 帮助你挽救已经变成一团烂泥的代码库。我建议每隔几天在代码库上运行一次。

### 总结

软件工程的基本功比以往任何时候都更重要。这些 skills 是我将这些基本功浓缩为可重复实践的最大努力，帮助你交付职业生涯中最好的应用。尽情享受。

## 参考

### 工程

我日常编码工作中使用的 Skills。

- **[diagnose](./skills/engineering/diagnose/SKILL.md)** — 针对疑难 bug 和性能回归的严谨诊断循环：复现 → 最小化 → 假设 → 埋点 → 修复 → 回归测试。
- **[grill-with-docs](./skills/engineering/grill-with-docs/SKILL.md)** — 深度访谈式对话，用现有领域模型挑战你的计划，精炼术语，并同步更新 `CONTEXT.md` 和 ADR。
- **[triage](./skills/engineering/triage/SKILL.md)** — 通过状态机模型对 issue 进行分类处理。
- **[improve-codebase-architecture](./skills/engineering/improve-codebase-architecture/SKILL.md)** — 在代码库中发现深化机会，以 `CONTEXT.md` 中的领域语言和 `docs/adr/` 中的决策为指导。
- **[setup-matt-pocock-skills](./skills/engineering/setup-matt-pocock-skills/SKILL.md)** — 搭建每个仓库的配置（issue 追踪器、分类标签词汇表、领域文档布局），供其他工程 skills 使用。每个仓库使用 `to-issues`、`to-prd`、`triage`、`diagnose`、`tdd`、`improve-codebase-architecture` 或 `zoom-out` 之前运行一次。
- **[tdd](./skills/engineering/tdd/SKILL.md)** — 以红-绿-重构循环进行测试驱动开发。每次构建一个垂直切片的功能或修复。
- **[to-issues](./skills/engineering/to-issues/SKILL.md)** — 使用垂直切片将任何计划、规格说明或 PRD 拆分为可独立认领的 GitHub issue。
- **[to-prd](./skills/engineering/to-prd/SKILL.md)** — 将当前对话上下文转化为 PRD 并提交为 GitHub issue。无需访谈——直接综合你已经讨论过的内容。
- **[zoom-out](./skills/engineering/zoom-out/SKILL.md)** — 让 agent 跳出细节，对不熟悉的代码段提供更广泛的上下文或更高层次的视角。
- **[prototype](./skills/engineering/prototype/SKILL.md)** — 构建一次性原型来充实设计——可以是用于状态/业务逻辑问题的可运行终端应用，也可以是从同一路由切换的多个截然不同的 UI 变体。

### 生产力

通用工作流工具，不仅限于编码。

- **[caveman](./skills/productivity/caveman/SKILL.md)** — 超压缩沟通模式。通过去除冗余内容将 token 消耗降低约 75%，同时保持完整的技术准确性。
- **[grill-me](./skills/productivity/grill-me/SKILL.md)** — 持续被追问你的计划或设计，直到决策树上的每个分支都被解决。
- **[handoff](./skills/productivity/handoff/SKILL.md)** — 将当前对话压缩为交接文档，以便另一个 agent 可以继续工作。
- **[write-a-skill](./skills/productivity/write-a-skill/SKILL.md)** — 创建结构合理、渐进式呈现、包含打包资源的新 skill。

### 杂项

保留但很少使用的工具。

- **[git-guardrails-claude-code](./skills/misc/git-guardrails-claude-code/SKILL.md)** — 设置 Claude Code hooks 以在执行前阻止危险的 git 命令（push、reset --hard、clean 等）。
- **[migrate-to-shoehorn](./skills/misc/migrate-to-shoehorn/SKILL.md)** — 将测试文件中的 `as` 类型断言迁移为 @total-typescript/shoehorn。
- **[scaffold-exercises](./skills/misc/scaffold-exercises/SKILL.md)** — 创建包含章节、问题、解决方案和解释的练习目录结构。
- **[setup-pre-commit](./skills/misc/setup-pre-commit/SKILL.md)** — 配置 Husky pre-commit hooks，集成 lint-staged、Prettier、类型检查和测试。