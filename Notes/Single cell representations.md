---
tags:
  - lit-reviews
category:
  - "[[Literature reviews]]"
---
```dataview
table without id
	("<progress max=100 value=" + progress + "> </progress> ") as "Progress",
	(link(file.link, citekey)) as "Article",
	(choice(length(title-short) > 0, title-short, title)) as Title,
		contribution as Contribution
from #articles
where
	contains(reading-lists, this.file.link)
sort progress asc
```

scRNA-seq generates 20k measurements
- models like to have lower dimensional spaces
	- $\rightarrow$ Eucliean geometry breaks down in 20k
- common to learn compressed representations
	- usually 10-100, 500 dims
	- mostly accomplished with [[auto-encoders]]
