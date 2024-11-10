<script>
	/**
	 * @typedef {Object} Props
	 * @property {'primary' | 'secondary' | 'tertiary'} [type] Is this the principal call to action on the page?
	 * @property {'small' | 'medium' | 'large'} [size] How large should the button be?
	 * @property {string} label Button contents
	 * @property {() => void} [onClick] The onclick event handler
	 */

	/** @type {Props} */
	const { type = 'primary', size = 'medium', label, onClick } = $props();
</script>

<button
	type="button"
	class={['button', `button--${size}`, `button--${type}`].join(' ')}
	onclick={onClick}
>
	{label}
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
	}
	.button--primary {
		background-color: var(--figma-color-bg-brand);
		color: var(--figma-color-text-onbrand);
		transition: ease-out 0.1s background-color;
	}
	.button--primary:hover {
		background-color: var(--figma-color-bg-brand-secondary);
		transition: ease-out 0.1s background-color;
	}
	.button--secondary {
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
	.button--secondary:hover {
		outline-color: var(--figma-color-border-onselected);
		transition: ease-out 0.1s outline-color;
	}
	.button--secondary:focus {
		outline-color: var(--figma-color-border-brand);
		transition: ease-out 0.1s outline-color;
	}
	.button--secondary:active {
		outline-color: var(--figma-color-border-brand);
		background-color: var(--figma-color-bg-pressed);
		transition: ease-out 0.1s outline-color;
		transition: ease-out 0.1s background-color;
	}
	.button--tertiary {
		background-color: transparent;
		color: var(--figma-color-text);
		outline: 1px solid transparent;
		transition: ease-out 0.1s background-color;
		outline-offset: -1px;
		background-clip: padding-box;
		box-sizing: border-box;
	}
	.button--tertiary:hover {
		background-color: var(--figma-color-bg-secondary);
		transition: ease-out 0.1s outline-color;
	}
	.button--small {
		font-size: var(--text-body-small-font-size);
		padding: var(--spacer-sm) var(--spacer-md);
		border-radius: var(--radius-small);
	}
	.button--medium {
		font-size: var(--text-body-medium-font-size);
		letter-spacing: var(--text-body-medium-letter-spacing);
		font-weight: var(--text-body-medium-font-weight);
		line-height: var(--text-body-medium-line-height);
		padding: 0 var(--spacer-md);
		border-radius: var(--radius-medium);
		height: var(--spacer-xl);
	}
	.button--large {
		font-size: var(--text-body-medium-font-size);
		letter-spacing: var(--text-body-medium-letter-spacing);
		font-weight: var(--text-body-medium-font-weight);
		line-height: var(--text-body-medium-line-height);
		padding: 0 var(--spacer-lg);
		border-radius: var(--radius-medium);
		height: var(--spacer-xxl);
	}
</style>
