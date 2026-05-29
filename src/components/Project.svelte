<script>
  let {
    projects = [
      {"name": "RuneChat", "URL": "https://runechat-production-16f4.up.railway.app/"},
      {"name": "RuneChat", "URL": "https://runechat-production-16f4.up.railway.app/"},
      {"name": "RuneChat", "URL": "https://runechat-production-16f4.up.railway.app/"},
      {"name": "RuneChat", "URL": "https://runechat-production-16f4.up.railway.app/"},
      {"name": "RuneChat", "URL": "https://runechat-production-16f4.up.railway.app/"},
    ]
  } = $props();
</script>

<div class="projects">
  {#each projects as project}
    <div class="project">
      <h1>{project.name}</h1>
      <a href={project.URL}>View Here</a>
    </div>
  {/each}
</div>