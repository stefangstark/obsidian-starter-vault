
```dataviewjs

let today = DateTime.now().toFormat("yyyy-MM-dd")
let tomorrow = DateTime.now().plus({ days: 1}).toFormat("yyyy-MM-dd")
let tasks = dv.pages().file.tasks
function date(d) { return dv.date(d).toFormat('yyyy-MM-dd') }

function task_callout(tasklist, header) {
	// this needs to copy above define

	const fxns = `
	let today = DateTime.now().toFormat("yyyy-MM-dd")
	let tomorrow = DateTime.now().plus({ days: 1}).toFormat("yyyy-MM-dd")
	let tasks = dv.pages().file.tasks
	function date(d) { return dv.date(d).toFormat('yyyy-MM-dd')}
	`
	const format = `
		.map( t => { t.text = t.text.replace(/^#task/, "").replace(/#bookmark/, ""); return t} )
		.map( t => {t.text = t.text.replace(/${today}/g, ''); return t} )
		.groupBy(t => dv.fileLink(
			t.path, false,
			t.path.replace(".md", "").split("/").slice(1).join(" > ")
		))
	`

	const text = '```dataviewjs\n' + fxns + '\ndv.taskList(\n' + tasklist + format + '\n)\n```'
    const allText = `> ${header}\n` + text;
    const lines = allText.split('\n');
    
    return lines.join('\n> ') + '\n'
}

let open_tasks = tasks.where(t => !t.completed)

// Overdue
let overdue_tasks = open_tasks
	.where( t =>
		!t.text.contains('#bookmark') && t.due && date(t.due) < today
	)

if (overdue_tasks.length > 0) {
	const query = `
		tasks
		.where( t =>
			!t.completed && !t.text.contains('#bookmark') && t.due && date(t.due) < today
		)
	`
	dv.span(task_callout(query, '[!Danger]+ Overdue: '))

}

// Due
let due_tasks = open_tasks
	.where( t => 
		t.due && !t.text.contains('#bookmark') && date(t.due) == today
	)

if (due_tasks.length > 0) {
	const query = `
		tasks
		.where( t =>
			!t.completed
			&& t.due && !t.text.contains('#bookmark') && date(t.due) == today
		)
	`
	dv.paragraph(task_callout(query, '[!important]+ Due: ' + due_tasks.length))
}

//Reschedule
let reschedule_tasks = open_tasks
	.where( t =>
		t.scheduled && !t.text.contains('#bookmark')
		&& date(t.scheduled) < today
	)

if (reschedule_tasks.length > 0) {

	const query = `
		tasks
		.where( t =>
			!t.completed && t.scheduled && !t.text.contains('#bookmark')
			&& (
				dv.date(t.scheduled).toFormat("yyyy-MM-dd")
				< "${today}"
			)
		)
	`
	dv.paragraph(task_callout(query, '[!warning]+ Reschedule: ' + reschedule_tasks.length))
}

// Needs scheduling
let to_schd_tasks = open_tasks
	.where( t =>
		t.due && !t.scheduled && date(t.due) > today
	)

if ( to_schd_tasks.length > 0 ) {
	const query = `
		tasks
		.where( t =>
			!t.completed
			&& t.due && !t.scheduled && date(t.due) > today
		)
	`
	dv.paragraph(task_callout(query, '[!warning]+ Needs Scheduling: ' + to_schd_tasks.length))

}


// Today
let today_tasks = tasks
	.where( t =>
		(t.completion && (date(t.completion) == today))
		|| (t.scheduled && (date(t.scheduled) == today))
	)

if (today_tasks.length > 0) {

	const query = `
		tasks
		.where( t =>
			(t.completion && (date(t.completion) == today))
			|| (t.scheduled && (date(t.scheduled) == today))
		)
		.sort( t => t.completion)
		.map( t => {t.text = t.text.replace(today, ''); return t} )
	`
	dv.paragraph(task_callout(query, '[!todo]+ Today: ' + today_tasks.length))
}

// Tomorrow
let tomorrow_tasks = open_tasks
	.where( t =>	
		(t.scheduled && (date(t.scheduled) == tomorrow))
		|| (t.due && (date(t.due) == tomorrow))
	)

if (tomorrow_tasks.length > 0) {

	const query = `
		tasks
		.where( t =>
			!t.completed
			&& (
				(t.scheduled && (date(t.scheduled) == tomorrow))
				|| (t.due && (date(t.due) == tomorrow))
			)
		)
	`
	dv.paragraph(task_callout(query, '[!summary]- Tomorrow: ' + tomorrow_tasks.length))
}

// Bookmarked
let bookmarked_tasks = open_tasks
	.where( t => !t.completed && t.text.contains('#bookmark'))

if (bookmarked_tasks.length > 0) {
	const query = `
		tasks
		.where( t => !t.completed && t.text.contains('#bookmark'))
		.map( t => {t.text = t.text.replace('#bookmark', ''); return t} )
	`
	dv.paragraph(task_callout(query, '[!quote]+ Bookmarked: ' + bookmarked_tasks.length))

}

//Upcoming

function callout(query, header) {
	const text = '```dataviewjs\n' + query + '\n```'
    const allText = `> ${header}\n` + text;
    const lines = allText.split('\n');
    return lines.join('\n> ') + '\n'
}

const query = `
	dv.taskList(
		dv.pages()
		.file.tasks
		.where( t => 
			!t.completed
			&& t.text.contains('#task')
		)
		.map(t => {t.text = t.text.replace('#task', ''); return t})
		.where( t => 
			(!d.due && !t.scheduled)
			||
			( t.scheduled && dv.date(t.scheduled) > DateTime.now() )
		)
		.groupBy(t => t.scheduled ?? 'Open')
		.groupIn(t => dv.fileLink(
			t.path, false,
			t.path.replace(".md", "").split("/").slice(1).join(" > ")
		))
	)
`
dv.paragraph(callout(query, '[!quote]- Upcoming'))
```