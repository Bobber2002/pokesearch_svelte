<script>
  import ToFButton from "./lib/switch.svelte";
  import Pokemons from "./api.svelte";
  import SearchForm from "./lib/SearchBar.svelte";

  let bool = false;
</script>

<main>
  <div class="wrapper">
    <div class="container">
      {#if bool}
        <h1 class="name">app</h1>
      {/if}
      <ToFButton bind:value={bool} />
    </div>
  </div>
  <SearchForm />
  <Pokemons />
</main>

<style>
  .wrapper {
    background: blue;
    width: 320px;
    height: 48px;
  }

  .container {
    background-color: red;
    display: flex;
    justify-content: space-evenly;
  }
</style>
