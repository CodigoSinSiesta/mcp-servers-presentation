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
      <span class="label">¿Y si fuera más fácil?</span>
      <h2 class="title">FastMCP: De <span class="count-highlight">~100</span> Líneas a <span class="count-highlight">6</span></h2>
    </div>

    <div class="main-layout">
      <div class="badge-center">6× menos código</div>
      
      <div class="code-panel card-glass">
        <h3 class="panel-title">SDK Oficial (TypeScript)</h3>
        <pre class="code-block"><code><span class="comment">// ~14 líneas de boilerplate...</span>
<span class="kw">import</span> &#123; <span class="type">Server</span> &#125; <span class="kw">from</span> <span class="str">"@modelcontextprotocol/sdk/..."</span>;
<span class="kw">import</span> &#123; <span class="type">StdioServerTransport</span> &#125; <span class="kw">from</span> <span class="str">"..."</span>;
<span class="kw">import</span> &#123; <span class="type">ListToolsRequestSchema</span>, <span class="type">CallToolRequestSchema</span> &#125; <span class="kw">from</span> <span class="str">"..."</span>;

<span class="kw">const</span> server = <span class="kw">new</span> <span class="type">Server</span>(&#123; name: <span class="str">"math"</span> &#125;, &#123; capabilities: &#123; tools: &#123;&#125; &#125; &#125;);

server.<span class="fn">setRequestHandler</span>(<span class="type">ListToolsRequestSchema</span>, <span class="kw">async</span> () =&gt; (&#123;
  tools: [&#123; name: <span class="str">"sumar"</span>, description: <span class="str">"Suma dos números"</span>,
    inputSchema: &#123; type: <span class="str">"object"</span>, properties: &#123; a: &#123; type: <span class="str">"number"</span> &#125;, b: &#123; type: <span class="str">"number"</span> &#125; &#125;, required: [<span class="str">"a"</span>,<span class="str">"b"</span>] &#125;
  &#125;]
&#125;));

server.<span class="fn">setRequestHandler</span>(<span class="type">CallToolRequestSchema</span>, <span class="kw">async</span> (req) =&gt; &#123;
  <span class="kw">const</span> &#123; a, b &#125; = req.params.arguments <span class="kw">as</span> &#123; a: <span class="type">number</span>; b: <span class="type">number</span> &#125;;
  <span class="kw">return</span> &#123; content: [&#123; type: <span class="str">"text"</span>, text: <span class="type">String</span>(a + b) &#125;] &#125;;
&#125;);
<span class="kw">const</span> transport = <span class="kw">new</span> <span class="type">StdioServerTransport</span>();
<span class="kw">await</span> server.<span class="fn">connect</span>(transport);</code></pre>
      </div>

      <div class="code-panel card-glass panel-highlight">
        <h3 class="panel-title">FastMCP (Python)</h3>
        <pre class="code-block"><code><span class="kw">from</span> fastmcp <span class="kw">import</span> <span class="type">FastMCP</span>

mcp = <span class="type">FastMCP</span>(<span class="str">"math"</span>)

<span class="type">@mcp.tool</span>
<span class="kw">def</span> <span class="fn">sumar</span>(a: <span class="type">int</span>, b: <span class="type">int</span>) -&gt; <span class="type">int</span>:
    <span class="str">"""Suma dos números"""</span>
    <span class="kw">return</span> a + b

<span class="kw">if</span> __name__ == <span class="str">"__main__"</span>:
    mcp.<span class="fn">run</span>()</code></pre>
      </div>
    </div>

    <div class="eliminated-features">
      <div class="feature-item">
        <span class="strikethrough">list_tools handler manual</span>
        <span class="arrow">→</span>
        <span class="replacement">Auto-generated</span>
      </div>
      <div class="feature-item">
        <span class="strikethrough">JSON Schema manual</span>
        <span class="arrow">→</span>
        <span class="replacement">Type hints automáticos</span>
      </div>
      <div class="feature-item">
        <span class="strikethrough">call_tool dispatcher</span>
        <span class="arrow">→</span>
        <span class="replacement">Eliminado</span>
      </div>
      <div class="feature-item">
        <span class="strikethrough">TextContent wrapping</span>
        <span class="arrow">→</span>
        <span class="replacement">Return Python puro</span>
      </div>
    </div>

    <div class="footer-note">
      <p>Type hints = JSON Schema · Docstrings = Descripciones para el LLM · Return = Respuesta</p>
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

  .count-highlight {
    color: var(--color-accent-bright);
    text-shadow: 0 0 20px rgba(59, 130, 246, 0.5);
  }

  .main-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--spacing-xl);
    align-items: stretch;
    position: relative;
  }

  .badge-center {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    color: var(--color-base-dark);
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 1rem;
    padding: var(--spacing-sm) var(--spacing-lg);
    border-radius: var(--radius-xl);
    box-shadow: 0 0 30px rgba(59, 130, 246, 0.6);
    z-index: 10;
    white-space: nowrap;
  }

  .code-panel {
    padding: var(--spacing-xl);
    background: rgba(10, 22, 40, 0.8);
    border: 1px solid rgba(96, 165, 250, 0.2);
    border-radius: var(--radius-lg);
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
  }

  .panel-highlight {
    border-color: var(--color-accent-bright);
    box-shadow: inset 0 0 20px rgba(59, 130, 246, 0.1);
  }

  .panel-title {
    font-size: 1.2rem;
    font-weight: 700;
    color: var(--color-neutral-light);
    margin-bottom: 0;
    text-align: center;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    padding-bottom: var(--spacing-sm);
  }

  .code-block {
    font-family: var(--font-mono);
    font-size: 0.85rem;
    line-height: 1.6;
    color: var(--color-neutral-light);
    margin: 0;
    white-space: pre-wrap;
    overflow-x: auto;
    flex-grow: 1;
  }

  .kw { color: #60A5FA; }
  .str { color: #86efac; }
  .fn { color: #fde68a; }
  .type { color: #67e8f9; }
  .comment { color: #6b7280; font-style: italic; }

  .eliminated-features {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: var(--spacing-md);
    margin-top: var(--spacing-md);
  }

  .feature-item {
    background: rgba(30, 58, 138, 0.15);
    border: 1px solid rgba(96, 165, 250, 0.2);
    border-radius: var(--radius-sm);
    padding: var(--spacing-md);
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: var(--spacing-xs);
  }

  .strikethrough {
    text-decoration: line-through;
    color: #ef4444;
    font-family: var(--font-mono);
    font-size: 0.8rem;
    opacity: 0.8;
  }

  .arrow {
    color: var(--color-electric);
    font-size: 1.2rem;
    line-height: 1;
  }

  .replacement {
    color: #10b981;
    font-weight: 600;
    font-size: 0.9rem;
  }

  .footer-note {
    text-align: center;
    margin-top: var(--spacing-sm);
  }

  .footer-note p {
    display: inline-block;
    font-family: var(--font-mono);
    font-size: 0.85rem;
    color: var(--color-electric);
    background: rgba(59, 130, 246, 0.1);
    padding: var(--spacing-sm) var(--spacing-lg);
    border-radius: var(--radius-xl);
    border: 1px solid rgba(96, 165, 250, 0.2);
    margin-bottom: 0;
  }

  @media (max-height: 900px) and (min-width: 769px) {
    .slide-content {
      padding: 10px var(--spacing-content);
      gap: var(--spacing-sm);
    }
    .title {
      font-size: clamp(1.6rem, 3vw, 2.2rem);
    }
    .main-layout {
      gap: var(--spacing-md);
    }
    .code-panel {
      padding: var(--spacing-md);
      gap: var(--spacing-xs);
    }
    .panel-title {
      font-size: 0.95rem;
      padding-bottom: var(--spacing-xs);
    }
    .code-block {
      font-size: 0.70rem;
      line-height: 1.4;
    }
    .eliminated-features {
      gap: var(--spacing-sm);
      margin-top: var(--spacing-xs);
    }
    .feature-item {
      padding: var(--spacing-sm);
    }
    .strikethrough { font-size: 0.72rem; }
    .replacement { font-size: 0.78rem; }
    .footer-note { margin-top: 0; }
    .footer-note p {
      font-size: 0.75rem;
      padding: var(--spacing-xs) var(--spacing-md);
    }
  }

  @media (max-width: 1024px) {
    .eliminated-features {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (max-width: 900px) {
    .main-layout {
      grid-template-columns: 1fr;
      gap: var(--spacing-xl);
    }

    .badge-center {
      top: 50%;
      transform: translate(-50%, -50%);
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

    .badge-center {
      font-size: 0.85rem;
      padding: var(--spacing-xs) var(--spacing-md);
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

    .code-panel {
      padding: var(--spacing-md);
    }

    .code-block {
      font-size: 0.65rem;
    }

    .eliminated-features {
      grid-template-columns: 1fr;
      gap: var(--spacing-sm);
    }

    .feature-item {
      flex-direction: row;
      justify-content: space-between;
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .footer-note p {
      font-size: 0.7rem;
      padding: var(--spacing-xs) var(--spacing-md);
    }
  }
</style>