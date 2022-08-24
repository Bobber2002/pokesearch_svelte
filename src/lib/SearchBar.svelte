<script>
  let query = "";

  let singlePokemon;

  async function searchPokemon() {
    const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${query}`);
    singlePokemon = await response.json();
  }
</script>

<form on:submit|preventDefault={searchPokemon}>
  <input
    type="text"
    name="pokemon_search"
    id="pokemon_search"
    placeholder="Search for a Pokemon"
    bind:value={query}
  />
</form>
{#if singlePokemon}
  {singlePokemon.name} - #{singlePokemon.order}
{/if}
