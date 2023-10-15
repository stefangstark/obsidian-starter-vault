---
tags:
  - categories
---
```dataview
table without id
	file.link as Person,
	join(org) as Org 
from #people 
where
  !contains(file.name,"Template")
sort file.name asc
```