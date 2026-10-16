---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
date: {{ .Date | time.Format "2006-01-02" }}
# author: type name here; note that as of fall 2026 there is no capacity to show or link to author profile
---

