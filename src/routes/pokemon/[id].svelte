<script context="module">
	import { getPokemonById } from '../../stores/pokeMart';
	export async function load({ page }) {
		const id = page.params.id;
		const poke = await getPokemonById(id);
		return {
			props: { poke }
		};
	}
</script>

<script>
	export let poke;
	let types = poke.types.map((data) => data.type.name);
	let moves = poke.moves.map((data) => data.move.name);
	let random;
	let moveset = moves.slice(0, 4);
	console.log(moveset);
</script>

<svelte:head>
	<title>Pokedex - {poke.name}</title>
</svelte:head>

<div class="flex flex-col items-center">
	<h1 class="text-4xl text-center my-8 uppercase">{poke.name}</h1>
	<p>
		Type: {#each types as type}<strong class="uppercase">{type}&nbsp;</strong> {/each} | Height:
		<strong>{poke.height}</strong>
		| Weight: <strong>{poke.weight}</strong>
	</p>
	<div class="h-25 grid grid-flow-col grid-rows-2">
		{#each moveset as move}
			<div>{move}</div>
		{/each}
	</div>
	<img class="card-image" src={poke.sprites['front_default']} alt={poke.name} />
</div>
