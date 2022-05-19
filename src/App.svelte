<script>
  export let name;
  export let testValue = true;
  export const runScript = () => {
    
  };
</script>

<main>
  <h1>Hello {name}!</h1>
  {testValue && <button class="test" on:click={runScript}>press me</button>}
  {!testValue && <button class="test" on:click={runScript}>or press me</button>}
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
