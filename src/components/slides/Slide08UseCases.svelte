<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  
  let slideElement: HTMLElement;
  
  onMount(() => {
    animateSlideEntrance(slideElement);
  });

  const useCases = [
    {
      icon: '🔧',
      title: 'Dev Tooling',
      desc: 'Conecta tu IDE con bases de datos, APIs internas y servicios en la nube. Sin salir de tu flujo de trabajo.',
      code: `"mcpServers": {
  "postgres": {
    "command": "npx",
    "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://..."]
  }
}`
    },
    {
      icon: '📊',
      title: 'Data & Analytics',
      desc: 'Consulta dashboards, genera informes, accede a métricas en tiempo real desde la conversación.',
      code: `"mcpServers": {
  "metabase": {
    "command": "python",
    "args": ["-m", "mcp_metabase", "--url", "https://..."]
  }
}`
    },
    {
      icon: '🤖',
      title: 'Agent Augmentation',
      desc: 'Da acceso a herramientas externas a tus agentes. El MCP es el puente entre el LLM y el mundo real.',
      code: `"mcpServers": {
  "github": {
    "command": "npx",
    "args": ["-y", "@modelcontextprotocol/server-github"]
  }
}`
    },
    {
      icon: '🏢',
      title: 'Enterprise Integration',
      desc: 'Conecta sistemas legacy sin reescribir código. El MCP adapta la interfaz, tú mantienes el backend.',
      code: `"mcpServers": {
  "legacy-erp": {
    "command": "java",
    "args": ["-jar", "erp-mcp-adapter.jar"]
  }
}`
    }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">En la Práctica</span>
      <h2 class="title">¿Dónde Brillan los MCPs?</h2>
    </div>

    <div class="use-cases-grid">
      {#each useCases as useCase}
        <div class="use-case-card card-glass">
          <div class="card-header">
            <span class="card-icon">{useCase.icon}</span>
            <h3 class="card-title">{useCase.title}</h3>
          </div>
          <p class="card-desc">{useCase.desc}</p>
          <div class="code-snippet">
            <div class="code-header">
              <span class="dot red"></span>
              <span class="dot yellow"></span>
              <span class="dot green"></span>
              <span class="filename">claude_desktop_config.json</span>
            </div>
            <pre><code>{useCase.code}</code></pre>
          </div>
        </div>
      {/each}
    </div>
  </div>
</div>

<style>
  .swiper-slide {
    position: relative;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .slide-background {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse at 20% 80%, rgba(59, 130, 246, 0.08) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 20%, rgba(30, 58, 138, 0.12) 0%, transparent 50%);
    z-index: 1;
  }

  .slide-content {
    position: relative;
    z-index: 2;
    max-width: 1200px;
    width: 100%;
    padding: var(--spacing-2xl) var(--spacing-content);
    display: flex;
    flex-direction: column;
    gap: var(--spacing-2xl);
  }

  .slide-header {
    text-align: center;
  }

  .label {
    display: inline-block;
    font-family: var(--font-mono);
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.15em;
    color: var(--color-electric);
    margin-bottom: var(--spacing-sm);
  }

  .title {
    font-size: clamp(2rem, 4.5vw, 3.2rem);
    font-weight: 800;
    color: var(--color-neutral-light);
    margin-bottom: 0;
    line-height: 1.15;
  }

  .use-cases-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: var(--spacing-xl);
  }

  .use-case-card {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
    padding: var(--spacing-xl);
    transition: all var(--transition-base);
  }

  .card-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
  }

  .card-icon {
    font-size: 2rem;
    line-height: 1;
  }

  .card-title {
    font-family: var(--font-display);
    font-size: 1.4rem;
    font-weight: 700;
    color: var(--color-neutral-light);
    margin: 0;
  }

  .card-desc {
    font-size: 0.95rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.6;
    margin: 0;
    flex-grow: 1;
  }

  .code-snippet {
    background: rgba(10, 22, 40, 0.6);
    border: 1px solid rgba(59, 130, 246, 0.2);
    border-radius: var(--radius-md);
    overflow: hidden;
    margin-top: var(--spacing-sm);
  }

  .code-header {
    display: flex;
    align-items: center;
    gap: 6px;
    padding: 8px 12px;
    background: rgba(0, 0, 0, 0.2);
    border-bottom: 1px solid rgba(59, 130, 246, 0.1);
  }

  .dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
  }

  .dot.red { background: #ff5f56; }
  .dot.yellow { background: #ffbd2e; }
  .dot.green { background: #27c93f; }

  .filename {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    color: var(--color-neutral-light);
    opacity: 0.5;
    margin-left: 8px;
  }

  pre {
    margin: 0;
    padding: 12px;
    overflow-x: auto;
  }

  code {
    font-family: var(--font-mono);
    font-size: 0.8rem;
    color: var(--color-electric);
    line-height: 1.5;
    white-space: pre;
  }

  @media (max-width: 1024px) {
    .use-cases-grid { grid-template-columns: 1fr; gap: var(--spacing-md); }
    .use-case-card { padding: var(--spacing-lg); }
  }

  @media (max-width: 768px) {
    .title { font-size: clamp(1.6rem, 5vw, 2.5rem); }
  }
</style>
