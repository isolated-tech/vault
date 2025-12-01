# 🎬 Video Pipeline Dashboard

## 💡 Ideas
```dataview
TABLE priority AS "⭐", category AS "Category"
FROM "Video Ideas"
WHERE status = "💡 idea"
SORT priority DESC

TABLE priority AS "⭐", category AS "Category"
FROM "Video Ideas"
WHERE status = "📝 scripting"
SORT priority DESC

TABLE priority AS "⭐", category AS "Category"
FROM "Video Ideas"
WHERE status = "🎬 filming"
SORT priority DESC

TABLE priority AS "⭐", category AS "Category"
FROM "Video Ideas"
WHERE status = "📤 ready"
SORT priority DESC

TABLE published AS "Date", link AS "URL"
FROM "Video Ideas"
WHERE status = "✅ published"
SORT published DESC

```