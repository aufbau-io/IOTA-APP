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
		<div class="row">
			<p class="field">iota:</p>
			<p>mental state tracking</p>
		</div>
		<div class="row">
			<p class="field">version:</p>
			<p class="mono">0.0.1</p>
		</div>
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
		overflow: hidden;
		display: flex;
	}

	.sidebar {
		/*
		width: calc(100vw / 5);
		*/
		position: absolute;
		top: 50%;
		left: 50%;

		width: 400px;
		max-width: calc(100vw - 40px);

		transform: translate(-50%, -50%);
		background: var(--background);

		border: solid 1px var(--primary-50);
		padding: 30px;
		box-shadow: 0.5px 0.5px 2px var(--primary-50);
	}

	input {
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;

		background: none;
		border-bottom: solid 1px var(--primary);
		margin-bottom: 10px;
		width: 65%;
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
		width: 35%;
		display: inline;
	}

	form {
		padding-bottom: 10px;
	}

	@media only screen and (max-width: 768px) {
		.sidebar {
			padding: 20px;
		}
	}
</style>
