
---
tags: 
- person 
first-name: y 
last-name: y 
aliases: y 
person-slug: y 
job-title: --- 
organization:  
product-slug: 
reports-to: 
web: 
email: undefined 
mobile: phone: 
twitter-id: 
reddit-id: 
facebook-id: 
medium-id: l
inkedin-id: 
discord-id: 
youtube: 
github-id: 
city: 
country: 
type: person 
peopleDomain: 
template_version: "1.1" 
cssclass:
undefined

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
SORT file.cday DESC
```
undefined