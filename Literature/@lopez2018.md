---
progress: 50
reading-lists: "[[Single cell representations]]"
contribution: VAE on raw counts, ZINB likelihood
title-short: scVI
aliases:
  - scVI
citekey: lopez2018
venue: Nature Methods
title: Deep generative modeling for single-cell transcriptomics
DOI: 10.1038/s41592-018-0229-2
year: 2018
authors: Romain Lopez, Jeffrey Regier, Michael B. Cole, Michael I. Jordan, Nir Yosef
web: https://www.nature.com/articles/s41592-018-0229-2
pdf: "[[Documents/Storage/lopez2018.pdf]]"
tags:
  - articles
---

# Deep generative modeling for single-cell transcriptomics
`$=dv.span("<progress max=101 value=" + dv.current().file.frontmatter.progress + "> </progress>")`
[web](https://www.nature.com/articles/s41592-018-0229-2) [laptop](<file:///Users/starks/Zotero/storage/XAXYY8NY/Lopez et al. - 2018 - Deep generative modeling for single-cell transcrip.pdf>) [[Documents/Storage/lopez2018.pdf|pdf]] 

> [!example]- Authors
> Romain Lopez, Jeffrey Regier, Michael B. Cole, Michael I. Jordan, Nir Yosef

> [!quote]- Abstract
> > Single-cell transcriptome measurements can reveal unexplored biological diversity, but they suffer from technical noise and bias that must be modeled to account for the resulting uncertainty in downstream analyses. Here we introduce single-cell variational inference (scVI), a ready-to-use scalable framework for the probabilistic representation and analysis of gene expression in single cells (https://github.com/YosefLab/scVI). scVI uses stochastic optimization and deep neural networks to aggregate information across similar cells and genes and to approximate the distributions that underlie observed expression values, while accounting for batch effects and limited sensitivity. We used scVI for a range of fundamental analysis tasks including batch correction, visualization, clustering, and differential expression, and achieved high accuracy for each task.

# Notes