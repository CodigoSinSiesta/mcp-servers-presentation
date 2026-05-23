<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="Aplicaciones"
  title="¿Dónde brillan los MCPs?"
  titleHighlight="brillan"
  columns={2}
  items={[
    {
      title: 'Dev Tooling',
      body: 'Conecta tu IDE con **bases de datos, APIs internas y servicios en la nube**. Sin salir de tu flujo de trabajo. Un `@postgres` en el chat y consultas directo.'
    },
    {
      title: 'Data & Analytics',
      body: '**Consulta dashboards, genera informes, accede a métricas** en tiempo real desde la conversación. Metabase, BigQuery, Grafana — todos con el mismo protocolo.'
    },
    {
      title: 'Agent Augmentation',
      body: 'Da acceso a herramientas externas a tus agentes. **El MCP es el puente entre el LLM y el mundo real**. Sin MCP, el agente solo habla. Con MCP, actúa.'
    },
    {
      title: 'Enterprise Integration',
      body: 'Conecta **sistemas legacy sin reescribir código**. El MCP adapta la interfaz, tú mantienes el backend. ERP, CRM, sistemas COBOL — todos accesibles desde el agente.'
    }
  ]}
/>
