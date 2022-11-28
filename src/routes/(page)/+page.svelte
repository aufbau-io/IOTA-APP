<script>
	import FormField from '$lib/components/common/formField.svelte';
	import Button from '$lib/components/common/button.svelte';
</script>

<main>
	<section>
		<div class="row">
			<p class="field" />
		</div>
		<div class="row">
			<h4 class="title">IOTA</h4>
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
				<p class="field">username</p>
				<input type="text" />
			</div>
			<div class="row">
				<p class="field">password</p>
				<input type="password" />
			</div>
			<div class="row right muted">
				<Button text="log in" />
			</div>
		</form>
	</section>
</main>

<style>
	main {
		width: 100%;
		margin-top: 320px;
		height: 320px;
		background: var(--background);

		border-top: solid 1px var(--primary-50);
		border-bottom: solid 1px var(--primary-50);

		padding: 40px 30px;
	}

	section {
		padding: 40px;

		max-width: 600px;
		margin: auto;
	}

	.shadow {
		position: absolute;
		top: 50%;
		left: 50%;
		z-index: -2;

		height: 100%;
		width: 100%;
		transform: translate(calc(-50% - 12px), calc(-50% - 12px));
		background: var(--background);
		border: solid 1px var(--primary);
	}

	.shift {
		transform: translate(-12px, -6px);
	}

	.muted {
		color: var(--primary-50);
	}

	input {
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;

		border-radius: 0;
		background: none;
		border-bottom: solid 1px var(--primary-50);
		margin-bottom: 10px;
		width: 65%;
	}
	input:focus {
		outline: none;
	}

	h4 {
		font-family: nb-architekt;
		font-weight: 500;
		letter-spacing: 2.4px;
	}

	.row {
		width: 100%;
		display: flex;
		align-items: center;
	}

	.row.right {
		justify-content: end;
		margin-top: 10px;
	}

	.field {
		width: 35%;
		display: inline;
	}

	.title {
		width: 35%;
		display: inline;
	}

	form {
		padding-bottom: 10px;
	}

	@media only screen and (max-width: 768px) {
		main {
			padding: 32px 20px;
			margin: auto;
			height: 240px;
		}
		section {
			padding: 8px 0;
		}
		form {
			padding-bottom: 0;
		}
	}
</style>
