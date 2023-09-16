---
title: "configuring blogs"
date: 2023-07-29T16:15:42+05:30
draft: true
---

From your `baseof.html` file, it seems like the footer is included twice:

```html
...
<div class="max-w:700 w:full box:content-box">
    {{- block "main" . }}{{- end }}
    {{- partial "footer.html" . -}}
</div>
...
{{ partial "footer.html" . }}
...
```

You should probably only include the footer once, so you should remove one of the `{{ partial "footer.html" . }}` lines.

Since the second footer is outside of the main `<div>`, I suggest you remove the first `{{ partial "footer.html" . }}` line:

```html
<!DOCTYPE html>
<html>
{{- partial "head.html" . -}}

<body class="bg:fade-84@dark font:fade-16@dark font:sans">
    {{ partial "header.html" . -}}
    <div class="d:flex flex:column@<=sm pt:90 px:24 jc:center gap:44 word-break:break-word">
        {{- block "side" . }}{{- end }}
        <div class="max-w:700 w:full box:content-box">
            {{- block "main" . }}{{- end }}
        </div>
    </div>
    {{ partial "footer.html" . }}
</body>

</html>
```

Also, ensure your `footer.html` partial is correctly formatted. It should contain something like:

```html
<footer>
  Powered by <a href="https://gohugo.io/">Hugo</a> & <a href="https://github.com/serkodev/holy">Holy theme</a>
</footer>
```

Remember to save your changes and restart the Hugo server to see them reflected on your site. If you're still having trouble, please let me know!
