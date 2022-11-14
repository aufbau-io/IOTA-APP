<script>
	import '../../app.css';
	import Header from '$lib/components/header/header.svelte';
</script>

<svelte:head>
	<title>IOTA</title>
</svelte:head>

<div class="container">
	<div class="bg" />
</div>

<!-- <Header /> -->
<main>
	<slot />
</main>

<style>
	.container {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		overflow: hidden;
	}

	.bg {
		width: 400%;
		height: 400%;
		background: linear-gradient(0.33turn, #f6a192, #ffd9df, #f6c492, #f6a192);
		background-size: 100% 100%;
		animation: GradientBackground 50s ease infinite;
	}

	@keyframes GradientBackground {
		0% {
			transform: translate(0, -50%);
		}
		50% {
			transform: translate(-75%, 0);
		}
		100% {
			transform: translate(0, -50%);
		}
	}
</style>
