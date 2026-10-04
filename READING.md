# Reading, citation and versions

## Cite the original / 引用原頁

Each content file begins with its original `Canonical:` URL, or a `Source:` URL when the page does not declare a canonical. The original page's citation and revision line is retained near the end of the mirrored body.

引用以 Trigpoint 原頁為主，沿用該頁署名及引用格式；引述原典時保留原典作者與來源，不把鏡像整理當作重新核實。

If the exact mirror copy matters, add a permalink to the file at a specific Git commit. On GitHub, press **Y** while viewing a file to obtain that commit-specific URL. A `main` branch URL can change. There is no invented DOI or source version.

## Read and compare

Shelf pages retain the website's sequence and grouping. Links to mirrored nodes point to relative Markdown paths, so they work both on GitHub and in a downloaded checkout. Original links remain in each file's header and footer.

Inline reference popovers from the public page appear as ordinary linked source notes. Their wording and stated verification depth are retained. The reference list remains in its original numbered wording. Original SVGs are kept byte-for-byte. Display copies add only a white background rectangle so dark source text remains readable in a dark interface; source captions, text, geometry and links to the original SVG are preserved.

Related-node links become readable lists. Six separator characters in four Chinese files use a middle dot in place of the source's long dash; link titles and destinations are otherwise retained. These navigation changes are recorded in `SOURCES.json`. Body sentences and diagrams are unchanged.

The `Captured:` timestamp records when the page was retrieved. A source revision date records what the original page says; neither is a GitHub publication date. `SOURCES.json` lists source URLs and HTML hashes, Markdown hashes and diagram hashes. These identify the captured material; they do not establish that a claim is true.

Use file **History** or Git diffs to see later changes. Consult the original page for its latest corrections and its feedback form. A failed network request alone does not mean a page was withdrawn.

## Scope and rights

The mirror contains the existing public theory introductions, reference material, corrections, reading indexes and reading rules. Verification-layer sections, counter-example sections in that layer, Lab case content including public trials, locked content, early-access material, forms and executable website code are excluded. Application-only labels without public node links are omitted from the source knowledge graph.

Source diagrams are Trigpoint's published inline SVGs. This repository does not bundle font files or download third-party original illustrations. Existing author attribution and notices remain attached to the content. Third-party quotations and materials are outside the content license; the original source and its rights still apply.

See [NOTICE.md](NOTICE.md) for the exact scope of the publisher's CC BY 4.0 grant, third-party exclusions and attribution guidance, and [LICENSE-CONTENT](LICENSE-CONTENT) for the complete terms.

## GitHub reading aids

The repository README, language indexes, this guide, the capture log and source records are mirror navigation and provenance material. Node and shelf prose is transcribed from the original pages, without new advice, theory summaries or translations.

GitHub headings, relative links, file history, diffs and commit permalinks provide the added convenience. This mirror has no separate website, skill catalog or application product line.

## GitHub documentation

- [README, headings and relative links](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)
- [Permanent links to a file version](https://docs.github.com/en/repositories/working-with-files/using-files/getting-permanent-links-to-files)
