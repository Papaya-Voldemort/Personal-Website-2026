<script lang="ts">
  interface ProjectItem {
    name: string;
    description: string;
    tech: string[];
    url: string;
    github: string;
    category: string;
    color: string;
  }

  let projects: ProjectItem[] = [
    {
      name: "RuneChat",
      description:
        "A real-time WebSocket chat application leveraging Svelte 5 reactivity and custom connection pooling.",
      tech: ["Svelte 5", "TypeScript", "WebSockets", "Node.js"],
      url: "https://runechat-production-16f4.up.railway.app/",
      github: "https://github.com/Papaya-Voldemort/RuneChat",
      category: "web",
      color: "var(--theme-green)",
    },
    {
      name: "Lost-Found",
      description:
        "A lost and found web platform designed and built for FBLA, featuring simple search, filtering, and reporting.",
      tech: ["HTML5", "CSS3", "JavaScript"],
      url: "https://papaya-voldemort.github.io/Lost-Found/",
      github: "https://github.com/Papaya-Voldemort/Lost-Found",
      category: "web",
      color: "var(--theme-pink)",
    },
    {
      name: "Dont-Click-That",
      description:
        "A modern security awareness and interactive phishing simulation application built for the Congressional App Challenge.",
      tech: ["Svelte", "Vite", "TypeScript", "TailwindCSS"],
      url: "https://github.com/Papaya-Voldemort/Dont-Click-That",
      github: "https://github.com/Papaya-Voldemort/Dont-Click-That",
      category: "web",
      color: "var(--theme-yellow)",
    },
    {
      name: "web-terminal",
      description:
        "A sleek webOS terminal interface implementing a responsive CLI shell environment built with TypeScript and Appwrite.",
      tech: ["TypeScript", "Appwrite", "Vite", "CSS"],
      url: "https://web-terminal.appwrite.network/",
      github: "https://github.com/Papaya-Voldemort/web-terminal",
      category: "tools",
      color: "var(--theme-blue)",
    },
    {
      name: "passcore",
      description:
        "A lightweight, blazing fast Rust library scoring password strength. Published on crates.io.",
      tech: ["Rust", "Cargo", "Crates.io"],
      url: "https://passcore-web-production.up.railway.app/",
      github: "https://github.com/Papaya-Voldemort/passcore",
      category: "libraries",
      color: "var(--theme-pink)",
    },
    {
      name: "Ink-Iron",
      description:
        "A terminal-based, choice-driven RPG set in a supernatural Song Dynasty. Choices influence destiny in this text-based adventure.",
      tech: ["TypeScript", "Node.js", "CLI", "Game Loop"],
      url: "https://github.com/Papaya-Voldemort/Ink-Iron/releases",
      github: "https://github.com/Papaya-Voldemort/Ink-Iron",
      category: "games",
      color: "var(--theme-yellow)",
    },
    {
      name: "Closed-AI",
      description:
        "An interactive, retro puzzle-adventure game developed for the Hack Club Campfire using Godot.",
      tech: ["Godot", "GDScript", "Game Dev"],
      url: "https://papaya-voldemort.itch.io/closed-ai",
      github: "https://github.com/Papaya-Voldemort/Closed-AI",
      category: "games",
      color: "var(--theme-blue)",
    },
    {
      name: "FishByte",
      description:
        "A retro 2D fishing simulator game featuring mechanics, inventories, and custom physics built using Python and Pygame.",
      tech: ["Python", "Pygame", "Game Loop"],
      url: "https://github.com/Papaya-Voldemort/FishByte",
      github: "https://github.com/Papaya-Voldemort/FishByte",
      category: "games",
      color: "var(--theme-green)",
    },
    {
      name: "Rubber-Factorio-Mod",
      description:
        "A custom Factorio mod adding rubber harvesting, recipe pipelines, and technology tree integrations.",
      tech: ["Lua", "Factorio API", "Modding"],
      url: "https://github.com/Papaya-Voldemort/Rubber-Factorio-Mod",
      github: "https://github.com/Papaya-Voldemort/Rubber-Factorio-Mod",
      category: "tools",
      color: "var(--theme-pink)",
    },
  ];

  let selectedFilter = $state("all");

  let filteredProjects = $derived(
    selectedFilter === "all"
      ? projects
      : projects.filter((p) => p.category === selectedFilter),
  );

  let filterButtons: string[] = [];

  projects.forEach((i) => {
    let category = i.category;
    if (filterButtons.includes(category)) return;
    filterButtons.push(category);
  });
</script>

<section class="projects-section" id="projects">
  <div class="container">
    <div class="header-row">
      <div class="section-title">
        <h2>Selected Works</h2>
      </div>

      <div class="filter-buttons">
        <button
          class="filter-btn"
          class:active={selectedFilter === "all"}
          onclick={() => (selectedFilter = "all")}
        >
          All
        </button>
        {#each filterButtons as category}
          <button
            class="filter-btn"
            class:active={selectedFilter === category}
            onclick={() => (selectedFilter = category)}
          >
            {category}
          </button>
        {/each}
      </div>
    </div>

    <div class="grid">
      {#each filteredProjects as project}
        <div class="project-card">
          <div class="cover" style="background-color: {project.color};">
            <svg
              viewBox="0 0 100 100"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <rect
                x="10"
                y="10"
                width="80"
                height="80"
                stroke="#000000"
                stroke-width="4"
                stroke-dasharray="8 6"
              />
              {#if project.name === "RuneChat"}
                <path
                  d="M30 40H70M30 50H60M30 60H50"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-linecap="round"
                />
              {:else if project.name === "Lost-Found"}
                <circle
                  cx="45"
                  cy="45"
                  r="16"
                  stroke="#000000"
                  stroke-width="4"
                />
                <path
                  d="M56 56 L76 76"
                  stroke="#000000"
                  stroke-width="6"
                  stroke-linecap="round"
                />
              {:else if project.name === "Dont-Click-That"}
                <path
                  d="M50 20 L80 75 H20 Z"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-linejoin="round"
                />
                <path
                  d="M50 40 V56"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-linecap="round"
                />
                <circle cx="50" cy="66" r="3" fill="#000000" />
              {:else if project.name === "web-terminal"}
                <path
                  d="M25 35 L45 50 L25 65"
                  stroke="#000000"
                  stroke-width="5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <path
                  d="M50 65 H75"
                  stroke="#000000"
                  stroke-width="5"
                  stroke-linecap="round"
                />
              {:else if project.name === "passcore"}
                <rect
                  x="30"
                  y="48"
                  width="40"
                  height="32"
                  rx="4"
                  stroke="#000000"
                  stroke-width="4"
                />
                <path
                  d="M40 48 V38 C40 30, 60 30, 60 38 V48"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-linecap="round"
                />
                <circle cx="50" cy="62" r="4" fill="#000000" />
                <path
                  d="M50 66 V72"
                  stroke="#000000"
                  stroke-width="3"
                  stroke-linecap="round"
                />
              {:else if project.name === "Ink-Iron"}
                <path
                  d="M30 70 L70 30"
                  stroke="#000000"
                  stroke-width="6"
                  stroke-linecap="round"
                />
                <path
                  d="M25 75 L35 65"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-linecap="round"
                />
                <path
                  d="M20 80 L25 75"
                  stroke="#000000"
                  stroke-width="6"
                  stroke-linecap="round"
                />
              {:else if project.name === "Closed-AI"}
                <path
                  d="M30 70 L70 70 M40 75 L60 65 M60 75 L40 65"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-linecap="round"
                />
                <path
                  d="M50 25 C60 40, 60 55, 50 65 C40 55, 40 40, 50 25 Z"
                  stroke="#000000"
                  stroke-width="4"
                  fill="none"
                  stroke-linejoin="round"
                />
              {:else if project.name === "FishByte"}
                <path
                  d="M25 50 C35 35, 65 35, 75 50 C65 65, 35 65, 25 50 Z"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-linejoin="round"
                />
                <path
                  d="M75 50 L85 40 V60 Z"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-linejoin="round"
                />
                <circle cx="38" cy="46" r="3" fill="#000000" />
              {:else if project.name === "Rubber-Factorio-Mod"}
                <circle
                  cx="50"
                  cy="50"
                  r="18"
                  stroke="#000000"
                  stroke-width="4"
                  stroke-dasharray="8 4"
                />
                <circle
                  cx="50"
                  cy="50"
                  r="8"
                  stroke="#000000"
                  stroke-width="4"
                />
                <path
                  d="M30 50 H70 M50 30 V70"
                  stroke="#000000"
                  stroke-width="2"
                />
              {:else}
                <path
                  d="M30 30L70 70M70 30L30 70"
                  stroke="#000000"
                  stroke-width="6"
                  stroke-linecap="round"
                />
              {/if}
            </svg>
          </div>

          <div class="info">
            <h3>{project.name}</h3>
            <p>{project.description}</p>

            <div class="tech-tags">
              {#each project.tech as t}
                <span class="tech-tag">{t}</span>
              {/each}
            </div>

            <div class="card-actions">
              <a
                href={project.url}
                target="_blank"
                rel="noopener noreferrer"
                class="action-btn btn-demo"
              >
                Launch App
              </a>
              <a
                href={project.github}
                target="_blank"
                rel="noopener noreferrer"
                class="action-btn btn-code"
              >
                Source Code
              </a>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .projects-section {
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

  .header-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 2rem;
    flex-wrap: wrap;
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
    transform: rotate(1deg);
  }

  .filter-buttons {
    display: flex;
    gap: 0.75rem;
    background: #ffffff;
    border: var(--border-thick);
    padding: 0.5rem;
    border-radius: var(--btn-radius);
    box-shadow: var(--shadow-flat);
  }

  .filter-btn {
    font-family: var(--font-mono);
    font-weight: 700;
    text-transform: uppercase;
    font-size: var(--ft-xs);
    background: transparent;
    border: none;
    padding: 0.4rem 0.8rem;
    cursor: pointer;
    border-radius: var(--btn-radius);
    transition: background-color 0.15s ease;
  }

  .filter-btn:hover {
    background-color: #f0f0f0;
  }

  .filter-btn.active {
    background-color: var(--primary);
    border: var(--border-thin);
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 3rem;
  }

  .project-card {
    background: #ffffff;
    border: var(--border-thick);
    box-shadow: var(--shadow-flat);
    border-radius: var(--btn-radius);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    transition:
      transform 0.15s ease,
      box-shadow 0.15s ease;
  }

  .project-card:hover {
    transform: translate(-3px, -3px);
    box-shadow: var(--shadow-flat-hover);
  }

  .cover {
    height: 180px;
    border-bottom: var(--border-thick);
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    position: relative;
  }

  .cover svg {
    width: 90px;
    height: 90px;
    transition: transform 0.3s ease;
  }

  .project-card:hover .cover svg {
    transform: scale(1.1) rotate(5deg);
  }

  .info {
    padding: 2rem;
    display: flex;
    flex-direction: column;
    flex: 1;
    gap: 1.25rem;
  }

  .info h3 {
    font-size: var(--ft-lg);
    text-transform: uppercase;
  }

  .info p {
    font-size: var(--ft-sm);
    color: #444444;
    line-height: 1.6;
    flex: 1;
  }

  .tech-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .tech-tag {
    font-family: var(--font-mono);
    font-size: var(--ft-xs);
    font-weight: 700;
    background: #f0f0f0;
    border: var(--border-thin);
    padding: 0.2rem 0.5rem;
    border-radius: var(--btn-radius);
  }

  .card-actions {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
    margin-top: 0.5rem;
  }

  .action-btn {
    text-align: center;
    font-weight: 700;
    font-size: var(--ft-xs);
    text-transform: uppercase;
    padding: 0.6rem 0.5rem;
    border: var(--border-thin);
    border-radius: var(--btn-radius);
    box-shadow: 2px 2px 0px #000000;
    transition:
      transform 0.1s ease,
      box-shadow 0.1s ease;
  }

  .action-btn:active {
    transform: translate(2px, 2px);
    box-shadow: 0px 0px 0px #000000;
  }

  .btn-demo {
    background-color: var(--primary);
  }

  .btn-code {
    background-color: #ffffff;
  }

  @media (max-width: 576px) {
    .grid {
      grid-template-columns: 1fr;
    }
  }
</style>
