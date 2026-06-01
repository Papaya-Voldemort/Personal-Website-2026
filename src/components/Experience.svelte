<script lang="ts">
  interface Job {
    role: string;
    company: string;
    period: string;
    points: string[];
  }

  const history: Job[] = [
    {
      role: "Modern Svelte & TS UI Engineer",
      company: "Independent & Hack Club Stardance",
      period: "Spring 2026 - Present",
      points: [
        "Building reactive, state-driven user interfaces using Svelte 5 and TypeScript (e.g., Dont-Click-That security simulator, web-terminal).",
        "Developing sleek, accessible web components and responsive layouts featuring modern CSS and micro-interactions.",
        "Contributing interactive features and frontend logic to the Hack Club Stardance event space."
      ],
    },
    {
      role: "API & Systems Programmer",
      company: "System Libraries & Game Servers",
      period: "Late 2025 - Early 2026",
      points: [
        "Published robust utility libraries (passcore strength meter, SimpleRNG LCG) to crates.io with extensive test suites in Rust.",
        "Constructed performant REST APIs with Hono (TypeScript) and backend validation services with Axum (Rust).",
        "Created custom event-driven plugins in Java (Diamond-SMP) for Minecraft server orchestration."
      ],
    },
    {
      role: "Interactive Game Dev & Community Contributor",
      company: "FBLA & Hack Club Campfire",
      period: "Winter 2025 - Spring 2026",
      points: [
        "Accelerated development skills by building community platforms for FBLA, including the Lost-Found web app and a Virtual Pet simulator.",
        "Programmed game mechanics, audio hooks, and physics logic in GDScript/Godot for Closed-AI, featured at Hack Club's Campfire workshop.",
        "Collaborated with community developers on styling guides, open-source repositories, and developer tools."
      ],
    },
    {
      role: "Getting Started & Early Scripting",
      company: "Hack Club Summer of Making & Flavortown",
      period: "Mid 2025",
      points: [
        "Began coding journey in Mid 2025, diving into development during the Hack Club Summer of Making and Flavortown hackathons.",
        "Developed 2D arcade games in Python using Pygame (FishByte, Turtle-Casino) to master OOP concepts and core logic flows.",
        "Authored custom Lua mods for Factorio to manipulate crafting tables, recipe pipelines, and technology tree designs."
      ],
    },
  ];
</script>

<section class="experience-section" id="experience">
  <div class="container">
    <div class="section-title">
      <h2>Work Logs</h2>
    </div>

    <div class="terminal">
      <div class="terminal-header">
        <span class="badge">eli_nelson.sh</span>
        <div class="header-dots">
          <span class="dot"></span>
          <span class="dot"></span>
          <span class="dot"></span>
        </div>
      </div>

      <div class="terminal-body">
        <div class="command-line">
          <span class="prompt">eli@nelson:~$</span>
          <span class="command">cat experience.json</span>
        </div>

        <div class="terminal-output">
          {#each history as job}
            <div class="experience-card">
              <div class="card-meta">
                <span class="period">{job.period}</span>
                <span class="company">{job.company}</span>
              </div>
              <h3 class="role">{job.role}</h3>
              <ul class="points">
                {#each job.points as point}
                  <li>{point}</li>
                {/each}
              </ul>
            </div>
          {/each}
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  .experience-section {
    padding: 2rem;
    max-width: 1200px;
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
    transform: rotate(-1.5deg);
  }

  .terminal {
    background: #ffffff;
    border: var(--border-thick);
    box-shadow: var(--shadow-flat);
    border-radius: var(--btn-radius);
    overflow: hidden;
  }

  .terminal-header {
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

  .terminal-body {
    background: #111111;
    color: #ffffff;
    padding: 2rem;
    font-family: var(--font-mono);
    min-height: 400px;
  }

  .command-line {
    display: flex;
    gap: 0.75rem;
    margin-bottom: 2rem;
    font-size: var(--ft-md);
  }

  .prompt {
    color: var(--primary);
  }

  .command {
    color: #ffffff;
  }

  .terminal-output {
    display: flex;
    flex-direction: column;
    gap: 2.5rem;
  }

  .experience-card {
    border-left: 3px dashed #333333;
    padding-left: 1.5rem;
    transition: border-color 0.2s ease;
  }

  .experience-card:hover {
    border-left-color: var(--primary);
  }

  .card-meta {
    display: flex;
    justify-content: space-between;
    font-size: var(--ft-xs);
    color: #888888;
    margin-bottom: 0.5rem;
  }

  .period {
    background: #222222;
    padding: 0.15rem 0.5rem;
    border-radius: 3px;
    color: #ffffff;
  }

  .company {
    font-weight: 700;
  }

  .role {
    font-size: var(--ft-lg);
    color: #ffffff;
    margin-bottom: 1rem;
    text-transform: uppercase;
    font-family: var(--font-body);
  }

  .points {
    list-style-type: square;
    padding-left: 1.25rem;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    font-size: var(--ft-sm);
    color: #cccccc;
    line-height: 1.6;
  }

  @media (max-width: 576px) {
    .terminal-body {
      padding: 1rem;
    }

    .card-meta {
      flex-direction: column;
      gap: 0.5rem;
      align-items: flex-start;
    }
  }
</style>
