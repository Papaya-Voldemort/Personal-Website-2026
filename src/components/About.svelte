<script>
</script>

<section class="hero" id="about">
  <div class="heroContent">
    <p class="heroEyebrow">Hi, I’m Eli.</p>
    <h1>Modern Web Development</h1>
    <p class="heroSubtitle">
      Front-end developer focused on accessible UI, strong typography, and
      clean, memorable interactions.
    </p>
    <div class="heroActions">
      <a class="button buttonPrimary" href="#projects">view projects</a>
      <a class="button buttonSecondary" href="#contact">say hello</a>
    </div>
  </div>
</section>

<style>
  .hero {
    min-height: 70vh;
    display: grid;
    place-items: center;
    padding: 4rem 1.5rem;
    background: linear-gradient(
      180deg,
      rgba(95, 255, 99, 0.18),
      rgba(199, 208, 192, 0.96)
    );
    color: #111;
  }

  .heroContent {
    width: min(100%, 60rem);
    text-align: center;
    padding: 3rem;
    border-radius: 28px;
    background: rgba(255, 255, 255, 0.8);
    box-shadow: 0 32px 72px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(14px);
    border: 4px solid #000000;
  }

  .heroEyebrow {
    margin: 0 0 1rem;
    color: var(--secondary);
    text-transform: uppercase;
    letter-spacing: 0.22em;
    font-size: var(--ft-md);
    font-weight: 700;
  }

  .hero h1 {
    margin: 0;
    font-size: clamp(2.7rem, 5vw, 5rem);
    line-height: 0.98;
    font-family: "Courier Prime";
  }

  .heroSubtitle {
    margin: 1.6rem auto 2.4rem;
    max-width: 42rem;
    font-size: 1.05rem;
    line-height: 1.85;
    color: #1d2222;
  }

  .heroActions {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
  }

  .button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-width: 12rem;
    padding: 0.95rem 1.6rem;
    border-radius: var(--btn-radius);
    font-size: 1rem;
    font-weight: 700;
    text-decoration: none;
    transition:
      transform 0.2s ease,
      box-shadow 0.2s ease,
      background-color 0.2s ease;
  }

  .buttonPrimary {
    background: var(--primary);
    color: #000;
    box-shadow: 0 10px 0 rgba(0, 0, 0, 0.14);
  }

  .buttonSecondary {
    background: rgba(255, 255, 255, 0.9);
    color: #111;
    border: 1px solid rgba(0, 0, 0, 0.12);
    box-shadow: 0 10px 0 rgba(0, 0, 0, 0.08);
  }

  .button {
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

  @media (max-width: 640px) {
    .hero {
      padding: 3rem 1rem;
    }

    .heroContent {
      padding: 2rem;
    }

    .heroActions {
      flex-direction: column;
      gap: 0.85rem;
    }

    .button {
      width: 100%;
      min-width: 0;
    }
  }
</style>
