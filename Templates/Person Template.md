---
tags:
  - people
category:
  - "[[People]]"
aliases: 
url: 
org:
---
## Meetings

```dataview
table without id
	link(file.link, "🔗") as " ",
	link(dateformat(date(file.frontmatter.time), "yyyy-MM-dd")) as Date,
	join(project) as Project,
	join(topics) as Content
from #meetings 
where
	contains(people, this.file.link)
sort time desc
```
