<script context="module">
	// const API_ENDPOINT = process.env['API_ENDPOINT_BEERS'];
	const API_ENDPOINT = 'https://api.punkapi.com/v2/beers/'

	export async function load({ fetch, params }) {
        const { id } = params
		const res = await fetch(`${API_ENDPOINT}${id}`);
        const data = await res.json()

		return {
			props: {
				beer: data[0]
			}
		};
	}
</script>

<script>
	export let beer;
    console.log(beer)
</script>

<div>
	<pre>{JSON.stringify(beer, null, 2)}</pre>
</div>
