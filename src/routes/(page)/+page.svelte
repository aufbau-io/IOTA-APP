<script>
		import { onMount } from 'svelte';
	let Geometry;

	onMount(async () => {
		const module = await import('$lib/components/geometry/Geometry.svelte');
		Geometry = module.default;
	});
</script>

<main>
	<div class="sidebar">
		<p>iota: mental state tracking</p>
		<p>version: 0.0.1</p>
		<br>
		<p>username:</p>
		<p>password:</p>
	</div>
	<svelte:component this={Geometry} />
</main>

<style>
	main {
		position: relative;
		height: calc(100vh - 51px);
		overflow: hidden;
		display: flex;
	}

	.sidebar {
		width: calc(100vw / 4);
		border-right: solid 1px var(--white-50);

		padding: 20px;
	}

	.geometry {
		width: calc(100vw / 4 * 3);
	}
</style>
