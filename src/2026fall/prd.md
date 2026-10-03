
# CourseShelf 产品需求说明书

**版本：** v1.1
**目标用户：** 本科生
**产品形态：** 本地桌面应用
**建议开发周期：** 1–2 学期

## 1. 产品定义

**CourseShelf 是一个了解学生整体学习状态，并告诉学生下一步该学什么的 AI 学习助手。**

它连接学生的课程、课程材料和个人学习记录，持续回答四个问题：

> **课程讲到哪里了？**
> **我自己学到哪里了？**
> **我哪里正在落下？**
> **我现在应该学什么？**

CourseShelf 不替代课程平台、文件管理器或笔记软件，而是在它们之上增加一层**个人学习状态**。

---

# 2. 要解决的问题

## 2.1 学习被 Deadline 驱动

本科生通常很清楚：

> 周五要交 Homework 3。

却不一定清楚：

> 这门课已经讲到哪里？
> 前几周的内容我真正理解了多少？

学生容易把“按时完成作业”等同于“课程学得不错”，学习状态往往到考试前才集中暴露。

---

## 2.2 缺少对整个学期的整体把握

一个学生同时学习多门课程。

不同课程可能分别处于：

> 跟得上
> 学过但没弄懂
> 落后一两周
> 很久没有继续

这些状态通常没有一个地方能够统一看到。

CourseShelf 要让学生打开软件就知道：

> **我这个学期整体处于什么状态。**

---

## 2.3 不知道现在应该从哪里开始

没有迫近的作业或考试时，学生经常不知道：

> 现在应该学哪门课？
> 应该继续新内容还是补旧内容？
> 哪一块最值得现在花时间？

CourseShelf 根据课程进度和个人学习状态，给出一个明确、可执行的 **Next Step**。

---

## 2.4 学习缺少及时的紧迫感

“没有理解一个 Topic”通常没有 Deadline，因此很容易不断推迟。

CourseShelf 应把这种差距变得可见：

> **Quantum Mechanics**
>
> 课程：Week 7
> 你的进度：主要停留在 Week 5
> 2 个 Topic 尚未完成学习检查
>
> **建议今天继续 Time Evolution**

紧迫感来自真实学习差距，而不是积分、排行榜或人为制造焦虑。

---

# 3. 核心产品模型

产品围绕四个核心概念：

> **Course → Topic → Learning State → Next Step**

材料是 Topic 的学习资源：

> **Topic → Materials**

AI 根据这些信息形成学生当前的学习状态：

```text
课程实际进度
      +
Topic 状态
      +
学习记录
      +
课程材料
      ↓
Student Learning State
      ↓
Next Step
```

---

# 4. 核心页面

产品第一版只需要四个主要页面：

## Today

整个学期的学习状态，以及今天最值得推进的内容。

## Courses

查看每门课程的学习路线和进度。

## Topic

实际学习某个知识主题。

## Materials

查看课程材料。

全局提供：

> **Ask Shelf**

用于自然语言操作和学习辅助。

---

# 5. Today

Today 是默认首页，也是产品最重要的页面。

顶部首先给出：

> ## Today
>
> **建议先继续 Quantum Mechanics**
>
> 课程已经进入 Week 7，你主要停留在 Week 5。
>
> **Time Evolution · 约 25 min**
>
> 1. 回顾上次留下的理解
> 2. 完成一个尚未覆盖的问题
> 3. 完成后进入 Angular Momentum
>
> **Continue →**

下面显示所有课程：

| Course            | Course Progress | My Progress | State  |
| ----------------- | --------------- | ----------- | ------ |
| Quantum Mechanics | Week 7          | Week 5      | 落后   |
| Algorithms        | Week 6          | Week 6      | 正常   |
| Linear Algebra    | Week 7          | Week 7      | 正常   |
| Statistics        | Week 6          | Week 4      | 待继续 |

重点不是给学生打分，而是让学习差距可见。

---

# 6. Course

每门课程使用简单 Learning Path：

```text
Quantum Mechanics

● Quantum States
│
● Operators
│
● Measurement
│
◐ Time Evolution       ← YOU ARE HERE
│
○ Angular Momentum
│
○ Perturbation Theory
```

Topic 只需要三种基本状态：

**○ 未开始**

**◐ 学习中**

**● 完成过学习检查**

同时显示：

> **课程目前：Angular Momentum**
> **你的学习：Time Evolution**

从而形成“课程在哪里 / 我在哪里”的对照。

第一版不做复杂二维知识图谱。

---

# 7. Topic

Topic 是主要学习页面。

例如：

## Time Evolution

### 需要理解

* Schrödinger equation 描述什么？
* Hamiltonian 起什么作用？
* 为什么 time evolution 是 unitary？

### 学习材料

> Lecture 07.pdf
> Textbook Chapter 2.pdf
> My Notes.md

材料仍保存在电脑原位置，CourseShelf 只建立索引。

### 我的理解

学生可以简单记录：

> “Time evolution 可以理解为由 Hamiltonian 生成的 unitary transformation……”

### AI 学习助手

提供：

> **解释这一块**
> **根据我的材料考我**
> **我哪里还没讲清？**

完成一次检查后记录：

> ✓ Oct 2 完成学习检查

并更新 Topic 状态。

---

# 8. AI 与 Agent

AI 是 CourseShelf 的核心能力之一，而不是独立聊天功能。

Shelf 主要完成五件事：

### ① 理解材料

读取课程材料，建议它属于哪个 Topic。

### ② 理解学习状态

综合课程进度、Topic、学习记录和材料，判断学生目前在哪里。

### ③ 给出 Next Step

回答：

> **我现在最值得学什么？**

并说明原因。

### ④ 辅助学习

只根据当前课程材料：

> 解释概念
> 回答问题
> 生成学习检查问题
> 指出学生解释中的缺口

### ⑤ 执行操作

用户可以说：

> “继续量子力学。”

> “考我一下 Time Evolution。”

> “这份课件放到 Angular Momentum。”

Agent 调用 CourseShelf 内部功能完成对应操作。

---

# 9. AI 的边界

遵守三个原则：

### AI 可以理解和建议

例如：

> “Lecture08.pdf 很可能属于 Angular Momentum。”

### 重要修改由用户确认

例如：

> 新建 Topic
> 修改课程结构
> 将材料关联到 Topic

### AI 不能自己判断学生“掌握了”

完成状态必须存在真实的 **Learning Evidence**，例如：

> 学生自己的解释；
> 一次学习检查；
> 一次复习记录。

AI 可以分析这些证据，但不能凭空生成学习状态。

---

# 10. Ask Shelf

全局提供：

> **Ask Shelf...**

支持：

> “我今天应该学什么？”

> “量子力学落下多少了？”

> “继续 Algorithms。”

> “解释一下这个 Topic。”

> “考我一下 Time Evolution。”

> “这份课件应该放哪里？”

自然语言成为操作软件的第二种方式。

---

# 11. 文件与材料

CourseShelf **不是文件管理器**。

学生继续使用原来的课程目录：

```text
University/
├── Quantum Mechanics/
├── Algorithms/
└── Linear Algebra/
```

CourseShelf 只：

> 读取用户授权的目录；
> 建立材料索引；
> 提取必要文本；
> 将材料关联到 Course / Topic。

不移动、不复制、不删除原文件。

第一版支持：

> PDF、PPTX、DOCX、Markdown、TXT。

---

# 12. 本地数据

核心数据保存在本地：

```text
Course
Topic
Material
UserNote
LearningRecord
```

第一版无需注册账户。

AI 的长期“记忆”来自这些结构化数据，而不是依赖聊天历史。

---

# 13. 第一学期开发范围

目标是完成基本产品闭环：

```text
创建课程
↓
关联课程目录
↓
建立 Topic
↓
记录课程当前进度
↓
记录个人学习状态
↓
Today 展示整体学习状态
↓
生成 Next Step
↓
进入 Topic 学习
↓
AI 基于材料问答 / 出题
↓
保存 Learning Record
↓
学习状态更新
```

AI 第一阶段只要求：

1. **基于材料问答**
2. **生成 Topic 学习检查**
3. **简单 Next Step 建议**

Next Step 第一版可以主要使用规则生成，不必全部交给 LLM。

---

# 14. 第二学期开发范围

第二阶段增强 AI Agent：

### Material Understanding

自动分析新材料并建议 Topic。

### Semantic Search

根据内容而不是准确文件名检索材料。

### Learning Agent

用户说：

> “今晚有 30 分钟，帮我继续量子力学。”

Agent 自动：

```text
读取课程进度
↓
读取个人学习状态
↓
发现主要 Gap
↓
读取上次 Learning Record
↓
生成学习计划
↓
进入对应 Topic
↓
完成学习检查
↓
更新 Learning Record
```

### Knowledge Gap Detection

发现：

> 课程已经进入新的 Topic，但学生之前的关键 Topic 仍没有完成学习检查。

并提出学习建议。

---

# 15. 明确不做

1–2 个学期内不做：

* 云同步；
* 手机 App；
* 社交和排行榜；
* 经验值系统；
* LMS 自动同步；
* 完整笔记软件；
* Zotero 替代；
* 全专业知识图谱；
* 复杂二维 Graph；
* 自动完成作业；
* AI 自动决定学生已经掌握；
* 复杂多 Agent 系统。

重点是把一个闭环做好，而不是增加功能数量。

---

# 16. 项目验收

邀请 3–5 名真实本科生使用自己的课程进行测试。

要求他们能够完成：

1. 添加至少 3 门真实课程；
2. 建立课程 Topic；
3. 标记“课程讲到哪里”和“自己学到哪里”；
4. 从 Today 看出自己当前整体学习状态；
5. 根据 Next Step 开始一次学习；
6. 在 Topic 中使用自己的材料与 AI 学习；
7. 完成一次 AI 学习检查；
8. 重新打开软件后，Shelf 仍然知道其学习状态。

---

# 17. 最终目标

CourseShelf 不应该让学生每天打开软件只是为了看：

> **“还有什么作业没交？”**

而应该让学生看到：

> **“这个学期整体学到哪里了？”**

并进一步得到：

> **“我现在最值得推进的是这一块。”**

最终希望一个学生使用一段时间后能够产生这样的感受：

> **“即使现在没有 Deadline，我也知道自己哪里落下了，以及下一步该学什么。”**

这就是 CourseShelf 第一版最重要的产品价值。
