---
tags:
  - projects
people:
  - "[[Charlotte]]"
  - "[[Gabri]]"
  - "[[Kjong]]"
  - "[[Lucas]]"
  - "[[Andreas]]"
  - "[[Gunnar Rätsch|Gunnar]]"
category:
  - "[[Projects]]"
---
> [!important]+ Open tasks
> ```dataview
> task
> where
> 	contains(project, this.file.link) and
> 	!completed
> ```


> [!example]- Work packages
> ```dataview
> list
> from #work-packages
> where
> 	contains(project, this.file.link)
> ```

> [!example]- Meetings
> ```dataview
> table without id
> 	link(file.link, "🔗") as "",
> 	join(people) as With,
> 	link(file.frontmatter.date) as Date,
> 	join(topics) as Content
> from #meetings 
> where
> 	contains(project, this.file.link)
> sort file.name desc
> ```
