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
TABLE status, priority
FROM #project AND #ongoing
```

## Previous Projects

```dataview
TABLE 
FROM #project AND #done
```
