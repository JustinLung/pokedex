<script>
  let inputValue = ''
  import { goto } from '$app/navigation'

  function submitSearch() {
    goto('/pokemon/' + inputValue)
  }
</script>

<form on:submit|preventDefault={submitSearch}>
  <input
    bind:value={inputValue}
    name="search_pokemon"
    class="search"
    type="text"
    placeholder="✨ Search Pokemon..."
    autocomplete="off"
  />
  <button><img src="/assets/icons/search.svg" alt="Search Icon" /></button>
</form>

<style>
  form {
    width: 100%;
    border-radius: 1.5em;
    box-shadow: var(--light-smoke) 0 10px 10px;
    background-color: var(--color-white);

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;

    padding: 0.8em 0;
    margin-top: 0.5em;
  }

  input {
    border: none;
    outline: none;
    font-size: 18px;
    flex: 1;
    margin-left: 1.5em;
    font-family: 'Ubuntu', sans-serif;
  }

  button {
    all: unset;
    margin-right: 1.5em;
    background-color: var(--color-teal-blue);
    height: 2.5em;
    width: 2.5em;
    border-radius: 10px;
    cursor: pointer;
    box-shadow: #00709088 5px 5px 15px;
    color: var(--color-white);
    font-size: 18px;

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
</style>
