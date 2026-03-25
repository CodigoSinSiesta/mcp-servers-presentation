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
        <span>Model Context Protocol</span>
      </div>
      <h2 class="title">¿Qué es MCP?</h2>
    </div>

    <div class="main-layout">
      <!-- Left column: Protocol diagram -->
      <div class="protocol-diagram card-glass">
        <h3 class="diagram-title">El Protocolo</h3>
        <div class="flow-steps">
          <div class="step">
            <div class="step-icon">💻</div>
            <div class="step-body">
              <span class="step-name">Host App</span>
              <span class="step-desc">Claude, Cursor, VS Code...</span>
            </div>
          </div>
          <div class="step-arrow">↓</div>
          <div class="step">
            <div class="step-icon">🔌</div>
            <div class="step-body">
              <span class="step-name">MCP Client</span>
              <span class="step-desc">Integrado en la app</span>
            </div>
          </div>
          <div class="step-arrow transport">
            <span class="transport-label">JSON-RPC 2.0 (stdio / HTTP)</span>
            <span class="transport-arrows">↕</span>
          </div>
          <div class="step">
            <div class="step-icon">⚙️</div>
            <div class="step-body">
              <span class="step-name">MCP Server</span>
              <span class="step-desc">Tu código (TypeScript/Python)</span>
            </div>
          </div>
          <div class="step-arrow">↓</div>
          <div class="step">
            <div class="step-icon">🗄️</div>
            <div class="step-body">
              <span class="step-name">Local Resources</span>
              <span class="step-desc">Archivos, APIs, Bases de datos</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Right column: key concepts -->
      <div class="concepts">
        <div class="concept-card card-glass">
          <div class="concept-icon">📖</div>
          <div class="concept-body">
            <h4>Protocolo abierto</h4>
            <p>Creado por Anthropic en 2024. Hoy lo usan Claude, Cursor, Windsurf, VS Code y más.</p>
          </div>
        </div>

        <div class="concept-card card-glass">
          <div class="concept-icon">⚡</div>
          <div class="concept-body">
            <h4>JSON-RPC 2.0</h4>
            <p>Transporte estándar. <strong>stdio</strong> para local, <strong>HTTP/SSE</strong> para remoto. Ligero y universal.</p>
          </div>
        </div>

        <div class="concept-card card-glass">
          <div class="concept-icon">🔄</div>
          <div class="concept-body">
            <h4>Client ↔ Server</h4>
            <p>El server expone <strong>capabilities</strong>. El client las descubre y usa. Bidireccional.</p>
          </div>
        </div>
      </div>
    </div>

    <div class="footer-clients">
      <span class="client-badge">Claude</span>
      <span class="client-badge">Cursor</span>
      <span class="client-badge">Windsurf</span>
      <span class="client-badge">VS Code</span>
      <span class="client-badge">Continue</span>
      <span class="client-badge">Zed</span>
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
      radial-gradient(ellipse at 70% 30%, rgba(59, 130, 246, 0.08) 0%, transparent 55%),
      radial-gradient(ellipse at 20% 70%, rgba(30, 58, 138, 0.1) 0%, transparent 55%);
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

  /* Main layout */
  .main-layout {
    display: grid;
    grid-template-columns: 1fr 1.4fr;
    gap: var(--spacing-xl);
    align-items: start;
  }

  /* Protocol diagram */
  .protocol-diagram {
    padding: var(--spacing-xl);
  }

  .diagram-title {
    font-family: var(--font-mono);
    font-size: 0.85rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-electric);
    margin-bottom: var(--spacing-lg);
  }

  .flow-steps {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  .step {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    background: rgba(59, 130, 246, 0.06);
    border: 1px solid rgba(96, 165, 250, 0.12);
    border-radius: var(--radius-sm);
    padding: var(--spacing-md) var(--spacing-lg);
  }

  .step-icon {
    width: 32px;
    height: 32px;
    background: rgba(30, 58, 138, 0.4);
    border: 1px solid rgba(96, 165, 250, 0.25);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }

  .step-body {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .step-name {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 1rem;
    color: var(--color-neutral-light);
  }

  .step-desc {
    font-size: 0.8rem;
    color: var(--color-neutral-light);
    opacity: 0.6;
    font-family: var(--font-body);
  }

  .step-arrow {
    text-align: center;
    color: var(--color-electric);
    opacity: 0.5;
    font-size: 1.2rem;
    line-height: 1;
  }

  .transport {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    opacity: 0.8;
    padding: var(--spacing-xs) 0;
  }

  .transport-label {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    color: var(--color-accent-bright);
    background: rgba(59, 130, 246, 0.1);
    padding: 2px 8px;
    border-radius: 4px;
    border: 1px solid rgba(59, 130, 246, 0.2);
  }

  .transport-arrows {
    font-size: 1.4rem;
    color: var(--color-accent-bright);
  }

  /* Concepts */
  .concepts {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
  }

  .concept-card {
    display: flex;
    gap: var(--spacing-lg);
    padding: var(--spacing-lg) var(--spacing-xl);
    align-items: flex-start;
  }

  .concept-icon {
    font-size: 2rem;
    line-height: 1;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .concept-body h4 {
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--color-neutral-light);
    margin-bottom: var(--spacing-xs);
  }

  .concept-body p {
    font-size: 0.88rem;
    color: var(--color-neutral-light);
    opacity: 0.75;
    line-height: 1.6;
    margin-bottom: 0;
  }

  .concept-body strong {
    color: var(--color-electric);
    opacity: 1;
    font-weight: 700;
  }

  /* Footer clients */
  .footer-clients {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: var(--spacing-md);
    margin-top: var(--spacing-md);
  }

  .client-badge {
    font-family: var(--font-mono);
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.6;
    padding: var(--spacing-xs) var(--spacing-md);
    border: 1px solid rgba(250, 249, 246, 0.1);
    border-radius: var(--radius-sm);
    background: rgba(250, 249, 246, 0.03);
  }

  /* Mobile: Tablet */
  @media (max-width: 900px) {
    .main-layout { grid-template-columns: 1fr; }
  }

  /* Mobile: Small tablet / large phone */
  @media (max-width: 768px) {
    .slide-content {
      padding: var(--spacing-lg) var(--spacing-md);
      gap: var(--spacing-lg);
    }

    .title {
      font-size: clamp(2rem, 6vw, 2.8rem);
    }

    .main-layout {
      gap: var(--spacing-lg);
    }

    .protocol-diagram {
      padding: var(--spacing-lg);
    }

    .diagram-title {
      font-size: 0.8rem;
      margin-bottom: var(--spacing-md);
    }

    .step {
      padding: var(--spacing-md);
      gap: var(--spacing-sm);
      min-height: 44px;
    }

    .step-icon {
      width: 28px;
      height: 28px;
      font-size: 0.9rem;
    }

    .step-name {
      font-size: 0.95rem;
    }

    .step-desc {
      font-size: 0.75rem;
    }

    .step-arrow {
      font-size: 1rem;
    }

    .transport-label {
      font-size: 0.65rem;
    }

    .concepts {
      gap: var(--spacing-sm);
    }

    .concept-card {
      padding: var(--spacing-md) var(--spacing-lg);
      gap: var(--spacing-md);
      min-height: 44px;
    }

    .concept-icon {
      font-size: 1.6rem;
    }

    .concept-body h4 {
      font-size: 1rem;
    }

    .concept-body p {
      font-size: 0.82rem;
    }

    .footer-clients {
      gap: var(--spacing-sm);
    }

    .client-badge {
      font-size: 0.75rem;
      padding: 4px 12px;
    }
  }

  /* Mobile: Phone */
  @media (max-width: 480px) {
    .slide-content {
      padding: var(--spacing-md) var(--spacing-sm);
      gap: var(--spacing-md);
    }

    .slide-header {
      margin-bottom: var(--spacing-sm);
    }

    .title {
      font-size: clamp(1.6rem, 6vw, 2rem);
    }

    .protocol-diagram {
      padding: var(--spacing-md);
    }

    .diagram-title {
      font-size: 0.75rem;
      margin-bottom: var(--spacing-sm);
    }

    .flow-steps {
      gap: 2px;
    }

    .step {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-sm);
      min-height: 48px;
    }

    .step-icon {
      width: 24px;
      height: 24px;
      font-size: 0.8rem;
    }

    .step-name {
      font-size: 0.9rem;
    }

    .step-desc {
      font-size: 0.7rem;
    }

    .step-arrow {
      font-size: 0.9rem;
    }

    .transport-label {
      font-size: 0.6rem;
    }

    .concept-card {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-sm);
    }

    .concept-icon {
      font-size: 1.4rem;
    }

    .concept-body h4 {
      font-size: 0.9rem;
      margin-bottom: 2px;
    }

    .concept-body p {
      font-size: 0.75rem;
      line-height: 1.5;
    }

    .client-badge {
      font-size: 0.7rem;
      padding: 4px 8px;
    }
  }

  /* Mobile: Small phone */
  @media (max-width: 390px) {
    .slide-content {
      padding: var(--spacing-sm);
      gap: var(--spacing-sm);
    }

    .title {
      font-size: clamp(1.4rem, 6vw, 1.8rem);
    }

    .protocol-diagram {
      padding: var(--spacing-sm);
    }

    .diagram-title {
      font-size: 0.7rem;
    }

    .step {
      padding: var(--spacing-sm);
      min-height: 44px;
    }

    .step-icon {
      width: 22px;
      height: 22px;
      font-size: 0.75rem;
    }

    .step-name {
      font-size: 0.85rem;
    }

    .step-desc {
      font-size: 0.65rem;
    }

    .step-arrow {
      font-size: 0.8rem;
    }

    .concept-card {
      padding: var(--spacing-sm);
    }

    .concept-icon {
      font-size: 1.2rem;
    }

    .concept-body h4 {
      font-size: 0.85rem;
    }

    .concept-body p {
      font-size: 0.7rem;
    }
  }

  /* Short desktop screens: compress vertical spacing so content fits without scroll */
  @media (max-height: 900px) and (min-width: 769px) {
    .slide-content {
      padding: 12px var(--spacing-content);
      gap: var(--spacing-md);
    }

    .slide-header {
      margin-bottom: var(--spacing-sm);
    }

    .title {
      font-size: clamp(2rem, 4vw, 2.8rem);
    }

    .main-layout {
      gap: var(--spacing-md);
    }

    .protocol-diagram {
      padding: var(--spacing-md);
    }

    .diagram-title {
      margin-bottom: var(--spacing-sm);
    }

    .flow-steps {
      gap: var(--spacing-xs);
    }

    .step {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-sm);
    }

    .step-icon {
      width: 28px;
      height: 28px;
    }

    .step-arrow {
      font-size: 1rem;
    }

    .concepts {
      gap: var(--spacing-sm);
    }

    .concept-card {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-md);
    }

    .concept-icon {
      font-size: 1.6rem;
    }

    .concept-body h4 {
      font-size: 1rem;
    }

    .concept-body p {
      font-size: 0.82rem;
    }

    .footer-clients {
      margin-top: var(--spacing-sm);
    }
  }
</style>