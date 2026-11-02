Canonical: https://trigpoint.pub/collections/information-theory/algorithmic-information-theory  
Captured: 2026-11-02T21:27:18.551302+08:00

> Public theory reading mirror. Verification and Lab case sections remain on the website.

Hard to guess and hard to describe are two rulers that can give one string opposite readings.

# Algorithmic information theory

Algorithmic Information Theory · Solomonoff (1964) / Kolmogorov (1965) / Chaitin (1966)

Bibliography checked ✓  
Information theory · a second route to the definition  
Read first: Entropy  
Read first: Coding and compression

## In three sentences

Besides Shannon's route, information has a second definition: the amount of information in something is the length of the shortest program that generates it. This route needs no probabilities, so it can ask about a single object, which Shannon's entropy cannot. The price is that the quantity is not computable. It can only be approached from above.

![A four-cell comparison of the two rulers: the horizontal axis is how statistically random something looks, the vertical axis is how hard it is to generate algorithmically, and the diverging cell holds strings that pass standard statistical tests of randomness yet come from a very short program](assets/algorithmic-information-theory.github.svg)

<strong>Figure 1</strong> · A four-cell comparison of the two rulers. The horizontal axis is how random something looks statistically; the vertical axis is how hard it is to generate algorithmically. The bottom-right cell is where the two rulers diverge most: a string of digits that passes standard tests of randomness may be produced by an extremely short program.

## 1. What happened

How hard something is to guess on average and how hard this one item is to describe are two different questions: the first needs probabilities, the second does not. Shannon's entropy has a precondition: you need a probability distribution first. That is natural for a body of data on average, but it has nothing to say about this one document, because a single object has no distribution. In the 1960s three people arrived independently at the same way out: talk about description rather than probability[\[1\]](#reference-note-1)[\[2\]](#reference-note-2)[\[3\]](#reference-note-3). The information in something equals the length of the shortest program that generates it on a universal machine.

The definition has several immediately usable properties. First, it barely depends on the choice of machine: switch universal machines and the quantity changes by no more than a fixed constant. Second, it gives randomness a clean definition: something is random if and only if it has no description shorter than itself, which is to say it cannot be compressed at all.

Third, and this is the price: the quantity is not computable. No general algorithm produces it, which follows from the halting problem. In practice it can only be approached from above, and the output length of any compression algorithm is one upper bound on it.

When the two routes diverge is the thing most worth keeping from this page. For a purely random source their expectations converge. But for objects with algorithmic structure they diverge sharply. The classic example is the first million digits of an irrational number: they pass standard tests of randomness, so on Shannon's ruler the uncertainty is near maximal and they are nearly incompressible, while a very short program generates them, so on this ruler the complexity is minimal.

The same object, opposite answers from the two rulers, and neither ruler is wrong. They were measuring different things all along.

The bridge between them appears in a paper published in 1982: for an ergodic invariant measure, the entropy of a dynamical system is almost everywhere equal to the algorithmic complexity per unit time[\[4\]](#reference-note-4). One thing about that result is easy to skip: ergodicity is a load-bearing condition rather than an omissible technical detail. An extension followed in 1993.

As for practice, the 1978 line turned choose the shortest total description into a workable criterion for model selection: add the description length of the model itself to the length of the data encoded under that model, and choose the smallest sum[\[5\]](#reference-note-5).

<strong>Attribution where due:</strong>Three independent lines stand side by side and cannot be compressed into one person. The algorithmic foundation of a universal prior and inductive inference belongs to Solomonoff (1964), the earliest published of the three[\[1\]](#reference-note-1). The formal definition of the complexity of an individual string belongs to Kolmogorov (1965)[\[2\]](#reference-note-2). The third line, on algorithmic randomness, belongs to Chaitin (1966)[\[3\]](#reference-note-3). The bridging theorem to Shannon entropy belongs to Brudno (1982), with its ergodicity condition as a load-bearing premise and an extension in 1993[\[4\]](#reference-note-4). The minimum description length principle, which made the route workable as a criterion for model selection, belongs to Rissanen (1978)[\[5\]](#reference-note-5). Compressing the whole route into a single name, as commonly done, erases an earlier independent originator and a real history of three parallel lines at once.

## 2. Why this matters to you

This page promotes something usually treated as taste into a criterion with a formal basis: brevity is not an aesthetic preference, it can be defined.

In everyday use, saying that one explanation is more concise is hard to defend, because concision looks subjective. What this theory offers instead: the cost of an explanation equals the length of describing the explanation itself plus the length needed to describe the phenomenon under it. The two are counted together.

That immediately accounts for two common failures. One is too few rules: the explanation is short, but every case needs separate handling, so the total length comes out larger. The other is too many rules: every case has its own clause, the data side needs almost no description, and the rules themselves are enormous. Both lose to the version in the middle with the smallest sum.

We use this principle ourselves, in one specific place: whether to add another rule to a governance surface. The test is not whether the rule is useful but whether, once added, the length of the rule itself outweighs the case-by-case description it saves. Most proposals fail that arithmetic, because what they save is one or two cases while what they cost is a rule everyone has to hold in mind from then on.

The second thing is a disenchantment of randomness. Looking messy does not mean carrying a lot of information, which is useful when reading data: output that looks like noise may come from a very simple mechanism, and conversely, content that looks well ordered may need a long description to rebuild. Surface regularity and generative complexity are two different things, and most people can see the first only.

The third is a boundary: do not take a compression ratio as a measurement of complexity. A compression ratio estimates an upper bound, and the two are not the same thing. That overreach is fairly common in data analysis.

## Common misreadings

Page verification: Bibliography checked ✓ · Content last revised 2026-10-25

- A common account says Kolmogorov complexity can be computed from a compression ratio. It cannot. It is not computable, and a compression ratio is only an upper-bound estimate of it. Taking the compression ratio as a measurement of complexity is a common overreach.
- A common account talks about the entropy of a single string. Entropy needs a probability distribution and is not defined for a single object. To talk about the information in a single object, what you use is precisely the theory on this page. The two are not interchangeable.
- A common account says this theory holds that random things carry the most information. What it says is that unstructured things are the hardest to compress. Some sequences that pass statistical tests of randomness in fact have extremely short generating programs, so on this ruler their complexity is very low. The two rulers diverge.

## References

<strong>How to read the source notes</strong> “Bibliographic details checked” means author, year, title and venue were confirmed. It does not mean the source's claims were checked. Definitions as of 2026-09-20.

- \[1\] Solomonoff, R. J. (1964). A Formal Theory of Inductive Inference, Part I. Information and Control, 7(1), 1–22; Part II, 7(2), 224–254.
- \[2\] Kolmogorov, A. N. (1965). Three Approaches to the Quantitative Definition of Information. Problems of Information Transmission, 1(1), 1–7.
- \[3\] Chaitin, G. J. (1966). On the Length of Programs for Computing Finite Binary Sequences. Journal of the ACM, 13(4), 547–569.
- \[4\] Brudno, A. A. (1982/1983). Entropy and the Complexity of the Trajectories of a Dynamical System. Trudy Moskovskogo Matematicheskogo Obshchestva, 44, 124–149; Transactions of the Moscow Mathematical Society, (2), 127–151.
- \[5\] Rissanen, J. (1978). Modeling by Shortest Data Description. Automatica, 14(5), 465–471.

Cite as: Trigpoint, “Algorithmic information theory”, trigpoint.pub/collections/information-theory/algorithmic-information-theory · © Strategitect Limited. · Content last revised 2026-10-25

## Source notes

<a id="reference-note-1"></a>

**[1]** Solomonoff, R. J. (1964). A Formal Theory of Inductive Inference, Part I. Information and Control, 7(1), 1–22; Part II, 7(2), 224–254. Bibliographic details checked against the official record. The algorithmic foundation of a universal prior and inductive inference, published in two parts; the earliest published of the three independent lines.

<a id="reference-note-2"></a>

**[2]** Kolmogorov, A. N. (1965). Three Approaches to the Quantitative Definition of Information. Problems of Information Transmission, 1(1), 1–7. Bibliographic details confirmed by two sources. The formal definition of the complexity of an individual string; the pages given are those of the English translation.

<a id="reference-note-3"></a>

**[3]** Chaitin, G. J. (1966). On the Length of Programs for Computing Finite Binary Sequences. Journal of the ACM, 13(4), 547–569. DOI 10.1145/321356.321363. Bibliographic details checked against the official record. The third independent line, on the theory of algorithmic randomness.

<a id="reference-note-4"></a>

**[4]** Brudno, A. A. (1982/1983). Entropy and the Complexity of the Trajectories of a Dynamical System. Trudy Moskovskogo Matematicheskogo Obshchestva, 44, 124–149; English translation in Transactions of the Moscow Mathematical Society, (2), 127–151. Bibliographic details checked against the official record. Provenance double-checked across models. For an ergodic invariant measure, the Kolmogorov-Sinai entropy equals the algorithmic complexity per unit time of almost every trajectory. Ergodicity is a load-bearing condition, not an omissible technical detail; White (1993) extended the result. The English text is the 1983 translation.

<a id="reference-note-5"></a>

**[5]** Rissanen, J. (1978). Modeling by Shortest Data Description. Automatica, 14(5), 465–471. DOI 10.1016/0005-1098(78)90005-5. Bibliographic details checked against the official record. The starting point of the minimum description length principle, which made this route workable as a criterion for model selection.

---

[繁體中文](../../../zh-Hant/collections/information-theory/algorithmic-information-theory.md) · [简体中文](../../../zh-Hans/collections/information-theory/algorithmic-information-theory.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/collections/information-theory/algorithmic-information-theory) · [Citation and versions](../../../READING.md)

[Original SVG](assets/algorithmic-information-theory.svg) · Display copy adds a white background only.
