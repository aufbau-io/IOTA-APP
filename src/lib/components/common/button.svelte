<script>
	export let text = 'Button';
	export let size = '';
	export let active = false;
	export let disabled = false;
	export let fluid = false;
	export let alt = false;
	export let style = '';

	let classString = 'btn ' + size + ' ' + style;
	if (fluid) {
		classString = classString.concat(' ', 'fluid');
	}
	if (alt) {
		classString = classString.concat(' ', 'alt');
	}
	if (disabled) {
		classString = classString.concat(' ', 'disabled');
	} else {
		if (active) {
			classString = classString.concat(' ', 'active');
		}
	}
</script>

<button class={classString}>
	<p>{text}</p>
</button>

<style>
	button {
		text-transform: none;
		border: solid 1px var(--accent);
		background: var(--black);
		color: var(--accent);
		padding: 8px;
		border-radius: 24px;
		font-family: nb-architekt;
		letter-spacing: 0.2em;
	}

	button:hover,
	.active {
		color: var(--black);
		background: var(--button-alt);
		border: solid 1px var(--primary);
	}

	button:active {
		background: var(--black);
		color: var(--accent);
		border: solid 1px var(--accent);
	}

	button.fluid {
		width: 100%;
	}

	button.alt {
		background: var(--background-fallback);
		color: var(--primary);
		border: solid 1px var(--primary);
	}

	button.alt:hover {
		background: var(--primary);
		color: var(--background-fallback);
	}

	button.alt:active {
		color: var(--primary);
		background: none;
	}

	.disabled,
	.disabled:hover {
		opacity: 0.2;
		cursor: default;
		color: var(--accent);
		background: var(--black);
		border: solid 1px var(--accent);
	}
</style>
