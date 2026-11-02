Canonical: https://trigpoint.pub/zh-Hant/collections/software-systems-architecture/  
Captured: 2026-11-02T21:27:09.676591+08:00

> 公開理論閱讀鏡像。驗證層及 Lab 案例請到原站閱讀。

# 軟體與系統架構

Software & Systems Architecture · 替一個知識系統選結構

「軟體架構是寫程式的人才需要的」：是誤讀。

你每天都在替一個知識系統選結構：真相放哪、派生怎麼來、邊界劃哪、誰決定邊界。這個領域把這幾題各問了幾十年，答案不在程式碼裡，在取捨裡。

## 節點序列

建議閱讀次序 · 真相住哪、派生怎麼來、邊界劃哪、邊界跟著誰走、分散之後放棄什麼、當讀寫兩端都是模型

### § 真相住在哪裡

段內序：先立原則 → 再看它在資料層怎麼落地 → 最後看一個被誤讀成它的祖宗

### [不重複原則](dry-pragmatic-programmer-1999.md)

Don't Repeat Yourself (DRY) · Hunt & Thomas (1999)

原則的原文說的是：每一塊知識在系統裡只能有一個明確而權威的表述。

### [單一真相來源](single-source-of-truth-concept-history.md)

Single Source of Truth (concept history) · Devlin & Murphy (1988) → Loshin (2008)

單一真相來源說的是：每個元素只在一處被維護，其他地方全部引用它。

### [模型視圖控制器](mvc-reenskaug-1979.md)

Model-View-Controller (MVC) · Reenskaug (1979)

把資料與畫面分開，讓同一批資料可以有多個同步的呈現。

### § 派生的東西怎麼來

段內序：事實源怎麼存 → 讀的那一面可以是另一個模型。兩者常被綁售，而兩個原始出處都說可以分開

### [事件溯源](event-sourcing-fowler-2005.md)

Event Sourcing · Fowler (2005)

把每一次變更存成一筆不可改的事件，當前狀態改由重播那串事件得出。

### [命令查詢職責分離](cqrs-young-2010.md)

Command Query Responsibility Segregation (CQRS) · Young (2010) / Meyer CQS (1988)

更新資訊用的模型，不必等於讀取資訊用的模型。

### § 邊界劃在哪裡

段內序：先給選址判準（成本結構，不是功能歸類）→ 再給語言邊界 → 最後給依賴方向

### [模組化與薄切面](modularity-baldwin-clark-2000.md)

Modularity & Thin Crossing Points · Baldwin & Clark (2000) / Baldwin (2008)

邊界該開在哪，不是照功能分類決定，是照往來成本決定。

### [領域驅動設計](domain-driven-design-evans-2003.md)

Domain-Driven Design (DDD) · Evans (2003)

複雜度的主戰場在領域本身，不在技術層。

### [六角架構](hexagonal-architecture-cockburn-2005.md)

Hexagonal Architecture (Ports and Adapters) · Cockburn (2005)

核心宣告它需要什麼樣的對話，技術來實作那組介面。

### § 邊界跟著誰走

段內序：先看約束（結構一定會鏡像溝通路徑）→ 再看可以怎麼設計（接口顯式化，且預期關係會演化）

### [康威定律](conways-law-conway-1968.md)

Conway's Law · Conway (1968)

設計系統的組織，會產出鏡像自身溝通結構的設計。

### [團隊拓撲](team-topologies-skelton-pais-2019.md)

Team Topologies · Skelton & Pais (2019)

團隊之間的關係要像介面一樣被明確宣告，而不是靠默契。

### § 分散之後你放棄了什麼

段內序：先看決定（拆）→ 再看代價（定理）→ 最後看一個明文反過來的立場。本段壓軸回頭改寫第一段，這是本架不是教條的證據

### [微服務](microservices-lewis-fowler-2014.md)

Microservices · Lewis & Fowler (2014)

把一個應用拆成一組各自獨立上線的服務，於是部署與擴充的單位變小。

### [CAP 定理](cap-theorem-brewer-2000.md)

CAP Theorem · Brewer (2000) / Gilbert & Lynch (2002)

網路分區發生時，一致與可用只能選一個。

### [資料網格](data-mesh-dehghani-2022.md)

Data Mesh · Dehghani (2019, 2022)

規模上來之後，維持一個全域統一的正典模型會讓那個模型變成瓶頸。

### § 當讀寫兩端都是模型

段內序：先看外掛證據 → 再看它為什麼還是會壞 → 再看壞在哪兩個軸 → 最後看最高危的那一類。本段同時是全架誠實層錨點：它把本站自己的把關動作攤出來

### [檢索增強生成](retrieval-augmented-generation-lewis-2020.md)

Retrieval-Augmented Generation (RAG) · Lewis et al. (2020)

把模型的記憶拆成兩層：壓在權重裡的，與生成當下才去取的。

### [生成幻覺](llm-hallucination-ji-2023.md)

Hallucination in NLG · Ji et al. (2023)

幻覺是生成流暢卻不忠於來源或不知所云。

### [忠實性與事實性](faithfulness-factuality-maynez-2020.md)

Faithfulness vs Factuality · Maynez et al. (2020)

忠實問的是這段話有沒有被來源支持，事實問的是它對世界是不是真的。

### [虛構引用](fabricated-citations-walters-wilder-2023.md)

Fabricated Citations · Walters & Wilder (2023)

引用的格式完整逼真，而它指向的東西不存在。

引用格式：Trigpoint，〈軟體與系統架構書架〉，trigpoint.pub/zh-Hant/collections/software-systems-architecture/ · © Strategitect Limited.

---

[English](../../../en/collections/software-systems-architecture/README.md) · [简体中文](../../../zh-Hans/collections/software-systems-architecture/README.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/zh-Hant/collections/software-systems-architecture/) · [Citation and versions](../../../READING.md)
