<script>
	import Arrow from './arrow.svelte';
</script>

<svelte:head>
	<title>404 not found</title>
</svelte:head>
<section>
	<div class="message">
		<h2>404 error.</h2>
	</div>

	<!--div class="nav">
		<a href="/" class="top-border">
			<h2>00</h2>
			<h1>MY DAY</h1>
			<Arrow direction="up" />
		</a>
		<a href="/" class="top-border">
			<h2>01</h2>
			<h1>ACCOUNT</h1>
			<Arrow direction="left" />
		</a>
	</div-->
</section>

<style>
	section {
		display: flex;
	}

	section div {
		height: 100vh;
		align-items: center;
	}

	.message {
		margin: auto auto;
		height: auto;
		width: auto;
	}

	section .message h2 {
		font-weight: 300;
	}

	section .message p {
		font-weight: 300;
		line-height: 150%;
		padding-top: 1em;
	}

	.nav {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		padding: 40px 40px 40px 0;
		min-width: 50vw;
	}

	.nav a {
		display: flex;
		width: 100%;
		height: 100%;
		margin: auto;
		border-bottom: solid var(--background) 2px;
		padding: 0 1rem;

		align-items: center;
		stroke: var(--background);
	}

	.nav h2 {
		font-size: 64px;
		width: 2em;
	}

	.nav h1 {
		font-size: 64px;
		margin-right: auto;
	}

	.nav a:hover {
		background: var(--background);
		color: var(--green);
		stroke: var(--green);
	}

	.nav a.top-border {
		border-top: solid var(--background) 2px;
	}

	@media only screen and (max-width: 976px) {
		section {
			flex-direction: column;
			height: 100vh;
		}

		section div {
			height: auto;
		}

		.nav {
			min-width: calc(100% - 40px);
			padding: 40px 20px;
			height: 60vh;
		}
	}

	@media only screen and (max-width: 768px) {
		.message {
			margin: auto auto;
			padding: 0 2rem;
		}

		.message h2 {
			font-size: 33px;
		}

		.nav a {
			height: 12vh;
		}

		.nav h2 {
			font-size: 32px;
		}

		.nav h1 {
			font-size: 40px;
		}
	}
</style>
