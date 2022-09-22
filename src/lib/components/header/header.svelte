<script>
	import Nav from './nav.svelte';
	import Logo from './logo.svelte';
	import Ticker from './ticker.svelte';
	// stub data out
	const navItems = [
		{
			name: 'MY DAY',
			href: '/'
		},
		{
			name: 'ACCOUNT',
			href: '/account'
		}
	];
</script>

<header>
	<Logo />
	<!--Ticker /-->
	<Nav {navItems} />
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0 40px;
		height: 50px;
		border-bottom: solid 1px var(--black);
		user-select: none;
	}
</style>
