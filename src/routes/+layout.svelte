<script>
	import '../app.css';
	import { onMount } from 'svelte';

	let screenType;
	onMount(async () => {
		// ---------------------------------------------------------------------------
		// HEIGHT
		// ---------------------------------------------------------------------------

		// First we get the viewport height and we multiple it by 1% to get a value for a vh unit
		let vh = window.innerHeight * 0.01;
		// Then we set the value in the --vh custom property to the root of the document
		document.documentElement.style.setProperty('--vh', `${vh}px`);

		window.addEventListener('resize', () => {
			// We execute the same script as before
			let vh = window.innerHeight * 0.01;
			document.documentElement.style.setProperty('--vh', `${vh}px`);
		});

		// ---------------------------------------------------------------------------
		// SCREEN
		// ---------------------------------------------------------------------------
		const ua = navigator.userAgent;
		if (/(tablet|ipad|playbook|silk)|(android(?!.*mobi))/i.test(ua)) {
			// tablet
			screenType = 1;
		} else if (
			/Mobile|Android|iP(hone|od)|IEMobile|BlackBerry|Kindle|Silk-Accelerated|(hpw|web)OS|Opera M(obi|ini)/.test(
				ua
			)
		) {
			// phone
			screenType = 2;
		} else {
			//laptop
			screenType = 3;
		}
	});
</script>

<svelte:head>
	<title>IOTA</title>

	<link
		rel="preload"
		as="font"
		href="/fonts/test-untitled-sans-light.woff2"
		type="font/woff2"
		crossorigin="anonymous"
	/>

	<link
		rel="preload"
		as="font"
		href="/fonts/NB-Architekt-Pro-Regular.woff"
		type="font/woff"
		crossorigin="anonymous"
	/>
</svelte:head>

<!-- {#if screenType == 1 || screenType == 2} -->
{#if false}
	<div id="phoneBlock"><p class="sml">wip, use desktop</p></div>
{:else}
	<slot />
{/if}

<style>
	#phoneBlock {
		position: absolute;
		top: 0;
		left: 0;

		display: flex;
		align-items: center;
		justify-content: center;

		height: 100vh;
		height: calc(var(--vh, 1vh) * 100);

		width: 100vw;
		background: var(--background);
		z-index: 1000;
	}

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
