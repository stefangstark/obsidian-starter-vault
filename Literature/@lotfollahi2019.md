---
progress: 80
reading-lists: "[[Single cell representations]]"
contribution: VAE on normalized counts, linear latent space interpolation
title-short: scGen
aliases:
  - scGen
citekey: lotfollahi2019
venue: Nature Methods
title: scGen predicts single-cell perturbation responses
DOI: 10.1038/s41592-019-0494-8
year: 2019
authors: Mohammad Lotfollahi, F. Alexander Wolf, Fabian J. Theis
web: https://www.nature.com/articles/s41592-019-0494-8
pdf: "[[Documents/Storage/lotfollahi2019.pdf]]"
tags:
  - articles
---

# scGen predicts single-cell perturbation responses
`$=dv.span("<progress max=101 value=" + dv.current().file.frontmatter.progress + "> </progress>")`
[web](https://www.nature.com/articles/s41592-019-0494-8) [laptop](<file:///Users/starks/Zotero/storage/SKF69XJ9/lotfollahi2019.pdf>) [[Documents/Storage/lotfollahi2019.pdf|pdf]] 

> [!example]- Authors
> Mohammad Lotfollahi, F. Alexander Wolf, Fabian J. Theis

> [!quote]- Abstract
> > Accurately modeling cellular response to perturbations is a central goal of computational biology. While such modeling has been based on statistical, mechanistic and machine learning models in specific settings, no generalization of predictions to phenomena absent from training data (out-of-sample) has yet been demonstrated. Here, we present scGen (https://github.com/theislab/scgen), a model combining variational autoencoders and latent space vector arithmetics for high-dimensional single-cell gene expression data. We show that scGen accurately models perturbation and infection response of cells across cell types, studies and species. In particular, we demonstrate that scGen learns cell-type and species-specific responses implying that it captures features that distinguish responding from non-responding genes and cells. With the upcoming availability of large-scale atlases of organs in a healthy state, we envision scGen to become a tool for experimental design through in silico screening of perturbation response in the context of disease and drug treatment.

# Notes