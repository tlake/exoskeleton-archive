---

title: "{{ default "" .Site.Params.name | title }}"

type: "exo"
exoevent: "{{ default "" .Site.Params.name | urlize }}"
cascade:
  type: "exo"
  exoevent: "{{ default "" .Site.Params.name | urlize }}"

date: {{ default now .Site.Params.date | time.Format "2006-01-02" }}

---
{{ if .Site.Params.contributors }}
## Contributors:
{{- $contributors := split .Site.Params.contributors "|" }}
{{ range $contributors }}
  - {{ . }}
{{- end }}
{{- end }}

