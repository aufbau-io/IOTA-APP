<script>
	import { user } from '$lib/store/sessionStore';
	import { page } from '$app/stores';

	let loggedIn = false;

	export let navItems = [];
	export async function load() {
		return {
			props: {
				navItems
			}
		};
	}
</script>

<nav>
	{#if loggedIn}
		{#each navItems as navItem}
			<a href={navItem.href} class:active={navItem.href === $page.url.pathname}
				>[&nbsp;{navItem.name}&nbsp;]</a
			>
		{/each}
	{:else}
		<a href="https://aufbau.io">EIN AUFBAU DING</a>
	{/if}
</nav>

<style>
	nav a {
		line-height: 110%;
		font-weight: 400;
		letter-spacing: 0.05em;
		padding: 10px;
		cursor: pointer;
		opacity: 0.4;
	}

	nav a:hover {
		opacity: 0.6;
	}

	.active,
	.active:hover {
		opacity: 1;
	}
</style>
