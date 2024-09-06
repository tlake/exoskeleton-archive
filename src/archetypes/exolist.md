---

title: "{{ default "" .Site.Params.name | title }}"

type: "exo"
exoevent: "{{ default "" .Site.Params.name | urlize }}"
cascade:
  type: "exo"
  exoevent: "{{ default "" .Site.Params.name | urlize }}"

---
{{ if .Site.Params.contributors }}
## Contributors:
{{- $contributors := split .Site.Params.contributors "|" }}
{{ range $contributors }}
  - {{ . }}
{{- end }}
{{- end }}

