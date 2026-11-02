Canonical: https://trigpoint.pub/zh-Hans/collections/information-theory/algorithmic-information-theory  
Captured: 2026-11-02T21:27:35.993321+08:00

> 公开理论阅读镜像。验证层及 Lab 案例请到原站阅读。

难猜和难描述是两把尺，同一串数字可以得到相反的读数。

# 演算法资讯观

Algorithmic Information Theory · Solomonoff (1964) / Kolmogorov (1965) / Chaitin (1966)

书目已核 ✓  
资讯理论 · 另一条定义路线  
先读：熵  
先读：编码与压缩

## 三句讲透

除了 Shannon 那条路，资讯还有第二个定义：一段东西的资讯量，是能生成它的最短程式长度。  
这条路不需要机率，因此可以对单一对象发问，而 Shannon 的熵不能。  
代价是这个量不可计算，只能从上方逼近。

![两把尺的四格对照：横轴为统计上的随机程度，纵轴为演算法上的生成难度；右下格为两尺分歧最大处，通过随机检定却可由极短程式生成](assets/algorithmic-information-theory.github.svg)

<strong>图 1</strong> · 两把尺的四格对照示意：横轴是统计上看起来有多随机，纵轴是演算法上有多难生成。  
右下格是两把尺分歧最大的地方，一段通过标准随机性检定的数字，可能由一个极短的程式产生。

## 一、发生什么事

平均而言有多难猜，和单独这一份有多难描述，是两个不同的问题：前一个需要机率，后一个不需要。Shannon 的熵有一个前提：你得先有一个机率分布。这对「一批资料平均而言」是自然的，但对「这一份文件」就无话可说了，因为单一对象没有分布。1960 年代有三个人各自独立想到同一个出路：不谈机率，谈<strong>描述</strong>[\[1\]](#reference-note-1)[\[2\]](#reference-note-2)[\[3\]](#reference-note-3)。一段东西的资讯量，等于在一台通用计算机上能把它生成出来的最短程式有多长。

这个定义有几个立刻可用的性质。第一，它几乎不依赖机器的选择：换一台通用计算机，这个量的变化不超过一个固定的常数。第二，它给了「随机」一个干净的定义：一段东西是随机的，当且仅当<strong>没有比它自己更短的描述</strong>，也就是完全无法压缩。第三，也是代价：这个量<strong>不可计算</strong>，不存在通用的演算法能算出它，这是停机问题的推论。实务上只能从上方逼近，任何压缩演算法的输出长度都是它的一个上界。

两条路线在什么时候会分歧，是这一页最值得记的东西。对纯随机的来源，两者的期望值会收敛；但对<strong>演算法上有结构</strong>的对象，它们会严重分歧。经典例子是一个无理数的前一百万位：它通过标准的随机性检定，因此在 Shannon 的尺下不确定性极大、几乎不可压缩；但它可以由一个很短的程式生成，因此在这把尺下复杂度极小。<strong>同一段东西，两把尺给出相反的答案，而两把尺都没有错</strong>，它们量的本来就是不同的东西。

两者的桥梁见于 1982 年刊出的一篇论文：对遍历的不变测度，动力系统的熵几乎处处等于单位时间的算法复杂度[\[4\]](#reference-note-4)。这个结果有一件容易被略过的事：<strong>遍历性是载重条件，不是可省略的技术细节</strong>；1993 年另有推广。

至于实务化，1978 年那条线把「选最短总描述」变成可操作的模型选择准则：把模型本身的描述长度与资料在该模型下的编码长度加起来，选总和最小的[\[5\]](#reference-note-5)。

<strong>署名要给对：</strong>三条独立线并列，不可压成一人：通用先验与归纳推理的算法基础归 Solomonoff（1964），三者中发表最早[\[1\]](#reference-note-1)；个体字串复杂度的形式定义归 Kolmogorov（1965）[\[2\]](#reference-note-2)；算法随机性的第三条线归 Chaitin（1966）[\[3\]](#reference-note-3)。与 Shannon 熵之间的桥接定理归 Brudno（1982），<strong>其遍历性条件为载重前提</strong>，1993 年有推广[\[4\]](#reference-note-4)。实务化为模型选择准则的最小描述长度原理归 Rissanen（1978）[\[5\]](#reference-note-5)。常见转述把整条路线压成单一人名，会同时抹去一位更早的独立提出者与一段真实的三线并行史。

## 二、为什么这对你重要

这一页把一个常被当作品味的东西，升格成有形式基础的判准：<strong>简洁不是美学偏好，是可以定义的。</strong>

日常里我们说一个解释「比较简洁」，通常没有办法辩护，因为简洁看起来是主观的。这套理论给的说法是：一个解释的成本，等于描述这个解释本身的长度，加上在这个解释之下描述现象所需的长度。两者要一起算。这立刻解释了两种常见的失败。一种是规则太少：解释本身很短，但每个个案都要另外交代，总长度反而更大。另一种是规则太多：每个个案都有专属条款，资料端几乎不用描述，但规则本身长得惊人。两者都输给中间那个总和最小的版本。

这条原则我们自己在用，而且用在一个具体的地方：治理面的规则要不要再加一条。判准不是「这条规则有没有用」，而是「加上它之后，规则本身的长度与它省下的个案描述，哪一边多」。多数提案在这个算法下会被否决，因为它们节省的是一两个个案，付出的是每个人此后都要记住的一条规则。

第二件事是对「随机」的祛魅。看起来很乱不等于资讯量大，这在判读资料时很有用：一段杂讯般的输出，可能来自一个极简单的机制；反过来，一段看起来井然有序的内容，也可能需要很长的描述才能重建。<strong>表面的规律性与生成的复杂度是两回事</strong>，而多数人只看得到前者。

第三是一个界线：不要拿压缩率当作复杂度的量测值。压缩率是上界的估计，两者不是同一个东西，这个越界在资料分析里相当常见。

## 常见误读

所属页核验：书目已核 ✓ · 内容最后修订 2026-10-25

- 常见转述「Kolmogorov 复杂度可以用压缩率算出来」：不能。它不可计算，压缩率只是它的一个上界估计。把压缩率当成复杂度的量测值是常见的越界。
- 常见转述「对单一字串谈熵」：熵需要一个机率分布，对单一对象没有定义。要谈单一对象的资讯量，用的正是本页这一套。两者不可互换。
- 常见转述「这套理论说随机的东西资讯量最大」：说的是无结构的东西最难压缩。而某些统计上通过随机检定的序列，其实有极短的生成程式，因此在这把尺下复杂度极低。两把尺会分歧。

## 参考文献

<strong>如何阅读来源注记</strong> 「书目经…核对」指作者、年份、题名与出版项已确认；不代表该来源的主张已被核对。 定义版本：2026-09-20。

- \[1\] Solomonoff, R. J. (1964). A Formal Theory of Inductive Inference, Part I. Information and Control, 7(1), 1–22; Part II, 7(2), 224–254.
- \[2\] Kolmogorov, A. N. (1965). Three Approaches to the Quantitative Definition of Information. Problems of Information Transmission, 1(1), 1–7.
- \[3\] Chaitin, G. J. (1966). On the Length of Programs for Computing Finite Binary Sequences. Journal of the ACM, 13(4), 547–569.
- \[4\] Brudno, A. A. (1982/1983). Entropy and the Complexity of the Trajectories of a Dynamical System. Trudy Moskovskogo Matematicheskogo Obshchestva, 44, 124–149; Transactions of the Moscow Mathematical Society, (2), 127–151.
- \[5\] Rissanen, J. (1978). Modeling by Shortest Data Description. Automatica, 14(5), 465–471.

引用格式：Trigpoint，〈演算法资讯观〉，trigpoint.pub/zh-Hans/collections/information-theory/algorithmic-information-theory · © Strategitect Limited. · 内容最后修订 2026-10-25

## 来源注记

<a id="reference-note-1"></a>

**[1]** Solomonoff, R. J. (1964). A Formal Theory of Inductive Inference, Part I. Information and Control, 7(1), 1–22; Part II, 7(2), 224–254. 书目经官方记录核对。通用先验与归纳推理的算法基础，分两部分刊出；三条独立线中发表最早。

<a id="reference-note-2"></a>

**[2]** Kolmogorov, A. N. (1965). Three Approaches to the Quantitative Definition of Information. Problems of Information Transmission, 1(1), 1–7. 书目经双源核对。个体字串复杂度之形式定义；此处页码为英译本。

<a id="reference-note-3"></a>

**[3]** Chaitin, G. J. (1966). On the Length of Programs for Computing Finite Binary Sequences. Journal of the ACM, 13(4), 547–569. DOI 10.1145/321356.321363. 书目经官方记录核对。算法随机性理论之第三条独立线。

<a id="reference-note-4"></a>

**[4]** Brudno, A. A. (1982/1983). Entropy and the Complexity of the Trajectories of a Dynamical System. Trudy Moskovskogo Matematicheskogo Obshchestva, 44, 124–149; English translation in Transactions of the Moscow Mathematical Society, (2), 127–151. 书目经官方记录核对。出处经跨模型双查核实。对遍历的不变测度，Kolmogorov-Sinai 熵几乎处处等于轨道单位时间的算法复杂度。遍历性为载重条件，不是可省略的技术细节；White（1993）推广了这个结果。英文本为 1983 年之译本。

<a id="reference-note-5"></a>

**[5]** Rissanen, J. (1978). Modeling by Shortest Data Description. Automatica, 14(5), 465–471. DOI 10.1016/0005-1098(78)90005-5. 书目经官方记录核对。最小描述长度原理的起点，将本路线实务化为模型选择准则。

---

[English](../../../en/collections/information-theory/algorithmic-information-theory.md) · [繁體中文](../../../zh-Hant/collections/information-theory/algorithmic-information-theory.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hans/collections/information-theory/algorithmic-information-theory) · [Citation and versions](../../../READING.md)

[Original SVG](assets/algorithmic-information-theory.svg) · Display copy adds a white background only.
