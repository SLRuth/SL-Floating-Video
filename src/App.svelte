<script>
  import FloatingVideo from "./FloatingVideo.svelte";
  export let name;
  let url = null;

  function activatePip() {
    console.log("activatePip");
    url = null;
    url = "https://www.youtube.com/embed/QgD5A2v3cp0";
  }
</script>

<main>
  <h1>Hello {name}!</h1>
  <p>
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>
  <button on:click={activatePip}>Test Floating Video</button>
  <FloatingVideo src={url} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
