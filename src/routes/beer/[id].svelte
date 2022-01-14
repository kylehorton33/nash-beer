<script context="module">
	//const API_ENDPOINT = process.env['API_ENDPOINT_BEERS'];
	const API_ENDPOINT = 'https://api.punkapi.com/v2/beers/'; // temporary API to mockup data

	export async function load({ fetch, params }) {
		const { id } = params;
		const res = await fetch(`${API_ENDPOINT}${id}`);
		const data = await res.json();

		return {
			props: {
				beer: data[0]
			}
		};
	}
</script>

<script>
	export let beer;
</script>

<article class="text-center m-4">
	<header class="my-4">
		<h1 class="title text-5xl">{beer.name}</h1>
		<div class="specifications my-2">
			{#each ['abv', 'ibu', 'srm'] as spec}
				<span>{beer[spec]} {spec} / </span>
			{/each}
		</div>
		<div class="header-content grid grid-cols-2 gap-4 flex items-center">
			<p class="text-xl">{beer.description}</p>
			<div class="img-container flex justify-center">
				<img class="object-contain h-96" src={beer.image_url} alt={`Image of ${beer.name}`} />
			</div>
		</div>
	</header>
	<hr />
	<div class="content grid md:grid-cols-2 my-4">
		<div class="ingredients mx-8">
			<h2 class="text-3xl my-3">Malt</h2>
			<ul class="list-disc text-left">
				{#each beer.ingredients.malt as m}
					<li>{m.amount.value} {m.amount.unit} - {m.name}</li>
				{/each}
			</ul>
			<h2 class="text-3xl my-3">Hops</h2>
			<ul class="list-disc text-left">
				{#each beer.ingredients.hops as h}
					<li>{h.amount.value} {h.amount.unit} - {h.name} (Added at {h.add} of boil)</li>
				{/each}
			</ul>
			<h2 class="text-3xl my-3">Yeast</h2>
			<ul class="list-disc text-left">
				<li>{beer.ingredients.yeast}</li>
			</ul>
		</div>
		<div class="directions">
			<h2 class="text-3xl my-3">Method</h2>
			<ol class="list-decimal text-left mx-4">
				{#each beer.method.mash_temp as mash}
					<li>Mash at {mash.temp.value} for {mash.duration} minutes</li>
				{/each}
				<li>Ferment at {beer.method.fermentation.temp.value}</li>
				<li>*TIP: {beer.brewers_tips}</li>
			</ol>
		</div>
	</div>
</article>
