<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <div class="eyebrow">
        <span class="eyebrow-dot"></span>
        <span>El Problema</span>
      </div>
      <h2 class="title">
        N×M: La Pesadilla<br />
        de las Integraciones
      </h2>
    </div>

    <div class="comparison-layout">
      <!-- Left Panel: Without MCP -->
      <div class="panel card-glass panel-red">
        <div class="panel-header">
          <span class="panel-icon">❌</span>
          <h3>Sin MCP</h3>
        </div>
        <div class="panel-body">
          <div class="diagram-chaos">
            <div class="column apps">
              <div class="node app">Claude</div>
              <div class="node app">Cursor</div>
              <div class="node app">VS Code</div>
            </div>
            <div class="column connections chaos">
              <!-- SVG for chaotic arrows -->
              <svg width="100%" height="100%" viewBox="0 0 100 200" preserveAspectRatio="none">
                <path d="M 0 30 C 50 30, 50 30, 100 30" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 30 C 50 30, 50 80, 100 80" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 30 C 50 30, 50 130, 100 130" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 30 C 50 30, 50 180, 100 180" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                
                <path d="M 0 100 C 50 100, 50 30, 100 30" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 100 C 50 100, 50 80, 100 80" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 100 C 50 100, 50 130, 100 130" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 100 C 50 100, 50 180, 100 180" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                
                <path d="M 0 170 C 50 170, 50 30, 100 30" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 170 C 50 170, 50 80, 100 80" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 170 C 50 170, 50 130, 100 130" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
                <path d="M 0 170 C 50 170, 50 180, 100 180" stroke="rgba(239, 68, 68, 0.4)" stroke-width="2" fill="none" />
              </svg>
            </div>
            <div class="column tools">
              <div class="node tool">GitHub</div>
              <div class="node tool">Slack</div>
              <div class="node tool">DB</div>
              <div class="node tool">Files</div>
            </div>
          </div>
          <p class="panel-desc">Cada app necesita integraciones separadas para cada herramienta. N × M conexiones.</p>
        </div>
      </div>

      <!-- Right Panel: With MCP -->
      <div class="panel card-glass panel-green">
        <div class="panel-header">
          <span class="panel-icon">✅</span>
          <h3>Con MCP</h3>
        </div>
        <div class="panel-body">
          <div class="diagram-clean">
            <div class="column apps">
              <div class="node app">Claude</div>
              <div class="node app">Cursor</div>
              <div class="node app">VS Code</div>
            </div>
            <div class="column connections clean">
              <svg width="100%" height="100%" viewBox="0 0 100 200" preserveAspectRatio="none">
                <path d="M 0 30 C 30 30, 30 100, 50 100" stroke="rgba(16, 185, 129, 0.6)" stroke-width="2" fill="none" />
                <path d="M 0 100 C 30 100, 30 100, 50 100" stroke="rgba(16, 185, 129, 0.6)" stroke-width="2" fill="none" />
                <path d="M 0 170 C 30 170, 30 100, 50 100" stroke="rgba(16, 185, 129, 0.6)" stroke-width="2" fill="none" />
                
                <path d="M 50 100 C 70 100, 70 30, 100 30" stroke="rgba(16, 185, 129, 0.6)" stroke-width="2" fill="none" />
                <path d="M 50 100 C 70 100, 70 80, 100 80" stroke="rgba(16, 185, 129, 0.6)" stroke-width="2" fill="none" />
                <path d="M 50 100 C 70 100, 70 130, 100 130" stroke="rgba(16, 185, 129, 0.6)" stroke-width="2" fill="none" />
                <path d="M 50 100 C 70 100, 70 180, 100 180" stroke="rgba(16, 185, 129, 0.6)" stroke-width="2" fill="none" />
              </svg>
              <div class="mcp-hub">MCP</div>
            </div>
            <div class="column tools">
              <div class="node tool">GitHub</div>
              <div class="node tool">Slack</div>
              <div class="node tool">DB</div>
              <div class="node tool">Files</div>
            </div>
          </div>
          <p class="panel-desc">Un protocolo estándar. Escribe el servidor una vez, úsalo en cualquier cliente. N + M conexiones.</p>
        </div>
      </div>
    </div>

    <div class="footer-pill">
      <span class="pill-icon">💡</span>
      <span class="pill-text">MCP es el USB-C de la IA — un conector universal</span>
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
      radial-gradient(ellipse at 20% 20%, rgba(239, 68, 68, 0.08) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 80%, rgba(16, 185, 129, 0.08) 0%, transparent 50%);
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
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: var(--spacing-md);
  }

  .eyebrow {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    font-family: var(--font-mono);
    font-size: 0.85rem;
    color: var(--color-electric);
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .eyebrow-dot {
    width: 8px;
    height: 8px;
    background: var(--color-accent-bright);
    border-radius: 50%;
    box-shadow: 0 0 8px rgba(59, 130, 246, 0.8);
  }

  .title {
    font-size: clamp(2.5rem, 5vw, 4rem);
    font-weight: 800;
    color: var(--color-neutral-light);
    margin-bottom: 0;
    line-height: 1.1;
  }

  .comparison-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--spacing-xl);
    width: 100%;
  }

  .panel {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
    padding: var(--spacing-xl);
  }

  .panel-red {
    background: rgba(239, 68, 68, 0.05);
    border-color: rgba(239, 68, 68, 0.2);
  }

  .panel-green {
    background: rgba(16, 185, 129, 0.05);
    border-color: rgba(16, 185, 129, 0.2);
  }

  .panel-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
  }

  .panel-icon {
    font-size: 1.5rem;
  }

  .panel-header h3 {
    font-size: 1.5rem;
    margin: 0;
    color: var(--color-neutral-light);
  }

  .panel-body {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
    flex: 1;
  }

  .diagram-chaos, .diagram-clean {
    display: flex;
    justify-content: space-between;
    align-items: stretch;
    height: 240px;
    position: relative;
  }

  .column {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    z-index: 2;
  }

  .apps {
    justify-content: space-around;
  }

  .tools {
    justify-content: space-between;
  }

  .node {
    padding: var(--spacing-sm) var(--spacing-md);
    border-radius: var(--radius-sm);
    font-family: var(--font-mono);
    font-size: 0.85rem;
    font-weight: 600;
    text-align: center;
    min-width: 90px;
    backdrop-filter: blur(4px);
  }

  .app {
    background: rgba(59, 130, 246, 0.15);
    border: 1px solid rgba(96, 165, 250, 0.3);
    color: var(--color-electric);
  }

  .tool {
    background: rgba(167, 139, 250, 0.15);
    border: 1px solid rgba(167, 139, 250, 0.3);
    color: #c4b5fd;
  }

  .connections {
    position: absolute;
    inset: 0 90px;
    z-index: 1;
  }

  .mcp-hub {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: linear-gradient(135deg, #10b981, #059669);
    color: white;
    padding: var(--spacing-sm) var(--spacing-md);
    border-radius: var(--radius-md);
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 1.2rem;
    box-shadow: 0 0 20px rgba(16, 185, 129, 0.4);
    z-index: 3;
  }

  .panel-desc {
    font-size: 0.95rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    text-align: center;
    margin: 0;
    margin-top: auto;
  }

  .footer-pill {
    align-self: center;
    display: inline-flex;
    align-items: center;
    gap: var(--spacing-sm);
    background: rgba(59, 130, 246, 0.1);
    border: 1px solid rgba(96, 165, 250, 0.3);
    padding: var(--spacing-sm) var(--spacing-xl);
    border-radius: 999px;
    margin-top: var(--spacing-md);
  }

  .pill-icon {
    font-size: 1.2rem;
  }

  .pill-text {
    font-family: var(--font-body);
    font-weight: 500;
    color: var(--color-electric);
    font-size: 1.05rem;
  }

  @media (max-width: 900px) {
    .comparison-layout {
      grid-template-columns: 1fr;
      gap: var(--spacing-lg);
    }
    
    .diagram-chaos, .diagram-clean {
      height: 180px;
    }
  }

  @media (max-width: 768px) {
    .slide-content {
      padding: var(--spacing-lg) var(--spacing-md);
    }
    
    .title {
      font-size: clamp(2rem, 6vw, 2.8rem);
    }
    
    .panel {
      padding: var(--spacing-lg);
    }
    
    .footer-pill {
      padding: var(--spacing-sm) var(--spacing-lg);
    }
    
    .pill-text {
      font-size: 0.9rem;
    }
  }

  @media (max-width: 480px) {
    .slide-content {
      padding: var(--spacing-md) var(--spacing-sm);
      gap: var(--spacing-md);
    }
    
    .title {
      font-size: clamp(1.6rem, 6vw, 2rem);
    }
    
    .panel {
      padding: var(--spacing-md);
      gap: var(--spacing-md);
    }
    
    .panel-header h3 {
      font-size: 1.2rem;
    }
    
    .diagram-chaos, .diagram-clean {
      height: 150px;
    }
    
    .node {
      padding: 4px 8px;
      font-size: 0.7rem;
      min-width: 60px;
    }
    
    .connections {
      inset: 0 60px;
    }
    
    .mcp-hub {
      padding: 4px 8px;
      font-size: 0.9rem;
    }
    
    .panel-desc {
      font-size: 0.8rem;
    }
    
    .footer-pill {
      padding: 6px 12px;
    }
    
    .pill-text {
      font-size: 0.8rem;
    }
  }
</style>