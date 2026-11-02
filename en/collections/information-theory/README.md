Canonical: https://trigpoint.pub/collections/information-theory/  
Captured: 2026-11-02T21:27:06.234080+08:00

> Public theory reading mirror. Verification and Lab case sections remain on the website.

# Information Theory

The ruler for measuring your own workflow

“Information theory is mathematics for communications engineers”: the fault is structural.

You work every day on a channel that is finite and noisy: saying something so the other side can reconstruct it. You have intuitions but no ruler. This is the ruler.

## Node sequence

Suggested reading order · pin the word down, why it degrades, how to shrink it, what measures relatedness and error, who bears these limits

### § First pin down the word “information”

Order within the group: the definition (not the content) → how to measure a single event → how to measure a whole system

### [Information and uncertainty](information-and-uncertainty.md)

Shannon (1948) / Hartley (1928)

Information is not content. It is the amount by which uncertainty is reduced.

### [Self-information](self-information.md)

Shannon (1948) / Samson (1951)

How much information something carries depends on how unlikely it was in the first place.

### [Entropy](entropy.md)

Shannon (1948)

Entropy is not disorder. It is the quantification of unpredictability.

### § Why it degrades: noise and capacity

Order within the group: tell what counts as noise first → then meet the hard ceiling of the channel itself

### [Signal and noise](signal-and-noise.md)

Shannon (1948)

Signal is the part of the input that reliably lowers uncertainty. The rest is noise.

### [Channel and capacity](channel-and-capacity.md)

Shannon (1948, 1949)

A channel is anything that lets information flow, not wires and radio only but also language, attention and memory.

### § How to shrink it: the three limits of compression

Order within the group: lossless (where the floor is) → lossy (how much distortion you will pay) → individual (a second route that does not use probability)

### [Coding and compression](coding-and-compression.md)

Shannon (1948) / Fano (1949) / Huffman (1952)

Compression is not deleting content. It is representing the same content in a shorter way.

### [Rate-distortion theory](rate-distortion-theory.md)

Shannon (1959) / Berger (1971)

Allow distortion and you can compress below the entropy, but how far below is fixed by a curve that cannot be crossed.

### [Algorithmic information theory](algorithmic-information-theory.md)

Solomonoff (1964) / Kolmogorov (1965) / Chaitin (1966)

Besides Shannon's route, information has a second definition: the amount of information in something is the length of the shortest program that generates it.

### § What measures relatedness and error

Order within the group: how much the two share → what a wrong assumption costs

### [Mutual information](mutual-information.md)

Shannon (1948) / Fano (1961)

Mutual information measures how much of the uncertainty in one thing goes away once you know the other.

### [Kullback-Leibler divergence](kl-divergence.md)

Kullback & Leibler (1951)

This quantity answers a practical question: if you encode real data with the wrong model, how much extra do you pay per item on average.

### § Who bears these limits

Order within the group: people → physics. This group is also the honesty anchor for the shelf: what we do here is exactly the cross-domain extrapolation the founder of the theory warned against, so the warning is printed alongside

### [Information theory and cognitive science](information-theory-and-cognition.md)

Miller (1956) / Bartlett (1932) / Simon (1955)

The mind is an information-processing system working under capacity limits and noise.

### [Information theory and thermodynamics](information-theory-and-thermodynamics.md)

Szilárd (1929) / Landauer (1961) / Bennett (1973)

Information is not purely abstract.

Cite as: Trigpoint, “Information Theory shelf”, trigpoint.pub/collections/information-theory/ · © Strategitect Limited.

---

[繁體中文](../../../zh-Hant/collections/information-theory/README.md) · [简体中文](../../../zh-Hans/collections/information-theory/README.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/collections/information-theory/) · [Citation and versions](../../../READING.md)
