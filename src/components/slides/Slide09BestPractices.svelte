<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  
  let slideElement: HTMLElement;
  
  onMount(() => {
    animateSlideEntrance(slideElement);
  });

  const doList = [
    { icon: '✅', text: 'Usa <code>console.error()</code> para logs — <code>stdout</code> es JSON-RPC' },
    { icon: '✅', text: 'Tools atómicas — una acción por tool, bien nombrada' },
    { icon: '✅', text: 'Valida inputs — usa Zod (TS) o type hints (Python)' },
    { icon: '✅', text: 'Documenta con docstrings — el LLM las lee como contexto' },
    { icon: '✅', text: 'In-memory primero — persiste solo si el caso lo requiere' }
  ];

  const dontList = [
    { icon: '❌', text: '<code>console.log()</code> en producción — rompe el protocolo JSON-RPC' },
    { icon: '❌', text: 'Tools con 10+ parámetros — divide en tools más pequeñas' },
    { icon: '❌', text: 'Secrets en el código — usa variables de entorno' },
    { icon: '❌', text: 'Ignorar errores — devuelve mensajes claros al LLM' },
    { icon: '❌', text: 'Un tool para todo — la granularidad ayuda al LLM a decidir' }
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Lo que He Aprendido</span>
      <h2 class="title">Buenas Prácticas para MCP Servers</h2>
    </div>

    <div class="practices-grid">
      <div class="practice-column do-column card-glass">
        <h3 class="column-title">DO</h3>
        <ul class="practice-list">
          {#each doList as item}
            <li>
              <span class="icon">{item.icon}</span>
              <span class="text">{@html item.text}</span>
            </li>
          {/each}
        </ul>
      </div>

      <div class="practice-column dont-column card-glass">
        <h3 class="column-title">DON'T</h3>
        <ul class="practice-list">
          {#each dontList as item}
            <li>
              <span class="icon">{item.icon}</span>
              <span class="text">{@html item.text}</span>
            </li>
          {/each}
        </ul>
      </div>
    </div>

    <div class="critical-box card-glass">
      <div class="critical-icon">⚠️</div>
      <div class="critical-content">
        <span class="critical-label">CRÍTICO:</span>
        <div class="critical-text">
          <code>console.log()</code> escribe en <code>stdout</code><br />
          JSON-RPC también usa <code>stdout</code><br />
          <span class="highlight">→ Usa siempre <code>console.error()</code></span>
        </div>
      </div>
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
      radial-gradient(ellipse at 50% 50%, rgba(59, 130, 246, 0.05) 0%, transparent 70%);
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
    gap: var(--spacing-xl);
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

  .practices-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--spacing-xl);
  }

  .practice-column {
    padding: var(--spacing-xl);
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
  }

  .do-column {
    background: rgba(16, 185, 129, 0.05);
    border-color: rgba(16, 185, 129, 0.2);
  }

  .dont-column {
    background: rgba(239, 68, 68, 0.05);
    border-color: rgba(239, 68, 68, 0.2);
  }

  .column-title {
    font-family: var(--font-display);
    font-size: 1.8rem;
    font-weight: 800;
    margin: 0;
    text-align: center;
    letter-spacing: 0.05em;
  }

  .do-column .column-title { color: #10b981; }
  .dont-column .column-title { color: #ef4444; }

  .practice-list {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
  }

  .practice-list li {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    font-size: 1.05rem;
    line-height: 1.5;
    color: var(--color-neutral-light);
    opacity: 0.9;
  }

  .icon {
    font-size: 1.2rem;
    line-height: 1.4;
    flex-shrink: 0;
  }

  .text :global(code) {
    font-family: var(--font-mono);
    font-size: 0.9em;
    background: rgba(0, 0, 0, 0.3);
    padding: 0.1em 0.3em;
    border-radius: 4px;
    color: var(--color-electric);
  }

  .critical-box {
    display: flex;
    align-items: center;
    gap: var(--spacing-lg);
    padding: var(--spacing-lg) var(--spacing-xl);
    background: rgba(245, 158, 11, 0.1);
    border-color: rgba(245, 158, 11, 0.3);
    margin-top: var(--spacing-sm);
  }

  .critical-icon {
    font-size: 3rem;
    line-height: 1;
  }

  .critical-content {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-xs);
  }

  .critical-label {
    font-family: var(--font-display);
    font-size: 1.2rem;
    font-weight: 800;
    color: #f59e0b;
    letter-spacing: 0.05em;
  }

  .critical-text {
    font-family: var(--font-mono);
    font-size: 1rem;
    line-height: 1.6;
    color: var(--color-neutral-light);
  }

  .critical-text code {
    color: #f59e0b;
    background: rgba(0, 0, 0, 0.3);
    padding: 0.1em 0.3em;
    border-radius: 4px;
  }

  .highlight {
    display: inline-block;
    margin-top: var(--spacing-xs);
    color: #10b981;
    font-weight: 700;
  }

  @media (max-width: 1024px) {
    .practices-grid { grid-template-columns: 1fr; gap: var(--spacing-md); }
    .practice-column { padding: var(--spacing-lg); }
    .critical-box { flex-direction: column; text-align: center; }
  }

  @media (max-width: 768px) {
    .title { font-size: clamp(1.6rem, 5vw, 2.5rem); }
    .practice-list li { font-size: 0.95rem; }
    .critical-text { font-size: 0.9rem; }
  }
</style>
