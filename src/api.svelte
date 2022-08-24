<script>
// @ts-nocheck

  import { onMount } from "svelte";

  let pokemon = [];
  let stats = [];

  let offset = 0;

  onMount(getPokemon);

  function previousPage() {
    if (offset <= 9) {
      offset = 0;
      getPokemon();
    } else {
      offset -= 1;
      getPokemon();
    }
  }

  function nextPage() {
    offset += 1;
    getPokemon();
  }

  const returnNade = () => '';

  async function getPokemon() {
    const response = await fetch(
      `https://pokeapi.co/api/v2/pokemon?limit=1&offset=${offset}`
    );
    const data = await response.json();
    pokemon = data.results;
  }

  async function getPokemonStats(pokemonURL) {
    const response = await fetch(pokemonURL);
    const data = await response.json();
    stats = data.stats;
  }
</script>
<ol>
{#each pokemon as singlePokemon}
  {returnNade(  getPokemonStats(singlePokemon.url) )}
  
  <li id="pokemon">
    <span>
    {singlePokemon.url.replace('https://pokeapi.co/api/v2/pokemon/','').replace('/','')}. {singlePokemon.name}
  </span>
    <ul>
      <li>
        ID = #{singlePokemon.url.replace('https://pokeapi.co/api/v2/pokemon/','').replace('/','')}
      </li>
      <li>
        Basestats:
      </li>
        <ul>
        {#each stats as stat}
          <li>
            {stat.stat.name} = {stat.base_stat}
          </li>
          {/each}
        </ul>
    </ul>
  </li>
{/each}
</ol>
<button on:click={previousPage}>prev</button>
<button on:click={nextPage}>next</button>

<style>
  #pokemon::marker{
    content: '';
  }
</style>
