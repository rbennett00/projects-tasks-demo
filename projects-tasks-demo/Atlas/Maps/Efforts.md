---
up:
  - "[[Welcome]]"
in:
  - "[[Collections]]"
created: 2023-08-19
tags:
  - map/view
---
This page is pretty much identical to Nick's Efforts map, except it uses the `project_status` property in the project template instead of the folder structure  where a project is stored.

> [!Box]+ ### 🔥 On
> ``` dataview
> TABLE WITHOUT ID
> file.link as "",
> area as "Area",
> rank as "Rank"
> FROM "Efforts"
> WHERE (type = "project") AND (project_status = "🔥 On")
> SORT rank desc
> ```

> [!Box]+ ### ♻️ Ongoing
> ``` dataview
> TABLE WITHOUT ID
> file.link as "",
> area as "Area",
> rank as "Rank"
> FROM "Efforts"
> WHERE project_status = "♻️ Ongoing"
> SORT rank desc
> ```

> [!Box]+ ### 〰️ Simmering
> Efforts can easily move from `on` to `simmering` in the background.
>
> ``` dataview
> TABLE WITHOUT ID
> file.link as "",
> area as "Area",
> rank as "Rank"
> FROM "Efforts"
> WHERE project_status = "〰️ Simmering"
> ```

---
[[Get some new flair]]
Back to `= this.up`