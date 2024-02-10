---
in:
  - "[[Collections]]"
tags:
  - "#map/view"
created: 2023-11-21
---
This note collects all notes where the `in` property says `Meetings`.

> [!calendar]+ # Meetings
> ```dataview
> TABLE WITHOUT ID
> 	file.link as Note,
> 	join(list(attendees)) as Group,
> 	project as Project
> WHERE
> 	contains(in, this.file.link) and
> 	!contains(file.name, "Template")
> SORT file.name desc
> ```

---


