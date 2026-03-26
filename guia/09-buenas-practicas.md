# Buenas Prácticas

## Tiempo estimado
3 minutos

## Puntos clave
- DO: usar console.error, crear tools atómicas, validar inputs.
- DON'T: usar console.log, tools con 10+ parámetros, exponer secrets.
- El error más común: romper el canal stdio con logs accidentales.

## Datos relevantes
- Las descripciones de las herramientas son "ingeniería de prompts".
- Validar los inputs previene alucinaciones y errores de ejecución.

## Transición
"¡Ahora sí, vamos a construirlo!"

## Notas
- Ser muy insistente con el tema de console.log vs console.error.
- Explicar que una herramienta que hace "demasiado" confunde al LLM.
