Canonical: https://trigpoint.pub/collections/software-systems-architecture/  
Captured: 2026-11-02T21:27:06.856470+08:00

> Public theory reading mirror. Verification and Lab case sections remain on the website.

# Software & Systems Architecture

Choosing a structure for a knowledge system

“Software architecture is only for people who write code”: that is a misreading.

You choose a structure for a knowledge system every day: where truth sits, how derivations arise, where the boundary falls and who decides it. This field has asked each of those questions for decades. The answers are not in the code; they are in the trade-offs.

## Node sequence

Suggested reading order · where truth lives, how derivations arise, where the boundary falls, what the boundary follows, what you give up once distributed, and when both ends of reading and writing are models

### § Where truth lives

Order within the group: state the principle → see how it lands in the data layer → then an ancestor that is often misread as it

### [Don't repeat yourself (DRY)](dry-pragmatic-programmer-1999.md)

Hunt & Thomas (1999)

What the original says is that every piece of knowledge in a system must have a single, unambiguous, authoritative representation.

### [Single source of truth (concept history)](single-source-of-truth-concept-history.md)

Devlin & Murphy (1988) → Loshin (2008)

A single source of truth says that every element is maintained in one place and everywhere else refers to it.

### [Model-view-controller (MVC)](mvc-reenskaug-1979.md)

Reenskaug (1979)

Separate the data from the display, so that one body of data can have several presentations that stay in step.

### § How derived things arise

Order within the group: how the source of fact is stored → the reading side can be a different model. The two are often sold together, though both original sources say they can be separated

### [Event sourcing](event-sourcing-fowler-2005.md)

Fowler (2005)

Store every change as one immutable event, and obtain the current state by replaying that sequence.

### [Command query responsibility segregation (CQRS)](cqrs-young-2010.md)

Young (2010) / Meyer CQS (1988)

The model you use to update information does not have to be the model you use to read it.

### § Where the boundary falls

Order within the group: criteria for siting it (cost structure, not feature grouping) → then the language boundary → then the direction of dependency

### [Modularity and thin crossing points](modularity-baldwin-clark-2000.md)

Baldwin & Clark (2000) / Baldwin (2008)

Where a boundary should open is settled by the cost of the traffic across it, not by which category the work falls into.

### [Domain-driven design (DDD)](domain-driven-design-evans-2003.md)

Evans (2003)

The main battleground of complexity is the domain itself, not the technical layer.

### [Hexagonal architecture (ports and adapters)](hexagonal-architecture-cockburn-2005.md)

Cockburn (2005)

The core declares the kind of conversation it needs, and technologies implement that set of ports.

### § What the boundary follows

Order within the group: the constraint first (structure will mirror communication paths) → then what can be designed (make interfaces explicit, and expect the relationships to evolve)

### [Conway's law](conways-law-conway-1968.md)

Conway (1968)

Organisations that design systems produce designs that mirror their own communication structures.

### [Team topologies](team-topologies-skelton-pais-2019.md)

Skelton & Pais (2019)

Relationships between teams want declaring explicitly, the way an interface is declared, rather than resting on tacit understanding.

### § What you gave up once you distributed it

Order within the group: the decision (split) → the cost (the theorem) → then a position that reverses it explicitly. This closing group rewrites the first one, which is the evidence that this shelf is not doctrine

### [Microservices](microservices-lewis-fowler-2014.md)

Lewis & Fowler (2014)

Split one application into a set of services that are released independently, and the unit of deployment and scaling gets smaller.

### [CAP theorem](cap-theorem-brewer-2000.md)

Brewer (2000) / Gilbert & Lynch (2002)

When a network partition happens, you can have consistency or availability, and not both.

### [Data mesh](data-mesh-dehghani-2022.md)

Dehghani (2019, 2022)

Once scale arrives, holding one globally uniform canonical model makes that model the bottleneck.

### § When both ends of reading and writing are models

Order within the group: the external evidence → why it still breaks → which two axes it breaks on → then the highest-risk class. This group is also the honesty anchor for the shelf: it lays out this site's own gatekeeping

### [Retrieval-augmented generation (RAG)](retrieval-augmented-generation-lewis-2020.md)

Lewis et al. (2020)

Split the model's memory in two: what is pressed into the weights, and what is fetched at the moment of generating.

### [Hallucination in NLG](llm-hallucination-ji-2023.md)

Ji et al. (2023)

Hallucination is generation that reads fluently while being unfaithful to its source, or making no sense at all.

### [Faithfulness vs factuality](faithfulness-factuality-maynez-2020.md)

Maynez et al. (2020)

Faithfulness asks whether a statement is supported by the source. Factuality asks whether it is true of the world.

### [Fabricated citations](fabricated-citations-walters-wilder-2023.md)

Walters & Wilder (2023)

The citation is complete and convincing in form, and the thing it points at does not exist.

Cite as: Trigpoint, “Software & Systems Architecture shelf”, trigpoint.pub/collections/software-systems-architecture/ · © Strategitect Limited.

---

[繁體中文](../../../zh-Hant/collections/software-systems-architecture/README.md) · [简体中文](../../../zh-Hans/collections/software-systems-architecture/README.md)

[Index](../../README.md) · [Original page](https://trigpoint.pub/collections/software-systems-architecture/) · [Citation and versions](../../../READING.md)
