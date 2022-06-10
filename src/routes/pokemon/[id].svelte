<script context="module">
  const baseURL = 'https://pokeapi.co/api/v2'
  const pokemonEndpoint = 'pokemon'
  const speciesEndpoint = 'pokemon-species'

  export async function load({ fetch, params }) {
    const res = await fetch(`${baseURL}/${pokemonEndpoint}/${params.id}`)
    const pokemon = await res.json()
    console.log(pokemon)
    if (res.ok) {
      return {
        props: { pokemon },
      }
    }
  }
</script>

<script>
  import { fly } from 'svelte/transition'
  export let pokemon
</script>

<div
  class="header"
  in:fly={{ y: -10, duration: 500, delay: 500 }}
  out:fly={{ y: -10, duration: 500 }}
>
  <img
    src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/{pokemon.id}.png"
    alt="Pokemon - {pokemon.name}"
  />
</div>

<section
  in:fly={{ y: -10, duration: 500, delay: 500 }}
  out:fly={{ y: -10, duration: 500 }}
>
  <h1>{pokemon.name}</h1>
  <div class="types-container">
    <p>{pokemon.types[0].type.name}</p>
  </div>
  <div class="weight-height-container">
    <section>
      <h2>Height</h2>
      <p>{pokemon.height / 10} M</p>
    </section>
    <section>
      <h2>Weight</h2>
      <p>{pokemon.weight / 10} KG</p>
    </section>
  </div>
  <section class="abilities-container">
    <h2>Abilities</h2>
    <div>
      <p>{pokemon.abilities[0].ability.name}</p>
      <p>{pokemon.abilities[1].ability.name}</p>
    </div>
  </section>
</section>

<style>
  .header {
    background-color: var(--color-sapphire);

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;

    margin-top: 2em;
  }

  .header img {
    max-width: 90%;
  }

  h1 {
    font-size: 1.5rem;
    text-align: center;
    padding: 1rem 0;
  }

  h2 {
    font-size: 1.44rem;
  }

  p {
    font-size: 1.1rem;
  }

  .types-container p,
  .weight-height-container p,
  .abilities-container p {
    padding: 0.5em 1.5em;
    margin: 0;

    background-color: var(--color-white);
    border: 2px solid var(--color-white);
    box-shadow: #ededed 0 10px 10px;
    border-radius: 0.5em;
  }

  .types-container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 1em;
    padding: 0 0 1rem;
  }

  .weight-height-container {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 1em;
    padding: 0 0 1rem;
  }

  .weight-height-container > section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .weight-height-container section > h2:first-child {
    font-weight: bold;
  }

  .abilities-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .abilities-container > div {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 1em;
  }
</style>
