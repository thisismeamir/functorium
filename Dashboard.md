---
sticker: lucide//layout-dashboard
banner:
---
# Dashboard 

## Models

```dataview
TABLE file.name
FROM #model
```
## Ongoing Projects

```dataview
TABLE 
FROM "agenda/projects"
```

## Agenda
```dataview
TASK
FROM "agenda/projects"
WHERE !completed
GROUP BY file.name
```
## All Todo

```dataview
TASK  
FROM ""  
WHERE !completed
```
