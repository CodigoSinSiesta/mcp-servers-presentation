# ¿Qué es MCP?

## Tiempo estimado
3 minutos

## Puntos clave
- Protocolo abierto creado por Anthropic en 2024.
- JSON-RPC 2.0 como transporte (stdio local, HTTP/SSE remoto).
- Modelo client-server: el server expone capabilities, el client las usa.

## Datos relevantes
- Clientes que lo soportan: Claude, Cursor, Windsurf, VS Code, Continue.
- Permite que cualquier LLM use cualquier herramienta sin código personalizado.

## Transición
"¿Qué puede exponer un MCP server? Tres primitivas..."

## Notas
- Explicar brevemente qué es JSON-RPC para los más técnicos.
- Mencionar que es un estándar que busca ser agnóstico al modelo.
