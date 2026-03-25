<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  
  let slideElement: HTMLElement;
  
  onMount(() => {
    animateSlideEntrance(slideElement);
  });

  const categories = [
    {
      icon: '🗃️',
      title: 'Bases de datos',
      items: 'PostgreSQL · SQLite · MongoDB · Redis',
      color: '#3B82F6'
    },
    {
      icon: '🌐',
      title: 'APIs',
      items: 'GitHub · Slack · Jira · Notion',
      color: '#10b981'
    },
    {
      icon: '📁',
      title: 'Filesystem',
      items: 'Local files · Google Drive · S3',
      color: '#f59e0b'
    },
    {
      icon: '🔍',
      title: 'Búsqueda',
      items: 'Brave · Google · Exa · Perplexity',
      color: '#8b5cf6'
    },
    {
      icon: '🛠️',
      title: 'DevTools',
      items: 'Docker · Kubernetes · Terraform · Git',
      color: '#ec4899'
    },
    {
      icon: '🧠',
      title: 'AI/ML',
      items: 'Hugging Face · Replicate · Stability AI',
      color: '#06b6d4'
    }
  ];

  const registries = ['mcp.run', 'smithery.ai', 'glama.ai'];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">El Ecosistema</span>
      <h2 class="title">Miles de MCP Servers,<br />Un Protocolo</h2>
      <p class="subtitle">No reinventes la rueda — busca primero</p>
    </div>

    <div class="categories-grid">
      {#each categories as category}
        <div class="category-card card-glass">
          <div class="category-header">
            <span class="category-icon">{category.icon}</span>
            <h3 class="category-title" style="color: {category.color}">{category.title}</h3>
          </div>
          <p class="category-items">{category.items}</p>
        </div>
      {/each}
    </div>

    <div class="registries-footer">
      <span class="registries-label">Directorios principales:</span>
      <div class="registries-list">
        {#each registries as registry}
          <span class="registry-badge">{registry}</span>
        {/each}
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
      radial-gradient(ellipse at 80% 20%, rgba(59, 130, 246, 0.08) 0%, transparent 50%),
      radial-gradient(ellipse at 10% 80%, rgba(30, 58, 138, 0.12) 0%, transparent 50%);
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
    margin-bottom: var(--spacing-sm);
    line-height: 1.15;
  }

  .subtitle {
    font-size: 1.1rem;
    color: var(--color-electric);
    opacity: 0.8;
    margin-bottom: 0;
  }

  .categories-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: var(--spacing-md);
  }

  .category-card {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
    padding: var(--spacing-xl);
    transition: all var(--transition-base);
  }

  .category-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
  }

  .category-icon {
    font-size: 2rem;
    line-height: 1;
  }

  .category-title {
    font-family: var(--font-display);
    font-size: 1.2rem;
    font-weight: 700;
    margin: 0;
  }

  .category-items {
    font-family: var(--font-mono);
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.6;
    margin: 0;
  }

  .registries-footer {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-md);
    margin-top: var(--spacing-md);
    padding-top: var(--spacing-xl);
    border-top: 1px solid rgba(96, 165, 250, 0.1);
  }

  .registries-label {
    font-family: var(--font-mono);
    font-size: 0.8rem;
    color: var(--color-electric);
    opacity: 0.7;
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }

  .registries-list {
    display: flex;
    gap: var(--spacing-md);
    flex-wrap: wrap;
    justify-content: center;
  }

  .registry-badge {
    font-family: var(--font-mono);
    font-size: 0.9rem;
    font-weight: 600;
    color: var(--color-neutral-light);
    background: rgba(59, 130, 246, 0.1);
    border: 1px solid rgba(59, 130, 246, 0.3);
    padding: 0.5rem 1.2rem;
    border-radius: 999px;
    transition: all 0.2s ease;
  }

  .registry-badge:hover {
    background: rgba(59, 130, 246, 0.2);
    border-color: rgba(59, 130, 246, 0.5);
    transform: translateY(-2px);
  }

  @media (max-width: 1024px) {
    .categories-grid { grid-template-columns: repeat(2, 1fr); }
  }

  @media (max-width: 768px) {
    .categories-grid { grid-template-columns: 1fr; }
    .title { font-size: clamp(1.6rem, 5vw, 2.5rem); }
  }
</style>
