<script lang="ts">
  import SlideDidactic from '@codigosinsiesta/theme/slides/SlideDidactic.svelte';
</script>

<SlideDidactic
  eyebrow="Fundamentos"
  title="¿Qué es MCP?"
  titleHighlight="MCP"
  definition={{
    title: 'Model Context Protocol',
    body: 'Protocolo abierto creado por **Anthropic en 2024**. Hoy lo usan Claude, Cursor, Windsurf, VS Code y más. Estandariza cómo los LLMs acceden a tools, resources y prompts externos.'
  }}
  analogy={{
    title: 'Analogía: USB para agentes',
    body: 'Igual que **USB estandarizó** cómo conectar periféricos a ordenadores, MCP estandariza cómo los agentes se conectan a herramientas y datos. Plug & play para LLMs.'
  }}
  examples={{
    title: 'Transporte estándar',
    items: [
      'stdio — para servidores locales (el más común)',
      'HTTP/SSE — para servidores remotos y en la nube',
      'JSON-RPC 2.0 — el protocolo de comunicación',
      'Ligero y universal: cualquier lenguaje puede implementarlo'
    ]
  }}
/>
