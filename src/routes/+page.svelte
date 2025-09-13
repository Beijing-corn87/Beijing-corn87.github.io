<script>
  import { onMount } from 'svelte';

  const fullTitle = 'Blue Kiwi';
  let displayedTitle = '';
  const typingSpeed = 150; // milliseconds per character

  onMount(() => {
    let i = 0;
    const typingInterval = setInterval(() => {
      if (i < fullTitle.length) {
        displayedTitle += fullTitle.charAt(i);
        i++;
      } else {
        clearInterval(typingInterval);
      }
    }, typingSpeed);

    // Cleanup interval when component is destroyed
    return () => {
      clearInterval(typingInterval);
    };
  });
</script>

<div class="container">
  <img src="/logo.png" alt="Blue Kiwi Logo" style="width: 150px; height: 150px; margin-bottom: 20px;">
  <h1 class="title">
    {displayedTitle}<span class="cursor"></span>
  </h1>
  <p class="bio">
    🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓🤓
  </p>
  <div class="buttons-container">
    <a href="https://github.com/Beijing-corn87" target="_blank" rel="noopener noreferrer" class="github-button">
      <i class="fab fa-github"></i> GitHub Profile
    </a>
    <a href="/projects" class="projects-button">Projects</a>
  </div>
</div>

<style>
  .container {
    padding: 2rem;
    max-width: 800px;
  }

  .title {
    font-size: 3rem;
    font-weight: 500;
    color: var(--primary-color);
    margin-bottom: 1rem;
    /* Ensure the container height doesn't jump during typing */
    min-height: 4rem; 
  }

  .cursor {
    display: inline-block;
    width: 10px;
    height: 3.1rem;
    background-color: var(--primary-color);
    animation: blink 1s step-end infinite;
    vertical-align: bottom;
    margin-left: 8px;
  }

  @keyframes blink {
    from, to {
      background-color: transparent;
    }
    50% {
      background-color: var(--primary-color);
    }
  }

  .bio {
    font-size: 1.1rem;
    line-height: 1.6;
    max-width: 600px;
    margin: 1.5rem auto;
  }

    .projects-button {
    display: inline-block;
    font-size: 1rem;
    padding: 12px 28px;
    margin-top: 1.5rem;
    border: 2px solid var(--primary-color);
    color: var(--primary-color);
    background-color: transparent;
    text-decoration: none;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;
  }

  .projects-button:hover {
    background-color: var(--primary-color);
    color: var(--background-color);
  }

  .github-button {
    display: inline-block;
    font-size: 0.9rem; /* Smaller font size */
    padding: 8px 15px; /* Reduced padding */
    border: none; /* No border */
    color: var(--primary-color); /* Text color */
    background-color: transparent; /* Transparent background */
    text-decoration: none;
    cursor: pointer;
    transition: color 0.3s; /* Transition for color only */
    margin-bottom: 0.5rem; /* Reduced margin */
  }

  .github-button:hover {
    color: #888; /* Slightly darker on hover */
    background-color: transparent; /* Keep transparent */
  }

  .buttons-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 1.5rem;
  }

  @media (max-width: 600px) {
    .title {
      font-size: 2.2rem;
      min-height: 3rem;
    }
    .cursor {
      height: 2.3rem;
    }
    .bio {
      font-size: 1rem;
    }
  }
</style>
