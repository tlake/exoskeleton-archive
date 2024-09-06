---

weight: {{ printf "%d%d%d0" (default 0 .Site.Params.zone) (default 0 .Site.Params.gear) (default 0 .Site.Params.question) }}

zone: {{ default 0 .Site.Params.zone }}
gear: {{ default 0 .Site.Params.gear }}
gear_theme: "{{ default "" .Site.Params.gear_theme }}"
question: {{ default 0 .Site.Params.question }}

title: "{{ default "" .Site.Params.name | title }}"

image_path: "{{ default "" .Site.Params.image_path }}"
clue: "{{ default "" .Site.Params.clue }}"
{{- if not .Site.Params.free_hints }}
free_hints: []
{{- else }}
free_hints:
{{- $free_hints := split .Site.Params.free_hints "|" }}
{{- range $free_hints }}
  - "{{ . }}"
{{- end }}
{{- end }}
{{- if not .Site.Params.hints }}
hints: []
{{- else }}
hints:
{{- $hints := split .Site.Params.hints "|" }}
{{- range $hints }}
  - "{{ . }}"
{{- end }}
{{- end }}
solution: "{{ default "" .Site.Params.solution }}"

author: "{{ default "Minion #00000" .Site.Params.author | title }}"

date: {{ default now .Site.Params.date | time.Format "2006-01-02" }}

---

