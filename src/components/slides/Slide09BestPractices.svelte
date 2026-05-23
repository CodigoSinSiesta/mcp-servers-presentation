<script lang="ts">
  import SlideCompare from '@codigosinsiesta/theme/slides/SlideCompare.svelte';
</script>

<SlideCompare
  eyebrow="Lo que he aprendido"
  title="Buenas prácticas para MCP Servers"
  titleHighlight="Buenas prácticas"
  leftKind="err"
  rightKind="ok"
  left={{
    label: "DON'T",
    headline: 'Errores que rompen el servidor',
    items: [
      'console.log() en producción — rompe el protocolo JSON-RPC',
      'Tools con 10+ parámetros — divide en tools más pequeñas',
      'Secrets en el código — usa variables de entorno',
      'Ignorar errores — devuelve mensajes claros al LLM',
      'Un tool para todo — la granularidad ayuda al LLM a decidir'
    ]
  }}
  right={{
    label: 'DO',
    headline: 'Patrones que funcionan',
    items: [
      'Usa console.error() para logs — stdout es JSON-RPC',
      'Tools atómicas — una acción por tool, bien nombrada',
      'Valida inputs — usa Zod (TS) o type hints (Python)',
      'Documenta con docstrings — el LLM las lee como contexto',
      'In-memory primero — persiste solo si el caso lo requiere'
    ]
  }}
/>
