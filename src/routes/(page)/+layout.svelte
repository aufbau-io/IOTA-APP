<script>
	import '../../app.css';
	import { onMount } from 'svelte';
	// import Header from '$lib/components/header/header.svelte';
	let Geometry;

	onMount(async () => {
		const module = await import('$lib/components/geometry/geometry.svelte');
		Geometry = module.default;
	});
</script>

<svelte:head>
	<title>IOTA</title>
</svelte:head>

<!-- <Header /> -->
<svelte:component this={Geometry} class="geometry" />
<main>
	<slot />
</main>

<style>
	main {
		width: 100vw;
		height: 100%;

		display: flex;
		justify-content: center;
	}

	.geometry {
		position: absolute;
		top: 0;
		left: 0;
		z-index: -10;
	}
</style>
