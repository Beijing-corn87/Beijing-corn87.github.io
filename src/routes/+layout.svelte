<script>
  import "../app.css";
</script>

<main>
  <slot />
</main>

<style>
  :global(:root) {
    --background-color: #121212; /* A softer black */
    --text-color: #e0e0e0;       /* A softer white */
    --primary-color: #ffffff;
    --font-family: 'SF Mono', 'Consolas', 'Menlo', monospace;
  }

  :global(body) {
    background-color: var(--background-color);
    color: var(--text-color);
    font-family: var(--font-family);
    margin: 0;
    padding: 0;
  }

  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    width: 100%;
    text-align: center;
  }
</style>
