Canonical: https://trigpoint.pub/zh-Hans/collections/information-theory/rate-distortion-theory  
Captured: 2026-11-02T21:27:38.760394+08:00

> 公开理论阅读镜像。验证层及 Lab 案例请到原站阅读。

影像要压缩，失真照数值差异算，还是照人眼在意的算？

# 率失真理论

Rate-Distortion Theory · Shannon (1959) / Berger (1971)

书目已核 ✓  
资讯理论 · 表示与压缩  
先读：熵  
先读：编码与压缩

## 三句讲透

允许失真，就能压得比熵更低，但低到哪里有一条不可逾越的曲线。  
真正的设计决策不是压多少，是<strong>先指定哪一种损失可以接受</strong>。  
选错了那个标准，你会非常有效率地优化一件错的事。

![率失真曲线示意：容许失真越大所需长度下界越低，失真为零时回到熵；曲线下方为不可能区域；另一条虚线示范换一个失真度量会得到完全不同的曲线](assets/rate-distortion-theory.github.svg)

<strong>图 1</strong> · 率与失真的取舍曲线示意：容许的失真越大，所需的长度下界越低；容许失真为零时，下界回到熵。  
曲线下方是不可能区域，任何宣称落在那里的压缩都不成立。  
本图刻意无数值刻度与单位。

## 一、发生什么事

允许失真之后，第一个设计决定是哪一种差异算作损失，然后才轮到能压多短。无损压缩的地板是熵。但很多时候我们不需要完整还原：一张照片、一段录音、一份摘要，损失一些细节换取大幅缩短是划算的。问题是划算到哪里为止。

答案的雏形在 1948 年那篇末段已就连续来源提出[\[4\]](#reference-note-4)，1959 年那篇给了它完整的形状[\[1\]](#reference-note-1)。它用一个「失真度量」来说明什么样的差异算是损失、损失多少；然后在「平均失真不超过 D」这个约束下，求所需长度的最小值。得到的是一条随 D 递减的曲线：容许的失真越大，需要的长度越少。曲线有两个端点值得记：<strong>容许失真为零时，它回到熵</strong>；容许失真大到极限时，它降到零，也就是什么都不传。1971 年那本教科书把这个领域系统化，成为此后的典律[\[2\]](#reference-note-2)。

这条曲线最重要的性质不是它的形状，是它下方的区域<strong>不可能</strong>。任何宣称能在某个失真水准下压得比曲线更低的方法，不是计算错了就是偷偷改了失真的定义。这给了你一个很硬的检查工具。

而整套理论真正的重量落在一个常被略过的地方：<strong>失真度量是你选的</strong>。理论本身不告诉你什么算损失，它只在你给定标准之后，告诉你极限在哪。所以同一份资料，换一个失真度量就会得到完全不同的曲线、完全不同的最优压缩法。影像压缩领域一个著名的后果是，用数值差异当标准做出来的方法，在人眼看来会产生特定形态的瑕疵，因为人眼在意的东西不是数值差异。

还有一条实务上的修正：曲线是<strong>渐近</strong>可达的，需要很长的码块。短讯息、要求即时的场合，实际能达到的率一般高于曲线[\[3\]](#reference-note-3)。

<strong>署名要给对：</strong>有损压缩的理论极限归 Shannon：概念在 1948 年那篇末段已就连续来源提出[\[4\]](#reference-note-4)，1959 年的会议纪录论文给出离散来源的完整表述[\[1\]](#reference-note-1)。领域的系统化与典律地位归 Berger（1971）那本教科书[\[2\]](#reference-note-2)，两者角色不同，不可互相代称。有损压缩在有限码长下的修正，可见 Kostina 与 Verdú（2012）[\[3\]](#reference-note-3)。至于把这套框架引入机器学习表征理论的后续变体，本站因其下游主张存在未决争议而未收入本书架，仅在此注明其存在。

## 二、为什么这对你重要

你每天做的摘要、交接、简报，全部是有损压缩。差别在于多数人没有意识到自己正在做一个选择：<strong>哪一种损失是可以接受的</strong>。

不指定这件事，就等于默认一个标准，而默认值通常是「读起来顺不顺」。于是压缩的过程变成砍掉那些让句子变长、变别扭的部分，而那些部分往往正是承载条件与例外的地方：「除非」「取决于」「只有在」「必须」。砍掉它们，文字流畅度上升，而流畅度正是那个被默认的失真度量，所以优化过程觉得自己做得很好。损失的是判断所需的边界，而这种损失不会产生错误讯息。

换一个度量，整个做法就变了。如果你把失真度量定成「读者会不会做出不同的决定」，那么首先要保住的就是所有改变决定的条件，而可以整段丢掉的是背景、动机、与过程叙述。同一份材料，同样压到一半长度，两个版本会完全不一样，而且各自在自己的标准下最优。

所以这一页给的操作是一句话：<strong>压缩之前，先写下你允许损失什么</strong>。这句话写出来通常不到十个字，但它决定了后面所有的取舍方向。我们自己的知识库把它写成一条硬规矩：压缩时承载因果与条件的词永不可删，其余皆可。这条规矩就是一个明文的失真度量。

第三件事是承认极限。当你发现无论怎么压都会损失掉你不能接受的东西，那不代表你技巧不够，代表<strong>你要的失真水准对应的长度就是那么长</strong>。这时候正确的动作是接受长度，或者改变读者，而不是继续压。

## 常见误读

所属页核验：书目已核 ✓ · 内容最后修订 2026-10-25

- 常见转述「有损压缩就是品质比较差的压缩」：不是品质好坏，是取舍位置。有损压缩的设计核心不是压多少，是事先指定哪一种损失可以接受、哪一种不行。没有指定失真度量的有损压缩，等于没有目标。
- 常见转述「曲线上的值是可以达到的」：那是渐近极限，需要很长的码块。短讯息与即时场合的实际率一般高于曲线；有损压缩在有限码长下的修正量，2012 年有论文系统刻画。

## 参考文献

<strong>如何阅读来源注记</strong> 「书目经…核对」指作者、年份、题名与出版项已确认；不代表该来源的主张已被核对。「与摘要一致」指主张与论文摘要相符；不含逐句对照全文。「对照全文核实」指主张已与来源文本本身比对。 定义版本：2026-09-20。

- \[1\] Shannon, C. E. (1959). Coding Theorems for a Discrete Source with a Fidelity Criterion. IRE National Convention Record, 7, Part 4, 142–163.
- \[2\] Berger, T. (1971). Rate Distortion Theory: A Mathematical Basis for Data Compression. Englewood Cliffs, NJ: Prentice-Hall.
- \[3\] Kostina, V., & Verdú, S. (2012). Fixed-Length Lossy Compression in the Finite Blocklength Regime. IEEE Transactions on Information Theory, 58(6), 3309–3338.
- \[4\] Shannon, C. E. (1948). A Mathematical Theory of Communication. Bell System Technical Journal, 27(3), 379–423; 27(4), 623–656.

引用格式：Trigpoint，〈率失真理论〉，trigpoint.pub/zh-Hans/collections/information-theory/rate-distortion-theory · © Strategitect Limited. · 内容最后修订 2026-10-25

## 来源注记

<a id="reference-note-1"></a>

**[1]** Shannon, C. E. (1959). Coding Theorems for a Discrete Source with a Fidelity Criterion. IRE National Convention Record, 7, Part 4, 142–163. 书目经双源核对。主张已对照全文核实。以失真度量与平均失真上限定义率失真函数 R(d)，并证明离散来源的编码定理；R(d) 随 d 单调递减，失真超过某一上限时降为零。

<a id="reference-note-2"></a>

**[2]** Berger, T. (1971). Rate Distortion Theory: A Mathematical Basis for Data Compression. Englewood Cliffs, NJ: Prentice-Hall. 书目经多源交叉核对。把率失真理论系统化整理的教科书。

<a id="reference-note-3"></a>

**[3]** Kostina, V., & Verdú, S. (2012). Fixed-Length Lossy Compression in the Finite Blocklength Regime. IEEE Transactions on Information Theory, 58(6), 3309–3338. DOI 10.1109/TIT.2012.2186786. 书目经官方记录核对。要旨与摘要一致。有损压缩在有限码长下的分析：给定码长与失真超标的机率，最低可达率近似为 R(d) 加上一项随码长平方根递减的修正，因此短码情形的实际率一般高于曲线。

<a id="reference-note-4"></a>

**[4]** Shannon, C. E. (1948). A Mathematical Theory of Communication. Bell System Technical Journal, 27(3), 379–423; 27(4), 623–656. 书目经官方记录核对。主张已对照全文核实。原刊第 26 至 27 节（后来的重排本作第 27 至 28 节）以距离函数衡量重建的保真度，定义来源相对于保真度的率，并给出对应的编码定理（定理 21）；处理的是连续来源。

---

[English](../../../en/collections/information-theory/rate-distortion-theory.md) · [繁體中文](../../../zh-Hant/collections/information-theory/rate-distortion-theory.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hans/collections/information-theory/rate-distortion-theory) · [Citation and versions](../../../READING.md)

[Original SVG](assets/rate-distortion-theory.svg) · Display copy adds a white background only.
