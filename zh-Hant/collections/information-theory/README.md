Canonical: https://trigpoint.pub/zh-Hant/collections/information-theory/  
Captured: 2026-11-02T21:27:09.311629+08:00

> 公開理論閱讀鏡像。驗證層及 Lab 案例請到原站閱讀。

# 資訊理論

Information Theory · 量度自己工作流的那把尺

「資訊理論是通訊工程師的數學」：錯在結構。

你每天都在一條有限、有噪音的通道上工作：把一件事說到對方能還原。你有直覺，但沒有尺；這裡是那把尺。

## 節點序列

建議閱讀次序 · 先定死這個詞、它為什麼會走樣、怎麼把它縮小、用什麼量度相關與錯、誰在承受這些限制

### § 先把「資訊」這個詞定死

段內序：定義（不是內容）→ 單一事件怎麼量 → 整個系統怎麼量

### [資訊與不確定性](information-and-uncertainty.md)

Information and Uncertainty · Shannon (1948) / Hartley (1928)

資訊不是內容，是不確定性的削減量。

### [資訊量](self-information.md)

Self-Information · Shannon (1948) / Samson (1951)

一件事帶多少資訊，取決於它原本有多不可能發生。

### [熵](entropy.md)

Entropy · Shannon (1948)

熵不是混亂，是不可預測性的量化。

### § 它為什麼會走樣：噪音與容量

段內序：先分辨什麼是噪音 → 再認識通道本身的硬上限

### [訊號與噪音](signal-and-noise.md)

Signal and Noise · Shannon (1948)

訊號是能穩定降低不確定性的那部分輸入，其餘是噪音。

### [通道與容量](channel-and-capacity.md)

Channel and Capacity · Shannon (1948, 1949)

通道是任何讓資訊流動的載體，不只是電線與無線電，也包括語言、注意力與記憶。

### § 怎麼把它縮小：壓縮的三條極限

段內序：無損（地板在哪）→ 有損（願意付多少失真）→ 個體（不用機率的第二條路）

### [編碼與壓縮](coding-and-compression.md)

Coding and Compression · Shannon (1948) / Fano (1949) / Huffman (1952)

壓縮不是刪內容，是換一種更短的方式表示同樣的內容。

### [率失真理論](rate-distortion-theory.md)

Rate-Distortion Theory · Shannon (1959) / Berger (1971)

允許失真，就能壓得比熵更低，但低到哪裡有一條不可逾越的曲線。

### [演算法資訊觀](algorithmic-information-theory.md)

Algorithmic Information Theory · Solomonoff (1964) / Kolmogorov (1965) / Chaitin (1966)

除了 Shannon 那條路，資訊還有第二個定義：一段東西的資訊量，是能生成它的最短程式長度。

### § 用什麼量度「相關」與「錯」

段內序：兩者共享多少 → 假設錯了要付多少

### [互信息](mutual-information.md)

Mutual Information · Shannon (1948) / Fano (1961)

互信息量的是：知道其中一個之後，另一個的不確定性少了多少。

### [相對熵](kl-divergence.md)

Kullback-Leibler Divergence · Kullback & Leibler (1951)

這個量回答一個很實際的問題：你用錯的模型去編碼真實的資料，每一筆平均要多付多少。

### § 誰在承受這些限制

段內序：人 → 物理。本段同時是全架誠實層錨點：我們做的正是這套理論的創立者警告過的跨域外推，所以把警告一併印出

### [資訊理論與認知科學](information-theory-and-cognition.md)

Information Theory and Cognitive Science · Miller (1956) / Bartlett (1932) / Simon (1955)

心智是一個在容量限制與噪音下運作的資訊處理系統。

### [資訊理論與熱力學](information-theory-and-thermodynamics.md)

Information Theory and Thermodynamics · Szilárd (1929) / Landauer (1961) / Bennett (1973)

資訊不是純粹的抽象。

引用格式：Trigpoint，〈資訊理論書架〉，trigpoint.pub/zh-Hant/collections/information-theory/ · © Strategitect Limited.

---

[English](../../../en/collections/information-theory/README.md) · [简体中文](../../../zh-Hans/collections/information-theory/README.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hant/collections/information-theory/) · [Citation and versions](../../../READING.md)
