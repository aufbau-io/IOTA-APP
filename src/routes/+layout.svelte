<script>
	import '../app.css';
	import { onMount } from 'svelte';
	import { screenType, darkMode } from '$lib/store/store';

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
			screenType.set(2);
		} else if (
			/Mobile|Android|iP(hone|od)|IEMobile|BlackBerry|Kindle|Silk-Accelerated|(hpw|web)OS|Opera M(obi|ini)/.test(
				ua
			)
		) {
			// phone
			// darkMode.set(false);
			// document.querySelector(':root').classList.toggle('dark-mode');
			screenType.set(3);
		} else {
			//laptop
			screenType.set(1);
		}
	});
</script>

<svelte:head>
	<title>IOTA</title>

	<link
		rel="preload"
		as="font"
		href="/fonts/NB-Architekt-Pro-Light.woff"
		type="font/woff"
		crossorigin="anonymous"
	/>

	<link
		rel="preload"
		as="font"
		href="/fonts/NB-Architekt-Pro-Regular.woff"
		type="font/woff"
		crossorigin="anonymous"
	/>

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
		href="/fonts/test-untitled-sans-regular.woff2"
		type="font/woff2"
		crossorigin="anonymous"
	/>
</svelte:head>

<!-- {#if screenType == 1 || screenType == 2} -->
{#if false}
	<div id="phoneBlock"><p class="sml">wip, use desktop</p></div>
{:else if $screenType}
	<main><slot /></main>
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

		width: 100%;
		background: var(--background);
		z-index: 1000;
	}

	main {
		overflow: hidden;
		height: 100%;
		width: 100%;
	}
</style>
