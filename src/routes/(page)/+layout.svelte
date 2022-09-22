<script>
	import '../../app.css';
	import { onMount } from 'svelte';
	let Geometry;

	import Header from '$lib/components/header/header.svelte';

	onMount(async () => {
		const module = await import('$lib/components/geometry/Geometry.svelte');
		Geometry = module.default;
	});
</script>

<svelte:head>
	<title>IOTA</title>
</svelte:head>

<!--svelte:component this={Geometry} /-->

<Header />
<main>
	<slot />
</main>

<style>
</style>
