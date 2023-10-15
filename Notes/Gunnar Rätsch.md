---
tags:
  - people
category:
  - "[[People]]"
aliases:
  - Gunnar
url: 
org:
---
## Meetings


```dataview
table without id
	link(file.link, "🔗") as Meeting,
	link(file.frontmatter.date) as Date,
	join(project) as Project,
	join(topics) as Content
from #meetings 
where
	contains(people, this.file.link)
sort time desc
```


Can also embed `dataview` queries in callout blocks:

> [!example]+ Meetings
> ```dataview
> table without id
> 	link(file.link, "🔗") as "",
> 	link(file.frontmatter.date) as " ",
> 	join(project) as Project,
> 	join(topics) as Content
> from #meetings 
> where
> 	contains(people, this.file.link)
> sort time desc
> ```