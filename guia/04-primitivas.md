# Primitivas de MCP

## Tiempo estimado
3 minutos

## Puntos clave
- Tools: funciones que el LLM llama activamente (model-controlled).
- Resources: datos que el server expone, el usuario los activa (app-controlled).
- Prompts: templates reutilizables de conversación (user-controlled).

## Datos relevantes
- El LLM decide cuándo usar Tools basándose en su descripción.
- Tú decides cuándo usar Resources y Prompts para dar contexto.

## Transición
"Veamos cómo se construye un server con estas primitivas..."

## Notas
- Diferenciar claramente quién tiene el control en cada primitiva.
- Poner ejemplos rápidos: Tool (buscar en DB), Resource (un log), Prompt (review de código).
