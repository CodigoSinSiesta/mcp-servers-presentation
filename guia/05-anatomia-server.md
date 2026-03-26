# Anatomía de un Server

## Tiempo estimado
4 minutos

## Puntos clave
- Recorrido del código: imports, instancia del server, handlers y transporte.
- inputSchema: el contrato fundamental con el LLM (JSON Schema).
- content: la respuesta que recibe el modelo (texto, imagen, etc).

## Datos relevantes
- CRÍTICO: usar console.error para logs, no console.log.
- El transporte stdio usa stdout para JSON-RPC; cualquier otro log lo rompe.

## Transición
"¿Y si hubiera una forma más simple? FastMCP..."

## Notas
- Mostrar un ejemplo mínimo en TypeScript.
- Explicar por qué el tipado y las descripciones son vitales para el LLM.
