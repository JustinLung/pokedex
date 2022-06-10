<script>
  export let pokemons
</script>

{#each pokemons as pokemon, i}
  <a veltekit:prefetch href={`/pokemon/${i + 1}`}>
    <section class="pokemon">
      <p>N° {i + 1}</p>
      <h2>{pokemon.name}</h2>
      <img
        src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/{i +
          1}.png"
        alt="Pokemon {pokemon.name}"
        loading="lazy"
      />
    </section>
  </a>
{/each}

<style>
  section {
    width: 100%;
    background-color: var(--color-white);
    border: 2px solid var(--color-white);
    box-shadow: #ededed 0 10px 10px;
    border-radius: 1.5em;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    margin-bottom: 2em;
  }

  section img {
    max-width: 70%;
  }
</style>
