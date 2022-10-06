<script>
	import { onMount } from 'svelte';
	import FormField from '$lib/components/common/formField.svelte';
	import Button from '$lib/components/common/button.svelte';
	let Geometry;

	onMount(async () => {
		const module = await import('$lib/components/geometry/geometry.svelte');
		Geometry = module.default;
	});
</script>

<main>
	<div class="sidebar">
		<p>iota: mental state tracking</p>
		<p>version: 0.0.1</p>
		<br />

		<form>
			<div class="row">
				<p class="field">username:</p>
				<input type="text" />
			</div>
			<div class="row">
				<p class="field">password:</p>
				<input type="password" />
			</div>
			<div class="row right">
				<Button text="log in" />
			</div>
		</form>
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
		width: calc(100vw / 5);
		min-width: 300px;
		border-right: solid 1px var(--white-50);
		display: block;
		padding: 20px;
	}

	.geometry {
		width: calc(100vw / 5 * 4);
	}

	input {
		background: none;
		border-bottom: solid 1px var(--white);
		margin-bottom: 10px;
		width: 60%;
	}
	input:focus {
		outline: none;
	}

	.row {
		width: 100%;
		display: flex;
	}

	.row.right {
		justify-content: end;
		margin-top: 10px;
	}

	.field {
		width: 40%;
		display: inline;
	}

	form {
		padding-bottom: 20px;
	}
</style>
