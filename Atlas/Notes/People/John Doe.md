---
tags: 
first-name: 
last-name: 
aliases: 
person-slug: 
job-title: 
organization-slug: 
product-slug: 
reports-to: 
web: 
email: 
mobile: 
phone: 
twitter-id: 
reddit-id: 
facebook-id: 
medium-id: 
linkedin-id: 
discord-id: 
youtube: 
github-id: 
city: 
country: 
type: person
peopleDomain:
  - work
  - sales
template_version: "1.1"
in:
  - "[[People]]"
---
> [!user] Bio
> 1. `what's their story?` 

> [!cite] References
> 1. `links that mention them` 


> [!network] Connections
>- `people they know or that quote them`

> [!write] Work
> 1. 

> [!BIKE] Interests
>
## Meeting Log
```dataview
TABLE WITHOUT ID meeting_date as Date, file.link as "Topic"
FROM "Calendar/meetings" where contains(attendees, this.file.link)
SORT file.cday DESC
```

## Related Projects
```dataview
TABLE WITHOUT ID file.link as Project
FROM "Efforts" where contains(stakeholders, this.file.link) or contains(project_team, this.file.link)
```
