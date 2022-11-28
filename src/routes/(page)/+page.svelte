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
			<h5 class="xl">IOTA - v:0.0.1</h5>
			<div />
		</div>
		<div class="row">
			<p class="field" />
		</div>
		<br />

		<form>
			<div class="row">
				<h6 class="field">username</h6>
				<input type="text" />
			</div>
			<div class="row">
				<h6 class="field">password</h6>
				<input type="password" />
			</div>
			<div class="row">
				<div class="field" />
				<div class="long">
					<Button size="lrg" text="log in" fluid={true} />
				</div>
			</div>
		</form>
	</section>
</main>

<style>
	main {
		width: 100%;
		margin-top: 320px;
		height: 360px;
		background: var(--background);

		border-top: solid 1px var(--primary-50);
		border-bottom: solid 1px var(--primary-50);

		font-family: nb-architekt, sans-serif;
		font-weight: 400;

		padding: 40px 30px;
	}

	section {
		padding: 32px;
		max-width: 600px;
		margin: auto;
	}

	.long {
		width: 75%;
		margin-top: 16px;
	}

	input {
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;

		border-radius: 0;
		background: none;
		border-bottom: solid 1px var(--primary-50);
		font-family: untitled-sans;
		font-size: 18px;
		margin-bottom: 16px;

		width: 75%;
	}
	input:focus {
		outline: none;
	}

	h5 {
		font-weight: 500;
		letter-spacing: 2px;
	}

	.row {
		width: 100%;
		display: flex;
		align-items: flex-start;
	}

	.field {
		width: 25%;
		display: inline;
	}

	.title {
		width: 25%;
		display: inline;
	}

	form {
		padding-bottom: 10px;
	}

	@media only screen and (max-width: 768px) {
		main {
			padding: 32px 20px;
			margin: auto;
			height: 280px;
		}
		section {
			padding: 10px 8px;
		}
		form {
			padding-bottom: 0;
		}
	}
</style>
