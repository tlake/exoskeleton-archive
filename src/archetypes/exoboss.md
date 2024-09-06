---
weight: {{ printf "%d%d%d0" (default 0 .Site.Params.zone) (default 0 .Site.Params.gear) (default 0 .Site.Params.question) }}

gear_theme: "{{ default "" .Site.Params.gear_theme }}"
question: {{ default 0 .Site.Params.question }}

image_path: "{{ default "" .Site.Params.image_path }}"
clue: "{{ default "" .Site.Params.clue }}"
{{- if .Site.Params.free_hints }}
free_hints:
{{- $free_hints := split .Site.Params.free_hints "|" }}
{{- range $free_hints }}
  - "{{ . }}"
{{- end }}
{{- if .Site.Params.hints }}
hints:
{{- $hints := split .Site.Params.hints "|" }}
{{- range $hints }}
  - "{{ . }}"
{{- end }}
solution: "{{ default "" .Site.Params.solution }}"

author: "{{ default "Minion #00000" .Site.Params.author | title }}"

date: {{ default now .Site.Params.date | time.Format "2006-01-02" }}

---

