<script lang="ts">
  import SlideToolsGrid from '@codigosinsiesta/theme/slides/SlideToolsGrid.svelte';
</script>

<SlideToolsGrid
  eyebrow="El ecosistema"
  title="Miles de MCP Servers, un protocolo"
  titleHighlight="Miles"
  intro="No reinventes la rueda — busca primero en `mcp.run`, `smithery.ai` o `glama.ai`. Probablemente ya existe."
  columns={3}
  tools={[
    { icon: '🗃️', title: 'Bases de datos', tag: 'Data', body: 'PostgreSQL · SQLite · MongoDB · Redis', meta: ['Local', 'Cloud'] },
    { icon: '🌐', title: 'APIs', tag: 'Integrations', body: 'GitHub · Slack · Jira · Notion', meta: ['OAuth', 'API Key'] },
    { icon: '📁', title: 'Filesystem', tag: 'Files', body: 'Local files · Google Drive · S3', meta: ['Read', 'Write'] },
    { icon: '🔍', title: 'Búsqueda', tag: 'Search', body: 'Brave · Google · Exa · Perplexity', meta: ['Web', 'Semantic'] },
    { icon: '🛠️', title: 'DevTools', tag: 'Dev', body: 'Docker · Kubernetes · Terraform · Git', meta: ['CLI', 'API'] },
    { icon: '🧠', title: 'AI/ML', tag: 'AI', body: 'Hugging Face · Replicate · Stability AI', meta: ['Models', 'Inference'] }
  ]}
/>
