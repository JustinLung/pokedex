<script context="module">
  const baseURL = 'https://pokeapi.co/api/v2'
  const pokemonListEndpoint = 'pokemon/?limit=898'

  export async function load({ params, fetch, session, stuff }) {
    const res = await fetch(`${baseURL}/${pokemonListEndpoint}`)
    const data = await res.json()
    if (res.ok) {
      return {
        props: { pokemons: data.results },
      }
    }
  }
</script>

<script>
  import PokemonList from '$lib/components/PokemonList.svelte'
  import ScrollToTop from '$lib/components/ScrollToTop.svelte'
  import { fly } from 'svelte/transition'

  export let pokemons
</script>

<div
  class="pokemon-list"
  in:fly={{ y: -10, duration: 500, delay: 500 }}
  out:fly={{ y: -10, duration: 500 }}
>
  <PokemonList {pokemons} />
</div>
<ScrollToTop />

<style>
  .pokemon-list {
    margin: 0 auto;
    max-width: 65em;
    padding: 1.8em;
    display: flex;
    flex-flow: wrap row;
    justify-content: center;
    align-items: center;
  }

  @media (min-width: 40em) {
    .pokemon-list {
      gap: 2em;
    }
  }
</style>
