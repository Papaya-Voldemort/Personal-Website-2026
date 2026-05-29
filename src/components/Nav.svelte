<!-- Nav.svelte - Navigation + Header file -->

<script>
  let { links = ["test", "test2", "test3"] } = $props();
</script>

<header>
  <div class="logo">
    <span>EliNelson.dev</span>
  </div>
  <nav>
    <ul>
      {#each links as link}
        <li>
          <a href={`#${link}`}>{link}</a>
        </li>
      {/each}
    </ul>
  </nav>
</header>

<style>
  header {
    background-color: var(--secondary);
    max-width: 100%;
    height: 100%;
    padding: 1rem;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }

  nav {
    margin: 0;
    padding: 0;
  }

  ul {
    list-style: none;
    display: flex;
    gap: 1.25rem;
    margin: 0;
    padding: 0;
  }

  .logo {
    position: relative;
    display: inline-block;
    cursor: pointer;

    span {
      display: inline-block;
      font-size: var(--ft-xl);
      transition:
        transform 0.25s ease,
        filter 0.25s ease,
        letter-spacing 0.25s ease;
      animation-fill-mode: forwards;
    }

    &:hover span {
      animation: fontChaos 700ms steps(1) infinite;
    }
  }

  @keyframes fontChaos {
    0% {
      font-family: "Space Grotesk", sans-serif;
      transform: translateY(-2px) rotate(-1deg);
      letter-spacing: 0.02em;
    }
    14% {
      font-family: "Courier Prime", monospace;
      transform: translateY(1px) rotate(1deg);
      letter-spacing: -0.03em;
    }
    28% {
      font-family: "Bebas Neue", cursive;
      transform: scale(1.04) skewX(-4deg);
      letter-spacing: 0.05em;
    }
    42% {
      font-family: "Permanent Marker", cursive;
      transform: rotate(-2deg) scale(1.02);
      filter: blur(0.4px);
    }
    56% {
      font-family: "Orbitron", sans-serif;
      transform: translateY(-1px) scaleY(1.1);
      letter-spacing: 0.08em;
    }
    70% {
      font-family: "VT323", monospace;
      transform: scale(1.08);
      filter: blur(0.6px);
    }
    84% {
      font-family: "Cinzel", serif;
      transform: translateY(-1px);
      letter-spacing: 0.04em;
    }
    100% {
      font-family: "Inter", sans-serif;
      transform: translateY(2px) rotate(1deg);
      letter-spacing: -0.01em;
    }
  }

  a {
    display: inline-block;
    padding: 0.6rem 1rem;
    background-color: var(--primary);
    border-radius: var(--btn-radius);
    font-size: var(--ft-lg);
    text-decoration: none;
    color: inherit;
    box-shadow: 5px 5px 0px 0px #000000;
    transition:
      background-color 0.1s ease-in-out,
      transform 0.1s ease,
      box-shadow 0.1s ease;

    &:hover {
      background-color: var(--primary-hover);
      transform: translate(-2px, -2px);
      box-shadow: 7px 7px 0px 0px #000000;
    }

    &:active {
      transform: translate(5px, 5px);
      box-shadow: 0px 0px 0px 0px #000000;
    }
  }
</style>
