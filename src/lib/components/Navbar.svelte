<script>
  import routes from '$lib/Routes.js';
  import Hamburger from './Hamburger.svelte';

  export let path;

  export let opened = false;
</script>

<div class={opened ? "navbar-closed" : "navbar-opened"}>
  <div class="button-container">
    <div class="burger">
      <Hamburger bind:open={opened} />
    </div>
    <div class="buttons">
      {#each routes as route}
        {#if path === route.href}
          <a class="button selected" href={route.href}>
            {route.label}
          </a>
        {:else}
          <a class="button" href={route.href}>
            {route.label}
          </a>
        {/if}
      {/each}
    </div>
  </div>
  <div class="burger-buttons">
    {#each routes as route}
      {#if path === route.href}
        <a class="button selected" href={route.href}>
          {route.label}
        </a>
      {:else}
        <a class="button" href={route.href}>
          {route.label}
        </a>
      {/if}
    {/each}
  </div>
</div>

<style>
  .navbar-opened {
    display: flex;
    justify-content: flex-end;
    margin-right: 5rem;
  }

  .button-container {
    display: flex;
    justify-content: flex-end;
    margin-right: 5rem;
  }

  .buttons {
    position: absolute;
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 100px;
    width: 100%;
    text-align: center;
    margin-top: 20px;
  }

  .buttons :global(a) {
    color: var(--fgColor);
  }

  .buttons .button {
    padding: 0;
    display: block;
    cursor: pointer;
    text-decoration: none;
    margin: 10px;
    font-size: 20px;
  }

  .button:hover {
    transition: color 0.4s ease-in-out;
    color: var(--hoverColor);
  }

  @media (min-width: 900px) {
    .burger {
      display: none !important;
    }

    .burger-buttons .button {
      display: none !important;
    }
  }

  @media (max-width: 900px) {

    .burger-buttons .button {
      display: flex;
      text-decoration: none;
      align-items: center;
      margin: 10 auto;
      padding: 10 auto;
      color: var(--fgColor);
    }

    .burger-buttons {
      display:none;
    }

    .burger {
      display: none;
    }

	  .button {
		  display: none;
		  justify-content: space-between;
		  align-items: center;
		  font-weight: 500;
	  }
  }
</style>
