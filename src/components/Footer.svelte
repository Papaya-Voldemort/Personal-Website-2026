<script lang="ts">
  const currentYear = new Date().getFullYear();
</script>

<footer>
  <div class="container">
    <div class="socials">
      <a
        href="https://github.com/papaya-voldemort"
        target="_blank"
        rel="noopener noreferrer"
        class="social-btn"
      >
        GitHub
      </a>
      <a href="mailto:elinelson992@gmail.com" class="social-btn"> Email </a>
    </div>

    <div class="meta">
      <p>&copy; {currentYear} Eli Nelson. Built with Svelte 5.</p>
    </div>
  </div>
</footer>

<style>
  footer {
    border-top: var(--border-thick);
    background-color: var(--bg-color);
    padding: 3rem 2rem;
    margin-top: 4rem;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
  }

  .socials {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    justify-content: center;
  }

  .social-btn {
    font-family: var(--font-mono);
    font-weight: 700;
    text-transform: uppercase;
    font-size: var(--ft-sm);
    padding: 0.6rem 1.25rem;
    background: #ffffff;
    border: var(--border-thin);
    border-radius: var(--btn-radius);
    box-shadow: 3px 3px 0px #000000;
    transition:
      transform 0.1s ease,
      box-shadow 0.1s ease,
      background-color 0.1s ease;
  }

  .social-btn:hover {
    background-color: var(--primary);
    transform: translate(-2px, -2px);
    box-shadow: 5px 5px 0px #000000;
  }

  .social-btn:active {
    transform: translate(3px, 3px);
    box-shadow: 0px 0px 0px #000000;
  }

  .meta {
    font-family: var(--font-mono);
    font-size: var(--ft-xs);
    color: #555555;
    text-align: center;
  }
</style>
