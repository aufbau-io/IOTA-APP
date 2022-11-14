<script>
	import Nav from './nav.svelte';
	import { darkMode } from '$lib/store/store';
	// stub data out
	const navItems = [
		{
			name: 'DATA',
			href: '/'
		},
		{
			name: 'ACCOUNT',
			href: '/account'
		}
	];

	let toggleDarkMode = () => {
		darkMode.set(!$darkMode);
	};
</script>

<header>
	<div />
	<!-- <a href="/"><h6>iota</h6> </a> -->
	<!-- <div />
	<div on:click={() => toggleDarkMode()} class="darkMode">
		<p class:selected={$darkMode == true}>day</p>
		<p class="selected">/</p>
		<p class:selected={$darkMode == false}>night</p>
	</div> -->

	<Nav {navItems} />
</header>

<style>
	header {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;

		z-index: 20;

		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0 20px;
		height: 50px;
		border-bottom: solid 1px var(--primary-50);
		user-select: none;
	}

	.darkMode {
		display: flex;
	}

	.darkMode p {
		line-height: 110%;
		font-weight: 400;
		letter-spacing: 0.05em;
		padding: 10px;
		cursor: pointer;
		opacity: 0.4;
	}

	.darkMode p.selected {
		opacity: 1;
	}
</style>
