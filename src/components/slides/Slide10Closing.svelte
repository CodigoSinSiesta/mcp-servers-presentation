<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  
  let slideElement: HTMLElement;
  
  onMount(() => {
    animateSlideEntrance(slideElement);
  });

  const summaryPills = [
    '✓ Qué es MCP',
    '✓ Cómo funciona',
    '✓ FastMCP vs SDK'
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background">
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>
    <div class="orb orb-3"></div>
  </div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">¡Vamos al Taller!</span>
      <h2 class="title gradient-text">Construyamos<br />un MCP Server</h2>
    </div>

    <div class="summary-pills">
      {#each summaryPills as pill}
        <span class="pill">{pill}</span>
      {/each}
    </div>

    <div class="cta-box card-glass">
      <div class="cta-header">
        <span class="cta-icon">🏗️</span>
        <div class="cta-titles">
          <h3 class="cta-title">Hora del Taller</h3>
          <p class="cta-subtitle">Bookmark Manager MCP</p>
        </div>
      </div>

      <div class="exercises">
        <div class="exercise-row">
          <span class="exercise-number">1</span>
          <span class="exercise-text">Ejercicio 1: TypeScript + SDK Oficial (~25 min)</span>
        </div>
        <div class="exercise-row">
          <span class="exercise-number">2</span>
          <span class="exercise-text">Ejercicio 2: Python + FastMCP (~20 min)</span>
        </div>
      </div>

      <div class="repo-badge">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M15 22v-4a4.8 4.8 0 0 0-1-3.5c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.403 5.403 0 0 0 4 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65-.17.6-.22 1.23-.15 1.85v4"/><path d="M9 18c-4.51 2-5-2-7-2"/></svg>
        <span>github.com/codigosinsiesta/taller-ia-agentes-mcp</span>
      </div>
    </div>

    <div class="bottom-row">
      <span class="author">@codigosinsiesta</span>
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
      radial-gradient(circle at 50% 50%, rgba(10, 22, 40, 1) 0%, rgba(5, 11, 20, 1) 100%);
    z-index: 1;
    overflow: hidden;
  }

  .orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.4;
    animation: float 20s infinite ease-in-out alternate;
  }

  .orb-1 {
    width: 400px;
    height: 400px;
    background: rgba(59, 130, 246, 0.6);
    top: -100px;
    left: -100px;
    animation-delay: 0s;
  }

  .orb-2 {
    width: 500px;
    height: 500px;
    background: rgba(139, 92, 246, 0.5);
    bottom: -150px;
    right: -100px;
    animation-delay: -5s;
  }

  .orb-3 {
    width: 300px;
    height: 300px;
    background: rgba(16, 185, 129, 0.4);
    top: 40%;
    left: 60%;
    animation-delay: -10s;
  }

  @keyframes float {
    0% { transform: translate(0, 0) scale(1); }
    50% { transform: translate(50px, 30px) scale(1.1); }
    100% { transform: translate(-30px, 50px) scale(0.9); }
  }

  .slide-content {
    position: relative;
    z-index: 2;
    max-width: 900px;
    width: 100%;
    padding: var(--spacing-2xl) var(--spacing-content);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-xl);
    text-align: center;
  }

  .slide-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-sm);
  }

  .label {
    display: inline-block;
    font-family: var(--font-mono);
    font-size: 0.9rem;
    text-transform: uppercase;
    letter-spacing: 0.2em;
    color: var(--color-electric);
    background: rgba(59, 130, 246, 0.15);
    padding: 0.4rem 1.2rem;
    border-radius: 999px;
    border: 1px solid rgba(59, 130, 246, 0.3);
  }

  .title {
    font-size: clamp(3rem, 6vw, 4.5rem);
    font-weight: 900;
    line-height: 1.1;
    margin: 0;
    letter-spacing: -0.02em;
  }

  .gradient-text {
    background: linear-gradient(135deg, #fff 0%, #60A5FA 50%, #8B5CF6 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .summary-pills {
    display: flex;
    gap: var(--spacing-md);
    flex-wrap: wrap;
    justify-content: center;
  }

  .pill {
    font-family: var(--font-mono);
    font-size: 0.95rem;
    font-weight: 600;
    color: var(--color-neutral-light);
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    padding: 0.6rem 1.5rem;
    border-radius: 999px;
    backdrop-filter: blur(10px);
  }

  .cta-box {
    width: 100%;
    padding: var(--spacing-2xl);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-xl);
    background: rgba(10, 22, 40, 0.6);
    border: 1px solid rgba(59, 130, 246, 0.3);
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5), inset 0 1px 1px rgba(255, 255, 255, 0.1);
    transform: scale(1.02);
  }

  .cta-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-md);
  }

  .cta-icon {
    font-size: 4rem;
    line-height: 1;
    filter: drop-shadow(0 10px 20px rgba(0, 0, 0, 0.3));
  }

  .cta-titles {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-xs);
  }

  .cta-title {
    font-family: var(--font-display);
    font-size: 2.2rem;
    font-weight: 800;
    color: var(--color-neutral-light);
    margin: 0;
  }

  .cta-subtitle {
    font-size: 1.2rem;
    color: var(--color-electric);
    opacity: 0.9;
    margin: 0;
    font-weight: 500;
  }

  .exercises {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
    width: 100%;
    max-width: 600px;
  }

  .exercise-row {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    background: rgba(255, 255, 255, 0.03);
    border: 1px solid rgba(255, 255, 255, 0.08);
    padding: 1rem 1.5rem;
    border-radius: var(--radius-md);
    transition: all 0.2s ease;
  }

  .exercise-row:hover {
    background: rgba(255, 255, 255, 0.06);
    border-color: rgba(59, 130, 246, 0.3);
    transform: translateX(5px);
  }

  .exercise-number {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 32px;
    height: 32px;
    background: var(--color-accent-bright);
    color: #fff;
    font-family: var(--font-mono);
    font-weight: 800;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .exercise-text {
    font-size: 1.1rem;
    color: var(--color-neutral-light);
    font-weight: 500;
  }

  .repo-badge {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    background: rgba(0, 0, 0, 0.4);
    border: 1px solid rgba(255, 255, 255, 0.15);
    padding: 0.8rem 1.5rem;
    border-radius: 999px;
    font-family: var(--font-mono);
    font-size: 1rem;
    color: var(--color-neutral-light);
    margin-top: var(--spacing-sm);
    transition: all 0.2s ease;
  }

  .repo-badge:hover {
    background: rgba(0, 0, 0, 0.6);
    border-color: var(--color-electric);
    color: var(--color-electric);
  }

  .bottom-row {
    margin-top: var(--spacing-lg);
  }

  .author {
    font-family: var(--font-mono);
    font-size: 1.1rem;
    font-weight: 600;
    color: var(--color-electric);
    opacity: 0.8;
    letter-spacing: 0.05em;
  }

  @media (max-height: 900px) and (min-width: 769px) {
    .slide-content {
      padding: 10px var(--spacing-content);
      gap: var(--spacing-md);
    }
    .title {
      font-size: clamp(2rem, 4vw, 3rem);
    }
    .label {
      font-size: 0.78rem;
      padding: 0.3rem 0.9rem;
    }
    .summary-pills { gap: var(--spacing-sm); }
    .pill {
      font-size: 0.82rem;
      padding: 0.4rem 1rem;
    }
    .cta-box {
      padding: var(--spacing-lg) var(--spacing-xl);
      gap: var(--spacing-md);
    }
    .cta-icon { font-size: 2.2rem; }
    .cta-title { font-size: 1.6rem; }
    .cta-subtitle { font-size: 0.95rem; }
    .exercises { gap: var(--spacing-sm); }
    .exercise-row { padding: 0.6rem 1.2rem; }
    .exercise-number { width: 26px; height: 26px; }
    .exercise-text { font-size: 0.9rem; }
    .repo-badge {
      font-size: 0.82rem;
      padding: 0.5rem 1rem;
      margin-top: 0;
    }
    .repo-badge svg { width: 16px; height: 16px; }
    .bottom-row { margin-top: var(--spacing-xs); }
    .author { font-size: 0.9rem; }
  }

  @media (max-width: 768px) {
    .title { font-size: clamp(2.2rem, 8vw, 3rem); }
    .cta-box { padding: var(--spacing-xl) var(--spacing-lg); }
    .cta-title { font-size: 1.8rem; }
    .exercise-text { font-size: 0.95rem; }
    .repo-badge { font-size: 0.85rem; padding: 0.6rem 1rem; }
    .repo-badge svg { width: 18px; height: 18px; }
  }
</style>
