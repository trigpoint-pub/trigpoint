Canonical: https://trigpoint.pub/zh-Hans/collections/software-systems-architecture/  
Captured: 2026-11-02T21:27:08.166299+08:00

> 公开理论阅读镜像。验证层及 Lab 案例请到原站阅读。

# 软体与系统架构

Software & Systems Architecture · 替一个知识系统选结构

「软体架构是写程式的人才需要的」：是误读。

你每天都在替一个知识系统选结构：真相放哪、派生怎么来、边界划哪、谁决定边界。这个领域把这几题各问了几十年，答案不在程式码里，在取舍里。

## 节点序列

建议阅读次序 · 真相住哪、派生怎么来、边界划哪、边界跟着谁走、分散之后放弃什么、当读写两端都是模型

### § 真相住在哪里

段内序：先立原则 → 再看它在资料层怎么落地 → 最后看一个被误读成它的祖宗

### [不重复原则](dry-pragmatic-programmer-1999.md)

Don't Repeat Yourself (DRY) · Hunt & Thomas (1999)

原则的原文说的是：每一块知识在系统里只能有一个明确而权威的表述。

### [单一真相来源](single-source-of-truth-concept-history.md)

Single Source of Truth (concept history) · Devlin & Murphy (1988) → Loshin (2008)

单一真相来源说的是：每个元素只在一处被维护，其他地方全部引用它。

### [模型视图控制器](mvc-reenskaug-1979.md)

Model-View-Controller (MVC) · Reenskaug (1979)

把资料与画面分开，让同一批资料可以有多个同步的呈现。

### § 派生的东西怎么来

段内序：事实源怎么存 → 读的那一面可以是另一个模型。两者常被绑售，而两个原始出处都说可以分开

### [事件溯源](event-sourcing-fowler-2005.md)

Event Sourcing · Fowler (2005)

把每一次变更存成一笔不可改的事件，当前状态改由重播那串事件得出。

### [命令查询职责分离](cqrs-young-2010.md)

Command Query Responsibility Segregation (CQRS) · Young (2010) / Meyer CQS (1988)

更新资讯用的模型，不必等于读取资讯用的模型。

### § 边界划在哪里

段内序：先给选址判准（成本结构，不是功能归类）→ 再给语言边界 → 最后给依赖方向

### [模组化与薄切面](modularity-baldwin-clark-2000.md)

Modularity & Thin Crossing Points · Baldwin & Clark (2000) / Baldwin (2008)

边界该开在哪，不是照功能分类决定，是照往来成本决定。

### [领域驱动设计](domain-driven-design-evans-2003.md)

Domain-Driven Design (DDD) · Evans (2003)

复杂度的主战场在领域本身，不在技术层。

### [六角架构](hexagonal-architecture-cockburn-2005.md)

Hexagonal Architecture (Ports and Adapters) · Cockburn (2005)

核心宣告它需要什么样的对话，技术来实作那组介面。

### § 边界跟着谁走

段内序：先看约束（结构一定会镜像沟通路径）→ 再看可以怎么设计（接口显式化，且预期关系会演化）

### [康威定律](conways-law-conway-1968.md)

Conway's Law · Conway (1968)

设计系统的组织，会产出镜像自身沟通结构的设计。

### [团队拓扑](team-topologies-skelton-pais-2019.md)

Team Topologies · Skelton & Pais (2019)

团队之间的关系要像介面一样被明确宣告，而不是靠默契。

### § 分散之后你放弃了什么

段内序：先看决定（拆）→ 再看代价（定理）→ 最后看一个明文反过来的立场。本段压轴回头改写第一段，这是本架不是教条的证据

### [微服务](microservices-lewis-fowler-2014.md)

Microservices · Lewis & Fowler (2014)

把一个应用拆成一组各自独立上线的服务，于是部署与扩充的单位变小。

### [CAP 定理](cap-theorem-brewer-2000.md)

CAP Theorem · Brewer (2000) / Gilbert & Lynch (2002)

网路分区发生时，一致与可用只能选一个。

### [资料网格](data-mesh-dehghani-2022.md)

Data Mesh · Dehghani (2019, 2022)

规模上来之后，维持一个全域统一的正典模型会让那个模型变成瓶颈。

### § 当读写两端都是模型

段内序：先看外挂证据 → 再看它为什么还是会坏 → 再看坏在哪两个轴 → 最后看最高危的那一类。本段同时是全架诚实层锚点：它把本站自己的把关动作摊出来

### [检索增强生成](retrieval-augmented-generation-lewis-2020.md)

Retrieval-Augmented Generation (RAG) · Lewis et al. (2020)

把模型的记忆拆成两层：压在权重里的，与生成当下才去取的。

### [生成幻觉](llm-hallucination-ji-2023.md)

Hallucination in NLG · Ji et al. (2023)

幻觉是生成流畅却不忠于来源或不知所云。

### [忠实性与事实性](faithfulness-factuality-maynez-2020.md)

Faithfulness vs Factuality · Maynez et al. (2020)

忠实问的是这段话有没有被来源支持，事实问的是它对世界是不是真的。

### [虚构引用](fabricated-citations-walters-wilder-2023.md)

Fabricated Citations · Walters & Wilder (2023)

引用的格式完整逼真，而它指向的东西不存在。

引用格式：Trigpoint，〈软体与系统架构书架〉，trigpoint.pub/zh-Hans/collections/software-systems-architecture/ · © Strategitect Limited.

---

[English](../../../en/collections/software-systems-architecture/README.md) · [繁體中文](../../../zh-Hant/collections/software-systems-architecture/README.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hans/collections/software-systems-architecture/) · [Citation and versions](../../../READING.md)
