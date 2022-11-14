<script>
	import { onMount } from 'svelte';
	import FormField from '$lib/components/common/formField.svelte';
	import Button from '$lib/components/common/button.svelte';
	// let Geometry;

	// onMount(async () => {
	// 	const module = await import('$lib/components/geometry/geometry.svelte');
	// 	Geometry = module.default;
	// });
</script>

<main>
	<div class="row">
		<p class="field" />
	</div>
	<div class="row">
		<h4 class="field">IOTA</h4>
		<div>
			<p>mental state tracking</p>
			<p class="mono">version: 0.0.1</p>
		</div>
	</div>
	<div class="row">
		<p class="field" />
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
	<!-- <svelte:component this={Geometry} /> -->
</main>

<style>
	main {
		position: relative;
		overflow: hidden;

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

		border-radius: 0;
		background: none;
		border-bottom: solid 1px var(--primary);
		margin-bottom: 10px;
		width: 65%;
	}
	input:focus {
		outline: none;
	}

	h4 {
		letter-spacing: 1px;
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
		main {
			padding: 20px;
		}
		form {
			padding-bottom: 0;
		}
	}
</style>
