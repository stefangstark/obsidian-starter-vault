---
tags:
  - lit-reviews
category:
  - "[[Literature reviews]]"
---
```dataview
table without id
	("<progress max=100 value=" + progress + "> </progress> ") as " ",
	(link(file.link, citekey)) as "Article",
	(choice(length(titleshort) > 0, titleshort, title)) as Title,
		contribution as Contribution
from #articles
where
	contains(keywords, this.file.link)
sort file.name asc
```