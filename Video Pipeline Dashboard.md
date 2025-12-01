# 🎬 Video Pipeline Dashboard

## 💡 Ideas
```dataview
TABLE priority AS "Priority", category AS "Category"
FROM "Video Ideas"
WHERE status = "idea" 
SORT priority DESC

TABLE priority AS "Priority", category AS "Category"
FROM "Video Ideas"
WHERE status = "scripting"
SORT priority DESC

TABLE priority AS "Priority", category AS "Category"
FROM "Video Ideas"
WHERE status = "filming"
SORT priority DESC


```dataview
TABLE priority AS "Priority", category AS "Category"
FROM "Video Ideas"
WHERE status = "ready"
SORT priority DESC
```
```dataview
TABLE published AS "Date", link AS "URL"
FROM "Video Ideas"
WHERE status = "published"
SORT published DESC
```
