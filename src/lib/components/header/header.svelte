<script>
	import Nav from './nav.svelte';
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
</script>

<header>
	<a href="/"><h6>iota</h6> </a>
	<Nav {navItems} />
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0 20px;
		height: 50px;
		border-bottom: solid 1px var(--white-50);
		user-select: none;
	}
</style>
