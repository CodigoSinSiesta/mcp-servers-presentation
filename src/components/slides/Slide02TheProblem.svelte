<script lang="ts">
  import SlideCompare from '@codigosinsiesta/theme/slides/SlideCompare.svelte';
</script>

<SlideCompare
  eyebrow="El problema"
  title="N×M: La Pesadilla de las Integraciones"
  titleHighlight="N×M"
  leftKind="err"
  rightKind="ok"
  left={{
    label: 'Sin MCP',
    headline: 'N agentes × M servicios = caos',
    items: [
      'Cada agente necesita su propia integración con cada servicio',
      'GitHub, Slack, Postgres, Notion… integraciones ad-hoc',
      'Sin estándar de seguridad ni autenticación común',
      'Imposible reutilizar código entre proyectos',
      'Mantenimiento exponencial con cada nuevo agente o servicio'
    ]
  }}
  right={{
    label: 'Con MCP',
    headline: 'Un protocolo para todo',
    items: [
      'Un servidor MCP expone cualquier servicio de forma estándar',
      'Cualquier agente compatible consume cualquier MCP server',
      'Autenticación, logging y control de permisos integrados',
      'Reutilizable: escribe una vez, usa desde Claude, Cursor, Windsurf…',
      'Ecosistema de miles de servidores ya disponibles'
    ]
  }}
/>
