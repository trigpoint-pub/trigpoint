Canonical: https://trigpoint.pub/zh-Hant/collections/software-systems-architecture/modularity-baldwin-clark-2000  
Captured: 2026-11-02T21:28:00.420140+08:00

> 公開理論閱讀鏡像。驗證層及 Lab 案例請到原站閱讀。

「照功能切就是好邊界」：沒這麼簡單。

# 模組化與薄切面

Modularity & Thin Crossing Points · Baldwin & Clark (2000) / Baldwin (2008)

書目已核 ✓  
軟體架構 · 邊界選址  
先讀：不重複原則

## 三句講透

邊界該開在哪，不是照功能分類決定，是照往來成本決定。  
判準是一句話：這個切面上的往來，容不容易定義、計數與計價。  
不容易，就不要在這裡開接口。

![邊界選址象限示意：橫軸為往來是否容易定義與計價，縱軸為往來頻繁與反覆程度；容易計價且往來稀疏處為薄切面，接口應開此處](assets/modularity-baldwin-clark-2000.github.svg)

<strong>圖 1</strong> · 兩個軸決定邊界該開在哪：橫軸是這個切面上的往來容不容易定義與計價，縱軸是往來的頻繁與反覆程度。  
右下那格是薄切面，接口開在那裡最便宜；左上那格是稠密區，硬開接口等於把摩擦制度化。  
中間是連續的，不是兩格。

## 一、發生什麼事

模組化的直覺很老：把複雜系統切成幾塊，各塊內部自理、塊之間靠約定往來。1962 年那篇講近可分解性[\[3\]](#reference-note-3)、1972 年那篇講資訊隱藏[\[4\]](#reference-note-4)，本站舉為這條線上的祖先之例。

2000 年那本書做的是另一件事：<strong>把模組化從工程直覺升為經濟理論</strong>[\[1\]](#reference-note-1)。核心結構是把設計資訊分兩類：可見的設計規則（大家都要遵守的約定）與隱藏在模組內部的實作。這一分之後，每個模組就變成一份可以獨立替換的實質選擇權：你可以只換其中一塊去試，而不必動整體。模組化的價值因此不只是「好維護」，而是<strong>可以用低成本做很多次局部實驗</strong>。

而真正把判準說死的是 2008 年那篇。它問了一個更前面的問題：邊界為什麼落在這裡而不是那裡。答案是往來成本：任務網絡裡那些<strong>往來容易定義、容易計數、容易付價</strong>的地方，其瑣碎交易成本一般偏低，而模組邊界（乃至公司邊界）就對應這些地方[\[2\]](#reference-note-2)。那些往來稠密、反覆迭代、難以計價的區域，硬在中間開一個接口，等於把摩擦制度化。

這個判準有一個很實用的性質：<strong>它可以在你動手之前用</strong>。功能分類要等系統存在才看得出來，往來成本可以先觀察。你不需要先切錯一次才知道哪裡該切。

<strong>署名要給對：</strong>概念祖，本站舉 Simon（1962，近可分解性）[\[3\]](#reference-note-3)與 Parnas（1972，資訊隱藏）[\[4\]](#reference-note-4)為例；模組化之經濟形式化與選擇權價值歸 Baldwin 與 Clark（2000）[\[1\]](#reference-note-1)；<strong>薄切面與瑣碎交易成本這組判準歸 Baldwin（2008）</strong>，本頁核心那句取自該篇摘要逐字[\[2\]](#reference-note-2)。四段要分開署名：把「模組化」整個概念歸給 2000 年那本書，會抹掉早它三、四十年的祖先（如這兩位），這是本站在此頁明文更正的一條。

## 二、為什麼這對你重要

你每天在做的邊界決定，多數是按「這件事屬於哪一類」在切。這頁要你換成按「這個交接貴不貴」在切。

差別最明顯的地方是把工作交給模型。假設你要把一段工作切出去：如果那個切面上的往來是「我給一份明確的輸入，它回一份明確的輸出，我看得出對不對」，那是薄切面，交出去很便宜，因為交接本身可以被定義和驗收。如果那個切面上的往來是「我得先解釋一堆背景、來回澄清好幾輪、而且我沒有簡單方法判斷結果對不對」，那是稠密區：在這裡開接口，你會把大部分時間花在維護那個接口上。

同一個判準也解釋了一件常見的挫折：為什麼有些工作外包出去反而更慢。不是對方不行，是<strong>你把邊界開在了往來稠密的地方</strong>。

三個可以直接用的問句，都是判準的直譯。第一，這個交接的產出，我講不講得清「什麼樣算完成」。第二，我驗收它要花多少時間，比自己做省不省。第三，這條線上一週會來回幾次：如果答案是「很多次而且每次都要重新解釋」，那條線就不該在那裡。

## 常見誤讀

所屬頁核驗：書目已核 ✓ · 內容最後修訂 2026-10-25

- 常見轉述「模組化是這兩位作者提出的」：概念至少早了三、四十年（例：1962 年的近可分解性、1972 年的資訊隱藏）。這兩位的貢獻是經濟形式化，邊界選址理論則見其中一位 2008 年那篇。引用時勿誤植概念原創。
- 常見轉述「薄與厚是兩類，判斷就是分類」：原文的判準是往來的密度與複雜度，以及界定、計數、付價各要花多少功夫，這些都是程度問題，判定需要實際的往來觀察。把它當二分法會讓人憑印象分類。

## 參考文獻

<strong>如何閱讀來源註記</strong> 「書目經…核對」指作者、年份、題名與出版項已確認；不代表該來源的主張已被核對。「與摘要一致」指主張與論文摘要相符；不含逐句對照全文。「依多源一致轉述」指主張建立於多份彼此一致、轉述該來源的資料，而非原文件本身。 定義版本：2026-09-20。

- \[1\] Baldwin, C. Y. & Clark, K. B. (2000). Design Rules, Volume 1: The Power of Modularity. MIT Press. ISBN 978-0-262-02466-2.
- \[2\] Baldwin, C. Y. (2008). Where Do Transactions Come from? Modularity, Transactions, and the Boundaries of Firms. Industrial and Corporate Change, 17(1), 155–195.
- \[3\] Simon, H. A. (1962). The Architecture of Complexity. Proceedings of the American Philosophical Society, 106(6), 467–482.
- \[4\] Parnas, D. L. (1972). On the Criteria To Be Used in Decomposing Systems into Modules. Communications of the ACM, 15(12), 1053–1058.

## 知識圖譜

- [<em>前置 ▸</em>康威定律（Conway's Law）](conways-law-conway-1968.md)
- [<em>應用於 ▸</em>微服務（Microservices）](microservices-lewis-fowler-2014.md)
- [<em>應用於 ▸</em>領域驅動設計（Domain-Driven Design (DDD)）](domain-driven-design-evans-2003.md)

引用格式：Trigpoint，〈模組化與薄切面〉，trigpoint.pub/zh-Hant/collections/software-systems-architecture/modularity-baldwin-clark-2000 · © Strategitect Limited. · 內容最後修訂 2026-10-25

## 來源註記

<a id="reference-note-1"></a>

**[1]** Baldwin, C. Y. & Clark, K. B. (2000). Design Rules, Volume 1: The Power of Modularity. MIT Press. ISBN 9780262024662. 書目經雙源核對。設計規則與隱藏模組之分及其選擇權價值依多源一致轉述。把模組化從工程直覺升為經濟理論：可見的設計規則與隱藏的模組分離，模組因此構成一組實質選擇權。書內內容本頁只核到多份一致的轉述。

<a id="reference-note-2"></a>

**[2]** Baldwin, C. Y. (2008). Where Do Transactions Come from? Modularity, Transactions, and the Boundaries of Firms. Industrial and Corporate Change, 17(1), 155–195. 書目經官方記錄核對。要旨與摘要一致。摘要原句之中譯：那些工作的成本（稱為 mundane transaction costs）在任務網絡的 thin crossing points 上一般偏低，而這些點對應模組邊界。

<a id="reference-note-3"></a>

**[3]** Simon, H. A. (1962). The Architecture of Complexity. Proceedings of the American Philosophical Society, 106(6), 467–482. 書目經雙源核對。近可分解性之歸屬依多源一致轉述。近可分解性：本站標為概念祖之一，早於本節點錨點約四十年。

<a id="reference-note-4"></a>

**[4]** Parnas, D. L. (1972). On the Criteria To Be Used in Decomposing Systems into Modules. Communications of the ACM, 15(12), 1053–1058. 書目經官方記錄核對。資訊隱藏之歸屬依多源一致轉述。資訊隱藏：本站標為另一位概念祖。

---

[English](../../../en/collections/software-systems-architecture/modularity-baldwin-clark-2000.md) · [简体中文](../../../zh-Hans/collections/software-systems-architecture/modularity-baldwin-clark-2000.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hant/collections/software-systems-architecture/modularity-baldwin-clark-2000) · [Citation and versions](../../../READING.md)

[Original SVG](assets/modularity-baldwin-clark-2000.svg) · Display copy adds a white background only.
