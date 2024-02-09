---
up:
  - "[[Welcome]]"
in:
  - "[[Collections]]"
created: 2023-08-19
tags:
  - map/view
---
Keep your priorities in order. Quickly adjust your bandwidth as needed. 

> [!Box]+ ### 🔥 On
> ``` dataview
> TABLE WITHOUT ID
> file.link as "",
> area as "Area",
> rank as "Rank"
> WHERE (type = "project") AND (project_status = "on")
> SORT rank desc
> ```


> [!Box]+ ### ♻️ Ongoing
> ``` dataview
> TABLE WITHOUT ID
> file.link as "",
> area as "Area",
> rank as "Rank"
> FROM "projects"
> WHERE project_status = "ongoing"
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
> FROM "projects"
> WHERE project_status = "simmering"
> ```

---

Back to `= this.up`