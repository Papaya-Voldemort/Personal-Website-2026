<script lang="ts">
  const skillCategories = [
    {
      title: "Frontend Development",
      skills: [
        "HTML5",
        "CSS3 / SCSS",
        "JavaScript",
        "TypeScript",
        "Svelte 5",
        "Vite",
      ],
    },
    {
      title: "Systems & Backends",
      skills: ["Rust", "TypeScript", "Python", "Java", "Godot", "Lua"],
    },
    {
      title: "Tools & Workflows",
      skills: ["Git & GitHub", "Cargo", "npm", "bun", "Railway", "Linux Shell"],
    },
  ];

  const skillIcons: Record<string, string> = {
    "HTML5": "html.svg",
    "CSS3 / SCSS": "css.svg",
    "JavaScript": "javascript.svg",
    "TypeScript": "typescript.svg",
    "Svelte 5": "svelte.svg",
    "Vite": "vite.svg",
    "Rust": "rust.svg",
    "Python": "python.svg",
    "Java": "java.svg",
    "Godot": "godot.svg",
    "Lua": "lua.svg",
    "Git & GitHub": "git.svg",
    "Cargo": "cargo.svg",
    "npm": "npm.svg",
    "bun": "bun.svg",
    "Railway": "railway.svg",
    "Linux Shell": "bash.svg",
  };
</script>

<section class="skills-section" id="skills">
  <div class="container">
    <div class="section-title">
      <h2>Technical Arsenal</h2>
    </div>

    <div class="grid">
      {#each skillCategories as category}
        <div class="category-card">
          <h3>{category.title}</h3>
          <div class="tags">
            {#each category.skills as skill}
              <div class="tag">
                {#if skillIcons[skill]}
                  <img
                    src={`src/assets/icons/${skillIcons[skill]}`}
                    alt={skill}
                    class="tag-icon"
                  />
                {/if}
                <span>{skill}</span>
              </div>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .skills-section {
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
    transform: rotate(-1deg);
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2.5rem;
  }

  .category-card {
    background: #ffffff;
    border: var(--border-thick);
    box-shadow: var(--shadow-flat);
    border-radius: var(--btn-radius);
    padding: 2.5rem;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    transition:
      transform 0.15s ease,
      box-shadow 0.15s ease;
  }

  .category-card:hover {
    transform: translate(-3px, -3px);
    box-shadow: var(--shadow-flat-hover);
  }

  .category-card h3 {
    font-size: var(--ft-lg);
    text-transform: uppercase;
    border-bottom: var(--border-thin);
    padding-bottom: 0.5rem;
  }

  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.75rem;
  }

  .tag {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    font-family: var(--font-mono);
    font-size: var(--ft-sm);
    font-weight: 700;
    background: #ffffff;
    border: var(--border-thin);
    padding: 0.4rem 0.8rem;
    border-radius: var(--btn-radius);
    box-shadow: 2px 2px 0px #000000;
    cursor: default;
    transition:
      transform 0.15s ease,
      box-shadow 0.15s ease,
      background-color 0.15s ease;
  }

  .tag:hover {
    background-color: var(--primary);
    transform: translate(-2px, -2px) rotate(1.5deg);
    box-shadow: 4px 4px 0px #000000;
  }

  .tag-icon {
    width: 16px;
    height: 16px;
    display: block;
    object-fit: contain;
  }
</style>

