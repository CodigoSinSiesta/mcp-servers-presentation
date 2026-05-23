<script lang="ts">
  import SlideCodeCompare from '@codigosinsiesta/theme/slides/SlideCodeCompare.svelte';
</script>

<SlideCodeCompare
  eyebrow="¿Y si fuera más fácil?"
  title="FastMCP: De ~100 líneas a 6"
  titleHighlight="FastMCP"
  leftLabel="SDK Oficial (TypeScript)"
  leftLang="typescript"
  leftCode={`// ~14 líneas de boilerplate...
import { Server } from "@modelcontextprotocol/sdk/...";
import { StdioServerTransport } from "...";
import { ListToolsRequestSchema, CallToolRequestSchema } from "...";

const server = new Server({ name: "math" }, { capabilities: { tools: {} } });

server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [{ name: "sumar", description: "Suma dos números",
    inputSchema: { type: "object", properties: { a: { type: "number" }, b: { type: "number" } }, required: ["a","b"] }
  }]
}));

server.setRequestHandler(CallToolRequestSchema, async (req) => {
  const { a, b } = req.params.arguments as { a: number; b: number };
  return { content: [{ type: "text", text: String(a + b) }] };
});
const transport = new StdioServerTransport();
await server.connect(transport);`}
  rightLabel="FastMCP (Python)"
  rightLang="python"
  rightCode={`from fastmcp import FastMCP

mcp = FastMCP("math")

@mcp.tool
def sumar(a: int, b: int) -> int:
    """Suma dos números"""
    return a + b

if __name__ == "__main__":
    mcp.run()`}
/>
