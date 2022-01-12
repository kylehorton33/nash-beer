<script context="module">
	// const API_ENDPOINT = process.env['API_ENDPOINT_BEERS'];
	const API_ENDPOINT = 'https://api.punkapi.com/v2/beers/'

	export async function load({ fetch }) {
		const res = await fetch(`${API_ENDPOINT}`);
		return {
			props: {
				loadedBeers: await res.json()
			}
		};
	}
</script>

<script>
	import BeerCard from '$lib/components/BeerCard.svelte';
	export let loadedBeers;
</script>

<div class="hero h-96 bg-base-200">
	<div class="text-center hero-content">
		<div class="">
			<h1 class="mb-5 text-5xl font-bold">Beer Page</h1>
			{#if loadedBeers}
				<div class="grid grid-cols-2 md:grid-cols-3 gap-4">
					{#each loadedBeers as beer}
						<BeerCard {beer} />
					{/each}
				</div>
			{:else}
				<p class="mb-5">Out of beer...</p>
			{/if}
		</div>
	</div>
</div>
