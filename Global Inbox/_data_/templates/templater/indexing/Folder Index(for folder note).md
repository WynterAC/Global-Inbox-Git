`

```dataview
TABLE excerpt AS Comment, file.cday AS Date 
FROM "<% tp.file.folder(true) %>"
WHERE date>0
SORT date asc
```