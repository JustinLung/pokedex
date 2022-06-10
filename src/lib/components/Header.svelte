<script>
  import SearchPokemon from '$lib/components/SearchPokemon.svelte'
</script>

<header>
  <a veltekit:prefetch href="/">Pokedex</a>
  <SearchPokemon />
</header>

<style>
  header {
    text-align: center;
  }

  a {
    font-size: 2rem;
    font-weight: bold;
  }
</style>
