<!-- src/Markdown.svelte -->
<script>
    import MarkdownIt from 'markdown-it'
    import 'highlight.js/styles/a11y-light.css'
  
    import hljs from 'highlight.js'
  
    export let markdown = ''
  
    // Initialize `markdown-it`
    const md = new MarkdownIt({
        highlight: function (str, lang) {
        if (lang && hljs.getLanguage(lang)) {
          try {
            return hljs.highlight(lang, str).value
          } catch (e) {
            // eslint-disable-next-line no-console
            console.error('Failed to highlight string')
          }
        }
        return '' // use external default escaping
      },
    })
  
    // Render to an html string
    const rendered = md.render(markdown)
  </script>
  
  <!-- Render with the `@html` directive -->
  <div>
    {@html rendered}
  </div>
