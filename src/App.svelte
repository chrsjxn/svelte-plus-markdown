<script>
import Markdown from "./Markdown.svelte"
import { onMount } from 'svelte'
let exampleMarkdown = ''

onMount(async () => {
    exampleMarkdown = (await import('./example.md')).default
})
</script>

<Markdown markdown={exampleMarkdown} />
