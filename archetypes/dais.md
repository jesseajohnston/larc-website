---
title: "{{ replace (substr .File.ContentBaseName 11) "-" " " | title }}"
date: {{ .Date | time.Format "2006-01-02" }}
affiliation: ""
term: ""
# talkTitle: ""
# location: ""
# eventDateDisplay: ""
# acknowledgment: ""
# image: "talks/YYYYMM_lastname.png"
# links:
#   - label: "Details page"
#     url: ""
---

