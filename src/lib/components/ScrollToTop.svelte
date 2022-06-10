<script>
  import { slide } from 'svelte/transition'
  let y
</script>

<svelte:window bind:scrollY={y} />
{#if y >= 80}
  <a href="#" transition:slide
    ><img src="/assets/icons/scroll-icon.png" alt="Scroll to Top" /></a
  >
{/if}

<style>
  a {
    position: fixed;
    bottom: 1em;
    right: 1em;

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

  a > img {
    width: 70%;
  }
</style>
