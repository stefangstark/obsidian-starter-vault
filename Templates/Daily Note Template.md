---
tags:
  - daily
---

# Meetings
```dataview
table without id
	link(file.link, "🔗") as " ",
	join(project) as Project,
	join(people) as People,
	start-time as Time,
	join(topics) as Content
from #meetings 
where
	contains(string(file.frontmatter), string(dateformat(this.file.day,"yyyy-MM-dd")))
sort date desc
```

# Tasks
```dataview
task
where happens = today
```
# Mentions
```dataview
list
where
	!contains(file.tags, "daily") and
	!contains(file.tags, "meetings") and
	contains(file.outlinks, this.file.link) or
	contains(string(file.frontmatter), string(dateformat(this.file.day,"yyyy-MM-dd")))
sort file.ctime asc
```

# Notes
