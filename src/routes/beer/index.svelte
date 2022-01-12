<script context="module">
	const API_ENDPOINT = process.env['API_ENDPOINT'];

	export async function load({ fetch }) {
		const res = await fetch(`${API_ENDPOINT}/beer`);
		return {
			props: {
				loadedBeers: await res.json()
			}
		};
	}
</script>

<script>
	export let loadedBeers;
</script>

<div class="hero h-96 bg-base-200">
	<div class="text-center hero-content">
		<div class="max-w-md">
			<h1 class="mb-5 text-5xl font-bold">Beer Page</h1>
			{#if loadedBeers}
				{#each loadedBeers as beer}
					<p>{beer.name}</p>
				{/each}
			{:else}
				<p class="mb-5">Out of beer...</p>
			{/if}
		</div>
	</div>
</div>
