<script>
	import { pokemon } from '../stores/pokeMart';
	import PokeCard from '../components/pokeCard.svelte';

	let searchTerm = '';
	let filteredPokemon = [];

	$: {
		if (searchTerm) {
			// search for the pokemon
			filteredPokemon = $pokemon.filter((poke) =>
				poke.name.toLowerCase().includes(searchTerm.toLowerCase())
			);
		} else {
			filteredPokemon = [...$pokemon];
		}
	}
</script>

<svelte:head>
	<title>Svelte Kit Pokemon App</title>
</svelte:head>

<h1 class="text-4xl text-center my-8 uppercase">Sevlte kit Pokedex</h1>
<input
	class="text-lg rounded-md p-4 border-2 w-full"
	bind:value={searchTerm}
	type="text"
	placeholder="Search Pokemon"
/>
<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
	{#each filteredPokemon as poke}
		<PokeCard {poke} />
	{/each}
</div>
