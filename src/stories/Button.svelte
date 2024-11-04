<script>
	/**
	 * @typedef {Object} Props
	 * @property {boolean} [primary] Is this the principal call to action on the page?
	 * @property {'small' | 'medium' | 'large'} [size] How large should the button be?
	 * @property {string} label Button contents
	 * @property {any} children Button contents
	 * @property {() => void} [onClick] The onclick event handler
	 */

	/** @type {Props} */
	const { primary = false, size = 'medium', label, children, onClick } = $props();
</script>

<button
	type="button"
	class={['button', `button--${size}`].join(' ')}
	class:button--primary={primary}
	class:button--secondary={!primary}
	onclick={onClick}
>
	{@render children()}
</button>

<style>
	button {
		font-family: inherit;
		background-color: var(--figma-color-bg-brand);
		color: var(--figma-color-text-onbrand);
		border: 0;
	}
	button:hover {
		background-color: var(--figma-color-bg-brand-secondary);
		transition: ease-out 0.1s background-color;
	}
	.button--primary {
		background-color: var(--figma-color-bg-brand);
		color: var(--figma-color-text-onbrand);
	}
	.button--secondary {
		background-color: var(--figma-color-bg-brand-secondary);
		color: var(--figma-color-text-onbrand-secondary);
	}
	.button--small {
		font-size: 12px;
		padding: 10px 16px;
		border-radius: var(--radius-small);
	}
	.button--medium {
		font-size: 14px;
		padding: 11px 20px;
		border-radius: var(--radius-medium);
	}
	.button--large {
		font-size: 16px;
		padding: 12px 24px;
		border-radius: var(--radius-large);
	}
</style>
