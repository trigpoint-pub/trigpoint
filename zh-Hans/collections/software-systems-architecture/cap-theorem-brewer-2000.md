Canonical: https://trigpoint.pub/zh-Hans/collections/software-systems-architecture/cap-theorem-brewer-2000  
Captured: 2026-11-02T21:27:39.533685+08:00

> 公开理论阅读镜像。验证层及 Lab 案例请到原站阅读。

2012 年，原作者撰文说「三选二」一向具误导性。

# CAP 定理

CAP Theorem · Brewer (2000) / Gilbert & Lynch (2002)

已对照来源本身 ✓  
Lab 实测 ✓  
系统设计 · 分散式取舍  
先读：微服务

## 三句讲透

网路分区发生时，一致与可用只能选一个。  
分区不是可以放弃的选项，是环境前提。  
所以真正的问题不是三选二，是分区当下你要哪一边。

![时间轴示意：分区窗口之外一致与可用可同时具备，窗口之内只能二选一，选可用者需在窗口结束后收敛冲突。横轴刻意无刻度与单位](assets/cap-theorem-brewer-2000.github.svg)

<strong>图 1</strong> · 横轴是时间，中间那一段是网路分区发生的窗口。  
窗口之外，只要系统确知没有分区，一致与可用可以同时有；窗口之内，只能二选一，而且选哪一边决定了窗口结束后要不要收敛冲突。  
本图刻意无时间刻度与单位：分区的长短因环境而异，不是本页能给的数字。

## 一、发生什么事

这个说法提出十二年后，原作者自己写了一篇回顾，指流行的讲法把三者之间的张力过度简化。三个性质先讲清楚。一致：每次读都看到最近一次写的结果。可用：每个没故障的节点对每个请求都回一个有效回应。分区容错：即使节点之间的讯息任意遗失或延迟，系统仍运作。

2000 年那场主题演讲提出：三者至多得其二[\[1\]](#reference-note-1)。而那句话的流行版本正是它最大的问题。<strong>因为它把分区容错讲成一个选项</strong>，而在真正的分散式网路里，封包遗失与节点失联一定会发生：分区是环境前提，不是勾选项。

所以正确的形状是这样：分区<strong>没有发生</strong>、而且系统确知没有发生的时候，一致与可用可以同时有，不必取舍。分区<strong>一旦发生</strong>，你只能二选一：要嘛拒绝或阻塞那些会破坏一致的请求（可用下降），要嘛让分区两侧各自继续服务（一致下降，事后再收敛冲突）。

「确知」两个字不是多余的。在讯息延迟没有上界、节点也没有时钟的网路里，讯息迟到与讯息遗失分不出来，所以即使实际上一封都没丢，一个坚持随时回应的系统也保证不了一致[\[4\]](#reference-note-4)。有了时钟，情况就不同：同一篇论文指出，这时存在这样的演算法，讯息全数送达时回传一致的资料，只在讯息遗失时才回传过期资料。实务上的对应是替通讯设一个时间上限，逾时没达成一致，就当作分区处理。

归属这一页必须分三段，而多数转述会压成一段。2000 年那场是<strong>猜想</strong>：其中一张投影片的标题就叫「The CAP Theorem」，正文也以「Theorem:」起首，却没有附任何证明[\[1\]](#reference-note-1)。2002 年另两位作者以「Brewer 的猜想」为题的论文才是<strong>证明</strong>：先在非同步网路模型（无时钟，讯息延迟无上界）下证明，再证明在各节点有时钟的部分同步模型里，只要讯息可能任意遗失，结论依然成立[\[2\]](#reference-note-2)[\[4\]](#reference-note-4)。「定理」这个地位来自那篇，不是 2000 年那场。而 2012 年，原作者本人写了一篇回顾，明说流行的<strong>「三选二」表述一向具误导性</strong>，因为它把三者之间的张力过度简化；并澄清：分区罕见，系统未分区时没有理由放弃一致或可用[\[3\]](#reference-note-3)。

这三段合起来的教训不只关于分散式系统：<strong>一个被广泛引用的说法，其原作者可能十二年后公开说它被读错了，而流行版本仍然继续流行。</strong>

<strong>署名要给对：</strong>取舍之提出归 Brewer（据他 2012 年的回顾，这个定理 1998 年秋首次出现、1999 年见刊，而一致与可用之争更早已以 ACID 对 BASE 的形式见于 1997 年一篇他参与合著的论文[\[3\]](#reference-note-3)；2000 年 7 月那场主题演讲的投影片自称定理而未附证明，文献上称猜想[\[1\]](#reference-note-1)）；<strong>形式证明归 Gilbert 与 Lynch（2002，ACM SIGACT News）</strong>，定理地位来自该篇而非 2000 年那场[\[2\]](#reference-note-2)；对流行误读之澄清归 Brewer 本人（2012）[\[3\]](#reference-note-3)。三段要分开署名，且第三段特别重要：原作者公开说过流行版本误导人。

## 二、为什么这对你重要

只要你有「同一件事在两个地方各自被改」的情况，这页就适用，不需要有伺服器。

最常见的形态：你的笔记或档案在两台装置上、或者你跟协作者各改一份、或者你同时开了几条工作在动同一批东西。网路断了、或你忘了同步、或两边同时在改：这就是分区。而你在那一刻其实已经选了一边，只是通常不是有意识地选。

<strong>选一致长什么样</strong>：非要等同步完成才能继续动（锁住、排队、宁可停下来）。好处是不会有两个版本，代价是你被挡住。

<strong>选可用长什么样</strong>：两边各自继续改，事后再处理冲突。好处是不停工，代价是收敛那一刻你得真的去收敛：而多数人在这一步偷懒，于是留下两个都不完整的版本。

三个可以直接用的判断。

第一，<strong>分区之外不必预先取舍</strong>。这是原作者 2012 年那篇的重点，也是最实用的一句：分区罕见，没分区的时候没有理由放弃一致或可用，不要因为读过这个定理就预先牺牲什么。但「没分区」必须是系统知道的事，不是假设出来的：给同步设一个时限，逾时就当作分区处理，而不是默认网路永远不断。

第二，<strong>取舍可以按面分开做</strong>，不必全系统一刀切。对外发布的东西选一致（宁可排队），内部草稿选可用（各自跑），派生的看板选可用但明标生成时间。

第三，也是最少人做的一条：<strong>选了可用，就要把收敛那一步当成工作排进去。</strong> 选可用不等于不用处理冲突，只是把处理往后推。推而不做，等于既失一致又失可用。

## 常见误读

所属页核验：已对照来源本身 ✓ · 本页版次 v2 · 内容最后修订 2026-10-25

- 常见转述「三个性质里面挑两个」：作者本人 2012 年那篇明说，「三选二」这个表述一向具误导性，因为它把三者之间的张力过度简化；分区罕见，系统未分区时没有理由放弃一致或可用。取舍只在分区当下、局部地发生。
- 常见转述「放弃分区容错也是一个选项」：在真正的分散式网路里分区是环境前提而非可勾选项。同时保一致与可用只在假设分区不会发生时成立，典型是单机或单站点。
- 常见转述「这是 2000 年被证明的定理」：2000 年那场的投影片虽有一张以「定理」为题，却没有附证明；2002 年另两位作者以「Brewer 的猜想」为题的论文才是证明，而且证明绑定特定的网路模型与定义。三件要分开记。

## 修正记录

- 2026-10-09 · 本页前版有三处与原始材料不符，已依原文改正。其一，前版说 2000 年那场的作者不把这个取舍框为定理、来源是运维观察；其中一张投影片其实以「The CAP Theorem」为题，只是没有附证明，「猜想」之名出自 2002 年那篇的标题。其二，前版当作 2012 年那篇作者原句引用的两句话（包括「这个定理具误导性」），实出自第三方读书摘要；作者原文说的是「三选二」这个表述具误导性，不是定理本身。其三，前版把「未分区时一致与可用可以兼得」写成无条件；这只在系统确知没有分区时成立。

## 参考文献

<strong>如何阅读来源注记</strong> 「书目经…核对」指作者、年份、题名与出版项已确认；不代表该来源的主张已被核对。「对照全文核实」指主张已与来源文本本身比对。 定义版本：2026-09-20。

- \[1\] Brewer, E. A. (2000). Towards Robust Distributed Systems. Keynote, ACM PODC, Portland, OR, 19 July 2000. Abstract in Proceedings of PODC '00, p. 7.
- \[2\] Gilbert, S. & Lynch, N. (2002). Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services. ACM SIGACT News, 33(2), 51–59.
- \[3\] Brewer, E. (2012). CAP Twelve Years Later: How the 'Rules' Have Changed. Computer, 45(2), 23–29.
- \[4\] Gilbert, S. & Lynch, N. (2002). Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services. ACM SIGACT News, 33(2), 51–59.
- \[5\] 编辑注，无外部来源；全文见正文注 \[5\]。

## 知识图谱

- [<em>对照 ▸</em>单一真相来源（Single Source of Truth (concept history)）](single-source-of-truth-concept-history.md)

引用格式：Trigpoint，〈CAP 定理〉，trigpoint.pub/zh-Hans/collections/software-systems-architecture/cap-theorem-brewer-2000 · © Strategitect Limited. · 内容最后修订 2026-10-25

## 来源注记

<a id="reference-note-1"></a>

**[1]** Brewer, E. A. (2000-07-19). Towards Robust Distributed Systems. Keynote, ACM PODC, Portland, OR. Abstract in Proceedings of PODC '00, p. 7. DOI 10.1145/343477.343502. 书目经双源核对。主张已对照全文核实。分散式运算原理研讨会（PODC）之主题演讲投影片。其中一张投影片题为「The CAP Theorem」，正文以「Theorem:」起首，但未附证明；「猜想」之名出自 2002 年那篇论文的标题。据作者 2012 年的回顾，这个定理 1998 年秋首次出现、1999 年见刊，并在 2000 年这场主题演讲中提出；同文并记，一致与可用之争的最早版本是 1997 年一篇系统论文里的 ACID 对 BASE，他是作者之一。

<a id="reference-note-2"></a>

**[2]** Gilbert, S. & Lynch, N. (2002). Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services. ACM SIGACT News, 33(2), 51–59. DOI 10.1145/564585.564601. 书目经官方记录核对。主张已对照全文核实。在非同步网路模型下证明：容许讯息遗失时，读写物件不可能同时保证可用与原子一致；另证明在各节点有时钟的部分同步模型下，只要讯息可能任意遗失，结论依然成立。此文才是「定理」地位的来源。

<a id="reference-note-3"></a>

**[3]** Brewer, E. (2012). CAP Twelve Years Later: How the ‘Rules’ Have Changed. Computer, 45(2), 23–29. DOI 10.1109/MC.2012.37. 书目经官方记录核对。主张已对照全文核实。作者原句：“The ‘2 of 3’ formulation was always misleading because it tended to oversimplify the tensions among properties.” 以及 “Because partitions are rare, there is little reason to forfeit C or A when the system is not partitioned.” 误导的是「三选二」这个表述，不是定理本身。

<a id="reference-note-4"></a>

**[4]** Gilbert, S. & Lynch, N. (2002). Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services. ACM SIGACT News, 33(2), 51–59. 书目经官方记录核对。主张已对照全文核实。同文推论 1.1：非同步模型下（无时钟），即使在没有任何讯息遗失的执行中，恒可用的演算法也保证不了原子一致，因为讯息遗失与任意延迟无法区分。在各节点有时钟的部分同步模型下，同文另证不可兼得仍成立（定理 2），但推论 1.1 的对应版本不成立：存在演算法在讯息全数送达时回传一致的资料，只在讯息遗失时才回传过期资料。

---

[English](../../../en/collections/software-systems-architecture/cap-theorem-brewer-2000.md) · [繁體中文](../../../zh-Hant/collections/software-systems-architecture/cap-theorem-brewer-2000.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hans/collections/software-systems-architecture/cap-theorem-brewer-2000) · [Citation and versions](../../../READING.md)

[Original SVG](assets/cap-theorem-brewer-2000.svg) · Display copy adds a white background only.
