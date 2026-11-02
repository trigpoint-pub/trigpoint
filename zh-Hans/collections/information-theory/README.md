Canonical: https://trigpoint.pub/zh-Hans/collections/information-theory/  
Captured: 2026-11-02T21:27:07.842654+08:00

> 公开理论阅读镜像。验证层及 Lab 案例请到原站阅读。

# 资讯理论

Information Theory · 量度自己工作流的那把尺

「资讯理论是通讯工程师的数学」：错在结构。

你每天都在一条有限、有噪音的通道上工作：把一件事说到对方能还原。你有直觉，但没有尺；这里是那把尺。

## 节点序列

建议阅读次序 · 先定死这个词、它为什么会走样、怎么把它缩小、用什么量度相关与错、谁在承受这些限制

### § 先把「资讯」这个词定死

段内序：定义（不是内容）→ 单一事件怎么量 → 整个系统怎么量

### [资讯与不确定性](information-and-uncertainty.md)

Information and Uncertainty · Shannon (1948) / Hartley (1928)

资讯不是内容，是不确定性的削减量。

### [资讯量](self-information.md)

Self-Information · Shannon (1948) / Samson (1951)

一件事带多少资讯，取决于它原本有多不可能发生。

### [熵](entropy.md)

Entropy · Shannon (1948)

熵不是混乱，是不可预测性的量化。

### § 它为什么会走样：噪音与容量

段内序：先分辨什么是噪音 → 再认识通道本身的硬上限

### [讯号与噪音](signal-and-noise.md)

Signal and Noise · Shannon (1948)

讯号是能稳定降低不确定性的那部分输入，其余是噪音。

### [通道与容量](channel-and-capacity.md)

Channel and Capacity · Shannon (1948, 1949)

通道是任何让资讯流动的载体，不只是电线与无线电，也包括语言、注意力与记忆。

### § 怎么把它缩小：压缩的三条极限

段内序：无损（地板在哪）→ 有损（愿意付多少失真）→ 个体（不用机率的第二条路）

### [编码与压缩](coding-and-compression.md)

Coding and Compression · Shannon (1948) / Fano (1949) / Huffman (1952)

压缩不是删内容，是换一种更短的方式表示同样的内容。

### [率失真理论](rate-distortion-theory.md)

Rate-Distortion Theory · Shannon (1959) / Berger (1971)

允许失真，就能压得比熵更低，但低到哪里有一条不可逾越的曲线。

### [演算法资讯观](algorithmic-information-theory.md)

Algorithmic Information Theory · Solomonoff (1964) / Kolmogorov (1965) / Chaitin (1966)

除了 Shannon 那条路，资讯还有第二个定义：一段东西的资讯量，是能生成它的最短程式长度。

### § 用什么量度「相关」与「错」

段内序：两者共享多少 → 假设错了要付多少

### [互信息](mutual-information.md)

Mutual Information · Shannon (1948) / Fano (1961)

互信息量的是：知道其中一个之后，另一个的不确定性少了多少。

### [相对熵](kl-divergence.md)

Kullback-Leibler Divergence · Kullback & Leibler (1951)

这个量回答一个很实际的问题：你用错的模型去编码真实的资料，每一笔平均要多付多少。

### § 谁在承受这些限制

段内序：人 → 物理。本段同时是全架诚实层锚点：我们做的正是这套理论的创立者警告过的跨域外推，所以把警告一并印出

### [资讯理论与认知科学](information-theory-and-cognition.md)

Information Theory and Cognitive Science · Miller (1956) / Bartlett (1932) / Simon (1955)

心智是一个在容量限制与噪音下运作的资讯处理系统。

### [资讯理论与热力学](information-theory-and-thermodynamics.md)

Information Theory and Thermodynamics · Szilárd (1929) / Landauer (1961) / Bennett (1973)

资讯不是纯粹的抽象。

引用格式：Trigpoint，〈资讯理论书架〉，trigpoint.pub/zh-Hans/collections/information-theory/ · © Strategitect Limited.

---

[English](../../../en/collections/information-theory/README.md) · [繁體中文](../../../zh-Hant/collections/information-theory/README.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hans/collections/information-theory/) · [Citation and versions](../../../READING.md)
