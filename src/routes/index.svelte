<script>
  import {pokemon} from "../stores/pokeMart"
</script>

<svelte:head>
	<title>Svelte Kit Pokemon App</title>
</svelte:head>

<h1 class="text-4xl text-center my-8 uppercase">Sevlte kit Pokedex</h1>

{#each $pokemon as poke}
  <p>{poke.name}</p>
{/each}
