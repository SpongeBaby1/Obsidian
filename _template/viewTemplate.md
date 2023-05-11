---
alias: <% tp.file.cursor(1) %>
year: <% tp.file.cursor(2) %>
sort: <% tp.file.cursor(3) %>
nation: <% tp.file.cursor(4) %>
crew: <% tp.file.cursor(5) %>
rate: <% tp.file.cursor(6) %>
info: <% tp.file.cursor(7) %>
date: {{DATE:YYYY-MM-DD-dddd HH:mm:ss}}
update: 
tags: [view/year{{DATE:YYYY}}, view/month{{DATE:MM}}]
id: view{{DATE:YYYYMMDDHHmmss}}
---
---

<% tp.file.cursor(7) %>