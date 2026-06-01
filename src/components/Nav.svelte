<script lang="ts">
  let { links = [], theme = $bindable() } = $props();
  
  let menuOpen = $state(false);

  const themes = [
    { id: "green", color: "#afff5e", label: "Green" },
    { id: "pink", color: "#ff6eb9", label: "Pink" },
    { id: "yellow", color: "#ffee54", label: "Yellow" },
    { id: "blue", color: "#5ee9ff", label: "Blue" }
  ];

  function toggleMenu() {
    menuOpen = !menuOpen;
  }

  function selectTheme(themeId: string) {
    theme = themeId;
  }
</script>

<header>
  <a href="#about" class="logo">
    <span>EliNelson.dev</span>
  </a>

  <div class="nav-actions">
    <div class="theme-selector">
      {#each themes as t}
        <button
          class="theme-dot"
          class:active={theme === t.id}
          style="background-color: {t.color};"
          aria-label={t.label}
          onclick={() => selectTheme(t.id)}
        ></button>
      {/each}
    </div>

    <nav class:open={menuOpen}>
      <ul>
        {#each links as link}
          <li>
            <a href={`#${link}`} onclick={() => menuOpen = false}>{link}</a>
          </li>
        {/each}
      </ul>
    </nav>

    <button class="menu-toggle" onclick={toggleMenu} aria-label="Toggle navigation menu">
      <div class="bar"></div>
      <div class="bar"></div>
      <div class="bar"></div>
    </button>
  </div>
</header>

<style>
  header {
    background-color: var(--bg-color);
    padding: 1.25rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: var(--border-thick);
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .nav-actions {
    display: flex;
    align-items: center;
    gap: 1.5rem;
  }

  .theme-selector {
    display: flex;
    gap: 0.5rem;
    background: #ffffff;
    border: var(--border-thin);
    padding: 0.35rem 0.5rem;
    border-radius: var(--btn-radius);
    box-shadow: 2px 2px 0px #000000;
  }

  .theme-dot {
    width: 1.2rem;
    height: 1.2rem;
    border-radius: 50%;
    border: 2px solid #000000;
    cursor: pointer;
    transition: transform 0.1s ease;
  }

  .theme-dot:hover {
    transform: scale(1.15);
  }

  .theme-dot.active {
    box-shadow: inset 0 0 0 2px #ffffff, 0 0 0 1px #000000;
  }

  nav ul {
    list-style: none;
    display: flex;
    gap: 1.25rem;
  }

  nav a {
    display: inline-block;
    padding: 0.5rem 1rem;
    background-color: #ffffff;
    border: var(--border-thin);
    border-radius: var(--btn-radius);
    font-size: var(--ft-sm);
    text-transform: uppercase;
    font-weight: 700;
    box-shadow: 3px 3px 0px #000000;
    transition: transform 0.1s ease, box-shadow 0.1s ease, background-color 0.1s ease;
  }

  nav a:hover {
    background-color: var(--primary);
    transform: translate(-2px, -2px);
    box-shadow: 5px 5px 0px #000000;
  }

  nav a:active {
    transform: translate(3px, 3px);
    box-shadow: 0px 0px 0px #000000;
  }

  .logo {
    display: inline-block;
    cursor: pointer;
    font-weight: 900;
  }

  .logo span {
    display: inline-block;
    font-size: var(--ft-lg);
    font-family: var(--font-heading);
    letter-spacing: 0.05em;
  }

  .logo:hover span {
    animation: fontChaos 750ms steps(1) infinite;
  }

  .menu-toggle {
    display: none;
    flex-direction: column;
    justify-content: space-between;
    width: 2.25rem;
    height: 1.75rem;
    background: #ffffff;
    border: var(--border-thin);
    border-radius: var(--btn-radius);
    padding: 0.35rem;
    cursor: pointer;
    box-shadow: 3px 3px 0px #000000;
  }

  .menu-toggle:active {
    transform: translate(2px, 2px);
    box-shadow: 1px 1px 0px #000000;
  }

  .menu-toggle .bar {
    width: 100%;
    height: 3px;
    background-color: #000000;
  }

  @keyframes fontChaos {
    0% {
      font-family: "Space Grotesk", sans-serif;
      transform: translateY(-2px) rotate(-1deg);
    }
    14% {
      font-family: "Courier Prime", monospace;
      transform: translateY(1px) rotate(1deg);
    }
    28% {
      font-family: "Bebas Neue", cursive;
      transform: scale(1.04) skewX(-4deg);
    }
    42% {
      font-family: "Permanent Marker", cursive;
      transform: rotate(-2deg) scale(1.02);
    }
    56% {
      font-family: "Orbitron", sans-serif;
      transform: translateY(-1px) scaleY(1.1);
    }
    70% {
      font-family: "VT323", monospace;
      transform: scale(1.08);
    }
    84% {
      font-family: "Cinzel", serif;
      transform: translateY(-1px);
    }
    100% {
      font-family: "Inter", sans-serif;
      transform: translateY(2px) rotate(1deg);
    }
  }

  @media (max-width: 768px) {
    .menu-toggle {
      display: flex;
    }

    nav {
      position: absolute;
      top: 100%;
      left: 0;
      right: 0;
      background-color: var(--bg-color);
      border-bottom: var(--border-thick);
      padding: 1.5rem 2rem;
      display: none;
    }

    nav.open {
      display: block;
    }

    nav ul {
      flex-direction: column;
      gap: 1rem;
    }

    nav a {
      display: block;
      text-align: center;
    }
  }
</style>

