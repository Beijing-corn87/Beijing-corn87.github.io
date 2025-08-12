<script>
  import { onMount } from 'svelte';

  export let data;
  let currentProjectIndex = 0;
  let projectsContainer;

  function scrollToProject(index) {
    if (projectsContainer) {
      const projectElement = projectsContainer.children[index];
      if (projectElement) {
        projectElement.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }

  function nextProject() {
    if (currentProjectIndex < data.projects.length - 1) {
      currentProjectIndex++;
      scrollToProject(currentProjectIndex);
    }
  }

  function prevProject() {
    if (currentProjectIndex > 0) {
      currentProjectIndex--;
      scrollToProject(currentProjectIndex);
    }
  }

  onMount(() => {
    // Optional: Add keyboard navigation
    const handleKeyDown = (event) => {
      if (event.key === 'ArrowRight') {
        nextProject();
      } else if (event.key === 'ArrowLeft') {
        prevProject();
      }
    };
    window.addEventListener('keydown', handleKeyDown);

    return () => {
      window.removeEventListener('keydown', handleKeyDown);
    };
  });
</script>

<div class="projects-wrapper" bind:this={projectsContainer}>
  {#if data.projects && data.projects.length > 0}
    {#each data.projects as project, i}
      <div class="project-page">
        <div class="project-content">
          <h1>{project.title}</h1>
          <p>{project.description}</p>
          <div class="languages">
            {#each project.languages as lang}
              <span>{lang}</span>
            {/each}
          </div>
          {#if project.github_link}
            <a href={project.github_link} target="_blank" rel="noopener noreferrer" class="github-link">
              <i class="fab fa-github"></i> GitHub
            </a>
          {/if}
        </div>
      </div>
    {/each}
  {:else}
    <div class="project-page">
      <div class="project-content">
        <h1>No Projects Yet</h1>
        <p>This section is currently under construction. Please check back soon to see my work!</p>
      </div>
    </div>
  {/if}

  <div class="navigation-buttons">
    <button on:click={prevProject} disabled={currentProjectIndex === 0}>Previous</button>
    <button on:click={nextProject} disabled={currentProjectIndex === data.projects.length - 1}>Next</button>
  </div>

  <a href="/" class="back-home-button">← Back to Home</a>
</div>

<style>
  .projects-wrapper {
    height: 100vh;
    overflow-y: scroll;
    scroll-snap-type: y mandatory;
  }

  .project-page {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    scroll-snap-align: start;
    padding: 2rem;
    box-sizing: border-box;
  }

  .project-content {
    max-width: 800px;
    text-align: center;
    background-color: var(--card-background);
    padding: 3rem;
    border-radius: 10px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  }

  h1 {
    font-size: 3rem;
    color: var(--primary-color);
    margin-bottom: 1rem;
  }

  p {
    font-size: 1.2rem;
    line-height: 1.6;
    margin-bottom: 1.5rem;
  }

  .languages span {
    display: inline-block;
    background-color: var(--primary-color);
    color: var(--background-color);
    padding: 0.5rem 1rem;
    border-radius: 5px;
    font-size: 0.9rem;
    margin: 0.5rem;
  }

  .github-link {
    display: inline-flex;
    align-items: center;
    font-size: 1.1rem;
    color: var(--primary-color);
    text-decoration: none;
    margin-top: 1.5rem;
    border: 2px solid var(--primary-color);
    padding: 0.8rem 1.5rem;
    border-radius: 5px;
    transition: background-color 0.3s, color 0.3s;
  }

  .github-link:hover {
    background-color: var(--primary-color);
    color: var(--background-color);
  }

  .navigation-buttons {
    position: fixed;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 1rem;
    z-index: 1000;
  }

  .navigation-buttons button {
    background-color: var(--primary-color);
    color: var(--background-color);
    border: none;
    padding: 0.8rem 1.5rem;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1rem;
    transition: opacity 0.3s;
  }

  .navigation-buttons button:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }

  .back-home-button {
    position: fixed;
    top: 2rem;
    left: 2rem;
    font-size: 1.1rem;
    color: var(--primary-color);
    text-decoration: none;
    border: 2px solid var(--primary-color);
    padding: 0.8rem 1.5rem;
    border-radius: 5px;
    transition: background-color 0.3s, color 0.3s;
    z-index: 1000;
  }

  .back-home-button:hover {
    background-color: var(--primary-color);
    color: var(--background-color);
  }
</style>