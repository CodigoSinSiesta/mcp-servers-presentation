<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  
  let slideElement: HTMLElement;
  
  onMount(() => {
    animateSlideEntrance(slideElement);
  });
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Las Tres Primitivas</span>
      <h2 class="title">Tools, Resources y Prompts</h2>
      <p class="subtitle">El LLM controla Tools · El usuario controla Resources y Prompts</p>
    </div>

    <div class="main-layout">
      <div class="primitive-card card-glass card-blue">
        <div class="card-icon">🔧</div>
        <h3 class="card-title">Tools</h3>
        <p class="card-desc">Funciones que el LLM puede llamar activamente</p>
        <div class="code-snippet">
          <code>agregar_marcador(url, titulo, categoria)</code>
        </div>
      </div>

      <div class="primitive-card card-glass card-green">
        <div class="card-icon">📄</div>
        <h3 class="card-title">Resources</h3>
        <p class="card-desc">Datos que el server expone (read-only, pull)</p>
        <div class="code-snippet">
          <code>marcadores://todos</code>
        </div>
      </div>

      <div class="primitive-card card-glass card-purple">
        <div class="card-icon">💬</div>
        <h3 class="card-title">Prompts</h3>
        <p class="card-desc">Templates reutilizables de conversación</p>
        <div class="code-snippet">
          <code>organizar_marcadores(criterio)</code>
        </div>
      </div>
    </div>

    <div class="bottom-note">
      <p>En el taller construiremos las tres</p>
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
      radial-gradient(ellipse at 50% 50%, rgba(59, 130, 246, 0.05) 0%, transparent 60%);
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
    margin-bottom: var(--spacing-xs);
    line-height: 1.15;
  }

  .subtitle {
    font-size: 1.1rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    font-family: var(--font-body);
  }

  .main-layout {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: var(--spacing-xl);
    align-items: stretch;
  }

  .primitive-card {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
    padding: var(--spacing-xl);
    text-align: center;
    align-items: center;
  }

  .card-icon {
    font-size: 3rem;
    line-height: 1;
    margin-bottom: var(--spacing-sm);
  }

  .card-title {
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--color-neutral-light);
    margin-bottom: 0;
  }

  .card-desc {
    font-size: 0.95rem;
    color: var(--color-neutral-light);
    opacity: 0.75;
    line-height: 1.5;
    flex-grow: 1;
  }

  .code-snippet {
    background: rgba(10, 22, 40, 0.6);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: var(--radius-sm);
    padding: var(--spacing-sm) var(--spacing-md);
    width: 100%;
    margin-top: auto;
  }

  .code-snippet code {
    font-family: var(--font-mono);
    font-size: 0.85rem;
    color: var(--color-electric);
    word-break: break-all;
  }

  /* Color Accents */
  .card-blue {
    border-top: 3px solid var(--color-accent-bright);
  }
  
  .card-green {
    border-top: 3px solid #10b981;
  }
  .card-green .code-snippet code {
    color: #34d399;
  }
  
  .card-purple {
    border-top: 3px solid #8b5cf6;
  }
  .card-purple .code-snippet code {
    color: #a78bfa;
  }

  .bottom-note {
    text-align: center;
    margin-top: var(--spacing-md);
  }

  .bottom-note p {
    display: inline-block;
    font-family: var(--font-mono);
    font-size: 0.85rem;
    color: var(--color-electric);
    background: rgba(59, 130, 246, 0.1);
    padding: var(--spacing-sm) var(--spacing-lg);
    border-radius: var(--radius-xl);
    border: 1px solid rgba(96, 165, 250, 0.2);
  }

  /* Responsive */
  @media (max-width: 900px) {
    .main-layout {
      grid-template-columns: 1fr;
      gap: var(--spacing-md);
    }
    
    .primitive-card {
      padding: var(--spacing-lg);
      flex-direction: row;
      text-align: left;
      flex-wrap: wrap;
    }
    
    .card-icon {
      font-size: 2rem;
      margin-bottom: 0;
    }
    
    .card-title {
      font-size: 1.2rem;
    }
    
    .card-desc {
      width: 100%;
      margin-bottom: 0;
    }
    
    .code-snippet {
      width: 100%;
    }
  }

  @media (max-width: 768px) {
    .slide-content {
      padding: var(--spacing-lg) var(--spacing-md);
      gap: var(--spacing-lg);
    }

    .title {
      font-size: clamp(1.6rem, 5vw, 2.4rem);
    }
    
    .subtitle {
      font-size: 0.9rem;
    }
  }

  @media (max-width: 480px) {
    .slide-content {
      padding: var(--spacing-md) var(--spacing-sm);
      gap: var(--spacing-md);
    }

    .label {
      font-size: 0.7rem;
    }

    .title {
      font-size: clamp(1.4rem, 6vw, 1.8rem);
    }
    
    .primitive-card {
      padding: var(--spacing-md);
      gap: var(--spacing-sm);
    }
    
    .card-icon {
      font-size: 1.5rem;
    }
    
    .card-title {
      font-size: 1.1rem;
    }
    
    .card-desc {
      font-size: 0.85rem;
    }
    
    .code-snippet code {
      font-size: 0.75rem;
    }
    
    .bottom-note p {
      font-size: 0.75rem;
      padding: var(--spacing-xs) var(--spacing-md);
    }
  }
</style>