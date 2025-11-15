---
gallon:
workOut:
sugar:
carbs:
headache:
surf:
medicine:
writing:
---
# <% tp.date.now("dddd, MMMM D", 0, tp.file.title, "YYYY-MM-DD") %> 

<  [[<% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD" ) %>]] | [[<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>]]  >

<% tp.web.daily_quote() %>

## Tasks


### Content Creation

- [ ] Write 200 words

<%* let day = tp.date.now("dd") 
if ((day != "Sa") && (day != "Su")) { %> 
### Work

- [ ] Summarize Today's Work
### Work Summary
<%* } else { %>
<%* } %>


## Writing


## Daily

> Daily notes, thoughts, anything, really.

## Sleep