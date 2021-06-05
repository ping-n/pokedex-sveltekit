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
	<img class="card-image" src={poke.sprites['front_default']} alt={poke.name} />
</div>
