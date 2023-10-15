> [!warning] Backlog
> ```dataview
> task
> where
> 	!completed
> 	and (
> 		(due and due < date(today))
> 		or
> 		(scheduled and scheduled < date(today))
> 	)
> group by link
> ```

> [!important] Today
> ```dataview
> task
> where
> 	due = date(today) 
> 	or scheduled = date(today)
> 	or completion = date(today)
> group by link
> ```

> [!info]- Tomorrow
> ```dataview
> task
> where
> 	due = date(tomorrow) 
> 	or scheduled = date(tomorrow)
> 	or completion = date(tomorrow)
> group by link
> ```

> [!quote]+ Bookmarks
> ```dataview
> task
> where
> 	!completed and econtains(tags, "#bookmark") and econtains(tags, "#task")
> group by link
> ```

> [!example]- Upcoming
> ```dataview
> task
> where
> 	
> 	!completed and econtains(tags, "#task")
> 	and (
> 		(due and due > date(tomorrow ))
> 		or
> 		(scheduled and scheduled > date(tomorrow))
> 		or
> 		(!scheduled and !due)
> 	)
> group by link
> ```
