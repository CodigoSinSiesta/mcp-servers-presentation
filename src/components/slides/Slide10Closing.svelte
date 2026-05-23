<script lang="ts">
  import SlideResources from '@codigosinsiesta/theme/slides/SlideResources.svelte';
</script>

<SlideResources
  eyebrow="¡Vamos al taller!"
  title="Construyamos un MCP Server"
  titleHighlight="MCP Server"
  closing="Hecho con ♥ por Código Sin Siesta · 2026"
  takeaways={[
    { text: '**MCP** es el estándar abierto para conectar LLMs con herramientas externas.' },
    { text: '**3 primitivas**: Tools (LLM controla) · Resources (usuario controla) · Prompts (plantillas).' },
    { text: '**FastMCP** en Python = 6 líneas vs ~100 del SDK oficial. Usa el que encaje con tu stack.' },
    { text: '`console.error()` para logs — **stdout es JSON-RPC**, no texto libre.' }
  ]}
  links={[
    { icon: '📖', title: 'MCP Docs', url: 'https://modelcontextprotocol.io', tag: 'docs' },
    { icon: '🔍', title: 'mcp.run', url: 'https://mcp.run', tag: 'registry' },
    { icon: '🚀', title: 'FastMCP', url: 'https://github.com/jlowin/fastmcp', tag: 'github' }
  ]}
  qr={{ title: 'modelcontextprotocol.io', url: 'https://modelcontextprotocol.io' }}
/>
