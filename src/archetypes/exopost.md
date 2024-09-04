---

author: {{ default "" .Site.Params.Author | title }}
category: {{ default "" .Site.Params.Category | title }}
date: {{ default now .Site.Params.Date | time.Format "2006-01-02" }}
gear: {{ default 0 .Site.Params.Gear }}
question: {{ default 0 .Site.Params.Question }}
title: {{ default "" .Site.Params.Name | title }}
weight: {{ default 0000 (printf "%s%s%s0" .Site.Params.Zone .Site.Params.Gear .Site.Params.Question) }}
zone: {{ default 0 .Site.Params.Zone }}

---

CLUE

HINT: {{< spoiler >}} HINT {{< /spoiler >}}

---

ANSWER: {{< spoiler >}} ANSWER {{< /spoiler >}}

