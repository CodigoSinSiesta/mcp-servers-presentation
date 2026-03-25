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
      <span class="label">Manos al Código</span>
      <h2 class="title">Anatomía de un MCP Server</h2>
    </div>

    <div class="main-layout">
      <div class="code-container card-glass">
        <pre class="code-block"><code><span class="kw">import</span> &#123; <span class="type">Server</span> &#125; <span class="kw">from</span> <span class="str">"@modelcontextprotocol/sdk/server/index.js"</span>;
<span class="kw">import</span> &#123; <span class="type">StdioServerTransport</span> &#125; <span class="kw">from</span> <span class="str">"@modelcontextprotocol/sdk/server/stdio.js"</span>;
<span class="kw">import</span> &#123; <span class="type">ListToolsRequestSchema</span>, <span class="type">CallToolRequestSchema</span> &#125; <span class="kw">from</span> <span class="str">"@modelcontextprotocol/sdk/types.js"</span>;

<span class="kw">const</span> server = <span class="kw">new</span> <span class="type">Server</span>(
  &#123; name: <span class="str">"MiServidor"</span>, version: <span class="str">"1.0.0"</span> &#125;,
  &#123; capabilities: &#123; tools: &#123;&#125; &#125; &#125;
);

server.<span class="fn">setRequestHandler</span>(<span class="type">ListToolsRequestSchema</span>, <span class="kw">async</span> () =&gt; (&#123;
  tools: [&#123; name: <span class="str">"mi_tool"</span>, description: <span class="str">"..."</span>, inputSchema: &#123; ... &#125; &#125;]
&#125;));

server.<span class="fn">setRequestHandler</span>(<span class="type">CallToolRequestSchema</span>, <span class="kw">async</span> (req) =&gt; &#123;
  <span class="kw">return</span> &#123; content: [&#123; type: <span class="str">"text"</span>, text: <span class="str">"resultado"</span> &#125;] &#125;;
&#125;);

<span class="kw">const</span> transport = <span class="kw">new</span> <span class="type">StdioServerTransport</span>();
<span class="kw">await</span> server.<span class="fn">connect</span>(transport);</code></pre>
      </div>

      <div class="annotations">
        <div class="annotation" style="top: 5%;">
          <div class="arrow">←</div>
          <div class="annotation-text">📦 Imports</div>
        </div>
        <div class="annotation" style="top: 25%;">
          <div class="arrow">←</div>
          <div class="annotation-text">🔧 Crear servidor</div>
        </div>
        <div class="annotation" style="top: 50%;">
          <div class="arrow">←</div>
          <div class="annotation-text">📋 Registrar tools</div>
        </div>
        <div class="annotation" style="top: 85%;">
          <div class="arrow">←</div>
          <div class="annotation-text">🚀 Conectar</div>
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
    margin-bottom: 0;
    line-height: 1.15;
  }

  .main-layout {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: var(--spacing-xl);
    align-items: stretch;
    position: relative;
  }

  .code-container {
    padding: var(--spacing-xl);
    background: rgba(10, 22, 40, 0.8);
    border: 1px solid rgba(96, 165, 250, 0.2);
    border-radius: var(--radius-lg);
    overflow-x: auto;
  }

  .code-block {
    font-family: var(--font-mono);
    font-size: 0.9rem;
    line-height: 1.6;
    color: var(--color-neutral-light);
    margin: 0;
    white-space: pre;
  }

  .kw { color: #60A5FA; }
  .str { color: #86efac; }
  .fn { color: #fde68a; }
  .type { color: #67e8f9; }
  .comment { color: #6b7280; font-style: italic; }

  .annotations {
    position: relative;
    display: flex;
    flex-direction: column;
  }

  .annotation {
    position: absolute;
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    transform: translateY(-50%);
    width: 100%;
  }

  .arrow {
    color: var(--color-electric);
    font-size: 1.5rem;
    font-weight: bold;
  }

  .annotation-text {
    font-family: var(--font-display);
    font-size: 1.2rem;
    font-weight: 600;
    color: var(--color-neutral-light);
    background: rgba(30, 58, 138, 0.3);
    padding: var(--spacing-sm) var(--spacing-md);
    border-radius: var(--radius-sm);
    border-left: 3px solid var(--color-accent-bright);
    white-space: nowrap;
  }

  @media (max-width: 900px) {
    .main-layout {
      grid-template-columns: 1fr;
      gap: var(--spacing-lg);
    }

    .annotations {
      display: none;
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

    .code-block {
      font-size: 0.75rem;
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

    .code-container {
      padding: var(--spacing-md);
    }

    .code-block {
      font-size: 0.65rem;
    }
  }
</style>