<script>
	import '../../app.css';
	import { onMount } from 'svelte';
	import Header from '$lib/components/header/header.svelte';
	let Geometry;

	onMount(async () => {
		const module = await import('$lib/components/geometry/geometry.svelte');
		Geometry = module.default;
	});
</script>

<Header />
{#key Geometry}
	<svelte:component this={Geometry} />
{/key}
<main>
	<slot />
</main>

<style>
	main {
		position: absolute;
		top: 0;

		width: 100vw;
		height: 100%;

		display: flex;
		justify-content: center;
	}
</style>
