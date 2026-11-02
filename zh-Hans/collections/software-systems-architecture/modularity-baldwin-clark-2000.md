Canonical: https://trigpoint.pub/zh-Hans/collections/software-systems-architecture/modularity-baldwin-clark-2000  
Captured: 2026-11-02T21:27:43.233462+08:00

> 公开理论阅读镜像。验证层及 Lab 案例请到原站阅读。

「照功能切就是好边界」：没这么简单。

# 模组化与薄切面

Modularity & Thin Crossing Points · Baldwin & Clark (2000) / Baldwin (2008)

书目已核 ✓  
软体架构 · 边界选址  
先读：不重复原则

## 三句讲透

边界该开在哪，不是照功能分类决定，是照往来成本决定。  
判准是一句话：这个切面上的往来，容不容易定义、计数与计价。  
不容易，就不要在这里开接口。

![边界选址象限示意：横轴为往来是否容易定义与计价，纵轴为往来频繁与反复程度；容易计价且往来稀疏处为薄切面，接口应开此处](assets/modularity-baldwin-clark-2000.github.svg)

<strong>图 1</strong> · 两个轴决定边界该开在哪：横轴是这个切面上的往来容不容易定义与计价，纵轴是往来的频繁与反复程度。  
右下那格是薄切面，接口开在那里最便宜；左上那格是稠密区，硬开接口等于把摩擦制度化。  
中间是连续的，不是两格。

## 一、发生什么事

模组化的直觉很老：把复杂系统切成几块，各块内部自理、块之间靠约定往来。1962 年那篇讲近可分解性[\[3\]](#reference-note-3)、1972 年那篇讲资讯隐藏[\[4\]](#reference-note-4)，本站举为这条线上的祖先之例。

2000 年那本书做的是另一件事：<strong>把模组化从工程直觉升为经济理论</strong>[\[1\]](#reference-note-1)。核心结构是把设计资讯分两类：可见的设计规则（大家都要遵守的约定）与隐藏在模组内部的实作。这一分之后，每个模组就变成一份可以独立替换的实质选择权：你可以只换其中一块去试，而不必动整体。模组化的价值因此不只是「好维护」，而是<strong>可以用低成本做很多次局部实验</strong>。

而真正把判准说死的是 2008 年那篇。它问了一个更前面的问题：边界为什么落在这里而不是那里。答案是往来成本：任务网络里那些<strong>往来容易定义、容易计数、容易付价</strong>的地方，其琐碎交易成本一般偏低，而模组边界（乃至公司边界）就对应这些地方[\[2\]](#reference-note-2)。那些往来稠密、反复迭代、难以计价的区域，硬在中间开一个接口，等于把摩擦制度化。

这个判准有一个很实用的性质：<strong>它可以在你动手之前用</strong>。功能分类要等系统存在才看得出来，往来成本可以先观察。你不需要先切错一次才知道哪里该切。

<strong>署名要给对：</strong>概念祖，本站举 Simon（1962，近可分解性）[\[3\]](#reference-note-3)与 Parnas（1972，资讯隐藏）[\[4\]](#reference-note-4)为例；模组化之经济形式化与选择权价值归 Baldwin 与 Clark（2000）[\[1\]](#reference-note-1)；<strong>薄切面与琐碎交易成本这组判准归 Baldwin（2008）</strong>，本页核心那句取自该篇摘要逐字[\[2\]](#reference-note-2)。四段要分开署名：把「模组化」整个概念归给 2000 年那本书，会抹掉早它三、四十年的祖先（如这两位），这是本站在此页明文更正的一条。

## 二、为什么这对你重要

你每天在做的边界决定，多数是按「这件事属于哪一类」在切。这页要你换成按「这个交接贵不贵」在切。

差别最明显的地方是把工作交给模型。假设你要把一段工作切出去：如果那个切面上的往来是「我给一份明确的输入，它回一份明确的输出，我看得出对不对」，那是薄切面，交出去很便宜，因为交接本身可以被定义和验收。如果那个切面上的往来是「我得先解释一堆背景、来回澄清好几轮、而且我没有简单方法判断结果对不对」，那是稠密区：在这里开接口，你会把大部分时间花在维护那个接口上。

同一个判准也解释了一件常见的挫折：为什么有些工作外包出去反而更慢。不是对方不行，是<strong>你把边界开在了往来稠密的地方</strong>。

三个可以直接用的问句，都是判准的直译。第一，这个交接的产出，我讲不讲得清「什么样算完成」。第二，我验收它要花多少时间，比自己做省不省。第三，这条线上一周会来回几次：如果答案是「很多次而且每次都要重新解释」，那条线就不该在那里。

## 常见误读

所属页核验：书目已核 ✓ · 内容最后修订 2026-10-25

- 常见转述「模组化是这两位作者提出的」：概念至少早了三、四十年（例：1962 年的近可分解性、1972 年的资讯隐藏）。这两位的贡献是经济形式化，边界选址理论则见其中一位 2008 年那篇。引用时勿误植概念原创。
- 常见转述「薄与厚是两类，判断就是分类」：原文的判准是往来的密度与复杂度，以及界定、计数、付价各要花多少功夫，这些都是程度问题，判定需要实际的往来观察。把它当二分法会让人凭印象分类。

## 参考文献

<strong>如何阅读来源注记</strong> 「书目经…核对」指作者、年份、题名与出版项已确认；不代表该来源的主张已被核对。「与摘要一致」指主张与论文摘要相符；不含逐句对照全文。「依多源一致转述」指主张建立于多份彼此一致、转述该来源的资料，而非原文件本身。 定义版本：2026-09-20。

- \[1\] Baldwin, C. Y. & Clark, K. B. (2000). Design Rules, Volume 1: The Power of Modularity. MIT Press. ISBN 978-0-262-02466-2.
- \[2\] Baldwin, C. Y. (2008). Where Do Transactions Come from? Modularity, Transactions, and the Boundaries of Firms. Industrial and Corporate Change, 17(1), 155–195.
- \[3\] Simon, H. A. (1962). The Architecture of Complexity. Proceedings of the American Philosophical Society, 106(6), 467–482.
- \[4\] Parnas, D. L. (1972). On the Criteria To Be Used in Decomposing Systems into Modules. Communications of the ACM, 15(12), 1053–1058.

## 知识图谱

- [<em>前置 ▸</em>康威定律（Conway's Law）](conways-law-conway-1968.md)
- [<em>应用于 ▸</em>微服务（Microservices）](microservices-lewis-fowler-2014.md)
- [<em>应用于 ▸</em>领域驱动设计（Domain-Driven Design (DDD)）](domain-driven-design-evans-2003.md)

引用格式：Trigpoint，〈模组化与薄切面〉，trigpoint.pub/zh-Hans/collections/software-systems-architecture/modularity-baldwin-clark-2000 · © Strategitect Limited. · 内容最后修订 2026-10-25

## 来源注记

<a id="reference-note-1"></a>

**[1]** Baldwin, C. Y. & Clark, K. B. (2000). Design Rules, Volume 1: The Power of Modularity. MIT Press. ISBN 9780262024662. 书目经双源核对。设计规则与隐藏模组之分及其选择权价值依多源一致转述。把模组化从工程直觉升为经济理论：可见的设计规则与隐藏的模组分离，模组因此构成一组实质选择权。书内内容本页只核到多份一致的转述。

<a id="reference-note-2"></a>

**[2]** Baldwin, C. Y. (2008). Where Do Transactions Come from? Modularity, Transactions, and the Boundaries of Firms. Industrial and Corporate Change, 17(1), 155–195. 书目经官方记录核对。要旨与摘要一致。摘要原句之中译：那些工作的成本（称为 mundane transaction costs）在任务网络的 thin crossing points 上一般偏低，而这些点对应模组边界。

<a id="reference-note-3"></a>

**[3]** Simon, H. A. (1962). The Architecture of Complexity. Proceedings of the American Philosophical Society, 106(6), 467–482. 书目经双源核对。近可分解性之归属依多源一致转述。近可分解性：本站标为概念祖之一，早于本节点锚点约四十年。

<a id="reference-note-4"></a>

**[4]** Parnas, D. L. (1972). On the Criteria To Be Used in Decomposing Systems into Modules. Communications of the ACM, 15(12), 1053–1058. 书目经官方记录核对。资讯隐藏之归属依多源一致转述。资讯隐藏：本站标为另一位概念祖。

---

[English](../../../en/collections/software-systems-architecture/modularity-baldwin-clark-2000.md) · [繁體中文](../../../zh-Hant/collections/software-systems-architecture/modularity-baldwin-clark-2000.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hans/collections/software-systems-architecture/modularity-baldwin-clark-2000) · [Citation and versions](../../../READING.md)

[Original SVG](assets/modularity-baldwin-clark-2000.svg) · Display copy adds a white background only.
