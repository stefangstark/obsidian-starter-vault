---
tags:
  - categories
---

```dataview
table without id
	file.link as Project,
	join(people) as With
from #projects
where
	!contains(file.name,"Template")
sort year desc
```
