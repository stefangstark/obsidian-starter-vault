---
progress: 30
reading-lists: "[[Single cell representations]]"
contribution: Transformer on ranked gene ranks
title-short: Geneformer
aliases:
  - Geneformer
citekey: theodoris2023
venue: Nature
title: Transfer learning enables predictions in network biology
DOI: 10.1038/s41586-023-06139-9
year: 2023
authors: Christina V. Theodoris, Ling Xiao, Anant Chopra, Mark D. Chaffin, Zeina R. Al Sayed, Matthew C. Hill, Helene Mantineo, Elizabeth M. Brydon, Zexian Zeng, X. Shirley Liu, Patrick T. Ellinor
web: https://www.nature.com/articles/s41586-023-06139-9
pdf: "[[Documents/Storage/theodoris2023.pdf]]"
tags:
  - articles
---

# Transfer learning enables predictions in network biology
`$=dv.span("<progress max=101 value=" + dv.current().file.frontmatter.progress + "> </progress>")`
[web](https://www.nature.com/articles/s41586-023-06139-9) [laptop](<file:///Users/starks/Zotero/storage/QHBM3G4Y/theodoris2023.pdf>) [[Documents/Storage/theodoris2023.pdf|pdf]] 

> [!example]- Authors
> Christina V. Theodoris, Ling Xiao, Anant Chopra, Mark D. Chaffin, Zeina R. Al Sayed, Matthew C. Hill, Helene Mantineo, Elizabeth M. Brydon, Zexian Zeng, X. Shirley Liu, Patrick T. Ellinor

> [!quote]- Abstract
> > Mapping gene networks requires large amounts of transcriptomic data to learn the connections between genes, which impedes discoveries in settings with limited data, including rare diseases and diseases affecting clinically inaccessible tissues. Recently, transfer learning has revolutionized fields such as natural language understanding1,2 and computer vision3 by leveraging deep learning models pretrained on large-scale general datasets that can then be fine-tuned towards a vast array of downstream tasks with limited task-specific data. Here, we developed a context-aware, attention-based deep learning model, Geneformer, pretrained on a large-scale corpus of about 30 million single-cell transcriptomes to enable context-specific predictions in settings with limited data in network biology. During pretraining, Geneformer gained a fundamental understanding of network dynamics, encoding network hierarchy in the attention weights of the model in a completely self-supervised manner. Fine-tuning towards a diverse panel of downstream tasks relevant to chromatin and network dynamics using limited task-specific data demonstrated that Geneformer consistently boosted predictive accuracy. Applied to disease modelling with limited patient data, Geneformer identified candidate therapeutic targets for cardiomyopathy. Overall, Geneformer represents a pretrained deep learning model from which fine-tuning towards a broad range of downstream applications can be pursued to accelerate discovery of key network regulators and candidate therapeutic targets.

# Notes

###  Rank value gene encoding [[Pasted image 20231012143202.png|Fig 1c]]
- Normalize expr across dataset then rank genes within each cell
- Goal is to distinguish cell state
	- a non-parametric representation, does not model eg counts
	- deprioritizes ubiquitously highly expressed housekeeping genes
		- $\rightarrow$ normalizes to a lower rank
	- genes such as transcription factors
		- expressed at low levels but distinguish cell state
		- $\rightarrow$ will move to a higher rank within the encoding^[Extended Data Fig. 1c]
- more robust to batch effects, but unexplored

### Transformer architecture
- fed into 6x pretrained [[transformer blocks]]
- pretrained by a masked learning objective
	- 15% of genes are masked out
	- given 85% guess the rank of the 15%
