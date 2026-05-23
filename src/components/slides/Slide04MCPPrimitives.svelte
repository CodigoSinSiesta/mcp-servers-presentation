<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="Las primitivas"
  title="Tools, Resources y Prompts"
  titleHighlight="Tools"
  columns={3}
  items={[
    {
      title: 'Tools',
      body: 'Funciones que **el LLM controla y puede llamar activamente**. Tienen un nombre, descripción y JSON Schema para validar los inputs. Son la primitiva más usada.'
    },
    {
      title: 'Resources',
      body: 'Datos que **el usuario controla**. El servidor expone URIs (ficheros, endpoints) que la aplicación cliente inyecta en el contexto cuando los necesita.'
    },
    {
      title: 'Prompts',
      body: 'Plantillas de mensajes reutilizables definidas en el servidor. Permiten estandarizar flujos complejos y compartirlos entre usuarios y agentes.'
    }
  ]}
/>
