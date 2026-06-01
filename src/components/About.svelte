<script lang="ts">
  let stickers = $state([
    {
      text: "Svelte",
      icon: "svelte.svg",
      x: 0,
      y: 0,
      rotate: -4,
      color: "var(--theme-green)",
    },
    {
      text: "TypeScript",
      icon: "typescript.svg",
      x: 0,
      y: 0,
      rotate: 5,
      color: "var(--theme-pink)",
    },
    {
      text: "Vanilla CSS",
      icon: "css.svg",
      x: 0,
      y: 0,
      rotate: -3,
      color: "var(--theme-yellow)",
    },
    {
      text: "Rust APIs",
      icon: "rust.svg",
      x: 0,
      y: 0,
      rotate: 3,
      color: "var(--theme-blue)",
    },
  ]);

  let activeIndex = $state<number | null>(null);
  let dragStart = { x: 0, y: 0 };
  let stickerStart = { x: 0, y: 0 };

  function handlePointerDown(e: PointerEvent, index: number) {
    const target = e.currentTarget as HTMLElement;
    target.setPointerCapture(e.pointerId);

    activeIndex = index;
    dragStart = { x: e.clientX, y: e.clientY };
    stickerStart = { x: stickers[index].x, y: stickers[index].y };
  }

  function handlePointerMove(e: PointerEvent, index: number) {
    if (activeIndex !== index) return;
    const dx = e.clientX - dragStart.x;
    const dy = e.clientY - dragStart.y;
    stickers[index].x = stickerStart.x + dx;
    stickers[index].y = stickerStart.y + dy;
  }

  function handlePointerUp(e: PointerEvent, index: number) {
    if (activeIndex === index) {
      activeIndex = null;
    }
  }
</script>

<section class="hero" id="about">
  <div class="hero-container">
    <div class="hero-card">
      <div class="card-header">
        <span class="badge">eli_nelson.sh</span>
        <div class="header-dots">
          <span class="dot"></span>
          <span class="dot"></span>
          <span class="dot"></span>
        </div>
      </div>
      <div class="card-body">
        <span class="eyebrow">Hi, I'm Eli Nelson</span>
        <h1>Building the modern web</h1>
        <p class="subtitle">
          I am a developer focused on crafting highly accessible interfaces,
          expressive typography, and memorable interactive experiences.
        </p>
        <div class="actions">
          <a href="#projects" class="btn btn-primary">Browse Projects</a>
          <a href="#contact" class="btn btn-secondary">Say Hello</a>
        </div>
      </div>
    </div>

    <div class="sticker-board">
      <p class="sticker-instruction">Grab & drag my stack:</p>
      {#each stickers as sticker, i}
        <button
          type="button"
          class="sticker"
          class:dragging={activeIndex === i}
          style="
            background-color: {sticker.color};
            transform: translate({sticker.x}px, {sticker.y}px) rotate({sticker.rotate}deg);
            z-index: {activeIndex === i ? 10 : 1};
          "
          onpointerdown={(e) => handlePointerDown(e, i)}
          onpointermove={(e) => handlePointerMove(e, i)}
          onpointerup={(e) => handlePointerUp(e, i)}
        >
          <img
            src={`src/assets/icons/${sticker.icon}`}
            alt={sticker.text}
            class="sticker-icon"
          />
          {sticker.text}
        </button>
      {/each}
    </div>
  </div>
</section>

<style>
  .hero {
    min-height: 85vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 4rem 2rem;
  }

  .hero-container {
    max-width: 1200px;
    width: 100%;
    display: grid;
    grid-template-columns: 1.2fr 0.8fr;
    gap: 4rem;
    align-items: center;
  }

  .hero-card {
    background: #ffffff;
    border: var(--border-thick);
    box-shadow: var(--shadow-flat);
    border-radius: var(--btn-radius);
    overflow: hidden;
  }

  .card-header {
    background: #000000;
    padding: 0.75rem 1.25rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: #ffffff;
  }

  .badge {
    font-family: var(--font-mono);
    font-size: var(--ft-sm);
    background: #222;
    padding: 0.2rem 0.6rem;
    border-radius: 3px;
  }

  .header-dots {
    display: flex;
    gap: 0.35rem;
  }

  .dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: #555;
  }

  .card-body {
    padding: 3rem;
  }

  .eyebrow {
    display: inline-block;
    background: var(--primary);
    border: var(--border-thin);
    padding: 0.25rem 0.75rem;
    font-family: var(--font-mono);
    font-weight: 700;
    font-size: var(--ft-sm);
    margin-bottom: 1.5rem;
    box-shadow: 2px 2px 0px #000000;
  }

  h1 {
    font-size: clamp(3rem, 6vw, 5.5rem);
    margin-bottom: 1.5rem;
    text-transform: uppercase;
  }

  .subtitle {
    font-size: var(--ft-md);
    margin-bottom: 2.5rem;
    max-width: 32rem;
    color: #333333;
  }

  .actions {
    display: flex;
    gap: 1.25rem;
    flex-wrap: wrap;
  }

  .btn {
    display: inline-block;
    padding: 0.75rem 1.5rem;
    font-weight: 700;
    text-transform: uppercase;
    border: var(--border-thick);
    border-radius: var(--btn-radius);
    transition:
      transform 0.1s ease,
      box-shadow 0.1s ease;
    cursor: pointer;
  }

  .btn-primary {
    background: var(--primary);
    box-shadow: var(--shadow-flat);
  }

  .btn-primary:hover {
    transform: translate(-3px, -3px);
    box-shadow: var(--shadow-flat-hover);
  }

  .btn-primary:active {
    transform: translate(3px, 3px);
    box-shadow: var(--shadow-flat-active);
  }

  .btn-secondary {
    background: #ffffff;
    box-shadow: var(--shadow-flat);
  }

  .btn-secondary:hover {
    transform: translate(-3px, -3px);
    box-shadow: var(--shadow-flat-hover);
  }

  .btn-secondary:active {
    transform: translate(3px, 3px);
    box-shadow: var(--shadow-flat-active);
  }

  .sticker-board {
    position: relative;
    height: 400px;
    border: var(--border-thick);
    background: #ffffff;
    border-radius: var(--btn-radius);
    box-shadow: var(--shadow-flat);
    background-image: radial-gradient(#000000 1.5px, transparent 1.5px);
    background-size: 24px 24px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .sticker-instruction {
    font-family: var(--font-mono);
    color: #555555;
    font-size: var(--ft-sm);
    margin-bottom: 2rem;
    pointer-events: none;
    user-select: none;
  }

  .sticker {
    position: absolute;
    padding: 0.75rem 1.25rem;
    border: var(--border-thick);
    box-shadow: 4px 4px 0px #000000;
    font-weight: 700;
    font-family: var(--font-mono);
    font-size: var(--ft-sm);
    color: #000000;
    cursor: grab;
    user-select: none;
    touch-action: none;
    transition: box-shadow 0.1s ease;
    text-align: center;
  }

  .sticker:hover {
    box-shadow: 6px 6px 0px #000000;
  }

  .sticker.dragging {
    cursor: grabbing;
    box-shadow: 10px 10px 0px #000000;
  }

  .sticker:nth-of-type(1) {
    top: 20%;
    left: 10%;
  }
  .sticker:nth-of-type(2) {
    top: 35%;
    right: 15%;
  }
  .sticker:nth-of-type(3) {
    bottom: 25%;
    left: 15%;
  }
  .sticker:nth-of-type(4) {
    top: 15%;
    right: 25%;
  }
  .sticker:nth-of-type(5) {
    bottom: 15%;
    right: 20%;
  }

  .sticker-icon {
    width: 24px;
    height: 24px;
  }

  @media (max-width: 992px) {
    .hero-container {
      grid-template-columns: 1fr;
      gap: 3rem;
    }
  }

  @media (max-width: 576px) {
    .card-body {
      padding: 1.5rem;
    }

    .actions {
      flex-direction: column;
    }

    .btn {
      text-align: center;
      width: 100%;
    }
  }
</style>
