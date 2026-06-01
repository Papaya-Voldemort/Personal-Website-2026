<script lang="ts">
  let name = $state("");
  let email = $state("");
  let message = $state("");
  let submitted = $state(false);

  function handleSubmit(e: SubmitEvent) {
    e.preventDefault();
    if (!name || !email || !message) return;
    submitted = true;
  }

  function resetForm() {
    name = "";
    email = "";
    message = "";
    submitted = false;
  }
</script>

<section class="contact-section" id="contact">
  <div class="container">
    <div class="section-title">
      <h2>Drop a line</h2>
    </div>

    <div class="contact-box">
      {#if submitted}
        <div class="success-message">
          <div class="success-header">
            <span>transmission_success.log</span>
          </div>
          <div class="success-body">
            <h3>Message Sent!</h3>
            <p>Thanks, {name}. Your transmission has been queued successfully. I will get back to you soon.</p>
            <button class="btn btn-secondary" onclick={resetForm}>Send Another</button>
          </div>
        </div>
      {:else}
        <form onsubmit={handleSubmit} class="contact-form">
          <div class="form-group">
            <label for="name">Name</label>
            <input
              type="text"
              id="name"
              bind:value={name}
              placeholder="YOUR NAME"
              required
            />
          </div>

          <div class="form-group">
            <label for="email">Email</label>
            <input
              type="email"
              id="email"
              bind:value={email}
              placeholder="YOUR_EMAIL@DOMAIN.COM"
              required
            />
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea
              id="message"
              rows="6"
              bind:value={message}
              placeholder="WRITE YOUR MESSAGE HERE..."
              required
            ></textarea>
          </div>

          <button type="submit" class="btn btn-primary submit-btn">
            Send Message
          </button>
        </form>
      {/if}
    </div>
  </div>
</section>

<style>
  .contact-section {
    padding: 2rem;
    max-width: 800px;
    margin: 0 auto;
    width: 100%;
  }

  .container {
    display: flex;
    flex-direction: column;
    gap: 3rem;
  }

  .section-title h2 {
    font-size: var(--ft-xl);
    text-transform: uppercase;
    display: inline-block;
    background: #ffffff;
    border: var(--border-thick);
    padding: 0.75rem 1.5rem;
    box-shadow: var(--shadow-flat);
    border-radius: var(--btn-radius);
    transform: rotate(2deg);
  }

  .contact-box {
    background: #ffffff;
    border: var(--border-thick);
    box-shadow: var(--shadow-flat);
    border-radius: var(--btn-radius);
    overflow: hidden;
  }

  .contact-form {
    padding: 3rem;
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .form-group label {
    font-family: var(--font-mono);
    font-weight: 700;
    text-transform: uppercase;
    font-size: var(--ft-sm);
  }

  .form-group input,
  .form-group textarea {
    font-family: var(--font-body);
    font-size: var(--ft-md);
    padding: 0.85rem 1rem;
    border: var(--border-thick);
    border-radius: var(--btn-radius);
    background-color: var(--bg-color);
    outline: none;
    transition: transform 0.1s ease, box-shadow 0.1s ease;
  }

  .form-group input:focus,
  .form-group textarea:focus {
    background-color: #ffffff;
    box-shadow: 4px 4px 0px #000000;
    transform: translate(-2px, -2px);
    border-color: var(--primary);
  }

  .btn {
    display: inline-block;
    padding: 0.85rem 1.75rem;
    font-weight: 700;
    text-transform: uppercase;
    border: var(--border-thick);
    border-radius: var(--btn-radius);
    transition: transform 0.1s ease, box-shadow 0.1s ease;
    cursor: pointer;
    font-size: var(--ft-sm);
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
    transform: translate(-2px, -2px);
    box-shadow: var(--shadow-flat-hover);
  }

  .btn-secondary:active {
    transform: translate(2px, 2px);
    box-shadow: var(--shadow-flat-active);
  }

  .submit-btn {
    align-self: flex-start;
  }

  .success-message {
    text-align: center;
  }

  .success-header {
    background: #000000;
    padding: 0.75rem;
    color: #ffffff;
    font-family: var(--font-mono);
    font-size: var(--ft-sm);
  }

  .success-body {
    padding: 3rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
  }

  .success-body h3 {
    font-size: var(--ft-lg);
    text-transform: uppercase;
  }

  .success-body p {
    max-width: 400px;
    font-size: var(--ft-sm);
    color: #444444;
  }

  @media (max-width: 576px) {
    .contact-form {
      padding: 1.5rem;
    }
    
    .submit-btn {
      width: 100%;
    }
  }
</style>
