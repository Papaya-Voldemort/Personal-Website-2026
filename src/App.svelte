<script lang="ts">
  import Nav from "./components/Nav.svelte";
  import About from "./components/About.svelte";
  import Skills from "./components/Skills.svelte";
  import Project from "./components/Project.svelte";
  import Experience from "./components/Experience.svelte";
  import Contact from "./components/Contact.svelte";
  import Footer from "./components/Footer.svelte";

  const navigationLinks = ["about", "skills", "projects", "experience", "contact"];
  
  let currentTheme = $state("green");

  $effect(() => {
    document.documentElement.setAttribute("data-theme", currentTheme);
  });
</script>

<svelte:head>
  <meta name="description" content="Eli Nelson's personal developer portfolio" />
</svelte:head>

<div class="app-container">
  <Nav links={navigationLinks} bind:theme={currentTheme} />
  
  <main>
    <About />
    <Skills />
    <Project />
    <Experience />
    <Contact />
  </main>

  <Footer />
</div>

<style>
  .app-container {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }

  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 6rem;
    padding-bottom: 6rem;
  }
</style>

