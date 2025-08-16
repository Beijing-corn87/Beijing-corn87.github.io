<script>
  import { onMount } from 'svelte';

  export let data;
  let currentProjectIndex = 0;
  let projectsContainer;

  const languageMap = {
    "Svelte": { icon: "fa-svelte", color: "#FF3E00" },
    "JavaScript": { icon: "fa-js", color: "#F7DF1E" },
    "CSS": { icon: "fa-css3-alt", color: "#1572B6" },
    "Python": { icon: "fa-python", color: "#3776AB" },
    "Flask": { icon: "fa-flask", color: "#000000" }, // Flask doesn't have a direct FA icon, using a generic one
    "HTML": { icon: "fa-html5", color: "#E34F26" },
    "Go": { icon: "fa-golang", color: "#00ADD8" },
    "Golang": { icon: "fa-golang", color: "#00ADD8" },
    "C++": { icon: "fa-cpp", color: "#00599C" },
    "Ruby": { icon: "fa-ruby", color: "#CC342D" },
    // Add more languages as needed
  };

  function scrollToProject(index) {
    if (projectsContainer) {
      const projectElements = projectsContainer.querySelectorAll('.project-page');
      if (projectElements[index]) {
        projectElements[index].scrollIntoView({ behavior: 'smooth' });
      }
    }
  }

  function nextProject() {
    const projectElements = projectsContainer.querySelectorAll('.project-page');
    if (currentProjectIndex < projectElements.length - 1) {
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
              {#if languageMap[lang]}
                <a href="https://github.com/topics/{lang.toLowerCase()}" target="_blank" rel="noopener noreferrer" class="language-link" style="color: {languageMap[lang].color};">
                  <i class="fab {languageMap[lang].icon}"></i> {lang}
                </a>
              {:else}
                <a href="https://github.com/topics/{lang.toLowerCase()}" target="_blank" rel="noopener noreferrer" class="language-link">
                  {lang}
                </a>
              {/if}
            {/each}
          </div>
          {#if project.public_archive}
            <div class="public-archive-box">
              Public Archive
            </div>
          {/if}
          {#if project.github_link}
            <a href={project.github_link} target="_blank" rel="noopener noreferrer" class="github-link">
              <i class="fab fa-github"></i> GitHub
            </a>
          {/if}
        </div>
      </div>
      {#if i < data.projects.length - 1}
        <div class="project-divider"></div>
      {/if}
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
    <button on:click={nextProject} disabled={currentProjectIndex >= data.projects.length - 1}>Next</button>
  </div>

  <a href="/" class="back-home-button">← Back to Home</a>
</div>

<style>
  .projects-wrapper {
    height: 100vh;
    overflow-y: scroll;
    /* Removed scroll-snap-type: y mandatory; */
    /* Hide scrollbar for Chrome, Safari and Opera */
    &::-webkit-scrollbar {
      display: none;
    }
    /* Hide scrollbar for IE, Edge and Firefox */
    -ms-overflow-style: none;  /* IE and Edge */
    scrollbar-width: none;  /* Firefox */
  }

  .project-page {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 2rem;
    box-sizing: border-box;
  }

  .project-divider {
    height: 2px; /* Make it thin */
    background-color: var(--primary-color); /* Color of the divider */
    width: 100%; /* Ensure it goes across the whole page */
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
    font-size: 1.5rem; /* Increased font size for icons */
    margin: 1rem; /* Increased margin for more spacing */
  }

  .language-link {
    text-decoration: none; /* Remove default underline */
    transition: text-decoration 0.3s ease; /* Smooth transition for underline */
  }

  .language-link:hover {
    text-decoration: underline; /* Underline on hover */
  }

  .public-archive-box {
    background-color: transparent; /* No fill */
    border: 2px solid #FFD700; /* Yellow border */
    color: #FFD700; /* Yellow text */
    padding: 0.8rem 1.5rem;
    border-radius: 5px;
    font-size: 1.1rem;
    font-weight: bold;
    margin-bottom: 1.5rem; /* Space between this and GitHub button */
    display: block; /* Changed to block to take full width and allow centering */
    margin-left: auto; /* Center the block */
    margin-right: auto; /* Center the block */
    margin-top: 1.5em;
    margin-bottom: 1em;
    width: fit-content; /* Adjust width to content */
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