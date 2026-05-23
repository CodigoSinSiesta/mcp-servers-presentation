<script lang="ts">
  import SlideCode from '@codigosinsiesta/theme/slides/SlideCode.svelte';
</script>

<SlideCode
  eyebrow="Manos al código"
  title="Anatomía de un MCP Server"
  titleHighlight="MCP Server"
  language="typescript"
  code={`import { Server } from "@modelcontextprotocol/sdk/server/index.js";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";
import { ListToolsRequestSchema, CallToolRequestSchema } from "@modelcontextprotocol/sdk/types.js";

const server = new Server(
  { name: "MiServidor", version: "1.0.0" },
  { capabilities: { tools: {} } }
);

server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [{ name: "mi_tool", description: "...", inputSchema: { ... } }]
}));

server.setRequestHandler(CallToolRequestSchema, async (req) => {
  return { content: [{ type: "text", text: "resultado" }] };
});

const transport = new StdioServerTransport();
await server.connect(transport);`}
  annotations={[
    { line: 1, text: 'Imports del SDK oficial' },
    { line: 5, text: 'Crear el servidor' },
    { line: 10, text: 'Registrar las tools' },
    { line: 14, text: 'Implementar la lógica' },
    { line: 18, text: 'Conectar por stdio' }
  ]}
  callout={{
    kind: 'info',
    title: 'Nota',
    body: 'Usa `console.error()` para logs — **stdout está reservado para JSON-RPC**. Un `console.log()` rompe el protocolo.'
  }}
/>
