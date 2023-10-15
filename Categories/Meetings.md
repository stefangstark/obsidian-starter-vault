---
tags: categories
---
```dataview
table without id
	link(file.link, "🔗") as " ",
	link(file.frontmatter.date) as Date,
	join(project) as Project,
	join(topics) as Content
	
from #meetings 
where
  !contains(file.name, "Template")

sort date(file.frontmatter.time) desc
```
