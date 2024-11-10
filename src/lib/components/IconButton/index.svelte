<script>
	import Icon from '$lib/components/Icon/index.svelte';
	/**
	 * @typedef {Object} Props
	 * @property {'primary' | 'secondary' | 'tertiary'} [type] Is this the principal call to action on the page?
	 * @property {any} [iconName] The icon itself from the icon library
	 * @property {() => void} [onClick] The onclick event handler
	 * @property {string} [iconChar] The character to display instead of the icon
	 */

	/** @type {Props} */

	const { type = 'primary', onClick, iconName, iconChar } = $props();
</script>

<button type="button" class={['button', `icon-button--${type}`].join(' ')} onclick={onClick}>
	<Icon {iconName} {iconChar} color="currentColor" />
</button>

<style>
	button {
		font-family: inherit;
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-shrink: 0;
		text-align: center;
		border: 0 none;
		padding: 0;
		border-radius: var(--radius-medium);
		height: var(--spacer-xl);
	}
	.icon-button--primary {
		background-color: var(--figma-color-bg-brand);
		color: var(--figma-color-text-onbrand);
		transition: ease-out 0.1s background-color;
		fill: var(--figma-color-icon-onbrand);
	}
	.icon-button--primary:hover {
		background-color: var(--figma-color-bg-brand-secondary);
		transition: ease-out 0.1s background-color;
	}
	.icon-button--secondary {
		background-color: var(--figma-color-bg);
		color: var(--figma-color-text);
		outline: 1px solid transparent;
		outline-color: var(--figma-color-border);
		transition: ease-out 0.1s outline-color;
		transition: ease-out 0.1s background-color;
		outline-offset: -1px;
		background-clip: padding-box;
		box-sizing: border-box;
	}
	.icon-button--secondary:hover {
		outline-color: var(--figma-color-border-onselected);
		transition: ease-out 0.1s outline-color;
	}
	.icon-button--secondary:focus {
		outline-color: var(--figma-color-border-brand);
		transition: ease-out 0.1s outline-color;
	}
	.icon-button--secondary:active {
		outline-color: var(--figma-color-border-brand);
		background-color: var(--figma-color-bg-pressed);
		transition: ease-out 0.1s outline-color;
		transition: ease-out 0.1s background-color;
	}
	.icon-button--tertiary {
		background-color: transparent;
		color: var(--figma-color-text);
		outline: 1px solid transparent;
		transition: ease-out 0.1s background-color;
		outline-offset: -1px;
		background-clip: padding-box;
		box-sizing: border-box;
	}
	.icon-button--tertiary:hover {
		background-color: var(--figma-color-bg-secondary);
		transition: ease-out 0.1s outline-color;
	}
</style>
