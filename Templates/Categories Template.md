---
tags:
  - categories
---
```dataview
table without id
	file.link as " "
from #tags
where
	!contains(file.name, "Template")
```