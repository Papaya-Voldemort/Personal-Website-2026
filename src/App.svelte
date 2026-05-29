<script>
  import Nav from "./components/Nav.svelte";
  import About from "./components/About.svelte";
  import Project from "./components/Project.svelte";

  const navigationLinks = ["about", "projects", "experience", "contact"];
</script>

<svelte:head>
  <!-- Extra Meta Data -->
  <meta
    name="description"
    content="Eli Nelson's personal developer portfolio"
  />
</svelte:head>

<main>
  <Nav links={navigationLinks}/>
  <About />
  <Project />
</main>

<style>
</style>
